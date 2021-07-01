---
title: Rediriger les utilisateurs du centre Office 365 sécurité et conformité vers le Centre de conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
localization_priority: Normal
description: Découvrez comment rediriger automatiquement Office 365 utilisateurs du Centre de sécurité et conformité vers le Centre de conformité Microsoft 365.
ms.collection: M365-security-compliance
ms.openlocfilehash: 83d6a08d5c189c08c8f7d25daa3af39f28cbf8f1
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53226274"
---
# <a name="redirect-users-from-the-office-365-security-and-compliance-center-to-the-microsoft-365-compliance-center"></a>Rediriger les utilisateurs du centre Office 365 sécurité et conformité vers le Centre de conformité Microsoft 365

Cet article explique comment fonctionne la redirection automatique pour les utilisateurs accédant à des solutions de conformité à partir du Centre de sécurité et conformité Office 365 (protection.office.com) vers le Centre de conformité Microsoft 365 (compliance.microsoft.com).

## <a name="what-to-expect"></a>À quoi s’attendre

La redirection automatique est activée par défaut pour tous les utilisateurs accédant aux solutions de conformité suivantes dans Office 365 Security and Compliance (protection.office.com) :

- Protection contre la perte de données (DLP)
- Classification
- Gouvernance des informations
- Gestion des enregistrements
- Conformité des communications (anciennement « Supervision » )

Les utilisateurs sont automatiquement acheminés vers les mêmes solutions de conformité dans le Centre de conformité Microsoft 365 (compliance.microsoft.com).

> [!NOTE]
> Pour les autres solutions de conformité incluses dans le Centre de sécurité et conformité Office 365, les utilisateurs continueront à gérer ces solutions dans le centre de sécurité et conformité Centre de conformité Microsoft 365 ou Office 365. La redirection automatique pour ces solutions de conformité sera bientôt disponible.*

Cette fonctionnalité et les contrôles associés n’activent pas la redirection automatique des fonctionnalités de sécurité pour Microsoft Defender pour Office 365. Pour activer la redirection pour les [fonctionnalités](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection) de sécurité, consultez La redirection des comptes de Microsoft Defender Office 365 vers le centre de sécurité Microsoft 365 pour plus d’informations.

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?

Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne parvenez pas à effectuer via le portail Centre de conformité Microsoft 365, vous pouvez désactiver temporairement la redirection automatique pour tous les utilisateurs.

> [!IMPORTANT]
> Le Centre de conformité Microsoft 365 est le portail de gestion de remplacement pour les solutions de conformité actuellement gérées dans le Centre Office 365 sécurité et conformité. Toutes Microsoft 365 solutions de conformité seront gérées uniquement dans le Centre de conformité Microsoft 365. La désactivation de la redirection vers le Centre de conformité Microsoft 365 doit être une solution à court terme.*

Pour revenir au Centre Office 365 sécurité et conformité (protection.microsoft.com) pour tous les utilisateurs, passez aux étapes suivantes :

1. Connectez-vous au [Centre de conformité Microsoft 365](https://compliance.microsoft.com) en tant qu’administrateur général ou en utilisant n’importe quel compte ayant des autorisations d’administrateur de conformité dans Azure Active Directory.
2. Accédez à **Paramètres**  >  **redirection du Centre de conformité.**
3. Basculez le paramètre de redirection automatique sur **Désintégation.**
4. Sélectionnez **Désactiver et** partager des commentaires lorsque vous y avez été invité.

Une fois désactivés, les utilisateurs ne sont plus acheminés vers compliance.microsoft.com et ils sont dirigés vers le Centre de sécurité et conformité Office 365 (protection.microsoft.com). Ce paramètre peut être à nouveau activé à tout moment par les administrateurs globaux ou de conformité.

## <a name="related-information"></a>Informations connexes

- [Centre de conformité Microsoft 365 vue d’ensemble](/microsoft-365/compliance/microsoft-365-compliance-center)
