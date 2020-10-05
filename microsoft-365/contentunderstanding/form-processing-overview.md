---
title: Vue d’ensemble du traitement des formulaires
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: Priority
description: En savoir plus sur le traitement de formulaires dans Microsoft SharePoint Syntex
ms.openlocfilehash: bbdf318b7d0c4a9f58cc79453dfaaf0daf5b9a5c
ms.sourcegitcommit: b06a4f21da247edb03fdf6a01eafb7d4fb387b33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48333900"
---
# <a name="form-processing-overview"></a>Vue d’ensemble du traitement des formulaires

 ![Générateur d’intelligence artificielle](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex utilise le traitement de formulaire Microsoft PowerApps [AI Builder](https://docs.microsoft.com/ai-builder/overview) pour créer des modèles au sein de bibliothèques de documents SharePoint.

Vous pouvez utiliser le traitement de formulaire du générateur AI pour créer des modèles AI qui utilisent la technologie d’apprentissage automatique pour identifier et extraire des paires clés et des données de tableau à partir de documents structurés ou semi-structurés, tels que les formulaires et les factures.

Les organisations reçoivent souvent des factures en grande quantité provenant de sources variées, telles que le courrier, les télécopies, la messagerie, etc. Le traitement de ces documents et leur saisie manuelle dans une base de données peut prendre beaucoup de temps. L’utilisation de l’AI pour extraire le texte, les paires clé/valeur et les tables de vos documents, le traitement de formulaire automatise ce processus. 

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios de traitement de formulaires, consultez l’article [SharePoint Syntex adoption : Guide de démarrage](https://docs.microsoft.com/microsoft-365/contentunderstanding/adoption-getstarted#form-processing-scenario-example).

Par exemple, vous pouvez créer un modèle de traitement de formulaire qui identifie tous les documents de bon de commande téléchargés dans la bibliothèque de documents. À partir de chaque bon de commande, vous pouvez extraire et afficher des données spécifiques qui vous sont importantes, telles que *numéro de bon de commande*, *date* ou *coût total*.

![Vue de la bibliothèque de documents](../media/content-understanding/doc-lib-done.png)</br>  

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est acquise en formant votre modèle ; il apprend à extraire vos données à partir d’emplacements similaires dans vos formulaires, car ils ont une disposition similaire. 

Vous avez besoin d’un minimum de cinq documents de formulaires pour commencer. AI analyse vos exemples de fichiers pour les paires clé-valeur, puis identifie manuellement celles qui n’ont pas été détectées.  Le générateur AI vous permet de tester la précision de votre modèle dans vos exemples de fichiers.

Une fois que vous avez créé votre modèle et que vous l’avez créé, vous pouvez l’utiliser pour créer un flux de [Power Automated Flow](https://docs.microsoft.com/power-automate/getting-started) qui s’exécute suite au téléchargement d’un fichier dans la bibliothèque de documents SharePoint. Il extrait ensuite les données qui ont été identifiées dans le modèle. Les données extraites s’affichent dans les colonnes de la vue bibliothèque de documents de votre modèle.

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est acquise en formant votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. AI analyse vos exemples de fichiers pour les paires clé-valeur, puis identifie manuellement celles qui n’ont pas été détectées.  Le générateur AI vous permet de tester la précision de votre modèle dans vos exemples de fichiers.

Une fois que vous avez créé votre modèle et que vous l’avez publié, celui-ci crée un [Power Automate Flow](https://docs.microsoft.com/power-automate/getting-started). Le flux s’exécute lorsqu’un fichier est téléchargé dans la bibliothèque de documents SharePoint et extrait les données qui ont été identifiées dans le modèle. Les données extraites s’affichent dans les colonnes de la vue bibliothèque de documents de votre modèle.

Un administrateur Office 365 doit [activer le traitement de formulaires](https://docs.microsoft.com/microsoft-365/contentunderstanding/set-up-content-understanding#to-set-up-content-understanding)pour la bibliothèque de documents SharePoint pour permettre aux utilisateurs de [créer un modèle de traitement de formulaire](create-a-form-processing-model.md) dans celui-ci.



## <a name="see-also"></a>Voir aussi
  
[Documentation Power Automate](https://docs.microsoft.com/power-automate/)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Présentation de la présentation des documents](document-understanding-overview.md)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)
