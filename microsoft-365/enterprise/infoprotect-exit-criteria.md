---
title: Critères de sortie de l’infrastructure de protection des informations
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Examinez les critères de l’infrastructure et des services de protection des informations pour vérifier que votre configuration remplit les conditions requises de Microsoft 365 Entreprise.
ms.openlocfilehash: 681b3bb2500680b4f5d5801486347aec1b801714
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32283694"
---
# <a name="information-protection-infrastructure-exit-criteria"></a>Critères de sortie de l’infrastructure de protection des informations

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Vérifiez que votre infrastructure de protection des informations répond aux critères obligatoires suivants et que vous avez pris en considération les critères facultatifs.

<a name="crit-infoprotect-step1"></a>
## <a name="required-security-and-information-protection-levels-for-your-organization-are-defined"></a>Obligatoire : définition des niveaux de protection des informations et de sécurité pour votre organisation

Vous avez planifié et défini les niveaux de sécurité dont votre organisation a besoin. Ces niveaux définissent un niveau minimal de sécurité et des niveaux supplémentaires pour les informations de plus en plus sensibles et la sécurité requise de leurs données.

Vous utilisez au moins trois niveaux de sécurité :

- Baseline
- Sensible
- Hautement réglementé

Si nécessaire, l’[Étape 1](infoprotect-define-sec-infoprotect-levels.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step4"></a>
## <a name="required-increased-security-for-microsoft-365-is-configured"></a>Obligatoire : le paramètre Sécurité accrue de Microsoft 365 est configuré

Vous avez configuré les paramètres de [Sécurité accrue d’Office 365](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security) suivants :

- Stratégies de gestion des menaces dans le Centre de sécurité Microsoft 365
- Autres paramètres à l’échelle du client Exchange Online
- Stratégies de partage à l’échelle du client dans le Centre d’administration SharePoint
- Paramètres d’Azure Active Directory (Azure AD)

Vous avez également [activé Office 365 - Protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams](https://docs.microsoft.com/fr-FR/office365/securitycompliance/turn-on-atp-for-spo-odb-and-teams).

Si nécessaire, l’[Étape 3](infoprotect-configure-increased-security-office-365.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step3"></a>
## <a name="optional-classification-is-configured-across-your-environment"></a>Facultatif : configurer la classification au sein de votre environnement

Vous avez travaillé avec vos équipes juridiques et de conformité afin de développer une classification et un système d’étiquetage appropriés pour les stratégies de sécurité et de gouvernance des données de votre organisation. 

Ces stratégies correspondent à la configuration et au déploiement de ce qui suit :

- Types de données sensibles
- Étiquettes de rétention
- Étiquettes de niveau de confidentialité
- Étiquettes Azure Information Protection

Si nécessaire, l’[Étape 2](infoprotect-configure-classification.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step5"></a>
## <a name="optional-configure-privileged-access-management-in-office-365"></a>Facultatif : configurer la gestion des accès privilégiés pour Office 365

Vous avez utilisé les informations de la rubrique [Configurer la gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration) pour activer l’accès privilégié et créer une ou plusieurs stratégies d’accès privilégié au sein de votre organisation. Vous avez configuré ces stratégies et l’accès juste-à-temps est activé pour l’accès aux données sensibles ou aux paramètres de configuration critiques.

Si nécessaire, l’[Étape 4](infoprotect-configure-privileged-access-management.md) peut vous aider à répondre à cette exigence. 

## <a name="results-and-next-steps"></a>Résultats et étapes suivantes

Votre infrastructure de protection des informations Microsoft 365 Entreprise utilise des niveaux de sécurité définis, une sécurité renforcée pour Office 365, une classification à l’aide d’étiquettes et de types de données sensibles, ainsi qu’une gestion des accès privilégiés.

Si vous suivez le déploiement de bout en bout de Microsoft 365 Entreprise, vous êtes maintenant prêt à tirer parti de l’ensemble des fonctionnalités et de la configuration de votre infrastructure de base pour vos [charges de travail et scénarios](deploy-workloads.md).
