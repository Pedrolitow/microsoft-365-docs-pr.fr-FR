---
title: Informations sur les courriers électroniques de nouveaux utilisateurs
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les nouveaux utilisateurs qui transfèrent des informations sur les e-mails dans le Centre de sécurité & conformité pour déterminer quand les utilisateurs de leur organisation transfèrent des messages vers de nouveaux domaines.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.collection: m365-security
search.appverid: met150
ms.openlocfilehash: 7cade67d1fc4ae6e408fc3be3ca95a3acba84a76
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68086748"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>Nouveaux utilisateurs transférant des informations sur les e-mails dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Il est suspect lorsque de nouveaux comptes d’utilisateurs de votre organisation commencent soudainement à transférer des messages électroniques vers des domaines externes.

Les **nouveaux utilisateurs qui transfèrent des informations sur les e-mails** dans le [Centre de sécurité & conformité](https://protection.office.com) vous avertit lorsque les utilisateurs nouvellement créés dans votre organisation transfèrent des messages vers des domaines externes. Cette condition peut indiquer que des comptes d’administrateur compromis ont été utilisés pour créer les nouveaux utilisateurs. Si vous pensez que les comptes ont été compromis, consultez [Répondre à un compte de messagerie compromis](responding-to-a-compromised-email-account.md).

Cet aperçu s’affiche uniquement lorsque le problème est détecté et s’affiche sur la page [du rapport de transfert](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-users-forwarding-email.png" alt-text="Informations sur le transfert d’e-mails par les nouveaux utilisateurs" lightbox="../../media/mfi-new-users-forwarding-email.png":::

Lorsque vous cliquez sur le widget, un menu volant s’affiche, dans lequel vous trouverez plus d’informations sur les messages transférés, y compris un lien vers le [rapport des modifications de transfert](#forwarding-modifications-report) , comme décrit plus loin dans cet article.

:::image type="content" source="../../media/mfi-new-users-forwarding-email-details.png" alt-text="Menu volant Détails qui s’affiche après avoir cliqué sur les nouveaux utilisateurs qui transfèrent des informations sur les e-mails" lightbox="../../media/mfi-new-users-forwarding-email-details.png":::

Vous pouvez également accéder à cette page de détails lorsque vous sélectionnez l’insight après avoir cliqué sur **Afficher tout** dans la zone **Informations principales & recommandations** (**Tableau de bord** **des rapports** \> ou <https://protection.office.com/insightdashboard>).

Vous pouvez cliquer sur le **rapport Voir associé au lien Insight** pour accéder au **rapport des modifications de transfert** , comme décrit dans la section suivante.

## <a name="forwarding-modifications-report"></a>Rapport de transfert des modifications

Le **rapport des modifications de transfert** affiche des détails sur les messages qui sont automatiquement transférés à partir d’expéditeurs de votre organisation :

- Comptes nouvellement créés qui transfèrent des messages à des domaines externes.
- Comptes qui transfèrent des messages vers des domaines externes qui n’ont jamais été transférés par d’autres expéditeurs de votre organisation.

Ces types de messages transférés peuvent présenter un risque de sécurité ou de conformité, et peuvent indiquer des comptes compromis.

Le rapport contient des données pendant 90 jours maximum. Par défaut, le rapport affiche les données des 7 derniers jours.

Ce rapport n’est pas directement disponible dans le [tableau de bord](mail-flow-insights-v2.md) Flux de courrier ou dans le [tableau de bord Rapports](view-mail-flow-reports.md). En plus de cliquer sur le **rapport Voir associé au lien d’insights** dans l’aperçu des **nouveaux utilisateurs qui transfèrent** des informations sur les e-mails, vous accédez au rapport en :

- Cliquez sur le lien du **rapport de notifications de transfert** dans les détails des [nouveaux domaines transférés par e-mail](mfi-new-domains-being-forwarded-email.md).
- Ouverture <https://protection.office.com/reportv2?id=MailFlowNewForwarding>.

### <a name="report-view-for-the-forwarding-modifications-report"></a>Vue Rapport pour le rapport de modifications de transfert

Les graphiques suivants sont disponibles dans la vue rapport :

- **Afficher les données pour : Nouveaux utilisateurs de transfert** :

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarding-users.png" alt-text="Affichage Des nouveaux utilisateurs de transfert dans le rapport des modifications de transfert" lightbox="../../media/forwarding-modifications-report-new-forwarding-users.png":::

- **Afficher les données pour : Nouveaux domaines de transfert** :

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarded-domains.png" alt-text="Vue Nouveaux domaines transférés dans le rapport des modifications de transfert" lightbox="../../media/forwarding-modifications-report-new-forwarded-domains.png":::

Si vous cliquez sur **Filtres** dans une vue de rapport, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>Vue de table Détails pour le rapport des modifications de transfert

Si vous cliquez sur **Afficher la table de détails**, les informations affichées dépendent du graphique que vous examiniez :

- **Afficher les données pour : Nouveaux utilisateurs de transfert** :

  - **Nom** : adresse e-mail de l’expéditeur.
  - **Type de transfert**
  - **Adresse du destinataire**
  - **Détails**
  - **Count**
  - **Première date de transfert**

- **Afficher les données pour : Nouveaux domaines de transfert** :

  - **Nom** : domaine de messagerie de l’expéditeur.
  - **Type de transfert**
  - **Adresse du destinataire**
  - **Détails**
  - **Count**
  - **Première date de transfert**

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Si vous sélectionnez une ligne dans le tableau, un menu volant **Détails** s’affiche avec les informations suivantes :

- **Nom** : il s’agit de l’adresse e-mail de l’expéditeur (à partir de **l’affichage Afficher les données pour : Affichage des nouveaux utilisateurs de transfert** ) ou du domaine de messagerie de l’expéditeur (à partir de **l’affichage Afficher les données pour : Nouvel affichage des domaines de transfert** ).
- **Type de transfert**
- **Destinataire**
- **Détails**
- **Count**
- **Date de début**
- **Recommandation** : À partir de là, vous pouvez cliquer sur le lien pour gérer l’utilisateur dans le Centre d'administration Microsoft 365.

  :::image type="content" source="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png" alt-text="Menu volant Détails de la table de détails de la vue Nouveaux utilisateurs de transfert dans le rapport des modifications de transfert" lightbox="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png":::

Pour revenir à la vue Rapports, cliquez sur **Afficher le rapport**.

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
