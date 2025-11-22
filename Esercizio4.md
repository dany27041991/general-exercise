# Esercizio 4: Diagramma di flusso - Differenza cifra per cifra e media

## Traccia
Si disegni il diagramma di flusso dell'algoritmo che:
* legga in input 20 numeri interi non negativi in base 10;
* memorizzi tali numeri in due array di 10 elementi ciascuno.
* calcoli la differenza cifra per cifra dei 2 array memorizzando il risultato in un terzo array di 10 elementi;
* calcoli la media degli elementi del terzo array.

## Spiegazione

L'algoritmo deve:
1. Leggere 20 numeri interi non negativi
2. Dividere questi numeri in due array da 10 elementi ciascuno
3. Per ogni posizione, calcolare la differenza tra i due numeri corrispondenti (valore assoluto)
4. Memorizzare queste differenze in un terzo array
5. Calcolare la media aritmetica degli elementi del terzo array

**Nota**: "Differenza cifra per cifra" viene interpretata come differenza tra i numeri nelle posizioni corrispondenti dei due array, calcolata come valore assoluto per garantire un risultato non negativo.

## Algoritmo

1. **INIZIO**
2. Dichiara `array1[10]`, `array2[10]`, `array3[10]`
3. Inizializza `i = 0`
4. **Ciclo 1**: Per `i` da 0 a 9:
   - Leggi numero e salva in `array1[i]`
5. **Ciclo 2**: Per `i` da 0 a 9:
   - Leggi numero e salva in `array2[i]`
6. **Ciclo 3**: Per `i` da 0 a 9:
   - `array3[i] = |array1[i] - array2[i]|` (valore assoluto)
7. Inizializza `somma = 0`
8. **Ciclo 4**: Per `i` da 0 a 9:
   - `somma = somma + array3[i]`
9. `media = somma / 10.0`
10. Stampa `media`
11. **FINE**

## Diagramma di flusso

```mermaid
flowchart TD
    START([INIZIO]) --> DECLARE["Dichiara array1, array2, array3<br/>di 10 elementi ciascuno"]
    DECLARE --> INIT1["i = 0"]
    INIT1 --> LOOP1{"i < 10?"}
    LOOP1 -->|NO| INIT2["i = 0"]
    LOOP1 -->|SÌ| READ1["Inserisci numero non negativo:"<br/>Leggi numero"]
    READ1 --> VALID1{"numero < 0?"}
    VALID1 -->|SÌ| ERROR1["Errore! Riprova"]
    ERROR1 --> READ1
    VALID1 -->|NO| STORE1["array1[i] = numero"]
    STORE1 --> INCR1["i = i + 1"]
    INCR1 --> LOOP1
    INIT2 --> LOOP2{"i < 10?"}
    LOOP2 -->|NO| INIT3["i = 0"]
    LOOP2 -->|SÌ| READ2["Inserisci numero non negativo:"<br/>Leggi numero"]
    READ2 --> VALID2{"numero < 0?"}
    VALID2 -->|SÌ| ERROR2["Errore! Riprova"]
    ERROR2 --> READ2
    VALID2 -->|NO| STORE2["array2[i] = numero"]
    STORE2 --> INCR2["i = i + 1"]
    INCR2 --> LOOP2
    INIT3 --> LOOP3{"i < 10?"}
    LOOP3 -->|NO| INIT4["somma = 0<br/>i = 0"]
    LOOP3 -->|SÌ| CALC_DIFF["diff = array1[i] - array2[i]"]
    CALC_DIFF --> CHECK_DIFF{"diff < 0?"}
    CHECK_DIFF -->|SÌ| ABS["diff = -diff"]
    CHECK_DIFF -->|NO| STORE["array3[i] = diff"]
    ABS --> STORE
    STORE --> INCR3["i = i + 1"]
    INCR3 --> LOOP3
    INIT4 --> LOOP4{"i < 10?"}
    LOOP4 -->|NO| MEDIA["media = somma / 10.0"]
    LOOP4 -->|SÌ| SUM["somma = somma + array3[i]"]
    SUM --> INCR4["i = i + 1"]
    INCR4 --> LOOP4
    MEDIA --> PRINT["Stampa media"]
    PRINT --> END([FINE])
```

## Descrizione dettagliata dei passaggi

1. **Inizializzazione**: Si dichiarano tre array di 10 elementi ciascuno

2. **Lettura primo array** (10 numeri):
   - Ciclo da 0 a 9
   - Per ogni iterazione, legge un numero e lo salva in `array1[i]`

3. **Lettura secondo array** (10 numeri):
   - Ciclo da 0 a 9
   - Per ogni iterazione, legge un numero e lo salva in `array2[i]`

4. **Calcolo differenze**:
   - Ciclo da 0 a 9
   - Per ogni posizione `i`, calcola `diff = array1[i] - array2[i]`
   - Se `diff < 0`, calcola il valore assoluto: `diff = -diff`
   - Salva `diff` in `array3[i]`

5. **Calcolo media**:
   - Inizializza `somma = 0`
   - Ciclo da 0 a 9 per sommare tutti gli elementi di `array3`
   - Calcola `media = somma / 10.0` (divisione float per precisione)

6. **Output**: Stampa la media calcolata

## Esempio di esecuzione

**Input:**
- Array1: [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
- Array2: [5, 25, 15, 45, 55, 50, 75, 70, 95, 110]

**Calcolo differenze:**
- array3[0] = |10 - 5| = 5
- array3[1] = |20 - 25| = 5
- array3[2] = |30 - 15| = 15
- array3[3] = |40 - 45| = 5
- array3[4] = |50 - 55| = 5
- array3[5] = |60 - 50| = 10
- array3[6] = |70 - 75| = 5
- array3[7] = |80 - 70| = 10
- array3[8] = |90 - 95| = 5
- array3[9] = |100 - 110| = 10

**Array3:** [5, 5, 15, 5, 5, 10, 5, 10, 5, 10]

**Media:** (5+5+15+5+5+10+5+10+5+10) / 10 = 75 / 10 = 7.5

## Note

- Il valore assoluto garantisce che le differenze siano sempre non negative
- La divisione per 10.0 (float) assicura un risultato decimale preciso
- I numeri sono memorizzati in base 10 come specificato