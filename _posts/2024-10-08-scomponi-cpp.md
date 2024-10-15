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

TLDR: sorgetnte di unfile per la scomposizione in fattori primi di un numero

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
