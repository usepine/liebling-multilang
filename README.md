# Liebling Multilang

Liebling Multilang is a fork of the [Liebling](https://github.com/eddiesigner/liebling/) Ghost theme,
which refactors it to support multiple languages in a single Ghost website.

Currently supported languages:

* 🇺🇸 English
* 🇫🇷 Français

## Preview

You can see a live demo here: <https://lieblingdemo.i.usepine.com>

Here is a blog post that outlines what goes into creating multi-language Ghost themes:

- https://www.usepine.com/blog/en/creating-a-multi-language-theme/

## How to use?

Multi-language support is achieved by systematic tagging and custom routes/redirects.

### Set up routes and redirects

You need to set up custom collection routes,
which filter on the language tag (e.g. `hash-en` or `hash-fr` etc.)

```
collections:
  /en/:
    permalink: /en/{slug}/
    template: index-en
    filter: 'tag:hash-en'
  /fr/:
    permalink: /fr/{slug}/
    template: index-fr
    filter: 'tag:hash-fr'

taxonomies:
  tag: /tag/{slug}/
  author: /author/{slug}/
```

Then set up a redirect from the root to the default language:

```
[{
  "from":"^/","to":"/en","permanent":true
}]
```

Alternatively, if you use Netlify, you can use [language-based redirects](https://docs.netlify.com/routing/redirects/redirect-options/#redirect-by-country-or-language).


### Tagging

- Posts and Pages
  - tag English language posts with `#en`
  - tag French language posts with `#fr`
  - to enable language switching for specific posts, the first tag on every post is used as a "post identifier" tag. This means:
    - multiple posts which have the same content (but in different languages) should always have
    the same first tag (it should be an internal tag so it does not show up in tag lists)
    - two posts which do not have the same content, should always have different first tags
    - for example, two posts might have tags `#post-1 #en` and `#post-1 #fr`. These posts will show up
      in the English and French sections respectively, and allow language switching. If another post is
      written, which is unrelated, its tag list should begin with `#post-2 ...`
    - the actual naming scheme of the first tag does not matter (it can be `#post-1` or `#20210101-01-v1` or `#nuclear-powerplant-design-dissection`)
- Navigation
  - **do not use the built-in Ghost navigation page** (it is not used because it
    does not support localization)
  - instead, create Pages that are tagged with:
    - `#en-nav` (for English primary navigation)
    - `#en-nav2` (for English secondary navigation)
    - `#fr-nav` (for French primary navigation)
    - `#fr-nav2` (for French secondary navigation)

## Limitations

- unlike the original [Liebling](https://github.com/eddiesigner/liebling/) theme, the *Recommended posts*
  section performs post lookup by author, instead of by similar tags. This is because the language tag
  gets included as well, which leads to every post in the same language being returned.
- the author and tag pages default to English

## Features

This theme supports the same features as the original [Liebling](https://github.com/eddiesigner/liebling/) theme.

### Supported languages

* 🇺🇸 English
* 🇫🇷 Français

### General features

* Clean and beautiful design 💅🏼
* Lightning fast ⚡️
* Fully responsive, looks great on any device 📱
* Compatible with modern browsers 💻
* Fast support 📞

### Ghost features

* Subscription form [more info here](https://github.com/eddiesigner/liebling/wiki/How-to-enable-subscribers)
* Multiple authors
* Logo support
* Secondary menu
* Featured posts and pages
* Post, Page, Tag, Authors, pages
* Koenig editor
* Bookmark card
* Gallery card
* Blog title and description
* Cover image for Home, Post, Page, Tag, Author pages
* Author avatar, bio, location, website and social links
* Facebook and Twitter social links
* Reading time
* Next and Previous post navigation
* Primary tag in posts

### Liebling unique features

* Dark mode
* Search
* Custom Subscribe page
* Custom authors page
* Custom error page
* Medium style image zoom
* Comments with Disqus
* Share post on Facebook and Twitter
* Slider for featured posts
* Support for normal, wide and full images in posts
* Reading progress indicator
* RTL language support

## Credits and Related

* [Liebling](https://github.com/eddiesigner/liebling) - the Ghost theme that was used as the basis for this multi language theme.

* [Pine](https://www.usepine.com) - an easy to use Ghost hosting provider.

## License

Released under the [MIT license](LICENSE) like the original theme.
