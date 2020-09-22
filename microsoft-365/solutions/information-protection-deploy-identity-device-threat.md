---
title: Utiliser l’identité, l’appareil et la protection contre les menaces pour le règlement de confidentialité des données
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
ms.custom: ''
description: Empêchez les violations de données personnelles grâce aux services d’identité, de périphérique et de protection contre les menaces de Microsoft 365.
ms.openlocfilehash: a0efdcfe8e9d27e19b6cf1355a6d0943b7cdaa59
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48195662"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Utiliser l’identité, l’appareil et la protection contre les menaces pour le règlement de confidentialité des données

Microsoft 365 fournit un certain nombre de fonctionnalités d’identité, de protection des appareils et de protection contre les menaces que les organisations peuvent utiliser pour se conformer aux réglementations de conformité liées à la confidentialité des données. Cet article décrit les réglementations relatives à la confidentialité des données dans ces domaines et fournit une liste des services et fonctionnalités Microsoft 365 associés avec des liens vers des informations supplémentaires pour vous aider à répondre aux besoins de l’implémentation.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Relation entre l’identité, l’appareil et la protection contre les menaces et le règlement sur la confidentialité des données

Bien que les réglementations relatives à la confidentialité des données varient en fonction de leur spécificité, l’essence de ce qu’elles appellent est incorporée dans l’article 5 (1) (f) du RGPD, qui indique les points suivants : 

- Les données personnelles doivent être traitées de manière à garantir une sécurité appropriée des données personnelles, y compris la protection contre le traitement non autorisé ou illégal et contre la perte accidentelle, la destruction ou les dégâts, à l’aide de mesures techniques ou organisationnelles appropriées (« intégrité et confidentialité »).

Étant donné que les violations de données personnelles sont souvent dues à une compromission administrative ou à un compte d’utilisateur final et à un accès système malveillant. Par exemple, un compte administrateur hack peut entraîner l’exfiltration des numéros de carte de crédit des clients ou d’autres informations personnelles. Toutes les protections d’identité, de périphérique et de menace généralement recommandées avec Microsoft 365 peuvent être implémentées, qui seront reflétées dans votre score de conformité, dans le gestionnaire de conformité.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Utilisation des résultats de votre analyse et du gestionnaire de conformité

Le gestionnaire de conformité inclut la protection des identités, des périphériques et des menaces à l’aide des catégories suivantes :

- Identity correspond à la catégorie d' **accès au contrôle**
- Le périphérique correspond à la catégorie **gérer les appareils** .
- Protection contre les menaces correspond à la catégorie **protéger contre les menaces**
 
Si ces éléments sont sélectionnés dans notre ensemble d’exemples de quatre principales réglementations de confidentialité des données, le gestionnaire de conformité indique 90 actions d’amélioration, dont la plupart sont notées « 27 ». Étant donné qu’un tel grand nombre est appelé par le gestionnaire de conformité pour ces catégories, certaines des plus courantes sont répertoriées ici, à des fins de référence.

Utilisez [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) pour l’identité et la catégorie d' **accès au contrôle** , avec lequel vous pouvez :

- Implémenter l’authentification resistante à la relecture (pour éviter les attaques de « l’homme en milieu »)
- Bloquer l’authentification héritée.
- Configurez les risques utilisateur et les stratégies de risque de connexion utilisateur.
- Activer l’accès conditionnel et l’authentification multifacteur (MFA) pour les administrateurs et les non-administrateurs.
- Configurez et appliquez des stratégies de mot de passe.
- Restreignez l’accès aux comptes privilégiés avec Azure AD Privileged Identity Management.
- Désactiver l’accès lors de l’arrêt.
- Audit des comptes d’utilisateur et des modifications d’État.
- Passez en revue les groupes de rôles et les modifications administratives.

Utilisez le [Gestionnaire de points de terminaison Microsoft](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) pour les appareils et la catégorie **gérer les appareils** , avec lequel vous pouvez :

- Blocage de la prison et des appareils mobiles enracinés.
- Configurez Intune pour la gestion des appareils mobiles.
- Créer des stratégies de conformité pour les appareils Android, iOS, macOS et Windows.
- Créez un profil de configuration d’appareil pour Android, iOS, macOS et appareils Windows.
- Créez des stratégies de protection des applications pour iOS et Windows.
- Masquer les informations avec l’écran de verrouillage.
- Implémenter des stratégies de mot de passe pour les appareils mobiles.
- Exiger que les appareils mobiles soient verrouillés lors de l’inactivité.
- Exigez la réinitialisation des appareils mobiles sur plusieurs échecs de connexion.

Utilisez [Exchange Online Protection et Office 365 protection avancée contre les menaces (ATP)](../security/office-365-security/office-365-atp.md) pour la catégorie **protéger contre les menaces** , avec lequel vous pouvez :

- Activer l’authentification des expéditeurs (SPF, DMARC et DKIM).
- Configurez les stratégies de protection avancée contre les menaces Office 365 (ATP).
- Implémenter des pièces jointes fiables ATP.
- Implémenter des liens fiables ATP.
- Implémenter des stratégies de détection et de réponse contre les programmes malveillants.
- Implémenter des stratégies de courrier indésirable entrant et sortant.

### <a name="references"></a>Référenç

- [Stratégies communes pour les identités et l’accès aux appareils](../enterprise/identity-access-policies.md)
- [Se protéger contre les menaces dans Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Pièces jointes fiables ATP](../security/office-365-security/atp-safe-attachments.md)
- [Liens fiables ATP](../security/office-365-security/atp-safe-links.md)
- [Documents fiables PACM](../security/office-365-security/safe-docs.md)
