
# BLOK 1 z Architektúry počítačov

Toto je ako taký návod ako som urobil všetky úlohy z Bloku 1

Za tento blok môžeme získať maximálne 10 bodov, čiže netreba robiť všetko :)




 - [Úloha 1.1 - Prevodník na DEC, HEXA a BIN (2b)](#úloha-11)
 - [Úloha 1.2 - Prevodník na rímske číslice (2b)](#úloha-12)
 - [Úloha 1.3 - Fibonacciho postupnosť (2b)](#úloha-13)
 - [Úloha 1.4 - Strojový Epsilon (3b)](#úloha-14)
 - [Úloha 1.5 - Sínus, Kosínus (4b)](#úloha-15)
 - [Úloha 1.6 - IntelHEX a kontrolný súčet (4b)](#úloha-16)
 ---
 ---
 ---
 ---
## Úloha 1.1
- Ako prvé som si vyjadril moje číslo a písmeno pomocou INT
```
int cislo=33777, pismeno=0;
```
- Následne jednoduchý **printf()** kde je požiadavka na používateľa o zadanie písmena (napr. X). Načítanie písmena som docielil pomocou **getchar()**, ale môže sa použiť aj **scanf()**
- Ku koncu už je len prevod v **printf()**

| Formátovanie            | Zápis                                                               |
| ----------------- | ------------------------------------------------------------------ |
| Desiatkové číslo | %d |
| Hexadecimálne číslo | %x |
| Osmičkové číslo | %o |
| Jeden znak |  %c  |
| Reťazec | %s |
| Číslo s pohyblivou rádovou čiarkou | %f |
| Číslo s pohyblivou rádovou čiarkou vo vedeckom zápise| %e *alebo* %E |

- Ďalej treba urobiť funkciu, ktorá nám umožní previesť číslo z decimálnej (**desiatkovej) na binárnu (*dvojkovú*)
- Toto som urobil pomocou pola a modula...
- Najskôr som definoval pole a aj premenné:
```
 int pole[8], i;
```
- Následne pomocou prvého **for loop()u** som bol schopný zistiť hodnotu buď **1** alebo **0** a zapísať ju do už preddefinovaného pola:
```
for(i=0;znak>0;i++) 
    {
        pole[i]=znak%2;
        znak=znak/2;
    }
```
- Druhý for loop() slúži na vypísanie cifry:
```
 for(i=i-1;i>=0;i--)  
    {
        printf("%d",pole[i]);
    }
```

- Pre pochopenie... funkcia dostane číslo 12, ako prvé čo sa urobí je to, že číslo **12%2** čo je **0** (0 je posledné číslo v binárnom zápise) a číslo 12/2 nám už dá 6... Toto sa opakuje dokým **znak>0**
- Následne v druhom **for loop()e** máme ošetrené to, že sa nám čísla vypisujú od zadu... To znamená, že síce po prvom **for loop()e** by sme mali výpis **0011** tak tento druhý **for loop()** nám zabezpečí to, že sa čísla vypíšu v správnom poradí **1100**
---
 ---
 ---
 ---


## Úloha 1.2
- Ako aj pri predošlej úlohe definoval som si INT a následne pomocou **printf()** sme požiadali používateľa o číslo, ktoré chce previesť
- Tu som už použil **scanf()**
- Urob som jednoudchú funckiu, ktorá zoberie poskytnutú premennú a ak táto premenná je vyššia ako 100 (ako prvý **if**) tak následne odpočíta číslo 100 od nami zvolenej premennej
- Táto funckia je urobená pomocou while a bude sa opakovať až dokým premenná nebude 0
```
 while(n != 0)
    {

        if (n >= 100)   // 100 - C
        {
           printf("C");
           n -= 100;
        }

        else if (n >= 90)    // 90 - XC
        {
           printf("XC");
           n-= 90;
        }
        .
        .
        .
        .
```
---
 ---
 ---
 ---

## Úloha 1.3
- Fibonacciho postupnosť sa počíta tak, že predošlé dva členy sa zrátajú dokopy tým nám vznikne nový tretí člen...
- Tu sa náš druhý a tretí sčítajú a vznikne štvrtý atď.
- Touto logikou vieme urobiť aj **for loop()**, ktorý bude pokračovať až dokým nenastane 
    -

- najskôr som si definoval INT:
```
int premenna=0,premenna1=1,nasledujuca_premenna=premenna+premenna1, k=0, i =0;
```
- A vďaka tomuto som vedel urobiť **for loop()**, ktorý pôjde až dokým **i** bude menšie alebo rovné ako používateľom zvolené **k**
```
for(i=1;i<=k;i++)
    {
        printf(", %d",nasledujuca_premenna);
        premenna = premenna1;
        premenna1 = nasledujuca_premenna;
        nasledujuca_premenna= premenna+premenna1;
        if (nasledujuca_premenna>k) break;
    }
```
- Loop najskôr vypíše nasledujúcu premennú, ktorá bola vypočítaná už pri definovaní premenných...
- Potom premenná čo bola **0** bude prepísaná na **1**
- A premenna 1 bude prepísaná z **1** na **1**
- Ďalej sa definuje nasledujúca premenná ako premenná+premenná1, čiže to bude **2**
-Loop pokračuje až dokým nasledujúca premenná nebude väčšia ako je používateľom zvolené **k** (*Vtedy loop dostane break a Fibonacciho postupnosť nebude pokračovať ďalej*)

## Úloha 1.4
- __Strojový epsilon__ - je ako malý merač, ktorý pomáha počítačom rozhodovať, či sú čísla skoro rovnaké. Je to taký mikroskopický "limit" pre presnosť výpočtov.
