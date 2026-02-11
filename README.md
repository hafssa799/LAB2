
# LAB2 – Test de Root et Sécurité Android

# Étape 1 : Rooter l’AVD

Dans cette étape, j’ai démarré un AVD via Android Studio et vérifié qu’il est bien détecté par ADB.

![](https://github.com/user-attachments/assets/4f334df2-b283-434d-8f07-495d4ce03b64)

 La commande adb shell id affiche uid=0(root), ce qui confirme que l’émulateur fonctionne avec des privilèges root.
Cela permet d’observer l’impact du root sur la sécurité du système Android dans un environnement de test contrôlé.

# Étape 2 : Fiche périmètre

Le test concerne l’application de démonstration Hello Android.
Il est réalisé sur un AVD avec des données fictives et un réseau de test.
 
![](https://github.com/user-attachments/assets/498e52af-7d9a-4e0f-ae85-b6d11a86b260)

# Étape 3 : Démarrer un AVD propre

Un AVD propre a été lancé depuis le gestionnaire de périphériques d’Android Studio.
Aucun compte personnel ni application externe n’a été configuré sur l’émulateur.

Cette étape est essentielle pour garantir la fiabilité des résultats, car elle permet d’éviter toute interférence avec des configurations ou des tests précédents.

![](https://github.com/user-attachments/assets/6e965d24-74a4-4e5b-96bc-b942b760cf33)

![](https://github.com/user-attachments/assets/f8d5aa6e-ff71-42a8-88b5-de0997051cb4)

# Étape 4 : Installer et lancer l’app

L’application a été installée sur l’AVD à l’aide de la commande suivante :
adb install app-debug.apk
L’installation s’est terminée avec succès.
Après le lancement de l’application, l’écran principal s’affiche correctement avec le message Hello Android!, ce qui confirme que l’environnement de test est fonctionnel et correctement configuré.

![](https://github.com/user-attachments/assets/27549cf6-abd4-49c8-9d72-5541fc745a6a)

![](https://github.com/user-attachments/assets/f9d98641-080a-4226-9a3a-c850190a725b)

# Étape 5 : Réalisation de trois scénarios simples

# Scénario 1 : Ouverture de l’écran d’accueil

L’application démarre correctement et affiche l’écran d’accueil sans erreur.

![](https://github.com/user-attachments/assets/871fc1ce-994f-4d67-b8f6-3859706f6820)

# Scénario 2 : Recherche d’un item dans l’application

Une recherche est effectuée à l’intérieur de l’application. Les résultats s’affichent correctement, ce qui montre que la fonctionnalité de recherche fonctionne comme prévu.

![](https://github.com/user-attachments/assets/67c3a9b1-029f-4eb0-bb32-01e72a2e0162)

![](https://github.com/user-attachments/assets/f50e29bf-3817-4e57-bb26-253f7aa2c723)

# Scénario 3 : Ouverture du détail d’un item

Le détail d’un item (profil ou fiche produit) est ouvert avec succès, et les informations correspondantes sont affichées correctement.

![](https://github.com/user-attachments/assets/450097f0-2a04-4889-9ed3-b2bdf5399ea8)

# Étape 6 : Lecture et analyse de la sécurité Android

![](https://github.com/user-attachments/assets/ed786c50-b9af-4543-90d8-605cf1038b5c)

À partir de la documentation Android Security, plusieurs points clés peuvent être retenus :

1. Android offre un haut niveau de sécurité dès la première utilisation.

2. Chaque application fonctionne dans une sandbox, ce qui garantit l’isolation entre les applications.

3. Le système de permissions contrôle l’accès aux données sensibles et aux fonctionnalités critiques.

4. Le système Android protège les fichiers et le système global contre les modifications non autorisées.

5. Les mises à jour et bulletins de sécurité corrigent régulièrement les vulnérabilités.

6. Les tests de sécurité et les bonnes pratiques contribuent à la protection de l’écosystème Android.

# Étape 7 : Verified Boot (analyse sur AVD)

L’objectif principal de Verified Boot est de garantir que le système Android qui démarre est authentique, c’est‑à‑dire celui prévu par le fabricant, sans modification malveillante du système ou du noyau.

Notion de Chain of Trust

La chain of trust est une chaîne de vérifications successives où chaque composant du démarrage vérifie l’authenticité du suivant avant de lui donner le contrôle.
Si un maillon échoue, le démarrage est bloqué ou signalé comme non sûr.

Importance de l’intégrité au démarrage

L’intégrité au démarrage est critique car si le processus de boot est compromis, toutes les protections de sécurité mises en place après peuvent être contournées, comme une forteresse dont la porte principale serait ouverte.

Vérification sur l’AVD

![](https://github.com/user-attachments/assets/ad9aa1e4-6058-4769-8336-940648437b89)

Résultat observé :(aucune sortie)

Interprétation

Sur un AVD Android Studio, cette propriété n’est pas définie.
Les images AVD sont déverrouillées et rootées par défaut, et Verified Boot n’y est pas activé.
Sur un appareil physique avec une image système signée, le résultat attendu serait :

Green : système vérifié et intègre

Yellow / Orange : système modifié mais fonctionnel

Red : intégrité compromise, démarrage dangereux

# Étape 8 : AVB (Android Verified Boot)

AVB (Android Verified Boot) est l’évolution moderne de Verified Boot.
Il apporte une vérification d’intégrité plus robuste et une protection contre le rollback, empêchant l’installation d’anciennes versions vulnérables du système.

Protection anti‑rollback

La protection anti‑rollback empêche l’installation d’anciennes versions du système pouvant contenir des failles connues.
C’est comparable au fait d’empêcher quelqu’un de remplacer une serrure moderne par une ancienne plus facile à forcer.

Test AVB

![](https://github.com/user-attachments/assets/d43e1580-2cc8-44be-bb4c-076674fa5457)


Résultat observé :

< waiting for any device >

Interprétation

Le mode fastboot n’est pas supporté par l’AVD.
Cette commande fonctionne uniquement sur un appareil Android physique connecté en mode bootloader.
Sur AVD, l’absence de réponse est normale et attendue.

# Étape 9 : Définition du Rooting

Le rooting correspond à l’obtention des privilèges super‑utilisateur (root) sur Android.
Cela modifie profondément les protections du système et remet en cause la confiance globale du modèle de sécurité Android.
En laboratoire, le rooting est utile pour observer certains comportements internes et tester la sécurité.
Cependant, il est risqué et nécessite un environnement isolé, une traçabilité stricte et un reset après les tests.

Vérification du root sur l’AVD

Commande exécutée :

![](https://github.com/user-attachments/assets/e3473e40-08c9-42b7-bd4d-2b0eccb9303d)

Résultat observé :

uid=0(root) gid=0(root) groups=0(root) ...

Cela confirme que l’émulateur fonctionne avec les droits root actifs.

# Étape 10 : Intérêt du laboratoire (environnement non opérationnel)

En laboratoire, un environnement privilégié permet d’observer et d’analyser des comportements du système Android qui sont normalement inaccessibles dans un contexte utilisateur standard.
L’accès root facilite l’observation d’artefacts système, l’analyse du comportement runtime des applications à bas niveau et l’évaluation de la robustesse des mécanismes de stockage face à un attaquant disposant de privilèges élevés.

# Cas d’usage concret

Par exemple, avec les privilèges root, il est possible d’examiner la manière dont une application stocke ses données sensibles.
Cette analyse permet de vérifier si l’application repose uniquement sur la protection du système Android (mauvaise pratique) ou si elle implémente son propre mécanisme de chiffrement (bonne pratique).

# Cadre strict :
Ces tests sont réalisés uniquement dans un laboratoire autorisé, sur des données fictives et des environnements dédiés.

# Contexte légal

Dans certains pays, le rooting peut violer les conditions d’utilisation du fabricant ou des lois relatives à la protection des mesures techniques.
Il est impératif de disposer d’une autorisation explicite avant toute expérimentation de ce type.

# Étape 11 : Matrice de risques

Chaque risque identifié dans un laboratoire de sécurité doit être associé à une mesure d’atténuation appropriée, conformément aux principes de la gestion des risques en cybersécurité.

1. Intégrité non garantie → peut conduire à des conclusions biaisées sur la sécurité réelle de l’application.

2. Surface d’attaque accrue → un appareil sortant du labo peut être exposé à des menaces externes.

3. Données sensibles exposées → risque de violation de la confidentialité si des données réelles sont présentes.

4. Instabilité du système → peut rendre les tests non reproductibles et incohérents.

5. Mélange comptes personnels / tests → entraîne un risque de fuite d’informations privées.

6. Nettoyage insuffisant en fin de séance → persistance de données sensibles après les tests.

7. Réseau non isolé → peut impacter involontairement des systèmes externes.

8. Traçabilité insuffisante → rend impossible l’audit ou la reproduction des tests.

# Étape 12 : Mesures défensives

Les mesures suivantes sont mises en place pour réduire les risques identifiés et garantir un cadre expérimental sécurisé :

1. Réseau isolé afin d’éviter toute communication non contrôlée.

2. Utilisation exclusive de données fictives pour éliminer tout risque de fuite réelle.

3. AVD ou appareil dédié uniquement aux tests de sécurité.

4. Snapshots ou réinitialisation complète en fin de séance pour ne laisser aucune trace.

5. Journal de configuration détaillé afin d’assurer la reproductibilité des tests.

6. Aucun compte personnel configuré pour éviter tout mélange de données.

7. Contrôle strict des APK installées afin de limiter la surface d’attaque.

8. Horodatage et captures des étapes clés pour garantir une traçabilité complète.

# Étape 13 : OWASP MASVS

# Objectif : Connaître les standards de sécurité des applications mobiles.

Exigences testées :

STORAGE-1 : Les données sensibles (mots de passe, tokens, clés API) doivent être stockées de manière sécurisée en utilisant un chiffrement approprié.

NETWORK-1 : Les communications réseau doivent utiliser TLS avec une configuration correcte et vérifier les certificats.

Application pratique sur l’AVD :
Grâce aux privilèges root sur l’émulateur, il est possible de vérifier si l’application respecte ces exigences en examinant :

Le stockage interne (/data/data/[package_name]/) pour détecter des données sensibles non chiffrées.

Le trafic réseau pour s’assurer que les communications sont sécurisées (TLS).

# Étape 14 : OWASP MASTG

# Objectif : Démontrer comment tester concrètement les exigences MASVS.

Relation MASVS-MASTG :

MASVS indique quoi vérifier.

MASTG explique comment le vérifier.

# Idées de tests pratiques :

1. Vérification des fichiers de préférences partagées :
Inspecter /data/data/[package_name]/shared_prefs/ pour détecter des informations sensibles en clair (mots de passe, tokens, clés API).

2. Analyse des logs de l’application :
Utiliser adb logcat pour détecter des fuites d’informations sensibles pendant l’exécution.

Astuce technique :
Le root permet d’accéder au dossier /data/data/ normalement protégé, ce qui facilite l’inspection directe des données privées des applications.

# Étape 15 : Commandes de rooting (rappel synthèse)

# Objectif : Résumer les commandes essentielles pour travailler en environnement root.

Commandes ADB principales :

adb devices
adb root
adb remount
adb shell id
adb shell getprop ro.boot.veritymode
adb shell getprop ro.boot.vbmeta.device_state
adb shell "su -c id"


Guide de dépannage :

Si adb root échoue avec « adbd cannot run as root in production builds », utilisez un émulateur ou un appareil de laboratoire spécialement configuré pour le root.

Options permissives pour tests en labo :

adb disable-verity      # Désactiver dm-verity
adb reboot              # Redémarrer l'appareil
adb remount             # Remonter les partitions après redémarrage
adb logcat -d | tail -n 200 > logcat_root_check.txt


Explication technique :
Désactiver dm-verity permet de modifier les partitions système normalement en lecture seule, comme désactiver l’alarme avant d’ouvrir un coffre-fort.

Commandes Fastboot (labo uniquement) :

fastboot oem device-info
fastboot getvar avb_boot_state
fastboot boot magisk_patched.img    # Boot temporaire, pas de flash

   

