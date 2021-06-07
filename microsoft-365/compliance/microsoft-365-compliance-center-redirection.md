---
title: Rediriger les utilisateurs du centre Office 365 sécurité et conformité vers le centre Microsoft 365 conformité de l’application
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
localization_priority: Normal
description: Découvrez comment rediriger automatiquement Office 365 utilisateurs du Centre de sécurité et conformité vers le centre Microsoft 365 conformité.
ms.collection: M365-security-compliance
ms.openlocfilehash: fb667e8f19b26cbe229b3aceffe194a86133c261
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52772479"
---
# <a name="redirect-users-from-the-office-365-security-and-compliance-center-to-the-microsoft-365-compliance-center"></a>Rediriger les utilisateurs du centre Office 365 sécurité et conformité vers le centre Microsoft 365 conformité de l’application

Cet article explique comment fonctionne la redirection automatique pour les utilisateurs accédant à des solutions de conformité à partir du Centre de sécurité et conformité Office 365 (protection.office.com) vers le Centre de conformité Microsoft 365 (compliance.microsoft.com).

## <a name="what-to-expect"></a>À quoi s’attendre

La redirection automatique est activée par défaut pour tous les utilisateurs accédant aux solutions de conformité suivantes dans Office 365 Security and Compliance (protection.office.com) :

- Protection contre la perte de données (DLP)
- Classification
- Gouvernance des informations
- Gestion des enregistrements
- Conformité des communications (anciennement « Supervision » )

Les utilisateurs sont automatiquement acheminés vers les mêmes solutions de conformité dans le centre Microsoft 365 conformité (compliance.microsoft.com).

>[!NOTE]
>Pour les autres solutions de conformité incluses dans le Centre de sécurité et conformité Office 365, les utilisateurs continueront à gérer ces solutions dans le Centre de conformité Microsoft 365 ou le Centre de sécurité et conformité Office 365. La redirection automatique pour ces solutions de conformité sera bientôt disponible.*

Cette fonctionnalité et les contrôles associés n’activent pas la redirection automatique des fonctionnalités de sécurité pour Microsoft Defender pour Office 365. Pour activer la redirection pour les [fonctionnalités](/microsoft-365/security/defender/microsoft-365-security-mdo-redirection) de sécurité, consultez La redirection des comptes de Microsoft Defender Office 365 vers le centre de sécurité Microsoft 365 pour plus d’informations.

## <a name="can-i-go-back-to-using-the-former-portal"></a>Puis-je revenir à l’ancien portail ?

Si quelque chose ne fonctionne pas pour vous ou s’il y a quelque chose que vous ne parvenez pas à effectuer via le portail du Centre de conformité Microsoft 365, vous pouvez désactiver temporairement la redirection automatique pour tous les utilisateurs.

>[!IMPORTANT]
>Le centre Microsoft 365 conformité est le portail de gestion des remplacements pour les solutions de conformité actuellement gérées dans le centre de sécurité Office 365 conformité. Toutes Microsoft 365 solutions de conformité seront gérées uniquement dans le centre Microsoft 365 conformité. La désactivation de la redirection vers le centre Microsoft 365 conformité doit être une solution à court terme.*

Pour revenir au Centre Office 365 sécurité et conformité (protection.microsoft.com) pour tous les utilisateurs, passez aux étapes suivantes :

1. Connectez-vous au [centre Microsoft 365](https://compliance.microsoft.com) conformité en tant qu’administrateur général ou en utilisant n’importe quel compte ayant des autorisations d’administrateur de conformité dans Azure Active Directory.
2. Accédez à **Paramètres**  >  **redirection du Centre de conformité.**
3. Basculez le paramètre de redirection automatique sur **Désintégation.**
4. Sélectionnez **Désactiver et** partager des commentaires lorsque vous y sont invités.

Une fois désactivés, les utilisateurs ne sont plus acheminés vers compliance.microsoft.com et ils sont dirigés vers le Centre de sécurité et conformité Office 365 (protection.microsoft.com). Ce paramètre peut être à nouveau activé à tout moment par les administrateurs globaux ou de conformité.

## <a name="related-information"></a>Informations connexes

- [vue d Microsoft 365 du centre de conformité de l’application](/microsoft-365/compliance/microsoft-365-compliance-center)
