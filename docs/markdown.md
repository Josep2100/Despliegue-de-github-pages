# Pràctica 2 - Introducció a Markdown

## Introducció

En aquesta pràctica hem treballat amb Markdown i hem creat
documents amb extensió `.md` dins d'un repositori.

L'objectiu és practicar la creació i edició de fitxers Markdown,
la incorporació d'imatges, la creació d'enllaços i la conversió
d'un fitxer Markdown a PDF.

---

## 1. Creació de la carpeta

El primer pas és crear una carpeta dins del repositori que ja
havíem creat anteriorment.

La carpeta utilitzada en la pràctica és:

```text
IAW_markdown
```

Dins d'aquesta carpeta es treballa amb els documents Markdown.

---

## 2. Creació i edició del README.md

Dins de la carpeta `IAW_markdown` es crea el fitxer:

```text
README.md
```

A continuació es completa el contingut indicat en l'exercici.

El fitxer `README.md` és el document principal que utilitzem
per practicar la sintaxi Markdown.

---

## 3. Afegir contingut al document Markdown

En aquest apartat es realitzen diferents exercicis amb Markdown.

### 3.1. Afegir una imatge mitjançant una URL externa

El primer exercici consisteix a incorporar una imatge al document
utilitzant una URL externa.

La sintaxi utilitzada en Markdown és:

```markdown
![Descripció de la imatge](URL_DE_LA_IMATGE)
```

D'aquesta manera la imatge es mostra dins del document Markdown
a partir d'una URL externa.

---

### 3.2. Crear el directori img

A continuació es crea un directori anomenat:

```text
img
```

Aquest directori es troba dins del repositori.

La seua funció és emmagatzemar les imatges que utilitzarem en
el document Markdown.

L'estructura queda de la següent manera:

```text
IAW_markdown/
├── README.md
└── img/
    └── imatge
```

---

### 3.3. Incorporar una imatge local

Després d'afegir una imatge dins del directori `img`, la
incorporem al document Markdown.

Per exemple:

```markdown
![Descripció de la imatge](img/imatge.png)
```

D'aquesta manera el document utilitza una imatge que es troba
dins del propi repositori.

---

## 4. Creació d'un nou document Markdown

A continuació creem un nou document Markdown dins del repositori.

El nou document es crea amb extensió:

```text
.md
```

Després de crear el document es realitza un commit per guardar
els canvis:

```bash
git add .
git commit -m "Nou document Markdown"
```

---

## 5. Creació d'un enllaç

Des del fitxer `README.md` creem un enllaç cap al nou document
Markdown que acabem de crear.

La sintaxi d'un enllaç en Markdown és:

```markdown
[Text de l'enllaç](fitxer.md)
```

D'aquesta manera podem navegar des del `README.md` fins al nou
document.

Després d'afegir l'enllaç realitzem un commit per guardar els
canvis:

```bash
git add .
git commit -m "Afegim enllaç al document"
```

---

## 6. Conversió del fitxer Markdown a PDF

Finalment convertim el document Markdown a PDF.

El resultat és un document PDF generat a partir del contingut
del fitxer Markdown.

---

## Resultat de la pràctica

Amb aquesta pràctica he treballat els conceptes bàsics de
Markdown.

He après a:

- Crear una carpeta dins d'un repositori.
- Crear i editar un fitxer `README.md`.
- Afegir una imatge mitjançant una URL externa.
- Crear un directori `img`.
- Afegir una imatge local al document.
- Crear un nou document Markdown.
- Crear enllaços entre documents Markdown.
- Realitzar commits dels canvis.
- Convertir un document Markdown a PDF.

La pràctica m'ha permès familiaritzar-me amb l'estructura i
les possibilitats bàsiques dels documents Markdown.
