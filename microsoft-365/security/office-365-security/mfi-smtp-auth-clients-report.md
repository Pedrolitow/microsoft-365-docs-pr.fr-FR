---
title: Analyse des clients SMTP AUTH et rapports dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le rapport et l’analyseur d’authentification SMTP dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité afin de surveiller les expéditeurs de messages électroniques de leur organisation qui utilisent SMTP authentifié (authentification SMTP) pour envoyer des messages électroniques.
ms.openlocfilehash: 65e5569bcd79caef071ee2103d18a4e985c19dbb
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46826868"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>Clients d’authentification SMTP Insight and report dans le centre de conformité & Security

Les **clients d’authentification SMTP** du [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) et du [rapport clients SMTP](#smtp-auth-clients-report) associés mettent en surbrillance l’utilisation du protocole de soumission du client SMTP AUTH par les utilisateurs ou les comptes système de votre organisation. Ce protocole hérité (qui utilise le point de terminaison smtp.office365.com) offre uniquement l’authentification de base et est susceptible d’être utilisé par des comptes compromis pour envoyer des courriers électroniques. L’aperçu et le rapport vous permettent de vérifier l’activité inhabituelle pour les envois de courrier électronique SMTP. Il indique également les données d’utilisation TLS pour les clients ou les appareils utilisant l’authentification SMTP.

Le widget indique le nombre d’utilisateurs ou de comptes de service qui ont utilisé le protocole SMTP AUTH au cours des 7 derniers jours.

![Widget clients SMTP AUTH dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité](../../media/mfi-smtp-auth-clients-report-widget.png)

Si vous cliquez sur le nombre de messages dans le widget, un lanceur de **clients SMTP AUTH** apparaît. La fenêtre mobile offre une vue agrégée de l’utilisation et des volumes TLS pour la semaine précédente.

![Menu volant des détails après avoir cliqué sur le widget clients SMTP AUTH dans le tableau de bord de flux de messagerie](../../media/mfi-smtp-auth-clients-report-details.png)

Vous pouvez cliquer sur le lien **rapport des clients d’authentification SMTP** pour accéder au rapport clients SMTP AUTH, comme décrit dans la section suivante.

## <a name="smtp-auth-clients-report"></a>Rapport de clients d’authentification SMTP

### <a name="report-view-for-the-smtp-auth-clients-report"></a>Affichage de rapport pour le rapport clients SMTP AUTH

Par défaut, le rapport affiche les données des 7 derniers jours, mais les données sont disponibles pendant les 90 derniers jours.

La section vue d’ensemble contient les graphiques suivants :

- **Afficher les données par : volume d’envoi**: par défaut, le graphique indique le nombre de messages client SMTP AUTH qui ont été envoyés à partir de tous les domaines (**afficher les données pour : tous les domaines des expéditeurs** sont sélectionnés par défaut). Vous pouvez filtrer les résultats sur un domaine d’expéditeur spécifique en cliquant sur **afficher les données pour** et en sélectionnant le domaine de l’expéditeur dans la liste déroulante. Si vous pointez sur un point de données spécifique (jour), le nombre de messages s’affiche.

  ![Affichage du volume d’envoi dans le rapport clients SMTP AUTH dans le centre de sécurité & conformité](../../media/mfi-smtp-auth-clients-report-sending-volume-view.png)

- **Afficher les données par : utilisation de TLS**: le graphique indique le pourcentage d’utilisation TLS pour tous les messages client SMTP AUTH pendant la période sélectionnée. Ce graphique vous permet d’identifier et de prendre des mesures sur les utilisateurs et les comptes système qui utilisent encore des versions plus anciennes de TLS.

  ![Affichage de l’utilisation de TLS dans le rapport clients d’authentification SMTP dans le centre de sécurité & conformité](../../media/mfi-smtp-auth-clients-report-tls-usage-view.png)

Si vous cliquez sur **filtres** dans un affichage de rapport, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Cliquez sur **demander un rapport** pour recevoir une version plus détaillée du rapport dans un message électronique. Vous pouvez spécifier la plage de dates et les destinataires qui recevront le rapport.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>Vue de la table Détails pour le rapport clients SMTP AUTH

Si vous cliquez sur **afficher les détails table**, les informations affichées dépendent du graphique que vous examinez :

- **Afficher les données par : volume d’envoi**: les informations suivantes sont affichées dans un tableau :

  - **Adresse de l’expéditeur**
  - **Nombre de messages**

  Si vous sélectionnez une ligne, les mêmes détails s’affichent dans un menu volant.

- **Afficher les données par : utilisation de TLS**: les informations suivantes sont affichées dans un tableau :

  - **Adresse de l’expéditeur**
  - **TLS 1.0%**<sup>\*</sup>
  - **TLS 1.1%**<sup>\*</sup>
  - **TLS 1.2%**<sup>\*</sup>
  - **Nombre de messages**

  <sup>\*</sup> Cette colonne indique à la fois le pourcentage et le nombre de messages provenant de l’expéditeur.

Si vous cliquez sur **filtres** dans un affichage tableau détaillé, vous pouvez spécifier une plage de dates avec **Date de début** et date de **fin**.

Si vous sélectionnez une ligne, des détails similaires s’affichent dans un menu volant :

![Fenêtre mobile détails à partir de la table Détails de la vue utilisation TLS dans le rapport clients SMTP AUTH](../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png)

Cliquez sur **demander un rapport** pour recevoir une version plus détaillée du rapport dans un message électronique. Vous pouvez spécifier la plage de dates et les destinataires qui recevront le rapport.

Pour revenir à l’affichage rapports, cliquez sur **afficher le rapport**.

## <a name="related-topics"></a>Rubriques connexes

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
