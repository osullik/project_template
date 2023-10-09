# Project Template

Clone this when starting a new project to serve as a structural backbone. 

## Useful Links
Update these links to point to your relevant project resources

[Project Overleaf](https://www.overleaf.com)

[Project Github](https://github.com)

[Paper Repository (Google Drive)](https://drive.google.com/drive/) *Alternately, create reference_papers in bibliography*

[Project Calendar](https://drive.google.com/drive/)

[Project Jira](https://www.atlassian.com/software/jira)

[Paper Token Tracker](https://docs.google.com/spreadsheets/d/1KDuRjv6qjNGhNRXR7ndzlwfd_iGQ3Wi74J1l4BdOmIE/edit?usp=sharing)

## Project Structure

The structure of the project is shown in the tree below. Put simply, we divide among the stuff we need for writing [(papers)](https://github.com/osullik/project_template/papers), the stuff we use for coding[(code)](https://github.com/osullik/project_template/code) and the place we keep data [(data)](https://github.com/osullik/project_template/data)

### papers

For ease of collaborative editing, I have decomposed the ACL format into several subcomponents. In general, the [project_template.tex](https://github.com/osullik/project_template/blob/main/papers/project_template.tex) file just holds the framework to arrange each of the sections, which are kept in their own files in [sections](https://github.com/osullik/project_template/tree/main/papers/sections). The [project_template.tex](https://github.com/osullik/project_template/blob/main/papers/project_template.tex) file also knows to grab the relevant [style](https://github.com/osullik/project_template/tree/main/papers/style) and [Bibliography](https://github.com/osullik/project_template/tree/main/papers/bibliography) files from their respective directories. It might seem like overkill, but when we're editing & tracking this all with github it will make our lives **much** easier.

If you're compiling offline (i.e. not using overleaf), you can use the Makefile I've included. You need to have *[latexmk](https://mg.readthedocs.io/latexmk.html)*, *[inkscape](https://inkscape.org/)* and *[gnu make](https://www.gnu.org/software/make/)* installed to run it. If you want to work on it locally and aren't sure how to set this up let me know. 

#### Setting up compilation environment for MacOS: 

1. Download [Homebrew](brew.sh): 

        /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

2. Install TexLive: 

        brew install texlive

3. Install Inkscape

        brew install --cask inkscape

4. (If it isn't on your machine by default) GNU Make

        brew install make

#### Setting up comilation environment For Windows: 

1. Run Powershell as administrator: 

2. Install [Chocolatey](https://chocolatey.org/): 

        Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

3. Install GNU Make: 

        choco install Make

4. Install Perl (for LatexMk)

        choco install strawberryperl

5. Install Ruby (for Editing Scripts)

        choco install ruby

6. Install TexLive Utilites: 

        choco install texlive

7. Install MikTex: 

        choco install miktex

8. Install LatexMK with MikTex Package Manager (through GUI)

9. Install InkScape

        choco install inkscape


#### Key commands for Making the file: 

To compile the PDF, simply run the following from the root of the papers directory:

    make main.pdf

You'll notice a lot of random intermediary files get made. To get rid of them and leave your PDF use:

    make publish

Sometimes everything goes wrong and we need to start again, when that happens use: 

    make clean

The [scripts](https://github.com/osullik/project_template/tree/main/papers/scripts) directory contains a lot of [Jordan's](https://github.com/Pinafore/publications/tree/master/scripts) useful editing and checking scripts. Github tends to mess with the permissions on these, so you'll likely need to CHMOD them back to be executable again. The *make main.pdf* command uses some of these scripts, so it is a good idea to do that occasionally. 

### code

The [code](https://github.com/osullik/project_template/tree/main/code) directory has a [src](https://github.com/osullik/project_template/tree/main/code/src) subdirectory, which is where all of our substantive code files should live. The [tests](https://github.com/osullik/project_template/tree/main/code/tests) subdirectory is where we'll build and store any relevant tests (we like unit tests in this house) and the [scripts](https://github.com/osullik/project_template/tree/main/code/scripts) subdirectory will hold any shell / python scripts we use to standardize the conduct of experiments (i.e. making things more replicable)

### data

The [data](https://github.com/osullik/project_template/tree/main/data) directory may directly hold the actual data files (if small enough) but in general should contain the scripts / instructions required to download / generate data from more appropriate sources (git LFS, Google Drive etc)

```
.
├── LICENSE
├── README.md
├── code
│   ├── scripts
│   ├── src
│   └── tests
├── data
└── papers
    ├── project_template.tex
    ├── bibliography
    │   └── project_template.bib
    ├── makefile
    ├── scripts
    │   ├── -h.tex
    │   ├── acl_formatchecker.py
    │   ├── camera_copy.sh
    │   ├── clean_bib.py
    │   ├── dictionary.txt
    │   ├── diff.py
    │   ├── hunspell_dictionary.dic
    │   ├── latex2txt.py
    │   ├── latex_deps.py
    │   ├── latex_lines.py
    │   ├── latex_lines_test.py
    │   ├── merge_bibtex.py
    │   ├── output.tex
    │   ├── preamble_check.py
    │   ├── rscript_if_ne.sh
    │   ├── sanitize.py
    │   ├── sanitizeBib.py
    │   ├── spell.py
    │   ├── split_pdf.py
    │   ├── start_paper.py
    │   ├── style-censor
    │   ├── style-check.rb
    │   ├── styleCheckResults.txt
    │   ├── test.tex
    │   └── thesis_formatchecker.py
    ├── sections
    │   ├── 00_abstract.tex
    │   ├── 10_introduction.tex
    │   ├── 20_baselines.tex
    │   ├── 30_experiment_design.tex
    │   ├── 40_results.tex
    │   ├── 50_related_work.tex
    │   ├── 60_discussion_future_work.tex
    │   └── 70_conclusion.tex
    └── style
        ├── acl.sty
        └── acl_natbib.bst
```

## Coding
We'll work out how we want to manage our approach to coding later. I'm a big fan of TDD, but we can work out how we want to approach it. 

As a rule of thumb, don't commit things direct to the master branch. Make your own branch locally using something like: 

        git checkout -b branch_name

Then synch it to the upstream: 

        git --set-upstream origin branch_name

so when you push things to gitm we can review and verify work doesn't break via a pull request. 



## Writing

### Reading Papers

We should keep a shared bibliography. The bib file lives in the github repo, in the [papers/bibliography](https://github.com/osullik/project_template/tree/main/papers/bibliography) directory. I have set up a google drive to drop the relevant papers in if you find something that might be of use [your link here](https://drive.google.com).

For the .bib file, follow the writing conventions below, but the main one is naming of files and bib entries. 

Bib file entries require a citation key. Applications like [Jabref](https://www.jabref.org/) tend to generate it as FirstAuthorLastNameYear, so that's what we'll go with. For example if I was reading an article by Jacobs published in 2023 the citation key would be Jacobs2023. If we then name the paper in the google drive the same thing, we have a pretty good mechanism to track what papers are what between the two. You can use jabRef and just point it at the bib file in this repo, or however else you want to edit them. (Just be warned, .bib issues seem to cause a lot of the compilation failures)

For multiple papers in the same year, add a, b, c etc - Jacobs2023, Jacobs2023a 

### Writing Sections
We can use overleaf, or edit the sections offline. Either way, we'll back things up to github as we go. The plus side is that it makes it very difficult for us to lose work! The downside is that we need to be a little bit careful about how we manage working on the documents so that we don't create merge conflicts. For each, the process below should work: 

#### Working on Overleaf
1. Pull changes from github (in the menu on the LHS of the page)
2. Check out the section(s) you want to work on on the token tracker. 
3. Edit each section you have checked out in overleaf. 
4. Once you are happy with your changes, and it compiles without errors in the overleaf editor...
5. Push your changes to github
6. Delete your name from the token tracker for the sections you're done with. 

#### Working Offline: 
1. Pull changes from github. Command will be something like: 

        git pull

2. Check out the section(s) you want to work on on the token tracker. 
3. Edit each section you have checked out. Use your editor of choice, but VScode has some nice LateX plugins
4. Once you're happy it works, make sure it compiles with the makefile, command will be something like:

        make main.pdf

5. Get rid of all the intermediary files: 

        make publish

6. Stage the files for github, commands will be something like... 

        git add sections/filename1 
    
        git commit -m "description of what you did"

        git push

7. If it pushes without error, go ahead and release it from the token tracker. 