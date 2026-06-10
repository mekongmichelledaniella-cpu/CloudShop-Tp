# TP CloudShop — Cloud Computing & DevOps (semaines 1 à 7)

**Lisez uniquement ce fichier.** Suivez les étapes **dans l’ordre**, une par une.

---

## Rendu

Envoyez à l’enseignant :

1. **L’URL** de votre dépôt GitHub (public ou partagé)
2. Le fichier `**RAPPORT.md`** complété (dans le dépôt)

**Prérequis :** compte GitHub · Docker Desktop · Python 3.10+

**Note :** pas besoin de compte AWS pour avoir **40/40**. AWS = bonus optionnel.

---

## Où travailler ?

Ouvrez un terminal dans le dossier `**cloudshop-tp/`** (c’est la racine de votre projet Git).

```
TP/
  INSTRUCTIONS.md      ← vous êtes ici
  cloudshop-tp/        ← tout le travail se fait ici
    docs/              ← phases A, B, C (fichiers à compléter)
    RAPPORT.md         ← à compléter à la fin
    screenshots/       ← captures d’écran à la fin
```

---

## Étape 1 — Créer le dépôt Git

```bash
cd cloudshop-tp
git init
git branch -M main
git add .gitignore docs/ screenshots/
git commit -m "chore: init cloudshop repository"
```

Créez un dépôt vide sur GitHub, puis :

```bash
git remote add origin https://github.com/VOTRE_NOM/cloudshop-tp.git
git push -u origin main
```

---

## Étape 2 — Phase A (semaines 1 & 2)

1. Ouvrez `**docs/phase-a.md**` et répondez à toutes les questions.
2. Committez **uniquement** ce fichier :

```bash
git add docs/phase-a.md
git commit -m "docs: phase A cloud semaines 1-2"
git push
```

---

## Étape 3 — Phase B1 (semaine 3, architecture AWS)

1. Ouvrez `**docs/phase-b-aws.md**` (schéma, ports, commandes SSH — **sans créer de VM**).
2. Committez :

```bash
git add docs/phase-b-aws.md
git commit -m "docs: phase B1 architecture AWS"
git push
```

---

## Étape 4 — Phase B2 (semaine 4, multi-cloud)

1. Ouvrez `**docs/phase-b-multicloud.md**` et complétez le tableau.
2. Committez :

```bash
git add docs/phase-b-multicloud.md
git commit -m "docs: phase B2 multicloud"
git push
```

---

## Étape 5 — Phase C (semaine 5, pipeline DevOps)

1. Ouvrez `**docs/phase-c.md**` (schéma du pipeline + 3 questions).
2. Committez :

```bash
git add docs/phase-c.md
git commit -m "docs: phase C pipeline devops"
git push
```

---

## Étape 6 — API Flask (semaines 6 & 7)

Créez `**app.py**` à la racine de `cloudshop-tp/` :

```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.get("/")
def home():
    return jsonify({"message": "Hello from CloudShop", "status": "ok"})

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

Créez `**requirements.txt**` :

```
flask==3.1.0
```

Test local : `python -m pip install -r requirements.txt` puis `python app.py` → [S](http://localhost:5000)

Committez :

```bash
git add app.py requirements.txt
git commit -m "feat: add flask api"
git push
```

---

## Étape 7 — Docker (semaine 7)

Créez `**Dockerfile**` :

```dockerfile
FROM python:3.10-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]
```

Créez `**.dockerignore**` :

```
__pycache__
.venv
.git
```

Test local :

```bash
docker build -t cloudshop-api .
docker run --rm -p 5000:5000 cloudshop-api
```

→ Capturez [http://localhost:5000](http://localhost:5000) (vous la mettrez dans `screenshots/` à l’étape 9).

Committez :

```bash
git add Dockerfile .dockerignore
git commit -m "feat: add dockerfile"
git push
```

---

## Étape 8 — CI GitHub Actions (semaine 6)

Créez le dossier et le fichier `**.github/workflows/ci.yml**` :

```yaml
name: CI CloudShop
on:
  push:
    branches: [main]
jobs:
  test-and-build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: "3.10"
      - run: pip install -r requirements.txt
      - run: python -c "import app; print('OK')"
      - run: docker build -t cloudshop-api .
```

Committez et poussez :

```bash
git add .github/workflows/ci.yml
git commit -m "ci: add github actions pipeline"
git push
```

Allez sur GitHub → onglet **Actions** → vérifiez que le pipeline est **vert**.  
→ Capture d’écran à mettre dans `screenshots/` à l’étape 9.

Dans `**RAPPORT.md`**, répondez aussi : *« GitHub Actions, plutôt PaaS ou IaaS ? »* (5 lignes).

---

## Étape 9 — Rapport final (Phase F)

1. Complétez `**RAPPORT.md*`* (noms, URL GitHub, `git log --oneline`, section « Bilan à domicile »).
2. Mettez vos captures dans `**screenshots/**` (CI verte + Docker local).
3. Committez :

```bash
git add RAPPORT.md screenshots/
git commit -m "docs: rapport final"
git push
```

---

## Checklist avant envoi

- **9 commits minimum** (étapes 1 à 9)
- Pipeline GitHub Actions **vert**
- `docker run` testé en local
- `RAPPORT.md` complété avec l’URL du dépôt
- `git log --oneline` collé dans le rapport

---

## Bonus AWS (+5 pts, optionnel)

Si vous créez une vraie VM AWS : ajoutez une section dans `RAPPORT.md` (IP, captures, **instance terminée**). Un commit dédié n’est pas obligatoire.

---

## Dépannage


| Problème              | Solution                                             |
| --------------------- | ---------------------------------------------------- |
| `pip` introuvable     | `python -m pip install -r requirements.txt`          |
| Docker ne démarre pas | Ouvrir Docker Desktop                                |
| CI rouge              | Lire les logs sur GitHub Actions ; retester en local |
| Pas de compte AWS     | Normal — le parcours sans AWS suffit pour 40/40      |


---

*GSUI · L2 · Cloud Computing & DevOps*