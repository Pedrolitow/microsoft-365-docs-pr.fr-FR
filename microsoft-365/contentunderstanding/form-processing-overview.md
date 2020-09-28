---
title: Vue d’ensemble du traitement des formulaires
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: En savoir plus sur le traitement de formulaire dans Microsoft SharePoint Syntex
ms.openlocfilehash: 518bc13017762bbe21420a81726e89c9c327834d
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295175"
---
# <a name="form-processing-overview-preview"></a>Vue d’ensemble du traitement des formulaires (aperçu)

Le contenu de cet article est destiné à la préversion privée du projet cortex. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

Le projet cortex utilise le traitement des formulaires Microsoft PowerApp. [ai Builder](https://docs.microsoft.com/ai-builder/overview) pour créer des modèles dans les bibliothèques de documents SharePoint.

Vous pouvez utiliser le traitement des formulaires du générateur AI pour créer des modèles AI qui utilisent la technologie machine learning pour identifier et extraire des paires clé-valeur et des données de tableau à partir de documents structurés ou semi-structurés, tels que les formulaires et les factures.

Utilisez le traitement des formulaires AI Builder pour créer des modèles AI qui utilisent la technologie machine learning (ML) pour identifier et extraire des paires clé-valeur et des données de tableau à partir de documents structurés ou semi-structurés, tels que les formulaires et les factures.

Les organisations reçoivent souvent des factures en grandes quantités provenant de différentes sources, telles que des courriers électroniques, des fax, des courriers électroniques, etc. Le traitement de ces documents et leur saisie manuelle dans une base de données peuvent prendre beaucoup de temps. En utilisant l’IA pour extraire le texte, les paires clé/valeur et les tables de vos documents, le traitement de formulaire automatise ce processus. 

Par exemple, vous pouvez créer un modèle de traitement de formulaire qui identifie tous les documents de bons de commande chargés dans la bibliothèque de documents. À partir de chaque bon de commande, vous pouvez extraire et afficher des données spécifiques importantes pour vous, telles que le *numéro de bon de commande*, la *Date*ou le *coût total*.

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est une formation sur votre modèle. Vous avez besoin d’un minimum de cinq documents de formulaires pour commencer. AI Building analyse vos fichiers d’exemple pour les paires clé-valeur, puis identifie manuellement ceux qui n’ont peut-être pas été détectés.  Le générateur AI vous permet de tester la précision de votre modèle sur vos fichiers d’exemple.

Une fois que vous avez formé et publié votre modèle, utilisez-le pour créer un [flux automatique d’alimentation](https://docs.microsoft.com/power-automate/getting-started) qui s’exécute après le chargement d’un fichier dans la bibliothèque de documents SharePoint. Il extrait ensuite les données qui ont été identifiées dans le modèle. Les données extraites s’afficheront dans les colonnes de la vue bibliothèque de documents de votre modèle.

Vous utilisez des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est une formation sur votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. Le générateur AI analyse vos fichiers d’exemple pour les paires clé-valeur, et vous pouvez également identifier manuellement ceux qui n’ont pas été détectés.  Le générateur AI vous permet de tester la précision de votre modèle sur vos fichiers d’exemple.

Une fois que vous avez formé et publié votre modèle, vous pouvez l’utiliser pour créer un [flux Automated Power](https://docs.microsoft.com/power-automate/getting-started). Le flux s’exécute lorsqu’un fichier est téléchargé vers la bibliothèque de documents SharePoint et extrait les données qui ont été identifiées dans le modèle. Les données extraites s’afficheront dans les colonnes de la vue bibliothèque de documents de votre modèle.

Un administrateur Office 365 doit [activer le traitement de formulaire](https://docs.microsoft.com/microsoft-365/contentunderstanding/set-up-content-understanding#to-set-up-content-understanding) pour la bibliothèque de documents SharePoint afin que les utilisateurs puissent [créer un modèle de traitement de formulaire](create-a-form-processing-model.md) dans celui-ci.

## <a name="see-also"></a>Voir aussi
  
[Mise à l’arrêt de la documentation](https://docs.microsoft.com/power-automate/)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>
[Présentation de l’explication des documents](document-understanding-overview.md)</br>
[Formation : améliorer les performances d’entreprise avec le générateur AI](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)</br>
