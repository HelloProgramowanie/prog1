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
* [Online edytor schematu blokowego](https://app.diagrams.net/)

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
    printf("Podaj znak a-z: ");
    c = getchar();
    // tekst zadania mowi ze tutaj nie trzeba sprawdzic czy podany znak 'a' <= c <= 'z'
    // kod ASCII dla 'A' = 01000001b = 65
    // kod ASCII dla 'a' = 01100001b = 97
    // zeby robic 'A' za pomoca 'a', musimi odejmowac 00100000b = 32
    // 'a' - 32 = 'A'
    printf("%c, %c\n", c-32, c);
    return 0;
}
```
## Zadanie 2
![Schemat blokowy L2Z2](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z2.drawio.png)
```c
#include <stdio.h>

int main(){

  int x; // Zmienna do ktorej wczytujemy liczb podanych przez uzytkownika.
         // Wystarczy nam 1 zmienna, bo nie musimy dlugo zachowac w pamieci wprowadzonych liczb,
         // przeciez mozemy sprawdzac parzystosc od razu po wczytywaniu.
  
  int ilosc_parzystych = 0;  // Ilosc parzystych licz podczas wczytywania.
                             // Skoro jeszcze nie wczytalismy nic, na razie mamy 0 szt. parzystych,
                             // i dokladnie dlatego inicializujemy wartosc zmiennej na 0.
                             
  printf("Podaj 3 liczby:\n");

    // tutaj sprawdze od razu podczas wczytywania liczb, czy podana liczba jest parzysta
    // (liczba jest parzysta, jezeli x % 2 == 0)
    // a jezeli podana liczba jest parzysta, to wartosc zmiennej ilosc_parzystych zwiekszamy o jeden.  

    printf("1. liczba: ");
    scanf("%d", &x);
    if(x%2 == 0) ilosc_parzystych += 1;

    printf("2. liczba: ");
    scanf("%d", &x);
    if(x%2 == 0) ilosc_parzystych += 1;

    printf("3. liczba: ");
    scanf("%d", &x);
    if(x%2 == 0) ilosc_parzystych += 1;

    // teraz skonczylismy wczytywania (i sprawdzania) liczb musimy sprawdzic
    // czy     ilosc_parzystych > 0     i wyswietlic komunikat wedlug tego

  if(ilosc_parzystych > 0) printf("Byla parzysta.");
  else printf("Nie bylo parzystej.");
  return 0;
}
```
Prosił żebyśmy nie używali pętli, bo dla większość nas one są zbyt nowe. Akurat tutaj bardzo dobrze widać, że część kodu (do wczytywania i sprawdzania liczb) prawie `Ctrl+c` - `Ctrl+v`. Jeśli zadanie byłoby to samo, ale byśmy musieli wczytywać 10 lub 100 lub 1000 liczb, to byśmy przecież nie robili pojedynczo. Wtedy za pomocą petli [**for**](https://en.wikipedia.org/wiki/For_loop):

![Schemat blokowy L2Z2b](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z2b.drawio.png)
```c
for(int i=1; i<=3; i+=1){
  printf("%d. liczba: ",i);
  scanf("%d", &x);
  if(x%2 == 0) ilosc_parzystych += 1;
}
```
## Zadanie 3
![Schemat blokowy L2Z3](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z3.drawio.png)
```c
#include <stdio.h>

int main(){
  int a, b, c, najmniejszy, a_kw, b_kw, c_kw;
  printf("Podaj 3 liczby calkowite:\n");
  printf("a = ");
  scanf("%d", &a);
  printf("b = ");
  scanf("%d", &b);
  printf("c = ");
  scanf("%d", &c);
  a_kw=a*a;
  b_kw=b*b;
  c_kw=c*c;
  if(a_kw<b_kw){
    if(a_kw<c_kw){
      najmniejszy = a;
    } else {
      najmniejszy = c;
    }
  } else {
    if(b_kw<c_kw){
      najmniejszy = b;
    } else {
      najmniejszy = c;
    }
  }
  printf("%d ma najmniejszy kwadrat.\n", najmniejszy);
  return 0;
}
```
## Zadanie 4
![Schemat blokowy L2Z4](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z4.drawio.png)
```c
#include <stdio.h>

int main(){
    int min, x;
    printf("Podaj 5 liczb:\n");
    scanf("%d", &min); // kiedy pobieramy pierwsza liczbe, wiemy ze do tej pory ta liczba jest najmniejsza
                       // wiec mozemy od razu zapisac jako min
    scanf("%d", &x); // pobieramy druga liczbe
    if(x<min) min=x; // jezeli ta druga liczba jest mniejsza niz min, zapisujemy ta liczbe jako min
                     // jezeli nie to tylko dzialamy dalej
    scanf("%d", &x); // pobieramy kolejna liczbe
    if(x<min) min=x; // jesli to mniejsza niz nasza najmniejsza, to zapisujemy jako min
    scanf("%d", &x); // i tak dalej jeszcze 2 razy
    if(x<min) min=x;
    scanf("%d", &x);
    if(x<min) min=x; 
    printf("Minimalna: %d", min); // wypiszemy wynik
    return 0;
}
```
## Zadanie 5
![Schemat blokowy L2Z5](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z5.drawio.png)
```c
#include <stdio.h>

int main(){
    int x;
    printf("Podaj liczbe calkowita > 99: ");
    scanf("%d", &x);
    int j = x % 10;
    int d = (x / 10) % 10;
    int s = x / 100;
    printf("%d jednosci, %d dziesiatek, i %d setek", j, d, s);
    return 0;
}
```
## Zadanie 6
### Za pomocą rzutowania
![Schemat blokowy L2Z6](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z6.drawio.png)
```c
#include <stdio.h>
#include <math.h>

int main(){
  int a, pierwiastek;
  printf("Podaj liczbe calkowita: ");
  scanf("%d", &a);
  pierwiastek = (int) sqrt(a);
  if(pierwiastek * pierwiastek == a){
    printf("Ta liczba jest kwadratowa.");
  } else {
    printf("Ta liczba nie jest kwadratowa.");
  }
  return 0;
}
```
Funkcja `sqrt(a)` powie dokladnie ile jest pierwiastek liczby `a`, zwraca typ `double`. Jeśli rzutujemy `double` na `int`, to odrzuczymy wszystko po przecinku. To wykorzystujemy w tym programie. 
Przykłady:

| a | sqrt(a) | pierwiastek = (int) sqrt(a) | pierwiastek² | pierwiastek² == a? |
|---|---------|-----------------------------|--------------|--------------------|
| 0 | 0.000000 | 0 | 0 | tak |
| 1 | 1.000000 | 1 | 1 | tak |
| 2 | 1.414214 | 1 | 1 | nie |
| 3 | 1.732051 | 1 | 1 | nie |
| 4 | 2.000000 | 2 | 4 | tak |
| 5 | 2.236068 | 2 | 4 | nie |
| 6 | 2.449490 | 2 | 4 | nie |
| 7 | 2.645751 | 2 | 4 | nie |
| 8 | 2.828427 | 2 | 4 | nie |
| 9 | 3.000000 | 3 | 9 | tak |
### Za pomocą pętli
![Schemat blokowy L2Z6b](https://github.com/HelloProgramowanie/prog1/blob/main/L2Z6b.drawio.png)
```c
#include <stdio.h>

int main(){
    int x;
    printf("Podaj liczbe calkowita: ");
    scanf("%d", &x);
    int i = 0;
    while (i*i < x){ i++; } // szukamy najmniejsza liczbe kwadratowa ktora jest nie mniejsza niz podana liczba
    if(i*i == x) printf("Ta liczba jest kwadratowa.");
    else printf("Ta liczba nie jest kwadratowa.");
}
```
# Lista 3
## Zadanie 1 https://youtu.be/E4ZuUSWu2w0
![Schemat blokowy L3Z1](https://github.com/HelloProgramowanie/prog1/blob/main/L3Z1.drawio.png)
```c
#include <stdio.h>
#include <string.h>
#include <conio.h>

int main(){

    char JESZCZERAZ;

    do{
        char slowo[50];
        printf("Podaj slowo: ");
        scanf("%s", slowo);
        int len = strlen(slowo);
        int i;
        int PALINDROM = 1;
        for(i=0; i<len/2; i++){
            if(slowo[i] != slowo[len-1-i]){
                PALINDROM = 0;
            }
        }
        if(PALINDROM == 1){
            printf("to jest palindrom");
        } else {
            printf("to nie palindrom");
        }

        printf("\nWpisz 1 zeby powtorzyc, lub cos innego zeby wyjsc.\n");
        JESZCZERAZ = getch();
    } while (JESZCZERAZ == '1');
    return 0;
}
```
## Zadanie 3 https://youtu.be/NI3Scbe2Kfg
![Schemat blokowy L3Z3](https://github.com/HelloProgramowanie/prog1/blob/main/L3Z3.drawio.png)
```c
#include <stdio.h>
#include <conio.h>

int main(){
    for(char JESZCZERAZ = '1'; JESZCZERAZ=='1'; JESZCZERAZ = getch()){
        int tablica[10];

        printf("Podaj 10 liczb calkowytych:\n");
        for(int i = 0; i < 10; i++ ){
            printf("tablica[%d] = ", i);
            scanf("%d", &tablica[i]);
        }

        int min=tablica[0];
        int max=tablica[0];

        for(int i = 1; i < 10; i++ ){
            if(tablica[i] < min){
                min = tablica[i];
            }
            if(tablica[i] > max){
                max = tablica[i];
            }
        }

        printf("Najmniejszy element: %d\n", min);
        printf("Najwiekszy element: %d\n", max);

        printf("\nWpisz 1 zeby powtorzyc, lub cos innego zeby wyjsc.\n");
    }
    return 0;
}
```
