---
title: Afficher les rapports de protection avancée contre les menaces
f1.keywords:
- CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- M365-security-compliance
description: Recherchez et utilisez des rapports pour Office 365 protection avancée contre les menaces dans le centre de sécurité &amp; conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 16fef101f722a23b3a64d91c85c2f946c67036f0
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48328031"
---
# <a name="view-reports-for-office-365-advanced-threat-protection"></a>Afficher les rapports pour Office 365 protection avancée contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Les organisations Office 365 Advanced Threat Protection (ATP) (par exemple, les abonnements Microsoft 365 E5 ou les modules complémentaires ATP plan 1 ou ATP plan 2) contiennent un grand nombre de rapports liés à la sécurité. Si vous disposez des [autorisations nécessaires](#what-permissions-are-needed-to-view-the-atp-reports), vous pouvez afficher ces rapports dans le centre de sécurité & conformité en accédant au **Reports** \> **tableau de bord**rapports. Pour accéder directement au tableau de bord rapports, ouvrez <https://protection.office.com/insightdashboard> .

![Tableau de bord des rapports dans le centre de sécurité & conformité](../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png)

## <a name="advanced-threat-protection-file-types-report"></a>Rapport sur les types de fichiers de Protection avancée contre les menaces

Le rapport de rapports sur les **types de fichiers de protection avancée contre les menaces** indique le type de fichiers détectés comme malveillants par des [pièces jointes fiables](atp-safe-attachments.md).

 La vue agrégée du rapport autorise 90 jours de filtrage, tandis que l’affichage détaillé autorise uniquement les 10 jours de filtrage.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez **Reports** au \> **tableau de bord** rapports et sélectionnez **types de fichiers Office ATP**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=ATPFileReport> .

![Widget de types de fichiers ATP Office dans le tableau de bord rapports](../../media/atp-file-types-report-widget.png)

> [!NOTE]
> Les informations contenues dans ce rapport sont également disponibles dans le [rapport de suppression des messages de protection avancée contre les menaces](#advanced-threat-protection-message-disposition-report).

### <a name="report-view-for-the-advanced-threat-protection-file-types-report"></a>Affichage de rapport pour le rapport de types de fichiers de protection avancée contre les menaces

Les vues disponibles sont les suivantes :

- **Afficher les données par : fichier**: le graphique contient les informations suivantes :

  - **Pièces jointes Excel malveillantes**
  - **Pièces jointes Flash malveillantes**
  - **Pièces jointes PDF malveillantes**
  - **Pièces jointes PowerPoint malveillantes**
  - **URL malveillantes**
  - **Pièces jointes de mots malveillants**
  - **Pièces jointes exécutables malveillants**
  - **Autres**

  Lorsque vous pointez sur un jour particulier (point de données), vous pouvez voir la répartition des types de fichiers malveillants détectés par [les pièces jointes fiables](atp-safe-attachments.md) et la protection contre les [programmes malveillants dans EOP](anti-malware-protection.md).

  ![Vue de fichier dans le rapport des types de fichiers ATP](../../media/atp-file-types-report-file-view.png)

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de types de fichiers qui sont visibles dans le graphique.

- **Afficher les données par : message**: le graphique contient les informations suivantes :

  - **Bloquer l’accès**
  - **Messages remplacés**
  - **Messages surveillés**
  - **Remplacé par remise de courrier dynamique**: pour plus d’informations, consultez la rubrique [distribution dynamique dans les stratégies de pièces jointes approuvées](atp-safe-attachments.md#dynamic-delivery-in-safe-attachments-policies).

  ![Affichage des messages dans le rapport sur les types de fichiers ATP](../../media/atp-file-types-report-message-view.png)

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de disposition de message disponibles dans le graphique et la valeur de **messages supplémentaires transmises** .

### <a name="details-table-view-for-the-advanced-threat-protection-file-types-report"></a>Vue de la table Détails pour le rapport des types de fichiers de protection avancée contre les menaces

Si vous cliquez sur **afficher les détails table**, le rapport fournit une vue quasi en temps réel de tous les clics effectués au sein de l’organisation au cours des 10 derniers jours. Les informations affichées dépendent du graphique que vous recherchez :

- **Afficher les données par : fichier**:

  - **Date**
  - **Adresse du destinataire**
  - **Adresse de l’expéditeur**
  - **ID du message**: disponible dans le champ d’en-tête **message-ID** de l’en-tête du message et doit être unique. Un exemple de valeur est `<08f1e0f6806a47b4ac103961109ae6ef@server.domain>` (Notez les chevrons).
  - **File**

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de types de fichiers qui sont visibles dans le graphique.

- **Afficher les données par : message**:

  - **Date**
  - **Adresse du destinataire**
  - **Adresse de l’expéditeur**
  - **ID de message**
  - **File**
  - **Subject**

  Si vous cliquez sur **filtres**, vous pouvez modifier les résultats à l’aide des filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de disposition de message disponibles dans le graphique et la valeur de **messages supplémentaires transmises** .

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="advanced-threat-protection-message-disposition-report"></a>Rapport sur la destruction des messages de Protection avancée contre les menaces

Le rapport de **disposition des messages ATP** indique les actions qui ont été effectuées pour les messages électroniques détectés comme présentant du contenu malveillant.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez à **rapports** \> **Dashboard** et sélectionnez **Office ATP message disposition**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=ATPMessageReport> .

![Widget disposition du message DAV Office 365 dans le tableau de bord rapports](../../media/atp-message-disposition-report-widget.png)

> [!NOTE]
> Les informations contenues dans ce rapport sont également disponibles dans le [rapport types de fichiers de protection avancée contre les menaces](#advanced-threat-protection-file-types-report).

### <a name="report-view-for-the-advanced-threat-protection-message-disposition-report"></a>Affichage de rapport pour le rapport de disposition de messages de protection avancée contre les menaces

Les vues disponibles sont les suivantes :

- **Afficher les données par : message**: le graphique contient les informations suivantes :

  - **Bloquer l’accès**
  - **Messages remplacés**
  - **Messages surveillés**
  - **Remplacé par remise de courrier dynamique**: pour plus d’informations, consultez la rubrique [distribution dynamique dans les stratégies de pièces jointes approuvées](atp-safe-attachments.md#dynamic-delivery-in-safe-attachments-policies).

  ![Affichage des messages dans le rapport sur les types de fichiers ATP](../../media/atp-file-types-report-message-view.png)

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de disposition de message disponibles dans le graphique et la valeur de **messages supplémentaires transmises** .

- **Afficher les données par : fichier**: le graphique contient les informations suivantes :

  - **Pièces jointes Excel malveillantes**
  - **Pièces jointes Flash malveillantes**
  - **Pièces jointes PDF malveillantes**
  - **Pièces jointes PowerPoint malveillantes**
  - **URL malveillantes**
  - **Pièces jointes de mots malveillants**
  - **Pièces jointes exécutables malveillants**
  - **Autres**

  Lorsque vous pointez sur un jour particulier (point de données), vous pouvez voir la répartition des types de fichiers malveillants détectés par [les pièces jointes fiables](atp-safe-attachments.md) et la protection contre les [programmes malveillants dans EOP](anti-malware-protection.md).

  ![Vue de fichier dans le rapport des types de fichiers ATP](../../media/atp-file-types-report-file-view.png)

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de types de fichiers qui sont visibles dans le graphique.

### <a name="details-table-view-for-the-advanced-threat-protection-message-disposition-report"></a>Vue de la table Détails pour le rapport de disposition de messages de protection avancée contre les menaces

Si vous cliquez sur **afficher les détails table**, le rapport fournit une vue quasi en temps réel de tous les clics effectués au sein de l’organisation au cours des 10 derniers jours. Les informations affichées dépendent du graphique que vous recherchez :

- **Afficher les données par : message**:

  - **Date**
  - **Adresse du destinataire**
  - **Adresse de l’expéditeur**
  - **ID de message**
  - **File**
  - **Subject**

  Si vous cliquez sur **filtres**, vous pouvez modifier les résultats à l’aide des filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de disposition de message disponibles dans le graphique et la valeur de **messages supplémentaires transmises** .

- **Afficher les données par : fichier**:

  - **Date**
  - **Adresse du destinataire**
  - **Adresse de l’expéditeur**
  - **ID de message**
  - **File**

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les mêmes valeurs de types de fichiers qui sont visibles dans le graphique.

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="threat-protection-status-report"></a>Rapport sur l’état de la protection contre les menaces

Le rapport d' **État de protection contre les menaces** est une vue unique qui rassemble des informations sur le contenu malveillant et les e-mails malveillants détectés et bloqués par [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) et Office 365 ATP. Pour plus d’informations, consultez la rubrique [Threat Protection Status Report](view-email-security-reports.md#threat-protection-status-report).

## <a name="url-threat-protection-report"></a>Rapport d’URL de protection contre les menaces

Le **rapport URL protection contre les menaces** fournit des vues récapitulatives et des tendances pour les menaces détectées, ainsi que les actions effectuées sur les clics d’URL dans le cadre de [liens fiables](atp-safe-links.md). Ce rapport n’aura pas de clic sur les données des utilisateurs pour lesquels la stratégie de liens fiables est sélectionnée, l’option **ne pas suivre les clics utilisateur** est activée.

Pour afficher le rapport, ouvrez le [Centre de sécurité & conformité](https://protection.office.com), accédez **Reports** au \> **tableau de bord** rapports et sélectionnez **URL protection Report**. Pour accéder directement au rapport, ouvrez <https://protection.office.com/reportv2?id=URLProtectionActionReport> .

![Widget rapport de protection des URL dans le tableau de bord rapports](../../media/url-protection-report-widget.png)

> [!NOTE]
> Il s’agit d’un *rapport de tendance de protection*, ce qui signifie que les données représentent des tendances dans un jeu de données plus volumineux. Par conséquent, les données de l’affichage agrégé ne sont pas disponibles en temps réel ici, mais les données de la vue de la table des détails sont, de sorte que vous pouvez constater une légère divergence entre les deux vues.

### <a name="report-view-for-the-url-threat-protection-report"></a>Affichage de rapport pour le rapport d’URL protection contre les menaces

Le rapport **URL protection contre les menaces** comporte deux vues agrégées qui sont actualisées toutes les quatre heures, qui affichent les données des 90 derniers jours :

- **URL cliquez sur protection action**: indique le nombre de clics d’URL par les utilisateurs de l’organisation, ainsi que les résultats du Click :

  - **Bloqué** (l’utilisateur n’a pas pu accéder à l’URL)
  - **Bloqué et clic sur**
  - **Clic lors de l’analyse**

  Un clic indique que l’utilisateur a cliqué sur la page bloquer pour le site Web malveillant (les administrateurs peuvent désactiver l’option cliquer via dans les stratégies de liens fiables).

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les actions de protection clic disponibles, plus la valeur **autorisée** (l’utilisateur a été autorisé à accéder à l’URL).

  ![URL cliquez sur affichage d’action de protection dans le rapport d’URL protection contre les menaces](../../media/url-threat-protection-report-url-click-protection-action-view.png)

- **URL cliquez par application**: indique le nombre de clics d’URL par les applications qui prennent en charge les liens fiables :

  - **Client de messagerie**
  - **PowerPoint**
  - **Word**
  - **Excel**
  - **OneNote**
  - **Visio**
  - **Teams**
  - **Other**

  Si vous cliquez sur **filtres**, vous pouvez modifier le rapport avec les filtres suivants :

  - **Date de début** et **Date de fin**
  - Les applications disponibles.

### <a name="details-table-view-for-the-url-threat-protection-report"></a>Vue de la table Détails pour le rapport URL protection contre les menaces

Si vous cliquez sur **afficher les détails**de la table, le rapport fournit une vue quasi en temps réel de tous les clics effectués au sein de l’organisation pendant les 7 derniers jours avec les détails suivants :

- **Cliquez sur heure**
- **Utilisateur**
- **URL**
- **Action**
- **App**

Si vous cliquez sur **filtres** dans la vue table des détails, vous pouvez filtrer selon les mêmes critères que dans l’affichage rapport, ainsi que par les **domaines** ou les **destinataires** séparés par des virgules.

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="additional-reports-to-view"></a>Rapports supplémentaires à afficher

Outre les rapports ATP décrits dans cette rubrique, plusieurs autres rapports sont disponibles, comme décrit dans le tableau suivant :

****

|Rapport|Rubrique|
|---|---|
|**Explorateur** (plan ATP 2) ou **détections en temps réel** (plan ATP 1)|[Explorateur de menaces (et détections en temps réel)](threat-explorer.md)|
|**Rapports de sécurité de messagerie**, tels que le rapport des expéditeurs et des destinataires principaux, le rapport de courrier indésirable et le rapport des détections de courrier indésirable.|[Afficher les rapports de sécurité de courrier dans le centre de sécurité et conformité](view-email-security-reports.md)|
|Les **rapports de flux de messagerie**, tels que le rapport de transfert, le rapport d’état de flux de messagerie et le rapport des expéditeurs et des destinataires principaux.|[Afficher les rapports de flux de messagerie dans le centre de sécurité & conformité](view-mail-flow-reports.md)|
|**Suivi des URL pour les liens fiables** (PowerShell uniquement). La sortie de cette cmdlet vous indique les résultats des actions de liens fiables au cours des sept derniers jours.|[Get-UrlTrace](https://docs.microsoft.com/powershell/module/exchange/get-urltrace)|
|**Résultats du trafic de messagerie pour EOP et ATP** (PowerShell uniquement). La sortie de cette applet de commande contient des informations sur le domaine, la date, le type d’événement, la direction, l’action et le nombre de messages.|[Get-MailTrafficATPReport](https://docs.microsoft.com/powershell/module/exchange/get-mailtrafficatpreport)|
|**Rapports de détail du courrier pour les détections EOP et ATP** (PowerShell uniquement). La sortie de cette applet de commande contient des détails sur les URL ou les fichiers malveillants, les tentatives de hameçonnage, l’emprunt d’identité et d’autres menaces potentielles dans les messages ou les fichiers.|[Get-MailDetailATPReport](https://docs.microsoft.com/powershell/module/exchange/get-maildetailatpreport)|
|

## <a name="what-permissions-are-needed-to-view-the-atp-reports"></a>Quelles sont les autorisations nécessaires pour afficher les rapports ATP ?

Pour afficher et utiliser les rapports décrits dans cette rubrique, **vous devez disposer d’un rôle approprié pour le centre de sécurité &amp; et le centre d’administration Exchange**.

- Pour le centre de sécurité & conformité, vous devez disposer de l’un des rôles suivants :

  - Gestion de l’organisation
  - Administrateur de la sécurité (qui peut être affecté dans le centre d’administration Azure Active Directory ( [https://aad.portal.azure.com](https://aad.portal.azure.com) ))
  - Opérateur de sécurité (cela peut être attribué dans le centre d’administration Azure Active Directory ( [https://aad.portal.azure.com](https://aad.portal.azure.com) ))
  - Lecteur de sécurité

- Pour Exchange Online, vous devez disposer de l’un des rôles suivants, qui est affecté dans le centre d’administration Exchange ( [https://outlook.office365.com/ecp](https://outlook.office365.com/ecp) ) ou avec des applets de commande PowerShell (consultez la rubrique [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell)) :

  - Gestion de l’organisation
  - Gestion de l’organisation en affichage seul
  - Rôle Destinataires en affichage uniquement
  - Gestion de la conformité

Pour en savoir plus, consultez les ressources suivantes :

- [Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)

- [Autorisations des fonctionnalités dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)

## <a name="what-if-the-reports-arent-showing-data"></a>Qu’en est-il si les rapports n’affichent pas de données ?

Si vous ne voyez pas de données dans vos rapports ATP, vérifiez que vos stratégies sont correctement configurées. Votre organisation doit avoir [des stratégies de liens fiables](set-up-atp-safe-links-policies.md) et des [stratégies de pièces jointes approuvées](set-up-atp-safe-attachments-policies.md) définies afin que la protection ATP soit mise en place. Consultez également la rubrique protection contre le [courrier indésirable et les programmes malveillants](anti-spam-and-anti-malware-protection.md).

## <a name="related-topics"></a>Voir aussi

[Rapports intelligents et aperçus dans le Centre de sécurité et conformité](reports-and-insights-in-security-and-compliance.md)
  
[Autorisations de rôle (Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#role-permissions)
