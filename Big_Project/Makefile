# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                            :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: Foxan         <foxan57@gmail.com>          +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2022/11/03 10:23:53 by Foxan             #+#    #+#              #
#    Updated: 2022/11/03 10:23:54 by Foxan            ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

#//= Colors =//#
BOLD			:= \033[1m
BLACK			:= \033[30;1m
RED				:= \033[31;1m
GREEN			:= \033[32;1m
YELLOW			:= \033[33;1m
BLUE			:= \033[34;1m
MAGENTA			:= \033[35;1m
CYAN			:= \033[36;1m
WHITE			:= \033[37;1m
RESET			:= \033[0m

#//= Variables =//#
CC				:= gcc  # compiler
NAME			:= name  # name of the output file
PROJECT_NAME	:= NAME  # name of the project for diplaying purpose

SRCS			:= ./src/dummy1.c \
					./src/dummy2.c \
					./src/dummy3.c  # add here each source file of your project
# there are alternatives to automate the
# listing of the source files, but adding
# each one by one everytime you create a
# new one is not really time consuming, and
# safer

INCLUDES		:= -I ./includes  # directory with your headers

LIBDUMMY		:= ./libs/libdummy # for each lib, add path in a specific variable
LIBS			:= $(LIBDUMMY)/libdummy.a # add libs .a path for each lib

FLAGS			:= -Wall -Wextra -Werror  # flags to use during the compilation
OBJS			:= ${SRCS:.c=.o}  # defining the rule for OBJS
SOMETHING		:= 0  # variable that will help us determine if the make did something
						# and display the right message

#//= Main compiling rules =//#

all: startall libdummy ${NAME} end # main rule of the makefile
	@if [ $(SOMETHING) = 1 ]; then printf "$(MAGENTA)Done !\n$(RESET)"; fi  # if something was done we display it
	@if [ $(SOMETHING) = 0 ]; then printf "$(MAGENTA)Nothing to do !\n$(RESET)"; fi  # if nothing was done we display it

${NAME}: start ${OBJS} endall  # main rule of the makefile
	@printf "$(BOLD)--------------------\n$(RESET)"
	@$(CC) -o $(NAME) $(OBJS) $(LIBS) $(INCLUDES)  # compiling the main

.c.o:  # rule to compile every SRCS files
	@${CC} ${FLAGS} -c $< -o ${<:.c=.o} ${INCLUDES} &&  printf "$(MAGENTA)$(PROJECT_NAME)$(RESET)$(BOLD) Compiling: $(notdir $<) \n$(RESET)"
	# compilation command to compile every c file in SRCS
	@$(eval SOMETHING = 1)  # changing the variable to get the right message at the end

#//= Libs compiling rules =//#
# for each lib you have, make a new rule to compile its makefile, if it is necessary
libdummy:
	@printf "$(MAGENTA)Making LIBDUMMY...\n$(RESET)" && $(MAKE) -C $(LIBDUMMY)
	@printf "$(BOLD)Done making $(MAGENTA)LIBDUMMY\n$(RESET)"
	@printf "$(BOLD)--------------------\n$(RESET)"

#//= Cleaning rules =//#

clean:  # cleaning rule
	@rm -f ${OBJS} && printf "$(GREEN)Cleaning $(PROJECT_NAME) OBJS...\n$(RESET)"
	# cleaning compiled SRCS files
	@$(MAKE) -C $(LIBDUMMY) clean && printf "$(RED)Cleaning LIBDUMMY...\n$(RESET)"
	# add a call to clean rule of each library you compiled
	@printf "$(YELLOW)Finished cleaning !\n$(RESET)"
	@printf "$(YELLOW)--------------------\n$(RESET)"

fclean: clean  # cleaning rule
	@rm -f ${NAME} && printf "$(GREEN)Cleaning $(PROJECT_NAME) $(NAME)...\n$(RESET)"
	# cleaning output file
	@$(MAKE) -C $(LIBDUMMY) fclean && printf "$(RED)Cleaning LIBDUMMY...\n$(RESET)"
	# add a call to fclean rule of each library you compiled
	@printf "$(YELLOW)Finished cleaning everything !\n$(RESET)"
	@printf "$(YELLOW)--------------------\n$(RESET)"

#//= Beautification rules =//#

startall:
	@printf "$(BOLD)--------------------\n$(RESET)"
	@printf "$(MAGENTA)Starting making everything\n$(RESET)"
	@printf "$(BOLD)--------------------\n$(RESET)"

start:
	@printf "$(MAGENTA)Making $(PROJECT_NAME)...\n$(RESET)"

end:
	@printf "$(BOLD)Done making $(MAGENTA)$(PROJECT_NAME)\n$(RESET)"
	@printf "$(BOLD)--------------------\n$(RESET)"

endall:
	@printf "$(BOLD)Done compiling $(MAGENTA)e$(CYAN)v$(GREEN)e$(YELLOW)r$(BLUE)y$(RED)t$(MAGENTA)h$(CYAN)i$(GREEN)n$(YELLOW)g !\n$(RESET)"
	@printf "$(BOLD)--------------------\n$(RESET)"

re:	fclean all  # re command

.PHONY: all clean fclean re start end startall endall libdummy
