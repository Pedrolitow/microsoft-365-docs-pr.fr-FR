---
title: Fonctionnement de l’investigation et de la réponse automatisées dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
- m365initiative-defender-office365
keywords: réponse automatisée aux incidents, investigation, correction, protection contre les menaces
ms.date: 01/29/2021
description: Découvrez comment fonctionnent les fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: cb99c8938aac9b0cb8a721db7c23bd0396866819
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625080"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Fonctionnement de l’investigation et de la réponse automatisées dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

À mesure que les alertes de sécurité sont déclenchées, c’est à votre équipe des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. Parfois, les équipes d’opérations de sécurité peuvent se sentir submergées par le volume d’alertes déclenchées. Les fonctionnalités d’investigation et de réponse automatisées (AIR) dans Microsoft Defender pour Office 365 peuvent vous aider.

AIR permet à votre équipe des opérations de sécurité de fonctionner plus efficacement et plus efficacement. Les fonctionnalités AIR incluent des processus d’investigation automatisés en réponse aux menaces connues qui existent aujourd’hui. Les actions de correction appropriées attendent l’approbation, ce qui permet à votre équipe des opérations de sécurité de répondre aux menaces détectées.

Cet article décrit le fonctionnement d’AIR à l’aide de plusieurs exemples. Lorsque vous êtes prêt à commencer à utiliser AIR, consultez [Examiner automatiquement les menaces et y répondre](office-365-air.md).

- [Exemple 1 : Un message de hameçonnage signalé par l’utilisateur lance un playbook d’investigation](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Exemple 2 : Un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Exemple 3 : Une équipe des opérations de sécurité intègre AIR à son SIEM à l’aide de l’API d’activité de gestion Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Exemple : Un message de hameçonnage signalé par l’utilisateur lance un playbook d’investigation

Supposons qu’un utilisateur de votre organisation reçoive un e-mail qu’il considère comme une tentative de hameçonnage. L’utilisateur, formé pour signaler ces messages, utilise le [complément Message](enable-the-report-message-add-in.md) de rapport ou le [complément Report Phishing](enable-the-report-phish-add-in.md) pour l’envoyer à Microsoft à des fins d’analyse. La soumission est également envoyée à votre système et est visible dans l’Explorateur dans la vue **Soumissions** (anciennement appelée vue **signalée par l’utilisateur** ). En outre, le message signalé par l’utilisateur déclenche désormais une alerte d’information basée sur le système, qui lance automatiquement le playbook d’investigation.

Au cours de la phase d’investigation racine, différents aspects de l’e-mail sont évalués. Ces aspects sont les suivants :

- Détermination du type de menace qu’elle pourrait être;
- Qui l’a envoyé;
- Où l’e-mail a été envoyé (infrastructure d’envoi) ;
- Indique si d’autres instances de l’e-mail ont été remises ou bloquées ;
- Une évaluation de nos analystes;
- Indique si l’e-mail est associé à des campagnes connues ;
- et bien plus encore.

Une fois l’examen racine terminé, le playbook fournit une liste des actions recommandées à effectuer sur l’e-mail d’origine et les entités qui lui sont associées.

Ensuite, plusieurs étapes d’investigation et de chasse des menaces sont exécutées :

- Des messages électroniques similaires sont identifiés par le biais de recherches de cluster de messagerie.
- Le signal est partagé avec d’autres plateformes, telles que [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Vous déterminez si des utilisateurs ont cliqué sur des liens malveillants dans des messages électroniques suspects.
- Une vérification est effectuée sur Exchange Online Protection ([EOP](exchange-online-protection-overview.md) et ([Microsoft Defender pour Office 365](defender-for-office-365.md) pour voir s’il existe d’autres messages similaires signalés par les utilisateurs.
- Une vérification est effectuée pour voir si un utilisateur a été compromis. Cette vérification tire parti des signaux entre Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) et [Azure Active Directory](/azure/active-directory), en éloquant toutes les anomalies d’activité utilisateur associées.

Pendant la phase de chasse, les risques et les menaces sont affectés à différentes étapes de chasse.

La correction est la dernière phase du playbook. Au cours de cette phase, les étapes de correction sont effectuées en fonction des phases d’investigation et de chasse.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Exemple : Un administrateur de sécurité déclenche une enquête à partir de l’Explorateur de menaces

En plus des enquêtes automatisées déclenchées par une alerte, l’équipe des opérations de sécurité de votre organisation peut déclencher une enquête automatisée à partir d’une vue dans [l’Explorateur de menaces](threat-explorer.md). Cette enquête crée également une alerte, de sorte que Microsoft 365 Defender incidents et les outils SIEM externes peuvent voir que cette enquête a été déclenchée.

Par exemple, supposons que vous utilisez la vue **Programmes malveillants** dans l’Explorateur. À l’aide des onglets situés sous le graphique, vous sélectionnez l’onglet **Email**. Si vous sélectionnez un ou plusieurs éléments dans la liste, le bouton **+ Actions** s’active.

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="L’Explorateur avec les messages sélectionnés" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::

À l’aide du menu **Actions** , vous pouvez sélectionner **Déclencher l’investigation**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Menu Actions pour les messages sélectionnés" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

À l’instar des playbooks déclenchés par une alerte, les investigations automatiques déclenchées à partir d’une vue dans l’Explorateur incluent une investigation racine, des étapes pour identifier et mettre en corrélation les menaces, ainsi que des actions recommandées pour atténuer ces menaces.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Exemple : Une équipe des opérations de sécurité intègre AIR à son SIEM à l’aide de l’API d’activité de gestion Office 365

Les fonctionnalités AIR de Microsoft Defender pour Office 365 incluent [des rapports & des détails que les équipes des opérations](air-view-investigation-results.md) de sécurité peuvent utiliser pour surveiller et traiter les menaces. Mais vous pouvez également intégrer des fonctionnalités AIR à d’autres solutions. Par exemple, un système SIEM (Security Information and Event Management), un système de gestion de cas ou une solution de création de rapports personnalisée. Ces types d’intégrations peuvent être effectués à l’aide de [l’API d’activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

Par exemple, récemment, une organisation a configuré un moyen pour son équipe chargée des opérations de sécurité d’afficher les alertes de hameçonnage signalées par l’utilisateur qui ont déjà été traitées par AIR. Leur solution intègre les alertes pertinentes au serveur SIEM de l’organisation et à son système de gestion des cas. La solution réduit considérablement le nombre de faux positifs afin que leur équipe des opérations de sécurité puisse concentrer son temps et ses efforts sur les menaces réelles. Pour en savoir plus sur cette solution personnalisée, consultez [le blog Tech Community : Améliorer l’efficacité de votre SOC avec Microsoft Defender pour Office 365 et l’API de gestion O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Prochaines étapes

- [Prise en main d’AIR](office-365-air.md)
- [Afficher les actions de correction en attente ou terminées](air-review-approve-pending-completed-actions.md)
