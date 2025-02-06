# get_next_line

**get_next_line** est un projet de l'école 42 dont l'objectif est d'écrire une fonction capable de lire une ligne à la fois depuis un descripteur de fichier. Ce projet met en avant la gestion de la mémoire, des buffers et des lectures partielles.

## Sommaire
- [Introduction](#introduction)
- [Fonctionnalités](#fonctionnalités)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Structure du projet](#structure-du-projet)
- [Exemples](#exemples)
- [Auteur](#auteur)

## Introduction
Le projet **get_next_line** consiste à implémenter une fonction `get_next_line` qui permet de lire un fichier ligne par ligne, gérant des buffers de tailles variables et des lectures consécutives sur plusieurs descripteurs de fichiers.

## Fonctionnalités
- Lecture ligne par ligne depuis un descripteur de fichier.
- Support de plusieurs descripteurs de fichiers simultanément (bonus).
- Gestion efficace de la mémoire pour des lectures optimisées.

## Installation
Bien que le projet n'impose pas l'utilisation d'un `Makefile`, j'ai inclus un `Makefile` pour faciliter la compilation sous forme de bibliothèque.

1. Clonez le dépôt :
   ```bash
   git clone git@github.com:Kiores23/42-Project-get_next_line.git
   cd 42-Project-get_next_line
   cd get_next_line
   ```

2. Compilation standard :
   ```bash
   make
   ```

3. Compilation du bonus :
   ```bash
   make bonus
   ```

4. Nettoyage des fichiers objets :
   ```bash
   make clean
   ```

5. Nettoyage complet :
   ```bash
   make fclean
   ```

6. Recompilation :
   ```bash
   make re
   ```

## Utilisation
Pour utiliser **get_next_line** dans un projet C :

```c
#include "get_next_line.h"

int main(void) {
    int fd = open("fichier.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL) {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## Structure du projet
```
get_next_line/
├── includes
│   └── get_next_line.h
├── includes_bonus
│   └── get_next_line_bonus.h
├── Makefile
├── srcs
│   ├── get_next_line.c
│   └── get_next_line_utils.c
└── srcs_bonus
    ├── get_next_line_bonus.c
    └── get_next_line_utils_bonus.c
```

## Exemples
```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void) {
    int fd = open("example.txt", O_RDONLY);
    char *line;

    while ((line = get_next_line(fd)) != NULL) {
        printf("%s", line);
        free(line);
    }
    close(fd);
    return 0;
}
```

## Auteur
- **Nom :** Alexis Mery
- **Email :** amery@student.42nice.fr
- **GitHub :** [Kiores23](https://github.com/kiores23)

---

*Ce projet a été réalisé dans le cadre du cursus de l'école 42.*

