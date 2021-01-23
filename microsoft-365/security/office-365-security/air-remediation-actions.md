---
title: Actions de correction suite à un examen automatisé dans Microsoft Defender pour Office 365
keywords: AIR, autoIR, ATP, automatisé, examen, réponse, correction, menaces, avancé, menace, protection
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
description: Découvrez les actions de correction à la suite d’un examen automatisé dans Microsoft Defender pour Office 365.
ms.date: 01/21/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 39032cb187b2654b6ae03c048e706afb665a8761
ms.sourcegitcommit: ba830e85899f247e5a1e117d63e09e4d5b8a8020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49939306"
---
# <a name="remediation-actions-following-automated-investigation-in-microsoft-defender-for-office-365"></a>Actions de correction suite à un examen automatisé dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="remediation-actions"></a>Actions de correction

[Les fonctionnalités d’investigation](office-365-air.md) et de réponse automatisées (AIR) dans [Microsoft Defender pour Office 365](office-365-atp.md) incluent certaines actions de correction. Chaque fois qu'un examen automatisé est en cours ou terminé, vous verrez généralement une ou plusieurs mesures correctives nécessitant l'approbation de votre équipe d'opérations de sécurité pour être mises en œuvre. Ces actions de correction peuvent inclure :

- Supprimer (récupération possible) le courrier ou des clusters
- Bloquer l’URL (heure du clic)
- Désactiver le transfert de courrier externe
- Désactiver la délégation

> [!NOTE]
> Dans Microsoft Defender pour Office 365, les enquêtes automatisées n’entraînent pas de mesures correctives prises automatiquement. Les mesures correctives ne sont prises qu’après approbation par l’équipe des opérations de sécurité de votre organisation.

## <a name="threats-and-remediation-actions"></a>Menaces et actions de correction

Le tableau de cette section récapitule les menaces et les actions de correction appropriées dans Microsoft Defender pour Office 365. Dans certains cas, un examen automatisé ne donne pas lieu à une action de correction spécifique. Votre équipe des opérations de sécurité peut examiner plus en détail et prendre les mesures appropriées comme décrit dans le tableau ci-dessous.

|Catégorie|Menace/risque|Action de correction|
|:---|:---|:---|
|E-mail|Programme malveillant|Suppression de courrier électronique/cluster de suppression (soft delete email/cluster) <br> Si plusieurs messages électroniques d’un cluster contiennent des programmes malveillants, le cluster est considéré comme malveillant.|
|E-mail|URL malveillante <br> (Une URL malveillante a été détectée par des [liens sécurisés dans Microsoft Defender pour Office 365](atp-safe-links.md)).|Suppression de courrier électronique/cluster de suppression (soft delete email/cluster) <p> Les messages électroniques contenant une URL malveillante sont considérés comme malveillants.|
|E-mail|Hameçonnage|Suppression de courrier électronique/cluster de suppression (soft delete email/cluster) <br> Si plusieurs messages électroniques d’un cluster contiennent des tentatives de hameçonnage, le cluster est considéré comme un hameçonnage.|
|E-mail|Hameçonnage par hameçonnage <br> (Les messages électroniques ont été remis et [envoyés.)](zero-hour-auto-purge.md)|Suppression de courrier électronique/cluster de suppression (soft delete email/cluster) <p> Les rapports sont disponibles pour afficher les messages reçus. [Voir si ZAP a déplacé un message et des FAQ.](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message)|
|E-mail|Courrier de hameçonnage manqué [signalé](enable-the-report-message-add-in.md) par un utilisateur|[Enquête automatisée déclenchée par le rapport de l’utilisateur](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|E-mail|Anomalie de volume <br> (Les quantités de courriers électroniques récentes dépassent les 7 à 10 jours précédents pour les critères correspondants.)|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> L’anomalie de volume n’est pas une menace évidente, mais indique simplement un volume de courrier plus important au cours des derniers jours par rapport aux 7 à 10 derniers jours. Bien que des anomalies de volume peuvent indiquer des problèmes potentiels, une confirmation est nécessaire en termes de verdicts malveillants ou d’un examen manuel des messages électroniques/clusters. Consultez [Rechercher les messages suspects qui ont été remis.](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered)|
|E-mail|Aucune menace détectée <br> (Le système n’a trouvé aucune menace basée sur les fichiers, les URL ou l’analyse des verdicts de cluster de messagerie.)|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> Les menaces trouvées [et trouvées](zero-hour-auto-purge.md) une fois l’enquête terminée ne sont pas reflétées dans les résultats numériques d’un examen, mais ces menaces sont consultables dans l’Explorateur [de menaces.](threat-explorer.md)|
|Utilisateur|Un utilisateur a cliqué sur une URL malveillante <br> (Un utilisateur a accédé à une page qui a été ultérieurement trouvée comme malveillante, ou un utilisateur a contourné une [page](atp-safe-links.md#warning-pages-from-safe-links) d’avertissement de liens sécurisés pour accéder à une page malveillante.)|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> Utilisez l’Explorateur de [menaces pour afficher les données sur les URL et cliquer sur les verdicts.](threat-explorer.md#view-phishing-url-and-click-verdict-data) <p> Si votre organisation utilise Microsoft Defender [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/investigate-user) [pour le](https://docs.microsoft.com/windows/security/threat-protection/)point de terminaison, envisagez d’examiner l’utilisateur pour déterminer si son compte est compromis.|
|Utilisateur|Un utilisateur envoie un programme malveillant/hameçonnage|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> L’utilisateur peut signaler des programmes malveillants/hameçonnages, ou une personne peut [usurper](anti-spoofing-protection.md) l’utilisateur dans le cadre d’une attaque. Utilisez [l’Explorateur de menaces](threat-explorer.md) pour afficher et gérer les e-mails contenant des [programmes malveillants](threat-explorer-views.md#email--malware) ou du [hameçonnage.](threat-explorer-views.md#email--phish)|
|Utilisateur|Transfert de messages électroniques <br> (Les règles de forwarding de boîtes aux lettres sont configurées et peuvent être utilisées pour l’exfiltration des données.)|Supprimer la règle de forwarding <p> Utilisez [les informations sur le flux de](mail-flow-insights-v2.md)messagerie, y compris le rapport des messages [auto-envoyés,](mfi-auto-forwarded-messages-report.md)pour afficher des détails plus spécifiques sur le courrier électronique transmis.|
|Utilisateur|Règles de délégation de messagerie <br> (La délégation est définie sur le compte d’un utilisateur.)|Supprimer une règle de délégation <p> Si votre organisation utilise Microsoft Defender [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/investigate-user) [pour le](https://docs.microsoft.com/windows/security/threat-protection/)point de terminaison, envisagez d’examiner l’utilisateur qui a obtenu l’autorisation de délégation.|
|Utilisateur|Data exfiltration <br> (Un utilisateur a enfreint des stratégies DLP de partage de [fichiers ou de courrier électronique.)](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies)|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> [Afficher les rapports DLP et prendre des mesures.](https://docs.microsoft.com/microsoft-365/compliance/view-the-dlp-reports)|
|Utilisateur|Envoi de messages électroniques anormal <br> (Un utilisateur a récemment envoyé plus de messages électroniques qu’au cours des 7 à 10 jours précédents.)|L’examen automatisé ne donne pas lieu à une action en attente spécifique. <p> L’envoi d’un grand volume de messages électroniques n’est pas malveillant en soi ; L’utilisateur a peut-être simplement envoyé un courrier électronique à un grand groupe de destinataires pour un événement. Pour examiner, utilisez les informations [](mfi-mail-flow-map-report.md) sur le [flux](mail-flow-insights-v2.md)de messagerie, y compris le rapport de carte de flux de messagerie pour déterminer ce qui se passe et prendre des mesures.|
|

## <a name="next-steps"></a>Étapes suivantes

- [Afficher les détails et les résultats d’une enquête automatisée dans Microsoft Defender pour Office 365](air-view-investigation-results.md)

- [Afficher les actions de correction en attente ou terminées suite à un examen automatisé dans Microsoft Defender pour Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>Articles connexes

- [En savoir plus sur l’examen automatisé dans Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [En savoir plus sur les fonctionnalités de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection)
