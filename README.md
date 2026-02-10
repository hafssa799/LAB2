
# LAB2 – Test de Root et Sécurité Android

# Étape 1 : Rooter l’AVD

Dans cette étape, j’ai démarré un AVD via Android Studio et vérifié qu’il est bien détecté par ADB.

![](https://github.com/user-attachments/assets/4f334df2-b283-434d-8f07-495d4ce03b64)

 La commande adb shell id affiche uid=0(root), ce qui confirme que l’émulateur fonctionne avec des privilèges root.
Cela permet d’observer l’impact du root sur la sécurité du système Android dans un environnement de test contrôlé.

# Étape 2 : Fiche périmètre

Cette fiche définit clairement le cadre du test afin d’éviter toute ambiguïté.
L’application testée est une application de démonstration (Hello Android).
Le support utilisé est un AVD (émulateur Android).
L’objectif est de comprendre le rooting et ses impacts sur la sécurité.
Les données utilisées sont fictives et le réseau est un réseau de test.
 
![](https://github.com/user-attachments/assets/498e52af-7d9a-4e0f-ae85-b6d11a86b260)

# Étape 3 : Démarrer un AVD propre

Un AVD propre a été démarré depuis le gestionnaire de périphériques d’Android Studio.
Aucun compte personnel ni application externe n’est présent sur l’émulateur.
Cette étape est importante pour garantir des résultats fiables et éviter toute interférence avec d’anciens tests.

![](https://github.com/user-attachments/assets/6e965d24-74a4-4e5b-96bc-b942b760cf33)

![](https://github.com/user-attachments/assets/f8d5aa6e-ff71-42a8-88b5-de0997051cb4)

# Étape 4 : Installer et lancer l’app

L’application a été installée sur l’AVD à l’aide de la commande adb install app-debug.apk.
L’installation s’est terminée avec succès.
L’application se lance correctement et affiche l’écran principal avec le message Hello Android!.
Cela confirme que l’environnement de test fonctionne correctement.

![](https://github.com/user-attachments/assets/27549cf6-abd4-49c8-9d72-5541fc745a6a)

![](https://github.com/user-attachments/assets/f9d98641-080a-4226-9a3a-c850190a725b)

# Étape 5 : Faire 3 scénarios simples

# Scénario 1 : Ouvre l’écran d’accueil.

![](https://github.com/user-attachments/assets/871fc1ce-994f-4d67-b8f6-3859706f6820)

# Scénario 2 : Cherche un item dans l’app.

![](https://github.com/user-attachments/assets/67c3a9b1-029f-4eb0-bb32-01e72a2e0162)

![](https://github.com/user-attachments/assets/f50e29bf-3817-4e57-bb26-253f7aa2c723)

# Scénario 3 : Ouvre le détail d’un item (profil ou fiche produit).

![](https://github.com/user-attachments/assets/450097f0-2a04-4889-9ed3-b2bdf5399ea8)

# Étape 6 : Lire Android Security

![](https://github.com/user-attachments/assets/ed786c50-b9af-4543-90d8-605cf1038b5c)

	
1. Android offre une sécurité robuste dès la première utilisation.	
2. Chaque application fonctionne dans sa propre sandbox, isolée des autres apps.	
3. Les permissions contrôlent l’accès aux données sensibles et aux fonctionnalités du système.	
4. Le système protège les fichiers et le système global contre les modifications non autorisées.	
5. Les bulletins de sécurité et mises à jour corrigent régulièrement les vulnérabilités.	
6. Les tests et bonnes pratiques garantissent la sécurité de la plateforme et de l’écosystème Android.	



