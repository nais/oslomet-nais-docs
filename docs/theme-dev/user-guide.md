---
description: User guide for modified Cinder theme
---

# User guide

The theme you are currently seeing is modified version of [Cinder theme](https://sourcefoundry.org/cinder/) for MkDocs. Because it is modified, the orginal documentation is not fully relevant. Therefore any changes that needs to be documented, will be published here.

!!! warning
    Changes to this theme was not tested extensively, therefore there is possiblity that functionalites described here will not behave as expected.

## About plugin support
Cinder theme does not support all plugins and so does this modified theme. Adding support for plugins is not scope of this project. Therefore one must be satisified with limited list of supported plugins.

## Favicon
In order to use custom favicon use following `mkdocs.yml` file entry:
```
theme: 
    favicon: path/to/icon
```
If no favicon is specified in config file, default icon located under `cinder/img/favicon.ico` will be used instead. It is also possible to substitute this file to achieve the same goal. 

## Nav title section
Nav title section is the section that shows logo and title of the page on header. There are few customization options regarding this seciton we have implemented.

### Logo
In order to use custom logo on navigation bar use following `mkdocs.yml` file entry:

```
theme: 
    logo: path/to/logo
```
If no logo is specified in config file, only [site title](#site-title) will be shown.

### Site title
This is text that will show up next to the logo. It is possible (and advised) to use custom title for this element. This is because this element should be descriptive and tell the user what the pages are about. Therefore it is possible to customize this text by `site_title` attribute in mkdocs config file.

Specifing custom title:
```
theme:
    site_title: Documentation for my precious project.
```

If no `site_title` is specified in config file, `site_name` attribute will be used instead.

## Repo links 
Repo links has been changed, now link to repo is separate from edit links. Before, edit links has been overwritten by link to repo if they were specified. Now it is possible to have both, link to repo and edit link

### Repo link
Links to repo will show up on navigation bar. Appropriate icon is choosen based on keyword in repo url. This means that if `repo_url` in `mkdocs.yml` file contains `'github'`, then github icon will be shown beside. Currently only `'github'`, `'bitbucket'` and `'gitlab'` keywords are supported. If `repo_url` does not contain any of these keywords, then no icon will be shown.

Link text is determined by `repo_name` attribute in `mkdocs.yml`. If this attribute is not specified, then default keyword will be shown i.e 'GitHub'.

### Edit link
Edit link will be shown on top of content and it is controlled by `edit_uri` in `mkdocs.yml` ([about edit_uri in MkDocs](https://www.mkdocs.org/user-guide/configuration/#edit_uri)). This link text is agnostic to repo provider, which means that it will stay the same regardless if edit link is refering to Github, Gitlab etc.  

## HTML lang attribute 
It is possbile to specify the html lang attribute (that defnies the content language) in `mkdocs.yml` file. This is done by following entry:

```
theme: 
    locale: fr //set the language to french
```
!!! note
    This functionality is implemented according to mkdocs guide. More info about mkdocs locales refer to its documentation. [localization in MkDocs themes](https://www.mkdocs.org/dev-guide/themes/#supporting-theme-localizationtranslation)

## Position Sticky
Header and aside sections uses `position: sticky;` css rule to keep them attached in place. This rule however is not fully supported on all browser, therefore they will most likely scroll with the page content (this has not been tested). Such solution is best compromise between functionality and clean code.

## hljs (syntax highlighter)
"hljs" is syntax highlighter for code snippets and it is used by this theme.

### Color scheme
 There are dozen of different color schemes created for hljs that one can choose. On how to change color, refer to cinder's official documentation ([Cinder theme - Syntax Highlighting Color Scheme](https://sourcefoundry.org/cinder/#syntax-highlighting-color-scheme)). 

However, the default color scheme for this theme is a modified "StackOverflow Light" theme for hljs. The colors has been adjusted so the contrast ratio is above 7.1.
This is in order to meet WCAG requirements related to contrast. Therefore one should note that choosing different color scheme may not compile with WCAG regulations.

### Language detection
MkDocs allow to define language for code blocks using the standart makrdown syntax. This is done by writing given language after first 3 backticks, like so:
```` 
```java

public static void...

```
```` 
[Language definition for code snippets in MkDocs](https://www.mkdocs.org/user-guide/writing-your-docs/#fenced-code-blocks)

However this won't work for hljs as language definition is done via class name in `<code>` tags.

[Language definition in hljs](https://highlightjs.readthedocs.io/en/latest/readme.html#in-the-browser)

 In result hljs will still use auto detection even if language is defined in markdown. Therefore it is advised not to specify language in markdown as there is no use for it.

## Page meta-data
MkDocs supports meta-data for markdown files. You can read more about it on their official documentation. [page-metadata in MkDocs](https://www.mkdocs.org/user-guide/writing-your-docs/#meta-data). Cinder theme uses this feature to add support for printing out page sources. This feature however has been removed in this theme due to its unpopularity. There is lack of information regardles on how this feature should be and therefore it has been removed.



 



