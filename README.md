# Reconstruction du fichier .md en incluant TOUTES les images et informations fournies par l'utilisateur
markdown_content = """# 📱 Sécurité Mobile - Lab: Root Detection Bypass
**Auteur :** Abdelghafour
**Sujet :** # securite-mobile-lab19x

---

## 🎯 Objectif du Lab
L'objectif est d'analyser l'application, d'identifier le mécanisme de détection du "Root" et de patcher le code Smali pour contourner cette sécurité et obtenir le flag final.

---

## 🚀 Étapes de Réalisation

### 1. Analyse Initiale
Nous commençons par l'analyse de l'environnement.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d16b2f8f-e5b8-4918-90f4-9949d7be8ae4" />

### 2. Décompilation et Identification du Code
Décompilation de l'APK pour accéder aux sources :
<img width="996" height="340" alt="image" src="https://github.com/user-attachments/assets/bbf03f51-37ec-4e97-8d50-c8c1767d5117" />

Analyse des classes avec JADX :
<img width="900" height="862" alt="image" src="https://github.com/user-attachments/assets/aefa4fef-3a39-4c8b-8f79-aad6bd5bf3ab" />

Localisation de la méthode de détection root :
<img width="1281" height="1000" alt="image" src="https://github.com/user-attachments/assets/c3999dfd-b1b8-40a8-8c1c-ebe31282f590" />

Extraction des ressources :
<img width="1552" height="146" alt="image" src="https://github.com/user-attachments/assets/58e125ad-c757-4027-b3c2-11e5ba6ed026" />

### 3. Analyse du Code Smali
Examen du code Smali avant modification :
<img width="1260" height="761" alt="image" src="https://github.com/user-attachments/assets/b064a3f4-38f6-46f8-96a9-f94285d68ba0" />
<img width="1260" height="761" alt="image" src="https://github.com/user-attachments/assets/894f408e-a206-42f2-88e8-eaa3c7bbcde2" />

Identification de la ligne à modifier :
<img width="1920" height="234" alt="image" src="https://github.com/user-attachments/assets/99093153-93eb-4a5d-91ef-85c4c096a7e2" />

### 4. Application du Patch
Le patch est appliqué correctement ! La méthode retourne maintenant toujours false.
<img width="1920" height="582" alt="image" src="https://github.com/user-attachments/assets/1fae02d6-6c5e-43cf-84ae-950e5769c6e9" />

Vérification des registres :
<img width="1920" height="508" alt="image" src="https://github.com/user-attachments/assets/865fa589-9b04-49b1-9acd-9fc6e1801042" />

Analyse du flux dans onCreate :
<img width="1294" height="844" alt="image" src="https://github.com/user-attachments/assets/074b799a-2493-42e2-94bd-35d3d2cacb3b" />

**Note sur le flux :**
- `invoke-static {p1}, isDeviceRooted()` ← on a déjà patché ✅
- `move-result p1`
- `if-eqz p1, :cond_0` ← si false → saute à cond_0 ✅
- `...finish() / exit()` ← sera ignoré ✅
- `:cond_0` ← l'app continue ✅

### 5. Reconstruction et Signature
Notre patch fonctionne correctement. La détection root est bypassée. Maintenant on recompile l'APK.
<img width="1025" height="330" alt="image" src="https://github.com/user-attachments/assets/ee11341d-558b-4b6b-afe9-6bf55a00d664" />

La recompilation a réussi ! ✅
Maintenant on signe l'APK :
<img width="1521" height="453" alt="image" src="https://github.com/user-attachments/assets/9a8fcef4-40d2-4570-8fc5-61d2f14b512d" />
<img width="1521" height="576" alt="image" src="https://github.com/user-attachments/assets/ffa31dc9-3736-4d3a-ad62-96217797dfb5" />

Keystore créé avec succès ! ✅
Signature avec Jarsigner :
<img width="1309" height="888" alt="image" src="https://github.com/user-attachments/assets/884c2cfb-cce4-4ace-9aec-94feb2cfffa0" />
<img width="1309" height="888" alt="image" src="https://github.com/user-attachments/assets/781be39b-9814-4a5c-ad8a-3ac52d248350" />

Jar signed. ✅ L'APK est signé avec succès !

### 6. Installation et Capture du Flag
Installation sur l'émulateur :
<img width="1754" height="441" alt="image" src="https://github.com/user-attachments/assets/69ed8086-8b31-454e-92b9-16f2add1ac32" />

Parfait ! ✅ Fichier transféré. Lancement de l'application avec l'Intent :
<img width="1920" height="442" alt="image" src="https://github.com/user-attachments/assets/9a98c14f-9936-42c7-86b2-ba601e46431e" />

Success ✅ APK installé !

---

## 🏆 Résultat Final : Flag
**Flag attendu :**
`PWNSEC{W3'r3_N0t_T00l5_0f_The_g0v3rnm3n7_0R_4ny0n3_3ls3}`
"""

with open("README_securite_mobile_v2.md", "w", encoding="utf-8") as f:
    f.write(markdown_content)
