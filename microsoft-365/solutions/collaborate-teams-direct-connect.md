---
title: Collaborer avec des participants externes dans un canal partagé
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- highpri
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom: ''
localization_priority: Priority
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment activer les canaux partagés dans Microsoft Teams pour la collaboration avec des personnes extérieures à votre organisation.
ms.openlocfilehash: 6f188f82e6f1c17cfc963449872e1c88a1c205ac
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730680"
---
# <a name="collaborate-with-external-participants-in-a-shared-channel"></a>Collaborer avec des participants externes dans un canal partagé

Si vous souhaitez permettre à vos utilisateurs de collaborer avec des personnes d’autres organisations Microsoft 365 dans des [canaux partagés](/MicrosoftTeams/shared-channels), vous devez configurer la connexion directe B2B pour chaque organisation avec laquelle vous souhaitez collaborer. (Vous pouvez également [Activer les canaux partagés avec toutes les organisations externes](/microsoft-365/solutions/allow-direct-connect-with-all-organizations).)

Lorsque vous activez des canaux partagés avec une autre organisation :

- Les propriétaires d’équipe de votre organisation pourront inviter des personnes d’autres organisations à participer à des canaux partagés.
- Les applications personnalisées (métier) de votre organisation seront disponibles dans les canaux partagés et les participants externes pourront y accéder.
- La liste des applications de votre organisation sera disponible dans les canaux partagés et les participants externes pourront y accéder.

> [!NOTE]
> [Les paramètres invités pour Groupes Microsoft 365](/microsoft-365/admin/create-groups/manage-guest-access-in-groups) doivent être activés pour utiliser des canaux partagés avec des participants externes.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo décrit les étapes de configuration décrites dans ce document.
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4WRMx?autoplay=false]

## <a name="enable-shared-channels-in-teams"></a>Activer les canaux partagés dans Teams

Les canaux partagés sont activés par défaut dans Teams. Suivez cette procédure pour confirmer les paramètres.

Pour configurer des canaux partagés
1. Dans le [centre d’administration Teams](https://admin.teams.microsoft.com/), développez **Teams**, puis sélectionnez **Stratégies Teams**.
1. Sélectionnez la stratégie pour laquelle vous souhaitez activer les canaux partagés, puis sélectionnez **Modifier**.
1. Sélectionnez les options que vous souhaitez activer :
    - Pour permettre aux propriétaires d’équipe de créer des canaux partagés, activez **Créer des canaux partagés** .
    - Pour permettre aux propriétaires d’équipe de partager des canaux partagés avec des personnes extérieures à l’organisation, activez **Partager des canaux partagés en externe**.
    - Pour permettre aux utilisateurs d’être invités à des canaux partagés dans d’autres organisations, activez **Peut être invité à des canaux partagés externes** .
1. Sélectionnez **Appliquer**.

Pour que les participants du canal externe puissent participer aux réunions, l’accès externe doit être activé. Cela est également nécessaire pour pouvoir voir la présence des participants externes dans le canal.

Pour activer l’accès externe
1. Dans le [centre d’administration Teams](https://admin.teams.microsoft.com/), développez **Utilisateurs**, puis sélectionnez **d’accès externe**.
1. Sous **les utilisateurs teams et Skype Entreprise des organisations externes**, assurez-vous que les organisations avec lesquelles vous souhaitez collaborer ne sont pas bloquées.

## <a name="configure-cross-tenant-access-settings-in-azure-ad"></a>Configurer les paramètres d’accès entre locataires dans Azure AD

Azure AD connexion directe B2B est désactivée par défaut. Pour permettre la collaboration dans les canaux partagés avec des personnes d’autres organisations, vous devez :

1. [Ajouter une organisation](#add-an-organization).
1. [Configurer les paramètres entrants](#configure-inbound-settings) pour que l’organisation autorise les utilisateurs de l’organisation à être invités à vos canaux partagés.
1. [Configurer les paramètres sortants](#configure-outbound-settings) pour que l’organisation autorise vos utilisateurs à être invités aux canaux partagés de l’autre organisation.

Dans le cadre de cette configuration, nous activons l’application **Office 365**, qui inclut Teams et les services intégrés à Teams tels que SharePoint.

> [!NOTE]
> Les modifications apportées aux paramètres d’accès entre tenants (clients/locataires) peuvent prendre jusqu'à six heures pour prendre effet.

> [!NOTE]
> Les canaux partagés entre les clouds commerciaux et les cloud de la communauté du secteur public ne sont pas pris en charge.

### <a name="add-an-organization"></a>Ajouter une organisation

Ajoutez chaque organisation avec laquelle vous souhaitez participer à des canaux partagés.

Pour ajouter une organisation
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identities externes**, puis sélectionnez **Paramètres d’accès inter-clients**.
1. Sélectionnez **Paramètres de l’organisation**.
1. Sélectionnez **Ajouter une organisation**.
1. Dans le volet **Ajouter une organisation**, tapez le nom de domaine complet (ou l’ID de locataire) de l’organisation, puis appuyez sur Entrée.
1. Sélectionnez **Ajouter**.
1. À ce stade, tous les paramètres d’accès de cette organisation sont hérités de vos paramètres par défaut.

### <a name="configure-inbound-settings"></a>Configurer les paramètres entrants

Suivez cette procédure pour chaque organisation dans laquelle vous souhaitez inviter des participants externes.

Pour configurer les paramètres entrants d’une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités Externes**, puis **Paramètres d’accès inter-clients**.
1. Sélectionnez le lien d’accès entrant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Connexion directe B2B**, choisissez **Personnaliser les paramètres**.
1. Sous l’onglet **Utilisateurs et groupes externes** , choisissez **Autoriser l’accès** et **Tous les utilisateurs et groupes**. (Vous pouvez choisir **Sélectionner des utilisateurs et des groupes externes** si vous souhaitez limiter l’accès à des utilisateurs et groupes spécifiques, tels que ceux qui ont signé un accord de confidentialité.)
1. Sous l’onglet **Applications**, sélectionnez **Autoriser l’accès** et **Sélectionner des applications**.
1. Sélectionnez **Ajouter des applications Microsoft**.
1. Sélectionnez l’application **Office 365**, puis choisissez **Sélectionner**.
1. Sélectionnez **Enregistrer** et fermez le panneau **Paramètres d’accès entrant** .

### <a name="configure-outbound-settings"></a>Configurer les paramètres de trafic sortant

Suivez cette procédure pour chaque organisation dans laquelle vous souhaitez que vos utilisateurs puissent participer à des canaux partagés externes.

Pour configurer les paramètres sortants d’une organisation
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités Externes**, puis **Paramètres d’accès inter-clients**.
1. Sélectionnez le lien d’accès sortant pour l’organisation que vous souhaitez modifier.
1. Sous l’onglet **Connexion directe B2B**, choisissez **Personnaliser les paramètres**.
1. Sous l’onglet **Utilisateurs et groupes externes**, choisissez **Autoriser l’accès** et définissez **S’applique à** pour tous les utilisateurs.
1. Sous l’onglet **Applications externes**, choisissez **Autoriser l’accès** et **Sélectionner les applications externes**.
1. Sélectionnez **Ajouter des applications Microsoft**.
1. Sélectionnez l’application **Office 365**, puis choisissez **Sélectionner**.
1. Sélectionnez **Enregistrer**, choisissez **Oui** pour confirmer, puis fermez le panneau **Paramètres d’accès sortant**.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Limiter les personnes pouvant être invitées par une organisation](limit-invitations-from-specific-organization.md)

[Limites des canaux partagés](/MicrosoftTeams/shared-channels#shared-channel-limits)
