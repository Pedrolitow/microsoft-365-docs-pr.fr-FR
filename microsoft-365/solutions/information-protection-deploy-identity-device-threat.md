---
title: Utiliser la protection des identités, des appareils et des menaces pour la réglementation sur la confidentialité des données
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
- m365solution-scenario
ms.custom: ''
description: Empêcher les violations de données personnelles avec les services de protection contre les identités, appareils et menaces de Microsoft 365.
ms.openlocfilehash: 5e08ef574e199769e572b3836b3323dc88fc4bbd
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51199464"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Utiliser la protection des identités, des appareils et des menaces pour la réglementation sur la confidentialité des données

Microsoft 365 fournit un certain nombre de fonctionnalités de protection contre les menaces, les appareils et les identités que les organisations peuvent utiliser pour se conformer aux réglementations de conformité liées à la confidentialité des données. Cet article décrit les exigences en matière de confidentialité des données dans ces domaines et fournit une liste des fonctionnalités et services Microsoft 365 associés avec des liens vers des informations supplémentaires pour vous aider à répondre aux exigences d’implémentation.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Lien entre l’identité, l’appareil et la protection contre les menaces par rapport à la réglementation sur la confidentialité des données

Bien que les réglementations en matière de confidentialité des données varient en fonction de leur spécificité, la nature de ce qu’elles appellent est incorporée dans l’article 5(1)(f) du R GDPR, qui stipule que :

- Les données personnelles doivent être traitées d’une manière qui garantit la sécurité appropriée des données personnelles, y compris la protection contre le traitement non autorisé ou illégal et contre les pertes, destructions ou dommages accidentels, à l’aide de mesures techniques ou organisationnelles appropriées (intégrité et confidentialité).

Étant donné que les violations de données personnelles sont souvent dues à une compromission de compte d’administration ou d’utilisateur final et à un accès malveillant au système. Par exemple, un piratage de compte d’administrateur peut entraîner l’exfiltration de numéros de carte de crédit client ou d’autres informations personnelles. Toutes les protections généralement conseillées en matière d’identité, d’appareil et de menaces disponibles avec Microsoft 365 doivent éventuellement être implémentées, ce qui sera reflété dans votre score de conformité, disponible dans le Gestionnaire de conformité.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Utilisation des résultats de votre travail d’évaluation et du Gestionnaire de conformité

Le Gestionnaire de conformité inclut la protection contre les identités, les appareils et les menaces à l’aide des catégories suivantes :

- L’identité correspond à la **catégorie Contrôle d’accès**
- L’appareil correspond à la **catégorie Gérer les appareils**
- La protection contre les menaces correspond à la **catégorie Protéger contre les menaces**
 
Si celles-ci sont sélectionnées dans notre exemple de quatre réglementations majeures en matière de confidentialité des données, le Gestionnaire de conformité spécifie 90 actions d’amélioration, dont la plupart ont le niveau « 27 ». Étant donné qu’un nombre aussi élevé est appelé par le Gestionnaire de conformité pour ces catégories, certaines des plus courantes sont répertoriées ici, à titre de référence.

Utilisez [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) pour l’identité et la catégorie **d’accès** au contrôle, avec laquelle vous pouvez :

- Implémenter une authentification résistant à la relecture (pour empêcher les attaques « De l’homme au milieu » )
- Bloquer l’authentification héritée.
- Configurez les stratégies de risque de l’utilisateur et de la connectez-vous.
- Activer l’accès conditionnel et l’authentification multifacteur (MFA) pour les administrateurs et les non-administrateurs.
- Configurer et appliquer des stratégies de mot de passe.
- Restreindre l’accès aux comptes privilégiés avec Azure AD Privileged Identity Management.
- Désactiver l’accès lors de l’arrêt.
- Auditer les comptes d’utilisateur et les changements d’état.
- Passer en revue les modifications administratives et de groupe de rôles.

Utilisez [Microsoft Endpoint Manager pour](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) les appareils et la catégorie **Gérer** les appareils, avec laquelle vous pouvez :

- Bloquez les appareils mobiles rompus et racines de la cellule.
- Configurez Intune pour la gestion des appareils mobiles.
- Créez des stratégies de conformité pour les appareils Android, iOS, macOS et Windows.
- Créez un profil de configuration d’appareil pour les appareils Android, iOS, macOS et Windows.
- Créez des stratégies de protection des applications pour iOS et Windows.
- Masquer les informations à l’écran de verrouillage.
- Implémenter des stratégies de mot de passe pour les appareils mobiles.
- Exiger que les appareils mobiles se verrouillent en cas d’inactivité.
- Exiger que les appareils mobiles s’effacent en cas d’échec de plusieurs connecteurs.

Utilisez Exchange Online Protection et Microsoft Defender pour  [Office 365](../security/office-365-security/defender-for-office-365.md) pour la catégorie Protéger contre les menaces, avec laquelle vous pouvez :

- Activer l’authentification de l’expéditeur (SPF, DMARC et DKIM).
- Configurer Microsoft Defender pour les stratégies anti-hameçonnage d’Office 365.
- Implémenter les pièces jointes sécurisées.
- Implémenter des liens sécurisés.
- Implémenter des stratégies de détection et de réponse aux programmes malveillants.
- Implémenter des stratégies de courrier indésirable sortant et entrant.

### <a name="references"></a>Références :

- [Stratégies communes pour les identités et l’accès aux appareils](../security/office-365-security/identity-access-policies.md)
- [Se protéger contre les menaces dans Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Pièces jointes fiables](../security/office-365-security/safe-attachments.md)
- [Liens fiables](../security/office-365-security/safe-links.md)
- [Documents sécurisés](../security/office-365-security/safe-docs.md)
