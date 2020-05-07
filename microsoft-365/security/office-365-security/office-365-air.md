---
title: 'Recherche et réponse automatisées (AIR) : prise en main'
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
ms.custom: air - seo-marvel-mar2020
ms.openlocfilehash: cb65b5a7f0b12ff977c0e8bd92912b8f741a2281
ms.sourcegitcommit: 7ff75a0f45371b247d975fc61cfa286f5b6f42f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "44141546"
---
# <a name="get-started-using-automated-investigation-and-response-air-in-office-365"></a>Prise en main de l’analyse et de la réponse automatisées (AIR) dans Office 365

[Office 365 Advanced Threat Protection](office-365-atp.md) (Office 365 ATP) plan 2 inclut de puissantes fonctionnalités d’analyse et de réponse automatisées (air) qui permettent d’économiser le temps et les efforts de l’équipe des opérations de sécurité. Comme les alertes sont déclenchées, c’est à votre équipe chargée des opérations de sécurité de passer en revue les alertes, de les classer par ordre de priorité et de les répondre. Le volume des alertes entrantes peut être insurmontable. L’automatisation de certains d’entre eux peut vous aider. Avec AIR, votre équipe des opérations de sécurité peut se concentrer sur les tâches de plus haute priorité sans perdre en visibilité les alertes déclenchées.

Cet article décrit le [flux](#the-overall-flow-of-air) d’air global, la [façon d’obtenir](#how-to-get-air)de l’air et les [autorisations requises](#required-permissions-to-use-air-capabilities) pour configurer ou utiliser les fonctionnalités air. 

## <a name="the-overall-flow-of-air"></a>Flux d’AIR global

À un niveau élevé, une alerte est déclenchée et un manifeste de sécurité démarre et une enquête automatisée, qui entraîne des conclusions et des recommandations. Voici le flux d’AIR global, étape par étape :

1. Une enquête automatisée est lancée de l’une des manières suivantes :

   - Une [alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) est déclenchée par un événement Office, ce qui crée un incident. Selon le type d’incident, un manuel de [sécurité](automated-investigation-response-office.md#security-playbooks) lance une enquête automatisée. 

     --- ou ---
   
   - Un analyste de la sécurité [lance une enquête automatisée](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) lors de l’utilisation de l' [Explorateur de menaces](threat-explorer.md).

2. Lorsqu’une enquête automatisée s’exécute, elle recueille des données supplémentaires sur le courrier électronique en question et les entités associées à ce message. Ces entités peuvent inclure des fichiers, des URL et des destinataires.  L’étendue de l’enquête peut augmenter au fur et à mesure que des alertes nouvelles et associées sont déclenchées.

3. Pendant et après une enquête automatisée, des [Détails et des résultats](air-view-investigation-results.md) peuvent être consultés. Les résultats incluent les [actions recommandées](air-remediation-actions.md) qui peuvent être prises pour répondre et corriger les menaces détectées. De plus, un [Journal des manifestes](air-view-investigation-results.md#playbook-log) est disponible pour suivre toutes les activités d’enquête.

    Si votre organisation utilise une solution de création de rapports personnalisée ou une solution tierce, vous pouvez [utiliser l’API activité de gestion d’Office 365](air-custom-reporting.md) pour afficher des informations sur les analyses et les menaces automatisées.

4. Votre équipe de gestion des opérations de sécurité examine les [résultats de l’enquête](air-view-investigation-results.md), puis [approuve ou rejette les actions correctives](air-review-approve-pending-completed-actions.md). 

    Comme les actions de correction en attente sont approuvées (ou rejetées), l’enquête automatisée se termine.

> [!NOTE]
> Dans Office 365 ATP, aucune action de correction n’est effectuée automatiquement. Les actions correctives sont mises en œuvre uniquement après approbation par l’équipe de sécurité de votre organisation. 

Pendant et après un processus d’enquête automatisé, votre équipe de sécurité peut effectuer les opérations suivantes :

- [Afficher les détails d’une alerte liée à une enquête](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)

- [Afficher les détails des résultats d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)

- [Passer en revue et approuver les actions à la suite d’une enquête](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Pour plus d’informations, consultez la rubrique fonctionnement de [l’air](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office).

## <a name="how-to-get-air"></a>Comment obtenir de l’AIR

Les fonctionnalités AIR d’Office 365 sont incluses dans [office 365 Advanced Threat Protection Plan 2](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#office-365-atp-plan-1-and-plan-2). Toutefois, vos [stratégies ATP Office 365 doivent être configurées](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats) afin que l’air fonctionne comme prévu. En outre, veillez à consulter et éventuellement configurer les stratégies d' [alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)de votre organisation. 

Microsoft 365 fournit de nombreuses stratégies d’alerte intégrées qui permettent d’identifier les abus des autorisations d’administration Exchange, l’activité de programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Plusieurs stratégies d' [alerte par défaut](https://docs.microsoft.com/microsoft-365/compliance/alert-policies#default-alert-policies) peuvent déclencher des analyses automatiques. Elles incluent notamment les éléments suivants :

- Un clic d’URL potentiellement malveillant est détecté

- Un message électronique est signalé par un utilisateur comme hameçonnage

- Les messages électroniques contenant des programmes malveillants sont supprimés après la remise

- Les messages électroniques contenant des URL d’hameçonnage sont supprimés après la remise

- Des modèles d’envoi de courrier électronique suspects sont détectés

- Un utilisateur ne peut pas envoyer de courrier électronique

[En savoir plus sur les alertes et l’air](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office).

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant : 

|Tâche |Rôle (s) requis |
|--|--|
|Pour configurer les fonctionnalités AIR |Un des rôles suivants : <br/>-Administrateur général<br/>-Administrateur de la sécurité <br/>Ces rôles peuvent être attribués dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). |
|Pour approuver ou rejeter des actions recommandées|L’un des rôles suivants, affecté dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)) :<br/>-Administrateur général <br/>-Administrateur de la sécurité<br/>-Lecteur de sécurité <br/>--- et ---<br/>-Rechercher et purger (ce rôle est affecté uniquement dans le [Centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). Vous devrez peut-être créer un groupe de rôles à cet emplacement et ajouter le rôle de recherche et de purge à ce nouveau groupe de rôles.)

[Office 365 DAV plan 2](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#office-365-atp-plan-1-and-plan-2) les licences doivent être affectées à :
- Administrateurs de la sécurité (y compris les administrateurs généraux)
- Équipe des opérations de sécurité de votre organisation (y compris les lecteurs de sécurité et les rôles de recherche et de purge)
- Utilisateurs finals

En outre, les stratégies [Office 365 ATP](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) doivent être définies et appliquées afin que la protection soit mise en place.

## <a name="next-steps"></a>Étapes suivantes

- [Afficher les détails et les résultats d’une enquête automatisée](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results#view-details-of-an-investigation)

- [Vérifier et approuver les actions en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions)

## <a name="related-articles"></a>Articles connexes

- [Recherche et correction automatisées dans la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
