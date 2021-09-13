---
title: Vue d’ensemble sur le traitement de formulaires dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: Découvrez le traitement de formulaires dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 7a411a4150f09d62ae539ca35dee05df201e707c
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202295"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>Vue d’ensemble sur le traitement de formulaires dans Microsoft SharePoint Syntex

 ![Générateur d’intelligence artificielle.](../media/content-understanding/ai-builder.png)</br>

Microsoft SharePoint Syntex utilise le traitement de formulaire Microsoft PowerApps [AI Builder](/ai-builder/overview) pour créer des modèles au sein de bibliothèques de documents SharePoint.

Vous pouvez utiliser le traitement de formulaire du générateur AI pour créer des modèles AI qui utilisent la technologie d’apprentissage automatique pour identifier et extraire des paires clés et des données de tableau à partir de documents structurés ou semi-structurés, tels que des formulaires et des factures.

Les organisations reçoivent souvent des factures en grande quantité provenant de sources variées, telles que le courrier, les télécopies, la messagerie, etc. Le traitement de ces documents et leur saisie manuelle dans une base de données peut prendre beaucoup de temps. L’utilisation de l’AI pour extraire le texte, les paires clé/valeur et les tables de vos documents, le traitement de formulaire automatise ce processus. 

> [!NOTE]
> Pour plus d’informations sur les exemples de scénarios de traitement de formulaires, consultez l’article [SharePoint Syntex adoption : Guide de démarrage](./adoption-getstarted.md).

Par exemple, vous pouvez créer un modèle de traitement de formulaire qui identifie tous les documents de bon de commande téléchargés dans la bibliothèque de documents. À partir de chaque bon de commande, vous pouvez extraire et afficher des données spécifiques qui vous sont importantes, telles que *numéro de bon de commande*, *date* ou *coût total*.

![Vue de la bibliothèque de documents.](../media/content-understanding/doc-lib-done.png)</br>  

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est acquise en formant votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. AI analyse vos exemples de fichiers pour les paires clé-valeur, puis identifie manuellement celles qui n’ont pas été détectées.  Le générateur AI vous permet de tester la précision de votre modèle dans vos exemples de fichiers.

Une fois que vous avez créé votre modèle et que vous l’avez publié, celui-ci crée un [Power Automate Flow](/power-automate/getting-started). Le flux s’exécute lorsqu’un fichier est téléchargé dans la bibliothèque de documents SharePoint et extrait les données qui ont été identifiées dans le modèle. Les données extraites s’affichent dans les colonnes de la vue bibliothèque de documents de votre modèle.

Un administrateur Office 365 doit [activer le traitement de formulaires](./set-up-content-understanding.md)pour la bibliothèque de documents SharePoint pour permettre aux utilisateurs de [créer un modèle de traitement de formulaire](create-a-form-processing-model.md) dans celui-ci. Vous pouvez sélectionner les sites pendant ou après la configuration dans vos paramètres de gestion.

### <a name="file-limitations"></a>Limitations de fichier

Lorsque vous utilisez des modèles de traitement de formulaires, veillez à noter les [exigences et les limites d'utilisation des fichiers](/ai-builder/form-processing-model-requirements).

### <a name="multi-geo-environments"></a>Microsoft 365 Multigéographie

Lors de la configuration de SharePoint Syntex dans un[environnement Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md), vous pouvez seulement le configurer pour utiliser le traitement des formulaires à l’emplacement central. Si vous souhaitez utiliser le traitement de formulaires dans un emplacement satellite, contactez le support Microsoft.






## <a name="see-also"></a>Voir aussi
  
[Documentation Power Automate](/power-automate/)

[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)

[Présentation de la présentation des documents](document-understanding-overview.md)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)