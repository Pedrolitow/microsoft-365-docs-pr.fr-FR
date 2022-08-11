---
title: Activer des canaux partagés avec toutes les organisations externes
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment activer les canaux partagés avec toutes les autres organisations Microsoft 365 et Azure Active Directory.
ms.openlocfilehash: 41acba8e6097946d80d970a3220a61486c39def2
ms.sourcegitcommit: 34910ea9318289d78c35b0e7990238467c05384b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2022
ms.locfileid: "67306501"
---
# <a name="enable-shared-channels-with-all-external-organizations"></a>Activer des canaux partagés avec toutes les organisations externes

Bien que le partage de canaux partagés en externe soit activé par défaut dans Teams, les paramètres d’accès multilocataire Azure Active Directory pour [B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview) doivent également être configurés pour partager un canal en externe. Par défaut, ces paramètres sont définis pour bloquer toutes les organisations.

Vous pouvez modifier les paramètres par défaut de connexion directe B2B pour autoriser toutes les organisations. Cela permet aux utilisateurs de collaborer dans des canaux partagés sans que votre organisation ait à créer une configuration distincte pour chaque organisation avec laquelle vous souhaitez collaborer. (Notez que les organisations avec lesquelles vous collaborez devront également configurer leurs paramètres de connexion directe B2B.)

Si votre organisation n’a pas besoin de restreindre la collaboration avec d’autres organisations, l’activation de toutes les organisations par défaut peut vous faire gagner du temps et de la complexité dans la gestion de chaque organisation séparément.

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

> [!NOTE]
> [Les paramètres invités pour Groupes Microsoft 365](/microsoft-365/admin/create-groups/manage-guest-access-in-groups) doivent être activés pour utiliser des canaux partagés avec des participants externes.

## <a name="allow-users-to-invite-people-in-other-organizations-to-participate-in-shared-channels"></a>Autoriser les utilisateurs à inviter des personnes d’autres organisations à participer à des canaux partagés

Par défaut, vous pouvez autoriser vos utilisateurs à inviter des personnes d’autres organisations à utiliser des ressources partagées, telles que des canaux partagés dans Teams.

Pour permettre aux utilisateurs d’inviter des participants B2B Direct Connect par défaut
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sous l’onglet **Paramètres par défaut** , sous **Paramètres d’accès entrant**, **sélectionnez Modifier les valeurs par défaut entrantes**.
1. Sélectionnez l’onglet **Connexion directe B2B** .
1. Sous l’onglet **Utilisateurs et groupes** , sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous l’onglet **Applications externes** , sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sélectionnez **Enregistrer**.
1. Sélectionnez l’onglet **Paramètres d’approbation** .
1. Choisissez si vous souhaitez approuver l’authentification multifacteur, les appareils conformes ou les appareils joints à Azure AD hybrides d’autres organisations.
1. Sélectionnez **Enregistrer**.
1. Fermez le panneau **Paramètres par défaut** .

## <a name="allow-users-to-participate-in-shared-channels-in-other-organizations"></a>Autoriser les utilisateurs à participer à des canaux partagés dans d’autres organisations

Par défaut, vous pouvez autoriser vos utilisateurs à accéder aux ressources hébergées par une organisation externe, telles que les canaux partagés dans Teams.

Pour permettre aux utilisateurs d’accéder aux ressources d’autres organisations par défaut
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (préversion)**.
1. Sous l’onglet **Paramètres par défaut** , sous **Paramètres d’accès sortant**, **sélectionnez Modifier les paramètres sortants par défaut**.
1. Sélectionnez l’onglet **Connexion directe B2B** .
1. Sous l’onglet **Utilisateurs et groupes** , sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sous l’onglet **Applications externes** , sous **État d’Accès**, choisissez **Autoriser l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le panneau **Paramètres par défaut** .

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

