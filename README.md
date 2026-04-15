# Contenu final du fichier .md bien organisé pour le lab de sécurité mobile
markdown_content = """# 📱 Sécurité Mobile - Rapport de Lab : Root Detection Bypass
**Auteur :** Abdelghafour
**Classe :** 5IIR
**Projet :** # securite-mobile-lab19x

---

## 📝 Introduction
Ce laboratoire porte sur l'analyse et le contournement (bypass) des mécanismes de sécurité au sein d'une application Android. L'objectif principal est de neutraliser la détection du mode "Root" qui empêche l'application de s'exécuter.

## 🛠️ Outils Utilisés
- **Apktool** : Pour la décompilation et la recompilation de l'APK.
- **JADX-GUI** : Pour l'analyse du code source Java.
- **Keytool & Jarsigner** : Pour générer un keystore et signer l'APK modifié.
- **ADB (Android Debug Bridge)** : Pour l'installation et les tests sur émulateur.

---

## 🚀 Étapes de Réalisation

### 1. Décompilation et Analyse Statique
La première étape consiste à décompiler l'APK pour explorer son contenu et identifier la logique de détection du root.

<img width="996" alt="Décompilation de l'APK" src="https://github.com/user-attachments/assets/bbf03f51-37ec-4e97-8d50-c8c1767d5117" />

Dans le code Java, nous avons identifié la méthode critique `isDeviceRooted()` qui renvoie un booléen.

<img width="1281" alt="Code source Java identifié" src="https://github.com/user-attachments/assets/c3999dfd-b1b8-40a8-8c1c-ebe31282f590" />

### 2. Modification du Code Smali (Patching)
Pour contourner la sécurité, nous modifions directement le fichier Smali. L'objectif est de forcer la méthode `isDeviceRooted` à retourner toujours `false` (0x0).

**Modification appliquée :**
<img width="1920" alt="Patch Smali" src="https://github.com/user-attachments/assets/1fae02d6-6c5e-43cf-84ae-950e5769c6e9" />

**Vérification du flux logique :**
Le patch garantit que la condition de fermeture (`finish()`) dans le `onCreate` ne sera jamais déclenchée.

<img width="1294" alt="Flux logique après patch" src="https://github.com/user-attachments/assets/074b799a-2493-42e2-94bd-35d3d2cacb3b" />

### 3. Recompilation et Signature
Après la modification, l'APK doit être reconstruit et signé avec un nouveau certificat pour être installable.

**Recompilation :**
<img width="1025" alt="Recompilation APK" src="https://github.com/user-attachments/assets/ee11341d-558b-4b6b-afe9-6bf55a00d664" />

**Création du Keystore et Signature :**
<img width="1521" alt="Signature de l'APK" src="https://github.com/user-attachments/assets/9a8fcef4-40d2-4570-8fc5-61d2f14b512d" />
<img width="1309" alt="Jarsigner confirmation" src="https://github.com/user-attachments/assets/781be39b-9814-4a5c-ad8a-3ac52d248350" />

### 4. Installation et Exécution
Nous installons l'APK final sur l'émulateur via ADB.

<img width="1754" alt="Installation ADB" src="https://github.com/user-attachments/assets/69ed8086-8b31-454e-92b9-16f2add1ac32" />

Lancement de l'application :
<img width="1920" alt="Lancement Application" src="https://github.com/user-attachments/assets/9a98c14f-9936-42c7-86b2-ba601e46431e" />

---

## 🏆 Résultat Final
Le mécanisme de détection a été bypassé avec succès. L'application s'exécute et affiche le flag :

```text
PWNSEC{W3'r3_N0t_T00l5_0f_The_g0v3rnm3n7_0R_4ny0n3_3ls3}
