---
title: Afficher les rapports de sécurité de messagerie dans le portail Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 3a137e28-1174-42d5-99af-f18868b43e86
ms.collection:
- M365-security-compliance
description: Découvrez comment rechercher et utiliser des rapports de sécurité du courrier électronique pour votre organisation. Les rapports de sécurité de messagerie sont disponibles dans le portail Microsoft 365 Defender.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bb7570722fcc957ca86d68f6b42ef254578d7bd7
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52930320"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Afficher les rapports de sécurité de messagerie dans le portail Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

De nombreux rapports sont disponibles dans le portail [Microsoft 365 Defender](https://security.microsoft.com) pour vous aider à voir comment les fonctionnalités de sécurité du courrier électronique, telles que les fonctionnalités anti-courrier indésirable, anti-programme malveillant et chiffrement dans Microsoft 365 protègent votre organisation. Si vous avez les [autorisations](#what-permissions-are-needed-to-view-these-reports)nécessaires, vous pouvez afficher ces rapports  dans le portail Microsoft 365 Defender en allant à Rapports e-mail & \> **collaboration** \> **e-mail & rapports de collaboration.** Pour aller directement au tableau de bord Rapports, ouvrez <https://security.microsoft.com/emailandcollabreport> .

![Tableau de bord Rapports dans le portail Microsoft 365 Defender](../../media/email-collaboration-reports.png)

## <a name="compromised-users-report"></a>Rapport utilisateurs compromis

> [!NOTE]
> Ce rapport est disponible dans les organisations Microsoft 365 avec Exchange Online boîtes aux lettres. Il n’est pas disponible dans les organisations Exchange Online Protection autonomes (EOP).

Le **rapport Utilisateurs** compromis indique le nombre de  comptes  d’utilisateurs marqués comme suspects ou restreints au cours des 7 derniers jours. Les comptes dans l’un de ces états sont problématiques, voire compromis. Avec une utilisation fréquente, vous pouvez utiliser le rapport pour repérer des pics, voire des tendances, dans des comptes suspects ou restreints. Pour plus d’informations sur les utilisateurs compromis, voir [Répondre à un compte de messagerie compromis.](responding-to-a-compromised-email-account.md)

![Widget Utilisateurs compromis dans le tableau de bord Rapports](../../media/compromised-users-report-widget.png)

L’affichage agrégé affiche les données des 90 derniers jours et l’affichage détail affiche les données des 30 derniers jours.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail \> **& collaboration** \> **e-mail & rapports** de collaboration et cliquez sur Afficher les détails sous **Utilisateurs** compromis. Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/CompromisedUsers> .

Vous pouvez filtrer le graphique et le tableau de détails en cliquant sur **Filtres** et en sélectionnant une ou plusieurs des valeurs suivantes :

- **Date de début et** **date de fin**

- **Suspect**: le compte d’utilisateur a envoyé des messages suspects et risque d’être limité à l’envoi de courriers électroniques.

- **Restreint :** le compte d’utilisateur n’a pas pu envoyer de courrier électronique en raison de modèles hautement suspects.

![Affichage du rapport dans le rapport Utilisateurs compromis](../../media/compromised-users-report-activity-view.png)

Si vous cliquez **sur Afficher le tableau des détails,** vous pouvez voir les détails suivants :

- **Heure de création**
- **ID d'utilisateur**
- **Action**

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="encryption-report"></a>Rapport de chiffrement

Le **rapport de chiffrement** est disponible dans EOP (abonnements avec boîtes aux lettres dans Exchange Online ou EOP autonome sans boîtes aux lettres Exchange Online autonomes). L’équipe de sécurité de votre organisation peut utiliser les informations de ce rapport pour identifier les modèles et appliquer ou ajuster de manière proactive les stratégies pour les messages électroniques sensibles. Par exemple :

- Si un nombre élevé de messages électroniques est chiffré par les utilisateurs, vous pouvez ajouter une stratégie de chiffrement pour automatiser le chiffrement dans certains cas d’utilisation. Pour plus d’informations, voir Définir des règles de flux de messagerie [pour chiffrer](../../compliance/define-mail-flow-rules-to-encrypt-email.md)les messages électroniques Microsoft 365 .

- Si plusieurs modèles de chiffrement sont disponibles, mais que personne ne les utilise, vous pouvez déterminer si les utilisateurs ont besoin d’une formation sur les fonctionnalités.

L’affichage agrégé autorise le filtrage pour les 90 derniers jours, tandis que l’affichage détail autorise le filtrage pendant 10 jours.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail & collaboration e-mail & rapports de collaboration et cliquez sur Afficher les détails sous Rapport de \>  \>  **chiffrement.**  Pour aller directement dans le rapport, ouvrez <https://protection.office.com/reportv2?id=EncryptionReport> .

Pour en savoir plus sur le chiffrement, voir [chiffrement de courrier électronique dans Microsoft 365](../../compliance/email-encryption.md).

### <a name="report-view-for-the-encryption-report"></a>Affichage du rapport pour le rapport de chiffrement

Vous pouvez utiliser les filtres suivants sur le graphique :

- **Afficher les données par : Rapport de chiffrement des** messages et Décomposer par **:** Méthode de chiffrement : les méthodes de chiffrement suivantes sont disponibles :

  - **Chiffrement par utilisateur**
  - **Chiffrement par stratégie**

  Si vous cliquez **sur Filtres,** vous pouvez modifier le graphique avec les filtres suivants :

  - **Date de début et** **date de fin**
  - Méthode de chiffrement.
  - Modèle de chiffrement.

- **Afficher les données par : Rapport de chiffrement des** messages et Décomposer par **:** Modèle de chiffrement : les méthodes de chiffrement suivantes sont disponibles :

  - **Ne pas avancer**
  - **Chiffrer uniquement**
  - **Précédent d’OME**
  - **Custom**

  Si vous cliquez **sur Filtres,** vous pouvez modifier le graphique avec les filtres suivants :

  - **Date de début et** **date de fin**
  - Méthode de chiffrement
  - Modèle de chiffrement

- **Afficher les données par : 5** principaux domaines de destinataires : cet affichage affiche un graphique en secteurs avec le nombre de messages envoyés pour les 5 principaux domaines de destinataires.

  Si vous cliquez sur **Filtres,** vous pouvez sélectionner une **date de début** et une **date de fin.**

### <a name="details-table-view-for-the-encryption-report"></a>Vue de table Détails pour le rapport de chiffrement

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Décomposez par : méthode de chiffrement** ou décomposer par : modèle de **chiffrement**: les informations suivantes sont affichées :

  - **Date**
  - **Adresse de l’expéditeur**
  - **Modèle de chiffrement**
  - **Méthode de chiffrement**
  - **Adresse du destinataire**
  - **Subject**

- **Afficher les données par : 5 principaux domaines de destinataires**:

  - **Date**
  - **Domaine du destinataire**
  - **Nombre de messages**

Si vous cliquez **sur Filtres** dans une vue de tableau de détails, vous pouvez modifier les résultats avec les filtres suivants :

- **Date de début et** **date de fin**
- Méthode de chiffrement
- Modèle de chiffrement

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="mailflow-status-report"></a>Rapport d’état du flux de messagerie

Le **rapport d’état du flux de messagerie** contient des informations sur les programmes malveillants, le courrier indésirable, le hameçonnage et les messages edge bloqués. Pour plus d’informations, consultez [le rapport d’état du flux de messagerie.](view-mail-flow-reports.md#mailflow-status-report)

## <a name="malware-detections-in-email-report"></a>Détections de programmes malveillants dans le rapport de courrier électronique

Le **rapport sur les programmes malveillants détectés** dans le rapport de courrier électronique affiche des informations sur les programmes malveillants détectés dans les messages électroniques entrants et sortants (programmes malveillants détectés par Exchange Online Protection ou EOP). Pour plus d’informations sur la protection contre les programmes malveillants dans EOP, voir Protection contre les programmes [malveillants dans EOP.](anti-malware-protection.md)

 Le filtre d’affichage agrégé autorise 90 jours, tandis que le filtre de tableau détails ne le permet que sur 10 jours.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail & collaboration e-mail & rapports de collaboration et cliquez sur Afficher les détails sous Programmes \>  \>  **malveillants détectés** dans le courrier **électronique.** Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/MalwareDetections> .

![Détections de programmes malveillants dans le widget de messagerie dans le tableau de bord Rapports](../../media/malware-detections-widget.png)

Vous pouvez filtrer le graphique et le tableau de détails en cliquant sur **Filtres** et en sélectionnant :

- **Date de début et** **date de fin**
- **Entrant**
- **Sortant**

![Affichage du rapport dans le rapport de détection des programmes malveillants dans le rapport de courrier électronique](../../media/malware-detections-report-view.png)

Si vous cliquez **sur Afficher le tableau des détails,** vous pouvez voir les détails suivants :

- **Date**
- **Adresse de l’expéditeur**
- **Adresse du destinataire**
- **ID de message**: disponible dans le champ d’en-tête **Message-ID** dans l’en-tête du message et doit être unique. Un exemple de valeur est `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (notez les crochets).
- **Subject**
- **Filename**
- **Nom du programme malveillant**

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="mail-latency-report"></a>Rapport de latence du courrier

Le **rapport de latence du courrier** contient des informations sur la remise et la latence de détonation du courrier au sein de votre organisation. Pour plus d’informations, voir [Rapport de latence de messagerie.](view-reports-for-mdo.md#mail-latency-report)

## <a name="sent-and-received-email-report"></a>Rapport de courrier électronique envoyé et reçu

Le **rapport de** courrier électronique envoyé et reçu contient des informations sur les programmes malveillants, le courrier indésirable, les règles de flux de messagerie (également appelées règles de transport) et les détections avancées de programmes malveillants une fois que le courrier électronique est entré dans le service. Pour plus d’informations, consultez [le rapport de courrier électronique envoyé et reçu.](view-mail-flow-reports.md#sent-and-received-email-report)

## <a name="spam-detections-report"></a>Rapport sur la détection des courriers indésirables

Le **rapport détections de** courrier indésirable affiche les messages électroniques de courrier indésirable bloqués par EOP. Les messages sont comptés individuellement, et non par destinataire. Par exemple, si le même message de courrier indésirable a été envoyé à 100 destinataires de votre organisation, il compte comme un seul message.

L’affichage agrégé autorise le filtrage sur 90 jours, tandis que le tableau de détails autorise le filtrage sur 10 jours.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail & collaboration e-mail & rapports de collaboration et cliquez sur Afficher les \>  \>  **détails** sous Détections de courrier **indésirable.** Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/SpamDetections> .

![Widget de détection de courrier indésirable dans le tableau de bord Rapports](../../media/spam-detections-report-widget.png)

Pour plus d’informations sur la protection contre le courrier indésirable, consultez la [protection anti-courrier indésirable dans EOP.](anti-spam-protection.md)

### <a name="report-view-for-the-spam-detections-report"></a>Affichage du rapport pour le rapport détections de courrier indésirable

Les graphiques suivants sont disponibles dans l’affichage de rapport :

- **Décomposez par : Action**: les types d’événements suivants sont affichés :

  - **Contenu de courrier indésirable filtré**
  - **Blocage d’adresses IP de courrier indésirable**
  - **Bloc d’enveloppe de courrier indésirable**
  - **Filtre DBEB de courrier indésirable**: blocage du bord basé sur l’annuaire (DBEB)

  Lorsque vous pointez sur un jour (point de données) dans le graphique, vous pouvez voir le nombre d’éléments bloqués ce jour-là, ainsi que la façon dont ces éléments sont classés.

  ![Affichage des actions dans le rapport détections de courrier indésirable](../../media/spam-detections-report-action-view.png)

- **Décomposez par : Direction**: les instructions suivantes sont indiquées :

  - **Entrant**
  - **Sortant**

  ![Affichage de direction dans le rapport détections de courrier indésirable](../../media/spam-detections-report-direction-view.png)

Si vous cliquez **sur Filtres** dans un affichage de rapport, vous pouvez modifier les résultats avec les filtres suivants :

- **Date de début et** **date de fin**
- Valeurs de direction
- Valeurs de type d’événement

### <a name="details-table-view-for-the-spam-detections-report"></a>Vue de table Détails pour le rapport détections de courrier indésirable

Si vous cliquez **sur Afficher le tableau des détails** dans un affichage de rapport, les informations suivantes sont affichées :

- **Date**
- **Adresse de l’expéditeur**
- **Adresse du destinataire**
- **Type d’événement**
- **Action**
- **Subject**

Si vous cliquez **sur Filtres** dans un tableau de détails, vous pouvez modifier les résultats avec les filtres suivants :

- **Date de début et** **date de fin**
- Valeurs de direction
- Valeurs de type d’événement

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

## <a name="spoof-detections-report"></a>Rapport sur les détections d’usurpation d’usurpation

> [!NOTE]
> Le rapport sur les détections d’usurpation d’usurpation d’informations amélioré, tel que décrit dans cet article, est disponible en prévisualisation, peut faire l’objet de changements et n’est pas disponible dans toutes les organisations. L’ancienne version du rapport n’a affiché que les messages **électroniques de qualité** et les **courriers indésirables**.

Le **rapport sur les détections d’usurpation d’informations** affiche des informations sur les messages qui ont été bloqués ou autorisés en raison de l’usurpation. Pour plus d’informations sur l’usurpation d’adresse, voir Protection contre l’usurpation [d’adresses dans EOP.](anti-spoofing-protection.md)

L’affichage agrégé du rapport autorise 45 jours de filtrage, tandis que l’affichage détaillé ne permet que dix jours <sup>\*</sup> de filtrage.

<sup>\*</sup> Au final, vous pourrez utiliser jusqu’à 90 jours de filtrage.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail & \> **collaboration** \> **e-mail & rapports** de collaboration et cliquez sur Afficher les détails sous **détections** d’usurpation d’adresses . Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/SpoofMailReport> .

![Widget de détections d’usurpation d’informations dans le tableau de bord Rapports](../../media/spoof-detections-widget.png)

Lorsque vous pointez sur un jour (point de données) dans le graphique, vous pouvez voir combien de messages usurpés ont été détectés et pourquoi.

Vous pouvez filtrer le graphique et le tableau de détails en cliquant sur **Filtres** et en sélectionnant une ou plusieurs des valeurs suivantes :

- **Date de début et** **date de fin**

- **Résultat**
  - **Pass**
  - **Échec**
  - **SoftPass**
  - **Aucune**
  - **Other**

- **Type d’usurpation :** **interne** et **externe**

![Affichage du rapport dans le rapport de détections d’usurpation d’usurpation d’état](../../media/spoof-detections-report-view.png)

Si vous cliquez **sur Afficher le tableau des détails,** vous pouvez voir les détails suivants :

- **Date**
- **Utilisateur usurpé**
- **Infrastructure d’envoi**
- **Type d’usurpation**
- **Résultat**
- **Code de résultat**
- **SPF**
- **DKIM**
- **DMARC**
- **Nombre de messages**

Pour revenir à l’affichage du rapport, cliquez **sur Afficher le rapport.**

Pour plus d’informations sur les codes de résultats d’authentification composite, consultez les [en-têtes de message anti-courrier](anti-spam-message-headers.md)indésirable Microsoft 365 .

## <a name="threat-protection-status-report"></a>Rapport sur l’état de la protection contre les menaces

Le **rapport d’état de la protection** contre les menaces est disponible dans EOP et Microsoft Defender pour Office 365 ; toutefois, les rapports contiennent des données différentes. Par exemple, les clients EOP peuvent afficher des informations sur les programmes malveillants détectés dans le courrier électronique, mais pas sur les fichiers malveillants détectés par les pièces [jointes sécurisées](mdo-for-spo-odb-and-teams.md)pour SharePoint, OneDrive et Microsoft Teams .

Le rapport indique le nombre de messages électroniques avec du contenu malveillant, tels que des fichiers ou des adresses web (URL) bloqués par le [](safe-links.md)moteur anti-programme malveillant, la purge automatique d’heure zéro [(ZAP)](zero-hour-auto-purge.md)et Defender pour les fonctionnalités de Office 365 telles que les liens [sécurisés,](safe-attachments.md)les pièces jointes et l’anti-hameçonnage. [](set-up-anti-phishing-policies.md) Vous pouvez utiliser ces informations pour identifier les tendances ou déterminer si les stratégies d’organisation doivent être ajuster.

**Remarque**: il est important de comprendre que si un message est envoyé à cinq destinataires, nous le compterons comme cinq messages différents et pas un seul message.

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail \> **& collaboration** \> **e-mail & rapports** de collaboration et cliquez sur Afficher les détails sous État de la protection contre les **menaces.**  Pour aller directement dans le rapport, ouvrez l’une des URL suivantes :

- Microsoft Defender pour Office 365 :<https://protection.office.com/reportv2?id=TPSAggregateReportATP>
- EOP : <https://protection.office.com/reportv2?id=TPSAggregateReport>

![Widget d’état de la protection contre les menaces dans le tableau de bord Rapports](../../media/threat-protection-status-report-widget.png)

Par défaut, le graphique affiche les données des 7 derniers jours. Si vous cliquez sur **Filtres,** vous pouvez sélectionner une plage de dates de 90 jours (les abonnements d’essai peuvent être limités à 30 jours). L’affichage Tableau détails autorise le filtrage pendant 30 jours.

### <a name="report-view-for-the-threat-protection-status-report"></a>Affichage du rapport pour le rapport d’état de la protection contre les menaces

Les vues disponibles sont les suivantes :

- **Afficher les données par : Vue d’ensemble**: les informations de détection suivantes sont affichées :

  - **Programme malveillant de messagerie**
  - **Hameçonnage par e-mail**
  - **Programme malveillant de contenu**

  ![Vue d’ensemble dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-overview-view.png)

- **Afficher les données par : Contenu \> Programme**<sup>malveillant 1</sup>: les informations suivantes s’affiche pour Microsoft Defender pour Office 365 organisations :

  - **Moteur anti-programme** malveillant : fichiers malveillants détectés dans Sharepoint, OneDrive et Microsoft Teams par la détection de virus intégrée dans [Microsoft 365](virus-detection-in-spo.md).
  - **Détonation de fichiers**: fichiers malveillants détectés par les pièces [jointes SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

  ![Affichage des programmes malveillants de contenu dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-content-malware-view.png)

- **Afficher les données par : Remplacement de message**: les informations de motif de remplacement suivantes sont affichées :

  - **Ignorer l’local**
  - **IP Allow**
  - **Règle de flux de messagerie**
  - **Autoriser l’expéditeur**
  - **Domaine autoriser**
  - **ZAP non activé**
  - **Dossier Courrier indésirable non activé**
  - **Expéditeur sécurisé de l’utilisateur**
  - **Domaine sécurisé de l’utilisateur**

  ![Affichage des remplacements de messages dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-message-override-view.png)

- **Décomposez par : technologie de détection et** affichage des données par : Hameçonnage de messagerie : les informations suivantes sont affichées : **\>**

  - **Réputation d’URL** générée par atp <sup>1</sup>: réputation d’URL malveillante générée à partir de Defender pour Office 365 détonations dans d’autres Microsoft 365 clients.
  - **Filtre de hameçonnage avancé**: signaux de hameçonnage basés sur l’apprentissage automatique.
  - **Anti-usurpation - Échec DMARC**: échec de l’authentification DMARC sur les messages.
  - **Anti-usurpation - intra-organisation**: l’expéditeur tente d’usurper le domaine du destinataire.
  - **Anti-usurpation - domaine externe**: l’expéditeur tente d’usurper un autre domaine.
  - **Emprunt d’identité de marque**: emprunt d’identité de marques connues basées sur des expéditeurs.
  - **Emprunt d’identité**<sup>de domaine 1</sup>: emprunt d’identité des domaines que le client possède ou définit.
  - **Réputation de l’URL EOP**: réputation d’URL malveillante.
  - **Filtre d’hameçonnage général**: signaux de hameçonnage basés sur des règles d’analyste.
  - **Autres**
  - **Phish ZAP**<sup>2 :</sup>purge automatique zéro heure des messages de hameçonnage.
  - **Détonation d’URL**<sup>1</sup>
  - **Emprunt d’identité**<sup>d’utilisateur 1</sup>: emprunt d’identité des utilisateurs définis par l’administrateur ou appris par le biais de l’intelligence des boîtes aux lettres.

  ![Affichage de la technologie de détection pour le courrier d’hameçonnage dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-phishing-detection-tech-view.png)

- **Décomposez par : technologie de détection et** affichage des données par : Programme malveillant de messagerie : les informations suivantes sont affichées : **\>**

  - Réputation de fichier générée **par atp**<sup>1</sup>: toutes les réputations de fichiers malveillants générées par Defender pour Office 365 détonations.
  - **Moteur anti-programme malveillant**<sup>1 :</sup>détection des moteurs anti-programme malveillant.
  - Blocage du type de fichier de stratégie **anti-programme** malveillant : il s’adresse aux messages électroniques filtrés en raison du type de fichier malveillant identifié dans le message.
  - **Détonation de fichier**<sup>1</sup>: détection par pièces jointes fiables.
  - **Réputation d’un fichier malveillant**
  - **Programme malveillant ZAP**<sup>2</sup>
  - **Autres**

  ![Affichage de la technologie de détection pour les programmes malveillants dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-malware-detection-tech-view.png)

- **Décomposez par : Type** de stratégie et afficher les données par **: \> Hameçonnage** de messagerie ou Affichage des données par : Programme malveillant de messagerie : les informations suivantes sont affichées : **\>**

  - **Anti-programme malveillant**
  - **Pièces jointes sécurisées**<sup>1</sup>
  - **Anti-hameçonnage**
  - **Anti-courrier indésirable**
  - **Règle de flux de messagerie** (également appelée règle de transport)
  - **Autres**

  ![Affichage du type de stratégie pour le courrier de hameçonnage dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-phishing-policy-type-view.png)

- **Décomposez par : État de** remise et affichage des données par : **\> Hameçonnage** de messagerie ou Affichage des données par : Programme malveillant de messagerie : les informations suivantes sont affichées : **\>**

  - **Échec de remise**
  - **Dropped**
  - **Forwarded**
  - **Boîte aux lettres hébergée : dossier personnalisé**
  - **Boîte aux lettres hébergée : éléments supprimés**
  - **Boîte aux lettres hébergée : Boîte de réception**
  - **Boîte aux lettres hébergée : courrier indésirable**
  - **Serveur local : remis**
  - **Mise en quarantaine**

  ![Affichage de l’état de remise du courrier de hameçonnage dans le rapport d’état de la protection contre les menaces](../../media/threat-protection-status-report-phishing-delivery-status-view.png)

<sup>1</sup> Defender pour Office 365 uniquement

La purge automatique de <sup>2</sup> heures zéro (ZAP) n’est pas disponible dans EOP autonome (elle fonctionne uniquement dans Exchange Online boîtes aux lettres).

Si vous cliquez sur **Filtres,** les filtres disponibles dépendent du graphique que vous regardiez :

- Pour **afficher les données par : Programme malveillant de \> contenu,** vous pouvez modifier le rapport par **date** de début et **de fin,** ainsi que la **valeur de** détection.

- Pour **afficher les données par : Remplacement de message,** vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **date de fin**
  - **Override Reason**
  - **Balise**: filtrer les résultats par utilisateurs ou groupes pour lesquels la balise utilisateur spécifiée a été appliquée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, voir [Balises utilisateur.](user-tags.md)
  - **Domaine**

- Pour tous les autres affichages, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **date de fin**
  - **Détection**
  - **Protégé par**: **ATP** ou **EOP**
  - **Balise**: filtrer les résultats par utilisateurs ou groupes pour lesquels la balise utilisateur spécifiée a été appliquée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, voir [Balises utilisateur.](user-tags.md)
  - **Domaine**

### <a name="details-table-view-for-the-threat-protection-status-report"></a>Affichage du tableau détails pour le rapport d’état de la protection contre les menaces

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Afficher les données par : Vue d’ensemble**: aucun bouton de **table Afficher les détails** n’est disponible.

- **Afficher les données par : Contenu \> Programmes malveillants**:

  - **Date**
  - **Emplacement**
  - **Dirigé par**
  - **Nom du programme malveillant**

  Si vous cliquez sur **Filtres** dans cet affichage, vous pouvez modifier le rapport par **date** de début et **de fin,** ainsi que la **valeur de** détection.

- **Afficher les données par : Remplacement de message**:

  - **Date**
  - **Subject**
  - **Expéditeur**
  - **Destinataires**
  - **Détecté par**
  - **Override Reason**
  - **Source de compromis**
  - **Tags**

  Si vous cliquez **sur Filtres** dans cet affichage, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début et** **date de fin**
  - **Override Reason**
  - **Balise**: filtrer les résultats par utilisateurs ou groupes pour lesquels la balise utilisateur spécifiée a été appliquée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, voir [Balises utilisateur.](user-tags.md)
  - **Domaine**
  - **Destinataires** (notez que cette propriété filtrable est disponible uniquement dans l’affichage Tableau des détails)

- Tous les autres graphiques :

  - **Date**
  - **Subject**
  - **Expéditeur**
  - **Destinataires**
  - **Détecté par**
  - **État de remise**
  - **Source de compromis**
  - **Tags**

  Si vous cliquez **sur Filtres,** vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début et** **date de fin**
  - **Détection**
  - **Protégé par**: **Defender pour Office 365** ou **EOP**
  - **Balise**: filtrer les résultats par utilisateurs ou groupes pour lesquels la balise utilisateur spécifiée a été appliquée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, voir [Balises utilisateur.](user-tags.md)
  - **Domaine**
  - **Destinataires** (notez que cette propriété filtrable est disponible uniquement dans l’affichage Tableau des détails)

## <a name="top-malware-report"></a>Principaux rapports sur les programmes malveillants

Le **rapport des principaux programmes** malveillants présente les différents types de programmes malveillants détectés par la protection [anti-programme malveillant dans EOP.](anti-malware-protection.md)

Pour afficher le rapport, ouvrez le portail  [Microsoft 365 Defender,](https://security.microsoft.com)allez à Rapports e-mail & collaboration e-mail & rapports de collaboration et cliquez sur Afficher les détails sous Principaux programmes \>  \>  **malveillants.**  Pour aller directement dans le rapport, ouvrez <https://security.microsoft.com/reports/TopMalware> .

![Widget de programmes malveillants de premier niveau dans le tableau de bord Rapports](../../media/top-malware-report-widget.png)

Lorsque vous pointez sur une souris dans le graphique en secteurs, vous pouvez voir le nom d’un type de programme malveillant et le nombre de messages détectés comme ayant ce programme malveillant.

![Affichage du rapport sur les programmes malveillants le plus haut](../../media/top-malware-report-view.png)

Si vous cliquez **sur Afficher le tableau des détails,** vous pouvez voir les détails suivants :

- **Principaux programmes malveillants**
- **Count**

Si vous cliquez sur **Filtres** dans l’affichage Rapport ou dans l’affichage Tableau détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

## <a name="url-threat-protection-report"></a>Rapport sur la protection contre les menaces d’URL

Le **rapport sur la protection contre les menaces d’URL** est disponible dans Microsoft Defender Office 365. Pour plus d’informations, voir le rapport sur la [protection contre les menaces d’URL.](view-reports-for-mdo.md#url-threat-protection-report)

## <a name="user-reported-messages-report"></a>Rapport des messages signalés par l’utilisateur

Le rapport des **messages** signalés par l’utilisateur affiche des informations sur les messages électroniques que les utilisateurs ont signalés comme courrier indésirable, tentatives de hameçonnage ou courriers électroniques de qualité à l’aide du [add-in Signaler](enable-the-report-message-add-in.md) un message ou du module de signalement du hameçonnage. [](enable-the-report-phish-add-in.md)

Des détails sont disponibles pour chaque message, y compris la raison de la remise, une exception de stratégie de courrier indésirable ou une règle de flux de messagerie configurée pour votre organisation. Pour afficher les détails, sélectionnez un élément dans la liste  des rapports utilisateur, puis affichez les informations sous les **onglets** Résumé et Détails.

![Le rapport des messages signalés par l’utilisateur affiche les messages étiquetés comme courrier indésirable, non indésirable ou tentatives de hameçonnage.](../../media/ad5e9a3d-b833-419c-bcc9-3425d9604ead.png)

Pour afficher ce rapport, dans le portail [Microsoft 365 Defender,](https://security.microsoft.com)go to **Reports** \> **Email & collaboration** Email & collaboration \> **reports** User \> **reported messages**.

- Go to **Reports** \> **Email & collaboration** Email & collaboration \> **reports** User \> **reported messages**.

![In the Microsoft 365 Defender portal, choose Reports \> Email & collaboration Email & collaboration reports User reported \> \> messages](../../media/user-reported-messages.png)

> [!IMPORTANT]
> Pour que le rapport des messages signalés par l’utilisateur fonctionne correctement, l’enregistrement **d’audit** doit être Office 365 votre environnement. Cette tâche est généralement effectuée par une personne dont le rôle Journaux d’audit est Exchange Online. Pour plus d’informations, [voir Turn Microsoft 365 audit log search on or off](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles autorisations sont nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le portail Microsoft 365 Defender :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur sécurité**
- **Lecteur global**

Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender.](permissions-in-the-security-and-compliance-center.md)

Remarque : l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne  aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Que se passe-t-il si les rapports n’affichent pas de données ?

Si vous ne voyez pas de données dans vos rapports, vérifiez que vos stratégies sont correctement définies. Pour en savoir plus, [consultez La protection contre les menaces.](protect-against-threats.md)

## <a name="related-topics"></a>Voir aussi

[Protection contre le courrier indésirable et les programmes malveillants dans EOP](anti-spam-and-anti-malware-protection.md)

[Rapports intelligents et informations sur le portail Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[Afficher les rapports de flux de messagerie dans le portail Microsoft 365 Defender](view-mail-flow-reports.md)

[Afficher des rapports pour Defender pour Office 365](view-reports-for-mdo.md)
