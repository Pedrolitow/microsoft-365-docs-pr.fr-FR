---
title: Examiner les incidents de perte de données avec Microsoft 365 Defender
description: Examinez la perte de données dans Microsoft 365 Defender.
keywords: Protection contre la perte de données, incidents, alertes, examiner, analyser, répondre, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
f1.keywords:
- NOCSH
ms.service: microsoft-365-security
ms.subservice: m365d
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- met150
ms.openlocfilehash: c4ce493800506d619a5dbcbee955dfd1f40e4615
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67710431"
---
# <a name="investigate-data-loss-incidents-with-microsoft-365-defender"></a>Examiner les incidents de perte de données avec Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Les incidents pour Protection contre la perte de données Microsoft Purview (DLP) peuvent désormais être gérés dans le portail Microsoft 365 Defender. Vous pouvez gérer les incidents DLP ainsi que les incidents de sécurité des **incidents & les incidents** \> **d’alertes** lors du lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. À partir de cette page, vous pouvez :

- Affichez toutes vos alertes DLP regroupées sous des incidents dans la file d’attente d’incidents Microsoft 365 Defender.
- Affichez les alertes corrélées entre solutions intelligentes (DLP-MDE, DLP-MDO) et intra-solution (DLP-DLP) sous un seul incident.
- Recherchez les journaux de conformité ainsi que la sécurité sous Repérage avancé.
- Actions de correction de l’administrateur sur place sur l’utilisateur, le fichier et l’appareil. 
- Associez des balises personnalisées à des incidents DLP et filtrez-les.
- Filtrez par nom de stratégie DLP, étiquette, date, source de service, état d’incident et utilisateur dans la file d’attente d’incidents unifiée. 

Vous pouvez également utiliser le connecteur Microsoft 365 Defender dans Microsoft Sentinel pour extraire des incidents DLP, ainsi que des événements et des preuves dans Microsoft Sentinel à des fins d’investigation et de correction.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Pour examiner Protection contre la perte de données Microsoft Purview incidents dans le portail Microsoft 365 Defender, vous avez besoin d’une licence de l’un des abonnements suivants : 

- Microsoft Office 365 E5/A5
- Microsoft 365 E5/A5
- Conformité Microsoft 365 E5/A5
- Microsoft 365 sécurité E5/A5
- Microsoft 365 E5/A5 Protection de l’information et Gouvernance

> [!NOTE] 
> Lorsque vous disposez d’une licence et que vous êtes éligible à cette fonctionnalité, les alertes DLP sont automatiquement transmises dans Microsoft 365 Defender. Ouvrez un cas de support si vous souhaitez désactiver cette fonctionnalité. 

## <a name="dlp-investigation-experience-in-the-microsoft-365-defender-portal"></a>Expérience d’investigation DLP dans le portail Microsoft 365 Defender

Avant de commencer, [activez les alertes pour toutes vos stratégies DLP](/microsoft-365/compliance/dlp-configure-view-alerts-policies#alert-configuration-experience) dans le <a href="https://purview.microsoft.com" target="_blank">portail de conformité Microsoft Purview</a>.

1. Accédez au portail Microsoft 365 Defender, puis sélectionnez **Incidents** dans le menu de navigation de gauche pour ouvrir la page Incidents.

2. Sélectionnez **Filtres** en haut à droite, puis choisissez **Source de service : Protection contre la perte de données** pour afficher tous les incidents avec des alertes DLP.

3. Recherchez le nom de stratégie DLP des alertes et des incidents qui vous intéressent.

4. Pour afficher la page récapitulative de l’incident, sélectionnez l’incident dans la file d’attente. De même, sélectionnez l’alerte pour afficher la page d’alerte DLP.

5. Consultez **l’article d’alerte** pour plus d’informations sur la stratégie et les types d’informations sensibles détectés dans l’alerte. Sélectionnez l’événement dans la section **Événements connexes** pour afficher les détails de l’activité utilisateur.

6. Affichez le contenu sensible correspondant dans l’onglet **Types d’informations sensibles** et le contenu du fichier sous l’onglet **Source** si vous disposez de l’autorisation requise (voir les détails <a href="/microsoft-365/compliance/dlp-alerts-dashboard-get-started#roles" target="_blank">ici</a>).

7. Vous pouvez également utiliser La chasse avancée pour effectuer des recherches dans les journaux d’audit des utilisateurs, des fichiers et des emplacements de site pour votre investigation. La table **CloudAppEvents** contient tous les journaux d’audit de tous les emplacements tels que SharePoint, OneDrive, Exchange et Appareils.

8. Vous pouvez également télécharger l’e-mail en sélectionnant **Actions** \> **Télécharger l’e-mail**. 

9. Pour les actions de correction sur des fichiers sur des sites SPO ou ODB, vous pouvez voir des actions telles que :

    - Appliquer une étiquette de rétention
    - Appliquer une étiquette de confidentialité
    - Annuler le partage de fichiers
    - Supprimer

   Pour les actions de correction, sélectionnez la **carte utilisateur** en haut de la page d’alerte pour ouvrir les détails de l’utilisateur.

   Pour les alertes DLP des appareils, sélectionnez la carte d’appareil en haut de la page d’alerte pour afficher les détails de l’appareil et effectuer des actions de correction sur l’appareil.

10. Accédez à la page récapitulative des incidents et sélectionnez **Gérer l’incident** pour ajouter des balises d’incident, affecter ou résoudre un incident.

## <a name="dlp-investigation-experience-in-microsoft-sentinel"></a>Expérience d’investigation DLP dans Microsoft Sentinel

Vous pouvez utiliser le connecteur Microsoft 365 Defender dans Microsoft Sentinel pour importer tous les incidents DLP dans Sentinel afin d’étendre votre corrélation, votre détection et votre investigation à d’autres sources de données et d’étendre vos flux d’orchestration automatisés à l’aide des fonctionnalités SOAR natives de Sentinel. 

1. Suivez les instructions sur la connexion des données de Microsoft 365 Defender à Microsoft Sentinel pour importer tous les incidents, y compris les incidents DLP et les alertes dans Sentinel. Activez le `CloudAppEvents` connecteur d’événements pour extraire tous les journaux d’audit O365 dans Sentinel.

   Vous devriez être en mesure de voir vos incidents DLP dans Sentinel une fois le connecteur ci-dessus configuré.

2. Sélectionnez **Alertes** pour afficher la page d’alerte.

3. Vous pouvez utiliser **AlertType**, **startTime** et **endTime** pour interroger la table **CloudAppEvents** afin d’obtenir toutes les activités utilisateur qui ont contribué à l’alerte. Utilisez cette requête pour identifier les activités sous-jacentes :

```kusto
let Alert = SecurityAlert
| where TimeGenerated > ago(30d)
| where SystemAlertId == ""; // insert the systemAlertID here
CloudAppEvents
| extend correlationId1 = parse_json(tostring(RawEventData.Data)).cid
| extend correlationId = tostring(correlationId1)
| join kind=inner Alert on $left.correlationId == $right.AlertType
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)
