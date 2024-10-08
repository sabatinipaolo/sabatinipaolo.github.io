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

int main (){
    int n;
    while (1){
		string scomposizione="";
        //scomposizione="";
       
        cout << "inserire un numero >1 da scomporre in fattori primi, [ ctrl ] + [ d ] per uscire ";
        cin >> n ;
        if (std::cin.eof()){cout << "\n"; return 0;}
        //if ( n == 0 ) return 0;
        while ( n< 1 ){
            cout<<"errore \n";
            cout<< "inserire un numero >1 da scomporre in fattori primi, [ ctrl ] + [ d ] per uscire ";
            cin >> n ;
			if (std::cin.eof()) {cout << "\n"; return 0;}
        };
         
        int nap=n;
        int div= 1;
        while ( n > 1 ) {
			div++;
            int esp= 0;
            while (( n % div )==0 ){
                n = n / div;
                esp++;
            };
            
            if (esp == 0 ) continue; 
            scomposizione += to_string(div) + 
                            ( esp ==1 ? "": "^" + to_string(esp) )  + 
                            ( n > 1 ?  " * ": "");
        
        }
        
        cout <<"\n"<<nap << " = "<< scomposizione<<"\n"; 
    }
}


```