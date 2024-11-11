# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu 
sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. 

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1)) ([UC2](#uc2))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2)) ([UC3](#uc3))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([UC4](#uc4))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu. ([UC5](#uc5))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.

<a id="ac3"></a
### AC2: System

Sytem umożliwiający i przeprowadzający cała operację.

## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC5](#uc5): Przekazanie produktów

[Kupujący](#ac2):
* [UC2](#uc2): Złożenie oferty w aukcji
* [UC4](#uc4): Dokonanie płatności za wygrany produkt

[System](#ac3):
* [UC3](#uc3): Zakończenie aukcji z najwyższą ofertą

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1), [System](#ac3)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. [System](#ac3) prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. [System](#ac3) weryfikuje poprawność danych.
5. [System](#ac3) informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

3.A. [Sprzedający](#ac1) anuluje operację.
* 3.A.1 Koniec przypadku użycia.

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. [System](#ac3) informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Złożenie oferty w aukcji

**Aktorzy:** [Kupujący](#ac2), [System](#ac3)

**Scenariusz główny:**
1. [Kupujący](#ac2) wybiera aukcję.
2. [Kupujący](#ac2) podaje kwotę jaką chce zaoferować.
3. [System](#ac3) weryfikuje, czy oferta jest wyższa od aktualnej.
4. [System](#ac3) rejestruje ofertę jako aktualnie najwyższą.

**Scenariusze alternatywne:** 
2.A. [Kupujący](#ac2) anuluje operację.
* 2.A.1. Koniec przypadku użycia.

3.A. Oferta [Kupującego](#ac2) jest niższa niż aktualna najwyższa.
* 3.A.1. [System](#ac3) informuje o tym, że podana kwota jest niższa niż aktualna oferta.
* 3.A.2. Przejdź do kroku 2.
  
<a id="uc3"></a>
### UC3: Zakończenie aukcji z najwyższą ofertą

**Aktorzy:** [System](#ac3), [Kupujący](#ac2)

**Scenariusz główny:**
1. [System](#ac3) automatycznie kończy aukcję po upływie czasu.
2. [System](#ac3) identyfikuje najwyższą ofertę i przyznaje zwycięstwo [Kupującemu](#ac2).

**Scenariusze alternatywne:**
2.A. [System](#ac3) stwierdza brak ofert.
* 2.A.1. Koniec przypadku użycia.

<a id="uc4"></a>
### UC4: Dokonanie płatności za wygrany produkt

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), [System](#ac3)

**Scenariusz główny:**
1. [Kupujący](#ac2) inicjuje płatność.
2. [System](#ac3) przetwarza płatność i informuje Sprzedającego o dokonaniu wpłaty.

**Scenariusze alternatywne:**
2.A. [System](#ac3) wykrywa brak wystarczających środków.
* 2.A.1. Koniec przypadku użycia.

<a id="uc5"></a>
### UC5: 
**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. [Sprzedający](#ac1) przekazuje produkt [Kupującemu](#ac2).
2. [System](#ac3) usuwa aukcje.

**Scenariusze alternatywne:**
1.A. Brak możliwości dostarczenia produktu.
* 1.A.1. Powtórz krok 1.
---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

### B03: Oferta

Propozycja zakupu składana przez [Kupującego](#ac2) zawierająca kwotę wyższą niż aktualna najwyższa oferta.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.

<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | Oferta |
| ------------------------------------------------- | ------ | ------- | ------ |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    |        |
| UC2: Złożenie oferty w aukcji                     |    R   |         |   C    |
| UC3: Zakończenie aukcji z najwyższą ofertą        |    U   |         |   R    |
| UC4: Dokonanie płatności za wygrany produkt       |    R   |    R    |        |
| UC5: Przekazanie produktów                        |    D   |    U    |        |



Legenda: C - Create (tworzenie), R - Read (odczyt), U - Update (aktualizacja), D - Delete (usuwanie), L - Link (powiązanie).
