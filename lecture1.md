
# Lecture 1: Introduction to the command line

**Concept I: Programming with Data**

* Introduction to the command line
* Command input and output
* Functional programming
* Object Oriented programming
* Database programming
* Web programming

Roughly, a computer is made out to components: datas and computing power, as
illustrated in the figure below.

FIGURE: DATA AND COMPUTING POWER

## Data files and program files

One accesses

* the computing power of the computer by launching programs
* the data stored on the computer by opening files and reading their content

In Unix, both programs and data are stored in regular files. Files can be

* read (r)
* written (w)
* executed (x)

r (read), w (write), x (execute) are the file **permissions**. They depend on
both the file and the user. Not all users have the same access rigths (i.e. not
every user is allowed to execute or read a certain file; file access is
controlled by the Unix permission system) to a given file (we will come back to
that later in more details).

Of course, the "execute" (x) permission makes sense only if the file is a
program. There are two main types of program files:

* **binary files:** the intructions to be carried out by the computer are
written in the form of 0 and 1, that is, in **machine language,** which the
computer can understand directly

* **text files:** the instructions to be carried out by the computer are written
in a simplified form of the english language, called a **script** or a
**scripting language**; the computer does not understand these instructions
directly and needs a special program, called an **interpreter**, to translate
them so that it can execute them.


In this course, we will study three interpreters using three different scripting
languages: the **Bash interpreter**, the **Python interpreter**, and the **R
interpreter**. Each interpreter has its strenghts and weaknesses:

* Bash is very good at manipulating files stored on Unix machines
* R is very good at statiscal analysis
* Python is a very good at performing general programmation tasks, including
file manipulations and data analysis

Interpreters are also called **shells**, although the word "shell" may be
reserved to interpreters that are especially designed to interact with the
computer filesystem (such as bash, ash, bsh, csh, kzh, zsh, etc.).

Python is the prefered scripting language for data analysis in the industry,
while R is prevalent in the academic world.

Interpreters can be used in two ways:

* **batch mode:** one writes a script in a certain scripting language (such as
Bash, python, or R) and feeds the interprester with the file containing the
script; then the instructions contained in the file are carried out, all at
once, by the interpreter.

* **interactive mode:** one launches the interpreter (which is itself a program)
without any instruction file; then the interpreter waits for the user to enter
instructions interactively, one at a time, in a **terminal**.

## Filesystems, Windowing Systems, and Terminals

Usually, program launching and file access is done through a **Graphical User
Interface** (**GUI** for short), called a a **Windowing System**). The GUI
presents the user with windows representing folders, which themselves contain a
certain number of subfolders and files. This is a graphical representation of
the **filesystem** that organizes the data stored in the computer.

Mathematically, a filestem is represented by a **rooted tree**, which is a
special type of ** network** or **graph**. Here are the corresponding formal
mathematical definitions:

> **Definition:** A **network** (or **graph**) $(V,E)$ is the data of set $V$ of
**nodes** (or **vertices**) and a set $E\subset V\times V$ of **links** (or
**edges**).

>**Definition:** Recall that the **cartesian product** of two sets $A$ and $B$
is the set $A\times B$ of all **ordered pairs** $(a,b)$, where $a\in A$ and
$b\in B$.

Graphically, one represents a node $v\in V$ as point and a link $(v_1,v_2)\in E$
as an arrow from the node $v_1$ to the node $v_2$, as in the following figure:

FIGURE: A graph


>**Definition:** A **path** in a network $(V,E)$ is a sequence of nodes
$v_1,v_2,\dots,v_n$ in $V$ having links between them (all in the same
direction).

>**Definition:** A **cycle** is a path whose first node coincides with the last
node.

>**Definition:** An **initial node** is a node with no other node with a link to
it.

>**Definition:** A **terminal node** or **leaf** is a node with no link from it.

>**Definition:** A **roteed tree** is a network

>* with no cycles
>* with a single initial node, called the root
>* with all links pointing away from the root


FIGURE: examples of trees

The root of a filesystem is the folder (or directory) representing the
**harddrive**, which oftentimes is represented by the icon of a harddrive by the
Windowing System. The nodes of a filesystem are all the files and directories
that you can access from the harddrive icon (i.e., from the filesystem root).
The terminal nodes are the actual files stored on the computer. The other nodes
(the ones that are not the root nor terminal nodes) are the folders or
directories. There is a link between from folder $A$ and folder $B$ if folder
$B$ is a subfolder of folder $A$.


Here is a picture to better illustrate the situation:

FIGURE: a filesystem as a tree

In Unix, directories are special types of files (they are files containing the
list of all the subdirectories and files they contain). There are two main ways
to access the filesystem:

* Through the Windowing System, as you are used to
* Through a terminal (also called the **command line**), which you may be less
familiar with

Windowing Systems are easy to use, but they are not powerful. On the other hand,
terminals are harder to get accustomed to but are extremely powerful, especially
for repeated tasks involving a large amount of data.

Our first step in this class will be to learn how to use the terminal and the
command line, which is nothing but the Bash interpreter, run in interactive
mode.

It is a good place now to watch the following video to get you started with the
terminal and to get a more concrete feel about what we have been talking about:

[Introduction to the terminal and the command line](http://openclassroom.stanfor
d.edu/MainFolder/VideoPage.php?course=PracticalUnix&video=intro-shell&speed=100)

The main tasks the Windowing System allow you to do with the filesystem are the
following:

1. naviguating the filesystem (i.e. going from one folder to the another one)
1. modifying the filesystem (i.e. creating, deleting, copying, moving files
around)
1. accessing file content and launching programs
1. finding files and programs

We will now review how to perform these tasks with the terminal.

## Navigating the filesystem

**Relevant commands:**

* **ls**: list directory
* **cd**: change directory
* **pwd**: print working directory

The location of a file or a directory in the filesystem is given by the path
from the root (i.e. the hardrive folder) to this file or directory. The Unix
convention is to separate the folder names (i.e. the nodes names) by a "/" and
to omit the name of the root folder. For instance the path /Users/Benoit/Stat133
indicates the location of my Stat133 folder, and
/Users/Benoit/Stat133/Stat133.html indicates the location on my filesystem of
the webpage for the class.

When you lauch a terminal, the terminal always operates from a given directory
(called the **working directory**). This is very similar to what happens when
you have a window opened in a Windowing System: the window represents a certain
directory and if you create a file, it will be saved in this directory for
example.

The **pw** (print directory) command will give you the path (i.e. location) of
your current working directory:



    %%bash
    pwd

    /accounts/gen/guest/bdherin/Dropbox/Public/Stat133/NoteBooks


The **ls** command will list the content of your current directory:


    %%bash
    ls

    CH1.ipynb
    Introduction.ipynb
    MyTest
    drawing.png
    drawing.svg
    nb-slideshow-template-master
    notebook-slideshow-example.ipynb
    try.jpg


The **cd** command will allow you to change your current directory and to
navigate the file system. You need to specify the location (i.e. the path) of
the directory you want to go to. Here you have to options:

* give the **absolute path**
* give the **relative path**

to the cd command of the directory you want to change your working directory to.
The absolute path is what we describe before, that is, the path in the
filesystem tree from the root to the directory you want to go to. The relative
path is the path to this director *from your current directory*. To form the
relative path of a directory, you usually need to use to spcial *symbolic*
paths:

* a single dot "." is a "symbolic name" for the path to your current working
directory
* two dots ".." stands for the directory that is just above your current working
directory

A relative path is thus of the following form:

* ../leon/freak
* ./strange_animals/raccoon

The first relative path above indicates the location of the directory named
""freak" which is in the directory "leon" just above my current working
directory. While the second relative path indicates the location of the
directory "raccoon" which is in the directory "strange_animals" contained in my
current working directory.

For instance, the command "ls .." will list the content of the directory that
contains your working directory


    %%bash
    ls ..

    Homeworks
    LectureTextBooks
    NoteBooks
    PythonBootCamp
    Stat133.html
    Stat133Fa12
    Stat133_files


while the command "ls ." will list the content of your working directory
(achieving thus the same effect as "ls").


    %%bash
    ls .

    CH1.ipynb
    Introduction.ipynb
    MyTest
    drawing.png
    drawing.svg
    nb-slideshow-template-master
    notebook-slideshow-example.ipynb
    try.jpg


## Modifying the filesytem

**Relevant commands:**

* **touch**: create a file
* **mkdir**: create (make) a directory
* **rm**: delete (remove) a directory or a file
* **cp**: copy a directory or a file
* **mv**: move directory or a file
* **chmod**: change (mode) the permissions of a file or a directory

These commands, except maybe for the last one, are straightforward to understand
and use. You should already be familiar with most of them if you watched the
previous video. You'll find more details in Chapter 10 of the textbook:

[Chapter 10. Working with files.](http://proquest.safaribooksonline.com/book
/operating-systems-and-server-administration/unix/0596005954/working-with-files
/shellsrptg-chp-10)

To understand the persmission system and how to operate with it, it's now a good
place to watch the following video:

[Setting and checking file permissions](http://openclassroom.stanford.edu/MainFo
lder/VideoPage.php?course=PracticalUnix&video=permissions&speed=100)

**To obtain detailed, but often cryptic information on most Unix command, you
can always type "man command_name" in the the terminal.**

## Finding files

**Relevant commands:**

* **find**
* **locate**

The commands "find" and "locate" allow you to look up files in the filesystem.

The "find" comand requires a starting node (i.e. directory) in the filesystem to
start the search from. It can look up files by name and permissions.

The "locate" command doesn't need a starting directory to begin with; it will
search the entire filesystem very rapidly for a file name containing a certain
string of characters.

These commands are very handy and powerful. Now it's a good time to watch how to
make use of them:


[Finding files on your computer with find and locate](http://openclassroom.stanf
ord.edu/MainFolder/VideoPage.php?course=PracticalUnix&video=find&speed=100)


## Accessing file content

**Relevant commands:**

* **cat**: (concatenate) display the content of a file
* **head**: display the first lines of a file
* **tail**: display the last lines of a file
* **vi**: text editor

The "vi" editor allows you to edit files. It is a very powerful editor, which I
strongly encourage you to learn. The learning curve is quite steep, so be
prepared. The following video and interative tutorial will help you greatly:

[Introduction to Unix editors](http://openclassroom.stanford.edu/MainFolder/Vide
oPage.php?course=PracticalUnix&video=intro-text-editors&speed=100)

[Interactive vi tutorial](http://www.openvim.com/tutorial.html)

We will learn a bit more about cat, head, and tail in a class demo, where we
will buil a simple chat system for the class.
