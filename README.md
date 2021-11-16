# Programowanie 1

Postaram się umieścić tu wszystkie zadania i rozwiązania przedmiotu *Programowanie 1*. 
<details><summary>Wstęp - Hello World - Windows/Linux</summary><p>
  
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
</p></details>

## Linki
* [Najlepsze edytory tekstu na Linux (LMGTFY)](https://www.google.com/search?q=code+editor+for+linux)
* [Najlepsze edytory tekstu na Windows (LMGTFY)](https://www.google.com/search?q=code+editor+for+windows)
* [15 najczęściej używanych opcji kompilatora *gcc*](https://www.thegeekstuff.com/2012/10/gcc-compiler-options/)
* [Online edytor schematu blokowego](https://app.diagrams.net/)

<details><summary>Lista 1</summary><p>
  
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
</p></details>
<details><summary>Lista 2</summary><p>
  
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
</p></details>
<details><summary>Lista 3</summary><p>
  
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
## Zadanie 2
![Schemat blokowy L3Z2](https://github.com/HelloProgramowanie/prog1/blob/main/L3Z2.drawio.png)
```c
#include <stdio.h>
#include <conio.h>
#include <string.h>

int main(){
    do{
        printf("Podaj liczbe 0<n<10:\n");
        int n;
        scanf("%d", &n);

        int wynik = 1;

        for (int i=2; i<=n; i++){
            wynik *= i;
        }

        printf("%d! = %d\n", n, wynik);

        printf("Powtorka? nacisnij 'T' jesli tak.\n");
    } while(toupper(getch()) == 'T');
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
## Zadanie 4
![Schemat blokowy L3Z4](https://github.com/HelloProgramowanie/prog1/blob/main/L3Z4.drawio.png)
```c
#include <stdio.h>
#include <conio.h>

int main(){
    unsigned int n;
    char JESZCZERAZ;
    do{
        printf("Podaj liczbe calkowita dodatnia n>=1: ");
        scanf("%u", &n);

        printf("1");

        float suma = 1.0;

        for(unsigned int k=2; k <= n; k++){
            printf(" + 1/%u", k);
            suma += 1.0/k;
        }

        printf(" = %f\n", suma);

        printf("Wykonac jeszcze raz? Nacisnij 't' jesli tak, lub cokolwiek inne zeby wyjsc.\n");
        JESZCZERAZ = getch();
    } while( JESZCZERAZ == 't');
    return 0;
}
```

## Zadanie 5
![Schemat blokowy L3Z5](https://github.com/HelloProgramowanie/prog1/blob/main/L3Z5.drawio.png)
```c
#include <stdio.h>

int main(){
    int _od, _do;

    printf("Podaj liczbe 'od': ");
    scanf("%d", &_od);
    printf("Podaj liczbe 'do': ");
    scanf("%d", &_do);

    if(_od < _do){
        //for(int i = _od; i<=_do; i++){
        for(int i = _od+1; i<_do; i++){
            if(i%2==0 && i>=0){ printf("%d ", i);}
        }
    }else{
        //for(int i = _od; i>=_do; i--){
        for(int i = _od-1; i>_do; i--){
            if(i%2==0 && i>=0){ printf("%d ", i);}
        }
    }
    return 0;
}
```
</p></details>
<details><summary>Lista 4</summary><p>
  
# Lista 4
## Zadanie 1
![Schemat blokowy L4Z1](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1.drawio.png)
```c
#include <stdio.h>

int main(){
    int n;
    do{
        printf("Podaj N: ");
        do {
            scanf("%d", &n);
        } while(n<1 || n>15);
        
        // MAGIC

        printf("Powtorka? 'T' = tak\n\n");
    } while(toupper(getch()) == 'T');
}

```
### Zadanie 1.a
![Schemat blokowy L4Z1a](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1a.drawio.png)
```c
        for(int i=1; i<=n; i++){
            ile_gwiazdek = i;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
```
### Zadanie 1.b
![Schemat blokowy L4Z1b](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1b.drawio.png)
```c
        for(int i=1; i<=n; i++){
            ile_gwiazdek = n-i+1;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
```
### Zadanie 1.c
![Schemat blokowy L4Z1c](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1c.drawio.png)
```c
        for(int i=1; i<=n; i++){
            ile_spacji = n-i;
            while(ile_spacji > 0){ printf(" "); ile_spacji--; }
            ile_gwiazdek = i*2-1;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }

```
### Zadanie 1.d
![Schemat blokowy L4Z1d](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1d.drawio.png)
```c
        for(int i=1; i<=n; i++){
            ile_spacji = i-1;
            while(ile_spacji > 0){ printf(" "); ile_spacji--; }
            ile_gwiazdek = (n-i)*2+1;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
```
### Zadanie 1.e
![Schemat blokowy L4Z1e](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1e.drawio.png)
```c
        printf("jesli n jest parzysty, bedzie traktowany jako n+1\n");
        for(int i=1; i<=n/2+1; i++){
            ile_gwiazdek = i;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
        for(int i=1; i<=n/2; i++){
            ile_gwiazdek = n/2+1-i;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
```
### Zadanie 1.f
![Schemat blokowy L4Z1f](https://github.com/HelloProgramowanie/prog1/blob/main/L4Z1f.drawio.png)
```c
        printf("jesli n jest parzysty, bedzie traktowany jako n+1\n");
        for(int i=1; i<=n/2+1; i++){
            ile_spacji = n/2+1-i;
            while(ile_spacji > 0){ printf(" "); ile_spacji--; }
            ile_gwiazdek = i;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
        for(int i=1; i<=n/2; i++){
            ile_spacji = i;
            while(ile_spacji > 0){ printf(" "); ile_spacji--; }
            ile_gwiazdek = n/2+1-i;
            while(ile_gwiazdek > 0){ printf("*"); ile_gwiazdek--; }
            printf("\n");
        }
```
</p></details>
  
# Lista 5
## Zadanie 1
```c
#include <stdio.h>

int main(){
    int a, b;
    scanf("%d", &a);
    scanf("%d", &b);
    while(a!=b){
        if(a>b) a-=b;
        else b-=a;
    }
    printf("%d",a);
}
```
## Zadanie 2 oraz Zadanie 3
```c
// printf() scanf()
#include <stdio.h>

// strrev()
#include <string.h>

// tolower()
#include <ctype.h>

// getch()
#include <conio.h>


// Funkcja x_mod_y wraca znak ze zakresu <'0', '9'> lub <'A', 'Z'>
// wynik tej funkcji = ostatnia liczba po konwersji liczby x do
// systemu y-owego
char x_mod_y(int x, int y){
    int wynik = x%y;
    if(wynik<10) return '0'+wynik;
    else return 'A'-10+wynik;
}

int main(){

    int liczba_do_konwertowania;
    int system_liczb;
    
    char wynik[17]; // lancuch znakow o dlugosci 17
                    // bo 16 znakow potrzebne zeby zapisac 65535
                    // w systemie binarnym, oraz jeszcze jeden,
                    // aby tam umiescic 0 (0 = koniec tekstu)
                    
    int i,a; // do pozniejszych liczen

    do{
        // Wczytanie liczby do konwertowania
        printf("Jaka liczbe dziesiatna konwertujemy? <0; 65535>\n Liczba do konwertowania: ");
        scanf("%d",&liczba_do_konwertowania);
        
        // Sprawdzenie czy liczba prawidlowa, jesli nie, to zaczynami znowu od poczatku
        if(liczba_do_konwertowania < 0){ printf("Liczba jest ujemna :(\n"); continue; }
        if(liczba_do_konwertowania == 0){ printf("0 w kazdym systemie liczb jest 0\n"); continue; }
        if(liczba_do_konwertowania > 65535){ printf("Liczba jest za duza :(\n"); continue; }
        // Jesli nie zaczynalismy od poczatku, to znaczy ze liczba prawidlowa, mozemy dalej dzialac
        
        // Wczytanie systemu liczb
        printf("Na jaki system liczb konwertujemy? <2; 36>\n System liczb: ");
        scanf("%d",&system_liczb);
        
        // Sprawdzenie czy podana liczba prawidlowa, jesli nie, to leci od poczatku...
        if(system_liczb < 2 || system_liczb > 36){ printf("Nieprawidlowy system liczb :(\n"); continue; }
        // Jesli nie zaczynalismy od poczatku, to znaczy ze liczba prawidlowa, mozemy dalej dzialac

        // wprowadzimy nowa zmienna `a`
        // zeby nie popsuc wartosc zmiennej `liczba_do_konwertowania`
        a=liczba_do_konwertowania;
        
        // i to indeks aktualnego znaku wyniku
        i=0;
        while (a>0){
            // komunikat: co sie dzieje w tej petli
            printf("%2d |%6d %% %d = %c\n",i,a,system_liczb,x_mod_y(a,system_liczb));
            
            // wynik[i] = aktualny znak wyniku
            wynik[i] = x_mod_y(a,system_liczb);
            a/=system_liczb;
            
            // indeks rosnie, wiec jesli nastepny raz wejdziemy w ta petle
            // juz do kolejnego miejsca bedziemy pisac
            i++;
        }
        // i roslo wczesniej, wiec pokazuje kolejne miejsce
        // gdzie trzeba umiescic 0 (0 = koniec tekstu)
        wynik[i]=0;
        
        // potem odwrucimy wynik, bo mamy od tylu zapisane
        strrev(wynik);
        
        // w koncu ladnie wypiszemy wynik
        printf("%d (10) = %s (%d)\n",liczba_do_konwertowania, wynik, system_liczb);

        // pytamy czy powtorzyc
        printf("Powtorka? t=tak\n\n");
    } while (tolower(getch())=='t'); // tolower() zeby dzialalo nawet
                                     // jezeli uzytkownik ma CapsLock wlaczony
}
```
## Zadanie 4
```c
// printf() scanf()
#include <stdio.h>

// srand() rand()
#include <stdlib.h>

// time()
#include <time.h>

// kod z wykladu
void zamiana(int *x, int *y){
    int temp = *x;
    *x = *y;
    *y = temp;
}

int main(){
    // kod z wykladu
    srand((unsigned int)time(NULL));

    // uzupelnienie zbioru liczb
    int zbior_liczb[900];
    for(int i=0;i<=899;i++){
        zbior_liczb[i]=100+i;
    }

    printf("Mieszanie:    0%");
    
    // dostatecznie duzo razy wymienimy dwuch losowych elementow zbioru
    for(int i=1; i<=100000000; i++){
        // zeby uzytkownik sie nie nudzil... ;)
        if(i%1000000==0) printf("%c%c%c%c%3d%%",8,8,8,8, i/1000000);  // printf("%c", 8); = backspace
        
        zamiana(&zbior_liczb[rand()%900], &zbior_liczb[rand()%900]);
    }
    
    // teraz pierwszy 5 element zbioru sa losowe, mozemy je wypisac.
    printf("\n5 roznich losowych liczb:");
    for (int i=0; i<5; i++) printf(" %d", zbior_liczb[i]);

    return 0;
}
```
## Zadanie 5
```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <ctype.h>
#include <conio.h>

// kod z laboratorium
typedef struct {
   int id;
   char imie[20];
   char nazwisko[20];
   int rok_u,mies_u,dzien_u;
} tosoba;

// funkcja co wruci liczbe losowa ze zakresu [min,max)
int losowy(int min, int max){
    return rand()%(max-min)+min;
}

int main(){
    // kod z wykladu
    srand((unsigned int)time(NULL));

    tosoba ktos;
    do{
        // sprintf() dziala podobno do printf()-a tylko zamiast ekranu
        // pisze formatowany tekst do zmiennej char*
        sprintf(ktos.imie, "imie%d", losowy(0, 100));
        sprintf(ktos.nazwisko, "naz%d", losowy(0, 100));
        ktos.rok_u = losowy(1900, 2000);
        ktos.mies_u = losowy(1, 13);
        ktos.dzien_u = losowy(1, 32);
        ktos.id = losowy(1, 100);
        printf("Id: %d\nImie, nazwisko: %s, %s\nData urodzenia: %02d.%02d.%d r.\n",
               ktos.id, ktos.imie, ktos.nazwisko, ktos.dzien_u, ktos.mies_u, ktos.rok_u);
        printf("Generujmy jeszcze jedna osobe? 't'=tak\n");
    } while(tolower(getch())=='t');
    return 0;
}
```
