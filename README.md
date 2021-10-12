# Programowanie 1

Postaram się umieścić tu wszystkie zadania i rozwiązania przedmiotu *Programowanie 1*. 

## Hello World!
```c
#include <stdio.h>

int main(){
  printf("Hello World!\n");
  return 0;
}
```

### Linux
* Otworzymy sympatyczny edytor tekstu, zapiszemy wyższy kod jako `~/prog1/hello.c`.
* [Otworzymy terminal, i nawigujemy do miejsca roboczego](https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal). `cd ~/prog1/`
* Kompilujemy program pisząc w terminal `gcc hello.c -o hello` gdzie `gcc` to jest kompilator C, `hello.c` to jest input dla kompilatora, `-o hello` zaznacza że output bedzie plik o nazwie `hello` bez rozszerzenia. 
* Uruchomiemy program pisząc w terminal `./hello` gdzie `./` zaznacza aktualny katalog roboczy, i `hello` to nazwa pliku do uruchomienia.

### Windows
* Otworzymy sympatyczny edytor tekstu, zapiszemy wyższy kod jako `c:\prog1\hello.c`.
* [Otworzymy terminal, i nawigujemy do miejsca roboczego](https://www.howtogeek.com/659411/how-to-change-directories-in-command-prompt-on-windows-10/). `cd c:\prog1\`
* Kompilujemy program pisząc w terminal `gcc hello.c -o hello.exe` gdzie `gcc` to jest kompilator C, `hello.c` to jest input dla kompilatora, `-o hello.exe` zaznacza że output bedzie plik o nazwie `hello.exe`. 
* Uruchomiemy program pisząc w terminal `hello.exe`.

### Różnica
* W ścieżce pliku ukośnik w przód (`/`) w Linuksie kontra ukośnik odwrotny (`\`) w Windows.
* Brak rozszerzenia pliku uruchamialnego w Linuksie kontra `.exe` w Windows.
* W systemach Linux wielkość litera ma znaczenia (case sensitive) nie tylko w komendach a także w nazwach plików! 

| Działanie | Linux | Windows |
|-----------|-------|---------|
| Zapisiwanie pliku | `~/prog1/hello.c` | `C:\prog1\hello.c` |
| Nawigacja w wierszu poleceń | `cd ~/prog1` | `cd C:\prog1` |
| Kompilacja | `gcc hello.c -o hello` | `gcc hello.c -o hello.exe` |
| Uruchomienie | `./hello` | `hello.exe` |


## Linki
* [Najlepsze edytory tekstu na Linux (LMGTFY)](https://www.google.com/search?q=code+editor+for+linux)
* [Najlepsze edytory tekstu na Windows (LMGTFY)](https://www.google.com/search?q=code+editor+for+windows)
* [15 najczęściej używanych opcji kompilatora *gcc*](https://www.thegeekstuff.com/2012/10/gcc-compiler-options/)

# Lista 1
## Zadanie 1
```c
#include <stdio.h>

int main()
{
  printf("Jan Kowalski, adres: 48-140 Wodka, ul. Przykladowa 1, tel.: 696969696");
  return 0;
}

```
## Zadanie 2
```c
#include <stdio.h>

int main()
{
  float R;
  printf("R=");
  scanf("%f", &R);
  printf("V=%f", 3.14f*4/3*R*R*R);
  return 0;
}
```
## Zadanie 3
```c
#include <stdio.h>

int main(){
  int A,B,C,D;
  printf("A=");
  scanf("%d",&A);
  printf("B=");
  scanf("%d",&B);
  printf("C=");
  scanf("%d",&C);
  D = B*B-4*A*C;
  printf("D=%d",D);
  return 0;
}
```
## Zadanie 4
```c
#include <stdio.h>

int main(){
  int c;
  printf("C=");
  scanf("%d",&c);
  printf("%d",(c*2-c+5)/(1.0/c*c));
  return 0;
}
```
## Zadanie 5
```c
#include <stdio.h>

int main(){
  int a,b;
  printf("A=");
  scanf("%d",&a);
  printf("B=");
  scanf("%d",&b);
  printf("%d+%d=%d | ", a, b, a+b);
  printf("%d-%d=%d | ", a, b, a-b);
  printf("%d*%d=%d | ", a, b, a*b);
  printf("%d/%d=", a, b);
  if(b!=0){printf("%d | ", a/b);} else{printf("n/a | ");}
  printf("%d%%%d = ", a, b);
  if(b!=0){printf("%d", a%b);} else{printf("n/a");}
  return 0;
}
```
