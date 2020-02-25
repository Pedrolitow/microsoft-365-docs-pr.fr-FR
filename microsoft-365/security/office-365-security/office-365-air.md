---
title: Recherche et réponse automatiques dans Office 365
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: Prise en main des fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 3a362f7d15a9cc8e1f5784ec03c8c04d3d77886d
ms.sourcegitcommit: 133bf7936e5ef1a4d06998429d0d01096bda929f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42262011"
---
# <a name="automated-investigation-and-response-air-in-office-365"></a>Recherche et réponse automatiques dans Office 365

[Office 365 protection avancée contre les menaces](office-365-atp.md) Le plan 2 inclut des fonctionnalités d’analyse et de réponse automatisées puissantes qui permettent d’économiser le temps et les efforts de votre équipe en matière de sécurité. Lorsque certaines alertes sont déclenchées, un ou plusieurs règles de sécurité se déclenchent et le processus d’enquête automatisé commence. Cela permet à votre équipe des opérations de sécurité de se concentrer sur les tâches à haute priorité sans perdre en visibilité les alertes déclenchées. 

## <a name="the-overall-flow-of-air"></a>Flux d’AIR global

À un niveau élevé, le flux d’AIR fonctionne comme ceci :

|Étape  |Action exécutée  |
|---------|---------|
|0,1     |Une alerte est déclenchée par un événement Office et un [Manuel de sécurité](automated-investigation-response-office.md#security-playbooks) lance une enquête automatisée pour les alertes sélectionnées. <br/><br/>Par ailleurs, un analyste de la sécurité peut [déclencher une enquête automatisée](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) tout en utilisant l' [Explorateur de menaces](threat-explorer.md).        |
|n°2     |Lorsqu’une enquête automatisée s’exécute, elle recueille des données supplémentaires sur le courrier électronique et les entités associées à cet e-mail (fichiers, URL et destinataires).  L’étendue de l’enquête peut augmenter, car de nouvelles alertes associées sont déclenchées.         |
|3     |Pendant et après une enquête automatisée, des [Détails et des résultats](air-view-investigation-results.md) peuvent être consultés. Les résultats incluent les [actions recommandées](air-remediation-actions.md) qui peuvent être prises pour répondre et corriger les menaces détectées. De plus, un [Journal des manifestes](air-view-investigation-results.md#playbook-log) est disponible pour suivre toutes les activités d’enquête.<br/><br/>Si votre organisation utilise une solution de création de rapports personnalisée ou une solution tierce, vous pouvez [utiliser l’API activité de gestion d’Office 365](air-custom-reporting.md) pour afficher des informations sur les analyses et les menaces automatisées.         |
|4     |Votre équipe de gestion des opérations de sécurité examine les [résultats d’enquête et les recommandations](air-view-investigation-results.md), et [approuve les actions de correction](air-remediation-actions.md#approve-or-reject-pending-actions). Dans Office 365, aucune action n’est effectuée automatiquement. Les actions de correction ne sont prises qu’après approbation de l’équipe de sécurité de votre organisation.         |

Pendant et après un processus d’enquête automatisé, votre équipe de sécurité peut effectuer les opérations suivantes :

- [Afficher les détails d’une alerte liée à une enquête](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)
- [Afficher les détails des résultats d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)
- [Passer en revue et approuver les actions à la suite d’une enquête](air-remediation-actions.md#approve-or-reject-pending-actions)

Pour en savoir plus, consultez la rubrique fonctionnement de [l’air](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office).

## <a name="how-to-get-air"></a>Comment obtenir de l’AIR

Office 365 Examen et réponse automatisés est inclus dans les abonnements suivants :

- Microsoft 365 E5
- Office 365 E5
- Protection Microsoft contre les menaces
- Office 365 – Protection avancée contre les menaces Plan 2

Si vous n’avez pas l’un de ces abonnements, [Démarrez une version d’évaluation gratuite](https://go.microsoft.com/fwlink/p/?LinkID=698279&culture=en-US&country=US).

Pour en savoir plus sur la disponibilité des fonctionnalités, consultez la rubrique [disponibilité des fonctionnalités dans les plans de protection avancée contre les menaces](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant : 

|Tâche |Rôle (s) requis |
|--|--|
|Pour configurer les fonctionnalités AIR |Un des rôles suivants : <br/>- **Administrateur général**<br/>- **Administrateur de la sécurité** <br/>Ces rôles peuvent être attribués dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [Centre de conformité Office 365 Security &](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). |
|Pour approuver ou rejeter des actions recommandées|L’un des rôles suivants, affecté dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)) :<br/>- **Administrateur général** <br/>- **Administrateur de la sécurité**<br/>- **Lecteur de sécurité** <br/>--- et ---<br/>- **Recherche et purger** (ce rôle est affecté uniquement dans le [Centre de conformité Office 365 Security &](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). Vous devrez peut-être créer un groupe de rôles à cet emplacement et ajouter le rôle de recherche et de purge à ce nouveau groupe de rôles.)

## <a name="related-articles"></a>Articles connexes

- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

- [Recherche et correction automatisées dans la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)