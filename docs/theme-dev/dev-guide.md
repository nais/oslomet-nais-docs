# Developer guide
This page is everyone that happens to continue our work. It does contain information that we would like you to know. Read it carefully as it may save you some trouble.

## Source code
Information about soucre code and source files.

### Css structure
Css for this theme is divided into 3 "levels", basicly there are 3 different stylesheet where one can provide changes. 
Those are: 

- cinder
- base/highlight
- bootstrap 

**cinder.css** - "local" changes that controlls cinder looks. So this is where i.e color of headers is set.

**base.css** - this is where extension to bootstrap are made, or definisions of sets i.e alerts styles

**highlight.css** - this is file that contains styles for hljs (code snippets syntax highlighter). In terms of level, this one is equal with base.

**bootstrap.css** - bootstrap file that provides backbone. 

It has been this way since orginal cinder theme. You can alter it as you like, but we did not see the reason to do it.

### *img* directory
There are some images of grid, they looks useless, but removing them causes MkDocs to fail. One could investigate on what is the deal with them. They are not acutally used by the theme itself.

### Local version notifier
During our development sprint, we found need for indication of local version. This is because we used back to back local version (served by `mkdocs serve` command) and version hosted through github repo. To avoid confusion between these two (which were identical) we decided to mark one of them which in this case was the local version.

What it does is basicly printing a message (in this case on navbar) only when the address of the page is a local address. It does print a message that consist of information "This is local version" and a number which is nothing else than UNIX epoch. The reason behind the number is to be able to distinguish between reloads and because it looks cooler 😎. Another functionality is the ability for the message to be removed when clicked. This becomes helpful when the message is in the way and have to be deleted.

This notifier however has been excluded from the final version source code to avoid unessecary code that could lead to problems. If this is something you thing is cool and want it back, here it is:

It consist of two parts, one jinja if-statement and one javascript code. 

- jinja if-statement:
```html
<!--
    technically you can put this if-statement wherever you want.
    We recomend though to put this on navbar, 
    if using bootstrap place it inside <header><nav>...</nav></header> in 'header.html'
-->

{% if '127.0.0.1' in page.canonical_url %}
    <!-- 
        '127.0.0.1' defines the local address on which mkdocs is serving the local version,
         if it is different for you, then change it
    -->
    <div id="local-version-notice" class="text-warning" role="alert">
        message
    </div>
{% endif %}
```

- javascript:
```js
//put this in javascript where it will be executed automaticly, i.e jquery $(document).ready(function() {}

const $local_version_notice = $('#local-version-notice');

$('#local-version-notice').text("This is local version nr. "+Date.now());

$local_version_notice.on("click", function () {
    this.remove();
});
```

## Known bugs
Things that we found not working, but you can maybe fix

- headers defined as `<summary>` inside `<details>` when hidden will show up on table of content, but they are inaccessible meaning that page will not scroll to them when directed to by table of content or permalink

- tabbed sections are not supported by cinder theme, but are used by this documentation. However this is more incompatibility issure rather than bug and therefore it should not be considered as one. 


## Recomendations
Insight into currently problematic areas and what we recomend to do about them.

### Use of position sticky
Generally, position sticky rule is tricky. It make it easier to make content stay while scrolling, but it also creates tricky behaviour. Basicly if content A is nested in content B and content A and B is longer than viewport, then in order to scroll through whole content A, you have to scroll through whole content B. This result in situation where the end of content A will be shown at the bottom of content B. We wouldn't say this behaviour is very accessibility friendly, but in this case this is the best solution we have. We cannot use postion fixed as this goes against bootstrap (you have to redo breakpoints). At the same time, we assume that having aside content scroll with the page will be more frustating than position sticky.

Use of position sticky is dictated by use of bootstrap (or maybe you find a way). Therefore this is also reason why switching off of bootstrap should be considered.

### Bootstrap
Bootstrap is usefull as styling of a webpage is faster, but it is also problematic. The main problem with bootstrap is that it is constraining. Creating new elements/layouts that are not native for bootstrap becomes nightmare as you effectively go against bootstrap and have to overrite its rules. At the same time, bootstrap does not have implementation of everything that one can imagine. Therefore you are forced to create them yourself, but you have limited controll on what you can do and can not. 

In this project, most problematic elements are side menu and layout breakpoints. Bootstrap does not have implementation of endless nested side menu that would be WCAG compilant. Grid system is also problematic as the column breakpoints are not optimal. They occur in positions that makes some elements too narrow or too wide.

Limitations of bootstrap also impacts implemetation choices for some functions. This is mainly search functionality, it had to become a modal that is opened by a button instead of a search input with a dropdown where results are printed. Not optimal position sticky rule also had to be used instead of position fixed rule. 

We believe that in order for this project to become better, a migration from bootstrap to custom css is needed. This way one could create layout and style that is more suitable for WCAG. This however will be more time consuming compared to use of bootstrap.