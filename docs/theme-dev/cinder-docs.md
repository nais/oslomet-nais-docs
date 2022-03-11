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
    language: fr //set the language to french
```
!!! Warning
    Language tag is not validated so verify that provided tag is correct. Otherwise the html lang attribute will be invalid. 

!!! Warning
    Currently the static labels are hardcoded and will not follow set language. Words such as "next", "previous", "search" will appear in english regardles of the set html lang tag. This is invalid

If no language is specified in config file, english as default language will be set.

## Navigation
New type of navigation is created for documentation. The way it works is simply to print out only path to currently active section. 


### Section urls:
What is special about it is that the sections leads to the first page item they are parent of. This is simply because mkdocs does not have anything to display for given section. Section is basicly folder that contains pages while only pages can be shown. Therefore by clicking on section, first page that is assosiated with the section will be show. 

example:
```
//Here "Products" will lead to "Apple"
Products
    Fruits
        Apple
        Banana
        Orange
```

This allows to create "stepped" navigation as the user gradually works his way to desired content. Firstly the user press on the section that he is interested in. Then he will be moved to the first page of that section. If there is more nested sections, the steps repeats untill the user hopefull finds what he is looking for

Simular navigation works on bootstrap documentation 

### Critisism
I believe that this may not be the best way to create navigation. The main problem here is that the user is acutally redirected to given section, something he may not realize. It will also render many website changes, something that may be overkill espesially when the user is just moving around. Blind users may become lost with these site changes.

### Why use it then?
- Bootstrap uses it, so it not obsolete
- WAI.org also uses it 
- No need for dropdows, someting that is difficult to create correctly in modded bootstrap or bootstap (from my experience)
- We may change it 

### Remember
If we actually decide to go for this navigation, there is optimizing to do. 

Also the recrusion method that find the first child/page of a section need secruing, it will most likely fail if section does not contain any page, only links. 