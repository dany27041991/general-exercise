# Esercizio 9: Sottrazione posizione da elementi array

## Traccia
Scrivere un programma in C che:
* legga in input 20 numeri interi non negativi in base 10 e li memorizzi in un array;
* memorizzi in un secondo array il numero ottenuto sottraendo a ciascun elemento la sua posizione.

## Spiegazione

Il programma deve:
1. Leggere 20 numeri interi non negativi
2. Memorizzarli in un primo array
3. Creare un secondo array dove ogni elemento è ottenuto sottraendo la posizione (indice) dal valore corrispondente del primo array

**Formula**: `array2[i] = array1[i] - i`

Dove `i` è la posizione (indice) dell'elemento nell'array, che parte da 0.

**Esempio**:
- Se `array1[0] = 10`, allora `array2[0] = 10 - 0 = 10`
- Se `array1[1] = 15`, allora `array2[1] = 15 - 1 = 14`
- Se `array1[2] = 8`, allora `array2[2] = 8 - 2 = 6`

## Soluzione

```c
#include <stdio.h>

int main() {
    int array1[20];  // Array per memorizzare i numeri in input
    int array2[20];  // Array per memorizzare i risultati
    int i;
    
    // Lettura dei 20 numeri
    printf("Inserisci 20 numeri interi non negativi:\n");
    for (i = 0; i < 20; i++) {
        printf("Numero %d (posizione %d): ", i + 1, i);
        scanf("%d", &array1[i]);
        
        // Verifica che il numero sia non negativo
        if (array1[i] < 0) {
            printf("Errore: il numero deve essere non negativo!\n");
            i--;  // Riprova questa posizione
        }
    }
    
    // Calcolo del secondo array: sottrazione della posizione
    for (i = 0; i < 20; i++) {
        array2[i] = array1[i] - i;
    }
    
    // Stampa dei risultati
    printf("\n--- Risultati ---\n");
    printf("Array originale (array1):\n");
    for (i = 0; i < 20; i++) {
        printf("array1[%2d] = %3d\n", i, array1[i]);
    }
    
    printf("\nArray con sottrazione posizione (array2):\n");
    for (i = 0; i < 20; i++) {
        printf("array2[%2d] = array1[%2d] - %2d = %3d\n", 
               i, i, i, array2[i]);
    }
    
    return 0;
}
```

## Spiegazione del codice

### 1. Dichiarazione array
```c
int array1[20];  // Array per memorizzare i numeri in input
int array2[20];  // Array per memorizzare i risultati
```
- `array1[20]`: memorizza i 20 numeri inseriti dall'utente
- `array2[20]`: memorizza i risultati dopo la sottrazione della posizione

### 2. Lettura input
```c
for (i = 0; i < 20; i++) {
    printf("Numero %d (posizione %d): ", i + 1, i);
    scanf("%d", &array1[i]);
}
```
- Ciclo che legge 20 numeri
- Ogni numero viene salvato in `array1[i]` dove `i` è la posizione (0-19)
- Include controllo per numeri non negativi

### 3. Calcolo sottrazione posizione
```c
for (i = 0; i < 20; i++) {
    array2[i] = array1[i] - i;
}
```
- Per ogni posizione `i`:
  - Sottrae `i` (la posizione) da `array1[i]`
  - Salva il risultato in `array2[i]`

### 4. Output
- Stampa entrambi gli array per mostrare il confronto

## Versione semplificata (senza validazione)

```c
#include <stdio.h>

int main() {
    int array1[20], array2[20];
    int i;
    
    // Lettura dei 20 numeri
    printf("Inserisci 20 numeri interi non negativi:\n");
    for (i = 0; i < 20; i++) {
        printf("Numero %d: ", i + 1);
        scanf("%d", &array1[i]);
    }
    
    // Calcolo del secondo array
    for (i = 0; i < 20; i++) {
        array2[i] = array1[i] - i;
    }
    
    // Stampa risultati
    printf("\nArray originale:\n");
    for (i = 0; i < 20; i++) {
        printf("%d ", array1[i]);
    }
    
    printf("\n\nArray con sottrazione posizione:\n");
    for (i = 0; i < 20; i++) {
        printf("%d ", array2[i]);
    }
    printf("\n");
    
    return 0;
}
```

## Versione con un solo ciclo (ottimizzata)

Se non serve mantenere `array1` dopo il calcolo, possiamo combinare lettura e calcolo:

```c
#include <stdio.h>

int main() {
    int array1[20], array2[20];
    int i, num;
    
    printf("Inserisci 20 numeri interi non negativi:\n");
    
    for (i = 0; i < 20; i++) {
        printf("Numero %d: ", i + 1);
        scanf("%d", &num);
        array1[i] = num;
        array2[i] = num - i;  // Calcolo immediato
    }
    
    // Stampa risultati
    printf("\nArray originale: ");
    for (i = 0; i < 20; i++) {
        printf("%d ", array1[i]);
    }
    
    printf("\nArray con sottrazione: ");
    for (i = 0; i < 20; i++) {
        printf("%d ", array2[i]);
    }
    printf("\n");
    
    return 0;
}
```

## Esempio di esecuzione

```
Inserisci 20 numeri interi non negativi:
Numero 1 (posizione 0): 10
Numero 2 (posizione 1): 15
Numero 3 (posizione 2): 20
Numero 4 (posizione 3): 25
Numero 5 (posizione 4): 30
Numero 6 (posizione 5): 35
Numero 7 (posizione 6): 40
Numero 8 (posizione 7): 45
Numero 9 (posizione 8): 50
Numero 10 (posizione 9): 55
Numero 11 (posizione 10): 60
Numero 12 (posizione 11): 65
Numero 13 (posizione 12): 70
Numero 14 (posizione 13): 75
Numero 15 (posizione 14): 80
Numero 16 (posizione 15): 85
Numero 17 (posizione 16): 90
Numero 18 (posizione 17): 95
Numero 19 (posizione 18): 100
Numero 20 (posizione 19): 105

--- Risultati ---
Array originale (array1):
array1[ 0] =  10
array1[ 1] =  15
array1[ 2] =  20
array1[ 3] =  25
array1[ 4] =  30
array1[ 5] =  35
array1[ 6] =  40
array1[ 7] =  45
array1[ 8] =  50
array1[ 9] =  55
array1[10] =  60
array1[11] =  65
array1[12] =  70
array1[13] =  75
array1[14] =  80
array1[15] =  85
array1[16] =  90
array1[17] =  95
array1[18] = 100
array1[19] = 105

Array con sottrazione posizione (array2):
array2[ 0] = array1[ 0] -  0 =  10
array2[ 1] = array1[ 1] -  1 =  14
array2[ 2] = array1[ 2] -  2 =  18
array2[ 3] = array1[ 3] -  3 =  22
array2[ 4] = array1[ 4] -  4 =  26
array2[ 5] = array1[ 5] -  5 =  30
array2[ 6] = array1[ 6] -  6 =  34
array2[ 7] = array1[ 7] -  7 =  38
array2[ 8] = array1[ 8] -  8 =  42
array2[ 9] = array1[ 9] -  9 =  46
array2[10] = array1[10] - 10 =  50
array2[11] = array1[11] - 11 =  54
array2[12] = array1[12] - 12 =  58
array2[13] = array1[13] - 13 =  62
array2[14] = array1[14] - 14 =  66
array2[15] = array1[15] - 15 =  70
array2[16] = array1[16] - 16 =  74
array2[17] = array1[17] - 17 =  78
array2[18] = array1[18] - 18 =  82
array2[19] = array1[19] - 19 =  86
```

## Esempio con numeri più piccoli

**Input:**
```
[5, 3, 8, 2, 10, 1, 7, 4, 9, 6, 12, 15, 3, 8, 11, 2, 6, 9, 13, 5]
```

**Output array2:**
```
[5, 2, 6, -1, 6, -4, 1, -3, 1, -3, 2, 4, -9, -5, -3, -13, -10, -8, -5, -14]
```

**Nota**: Alcuni valori risultano negativi quando `array1[i] < i`. Questo è corretto matematicamente, ma se servono solo valori non negativi, si può aggiungere un controllo.

## Versione con controllo valori negativi

Se vogliamo evitare valori negativi in `array2`:

```c
// Calcolo del secondo array con controllo
for (i = 0; i < 20; i++) {
    int risultato = array1[i] - i;
    if (risultato < 0) {
        array2[i] = 0;  // Oppure: array2[i] = -risultato; (valore assoluto)
    } else {
        array2[i] = risultato;
    }
}
```

## Note

- **Indici array**: Gli array in C partono da 0, quindi la prima posizione è 0
- **Valori negativi**: Se `array1[i] < i`, `array2[i]` sarà negativo (matematicamente corretto)
- **Efficienza**: Due cicli separati sono più chiari, ma si può ottimizzare combinando lettura e calcolo
- **Memoria**: Entrambi gli array vengono mantenuti in memoria per permettere la stampa di entrambi