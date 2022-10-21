---
title: Entraîner un modèle de traitement de document de forme libre dans Microsoft Syntex
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Découvrez comment entraîner un modèle de traitement de document de forme libre dans Microsoft Syntex.
ms.openlocfilehash: cb0aa89f1c0f7e1a34c08d67a11ea82b45e48c29
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68664110"
---
# <a name="train-a-freeform-document-processing-model-in-microsoft-syntex"></a>Entraîner un modèle de traitement de document de forme libre dans Microsoft Syntex

Suivez les instructions fournies dans [Créer un modèle dans Syntex](create-syntex-model.md) pour créer un modèle de traitement de document de forme libre dans un centre de contenu. Vous pouvez également suivre les instructions fournies dans [Créer un modèle sur un site SharePoint local](create-local-model.md) pour créer le modèle sur un site local. Utilisez ensuite cet article pour effectuer l’apprentissage de votre modèle.

![Diagramme du flux de travail pour entraîner un modèle AI Builder.](../media/content-understanding/train-aib-model.png)

Pour entraîner un modèle de traitement de document de forme libre, procédez comme suit :

 - [Étape 1 : Ajouter et analyser des documents](#step-1-add-and-analyze-documents)
 - [Étape 2 : Étiqueter les champs et les tables](#step-2-tag-fields-and-tables)
 - [Étape 3 : Entraîner et publier votre modèle](#step-3-train-and-publish-your-model)
 - [Étape 4 : Utiliser votre modèle](#step-4-use-your-model)

## <a name="step-1-add-and-analyze-documents"></a>Étape 1 : Ajouter et analyser des documents

Une fois que vous avez créé votre modèle de traitement de document structuré, la page **Choisir les informations à extraire** s’ouvre. Ici, vous répertoriez toutes les informations que vous souhaitez que le modèle IA extrait de vos documents, telles que le nom, l’adresse ou le montant.  

> [!NOTE]
> Lorsque vous recherchez des exemples de fichiers à utiliser, consultez les [exigences de document d’entrée du modèle de traitement de document et les conseils d’optimisation](/ai-builder/form-processing-model-requirements). 
 
1. Vous définissez d’abord les champs et les tables que vous souhaitez enseigner à votre modèle à extraire sur la page **Choisir les informations à extraire**. Pour obtenir des instructions détaillées, consultez [Définir des champs et des tables pour extraire](/ai-builder/create-form-processing-model#define-fields-and-tables-to-extract). 

2.  Vous pouvez créer autant de collections de dispositions de documents que vous souhaitez que votre modèle traite. Pour obtenir des instructions détaillées, consultez [Grouper les documents par collections](/ai-builder/create-form-processing-model#group-documents-by-collections). 

3. Après avoir créé vos collections et ajouté au moins cinq exemples de fichiers pour chacun, AI Builder sur Syntex examine les documents chargés pour détecter les champs et les tables. Ce processus prend généralement quelques secondes. Une fois l’analyse terminée, vous pouvez poursuivre l’étiquetage des documents.

## <a name="step-2-tag-fields-and-tables"></a>Étape 2 : Étiqueter les champs et les tables

Vous devez baliser les documents pour apprendre au modèle à comprendre les champs et les données de table que vous souhaitez extraire. Pour obtenir des instructions détaillées, consultez [Baliser les documents](/ai-builder/create-form-processing-model#tag-documents).

## <a name="step-3-train-and-publish-your-model"></a>Étape 3 : Entraîner et publier votre modèle

1. Après avoir créé et entraîné votre modèle, vous êtes prêt à le publier et à l’utiliser dans SharePoint. Pour publier le modèle, sélectionnez **Publier**. Pour obtenir des instructions détaillées, consultez [Entraîner et publier votre modèle de traitement de document](/ai-builder/form-processing-train). 

    ![Capture d’écran montrant les détails du modèle sur la page d’accueil du modèle.](../media/content-understanding/ai-builder-create-a-flow-1.png)

2. Une fois le modèle publié, vous accédez à la page d’accueil du modèle. Vous aurez ensuite la possibilité d’appliquer le modèle à une bibliothèque de documents.

    ![Capture d’écran de la page d’accueil du modèle pour appliquer le modèle à une bibliothèque.](../media/content-understanding/ai-builder-apply-model.png)

## <a name="step-4-use-your-model"></a>Étape 4 : Utiliser votre modèle

1. Dans la vue du modèle de la bibliothèque de documents, notez que les champs que vous avez sélectionnés s’affichent désormais sous forme de colonnes.

    ![Capture d’écran montrant le modèle de bibliothèque de documents appliqué.](../media/content-understanding/doc-lib-view.png)

2. Notez que le lien Informations en regard de **Documents** indique qu’un modèle de traitement de formulaire est appliqué à cette bibliothèque de documents.

3. Upload files to your document library. Any files that the model identifies as its content type lists the files in your view and displays the extracted data in the columns.

    ![Capture d’écran montrant que le processus est terminé.](../media/content-understanding/doc-lib-done.png) 

> [!NOTE]
> Si un modèle de traitement de document de forme libre ou structuré et un modèle de traitement de document non structuré sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle de traitement de document non structuré et de tous les extracteurs entraînés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle de traitement de document structuré ou de forme libre, les colonnes sont remplies à l’aide de ces valeurs extraites.

### <a name="classification-date-field"></a>Champ Date de classification

Lorsqu’un modèle personnalisé Syntex est appliqué à une bibliothèque de documents, le champ **Date de classification** est inclus dans le schéma de bibliothèque. Par défaut, ce champ est vide. Toutefois, lorsque des documents sont traités et classés par un modèle, ce champ est mis à jour avec un horodatage d’achèvement. 

Lorsqu’un modèle est marqué avec la **Date de classification**, vous pouvez utiliser le flux **Envoyer un e-mail après que Syntex a traité un fichier** pour informer les utilisateurs qu’un nouveau fichier a été traité et classifié par un modèle dans la bibliothèque de documents SharePoint.

Pour exécuter le flux :

1. Sélectionnez un fichier, puis **Intégrer** > **Power Automate** > **Créer un flux**.

2. Dans le panneau **Créer un flux** , sélectionnez **Envoyer un e-mail après que Syntex a traité un fichier**.

    ![Capture d’écran montrant le panneau Créer un flux et l’option de flux mises en évidence.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Voir aussi
  
[Créer un modèle dans Microsoft Syntex](create-syntex-model.md)

[Documentation Power Automate](/power-automate/)

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)
