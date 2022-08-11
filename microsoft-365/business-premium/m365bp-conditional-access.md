---
title: Accès conditionnel et de la sécurité par défaut
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 08/08/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment les paramètres de sécurité par défaut peuvent aider à protéger votre organisation contre les attaques liées à l’identité en fournissant des paramètres de sécurité préconfigurés pour Microsoft 365 Business Premium.
ms.openlocfilehash: 2d4dc4af9f003245b25a85c5b18abf593db8fbe8
ms.sourcegitcommit: 402e0b2095b6cb141b8525a53194d47357bcd612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2022
ms.locfileid: "67285184"
---
# <a name="security-defaults-and-multi-factor-authentication"></a>Authentification multifacteur et sécurité par défaut.

Microsoft 365 Business Premium a été conçu pour protéger les comptes d’utilisateur de votre entreprise avec des paramètres de sécurité préconfigurés. Ces paramètres incluent l’activation de l’authentification multifacteur (MFA) pour tous vos comptes administrateurs et utilisateur. Pour la plupart des organisations, les valeurs de sécurité par défaut offrent un niveau de sécurité de connexion supplémentaire.

> [!TIP]
> Pour plus d’informations sur les paramètres de sécurité par défaut et les stratégies appliquées, consultez [Que sont les paramètres de sécurité par défaut?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Cet article fournit des informations sur :

- **[Paramètres de sécurité par défaut](#security-defaults)** (adapté à la plupart des entreprises)
- **[Accès conditionnel](#conditional-access)** (pour les entreprises avec des exigences de sécurité plus strictes)

> [!NOTE]
> Si vous utilisez des stratégies d’accès conditionnel, vous devez les désactiver avant d’utiliser les paramètres de sécurité par défaut. Vous pouvez utiliser les paramètres de sécurité par défaut ou les stratégies d’accès conditionnel, mais vous ne pouvez pas utiliser les deux en même temps.

## <a name="security-defaults"></a>Paramètres de sécurité par défaut

Les paramètres de sécurité par défaut ont été conçus pour protéger les comptes d’utilisateur de votre entreprise dès le départ. Lorsqu’ils sont activés, les paramètres de sécurité par défaut fournissent des paramètres sécurisés par défaut qui vous aident à sécuriser votre entreprise en :

- Demander à tous les utilisateurs et administrateurs de s’inscrire à l’authentification multifacteur à l’aide de l’application Microsoft Authenticator.
- Difficultés pour les utilisateurs avec l’authentification multifacteur, principalement lorsqu’ils apparaissent sur un nouvel appareil ou une nouvelle application, mais plus souvent pour les rôles et les tâches critiques.
- Désactivation de l’authentification à partir de clients d’authentification hérités qui ne peuvent pas effectuer la MFA.
- Protection des administrateurs en exigeant une authentification supplémentaire chaque fois qu’ils se connectent.

L’authentification multifacteur est une première étape importante de la sécurisation de votre entreprise, et les paramètres de sécurité par défaut facilitent l’implémentation de l’authentification multifacteur. Si votre abonnement a été créé le ou après le 22 octobre 2019, les paramètres de sécurité par défaut peuvent avoir été automatiquement activés pour vous&mdash; devez vérifier vos paramètres pour confirmer.

> [!TIP]
> Pour plus d’informations sur les paramètres de sécurité par défaut et les stratégies qu’ils appliquent, consultez [Que sont les paramètres de sécurité par défaut?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

### <a name="to-enable-security-defaults-or-confirm-theyre-already-enabled"></a>Pour activer les paramètres de sécurité par défaut (ou confirmer qu’ils sont déjà activés)

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> avec l’administrateur de sécurité, l’administrateur d’accès conditionnel ou les informations d’identification de l’administrateur général.

2. Dans le volet gauche, sélectionnez **Afficher tout**, and puis sous **Centres d’administration**, sélectionnez **Azure Active Directory**.

3. Dans le volet gauche du centre d’administration **Azure Active Directory**, sélectionnez **Azure Active Directory**.

4. Dans le menu de gauche du tableau de bord, dans la section **Gérer**, sélectionnez **Propriétés**.

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="Capture d’écran du centre d’administration Azure Active Directory montrant l’emplacement de l’élément de menu Propriétés":::.

5. En bas de la page **Propriétés**, sélectionnez **Gérer la sécurité par défauts**.

6. Dans le volet droit, vous verrez le paramètre **Activez la sécurité par défaut**. Si **Oui** est sélectionné, les paramètres de sécurité par défaut sont déjà activés et aucune autre action n’est requise. Si les paramètres de sécurité par défaut ne sont pas activés, sélectionnez **Oui** pour les activer, puis sélectionnez **Enregistrer**.

## <a name="conditional-access"></a>Accès conditionnel

> [!NOTE]
> Si vous utilisez les paramètres de sécurité par défaut, vous devrez les désactiver avant d’utiliser l’accès conditionnel. Vous pouvez utiliser les paramètres de sécurité par défaut ou les stratégies d’accès conditionnel, mais vous ne pouvez pas utiliser les deux en même temps.

Si votre entreprise ou votre entreprise a des exigences de sécurité complexes ou si vous avez besoin d’un contrôle plus précis sur vos stratégies de sécurité, vous devez envisager d’utiliser l’accès conditionnel plutôt que les paramètres de sécurité par défaut pour obtenir une posture de sécurité similaire ou supérieure.

L’accès conditionnel vous permet de créer et de définir des stratégies qui réagissent aux événements de connexion et de demander des actions supplémentaires avant qu’un utilisateur ne soit autorisé à accéder à une application ou un service. Les stratégies d’accès conditionnel peuvent être granulaires et spécifiques, afin de permettre aux utilisateurs de gagner en productivité où qu’ils soient et à tout moment, mais également de protéger votre organisation.

Les paramètres de sécurité par défaut sont disponibles pour tous les clients, tandis que l’accès conditionnel nécessite l’un des plans suivants :

- Azure Active Directory Premium P1 ou P2 (version d’évaluation)
- Microsoft 365 Business Premium
- Microsoft 365 E3 ou E5
- Enterprise Mobilité & Sécurité E3 ou E5

Si vous souhaitez utiliser l’accès conditionnel pour configurer des stratégies, consultez les guides pas à pas suivants :

- [Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Exiger l’authentification multifacteur pour la gestion Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Exiger l’inscription MFA Azure AD](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) : Nécessite Azure AD Identity Protection, qui fait partie de Azure Active Directory Premium P2

Pour en savoir plus sur l’accès conditionnel, consultez [Qu’ est-ce que l’accès conditionnel?](/azure/active-directory/conditional-access/overview) Pour plus d’informations sur la création de stratégies d’accès conditionnel, consultez [Créer une stratégie d’accès conditionnel](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> Si vous disposez d’un plan ou d’une licence qui fournit l’accès conditionnel mais n’avez pas encore créé de stratégies d’accès conditionnel, vous pouvez utiliser les paramètres de sécurité par défaut. Toutefois, vous devez désactiver les paramètres de sécurité par défaut avant de pouvoir utiliser des stratégies d’accès conditionnel.

## <a name="next-objective"></a>Objectif suivant

[Protéger vos comptes d’administrateur dans Microsoft 365 Business Premium](m365bp-protect-admin-accounts.md)
