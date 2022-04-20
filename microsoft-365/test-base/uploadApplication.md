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
ms.openlocfilehash: 9ee299c0972ed4e286e5a660f5082dd5632167e4
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934266"
---
# <a name="upload-your-test-base-package-zip"></a>Télécharger votre package de base de test (Zip) 

Dans la page du portail de base de test, accédez à la **Télécharger nouvelle** option de package dans la barre de navigation de gauche, comme indiqué ci-dessous :

:::image type="content" alt-text="Télécharger un nouveau package." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

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

## <a name="next-steps"></a>Étapes suivantes

Notre prochain article traite du chargement de vos fichiers binaires dans notre service.

> [!div class="nextstepaction"]
> [Étape suivante](binaries.md)

<!---
Add button for next page
-->
