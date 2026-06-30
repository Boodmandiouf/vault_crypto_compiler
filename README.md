# 🛠️ Guide de Workflow : Sanctuary Admin Core

Ce projet utilise un système de sécurité par chiffrement AES-256 côté client pour protéger le panneau d'administration. Étant donné que le site est hébergé sur GitHub Pages (statique), le workflow de modification est spécifique.

## ⚠️ Règle d'or
**Ne jamais chiffrer l'intégralité du fichier `admin.html`.** Le fichier de production doit conserver sa structure de décodeur. Seul le contenu de la variable `ENCRYPTED_ADMIN_DATA` doit être remplacé lors de chaque mise à jour.

---

## 🔄 Organisation des fichiers
Pour travailler efficacement, séparez vos fichiers sur votre machine locale :

1.  **`admin.html` (Production) :** Le fichier présent sur GitHub. Il contient l'interface de verrouillage et le moteur de déchiffrement.
2.  **`admin-source.html` (Source) :** Votre fichier de travail en clair. 
    * *Note :* Ajoutez ce fichier à votre `.gitignore` pour qu'il ne soit jamais publié sur GitHub.

---

## 🚀 Étapes de modification

### 1️⃣ Modification du contenu
Ouvrez votre fichier `admin-source.html` en local et effectuez vos ajouts ou modifications.

### 2️⃣ Chiffrement
1. Copiez l'intégralité du code HTML contenu dans `admin-source.html`.
2. Ouvrez votre **Compilateur Crypto Sanctuaire**.
3. Collez le code dans la zone prévue à cet effet.
4. Saisissez votre clé secrète et lancez la compilation **AES-256**.

### 3️⃣ Mise à jour de la production
1. Copiez la chaîne chiffrée générée par le compilateur.
2. Ouvrez votre fichier `admin.html` (production).
3. Localisez la variable `ENCRYPTED_ADMIN_DATA` et remplacez l'ancienne chaîne par la nouvelle :
   ```javascript
   const ENCRYPTED_ADMIN_DATA = "VOTRE_NOUVELLE_CHAINE_GEANTE_ICI";
