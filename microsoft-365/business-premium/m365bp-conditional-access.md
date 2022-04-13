---
title: Activer les paramètres de sécurité par défaut pour Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment les paramètres de sécurité par défaut peuvent aider à protéger votre organisation contre les attaques liées aux identités en fournissant des paramètres de sécurité préconfigurés pour Microsoft 365 Business Premium.
ms.openlocfilehash: 58477da3d44844c763dff95d35fc71753afc7ce2
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824507"
---
# <a name="turn-on-security-defaults-for-microsoft-365-business-premium"></a>Activer les paramètres de sécurité par défaut pour Microsoft 365 Business Premium

Les paramètres de sécurité par défaut aident à protéger votre organisation contre les attaques liées aux identités en fournissant des paramètres de sécurité préconfigurés que Microsoft gère pour le compte de votre organisation. Ces paramètres incluent l’activation de l’authentification multifacteur (MFA) pour tous les administrateurs et comptes d’utilisateurs. Pour la plupart des organisations, les paramètres de sécurité par défaut offrent un bon niveau de sécurité de connexion supplémentaire.

Pour plus d’informations sur les paramètres de sécurité par défaut et les stratégies qu’ils appliquent, consultez [Que sont les valeurs par défaut de sécurité ?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement a été créé le 22 octobre 2019 ou après, les paramètres de sécurité par défaut ont peut-être été automatiquement activés.&mdash; Vous devez vérifier vos paramètres pour confirmer.

Pour activer les paramètres de sécurité par défaut dans votre Azure Active Directory (Azure AD) ou pour vérifier s’ils sont déjà activés :

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> avec les informations d’identification de l’administrateur de sécurité, de l’administrateur de l’accès conditionnel ou de l’administrateur général.

2. Dans le volet gauche, sélectionnez **Afficher tout, puis sous** **Centres d’administration**, sélectionnez **Azure Active Directory**.

3. Dans le volet gauche du **centre d’administration Azure Active Directory,** sélectionnez **Azure Active Directory**.

4. Dans le menu de gauche du tableau de bord, dans la section **Gérer** , sélectionnez **Propriétés**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Capture d’écran du centre d’administration Azure Active Directory montrant l’emplacement de l’élément de menu Propriétés.":::

5. En bas de la page **Propriétés** , **sélectionnez Gérer les paramètres de sécurité par défaut**.

6. Dans le volet droit, vous **verrez le paramètre Activer la sécurité par défaut** . Si **Oui** est sélectionné, les paramètres de sécurité par défaut sont déjà activés et aucune autre action n’est requise. Si les paramètres de sécurité par défaut ne sont pas activés, sélectionnez **Oui** pour les activer, puis **sélectionnez Enregistrer**.

> [!NOTE]
> Si vous avez utilisé des stratégies d’accès conditionnel, vous devez les désactiver avant d’utiliser les paramètres de sécurité par défaut.
>
> Vous pouvez utiliser des stratégies de sécurité par défaut ou d’accès conditionnel, mais vous ne pouvez pas utiliser les deux en même temps.

## <a name="consider-using-conditional-access"></a>Envisagez d’utiliser l’accès conditionnel

Si votre organisation a des exigences de sécurité complexes ou si vous avez besoin d’un contrôle plus précis sur vos stratégies de sécurité, vous devez envisager d’utiliser l’accès conditionnel plutôt que les paramètres de sécurité par défaut pour obtenir une posture de sécurité similaire ou supérieure. 

L’accès conditionnel vous permet de créer et de définir des stratégies qui réagissent aux événements de connexion et de demander des actions supplémentaires avant qu’un utilisateur ne se voit accorder l’accès à une application ou un service. Les stratégies d’accès conditionnel peuvent être précises et précises, ce qui permet aux utilisateurs d’être productifs où et quand, mais aussi de protéger votre organisation.

Les paramètres de sécurité par défaut sont disponibles pour tous les clients, tandis que l’accès conditionnel nécessite une licence pour l’un des plans suivants :

- Azure Active Directory Premium P1 ou P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 ou E5
- Enterprise Mobility & Security E3 ou E5

Si vous souhaitez utiliser l’accès conditionnel pour configurer des stratégies équivalentes à celles activées par défaut de sécurité, consultez les guides pas à pas suivants :

- [Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)

- [Exiger l’authentification multifacteur pour la gestion Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)

- [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

- [Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)

- [Exiger Azure AD l’inscription MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - Nécessite Azure AD Identity Protection, qui fait partie de Azure Active Directory Premium P2

Pour en savoir plus sur l’accès conditionnel, consultez [Qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview) Pour plus d’informations sur la création de stratégies d’accès conditionnel, consultez [Créer une stratégie d’accès conditionnel](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Si vous disposez d’un plan ou d’une licence qui fournit l’accès conditionnel, mais que vous n’avez pas encore créé de stratégies d’accès conditionnel, vous pouvez utiliser les paramètres de sécurité par défaut. Toutefois, vous devez désactiver les paramètres de sécurité par défaut avant de pouvoir utiliser des stratégies d’accès conditionnel.
