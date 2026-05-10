# 🚀 GUIDE COMPLET - TP DevOps Module 158
**LeniMoras - Projet Flask + Jenkins + Raspberry Pi**

---

## 📌 INFOS PERSO À AVOIR SOUS LA MAIN

| Info | Valeur |
|---|---|
| GitHub username | `leniVithu` |
| Email GitHub | `vithurshan.leni@eduvaud.ch` |
| Nouveau dépôt | `devops-158-LeniMoras-tp-v2` |
| URL dépôt | `https://github.com/leniVithu/devops-158-LeniMoras-tp-v2` |
| User Pi | `pi_vithurshan` |
| Hostname Pi | `pi-158-vithurshan.local` |
| Token GitHub | (sur ta clé USB dans `token.txt`) |

---

# 🏠 PARTIE 1 — CHEZ TOI (WINDOWS)

## ✅ ÉTAPE 1 — Sécurité (URGENT, 2 min)

### 1.1 Révoque l'ancien token compromis
- Va sur : https://github.com/settings/tokens
- Trouve `raspberry-pi-tp` → **Delete**

### 1.2 Supprime ou rends privé l'ancien dépôt
- Va sur : https://github.com/leniVithu/devops-158-LeniMoras-tp/settings
- Descends tout en bas → **"Danger Zone"**
- **"Delete this repository"** ou **"Change visibility" → Private**

---

## ✅ ÉTAPE 2 — Crée un nouveau token (3 min)

1. Va sur : https://github.com/settings/tokens
2. Clique **"Generate new token (classic)"**
3. Remplis :
   - Note : `raspberry-pi-v2`
   - Expiration : `90 days`
   - ✅ Coche **`repo`**
4. Clique **"Generate token"**
5. **Copie le token** (commence par `ghp_...`)
6. ⚠️ Sauvegarde-le UNIQUEMENT sur ta clé USB dans `token.txt`
7. ❌ JAMAIS sur GitHub ou dans un chat !

---

## ✅ ÉTAPE 3 — Crée le nouveau dépôt GitHub (2 min)

1. Va sur : https://github.com/new
2. Remplis :

| Champ | Valeur |
|---|---|
| Repository name | `devops-158-LeniMoras-tp-v2` |
| Description | `TP DevOps Module 158 - Flask + Jenkins + Raspberry Pi` |
| Visibility | ✅ **Public** |
| Initialize with README | ❌ NE PAS COCHER |
| .gitignore | ❌ NE PAS COCHER |
| License | ❌ NE PAS COCHER |

3. Clique **"Create repository"**

---

## ✅ ÉTAPE 4 — Vérifications Windows

### 4.1 Vérifier Python
```powershell
python --version
```
→ Doit afficher `Python 3.14.5`

### 4.2 Vérifier Git
```powershell
git --version
```
→ Doit afficher `git version 2.x.x`

---

## ✅ ÉTAPE 5 — Préparer le projet en local

### 5.1 Crée le dossier
Clic droit sur le bureau → Nouveau → Dossier → **`devops-158-tp`**

### 5.2 Mets dedans les 4 fichiers fournis :
- `app.py`
- `Jenkinsfile`
- `test_app.py`
- `requirements.txt`

### 5.3 Ouvre PowerShell et navigue dans le dossier
```powershell
cd "C:\Users\M329890\OneDrive - MerckGroup\Desktop\devops-158-tp"
```
*(Les guillemets sont importants à cause des espaces dans le chemin !)*

### 5.4 Vérifie le contenu
```powershell
dir
```
→ Tu dois voir les 4 fichiers

---

## ✅ ÉTAPE 6 — Tester Flask sur Windows

### 6.1 Crée l'environnement virtuel
```powershell
python -m venv venv
```

### 6.2 Active-le
```powershell
.\venv\Scripts\activate
```
→ Tu dois voir `(venv)` au début de ta ligne

### 6.3 Installe les dépendances
```powershell
pip install -r requirements.txt
```

### 6.4 Lance Flask
```powershell
python app.py
```

### 6.5 Teste dans le navigateur
Ouvre : http://localhost:5000

→ Tu dois voir : **"Hello depuis le Raspberry Pi - Groupe 158 !"** ✅

### 6.6 Arrête Flask
`Ctrl+C` dans PowerShell

---

## ✅ ÉTAPE 7 — Tester les tests unitaires

```powershell
python -m pytest test_app.py -v
```

→ Tu dois voir 4 tests **PASSED** en vert ✅

```
test_home_page_status_code PASSED
test_response_contains_hello PASSED
test_response_not_empty PASSED
test_response_type_is_string PASSED
```

Si tu vois 4 PASSED → **TON CODE EST PARFAIT** 💯

---

## ✅ ÉTAPE 8 — Pousser sur GitHub

### 8.1 Configure Git (1 fois seulement)
```powershell
git config --global user.email "vithurshan.leni@eduvaud.ch"
git config --global user.name "leniVithu"
```

### 8.2 Crée un .gitignore (pour exclure venv)
```powershell
echo "venv/" > .gitignore
```

### 8.3 Initialise Git et commit
```powershell
git init
git add .
git commit -m "Setup initial du projet DevOps"
```

### 8.4 Pousse sur GitHub
```powershell
git branch -M main
git remote add origin https://github.com/leniVithu/devops-158-LeniMoras-tp-v2.git
git push -u origin main
```

### 8.5 Authentification
- **Username** : `leniVithu`
- **Password** : ton **token** (depuis ta clé USB) — pas ton mot de passe GitHub !

---

## ✅ ÉTAPE 9 — Vérifie sur GitHub

Va sur : https://github.com/leniVithu/devops-158-LeniMoras-tp-v2

Tu dois voir tes 4 fichiers ✅

---

# 🏫 PARTIE 2 — DEMAIN AU LABO (1H CHRONO)

## ✅ ÉTAPE 10 — Connexion au Pi

### Option A — SSH (préféré)
```bash
ssh pi_vithurshan@pi-158-vithurshan.local
```
ou
```bash
ssh pi_vithurshan@<IP_DU_PI>
```

### Option B — Si SSH ne marche pas
Travaille directement sur le bureau du Pi avec écran et clavier.
Ouvre claude.ai dans le navigateur du Pi pour copier-coller mes commandes.

---

## ✅ ÉTAPE 11 — Cloner le projet

```bash
cd ~
git clone https://github.com/leniVithu/devops-158-LeniMoras-tp-v2.git
cd devops-158-LeniMoras-tp-v2
```

---

## ✅ ÉTAPE 12 — Setup Python

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## ✅ ÉTAPE 13 — Test Flask manuel

```bash
python app.py
```

Trouve l'IP du Pi avec `hostname -I` (dans un autre terminal)

Ouvre dans le navigateur : `http://<IP_PI>:5000`

→ Tu vois "Hello depuis le Raspberry Pi - Groupe 158 !" ✅

`Ctrl+C` pour arrêter.

---

## ✅ ÉTAPE 14 — Test des tests unitaires

```bash
source venv/bin/activate
python -m pytest test_app.py -v
```

→ 4 tests verts ✅

---

## ✅ ÉTAPE 15 — Installer Jenkins

```bash
sudo apt install -y openjdk-17-jre

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install -y jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

→ Tu dois voir **Active (running)** en vert

---

## ✅ ÉTAPE 16 — Configurer Jenkins

### 16.1 Récupère le mot de passe initial
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### 16.2 Ouvre Jenkins dans le navigateur
```
http://<IP_PI>:8080
```
ou
```
http://localhost:8080
```
(si tu es sur le Pi directement)

### 16.3 Suis les étapes
1. Colle le mot de passe initial
2. Clique **"Install suggested plugins"** (attends que ça finisse)
3. Crée ton compte admin :
   - Username : `admin`
   - Password : (choisis un)
   - Email : `vithurshan.leni@eduvaud.ch`
4. **Save and Continue**
5. Garde l'URL par défaut → **Save and Finish**
6. **Start using Jenkins**

### 16.4 Installe les plugins manquants
**Manage Jenkins → Plugins → Available plugins**

Coche :
- ✅ Git
- ✅ Pipeline
- ✅ GitHub Integration

→ Install → cocher "Restart Jenkins after install"

---

## ✅ ÉTAPE 17 — Créer le pipeline

### 17.1 Nouveau pipeline
- **New Item** (en haut à gauche du dashboard)
- Nom : `devops-158-LeniMoras-pipeline`
- Type : **Pipeline**
- **OK**

### 17.2 Configuration

**General :**
- ✅ Coche **"GitHub project"**
- Project URL : `https://github.com/leniVithu/devops-158-LeniMoras-tp-v2`

**Build Triggers :**
- ✅ Coche **"GitHub hook trigger for GITScm polling"**
- ✅ Coche aussi **"Poll SCM"** → Schedule : `* * * * *`
  *(Au cas où le webhook ne marche pas, Jenkins vérifie chaque minute)*

**Pipeline :**
- Definition : `Pipeline script from SCM`
- SCM : `Git`
- Repository URL : `https://github.com/leniVithu/devops-158-LeniMoras-tp-v2.git`
- Branches to build : `*/main`
- Script Path : `Jenkinsfile`

**Save**

---

## ✅ ÉTAPE 18 — Premier build manuel

1. Clique **"Build Now"** dans la sidebar
2. Attends que le build apparaisse (#1)
3. Clique sur **#1** → **"Console Output"**
4. Tu dois voir tous les stages en vert ✅

---

## ✅ ÉTAPE 19 — Test du cycle CI/CD

### 19.1 Modifier le code (sur le Pi ou via GitHub web)
```bash
nano app.py
```
Change le texte :
```python
return "Hello MODIFIE - Test CI/CD - LeniMoras"
```
Sauvegarde : `Ctrl+X` → `Y` → `Entrée`

### 19.2 Push sur GitHub
```bash
git add app.py
git commit -m "Test CI/CD - modification du message"
git push
```
- Username : `leniVithu`
- Password : ton token

### 19.3 Observe Jenkins
- Dans Jenkins dashboard, le pipeline démarre automatiquement (max 1 min)
- Build en cours → vert quand fini
- Recharge http://<IP_PI>:5000 → nouveau message affiché ✅

---

## ✅ ÉTAPE 20 — Crash volontaire du pipeline

### 20.1 Casse un test
```bash
nano test_app.py
```
Cherche la ligne :
```python
self.assertIn('Hello', response.data.decode('utf-8'))
```
Change `'Hello'` en `'Bonjour'`

### 20.2 Push
```bash
git add test_app.py
git commit -m "Test crash volontaire"
git push
```

### 20.3 Observe Jenkins
→ Le build passe en **rouge** (FAILED) ✅

### 20.4 Remets en vert
```bash
nano test_app.py
# Remets 'Hello' à la place de 'Bonjour'
git add test_app.py
git commit -m "Fix - retour au vert"
git push
```

→ Build vert ✅

---

# 🎯 RÉCAP DES URLS À RETENIR

| Service | URL |
|---|---|
| Application Flask | http://`<IP_PI>`:5000 |
| Jenkins | http://`<IP_PI>`:8080 |
| GitHub | https://github.com/leniVithu/devops-158-LeniMoras-tp-v2 |

---

# 🆘 SI ÇA BLOQUE

## Problème : `python` introuvable
- Ferme et rouvre PowerShell
- Si toujours pas → Python pas dans le PATH, réinstalle en cochant la case PATH

## Problème : `git push` demande un mot de passe
- C'est le **token** qu'il faut coller, pas ton mot de passe GitHub
- Le token est sur ta clé USB

## Problème : Jenkins ne démarre pas
```bash
sudo systemctl restart jenkins
sudo systemctl status jenkins
```

## Problème : Pipeline ne se déclenche pas auto
- Vérifie que **Poll SCM** est coché avec `* * * * *`
- Sinon clique "Build Now" manuellement

## Problème : SSH refusé
- Travaille directement sur le bureau du Pi
- Le réseau de l'école bloque souvent SSH

---

# 🏆 OBJECTIFS DU TP (Note 6/6)

- [x] Application Flask qui tourne sur le Pi
- [x] Code versionné sur GitHub
- [x] Jenkins installé et configuré
- [x] Pipeline CI/CD opérationnel
- [x] Tests unitaires intégrés
- [x] Push GitHub déclenche redéploiement automatique
- [x] Démonstration crash + fix du pipeline

**LET'S GO ! 💪**
