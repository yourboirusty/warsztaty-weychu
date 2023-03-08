Obok ciebie przepływa pokaźna szkółka [świetlików](https://pl.wikipedia.org/wiki/%C5%9Awietlik_t%C4%99pog%C5%82owy). Muszą rozmnażać się bardzo szybko, żeby osiągać tak duże ilości ryb w jednym stadzie - może [eksponencjalnie](https://pl.wikipedia.org/wiki/Funkcja_wyk%C5%82adnicza#Funkcja_eksponencjalna) szybko? Stwierdzasz że [zamodelujesz](https://pl.wikipedia.org/wiki/Modelowanie_matematyczne) ich rozrost, tak dla pewności.


Nie wiesz za dużo o tym gatunku świetlików, ale możesz domyślać się pewnych rzeczy. Na pewno każdy świetlik tworzy kolejnego świetlika co 7 dni.

Niestety ten proces nie jest dokładnie zsynchronizowany u wszystkich świetlików jednocześnie - jedna ryba może mieć jeszcze 2 dni zanim stworzy kolejną, a inna 4. Możesz więc przedstawić każdą rybę poprzez numer, który przedstawia **liczbę dni które jej zajmą zanim stworzy nowego świetlika**.

Co więcej, uważasz że każda **nowa** ryba, na pewno będzie potrzebowała chwili żeby dorosnąć zanim zacznie tworzyć inne ryby. **Ryba potrzebuje 2 dni żeby dojrzeć**.

Więc, zakładając że masz latarnika z wewnętrznym odliczaniem o wartości `3`:

- Po jednym dniu, jej numer zmieni się na `2`.
- Po kolejnym dniu, jej numer zmieni się na `1`.
- Po kolejnym dniu, jej numer zmieni się na `0`.
- Po kolejnym dniu, jej numer przejdzie na `6` i stworzy **nową** rybę o wartości `8`.
- Po kolejnym dniu, pierwsza ryba ma numer `5`, a druga ryba ma numer o wartości `7`.

Latarnik który stworzy nową rybę, resetuje swój numer na 6, **nie 7** (ponieważ `0` jest przyjmowane jako prawidłowa wartość odliczania). Nowa ryba zaczyna z numerem `8` i nie zaczyna odliczania aż do kolejnego dnia.

Rozumiejąc co potrzebujesz zrobić, komputer pokładowy Twojej łodzi podwodnej, automatycznie produkuje listę z danymi kilkuset latarników w pobliżu (plik który dostaniesz później).
Dla przykładu, otrzymujesz następujące **dane wejściowe**:

```
3,4,3,1,2
```

Jest to **lista** na której pierwsza ryba ma wewnętrzny zegar z numerem `3`, druga ryba ma numer `4` i tak dalej, aż do piątej ryby, która ma wewnętrzny numer `2`. Symulowanie rozmnażania tych ryb wyglądałoby następująco:

```
Initial state: 3,4,3,1,2
After  1 day:  2,3,2,0,1
After  2 days: 1,2,1,6,0,8
After  3 days: 0,1,0,5,6,7,8
After  4 days: 6,0,6,4,5,6,7,8,8
After  5 days: 5,6,5,3,4,5,6,7,7,8
After  6 days: 4,5,4,2,3,4,5,6,6,7
After  7 days: 3,4,3,1,2,3,4,5,5,6
After  8 days: 2,3,2,0,1,2,3,4,4,5
After  9 days: 1,2,1,6,0,1,2,3,3,4,8
After 10 days: 0,1,0,5,6,0,1,2,2,3,7,8
After 11 days: 6,0,6,4,5,6,0,1,1,2,6,7,8,8,8
After 12 days: 5,6,5,3,4,5,6,0,0,1,5,6,7,7,7,8,8
After 13 days: 4,5,4,2,3,4,5,6,6,0,4,5,6,6,6,7,7,8,8
After 14 days: 3,4,3,1,2,3,4,5,5,6,3,4,5,5,5,6,6,7,7,8
After 15 days: 2,3,2,0,1,2,3,4,4,5,2,3,4,4,4,5,5,6,6,7
After 16 days: 1,2,1,6,0,1,2,3,3,4,1,2,3,3,3,4,4,5,5,6,8
After 17 days: 0,1,0,5,6,0,1,2,2,3,0,1,2,2,2,3,3,4,4,5,7,8
After 18 days: 6,0,6,4,5,6,0,1,1,2,6,0,1,1,1,2,2,3,3,4,6,7,8,8,8,8
```

Każdego dnia `0` staje się `6` i dodaje nowe `8` na koniec listy, a każdy inny numer zmniejsza się o `1` **jeżeli istniał na początku dnia**.

W tym przykładzie, po `18` dniach, będzie `26` ryb. Po `80` dniach, będzie `5934` ryb.

Napisz funkcję która na podstawie listy 
```
stado_ryb = [3, 4, 3, 1, 2]
```
policzy **ile ryb będzie w stadzie po 80 dniach**?

> Jedna funkcja może wywoływać inną, rozbij problem na mniejsze części.

> Jeżeli się zatniesz, przerwij i wróć później. Nie musisz tego skończyć, ani nawet zacząć.
Wystarczy że to trochę przemyślisz, chociaż wydaje mi się że powinieneś dać radę.

> Listy posiadają metodę `extend(L: list)`, więcej znajdziesz w [dokumentacji](https://pl.python.org/docs/tut/node7.html).
