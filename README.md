# Hop Website

This repository is used to generate the Hop website

Tools used to generate the website:

 - [Git](https://git-scm.com/) a source code management tool used to fetch document sources from different
   github repositories.
 - [Node.js](https://nodejs.org/) a JavaScript runtime used to build the website. You will need to use Node.js version 10.
 - [yarn](https://yarnpkg.com/) a blazing fast dependency and package manager tool used to download
   and manage required libraries.
 - (installed via yarn) [Gulp](http://gulpjs.com/) a task automation tool. Used to build the Hop
   Antora UI theme.
 - (installed via yarn) [Hugo](https://gohugo.io) a static site generator. Simplified, it takes the
   documentation from the `content` directory and applies templates from `layouts`
   directory and together with any resources in `static` directory generates output in
   the `public` directory.
 - (installed via yarn) [Antora](https://antora.org/) a documentation site generator. It uses
   Asciidoc documents from different sources.

## Build with Node and yarn

You can build the website locally using the tools `Node.js` and `yarn`.


### Preparing the tools

#### Node

Make sure that you have Node.js (herein "`Node`") installed.

    $ node --version

If this command fails with an error, you do not have Node installed.

This project requires the Node LTS version 10 (e.g., v10.15.3).

Please make sure to have a suitable version of Node installed. You have several options to install
Node on your machine.

- Install using the Node version manager [nvm](https://github.com/creationix/nvm)
- Install using [Homebrew](https://brew.sh/) and [Node formulae](https://formulae.brew.sh/formula/node)
- Install from official [Node packages](https://nodejs.org/en/download/)

Note - If you have different Node version other than Node LTS version 10 you can use following command to make
Node LTS version 10 as default Node version.

    $ nvm alias default 10

Now that you have Node 10 installed, you can proceed with checking the Yarn installation.

#### Yarn

Follow [the documentation on installing](https://yarnpkg.com/en/docs/install) Yarn for your Operating system.

#### Clone and Initialize the project

Clone the hop-webiste git repository:

    $ git clone https://github.com/project-hop/hop-website.git


## Build the Antora Hop UI theme

First step is to build the Antora ui theme used for the Hop website. The theme sources are located
inside [Project root directory/antora-ui-hop](antora-ui-hop). So first switch to that directory:

    $ cd antora-ui-hop

In that directory execute:

    $ yarn install # needed only once, or if dependencies change
    $ yarn build   # to perform the ui theme build

You should see the Antora theme bundle generated in [antora-ui-hop/build/ui-bundle.zip](antora-ui-hop).

## Build the website content

Before you are able to build the website content the ui bundle must be present.

To build the website go to the project root directory and run:

    $ yarn install # needed only once, or if dependencies change
    $ yarn build   # to perform the build

You should see the generated website in the `public` directory.

## Preview website locally

You can preview the the website on your local machine once you have the generated website available in
the `public` directory.

Hugo can start a simple web server serving the generated site content so you can view it in your favorite browser.

Simply call

    $ yarn preview

and you will be provided with a web server running the site on [http://localhost:1313/](http://localhost:1313/)

Point your favorite browser to `http://localhost:1313/` and you will see the Hop website.

## Contributing

The website content is added under the `content` directory, logical groups have been created to group website content. This repository will only be used for the more "static" types of information (blog/news/announcements). Software documentation will reside in a seperate repository or in the same repository as the code.

Asciidoc is used to write content for the website, more information about asciidoc syntax can be found [here](https://asciidoctor.org/docs/asciidoc-syntax-quick-reference/)

Images and other resources should be added in the `static` folder.

## Jenkins
This repository also contains a Jenkins hook, when you add a new branch or pull request with changed content the website is automatically build and a preview is available. When merged with master the site is redeployed

You can check your pull request and see if the site is correctly rendered by going to the [Hop Jenkins website](https://jenkins.project-hop.org/job/hop-website


/)



* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family:"Quicksand",sans-serif;
  
}

body{
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #111;
  
}

.container
{
  position: relative;
  width: 800px;
  height: 500px;
  background: #222;
}

.container .clip
{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: 0.5%;
  
}

.container .clip.clip1
{
  background: url(https://lh3.googleusercontent.com/fife/ABSRlIoUPlZpSV9wXgEw2k9BHVXlDD4diTpKAa3nOHY3Uwbff0aFy_cQOAszLSr2IA67dV7-xZTNlVuY7C7klwN2UsECnSlfBZ6gBaOdcuLeeOJQsi7a4k4gs9difvWIb-B0vsEhii8ZhV7kLbjUZKXajj3Nff_RQa8QL7UdfppQJ5_GlJZYX6qZrIqDXFZhtpDJoHRdXQJVMJFB3exJ2OBssmFVVX11dPPFLjkTvy2JPKN1cMfVtSEFI-Tp9PrA4dp9ILmKKRrlnPfKLhJGUffJNdoSmd_2Bb5eqU9Wr_25uMlYncVp2FZjZuHhfh3rxECmVhbE5kctnyH95DzqyF5qr2q0qIlOL26p-74jX_uLLSqcapbq6MFit1Q9AIwoJtCZwMuwKZMRZOlCvSmoM7uQ1pBFOdXAidc43-XsA5_XJoFyw-a5YJHYzD1UKNxSJRov3kZEOvTFKn3NAVbRPZ_3ZETgKQFNQeFgSUi8hhwH9K2tUWtP-lJibQBGzE4DsyYNbSeBCZgoFlBjEMt2n2uDCwHD-F13Bb3UlgCy33zosPZ2rmNczF3pmLFeMr7c2z0gQ9p38zmqUWp47ww5nXaUrdazJXjgX7U4OZjUxSYvOJmNmmToZ6DAPAy0bD8z-jpIbL9I0RiqVMTu5igpfFdoMmdIOgm3fBqKShxAoBZdIxCcOE5nW82XIduiC2hi3zhAsjlx_tMV1R6e8eo4Ni8Rn7Kltk6Hb46DNQ=w348-h260-p-k-nu-ft);
  background-size: cover;
  clip-path: polygon(0 0, 41% 0, 16% 100%, 0% 100%);
  
}

.container .clip.clip2
{
  background: url(https://lh3.googleusercontent.com/fife/ABSRlIqMrUO7xKs1X0lDT5BEAEYWYb_kutWBDncW_G15XaHwcCxJheWFijmF5qE8rObIro6iazxzQxXxxfjKzBrBv-2jDcXImbpiRLyK4JXpCiVbNCoQl7v54VN39N0ieDkeOL0FDepibEPQIE_eHc0mgEFL6mQ_WKlbd_pgt6mZj2wS4E0h57XkHi3FYFrOS5g9i7TktuRBDadw9NCKI--bmM2lKgTWvOk6Jh-gVlHO3OJSPqIL5qEfu_4AtQVHpqOY1f8xqNgcJ2OHQ_uvOnBr1PODmlmxdffEflgQKCJ3pse0lyYbEdDQYr96_WqYI1f8HUm5myCSnxFd4Ff8aB3sGuQ-KFtU1gIGZWzScLcmMzUCBKTWDvK1-EWlxv64kPRZtJmSmUbdaEsuo4s9GCoWHZPSOyvhhZcyPpE9-uiGXnLZWGupM3NGlumkkQvIAjjiIGvE5JlbL29ZP9UoA-55cZ9PmcxzLzr-Pcqqv99KIi5EbVncZKD9GZtoLme3sv7-4v0Jgit3N7MtRHBSTpvYw66dLMf8dBt60jTww6_drTQLLF6-dTZakttrOoVYUhLB9jWIMN7Sxkbo9cG2MnBvOK0YarlayDcIbbLnafs5AmOdG1a6_J9D2Hy459bdCc4OQZA0ynHhO6LlIvGUISY3HMN8nGQ29bdrWnUMaCIN7UIQfETj2TzHoDn2lzms6lAX4sjGx5o-F40n7C5_bkLLCOWdWdrA68D1rg=w348-h260-p-k-nu-ft);
  background-size: cover;
  clip-path: polygon(100% 0, 41% 0, 16% 100%, 51% 100%);
}

.container .clip.clip3
{
  background: url(https://images.pexels.com/photos/177598/pexels-photo-177598.jpeg?cs=srgb&dl=pexels-markus-spiske-177598.jpg&fm=jpg);
  background-size: cover;
  clip-path: polygon(100% 0, 100%  0, 100% 100%, 51% 100%);
  
}

.container:hover .clip
{
  clip-path:  polygon(100% 0, 100% 0, 100% 100%, 100% 100%);
}


.container .clip:hover
{
 
  clip-path: polygon(100% 0, 0 0, 0 100%, 100% 100%);
  
}

.container .clip.content
{
  position: absolute;
  bottom: 0;
  left: 0;
  width: 70%;
  padding: 20px;
  opacity: 0;
  background: #FFF;
  transition: 0.5%;
  
}

.container .clip:hover.content
{
  bottom: 0;
  opacity: 1%;
}


