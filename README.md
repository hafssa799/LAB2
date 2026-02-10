
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


