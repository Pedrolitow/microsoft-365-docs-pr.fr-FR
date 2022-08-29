---
title: Stratégie d’expiration de groupe Microsoft 365
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
description: Découvrez les stratégies d’expiration des groupes Microsoft 365.
ms.openlocfilehash: d91f3f09ccc1ffd562d87f5018953a6cd4fc8574
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67388394"
---
# <a name="microsoft-365-group-expiration-policy"></a>Stratégie d’expiration de groupe Microsoft 365

Avec l’augmentation de l’utilisation des groupes Microsoft 365 et des équipes Microsoft, les administrateurs et les utilisateurs ont besoin d’un moyen de nettoyer les groupes et les équipes inutilisés. Une stratégie d’expiration des groupes Microsoft 365 peut aider à supprimer les groupes inactifs du système et à rendre les choses plus propres.

Lorsqu’un groupe expire, [presque tous ses services associés (boîte aux lettres, Planificateur, site SharePoint, équipe, etc.) sont également supprimés](/microsoft-365/solutions/end-life-cycle-groups-teams-sites-yammer).

Lorsqu’un groupe expire, il est « supprimé de manière réversible », ce qui signifie qu’il peut toujours être récupéré jusqu’à 30 jours.

Les administrateurs peuvent spécifier une période d’expiration et tout groupe inactif qui atteint la fin de cette période, et qui n’est pas renouvelé, sera supprimé. (Cela inclut les équipes archivées.) La période d’expiration commence lorsque le groupe est créé ou à la date de son dernier renouvellement. Les propriétaires de groupe recevront automatiquement une notification avant l’expiration qui leur permet de renouveler le groupe pour un autre intervalle d’expiration. Les avis d’expiration pour les groupes utilisés dans Teams apparaissent dans le flux Propriétaires teams.

Les groupes activement utilisés sont renouvelés automatiquement. N’importe laquelle des actions suivantes renouvellera automatiquement un groupe :
- SharePoint - Afficher, modifier, télécharger, déplacer, partager ou charger des fichiers. (L’affichage d’une page SharePoint ne compte pas comme une action pour le renouvellement automatique.)
- Outlook - Joindre ou modifier un groupe, lire ou écrire un message de groupe à partir du groupe, et comme un message (Outlook sur le web).
- Teams - Visitez un canal Teams.
- Yammer : afficher un billet dans une communauté Yammer ou un e-mail interactif dans Outlook.
- Formulaires : afficher, créer ou modifier des formulaires, ou envoyer une réponse à un formulaire. 

> [!IMPORTANT]
> Lorsque vous modifiez la stratégie d’expiration, le service recalcule la date d’expiration de chaque groupe. Il commence toujours à compter de la date de création du groupe, puis applique la nouvelle stratégie d’expiration.

Il est important de savoir que l’expiration est désactivée par défaut. Les administrateurs doivent l’activer pour leur organisation s’ils souhaitent l’utiliser.

> [!NOTE]
> La configuration et l’utilisation de la stratégie d’expiration pour les groupes Microsoft 365 vous obligent à posséder, mais pas nécessairement à attribuer des licences Azure AD Premium pour les membres de tous les groupes auxquels la stratégie d’expiration est appliquée. Pour plus d’informations, consultez [Prise en main de Azure Active Directory Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Qui peut configurer et utiliser la stratégie d’expiration des groupes Microsoft 365 ?

|Rôle|Ce qu’elles peuvent en faire|
|---------|---------|
|Office 365 administrateur général (dans Azure, l’administrateur de la société), administrateur d’utilisateurs|Créez, lisez, mettez à jour ou supprimez les paramètres de stratégie d’expiration des groupes Microsoft 365.|
|Utilisateur|Renouveler ou [restaurer](/azure/active-directory/users-groups-roles/groups-restore-deleted) un groupe Microsoft 365 dont il est propriétaire|

## <a name="how-to-set-the-expiration-policy"></a>Comment définir la stratégie d’expiration

Comme indiqué ci-dessus, l’expiration est désactivée par défaut. Un administrateur doit activer la stratégie d’expiration et définir les propriétés pour qu’elle prenne effet. Pour l’activer, accédez à **l’expiration** **des groupes** >  **Azure Active Directory** > . Ici, vous pouvez définir la durée de vie du groupe par défaut.

La durée de vie du groupe est spécifiée en jours et peut être définie sur 180, 365 ou sur une valeur personnalisée que vous spécifiez. La valeur personnalisée doit être d’au moins 30 jours.

Si le groupe n’a pas de propriétaire, les e-mails d’expiration sont envoyés à l’e-mail spécifié.

Vous pouvez définir la stratégie pour tous vos groupes, uniquement les groupes sélectionnés (jusqu’à 500) ou la désactiver complètement en sélectionnant **Aucun**. Lorsque vous sélectionnez **Aucun** , tous les groupes actifs et en attente de vérification n’ont aucune date d’expiration. Toutefois, les groupes qui sont déjà arrivés à expiration ne sont pas affectés.

Notez qu’actuellement, vous ne pouvez pas avoir de stratégies différentes pour différents groupes.

![Capture d’écran des paramètres d’expiration des groupes dans Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Fonctionnement de l’expiration avec la stratégie de rétention

Si vous avez configuré une stratégie de rétention pour les groupes dans le portail de conformité Microsoft Purview, la stratégie d’expiration fonctionne en toute transparence avec la stratégie de rétention. Lorsqu’un groupe expire, les conversations de boîte aux lettres du groupe et les fichiers du site de groupe sont conservés dans le conteneur de rétention pendant le nombre de jours spécifique défini dans la stratégie de rétention. Cependant, les utilisateurs ne verront pas le groupe ou son contenu après l’expiration.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Comment et quand un propriétaire de groupe apprend si ses groupes vont expirer

Si le groupe a été créé via Planner, SharePoint ou toute autre application, les notifications d’expiration seront toujours envoyées par e-mail.
Si le groupe a été créé via Teams, le propriétaire du groupe reçoit un e-mail et une notification de renouvellement via la section d’activité. Il n’est pas recommandé d’activer l’expiration sur un groupe si le propriétaire de votre groupe n’a pas d’adresse e-mail valide.

30 jours avant l’expiration du groupe, les propriétaires du groupe (ou les adresses e-mail que vous avez spécifiées pour les groupes qui n’ont pas de propriétaire) recevront un e-mail leur permettant de renouveler facilement le groupe. S’il ne le renouvelle pas, il reçoit un autre e-mail de renouvellement 15 jours avant l’expiration. S’ils ne l’ont toujours pas renouvelé, ils recevront une autre notification par e-mail la veille de l’expiration.

Si, pour une raison quelconque, aucun des propriétaires ou administrateurs ne renouvelle le groupe avant son expiration, l’administrateur peut toujours restaurer le groupe jusqu’à 30 jours après l’expiration. Pour plus d’informations, consultez : [Restaurer un groupe Microsoft 365 supprimé](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Archivage du contenu du groupe

Si vous avez un groupe que vous n’envisagez plus d’utiliser, mais que vous souhaitez conserver son contenu, consultez [Les groupes d’archives, les équipes et Yammer](end-life-cycle-groups-teams-sites-yammer.md) pour plus d’informations sur la façon d’exporter des informations à partir des différents services de groupes.

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Vue d’ensemble des stratégies de rétention](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Attribuer un nouveau propriétaire à un groupe orphelin](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Configurer l’expiration des groupes Microsoft 365](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
