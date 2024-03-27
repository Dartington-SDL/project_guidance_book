# Quantitative project outputs and dissemination

## GitHub repository
All quantitative projects should have a GitHub repository which is setup at the beginning of the project and used as the collaborative platform for all project work. Information on the setup and use of [Git and GitHub is available here](../project_guidance_book/git.md) and guidance on [collaborative working practices is available here](../project_guidance_book/workflows.md)

Every project will have slightly different outputs but as a minimum you should try to have:
- A project report in the format of a Jupyter book
- A DOI associated with the GitHub repository
- An open dataset that would enable anyone to run the code

In addition it would be useful to have:
- The project protocol - this could be included in the project report
- A pre-print publication and/or link to a journal publication

## Jupyter book report

Jupyter books provide an excellent way to produce well formatted reports with interactive content that can be published online and as a PDF. This section provides a basic introduction to creating a Jupyter book and publishing it on GitHub. More information and tutorials are available on the [Jupyter Books website](https://jupyterbook.org/en/stable/intro.html "Jupyter Books documentation and tutorials").

Start by creating a new folder for your Jupyter book

A basic Jupyter book is structured using the follow files:
- a configuration file in YAML format called '_config.yml'
- a table of contents file in YAML format called '_toc.yml'
- content files in markdown format
    - the front page will be called 'intro.md'
    - all subsequent pages can be named anything as '.md' file types

The _config.yml file should contain as a minimum

```yaml
# In _config.yml
title: DSDL quantitative working practices
author: DSDL
copyright: "2024"
logo: DSDL_rgb_logo.png
exclude_patterns: [.venv]
```

The _toc.yml file is structured as

```yaml
# In _toc.yml
format: jb-book
root: intro
chapters:
- file: ide
- file: git
- file: workflows
- file: protocols
- file: outputs
```

The first line is a comment just stating the file name  
`Format` states this is a Jupyter Book  
`root` is the front page of the book  
`chapters` are listed in order using the file names

Markdown is a simple and intuitive language to use. An excellent guide is available at <https://www.markdownguide.org/basic-syntax/>

When creating new files in VScode that are not python or ipython types, select 'New text file' then save the file and add the required file extension such as .md or .yml

Once you have created your configuration, table of contents and content files you are ready to build your book. In the VScode terminal change your directory to the folder to where your book is located. If you are in your book directory you can go up a level using the command `cd ..`

The command to build your book is `jupyter-book build mybookname/`

A _build file will be created in your book folder. You can now go to your file explorer and click through _build > html > index.html. The index.html file will open your book in your browser.

## GitHub repository archiving, DOI and releases using Zenodo

GitHub repositories are not inherently persistent or citable. To ensure that the correct version of a repository persists over time and is citable in reports and publications we need to archive specific releases of our repository and produce a DOI (data object identifier). The DOI is then citable as a persistent reference in any publications associated with the project.

### Setup Zenodo

1. Go to <https://zenodo.org/> navigate to the login page
2. Choose to login with GitHub
3. Review the access permissions and authorise Zenodo

### Initalise the archiving of a repository

1. Navigate to the Zenodo GitHub page within your account
2. All of your public repositories should be visible. If they are not, click on Sync, then reload the page
3. Toggle the button next to the repo you wish to archive to On

### Creating a new repository release to produce a DOI

1. Go to the repository you are archiving on GitHub
2. In the Code page of the repository on the right hand side there is a section called Releases
3. Click on Create new release
4. Click on Choose a tag and create a new tag. The tag should be formatted as 'v1.0'. Releases should be incremented as 'v1.1' for minor changes and 'v2.0' for major changes
5. Enter a title and description of the release. The title should briefly summarise the key changes in the new release. The description should list the changes made in the release
6. Click the green Publish release button

### Retrieving the DOI from Zenodo

1. Go to the GitHub section in your Zenodo account
2. You should now see a DOI badge next to the repo you have just produced the release for
3. If the DOI badge is not visible, click the Sync button then reload the page and the badge should appear
4. Double click on the badge and a window will open with various code options. Copy the markdown code
5. Go to the Readme in your GitHub repo, edit it directly in the browser and paste the DOI badge markdown code which will look similar to
```md
[![DOI](https://zenodo.org/badge/754072112.svg)](https://zenodo.org/doi/10.5281/zenodo.10629600)
```
6. You will then be asked to commit these changes
7. The badge will now appear in the repo Readme

### Note

When you create a new release of your repository a new DOI will be generated in Zenodo. You will need to manually update the badge code in the repo Readme so it reflects the latest release

## Open data

- Dummy data
- Fully anonymised data
- Synthetic data
- Pseudonymised data

## Pre-print publication