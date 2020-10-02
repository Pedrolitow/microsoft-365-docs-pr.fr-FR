---
title: Configurer SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: MET150
localization_priority: Priority
description: Configurer la compréhension de contenu dans Projet Cortex
ms.openlocfilehash: 7fb5998729c9f11902f8fdfaffa62b160928077c
ms.sourcegitcommit: f7ca339bdcad38796c550064fb152ea09687d0f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48321348"
---
# <a name="set-up-sharepoint-syntex"></a>Configurer SharePoint Online

Les administrateurs peuvent utiliser le Centre d’administration Microsoft 365 pour configurer [Microsoft SharePoint Syntex](document-understanding-overview.md). 

Tenez compte des informations suivantes avant de démarrer :

- Pour quels sites SharePoint allez-vous activer le traitement des formulaires ? Tous les sites, certains sites ou des sites sélectionnés ?
- Comment allez-vous nommer votre centre de contenu par défaut ?

Vous pouvez modifier vos paramètres après la configuration initiale dans le Centre d’administration Microsoft 365.

Le contenu de cet article est destiné à la préversion privée du Projet Cortex. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Avant la configuration, veillez à planifier la meilleure manière d’installer et de configurer la compréhension de contenu dans votre environnement. Par exemple, vous devez prendre en compte les noms suivants :

- Sites SharePoint pour lesquels vous souhaitez activer le traitement des formulaires : tous les sites, certains sites ou des sites sélectionnés
- Votre centre de contenu et le nom de l’administrateur de site principal

## <a name="requirements"></a>Configuration requise 

> [!NOTE]
> Pour accéder au Centre d’administration Microsoft 365 et configurer la compréhension de contenu, vous devez disposer des autorisations d’administrateur général ou d’administrateur SharePoint.

En tant qu’administrateur, vous pouvez également modifier vos paramètres sélectionnés à tout moment après la configuration, ainsi que les paramètres de gestion de la compréhension de contenu dans le Centre d’administration Microsoft 365.

## <a name="to-set-up-sharepoint-syntex"></a>Pour configurer SharePoint Syntex

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Configuration**, puis affichez la section **Connaissances organisationnelles**.

2. Dans la section **Connaissances organisationnelles**, sélectionnez **Automatiser la compréhension de contenu**.<br/>

    ![Page de configuration des connaissances organisationnelles](../media/content-understanding/admin-org-knowledge-options.png)</br>

3. À la page **Automatiser la compréhension de contenu** , cliquez sur **Commencer** pour parcourir le processus de configuration.<br/>

    ![Commencer la configuration](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. Dans la page Activer le balisage d’image, choisissez d’autoriser ou non le [balisage d’image](image-tagging.md).

    ![Capture d’écran des options de balisage d’image](../media/content-understanding/admin-content-understanding-setup-image-tagging.png)</br>

5. Sur la page **Configurer le traitement des formulaires**, vous pouvez choisir d’autoriser ou non les utilisateurs à créer des modèles de traitement de formulaire dans des bibliothèques de documents SharePoint spécifiques. Une option de menu **Créer un modèle de traitement de formulaire** sera disponible dans les rubans des bibliothèques de documents SharePoint où le traitement des formulaires est activé.
 
     Concernant les **bibliothèques SharePoint qui doivent afficher l’option de création d’un modèle de traitement de formulaire**, vous pouvez sélectionner les éléments suivants :</br>
      - **Toutes les bibliothèques SharePoint** pour rendre cette option disponible dans toutes les bibliothèques SharePoint au sein de votre organisation.</br>
      - **Seules les bibliothèques de sites sélectionnés**. Sélectionnez ensuite les sites dans lesquels vous souhaitez rendre cette option disponible ou chargez une liste de 50 sites maximum.</br>
      - **Aucune bibliothèque SharePoint** si cette option ne doit être disponible sur aucun site (vous pouvez modifier ce paramètre après la configuration).

   ![Configurer le traitement des formulaires](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > La suppression d’un site une fois inclus n’affecte pas les modèles existants appliqués aux bibliothèques de ce site. Cette action ne vous empêche pas non plus d’appliquer des modèles de compréhension de document à une bibliothèque. 
    
6. À la page **Créer un centre de contenu**, vous pouvez créer un site de centre de contenu SharePoint. Vos utilisateurs pourront alors créer et gérer des modèles de compréhension de document sur ce même site. </br>
    a. Dans le champ **Nom du site**, tapez le nom souhaité pour votre site de centre de contenu.</br>
    b. Le champ **Adresse du site** affiche l’URL de votre site, en fonction du nom de site choisi. Si vous souhaitez le modifier, cliquez sur **Modifier**.</br>

      ![Créer un centre de contenu](../media/content-understanding/admin-cu-create-cc.png)</br>

    Sélectionnez **Suivant**.

7. À la page **Examiner et finaliser**, vous pouvez consulter le paramètre sélectionné, puis choisir d’apporter des modifications. Si vos sélections vous conviennent, sélectionnez **Activer**.

8. À la page de confirmation, cliquez sur **Terminé**.

9. Le programme vous renverra alors à la page **Automatiser la compréhension de contenu**. Dans cette page, vous pouvez sélectionner **Gérer** pour modifier vos paramètres de configuration. 

## <a name="assign-licenses"></a>Attribuer des licences

Après avoir configuré SharePoint Syntex, vous devez attribuer des licences aux futurs utilisateurs des fonctionnalités de SharePoint Syntex.

Pour attribuer des licences :

1. Dans le Centre d’administration Microsoft 365, sous **Utilisateurs**, cliquez sur **Utilisateurs actifs**.

2. Sélectionnez les utilisateurs auxquels attribuer une licence, puis cliquez sur **Gérer les licences de produits**.

3. Sélectionnez **Attribuer plus**.

4. Sélectionnez **Services de contenu intelligents**. Sous **Applications**, vérifiez que les deux options **Common Data Service pour les services de contenu intelligents** et **Services de contenu intelligents** sont sélectionnés.

    ![Licences SharePoint Syntex dans le Centre d’administration Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Cliquez sur **Enregistrer les modifications**.

## <a name="ai-builder-credits"></a>Crédits AI Builder

Si vous possédez 300 licences SharePoint Syntex au sein de votre organisation, vous bénéficierez d’un million de crédits AI Builder. Si vous possédez moins de 300 licences, vous devez acheter des crédits AI Builder pour utiliser le traitement des formulaires.

Vous pouvez estimer la capacité d’AI Builder qui vous convient, grâce à la calculatrice [AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Accédez au [centre d’administration Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) pour vérifier vos crédits et leur utilisation.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du modèle de traitement de formulaire](https://docs.microsoft.com/ai-builder/form-processing-model-overview)

[Étape par étape : créer un modèle de compréhension de document (vidéo)](https://www.youtube.com/watch?v=DymSHObD-bg)

