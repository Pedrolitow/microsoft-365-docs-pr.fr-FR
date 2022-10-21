---
title: Vue d’ensemble des types de modèles dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.custom: intro-overview
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les modèles personnalisés et les modèles prédéfinis dans Microsoft Syntex.
ms.openlocfilehash: 47eea92e8e9e4e5eb4588d04dd1422a43afd16ae
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68664051"
---
# <a name="overview-of-model-types-in-microsoft-syntex"></a>Vue d’ensemble des types de modèles dans Microsoft Syntex

La compréhension du contenu dans Microsoft Syntex commence par les modèles IA. Les modèles vous permettent d’identifier et de classer les documents chargés dans les bibliothèques de documents SharePoint, puis d’extraire les informations dont vous avez besoin à partir de chaque fichier.

Lorsqu’il est appliqué à une bibliothèque de documents SharePoint, le modèle est associé à un type de contenu et comporte des colonnes pour stocker les informations extraites. Le type de contenu que vous créez est stocké dans la Galerie de types de contenu SharePoint. Vous pouvez également choisir d’utiliser des types de contenu existants pour utiliser leur schéma.

Syntex utilise [des modèles personnalisés](#custom-models) et [des modèles prédéfinis](#prebuilt-models). 

![Diagramme montrant les types de modèles personnalisés et prédéfinis Syntex.](../media/content-understanding/syntex-model-types-diagram.png)

Les modèles peuvent être des *modèles d’entreprise*, qui sont créés dans un [centre de contenu](create-a-content-center.md), ou *des modèles locaux*, qui sont créés sur votre [site SharePoint local](create-local-model.md).

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GJXS] 

</br>
--->

## <a name="custom-models"></a>Modèles personnalisés

Le type de modèle personnalisé que vous choisissez dépend des types de fichiers que vous utilisez, du format et de la structure des fichiers et de l’emplacement où vous souhaitez appliquer le modèle.

Les modèles personnalisés sont les suivants :

- [Traitement de documents non structurés](#unstructured-document-processing)
- [Traitement de documents en forme libre](#freeform-document-processing)
- [Traitement de document structuré](#structured-document-processing)

Pour afficher les différences côte à côte dans les modèles personnalisés, consultez [Comparer des modèles personnalisés](./difference-between-document-understanding-and-form-processing-model.md).

### <a name="unstructured-document-processing"></a>Traitement de documents non structurés

Utilisez le modèle de traitement de document non structuré pour classifier automatiquement les documents et en extraire des informations. Il fonctionne de façon optimale avec les documents non structurés, tels que les lettres ou les contrats. Ces documents doivent comporter du texte qui peut être identifié sur la base de phrases ou de modèles. Le texte identifié désigne à la fois le type de fichier (sa classification) et ce que vous voulez extraire (ses extracteurs).

Par exemple, un document non structuré peut être une lettre de renouvellement de contrat, qui peut être rédigée de différentes manières. Toutefois, des informations existent systématiquement dans le corps de chaque document de renouvellement de contrat, telles que la chaîne de texte « Date de début du service de » suivie d’une date réelle.

Ce type de modèle prend en charge la plus large gamme de types de fichiers et fonctionne uniquement sur les fichiers utilisant l’alphabet latin (caractères anglais).

Pour plus d’informations, consultez [Vue d’ensemble du traitement de documents non structurés](document-understanding-overview.md).

### <a name="freeform-document-processing"></a>Traitement de documents en forme libre

Utilisez le modèle de traitement de document de forme libre pour extraire automatiquement des informations à partir de documents non structurés et de forme libre, tels que des lettres et des contrats où les informations peuvent apparaître n’importe où dans le document.

Les modèles de traitement de documents de forme libre utilisent Microsoft Power Apps [AI Builder](/ai-builder/form-processing-model-overview) pour créer et entraîner des modèles dans Syntex. 

> [!NOTE]
> Le modèle de traitement des documents de forme libre n’est pas encore disponible dans certaines régions. Pour plus d’informations, consultez [Disponibilité des fonctionnalités par région](/ai-builder/availability-region).

Parce que votre organisation reçoit des lettres et des documents en grande quantité à partir de diverses sources, telles que le courrier, la télécopie et le courrier électronique. Le traitement de ces documents et leur saisie manuelle dans une base de données peuvent prendre beaucoup de temps. En utilisant l’IA pour extraire le texte et d’autres informations de ces documents, ce modèle automatise ce processus.

Ce type de modèle est la meilleure option pour les documents en anglais dans des fichiers PDF ou image lorsque vous n’avez pas besoin d’une classification automatique du type de document.

Pour plus d’informations, consultez [Vue d’ensemble du traitement des documents en forme libre](freeform-document-processing-overview.md).

### <a name="structured-document-processing"></a>Traitement de document structuré

Utilisez le modèle de traitement de document structuré pour identifier automatiquement les valeurs des champs et des tables. Il fonctionne mieux pour les documents structurés ou semi-structurés, tels que les formulaires et les factures.

Les modèles de traitement de documents structurés utilisent le traitement de documents Microsoft Power Apps [AI Builder](/ai-builder/form-processing-model-overview) (anciennement appelé traitement de formulaire) pour créer et entraîner des modèles dans Syntex. 

Ce type de modèle prend en charge la plus large gamme de langues et est formé pour comprendre la disposition de votre formulaire à partir d’exemples de documents, puis apprend à rechercher les données dont vous avez besoin pour extraire des emplacements similaires. Les formulaires ont généralement une disposition plus structurée où les entités se trouvent au même emplacement (par exemple, un numéro de sécurité sociale sur un formulaire fiscal).

Pour plus d’informations, consultez [Vue d’ensemble du traitement de documents structurés](form-processing-overview.md).

## <a name="prebuilt-models"></a>Modèles préconçus

Si vous n’avez pas besoin de créer un modèle personnalisé, vous pouvez utiliser un [modèle prédéfini](prebuilt-overview.md) qui a déjà été formé pour des documents structurés spécifiques.

Les modèles prédéfinis sont les suivants :

- [Traitement des factures](#invoice-processing)
- [Traitement des reçus](#receipt-processing)

Les modèles prédéfinis sont préformés pour reconnaître les documents et les informations structurées dans les documents. Au lieu d’avoir à créer un modèle personnalisé à partir de zéro, vous pouvez itérer sur un modèle préentraîné existant pour ajouter des champs spécifiques qui répondent aux besoins de votre organisation.

### <a name="invoice-processing"></a>Traitement des factures

Le modèle de traitement des factures analyse et extrait les informations clés des factures de vente. L’API analyse les factures dans différents formats et extrait des informations clés sur les factures, telles que le nom du client, l’adresse de facturation, la date d’échéance et le montant dû.

Pour plus d’informations sur les modèles de traitement des factures prédéfinis, consultez [Utiliser un modèle prédéfini pour extraire des informations de factures](prebuilt-model-invoice.md).

### <a name="receipt-processing"></a>Traitement des reçus

Le modèle prédéfini de traitement des reçus analyse et extrait les informations clés des reçus. L’API analyse les reçus imprimés et manuscrits et extrait les informations de reçu clé telles que le nom du commerçant, le numéro de téléphone du commerçant, la date de transaction, la taxe et le total de la transaction.

Pour plus d’informations sur les modèles de traitement des reçus prédéfinis, consultez [Utiliser un modèle prédéfini pour extraire des informations de reçus](prebuilt-model-receipt.md).

## <a name="see-also"></a>Voir aussi

[Comparer des modèles personnalisés dans Microsoft Syntex](./difference-between-document-understanding-and-form-processing-model.md)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)
