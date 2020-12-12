---
title: Afficher les rapports de flux de messagerie dans le tableau de bord rapports
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les rapports de flux de messagerie disponibles dans le tableau de bord des rapports dans le centre de sécurité & conformité.
ms.custom: ''
ms.openlocfilehash: 1ededf2d0d693c537c159c52d00deb03f278b4b2
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659464"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Afficher les rapports de flux de messagerie dans le tableau de bord rapports du centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


En plus des rapports de flux de messagerie disponibles dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de sécurité & conformité, un grand nombre de rapports de flux de messagerie supplémentaires sont disponibles dans le tableau de bord rapports pour vous aider à surveiller votre organisation Microsoft 365.

Si vous disposez des [autorisations nécessaires](#what-permissions-are-needed-to-view-these-reports), vous pouvez afficher ces rapports dans le [Centre de sécurité & conformité](https://office.protection.com) en accédant au tableau de  \> **bord** rapports. Pour accéder directement au tableau de bord rapports, ouvrez <https://protection.office.com/insightdashboard> .

![Tableau de bord des rapports dans le centre de sécurité & conformité](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="connector-report"></a>Rapport de connecteur

Le **rapport de connecteur** affiche l’activité de flux de messagerie sur les connecteurs entrants [et sortants](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) configurés pour votre organisation.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez  au \> **tableau de bord** rapports et sélectionnez rapport de **connecteur**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=ConnectorReport> .

![Widget rapport de connecteur dans le tableau de bord rapports](../../media/connector-report-widget.png)

### <a name="report-view-for-the-connector-report"></a>Affichage de rapport pour le rapport de connecteur

Les graphiques suivants sont disponibles en mode état :

- **Afficher les données par : flux de messagerie**: ce graphique indique le nombre de messages entrants et sortants organisés par :

  - **Total**
  - **À partir d’Internet sans connecteur**
  - **Sur Internet sans connecteur**
  - Un connecteur spécifique que vous avez configuré.

  Pour isoler les données du graphique, utilisez l’option **afficher les données pour** le contrôle pour sélectionner une de ces options ou **tout le flux de messagerie**.

  ![Afficher les données par flux de messagerie dans le rapport du connecteur](../../media/connector-report-view-data-by-mail-flow.png)

- **Afficher les données par : utilisation de TLS**: ce graphique indique le pourcentage d’utilisation de la version TLS (Transport Layer Security) pour le flux de messagerie.

  Pour isoler les données dans le graphique, utilisez l’option **afficher les données pour** le contrôle afin de sélectionner l’une des options suivantes :

  - **Tout le flux de messagerie**
  - **À partir d’Internet sans connecteur**
  - **Sur Internet sans connecteur**
  - Un connecteur spécifique que vous avez configuré.

  ![Afficher les données par utilisation de TLS dans le rapport de connecteur](../../media/connector-report-view-data-by-tls-usage.png)

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

### <a name="details-table-view-for-the-connector-report"></a>Vue de la table Détails pour le rapport de connecteur

Si vous cliquez sur **afficher la table des détails** dans un affichage de rapport, les informations suivantes s’affichent :

- **Date**
- **Nom et direction du connecteur**
- **Type de connecteur**
- **TLS forcé ?**: valeur **true** ou **false**.
- **Pas de TLS** (pourcentage)
- **TLS 1,0** (pourcentage)
- **TLS 1,1** (pourcentage)
- **TLS 1,2** (pourcentage)
- **Volume**: nombre de messages.

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Pour revenir à l’affichage de rapport, cliquez sur **afficher le rapport**.

## <a name="exchange-transport-rule-report"></a>Rapport de règle de transport Exchange

Le rapport des règles de **transport Exchange** affiche l’effet des règles de flux de messagerie (également appelées règles de transport) sur les messages entrants et sortants dans votre organisation.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez  au \> **tableau de bord** rapports et sélectionnez **règle de transport Exchange**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=ETRRuleReport> .

![Widget règle de transport Exchange dans le tableau de bord rapports](../../media/transport-rule-report-widget.png)

### <a name="report-view-for-the-exchange-transport-rule-report"></a>Affichage de rapport pour le rapport des règles de transport Exchange

Les graphiques suivants sont disponibles en mode état :

- **Afficher les données par : règles** \> de transport Exchange **Décomposer en : sens**: ce graphique indique le **nombre de messages entrants** et **sortants** affectés par les règles de transport.

- **Afficher les données par : règles** \> de transport Exchange Dépanner **par : gravité**: ce graphique indique le nombre de messages de gravité **élevée** et de gravité **moyenne**, ainsi que les messages à **faible gravité** . Vous définissez le niveau de gravité en tant qu’action dans la règle (**auditez cette règle avec le niveau de gravité** ou _SetAuditSeverity_). Pour plus d’informations, consultez la rubrique [actions de règle de flux de messagerie dans Exchange Online](https://docs.microsoft.com//Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **Afficher les données par : DLP Exchange transport Rules** \> **Décomposer en : sens**: ce graphique indique le **nombre de messages entrants** et **sortants** affectés par les règles de transport de la protection contre la perte de données (DLP). Vous pouvez affiner le graphique en sélectionnant l’une des options suivantes :

  - **Afficher les données pour : toutes les règles de transport DLP**
  - **Afficher les données de : utilisateurs compromis**
  - **Afficher les données pour : faible volume de contenu détecté par les États-Unis Patriot Act**

- **Afficher les données par : DLP Exchange transport Rules** \> **Décomposer en : sens**: cette vue indique le nombre de messages de gravité **élevée** et de gravité **moyenne**, ainsi que les messages à **faible gravité** qui ont été affectés par les règles de transport DLP. Vous pouvez affiner le graphique en sélectionnant l’une des options suivantes :

  - **Afficher les données pour : toutes les règles de transport DLP**
  - **Afficher les données de : utilisateurs compromis**
  - **Afficher les données pour : faible volume de contenu détecté par les États-Unis Patriot Act**

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez modifier les résultats à l’aide des filtres suivants :

- **Date de début** et **Date de fin**
- Valeurs de la direction
- Valeurs de gravité

![Affichage de rapport dans le rapport des règles de transport Exchange](../../media/transport-rule-report-report-view.png)

### <a name="details-table-view-for-the-exchange-transport-rule-report"></a>Vue de la table Détails pour le rapport des règles de transport Exchange

Si vous cliquez sur **afficher les détails table**, les informations affichées dépendent du graphique que vous examinez :

- **Afficher les données par : règles de transport Exchange**:

  - **Date**
  - **Règle de transport**
  - **Subject**
  - **Adresse de l’expéditeur**
  - **Adresse du destinataire**
  - **Gravité**
  - **Direction**

- **Afficher les données par : DLP Exchange transport Rules**:

  - **Date**
  - **Stratégie DLP**
  - **Règle de transport**
  - **Subject**
  - **Adresse de l’expéditeur**
  - **Adresse du destinataire**
  - **Gravité**
  - **Direction**

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez modifier les résultats à l’aide des filtres suivants :

- **Date de début** et **Date de fin**
- Valeurs de la direction
- Valeurs de gravité

Pour revenir à l’affichage de rapport, cliquez sur **afficher le rapport**.

## <a name="forwarding-report"></a>Rapport de transfert

Le **rapport de transfert** indique que les messages envoyés par votre organisation sont transférés automatiquement vers des domaines externes à partir de boîtes aux lettres Exchange Online. Les messages transférés peuvent présenter un risque de sécurité ou de conformité, et peuvent indiquer un compte compromis.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), cliquez sur **rapports** de \> **tableau de bord** et sélectionnez rapport de **transfert**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=MailFlowForwarding> .

![Widget rapport de transfert dans le tableau de bord rapports](../../media/forwarding-report-widget.png)

### <a name="report-view-for-the-forwarding-report"></a>Affichage de rapport pour le rapport de transfert

Les graphiques suivants sont disponibles dans l’affichage rapport :

- **Afficher les données pour : méthodes de transfert**: les méthodes suivantes sont affichées :

  - **Règle de transport**: également appelée [règles de flux de messagerie](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).
  - **Règle de boîte aux lettres**: également appelée règles de boîte de [réception](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59).

  ![Vue des méthodes de transfert dans le rapport de transfert](../../media/forwarding-report-forwarding-methods.png)

- **Afficher les données pour : transferts de domaines**: cette vue affiche les domaines de destinataire qui sont les destinations pour le transfert.

  ![Vue des domaines de transfert dans le rapport de transfert](../../media/forwarding-report-forwarding-domains.png)

- **Afficher les données : redirecteurs**: les redirecteurs suivants sont affichés :

  - **Règle de transport**
  - Boîte aux lettres qui contient la règle de boîte de réception de transfert.

  ![Vue redirecteurs dans le rapport de transfert](../../media/forwarding-report-forwarders.png)

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

### <a name="details-table-view-for-the-forwarding-report"></a>Vue de la table Détails pour le rapport de transfert

Si vous cliquez sur **afficher la table des détails** dans un affichage de rapport, les informations suivantes s’affichent :

- **Redirecteurs**: la **règle de transport** value ou la boîte aux lettres qui contient la règle de boîte de réception de transfert.
- **Type de transfert**: règle de la **boîte aux lettres** ou **règle de transport**.
- **Nom du destinataire**
- **Domaine du destinataire**
- **Détails**: il s’agit de la valeur GUID de la règle de flux de messagerie ou de la valeur RuleIdentity de la règle de boîte de réception.
- **Count**
- **Première date de transfert**

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="mailflow-status-report"></a>Rapport d’état de flux de flux

Le **rapport d’état de flux** de messagerie est similaire au [rapport de courrier électronique envoyé et reçu](#sent-and-received-email-report), avec des informations supplémentaires sur le courrier électronique autorisé ou bloqué sur le serveur Edge. Il s’agit du seul rapport qui contient les informations de protection du serveur Edge et indique le nombre de messages bloqués avant d’être autorisés dans le service pour l’évaluation par Exchange Online Protection (EOP). Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le dénombrez cinq messages différents et pas un message.
Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez  au \> **tableau de bord** rapports et sélectionnez rapport d’État du **flux de flux**. Pour accéder directement au **rapport d’État du flux de messagerie**, ouvrez <https://protection.office.com/mailflowStatusReport> .

![Widget rapport d’état de flux de notification dans le tableau de bord rapports](../../media/mail-flow-status-report-widget.png)

### <a name="type-view-for-the-mailflow-status-report"></a>Vue type pour le rapport d’état de flux de flux

Lorsque vous ouvrez le rapport, l’onglet **type** est sélectionné par défaut. Par défaut, cette vue contient un graphique et une table de données configurée avec les filtres suivants :

- **Date**: les 7 derniers jours.
- **Sens**:

  - **Entrants**
  - **Sortant**
  - **Intra-org**: ce nombre est pour les messages au sein d’un client, c’est-à-dire l’expéditeur abc@domain.com envoie au destinataire xyz@domain.com (compté indépendamment des **ports entrants et** **sortants**)

- **Type**:

  - **Courrier électronique approprié**
  - **Programme malveillant**
  - **Courrier indésirable**
  - **Protection des serveurs Edge**
  - **Messages de règle**
  - **Courriers hameçons**

Le graphique est organisé selon les valeurs de **type** .

Vous pouvez modifier ces filtres en cliquant sur **Filtrer** ou en cliquant sur une valeur dans la légende du graphique.

Le tableau de données contient les informations suivantes :

- **Direction**
- **Type**
- **24 heures**
- **3 jours**
- **7 jours**
- **15 jours**
- **30 jours**

Si vous cliquez sur **choisir une catégorie pour plus d’informations**, vous pouvez sélectionner l’une des valeurs suivantes :

- **Courrier électronique de hameçonnage**: cette sélection vous permet d’accéder au [rapport d’état de protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Programme malveillant dans la messagerie**: cette sélection vous permet d’accéder au [rapport d’état de protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Détections de courrier indésirable**: cette sélection vous permet d’accéder au [rapport des détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).
- **Courrier indésirable bloqué** pour le serveur Edge : cette sélection vous permet d’accéder au [rapport des détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).

**Exportation**:

Pour l’affichage détaillé, vous pouvez uniquement exporter des données pour un jour. Par conséquent, si vous voulez exporter des données pendant 7 jours, vous devez effectuer 7 actions d’exportation différentes.

Chaque fichier. csv exporté est limité à 150 000 lignes. Si les données de ce jour contiennent plus de 150 000 lignes, plusieurs fichiers. csv seront créés.

![Tapez View dans le rapport d’état de flux de flux ](../../media/mail-flow-status-report-type-view.png)

### <a name="direction-view-for-the-mailflow-status-report"></a>Vue de direction pour le rapport d’état de flux de flux

Si vous cliquez sur l’onglet **direction** , les mêmes filtres par défaut de la vue **type** sont utilisés.

Le graphique est organisé par les valeurs de **direction** .

Vous pouvez modifier ces filtres en cliquant sur **Filtrer** ou en cliquant sur une valeur dans la légende du graphique. Les mêmes filtres de la vue **type** sont utilisés.

La table de données contient les mêmes informations à partir de la vue **type** .

La **catégorie choisir une catégorie pour plus de détails** disponibles et les sélections possibles est identique à la vue **type** .

**Exportation**:

Pour l’affichage détaillé, vous pouvez uniquement exporter des données pour un jour. Par conséquent, si vous voulez exporter des données pendant 7 jours, vous devez effectuer 7 actions d’exportation différentes.

Chaque fichier. csv exporté est limité à 150 000 lignes. Si les données de ce jour contiennent plus de 150 000 lignes, plusieurs fichiers. csv seront créés.

![Affichage de la direction dans le rapport d’état de flux de flux ](../../media/mail-flow-status-report-direction-view.png)

### <a name="funnel-view-for-the-mailflow-status-report"></a>Vue entonnoir pour le rapport d’état de flux de flux

L’affichage **entonnoir** vous montre comment les fonctionnalités de protection contre les menaces Microsoft filtrent le courrier électronique entrant et sortant dans votre organisation. Elle fournit des détails sur le nombre total de messages électroniques, ainsi que la façon dont les fonctionnalités de protection contre les menaces configurées, notamment la protection des serveurs Edge, les logiciels anti-programme malveillant, le hameçonnage, le blocage du courrier indésirable et la détection d’usurpation d’identité ont un impact sur ce nombre.

Si vous cliquez sur l’onglet **entonnoir** , par défaut, cet affichage contient un graphique et une table de données configurée avec les filtres suivants :

- **Date**: les 7 derniers jours.

- **Sens**:

  - **Entrants**
  - **Sortant**
  - **Intra-org**: ce nombre est pour les messages envoyés au sein d’un client ; par exemple, l’expéditeur abc@domain.com envoie au destinataire xyz@domain.com (compté indépendamment des messages entrants et sortants).

L’affichage d’agrégation et le tableau de données autorisent 90 jours de filtrage.

Si vous cliquez sur **filtre**, vous pouvez filtrer le graphique et la table de données.

Ce graphique indique le nombre de messages organisés par :

- **Nombre total de messages électroniques**
- **Courrier électronique après la protection du serveur Edge**
- **Courrier électronique après anti-programme malveillant, réputation de fichier, bloc de type fichier**
- **Courrier électronique après hameçonnage, réputation de l’URL, emprunt d’identité de marque, anti-usurpation**
- **Courrier électronique après blocage du courrier indésirable et filtrage du courrier en nombre**
- **Courrier électronique après l’emprunt d’identité d’utilisateur et de domaine**<sup>1</sup>
- **Courrier électronique après la détonation 1 du fichier et de l’URL**<sup></sup>
- **Courrier électronique détecté comme étant Bénin après une protection post-remise (URL-clic sur la protection du temps de clic)**

<sup>1</sup> Defender pour Office 365 uniquement

Pour afficher le courrier électronique filtré par EOP ou Defender pour Office 365 séparément, cliquez sur la valeur dans la légende du graphique.

La table de données contient les informations suivantes, indiquées dans l’ordre décroissant de date :

- **Date**
- **Nombre total de messages électroniques**
- **Protection des serveurs Edge**
- **Anti-programme malveillant, réputation de fichier, bloc de type de fichier**:
  - **Réputation de fichier**: messages filtrés en raison de l’identification d’un fichier joint par d’autres clients Microsoft.
  - **Bloc de type de fichier**: messages filtrés en raison du type de fichier malveillant identifié dans le message.
- **Hameçonnage, réputation de l’URL, emprunt d’identité de marque, anti-usurpation**:
  - **Réputation** de l’URL : messages filtrés en raison de l’identification de l’URL par d’autres clients Microsoft.
  - Emprunt d’identité de la **marque**: messages filtrés en raison du message provenant de marques connues empruntant des expéditeurs.
  - **Anti-usurpation**: messages filtrés en raison du message tentant d’usurper un domaine auquel appartient le destinataire, ou domaine dont l’expéditeur du message n’est pas propriétaire.
- **Blocage du courrier indésirable et filtrage du courrier en nombre**:
  - **Filtrage du courrier en nombre**: messages filtrés en raison d’une tentative de remise en nombre de messages à ses destinataires.
- **Emprunt d’identité d’utilisateur et de domaine (Defender pour Office 365)**:
  - **Emprunt d’identité** de l’utilisateur : messages filtrés en raison d’une tentative d’emprunt d’identité d’un utilisateur (expéditeur du message) défini dans les paramètres de protection contre l’emprunt d’identité d’une stratégie anti-hameçonnage.
  - **Emprunt** d’identité de domaine : messages filtrés en raison d’une tentative d’emprunt d’identité d’un domaine défini dans les paramètres de protection contre l’emprunt d’identité d’une stratégie anti-hameçonnage.
- **Détonation des fichiers et des URL (Defender pour Office 365)**:
  - **Détonation du fichier**: messages filtrés par une stratégie de pièces jointes fiables.
  - **Détonation d’URL**: message filtré par une stratégie de liens fiables.
- **Post-livraison protection et zap (ATP), ou zap (EoP)**: zap indique zéro vidage automatique.

Si vous sélectionnez une ligne dans le tableau de données, une autre répartition du nombre de messages est affichée dans le menu volant.

**Exportation**:

Après avoir cliqué sur **Exporter** sous **options**, vous pouvez sélectionner l’une des valeurs suivantes :

- **Résumé (avec les données au plus des 90 derniers jours)**
- **Détails (avec les données des 30 derniers jours)**

Sous **Date**, choisissez une plage, puis cliquez sur **appliquer**. Les données des filtres actuels seront exportées dans un fichier. csv.

Chaque fichier. csv exporté est limité à 150 000 lignes. Si les données contiennent plus de 150 000 lignes, plusieurs fichiers. csv seront créés.

 ![Vue entonnoir dans le rapport d’état de flux de flux ](../../media/mail-flow-status-report-funnel-view.png)

### <a name="tech-view-for-the-mailflow-status-report"></a>Vue technique pour le rapport d’état de flux de flux

La **vue Tech** est similaire à l’affichage **entonnoir** , qui fournit des détails plus granulaires pour les fonctionnalités de protection contre les menaces configurées. À partir du graphique, vous pouvez voir comment les messages sont catégorisés aux différentes étapes de la protection contre les menaces.

Si vous cliquez sur l’onglet **affichage Tech** , par défaut, cet affichage contient un graphique et une table de données configurée avec les filtres suivants :

- **Date**: les 7 derniers jours.

- **Sens**:

  - **Entrants**
  - **Sortant**
  - **Intra-org**: ce nombre est pour les messages au sein d’un client, c’est-à-dire l’expéditeur abc@domain.com envoie au destinataire xyz@domain.com (compté indépendamment des ports entrants et sortants)

L’affichage d’agrégation et le tableau de données autorisent 90 jours de filtrage.

Si vous cliquez sur **filtre**, vous pouvez filtrer le graphique et la table de données.

Ce graphique présente les messages organisés selon les catégories suivantes :

- **Nombre total de messages électroniques**
- Serveur Edge **allow** et **Edge filtré**
- **Pas de programmes malveillants**, **détection de pièces jointes fiables** <sup>\*</sup> , **détection de moteur anti-programme malveillant** et **messages de règles**
- **Non-hameçonnage**, **échec DMARC**, détection d’usurpation d' **identité**, détection d' **usurpation** d’identité et **détection de hameçonnage**
- **Absence de détection avec détonation d’URL** et **détection de détonation d’URL**<sup>\*</sup>
- Courrier **indésirable** et **courrier indésirable**
- **Courrier électronique**, détection de **liens fiables** <sup>\*</sup> et **zap** non malveillants

<sup>\*</sup> Defender pour Office 365

Lorsque vous placez le curseur de la souris sur une catégorie dans le graphique, vous pouvez voir le nombre de messages dans cette catégorie.

La table de données contient les informations suivantes, indiquées dans l’ordre décroissant de date :

- **Date**
- **Nombre total de messages électroniques**
- **Serveur Edge filtré**
- **Moteur anti-programme malveillant, pièces jointes fiables, règle filtrée**:
  - **Règle filtrée**: messages filtrés en raison de règles de flux de messagerie (également appelées règles de transport).
- **DMARC, emprunt d’identité, usurpation, hameçonnage filtré**:
  - **DMARC**: messages filtrés en raison d’un échec de la vérification de l’authentification DMARC du message.
- **Détection de la détonation d’URL**
- **Filtrage du courrier indésirable**
- **ZAP supprimé**
- **Détection par les liens fiables**

Si vous sélectionnez une ligne dans le tableau de données, une autre répartition du nombre de messages est affichée dans le menu volant.

**Exportation**:

Lorsque vous cliquez sur **Exporter**, sous **options** , vous pouvez sélectionner l’une des valeurs suivantes :

- **Résumé (avec les données au plus des 90 derniers jours)**
- **Détails (avec les données des 30 derniers jours)**

Sous **Date**, choisissez une plage, puis cliquez sur **appliquer**. Les données des filtres actuels seront exportées dans un fichier. csv.

Chaque fichier. csv exporté est limité à 150 000 lignes. Si les données contiennent plus de 150 000 lignes, plusieurs fichiers. csv seront créés.

 ![Vue technique dans le rapport d’état de flux de flux ](../../media/mail-flow-status-report-Tech-view.png)

## <a name="sent-and-received-email-report"></a>Rapport de courrier électronique envoyé et reçu

Le rapport de **courrier électronique envoyé et reçu** est un rapport intelligent qui affiche des informations sur les messages entrants et sortants, notamment les détections de courrier indésirable, les programmes malveillants et la messagerie électronique identifiés comme étant « en qualité ». La différence entre ce rapport et le [rapport d’état de flux](#mailflow-status-report) de courrier est la suivante : ce rapport n’inclut pas de données sur les messages bloqués par la protection du serveur Edge. Il est important de comprendre que si un message est envoyé à cinq destinataires, il est considéré comme un seul message.

L’affichage Aggregate et l’affichage détaillé du rapport autorisent 90 jours de filtrage.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez  au \> **tableau de bord** rapports et sélectionnez **Envoyer et recevoir un message**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=SentAndReceivedMailATP> .

![Widget courrier électronique envoyé et reçu dans le tableau de bord rapports](../../media/sent-and-received-email-report-widget.png)

### <a name="report-view-for-the-sent-and-received-email-report"></a>Affichage de rapport pour le rapport de courrier électronique envoyé et reçu

Les graphiques suivants sont disponibles dans l’affichage rapport :

- **Décomposer en : type**: le graphique affiche toutes les catégories disponibles :

  - **Total**
  - **Courrier électronique approprié**
  - **Programme malveillant (blocage des programmes malveillants)** (EoP)
  - **Détections de courrier indésirable**
  - **Messages de règle**
  - **Programme malveillant avancé** (Microsoft Defender pour Office 365)

  Lorsque vous placez le curseur de la souris sur un jour (point de données) dans le graphique, vous pouvez afficher les détails de ce jour.

  ![Type de vue dans le rapport des courriers électroniques envoyés et reçus](../../media/sent-and-received-email-report-type-view.png)

- **Décomposer en : sens**: le graphique indique le **total**, les données **entrantes** et **sortantes** . Lorsque vous placez le curseur de la souris sur un jour (point de données) dans le graphique, vous pouvez afficher les détails de ce jour.

  ![Affichage de la direction dans le rapport de courrier électronique envoyé et reçu](../../media/sent-and-received-email-report-direction-view.png)

- **Explorer en détail** \> **Programme malveillant (anti-programme malveillant)**: cette sélection vous permet d’accéder aux [détections de programmes malveillants dans le rapport par courrier électronique](view-email-security-reports.md#malware-detections-in-email-report).

- **Explorer en détail** \> **Détections de courrier indésirable)**: cette sélection vous permet d’accéder au [rapport des détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez modifier les résultats à l’aide des filtres suivants :

- **Date de début** et **Date de fin**
- Valeurs de la direction
- Valeurs de type

Pour revenir à l’affichage de rapport, cliquez sur **afficher le rapport**.

### <a name="details-table-view-for-the-sent-and-received-email-report"></a>Vue de la table des détails pour le rapport de courrier électronique envoyé et reçu

Si vous cliquez sur **afficher les détails** de la table dans la fenêtre dépanner **par : direction** ou dépanner **par :** le mode de direction, les informations suivantes sont affichées :

- **Date (UTC)**
- **Type**
- **Direction**
- **Nombre de messages**

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez modifier les résultats à l’aide des filtres suivants :

- **Date de début** et **Date de fin**
- Valeurs de la direction
- Valeurs de type

Pour revenir à l’affichage de rapport, cliquez sur **afficher le rapport**.

## <a name="top-senders-and-recipients-report"></a>Rapport des expéditeurs et des destinataires principaux

Le rapport des **expéditeurs et des destinataires principaux** est un graphique en secteurs illustrant les principaux expéditeurs et destinataires de votre courrier électronique.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez à **rapports** \>  et sélectionnez **principaux expéditeurs et destinataires**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=TopSenderRecipientsATP> .

![Widget principaux expéditeurs et destinataires dans le tableau de bord rapports](../../media/top-senders-and-recipients-widget.png)

### <a name="report-view-for-the-top-senders-and-recipient-report"></a>Affichage de rapport pour le rapport des expéditeurs et des destinataires principaux

Les graphiques suivants sont disponibles dans l’affichage rapport :

- **Afficher les données des \> expéditeurs de messages principaux**
- **Afficher les données des \> destinataires de messagerie les plus fréquents**
- **Afficher les données pour les \> destinataires de courrier indésirable principaux**
- **Afficher les données pour \> Principaux destinataires de programmes malveillants** (EoP)
- **Afficher les données pour les \> destinataires de programmes malveillants principaux (Defender pour Office 365)**

La composition du graphique en secteurs est modifiée en fonction de ces sélections.

Lorsque vous placez le curseur de la souris sur un coin du graphique en secteurs, vous pouvez voir le nombre de messages envoyés ou reçus.

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

![Graphique en secteurs en mode état dans le rapport des expéditeurs et destinataires principaux](../../media/top-senders-and-recipients-report-view.png)

### <a name="details-table-view-for-the-top-senders-and-recipient-report"></a>Vue de la table Détails pour le rapport des expéditeurs et des destinataires principaux

Si vous cliquez sur **afficher les détails table**, les informations affichées dépendent du graphique que vous examinez :

- **Afficher les données des \> expéditeurs de messages principaux**

  - **Principaux expéditeurs de messagerie**
  - **Count**

- **Afficher les données des \> destinataires de messagerie les plus fréquents**

  - **Principaux destinataires de messagerie**
  - **Count**

- **Afficher les données pour les \> destinataires de courrier indésirable principaux**

  - **Principaux destinataires de courrier indésirable**
  - **Count**

- **Afficher les données pour \> Principaux destinataires de programmes malveillants** (EoP)

  - **Principaux destinataires de programmes malveillants**
  - **Count**

- **Afficher les données pour les \> destinataires de programmes malveillants principaux (Defender pour Office 365)**

  - **Principaux destinataires de programmes malveillants (Defender pour Office 365)**
  - **Count**

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Pour revenir à l’affichage de rapport, cliquez sur **afficher le rapport**.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles sont les autorisations nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le centre de sécurité & conformité :

- **Gestion de l'organisation**
- **Administrateur de la sécurité**
- **Lecteur de sécurité**
- **Lecteur global**

Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

**Remarque**: l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le centre d’administration 365 de Microsoft donne aux utilisateurs les autorisations requises dans le centre de sécurité & conformité _et_ des autorisations pour d’autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).

## <a name="related-topics"></a>Voir aussi

[Rapports intelligents et aperçus dans le Centre de sécurité et conformité](reports-and-insights-in-security-and-compliance.md)

[Informations sur le flux de messagerie dans le centre de sécurité et conformité](mail-flow-insights-v2.md)

[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)

[Afficher les rapports pour Microsoft Defender pour Office 365](view-reports-for-atp.md)
