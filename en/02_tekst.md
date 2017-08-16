# Rozdział 2. Tekst

W tym rozdziale:

* dowiesz się czym jest `string` i co można z nim zrobić,
* nauczysz się pisać programy, które wyświetlają tekst.

## String

Niemal każdy program generuje jakiś tekst.  Aplikacje na smartfonach
pokazują komunikaty o odebranych wiadomościach.  Aplikacje webowe zwracają
treść stron internetowych.  Serwery zapisują na dysku informacje o tym jak
przebiega ich działanie.  Tekst to podstawa komunikacji między komputerem
a człowiekiem.  Właśnie dlatego naukę programowania zaczniemy od operacji
na tekście, lub, jak mówimy w żargonie programistycznym, na **stringach**.

String, czyli łańcuch znaków, to po prostu ciąg liter, cyfr, kropek,
przecinków etc. Żeby w Pythonie zdefiniować string, po prostu umieść jakiś
tekst między znakami `'` (pojedynczy apostrof):

```python
>>> 'PyLadies 2017'
```

W powyższym stringu znalazły się duże i małe litery, odstęp (spacja) oraz
cyfry.  Istnieją [tysiące znaków](https://pl.wikipedia.org/wiki/Unikod)
jakich możesz użyć.

:snake: Zanim przejdziesz dalej spróbuj samodzielnie utworzyć stringi
z następującymi informacjami: Twoje imię i nazwisko, nazwa miejscowości
z której pochodzisz, tytuł Twojego ulubionego filmu lub książki.


## Apostrofy

Przykład, którym posłużyliśmy się przed chwilą, pokazuje string ujęty
w pojedyncze apostrofy, czyli `'`.  Jeżeli chcesz, możesz używać znaku
`"`.  Dla Pythona nie ma to żadnego znaczenia.  Ważne jest natomiast,
aby z obu stron stringa znalazł się taki sam apostrof: jeżeli zaczynasz
podwójnym, musisz zakończyć podwójnym.  Tak samo z pojedynczym.


## Operacje na stringach

Teraz, kiedy już umiesz zdefiniować stringa, spróbujmy wykonać na nim
jakąś operację.  Przez "operację" rozumiemy przekształcenie jednego
stringa na inny string, na przykład:

```python
>>> 'Kubuś Puchatek'.lower()
'kubuś puchatek'
```

(Zwróć uwagę na brak spacji wokół kropki!)

W tym przykładzie wykonaliśmy dwie operacje: zdefiniowaliśmy stringa
`'Kubuś Puchatek'` oraz **wywołaliśmy metodę** `lower`.  Metoda to po
prostu operacja jaką można wykonać na jakimś obiekcie.  W tym przypadku
obiektem jest nasz string, a metoda powoduje stworzenie nowego stringa,
w którym wszystkie wielkie litery zostały zastąpione małymi.

String w Pythonie posiada wiele innych metod, na przykład:

* `upper` - przeciwieństwo `lower`,
* `title` - zamienia każdą pierwszą literę każdego wyrazu z małej na
wielką,
* `strip` - usuwa spacje z lewej i prawej strony stringa (jeżeli
istnieją).

:snake: Teraz wypróbuj te metody w taki sposób, żeby zobaczyć efekty ich
działania.  Przetestuj je na stringach, które tworzyliśmy w poprzednim
zadaniu.


## Do czego służą operacje na stringach?

Pisząc programy często musimy sobie radzić ze stringami, które pochodzą
ze źródeł na które nie mamy wpływu.  Na przykład informacje z formularza
wypełnionego przez użytkownika, albo dane odczytane z pliku.
We wszystkich tych przypadkach przetwarzamy stringi, o których strukturze
nic nie wiemy.  Operacje pomagają nam przekształcić stringi na jednolitego
formatu, albo wyszukać w nich jakieś informacje.

Dobrym przykładem jest imię i nazwisko.  Wyobraź sobie, że tworzysz
program, który pobiera od użytkownika jego imię i nazwisko.  Chcesz
zapisać te dane w formacie `Imię Nazwisko`, czyli tak, aby każde ze słów
zaczynało się wielką literą.  Problem polega na tym, że użytkownik może
wpisać `jan kowalski`, albo `JAN KOWALSKI`.  W obu przypadkach dostaniesz
stringi w innym formacie niż się spodziewasz.  Możesz sobie z tym poradzić
używając metody `title`, która obie te wartości zamieni na `Jan Kowalski`.


## Operacje z argumentami

Niektóre operacje wymagają podania dodatkowych opcji.  Na przykład:

```python
>>> 'Kubuś Puchatek'.find('Pu')
6
```

Metoda `find` wyszukuje w stringu podany łańcuch i zwraca numer znaku, w
którym ten łańcuch się zaczyna.  Zwróć uwagę, że znaki numerowane są od
zera:

```
K u b u ś   P u c h ...
0 1 2 3 4 5 6 7 8 9 ...
```

Wywołaliśmy metodę `find` podając jej stringa `'Pu'`.  Taki łańcuch
znajduje się wewnątrz stringa `'Kubuś Puchatek'` i zaczyna się od znaku
numer 6, dlatego tą liczbę zobaczyliśmy na ekranie.

Wartości, które musimy podać wywołując metodę (np. `'Pu'` z przykładu)
nazywamy **argumentami**.  Niektóre metody nie przyjmują żadnych
argumentów, ale są też takie, które wymagają podania jednego lub więcej.
Jeżeli metoda przyjmuje wiele argumentów, to muszą być oddzielone od
siebie przecinkami.


## `find`, `replace`, `count`

Nie będziemy teraz przechodzili przez wszystkie metody jakie posiada
string, ale trzy z nich warto poznać już na samym początku.

### `find`

`find` jako argument przyjmuje string i szuka go w stringu na jakim
wywołaliśmy operację.  Jeżeli łańcuch zostanie znaleziony, otrzymujemy
numer znaku od którego się zaczyna.  W przeciwnym wypadku dostaniemy `-1`.

Ta metoda jest przydatna na przykład kiedy szukamy jakieś frazy i chcemy
się przekonać czy dany string ją zawiera.

```python
>>> 'Anna Nowak'.find('Nowak')
5
>>> 'Jan Kowalski'.find('Nowak')
-1
>>> 'Tomasz Nowak'.find('Nowak')
7
```

Zwróć uwagę, że wielkość liter ma znaczenie:

```python
>>> 'Prosiaczek'.find('Pro')
0
>>> 'Prosiaczek'.find('pro')
-1
>>> 'prosiaczek'.find('Pro')
-1
```

### `replace`

`replace` przyjmuje dwa argumenty: stringi `a` i `b`.  Kiedy wywołamy tę
metodę na stringu, to wszystkie wystąpienia łacucha `a` zostaną zastąpione
łańcuchem `b`.

Przykładowo, możesz zastąpić wszystkie spacje znakiem `-`:

```python
>>> 'Ala ma kota'.replace(' ', '-')
'Ala-ma-kota'
```

Albo zastąpić całe wyrazy:

```python
>>> 'Ala ma kota'.replace('kota', 'psa')
'Ala ma psa'
```

Innym przykładem użycia tej metody jest usunięcie ze stringa jakiegoś
znaku.  Możesz to zrobić podając pusty string jako drugi argument:

```python
>>> 'Jan Kowalski'.replace('Kowalski', '')
'Jan '
```
### `count`

`count` przyjmuje jeden string jako argument i zwraca liczbę wystąpień
tego łańcucha w stringu na jakim wykonaliśmy operację.

Metoda ta przydaje się, kiedy na przykład chcemy sprawdzić czy jakaś
fraza powtarza się więcej niż raz w danym stringu:

```python
>>> 'Ala ma kota'.count('ma')
1
>>> 'Ala ma kota, a Ola ma psa'.count('ma')
2
```

:snake: Zdefiniuj kilka stringów i na każdym z nich wywołaj każdą z
powyższych metod.  Upewnij się, że rozumiesz jak działają, a w razie
wątpliwości poproś o pomoc mentora.


## Długość stringa, funkcja `len`

Jedną z najbardziej przydatnych operacji jaką możemy wykonać na stringu
jest sprawdzenie jego długości.  Na przykład chcemy sprawdzić czy nie
jest zbyt długi, albo chcemy sprawdzić który z dwóch stringów jest
dłuższy.  Tutaj z pomocą przychodzi funkcja `len`:

```python
>>> len('Kubuś Puchatek')
14
```

Zwróć uwagę, że `len` nie jest metodą, czyli nie stosujemy notacji
`obiekt.metoda()`.  Dzieje się tak, ponieważ sprawdzenie długości
jakiegoś obiektu (w tym przypadku: stringa) jest na tyle popularną
operacją, że w Pythonie stworzono osobną funkcję która ją wykonuje.

:snake: Sprawdź długość Twojego imienia i nazwiska. Zobacz jaką długość
ma pusty string, czyli `''`.


## :pushpin: Podsumowanie

W tym rozdziale:

* dowiedzieliśmy się czym jest string,
* poznaliśmy znaczenie słów **metoda** oraz **argument**,
* nauczyliśmy się najważniejszych metod jakie można wywołać na stringu,
* poznaliśmy funkcję `len`, która zwraca długość stringa.

---

:checkered_flag: Następny rozdział: [Funkcja `help`](./03_help.md)
:checkered_flag:
