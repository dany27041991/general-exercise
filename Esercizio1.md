# Esercizio 1: Verifica numeri primi in un array

## Traccia
Scrivere un programma in C che:
* acquisisce 20 numeri interi in input e li salva in un array;
* richiamando la funzione precedente verifica se ciascun numero dell'array è primo e lo scrive in uscita.

## Spiegazione

Questo esercizio richiede di:
1. Creare un array di 20 elementi
2. Acquisire 20 numeri interi dall'utente e memorizzarli nell'array
3. Per ogni numero nell'array, verificare se è primo usando la funzione `isPrimo()` dell'Esercizio 3
4. Stampare in output i numeri primi trovati

## Soluzione

```c
#include <stdio.h>
#include <math.h>

// Funzione per verificare se un numero è primo (dall'Esercizio 3)
int isPrimo(int n) {
    int i;
    
    // I numeri minori di 2 non sono primi
    if (n < 2) {
        return 0; // false
    }
    
    // 2 è primo
    if (n == 2) {
        return 1; // true
    }
    
    // I numeri pari maggiori di 2 non sono primi
    if (n % 2 == 0) {
        return 0; // false
    }
    
    // Controlla se n è divisibile per qualche numero dispari
    // da 3 fino alla radice quadrata di n
    for (i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0) {
            return 0; // false: trovato un divisore
        }
    }
    
    return 1; // true: è primo
}

int main() {
    int array[20];  // Array per memorizzare 20 numeri interi
    int i;
    
    // Acquisizione dei 20 numeri
    printf("Inserisci 20 numeri interi:\n");
    for (i = 0; i < 20; i++) {
        printf("Numero %d: ", i + 1);
        scanf("%d", &array[i]);
    }
    
    // Verifica e stampa dei numeri primi
    printf("\nNumeri primi trovati nell'array:\n");
    for (i = 0; i < 20; i++) {
        if (isPrimo(array[i])) {
            printf("%d (posizione %d)\n", array[i], i);
        }
    }
    
    return 0;
}
```

## Spiegazione del codice

1. **Dichiarazione dell'array**: `int array[20]` crea un array di 20 interi

2. **Acquisizione dati**:
   - Ciclo `for` da 0 a 19 per leggere 20 numeri
   - Ogni numero viene salvato in `array[i]` usando `scanf()`

3. **Verifica numeri primi**:
   - Secondo ciclo `for` per scorrere tutti gli elementi
   - Per ogni elemento, chiama `isPrimo(array[i])`
   - Se la funzione restituisce 1 (vero), stampa il numero e la sua posizione

4. **Funzione `isPrimo()`**: 
   - Riutilizzata dall'Esercizio 3
   - Verifica se un numero è primo usando l'algoritmo ottimizzato

## Esempio di esecuzione

```
Inserisci 20 numeri interi:
Numero 1: 2
Numero 2: 3
Numero 3: 4
Numero 4: 5
Numero 5: 6
Numero 6: 7
Numero 7: 8
Numero 8: 9
Numero 9: 10
Numero 10: 11
Numero 11: 12
Numero 12: 13
Numero 13: 14
Numero 14: 15
Numero 15: 16
Numero 16: 17
Numero 17: 18
Numero 18: 19
Numero 19: 20
Numero 20: 21

Numeri primi trovati nell'array:
2 (posizione 0)
3 (posizione 1)
5 (posizione 3)
7 (posizione 5)
11 (posizione 9)
13 (posizione 11)
17 (posizione 15)
19 (posizione 17)
```

## Note

- Gli array in C sono indicizzati da 0 a n-1
- La funzione `isPrimo()` può essere riutilizzata in altri programmi
- Il programma stampa sia il numero primo che la sua posizione nell'array