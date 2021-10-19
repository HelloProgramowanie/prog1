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

#define PI 3.14159265359f
int main()
{
  float R;
  printf("R=");
  scanf("%f", &R);
  printf("P=%f, oraz V=%f", PI*4*R*R, PI*4/3*R*R*R); 
  return 0;
}
```
Wykorzystując że w przypadku operatorów dwuargumentowych łączność określa, w jaki sposób grupowane jest wykonywanie wyrażenia. `*` i `/` (i `%`) się wykonuje *od lewej do prawej*.
  * `float*int=float`
  * `float/int=float`

Nie działa jeśli liczymy `4/3*R*R*R*PI`, przecież `int/int=int`, w tym przypadku `4/3=1`. Żeby zapobiec błędów możemy używać `float` *wszędzie* w ten sposób: `4.0f/3.0f*R*R*R*PI`.
## Zadanie 3
Jeżeli oczekujemy podanych liczb *całkowitych*:
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
Jeżeli oczekujemy podanych liczb *rzeczywistych*:
```c
#include <stdio.h>

int main(){
  float A,B,C,D;
  printf("A=");
  scanf("%f",&A);
  printf("B=");
  scanf("%f",&B);
  printf("C=");
  scanf("%f",&C);
  D = B*B-4*A*C;
  printf("D=%f",D);
  return 0;
}
```
## Zadanie 4
```c
#include <stdio.h>

int main(){
  int C;
  printf("C=");
  scanf("%d",&C);
  if(C!=0) printf("%d",(C+5)*C*C);
  else print("error: Dzielenie z 0");
  return 0;
}
```
wykorzystując że `x*2-x=x` , oraz `x/(1/y)=x*y`
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
  printf("%d%%%d=", a, b);
  if(b!=0){printf("%d", a%b);} else{printf("n/a");}
  return 0;
}
```
# Lista 2
## Zadanie 1
```c
#include <stdio.h>

int main(){
    char c;
    printf("Podaj znak a-z lub A-Z: ");
    c = getchar();
    if(c < 'a') printf("%c, %c\n", c, c+32);
    else printf("%c, %c\n", c-32, c);
    return 0;
}
```
## Zadanie 2
```c
#include <stdio.h>

int main(){
    int PARZYSTY = 0;
    int x;
    printf("Podaj 3 liczby:\n");
    for(int i=1; i<=3; i++){
        printf("%d. liczba: ", i);
        scanf("%d", &x);
        if(x%2 == 0) PARZYSTY = 1;
    }
    if(PARZYSTY == 1) printf("Byla parzysta.");
    else printf("Nie bylo parzystej.");
    return 0;
}
```
