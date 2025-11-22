# Esercizio 5: Differenza cifra per cifra e media

## Traccia
Scrivere un programma in C che:
* legga in input 20 numeri interi non negativi in base 10;
* memorizzi tali numeri in due array di 10 elementi ciascuno.
* calcoli la differenza cifra per cifra dei 2 array memorizzando il risultato in un terzo array di 10 elementi;
* calcoli la media degli elementi del terzo array.

## Spiegazione

Il programma deve:
1. Leggere 20 numeri interi non negativi
2. Dividere questi numeri in due array da 10 elementi ciascuno
3. Per ogni posizione corrispondente, calcolare la differenza (valore assoluto) tra i due numeri
4. Memorizzare queste differenze in un terzo array
5. Calcolare e stampare la media aritmetica degli elementi del terzo array

**Nota**: "Differenza cifra per cifra" viene interpretata come differenza tra i numeri nelle posizioni corrispondenti, calcolata come valore assoluto.

## Soluzione

```c
#include <stdio.h>
#include <stdlib.h>  // Per abs() o per calcolo manuale del valore assoluto

int main() {
    int array1[10], array2[10], array3[10];
    int i;
    int somma = 0;
    float media;
    
    // Lettura del primo array (10 numeri)
    printf("Inserisci i primi 10 numeri interi non negativi:\n");
    for (i = 0; i < 10; i++) {
        printf("Numero %d: ", i + 1);
        scanf("%d", &array1[i]);
        
        // Verifica che il numero sia non negativo
        if (array1[i] < 0) {
            printf("Errore: il numero deve essere non negativo!\n");
            i--;  // Riprova questa posizione
        }
    }
    
    // Lettura del secondo array (10 numeri)
    printf("\nInserisci i secondi 10 numeri interi non negativi:\n");
    for (i = 0; i < 10; i++) {
        printf("Numero %d: ", i + 1);
        scanf("%d", &array2[i]);
        
        // Verifica che il numero sia non negativo
        if (array2[i] < 0) {
            printf("Errore: il numero deve essere non negativo!\n");
            i--;  // Riprova questa posizione
        }
    }
    
    // Calcolo della differenza cifra per cifra (valore assoluto)
    printf("\nCalcolo delle differenze:\n");
    for (i = 0; i < 10; i++) {
        // Calcola la differenza
        int differenza = array1[i] - array2[i];
        
        // Calcola il valore assoluto
        if (differenza < 0) {
            array3[i] = -differenza;  // oppure: array3[i] = differenza * (-1);
        } else {
            array3[i] = differenza;
        }
        
        // Alternativa usando abs() dalla libreria stdlib.h:
        // array3[i] = abs(array1[i] - array2[i]);
        
        printf("array1[%d] = %d, array2[%d] = %d, differenza = %d\n", 
               i, array1[i], i, array2[i], array3[i]);
    }
    
    // Calcolo della somma degli elementi del terzo array
    for (i = 0; i < 10; i++) {
        somma = somma + array3[i];
    }
    
    // Calcolo della media
    media = (float)somma / 10.0;
    
    // Stampa dei risultati
    printf("\n--- Risultati ---\n");
    printf("Array delle differenze: ");
    for (i = 0; i < 10; i++) {
        printf("%d ", array3[i]);
    }
    printf("\n");
    
    printf("Somma degli elementi: %d\n", somma);
    printf("Media degli elementi: %.2f\n", media);
    
    return 0;
}
```

## Spiegazione del codice

### 1. Dichiarazione variabili
```c
int array1[10], array2[10], array3[10];
```
- Tre array di 10 elementi interi ciascuno
- `array1` e `array2` per memorizzare i numeri in input
- `array3` per memorizzare le differenze

### 2. Lettura primo array
```c
for (i = 0; i < 10; i++) {
    scanf("%d", &array1[i]);
}
```
- Ciclo che legge 10 numeri e li memorizza in `array1`
- Include controllo per numeri non negativi

### 3. Lettura secondo array
```c
for (i = 0; i < 10; i++) {
    scanf("%d", &array2[i]);
}
```
- Ciclo che legge altri 10 numeri e li memorizza in `array2`

### 4. Calcolo differenze
```c
int differenza = array1[i] - array2[i];
if (differenza < 0) {
    array3[i] = -differenza;
} else {
    array3[i] = differenza;
}
```
- Per ogni posizione `i`, calcola la differenza
- Se negativa, calcola il valore assoluto moltiplicando per -1
- Salva il risultato in `array3[i]`

**Alternativa con `abs()`:**
```c
#include <stdlib.h>
array3[i] = abs(array1[i] - array2[i]);
```

### 5. Calcolo somma
```c
for (i = 0; i < 10; i++) {
    somma = somma + array3[i];
}
```
- Somma tutti gli elementi di `array3`

### 6. Calcolo media
```c
media = (float)somma / 10.0;
```
- Converte `somma` in float per ottenere un risultato decimale
- Divide per 10.0 (float) per garantire precisione

## Esempio di esecuzione

```
Inserisci i primi 10 numeri interi non negativi:
Numero 1: 10
Numero 2: 20
Numero 3: 30
Numero 4: 40
Numero 5: 50
Numero 6: 60
Numero 7: 70
Numero 8: 80
Numero 9: 90
Numero 10: 100

Inserisci i secondi 10 numeri interi non negativi:
Numero 1: 5
Numero 2: 25
Numero 3: 15
Numero 4: 45
Numero 5: 55
Numero 6: 50
Numero 7: 75
Numero 8: 70
Numero 9: 95
Numero 10: 110

Calcolo delle differenze:
array1[0] = 10, array2[0] = 5, differenza = 5
array1[1] = 20, array2[1] = 25, differenza = 5
array1[2] = 30, array2[2] = 15, differenza = 15
array1[3] = 40, array2[3] = 45, differenza = 5
array1[4] = 50, array2[4] = 55, differenza = 5
array1[5] = 60, array2[5] = 50, differenza = 10
array1[6] = 70, array2[6] = 75, differenza = 5
array1[7] = 80, array2[7] = 70, differenza = 10
array1[8] = 90, array2[8] = 95, differenza = 5
array1[9] = 100, array2[9] = 110, differenza = 10

--- Risultati ---
Array delle differenze: 5 5 15 5 5 10 5 10 5 10 
Somma degli elementi: 75
Media degli elementi: 7.50
```

## Versione alternativa con abs()

```c
#include <stdio.h>
#include <stdlib.h>  // Per abs()

int main() {
    int array1[10], array2[10], array3[10];
    int i, somma = 0;
    float media;
    
    // ... (lettura array1 e array2 come sopra) ...
    
    // Calcolo differenze con abs()
    for (i = 0; i < 10; i++) {
        array3[i] = abs(array1[i] - array2[i]);
    }
    
    // ... (resto del codice) ...
    
    return 0;
}
```

## Note

- Il valore assoluto garantisce differenze sempre non negative
- La conversione `(float)somma` è importante per ottenere una media decimale
- Il controllo sui numeri negativi può essere opzionale se si assume input corretto
- `abs()` è disponibile in `<stdlib.h>` e semplifica il codice