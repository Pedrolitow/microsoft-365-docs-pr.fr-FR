---
title: Vue d’ensemble du traitement des formulaires (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.service: ''
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: En savoir plus sur le traitement de formulaire dans le projet cortex.
ms.openlocfilehash: dbea06cdf2dbb232a7ea48c78d7ea968dd18b9c0
ms.sourcegitcommit: a3a5dc541b0c971608cc86ef480509c25a13ca60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46612725"
---
# <a name="form-processing-overview-preview"></a>Vue d’ensemble du traitement des formulaires (aperçu)
> [!Note]
> Le contenu de cet article est destiné à Project cortex privé preview. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

Le projet cortex utilise le traitement des formulaires Microsoft PowerApp. [ai Builder](https://docs.microsoft.com/ai-builder/overview) pour créer des modèles dans les bibliothèques de documents SharePoint.
Vous pouvez utiliser le traitement des formulaires du générateur AI pour créer des modèles AI qui utilisent la technologie machine learning pour identifier et extraire des paires clé-valeur et des données de tableau à partir de documents structurés ou semi-structurés, comme le formulaire et les factures.

Les entreprises reçoivent souvent des factures en grandes quantités et provenant de diverses sources, telles que des courriers électroniques, des télécopies, des messages électroniques ou en personne. Le traitement de ces documents et leur saisie manuelle dans votre base de données peuvent prendre beaucoup de temps. En utilisant l’IA pour extraire le texte, les paires clé/valeur et les tables de vos documents, le traitement de formulaire automatisera ce processus. 

Par exemple, vous pouvez créer un modèle de traitement de formulaire qui identifie tous les documents de bons de commande chargés dans la bibliothèque de documents. Et à partir de chaque bon de commande, vous pouvez extraire et afficher des données spécifiques importantes pour vous, telles que le *numéro de bon de commande*, la *Date*ou le *coût total*.

Vous utilisez des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est une formation sur votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. Les composants AI Building analysent vos exemples de fichiers pour les paires clé-valeur et vous pouvez également identifier manuellement ceux qui n’ont pas été détectés.  Le générateur AI vous permet de tester la précision de votre modèle sur vos fichiers d’exemple.

Une fois que vous avez formé et publié votre modèle, vous pouvez l’utiliser pour créer un [flux automate de puissance](https://docs.microsoft.com/power-automate/getting-started) qui s’exécutera lorsqu’un fichier est téléchargé vers la bibliothèque de documents SharePoint et extraira les données qui ont été identifiées dans le modèle. Les données extraites s’afficheront dans les colonnes de la vue bibliothèque de documents de votre modèle.

Un administrateur Office 365 doit [activer le traitement de formulaire](https://docs.microsoft.com/microsoft-365/contentunderstanding/set-up-content-understanding?view=o365-worldwide#to-set-up-content-understanding) pour la bibliothèque de documents SharePoint afin que les utilisateurs puissent [créer un modèle de traitement de formulaire](create-a-form-processing-model.md) dans celui-ci.



## <a name="see-also"></a>Voir aussi
  
[Mise à l’arrêt de la documentation](https://docs.microsoft.com/power-automate/)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>
[Présentation de l’explication des documents](document-understanding-overview.md)</br>
[Formation : améliorer les performances d’entreprise avec le générateur AI](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)</br>




