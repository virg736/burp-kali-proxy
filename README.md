# Burp-kali-proxy


<p align="center">
<img src="Burp%20Suite.PNG" alt="Burp Suite MITM Illustration" style="max-width: 100%; height: auto;" />
</p>

<p align="center"><i>© 2025 <strong>virginie lechene</strong> - Tous droits réservés.<br>
Reproduction interdite sans autorisation.</i></p>

<p align="center">
<a href="https://creativecommons.org/licenses/by-nd/4.0/">
<img src="https://licensebuttons.net/l/by-nd/4.0/88x31.png" alt="Licence: CC BY-ND 4.0">
</a>
<img src="https://img.shields.io/badge/stabilité-stable-brightgreen" alt="Stabilité: stable">
</p>
<p align="center"><strong>📸 Image protégée - Propriété exclusive</strong></p>

<p align="center">

Projet pédagogique : analyse de trafic avec Burp Suite sous Kali Linux

---



# Interception de trafic HTTPS avec Burp Suite

 **Note importante** : l’objectif est strictement éducatif, pour illustrer l'interception de trafic HTTPS avec Burp Suite.

---

### Sommaire

1. [Lancer Burp Suite](#1-lancer-burp-suite)
2. [Vérifier que le proxy est actif](#2-vérifier-que-le-proxy-est-actif)
3. [Configurer le proxy dans Firefox](#3-configurer-le-proxy-dans-firefox)
4. [Installer le certificat CA de Burp dans Firefox](#4-installer-le-certificat-ca-de-burp-dans-firefox)
5. [Test de navigation HTTPS](#5-test-de-navigation-https)
6. [Intérêt pour un attaquant](#6-intérêt-pour-un-attaquant)
7. [Pourquoi c’est critique](#7-pourquoi-cest-critique)
8. [Captures écran](#8-captures-écran)
9. [Conclusion](#9-conclusion)

 ---   
    
## Objectif du projet

Ce projet montre comment un analyste ou un attaquant pourrait intercepter le trafic HTTPS entre un navigateur web (Firefox) et un site web, en utilisant **Burp Suite** comme proxy.
L'objectif est strictement éducatif, afin de démontrer l'importance de la sécurité des certificats et des connexions réseau.

---
### 1. Lancer Burp Suite

- Ouvrir un terminal et taper `burpsuite`
- Choisir : **Temporary project**
- Configurer : **Use Burp defaults**
- Démarrer avec : **Start Burp**

![Lancer Burp Suite](./burp-kali-vn.png)


---

## 2. Vérifier que le proxy est actif

- Aller dans l’onglet **Proxy > Options**
- Vérifier que l’écouteur est activé :
- **Adresse** : `127.0.0.1`
- **Port** : `8080`

![Vérifier que le proxy est actif](./projet%20burp-kaly-proxy.2.PNG)

---

## 3. Configurer le proxy dans Firefox

- Aller dans `about:preferences`
- Descendre jusqu’à **Paramètres réseau**
- Cliquer sur **Paramètres...**
- Cocher : **Configuration manuelle du proxy**
- **HTTP proxy** : `127.0.0.1`
- **Port** : `8080`
- Cocher : **Utiliser ce proxy pour tous les protocoles**
- Valider avec **OK**

---

## 4. Installer le certificat CA de Burp dans Firefox

- Aller à l’adresse : `http://burp`
- Télécharger le fichier **cacert.der**
- Aller dans `about:preferences#privacy`
- Cliquer sur **Afficher les certificats**
- Importer le fichier **cacert.der**
- Cocher : **Faire confiance à ce CA pour identifier des sites web**
- Valider

![Vérifier que le proxy est actif](./projet%20burp-kaly-proxy.4.PNG)

---

## 5. Test de navigation HTTPS

- Ouvrir un onglet Firefox et visiter le site : `https://exemple-securite.com`
- Retourner dans **Burp Suite** → onglet **Proxy > HTTP history**
- Observer les requêtes interceptées :
- **URLs**
- **Headers**
- **Cookies**
- **Méthodes** (`GET`, `POST`)


![Vérifier que le proxy est actif](./projet%20burp-kaly-proxy.3.PNG)

---

## 6. Intérêt pour un attaquant

Un attaquant pourrait :

- Lire et manipuler les cookies (ex. : vol de session)
- Injecter des scripts ou du code malveillant
- Analyser les formulaires vulnérables
- Capturer des identifiants envoyés en clair
- Observer toutes les données échangées

---

### 7. Pourquoi c’est critique

- Une fois le certificat racine installé, **Burp Suite** peut intercepter toutes les connexions **HTTPS**
- Si cette installation est faite via un malware ou une ruse, l’utilisateur ne verra pas que ses données sont surveillées

---

## 8. Captures d’écran

Le dossier `/captures` contient :

- Le lancement de **Burp Suite**
- La configuration du proxy **Firefox**
- L’installation du certificat
- Un exemple de requête interceptée

---

## 9. Conclusion

Ce projet montre que :

- Il est possible d’intercepter du trafic **HTTPS** si l’on contrôle le système ou le navigateur
- La confiance dans les certificats est essentielle
- Il ne faut jamais installer un certificat dont on n’est pas sûr

### 10. Avertissement légal

 Ce projet est exclusivement destiné à des fins éducatives, dans le cadre de la formation à la cybersécurité.
 L’auteure ne cautionne ni n’autorise l’utilisation de ces techniques en dehors d’un cadre légal strictement défini.
 Toute utilisation non autorisée est interdite et relève de la seule responsabilité de l’utilisateur.


## 11. Auteur / Droits

© 2025 Virginie Lechene - Tous droits réservés.
Reproduction interdite sans autorisation.


