---
title: Stratégie d’expiration de groupe Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
description: Découvrez les stratégies d’expiration des groupes Microsoft 365.
ms.openlocfilehash: 4b283bcc9f4e54462a71b9aee70d6312b9f127d6
ms.sourcegitcommit: 5480982967a90ca3060a59676a6b29155f2de861
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49350711"
---
# <a name="microsoft-365-group-expiration-policy"></a>Stratégie d’expiration de groupe Microsoft 365

Avec l’augmentation de l’utilisation des groupes Microsoft 365 et de Microsoft Teams, les administrateurs et les utilisateurs doivent disposer d’un moyen de nettoyer les groupes et les équipes inutilisés. Une stratégie d’expiration de groupes Microsoft 365 peut vous aider à supprimer des groupes inactifs du système et à effectuer le nettoyage.

Lorsqu’un groupe expire, tous ses services associés (la boîte aux lettres, le planificateur, le site SharePoint, l’équipe, etc.) sont également supprimés.

Lorsqu’un groupe expire, il est « supprimé de manière récupérable », ce qui signifie qu’il peut toujours être récupéré pendant 30 jours maximum.

Les administrateurs peuvent spécifier une période d’expiration et tout groupe inactif qui atteint la fin de cette période, et qui n’est pas renouvelé, sera supprimé. (Cela inclut les équipes archivées.) La période d’expiration commence lorsque le groupe est créé, ou à la date à laquelle il a été renouvelé pour la dernière fois. Les propriétaires de groupe reçoivent automatiquement un courrier électronique avant l’expiration qui leur permet de renouveler le groupe pour un autre intervalle d’expiration. Les utilisateurs de teams verront les notifications permanentes dans Teams.

Les groupes qui sont actifs en cours d’utilisation sont automatiquement renouvelés. L’une des actions suivantes permet de renouveler automatiquement un groupe :
- SharePoint : afficher, modifier, télécharger, déplacer, partager ou télécharger des fichiers. (L’affichage d’une page SharePoint n’est pas compté comme une action de renouvellement automatique.)
- Outlook-rejoindre un groupe, lire ou écrire un message de groupe à partir du groupe et comme un message (Outlook sur le Web).
- Teams : visite d’un canal d’équipes.

> [!IMPORTANT]
> Lorsque vous modifiez la stratégie d’expiration, le service recalcule la date d’expiration pour chaque groupe. Il commence toujours à compter à partir de la date de création du groupe, puis applique la nouvelle stratégie d’expiration.

Il est important de comprendre que l’expiration est désactivée par défaut. Les administrateurs doivent l’activer pour leur organisation s’ils souhaitent l’utiliser.

> [!NOTE]
> La configuration et l’utilisation de la stratégie d’expiration pour les groupes Microsoft 365 nécessitent de posséder, mais pas nécessairement, des licences Azure AD Premium pour les membres de tous les groupes auxquels la stratégie d’expiration est appliquée. Pour plus d’informations, consultez la rubrique [prise en main d’Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Qui peut configurer et utiliser la stratégie d’expiration des groupes Microsoft 365 ?

|Role|Ce qu’ils peuvent faire|
|---------|---------|
|Administrateur général Office 365 (dans Azure, administrateur d’entreprise), administrateur d’utilisateurs|Créez, lisez, mettez à jour ou supprimez les paramètres de stratégie d’expiration des groupes Microsoft 365.|
|Utilisateur|Renouveler ou [restaurer](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-restore-deleted) un groupe Microsoft 365 dont il est propriétaire|

## <a name="how-to-set-the-expiration-policy"></a>Procédure de définition de la stratégie d’expiration

Comme indiqué ci-dessus, l’expiration est désactivée par défaut. Un administrateur doit activer la stratégie d’expiration et définir les propriétés pour qu’elle prenne effet. Pour l’activer, accédez à l’expiration des groupes **Azure Active Directory**  >  **Groups**  >  **Expiration**. Ici, vous pouvez définir la durée de vie du groupe par défaut et spécifier le délai d’expiration de la première et de la deuxième notifications d’expiration pour le propriétaire du groupe.

La durée de vie du groupe est spécifiée en jours et peut être définie sur 180, 365 ou sur une valeur personnalisée que vous spécifiez. La valeur personnalisée doit être d’au moins 30 jours.

Si le groupe n’a pas de propriétaire, les e-mails d’expiration sont envoyés à l’administrateur spécifié.

Vous pouvez définir la stratégie pour tous vos groupes, uniquement les groupes sélectionnés ou la désactiver complètement en sélectionnant **aucun**. Notez que vous ne pouvez pas utiliser actuellement des stratégies différentes pour différents groupes.

![Capture d’écran des paramètres d’expiration des groupes dans Azure Active Directory](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Fonctionnement de l’expiration avec la stratégie de rétention

Si vous avez configuré une stratégie de rétention pour les groupes dans le centre de sécurité et de conformité, la stratégie d’expiration fonctionne de manière transparente avec la stratégie de rétention. Lorsqu’un groupe expire, les conversations et les fichiers de boîte aux lettres du groupe sont conservés dans le conteneur de rétention pendant le nombre de jours défini dans la stratégie de rétention. Les utilisateurs ne verront pas le groupe, ni son contenu, après expiration.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Comment et quand un propriétaire de groupe apprend si ses groupes vont expirer

Les propriétaires de groupe seront uniquement avertis par courrier électronique. Si le groupe a été créé via Planner, SharePoint ou toute autre application, les notifications d’expiration seront toujours envoyées par courrier électronique. Si le groupe a été créé par le biais de teams, le propriétaire du groupe reçoit une notification pour le renouveler dans la section activité. Il n’est pas recommandé d’activer l’expiration sur un groupe si le propriétaire de votre groupe ne dispose pas d’une adresse de messagerie valide.

Trente jours avant l’expiration du groupe, les propriétaires du groupe (ou les adresses de messagerie que vous avez spécifiées pour les groupes qui n’ont pas de propriétaire) recevront un message électronique leur permettant de renouveler facilement le groupe. S’ils ne le rerenouvellent pas, ils recevront un autre courrier électronique de renouvellement 15 jours avant l’expiration. S’il ne l’a toujours pas renouvelé, il reçoit une notification par courrier électronique le jour précédant l’expiration.

Si, pour une raison quelconque, aucun des propriétaires ou administrateurs ne renouvelle le groupe avant qu’il n’expire, l’administrateur peut toujours restaurer le groupe pendant 30 jours après la date d’expiration. Pour plus d’informations, consultez la rubrique suivante : [Restore a Deleted Microsoft 365 Group](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Contenu du groupe d’archivage

Si vous avez un groupe que vous n’avez plus l’intention d’utiliser, mais que vous souhaitez conserver son contenu, voir [Archive Groups, teams et Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour plus d’informations sur l’exportation des informations à partir des différents groupes services.

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble des stratégies de rétention](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Attribuer un nouveau propriétaire à un groupe orphelin](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Configurer l’expiration des groupes Microsoft 365](https://docs.microsoft.com/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
