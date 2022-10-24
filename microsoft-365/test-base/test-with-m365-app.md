---
title: Tester votre application avec les dernières applications Microsoft 365
description: Comment tester votre application avec les dernières applications Microsoft 365
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 10/21/2022
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 8fa106208f537ea67202eaa6a60b700c2854614a
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68685274"
---
# <a name="test-your-application-with-latest-microsoft-365-apps"></a>Tester votre application avec les dernières applications Microsoft 365


Cette section fournit des instructions sur la façon de tester votre application avec les dernières applications Microsoft 365.

> [!IMPORTANT]
> Actuellement, seule la préversion de Office 365 du canal de préversion mensuelle est disponible.


### <a name="choose-the-microsoft-365-application"></a>Choisir l’application Microsoft 365 

Dans l’étape **Configurer le test** lors de l’intégration d’un nouveau package, activez le bouton bascule **Préinstaller les applications Microsoft** pour permettre à l’utilisateur de choisir la version préliminaire des applications Microsoft 365 avec la dernière mise à jour à installer à des fins de test.

 > [!div class="mx-imgBorder"]  
 > ![Capture d’écran montrant le test de configuration du package](Media/testwithm365app01.png)  
 > [!NOTE] 
 > Comme le canal Office preview fournit des mises à jour Office en préversion avec une cadence mensuelle, seul le type de **mise à jour de sécurité** est activé pour le package une fois que le bouton bascule est activé. Les versions du système d’exploitation Windows qui pourraient être sélectionnées dans la matrice de test seront également limitées aux produits Windows pour lesquels le produit Office choisi est disponible. En raison des conditions préalables mentionnées, si vous souhaitez activer la fonctionnalité de test de mise à jour Office pour les packages existants, le type de mise à jour non pris en charge et les produits du système d’exploitation Windows sont désactivés par défaut.

&nbsp;  
### <a name="define-the-install-sequence-for-the-chosen-microsoft-365-application"></a>Définir la séquence d’installation de l’application Microsoft 365 choisie 

Vous pouvez utiliser **le test fonctionnel** pour définir la séquence d’installation de la version préliminaire d’Office avec la dernière mise à jour. Cliquez sur l’icône **Ouvrir le panneau de test fonctionnel** comme ci-dessous après avoir créé votre propre script et ajouté à la liste des tests fonctionnels.

 > [!div class="mx-imgBorder"]  
 > ![Capture d’écran montrant le package de modification du package](Media/testwithm365app02.png)

Vous serez en mesure de réorganiser les scripts dans le panneau de liste fonctionnelle en faisant glisser les éléments vers le haut et le bas jusqu’à l’étape appropriée. Choisissez l’étape à laquelle exécuter l’installation d’Office en sélectionnant le script avant lequel vous souhaitez que l’installation d’Office en préversion se produise.  

Dans l’exemple ci-dessous, Windows Update sera installé en premier, suivi du script de préinstallation, puis la préversion Office sera installée avant le script d’installation de l’application de l’utilisateur, après quoi le script d’exécution-test sera exécuté.

 > [!div class="mx-imgBorder"]  
 > ![Capture d’écran montrant le test fonctionnel](Media/testwithm365app03.png)  
 > [!NOTE]
 > Pour le type de test Out of box, l’installation d’Office est exécutée par défaut après l’installation de Windows Update et avant l’exécution du script d’installation.

&nbsp;  
### <a name="view-the-test-result-with-microsoft-365-application"></a>Afficher le résultat du test avec l’application Microsoft 365  

Une série de tests est exécutée une fois que le package a réussi la validation. Sur une base mensuelle, une exécution automatisée sera planifiée à chaque mardi de correctif lorsque la dernière mise à jour de sécurité Windows sera publiée. Le package installe la dernière version préliminaire d’Office à partir du canal de préversion mensuelle à compter de la date d’exécution correspondante pour permettre à votre application d’être testée par rapport aux dernières mises à jour Windows et Office.

Vous pouvez afficher les résultats des séries de tests sous la page Résumé du test en cliquant sur le lien sur le nom du package.

 > [!div class="mx-imgBorder"]  
 > ![Capture d’écran montrant la mise à jour de sécurité](Media/testwithm365app04.png)

&nbsp;  
Dans la page détaillée, vous verrez install-Office sous la forme d’un script exécuté automatiquement qui représente l’état de l’installation d’Office en préversion.

 > [!div class="mx-imgBorder"]  
 > ![Capture d’écran montrant la fiabilité](Media/testwithm365app05.png)  
 > [!NOTE]
 > Pour le type de test Out of box, un script de test d’interopérabilité Office prédéfini est exécuté pour aider à collecter les signaux de conflit pour la préversion d’Office exécuté avec l’application installée de l’utilisateur par défaut. Vous pouvez utiliser le test fonctionnel pour définir votre propre flux de test et contourner le script de test Office si vous souhaitez vous concentrer sur le test du fonctionnement de votre application avec les dernières mises à jour Office.
