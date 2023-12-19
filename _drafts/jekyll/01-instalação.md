

In this post we will see how to install and start using Jekyll.

#### Table of Contents

<ul class="topics">
<li><a href="#what_jekyll_is">What is Jekyll</a></li>
<li><a href="#setting-up-the-environment">Setting up the environment</a></li>
<li><a href="#commands">Commands and starting a project</a></li>
</ul>

<h2 id="what_jekyll_is">What Jekyll is?</h2>

Jekyll is a static site generator that give us the ability to create a static website by using dynamic content like templates, partials, liquid code and more.

It is blog aware, meaning that we can build a blog using it.

Jekyll is what GitHub Pages uses to deliver pages. If you are going to host your page on GitHub building your website with Jekyll is the best option.

<a href="https://jekyllrb.com/" target="_blank">jekyllrb.com</a>

A static site generator is a tool that receives a predefined template and a markup to generate a HTML file that does not have changes by database dynamically by a language.

The advantages of using a static generator are its:
- simplicity: you will not need to write the entire HTML for each page, we can use one file (template) as the header and link it to the other pages that you want to use the same header.
- Do not uses database: we do not need to make a request to search for the content of the page. In this way the site can be considered faster than the ones that uses database.
- Any server supports static files.

<h2 id="setting-up-the-environment">Setting up the environment</h2>

Jekyll requires some prerequisites to work on your machine. You can see them at <a href="https://jekyllrb.com/docs/installation/" target="_blank">https://jekyllrb.com/docs/installation/</a>.

For Windows I like the <a href="https://jekyll-windows.juthilo.com/" target="_blank">https://jekyll-windows.juthilo.com/</a> tutorial's on how to install it. But you can simply follow the guide lines from Jekyll website: <a href="https://jekyllrb.com/docs/installation/#guides" target="_blank">https://jekyllrb.com/docs/installation/#guides</a>.

After having Ruby installed we can install Jekyll by running in the command line:

```cmd
gem install jekyll bundler
```

To check your jekyll version run: `jekyll -v`.


<h2 id="commands">Commands and starting a project</h2>

Here is a list of useful commands we will us when working with Jekyll:

- List of commands we can use: `jekyll help`

```cmd
jekyll 4.3.2 -- Jekyll is a blog-aware, static site generator in Ruby

Usage:

  jekyll <subcommand> [options]
  
Options:

    -s, --source [DIR]  Source directory (defaults to ./)
    -d, --destination [DIR]  Destination directory (defaults to ./_site)
        --safe         Safe mode (defaults to false)
    -p, --plugins PLUGINS_DIR1[,PLUGINS_DIR2[,...]]  Plugins directory (defaults to ./_plugins)
        --layouts DIR  Layouts directory (defaults to ./_layouts)
        --profile      Generate a Liquid rendering profile
    -h, --help         Show this message
    -v, --version      Print the name and version
    -t, --trace        Show the full backtrace when an error occurs
    
Subcommands:
  compose
  docs
  import
  build, b              Build your site
  clean                 Clean the site (removes site output and metadata file) without building.
  doctor, hyde          Search site and print specific deprecation warnings
  help                  Show the help message, optionally for a given subcommand.
  new                   Creates a new Jekyll site scaffold in PATH
  new-theme             Creates a new Jekyll theme scaffold
  serve, server, s      Serve your site locally  
```

- Import a website/blog from WordPress, Behance... to Jekyll [<a href="https://import.jekyllrb.com/" target="_blank">https://import.jekyllrb.com/</a>]: `jekyll import <params>`
- Create your site: `bundle exec jekyll build`
- Create a new project with the default jekyll theme: `jekyll new <blog/site name>`
- Create a new theme: `jekyll new-theme <theme name>`
- Create a local server to see your project at http://localhost:4000: `bundle exec jekyll serve`

To start a project open a cmd where you want the project to be created and run `jekyll new <blog/site name>`, change `<blog/site name>` with the name of your project.

> e.g.: `jekyll new Nolukai`

Wait for the bundler to be installed and you will be all set to start working on your site/blog.