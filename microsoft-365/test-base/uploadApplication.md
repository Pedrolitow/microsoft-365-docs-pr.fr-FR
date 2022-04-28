---
title: Téléchargement du package
description: Comment charger votre application, vos fichiers binaires et vos dépendances sur la base de test
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 23c21eae9ad149aea5442c0c8a00f716f3d22506
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099474"
---
# <a name="upload-your-test-base-package-zip"></a>Télécharger votre package de base de test (Zip) 

Dans la page du portail de base de test, **accédez** à l’option Nouveau package dans la barre de navigation de gauche, puis cliquez sur **Expérience de chargement héritée** pour activer l’expérience de chargement zip comme indiqué ci-dessous :

:::image type="content" alt-text="Télécharger un nouveau package." source="Media/testapplication01.png" lightbox="Media/testapplication01.png":::

:::image type="content" alt-text="Appliquez l’opération." source="Media/testapplication21.png" lightbox="Media/testapplication21.png":::

Une fois là- bas, suivez les étapes ci-dessous pour charger un nouveau package.

## <a name="enter-details-for-your-package"></a>Entrer les détails de votre package

Sous l’onglet Détails du test, tapez le nom, la version et d’autres détails de votre package, comme demandé.

Vous pouvez effectuer des **tests** fonctionnels et **out-of-box** via ce tableau de bord.

Les étapes ci-dessous fournissent un guide sur la façon de renseigner les détails de votre package :

1. Entrez le nom à donner à votre package dans le `Package name` champ.

    > [!NOTE]
    > Le nom du package et la combinaison de versions entrées doivent être uniques au sein de votre organisation. Cette opération est validée par la coche, comme indiqué ci-dessous.

    - Si vous choisissez de réutiliser le nom d’un package, le numéro de version doit être unique (autrement dit, n’a jamais été utilisé avec un package portant ce nom particulier).

    - Si la combinaison du nom de package + version ne réussit pas la vérification de l’unicité, un message d’erreur indiquant *« Package avec cette version de package existe déjà » s’affiche*.

    :::image type="content" alt-text="Image permettant de charger des instructions de package." source="Media/Instructions.png":::

2. Entrez une version dans le champ « Version du package ».

    :::image type="content" alt-text="Version du package." source="Media/ApplicationVersion.png":::

3. Sélectionnez le type de test que vous souhaitez exécuter sur ce package.

    Un test **OOB (Out-of-Box)** effectue une *installation*, un *lancement*, une *fermeture* et une *désinstallation* de votre package. Après l’installation, la routine de fermeture de lancement est répétée 30 fois avant l’exécution d’une seule désinstallation.

    Ce test OOB vous fournit des données de télémétrie standardisées sur votre package à comparer entre les builds Windows.

    Un **test fonctionnel** exécuterait votre ou vos scripts de test chargés sur votre package. Les scripts sont exécutés dans une séquence de chargement et un échec dans un script particulier empêche l’exécution des scripts suivants.

    > [!NOTE]
    > **Tous les** scripts s’exécutent pendant 80 minutes au maximum.

4. Sélectionnez le type de mise à jour du système d’exploitation.

    - Les « mises à jour de sécurité » permettent de tester votre package sur les évolutions incrémentielles de Windows mises à jour de sécurité mensuelles préversion.
    - Les « mises à jour des fonctionnalités » permettent de tester votre package par rapport à Windows versions de mises à jour de fonctionnalités bi-annuelles préversion du programme Windows Insider.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Type de mise à jour du système d’exploitation." source="Media/OSUpdateType.png":::

5. Sélectionnez la ou les versions du système d’exploitation pour les tests de mise à jour de sécurité.

    Dans la liste déroulante à sélection multiple, sélectionnez la ou les versions du système d’exploitation de Windows votre package sera installé.

    - Pour tester votre package uniquement sur Windows systèmes d’exploitation clients, sélectionnez les versions de système d’exploitation client Windows applicables dans la liste de menus.
    - Pour tester votre package uniquement sur Windows systèmes d’exploitation serveur, sélectionnez les versions de système d’exploitation Windows Server applicables dans la liste de menus.
    - Pour tester votre package sur Windows système d’exploitation client et Windows Server, sélectionnez tous les systèmes d’exploitation applicables dans la liste de menus.

    > [!NOTE]
    > Si vous sélectionnez de tester votre package sur les systèmes d’exploitation serveur et client, assurez-vous que le package est compatible et qu’il peut s’exécuter sur les deux systèmes d’exploitation.

    :::image type="content" alt-text="Sélection d’une version du système d’exploitation." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. Sélectionnez les options pour les tests de mise à jour des fonctionnalités :

    - Dans l’option « Sélectionner le canal Insider », sélectionnez la `Windows Insider Program Channel` build sur laquelle vos packages doivent être testés.

      Nous utilisons actuellement des builds en version d’évaluation dans le canal bêta Insider.

    - Dans l’option « Sélectionner la base de référence du système d’exploitation pour Insight », sélectionnez la Windows version du système d’exploitation à utiliser comme base de référence pour comparer vos résultats de test.

    > [!NOTE]
    > Nous ne prenons PAS en charge les tests de mise à jour des fonctionnalités pour les systèmes d’exploitation serveur pour l’instant
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Test de mise à jour des fonctionnalités." source="Media/FeatureUpdate.png":::

7. Une page de détails de test terminée doit ressembler à ceci :

    :::image type="content" alt-text="Affichage des détails du test." source="Media/TestDetails.png":::



## <a name="upload-your-binaries-dependencies-and-scripts"></a>Télécharger vos fichiers binaires, dépendances et scripts

Dans cet onglet, vous allez charger un package zip unique contenant vos fichiers binaires, dépendances et scripts utilisés pour exécuter votre suite de tests.

> [!NOTE]
> La taille du package zip doit être comprise entre un minimum de 10 Mo et un maximum de 2 Go.

**fichier zip de package Télécharger**

:::image type="content" alt-text="Télécharger vos fichiers binaires." source="Media/AddBinaries.png":::

  - Les dépendances chargées peuvent inclure des frameworks de test, des moteurs de script ou des données accessibles pour exécuter votre application ou les cas de test. Par exemple, vous pouvez charger Selenium et un programme d’installation de pilote web pour vous aider à exécuter des tests basés sur un navigateur.
  - Il est recommandé de s’assurer que vos activités de script sont conservées modulaires, c’est-à-dire. 
    - Le `Install` script effectue uniquement des opérations d’installation.
    - Le `Launch` script lance uniquement l’application.
    - Le `Close` script ferme uniquement l’application.
    - Le script facultatif `Uninstall` désinstalle uniquement l’application.

**Actuellement, le portail prend uniquement en charge les scripts PowerShell.**



## <a name="the-tasks-tab"></a>Onglet Tâches

Sous l’onglet Tâches, vous devez fournir les chemins d’accès à vos scripts de test qui se trouvent dans le dossier zip que vous avez chargé sous l’onglet binaires.

  - **Scripts de test out of box :** Tapez les chemins relatifs de vos scripts d’installation, de lancement, de fermeture et de désinstallation. Vous avez également la possibilité de sélectionner des paramètres supplémentaires pour le script d’installation.
  - **Scripts de test fonctionnel :** Tapez le chemin relatif de chaque script de test fonctionnel chargé. Des scripts de test fonctionnel supplémentaires peuvent être ajoutés à l’aide du ```Add Script``` bouton. Vous avez besoin d’au moins un (1) script et pouvez ajouter jusqu’à huit (8) scripts de test fonctionnels. 
  
    Les scripts s’exécutent dans la séquence dans laquelle ils sont répertoriés. Un échec dans un script particulier empêche l’exécution des scripts suivants.
    Vous avez également la possibilité de sélectionner des paramètres supplémentaires pour chaque script fourni.

**Définir le chemin d’accès du script**

:::image type="content" alt-text="Image de la tâche de test." source="Media/testtask.png":::

Voici un exemple de comment fournir le chemin relatif sur une structure de dossiers :

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1l’aurais** fait. _ScriptX.ps1_ comme chemin d’accès relatif.
  - **Script.ps1** aurait _dossier1/script.ps1_ comme chemin d’accès relatif.



## <a name="choose-your-test-options"></a>Choisissez vos options de test. 

L’onglet ```Test Options``` s’applique aux utilisateurs qui souhaitent effectuer des tests fonctionnels pour indiquer quand le correctif Windows Update doit être appliqué dans la séquence d’exécution de leurs scripts de test fonctionnels.

:::image type="content" alt-text="Image des options de test. Tests fonctionnels ou out-of-box." source="Media/testoptions.png":::

Sélectionnez _**Vérifier**_ pour accéder à l’onglet suivant et passer en revue les options de test sélectionnées.



## <a name="review-your-selections-to-create-your-package"></a>Passez en revue vos sélections pour créer votre package.

1. Dans cet onglet, le service affiche les détails de votre test et exécute une vérification rapide de l’exhaustivité.

    Un message **d’échec de validation ou de** **validation** indique si vous pouvez passer aux étapes suivantes ou non.

2. Passez en revue les détails de votre test et, si vous êtes satisfait, cliquez sur le bouton **Créer** .

    :::image type="content" alt-text="Afficher la validation." source="Media/validation.png" lightbox="Media/validation.png":::

3. Cela intégrera votre package à l’environnement de base de test. Si votre package est créé avec succès, un test automatisé qui vérifie si votre package peut être exécuté correctement sur Azure est déclenché.

    :::image type="content" alt-text="Résultat réussi." source="Media/successful.png":::

    > [!NOTE]
    > Vous recevrez une notification de la Portail Azure pour vous informer de la réussite ou de l’échec de la vérification du package.
    >
    > Notez que le processus peut prendre jusqu’à 24 heures. Il est donc probable que votre page web ait expiré si vous n’y êtes pas actif. Par conséquent, la notification ne vous informera pas de la fin de cette exécution à la demande.

    - Si cela se produit, vous pouvez afficher l’état de votre package sous l’onglet **Gérer les packages** .

      :::image type="content" alt-text="Image pour la gestion des packages." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - Pour les tests réussis, leurs résultats sont visibles via les pages **Résumé** des tests, **Résultats des mises à jour de sécurité** et **Résultats des mises à jour** des fonctionnalités à intervalles réguliers, souvent quelques jours après votre chargement.
  
    - En cas d’échec des tests, vous devez charger un nouveau package. 

      Vous pouvez télécharger les **journaux de test** pour une analyse plus approfondie à partir des **pages de résultats des mises à jour de sécurité** et des **mises à jour des** fonctionnalités.

    - Si vous rencontrez des échecs de test répétés, contactez testbasepreview@microsoft.com avec les détails de votre erreur.

## <a name="next-steps"></a>Étapes suivantes

Découvrez nos instructions de contenu via le lien ci-dessous.

> [!div class="nextstepaction"]
> [Étape suivante](contentguideline.md)
