---
title: Vue d’ensemble de Microsoft Syntex
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
description: Découvrez les fonctionnalités et fonctionnalités de Microsoft Syntex.
ms.openlocfilehash: b5c030231395284ece7342f8ed27349bce42f0df
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68663949"
---
# <a name="overview-of-microsoft-syntex"></a>Vue d’ensemble de Microsoft Syntex

Microsoft Syntex est un service de compréhension, de traitement et de conformité de contenu qui utilise le traitement intelligent des documents, l’intelligence artificielle de contenu (IA) et le Machine Learning avancé pour rechercher, organiser et classifier automatiquement et de manière réfléchie des documents dans vos bibliothèques SharePoint.

:::row:::
   :::column span="":::      
      Syntex vous permet d’automatiser vos processus basés sur le contenu, en capturant les informations contenues dans vos documents métier et en les transformant en connaissances de travail pour votre organisation.

      Au lieu de cliquer et de trier des centaines ou des milliers de fichiers, Syntex extrait, analyse et catégorise les données pour vous.
   :::column-end:::
   :::column span="":::
      ![Image des ordinateurs exécutant Syntex.](../media/content-understanding/syntex-devices-image.png)
   :::column-end:::
:::row-end:::

Vous pouvez approfondir votre contenu pour le comprendre réellement, et transformer les informations en insights significatifs que votre organisation peut utiliser pour prendre des décisions commerciales éclairées.

## <a name="models"></a>Modèles

:::row:::
   :::column span="":::
      ![Image de l’icône de modèle générique.](../media/content-understanding/model-generic-image.png) 
   :::column-end:::
   :::column span="3":::
      La compréhension de votre contenu avec Syntex commence par les modèles. Les modèles vous permettent d’identifier et de classer les documents chargés dans vos bibliothèques de documents SharePoint, puis d’extraire les informations dont vous avez besoin de chaque fichier.

      Dans Syntex, vous pouvez créer [des modèles personnalisés](model-types-overview.md) ou utiliser [des modèles prédéfinis](prebuilt-overview.md). 
   :::column-end:::
:::row-end:::

Le type de modèle que vous choisissez dépend des types de fichiers que vous utilisez, du format et de la structure des fichiers, des informations que vous souhaitez extraire et de l’emplacement où vous souhaitez appliquer le modèle.

### <a name="custom-models"></a>Modèles personnalisés

Vous créez des modèles personnalisés pour comprendre la disposition de vos fichiers à partir d’exemples de documents. Les modèles apprennent à rechercher les données dont vous avez besoin pour extraire des documents similaires. Les modèles personnalisés sont les suivants :

- [Traitement de documents non structurés](document-understanding-overview.md)
- [Traitement de documents en forme libre](freeform-document-processing-overview.md)
- [Traitement de document structuré](form-processing-overview.md)

| Non structurées<br>traitement des documents  | Forme libre<br>traitement des documents  | Structurées<br>traitement des documents  |
| ------------- | ------------- | ------------- |
|  ![Icône pour le modèle de traitement de document non structuré.](../media/content-understanding/custom-classify-and-extract-by-text-pattern.png) | ![Icône du modèle de traitement de document de forme libre.](../media/content-understanding/custom-extract-by-text-pattern-and-layout.png) |  ![Icône pour le modèle de traitement de document structuré.](../media/content-understanding/custom-extract-by-layout.png) |
| Utilisez ce modèle personnalisé pour classifier automatiquement les documents et en extraire des informations. Utilisez les modèles du texte dans des exemples de documents pour effectuer l’apprentissage du modèle. Idéal pour les fichiers Office et la classification automatique des fichiers. <br>[En savoir plus](document-understanding-overview.md) | Utilisez ce modèle personnalisé pour extraire automatiquement des informations à partir de documents non structurés. Utilisez les modèles du texte ou de la disposition dans des exemples de documents pour effectuer l’apprentissage du modèle. Idéal pour un mélange de texte et de mise en page. <br>[En savoir plus](freeform-document-processing-overview.md) |  Utilisez ce modèle personnalisé pour identifier automatiquement les valeurs de champ et de table à partir de documents structurés ou semi-structurés tels que des formulaires. Idéal pour la plupart des langages et des fichiers qui incluent des dispositions de formulaire ou des tableaux. <br>[En savoir plus](form-processing-overview.md) |

### <a name="prebuilt-models"></a>Modèles préconçus

Si vous n’avez pas besoin de créer un modèle personnalisé, vous pouvez utiliser un [modèle prédéfini](prebuilt-overview.md). Ce type de modèle est préentraîné pour extraire des entités prédéfinies à partir de fichiers métier courants. Les modèles prédéfinis sont les suivants :

- [Traitement des factures](prebuilt-model-invoice.md)
- [Traitement des reçus](prebuilt-model-receipt.md)

| Traitement des factures | Traitement des reçus | 
| ------------- | ------------- |
| ![Icône du modèle Factures.](../media/content-understanding/trained-invoices-model.png) | ![Icône du modèle Reçus.](../media/content-understanding/trained-receipts-model.png) |
| Utilisez ce modèle prédéfini pour gagner du temps pour traiter les factures. Extrayez automatiquement les informations clés spécifiques aux factures. <br>[En savoir plus](prebuilt-model-invoice.md) | Utilisez ce modèle prédéfini pour gagner du temps pour traiter les reçus. Extrayez automatiquement les informations clés spécifiques aux dépenses. <br>[En savoir plus](prebuilt-model-receipt.md) | 

Pour plus d’informations sur les modèles personnalisés et prédéfinis, consultez [Vue d’ensemble des types de modèles dans Microsoft Syntex](model-types-overview.md).

## <a name="content-assembly"></a>Assemblage de contenu

:::row:::
   :::column span="":::
      ![Image de l’icône de document générique.](../media/content-understanding/document-assembly-image.png) 
   :::column-end:::
   :::column span="3":::
      Avec Syntex, vous pouvez créer des *modèles modernes* basés sur les documents métier que vous utilisez le plus.

      Vous pouvez ensuite utiliser ces modèles pour générer automatiquement de nouveaux documents à l’aide de listes SharePoint ou d’entrées utilisateur comme source de données.
   :::column-end:::
:::row-end:::

 Ce processus vous permet de générer automatiquement des documents métier répétitifs standard, tels que des contrats, des relevés de travail, des contrats de service, des lettres de consentement et de la correspondance. Vous pouvez effectuer toutes ces tâches plus rapidement, de manière plus cohérente et avec moins d’erreurs dans Syntex.

Pour plus d’informations, consultez [Créer des documents à l’aide d’un assembly de contenu dans Microsoft Syntex](content-assembly.md).

## <a name="advanced-metadata-search"></a>Recherche avancée dans les métadonnées

:::row:::
   :::column span="3":::
      La fonctionnalité de recherche de métadonnées avancée dans Syntex vous permet d’effectuer des requêtes spécifiques basées sur les métadonnées sur les bibliothèques de documents SharePoint.

      Vous pouvez effectuer des requêtes plus rapides et plus précises basées sur des valeurs de colonne de métadonnées spécifiques, plutôt que de simplement rechercher des mots clés.    
   :::column-end:::
   :::column span="":::
      ![Image de l’icône de recherche générique.](../media/content-understanding/search-generic-image.png)
   :::column-end:::
:::row-end:::

Cette fonctionnalité est utile lorsque vous avez une information spécifique que vous souhaitez rechercher, par exemple quand un document a été modifié pour la dernière fois, une personne spécifique associée à un fichier ou un type de fichier spécifique.

Pour plus d’informations, consultez [Rechercher des métadonnées dans les bibliothèques de documents dans Microsoft Syntex](metadata-search.md).

--->

## <a name="content-compliance"></a>Conformité du contenu

:::row:::
   :::column span="":::
      ![Image de l’icône de conformité générique.](../media/content-understanding/compliance-image.png) 
   :::column-end:::
   :::column span="3":::
      La compréhension de votre contenu permet un meilleur contrôle de conformité et augmente les options de gestion et de gouvernance pour toutes vos données. Lorsque le contenu est correctement étiqueté et marqué, vous disposez d’un meilleur contrôle sur vos données et pouvez suivre les réglementations plus facilement. Syntex vous aide à garantir la conformité en utilisant des étiquettes de rétention et des étiquettes de confidentialité pour gérer vos documents.
   :::column-end:::
:::row-end:::

Pour plus d’informations, consultez [Appliquer une étiquette de rétention à un modèle dans Microsoft Syntex](apply-a-retention-label-to-a-model.md) et [Appliquer une étiquette de confidentialité à un modèle dans Microsoft Syntex](apply-a-sensitivity-label-to-a-model.md).

## <a name="premium-taxonomy-services"></a>Services de taxonomie Premium

:::row:::
   :::column span="3":::
      Le fait d’avoir une ou plusieurs licences Syntex dans votre organisation permet aux administrateurs de disposer des fonctionnalités de magasin de termes supplémentaires suivantes :<br><br>
       
      - Importation d’ensembles de [termes basés sur SKOS](import-term-set-skos.md), qui vous permet d’importer un ensemble de termes à l’aide d’un format SKOS.      
   :::column-end:::
   :::column span="":::
      ![Image de l’icône de taxonomie générique.](../media/content-understanding/taxonomy-image.png)
   :::column-end:::
:::row-end:::


- [Envoi de types de contenu d’entreprise à un site hub](push-content-type-to-hub.md), ce qui les ajoute également aux sites associés et aux listes ou bibliothèques nouvellement créées.

- [Rapports de magasin de termes](term-store-analytics.md), qui vous donnent des insights sur les ensembles de termes publiés et leur utilisation dans votre organisation.

## <a name="scenarios-and-use-cases"></a>Scénarios et cas d’utilisation

:::row:::
   :::column span="":::
      ![Image de l’icône de scénario générique.](../media/content-understanding/scenarios-image.png) 
   :::column-end:::
   :::column span="3":::
      Syntex peut aider votre organisation à automatiser les processus métier, à améliorer la précision de la recherche et à gérer les risques de conformité.

      Avec les services et fonctionnalités d’IA de contenu, vous pouvez créer une compréhension et une classification du contenu directement dans le flux de gestion de contenu.
   :::column-end:::
:::row-end:::

Pour obtenir des idées sur la façon dont vous pouvez utiliser Syntex dans votre organisation, consultez [Scénarios et cas d’usage pour Microsoft Syntex](adoption-scenarios.md).
<br><br>
> [!div class="nextstepaction"]
> [En savoir plus sur les modèles dans Microsoft Syntex](model-types-overview.md)
