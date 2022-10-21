---
title: Vue d’ensemble du traitement de documents structuré dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment utiliser AI Builder pour créer des modèles de traitement de documents structurés dans Microsoft Syntex.
ms.openlocfilehash: 9d006741cc236841f4438c5937666c1fc0f02e16
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662648"
---
# <a name="overview-of-structured-document-processing-in-microsoft-syntex"></a>Vue d’ensemble du traitement de documents structuré dans Microsoft Syntex

> [!NOTE]
> *Le traitement de documents structurés* était appelé *traitement de formulaire* dans les versions précédentes.

Utilisez le modèle de traitement de document structuré ([méthode de disposition](create-syntex-model.md#train-a-custom-model)) pour identifier automatiquement les valeurs de champ et de table. Il fonctionne mieux pour les documents structurés ou semi-structurés, tels que les formulaires et les factures.

Microsoft Syntex utilise le traitement de documents Microsoft Power Apps [AI Builder](/ai-builder/form-processing-model-overview) (anciennement appelé traitement de formulaires) pour créer des modèles de traitement de documents structurés dans des bibliothèques de documents SharePoint.
<!---
 ![AI Builder.](../media/content-understanding/ai-builder.png)
--->
Vous pouvez utiliser le traitement de documents AI Builder pour créer des modèles de traitement de documents structurés qui utilisent la technologie Machine Learning pour identifier et extraire des paires clé-valeur et des données de table à partir de documents structurés ou semi-structurés, tels que des formulaires et des factures.

Les organisations reçoivent souvent des factures en grandes quantités de diverses sources, telles que le courrier, la télécopie et le courrier électronique. Le traitement de ces documents et leur saisie manuelle dans une base de données peuvent prendre beaucoup de temps. En utilisant l’IA pour extraire le texte, les paires clé-valeur et les tables de vos documents, Syntex automatise ce processus. 

> [!NOTE]
> Pour plus d’idées sur l’utilisation de ces modèles dans votre organisation, consultez [Prise en main de l’adoption](adoption-getstarted.md) et [Scénarios et cas d’usage](adoption-scenarios.md).

Par exemple, vous pouvez créer un modèle de traitement de document structuré qui identifie tous les documents chargés dans la bibliothèque de documents. À partir de chaque document, vous pouvez ensuite extraire et afficher des données spécifiques qui sont importantes pour vous.

![Capture d’écran montrant l’affichage de la bibliothèque de documents.](../media/content-understanding/doc-lib-done.png)  

Vous pouvez également utiliser des exemples de fichiers pour former votre modèle et définir les informations à extraire de votre formulaire. La mise en page de votre document est acquise en formant votre modèle. Vous n’avez besoin que de cinq documents de formulaires pour commencer. Syntex analyse vos exemples de fichiers à la recherche de paires clé-valeur, et vous pouvez également identifier manuellement celles qui n’ont peut-être pas été détectées.  Le générateur AI vous permet de tester la précision de votre modèle dans vos exemples de fichiers.

Vous pouvez uniquement créer un modèle de traitement de document structuré dans les bibliothèques de documents SharePoint pour lesquelles il est activé. S’il a été activé, vous pouvez voir l’option **Classifier et extraire** dans votre bibliothèque de documents. 

![Capture d’écran montrant le modèle AI Builder.](../media/content-understanding/create-ai-builder-model2.png)

Si vous avez besoin qu’elle soit activée sur votre bibliothèque de documents, contactez votre administrateur Microsoft 365.

## <a name="requirements"></a>Conditions requises

Pour plus d’informations sur les exigences à prendre en compte lors du choix de ce modèle, consultez [Configuration requise et limitations des modèles dans Microsoft Syntex](requirements-and-limitations.md#structured-document-processing).

## <a name="see-also"></a>Voir aussi

[Comparer des modèles personnalisés](difference-between-document-understanding-and-form-processing-model.md)

[Entraîner un modèle de traitement de document structuré](create-a-form-processing-model.md)

[Documentation Power Automate](/power-automate/)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/training/paths/improve-business-performance-ai-builder/?source=learn)
