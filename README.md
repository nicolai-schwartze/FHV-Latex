[![Build Status](https://travis-ci.org/pasrom/FHV-Latex.svg?branch=master)](https://travis-ci.org/pasrom/FHV-Latex)
#   FHV-Latex template

To use this template, it is recommened to work with [TeXstudio](http://texstudio.sourceforge.net). You can use the given profile provided in [scripts](https://github.com/pasrom/FHV-Latex/tree/master/scripts)  (Mac, Windows, Linux). If you like to add a dictionary here is a [link](https://extensions.libreoffice.org/extensions/german-de-at-frami-dictionaries) where you can download one. To install the dictionary go to preference (TeXstudio), under Spell Checking Dictionary, change the directory to the folder you put your dictionary in and restart TeXstudio ([Source](https://tex.stackexchange.com/questions/87650/dictionary-for-texstudio-no-dictionary-available/87652)).

The bibliography uses Biber to build and is adapted to FHV guidelines.

I also recommend to use [TeX Live](https://www.tug.org/texlive/) Latex distribution. 

[Here](https://github.com/pasrom/FHV-Latex/blob/master/tex/Examples.tex) you find some examples: how to use Pictures, Tables, TikZ and the usage of referencing equations/sections.

An easy to use [tablegenerator.](http://www.tablesgenerator.com).

If you like to have a preview of the output mentioned in [LatexVorlage](https://github.com/pasrom/FHV-Latex#latexvorlagetex), [here](https://www.dropbox.com/sh/zu01sy61kavxjt9/AAAtWiXSjG5IDLw3g8G1s3Yka?dl=0) you will find the different builds.

# How to compile?

 1. `pdflatex`
 2. `biber`
 3. `makeglossaries`
 4. `pdflatex`
 5. `biber`
 6. `makeglossaries`
 7. `pdflatex`

For a more detailed description see the makefile.

Steps 5 and 6 are only necessary if you are using acronyms in the appendix.

If you are compiling with TexStudio and you get this error

```
Befehl konnte nicht gestartet werden: "/Users/roman/Documents/workspace/FHV-Latex-diff/scripts/copy_TeXstudio.sh" "LatexVorlage" "/Users/roman/Documents/workspace/FHV-Latex-diff/"
```

make sure the script is runable.

```
chmod +x scripts/copy_TeXstudio.sh
```


# overallDefines.sty

Here you can define new commands (`./sty/overallDefines.sty`).

 1. With the command `\def\debug{false}` you can choose to add the packages
 
    ```
    \usepackage{pagegrid}
    \usepackage{showframe}
    \usepackage{layout}
    ```
    This helps to lock at the page layout and to find `overfull \hbox` warnings.
 2. With the command `\def\newLanguage{ngerman}` you can choose between the language english and german, don't forget to build twice and don't panic if the first compilation throws an error.
 3. Setting names of the author, supervisor and titles:
    ```
    \def\authorName{Name\xspace}
    \def\authorSurname{Surname\xspace}
    \def\supervisorName{Supervisor Name\xspace}
    \def\supervisorSurname{Supervisor Surname\xspace}
    \def\authorTitleBefore{Title B\xspace}
    \def\authorTitleAfter{Title A\xspace}   
    \def\supervisorTitleBefore{Title B\xspace}
    \def\supervisorTitleAfter{Title A\xspace}
    ```
 4. Setting the gender of the author with the command `\def\wOrM{m}`
 5. With the command `\def\notesFHV{}` you can add notes beside or under a paragraph. Following input is allowed:

    `disable`: notes not showed
    
    `draft`: notes showed
    
# LatexVorlage.tex

This is the main file, where all subfiles and packages are loaded.

You can define here 

 1. The mode of the layout can be spezified with`\def\FHVmode{x}`. Where following arguments are working:

    `1`: **documentation**, e.g.: a documentation for a project done in a course
    
    `2`: **thesis**, e.g.: a master thesis (standard). It changes the style of the title page.
    
    `3`: **summary**, changes the layout. If you want to use all the space an the 
    page, but take in mind, the typography is destroyed!

    `5`: **presentation**, if an error is occurring, build twice or delete the build files!
    
    `9`: **paper**

 2. With the `\def\FHVtitlePage{fhv}` command it is possible to change the title layout:

    `minimal`: only a title, name, version number and date.
    
    `fhv`: following the layout from [ilias](https://ilias.fhv.at/goto_ilias_fhv_at_file_350312_download.html).
    
    `comment out`: comment out this line to use the layout defined with `FHVmode`.
    
 4. `\newcommand{\version}{v0.0}` self explaining, version numbering.

## Use autocompletion

Coppy [`fhv.cwl`](https://github.com/pasrom/FHV-Latex/blob/master/scripts/fhv.cwl) to `~/.config/texstudio/completion/user/` (Linux, Mac). For further information [FAQ: Where are cwl files stored?](https://sourceforge.net/p/texstudio/wiki/Frequently%20Asked%20Questions/#where-are-cwl-files-stored)