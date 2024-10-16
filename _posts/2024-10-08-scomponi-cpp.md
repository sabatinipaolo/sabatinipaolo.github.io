---
title: "fattorizzazione di un numero"
categories:
    - Blog
tags:
    - sorgente
    - cpp
    - c++
    - scomposizione in fattori primi

permalink: /blog/scomponi/
---

TLDR: sorgente di un file per la scomposizione in fattori primi di un numero

lanciare il comando

```c++

#include <iostream>
#include <string>

using namespace std;

int main()
{
    int n;

    while (1)
    {
        string scomposizione = "";
        // TODO: don't repeat yourself
        cout << "inserire un numero >1 da scomporre in fattori primi, [ ctrl ] + [ d ] per uscire ";
        cin >> n;
        if (std::cin.eof())
        {
            cout << "\n";
            return 0;
        }

        while (n <= 1)
        {
            cout << "errore \n";

            // TODO: don't repeat yourself
            cout << "inserire un numero >1 da scomporre in fattori primi, [ ctrl ] + [ d ] per uscire ";
            cin >> n;
            if (std::cin.eof())
            {
                cout << "\n";
                return 0;
            }
        };

        int n_appo = n;
        int divisore = 1;
        while (n > 1)
        {
            divisore++;
            int esponente = 0;
            while ((n % divisore) == 0)
            {
                n = n / divisore;
                esponente++;
            };

            if (esponente == 0)
                continue;
            scomposizione += to_string(divisore) +
                             (esponente == 1 ? "" : "^" + to_string(esponente)) +
                             (n > 1 ? " * " : "");
        }

        cout << "\n"
             << n_appo << " = " << scomposizione << "\n";
    }
}

```

fatica sprecata!
esiste il comando 

```bash 
 factor 
```
[https://www.gnu.org/software/coreutils/manual/html_node/factor-invocation.html#factor-invocation](https://www.gnu.org/software/coreutils/manual/html_node/factor-invocation.html#factor-invocation)


oltre ad essere molto più performante del mio programma prevede un controllo dell'input come si deve!
Se si passa a parametro una stringa invece di un intero il programma non va in loop infinito...

questo un estratto del sorgente di *factor.c*

```c

  /* Try converting the number to one or two words.  If it fails, use GMP or
     print an error message.  The 2nd condition checks that the most
     significant bit of the two-word number is clear, in a typesize neutral
     way.  */
  strtol_error err = strto2uintmax (&t1, &t0, str);

  switch (err)
    {
    case LONGINT_OK:
      if (((t1 << 1) >> 1) == t1)
        {
          devmsg ("[using single-precision arithmetic] ");
          print_factors_single (t1, t0);
          return true;
        }
      break;

    case LONGINT_OVERFLOW:
      /* Try GMP.  */
      break;

    default:
      error (0, 0, _("%s is not a valid positive integer"), quote (input));
      return false;
    }
```

notare la riga `strto2uintmax (&t1, &t0, str);` di fatto in input legge una stringa e la converte (prova) in un intero positivo se non riesce comunica l'errore.

insomma un input miglior di `cin` ... 