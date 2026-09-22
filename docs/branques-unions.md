# Pràctica 3 - Branques i Unions

## Introducció

En aquesta pràctica hem treballat amb les branques de Git i les
unions entre branques mitjançant l'ordre `merge`.

També hem creat un conflicte entre dues branques, l'hem solucionat
i finalment hem sincronitzat la branca amb GitHub.

---

## 1. Creació de la branca `primera`

El primer exercici consisteix a crear una branca anomenada
`primera` en el repositori local.

Per crear la branca:

```bash
git branch primera
```

Després canviem a la branca creada:

```bash
git checkout primera
```

Per comprovar que la branca s'ha creat correctament:

```bash
git branch
```

La branca `primera` apareix entre les branques disponibles.

---

## 2. Creació d'un fitxer i fusió amb la branca principal

Una vegada dins de la branca `primera`, creem un nou fitxer.

Per exemple:

```bash
touch f1.txt
```

Després afegim el fitxer a Git:

```bash
git add f1.txt
```

I fem un commit:

```bash
git commit -m "Creació del fitxer"
```

A continuació tornem a la branca principal:

```bash
git checkout main
```

I fusionem la branca `primera` amb la branca principal:

```bash
git merge primera
```

### Es va produir un conflicte?

No es va produir cap conflicte.

El motiu és que en la branca `primera` només s'havia creat un
fitxer nou. Per tant, Git va poder incorporar-lo automàticament
a la branca `main`.

---

## 3. Eliminació de la branca `primera`

Una vegada realitzada la fusió, eliminem la branca `primera`.

```bash
git branch -d primera
```

Després comprovem les branques que queden:

```bash
git branch
```

D'aquesta manera podem comprovar que la branca `primera` ha
estat eliminada.

---

## 4. Creació de la branca `segona`

A continuació creem una nova branca anomenada `segona`.

```bash
git checkout -b segona
```

Una vegada dins de la branca `segona`, modifiquem el fitxer:

```text
f1.txt
```

Afegim els canvis:

```bash
git add f1.txt
```

I fem un commit:

```bash
git commit -m "Modificació de f1.txt en segona"
```

---

## 5. Modificació del mateix fitxer en `main`

Després tornem a la branca principal:

```bash
git checkout main
```

En la branca `main` tornem a modificar el mateix fitxer:

```text
f1.txt
```

Després afegim els canvis:

```bash
git add f1.txt
```

I fem un altre commit:

```bash
git commit -m "Modificació de f1.txt en main"
```

---

## 6. Creació del conflicte

Ara intentem fusionar la branca `segona` amb la branca `main`:

```bash
git merge segona
```

En aquest moment Git indica que s'ha produït un conflicte.

El conflicte apareix perquè hem modificat el mateix fitxer
(`f1.txt`) en dues branques diferents.

Quan dues branques modifiquen la mateixa part d'un fitxer,
Git no pot decidir automàticament quin contingut ha de conservar.

---

## 7. Comprovació del conflicte

Per comprovar quin fitxer presenta el conflicte utilitzem:

```bash
git status
```

Git indica que el fitxer `f1.txt` presenta un conflicte.

Quan obrim el fitxer podem trobar els marcadors de conflicte:

```text
<<<<<<< HEAD
Contingut de la branca main
=======
Contingut de la branca segona
>>>>>>> segona
```

Aquests marcadors indiquen les dues versions diferents del fitxer.

---

## 8. Resolució del conflicte

Per solucionar el conflicte obrim el fitxer:

```bash
nano f1.txt
```

Eliminem els marcadors del conflicte i deixem únicament el
contingut que volem conservar.

Una vegada solucionat el conflicte, guardem el fitxer.

Després tornem a afegir-lo a Git:

```bash
git add f1.txt
```

I fem un commit:

```bash
git commit -m "Resolució del conflicte"
```

D'aquesta manera Git registra que el conflicte ha estat resolt.

---

## 9. Sincronització amb GitHub

Finalment sincronitzem la branca `segona` amb el repositori remot.

```bash
git push -u origin segona
```

La branca queda sincronitzada amb GitHub.

---

## Resultat

En aquesta pràctica he après a treballar amb branques de Git.

Els principals conceptes treballats són:

- Creació de branques.
- Canvi entre branques.
- Creació i modificació de fitxers.
- Commits.
- Unió de branques amb `git merge`.
- Eliminació de branques.
- Generació de conflictes.
- Resolució manual de conflictes.
- Sincronització de branques amb GitHub.

En el primer `merge` no es va produir cap conflicte perquè només
s'havia creat un fitxer nou.

En el segon `merge` sí que es va produir un conflicte perquè el
mateix fitxer havia estat modificat en branques diferents.

Finalment, el conflicte es va solucionar i la branca `segona`
es va sincronitzar correctament amb GitHub.
