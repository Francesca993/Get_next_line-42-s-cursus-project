# Get Next Line

**Leggere una linea da un file descriptor**

## 📌 Descrizione

**Get Next Line** è un progetto in C che implementa una funzione in grado di leggere una linea da un file descriptor. È un'ottima occasione per migliorare la gestione della memoria, comprendere meglio le variabili statiche e affinare le capacità di manipolazione di file in C.

## 🚀 Funzionalità

- Legge una linea per volta da un file descriptor.
- Restituisce `NULL` quando il file è stato completamente letto o in caso di errore.
- Utilizza `read`, `malloc` e `free` per la gestione della memoria.
- Funziona sia con file che con input standard (STDIN).

## 📜 Specifiche

- **Funzione principale:**
  ```c
  char *get_next_line(int fd);
  ```
- **File richiesti:**
  - `get_next_line.c`
  - `get_next_line_utils.c`
  - `get_next_line.h`
- **Compilazione:**
  ```sh
  cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c -o gnl
  ```
  (Dove `BUFFER_SIZE` può essere modificato per testare diverse configurazioni di lettura.)

## 🛠 Istruzioni di Progetto

- Il codice deve rispettare la **Norm**.
- Nessun **leak di memoria** è tollerato.
- Vietato l'uso di `lseek()` e di variabili globali.
- Testare il codice con **buffer size differenti** per verificarne la robustezza.

## 📁 Struttura della Repository
```
📂 get_next_line/
 ├── get_next_line.c
 ├── get_next_line.h
 ├── get_next_line_utils.c
 ├── Makefile
 ├── README.md
```

## 📌 Esempio di utilizzo

```c
#include <fcntl.h>
#include <stdio.h>
#include "get_next_line.h"

int main(void)
{
    int fd = open("test.txt", O_RDONLY);
    char *line;
    
    while ((line = get_next_line(fd)))
    {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## 🧪 Testing

Per testare il tuo codice:
```sh
make
./gnl < file_di_test.txt
```

## Votazione
![gradeScreenshot](gnl.png)

## 📜 Licenza

Progetto realizzato per scopi educativi nell'ambito del curriculum 42.
Sviluppato con ❤️ per migliorare la gestione della lettura di file in C. 😃

