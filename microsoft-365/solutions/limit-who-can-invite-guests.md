---
title: Limiter les personnes autorisées à inviter des invités
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- highpri
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment limiter les personnes pouvant inviter des invités dans votre organisation.
ms.openlocfilehash: 2eb6295a64afb867c1ee0ed6ea735d3382a1e23e
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986683"
---
# <a name="limit-who-can-invite-guests"></a>Limiter les personnes autorisées à inviter des invités

Vous pouvez limiter les personnes de votre organisation qui peuvent inviter des invités. Les comptes invités peuvent être utilisés pour partager des équipes, des sites SharePoint, des fichiers et des dossiers avec des personnes extérieures à votre organisation.

Si vos processus métier nécessitent que vous limitiez les personnes autorisées à partager avec des invités, ou si vous souhaitez que les utilisateurs terminent la formation avant de pouvoir partager avec des invités, vous pouvez limiter les personnes qui peuvent partager à l’aide du rôle d’inviteur d’invités dans Azure Active Directory.

## <a name="create-a-security-group-for-people-allowed-to-invite-guests"></a>Créer un groupe de sécurité pour les personnes autorisées à inviter des invités

La première étape consiste à créer un groupe de sécurité pour les utilisateurs qui seront autorisés à inviter des invités. Veillez à configurer ce groupe pour autoriser un rôle Azure AD, puis à lui attribuer le rôle d’inviteur d’invités.

Pour créer un groupe de sécurité pour les inviteurs invités
1. Connectez-vous à [Azure Active Directory](https://aad.portal.azure.com) à l’aide d’un compte Administrateur général ou Administrateur de la sécurité.
1. Dans la page **Active Directory** , sélectionnez **Groupes** , puis **Nouveau groupe**.
1. Choisissez **Sécurité** pour le **type de groupe**.
1. Tapez un **nom de groupe.** 
1. Si vous le souhaitez, ajoutez une description pour le groupe.
1. Pour que les **rôles Azure AD puissent être attribués au groupe**, choisissez **Oui**.
1. Ajoutez des propriétaires et des membres de groupe.
1. Sous **Rôles**, sélectionnez **Aucun rôle sélectionné**.
1. Recherchez et sélectionnez le rôle **d’inviteur d’invités** , puis **sélectionnez Sélectionner**.
1. Sélectionnez **Créer** et confirmez que vous souhaitez un groupe auquel les rôles peuvent être attribués. Votre groupe est créé et prêt pour vous permettre d’ajouter des membres.

## <a name="configure-external-collaboration-settings"></a>Configurer les paramètres de collaboration externe

Une fois que vous avez créé le groupe de sécurité et ajouté les utilisateurs que vous souhaitez pouvoir inviter des invités, l’étape suivante consiste à configurer les paramètres de collaboration externe Azure AD pour autoriser uniquement les utilisateurs disposant du rôle Inviteur d’invités à inviter des invités.

Notez que les administrateurs généraux peuvent toujours inviter des invités, quel que soit ce paramètre.

> [!NOTE]
> La prise en compte des modifications apportées aux paramètres d’accès entre locataires peut prendre deux heures.

Pour configurer Azure AD afin de limiter les invitations d’invités au rôle d’inviteur d’invités
1. Dans [Azure Active Directory](https://aad.portal.azure.com/), sélectionnez **Identités externes**.
1. Sélectionnez **paramètres de collaboration externe**.
1. Sous **Paramètres d’invitation** invité, choisissez **Seuls les utilisateurs affectés à des rôles d’administrateur spécifiques peuvent inviter des invités**.
1. Sélectionnez **Enregistrer**.

## <a name="related-topics"></a>Voir aussi

[Autoriser uniquement les utilisateurs de groupes de sécurité spécifiques à partager en externe dans SharePoint et OneDrive](/sharepoint/manage-security-groups)

[Activer la collaboration externe B2B, puis gérer les utilisateurs pouvant avoir des invités](/azure/active-directory/external-identities/delegate-invitations)