# Accessible documentation project
There is need for WCAG (Web Content Accessibility Guidelines) compilant documentation, but currently there is no well defined solution.
At the same time, this documentation has been created using MkDocs, a static page generator. MkDocs uses themes that determines how the pages looks and behave. Therefore themes are also a way to alter how the page will be. However currently there is no theme that focuses on WCAG compilance. Therefore the goal of this project is to create such. 

Prototype of WCAG compliant Mkdocs theme is developed. It is based on exisitng MkDocs theme ([Cinder theme for MkDocs](https://sourcefoundry.org/cinder/)) that has been modified.

## Documentation for this project
Relevant documentation for this project exist under section "theme-dev" (this/current section). Beside this page, it does consist of some additional pages such as:

- *User guide* - contains relevant information for users of this project's prototype. 
- *Developer guide* - contains relevant information regardless developing this projects's prototype. 
- *Sandbox* - is testing area for this project. 

!!! note
    this documentation has nothing to do with the orginal nais documentation. Scope of this documentation is only the modification of the theme.

## Next to do in this project
Here is a list that touches on topics that currently are missing, but are needed. Order of items in this list does reflect our order of execution, but one should note that some items may have higher piority than others.

!!! note
    If you are about to further develop this theme, make sure to read the developer guide and make yourself familiar with our recomendations.
    [Our developer guide](dev-guide)

- **current solution needs to be tested further** - No proper testing beside simple checks such as Windows narrator, contrast checker and/or manuall testing with keyboard has been peformed. This is mostly due to difficulty/trickyness of proper WCAG testing. Therefore it would be nice to actually test it so one can make sure that current solution works as intended.

- **text alternatives for non-text content** - Currently not all non-text elementes does have text alternatives. Some images/figues does not have any alternative text specified, see [Introduction to Nais](../README.md). [WCAG 1.1.1 - Non-text content](https://www.w3.org/TR/WCAG21/#non-text-content) specifies rule that non-text elements should have a text alternative. This either has to be done manualy by the content author or develop a solution that will specify these automatically.

- **markdown of main content needs to be WCAG compliant** - For the most part, the main content is WCAG compliant as it is rendered using standard html tags. However in case of custom elements such as admonitions, it is not given that these elements fullfill these guidelines.

    Note that modifying the way main content is rendered will require developing MkDocs plugins.

- **mechanisms to make textual content accessible needs to be developed/implemented** - [WCAG 3.1 - Readable](https://www.w3.org/TR/WCAG21/#readable) section focuses on text content where diverse sophisticated mechanisms needs to be implemented. Because these will require marking text sections on markdown level, creating new syntaxes in markup language and rendering them accordingly will probably be required. Therefore creating MkDocs plugins will be necessary.

- **mechanism for localization, it should be possible to change/translate gui to other languages** - [WCAG 3.1.1 - Language of page](https://www.w3.org/TR/WCAG21/#language-of-page) section states that human language of a page needs to be defined. Currently this functionality is implemented through html lang tag, see [user guide - HTML lang attribute](user-guide/#html-lang-attribute). However if content language other than english is desired, no mechanism to translate/change text labels exist. Labels such as "next page, search" will stay in english even if content language is different. This is against WCAG and therefore function to change/translate labels is needed.

    More information about theme localization in MkDocs: [Supporting theme Localization/Translation in MkDocs](https://www.mkdocs.org/dev-guide/themes/#supporting-theme-localizationtranslation)

- **shortcuts functionality needs to comply WCAG or otherwise be removed** - [WCAG 2.1.4 - Character Key Shortcuts](https://www.w3.org/TR/WCAG21/#character-key-shortcuts) section specifies a rule that shortcut functionality needs to obey. Current implementation does not obey this rule which makes it against WCAG. Other solution is to remove shorcuts, but one has to make sure it is a better choice.

- **headers links/permament links** 
    - These links should be described (i.e aria label) as what they are/ what they do. Currently the narrator will just read them as link/the symbol (#, §, etc.). This however will require modifing/creating MkDocs plugin as they are embeded in main content. 

    - Learn more about what the symbol of permament links should be and use it. Different websites uses different ones such as; "#", "§", "¶" which is not ideal. Maybe custom symbol should be created?

- **some figures/images are not "visible" to everyone** - Images of figures such as for example mind maps, tables or/and flow charts can not be explained equally good just by an alternative text. Therefore one should create such content to be interactive. Technicaly there is no such guideline, the closes one is [WCAG 1.4.9 - images of text](https://www.w3.org/TR/WCAG21/#images-of-text-no-exception) however we would imagine this can be a problem. Therefore one could research this topic further. 

- **\+ considerations from** [our recomentations section](dev-guide/#recomendations)
