# Esercizio 7: Contare numeri maggiori di 5

## Traccia
Scrivere un programma in C che, dopo aver chiesto per 20 volte all'utente di inserire un numero intero compreso tra 0 e 9, riporti quante volte è stato inserito un numero maggiore di 5.

## Spiegazione

Il programma deve:
1. Chiedere all'utente di inserire un numero 20 volte
2. Ogni numero deve essere compreso tra 0 e 9 (inclusi)
3. Contare quanti di questi numeri sono maggiori di 5 (cioè 6, 7, 8, 9)
4. Stampare il risultato del conteggio

**Nota**: I numeri maggiori di 5 sono 6, 7, 8, 9. Il numero 5 non viene contato perché la condizione è `> 5` (maggiore, non maggiore o uguale).

## Soluzione

```c
#include <stdio.h>

int main() {
    int num;           // Numero inserito dall'utente
    int contatore = 0; // Contatore per numeri > 5
    int i;             // Variabile per il ciclo
    
    printf("Inserisci 20 numeri interi compresi tra 0 e 9:\n");
    
    // Ciclo per 20 iterazioni
    for (i = 0; i < 20; i++) {
        do {
            printf("Numero %d: ", i + 1);
            scanf("%d", &num);
            
            // Verifica che il numero sia tra 0 e 9
            if (num < 0 || num > 9) {
                printf("Errore! Il numero deve essere compreso tra 0 e 9.\n");
            }
        } while (num < 0 || num > 9);  // Ripete finché non è valido
        
        // Verifica se il numero è maggiore di 5
        if (num > 5) {
            contatore = contatore + 1;  // oppure: contatore++;
        }
    }
    
    // Stampa il risultato
    printf("\nSono stati inseriti %d numeri maggiori di 5.\n", contatore);
    
    return 0;
}
```

## Spiegazione del codice

### 1. Dichiarazione variabili
```c
int num;           // Numero inserito dall'utente
int contatore = 0; // Contatore per numeri > 5
int i;             // Variabile per il ciclo
```
- `num`: memorizza il numero inserito in ogni iterazione
- `contatore`: conta quanti numeri sono maggiori di 5 (inizializzato a 0)
- `i`: variabile contatore per il ciclo `for`

### 2. Ciclo principale
```c
for (i = 0; i < 20; i++) {
    do {
        printf("Numero %d: ", i + 1);
        scanf("%d", &num);
        
        // Verifica che il numero sia tra 0 e 9
        if (num < 0 || num > 9) {
            printf("Errore! Il numero deve essere compreso tra 0 e 9.\n");
        }
    } while (num < 0 || num > 9);  // Ripete finché non è valido
    
    if (num > 5) {
        contatore = contatore + 1;
    }
}
```
- Il ciclo viene eseguito 20 volte (da `i = 0` a `i = 19`)
- Ad ogni iterazione:
  - Usa un ciclo `do-while` per validare l'input
  - Chiede all'utente di inserire un numero
  - Legge il numero con `scanf()`
  - Verifica che il numero sia compreso tra 0 e 9 (inclusi)
  - Se non valido, mostra un messaggio di errore e richiede di nuovo
  - Se `num > 5`, incrementa il contatore

### 3. Output
```c
printf("\nSono stati inseriti %d numeri maggiori di 5.\n", contatore);
```
- Stampa il risultato finale

## Versione semplificata (senza validazione)

Se vogliamo una versione più semplice che non verifica l'input (non consigliata, ma funziona se l'utente inserisce sempre numeri corretti):

```c
#include <stdio.h>

int main() {
    int num;
    int contatore = 0;
    int i;
    
    printf("Inserisci 20 numeri interi compresi tra 0 e 9:\n");
    
    for (i = 0; i < 20; i++) {
        do {
            printf("Numero %d: ", i + 1);
            scanf("%d", &num);
            
            // Verifica che il numero sia tra 0 e 9
            if (num < 0 || num > 9) {
                printf("Errore! Il numero deve essere compreso tra 0 e 9.\n");
            }
        } while (num < 0 || num > 9);  // Ripete finché non è valido
        
        // Verifica se il numero è maggiore di 5
        if (num > 5) {
            contatore++;
        }
    }
    
    printf("\nSono stati inseriti %d numeri maggiori di 5.\n", contatore);
    
    return 0;
}
```

**Spiegazione della validazione:**
- Usa un ciclo `do-while` per richiedere l'input finché non è valido
- Controlla che `num >= 0` e `num <= 9`
- Se non valido, mostra un messaggio di errore e richiede di nuovo

## Esempio di esecuzione

### Versione base

```
Inserisci 20 numeri interi compresi tra 0 e 9:
Numero 1: 3
Numero 2: 7
Numero 3: 2
Numero 4: 9
Numero 5: 1
Numero 6: 6
Numero 7: 4
Numero 8: 8
Numero 9: 0
Numero 10: 5
Numero 11: 7
Numero 12: 3
Numero 13: 9
Numero 14: 2
Numero 15: 6
Numero 16: 1
Numero 17: 8
Numero 18: 4
Numero 19: 7
Numero 20: 0

Sono stati inseriti 9 numeri maggiori di 5.
```

**Analisi dell'esempio:**
- Numeri inseriti: 3, 7, 2, 9, 1, 6, 4, 8, 0, 5, 7, 3, 9, 2, 6, 1, 8, 4, 7, 0
- Numeri > 5: 7, 9, 6, 8, 7, 9, 6, 8, 7
- Totale: 9 numeri

### Versione con validazione

```
Inserisci 20 numeri interi compresi tra 0 e 9:
Numero 1: 3
Numero 2: 12
Errore! Il numero deve essere compreso tra 0 e 9.
Numero 2: 7
Numero 3: 2
...
```

## Versione alternativa con array

Se volessimo memorizzare tutti i numeri (non necessario per questo esercizio):

```c
#include <stdio.h>

int main() {
    int numeri[20];    // Array per memorizzare tutti i numeri
    int contatore = 0;
    int i;
    
    printf("Inserisci 20 numeri interi compresi tra 0 e 9:\n");
    
    // Lettura dei numeri
    for (i = 0; i < 20; i++) {
        do {
            printf("Numero %d: ", i + 1);
            scanf("%d", &numeri[i]);
            
            // Verifica che il numero sia tra 0 e 9
            if (numeri[i] < 0 || numeri[i] > 9) {
                printf("Errore! Il numero deve essere compreso tra 0 e 9.\n");
            }
        } while (numeri[i] < 0 || numeri[i] > 9);  // Ripete finché non è valido
    }
    
    // Conteggio numeri > 5
    for (i = 0; i < 20; i++) {
        if (numeri[i] > 5) {
            contatore++;
        }
    }
    
    printf("\nSono stati inseriti %d numeri maggiori di 5.\n", contatore);
    
    return 0;
}
```

## Note

- **Condizione**: `num > 5` significa che vengono contati solo 6, 7, 8, 9
- **Efficienza**: Non è necessario memorizzare tutti i numeri, basta contare
- **Validazione**: Essenziale per rispettare la traccia che richiede numeri tra 0 e 9
- **Incremento contatore**: `contatore++` è equivalente a `contatore = contatore + 1`