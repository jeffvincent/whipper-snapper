# Whipper Snapper

This upstart is for building a blog on Jekyll, hosted on Heroku, using Unicorn. It includes support for HAML and Sass, and also Foundation, for being responsive. My live site is [http://jeffvincent.me](http://jeffvincent.me), and most of what I've got here is hodge-podge from other jekyll repos and things I've learned. 

I will do my absolute best to give credit where credit is due (pretty much everywhere).

Usage
-----

### Getting Started

After cloning, bundle install:

    $ gem install bundler
    $ bundle install

Open the `base.haml` layout and update the metadata tag with your name and content.  Good for SEO I suppose.

### Adding Content

I added a rake task for creating new posts

    $ rake np title="post title"

### Styling Changes

Custom changes belong in the `_sass/screen.sass` file.

### Compiling / Previewing Changes

Rake tasks exist for doing the two things I do most - preview changes, and deploy updates to github and heroku. 

* `rake preview` will compile haml-based layouts, sass->css, and generate the site. 
* `rake deploy` will push to github master and heroku master.

Languages/Framework Support
--------------------------

### HAML
The best way to design layouts is to use HAML. Jekyll doesn't have great built in support for HAML at this point, so I added a plugin for conversion (code is not my own, see file for source attribution). [http://haml.info/](http://haml.info/)

### Sass
I use Sass for pre-processing style - it's just so clean and powerful, you should use it too. [http://sass-lang.com/](http://sass-lang.com/)

### Compass
Compass is basically a group of mixins. Other developers are better than I am at cross-browser compatibility, so I use their mixins to keep my code really clean. [http://compass-style.org/](http://compass-style.org/)

### Foundation
Foundation is a responsive framework built by the folks at Zurb. I have taken the liberty of installing this by default. [http://foundation.zurb.com/](http://foundation.zurb.com/)

Structure
--------

    .
    |-- .gitignore
    |-- .rvrmc
    |-- Gemfile
    |-- Procfile
    |-- README
    |-- Rakefile
    |-- _config.yml  
    |-- _includes
    |-- _layouts  
    |   |-- haml
    |       `-- base.haml
    |       `-- post.haml
    |   |-- base.html
    |   `-- post.html
    |-- _plugins
    |   `-- haml_converter.rb
    |-- _posts  
    |   `-- 2012-07-02-test-post.md
    |-- _sass
    |   `-- _settings.sass
    |   `-- app.sass
    |   `-- screen.sass
    |-- config
    |   `-- unicorn.rb
    `-- config.rb
    `-- config.ru
    |-- images
    |    `-- all_your_base.png  
    `-- index.html  
    |-- stylesheets
    |    `-- ie.css  
    |    `-- print.css  
    |    `-- screen.css 

There is probably more in there that anyone will need, but I wanted to be as helpful as possible. To keep in that vein, I'll try and go over them below.

Troubleshooting
--------------

I certainly had my share of problems/issues.  Jekyll has a pretty vibrant community of developers. I found the 'google this' approach answered most of my questions, and I included most of the best links in a document 'building_a_jekyll_site.md' that you can find in the base.

To-Do
-----

1. **Adding support for Sinatra?** So folks can use contact forms, etc.
2. **Update Deploy** Would like to use post-commit hooks through Github instead.
