---
title: Configurer SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection: enabler-strategic
search.appverid: MET150
localization_priority: Priority
description: Configurer la compréhension de contenu dans Projet Cortex
ms.openlocfilehash: dfbcc8e41a28e3107b58ac6b8d471e3a2a08d036
ms.sourcegitcommit: e7bf23df4852b78912229d1d38ec475223597f34
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49087570"
---
# <a name="set-up-sharepoint-syntex"></a>Configurer SharePoint Online

Les administrateurs peuvent utiliser le Centre d’administration Microsoft 365 pour configurer [Microsoft SharePoint Syntex](index.md). 

Tenez compte des informations suivantes avant de démarrer :

- Which SharePoint sites will you enable form processing? All of them, some, or select sites?
- Comment allez-vous nommer votre centre de contenu par défaut ?

Vous pouvez modifier vos paramètres après la configuration initiale dans le Centre d’administration Microsoft 365.

Prior to setup, make sure to plan for the best way to set up and configure content understanding in your environment. For example, you need to make considerations about the following names of:

- Sites SharePoint pour lesquels vous souhaitez activer le traitement des formulaires : tous les sites, certains sites ou des sites sélectionnés
- Votre centre de contenu et le nom de l’administrateur de site principal

## <a name="requirements"></a>Configuration requise 

> [!NOTE]
> Pour accéder au Centre d’administration Microsoft 365 et configurer la compréhension de contenu, vous devez disposer des autorisations d’administrateur général ou d’administrateur SharePoint.

En tant qu’administrateur, vous pouvez également modifier vos paramètres sélectionnés à tout moment après la configuration, ainsi que les paramètres de gestion de la compréhension de contenu dans le Centre d’administration Microsoft 365.

## <a name="to-set-up-sharepoint-syntex"></a>Pour configurer SharePoint Syntex

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Configuration**, puis affichez la section **Fichiers et contenu**.

2. Dans la section **Fichiers et contenu**, sélectionnez **Automatiser la compréhension de contenu**.<br/>

3. À la page **Automatiser la compréhension de contenu** , cliquez sur **Commencer** pour parcourir le processus de configuration.<br/>

    > [!div class="mx-imgBorder"]
    > ![Commencer la configuration](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. On the **Configure Form Processing** page, you can choose if you want to let users be able to create form processing models in specific SharePoint document libraries. A menu option will be available in the document library ribbon to **Create a form processing model** in SharePoint document libraries in which it is enabled.
 
     Concernant les **bibliothèques SharePoint qui doivent afficher l’option de création d’un modèle de traitement de formulaire**, vous pouvez sélectionner les éléments suivants :</br>
      - **Toutes les bibliothèques SharePoint** pour rendre cette option disponible dans toutes les bibliothèques SharePoint au sein de votre organisation.</br>
      - **Seules les bibliothèques de sites sélectionnés**. Sélectionnez ensuite les sites dans lesquels vous souhaitez rendre cette option disponible ou chargez une liste de 50 sites maximum.</br>
      - **Aucune bibliothèque SharePoint** si cette option ne doit être disponible sur aucun site (vous pouvez modifier ce paramètre après la configuration).

   > [!div class="mx-imgBorder"]
   > ![Configurer le traitement des formulaires](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > La suppression d’un site une fois inclus n’affecte pas les modèles existants appliqués aux bibliothèques de ce site. Cette action ne vous empêche pas non plus d’appliquer des modèles de compréhension de document à une bibliothèque. 
    
5. À la page **Créer un centre de contenu**, vous pouvez créer un site de centre de contenu SharePoint. Vos utilisateurs pourront alors créer et gérer des modèles de compréhension de document sur ce même site.

    1. Dans le champ **Nom du site**, tapez le nom souhaité pour votre site de centre de contenu.
    
    1. The **Site address** will show the URL for your site, based on what you selected for the site name. If you want to change it, click **Edit**.

       > [!div class="mx-imgBorder"]
       > ![Créer un centre de contenu](../media/content-understanding/admin-cu-create-cc.png)</br>

       Sélectionnez **Suivant**.

6. On the **Review and finish** page, you can look at your selected setting and choose to make changes. If you are satisfied with your selections, select **Activate**.

7. À la page de confirmation, cliquez sur **Terminé**.

8. You'll be returned to your **Automate content understanding** page. From this page, you can select **Manage** to make any changes to your configuration settings. 

## <a name="assign-licenses"></a>Attribuer des licences

Après avoir configuré SharePoint Syntex, vous devez attribuer des licences aux futurs utilisateurs des fonctionnalités de SharePoint Syntex.

Pour attribuer des licences :

1. Dans le Centre d’administration Microsoft 365, sous **Utilisateurs**, cliquez sur **Utilisateurs actifs**.

2. Sélectionnez les utilisateurs auxquels attribuer une licence, puis cliquez sur **Gérer les licences de produits**.

3. Sélectionnez **Attribuer plus**.

4. Select **SharePoint Syntex**. Under **Apps**, make sure **Common Data Service for SharePoint Syntex**, **SharePoint Syntex**, and **SharePoint Syntex - SPO type** are all selected.

    > [!div class="mx-imgBorder"]
    > ![Licences SharePoint Syntex dans le Centre d’administration Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Cliquez sur **Enregistrer les modifications**.

## <a name="ai-builder-credits"></a>Crédits AI Builder

If you have 300 or more SharePoint Syntex licenses for SharePoint Syntex in your organization, you will be allocated one million AI Builder credits. If you have fewer than 300 licenses, you must purchase AI Builder credits in order to use forms processing.

Vous pouvez estimer la capacité d’AI Builder qui vous convient, grâce à la calculatrice [AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Accédez au [centre d’administration Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) pour vérifier vos crédits et leur utilisation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du modèle de traitement de formulaire](https://docs.microsoft.com/ai-builder/form-processing-model-overview)

[Étape par étape : créer un modèle de compréhension de document (vidéo)](https://www.youtube.com/watch?v=DymSHObD-bg)

