---
title: Critères de sortie de l’infrastructure de protection des informations
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/13/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Examinez les critères de l’infrastructure et des services de protection des informations pour vérifier que votre configuration remplit les conditions requises de Microsoft 365 Entreprise.
ms.openlocfilehash: 10d7b3b888999b65e5faff81e9a2d32e595294cf
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867367"
---
# <a name="information-protection-infrastructure-exit-criteria"></a>Critères de sortie de l’infrastructure de protection des informations

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Avant de terminer votre infrastructure de base, assurez-vous que votre infrastructure de protection des informations remplit les conditions suivantes. 

<a name="crit-infoprotect-step1"></a>
## <a name="required-security-and-information-protection-levels-for-your-organization-are-defined"></a>Obligatoire : définition des niveaux de protection des informations et de sécurité pour votre organisation

Vous avez planifié et défini les niveaux de sécurité dont votre organisation a besoin. Ces niveaux définissent un niveau minimal de sécurité et des niveaux supplémentaires pour les informations de plus en plus sensibles et la sécurité requise de leurs données.

Vous utilisez au moins trois niveaux de sécurité :

- Baseline
- Sensible
- Hautement réglementé

Si nécessaire, l’[Étape 1](infoprotect-define-sec-infoprotect-levels.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step4"></a>
## <a name="required-increased-security-for-office-365-is-configured"></a>Obligatoire : renforcer la sécurité d’Office 365

Vous avez configuré les paramètres suivants afin de renforcer la sécurité en fonction des informations figurant dans l’article [Configurer votre client Office 365 pour renforcer la sécurité](https://support.office.com/article/Configure-your-Office-365-tenant-for-increased-security-8d274fe3-db51-4107-ba64-865e7155b355) :

- Stratégies de gestion des menaces dans le Centre de sécurité et conformité Office 365
- Autres paramètres à l’échelle du client Exchange Online
- Stratégies de partage à l’échelle du client dans le Centre d’administration SharePoint
- Paramètres dans Azure Active Directory

Vous avez également [activé Office 365 – Protection avancée contre les menaces (ATP)](https://support.office.com/article/Office-365-ATP-for-SharePoint-OneDrive-and-Microsoft-Teams-26261670-db33-4c53-b125-af0662c34607#turniton).

Si nécessaire, l’[Étape 3](infoprotect-configure-increased-security-office-365.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step3"></a>
## <a name="optional-classification-is-configured-across-your-environment"></a>Facultatif : configurer la classification au sein de votre environnement

Vous avez travaillé avec vos équipes juridiques et de conformité afin de développer une classification et un système d’étiquetage appropriés pour les données de votre organisation, comme suit :

- Types de données sensibles
- Étiquettes Office 365
- Étiquettes Azure Information Protection

Si nécessaire, l’[Étape 2](infoprotect-configure-classification.md) peut vous aider à répondre à cette exigence. 

<a name="crit-infoprotect-step5"></a>
## <a name="optional-configure-privileged-access-management-in-office-365"></a>Facultatif : configurer la gestion des accès privilégiés pour Office 365

Vous avez utilisé les informations contenues dans la rubrique [Configurer la gestion des accès privilégié dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration) pour activer l’accès privilégié et créer une ou plusieurs stratégies d’accès privilégiés dans votre organisation Office 365. Ces stratégies sont configurés, et l’accès juste-à-temps est activé pour l’accès aux paramètres de configuration critiques et aux données sensibles.

Si nécessaire, l’[Étape 4](infoprotect-configure-privileged-access-management.md) peut vous aider à répondre à cette exigence. 

## <a name="next-step"></a>Étape suivante

Vous êtes maintenant prêt à déployer des [charges de travail et scénarios](deploy-workloads.md), tels que Microsoft Teams et Exchange Online, qui s’exécutent sur votre infrastructure de base Microsoft 365 Entreprise.
