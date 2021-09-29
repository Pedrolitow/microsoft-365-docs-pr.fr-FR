---
title: Vue d’ensemble du tableau de bord de sécurité
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Utilisez le nouveau tableau de bord de sécurité pour passer en revue Office 365 l’état de la protection contre les menaces, et afficher et agir sur les alertes de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0d239ffa2786b23465379de99a3e1ddc6865566f
ms.sourcegitcommit: 4b1bf6e4f4a0c016d148cdde7f7880dd774403d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2021
ms.locfileid: "59988258"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Tableau de bord de sécurité dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Fonctions de base et ouverture du tableau de bord de sécurité

Le Centre de sécurité & conformité permet à votre organisation de gérer la <https://protection.office.com> protection et la conformité des données. En supposant que vous avez les autorisations nécessaires, le tableau de bord de sécurité vous permet de passer en revue votre état de protection contre les menaces, ainsi que d’afficher et d’agir sur les alertes de sécurité.

Regardez la vidéo pour obtenir une vue d’ensemble, puis lisez cet article pour en savoir plus.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

En fonction de ce que comprend l’abonnement de votre organisation, le tableau de bord de sécurité inclut plusieurs widgets, tels que le résumé de la gestion des menaces, l’état de la protection contre les menaces, les détections hebdomadaires globales de menaces, les programmes malveillants, etc., comme décrit dans les sections suivantes.

Pour afficher le tableau de bord de sécurité dans le Centre de sécurité & conformité, consultez le Tableau de bord **de gestion des** \> **menaces.** Pour aller directement au tableau de bord de sécurité, utilisez <https://protection.office.com/searchandinvestigation/dashboard> .

> [!NOTE]
> Vous devez être un administrateur général, un administrateur de sécurité ou un lecteur de sécurité pour afficher le tableau de bord de sécurité. Certains widgets nécessitent des autorisations supplémentaires pour l’affichage. Pour plus d’informations, [voir Autorisations dans](permissions-in-the-security-and-compliance-center.md)le Centre de sécurité & conformité [.

## <a name="threat-management-summary"></a>Résumé de la gestion des menaces

Le widget Résumé de la gestion des menaces vous indique d’un coup d’œil comment votre organisation a été protégée contre les menaces au cours des sept (7) derniers jours.

![Tableau de bord de sécurité : widget résumé de la gestion des menaces.](../../media/SecDash-ThreatMgmtSummary.png)

Les informations que vous verrez dans le résumé de la gestion des menaces dépendent de ce que comprend votre abonnement. Le tableau suivant décrit les informations incluses pour les Office 365 E3 et Office 365 E5.

<br>

****

|Office 365 E3|Office 365 E5|
|---|---|
|Messages de programmes malveillants bloqués<br>Messages de hameçonnage bloqués<br>Messages signalés par les utilisateurs<br><br><br><br>|Messages de programmes malveillants bloqués<br>Messages de hameçonnage bloqués<br>Messages signalés par les utilisateurs<br>Programmes malveillants zero-day bloqués<br>Messages de hameçonnage avancés détectés<br>URL malveillantes bloquées|
|

Pour afficher ou accéder au widget Résumé de la gestion des menaces, vous devez être autorisé à afficher Defender pour Office 365 rapports. Pour en savoir plus, voir [quelles autorisations](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)sont nécessaires pour afficher les rapports defender pour Office 365' .

## <a name="threat-protection-status"></a>État de la protection contre les menaces

Le widget d’état de la protection contre les menaces montre l’efficacité de la protection contre les menaces avec une vue tendance et détaillée du hameçonnage et des programmes malveillants.

![Widget d’état de la protection contre les menaces.](../../media/tpswidget.png)

Les détails varient selon que [](exchange-online-protection-overview.md) votre abonnement Microsoft 365 inclut Exchange Online Protection (EOP) avec ou sans [Microsoft Defender pour Office 365](defender-for-office-365.md).

<br>

****

|Si votre abonnement inclut...|Vous verrez ces détails|
|---|---|
|EOP, mais pas Microsoft Defender pour Office 365|Courrier électronique malveillant détecté et bloqué par EOP.<p> Consultez [le rapport d’état de la protection contre les menaces (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Microsoft Defender pour Office 365|Contenu malveillant et e-mail malveillant détectés et bloqués par EOP et Defender pour Office 365 <p> Nombre agrégé de messages électroniques uniques avec du contenu malveillant bloqué par le moteur [anti-programme](zero-hour-auto-purge.md)malveillant, purge automatique d’heure zéro et fonctionnalités de Defender pour Office 365 (y compris les liens [Coffre,](safe-links.md)les pièces [jointes Coffre](safe-attachments.md)et l’anti-hameçonnage dans [Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> Voir [le rapport d’état de la protection contre les menaces.](view-reports-for-mdo.md#threat-protection-status-report)|
|

Pour afficher ou accéder au widget d’état de la protection contre les menaces, vous devez être autorisé à afficher Defender pour Office 365 rapports. Pour en savoir plus, [voir quelles autorisations](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports) sont nécessaires pour afficher les rapports Defender for Office 365 ?

## <a name="global-weekly-threat-detections"></a>Détections hebdomadaires globales des menaces

Le widget Global Weekly Threat Detections indique le nombre de menaces détectées dans les messages électroniques au cours des sept (7) derniers jours.

![Widget Global Weekly Threat Detections.](../../media/globalweeklythreatdetections.png)

Les mesures sont calculées comme décrit dans le tableau suivant :

<br>

****

|Métrique|Comment il est calculé|
|---|---|
|Messages analysés|Nombre de messages électroniques analysés multiplié par le nombre de destinataires|
|Menaces arrêtées|Nombre de messages électroniques identifiés comme contenant des programmes malveillants multipliés par le nombre de destinataires|
|Bloqué par [Defender pour Office 365](defender-for-office-365.md)|Nombre de messages électroniques bloqués par Defender pour Office 365 multiplié par le nombre de destinataires|
|Supprimé après la remise|Nombre de messages supprimés par purge automatique d’heure zéro [(ZAP)](zero-hour-auto-purge.md) multiplié par le nombre de destinataires|
|

## <a name="malware"></a>Programme malveillant

Les widgets de programmes malveillants montrent des détails sur les tendances des programmes malveillants et les types de famille de programmes malveillants au cours des sept (7) derniers jours.

![Tendances des programmes malveillants et types de famille.](../../media/malwarewidgetatpe5.png)

## <a name="insights"></a>Informations

Informations non seulement les problèmes clés que vous devez examiner, ils incluent également des recommandations et des actions à prendre en compte.

![Informations intelligentes.](../../media/smartinsights.png)

Par exemple, vous pouvez constater que les messages électroniques de hameçonnage sont remis, car certains utilisateurs ont désactivé leurs options de courrier indésirable. Pour en savoir plus sur le fonctionnement des informations, voir Rapports et informations dans le Centre de sécurité [& conformité.](reports-and-insights-in-security-and-compliance.md)

## <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

Si l’abonnement de votre organisation inclut Microsoft Defender pour [Office 365 Plan 2,](office-365-ti.md)votre tableau de bord de sécurité comporte une section qui inclut des outils avancés d’examen et de réponse aux menaces. Ces outils incluent [des fonctionnalités automatisées d’examen et de réponse.](automated-investigation-response-office.md) L’examen et la réponse automatisés peuvent être utiles dans des scénarios tels que la gestion rapide des comptes [d’utilisateur compromis.](address-compromised-users-quickly.md)

Pour plus d’informations, voir [Commencer à utiliser l’investigation automatisée et la réponse (AIR) dans Office 365](office-365-air.md).

## <a name="trends"></a>Tendances

En bas du tableau de bord de sécurité se trouve une section **Tendances,** qui récapitule les tendances de flux de messagerie pour votre organisation. Les rapports fournissent des informations sur les courriers électroniques classés comme courrier indésirable, programmes malveillants, tentatives d’hameçonnage et courrier électronique de qualité. Cliquez sur une vignette pour afficher des informations plus détaillées dans le rapport.

![La section Tendances récapitule les tendances de flux de messagerie pour l’organisation.](../../media/trends.png)

En outre, si l’abonnement de votre organisation inclut [Defender pour Office 365 Plan 2,](office-365-ti.md)vous aurez également un rapport d’alertes de gestion des **menaces récentes** dans cette section qui permet à votre équipe de sécurité d’afficher et d’agir sur les alertes de sécurité prioritaires.

Pour afficher ou accéder au widget Courrier envoyé et reçu, vous devez avoir les autorisations d’afficher Defender pour Office 365 rapports. Pour en savoir plus, voir [quelles autorisations](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)sont nécessaires pour afficher les rapports defender pour Office 365' .

Pour afficher ou accéder au widget Alertes de gestion des menaces récentes, vous devez être autorisé à afficher les alertes. Pour en savoir plus, consultez [les autorisations RBAC requises pour afficher les alertes.](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts)

## <a name="related-articles"></a>Articles connexes

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher des rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md)

[Defender pour Office 365](defender-for-office-365.md)

[Office 365 Examen et réponse contre les menaces](office-365-ti.md)
