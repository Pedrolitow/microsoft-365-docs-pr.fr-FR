---
title: Actions de correction suite à une enquête automatisée dans Microsoft Defender pour Office 365
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
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez les actions de correction suite à une enquête automatisée dans Microsoft Defender pour Office 365.
ms.date: 09/29/2020
ms.custom:
- air
ms.openlocfilehash: c178655d60b45e45680a86c3973317e63c354f17
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844535"
---
# <a name="remediation-actions-following-automated-investigation-in-microsoft-defender-for-office-365"></a>Actions de correction suite à une enquête automatisée dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="remediation-actions"></a>Actions de correction

Les fonctionnalités d’analyse [et de réponse automatisées](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) (air) dans [Microsoft defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) incluent certaines actions de correction. Chaque fois qu'un examen automatisé est en cours ou terminé, vous verrez généralement une ou plusieurs mesures correctives nécessitant l'approbation de votre équipe d'opérations de sécurité pour être mises en œuvre. Ces actions de correction peuvent être les suivantes :

- Supprimer (récupération possible) le courrier ou des clusters
- Bloquer l’URL (heure du clic)
- Désactiver le transfert de courrier externe
- Désactiver la délégation

> [!NOTE]
> Dans Microsoft Defender pour Office 365, les analyses automatisées ne génèrent pas de mesures correctives prises automatiquement. Les actions de correction ne sont prises qu’après approbation de l’équipe des opérations de sécurité de votre organisation.

## <a name="threats-and-remediation-actions"></a>Menaces et actions correctives

Le tableau suivant récapitule les menaces et les actions correctives appropriées dans Microsoft Defender pour Office 365. Dans certains cas, une enquête automatisée n’entraîne pas d’action corrective spécifique. Votre équipe des opérations de sécurité peut approfondir et prendre des mesures appropriées, comme décrit dans le tableau ci-dessous.

****

|Catégorie|Menace/risque|Action de correction|
|---|---|---|
|E-mail|Programme malveillant|Suppression logicielle/cluster <br/><br/>Si plus d’un petit nombre de messages électroniques dans un cluster contiennent un programme malveillant, le cluster est considéré comme malveillant.|
|E-mail|URL malveillante<br/>(Une URL malveillante a été détectée par les [liens fiables dans Microsoft Defender pour Office 365](atp-safe-links.md).|Suppression logicielle/cluster <br/><br/>Les messages électroniques qui contiennent une URL malveillante sont considérés comme malveillants.|
|E-mail|Hameçonnage|Suppression logicielle/cluster <br/><br/>Si plus d’un petit nombre de messages électroniques dans un cluster contiennent des tentatives de hameçonnage, le cluster est considéré comme un hameçonnage.|
|E-mail|Hameçonnage zapped <br/>(Les messages électroniques ont été remis et [zapped](https://docs.microsoft.com/microsoft-365/security/office-365-security/zero-hour-auto-purge).)|Suppression logicielle/cluster <br/><br/>Les rapports sont disponibles pour afficher les messages zapped. [Voir si zap a déplacé un message et une FAQ](https://docs.microsoft.com/microsoft-365/security/office-365-security/zero-hour-auto-purge#how-to-see-if-zap-moved-your-message).|
|E-mail|Messages hameçons manqués [signalés](https://docs.microsoft.com/microsoft-365/security/office-365-security/enable-the-report-message-add-in) par un utilisateur|[Enquête automatisée déclenchée par le rapport de l’utilisateur](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|E-mail|Anomalie de volume <br/>(Les quantités d’e-mail récentes dépassent les 7-10 jours précédents pour les critères correspondants.)|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>L’anomalie de volume n’est pas une menace claire, mais il s’agit simplement d’une indication des volumes de courrier plus importants en l’absence de jours récents par rapport aux 7-10 derniers jours. Bien que cela puisse indiquer des problèmes potentiels, la confirmation est nécessaire en cas de verdicts malveillants ou d’une révision manuelle des messages électroniques/clusters. Consultez la rubrique [Rechercher et supprimer les messages suspects qui ont été remis](https://docs.microsoft.com/microsoft-365/security/office-365-security/investigate-malicious-email-that-was-delivered#find-and-delete-suspicious-email-that-was-delivered).|
|E-mail|Aucune menace détectée <br/>(Le système n’a trouvé aucune menace basée sur les fichiers, les URL ou l’analyse des verdicts de cluster de messagerie.)|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>Les menaces détectées et [zapped](https://docs.microsoft.com/microsoft-365/security/office-365-security/zero-hour-auto-purge) une fois qu’une enquête est terminée ne sont pas reflétées dans les résultats numériques de l’enquête, mais elles sont visibles dans l' [Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer).|
|Utilisateur|Un utilisateur a cliqué sur une URL malveillante <br/>(Un utilisateur a accédé à une page qui a été déconseillée par la suite comme malveillante ou un utilisateur a contourné une [page d’avertissement de liens fiables](atp-safe-links.md#warning-pages-from-safe-links) pour accéder à une page malveillante.)|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>Utilisez l’Explorateur de menaces pour [afficher les données sur les URL et cliquez sur verdicts](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer#view-data-about-phishing-urls-and-click-verdict). <br/><br/>Si votre organisation utilise [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/), envisagez de demander à [l’utilisateur](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/investigate-user) de déterminer si son compte est compromis.|
|Utilisateur|Un utilisateur envoie des programmes malveillants/hameçons|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>Il est possible que l’utilisateur signale un programme malveillant ou un hameçonnage, ou que quelqu’un [usurpe l’identité de l’utilisateur dans le](https://docs.microsoft.com/microsoft-365/security/office-365-security/anti-spoofing-protection) cadre d’une attaque. Utilisez l' [Explorateur de menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer) pour afficher et gérer le courrier électronique contenant des [programmes malveillants](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer-views#email--malware) ou des [hameçons](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer-views#email--phish).|
|Utilisateur|Transfert de messages électroniques <br/>(Les règles de transfert des boîtes aux lettres sont configurées, ce qui peut être utilisé pour l’exfiltration des données.)|Supprimer la règle de transfert <br/><br/>Utilisez les informations de [flux de messagerie](https://docs.microsoft.com/microsoft-365/security/office-365-security/mail-flow-insights-v2), y compris le [rapport de messages transférés automatiquement](https://docs.microsoft.com/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report), pour afficher des détails plus spécifiques sur le courrier transféré.|
|Utilisateur|Règles de délégation de courrier électronique <br/>(Le compte d’un utilisateur dispose de la configuration de la délégation.)|Supprimer une règle de délégation <br/><br/> Si votre organisation utilise [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/), envisagez d’examiner [l’utilisateur](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/investigate-user) qui obtient l’autorisation de délégation.|
|Utilisateur|Data exfiltration<br/>(Une utilisateur A enfreint les [stratégies DLP](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)de partage de fichiers ou de messagerie.)|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>[Affichez les rapports DLP et effectuez une action](https://docs.microsoft.com/microsoft-365/compliance/view-the-dlp-reports).|
|Utilisateur|Envoi d’e-mail anormal <br/>(Un utilisateur A récemment envoyé plus de courriers électroniques qu’au cours des 7-10 jours précédents.)|L’analyse automatisée ne donne pas lieu à une action en attente spécifique. <br/><br/>L’envoi d’un grand nombre de messages électroniques n’est pas malveillant par lui-même ; l’utilisateur peut simplement envoyer un message électronique à un grand groupe de destinataires pour un événement. Pour examiner, utilisez les informations d' [accès au flux de messagerie](https://docs.microsoft.com/microsoft-365/security/office-365-security/mail-flow-insights-v2), y compris le rapport de carte de flux de [messagerie](https://docs.microsoft.com/microsoft-365/security/office-365-security/mfi-mail-flow-map-report) pour déterminer ce qui se passe et prendre des mesures.|
|

## <a name="next-steps"></a>Étapes suivantes

- [Afficher les détails et les résultats d’une enquête automatisée dans Microsoft Defender pour Office 365](air-view-investigation-results.md)

- [Afficher les actions de correction en attente ou terminées à la suite d’une enquête automatisée dans Microsoft Defender pour Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>Articles connexes

- [En savoir plus sur l’analyse automatisée pour le point de terminaison de Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [En savoir plus sur les fonctionnalités supplémentaires dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection)
