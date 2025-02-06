# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: amery <marvin@42.fr>                       +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2024/02/06                                #+#    #+#              #
#    Updated: 2024/02/06                                ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Nom de la librairie
NAME = get_next_line.a

# Compilateur et options
CC = gcc
CFLAGS = -Wall -Wextra -Werror

# Commandes pour l'archivage et le nettoyage
AR = ar rcs
RM = rm -f

# Dossiers des sources et des includes
INCLUDES = includes/
INCLUDES_B = includes_bonus/
SRCS_DIR = srcs/
SRCS_DIR_B = srcs_bonus/
OBJS_DIR = objs/

# Fichiers sources (standard et bonus)
SRCS = $(SRCS_DIR)get_next_line.c $(SRCS_DIR)get_next_line_utils.c
SRCS_B = $(SRCS_DIR_B)get_next_line_bonus.c $(SRCS_DIR_B)get_next_line_utils_bonus.c

# Fichiers objets générés
OBJS = $(patsubst $(SRCS_DIR)%.c,$(OBJS_DIR)%.o,$(SRCS))
OBJS_B = $(patsubst $(SRCS_DIR_B)%.c,$(OBJS_DIR)%.o,$(SRCS_B))

# Cible principale
$(NAME): $(OBJS)
	$(AR) $@ $^

# Crée le dossier des objets si nécessaire
$(OBJS_DIR):
	mkdir -p $(OBJS_DIR)

# Compilation des fichiers normaux
$(OBJS_DIR)%.o: $(SRCS_DIR)%.c | $(OBJS_DIR)
	$(CC) $(CFLAGS) -I$(INCLUDES) -c $< -o $@

# Compilation des fichiers bonus
$(OBJS_DIR)%.o: $(SRCS_DIR_B)%.c | $(OBJS_DIR)
	$(CC) $(CFLAGS) -I$(INCLUDES_B) -c $< -o $@

# Cible pour le bonus
bonus: $(OBJS_B)
	$(AR) $(NAME) $^

# Cible pour compiler tout le projet
all: $(NAME)

# Nettoyage des fichiers objets
clean:
	$(RM) $(OBJS) $(OBJS_B)
	$(RM) -r $(OBJS_DIR)

# Nettoyage complet (objets + librairie)
fclean: clean
	$(RM) $(NAME)

# Recompilation complète
re: fclean all

# Déclaration des cibles phony
.PHONY: all clean fclean re bonus
