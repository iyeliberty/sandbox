# 🧾 Convention de messages de commit

Ce projet suit la **convention de commit standard** pour assurer une histoire Git lisible et automatiser le changelog, le versioning, et la CI.

---

## ✅ Format général

```
<type>(<scope>): <message>
```

- `type` : **obligatoire** — décrit la nature du changement
- `scope` : **optionnel** — module ou feature concerné
- `message` : **obligatoire** — courte description du changement

---

## 🧠 Exemples valides

```bash
feat(auth): add SignInWithEmail use case
fix(payment): prevent crash when card is null
docs: update README with installation steps
refactor(core): simplify date formatting
test(auth): add unit tests for token refresh
```

---

## ❌ Exemples invalides

```bash
"update things"               # pas de type
"auth: fixed login"           # pas de type valide
"fix: "                       # message vide
"feat add payment method"     # mauvais séparateur (manque `:`)
```

---

## ✅ Types autorisés

| Type       | Description                                       |
|------------|---------------------------------------------------|
| `feat`     | Nouvelle fonctionnalité                           |
| `fix`      | Correction de bug                                 |
| `docs`     | Documentation seulement                           |
| `style`    | Formatage (indentation, virgules, etc.)           |
| `refactor` | Refactoring sans changement de comportement       |
| `test`     | Ajout/modification de tests                       |
| `chore`    | Tâches internes, CI/CD, dépendances, etc.         |
| `perf`     | Amélioration des performances                     |
| `build`    | Changements liés au build, outils, packages       |
| `ci`       | Configuration de l’intégration continue           |

---

## 📦 Pourquoi l’utiliser

- 📜 Génération automatique du changelog
- 🧪 Déclenchement ciblé des tests
- 📈 Versioning automatique
- ✅ Historique Git propre et compréhensible

---

## ⚙️ Installation de Husky + Commitlint

### 1. Installer les dépendances
```bash
npm install --save-dev husky @commitlint/cli @commitlint/config-conventional
```

### 2. Initialiser Husky
```bash
npx husky-init && npm install
```

### 3. Configurer le hook `commit-msg`
```bash
npx husky set .husky/commit-msg 'npx --no -- commitlint --edit "$1"'
```

### 4. Créer le fichier `commitlint.config.js` à la racine
```js
module.exports = {
  extends: ['@commitlint/config-conventional'],
};
```

### 5. (Optionnel) Pré-commit avec analyse Flutter
```bash
npx husky set .husky/pre-commit 'flutter analyze'
```

---

_Note : tout commit invalide est automatiquement rejeté par le hook Husky._