---
title: Afficher les rapports de Defender pour Office 365
f1.keywords:
- CSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à rechercher et à utiliser les rapports Defender pour Office 365 qui sont disponibles dans le portail Microsoft 365 Defender.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 28b0f31b59d7707e37d47982ee67a85e80adfe5a
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68075139"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>Afficher les rapports Defender pour Office 365 dans le portail Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender pour Office 365 organisations (par exemple, Microsoft 365 E5 abonnements ou Microsoft Defender pour Office 365 Plan 1 ou Microsoft Defender pour Office 365 modules complémentaires Plan 2) contiennent divers rapports liés à la sécurité. Si vous disposez [des autorisations nécessaires](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports), vous pouvez afficher et télécharger ces rapports dans le portail Microsoft 365 Defender.

## <a name="view-and-download-reports"></a>Consulter et télécharger les rapports

### <a name="view-reports"></a>Affichage des rapports

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Pour accéder directement à la page **des rapports de collaboration Email &**, utilisez <https://security.microsoft.com/emailandcollabreport>.

1. Choisissez le rapport à afficher, puis sélectionnez **Afficher les détails**.

### <a name="download-reports"></a>Télécharger des rapports existants

Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** >  Email & rapports de **collaboration** \> **à télécharger**. Pour accéder directement à la page **Rapports à télécharger** , utilisez <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="Page rapports de collaboration Email & dans le portail Microsoft 365 Defender" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> Email rapports de sécurité qui ne nécessitent pas de Defender pour Office 365 sont décrits dans [Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](view-email-security-reports.md).
>
> Les rapports liés au flux de messagerie se trouvent désormais dans le Centre d’administration Exchange (EAC). Pour plus d’informations sur ces rapports, consultez [les rapports de flux de courrier dans le nouveau centre d’administration Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>Rapport sur les types de fichiers pièces jointes fiables

> [!NOTE]
> Ce rapport a été déprécié. Les mêmes informations sont disponibles dans le [rapport d’état de la protection contre les menaces](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>Rapport de destruction des messages pièces jointes fiables

> [!NOTE]
> Ce rapport a été déprécié. Les mêmes informations sont disponibles dans le [rapport d’état de la protection contre les menaces](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport de latence de courrier

Le **rapport de latence** du courrier affiche une vue agrégée de la latence de remise et de détonation du courrier au sein de votre organisation. Les délais de remise du courrier dans le service sont affectés par un certain nombre de facteurs, et le temps de livraison absolu en secondes n’est souvent pas un bon indicateur de réussite ou un problème. Un délai de livraison lent un jour peut être considéré comme un délai de livraison moyen un autre jour, ou inversement. Cette opération tente de qualifier la remise des messages en fonction de données statistiques sur les délais de remise observés d’autres messages.

La latence côté client et réseau n’est pas incluse.

Pour afficher le rapport, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse : accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Pour accéder directement à la page **des rapports de collaboration Email &**, utilisez <https://security.microsoft.com/emailandcollabreport>.

Dans la page **Email & rapports de collaboration**, recherchez le **rapport de latence** du courrier, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, utilisez <https://security.microsoft.com/mailLatencyReport>.

:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="Widget rapport de latence du courrier dans la page des rapports de collaboration Email &" lightbox="../../media/mail-latency-report-widget.png":::

Dans la page **rapport de latence** du courrier, les onglets suivants sont disponibles dans la page rapport **de latence** du courrier :

- **50e centile** : il s’agit du milieu pour les délais de remise des messages. Vous pouvez considérer cette valeur comme un délai de livraison moyen. Cet onglet est sélectionné par défaut.
- **90e centile** : cela indique une latence élevée pour la remise des messages. Seuls 10 % des messages ont pris plus de temps que cette valeur.
- **99e centile** : indique la latence la plus élevée pour la remise des messages.

Quel que soit l’onglet que vous sélectionnez, le graphique affiche les messages organisés en catégories suivantes :

- **Global**
- **Détonation**

Lorsque vous pointez sur une catégorie dans le graphique, vous pouvez voir une répartition de la latence dans chaque catégorie.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="Vue des 50e centiles du rapport de latence du courrier" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

Si vous cliquez sur **Filtrer**, vous pouvez filtrer le graphique et la table de détails en fonction des valeurs suivantes :

- **Date (UTC)** : **Date de début** et **date de fin**
- **Affichage des** messages : l’une des valeurs suivantes :
  - **Tous les messages**
  - **Messages détonés** : l’une des valeurs suivantes :
    - **Détonation inline** : inclut les messages qui sont entièrement testés avant la remise.
    - **Détonation asynchrone**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date (UTC)**
- **Latence**
- **Nombre de messages**
- **50e centile**
- **90e centile**
- **99e centile**

Dans la page principale du rapport, l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **[Le bouton Exporter](view-email-security-reports.md#export-report)** est disponible.

## <a name="threat-protection-status-report"></a>Rapport sur l’état de la protection contre les menaces

Le rapport **d’état de la protection contre les menaces** est une vue unique qui rassemble des informations sur le contenu malveillant et les e-mails malveillants détectés et bloqués par [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) et Microsoft Defender pour Office 365. Pour plus d’informations, consultez le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>Rapport des principaux expéditeurs et destinataires

Le rapport **Meilleurs expéditeurs et destinataires** affiche les principaux destinataires pour les fonctionnalités de protection EOP et Defender pour Office 365. Pour plus d’informations, consultez [le rapport Meilleurs expéditeurs et destinataires](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>Rapport sur la protection des URL

Le **rapport de protection des URL** fournit des vues récapitulatives et de tendance pour les menaces détectées et les actions effectuées sur les clics d’URL dans le cadre des [liens fiables](safe-links.md). Ce rapport ne contient pas de données de clic des utilisateurs sur lesquels la stratégie Liens fiables a été appliquée lorsque l’option **Suivre les clics de l’utilisateur** n’est pas sélectionnée.

Pour afficher le rapport, ouvrez le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez la **page de protection d’URL**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="Widget de rapport de protection des URL dans la page des rapports de collaboration Email &" lightbox="../../media/url-protection-report-widget.png":::

Les vues disponibles sur la page du rapport **de protection des URL** sont décrites dans les sections suivantes.

> [!NOTE]
> Il s’agit d’un *rapport de tendance de protection*, ce qui signifie que les données représentent les tendances d’un jeu de données plus volumineux. Par conséquent, les données des graphiques ne sont pas disponibles en temps réel ici, mais les données de la table de détails sont, de sorte que vous pouvez voir une légère différence entre les deux. Les graphiques sont actualisés une fois toutes les quatre heures et contiennent des données pour les 90 derniers jours.

### <a name="view-data-by-url-click-protection-action"></a>Afficher les données par action de protection par clic d’URL

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="L’affichage, à savoir l’action de protection par clic d’URL dans le rapport de protection d’URL" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

La **vue Afficher les données par action de protection par clic d’URL** affiche le nombre de clics d’URL par les utilisateurs de l’organisation et les résultats du clic :

- **Autorisé** : clics autorisés.
- **Autorisé par l’administrateur client** : clics autorisés dans les stratégies Liens sécurisés.
- **Bloqué** : cliquez sur bloqué.
- **Bloqué par l’administrateur client** : les clics sont bloqués dans les stratégies Liens sécurisés.
- **Bloqué et cliqué :** clics bloqués sur lesquels les utilisateurs cliquent jusqu’à l’URL bloquée.
- **Bloqué par l’administrateur du locataire et cliqué** : Administration a bloqué le lien, mais l’utilisateur a cliqué dessus.
- **Clic lors de l’analyse** : cliquez sur l’emplacement où les utilisateurs cliquent sur la page d’analyse en attente pour accéder à l’URL.
- **Analyse en attente** : clique sur les URL en attente d’un verdict d’analyse.

Un clic indique que l’utilisateur a cliqué sur la page de blocs vers le site web malveillant (les administrateurs peuvent désactiver le clic dans les stratégies liens fiables).

Si vous cliquez sur **Filtres**, vous pouvez modifier le rapport et la table de détails en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** : **Date de début** et **date de fin**
- **Action** :
  - **Autorisé**
  - **Bloqué**
  - **Autorisé par l’administrateur client**
  - **Bloqué et cliqué**
  - **Bloqué par l’administrateur du locataire et cliqué sur**
  - **Clic lors de l’analyse**
  - **Analyse en attente**
- **Domaines** : domaines d’URL répertoriés dans les résultats du rapport.
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Le tableau des détails sous le graphique fournit la vue en quasi-temps réel suivante de tous les clics qui se sont produits au sein de l’organisation au cours des 7 derniers jours :

- **Heure du clic**
- **Utilisateur**
- **URL**
- **Action**
- **Application**

Dans la page principale du rapport, l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](view-email-security-reports.md#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](view-email-security-reports.md#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](view-email-security-reports.md#export-report)** sont disponibles.

### <a name="view-data-by-url-click-by-application"></a>Afficher les données par URL cliquez sur l’application

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="Affichage de l’action de protection par clic d’URL dans le rapport de protection d’URL" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

Le clic **Afficher les données par URL par vue d’application** indique le nombre de clics d’URL par les applications qui prennent en charge les liens fiables :

- **Client de messagerie**
- **Document Office**
- **Teams**

Si vous cliquez sur **Filtres**, vous pouvez modifier le rapport et la table de détails en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** : **Date de début** et **date de fin**
- **Détection** : applications disponibles à partir du graphique.
- **Domaines** : domaines d’URL répertoriés dans les résultats du rapport.
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Le tableau des détails sous le graphique fournit la vue en quasi-temps réel suivante de tous les clics qui se sont produits au sein de l’organisation au cours des 7 derniers jours :

- **Heure du clic**
- **Utilisateur**
- **URL**
- **Action**
- **Application**

Dans la page principale du rapport, l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](view-email-security-reports.md#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](view-email-security-reports.md#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](view-email-security-reports.md#export-report)** sont disponibles.

## <a name="additional-reports-to-view"></a>Rapports supplémentaires à afficher

Outre les rapports décrits dans cet article, plusieurs autres rapports sont disponibles, comme décrit dans le tableau suivant :

|Rapport|Rubrique|
|---|---|
|**Détections de l’Explorateur** (Microsoft Defender pour Office 365 Plan 2) ou **en temps réel** (Microsoft Defender pour Office 365 Plan 1)|[Explorateur de menaces (et détections en temps réel)](threat-explorer.md)|
|Email rapports de sécurité qui ne nécessitent pas de Defender pour Office 365|[Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](view-email-security-reports.md)|
|Rapports de flux de messagerie dans le Centre d’administration Exchange (EAC)|[Rapports de flux de courrier dans le nouveau centre d’administration Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

Applets de commande de création de rapports PowerShell :

|Rapport|Rubrique|
|---|---|
|Principaux expéditeurs et destinataires|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Programmes les plus malveillants |[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Trafic de messagerie|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Liens sûrs|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Utilisateurs compromis|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|État du flux de courrier|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|Utilisateurs usurpés|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Quelles sont les autorisations nécessaires pour afficher les rapports Defender pour Office 365 ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le portail Microsoft 365 Defender :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur de sécurité**
- **Lecteur général**

Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

**Remarque** : l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Que se passe-t-il si les rapports n’affichent pas de données ?

Si vous ne voyez pas de données dans vos rapports Defender pour Office 365, vérifiez que vos stratégies sont correctement configurées. Pour que Defender pour Office 365 protection soit en place, votre organisation doit disposer de stratégies de liens [sécurisés](set-up-safe-links-policies.md) et de stratégies de [pièces jointes](set-up-safe-attachments-policies.md) sécurisées. Consultez également [la protection anti-courrier indésirable](anti-spam-protection.md) et [anti-programme malveillant](anti-malware-protection.md).

