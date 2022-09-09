---
title: Gérer le partage pour le Tableau blanc Microsoft
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.service: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment gérer le partage pour le Tableau blanc Microsoft.
ms.openlocfilehash: 53409c352a3be95a720d6ebfc0759270140c7400
ms.sourcegitcommit: 6d86713c3b1da2db338c78fa60bd7d93e24aa6f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2022
ms.locfileid: "67639501"
---
# <a name="manage-sharing-for-microsoft-whiteboard"></a>Gérer le partage pour le Tableau blanc Microsoft

L’expérience de partage diffère selon que vous participez à une réunion Teams, si vous utilisez un appareil partagé ou quels paramètres de partage au niveau du locataire sont activés. Les scénarios suivants s’appliquent uniquement aux nouveaux tableaux blancs créés après le basculement du tableau blanc vers l’utilisation du stockage OneDrive Entreprise. Il n’y a aucune modification apportée aux tableaux créés précédemment encore stockés dans Azure.

## <a name="share-in-teams-meetings"></a>Partager dans des réunions Teams

Lorsque vous partagez un tableau blanc dans une réunion Teams, le tableau blanc crée un lien de partage. Ce lien est accessible à toute personne au sein de l’organisation. Le tableau blanc est également partagé avec tous les utilisateurs in-tenants de la réunion. Les tableaux blancs sont partagés à l’aide de liens partageables par l’entreprise, quel que soit le paramètre par défaut. La prise en charge du type de lien de partage par défaut est planifiée.

Il existe davantage de fonctionnalités de collaboration temporaire par des comptes d’appareils externes et partagés pendant une réunion Teams. Les utilisateurs peuvent temporairement afficher et collaborer sur des tableaux blancs partagés dans une réunion, de la même façon que PowerPoint Live partage.

Dans ce cas, le tableau blanc fournit un affichage temporaire et une collaboration sur le tableau blanc pendant la réunion Teams uniquement. Un lien de partage n’est pas créé et le Tableau blanc n’accorde pas l’accès au fichier.

Si le partage externe est activé pour OneDrive Entreprise, aucune autre action n’est requise.

Si vous limitez le partage externe pour OneDrive Entreprise, vous pouvez le limiter et simplement activer un nouveau paramètre pour que les comptes d’appareils externes et partagés fonctionnent. Pour ce faire, procédez comme suit :

1. Vérifiez que le tableau blanc est activé pour votre organisation. Pour plus d’informations, consultez [Gérer l’accès au Tableau blanc](manage-whiteboard-access-organizations.md).

2. À l’aide de PowerShell, connectez-vous à votre locataire et assurez-vous que le module SharePoint Online est mis à jour en exécutant la commande suivante :

   ```powershell
   Update-Module -Name Microsoft.Online.SharePoint.PowerShell
   ```

3. Exécutez ensuite la commande **Set-SPOTenant** suivante :

   ```powershell
   Set-SPOTenant -AllowAnonymousMeetingParticipantsToAccessWhiteboards On
   ```

4. Assurez-vous que le paramètre de réunion Teams **les utilisateurs anonymes peuvent interagir avec les applications dans les réunions** est activé. Si vous l’avez désactivé, les utilisateurs anonymes (par opposition aux invités ou aux utilisateurs fédérés) n’auront pas accès au tableau blanc pendant la réunion.

Ce paramètre s’applique uniquement aux tableaux blancs et remplace les paramètres précédemment partagés : **OneDriveLoopSharingCapability** et **CoreLoopSharingCapability**. Ces paramètres ne sont plus applicables et peuvent être ignorés.

> [!NOTE]
> Par défaut, le paramètre de réunion Teams **permettant aux utilisateurs anonymes d’interagir avec les applications dans les réunions** est activé. Si vous l’avez désactivé, les utilisateurs anonymes (par opposition aux invités ou aux utilisateurs fédérés) n’auront pas accès au tableau blanc pendant la réunion.

Ces modifications doivent prendre environ 60 minutes pour s’appliquer à l’ensemble de votre location.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Démarrer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Activé|Utilisateurs in-tenants : peut créer, afficher et collaborer<br><br>Utilisateurs externes : peut afficher et collaborer pendant la réunion uniquement (le bouton permettant de partager un tableau blanc n’apparaît pas pour les utilisateurs externes)<br><br>Comptes d’appareil partagés : peut afficher et collaborer pendant la réunion uniquement|
|Démarrer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Désactivé|Utilisateurs in-tenants : peuvent lancer, afficher et collaborer<br><br>Utilisateurs externes : impossible d’afficher ou de collaborer<br><br>Comptes d’appareil partagés : impossible d’afficher ou de collaborer|
|Démarrer le tableau blanc à partir d’un Surface Hub ou d’un Salles Microsoft Teams|Stockage : Azure (les fichiers tableau blanc seront déplacés vers OneDrive Entreprise à l’avenir)<br><br>Propriétaire : participant à la réunion|Non applicable|Utilisateurs in-tenants : peuvent lancer, afficher et collaborer<br><br>Utilisateurs externes : peut afficher et collaborer pendant la réunion uniquement<br><br> Comptes d’appareil partagés : peut afficher et collaborer pendant la réunion uniquement|

> [!NOTE]
>Si un tableau blanc est stocké dans OneDrive et déjà attaché à une réunion, il ne peut pas être lancé sur un Surface Hub ou un appareil Salles Microsoft Teams. Un utilisateur authentifié sur un autre appareil doit le faire. Nous travaillons sur un correctif pour ce problème.



## <a name="add-as-a-tab-in-teams-channels-and-chats"></a>Ajouter sous la forme d’un onglet dans les canaux et les conversations Teams

Lorsque vous ajoutez un tableau blanc sous forme d’onglet dans un canal ou une conversation Teams, le tableau blanc crée un lien de partage accessible à tous les membres de l’organisation.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Ajouter le tableau blanc à un canal ou une conversation à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Non applicable (s’applique uniquement aux réunions)|Utilisateurs in-tenants : peuvent lancer, afficher et collaborer<br><br>Utilisateurs externes : non pris en charge<br><br>Invités Teams : Non pris en charge<br><br>Comptes d’appareil partagés : non applicable|

## <a name="create-and-share-in-whiteboard-native-clients"></a>Créer et partager dans des clients natifs de tableau blanc

Lorsque vous partagez des tableaux blancs à partir de clients web, de bureau ou mobiles, vous pouvez choisir des personnes spécifiques. Vous pouvez également créer un lien de partage accessible à tous les membres de l’organisation.

> [!NOTE]
> Le partage externe pendant une réunion Teams n’est pas encore disponible, mais sera ajouté dans une version ultérieure.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Créer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Non applicable (s’applique uniquement aux réunions)|Utilisateurs internes : peuvent partager au sein de leur organisation<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant|
|Créer le tableau blanc à partir d’un Surface Hub|Stockage : local<br><br>Propriétaire : Aucun (sauf si l’utilisateur se connecte pour enregistrer et partager la carte, ce qui enregistre dans OneDrive Entreprise. Le partage facile sera ajouté à l’avenir.|Non applicable (s’applique uniquement aux réunions)|Utilisateurs in-tenants : l’utilisateur doit se connecter pour enregistrer et partager la carte (easy share sera ajouté à l’avenir)<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant en dehors d’une réunion Teams|
|Créer le tableau blanc à partir de Salles Microsoft Teams|Non encore pris en charge|Non applicable (s’applique uniquement aux réunions)|Non encore pris en charge|

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc](manage-whiteboard-access-organizations.md)

[Gérer les données pour le tableau blanc](manage-data-organizations.md)

[Déployer le tableau blanc sur Windows](deploy-on-windows-organizations.md)
