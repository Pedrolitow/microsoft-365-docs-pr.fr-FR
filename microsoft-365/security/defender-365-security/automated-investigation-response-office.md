---
title: Fonctionnement de l’examen et de la réponse automatisés dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: réponse automatisée aux incidents, examen, correction, protection contre les menaces
ms.date: 01/29/2021
description: Découvrez le fonctionnement des fonctionnalités d’examen et de réponse automatisées dans Microsoft Defender pour Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e377927156e8c98d07f4527bca09e3764bed3f74
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065462"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Fonctionnement de l’examen et de la réponse automatisés dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Lorsque des alertes de sécurité sont déclenchées, c’est à votre équipe des opérations de sécurité d’examiner ces alertes et de prendre les mesures nécessaires pour protéger votre organisation. Parfois, les équipes en matière d’opérations de sécurité peuvent se sentir submergées par le volume d’alertes déclenchées. Les fonctionnalités d’investigation et de réponse automatisées (AIR) dans Microsoft Defender pour Office 365 peuvent vous aider.

AIR permet à votre équipe des opérations de sécurité de fonctionner plus efficacement. Les fonctionnalités AIR incluent des processus d’examen automatisés en réponse aux menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre aux menaces détectées.

Cet article décrit le fonctionnement d’AIR à travers plusieurs exemples. Lorsque vous êtes prêt à commencer à utiliser AIR, consultez Automatiquement examiner et [répondre aux menaces.](office-365-air.md)

- [Exemple 1 : un message de hameçonnage signalé par l’utilisateur lance un manuel d’enquête](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Exemple 2 : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Exemple 3 : une équipe en charge des opérations de sécurité intègre AIR à son SIEM à l’aide de l’API Activité de gestion Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : un message d’hameçonnage signalé par l’utilisateur lance un manuel d’enquête

Supposons qu’un utilisateur de votre organisation reçoit un e-mail qu’il pense être une tentative de hameçonnage. L’utilisateur, formé pour signaler ces messages, utilise le [add-in Report Message](enable-the-report-message-add-in.md) ou le [add-in Report Phishing](enable-the-report-phish-add-in.md) pour l’envoyer à Microsoft pour analyse. La soumission est également envoyée à votre système et est visible dans l’Explorateur dans l’affichage **Soumissions** (anciennement appelé affichage signalé par **l’utilisateur).** En outre, le message signalé par l’utilisateur déclenche désormais une alerte informationnelle basée sur le système, qui lance automatiquement le manuel d’enquête.

Au cours de la phase d’examen racine, différents aspects du courrier électronique sont évalués. Ces aspects sont les suivants :

- Une détermination du type de menace qu’il peut être ;
- Qui l’a envoyé ;
- L’endroit d’où le courrier électronique a été envoyé (infrastructure d’envoi) ;
- Si d’autres instances du courrier électronique ont été remis ou bloqués ;
- Une évaluation de nos analystes ;
- Si l’e-mail est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’examen racine terminé, le manuel fournit la liste des actions recommandées à effectuer sur le courrier électronique d’origine et les entités qui lui sont associées.

Ensuite, plusieurs étapes d’examen et de recherche des menaces sont exécutées :

- Des messages électroniques similaires sont identifiés via des recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles [que Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- Il est déterminé si des utilisateurs ont cliqué sur des liens malveillants dans des messages électroniques suspects.
- Une vérification est effectuée dans Exchange Online Protection[(EOP)](exchange-online-protection-overview.md)et ([Microsoft Defender pour Office 365](defender-for-office-365.md)) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est effectuée pour voir si un utilisateur a été compromis. Cette vérification exploite les signaux dans Office 365, [Microsoft Cloud App Security](/cloud-app-security)et Azure Active [Directory,](/azure/active-directory)en corrélant les anomalies liées à l’activité des utilisateurs.

Pendant la phase de chasse, les risques et les menaces sont affectés à différentes étapes de recherche.

La correction est la phase finale du manuel. Au cours de cette phase, des mesures correctives sont prises, en fonction des phases d’examen et de recherche.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

Outre les enquêtes automatisées déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatisée à partir d’une vue dans [l’Explorateur de menaces.](threat-explorer.md)  Cette enquête crée également une alerte, afin que les incidents Microsoft Defender et les outils SIEM externes peuvent voir que cette enquête a été déclenchée.

Par exemple, supposons que vous utilisez la vue **Programmes** malveillants dans l’Explorateur. En utilisant les onglets sous le graphique, sélectionnez **l’onglet Courrier** électronique. Si vous sélectionnez un ou plusieurs éléments dans la liste, le **bouton + Actions** s’active.

![Explorateur avec des messages sélectionnés](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

À **l’aide du** menu Actions, vous pouvez sélectionner **Examen déclencheur.**

![Menu Actions pour les messages sélectionnés](../../media/explorer-malwareview-selectedemails-actions.jpg)

Comme pour les playbooks déclenchés par une alerte, les enquêtes automatiques déclenchées à partir d’un affichage dans l’Explorateur incluent un examen racine, des étapes pour identifier et corréler les menaces, ainsi que des actions recommandées pour atténuer ces menaces.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Exemple : une équipe des opérations de sécurité intègre AIR à son SIEM à l’aide de l’API Activité de gestion Office 365

Les fonctionnalités AIR de Microsoft Defender pour Office 365 incluent des rapports & détails que les équipes des [opérations](air-view-investigation-results.md) de sécurité peuvent utiliser pour surveiller et traiter les menaces. Toutefois, vous pouvez également intégrer des fonctionnalités AIR à d’autres solutions. Il peut s’agir par exemple d’un système de gestion des événements et des informations de sécurité (SIEM), d’un système de gestion des cas ou d’une solution de création de rapports personnalisée. Ces types d’intégrations peuvent être effectués à l’aide de l’API Activité de gestion [Office 365.](/office/office-365-management-api/office-365-management-activity-api-reference)

Par exemple, récemment, une organisation a mis en place un moyen pour son équipe des opérations de sécurité d’afficher les alertes de hameçonnage signalées par l’utilisateur qui ont déjà été traitées par AIR. Sa solution intègre des alertes pertinentes au serveur SIEM de l’organisation et à son système de gestion des cas. La solution réduit considérablement le nombre de faux positifs afin que l’équipe des opérations de sécurité puisse concentrer son temps et ses efforts sur les menaces réelles. Pour en savoir plus sur cette solution personnalisée, consultez le blog de la communauté technique : Améliorer l’efficacité de votre SOC avec Microsoft Defender pour Office 365 et l’API de gestion [O365.](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185)

## <a name="next-steps"></a>Étapes suivantes

- [Commencer à utiliser AIR](office-365-air.md)
- [Afficher les actions de correction en attente ou terminées](air-review-approve-pending-completed-actions.md)