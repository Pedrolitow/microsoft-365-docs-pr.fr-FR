---
title: Fonctionnement de l’analyse et de la réponse automatiques dans Microsoft Defender pour Office 365
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
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: réponse automatique aux incidents, investigation, correction, protection contre les menaces
ms.date: 11/05/2020
description: Découvrez comment fonctionnent les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Defender pour Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.openlocfilehash: bbc51201f9d96744ed5bc236516158a75f7af272
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615227"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Fonctionnement de l’analyse et de la réponse automatiques dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

À mesure que des alertes de sécurité sont déclenchées, c’est à votre équipe chargée des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. Parfois, les équipes d’opérations de sécurité peuvent être submergées par le volume des alertes déclenchées. Les fonctionnalités d’analyse et de réponse automatisées de Microsoft Defender pour Office 365 peuvent vous aider.

AIR permet à votre équipe des opérations de sécurité de fonctionner de manière plus efficace. Les fonctionnalités AIR incluent des processus d’enquête automatisés en réponse à des menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre aux menaces détectées.

Cet article explique comment AIR passe par plusieurs exemples. Lorsque vous êtes prêt à commencer à utiliser AIR, consultez la rubrique [enquêter et répondre aux menaces de manière automatique](office-365-air.md).

- [Exemple 1 : un message hameçon signalé par un utilisateur lance un manuel d’enquête.](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Exemple 2 : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Exemple 3 : une équipe d’opérations de sécurité intègre AIR avec sa SIEM à l’aide de l’API activité de gestion d’Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : un message hameçon signalé par un utilisateur lance un manuel d’enquête.

Supposons qu’un utilisateur de votre organisation reçoit un message indiquant qu’il s’agit d’une tentative de hameçonnage. L’utilisateur, formé pour signaler de tels messages, utilise le [complément de message de rapport](enable-the-report-message-add-in.md) pour l’envoyer à Microsoft pour analyse. L’envoi est également envoyé à votre système et est visible dans l’Explorateur dans l’affichage des **soumissions** (anciennement appelé vue **signalée** par l’utilisateur). En outre, le message signalée par l’utilisateur déclenche désormais une alerte d’information basée sur le système, qui lance automatiquement le manuel d’enquête.

Lors de la phase d’enquête de racine, différents aspects du courrier électronique sont évalués. Ces aspects sont les suivants :

- Détermination du type de menace susceptible de se présenter ;
- Expéditeur ;
- Emplacement d’envoi du courrier électronique (infrastructure émettrice);
- Si d’autres instances du courrier électronique ont été remises ou bloquées ;
- Une évaluation de nos analystes ;
- Si le courrier électronique est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’enquête terminée, le manuel fournit une liste des actions recommandées à effectuer sur le courrier électronique d’origine et les entités qui lui sont associées.

Ensuite, plusieurs étapes d’enquête sur les menaces et de chasse sont exécutées :

- Les messages électroniques similaires sont identifiés par des recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles que [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Une détermination est effectuée sur le fait que les utilisateurs aient cliqué sur les liens malveillants dans les messages électroniques suspects.
- Une vérification est effectuée sur Exchange Online Protection ([EOP](exchange-online-protection-overview.md)) et ([Microsoft defender pour Office 365](office-365-atp.md)) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est exécutée pour déterminer si un utilisateur a été compromis. Cette vérification exploite les signaux entre Office 365, [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security)et [Azure Active Directory](https://docs.microsoft.com/azure/active-directory), en mettant en corrélation les anomalies d’activité de l’utilisateur associées.

Au cours de la phase de chasse, les risques et les menaces sont affectés à différentes étapes de la chasse.

La correction est la phase finale du manuel. Pendant cette phase, les étapes de correction sont prises, en fonction des phases d’enquête et de chasse.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

En plus des recherches automatisées déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatisée à partir d’une vue dans l' [Explorateur de menaces](threat-explorer.md).  Cette enquête crée également une alerte, de sorte que les incidents de Microsoft Defender et les outils SIEM externes puissent voir que cette enquête a été déclenchée.

Par exemple, supposons que vous utilisiez l’affichage **programme malveillant** dans l’Explorateur. À l’aide des onglets situés sous le graphique, sélectionnez l’onglet **courrier électronique** . Si vous sélectionnez un ou plusieurs éléments dans la liste, le bouton **+ actions** est activé.

![Explorateur avec des messages sélectionnés](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

Dans le menu **actions** , vous pouvez sélectionner l' **enquête du déclencheur**.

![Menu actions pour les messages sélectionnés](../../media/explorer-malwareview-selectedemails-actions.jpg)

À l’instar des règles déclenchées par une alerte, les recherches automatiques déclenchées à partir d’une vue dans l’Explorateur incluent une enquête de racine, des étapes permettant d’identifier et de corréler les menaces, ainsi que les actions recommandées pour atténuer ces menaces.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Exemple : une équipe d’opérations de sécurité intègre AIR avec sa SIEM à l’aide de l’API activité de gestion d’Office 365

Les fonctionnalités AIR de Microsoft Defender pour Office 365 incluent des [rapports & les détails](air-view-investigation-results.md) que les équipes des opérations de sécurité peuvent utiliser pour surveiller et résoudre les menaces. Toutefois, vous pouvez également intégrer les fonctionnalités AIR à d’autres solutions. Les exemples incluent un système de gestion des événements et des informations de sécurité (SIEM), un système de gestion des cas ou une solution de création de rapports personnalisée. Ces types d’intégration peuvent être effectués à l’aide de l' [API activité de gestion d’Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).

Par exemple, une organisation a récemment mis en place un moyen pour l’équipe des opérations de sécurité d’afficher les alertes de hameçonnage signalées par l’utilisateur et déjà traitées par AIR. Leur solution intègre les alertes appropriées avec le serveur SIEM de l’organisation et son système de gestion de la casse. La solution réduit considérablement le nombre de faux positifs afin que l’équipe des opérations de sécurité puisse concentrer leur temps et leur efforts sur des menaces réelles. Pour en savoir plus sur cette solution personnalisée, consultez [le blog de la communauté technique : améliorer l’efficacité de votre SOC avec Microsoft Defender pour Office 365 et l’API de gestion d’Office 365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Étapes suivantes

- [Prise en main de l’utilisation de l’AIR](office-365-air.md)

- [Consultez la feuille de route Microsoft 365 pour voir ce qui est planifié et publié bientôt](https://www.microsoft.com/microsoft-365/roadmap?filters=)

- [En savoir plus sur les fonctionnalités d’analyse et de réponse automatisées dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
