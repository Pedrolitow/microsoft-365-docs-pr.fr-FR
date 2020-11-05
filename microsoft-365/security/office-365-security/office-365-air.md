---
title: Prise en main de l’analyse et de la réponse automatisées dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/04/2020
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Commencez à utiliser les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Defender pour Office 365.
ms.custom:
- air
- seo-marvel-mar2020
ms.openlocfilehash: 7e9b786a9d00a34f5e2e88a8481e82fa8425a501
ms.sourcegitcommit: 751dc531f0410ee075c179efe409a01664483ee2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48925603"
---
# <a name="get-started-using-automated-investigation-and-response-air-in-microsoft-defender-for-office-365"></a>Prise en main de l’analyse et de la réponse automatiques dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

[Microsoft Defender pour Office 365 comprend de](office-365-atp.md) puissantes fonctionnalités d’analyse et de réponse automatisées qui peuvent enregistrer le temps et les efforts de l’équipe des opérations de sécurité. Comme les alertes sont déclenchées, c’est à votre équipe chargée des opérations de sécurité de passer en revue les alertes, de les classer par ordre de priorité et de les répondre. Le volume des alertes entrantes peut être insurmontable. L’automatisation de certaines de ces tâches peut vous aider. Avec AIR, votre équipe des opérations de sécurité peut se concentrer sur les tâches de plus haute priorité sans perdre les alertes importantes déclenchées.

Cet article décrit les aspects suivants :
- Le [flux d’air global](#the-overall-flow-of-air);
- [Comment obtenir de l’air](#how-to-get-air); les 
- Les [autorisations requises](#required-permissions-to-use-air-capabilities) pour configurer ou utiliser les fonctionnalités air. 

## <a name="the-overall-flow-of-air"></a>Flux d’AIR global

Une alerte est déclenchée et un manifeste de sécurité lance une enquête automatisée, ce qui entraîne des conclusions et des actions recommandées. Voici le flux d’AIR global, étape par étape :

1. Une enquête automatisée est lancée de l’une des manières suivantes :

   - Une [alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) est déclenchée par un message suspect dans la messagerie (par exemple, un message, une pièce jointe ou une URL). Un incident est créé. Selon le type d’incident, un manifeste de [sécurité](automated-investigation-response-office.md#security-playbooks) s’exécute et une enquête automatisée commence. 

     --- ou ---
   
   - Un analyste de la sécurité [lance une enquête automatisée](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) lors de l’utilisation de l' [Explorateur de menaces](threat-explorer.md).

2. Lorsqu’une enquête automatisée s’exécute, elle recueille des données supplémentaires sur le courrier électronique en question et les entités associées à ce message. Ces entités peuvent inclure des fichiers, des URL et des destinataires.  L’étendue de l’enquête peut augmenter au fur et à mesure que des alertes nouvelles et associées sont déclenchées.

3. Pendant et après une enquête automatisée, des [Détails et des résultats](air-view-investigation-results.md) peuvent être consultés. Les résultats incluent les [actions recommandées](air-remediation-actions.md) qui peuvent être prises pour répondre à des menaces détectées et y remédier. De plus, un [Journal des manifestes](air-view-investigation-results.md#playbook-log) est disponible pour suivre toutes les activités d’enquête.


4. Votre équipe de gestion des opérations de sécurité examine les [résultats de l’enquête](air-view-investigation-results.md), puis [approuve ou rejette les actions correctives](air-review-approve-pending-completed-actions.md). 

5. Comme les actions de correction en attente sont approuvées (ou rejetées), l’enquête automatisée se termine.

> [!IMPORTANT]
> Dans Microsoft Defender pour Office 365, aucune action de correction n’est effectuée automatiquement. Les actions correctives sont mises en œuvre uniquement après approbation par l’équipe de sécurité de votre organisation. Toutefois, les fonctionnalités AIR économisent votre temps d’équipe des opérations de sécurité en identifiant les actions de correction et en fournissant les détails nécessaires pour prendre une décision informée.

Pendant et après chaque enquête automatisée, votre équipe des opérations de sécurité peut :

- [Afficher les détails d’une alerte liée à une enquête](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)

- [Afficher les détails des résultats d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation)

- [Passer en revue et approuver les actions à la suite d’une enquête](air-review-approve-pending-completed-actions.md)

> [!TIP]
> Pour obtenir une vue d’ensemble plus détaillée, voir [How air fonctionne](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office).

## <a name="how-to-get-air"></a>Comment obtenir de l’AIR

Les fonctionnalités AIR sont incluses dans [Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#office-365-atp-plan-1-and-plan-2), à condition que vos stratégies et alertes soient configurées. Si vous souhaitez obtenir de l’aide, suivez les instructions de la rubrique se [protéger contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats) pour configurer ou configurer les paramètres de protection suivants : 

1. [Journalisation d’audit](https://docs.microsoft.com/microsoft-365/compliance/turn-audit-log-search-on-or-off) (doit être activé)

2. [Stratégies contre les programmes malveillants](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?part-1---anti-malware-protection)

3. [Protection anti-hameçonnage](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?part-2---anti-phishing-protection)
   
4. [Protection anti-courrier indésirable](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?part-3---anti-spam-protection).
   
5. [Liens fiables et pièces jointes fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365).
   
6. [Pièces jointes fiables pour SharePoint, OneDrive et Microsoft teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?part-5---verify-atp-for-sharepoint-onedrive-and-microsoft-teams-is-turned-on).
   
7. [Purge automatique à zéro heure pour le courrier électronique](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats?zero-hour-auto-purge-for-email-in-eop).

En outre, veillez à [consulter les stratégies d’alerte de votre organisation](https://docs.microsoft.com/microsoft-365/compliance/alert-policies), en particulier les [stratégies par défaut dans la catégorie gestion des menaces](https://docs.microsoft.com/microsoft-365/compliance/alert-policies?default-alert-policies). 

## <a name="which-alert-policies-trigger-automated-investigations"></a>Quelles stratégies d’alerte déclenchent des enquêtes automatisées ?

Microsoft 365 fournit de nombreuses stratégies d’alerte intégrées qui permettent d’identifier les abus des autorisations d’administration Exchange, l’activité de programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Plusieurs stratégies d' [alerte par défaut](https://docs.microsoft.com/microsoft-365/compliance/alert-policies#default-alert-policies) peuvent déclencher des analyses automatiques. Elles incluent notamment les éléments suivants :

- Un clic d’URL potentiellement malveillant est détecté
- Un message électronique est signalé par un utilisateur comme hameçonnage
- Les messages électroniques contenant des programmes malveillants sont supprimés après la remise
- Les messages électroniques contenant des URL d’hameçonnage sont supprimés après la remise
- Des modèles d’envoi de courrier électronique suspects sont détectés
- Un utilisateur ne peut pas envoyer de courrier électronique

## <a name="required-permissions-to-use-air-capabilities"></a>Autorisations requises pour utiliser les fonctionnalités AIR

Les autorisations sont accordées par le biais de certains rôles, tels que ceux décrits dans le tableau suivant : 

|Tâche |Rôle (s) requis |
|--|--|
|Pour configurer les fonctionnalités AIR |Un des rôles suivants : <br/>-Administrateur général<br/>-Administrateur de la sécurité <br/>Ces rôles peuvent être attribués dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). |
|Pour approuver ou rejeter des actions recommandées|L’un des rôles suivants, affecté dans [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) ou dans le [centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)) :<br/>-Administrateur général <br/>-Administrateur de la sécurité<br/>-Lecteur de sécurité <br/>--- et ---<br/>-Rechercher et purger (ce rôle est affecté uniquement dans le [Centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center). Vous devrez peut-être créer un groupe de rôles à cet emplacement et ajouter le rôle de recherche et de purge à ce nouveau groupe de rôles.)

## <a name="required-licenses"></a>Licences requises

[Les licences Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#office-365-atp-plan-1-and-plan-2) doivent être affectées à :
- Administrateurs de la sécurité (y compris les administrateurs généraux)
- Équipe des opérations de sécurité de votre organisation (y compris les lecteurs de sécurité et les rôles de recherche et de purge)
- Utilisateurs finals


## <a name="next-steps"></a>Étapes suivantes

- [Afficher les détails et les résultats d’une enquête automatisée](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results#view-details-of-an-investigation)

- [Vérifier et approuver les actions en attente](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions)

## <a name="related-articles"></a>Articles connexes

- [Recherche et correction automatisées dans Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Recherche et réponse automatisées dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
