# Pràctica 1 - Introducció a Git i GitHub

## Introducció

En aquesta pràctica hem treballat amb Git i GitHub. L'objectiu
principal és aprendre a configurar Git, utilitzar SSH per a
l'autenticació amb GitHub, crear i clonar repositoris, realitzar
commits, pujar canvis i sincronitzar els repositoris.

---

## 1. Creació de les claus SSH

El primer pas és crear les claus SSH en el client.

Per crear-les utilitzem:

```bash
ssh-keygen
```

Aquesta ordre genera una clau privada i una clau pública.

Per comprovar que les claus s'han creat correctament:

```bash
ls ~/.ssh
```

En aquest directori podem trobar els fitxers corresponents a les
claus SSH.

---

## 2. Copiar la clau pública a GitHub

Per veure la nostra clau pública utilitzem:

```bash
cat ~/.ssh/id_ed25519.pub
```

Després copiem la clau pública i la introduïm en GitHub.

La ruta utilitzada en GitHub és:

**Perfil → Settings → SSH and GPG keys → New SSH Key**

Una vegada introduïda la clau, es guarda en el nostre compte de
GitHub.

---

## 3. Comprovació de la connexió SSH

Per comprovar que l'autenticació SSH funciona correctament
utilitzem:

```bash
ssh -T git@github.com
```

GitHub demana confirmar la connexió la primera vegada.

Una vegada acceptada, la connexió SSH queda configurada i podem
utilitzar GitHub des del terminal.

---

## 4. Creació d'un repositori

A continuació creem un nou repositori en GitHub.

El repositori creat en la pràctica s'anomena:

```text
prova_josep
```

Aquest repositori s'utilitza per practicar les diferents ordres
de Git.

---

## 5. Clonació del repositori

Una vegada creat el repositori, el clonem a la nostra màquina
virtual.

```bash
git clone git@github.com:Josep2100/prova_josep.git
```

Després entrem dins del directori:

```bash
cd prova_josep
```

D'aquesta manera tenim una còpia local del repositori de GitHub.

---

## 6. Comprovació de la configuració del repositori

Podem comprovar la configuració del repositori amb:

```bash
cat .git/config
```

En aquest fitxer podem veure informació relacionada amb el
repositori remot i la branca principal.

---

## 7. Comprovació de la configuració de Git

També podem consultar la configuració de Git mitjançant:

```bash
git config --list
```

Aquesta ordre mostra diferents dades de configuració, com
l'usuari, el correu electrònic i el repositori remot.

---

## 8. Creació d'un fitxer

A continuació creem un fitxer dins del repositori i li afegim
contingut.

Després podem comprovar l'estat del repositori:

```bash
git status
```

Aquesta ordre ens permet veure els fitxers que han estat
modificats o que encara no han estat afegits al control de
versions.

---

## 9. Afegir el fitxer a Git

Per afegir el fitxer al control de versions utilitzem:

```bash
git add .
```

Després podem tornar a comprovar l'estat:

```bash
git status
```

---

## 10. Primer commit

Una vegada afegit el fitxer, realitzem el primer commit.

```bash
git commit -m "Primera versió"
```

El commit permet guardar una versió dels canvis realitzats.

---

## 11. Pujar el fitxer a GitHub

Una vegada realitzat el commit, pugem els canvis al repositori
remot:

```bash
git push
```

D'aquesta manera el fitxer apareix també en el repositori de
GitHub.

---

## 12. Modificació del fitxer

Després modifiquem el fitxer:

```text
ejemplo.txt
```

En aquesta modificació es realitza un canvi en el nom del fitxer.

Una vegada realitzada la modificació, preparem el següent commit.

---

## 13. Segon commit

Per guardar la segona versió dels canvis utilitzem:

```bash
git commit -am "Segona versió"
```

L'opció `-am` permet afegir els fitxers modificats que ja estaven
sota control de versions i crear el commit.

---

## 14. Pujar els canvis

Després del segon commit pugem els canvis al repositori remot:

```bash
git push
```

Els canvis realitzats en el fitxer queden sincronitzats amb
GitHub.

---

## 15. Eliminació del fitxer

A continuació eliminem el fitxer del repositori.

Després de l'eliminació podem comprovar l'estat amb:

```bash
git status
```

---

## 16. Tercer commit

Després d'eliminar el fitxer realitzem un tercer commit.

Aquest commit registra l'eliminació del fitxer en l'historial
del repositori.

---

## 17. Pujar l'eliminació a GitHub

Finalment pugem els canvis al repositori remot:

```bash
git push
```

D'aquesta manera l'eliminació del fitxer també queda reflectida
en GitHub.

---

## 18. Comprovació de `git pull` i `git status`

En aquesta part comprovem dues ordres importants:

```bash
git pull
```

i:

```bash
git status
```

### git pull

L'ordre `git pull` permet actualitzar el nostre repositori local
amb els canvis que existeixen en el repositori remot.

Això permet treballar amb el mateix repositori des de diferents
llocs, per exemple des de casa o des de l'institut.

### git status

L'ordre `git status` permet saber en quin estat es troba el nostre
repositori local.

---

## 19. Creació de la carpeta del nou exercici

A continuació creem la carpeta corresponent al següent exercici.

```bash
mkdir exercici
```

Després entrem dins de la carpeta:

```bash
cd exercici
```

---

## 20. Inicialització de Git

Inicialitzem Git dins de la nova carpeta:

```bash
git init
```

Aquesta ordre crea un nou repositori Git local.

---

## 21. Creació del README

Dins del repositori creem el fitxer:

```text
README.md
```

Aquest fitxer s'utilitza per documentar i explicar el contingut
del repositori.

---

## 22. Afegir el README i fer el primer commit

Afegim el README a Git:

```bash
git add README.md
```

Després realitzem el primer commit:

```bash
git commit -m "Primer commit"
```

D'aquesta manera el README queda registrat en l'historial de Git.

---

## 23. Creació del repositori a GitHub

A continuació creem un nou repositori en GitHub.

Aquest repositori servirà com a repositori remot del projecte
que acabem de crear localment.

---

## 24. Connexió del repositori local amb GitHub

Des del terminal connectem el repositori local amb el repositori
remot de GitHub.

La connexió es realitza mitjançant SSH.

---

## 25. Pujar el repositori a GitHub

Finalment executem les ordres necessàries per publicar el
repositori local en GitHub.

Primer canviem el nom de la branca actual a `main`:

```bash
git branch -M main
```

Aquesta ordre canvia el nom de la branca actual a `main`.

Després pugem el repositori a GitHub:

```bash
git push -u origin main
```

Aquesta ordre puja el repositori local a GitHub i estableix
`origin/main` com a branca remota associada.

---

## Resultat de la pràctica

Amb aquesta pràctica he après els conceptes bàsics de Git i
GitHub.

He treballat amb:

- Claus SSH.
- Autenticació amb GitHub.
- Creació de repositoris.
- Clonació de repositoris.
- Configuració de Git.
- Creació i modificació de fitxers.
- `git add`.
- `git commit`.
- `git push`.
- `git pull`.
- `git status`.
- Creació de branques.
- Connexió entre repositoris locals i remots.
- Publicació d'un repositori local en GitHub.

La pràctica m'ha permès entendre el funcionament del control de
versions amb Git i la sincronització dels projectes amb GitHub.
