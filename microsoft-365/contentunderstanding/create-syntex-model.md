---
title: Créer un modèle d’entreprise dans Microsoft Syntex
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
description: Découvrez comment créer un modèle personnalisé ou prédéfini avec Microsoft Syntex.
ms.openlocfilehash: bd2275c40c491626e42f666d2a75dd809c04e584
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68664145"
---
# <a name="create-an-enterprise-model-in-microsoft-syntex"></a>Créer un modèle d’entreprise dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles prédéfinis</sup>

Un modèle d’entreprise est créé et entraîné dans le [centre de contenu](create-a-content-center.md) et peut être découvert par d’autres personnes à utiliser. Que vous souhaitiez créer un modèle personnalisé ou utiliser un modèle prédéfini, vous pouvez le faire à partir de l’un des emplacements suivants dans Microsoft Syntex :

- À partir de la bibliothèque **Models**
- À partir de la page d’accueil du [centre de contenu](create-a-content-center.md)
- À partir de n’importe quelle bibliothèque de documents d’un site où Syntex a été activé

Pour cet article, nous commençons dans la bibliothèque **Models** . Pour plus d’informations sur les différents types de modèles, consultez [Vue d’ensemble des types de modèles dans Syntex](model-types-overview.md).

Si vous souhaitez créer un modèle local, voir [Créer un modèle sur un site SharePoint local](create-local-model.md).

## <a name="create-a-model"></a>Créer un modèle

Dans la bibliothèque **Models** , sélectionnez **Créer un modèle**.

![Capture d’écran de la bibliothèque Models montrant le bouton Créer un modèle.](../media/content-understanding/create-a-model-from-the-models-page.png) 

Dans la page **Options de création de modèle** , il existe deux sections :

- [**Entraîner un modèle personnalisé**](#train-a-custom-model)
    
- [**Configurer un modèle prédéfini**](#set-up-a-prebuilt-model)

![Capture d’écran de la page Options de création de modèle montrant les modèles personnalisés et les modèles prédéfinis.](../media/content-understanding/options-for-model-creation.png) 

> [!NOTE]
> Toutes les options de modèle peuvent ne pas être disponibles. Ces options sont configurées par votre administrateur Microsoft 365.

## <a name="train-a-custom-model"></a>Entraîner un modèle personnalisé

La section **Entraîner un modèle personnalisé** affiche les types de modèles personnalisés que vous pouvez créer.

![Capture d’écran de la section Générer un modèle personnalisé dans la page Options de création de modèle.](../media/content-understanding/build-a-custom-model-section.png) 

- **Méthode d’enseignement** : crée un [modèle de traitement de document non structuré](document-understanding-overview.md).

- **Méthode de sélection de forme** libre : crée un [modèle de traitement de document de forme libre](freeform-document-processing-overview.md).

- **Méthode de disposition** : crée un [modèle de traitement de document structuré](form-processing-overview.md).

Sélectionnez l’un des onglets suivants pour continuer avec le modèle personnalisé que vous souhaitez utiliser.

# <a name="teaching-method"></a>[Méthode d’enseignement](#tab/teaching-method)

Utilisez la **méthode Teaching** pour créer un [modèle de traitement de document non structuré](document-understanding-overview.md).

1. Sélectionnez **Méthode d’enseignement**.

2. Dans la page **Méthode d’enseignement : Détails** , vous trouverez plus d’informations sur le modèle. Si vous souhaitez continuer à créer le modèle, sélectionnez **Suivant**.

3. Dans le volet droit de la page **Créer un modèle avec la méthode d’enseignement** , entrez les informations suivantes.

    - **Nom du modèle** : entrez le nom du modèle, par exemple *contrats de service*.

    - **Description** : entrez des informations sur la façon dont ce modèle sera utilisé.

        ![Capture d’écran du volet droit de la page Créer un modèle avec la méthode d’enseignement.](../media/content-understanding/create-a-model-panel.png) 
    
4. Sous **Paramètres avancés** :

    - Dans la section **Type de contenu** , choisissez de créer un type de contenu ou d’en utiliser un existant.

    - Dans la section **Conformité** , sous **Étiquettes de rétention**, sélectionnez l’étiquette de rétention que vous souhaitez ajouter. Sous **Étiquettes de confidentialité**, sélectionnez l’étiquette de confidentialité que vous souhaitez ajouter. Si une étiquette de conformité a déjà été appliquée à la bibliothèque où le fichier est stocké, elle s’affiche.

5. Lorsque vous êtes prêt à créer le modèle, sélectionnez **Créer**.

6. Vous êtes maintenant prêt à [effectuer l’apprentissage du modèle](create-a-classifier.md).

# <a name="freeform-selection-method"></a>[Méthode de sélection de forme libre](#tab/freeform-selection-method)

Utilisez la **méthode de sélection Freeform** pour créer un [modèle de traitement de document de forme libre](freeform-document-processing-overview.md).

1. Sélectionnez **Méthode de sélection de forme libre**.

2. Dans la page **Méthode de sélection de forme libre : Détails** , vous trouverez plus d’informations sur le modèle. Si vous souhaitez continuer à créer le modèle, sélectionnez **Suivant**.

3. Dans le volet droit de la page **Créer un modèle avec la méthode de sélection de forme libre** , entrez les informations suivantes.

    - **Nom du modèle** : entrez le nom du modèle, par exemple *contrats de service*.

    - **Description** : entrez des informations sur la façon dont ce modèle sera utilisé.

        ![Capture d’écran du panneau droit de la page Créer un modèle avec la méthode de sélection Freeform.](../media/content-understanding/create-a-model-panel.png) 
    
4. Sous **Paramètres avancés** :

    - Dans la section **Type de contenu** , choisissez de créer un type de contenu ou d’en utiliser un existant.

    - Dans la section **Conformité** , sous **Étiquettes de rétention**, sélectionnez l’étiquette de rétention que vous souhaitez ajouter. Si une étiquette de conformité a déjà été appliquée à la bibliothèque où le fichier est stocké, elle s’affiche.

    > [!NOTE]
    > Les étiquettes de confidentialité ne sont pas disponibles pour la **méthode de sélection de forme** libre (modèles de traitement de document de forme libre) pour l’instant.

5. Lorsque vous êtes prêt à créer le modèle, sélectionnez **Créer**.

6. Vous êtes maintenant prêt à [effectuer l’apprentissage du modèle](train-freeform-document-processing-model.md).

    > [!NOTE]
    > Une fois publié, ce type de modèle peut être réutilisé par d’autres personnes qui ne sont pas propriétaires du modèle. Actuellement, ce modèle peut être modifié et partagé pour modification uniquement par le propriétaire du modèle.

# <a name="layout-method"></a>[Layout, méthode](#tab/layout-method)

Utilisez la **méthode Layout** pour créer un [modèle de traitement de document structuré](form-processing-overview.md).

1. Sélectionnez **Méthode de disposition**.

2. Dans la page **Méthode de disposition : Détails** , vous trouverez plus d’informations sur le modèle. Si vous souhaitez continuer à créer le modèle, sélectionnez **Suivant**.

3. Dans le volet droit de la page **Créer un modèle avec la méthode de mise en page** , entrez les informations suivantes.

    - **Nom du modèle** : entrez le nom du modèle, par exemple *contrats de service*.

    - **Description** : entrez des informations sur la façon dont ce modèle sera utilisé.

        ![Capture d’écran du volet droit de la page Créer un modèle avec la méthode de mise en page.](../media/content-understanding/create-a-model-panel.png) 
    
4. Sous **Paramètres avancés** :

    - Dans la section **Type de contenu** , choisissez de créer un type de contenu ou d’en utiliser un existant.

    - Dans la section **Conformité** , sous **Étiquettes de rétention**, sélectionnez l’étiquette de rétention que vous souhaitez ajouter. Si une étiquette de conformité a déjà été appliquée à la bibliothèque où le fichier est stocké, elle s’affiche.

    > [!NOTE]
    > Les étiquettes de confidentialité ne sont pas disponibles pour la **méthode Layout** (modèles de traitement de documents structurés) pour l’instant.

5. Lorsque vous êtes prêt à créer le modèle, sélectionnez **Créer**.

6. Vous êtes maintenant prêt à [effectuer l’apprentissage du modèle](create-a-form-processing-model.md).

    > [!NOTE]
    > Une fois publié, ce type de modèle peut être réutilisé par d’autres personnes qui ne sont pas propriétaires du modèle. Actuellement, ce modèle peut être modifié et partagé pour modification uniquement par le propriétaire du modèle.

---

## <a name="set-up-a-prebuilt-model"></a>Configurer un modèle prédéfini

La section **Configurer un modèle prédéfini** présente les types de modèles prédéfinis que vous pouvez utiliser. 

![Capture d’écran de la section Utiliser un modèle prédéfini sur la page Configurer un modèle prédéfini.](../media/content-understanding/use-a-trained-model-section.png) 

- **Traitement des factures**

- **Traitement des reçus**

Sélectionnez l’un des onglets suivants pour continuer avec le modèle prédéfini que vous souhaitez utiliser.

# <a name="invoice-processing"></a>[Traitement des factures](#tab/invoice-processing)

1. Sélectionnez **Traitement de la facture**.

2. Dans la page Traitement de la **facture : Détails** , vous trouverez plus d’informations sur le modèle. Si vous souhaitez continuer à utiliser le modèle, sélectionnez **Suivant**.

3. Dans le volet droit de la page **Créer un modèle de traitement de facture** , entrez les informations suivantes.

    - **Nom du modèle** : entrez le nom du modèle, par exemple *les dépenses Office*.

    - **Description** : entrez des informations sur la façon dont ce modèle sera utilisé.

        ![Capture d’écran du volet droit de la page Créer un modèle de traitement de facture.](../media/content-understanding/create-a-model-panel.png) 
    
4. Sous **Paramètres avancés** :

    - Dans la section **Type de contenu** , choisissez de créer un type de contenu ou d’en utiliser un existant.

    - Dans la section **Conformité** , sous **Étiquettes de rétention**, sélectionnez l’étiquette de rétention que vous souhaitez ajouter. Si une étiquette de rétention a déjà été appliquée à la bibliothèque où le fichier est stocké, elle est sélectionnée. 

    > [!NOTE]
    > Les étiquettes de confidentialité ne sont pas disponibles pour les modèles prédéfinis pour l’instant.

5. Lorsque vous êtes prêt à créer le modèle, sélectionnez **Créer**.

6. Vous êtes maintenant prêt à [terminer la configuration du modèle](prebuilt-model-invoice.md).

# <a name="receipt-processing"></a>[Traitement des reçus](#tab/receipt-processing)


1. Sélectionnez **Traitement des reçus**.

2. Dans la page **Traitement du reçu : Détails** , vous trouverez plus d’informations sur le modèle. Si vous souhaitez continuer à utiliser le modèle, sélectionnez **Suivant**.

2. Dans le volet droit de la page **Créer un modèle de traitement des reçus** , entrez les informations suivantes.

    - **Nom du modèle** : entrez le nom du modèle, par exemple *les dépenses Office*.

    - **Description** : entrez des informations sur la façon dont ce modèle sera utilisé.

        ![Capture d’écran du volet droit de la page Créer un modèle pour traiter les reçus.](../media/content-understanding/create-a-model-panel.png) 
    
3. Sous **Paramètres avancés** :

    - Dans la section **Type de contenu** , choisissez de créer un type de contenu ou d’en utiliser un existant.

    - Dans la section **Conformité** , sous **Étiquettes de rétention**, sélectionnez l’étiquette de rétention que vous souhaitez ajouter. Si une étiquette de rétention a déjà été appliquée à la bibliothèque où le fichier est stocké, elle est sélectionnée. 

    > [!NOTE]
    > Les étiquettes de confidentialité ne sont pas disponibles pour les modèles prédéfinis pour l’instant.

4. Lorsque vous êtes prêt à créer le modèle, sélectionnez **Créer**.

5. Vous êtes maintenant prêt à [terminer la configuration du modèle](prebuilt-model-receipt.md).

---



<!---
### Teaching method

Use the **Teaching method** to create an [unstructured document processing model](document-understanding-overview.md).

1. Select **Teaching method**.

2. On the **Teaching method: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.

3. On the right panel of the **Create a model with the teaching method** page, enter the following information.

    - **Model name** – Enter the name of the model, for example *Service agreements*.

    - **Description** – Enter information about how this model will be used.

        ![Screenshot of the right panel of the Create a model with the teaching method  page.](../media/content-understanding/create-a-model-panel.png) 
    
4. Under **Advanced settings**:

    - In the **Content type** section, choose whether to create a new content type or to use an existing one.

    - In the **Compliance** section, under **Retention labels**, select the retention label you want to add. Under **Sensitivity labels**, select the sensitivity label you want to add. If a compliance label has been already applied to the library where the file is stored, it will be shown.

5. When you are ready to create the model, select **Create**.

6. You are now ready to [train the model](create-a-classifier).

### Freeform selection method

Use the **Freeform selection method** to create a [freeform document processing model](freeform-document-processing-overview.md).

1. Select **Freeform selection method**.

2. On the **Freeform selection method: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.

3. On the right panel of the **Create a model with the freeform selection method** page, enter the following information.

    - **Model name** – Enter the name of the model, for example *Service agreements*.

    - **Description** – Enter information about how this model will be used.

        ![Screenshot of the right panel of the Create a model with the Freeform selection method page.](../media/content-understanding/create-a-model-panel.png) 
    
4. Under **Advanced settings**:

    - In the **Content type** section, choose whether to create a new content type or to use an existing one.

    - In the **Compliance** section, under **Retention labels**, select the retention label you want to add. If a compliance label has been already applied to the library where the file is stored, it will be shown.

    > [!NOTE]
    > Sensitivity labels are not available for **Freeform selection method** (freeform document processing models) at this time.

5. When you are ready to create the model, select **Create**.

6. You are now ready to [train the model](train-freeform-document-processing-model.md).

    > [!NOTE]
    > When published, this model type is available for reuse by others who do not own the model. Currently, this model can be edited and shared for editing only by the model owner.

### Layout method

Use the **Layout method** to create a [structured document processing model](form-processing-overview.md).

1. Select **Layout method**.

2. On the **Layout method: Details** page, you'll find more information about the model. If you want to proceed with creating the model, select **Next**.

3. On the right panel of the **Create a model with the layout method** page, enter the following information.

    - **Model name** – Enter the name of the model, for example *Service agreements*.

    - **Description** – Enter information about how this model will be used.

        ![Screenshot of the right panel of the Create a model with the layout method page.](../media/content-understanding/create-a-model-panel.png) 
    
4. Under **Advanced settings**:

    - In the **Content type** section, choose whether to create a new content type or to use an existing one.

    - In the **Compliance** section, under **Retention labels**, select the retention label you want to add. If a compliance label has been already applied to the library where the file is stored, it will be shown.

    > [!NOTE]
    > Sensitivity labels are not available for **Layout method** (structured document processing models) at this time.

5. When you are ready to create the model, select **Create**.

6. You are now ready to [train the model](create-a-form-processing-model.md).

    > [!NOTE]
    > When published, this model type is available for reuse by others who do not own the model. Currently, this model can be edited and shared for editing only by the model owner.

## Set up a prebuilt model

1. In the **Set up a prebuilt model** section, view the types of prebuilt models you can use. Select the type of prebuilt model you want to learn more about or to start using. 

    ![Screenshot of the Use a prebuilt model section on the Set up a prebuilt model page.](../media/content-understanding/use-a-trained-model-section.png) 

    - [**Invoice processing**](#invoice-processing)

    - [**Receipt processing**](#receipt-processing)

2. When you select a prebuilt model, the next page will show you more information about the model. If you want to continue to create the model, select **Next**.

### Invoice processing

1. Select **Invoice processing**.

2. On the **Invoice processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.

3. On the right panel of the **Create an invoice processing model** page, enter the following information.

    - **Model name** – Enter the name of the model, for example *Office expenses*.

    - **Description** – Enter information about how this model will be used.

        ![Screenshot of the right panel of the Create an invoice processing model page.](../media/content-understanding/create-a-model-panel.png) 
    
4. Under **Advanced settings**:

    - In the **Content type** section, choose whether to create a new content type or to use an existing one.

    - In the **Compliance** section, under **Retention labels**, select the retention label you want to add. If a retention label has been already applied to the library where the file is stored, it will be selected. 

    > [!NOTE]
    > Sensitivity labels are not available for prebuilt models at this time.

5. When you are ready to create the model, select **Create**.

6. You are now ready to [complete setting up the model](prebuilt-model-invoice.md).

### Receipt processing

1. Select **Receipt processing**.

2. On the **Receipt processing: Details** page, you'll find more information about the model. If you want to proceed with using the model, select **Next**.

2. On the right panel of the **Create a receipt processing model** page, enter the following information.

    - **Model name** – Enter the name of the model, for example *Office expenses*.

    - **Description** – Enter information about how this model will be used.

        ![Screenshot of the right panel of the Create a model to process receipts page.](../media/content-understanding/create-a-model-panel.png) 
    
3. Under **Advanced settings**:

    - In the **Content type** section, choose whether to create a new content type or to use an existing one.

    - In the **Compliance** section, under **Retention labels**, select the retention label you want to add. If a retention label has been already applied to the library where the file is stored, it will be selected. 

    > [!NOTE]
    > Sensitivity labels are not available for prebuilt models at this time.

4. When you are ready to create the model, select **Create**.

5. You are now ready to [complete setting up the model](prebuilt-model-receipt.md).
--->