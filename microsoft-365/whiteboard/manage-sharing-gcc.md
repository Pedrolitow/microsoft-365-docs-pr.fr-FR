---
title: Gérer le partage pour le tableau blanc Microsoft dans les environnements GCC
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment gérer le partage pour le Tableau blanc Microsoft dans les environnements GCC.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: d5ad141d57c271a67d0db65a8b1367aa97131104
ms.sourcegitcommit: 031b3e963478f642a0d23be37a01f23a01cb3d84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2022
ms.locfileid: "67441926"
---
# <a name="manage-sharing-for-microsoft-whiteboard-in-gcc-environments"></a>Gérer le partage pour le tableau blanc Microsoft dans les environnements GCC

> [!NOTE]
> Ces conseils s’appliquent aux environnements cloud de la communauté du gouvernement des États-Unis (GCC). L’expérience de partage diffère en fonction de l’appareil et du client utilisés.

## <a name="share-in-teams-meetings"></a>Partager dans des réunions Teams

Lorsque vous partagez un tableau blanc dans une réunion Teams, le tableau blanc crée un lien de partage. Ce lien est accessible à toute personne au sein de l’organisation. Le tableau blanc est également partagé avec tous les utilisateurs in-tenants de la réunion. Les tableaux blancs sont partagés à l’aide de liens partageables par l’entreprise, quel que soit le paramètre par défaut. La prise en charge du type de lien de partage par défaut est planifiée.

La plupart des comptes d’appareils externes et partagés disposent de davantage de fonctionnalités de collaboration temporaire pendant une réunion. Les utilisateurs peuvent temporairement afficher et collaborer sur des tableaux blancs lorsqu’ils sont partagés dans une réunion Teams, comme PowerPoint Live partage.

Dans ce cas, le tableau blanc fournit un affichage temporaire et une collaboration sur le tableau blanc pendant la réunion Teams uniquement. Un lien de partage n’est pas créé et le Tableau blanc n’accorde pas l’accès au fichier.

Si le partage externe est activé pour OneDrive Entreprise, aucune autre action n’est requise.

Si vous limitez le partage externe pour OneDrive Entreprise, vous pouvez le limiter et simplement activer un nouveau paramètre pour que les comptes d’appareils externes et partagés fonctionnent. Pour ce faire, procédez comme suit :

1. Vérifiez que le tableau blanc est activé pour votre organisation. Pour plus d’informations, consultez [Gérer l’accès au Tableau blanc](manage-whiteboard-access-gcc-high.md).

2. À l’aide de PowerShell, connectez-vous à votre locataire et assurez-vous que le module SharePoint Online est mis à jour en exécutant la commande suivante :

   ```powershell
   Update-Module -Name Microsoft.Online.SharePoint.PowerShell
   ```

3. Exécutez ensuite la commande **Set-SPOTenant** suivante :

   ```powershell
   Set-SPOTenant -AllowAnonymousMeetingParticipantsToAccessWhiteboards On
   ```

Ce paramètre s’applique uniquement aux tableaux blancs et remplace les paramètres précédemment partagés : **OneDriveLoopSharingCapability** et **CoreLoopSharingCapability**. Ces paramètres ne sont plus applicables et peuvent être ignorés.

> [!NOTE]
> Cela s’applique uniquement aux invités et aux utilisateurs fédérés. Il ne s’applique pas aux utilisateurs de réunion anonymes pour l’instant.

Ces modifications doivent prendre environ 60 minutes pour s’appliquer à l’ensemble de votre location.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Démarrer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Activé|Utilisateurs in-tenants : peut créer, afficher et collaborer<br><br>Utilisateurs externes : peut afficher et collaborer pendant la réunion uniquement (le bouton permettant de partager un tableau blanc n’apparaît pas pour les utilisateurs externes)<br><br>Comptes d’appareil partagés : peut afficher et collaborer pendant la réunion uniquement|
|Démarrer le tableau blanc à partir d’un Surface Hub ou d’un Salles Microsoft Teams|N’est pas encore disponible.|||

## <a name="add-as-a-tab-in-teams-channels-and-chats"></a>Ajouter sous la forme d’un onglet dans les canaux et les conversations Teams

Lorsque vous ajoutez un tableau blanc sous forme d’onglet dans un canal ou une conversation Teams, le tableau blanc crée un lien de partage accessible à tous les membres de l’organisation.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Ajouter le tableau blanc à un canal ou une conversation à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Non applicable|Utilisateurs in-tenants : peuvent lancer, afficher et collaborer<br><br>Utilisateurs externes : non pris en charge|

## <a name="create-and-share-in-whiteboard-native-clients"></a>Créer et partager dans des clients natifs de tableau blanc

Lorsque vous partagez un tableau blanc à partir de clients web, de bureau ou mobiles, vous pouvez choisir des personnes spécifiques. Vous pouvez également créer un lien de partage accessible à tous les membres de l’organisation.

>[!NOTE]
> Le partage externe pendant une réunion Teams n’est pas encore disponible, mais sera ajouté dans une version ultérieure.

|Scénario|Stockage et propriété|Paramètres de partage|Expérience de partage|
|---|---|---|---|
|Créer le tableau blanc à partir d’un ordinateur de bureau ou d’un appareil mobile|Stockage : OneDrive Entreprise<br><br>Propriétaire : Utilisateur qui crée le tableau blanc|Non applicable|Utilisateurs internes : peuvent partager au sein de leur organisation<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant|
|Créer le tableau blanc à partir d’un Surface Hub|Stockage : local<br><br>Propriétaire : Aucun|Non applicable|Utilisateurs dans le locataire (bientôt disponibles) : l’utilisateur pourra se connecter pour enregistrer et partager le tableau<br><br>Utilisateurs externes : le partage avec des utilisateurs externes n’est pas pris en charge pour l’instant|
|Créer le tableau blanc à partir de Salles Microsoft Teams|N’est pas encore disponible.|||

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc - GCC High](manage-whiteboard-access-gcc-high.md)

[Gérer les données pour le tableau blanc - GCC High](manage-data-gcc-high.md)

[Gérer les clients pour le Tableau blanc - GCC High](manage-clients-gcc-high.md)