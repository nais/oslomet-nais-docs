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