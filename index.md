
---
title: "Community contributions for EDAV Fall 2019" 
date: "2019-11-03"
site: bookdown::bookdown_site
output: bookdown::gitbook
documentclass: book
github-repo: jtr13/cc19
description: "This book will hold all community contributions for STAT GR 5702 Fall 2019 at Columbia University"
---


# (PART) Introduction {-}

# Instructions
This chapter gives you all the information you need to upload your community contribution. **Please read this entire document carefully before making your submission.** Of particular note is the fact that **bookdown** requires a different .Rmd format than you're used to, so you must make changes to the beginning of the file as described below before submitting.

## Background

This web site makes use of the **bookdown** package to render a collection of `.Rmd` files into a nicely formatted online book with chapters and subchapters. Your job will be to submit a slightly modified version of your community contribution `.Rmd` file to the GitHub repository where the source files for this web site are stored. On the backend, the admins will divide the chapters into book sections and order them. We use [Travis CI](https://travis-ci.com){target="_blank"} to render the book and push the rendered `.html` files to our `gh-pages` branch--you can view [our builds here](https://travis-ci.com/jtr13/cc19){target="_blank"}--and GitHub Pages to host the site. 

If your community contribution is in a different format, then create a short `.Rmd` file that explains what you did, and includes links to any relevant files, such as slides, etc. which you can post on your GitHub repo (or another online site.)

## Preparing your `.Rmd` file

You should only submit **ONE** `Rmd` file. 

After completing these modifications, your `.Rmd` should look like this [sample bookdown `.Rmd`.](sample_project.Rmd){target="_blank"}

1. Create a concise, descriptive name for your project. For instance, name it `base_r_ggplot_graph` or something similar if your work is about contrasting/working with base R graphics and **ggplot2** graphics. Check the `.Rmd` filenames in [the project repo](https://github.com/jtr13/cc19){target="_blank"} to make sure your name isn't already taken. Your project name should be words only and joined with underscores, i.e. **Do not include whitespace in the name.** Create a copy of your `.Rmd` file with the new name. 

2.  Completely delete the YAML header (the section at the top of the `.Rmd` that includes name, title, date, output, etc.) including the `---` line.
    
3. Choose a short, descriptive, human readable title for your project as your title will show up in the table of contents -- look at examples in the [rendered book](https://jtr13.github.io/cc19/){target="_blank"}. Capitalize the first letter only ("sentence case"). On the first line of your document, enter a single hashtag, followed by a single whitespace, and then your title. It is important to follow this format so that bookdown renders your title as a header. Do not use single # headers anywhere else in the document.
    
4. The second line should be blank, followed by your name(s):
    
   ```
    # Base R vs. ggplot2
    
    Aaron Burr and Alexander Hamilton

    Your content starts here. 
   ```

5. If your project requires data, please use a built-in dataset or read directly from a URL, such as:

    `df <- readr::read_csv("https://people.sc.fsu.edu/~jburkardt/data/csv/addresses.csv")` <br> If you absolutely must include a data file, please use a small one, as for many reasons it is desirable to keep the repository size as small as possible.
    
6. If you have included a `setup` chunk in your `Rmd` file, please remember to remove the label `setup` in the chunk, ie., use :

  ```
  {r, include=False}
  ```
  
  instead of
  
  ```
  {r setup, include=False}
  ```

Want to get fancy? See the [optional tweaks](#optional-tweaks) section below.

## Submission Steps

To submit your work, we will be following the instructions in [this tutorial](https://edav.info/github.html#st-pr-on-another-repo-with-branching){target="_blank"}, which are provided in abbreviated form below, with specific instructions on naming conventions, content information, and other important details.

1. Fork [cc19 repo (this repo)](https://github.com/jtr13/cc19){target="_blank"} to your GitHub account. 

2. Clone/download the forked repo to your local computer.

3. Create a new branch and name it with your project name, in our case `sample_project`. If you forget to do so, check [this tutorial](https://edav.info/github.html#fixing-mistakes) to fix.  

4. Copy your modified `.Rmd` file with the same name into the root directory on the branch. In our example, it is [`sample_project.Rmd`](sample_project.Rmd){target="_blank"}. 
   
5. Do not include an `.html` file. (In order for the **bookdown** package to work, all `.Rmd` files will be rendered behind the scenes.)

6. [OPTIONAL] If you have other resources (such as images) included in your project, create a folder under `resources/`. In our example, it is [`resources/sample_project/`](resources/sample_project){target="_blank"}. Put the resources files there. 

7. When you are ready to submit your project, push your branch to your remote repo. Follow [this tutorial](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork) to create a pull request. If you follow the steps, we will merge it to the master branch. After submitting your pull request, do not be concerned if you see an "All builds have failed" message from Travis CI. There are things that need to be done on the backend, such as adding the libraries you use to the project for the Travis CI build to pass.

## Optional tweaks

1. If you prefer for links from your chapter to open in new tabs, add `{target="_blank"}` after the link, such as:

    `[edav.info](edav.info){target="_blank"}`

2. Note that your headers (##, ###, etc.) will be converted to numbered headings as such: <br> `##`  --> 3.1 <br> `###` --> 3.1.1 <br> These headings will appear as chapter subheadings and sub-subheadings in the navigation panel on the left. Think about a logical structure for users to navigate your chapter. We recommend using only `##` and `###` headings as subheadings such as 4.1.3.4 are generally not necessary and look messy.

3. Unfortunately, there's no simple way to preview your chapter before it's actually merged into the project. (**bookdown** has  `preview_chapter()` option but it only works after the entire book has been rendered at least once and that will become more and more complex and require more and more packages as the project grows.) If you really want to preview it, fork and clone this [minimal bookdown repo](https://github.com/yihui/bookdown-minimal){target="_blank"}, add your `.Rmd` file, click the "Build book" button on the Build tab (next to Git), and then open any of the `.html` files in the `_book` folder in a web browser to see the rendered book. (**Do not click the Knit button as it will not build a bookdown book.**) <br><br> If you're interested in more **bookdown** options, see the [official reference book](https://bookdown.org/yihui/bookdown/){target="_blank"}. <br><br> Have more useful tweaks to share? Submit an issue or PR.


## FAQ

### What should I expect after creating a pull request? 

1. Within a week after you create a pull request, we will apply a label to it and assign an administrater who will review all the files you submit to see if they meet the requirements. 

2. It will take some time before we can process all the pull requests, so as long as you see your pull request has been labeled and assigned to an administrater, don't worry. 

3. However, if the admin contacts you regarding the pull request, that usually means your files fail to meet some requirements. The admin will clearly state what is wrong, so please fix them as soon as possible. 

### What if I catch mistakes after my pull request is merged?

1. You may submit additional pull requests to fix material on the site. If the edits are small, such as fixing typos, it is easiest to make the edits directly on GitHub, following [these instructions](https://edav.info/contribute.html#github-only-walkthrough){target="_blank"}. We will merge first pull requests before edits, so please be patient.

### Other questions

If you encounter other problems, please [submit an issue](https://github.com/jtr13/cc19/issues){target="_blank"} and we will look into it. 

Thank you for your contributions!
