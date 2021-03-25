---
title: Informations sur les courriers électroniques de nouveaux utilisateurs
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les informations sur les nouveaux utilisateurs qui envoient des courriers électroniques dans le Centre de sécurité & conformité pour examiner quand les utilisateurs de leur organisation envoient des messages à de nouveaux domaines.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 807df82ca80e851554db7b8f373a5ca4af02a391
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204490"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>Nouveaux utilisateurs qui envoient des informations sur le courrier électronique dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Il est suspect lorsque de nouveaux comptes d’utilisateurs de votre organisation commencent soudainement à envoyer des messages électroniques à des domaines externes.

**L’aperçu** des nouveaux domaines transmis par courrier électronique dans le Centre de sécurité [&](https://protection.office.com) conformité vous informe lorsque des utilisateurs nouvellement créés dans votre organisation sont en train de forwarder des messages vers des domaines externes. Cette condition peut indiquer que des comptes d’administrateur compromis ont été utilisés pour créer les nouveaux utilisateurs. Si vous pensez que les comptes ont été compromis, voir Répondre [à un compte de messagerie compromis.](responding-to-a-compromised-email-account.md)

Cette information apparaît uniquement lorsque le problème est détecté et apparaît sur la page du rapport [de forwarding.](view-mail-flow-reports.md#forwarding-report)

![Informations sur les courriers électroniques de nouveaux utilisateurs](../../media/mfi-new-users-forwarding-email.png)

Lorsque vous cliquez sur le widget, un volant s’affiche, dans lequel vous trouverez plus de détails sur les messages transmis, y compris un lien vers le rapport de [modifications](#forwarding-modifications-report) de report, comme décrit plus loin dans cet article.

![Volant d’informations qui s’affiche après avoir cliqué sur l’aperçu du courrier électronique nouveaux utilisateurs](../../media/mfi-new-users-forwarding-email-details.png)

Vous pouvez également vous rendre sur cette page de  détails lorsque vous sélectionnez l’aperçu après avoir cliqué sur Afficher tout dans la zone Recommandations & informations les plus **détaillées** **(** Tableau de bord de rapports \>  ou <https://protection.office.com/insightdashboard> ).

Vous pouvez cliquer sur le **rapport Voir associé au** lien d’informations pour aller au rapport de modifications de **forwarding,** comme décrit dans la section suivante.

## <a name="forwarding-modifications-report"></a>Rapport de modifications de forwarding

Le **rapport de modifications de forwarding** affiche des détails sur les messages qui sont automatiquement transmis par des expéditeurs de votre organisation :

- Comptes nouvellement créés qui relaient des messages vers des domaines externes.
- Comptes qui envoient des messages à des domaines externes qui n’ont jamais été transmis par d’autres expéditeurs de votre organisation.

Ces types de messages transmis peuvent poser un risque de sécurité ou de conformité, et peuvent indiquer des comptes compromis.

Le rapport contient des données pendant 90 jours au plus. Par défaut, le rapport affiche les données des 7 derniers jours.

Ce rapport n’est pas directement disponible dans le tableau de bord de flux de [messagerie](mail-flow-insights-v2.md) ou dans le tableau de bord [Rapports.](view-mail-flow-reports.md) En plus de cliquer sur le rapport  **Voir** associé au lien Informations dans l’aperçu des nouveaux utilisateurs qui envoient des e-mails, vous pouvez obtenir le rapport en :

- Cliquez sur le **lien du rapport de notifications** de forwarding dans les détails de l’aperçu des nouveaux domaines transmis par courrier [électronique.](mfi-new-domains-being-forwarded-email.md)
- Ouverture <https://protection.office.com/reportv2?id=MailFlowNewForwarding> .

### <a name="report-view-for-the-forwarding-modifications-report"></a>Affichage du rapport pour le rapport de modifications de report

Les graphiques suivants sont disponibles dans l’affichage de rapport :

- **Afficher les données pour : Nouveaux utilisateurs de forwarding**:

  ![Affichage des nouveaux utilisateurs de forwarding dans le rapport de modifications de forwarding](../../media/forwarding-modifications-report-new-forwarding-users.png)

- **Afficher les données pour : Nouveaux domaines de forwarding**:

  ![Nouvel affichage des domaines transmis dans le rapport de modifications de forwarding](../../media/forwarding-modifications-report-new-forwarded-domains.png)

Si vous cliquez sur **Filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>Vue de table Détails pour le rapport de modifications de report

Si vous cliquez sur Afficher le tableau des **détails,** les informations affichées dépendent du graphique que vous regardiez :

- **Afficher les données pour : Nouveaux utilisateurs de forwarding**:

  - **Nom**: adresse e-mail de l’expéditeur.
  - **Type de forwarding**
  - **Adresse du destinataire**
  - **Détails**
  - **Count**
  - **Première date d’avance**

- **Afficher les données pour : Nouveaux domaines de forwarding**:

  - **Nom**: domaine de messagerie de l’expéditeur.
  - **Type de forwarding**
  - **Adresse du destinataire**
  - **Détails**
  - **Count**
  - **Première date d’avance**

Si vous cliquez sur **Filtres** dans une vue de tableau de détails, vous pouvez spécifier une plage de dates avec la **date** de début et la **date de fin.**

Si vous sélectionnez une ligne dans le tableau, un volant **Détails** s’affiche avec les informations suivantes :

- **Nom**: il s’agit de l’adresse e-mail de l’expéditeur (à partir de l’affichage Afficher les données pour : Nouvel affichage **utilisateurs** de **forwarding)** ou du domaine de messagerie de l’expéditeur (à partir de l’affichage Afficher les données pour : Nouvel affichage des nouveaux domaines de forwarding).
- **Type de forwarding**
- **Destinataire**
- **Détails**
- **Count**
- **Date de début**
- **Recommandation**: à partir de là, vous pouvez cliquer sur le lien pour gérer l’utilisateur dans le Centre d’administration Microsoft 365.

![Détails du tableau des détails de l’affichage Nouveaux utilisateurs de forwarding dans le rapport de modifications de forwarding](../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png)

Pour revenir à l’affichage Rapports, cliquez **sur Afficher le rapport.**

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)
