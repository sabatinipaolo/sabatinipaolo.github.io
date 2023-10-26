
**Installazione mingw (compilatore)** 
\
- [ ] **rimuovere** dalla variabile di sistema path (sia utente che sistema ) `c:\mingw`  `c:\mingw64`  se esistono
- [ ] **aggiungere** nella variabile di sistema path  `C:\msys64\ucrt64\bin` 
- [ ] (consigliato) cancellare le directory `c:\mingw`  `c:\mingw64`  se esistono
- [ ] scaricare ed installare come amministratore mingw via MSYS2  da [questo link](https://github.com/msys2/msys2-installer/releases/download/2023-05-26/msys2-x86_64-20230526.exe )
- [ ] a fine installazione **eseguire MSYS2** e dentro la consolle **digitare il comando** :
\
```pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain```
\
premere invio, invio e  e accettare tutti i default 


- [ ] aprire un prompt dei comandi  e digitare i comandi :
\
gcc --version\
g++ --version\
gdb --version

**Installazione VisualCodeStudio**

- [ ] se la versione di visual code non è 1.83.1  disinstallarla

- [ ] installazione di visualcode 1.83.1  [download da questo link] (https://code.visualstudio.com/Download#) (system installer X64 il file si chiama VSCodeSetup-x64-1.83.1.exe ) 

**A FINE INSTALLAZIONE CHIUDERE VISUAL CODE E RIAPRIRLO COME UTENTE !!**
\


**installazione plugin per il c/c++!!**

- [ ] installare l'estensione "C/C++ IntelliSense, debugging, and code browsing". della microsoft


- [ ] provare run e debug con hello.cpp 
