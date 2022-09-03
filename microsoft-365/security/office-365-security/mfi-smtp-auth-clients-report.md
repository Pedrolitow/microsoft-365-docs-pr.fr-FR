---
title: Informations et rapports sur les clients d’authentification SMTP dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’insight d’authentification SMTP et le rapport dans le tableau de bord de flux de courrier du Centre de sécurité & conformité pour surveiller les expéditeurs de courrier dans leur organisation qui utilisent SMTP authentifié (SMTP AUTH) pour envoyer des messages électroniques.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7fdd41d0a6c8d0104c524b577ea754ec915f321c
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67597346"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>Informations et rapports sur les clients d’authentification SMTP dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les informations sur les **clients d’authentification SMTP** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) et le [rapport des clients d’authentification SMTP](#smtp-auth-clients-report) associés dans le [Centre de sécurité & conformité](https://protection.office.com) mettent en évidence l’utilisation du protocole de soumission du client SMTP AUTH par les utilisateurs ou les comptes système de votre organisation. Ce protocole hérité (qui utilise le point de terminaison smtp.office365.com) offre uniquement l’authentification de base et est susceptible d’être utilisé par des comptes compromis pour envoyer des e-mails. L’insight et le rapport vous permettent de rechercher une activité inhabituelle pour les soumissions de courrier SMTP AUTH. Il affiche également les données d’utilisation TLS pour les clients ou les appareils utilisant SMTP AUTH.

Le widget indique le nombre d’utilisateurs ou de comptes de service qui ont utilisé le protocole d’authentification SMTP au cours des 7 derniers jours.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-widget.png" alt-text="Widget des clients d’authentification SMTP dans le tableau de bord de flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-smtp-auth-clients-report-widget.png":::

Si vous cliquez sur le nombre de messages sur le widget, un menu volant **des clients d’authentification SMTP** s’affiche. Le menu volant fournit une vue agrégée de l’utilisation et des volumes TLS de la semaine dernière.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-details.png" alt-text="Menu volant Détails après avoir cliqué sur le widget des clients d’authentification SMTP dans le tableau de bord flux de courrier" lightbox="../../media/mfi-smtp-auth-clients-report-details.png":::

Vous pouvez cliquer sur le lien du **rapport des clients d’authentification SMTP** pour accéder au rapport des clients d’authentification SMTP, comme décrit dans la section suivante.

## <a name="smtp-auth-clients-report"></a>Rapport de clients d’authentification SMTP

### <a name="report-view-for-the-smtp-auth-clients-report"></a>Vue rapport pour le rapport des clients d’authentification SMTP

Par défaut, le rapport affiche les données des 7 derniers jours, mais les données sont disponibles pour les 90 derniers jours.

La section Vue d’ensemble contient les graphiques suivants :

- **Afficher les données par : Volume d’envoi** : par défaut, le graphique affiche le nombre de messages clients d’authentification SMTP qui ont été envoyés à partir de tous les domaines (**Afficher les données pour : Tous les domaines expéditeurs** est sélectionné par défaut). Vous pouvez filtrer les résultats sur un domaine d’expéditeur spécifique en cliquant sur **Afficher les données et** en sélectionnant le domaine de l’expéditeur dans la liste déroulante. Si vous pointez sur un point de données spécifique (jour), le nombre de messages s’affiche.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png" alt-text="Affichage du volume d’envoi dans le rapport des clients d’authentification SMTP dans le Centre de sécurité & conformité" lightbox="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png":::

- **Afficher les données par : Utilisation de TLS** : le graphique affiche le pourcentage d’utilisation de TLS pour tous les messages clients d’authentification SMTP pendant la période sélectionnée. Ce graphique vous permet d’identifier et d’agir sur les utilisateurs et les comptes système qui utilisent toujours des versions antérieures de TLS.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png" alt-text="La vue d’utilisation de TLS dans le rapport des clients d’authentification SMTP dans le Centre de sécurité & conformité" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png":::

Si vous cliquez sur **Filtres** dans une vue de rapport, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Cliquez sur **Demander le rapport** pour recevoir une version plus détaillée du rapport dans un e-mail. Vous pouvez spécifier la plage de dates et les destinataires pour recevoir le rapport.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>Vue de table détails pour le rapport des clients d’authentification SMTP

Si vous cliquez sur **Afficher la table de détails**, les informations affichées dépendent du graphique que vous examiniez :

- **Afficher les données par : Envoi de volume** : les informations suivantes sont affichées dans un tableau :

  - **Adresse de l’expéditeur**
  - **Nombre de messages**

  Si vous sélectionnez une ligne, les mêmes détails sont affichés dans un menu volant.

- **Afficher les données par : Utilisation de TLS** : les informations suivantes sont affichées dans un tableau :

  - **Adresse de l’expéditeur**
  - **TLS1.0%**<sup>\*</sup>
  - **TLS1.1%**<sup>\*</sup>
  - **TLS1.2%**<sup>\*</sup>
  - **Nombre de messages**

  <sup>\*</sup> Cette colonne affiche à la fois le pourcentage et le nombre de messages de l’expéditeur.

Si vous cliquez sur **Filtres** dans une vue de table de détails, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Si vous sélectionnez une ligne, des détails similaires s’affichent dans un menu volant :

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png" alt-text="Menu volant Détails de la table de détails de la vue d’utilisation de TLS dans le rapport des clients d’authentification SMTP" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png":::

Cliquez sur **Demander le rapport** pour recevoir une version plus détaillée du rapport dans un e-mail. Vous pouvez spécifier la plage de dates et les destinataires pour recevoir le rapport.

Pour revenir à la vue Rapports, cliquez sur **Afficher le rapport**.

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
