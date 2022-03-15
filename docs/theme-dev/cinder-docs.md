---
description: Cinder modification documentation
---

# Documentation for Cinder changes
Cinder is the theme you are currently seeing. As other themes for mkdocs, it does have its own [documentation](https://sourcefoundry.org/cinder/). However we intend to modify this theme and therefore the changes will be documented here.

## Favicon
In order to use custom favicon use following mkdocs config file entry:
```
theme: 
    favicon: path/to/icon
```
If no favicon is specified in config file, default icon located under `cinder/img/favicon.ico` will be used instead. It is also possible to substitute this file to achieve the same goal. 

## Logo
In order to use custom logo on navigation bar use following mkdocs config file entry:
```
theme: 
    logo: path/to/logo
```
If no logo is specified in config file, name of the website (specified by the `site_name` attribute) will be shown instead. 

## HTML lang attribute 
It is possbile to specify the html lang attribute (that defnies the content language) in mkdocs config file. This is done by following entry:
```
theme: 
    locale: fr //set the language to french
```
!!! note
    This functionality is implemented according to mkdocs guide. More info about mkdocs locales refer to its [documentation](https://www.mkdocs.org/dev-guide/themes/#supporting-theme-localizationtranslation)

## Navigation
New type of navigation has been implemented for this theme/this documentation. I like to call it "partial menu" however i do not know the correct term for this kind of navigation. The way it works is simply by just rendering content of currently active sections. That way other sections that are not relevant are not expanded by default. This creates tradeof between compactness and openness as amount of entries are limited. This somewhat simulates the expand/hide sections functionality, but without css and js. 

### Section urls:
Navigation items such as sections now lead to their first child. By default sections does not have any url assiosiated with them as they simply are not an "endpoint". At the same time in order to be able to choose given section (so they become active), they have to lead somewhere. Therefore they now contain an link that leads to their first nav item that can be displayed.

example:
```
//Here "Products" item will lead to "Apple" item
Products
    Fruits
        Apple
        Banana
        Orange
```

Implementation of section urls works by finding recursively first nav item that is not a section. This ensures that script does not break if page is contained inside more nested sections. 
 



