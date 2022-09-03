---
title: Configurer SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: Configurer SharePoint Online
ms.openlocfilehash: 1db23fc1d1d5af03358867aaca901a279b0fe7a1
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67584913"
---
# <a name="set-up-sharepoint-syntex"></a>Configurer SharePoint Online

Les administrateurs peuvent utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> pour configurer [Microsoft SharePoint Syntex](index.md). 

Tenez compte des informations suivantes avant de démarrer :

- Dans quels sites SharePoint allez-vous activer le traitement des formulaires ? Tous les sites, certains sites ou des sites sélectionnés ?
- Comment allez-vous nommer votre centre de contenu par défaut ?

Vous pouvez modifier vos paramètres après la configuration initiale dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

Avant la configuration, veillez à planifier la meilleure manière d’installer et de configurer la compréhension de contenu dans votre environnement. Par exemple, vous devez prendre les décisions suivantes :

- Sites SharePoint dans lesquels vous souhaitez activer le traitement des formulaires : tous les sites, certains sites ou des sites sélectionnés
- Le nom et les administrateurs de votre centre de contenu 

## <a name="requirements"></a>Configuration requise 

> [!NOTE]
> Pour accéder au centre d’administration Microsoft 365 et configurer SharePoint Syntex, vous devez disposer des autorisations d’administrateur général ou d’administrateur SharePoint.

En tant qu’administrateur, vous pouvez également modifier vos paramètres sélectionnés à tout moment après la configuration, ainsi que les paramètres de gestion de la compréhension de contenu dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

### <a name="custom-power-platform-environments"></a>Environnements Power Platform personnalisés

Si vous envisagez d’utiliser un environnement Platform Power personnalisé, vous devez installer l’application *Générateur d’IA pour Project Cortex* dans cet environnement. Pour plus d’informations, consultez [Gérer les applications Dynamics 365](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) et recherchez l’application *Générateur d’IA pour Projet Cortex* dans la liste des applications Dynamics 365.

Vous devez également [allouer des crédits Générateur d’IA](/power-platform/admin/capacity-add-on) à l’environnement personnalisé avant de pouvoir créer des modèles de traitement de formulaire. 

Lors de l’utilisation d’un environnement personnalisé, le rôle de sécurité Créateur d’environnement doit être attribué aux créateurs de modèles et le rôle de sécurité Utilisateur de base doit être attribué aux utilisateurs de modèle. Voir [Attribuer un rôle de sécurité à un utilisateur](/power-platform/admin/assign-security-roles) pour obtenir plus d’informations.

Les utilisateurs qui créent des modèles dans un [site de centre de contenu](/microsoft-365/contentunderstanding/create-a-content-center) doivent être membres du site. Les utilisateurs qui créent des modèles localement en dehors du centre de contenu doivent être propriétaires de ces sites.

### <a name="licensing"></a>Gestion des licences

Pour utiliser SharePoint Syntex, votre organisation doit avoir un abonnement à SharePoint Syntex, et chaque utilisateur doit avoir les licences suivantes : SharePoint Syntex licences incluent les applications suivantes, qui doivent toutes être affectées :

- SharePoint Syntex
- SharePoint Syntex : Type DPO
- Service de données courant pour SharePoint Syntex

Pour utiliser le traitement des formulaires, vous avez également besoin de AI Builder crédits. Pour chaque utilisateur sous licence de SharePoint Syntex, une allocation de crédits AI Builder est fournie chaque mois.

Pour plus d’informations sur les licences SharePoint Syntex, voir [Gestion des licences SharePoint Syntex](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>Pour configurer SharePoint Syntex

1. Dans le Centre d’administration Microsoft 365, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Configuration**</a>, puis affichez la section **Fichiers et contenu**.

2. Dans la section **Fichiers et contenu**, sélectionnez **Automatiser la compréhension de contenu**. Notez que la disponibilité de votre crédit AI Builder actuel s’affiche dans la section **D’un coup d’œil**.<br/>

3. À la page **Automatiser la compréhension de contenu** , cliquez sur **Commencer** pour parcourir le processus de configuration. <br/>

    > [!div class="mx-imgBorder"]
    > ![Commencer la configuration.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. Sur la page **Configurer le traitement des formulaires**, vous pouvez choisir d’autoriser ou non les utilisateurs à créer des modèles de traitement de formulaire dans des bibliothèques de documents SharePoint spécifiques. Une option de menu **Créer un modèle de traitement de formulaire** sera disponible dans les rubans des bibliothèques de documents SharePoint où le traitement des formulaires est activé.
 
     Concernant les **bibliothèques SharePoint qui doivent afficher l’option de création d’un modèle de traitement de formulaire**, vous pouvez sélectionner les éléments suivants :</br>
      - **Les bibliothèques dans les sites SharePoint** pour rendre cette option disponible dans toutes les bibliothèques SharePoint au sein de votre organisation.</br>
      - **Ls bibliothèques dans les sites SharePoint sélectionnés**. Sélectionnez ensuite les sites dans lesquels vous souhaitez rendre cette option disponible ou chargez une liste de 50 sites maximum.</br>
      - **Aucune bibliothèque SharePoint** si cette option ne doit être disponible sur aucun site (vous pouvez modifier ce paramètre après la configuration).

   > [!div class="mx-imgBorder"]
   > ![Configurer les options du site de traitement des formulaires.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > La suppression d’un site une fois inclus n’affecte pas les modèles existants appliqués aux bibliothèques de ce site. Cette action ne vous empêche pas non plus d’appliquer des modèles de compréhension de document à une bibliothèque. 
    
    Si vous avez plusieurs environnements Power Platform configurés, vous pouvez choisir celui à utiliser avec le traitement des formulaires. (Cette option ne s’affiche pas si vous n’avez qu’un seul environnement.)

    ![Configurer les options de Power Platform de traitement des formulaires.](../media/content-understanding/setup-power-platform-env.png)

    Pour l’**environnement Power Platform**, vous pouvez sélectionner :
    - **Utilisez l’environnement par défaut** pour utiliser votre environnement Power Platform par défaut.
    - **Utilisez un environnement personnalisé** pour utiliser un environnement personnalisé. Sélectionnez l’environnement que vous souhaitez utiliser dans la liste. ([Voir la configuration requise pour un environnement personnalisé](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    Cliquez sur **Suivant**.

5. Sur la page **Créer un centre de contenu**, vous pouvez créer un site de centre de contenu SharePoint sur lequel vos utilisateurs peuvent créer et gérer des modèles de compréhension de documents. Si vous avez déjà créé un centre de contenu à partir du Centre d’administration SharePoint, ces informations s’affichent ici et vous pouvez simplement sélectionner **Suivant**.

    1. Dans le champ **Nom du site**, tapez le nom souhaité pour votre site de centre de contenu.
    
    1. **L'adresse du site** affichera l'URL de votre site, en fonction de ce que vous avez sélectionné pour le nom du site. Si vous souhaitez le modifier, cliquez sur **Modifier**.

       > [!div class="mx-imgBorder"]
       > ![Créer un centre de contenu.](../media/content-understanding/admin-cu-create-cc.png)</br>

       Sélectionnez **Suivant**.

6. À la page **Examiner et finaliser**, vous pouvez consulter le paramètre sélectionné, puis choisir d’apporter des modifications. Si vos sélections vous conviennent, sélectionnez **Activer**.

7. À la page de confirmation, cliquez sur **Terminé**.

8. Le programme vous renverra alors à la page **Automatiser la compréhension de contenu**. Dans cette page, vous pouvez sélectionner **Gérer** pour modifier vos paramètres de configuration. 

## <a name="assign-licenses"></a>Attribuer des licences

Après avoir configuré SharePoint Syntex, vous devez attribuer des licences aux futurs utilisateurs des fonctionnalités de SharePoint Syntex.

Pour attribuer des licences :

1. Dans la Centre d'administration Microsoft 365, sous **Utilisateurs**, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a>.

2. Sélectionnez les utilisateurs auxquels attribuer une licence, puis choisissez **Gérer les licences de produits**.

3. Sélectionnez **Applications** dans le menu déroulant.

4. Sélectionnez **Afficher les applications pour Microsoft Office Sharepoint Online Syntex**. Sous **Applications**, assurez-vous que les types **Common Data Service pour SharePoint Syntex**, **Microsoft Office SharePoint Online Syntex**, et **Microsoft Office SharePoint Online Syntex – SPO** sont tous sélectionnés.

    > [!div class="mx-imgBorder"]
    > ![Licences de SharePoint Syntex dans le Centre d’administration Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Cliquez sur **Enregistrer les modifications**.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du modèle de traitement de formulaire](/ai-builder/form-processing-model-overview)

[Étape par étape : créer un modèle de compréhension de document (vidéo)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Créer et gérer des environnements dans le Centre d'administration Power Platform](/power-platform/admin/create-environment)
