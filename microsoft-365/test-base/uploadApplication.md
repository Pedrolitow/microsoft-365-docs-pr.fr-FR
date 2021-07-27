---
title: Téléchargement du package
description: Comment télécharger votre application, les fichiers binaires et les dépendances sur la base de test
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 300b12f66143d72aa2cab6945a4df52d22ced635
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53538828"
---
# <a name="step-2-uploading-a-package"></a>Étape 2 : Téléchargement d’un package

Dans la page Portail de base de test, accédez à la Télécharger nouvelle option de **package** dans la barre de navigation de gauche, comme illustré ci-dessous :

:::image type="content" alt-text="Télécharger un nouveau package." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

Une fois là, suivez les étapes ci-dessous pour télécharger un nouveau package.

## <a name="enter-details-for-your-package"></a>Entrer les détails de votre package

Sous l’onglet Détails du test, tapez le nom, la version et d’autres détails de votre package, comme demandé. 

Vous pouvez faire  des tests fonctionnels et **out-of-box** via ce tableau de bord.

Les étapes ci-dessous fournissent un guide sur la façon de remplir les détails de votre package :

1.  Entrez le nom à donner à votre package dans le `Package name` champ.

    > [!Note]  
    > Le nom du package et la combinaison de version entrés doivent être uniques au sein de votre organisation. Cette vérification est validée par la coche, comme illustré ci-dessous.
  
    - Si vous choisissez de réutiliser le nom d’un package, le numéro de version doit être unique (c’est-à-dire qu’il n’a jamais été utilisé avec un package portant ce nom particulier).

    - Si la combinaison du nom du package + de la version ne passe pas la vérification de l’unicité, vous verrez un message d’erreur qui indique « Le package avec cette version de *package* existe déjà ». 

    :::image type="content" alt-text="Image pour le chargement des instructions de package." source="Media/Instructions.png":::

2. Entrez une version dans le champ « Version du package ».

    :::image type="content" alt-text="Version du package." source="Media/ApplicationVersion.png":::

3.  Sélectionnez le type de test que vous souhaitez exécuter sur ce package.

    Un test **OOB (Out-of-Box)** effectue une  *installation,* un *lancement,* une fermeture et *une désinstallation* de votre package. Après l’installation, la routine de fermeture de lancement est répétée 30 fois avant l’opération de désinstallation unique. 
    
    Ce test OOB vous fournit une télémétrie normalisée sur votre package à comparer entre Windows builds.

    Un **test fonctionnel** exécuterait vos scripts de test téléchargés sur votre package. Les scripts sont exécutés dans la séquence de chargement et un échec dans un script particulier arrête l’exécution des scripts suivants.

    > [!Note]
    > **Tous** les scripts s’exécutent pendant 80 minutes au maximum. 
    
4.  Sélectionnez le type de mise à jour du système d’exploitation.

    - Les « mises à jour de sécurité » permettent de tester votre package sur les évolutions incrémentielles de Windows mises à jour de sécurité mensuelles pré-publiées. 
    - Les « mises à jour des fonctionnalités » permettent de tester votre package par rapport aux mises à jour de fonctionnalités Windows pré-publication bi-annuelles à partir du programme Windows Insider.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Type de mise à jour du système d’exploitation." source="Media/OSUpdateType.png":::

5.  Sélectionnez les versions du système d’exploitation pour les tests de mise à jour de sécurité.

    Dans la sélection multiple, sélectionnez la ou les versions du système d’exploitation Windows votre package sera installé. 

    - Pour tester votre package uniquement sur Windows d’exploitation client, sélectionnez les versions Windows système d’exploitation 11 dans la liste de menus.
    - Pour tester votre package uniquement sur les systèmes d’exploitation Windows Server, sélectionnez les versions Windows système d’exploitation server applicables dans la liste de menus.
    - Pour tester votre package uniquement sur les systèmes d’Windows client et Windows Server, sélectionnez tous les systèmes d’exploitation applicables dans la liste de menus. 

    > [!Note]
    > Si vous choisissez de tester votre package par rapport aux OS serveur et client, assurez-vous que le package est compatible et qu’il peut s’exécuter sur les deux OSes

    :::image type="content" alt-text="Sélection d’une version du système d’exploitation." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6.  Sélectionnez les options pour les tests de mise à jour des fonctionnalités :

    - Dans l’option « Sélectionner le canal Insider », sélectionnez la build par rapport à la build sur qui vos `Windows Insider Program Channel` packages doivent être testés.
  
      Nous utilisons actuellement les builds dont la version d’essai est disponible dans le canal Insider Beta.

    - Dans l’option « Sélectionner la ligne de base du système d’exploitation pour Insight », sélectionnez la version Windows système d’exploitation à utiliser comme base pour comparer les résultats de vos tests. 

    > [!Note]
    > Pour l’instant, nous ne supportons PAS les tests de mise à jour des fonctionnalités pour les serveurs OS
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="Test de mise à jour des fonctionnalités." source="Media/FeatureUpdate.png":::

7.  Une page de détails test terminée doit ressembler à ceci : 

    :::image type="content" alt-text="Affichage des détails du test." source="Media/TestDetails.png":::

## <a name="next-steps"></a>Prochaines étapes

Notre article suivant traite du chargement de vos fichiers binaires vers notre service.

> [!div class="nextstepaction"]
> [Étape suivante](binaries.md)

<!---
Add button for next page
-->

