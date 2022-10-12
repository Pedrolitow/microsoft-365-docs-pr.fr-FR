---
title: Chargement d’un package zip prédéfagé
description: Guide pratique pour modifier, charger et tester un fichier .zip prédéfbrié sur la base de test
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: b2bb536df28f2b63114aa604241688458428760e
ms.sourcegitcommit: 893add1e40c3e26e5624663eaf272d12a72d0141
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68539980"
---
# <a name="uploading-a-pre-built-zip-package"></a>Chargement d’un package zip prédéfagé

Cette section fournit toutes les étapes nécessaires pour modifier, charger et tester sur la base de test lorsque vous disposez déjà d’un fichier .zip prédéfiné.

**Pré-demandes**

   - Compte de base de test : si vous n’avez pas de compte **de base** de test, vous devez en créer un avant de continuer, comme décrit dans [la création d’un compte de base de test](createAccount.md).
   - Fichier de .zip prédéf .zip créé hors connexion contenant le fichier binaire et les scripts de test de votre application. Voir [Créer un package | Microsoft Docs](buildpackage.md) préparer votre package de .zip de base de test à partir du bureau.

## <a name="upload-an-offline-built-package"></a>Charger un package généré hors connexion

Dans le [Portail Azure](https://portal.azure.com/), accédez au compte **de base** de test pour lequel vous allez créer et charger votre package, puis suivez les étapes ci-dessous.

Dans le menu de gauche sous **Catalogue de packages**, sélectionnez le **nouveau package**. Sélectionnez ensuite la troisième carte **« Charger le package prédéffagé** ».

> [!div class="mx-imgBorder"]
> [![Menu](Media/uploadingzip01-new-package.png) de gauche ](Media/uploadingzip01-new-package.png#lightbox)

### <a name="step-1-define-content"></a>Étape 1. Définir le contenu

1. Dans la section **Source du package** , sélectionnez Package prédéfiné (.zip) dans le type de source du package.

   > [!div class="mx-imgBorder"]
   > [![Nouveau package](Media/uploadingzip02-define-content.png) ](Media/uploadingzip02-define-content.png#lightbox)

2. Chargez votre fichier de package prédéfagé (zip) en sélectionnant le bouton « Sélectionner un fichier ».

3. Tapez le nom et la version de votre package dans la section **Informations de base** .

   > [!NOTE]
   > La combinaison du nom et de la version du package doit être unique dans votre compte de base de test.

   > [!div class="mx-imgBorder"]
   > ![Informations de base](Media/uploadingzip03-basic-information.png)

4. Une fois toutes les informations demandées spécifiées, sélectionnez le bouton **Suivant : Test de configuration** .

   > [!div class="mx-imgBorder"]
   > ![Suivant : Test de configuration](Media/uploadingzip04-next.png)

### <a name="step-2-configure-test"></a>Étape 2. Configurer le test

1. Sélectionnez le **type de test** en fonction de votre package prédéfagé. Deux types de test sont pris en charge :

   - Un **test OOB (Out of Box)** effectue une installation, un lancement, une fermeture et une désinstallation de votre package. Après l’installation, la routine de fermeture de lancement est répétée 30 fois avant l’exécution d’une seule désinstallation. Le test OOB vous fournit des données de télémétrie standardisées sur votre package à comparer entre les builds Windows.
   - Un **test fonctionnel** exécute vos scripts de test chargés sur votre package. Les scripts sont exécutés dans la séquence que vous avez spécifiée et un échec dans un script particulier arrête l’exécution des scripts suivants.

   > [!NOTE]
   > Le test Out of Box est désormais facultatif.

   > [!div class="mx-imgBorder"]
   > [![Option](Media/uploadingzip05-configure-test.png) de test Out of Box ](Media/uploadingzip05-configure-test.png#lightbox)

2. Une fois toutes les informations requises remplies, sélectionnez le bouton Suivant.

### <a name="step-3-edit-package"></a>Étape 3. Modifier le package

1. Sous l’onglet Modifier le package, vous pouvez :
   - vérifiez votre dossier de package et votre structure de fichiers dans la **préversion du package**.
   - modifiez vos scripts en ligne avec **l’éditeur de code PowerShell**.

   > [!NOTE]
   > Votre package prédéfini est extrait pour modification. Les balises de script sont ajoutées en fonction du nom du script. Passez en revue ces balises de script et ajustez-les si nécessaire. Les balises de script indiquent les chemins de script corrects qui seront utilisés lors du lancement du test.

   > [!div class="mx-imgBorder"]
   > [![Éditeur](Media/uploadingzip06-edit-package.png) de code PowerShell ](Media/uploadingzip06-edit-package.png#lightbox)

2. Dans la **préversion du package**, selon vos besoins, vous pouvez :

   - créer un dossier.
   - créer un script.
   - charger un nouveau fichier.

3. Sous **le dossier scripts**, des exemples de scripts et des balises de script ont été créés pour vous. Toutes les balises de script sont modifiables. Vous pouvez les réaffecter pour référencer vos chemins d’accès de script.

   - Si le **test Out of Box** est sélectionné à l’étape 2, vous pouvez voir le dossier **outofbox** sous le dossier des scripts. Vous pouvez également choisir d’ajouter la balise **« Redémarrer après l’installation »** pour le script d’installation.

   > [!div class="mx-imgBorder"]
   > [![Exemples de scripts et balises](Media/uploadingzip07-edit-script.png) de script ](Media/uploadingzip07-edit-script.png#lightbox)

   > [!NOTE]
   > Les balises d’installation, de lancement et de fermeture de script sont obligatoires pour le type de test OOB. La réaffectation des balises garantit que le chemin d’accès de script approprié sera utilisé lors du lancement du test.

   > [!div class="mx-imgBorder"]
   > [![Notification des scripts manquants](Media/uploadingzip08-required-prompt.png) ](Media/uploadingzip08-required-prompt.png#lightbox)

   - Si le **test fonctionnel** est sélectionné à l’étape 2, vous pouvez voir le dossier **fonctionnel** sous le dossier des scripts. Vous pouvez ajouter d’autres scripts de test fonctionnels à l’aide du bouton **« Ajouter à la liste de tests fonctionnels** ». Vous avez besoin d’au moins un (1) script et pouvez ajouter jusqu’à huit (8) scripts de test fonctionnels.

   > [!div class="mx-imgBorder"]
   > [![Ajouter à la liste de tests fonctionnels](Media/uploadingzip09-add-to-list.png) ](Media/uploadingzip09-add-to-list.png#lightbox)

   > [!NOTE]
   > Au moins 1 balise de script fonctionnel est obligatoire pour le type de test fonctionnel.

   Sélectionnez **Ajouter à la liste de tests fonctionnels** pour ajouter d’autres scripts fonctionnels à partir du panneau d’action. Les options suivantes sont disponibles :

   - Réorganisez les chemins d’accès de script en faisant glisser les boutons de sélection gauche. Les scripts fonctionnels s’exécutent dans la séquence dans laquelle ils sont répertoriés. Un échec dans un script particulier empêche l’exécution des scripts suivants.
   - Définissez « Redémarrer après l’exécution » pour plusieurs scripts.
   - Appliquer la mise à jour avant sur un chemin d’accès de script spécifique. Cette mise à jour s’applique aux utilisateurs qui souhaitent effectuer des tests fonctionnels pour indiquer quand le correctif Windows Update doit être appliqué dans la séquence d’exécution de leurs scripts de test fonctionnel.

   > [!div class="mx-imgBorder"]
   > [![Test](Media/uploadingzip10-functional-test.png) fonctionnel ](Media/uploadingzip10-functional-test.png#lightbox)

4. Une fois toutes les informations requises renseignées, vous pouvez passer à l’étape 4 en sélectionnant le bouton Suivant en bas.

### <a name="step-4-set-test-matrix"></a>Étape 4. Définir la matrice de test

L’onglet Matrice de test vous permet d’indiquer le programme de mise à jour Windows spécifique ou le produit Windows sur lequel vous souhaitez peut-être exécuter votre test.

   > [!div class="mx-imgBorder"]
   > ![Définir un nouveau package de matrice de test](Media/settestmatrix01-newpackage.png)

1. Choisir le **type de mise à jour du système d’exploitation**
   - La base de tests fournit des tests planifiés pour vous assurer que les performances de vos applications ne seront pas interrompues par les dernières mises à jour windows. 

   > [!div class="mx-imgBorder"]
   > ![Définir la matrice de test choisir osupdate](Media/settestmatrix02-chooseosupdate.png)

   - Il existe 2 options disponibles :
   
     - Les **mises à jour de sécurité** permettent de tester votre package par rapport aux évolutions incrémentielles des mises à jour de sécurité mensuelles Windows.
     - Les **mises à jour des fonctionnalités** permettent de tester votre package par rapport aux nouvelles fonctionnalités des dernières versions Windows Insider Preview du programme Windows Insider.

2. Configurer la **mise à jour de sécurité** Pour configurer les mises à jour de sécurité, vous devez spécifier le ou les produits Windows que vous souhaitez tester dans la liste déroulante « Versions de système d’exploitation à tester ».

   > [!div class="mx-imgBorder"]
   > ![Définir la matrice de test pour configurer securityupdate](Media/settestmatrix03-configuresecurityupdate.png)

   - Votre sélection inscrit votre application pour les séries de tests automatiques sur la version B des mises à jour de qualité mensuelles Windows des produits sélectionnés.
     - Pour les clients disposant d’un accès par défaut sur la base de test, leurs applications sont validées par rapport à la version finale des mises à jour de sécurité de la version B, à partir de Patch Tuesday.
     - Pour les clients disposant d’un accès complet sur la base de test, leurs applications sont validées par rapport aux versions préliminaires des mises à jour de sécurité de la version B, à compter de 3 semaines avant le correctif mardi. Cela permet aux clients d’accès complet de prendre des mesures proactives pour résoudre les problèmes détectés lors des tests avant la publication finale du correctif mardi.  
       (Comment devenir un client d’accès complet ? Reportez-vous à [la demande de modification du niveau d’accès | Microsoft Docs](accesslevel.md))

3. Configurer **la mise à jour des fonctionnalités**
   - Pour configurer les mises à jour des fonctionnalités, vous devez spécifier le produit cible et son canal d’aperçu dans la liste déroulante « Insider Channel ».

   > [!div class="mx-imgBorder"]
   > ![Définir la matrice de test pour configurer featureupdate](Media/settestmatrix04-configurefeatureupdate.png)

   - Votre sélection inscrit votre application pour les tests automatiques sur les dernières mises à jour de fonctionnalités de votre canal de produit sélectionné et toutes les nouvelles mises à jour futures dans les dernières versions Windows Insider Preview de votre sélection.

   - Vous pouvez également définir votre système d’exploitation actuel dans « Base de référence du système d’exploitation pour Insight ». Nous vous fournirons plus d’insights de test en effectuant une analyse de régression de votre environnement de système d’exploitation en l’état et du système d’exploitation cible le plus récent.

   > [!div class="mx-imgBorder"]
   > ![Définir le système d’exploitation de jeu de matrices de test](Media/settestmatrix05-setos.png)  

### <a name="step-5-review--publish"></a>Étape 5. Vérifier + publier

1. Passez en revue toutes les informations pour vérifier l’exactitude et l’exactitude de votre brouillon de package. Pour apporter des corrections, vous pouvez revenir aux premières étapes où vous avez spécifié les paramètres en fonction des besoins.

   > [!div class="mx-imgBorder"]
   > [![Vérifier et publier](Media/uploadingzip12-review.png) ](Media/uploadingzip12-review.png#lightbox)

2. Vous pouvez également cocher la case de notification pour recevoir la notification par e-mail de votre package pour l’avis d’exécution de validation.

   > [!div class="mx-imgBorder"]
   > ![Notification](Media/uploadingzip13-notification.png)

3. Lorsque vous avez terminé de finaliser la configuration des données d’entrée, sélectionnez **Publier** pour charger votre package dans la base de test. La notification qui suit s’affiche lorsque le package est correctement publié et qu’il est entré dans le processus de vérification.

   > [!NOTE]
   > Le package doit être vérifié avant d’être accepté pour les tests futurs. La vérification peut prendre jusqu’à 24 heures, car elle inclut l’exécution du package dans un environnement de test réel.

   > [!div class="mx-imgBorder"]
   > ![Publier une notification de réussite](Media/uploadingzip14-success.png)

4. Vous serez redirigé vers la page **Gérer les packages** pour vérifier la progression de votre package nouvellement chargé.

   > [!div class="mx-imgBorder"]
   > [![Gérer les packages](Media/uploadingzip15-package-list.png) ](Media/uploadingzip15-package-list.png#lightbox)

   > [!NOTE]
   > Une fois le processus de vérification terminé, l’état de vérification passe à Accepté. À ce stade, aucune autre action n’est requise. Votre package est acquis automatiquement pour l’exécution chaque fois que vos systèmes d’exploitation configurés disposent de nouvelles mises à jour. Si le processus de vérification échoue, votre package n’est pas prêt pour le test. Vérifiez les journaux et évaluez si des erreurs se sont produites. Vous devrez peut-être également vérifier les paramètres de configuration de votre package à la recherche de problèmes potentiels.


## <a name="continue-package-creation"></a>Continuer la création du package

Si vous avez des packages brouillons précédents, vous pouvez afficher la liste de vos packages brouillons enregistrés sur la page **Nouveau package** . Vous pouvez continuer votre modification directement à l’étape que vous avez suspendue la dernière fois en sélectionnant l’icône de crayon « Modifier ».

> [!div class="mx-imgBorder"]
> [![Page Nouveau package](Media/uploadingzip16-draft-packages.png) ](Media/uploadingzip16-draft-packages.png#lightbox)

> [!NOTE]
> Le tableau de bord affiche uniquement le package en cours d’exécution. Pour le package publié, vous pouvez consulter la page Gérer les packages.
