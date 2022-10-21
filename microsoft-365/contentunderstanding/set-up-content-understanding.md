---
title: Configurer Microsoft Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-syntex
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: Configurez Microsoft Syntex.
ms.openlocfilehash: b6a7309e9ae833f643930d9f308c1b748afeb0f5
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659584"
---
# <a name="set-up-microsoft-syntex"></a>Configurer Microsoft Syntex

Les administrateurs peuvent utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> pour configurer Microsoft Syntex. 

Tenez compte des informations suivantes avant de démarrer :

- Dans quels sites SharePoint allez-vous activer le traitement des documents ? Tous les sites, certains sites ou des sites sélectionnés ?
- Comment allez-vous nommer votre centre de contenu par défaut ?

Vous pouvez modifier vos paramètres après la configuration initiale dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

Prior to setup, make sure to plan for the best way to set up and configure content understanding in your environment. For example, you need to make the following decisions:

- Les sites SharePoint dans lesquels vous souhaitez activer le traitement des documents - tous, certains ou certains sites sélectionnés
- Le nom et les administrateurs de votre centre de contenu 

## <a name="requirements"></a>Configuration requise 

> [!NOTE]
> Vous devez disposer des autorisations d’administrateur général ou d’administrateur SharePoint pour pouvoir accéder au Centre d'administration Microsoft 365 et configurer Syntex.

En tant qu’administrateur, vous pouvez également modifier vos paramètres sélectionnés à tout moment après la configuration, ainsi que les paramètres de gestion de la compréhension de contenu dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

### <a name="custom-power-platform-environments"></a>Environnements Power Platform personnalisés

Si vous envisagez d’utiliser un environnement Platform Power personnalisé, vous devez installer l’application *Générateur d’IA pour Project Cortex* dans cet environnement. Pour plus d’informations, consultez [Gérer les applications Dynamics 365](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) et recherchez l’application *Générateur d’IA pour Projet Cortex* dans la liste des applications Dynamics 365.

Vous devez également [allouer des crédits AI Builder](/power-platform/admin/capacity-add-on) à l’environnement personnalisé avant de pouvoir créer des modèles de traitement de documents. 

When using a custom environment, model creators must be assigned the Environment Maker security role and model users must be assigned the Basic User security role. See [Assign a security role to a user](/power-platform/admin/assign-security-roles) for more information.

Les utilisateurs qui créent des modèles dans un [site de centre de contenu](/microsoft-365/contentunderstanding/create-a-content-center) doivent être membres du site. Les utilisateurs qui créent des modèles localement en dehors du centre de contenu doivent être propriétaires de ces sites.

### <a name="licensing"></a>Gestion des licences

Pour utiliser Syntex, votre organisation doit disposer d’un abonnement à Syntex, et chaque utilisateur doit disposer d’une licence affectée. Les licences Syntex incluent les applications suivantes, qui doivent toutes être affectées :

- Syntex
- Syntex - Type SPO
- Common Data Service pour Syntex

Pour utiliser des modèles de traitement de documents structurés ou de forme libre, vous avez également besoin de crédits AI Builder. Pour chaque utilisateur sous licence de Syntex, une allocation de crédits AI Builder est fournie chaque mois.

Pour plus d’informations sur les licences Syntex, consultez [Licences Microsoft Syntex](syntex-licensing.md)

## <a name="to-set-up-syntex"></a>Pour configurer Syntex

1. Dans le Centre d’administration Microsoft 365, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Configuration**</a>, puis affichez la section **Fichiers et contenu**.

2. Dans la section **Fichiers et contenu**, sélectionnez **Automatiser la compréhension de contenu**. Notez que la disponibilité de votre crédit AI Builder actuel s’affiche dans la section **D’un coup d’œil**.<br/>

3. À la page **Automatiser la compréhension de contenu** , cliquez sur **Commencer** pour parcourir le processus de configuration. <br/>

    > [!div class="mx-imgBorder"]
    > ![Commencer la configuration.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. Dans la page **Configurer le traitement des** formulaires, vous pouvez choisir si vous souhaitez permettre aux utilisateurs de créer des modèles de traitement de documents dans des bibliothèques de documents SharePoint spécifiques. Une option de menu **Créer un modèle de traitement de formulaire** sera disponible dans les rubans des bibliothèques de documents SharePoint où le traitement des formulaires est activé.
 
     Concernant les **bibliothèques SharePoint qui doivent afficher l’option de création d’un modèle de traitement de formulaire**, vous pouvez sélectionner les éléments suivants :</br>
      - **Les bibliothèques dans les sites SharePoint** pour rendre cette option disponible dans toutes les bibliothèques SharePoint au sein de votre organisation.</br>
      - **Ls bibliothèques dans les sites SharePoint sélectionnés**. Sélectionnez ensuite les sites dans lesquels vous souhaitez rendre cette option disponible ou chargez une liste de 50 sites maximum.</br>
      - **Aucune bibliothèque SharePoint** si cette option ne doit être disponible sur aucun site (vous pouvez modifier ce paramètre après la configuration).

   > [!div class="mx-imgBorder"]
   > ![Configurer les options de site de traitement des documents.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > La suppression d’un site après son inclusion n’affecte pas les modèles existants appliqués aux bibliothèques de ce site ni la possibilité d’appliquer des modèles de traitement de documents non structurés à une bibliothèque. 
    
    Si plusieurs environnements Power Platform sont configurés, vous pouvez choisir celui avec lequel vous souhaitez utiliser pour le traitement des documents. (Cette option ne s’affiche pas si vous n’avez qu’un seul environnement.)

    ![Configurer les options Power Platform pour le traitement des documents.](../media/content-understanding/setup-power-platform-env.png)

    Pour l’**environnement Power Platform**, vous pouvez sélectionner :
    - **Utilisez l’environnement par défaut** pour utiliser votre environnement Power Platform par défaut.
    - **Utilisez un environnement personnalisé** pour utiliser un environnement personnalisé. Sélectionnez l’environnement que vous souhaitez utiliser dans la liste. ([Voir la configuration requise pour un environnement personnalisé](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    Cliquez sur **Suivant**.

5. Dans la page **Créer un centre** de contenu, vous pouvez créer un site de centre de contenu SharePoint où vos utilisateurs peuvent créer et gérer des modèles de traitement de documents non structurés. Si vous avez déjà créé un centre de contenu à partir du Centre d’administration SharePoint, ces informations s’affichent ici et vous pouvez simplement sélectionner **Suivant**.

    1. Dans le champ **Nom du site**, tapez le nom souhaité pour votre site de centre de contenu.
    
    1. The **Site address** will show the URL for your site, based on what you selected for the site name. If you want to change it, click **Edit**.

       > [!div class="mx-imgBorder"]
       > ![Créer un centre de contenu.](../media/content-understanding/admin-cu-create-cc.png)</br>

       Sélectionnez **Suivant**.

6. À la page **Examiner et finaliser**, vous pouvez consulter le paramètre sélectionné, puis choisir d’apporter des modifications. Si vos sélections vous conviennent, sélectionnez **Activer**.

7. À la page de confirmation, cliquez sur **Terminé**.

8. Le programme vous renverra alors à la page **Automatiser la compréhension de contenu**. Dans cette page, vous pouvez sélectionner **Gérer** pour modifier vos paramètres de configuration. 

## <a name="assign-licenses"></a>Attribuer des licences

Une fois que vous avez configuré Syntex, vous devez attribuer des licences aux utilisateurs qui utiliseront les fonctionnalités de Syntex.

Pour attribuer des licences :

1. Dans la Centre d'administration Microsoft 365, sous **Utilisateurs**, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a>.

2. Sélectionnez les utilisateurs auxquels attribuer une licence, puis choisissez **Gérer les licences de produits**.

3. Sélectionnez **Applications** dans le menu déroulant.

4. Sélectionnez **Afficher les applications pour Syntex**. Sous **Applications**, vérifiez que **Common Data Service pour Syntex**, **Syntex** et **Syntex - Type SPO** sont tous sélectionnés.

    > [!div class="mx-imgBorder"]
    > ![Licences Syntex dans le Centre d'administration Microsoft 365.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. Cliquez sur **Enregistrer les modifications**.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du modèle de traitement de document dans AI Builder](/ai-builder/form-processing-model-overview)

[Créer et gérer des environnements dans le Centre d'administration Power Platform](/power-platform/admin/create-environment)
