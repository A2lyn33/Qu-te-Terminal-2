### ⚠️ Vérifications avant de commencer

1. **Le fichier `planets.zip` existe-t-il ?**
   Vérifiez si le fichier a bien été téléchargé :
   ```bash
   ls ~/quests/shell
   ```
   Si le fichier `planets.zip` n'est pas présent, recommencez le téléchargement avec cette commande :
   ```bash
   curl --ssl-no-revoke -L -o ~/quests/shell/planets.zip "https://github.com/WildCodeSchool/quests-resources/blob/master/terminal/planets.zip?raw=true"
   ```

2. **Unzip est-il installé ?**
   Vérifiez si la commande `unzip` est disponible :
   ```bash
   unzip --version
   ```
   Si la commande n'est pas disponible, installez-la :
   ```bash
   sudo apt-get install -y unzip
   ```

---

### 🛠️ Étapes pour décompresser l'archive

1. **Assurez-vous d'être dans le bon répertoire** :
   ```bash
   cd ~/quests/shell
   ```

2. **Tentez de décompresser l'archive** :
   ```bash
   unzip planets.zip
   ```

3. **Si l'archive ne se décompresse pas** :
   - **Erreur : "cannot find or open planets.zip"**  
     Le fichier est peut-être corrompu ou mal téléchargé. Supprimez-le et retéléchargez-le :
     ```bash
     rm planets.zip
     curl --ssl-no-revoke -L -o planets.zip "https://github.com/WildCodeSchool/quests-resources/blob/master/terminal/planets.zip?raw=true"
     ```

   - **Erreur : "End-of-central-directory signature not found"**  
     Cela signifie souvent que l'archive est corrompue. Assurez-vous que le téléchargement a bien été complet. Vous pouvez vérifier la taille du fichier :
     ```bash
     ls -lh planets.zip
     ```
     Le fichier devrait avoir une taille supérieure à zéro.

---

### 🚑 Solutions alternatives

1. **Utiliser `zipinfo` pour inspecter l'archive** :
   ```bash
   zipinfo planets.zip
   ```
   Si l'archive est valide, cette commande affichera une liste des fichiers qu'elle contient. Sinon, le fichier est probablement corrompu.

2. **Utiliser une autre méthode pour décompresser** :
   Si `unzip` ne fonctionne pas, essayez avec `7z` :
   ```bash
   sudo apt-get install -y p7zip-full
   7z x planets.zip
   ```
3. **Vérification manuelle dans un navigateur** (Optionnel)
Si le problème persiste, téléchargez l'archive directement depuis votre navigateur :

   Ouvrez ce lien dans un navigateur : [Planets.zip](https://github.com/WildCodeSchool/quests-resources/raw/master/terminal/planets.zip).<br>
   Téléchargez le fichier et placez-le dans ~/quests/shell.<br>
   Reprenez la décompression dans le terminal :
   ```bash
   cd ~/quests/shell
   unzip planets.zip
   ```
---

# 💪 Challenge : Organisation des planètes avec le terminal

Ce guide vous accompagnera pas à pas pour réussir le challenge en utilisant uniquement le terminal.

---

## 🛠️ Prérequis : Installer les outils nécessaires

Vous aurez besoin de deux outils en ligne de commande :
- **curl** : pour télécharger un fichier.
- **unzip** : pour décompresser une archive `.zip`.

### Installation de curl et unzip

#### Sous Linux
Exécutez cette commande pour installer curl et unzip :
```bash
sudo apt-get install -y curl unzip
```

---

## 📥 Étape 1 : Télécharger et décompresser le fichier planets.zip

1. **Naviguez dans le répertoire cible** :
   ```bash
   mkdir -p ~/quests/shell && cd ~/quests/shell
   ```

2. **Téléchargez l'archive** :
   ```bash
   curl --ssl-no-revoke -L -o planets.zip "https://github.com/WildCodeSchool/quests-resources/blob/master/terminal/planets.zip?raw=true"
   ```

3. **Décompressez l'archive** :
   ```bash
   unzip planets.zip
   ```

---

## 🌌 Étape 2 : Organisation des planètes

1. **Créez les répertoires nécessaires** :

   - Répertoires principaux :
     ```bash
     mkdir -p planets/real planets/fictional planets/inhabited
     ```

   - Sous-répertoires pour les planètes réelles :
     ```bash
     mkdir -p planets/real/terrestrial planets/real/gas-giants planets/real/dwarf-planets
     ```

2. **Classez les planètes** :

   - **Déplacez les planètes réelles** :
     ```bash
     mv planets/earth.jpeg planets/real/terrestrial/
     mv planets/mars.jpeg planets/real/terrestrial/
     mv planets/venus.jpeg planets/real/terrestrial/
     mv planets/jupiter.jpeg planets/real/gas-giants/
     mv planets/saturn.jpeg planets/real/gas-giants/
     mv planets/uranus.jpeg planets/real/gas-giants/
     mv planets/neptune.jpeg planets/real/gas-giants/
     mv planets/mercury.jpeg planets/real/terrestrial/
     mv planets/pluto.jpeg planets/real/dwarf-planets/
     ```

   - **Déplacez les planètes fictives** :
     ```bash
     mv planets/arrakis.jpeg planets/fictional/
     mv planets/cybertron.jpeg planets/fictional/
     mv planets/coruscant.jpeg planets/fictional/
     ```

   - **Copiez les planètes habitées** :
     ```bash
     cp planets/earth.jpeg planets/inhabited/
     cp planets/mars.jpeg planets/inhabited/
     cp planets/arrakis.jpeg planets/inhabited/
     cp planets/cybertron.jpeg planets/inhabited/
     ```

3. **Supprimez Pluton et son répertoire parent** :
   ```bash
   rm -rf planets/real/dwarf-planets/
   ```

---

## 🔍 Étape 3 : Vérification du résultat

1. **Listez l’organisation des fichiers** :
   ```bash
   find planets/
   ```

2. **Affichez l’historique des commandes** :
   ```bash
   history
   ```

---

## 🧹 Étape 4 : Nettoyage

Après validation, supprimez le répertoire utilisé :
```bash
rm -rf ~/quests/shell
```

---

## ✅ Critères de réussite

- Les planètes sont correctement classées :
  - **Planètes réelles** : dans `planets/real` et ses sous-dossiers.
  - **Planètes fictives** : dans `planets/fictional`.
  - **Planètes habitées** : copiées dans `planets/inhabited`.
- Pluton et son répertoire parent sont supprimés.
- Vous avez uniquement utilisé le terminal.

---

🎉 **Bravo, vous avez terminé le challenge !**
```
