---
title: Actions de correction dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, investigation, réponse, correction, menaces, avancées, menaces, protection
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
description: Découvrez les actions de correction à la suite d’une investigation automatisée dans Microsoft Defender pour Office 365.
ms.date: 04/30/2021
ms.custom:
- air
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: e3a50a2f194c6a82a28082acd8b86fe4b4466301
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630927"
---
# <a name="remediation-actions-in-microsoft-defender-for-office-365"></a>Actions de correction dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="remediation-actions"></a>Actions de correction

Les fonctionnalités de protection contre les menaces dans [Microsoft Defender pour Office 365](defender-for-office-365.md) incluent certaines actions de correction. Ces actions de correction peuvent inclure :

- Supprimer (récupération possible) le courrier ou des clusters
- Bloquer l’URL (heure du clic)
- Désactiver le transfert de courrier externe
- Désactiver la délégation

Dans Microsoft Defender pour Office 365, les actions de correction ne sont pas effectuées automatiquement. Au lieu de cela, les actions de correction sont effectuées uniquement après approbation par l’équipe des opérations de sécurité de votre organisation.

## <a name="threats-and-remediation-actions"></a>Menaces et actions de correction

Microsoft Defender pour Office 365 inclut des actions de correction pour résoudre différentes menaces. Les enquêtes automatisées aboutissent souvent à une ou plusieurs actions de correction à examiner et à approuver. Dans certains cas, une enquête automatisée n’entraîne pas d’action de correction spécifique. Pour examiner et prendre les mesures appropriées, suivez les instructions du tableau suivant.

|Catégorie|Menace/risque|Actions de correction|
|:---|:---|:---|
|E-mail|Programme malveillant|E-mail/cluster de suppression réversible <p> Si plus d’une poignée de messages électroniques dans un cluster contiennent des programmes malveillants, le cluster est considéré comme malveillant.|
|E-mail|URL malveillante <br> (Une URL malveillante a été détectée par [des liens fiables](safe-links.md).)|E-mail/cluster de suppression réversible <br> Bloquer l’URL (vérification au moment du clic) <p> Email qui contient une URL malveillante est considérée comme malveillante.|
|E-mail|Phish|E-mail/cluster de suppression réversible <p> Si plus d’une poignée de messages électroniques dans un cluster contiennent des tentatives de hameçonnage, l’ensemble du cluster est considéré comme une tentative de hameçonnage.|
|E-mail|Hameçonnage zappé <br> (Email messages ont été remis, puis [zappés](zero-hour-auto-purge.md).)|E-mail/cluster de suppression réversible <p> Les rapports sont disponibles pour afficher les messages zappés. [Voir si ZAP a déplacé un message et des FAQ](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message).|
|E-mail|E-mail de hameçonnage [manqué signalé](enable-the-report-message-add-in.md) par un utilisateur|[Investigation automatisée déclenchée par le rapport de l’utilisateur](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|E-mail|Anomalie de volume <br> (Les quantités d’e-mails récentes dépassent les 7 à 10 jours précédents pour les critères correspondants.)|L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p>L’anomalie de volume n’est pas une menace claire, mais elle indique simplement des volumes de courrier plus importants ces derniers jours par rapport aux 7 à 10 derniers jours. <p>Bien qu’un volume élevé d’e-mails puisse indiquer des problèmes potentiels, une confirmation est nécessaire en termes de verdicts malveillants ou de révision manuelle des messages électroniques/clusters. Voir [Rechercher les e-mails suspects qui ont été remis](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered).|
|E-mail|Aucune menace détectée <br> (Le système n’a trouvé aucune menace basée sur les fichiers, les URL ou l’analyse des verdicts de cluster de messagerie.)|L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p>Les menaces détectées et [zappées](zero-hour-auto-purge.md) une fois l’enquête terminée ne sont pas reflétées dans les résultats numériques d’une enquête, mais ces menaces sont visibles dans [l’Explorateur](threat-explorer.md) de menaces.|
|Utilisateur|Un utilisateur a cliqué sur une URL malveillante <br> (Un utilisateur a accédé à une page qui a été jugée malveillante par la suite, ou un utilisateur a contourné une [page d’avertissement Liens fiables](safe-links.md#warning-pages-from-safe-links) pour accéder à une page malveillante.)|L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p> Bloquer l’URL (heure du clic) <p> Utilisez l’Explorateur de [menaces pour afficher des données sur les URL, puis cliquez sur Verdicts](threat-explorer.md#view-phishing-url-and-click-verdict-data). <p> Si votre organisation utilise [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), envisagez [d’examiner l’utilisateur](/microsoft-365/security/defender-endpoint/investigate-user) pour déterminer si son compte est compromis.|
|Utilisateur|Un utilisateur envoie un programme malveillant/hameçonnage|L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p> L’utilisateur peut signaler un programme malveillant ou un hameçonnage, ou une personne peut [usurper l’identité de l’utilisateur dans le](anti-spoofing-protection.md) cadre d’une attaque. Utilisez [l’Explorateur de menaces](threat-explorer.md) pour afficher et gérer les e-mails contenant des [programmes malveillants](threat-explorer-views.md#email--malware) ou [des hameçonnages](threat-explorer-views.md#email--phish).|
|Utilisateur|Transfert de messages électroniques <br> (Les règles de transfert de boîte aux lettres sont configurées, chch peut être utilisé pour l’exfiltration de données.)|Supprimer la règle de transfert <p> Utilisez [des insights sur les flux de courrier](mail-flow-insights-v2.md), y compris le [rapport des messages transférés](mfi-auto-forwarded-messages-report.md) automatiquement, pour afficher des détails plus spécifiques sur les messages transférés.|
|Utilisateur|règles de délégation Email <br> (Les délégations sont configurées sur le compte d’un utilisateur.)|Supprimer la règle de délégation <p> Si votre organisation utilise [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), envisagez [d’examiner l’utilisateur](/microsoft-365/security/defender-endpoint/investigate-user) qui obtient l’autorisation de délégation.|
|Utilisateur|Data exfiltration <br> (Un utilisateur a enfreint les stratégies [DLP](../../compliance/dlp-learn-about-dlp.md) de partage de fichiers ou de courrier électronique |L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p> [Affichez les rapports DLP et prenez des mesures](../../compliance/view-the-dlp-reports.md).|
|Utilisateur|Envoi d’e-mails anormaux <br> (Un utilisateur a récemment envoyé plus d’e-mails qu’au cours des 7 à 10 derniers jours.)|L’investigation automatisée n’entraîne pas d’action en attente spécifique. <p> L’envoi d’un grand volume d’e-mails n’est pas malveillant par lui-même ; l’utilisateur peut simplement avoir envoyé un e-mail à un grand groupe de destinataires pour un événement. Pour effectuer des recherches, utilisez [des insights sur les flux de messagerie](mail-flow-insights-v2.md), y compris le [rapport de mappage de flux de messagerie](mfi-mail-flow-map-report.md) pour déterminer ce qui se passe et prendre des mesures.|

## <a name="next-steps"></a>Prochaines étapes

- [Afficher les détails et les résultats d’une enquête automatisée dans Microsoft Defender pour Office 365](air-view-investigation-results.md)
- [Afficher les actions de correction en attente ou terminées à la suite d’une enquête automatisée dans Microsoft Defender pour Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>Articles connexes

- [En savoir plus sur l’investigation automatisée dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [En savoir plus sur les fonctionnalités de Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
