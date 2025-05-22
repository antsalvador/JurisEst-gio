# Interviews with STJ employees

Summary of the the meetings with different employees of STJ on the 14th of May with the Library team and 15th of May with STJ judges. 


The first interview conducted was with the Librarian team at STJ led by André Capricho. They are responsible for creating new case rulings assigned by the STJ and of editing the existing case rulings that are viewed on Juris.

The way they receive the case rulings to be created is through email in a picture of the form the Courts use that contains all the case rulings metada and summary in the email itself. 

The most signficant discovery from the interview is that the librarians pretty much do not use Juris, the entire team dislikes it and finds its current version unpratical and not intuitive for various reasons.
Instead the team currently uses IBM's Lotus Notes for creating and editing the case rulings and DGDSI (the database Juris fetches from) and ECLI (European Case Law Identifier) to search for the existing case rulings in detriment to Juris because of better UI and features. 

In the meeting we had the opportunity to visualize all these tools, compare them to Juris and discuss what causes the team not to use it. 

# These are the biggest takeways:
 



## Search Functionality

In Juris only 10 case rulings appear in the search page, this amount should be costumizable as many users prefer to be able to scroll down through all of the case rulings available as you can in DGSI and ECLI.

Implement a calendar feature to look up a specific date (feature already finished).

Need to implement partial name field search capability

Implement simple regex string search for older case rulings

Process number search needs Elastic Search implementation

Search should work even when terms are not in the correct order

Implement "AND" operator in term searches, possibly add "OR" operator

Search should find case rulings containing all specified terms and not only some as it does currently

The current order of the existing metadata fields is unpratical. This can be modified already by users but some of the fields are found to be useless for both the librarians and judges and others for just one of them like "Área".

### Ideal Metadata Field Order

Número de acordão 
Secção 
Data 
Relator 
Meio Processual

### Useless Fields

Votaçãom
Área (Useful for Judges)
Meio processual (Important for the librarians useless for the judges)
Jurisprudencia
Decisao
Fonte
Estado

### Case Ruling Display
There was also a lot of feedback regarding case ruling display,

For each case ruling, show in small format:
- Number
- Date
- Reporter
- Summary
- Section
- Descriptors

## Backoffice Improvements

Juris currently duplicates a case ruling once it is edited, this is a major bug to be fixed that compromises data normalization.

Too many fields in the backoffice editing interface, make it more simple

Add suggestiongs to the text boxes for the metadata filter editing

Too many descriptors, too much information

Lotus Notes doesn't update all records

"Area" field is redundant as "Section" handles everything automatically


## UI/UX Improvements

Increase text size and shorten the width of the case ruling display as it's difficult to read case rulings due to small text and ver long sentences, compare it to ECLI who does it best 

Show fewer case rulings in demonstration but always keep summary open. Summary is the most important element, followed by section and descriptors
- Decision is not important for search purposes
- Descriptors are of little interest for search



## Additional Features
- Statistics dashboard would be very interesting
- For search purposes, old descriptors should neither be marked nor completely removed
- For creation, only use current descriptors, not the complete list







lotus n atualiza todos
area nao faz sentido, seccao faz tudo automaticamente

as 3 intruduçoes nao faz sentido, meter tudo num e fazer a produção no background

numero convencional nao está presente

copiar a ordem de descritor
isto sao as notas da reuniao, pouco organizadas mas pronto fica registado ao menos




aumentar ligeiramente o texto porque se sente dificuldade a ler acordãos por o texto ser pequeno

ter menos acordaos em demonstração mas ter o sumário sempre aberto

decisao nao é importante para pesquisa, pouco interesse nos descritores tambem mas o sumário é o mais importante

pesquisa de acordãos que têm todos os termos em 
pesquisa mesmo sem ser na ordem certa
ter pelo menos um "and" em pesquisa de termos maybe usar um "not"

no nr do processo nao tem elastic search e isso é frustrante
na pesquisa procura de palavras nao completas nao está a ser encontrada, melhorar a pesquisa!!
pesquisa por data é importante

uteis:
seccao
descritores
area
