---
title: Microsoft 365 d’expiration de groupe
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
recommendations: false
description: Découvrez les stratégies d Microsoft 365 d’expiration des groupes.
ms.openlocfilehash: 1c0ac1aa7e38fddb85bb9b434c46665cacd1ca69
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2021
ms.locfileid: "61064134"
---
# <a name="microsoft-365-group-expiration-policy"></a>Microsoft 365 d’expiration de groupe

Avec l’augmentation de l’utilisation des groupes Microsoft 365 et des Microsoft Teams, les administrateurs et les utilisateurs ont besoin d’un moyen de nettoyer les groupes et les équipes inutilisés. Une stratégie Microsoft 365'expiration des groupes peut aider à supprimer des groupes inactifs du système et à rendre les choses plus propres.

Lorsqu’un groupe expire, tous ses services associés (boîte aux lettres, planificateur, SharePoint site, équipe, etc.) sont également supprimés.

Lorsqu’un groupe expire, il est « supprimé (récupérez) », ce qui signifie qu’il peut toujours être récupéré pendant 30 jours.

Les administrateurs peuvent spécifier une période d’expiration et tout groupe inactif qui arrive à la fin de cette période et qui n’est pas renouvelé est supprimé. (Cela inclut les équipes archivées.) La période d’expiration commence lors de la création du groupe ou à la date de son dernier renouvellement. Les propriétaires de groupe sont automatiquement envoyés un e-mail avant l’expiration qui leur permet de renouveler le groupe pour un autre intervalle d’expiration. Teams utilisateurs voient les notifications persistantes dans Teams.

Les groupes qui sont activement utilisés sont renouvelés automatiquement. L’une des actions suivantes recrée automatiquement un groupe :
- SharePoint : afficher, modifier, télécharger, déplacer, partager ou télécharger des fichiers. (L’affichage d SharePoint page ne compte pas comme une action de renouvellement automatique.)
- Outlook - rejoindre un groupe, lire ou écrire un message de groupe à partir du groupe, et comme un message (Outlook sur le web).
- Teams - visite d’un canal d’équipe.

Notez que la seule activité Yammer qui déclenchera le renouvellement automatique d’un groupe est le téléchargement d’un document vers SharePoint au sein de la communauté.

> [!IMPORTANT]
> Lorsque vous modifiez la stratégie d’expiration, le service recalcule la date d’expiration de chaque groupe. Il commence toujours à compter de la date de création du groupe, puis applique la nouvelle stratégie d’expiration.

Il est important de savoir que l’expiration est désactivée par défaut. Les administrateurs doivent l’activer pour leur organisation s’ils souhaitent l’utiliser.

> [!NOTE]
> La configuration et l’utilisation de la stratégie d’expiration pour les groupes Microsoft 365 vous obligent à posséder, mais pas nécessairement attribuer des licences Azure AD Premium pour les membres de tous les groupes auquel la stratégie d’expiration est appliquée. Pour plus d’informations, voir [La mise en Azure Active Directory Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Qui pouvez configurer et utiliser la stratégie d’expiration Microsoft 365 groupes de sécurité ?

|Role|Ce qu’ils peuvent faire|
|---------|---------|
|Office 365 administrateur général (dans Azure, administrateur d’entreprise), administrateur utilisateur|Créez, lisez, mettez à jour ou supprimez les paramètres de stratégie d Microsoft 365 d’expiration des groupes.|
|Utilisateur|Renouveler [ou restaurer](/azure/active-directory/users-groups-roles/groups-restore-deleted) un groupe Microsoft 365 dont il est propriétaire|

## <a name="how-to-set-the-expiration-policy"></a>Comment définir la stratégie d’expiration

Comme indiqué ci-dessus, l’expiration est désactivée par défaut. Un administrateur devra activer la stratégie d’expiration et définir les propriétés pour qu’elle prenne effet. Pour l’activer, go to **Azure Active Directory**  >  **Groups**  >  **Expiration**. Ici, vous pouvez définir la durée de vie du groupe par défaut et spécifier à l’avance le délai d’accès des première et deuxième notifications d’expiration au propriétaire du groupe.

La durée de vie du groupe est spécifiée en jours et peut être définie sur 180, 365 ou sur une valeur personnalisée que vous spécifiez. La valeur personnalisée doit être d’au moins 30 jours.

Si le groupe n’a pas de propriétaire, les e-mails d’expiration sont envoyés à l’administrateur spécifié.

Vous pouvez définir la stratégie pour tous vos groupes, uniquement les groupes sélectionnés (jusqu’à 500), ou la désactiver complètement en sélectionnant **Aucun**. Notez qu’il n’est actuellement pas possible d’avoir des stratégies différentes pour différents groupes.

![Capture d’écran des paramètres d’expiration des groupes Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Fonctionnement de l’expiration avec la stratégie de rétention

Si vous avez mis en place une stratégie de rétention pour les groupes dans le Centre de sécurité et conformité, la stratégie d’expiration fonctionne de manière transparente avec la stratégie de rétention. Lorsqu’un groupe expire, les conversations et les fichiers de boîte aux lettres du groupe dans le site de groupe sont conservés dans le conteneur de rétention pendant le nombre de jours défini dans la stratégie de rétention. Toutefois, les utilisateurs ne voient pas le groupe, ni son contenu, après expiration.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Comment et quand un propriétaire de groupe apprend si ses groupes vont expirer

Les propriétaires de groupe ne seront avertis que par courrier électronique. Si le groupe a été créé via le Planificateur, SharePoint ou toute autre application, les notifications d’expiration sont toujours envoyés par courrier électronique. Si le groupe a été créé via Teams, le propriétaire du groupe reçoit une notification de renouvellement via la section activité. Il n’est pas recommandé d’activer l’expiration sur un groupe si le propriétaire de votre groupe n’a pas d’adresse de messagerie valide.

30 jours avant l’expiration du groupe, les propriétaires du groupe (ou les adresses de messagerie que vous avez spécifiées pour les groupes qui n’ont pas de propriétaire) recevront un e-mail leur permettant de renouveler facilement le groupe. S’il ne le renouvelle pas, il reçoit un autre e-mail de renouvellement 15 jours avant l’expiration. S’ils ne l’ont toujours pas renouvelé, ils recevront une notification par courrier électronique le jour avant l’expiration.

Si, pour une raison quelconque, aucun des propriétaires ou administrateurs ne renouvelle le groupe avant son expiration, l’administrateur peut toujours restaurer le groupe jusqu’à 30 jours après l’expiration. Pour plus d’informations, [voir : Restaurer un groupe Microsoft 365 supprimé.](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54)

## <a name="archiving-group-contents"></a>Contenu du groupe d’archivage

Si vous avez un groupe que vous ne prévoyez plus d’utiliser, mais que vous souhaitez conserver son contenu, voir Groupes d’archivage, équipes et [Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour plus d’informations sur l’exportation d’informations à partir des différents services de groupes.

## <a name="related-topics"></a>Sujets connexes

[Recommandations en matière de planification de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Vue d’ensemble des stratégies de rétention](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Attribuer un nouveau propriétaire à un groupe orphelin](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Configurer l’expiration Microsoft 365 groupes](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
