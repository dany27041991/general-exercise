# Esercizio 3: Verifica se un numero è primo

## Traccia
Scrivere un programma in C che, dopo aver acquisito un numero intero come input, stabilisca se è primo oppure no.
(Si ricordi che in C è possibile calcolare il resto r della divisione intera tra due numeri a e b come r=a%b).

## Spiegazione

Un numero primo è un numero naturale maggiore di 1 che è divisibile solo per 1 e per se stesso.

**Algoritmo:**
1. Se il numero è minore di 2, non è primo
2. Se il numero è 2, è primo
3. Se il numero è pari e diverso da 2, non è primo
4. Per numeri dispari maggiori di 2, controlliamo se è divisibile per qualche numero compreso tra 3 e la radice quadrata del numero
5. Se troviamo un divisore, il numero non è primo
6. Se non troviamo divisori, il numero è primo

## Soluzione

```c
#include <stdio.h>
#include <math.h>

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
    int numero;
    
    printf("Inserisci un numero intero: ");
    scanf("%d", &numero);
    
    if (isPrimo(numero)) {
        printf("%d è un numero primo.\n", numero);
    } else {
        printf("%d NON è un numero primo.\n", numero);
    }
    
    return 0;
}
```

## Spiegazione del codice

1. **Funzione `isPrimo(int n)`**: 
   - Restituisce 1 se il numero è primo, 0 altrimenti
   - Gestisce i casi base: numeri < 2, il numero 2, numeri pari
   - Per numeri dispari, controlla divisori solo fino a √n (ottimizzazione)
   - Usa `n % i == 0` per verificare se `i` divide `n`

2. **Funzione `main()`**:
   - Acquisisce il numero dall'utente
   - Chiama `isPrimo()` per verificare
   - Stampa il risultato

## Esempio di esecuzione

```
Inserisci un numero intero: 17
17 è un numero primo.

Inserisci un numero intero: 15
15 NON è un numero primo.
```

## Note

- L'operatore `%` restituisce il resto della divisione intera
- `sqrt(n)` richiede `#include <math.h>`
- L'ottimizzazione con `sqrt(n)` riduce il numero di controlli necessari