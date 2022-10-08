---
title: Vue d’ensemble du tableau de bord de sécurité
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Utilisez le nouveau tableau de bord de sécurité pour passer en revue Office 365 état de la protection contre les menaces, et afficher et agir sur les alertes de sécurité.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: f417c64329b0a8e276e34e65520b56f7d788171b
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67853971"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>Tableau de bord de sécurité dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="basic-functions-and-how-to-open-security-dashboard"></a>Fonctions de base et comment ouvrir le tableau de bord Sécurité

Le Centre de sécurité & conformité permet à <https://protection.office.com> votre organisation de gérer la protection et la conformité des données. En supposant que vous disposez des autorisations nécessaires, le tableau de bord de sécurité vous permet de passer en revue votre état de protection contre les menaces, ainsi que d’afficher et d’agir sur les alertes de sécurité.

Regardez la vidéo pour obtenir une vue d’ensemble, puis lisez cet article pour en savoir plus.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

En fonction de l’abonnement de votre organisation, le tableau de bord de sécurité inclut plusieurs widgets, tels que le résumé de la gestion des menaces, l’état de la protection contre les menaces, les détections de menaces hebdomadaires globales, les programmes malveillants et bien plus encore, comme décrit dans les sections suivantes.

Pour afficher le tableau de bord de sécurité dans le Centre de sécurité & conformité, accédez au tableau **de bord de gestion des** \> **menaces**. Pour accéder directement au tableau de bord Sécurité, utilisez <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> Vous devez être un administrateur général, un administrateur de sécurité ou un lecteur de sécurité pour afficher le tableau de bord de sécurité. Certains widgets nécessitent des autorisations supplémentaires pour l’affichage. Pour plus d’informations, consultez [Autorisations dans le Centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>Résumé de la gestion des menaces

Le widget Récapitulatif de la gestion des menaces vous indique en un clin d’œil comment votre organisation a été protégée contre les menaces au cours des sept (7) derniers jours.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="Tableau de bord de sécurité - Widget Récapitulatif de la gestion des menaces" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

Les informations que vous verrez dans le résumé de la gestion des menaces dépendent de ce que votre abonnement inclut. Le tableau suivant décrit les informations incluses pour Office 365 E3 et Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|Messages de programmes malveillants bloqués<br>Messages d’hameçonnage bloqués<br>Messages signalés par les utilisateurs<br><br><br><br>|Messages de programmes malveillants bloqués<br>Messages d’hameçonnage bloqués<br>Messages signalés par les utilisateurs<br>Programmes malveillants zero-day bloqués<br>Messages de hameçonnage avancés détectés<br>URL malveillantes bloquées|

Pour afficher ou accéder au widget Récapitulatif de la gestion des menaces, vous devez disposer des autorisations nécessaires pour afficher Defender pour Office 365 rapports. Pour en savoir plus, consultez [quelles autorisations sont nécessaires pour afficher les rapports Defender pour Office 365 ?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="threat-protection-status"></a>État de la protection contre les menaces

Le widget État de la protection contre les menaces affiche l’efficacité de la protection contre les menaces avec une vue tendance et détaillée du hameçonnage et des programmes malveillants.

:::image type="content" source="../../media/tpswidget.png" alt-text="Widget d’état de la protection contre les menaces" lightbox="../../media/tpswidget.png":::

Les détails varient selon que votre abonnement Microsoft 365 inclut [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) avec ou sans [Microsoft Defender pour Office 365](defender-for-office-365.md).

|Si votre abonnement inclut...|Vous verrez ces détails|
|---|---|
|EOP mais pas Microsoft Defender pour Office 365|E-mail malveillant détecté et bloqué par EOP.<p> Consultez le [rapport d’état de la protection contre les menaces (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Microsoft Defender pour Office 365|Contenu malveillant et e-mail malveillant détecté et bloqué par EOP et Defender pour Office 365 <p> Nombre agrégé de messages électroniques uniques avec contenu malveillant bloqué par le moteur anti-programme malveillant, [vidage automatique de zéro heure](zero-hour-auto-purge.md) et fonctionnalités de Defender pour Office 365 (y compris [les liens sécurisés](safe-links.md), [les pièces jointes sécurisées](safe-attachments.md) et [l’anti-hameçonnage dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> Consultez le [rapport d’état de la protection contre les menaces](view-reports-for-mdo.md#threat-protection-status-report).|

Pour afficher ou accéder au widget État de la protection contre les menaces, vous devez disposer des autorisations nécessaires pour afficher Defender pour Office 365 rapports. Pour en savoir plus, consultez [Quelles sont les autorisations nécessaires pour afficher les rapports Defender pour Office 365 ?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>Détections de menaces hebdomadaires globales

Le widget Détections de menaces hebdomadaires globales indique le nombre de menaces détectées dans les messages électroniques au cours des sept (7) derniers jours.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="Widget Détections de menaces hebdomadaires globales" lightbox="../../media/globalweeklythreatdetections.png":::

Les métriques sont calculées comme décrit dans le tableau suivant :

|Métrique|Mode de calcul|
|---|---|
|Messages analysés|Nombre d’e-mails analysés multiplié par le nombre de destinataires|
|Menaces arrêtées|Nombre de messages électroniques identifiés comme contenant des programmes malveillants multipliés par le nombre de destinataires|
|Bloqué par [Defender pour Office 365](defender-for-office-365.md)|Nombre d’e-mails bloqués par Defender pour Office 365 multiplié par le nombre de destinataires|
|Supprimé après la remise|Nombre de messages supprimés par [vidage automatique de zéro heure (ZAP)](zero-hour-auto-purge.md) multiplié par le nombre de destinataires|

## <a name="malware"></a>Programme malveillant

Les widgets de programmes malveillants affichent des détails sur les tendances des programmes malveillants et les types de familles de programmes malveillants au cours des sept (7) derniers jours.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="Tendances des programmes malveillants et types de famille" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Informations

Insights non seulement présente les principaux problèmes que vous devez examiner, mais inclut également des recommandations et des actions à prendre en compte.

:::image type="content" source="../../media/smartinsights.png" alt-text="Les insights intelligents" lightbox="../../media/smartinsights.png":::

Par exemple, vous pouvez voir que des messages électroniques de hameçonnage sont remis, car certains utilisateurs ont désactivé leurs options de courrier indésirable. Pour en savoir plus sur le fonctionnement des insights, consultez [Rapports et insights dans le Centre de sécurité & conformité](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>Examen et réponse contre les menaces

Si l’abonnement de votre organisation inclut [Microsoft Defender pour Office 365 plan 2](office-365-ti.md), votre tableau de bord de sécurité comporte une section qui inclut des outils avancés d’investigation et de réponse aux menaces. Ces outils incluent des [fonctionnalités d’investigation et de réponse automatisées](automated-investigation-response-office.md). L’examen et la réponse automatisés peuvent être utiles dans des scénarios tels que [l’adressage rapide des comptes d’utilisateur compromis](address-compromised-users-quickly.md).

Pour plus d’informations, consultez [Prise en main de l’investigation et de la réponse automatisées (AIR) dans Office 365](office-365-air.md).

## <a name="trends"></a>Tendances

En bas du tableau de bord de sécurité se trouve une section **Tendances** , qui récapitule les tendances de flux de courrier pour votre organisation. Les rapports fournissent des informations sur les courriers électroniques classés comme courrier indésirable, programmes malveillants, tentatives de hameçonnage et courrier électronique approprié. Cliquez sur une vignette pour afficher des informations plus détaillées dans le rapport.

:::image type="content" source="../../media/trends.png" alt-text="Section Tendances qui récapitule les tendances de flux de courrier pour l’organisation" lightbox="../../media/trends.png":::

De plus, si l’abonnement de votre organisation inclut [Defender pour Office 365 plan 2](office-365-ti.md), vous disposez également d’un rapport **d’alertes de gestion des menaces récents** dans cette section qui permet à votre équipe de sécurité d’afficher et d’agir sur les alertes de sécurité haute priorité.

Pour afficher ou accéder au widget Envoyé et Reçu Email, vous devez disposer des autorisations nécessaires pour afficher Defender pour Office 365 rapports. Pour en savoir plus, consultez [quelles autorisations sont nécessaires pour afficher les rapports Defender pour Office 365 ?](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

Pour afficher ou accéder au widget Alertes de gestion des menaces récentes, vous devez disposer des autorisations nécessaires pour afficher les alertes. Pour plus d’informations, consultez [les autorisations RBAC requises pour afficher les alertes](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>Articles connexes

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher les rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md)

[Defender pour Office 365](defender-for-office-365.md)

[Office 365 investigation et réponse aux menaces](office-365-ti.md)
