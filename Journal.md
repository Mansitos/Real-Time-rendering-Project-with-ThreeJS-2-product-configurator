# Journal
## Product Configuration - Interactive 3D Graphics
## Andrea Mansi UNIUD 2020

---

---
#### Giorno 1: 07/2/2020

- Scelta della tipologia di prodotto
- Specifica dei requisiti
- Pianificazione del progetto (stesura di una prima bozza di roadmap, contenente le fasi principale per completare il progetto.)

REQUISITI [ver 1]

| ID | Requisiti principali |
| :---:        |    :----:   
| 1 | La pagina web deve  visualizzare un oggetto 3D composto da diversi materiali|
| 2 | L'utente deve poter ruotare l'oggetto o la visuale |
| 3 | L'utente deve poter selezionare di quale materiale deve essere composta una specifica parte dell'oggetto |
| 3A | deve quindi poter selezionare la parte su cui agire |
| 3B | deve quindi poter selezionare il nuovo materiale |
| 4  | il sistema deve garantire buone performance su dispositivi mobili |



ROADMAP [ver 1]
| n° | Task | Priorità|
| :---:        |    :----:   | :---: |
| 1 |Modellazione di un prodotto composto da più parti da usare come test per le fasi successive.| Principale |
| 2 |Implementazione di un sistema che permetta di cambiare agevolmente il materiale di una determinata parte del prodotto. |Principale |
| 3 |Implementazione di una GUI che permetta di interagire con il codice a run-time.|Principale |
| 4 |Ideazione del sistema di illuminazione|Principale |
| 5 |Ideazione di vari materiali per configurare il prodotto |Principale |
| 6 |Modellazione del prodotto finale |Principale |
| 7 |Integrazione del sistema finale: luci, prodotto, GUI etc. |Principale |
| 8 |Creazione di un sito web e-commerce|Principale|
| 9 |Sistema per il controllo delle luci | Opzionale |

### Lavoro svolto:

- Scelta del prodotto finale
- Scelta del software di modellazione e successiva creazione di un primo modello composto da 2 mesh come punto di partenza.
  - software scelto: Blender
- Strutturazione del codice iniziale, importazione del modello tramite GLTF.loader e prime sperimentazioni con l'assegnazione/cambiamento del materiale dei vari mesh

Primo modello di test

![ModelloDiTest](images/journal/img1.png)

Funzione di assegnazione di un nuovo materiale a una specifica parte del modello:

![Funzione1](images/journal/img2.png)

Funzione per creare dinamicamente nuovi materiali una volta selezionati vertex e fragment shaders:

![Funzione2](images/journal/img3.png)


---
---
#### Giorno 2: 08/02/2020

### Lavoro svolto:
- Implementazione BRDF Lambertiana + Microfacets
- Modellazione del primo prototipo di modello
- Primi test di rendering

Immagini del primo modello:

![PrimoModello](images/journal/img4.png)
![PrimoRender](images/journal/img5.png)

Immagine del primo test di rendering (plastica opaca e lucida):

![Cubemap](images/journal/img6.png)


---
---
#### Giorno 3: 10/02/2020

### Lavoro svolto:
- Aggiunta di una cubemap

![Cubemap](/textures/cubemap/StandardCubeMap.png)

- Implementazione della prima GUI per interagire con l'oggetto tramite la liberaria di THREE.JS

![PrimaGUI](images/journal/img7.png)

- Implementato un sistema che interagisce con la GUI e cambia a run-time le modifiche dell'utente sui materiali


- Pulizia del codice
  
---
---
#### Giorno 4: 13/02/2020

### Lavoro svolto:
- Creazione del modello finale

![Modello Finale](images/journal/img8.png)

- Creazione di due nuovi materiali con la BRDF Lambertiana + Microfacet: Oro e Alluminio
- Implementazione dello Shader (vertex+fragment) per riflettere la luce della cubemap ("glossy reflection shader")

![Glossy Reflection gold](images/journal/img9.png)

- Miglioramento della gui e refactoring del codice

---
---
#### Giorno 5: 15/02/2020

### Lavoro svolto:
- Modifica di alcune parti del modello, cause problemi con tangenti e normali in fase di fragment shading
- Aggiornamento della GUI e modifiche sparse sul codice
- Aggiunta del materiale Alluminio e Argento
- La GUI ora non viene istanziata con parametri di default ma coerenti con la configurazione iniziale del modello
- Implementata la possibilità di aggiungere una cubemap ai materiali che utilizzano lo shader glossy (si prevede di unire i due shader: glossy + lambert così da poter illuminare l'oggetto sia dalla cubemap che da eventuali luci aggiuntive.)
  

---
---
#### Giorno 6: 16/02/2020

### Lavoro svolto:
- Unito il comportamento dello shader glossy e quello lambertiano+microfacet:
  - Il risultato è uno shader che permette di illuminare l'oggetto con la cubemap, di passare una normalMap, inoltre permette di illuminare l'oggetto con ulteriori luci presenti sulla scena.
  Il risultato è osservabile nell'immagine sottostante.
    - (a) Shader glossy reflection from cubemap
    - (b) Riflessi speculari di 3 luci presenti nella scena
    - (c) La somma dei due risultati

![sum of shaders](images/journal/img10.png)

- Refactoring del codice e miglioramento dei materiali già presenti (ovvero: oro,alluminio,argento, 2 tipologie di plastiche di qualsiasi colore: opaca e lucida).

- Segue una serie di alcuni rendering:
  
![renders](images/journal/img11.png)

---
---
#### Giorno 7: 17/02/2020

### Lavoro svolto:
- Tweaks finali del modello
- Aggiunta di due cubemaps, l'utente può swhitchare tra una e l'altra a run-time e i materiali vengono aggiornati
- Aggiunta di un modello schematico di "manichino"
- Creazione di due materiali possibili per le componenti ergonomiche (padiglioni + supporto testa) che ovviamente non possono essere in plastica/metalli: tessuto bianco e scuro con relativa normalmap
- Selezionate normalmap differenti per alluminio/oro/argento
- tweaks sulle 3 luci della scena per ottimizzare l'illuminazione dell'oggetto oltre alla luce dell'env.

- Segue una serie di alcuni render con le modifiche apportate:

![renders](images/journal/img12.png)


---
---
#### Giorno 8: 19/02/2020

### Lavoro svolto:
- Prima versione del sito web implementata tramite bootstrap
  - Ho personalmente preso ispirazione dai siti di: Asus, Sennheiser e Logitech
- Tweaks al codice

![website](images/journal/img13.png)

- L'attuale versione del progetto dovrebbe rispettare tutte le specifiche richieste, di conseguenza i giorni rimanenti verranno utilizzati per:
  - Migliorare il sito
  - Migliorare modello e materiali
  - 

Final tweaks ROADMAP [ver 2]
| n° | Task |
| :---:        |    :----:   |
| 1 | Cambiare la risoluzione delle cubemap (tempi di caricamento troppo elevati)|
| 2 | Aggiungere qualche cubemap|
| 3 | Aggiungere qualche materiale|
| 4 | Migliorare il sito|
| 5 | Migliorare la GUI (esteticamente)|

---
---
#### Giorno 9: 20/02/2020

### Lavoro svolto:
- Ridotta la dimensione delle cubemap di circa 2/3 passando da .png a .jpg (migliorato quindi il tempo di caricamento)
- Correzzione dello shader: in un punto p la quantità di luce deve essere = componente luce envMap + componente speculare dalle luci + componente diffusiva delle luci. (precedentemente, la parte diffusiva veniva sommata senza considerare la parte speculare della envMap (si violava qundi la conservazione dell'energia) ((1-specular) x cdiff ora è (1-specular-envMap) x cdiff).
- Miglioramento della GUI (modifiche estetiche per adattarle al sito).

![GUI prima e dopo ](images/journal/img14.png)

- Miglioramenti dei parametri dei vari materiali.
- Aggiunti pelle/cuoio scuro e chiaro per i padiglioni.
- Miglioramento del sito web.

---
---
#### Giorno 10: 21/02/2020

### Lavoro svolto:
- piccoli miglioramenti
- prima versione del README
- aggiunte 3 cubemaps
---
---

