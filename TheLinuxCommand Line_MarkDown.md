# The Linux Command Line -- (2nd Edition)
Early 1980s, **Unix**.
In 1991, **Linus Torvalds** wrote the first version of the Linux kernel.
Earlier, **Richard Stallman** began the GNU Project to create a free Unix-like operating system, GNU C Compiler (gcc), and created the GNU General Public License (GPL).
>**GUI** Graphical User Interface.
>**CLI** Command Line Interface.

---
---

## CONTENTS
- [The Linux Command Line -- (2nd Edition)](#the-linux-command-line----2nd-edition)
  - [CONTENTS](#contents)
  - [PART I: LEARNING THE SHELL](#part-i-learning-the-shell)
    - [Chapter 1: What Is the Shell?](#chapter-1-what-is-the-shell)
    - [Chapter 2: Navigation](#chapter-2-navigation)
    - [Chapter 3: Exploring the System](#chapter-3-exploring-the-system)
    - [Chapter 4: Manipulating Files and Directories](#chapter-4-manipulating-files-and-directories)
    - [Chapter 5: Working with Commands](#chapter-5-working-with-commands)
    - [Chapter 6: Redirection](#chapter-6-redirection)
    - [Chapter 7: Seeing the World as the Shell Sees It](#chapter-7-seeing-the-world-as-the-shell-sees-it)
    - [Chapter 8: Advanced Keyboard Tricks](#chapter-8-advanced-keyboard-tricks)
    - [Chapter 9: Permissions](#chapter-9-permissions)
    - [Chapter 10: Processes](#chapter-10-processes)
  - [Quotes](#quotes)
  - [Emphasis](#emphasis)
  - [Horizontal Rule](#horizontal-rule)
  - [Lists](#lists)
  - [Links](#links)
  - [Images](#images)
  - [Code](#code)
  - [Tables](#tables)
  - [Custom HTML](#custom-html)
  - [Custom CSS](#custom-css)
  - [Additional Resources](#additional-resources)

---
---

## PART I: LEARNING THE SHELL

### Chapter 1: What Is the Shell?

The **shell** is a program that takes keyboard commands and passes them to the operating system to carry out. Almost all Linux distributions supply a shell program from the GNU Project called **bash**. The name is an acronym for **b**ourne-**a**gain **sh**ell, a reference to the fact that bash is an enhanced replacement for **sh**a, the original Unix shell program written by Steve Bourne.

<!-- #### 1. Terminal Emulators -->

**1. Terminal Emulators**
When using a **graphical user interface (GUI)**, we need another program called a **terminal emulator** to interact with the shell.

**2. Making Your First Keystrokes**
Launch the terminal emulator. It will appears like this:
```
 [me@linuxbox ~]$
```
This is called a **shell prompt**, and it will appear whenever the shell is ready to accept input. While it might vary in appearance somewhat depending on the distribution, it will typically include your __*username@machinename*__, followed by the current working directory (more about that in a little bit) and a dollar sign.
If the last character of the prompt is a **hash mark (#)** rather than a dollar sign, the terminal session has superuser privileges. This means either we are logged in as the root user or we selected a terminal emulator that provides superuser (administrative) privileges.

>**Command History:** press the **up arrow**, we will see that the previous command entered, remember the last 1,000 commands by default.

>**Cursor Movement:** use the **left and right arrows** to move the cursor anywhere on the command line.

**3. Try Some Simple Commands**
`data` to display the current time and date.
```
(base) ➜  ~ date
Mon Jul 24 18:41:59 PDT 2023
```
`cal`to display a calendar of the current month.
```
(base) ➜  ~ cal
     July 2023        
Su Mo Tu We Th Fr Sa  
                   1  
 2  3  4  5  6  7  8  
 9 10 11 12 13 14 15  
16 17 18 19 20 21 22  
23 24 25 26 27 28 29  
30 31 
```
`df` to display the current space on our disk drives.
```
(base) ➜  ~ df
Filesystem     512-blocks       Used Available Capacity iused      ifree %iused  Mounted on
/dev/disk3s1s1 1942700360   61761392 488553984    12%  536643 2442769920    0%   /
devfs                 404        404         0   100%     700          0  100%   /dev
/dev/disk3s6   1942700360   29360232 488553984     6%      14 2442769920    0%   /System/Volumes/VM
/dev/disk3s2   1942700360   20050624 488553984     4%    1302 2442769920    0%   /System/Volumes/Preboot
/dev/disk3s4   1942700360    1443536 488553984     1%     285 2442769920    0%   /System/Volumes/Update
/dev/disk1s2      1024000      12328    977992     2%       1    4889960    0%   /System/Volumes/xarts
/dev/disk1s1      1024000      15016    977992     2%      29    4889960    0%   /System/Volumes/iSCPreboot
/dev/disk1s3      1024000       8944    977992     1%      92    4889960    0%   /System/Volumes/Hardware
/dev/disk3s5   1942700360 1337854488 488553984    74% 3471544 2442769920    0%   /System/Volumes/Data
map auto_home           0          0         0   100%       0          0  100%   /System/Volumes/Data/home
/dev/disk2s1     10485672    3324576   7119888    32%      58   35599440    0%   /System/Volumes/Update/SFR/mnt1
/dev/disk3s1   1942700360   61761392 488553984    12%  536672 2442769920    0%   /System/Volumes/Update/mnt1
```
`free` to display the amount of free memory. It doesn't work in macOS terminal.


**4. Ending a Terminal Session**
`exit` or pressing the **CTRL-D** to close the terminal emulator.

---

### Chapter 2: Navigation
`pwd` Print name of current working directory
`cd`  Change directory
`ls`  List directory contents

**1. Understanding the File System Tree**
Unix-like operating system such as Linux organizes its files in what is called a **hierarchical directory structure**. This means they are organized in a tree-like pattern of directories (sometimes called folders in other systems), which may contain files and other directories. The first directory in the file system is called the **root directory**. The root directory contains files and subdirectories, which contain more files and subdirectories, and so on.

Note that unlike Windows, which has a separate file system tree for each storage device, **Unix-like systems such as Linux always have a single file system tree**, regardless of how many drives or storage devices are attached to the computer. Storage devices are attached (or more correctly, mounted) at various points on the tree according to the whims of the system administrator, the person (or people) responsible for the maintenance of the system.

**2. The Current Working Directory**
Imagine that the file system is a maze shaped like an upside-down tree and we are able to stand in the middle of it. At any given time, we are inside a single directory, and we can see the files contained in the directory and the pathway to the directory above us (called the *parent directory*) and any subdirectories below us. The directory we are standing in is called the **current working directory**. To display the current working directory, we use the **`pwd`** (print working directory) command.
```
(base) ➜  ~ pwd
/Users/runzhezhang
```
When we first log in to our system (or start a terminal emulator session), our current working directory is set to our **home directory**. Each user account is given its own home directory, and it is the only place a regular user is allowed to write files.

**3. Listing the Contents of a Directory**
To list the files and directories in the current working directory, we use the **`ls`** command.
```
(base) ➜  ~ ls
Applications              Library                   Public
Desktop                   Movies                    anaconda3
Documents                 Music                     apptool
Downloads                 Pictures
```

**4. Changing the Current Working Directory**
To change our working directory (where we are standing in the tree-shaped maze), we use the **`cd`** command. To do this, type **`cd`** followed by the pathname of the desired working directory. A pathname is the route we take along the branches of the tree to get to the directory we want. We can specify pathnames in one of two different ways: as **absolute pathnames** or as **relative pathnames**.

* **_Absolute Pathnames_**
An absolute pathname begins with the root directory (represented by the leading slash in the pathname) and follows the tree branch by branch until the path to the desired directory or file is completed, such as `/usr/bin`
* **_Relative Pathnames_**
A relative pathname starts from the working directory. The **`.`** notation refers to **the working directory**, and the **`..`** notation refers to **the working directory’s parent directory**.
`cd ..` go back to parent directory
`cd ./bin` open bin file, same to `cd bin`
In general, if we do not specify a pathname to something, the working directory will be assumed.

    >**1. Filenames that begin with a period character are hidden.** This only means that **`ls`** will not list them unless you say **`ls -a`**. When your account was created, several hidden files were placed in your home directory to configure things for your account. 

    >**2. Filenames and commands in Linux, like Unix, are case sensitive.** The filenames File1 and file1 refer to different files.

    >**3.** Though Linux supports long filenames that may contain embedded spaces and punctuation characters, limit the punctuation characters in the names of files you create to period, dash, and underscore. **Most important, do not embed spaces in filenames. If you want to represent spaces between words in a filename, use underscore characters.** 

    >**4. Linux has no concept of a “file extension” like some other operating systems.** You may name files any way you like. The contents or purpose of a file is determined by other means. Although Unix-like operating systems don’t use file extensions to determine the contents/purpose of files, many application programs do.

* **_Some Helpful Shortcuts_**
`cd` Changes the working directory to your home directory.
`cd -` Changes the working directory to the previous working directory.
`cd ~user_name` Changes the working directory to the home directory of user_name.

---

### Chapter 3: Exploring the System
`ls` List directory contents
`file` Determine file type
`less` View file contents

**1. More Fun with `ls`**
We can simply enter `ls` to get a list of files and subdirectories contained in the current working directory. 
```
ls
```

We can specify the directory to list.
```
ls /usr
```

We can specify multiple directories. In the following example, we list both the user's home directory `~` and the `/usr` directory.
```
ls ~ /usr
```

* **_Options and Arguments_**
Commands are often followed by one or more **options** that modify their behavior and, further, by one or more **arguments**, the items upon which the command acts. So, most commands look kind of like this:
    ```
    command -options arguments
    ```
    Most commands use options, which consist of a **single character preceded by a dash**, for example,` -l`. Many commands, however, including those from the GNU Project, also support long options, consisting of a word preceded by **two dashes**. Also, many commands allow multiple short options to be strung together. In the following example, the ls command is given two options, which are the l option to produce long format output, and the t option to sort the result by the file’s modification time.
    ```
    ls -lt --reverse
    ```
    *Command options, like filenames in Linux, are case sensitive.*

    | Option    | Long option   | Description  |
    | ------    | -----------   | ------------ |
    |-a         | --all         | List all files, even those with names that begin with a period, which are normally not listed (that is, hidden).|
* **_A Longer Look at Long Format_**






---

### Chapter 4: Manipulating Files and Directories 

---

### Chapter 5: Working with Commands

---

### Chapter 6: Redirection

---

### Chapter 7: Seeing the World as the Shell Sees It

---

### Chapter 8: Advanced Keyboard Tricks 

---

### Chapter 9: Permissions

---

### Chapter 10: Processes

---
---


Headers are defined by the '#'symbol.  One '#' for H1, two for H2, etc.

<!-- 
    Example

    # H1 Header 
-->
> **TODO**. Create an H1 
> # Header 1

> **TODO**. Create an H2 
> ## Header 2

> **TODO**. Create an H3 
> ### Header 3

> **TODO**. Create an H4 
> #### Header 4

---

## Quotes


Quotes are defined by the  '>' symbol 

<!--
    Example

    > This is an example quote
-->

> **TODO**. Create a quote

> This is my quote

You can combine a header with a quote.

<!-- 
    Example

    > # H1 Quote
-->

> **TODO**. Create an H2 Quote 

> # This is really big quote
---

## Emphasis

Add emphasis with asterisks '*' and underscores '_'
Two before and after (no spaces) a section of texts makes it bold 

<!--
    Example

    **Bold Text with asterisks**
    __Bold Text with underscores__
-->

**Bold Sentence**

__Bold with italics__

One before and after (no spaces) a section of texts makes it bold 

<!-- 
    Example

    *Italicized Text with asterisks*
    _Italicized Text with underscores_
--> 

*Italic sentence*

_Italic sentence_

You can also put Bold and Italicized text inline by surrounding a group of words.

<!-- 
    Example

    This text is **bold** and this text is *italicized* 
-->

> **TODO**. Create a bold sentence, an italicized sentence, and a sentence with both bold and italicized text inline

This is my _italicized_ word and this is my **world**.

---

## Horizontal Rule
A horizontal rule gives a visible line break.  You can create one by putting three or more hypens, asterisks, or underscores (-, *, _).

For what it's worth, I prefer dashes...

<!-- 
    Example

    ---
    ***
    ___
-->

> **TODO** Create a horizontal rule

---

***

___



## Lists

Create unordered lists using '-', '*', '+, 
<!-- 
    Example with each 

    - item
    * item
    + item
    - sdfsd
-->

- item
* item
+ item
+ item


You can create sublists by indenting
<!-- 
    Example

    - item
    - subitem
-->

- list 
  - sublist
    - subsublist

Create ordered lists using a number prefix

<!-- 
    Example

    1. item 1
    2. item 2
    3. item 3 
-->

1. Item 1
2. Item 2
3. Item 3
   
> **TODO** Create an unordered list of your 5 favorite TV Shows 

> **TODO** Create an ordered list of your top 5 Movies 

---

## Links

Create a link by surrounding it with angle bracket
<!-- 
    Example

    <http://www.jamesqquick.com> 
-->
<https://github.com/RunzheZ/CppPrime>

Create a link with text by surrounding text with brackets, [], and link immediately following with parenthesis ()

<!-- 
    Example

    [James Q Quick](http://www.jamesqquick.com) 
-->

[My Github](https://github.com/RunzheZ/CppPrime)

> **TODO** Create a link to your website, twitter, or github. with no text

> **TODO** Create a link with text to your website, twitter, or github

What if you needed to reuse a link several times?  Well, you could copy and paste that link each time.  That means, if you need to update the link, you will have to do it each time its used.  There's a better way!

Create reference style links by defining your link with the a 'key' inside of brackets, colon, space, and the link

<!-- 
    Example

    [1]: http://jamesqquick.com/ 
-->

[Github Website]: https://github.com/RunzheZ/CppPrime
Then use the reference style link by using your text inside of brackets followed by the link 'key' inside of bracket.

<!-- 
    Example

    [My Website][1] 
-->

[My Github][Github Website]

> **TODO** Create a reference link to your website and reference it three times

You can also link to other locations on your markdown page.  Remember, your MarkDown will get converted to HTML, so you can, in theory, use a anchor tag to link to an element with a specific ID.  You can find an example of this in the list of sections at the top of this document.

When we create a header tag for example, it implicitly creates an id property.

Ex '# Header' becomes `<h1 id="header">Header</h1>`

Names will be converted to ids by replacing spaces with hyphens and uppercase letters with lowercase letters (think css naming convention).

Ex 'Header Info' becomes header-info

Header Info --> header-info

> **TODO** Create a link to another part of your page.

[Code](#code)

---

## Images

Defining an image is similar to defining a link, except you prefix it with '!'

<!-- 
    Example

    ![James Quick](https://pbs.twimg.com/profile_images/887455546890211329/tAoS7KUm_400x400.jpg) 
-->

Just like links, you can define images by reference in the same format.

Define the reference

<!-- 
    Example

    [profile]: https://pbs.twimg.com/profile_images/887455546890211329/tAoS7KUm_400x400.jpg 
-->

Use the reference

<!-- 
    Example

    ![James Quick][profile] 
-->

> **TODO** Create a reference link to your profile picture and then reference it.

---

## Code

You can do inline code with `backticks` (``)

> **TODO** Display a line of text with inline code

Here is some code inline `var item = {}`

You can do blocks of code by surroung it with 3 backticks (``` ```)

<!-- 
    Example

    ``` 
    var num = 0;
    var num2 = 0;
```
-->

> **TODO** Display a block of code from your favorite language
```
    var item = {}
    item.something = "something";
```
The above does not give language specific highlighting.  You can specify the programming language immediately following the opening 3 backticks.  You Should see a difference in highliting!

> Javescript code block
<!-- 
    Example Javascript

    ```javascript
    var num = 0;
    var num2 = 0;
    ``` 
-->

```javascript
    var num = 0;
    var num2 = 0;
``` 

<!--
    Example HTML

    ```html 
    <div>
        <p>This is an html example</p>
    </div>
    ```
-->

> HTML code block

```html 
    <div>
        <p>This is an html example</p>
    </div>
```

> **TODO** Display a block of code from your favorite language while specifying the language


---

## Tables
Tables are useful for displaying rows and columns of data.  Column headers can be defined in between pipes (|).  Headers are separated from table content with a row of dashes (-) (still separated by pipes), and there must be at least 3 dashes between each header.  The row data follows beneath (still separated by pipes).

<!-- 
    Example

    | Header 1    | Header 2    | Header 3    |
    | ----------- | ----------- | ----------- |
    | Row 1 Col 1 | Row 1 Col 2 | Row 1 Col 3 | 
-->


The column definitions and row definitions do not have to have the exact same width sizes, but it would be much more readable.  Notice the output of the following two tables are the same, but the second (the raw markdown) is much more readable.

<!-- 
    Example

    | Header 1 | Header 2 |
    | ----| ---|
    |Loooooooooooooong item 1 | looooooooooong item 2 | 
-->

| Header 1 | Header 2 |
| ----| ---|
|Loooooooooooooong item 1 | looooooooooong item 2 | 

<!-- 
    Example

    | Header 1                | Header 2              |
    | ----------------------- | --------------------- |
    |Loooooooooooooong item 1 | looooooooooong item 2 | -->

> **TODO** Create a table with three columns and two rows

You can also align (Center, left, right) the text in a column by using colons (:) in the line breaks between headers and rows.  No colon means the default **left alignment**.  Colons on each side signifies **center alignment**.  And a trailing colon means **right alignment**.

> **TODO** Create a table with three columns, one aligned left, one aligned center, and one aligned right

<!-- 
    Example
    
    | Header | Header 1 | Header 2  |
    | ------ | :------: | --------: |
    | Aligned Left | Aligned Center | Aligned Right | 
-->

| Header | Header 1 | Header 2  |
| ------ | :------: | --------: |
| Aligned Left | Aligned Center | Aligned Right | 

---

## Custom HTML

Since MarkDown gets automatically converted to HTML, you can add raw HTML directly to your MarkDown.


```html 
<p>Sample HTML Div</p>
```

Creates this 

<p>Sample HTML Div</p>

> **TODO** If you are comfortable with HTML, add some raw HTML.

---

## Custom CSS

You can also add custom CSS to your MarkDown to add additional styling to your document. You can also include CSS by including a style tag.

```html
    <style>
        body {
            color:red;
        }
    </style>
```
> **TODO** If you are comfortable with CSS, give your page some style.

---

## Additional Resources
- [Markdown Cheat Sheet - Adam P on Github](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images)
- [Daring Fireball Markdown Syntax](https://daringfireball.net/projects/markdown/syntax)
- [MarkDown in Visual Studio Code](https://code.visualstudio.com/docs/languages/markdown)