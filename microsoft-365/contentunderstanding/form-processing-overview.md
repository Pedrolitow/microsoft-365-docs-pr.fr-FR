---
title: Vue d’ensemble sur le traitement de formulaires dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment utiliser ai build pour créer des modèles de traitement de formulaires dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 8bcb5874ce62b8125e385fcf9eca8dbd2ca9f0fa
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585243"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Vue d’ensemble sur le traitement de formulaires dans Microsoft SharePoint Syntex

 ![Générateur d’intelligence artificielle.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex utilise le traitement de formulaire Microsoft PowerApps [AI Builder](/ai-builder/overview) pour créer des modèles au sein de bibliothèques de documents SharePoint.

Vous pouvez utiliser le traitement de formulaire AI Builder pour créer des modèles IA qui utilisent la technologie machine learning pour identifier et extraire des paires clé-valeur et des données de table à partir de documents structurés ou semi-structurés, tels que des formulaires et des factures.

Les organisations reçoivent souvent des factures en grande quantité à partir de diverses sources, telles que le courrier, la télécopie et le courrier électronique. Le traitement de ces documents et leur saisie manuelle dans une base de données peuvent prendre beaucoup de temps. L’utilisation de l’AI pour extraire le texte, les paires clé/valeur et les tables de vos documents, le traitement de formulaire automatise ce processus. 

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios de traitement de formulaires, consultez l’article [SharePoint Syntex adoption : Guide de démarrage](./adoption-getstarted.md).

Par exemple, vous pouvez créer un modèle de traitement de formulaire qui identifie tous les documents de bon de commande téléchargés dans la bibliothèque de documents. À partir de chaque bon de commande, vous pouvez ensuite extraire et afficher des données spécifiques qui sont importantes pour vous, telles que le *numéro* de bon de commande, *la date* ou *le coût total*.

![Vue de la bibliothèque de documents.](../media/content-understanding/doc-lib-done.png)</br>  

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est acquise en formant votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. AI Builder analyse vos exemples de fichiers pour les paires clé-valeur, et vous pouvez également identifier manuellement les fichiers qui n’ont peut-être pas été détectés.  Le générateur AI vous permet de tester la précision de votre modèle dans vos exemples de fichiers.

Après avoir entraîné et publié votre modèle, votre modèle crée un [flux Power Automate](/power-automate/getting-started). Le flux s’exécute lorsqu’un fichier est téléchargé dans la bibliothèque de documents SharePoint et extrait les données qui ont été identifiées dans le modèle. Les données extraites s’affichent dans les colonnes de la vue bibliothèque de documents de votre modèle.

Un administrateur Office 365 doit [activer le traitement des formulaires](./set-up-content-understanding.md) pour la bibliothèque de documents SharePoint afin que les utilisateurs [puissent y créer un modèle de traitement de formulaire](create-a-form-processing-model.md). Vous pouvez sélectionner les sites pendant ou après la configuration dans vos paramètres de gestion.

## <a name="file-limitations"></a>Limitations de fichier

Lorsque vous utilisez des modèles de traitement de formulaires, veillez à noter les [exigences et les limites d'utilisation des fichiers](/ai-builder/form-processing-model-requirements).

## <a name="supported-languages"></a>Langues prises en charge

Le traitement des formulaires prend en charge les documents dans plus de 73 langues. Pour obtenir la liste des langues, consultez la [prise en charge du langage de traitement de formulaire](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

## <a name="multi-geo-environments"></a>Microsoft 365 Multigéographie

Lors de la configuration de SharePoint Syntex dans un[environnement Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md), vous pouvez seulement le configurer pour utiliser le traitement des formulaires à l’emplacement central. Si vous souhaitez utiliser le traitement de formulaires dans un emplacement satellite, contactez le support Microsoft.

## <a name="custom-environments"></a>Environnements personnalisés

Si vous utilisez un environnement personnalisé (plutôt que l’environnement par défaut) pour le traitement de Power Platform, il existe des exigences de configuration supplémentaires. Pour plus d’informations, consultez [environnements Power Platform personnalisés](set-up-content-understanding.md#requirements).


## <a name="see-also"></a>Voir aussi
  
[Documentation Power Automate](/power-automate/)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Présentation de la présentation des documents](document-understanding-overview.md)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)