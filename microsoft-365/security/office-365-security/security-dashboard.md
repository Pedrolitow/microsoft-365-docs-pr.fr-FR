---
title: Vue d’ensemble du tableau de bord de sécurité
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Utilisez le nouveau tableau de bord de sécurité pour consulter l’état de protection contre les menaces d’Office 365, et afficher et agir sur les alertes de sécurité.
ms.openlocfilehash: f7576de9db1403c3c010b2fd826866ec11a7e20a
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843623"
---
# <a name="security-dashboard"></a>Tableau de bord de sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Fonctions de base et comment ouvrir le tableau de bord de sécurité

Le [Centre de sécurité & conformité](../../compliance/go-to-the-securitycompliance-center.md) permet à votre organisation de gérer la protection et la conformité des données. En supposant que vous disposez des autorisations nécessaires, le tableau de bord de sécurité vous permet d’examiner votre statut de protection contre les menaces, ainsi que d’afficher et d’agir sur les alertes de sécurité.

Regardez la vidéo pour obtenir une vue d’ensemble, puis lisez cet article pour en savoir plus.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

En fonction de l’abonnement de votre organisation, le tableau de bord de sécurité inclut plusieurs widgets, tels que le résumé de la gestion des menaces, l’état de protection contre les menaces, des détections de menaces globales hebdomadaires, des programmes malveillants, etc., comme décrit dans les sections suivantes.

Pour afficher le tableau de bord sécurité, dans le [Centre de sécurité & conformité](../../compliance/go-to-the-securitycompliance-center.md), accédez au tableau de bord **gestion des menaces** \> **Dashboard**.

> [!NOTE]
> Vous devez être un administrateur général, un administrateur de sécurité ou un lecteur de sécurité pour afficher le tableau de bord de sécurité. Certains widgets nécessitent des autorisations supplémentaires pour être visualisées. Pour en savoir plus, consultez [la rubrique autorisations dans le centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="threat-management-summary"></a>Résumé de la gestion des menaces

Le widget gestion des menaces explique en un clin d’œil comment votre organisation a été protégée contre les menaces au cours des sept (7) derniers jours.

![Tableau de bord de sécurité-widget gestion des menaces-Résumé](../../media/SecDash-ThreatMgmtSummary.png)

Les informations que vous verrez dans le résumé de gestion des menaces dépendent de ce que comprend l’abonnement. Le tableau suivant décrit les informations incluses pour Office 365 E3 et Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Messages malveillants bloqués<br/>Messages d’hameçonnage bloqués<br>Messages signalés par les utilisateurs<br><br><br><br>|Messages malveillants bloqués<br>Messages d’hameçonnage bloqués<br>Messages signalés par les utilisateurs<br>Blocage des programmes malveillants de jour zéro<br>Messages d’hameçonnage avancés détectés<br>URL malveillantes bloquées|

Pour afficher ou accéder au widget Résumé de la gestion des menaces, vous devez disposer des autorisations permettant d’afficher les rapports Defender pour Office 365. Pour en savoir plus, consultez [la rubrique Quelles autorisations sont nécessaires pour afficher les rapports Defender pour Office 365 ?](view-reports-for-atp.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>Statut de protection contre les menaces

Le widget état de protection contre les menaces indique l’efficacité de la protection contre les menaces avec une vue d’ensemble des tendances et programmes malveillants.

![Widget d’état de protection contre les menaces](../../media/tpswidget.png)

Les détails varient selon que votre abonnement Microsoft 365 inclut ou non [Exchange Online Protection](exchange-online-protection-overview.md) (EoP) avec ou sans [Microsoft defender pour Office 365](office-365-atp.md).

|Si votre abonnement inclut...|Ces détails s’affichent.|
|---|---|
|EOP mais pas Microsoft Defender pour Office 365|Courrier électronique malveillant détecté et bloqué par EOP.<br><br> Consultez la rubrique [Threat Protection Status Report (EoP)](view-email-security-reports.md#threat-protection-status-report).|
|Microsoft Defender pour Office 365|Contenu malveillant et courrier involontaire détecté et bloqué par EOP et Defender pour Office 365<br><br>Nombre agrégé de messages électroniques uniques dont le contenu malveillant est bloqué par le moteur anti-programme malveillant, la [purge automatique à zéro heure](zero-hour-auto-purge.md)et les fonctionnalités Defender pour Office 365 (y compris les [liens approuvés](atp-safe-links.md), [les pièces jointes fiables](atp-safe-attachments.md)et la [protection anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).<br><br>Consultez la rubrique [Threat Protection Status Report](view-reports-for-atp.md#threat-protection-status-report).|

Pour afficher ou accéder au widget d’État protection contre les menaces, vous devez disposer des autorisations permettant d’afficher les rapports Defender pour Office 365. Pour en savoir plus, consultez [la rubrique Quelles autorisations sont requises pour afficher les rapports Defender pour Office 365 ?](view-reports-for-atp.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Détections de menaces hebdomadaires globales

Le widget détections de menaces globales hebdomadaires indique le nombre de menaces détectées dans les messages électroniques au cours des sept (7) derniers jours.

![Widget de détections de menaces hebdomadaires globales](../../media/globalweeklythreatdetections.png)

Les mesures sont calculées de la manière décrite dans le tableau suivant :

|Métrique|Mode de calcul|
|---|---|
|Messages analysés|Nombre de messages électroniques analysés multiplié par le nombre de destinataires|
|Menaces arrêtées|Nombre de messages électroniques identifiés comme contenant des programmes malveillants multiplié par le nombre de destinataires|
|Bloqué par [Defender pour Office 365 ](office-365-atp.md)|Nombre de messages électroniques bloqués par Defender pour Office 365 multiplié par le nombre de destinataires|
|Supprimés après la remise|Nombre de messages supprimés par [purge automatique 0 heure](zero-hour-auto-purge.md) multiplié par le nombre de destinataires|

## <a name="malware"></a>Programme malveillant

Les widgets de programmes malveillants affichent des informations sur les tendances des programmes malveillants et les types de familles de programmes malveillants au cours des sept derniers jours.

![Tendances des programmes malveillants et types de famille](../../media/malwarewidgetatpe5.png)

## <a name="insights"></a>Informations

Insights non seulement les problèmes de clés de surface que vous devez examiner, ils incluent également des recommandations et des actions à prendre en considération.

![Informations intelligentes](../../media/smartinsights.png)

Par exemple, vous pouvez constater que les messages électroniques de hameçonnage sont remis car certains utilisateurs ont désactivé leurs options de courrier indésirable. Pour en savoir plus sur le fonctionnement des informations, reportez-vous à [la rubrique rapports et informations dans le centre de sécurité & conformité](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

Si l’abonnement de votre organisation inclut  [Microsoft Defender pour Office 365 plan 2](office-365-ti.md), votre tableau de bord de sécurité comporte une section qui inclut des outils d’enquête et de réponse de menace avancés. Ces outils incluent [des fonctionnalités d’analyse et de réponse automatisées](automated-investigation-response-office.md). L’analyse et la réponse automatisées peuvent être utiles dans des scénarios tels que l' [adressage rapide des comptes d’utilisateurs compromis](address-compromised-users-quickly.md).

Pour en savoir plus, consultez la rubrique [prise en main de l’enquête et de la réponse automatisées (air) dans Office 365](office-365-air.md).

## <a name="trends"></a>Tendances

Dans la partie inférieure du tableau de bord de sécurité se trouve une section **tendances** , qui récapitule les tendances de flux de messagerie pour votre organisation. Les rapports fournissent des informations sur les e-mails catégorisés comme courrier indésirable, programmes malveillants, tentatives de hameçonnage et courrier électronique. Cliquez sur une vignette pour afficher des informations plus détaillées dans le rapport.

![La section tendances récapitule les tendances de flux de messagerie de l’organisation.](../../media/trends.png)

De plus, si l’abonnement de votre organisation inclut [Defender pour Office 365 plan 2](office-365-ti.md), vous aurez également un rapport **alertes de gestion des menaces récentes** dans cette section qui permet à votre équipe de sécurité d’afficher et de prendre des mesures concernant les alertes de sécurité à priorité élevée.

Pour afficher ou accéder au widget courrier électronique envoyé et reçu, vous devez disposer des autorisations permettant d’afficher les rapports Defender pour Office 365. Pour en savoir plus, consultez [la rubrique Quelles autorisations sont nécessaires pour afficher les rapports Defender pour Office 365 ?](view-reports-for-atp.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

Pour afficher ou accéder au widget alertes de gestion des menaces récentes, vous devez disposer des autorisations pour afficher les alertes. Pour en savoir plus, consultez la rubrique [autorisations RBAC requises pour afficher les alertes](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-topics"></a>Voir aussi

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher les rapports pour Microsoft Defender pour Office 365](view-reports-for-atp.md)

[Defender pour Office 365](office-365-atp.md)

[Enquête et réponse aux menaces Office 365](office-365-ti.md)
