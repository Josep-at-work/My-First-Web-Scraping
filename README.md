# Scrapping University Researchers

As a project from my Master's in Big Data Analysis I've performed my first solo web scraping. The task consisted on extracting specific information on the university's members of the different research groups. [Universitat de les Illes Balears](https://www.uib.es/es/), *aka* UIB.

## Aim:
+ Identification and extraction of the researchers' information:
    + **Name**
    + **Gender** 
    + **Researcher Level**
    + **University Relationship**(Role)
    + **Title**
    + **CV**
    + **Research Group**

### Part 1

The researcher's information is available [here](https://www.uib.eu/research/groups/). The *All* cateogory displays all the research groups in a easier format so the scraping will start at:
  + [url_en](https://www.uib.eu/research/groups/grups_area/id_area=-1%2526npag=1) english version.
  + [url_cat](https://www.uib.cat/recerca/estructures/grups/grups_area/id_area=-1%2526npag=1) catalan version.
  + [url_sp](https://www.uib.es/es/recerca/estructures/grups/grups_area/id_area=-1) spanish version.


Then the first section consists of two parts: 
  1. Getting into an specific research group's web page and find the list of members.
  2. Identify when there are no more pages listing the departments to stop the scrapping.
  
### Part 2
 
Inside the research team's main page, the researchers are divided in 3 levels: 
 + **Main Resercher**. Usually just one high level researcher.
 + **Members**. Many mid-high level researchers
 + **Collaboratos**. Many reserchers with distinct professional levels.

The second part consists of identifying the following information from each member:
 + Name
 + Gender
 + Category of researcher in the team
 + Role at the univeristy (University Relationship)
 + Title

### Part 3

The last scraped data is a summary of the researcher's *curriculum vitae*. Some members don't have a personal university web page, hence there won't be any cv extraction in those cases. Moreover, not all researchers have their *cv* in all languages, so depending on the language some *cv* will be missing to. 

### Ensambling

At the end of the notebook the functions and procedures defined in the previous sections are merged together in order to complete the process of scraping all researchers data. 

The language of scrapping can be modifyed by replacing the initial url by the corresponding with the desired language. This project has been done with the catalan version of the web page in order to be able to identify the researchers gender, in spanish could be known too. 

For non-catalan or spanish speakers, note that the female version of the personal title is like the male's one, adding an *a* at the end. Eg: Dr./Dra., Sr./Sra. Hence the gender of the researcher can be easily identifyed. 

### Result

One researcher in Panda's dataframe format:

|      | name                    | gender   | reasearch_level   | uni_relation        | title   | cv   | research group                                           |
|-----:|:------------------------|:---------|:------------------|:--------------------|:--------|:-----|:---------------------------------------------------------|
| 2645 | Víctor Fernández Juárez | M        | Col·laboradors    | Tècnic especialista | Sr.     |      | Unitat de Gràfics i Visió per Ordinador i IA (UGiVpOeIA) |


#### Disclaimer: 

All the data has been scraped from the UIB's [R&D&I](https://www.uib.eu/research/groups/grups_area/id_area=-1&npag=1) web page which is public data. [Right of acces to public information](https://transparencia.uib.cat/Acces-a-la-informacio-publica/Dret-dacces-a-la-informacio-publica/). 
