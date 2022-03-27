---
title: Activer les canaux partagés avec toutes les organisations externes
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
description: Découvrez comment activer les canaux partagés avec tous les autres Microsoft 365 et Azure Active Directory organisations.
ms.openlocfilehash: 601bfaa825afdaf9ec5addb4b7c7e21804b07cb7
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716003"
---
# <a name="enable-shared-channels-with-all-external-organizations"></a>Activer les canaux partagés avec toutes les organisations externes

Bien que le partage de canaux partagés en externe soit activé par défaut dans Teams, les paramètres d’accès entre locataires Azure Active Directory pour la connexion [directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview) doivent également être configurés pour partager un canal en externe. Par défaut, ces paramètres sont définies pour bloquer toutes les organisations.

Vous pouvez modifier les paramètres par défaut de connexion directe B2B pour autoriser toutes les organisations. Cela permet aux utilisateurs de collaborer dans des canaux partagés sans que votre organisation n’a à créer une configuration distincte pour chaque organisation avec qui vous souhaitez collaborer. (Notez que les organisations avec qui vous collaborez devront également configurer leurs paramètres de connexion directe B2B.)

Si votre organisation n’a pas besoin de restreindre la collaboration avec d’autres organisations, l’activation de toutes les organisations par défaut peut vous faire gagner du temps et de la complexité dans la gestion de chaque organisation séparément.

> [!NOTE]
> L’application des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

## <a name="allow-users-to-invite-people-in-other-organizations-to-participate-in-shared-channels"></a>Autoriser les utilisateurs à inviter des personnes d’autres organisations à participer à des canaux partagés

Vous pouvez autoriser vos utilisateurs à inviter des personnes d’autres organisations à utiliser des ressources partagées, telles que des canaux partagés dans Teams, par défaut.

Pour permettre aux utilisateurs d’inviter des participants À la connexion directe B2B par défaut
1. Connectez-vous [à Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte d’administrateur général ou d’administrateur de sécurité.
1. **Sélectionnez Identités externes**, puis sélectionnez **Paramètres d’accès entre locataires (prévisualisation).**
1. Sous **l’onglet Paramètres par défaut** , sous **Paramètres** d’accès entrant, **sélectionnez Modifier les valeurs par défaut entrantes**.
1. Sélectionnez **l’onglet Connexion directe B2B** .
1. Sous **l’onglet Utilisateurs et groupes** , sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **l’onglet Applications externes** , sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sélectionnez **Enregistrer**.
1. Sélectionnez **l’onglet Paramètres d’confiance** .
1. Choisissez si vous souhaitez faire confiance à l’authentification multifacteur, aux appareils conformes ou aux appareils Azure AD joints à des appareils d’autres organisations.
1. Sélectionnez **Enregistrer**.
1. Fermez le **lame Paramètres par** défaut.

## <a name="allow-users-to-participate-in-shared-channels-in-other-organizations"></a>Autoriser les utilisateurs à participer à des canaux partagés dans d’autres organisations

Vous pouvez autoriser vos utilisateurs à accéder aux ressources hébergées par une organisation externe, telles que les canaux partagés dans Teams, par défaut.

Pour autoriser les utilisateurs à accéder aux ressources d’autres organisations par défaut
1. Dans [Azure Active Directory](https://aad.portal.azure.com), sélectionnez **Identités externes**, puis sélectionnez Paramètres d’accès entre **locataires (prévisualisation).**
1. Sous **l’onglet Paramètres par défaut** , sous **Paramètres** d’accès sortant, **sélectionnez Modifier les paramètres par défaut du trafic sortant**.
1. Sélectionnez **l’onglet Connexion directe B2B** .
1. Sous **l’onglet Utilisateurs et groupes** , sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sous **l’onglet Applications externes** , sous **État d’accès**, **sélectionnez Autoriser l’accès**.
1. Sélectionnez **Enregistrer**.
1. Fermez le **lame Paramètres par** défaut.

## <a name="related-topics"></a>Sujets associés

[Vue d’ensemble de la connexion directe B2B](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Configurer les paramètres d’accès entre locataires pour la connexion directe B2B](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

