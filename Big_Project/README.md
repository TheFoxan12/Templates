# Big Project template

Template made to do big projects with lots of src files, headers and some libs

## Organisation of the project files 
- put your .c source files into /src
- put your .h header files into /include
- put your static libraries into /lib
- just copy paste the libraries directories into libs
- modify the Makefile to adapt it to your project
- you can delete .placeholder files

## The Makefile
- modify the name of the output
- modify the name of the project for displaying
- list every .c source file into SRCS
- add includes paths into INCLUDES with -I before each one
- create a new LIB(NAME) variable for each library you're using
- add its .a path into LIBS
- you can modify the compilation flags with FLAGS
> **all** rule make the project </br>
> **clean** rule clean every object files of the project </br>
> **fclean** rule clean then clean the output file </br>
> **re** rule clean and remake the project </br>

- add a new rule for each library you get
> just copy paste the **libdummy** rule and modify the variables and name in it
- add a call to the **clean** rule and the **fclean** rule of each makefile of the libraries you added into clean and fclean rules
- add the name of the new rule in the .PHONY

> **start**, **starall**, **end** and **endall** are just here to beautify displaying </br>
> **@** at the beginning of every line is to tell the makefile not to display commands because we do clean displaying with printf

If you have any question or improvement ideas don't hesitate to ask me here or at my discord **Foxan#0001** </br>