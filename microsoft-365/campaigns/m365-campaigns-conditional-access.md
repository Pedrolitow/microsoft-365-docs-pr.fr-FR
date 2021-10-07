---
title: Activer les paramètres de sécurité par défaut
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
description: Découvrez comment les paramètres de sécurité par défaut peuvent aider à protéger votre organisation contre les attaques liées aux identités en fournissant des paramètres de sécurité préconfigurés.
ms.openlocfilehash: 49b20e4880774ce97d99dc95e60c0cb417b213bc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198977"
---
# <a name="turn-on-security-defaults"></a>Activer les paramètres de sécurité par défaut

Les paramètres de sécurité par défaut contribuent à protéger votre organisation contre les attaques liées aux identités en fournissant des paramètres de sécurité préconfigurés que Microsoft gère au nom de votre organisation. Ces paramètres incluent l’activation de l’authentification multifacteur (MFA) pour tous les administrateurs et comptes d’utilisateurs. Pour la plupart des organisations, les paramètres de sécurité par défaut offrent un bon niveau de sécurité de la signature supplémentaire.

Pour plus d’informations sur les paramètres de sécurité par défaut et les stratégies qu’ils appliquent, voir [Quelles sont les valeurs par défaut de sécurité ?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Si votre abonnement a été créé le ou après le 22 octobre 2019, les paramètres de sécurité par défaut ont peut-être été automatiquement activés pour vous, vous devez vérifier vos paramètres pour &mdash; vérifier.

Pour activer les paramètres de sécurité par défaut dans votre Azure Active Directory (Azure AD) ou pour vérifier s’ils sont déjà activés :

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> avec les informations d’identification d’administrateur global.

2. Dans le volet gauche, sélectionnez **Afficher tout,** puis sous Centres d’administration,  **sélectionnez Azure Active Directory**.

3. Dans le volet gauche du Centre **d’administration Azure Active Directory,** sélectionnez **Azure Active Directory**.

4. Dans le menu gauche du tableau de bord, dans la section **Gérer,** sélectionnez **Propriétés.**

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Capture d’écran Azure Active Directory centre d’administration montrant l’emplacement de l’élément de menu Propriétés.":::

5. En bas de la page **Propriétés,** **sélectionnez Gérer les paramètres de sécurité par défaut.**

6. Dans le volet droit, vous verrez le paramètre **Activer les paramètres de sécurité par défaut.** Si **Oui** est sélectionné, les paramètres de sécurité par défaut sont déjà activés et aucune action supplémentaire n’est requise. Si les paramètres de sécurité par défaut ne sont pas activés actuellement, sélectionnez **Oui** pour les activer, puis sélectionnez **Enregistrer.**

> [!NOTE]
> Si vous utilisez des stratégies d’accès conditionnel, vous devez les désactiver avant d’utiliser les paramètres de sécurité par défaut.
>
> Vous pouvez utiliser les paramètres de sécurité par défaut ou les stratégies d’accès conditionnel, mais vous ne pouvez pas utiliser les deux en même temps.

## <a name="consider-using-conditional-access"></a>Envisager d’utiliser l’accès conditionnel

Si votre organisation a des exigences de sécurité complexes ou si vous avez besoin d’un contrôle plus granulaire sur vos stratégies de sécurité, vous devez envisager d’utiliser l’accès conditionnel au lieu des paramètres de sécurité par défaut pour obtenir une posture de sécurité similaire ou supérieure. 

L’accès conditionnel vous permet de créer et de définir des stratégies qui réagissent aux événements de connectez-vous et de demander des actions supplémentaires avant qu’un utilisateur ne soit autorisé à accéder à une application ou un service. Les stratégies d’accès conditionnel peuvent être granulaires et spécifiques, permettant aux utilisateurs d’être productifs où et quand, mais aussi de protéger votre organisation.

Les valeurs par défaut de sécurité sont disponibles pour tous les clients, tandis que l’accès conditionnel nécessite une licence pour l’un des plans suivants :

- Azure Active Directory Premium P1 ou P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 ou E5
- Enterprise Mobility & Security E3 ou E5

Si vous souhaitez utiliser l’accès conditionnel pour configurer des stratégies équivalentes à celles activées par défaut de sécurité, consultez les guides pas à pas suivants :

- [Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Exiger l’mf pour la gestion Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Exiger l’inscription Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) : nécessite Azure AD Identity Protection, qui fait partie de Azure Active Directory Premium P2

Pour en savoir plus sur l’accès conditionnel, voir [qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview) Pour plus d’informations sur la création de stratégies d’accès conditionnel, voir [Créer une stratégie d’accès conditionnel.](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy)

> [!NOTE]
> Si vous disposez d’un plan ou d’une licence qui fournit l’accès conditionnel, mais que vous n’avez pas encore créé de stratégies d’accès conditionnel, vous pouvez utiliser les paramètres de sécurité par défaut. Toutefois, vous devez désactiver les paramètres de sécurité par défaut avant de pouvoir utiliser des stratégies d’accès conditionnel.
