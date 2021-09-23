---
title: Afficher les rapports de flux de messagerie dans le tableau de bord Rapports
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les rapports de flux de messagerie disponibles dans le tableau de bord Rapports du Centre de sécurité & conformité.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a049a0d78bff8b86c84e89f616662e00f984c778
ms.sourcegitcommit: 0ed93816e2c1e6620e68bd1c0f00390062911606
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59484130"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Afficher les rapports de flux de messagerie dans le tableau de bord Rapports du Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> La plupart des rapports de cet article sont disponibles dans le portail Microsoft 365 Defender ou le Centre d’administration Exchange (EAC). Pour plus d’informations, voir les rubriques suivantes :
>
> - [Rapports de flux de messagerie dans le nouveau centre Exchange’administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Afficher les rapports de sécurité de messagerie dans le portail Microsoft 365 Defender messagerie](view-email-security-reports.md)

Outre les rapports de flux de [](mail-flow-insights-v2.md) messagerie disponibles dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité, plusieurs rapports de flux de messagerie supplémentaires sont disponibles dans le tableau de bord Rapports pour vous aider à surveiller votre organisation Microsoft 365.

Si vous avez les [autorisations](#what-permissions-are-needed-to-view-these-reports)nécessaires, vous pouvez afficher ces rapports dans le Centre de sécurité [& conformité](https://protection.office.com) en allant au Tableau de bord **des** \> **rapports.** Pour aller directement au tableau de bord Rapports, ouvrez <https://protection.office.com/insightdashboard> .

![Tableau de bord Rapports dans le Centre de sécurité & conformité.](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="connector-report"></a>Rapport sur le connecteur

> [!NOTE]
> Ce rapport a été remplacé par le rapport **Messages** entrants et le rapport **Messages sortants** dans le EAC. Pour plus d’informations, voir messages entrants et rapports de [messages sortants dans le nouveau EAC.](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports)

## <a name="exchange-transport-rule-report"></a>Exchange de règles de transport

Le Exchange de règles de **transport** de messagerie affiche l’effet des règles de flux de messagerie (également appelées règles de transport) sur les messages entrants et sortants dans votre organisation.

Pour afficher le rapport, ouvrez le Centre  de sécurité [& conformité,](https://protection.office.com)allez au tableau de bord rapports et sélectionnez Exchange \>  règle **de transport.** Pour aller directement dans le rapport, ouvrez <https://protection.office.com/reportv2?id=ETRRuleReport> .

![Exchange widget de règle de transport dans le tableau de bord Rapports.](../../media/transport-rule-report-widget.png)

### <a name="report-view-for-the-exchange-transport-rule-report"></a>Affichage du rapport pour le rapport Exchange règles de transport

Les graphiques suivants sont disponibles en affichage état :

- **Afficher les données par : Exchange transport** \> **Décomposer par : Direction**: ce  graphique affiche le nombre de **messages** entrants et sortants affectés par les règles de transport.

- **Afficher les données par : Exchange transport** \> **Décomposez par : Gravité :** ce  graphique affiche le nombre de messages de gravité élevée, moyenne et **faible.** Vous définissez le niveau de gravité en tant qu’action dans la règle (**Auditez** cette règle avec le niveau de gravité _ou SetAuditSeverity_). Pour plus d’informations, voir [Actions de règle de flux](//Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions)de messagerie dans Exchange Online .

- Afficher les données par : règles de transport **Exchange DLP** \> **Décomposer par : Direction**: ce  graphique affiche le nombre de **messages** entrants et sortants affectés par les règles de transport de protection contre la perte de données (DLP). Vous pouvez affiner davantage le graphique en sélectionnant l’une des options suivantes :

  - **Afficher les données pour : toutes les règles de transport DLP**
  - **Afficher les données pour : utilisateurs compromis**
  - **Afficher les données pour : faible volume de contenu détecté pour le Patriot Act des États-Unis**

- **Afficher les données par : règles de transport Exchange DLP** \> **Décomposez par : Direction**: cet  affichage indique le nombre de **messages** de gravité élevée et moyenne **et** faible qui ont été affectés par les règles de transport DLP. Vous pouvez affiner davantage le graphique en sélectionnant l’une des options suivantes :

  - **Afficher les données pour : toutes les règles de transport DLP**
  - **Afficher les données pour : utilisateurs compromis**
  - **Afficher les données pour : faible volume de contenu détecté pour le Patriot Act des États-Unis**

Si vous cliquez **sur Filtres** dans un affichage de rapport, vous pouvez modifier les résultats avec les filtres suivants :

- **Date de début** et **date de fin**
- Valeurs de direction
- Valeurs de gravité

![Affichage du rapport dans le rapport Exchange règle de transport.](../../media/transport-rule-report-report-view.png)

### <a name="details-table-view-for-the-exchange-transport-rule-report"></a>Vue de table Détails pour le rapport Exchange règle de transport

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Afficher les données par : Exchange transport :**

  - **Date**
  - **Règle de transport**
  - **Sujet**
  - **Adresse de l’expéditeur**
  - **Adresse du destinataire**
  - **Gravité**
  - **Direction**

- **Afficher les données par : DLP Exchange de transport**:

  - **Date**
  - **Stratégie DLP**
  - **Règle de transport**
  - **Sujet**
  - **Adresse de l’expéditeur**
  - **Adresse du destinataire**
  - **Gravité**
  - **Direction**

Si vous cliquez **sur Filtres** dans une vue de tableau de détails, vous pouvez modifier les résultats avec les filtres suivants :

- **Date de début** et **date de fin**
- Valeurs de direction
- Valeurs de gravité

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="forwarding-report"></a>Rapport de forwarding

> [!NOTE]
> Le **rapport de forwarding** est désormais disponible dans le EAC. Pour plus d’informations, [reportez-vous au](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report)rapport des messages transmis automatiquement dans le nouveau EAC.

## <a name="mailflow-status-report"></a>Rapport d’état du flux de messagerie

Le **rapport d’état du** flux de messagerie est similaire au rapport de courrier électronique envoyé et reçu, avec des informations supplémentaires sur le courrier électronique autorisé ou bloqué sur le edge. [](#sent-and-received-email-report) Il s’agit du seul rapport qui contient des informations sur la protection edge et qui indique la quantité de messages électroniques bloqués avant d’être autorisé à entrer dans le service pour évaluation par Exchange Online Protection (EOP). Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le compterons comme cinq messages différents et pas un seul message.
Pour afficher le rapport, ouvrez le Centre de  sécurité [& conformité,](https://protection.office.com)puis sélectionnez Tableau de bord rapports et sélectionnez Rapport d’état du \>  flux **de messagerie.** Pour aller directement au rapport d’état du **flux de messagerie,** ouvrez <https://protection.office.com/mailflowStatusReport> .

![Widget de rapport d’état du flux de messagerie dans le tableau de bord Rapports.](../../media/mail-flow-status-report-widget.png)

### <a name="type-view-for-the-mailflow-status-report"></a>Affichage des types pour le rapport d’état du flux de messagerie

Lorsque vous ouvrez l’état, **l’onglet Type** est sélectionné par défaut. Par défaut, cet affichage contient un graphique et une table de données configurés avec les filtres suivants :

- **Date**: 7 derniers jours.
- **Direction**:

  - **Entrant**
  - **Sortant**
  - **Intra-organisation**: ce nombre est pour les messages au sein d’un client, c’est-à-dire sender abc@domain.com sends to recipient xyz@domain.com (counted separately from **Inbound** and **Outbound**)

- **Tapez**:

  - **Bon courrier**
  - **Programme malveillant**
  - **Courrier indésirable**
  - **Protection Edge**
  - **Messages de règle**
  - **Courriers hameçons**

Le graphique est organisé par les valeurs **Type.**

Vous pouvez modifier ces filtres en cliquant sur **Filtre** ou en cliquant sur une valeur dans la légende du graphique.

La table de données contient les informations suivantes :

- **Direction**
- **Type**
- **24 heures**
- **3 jours**
- **7 jours**
- **15 jours**
- **30 jours**

Si vous cliquez **sur Choisir une catégorie pour plus d’informations,** vous pouvez sélectionner l’une des valeurs suivantes :

- **E-mail de hameçonnage**: cette sélection vous place dans le rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
- **Programmes malveillants dans les e-mails**: cette sélection vous place dans le rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
- **Détections de courrier indésirable**: cette sélection vous permet d’envoyer le rapport [détections de courrier indésirable.](view-email-security-reports.md#spam-detections-report)
- **Courrier indésirable bloqué edge**: cette sélection vous permet d’envoyer le rapport [détections de courrier indésirable.](view-email-security-reports.md#spam-detections-report)

**Exporter**:

Pour l’affichage détaillé, vous ne pouvez exporter les données que pour une journée. Par exemple, si vous souhaitez exporter des données pendant 7 jours, vous devez faire 7 actions d’exportation différentes.

Chaque fichier .csv exporté est limité à 150 000 lignes. Si les données de ce jour contiennent plus de 150 000 lignes, plusieurs fichiers .csv seront créés.

![Affichage des types dans le rapport d’état du flux de messagerie.](../../media/mail-flow-status-report-type-view.png)

### <a name="direction-view-for-the-mailflow-status-report"></a>Affichage direction pour le rapport d’état du flux de messagerie

Si vous cliquez sur **l’onglet Direction,** les mêmes filtres par défaut de **l’affichage Type** sont utilisés.

Le graphique est organisé par **valeurs direction.**

Vous pouvez modifier ces filtres en cliquant sur **Filtre** ou en cliquant sur une valeur dans la légende du graphique. Les mêmes filtres de **l’affichage Type** sont utilisés.

La table de données contient les mêmes informations que **l’affichage Type.**

La **sélection d’une catégorie pour plus d’informations** sur les sélections disponibles et le comportement sont identiques à l’affichage **Type.**

**Exporter**:

Pour l’affichage détaillé, vous ne pouvez exporter les données que pour une journée. Par exemple, si vous souhaitez exporter des données pendant 7 jours, vous devez faire 7 actions d’exportation différentes.

Chaque fichier .csv exporté est limité à 150 000 lignes. Si les données de ce jour contiennent plus de 150 000 lignes, plusieurs fichiers .csv seront créés.

![Affichage direction dans le rapport d’état du flux de messagerie.](../../media/mail-flow-status-report-direction-view.png)

### <a name="funnel-view-for-the-mailflow-status-report"></a>Affichage en entonnoir pour le rapport d’état du flux de messagerie

La **vue Entonnoir** vous montre comment les fonctionnalités de protection contre les menaces de courrier électronique de Microsoft filtrent le courrier électronique entrant et sortant dans votre organisation. Il fournit des détails sur le nombre total de messages électroniques et sur la façon dont les fonctionnalités de protection contre les menaces configurées, y compris la protection edge, la protection contre les programmes malveillants, l’anti-hameçonnage, le courrier indésirable et la détection d’usurpation d’accès affectent ce nombre.

Si vous  cliquez sur l’onglet Entonnoir, par défaut, cet affichage contient un graphique et une table de données configurés avec les filtres suivants :

- **Date**: 7 derniers jours.

- **Direction**:

  - **Entrant**
  - **Sortant**
  - **Intra-organisation**: ce nombre est le nombre de messages envoyés au sein d’un client ; Autrement dit, l’expéditeur abc@domain.com envoyé au destinataire xyz@domain.com (comptabilisé séparément des messages entrants et sortants).

L’affichage agrégé et l’affichage de table de données autorisent 90 jours de filtrage.

Si vous cliquez **sur Filtre,** vous pouvez filtrer le graphique et la table de données.

Ce graphique indique le nombre de messages électroniques organisés par :

- **Nombre total de messages électroniques**
- **Courrier électronique après protection edge**
- **Courrier électronique après anti-programme malveillant, réputation du fichier, bloc de type de fichier**
- **Courrier électronique après anti-hameçonnage, réputation d’URL, emprunt d’identité de marque, anti-usurpation d’identité**
- **Courrier électronique après filtrage du courrier indésirable en bloc**
- **Courrier électronique après l’emprunt d’identité d’utilisateur et de**<sup>domaine 1</sup>
- **Email after file and URL detonation**<sup>1</sup>
- **Courrier électronique détecté comme étant anodin après la remise (protection de temps de clic d’URL)**

<sup>1</sup> Defender pour Office 365 uniquement

Pour afficher l’e-mail filtré par EOP ou Defender Office 365 séparément, cliquez sur la valeur dans la légende du graphique.

La table de données contient les informations suivantes, indiquées dans l’ordre décroit de date :

- **Date**
- **Nombre total de messages électroniques**
- **Protection Edge**
- **Anti-programme malveillant, réputation de fichier, bloc de type de fichier**:
  - **Réputation du** fichier : messages filtrés en raison de l’identification d’un fichier joint par d’autres clients Microsoft.
  - **Bloc de type de** fichier : messages filtrés en raison du type de fichier malveillant identifié dans le message.
- **Anti-hameçonnage, réputation de l’URL, emprunt d’identité de marque, anti-usurpation d’identité**:
  - **Réputation de l’URL**: messages filtrés en raison de l’identification de l’URL par d’autres clients Microsoft.
  - **Emprunt d’identité de marque**: messages filtrés en raison du message provenant de la marque connue usurpant l’identité des expéditeurs.
  - **Anti-usurpation**: messages filtrés en raison de la tentative d’usurpation d’un domaine appartenant au destinataire ou d’un domaine que l’expéditeur du message ne possède pas.
- **Anti-courrier indésirable, filtrage du courrier en bloc**:
  - **Filtrage du courrier en nombre**: messages filtrés en raison d’une tentative de remettre des messages en nombre à ses destinataires.
- **Emprunt d’identité d’utilisateur et** de domaine (Defender pour Office 365) :
  - **Emprunt d’identité** d’utilisateur : messages filtrés en raison d’une tentative d’emprunt d’identité d’un utilisateur (expéditeur de message) défini dans les paramètres de protection contre l’emprunt d’identité d’une stratégie anti-hameçonnage.
  - **Emprunt d’identité** de domaine : messages filtrés en raison d’une tentative d’emprunt d’identité d’un domaine défini dans les paramètres de protection contre l’emprunt d’identité d’une stratégie anti-hameçonnage.
- **Détonation de fichier et d’URL (Defender pour Office 365)**:
  - **Détonation de fichier**: messages filtrés par une stratégie Coffre pièces jointes.
  - **Détonation d’URL**: message filtré par une stratégie Coffre liens.
- **Protection post-remise et ZAP (ATP) ou ZAP (EOP)**: ZAP indique une purge automatique de zéro heure.

Si vous sélectionnez une ligne dans la table de données, une répartition supplémentaire du nombre de messages électroniques est affichée dans le volant.

**Exporter**:

Après avoir cliqué **sur Exporter** sous **Options,** vous pouvez sélectionner l’une des valeurs suivantes :

- **Résumé (avec des données pour les 90 derniers jours au maximum)**
- **Détails (avec des données pour les 30 derniers jours au maximum)**

Sous **Date**, choisissez une plage, puis cliquez sur **Appliquer**. Les données des filtres actuels sont exportées vers un .csv de données.

Chaque fichier .csv exporté est limité à 150 000 lignes. Si les données contiennent plus de 150 000 lignes, plusieurs .csv fichiers seront créés.

 ![Affichage en entonnoir dans le rapport d’état du flux de messagerie.](../../media/mail-flow-status-report-funnel-view.png)

### <a name="tech-view-for-the-mailflow-status-report"></a>Affichage technique pour le rapport d’état du flux de messagerie

La **vue Tech est** similaire à la vue Entonnoir, fournissant des détails plus détaillés pour les fonctionnalités de protection contre les menaces configurées.  À partir du graphique, vous pouvez voir comment les messages sont classés aux différentes étapes de la protection contre les menaces.

Si vous cliquez sur **l’onglet Affichage** Technique, par défaut, cet affichage contient un graphique et une table de données configurés avec les filtres suivants :

- **Date**: 7 derniers jours.

- **Direction**:

  - **Entrant**
  - **Sortant**
  - **Intra-organisation**: ce nombre est pour les messages au sein d’un client, c’est-à-dire sender abc@domain.com sends to recipient xyz@domain.com (counted separately from Inbound and Outbound)

L’affichage agrégé et l’affichage de table de données autorisent 90 jours de filtrage.

Si vous cliquez **sur Filtre,** vous pouvez filtrer le graphique et la table de données.

Ce graphique présente les messages organisés dans les catégories suivantes :

- **Nombre total de messages électroniques**
- **Edge autoriser** et **edge filtré**
- **Pas de programmes** **malveillants, Coffre détection des pièces jointes,** détection du moteur <sup>\*</sup> **anti-programme** malveillant et **messages de règle**
- **Pas de hameçonnage,**  **d’échec DMARC,** de détection d’emprunt d’identité, de détection d’usurpation **d’identité** et de **détection d’hameçonnage**
- **Aucune détection avec détection de détonation d’URL** et **de détonation d’URL**<sup>\*</sup>
- **Pas de courrier indésirable** et  **de courrier indésirable**
- **E-mail** non malveillant, **détection Coffre liens et** <sup>\*</sup> **ZAP**

<sup>\*</sup>Defender for Office 365

Lorsque vous pointez sur une catégorie dans le graphique, vous pouvez voir le nombre de messages dans cette catégorie.

La table de données contient les informations suivantes, indiquées dans l’ordre décroit de date :

- **Date**
- **Nombre total de messages électroniques**
- **Edge filtré**
- **Moteur anti-programme malveillant, Coffre pièces jointes, règle filtrée**:
  - **Règle filtrée**: messages filtrés en raison de règles de flux de messagerie (également appelées règles de transport).
- **DMARC, emprunt d’identité, usurpation d’identité, hameçonnage filtré**:
  - **DMARC**: messages filtrés en raison de l’échec de la vérification de l’authentification DMARC.
- **Détection de détonation d’URL**
- **Filtrage anti-courrier indésirable**
- **ZAP supprimé**
- **Détection par liens Coffre de détection**

Si vous sélectionnez une ligne dans la table de données, une répartition supplémentaire du nombre de messages électroniques est affichée dans le volant.

**Exporter**:

En cliquant sur **Exporter,** sous **Options,** vous pouvez sélectionner l’une des valeurs suivantes :

- **Résumé (avec des données pour les 90 derniers jours au maximum)**
- **Détails (avec des données pour les 30 derniers jours au maximum)**

Sous **Date**, choisissez une plage, puis cliquez sur **Appliquer**. Les données des filtres actuels sont exportées vers un .csv de données.

Chaque fichier .csv exporté est limité à 150 000 lignes. Si les données contiennent plus de 150 000 lignes, plusieurs .csv fichiers seront créés.

 ![Affichage technique dans le rapport d’état du flux de messagerie.](../../media/mail-flow-status-report-Tech-view.png)

## <a name="sent-and-received-email-report"></a>Rapport de courrier électronique envoyé et reçu

> [!NOTE]
> Ce rapport a été remplacé par le rapport [d’état du flux de messagerie.](#mailflow-status-report)

## <a name="top-senders-and-recipients-report"></a>Rapport des principaux expéditeurs et destinataires

Le **rapport Des principaux expéditeurs et destinataires** est un graphique en secteurs montrant vos principaux expéditeurs et destinataires de courrier électronique.

Pour afficher le rapport, ouvrez le Centre de  sécurité [& conformité,](https://protection.office.com)puis sélectionnez Tableau de bord rapports et sélectionnez Principaux \>  **expéditeurs et destinataires.** Pour aller directement dans le rapport, ouvrez <https://protection.office.com/reportv2?id=TopSenderRecipientsATP> .

![Widget des principaux expéditeurs et destinataires dans le tableau de bord Rapports.](../../media/top-senders-and-recipients-widget.png)

### <a name="report-view-for-the-top-senders-and-recipient-report"></a>Affichage du rapport pour le rapport des principaux expéditeurs et destinataires

Les graphiques suivants sont disponibles dans l’affichage de rapport :

- **Afficher les données pour \> les principaux expéditeurs de courrier**
- **Afficher les données pour \> les principaux destinataires du courrier**
- **Afficher les données des \> principaux destinataires du courrier indésirable**
- **Afficher les données pour \> Principaux destinataires de programmes malveillants** (EOP)
- **Afficher les données \> des principaux destinataires de programmes malveillants (Defender pour Office 365)**

La composition du graphique en secteurs change en fonction de ces sélections.

Lorsque vous pointez sur une souris dans le graphique en secteurs, vous pouvez voir le nombre de messages envoyés ou reçus.

Si vous cliquez sur **Filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec la **date de** début et la date **de fin.**

![Graphique en secteurs en affichage Rapport dans le rapport Des principaux expéditeurs et destinataires.](../../media/top-senders-and-recipients-report-view.png)

### <a name="details-table-view-for-the-top-senders-and-recipient-report"></a>Vue de table Détails pour le rapport des principaux expéditeurs et destinataires

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Afficher les données pour \> les principaux expéditeurs de courrier**

  - **Principaux expéditeurs de courrier**
  - **Count**

- **Afficher les données pour \> les principaux destinataires du courrier**

  - **Principaux destinataires du courrier**
  - **Count**

- **Afficher les données des \> principaux destinataires du courrier indésirable**

  - **Principaux destinataires du courrier indésirable**
  - **Count**

- **Afficher les données pour \> Principaux destinataires de programmes malveillants** (EOP)

  - **Principaux destinataires de programmes malveillants**
  - **Count**

- **Afficher les données \> des principaux destinataires de programmes malveillants (Defender pour Office 365)**

  - **Principaux destinataires de programmes malveillants (Defender pour Office 365)**
  - **Count**

Si vous cliquez sur **Filtres** dans une vue de tableau de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles autorisations sont nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le Centre de sécurité & conformité :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur de sécurité**
- **Lecteur général**

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>Sujets associés

[Rapports intelligents et aperçus dans le Centre de sécurité et conformité](reports-and-insights-in-security-and-compliance.md)

[Informations sur le flux de messagerie dans le centre de sécurité et conformité](mail-flow-insights-v2.md)

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher des rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md)
