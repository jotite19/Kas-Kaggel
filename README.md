# Kas-Kaggel
## Resum
https://www.kaggle.com/miell534/gamespot-article-classification
La base de dades que procesare en aquesta entrega conte els articles (trobats en www.gamespot.com) sobre els millors i pitjors jocs fins l'any 2019. Aquests articles son reviews del joc i li otorgan la nota.

### Atributs:
Aquesta base te 12 atributs dels quals 4 son numerics la resta esta composta per 2 links, 3 categorics i 3 strings. Previ a cap analisis dels atributs descarto utilitzar els links per generar els meus models.

### Atributs numerics:
- ID: va del 0 al 1183 i cada joc en te un diferent no te altre utilitat que no sigui per identificar i iteratr les diferents files de la base de dades.
- score: determina la puntuacio que un joc te, aquesta te un domini entre 1.6 i 10 pero com es pot observar en el historigrama presentat mes a baix hi ha un absencia de mostres desde el 4,9 fins al 8,3. Aixo prove del fet que la base de dades nomes te els jocs amb les puntuacions mes altes i baixes, aixi que els que es troben en el mitj no tenen entrades.
- Polarity i Subjectivity: son els dos atributs numerics restants i son valors generats amb TextBlob (llibreria externa de tractament de textos) a partir de l'article del joc en questio. Aquests estan el la base de dades amb el proposit de predir la score, en el codi sobministrat per el creador de la base de dades s'explica breument com s'extreuen.

### Altres atributs:
- name: el nom del joc.
- tagline: el titol de l'article del joc.
- boxart: link a la imatge de la portada del joc (gran part dels links no funcionen)
- system: determina la plataforma en la que el joc va ser disponible primer. Aquest atribut esta compost per 723 consoles diferents aixi que es bastant inutilitzable a l'hora de fer models.
- link: el link a l'article, el creador de la base de dades l'utilitza per extreuren l'article utilitzant BeautifulSoup.
- classifier: atribut que prove de la score del joc, si aquest es troba en el grup amb score alta el valor es "pos" i respectivament amb els de score baixa i "neg". Aquest es molt util per entrenar models de clasificacio, com ara un model NaiveBayes.
- article i filtered article: l'article raw amb totes les paraules d'aquest i l'article filtrat mitjancant "stopwords" un recurs utilitzat per filtrar les paraules mes utilitzades i fer la execucio molt mes rapida.
### Objectius del dataset
Utilitzare el score com a atribut onjectiu ja que aquest es el que hem sembla mes relevant, mes a baix faig la observacio que el score i el classifier poden ser directament igualats aixi que en algun model l'objectiu es el classifier.
## Experiments
Durant aquesta pràctica hem realitzat diferents experiments.
### Preprocessat
Quines proves hem realitzat que tinguin a veure amb el pre-processat? com han afectat als resultats?
### Model

| Model | Mètrica |
| -- | -- |
| LinearRegresion | 50% |
| LogisticRegresion | 85% |
| LogisticRegrsion(PCA) | 85% |
| BayesClass(I) | 67% |
| BayesClass(II) | 77% |
| BayesClass(III) | 87% |

## Conclusions
El model mes eficaç que he conseguit es la Clasificacio de bayes que prediu la positivitat de l'article del joc mitjançant el tag line de aquest. Amb aquest model hi pot competir el regresor logistic que conseguia una acuracy de 85% nomes un 2% menys que el clasificador.
## Idees per treballar en un futur
Es podria intentar trobar hyperparametres que milloresin l'acuracy dels models logistics en lloc de optar per els clasificadors.
