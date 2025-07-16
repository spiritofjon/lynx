# Modified by spiritofjon
This theme has been personalized to my personal tastes. As such I recommend getting the original upstream version or at a minimum checking out the changes I've made by reading the commit logs.

* * *
* * *

# Lynx

Lynx is designed to be a simple links page powered by [Hugo](https://gohugo.io). It's built using Tailwind CSS and inspired by services like LinkTree.

🌏 [Demo site](https://jpanther.github.io/lynx/)
🐛 [Bug reports & issues](https://github.com/jpanther/lynx/issues)
💡 [Questions & feature requests](https://github.com/jpanther/lynx/discussions)

![Screenshot](https://raw.githubusercontent.com/jpanther/lynx/stable/images/screenshot.png)


## Features

- Fully responsive layout built with Tailwind CSS 3.0
- Dark mode (auto-switching based upon browser)
- SVG icons from FontAwesome 5
- HTML and Emoji support
- Fathom Analytics and Google Analytics support
- Favicons support

* * *

## Installation

Install Hugo and create a new site. See [the Hugo documentation](https://gohugo.io/getting-started/quick-start/) for details.


### Git Submodule

Add Lynx as git submodule:

    $ git submodule add https://github.com/spiritofjon/lynx.git themes/lynx

UPDATE:

    $ git submodule update --remote --merge


### Hugo module

Initialize your site as hugo module:

    $ hugo mod init github.com/USERNAME/SITENAME

Add Lynx module as a dependency of your site:

    $ hugo mod get github.com/spiritofjon/lynx


### Site preview

Copy the content of `exampleSite` at the root of your project:

    cp -r themes/lynx/exampleSite/* . -iv

If you installed Lynx as hugo module, set your theme in your config file (hugo.toml):

    [[module.imports]]
      path = "github.com/spiritofjon/lynx"

Start Hugo:

    hugo serve
    
* * *

## Configuration

The main theme configuration is managed in the `hugo.toml` file. Most parameters are self explanatory and the default config contains some basic examples.

The author name and image are displayed at the top of the page. Both are optional and will default to the site title with no image when not provided.

Links can either be a simple string containing the URL for the link, or an object that defines the link parameters. Links are displayed in the order provided in the config file.

Acceptable link parameters are:

- `href` = the URL the link should point to (required)
- `icon` = the name of the icon to use for this link
- `text` = the link text
- `target` = the target of the link (default: `_blank`)
- `title` = the HTML title of the link

```toml
[params.author]
links = {
   # Simple link
   { github = "https://github.com/jpanther/lynx" }

   # Custom link
   { github = { href = "https://github.com/jpanther/lynx", text = "GitHub Project" } }
}
```

Additional page content can be provided by creating a Markdown file at `content/_index.md`. The contents of this file will be displayed between the title and links. Check out the exampleSite to see this in practice.

Basic content pages can also be created by placing Markdown files in the `content` directory. These can then be linked to using links in the config file or through the homepage content.


### Adding custom icons and link styles

Lynx supports adding your own SVG icons and link styles to fully customise your links page. In the **root of your Hugo project**, simply create an `assets` folder and add your assets. Icons should be placed in an `icons` folder and any CSS should be in a file named `css/custom.css`.

The custom CSS file will automatically be included and minified when the site is built. The styles can be as creative as you wish and anything in your custom CSS will override the default theme.

If you need icons, you can find free SVG icons for many services at [FontAwesome](https://fontawesome.com/icons?d=gallery&p=2&s=brands).


#### Example

Let's make a custom link for FontAwesome using the FA flag as the link icon and a gradient background as the link style.

> If you prefer to inspect the code, the exampleSite contains a custom link to FontAwesome that demonstrates this process.

1. Place the SVG icon in the icons folder `/assets/icons/font-awesome.svg`.
2. Create the CSS file at `/assets/css/custom.css` and add in a rule to style the link:

   ```css
   .link-font-awesome {
     background: rgb(131, 58, 180);
     background: linear-gradient(
       90deg,
       rgba(131, 58, 180, 1) 0%,
       rgba(253, 29, 29, 1) 50%,
       rgba(252, 176, 69, 1) 100%
     );
   }
   ```

   _Note: The CSS class name should be the icon name prefixed with `link-`._

3. Finally, in the `config.toml` file, create the link by referencing the new icon:

   ```toml
   font-awesome = { href = "https://fontawesome.com", text = "FontAwesome" }
   ```

When the site is rebuilt, the new custom link will appear.

* * *

## About

This is an adaptation of the Lynx theme [Lynx](https://https://github.com/jpanther/lynx/) by [James Panther](https://github.com/jpanther).
