---
title: Rapport des rendez-vous virtuels du connecteur EHR Teams
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: Découvrez comment utiliser le rapport Rendez-vous virtuels du connecteur DSE Teams dans le Centre d’administration Microsoft Teams pour obtenir une vue d’ensemble de l’utilisation des rendez-vous virtuels intégrés à la récupération d’urgence dans votre organisation.
ms.openlocfilehash: 6ec3423df4b6cd094bd2cab07e44c06923ec58bf
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822503"
---
# <a name="microsoft-teams-ehr-connector-virtual-appointments-report"></a>Rapport des rendez-vous virtuels du connecteur EHR Teams

Le connecteur Microsoft Teams Electronic Health Record (EHR) Rendez-vous virtuels rapport dans le Centre d’administration Microsoft Teams vous offre un moyen rapide et facile d’afficher l’utilisation des rendez-vous virtuels intégrés à la DSE Teams dans votre organisation.

Pour afficher le rapport, vous devez être administrateur général, administrateur Teams, lecteur général ou lecteur de rapport.

## <a name="view-the-report"></a>Afficher le rapport

Il existe deux façons d’accéder au rapport et de l’afficher dans le Centre d’administration Teams.

- Via la [carte d’utilisation du connecteur EHR](#the-ehr-connector-usage-card) dans le tableau de bord
- Directement en choisissant [**Rendez-vous virtuels du connecteur EHR**](#the-teams-ehr-connector-virtual-appointments-report) dans **Analyses & rapports** > **Rapports d’utilisation**

### <a name="the-ehr-connector-usage-card"></a>Carte d’utilisation du connecteur EHR

Dans le volet de navigation gauche du Centre d’administration Microsoft Teams, choisissez **Tableau de bord**, puis accédez à la carte **Rendez-vous virtuels du connecteur EHR**.

Ici, vous obtenez une vue d’ensemble de l’activité des rendez-vous virtuels intégrés à la récupération d’urgence Teams par mois, y compris les rendez-vous terminés, l’allocation restante et si vous avez dépassé la limite mensuelle (en fonction de la licence dont vous disposez).

:::image type="content" source="media/ehr-connector-report-card.png" alt-text="Capture d’écran de la carte d’utilisation du connecteur EHR dans le tableau de bord du Centre d’administration Teams." lightbox="media/ehr-connector-report-card.png":::

Choisissez **Afficher les détails** pour afficher les détails du rapport. Pour acheter d’autres licences, choisissez **Acheter plus**.

### <a name="the-teams-ehr-connector-virtual-appointments-report"></a>Rapport sur les rendez-vous virtuels du connecteur DSE Teams

1. Dans le volet de navigation gauche du Centre d’administration Teams, accédez à **Analyses et rapports** > **Rapports d’utilisation**.
1. Sous l’onglet **Afficher les rapports**, choisissez **Rendez-vous virtuels du connecteur EHR** et une plage de dates. Ensuite, sélectionnez **Exécuter le rapport**.

    :::image type="content" source="media/ehr-connector-report.png" alt-text="Capture d’écran du rapport Rendez-vous virtuels du connecteur EHR Teams dans le Centre d’administration Teams." lightbox="media/ehr-connector-report.png":::

#### <a name="interpret-the-report"></a>Interpréter le rapport

|Légende |Description  |
|--------|-------------|
|**1**   |Chaque rapport affiche la date de génération du rapport et la plage de dates que vous avez choisie.|
|**2**   |Le tableau fournit des informations détaillées sur chaque rendez-vous qui a eu lieu pendant la plage de dates sélectionnée. N’oubliez pas que vous ne verrez pas d’entrées pour les rendez-vous auxquels un membre du personnel ou un patient n’a pas rejoint. <ul><li>**L’heure de début (UTC)** est la date et l'heure auxquelles un membre du personnel et un participant sont tous deux présents au rendez-vous.  </li> <li>**La durée** est la différence d’heure entre l’heure de début et le moment où la dernière personne quitte le rendez-vous.</li> <li>**Primaire** est le nom de l’organisateur de la réunion. <li>**L’adresse e-mail du primaire** est l’adresse e-mail de l’organisateur de la réunion.</li> <li> **Service** se rapporte aux informations du service pour le rendez-vous. Si les informations ne s’affichent pas correctement, contactez votre équipe de support technique DSE. Pour l’intégration à Epic, assurez-vous que ```&departmentId=%PERFDEPID;;; ; ;;NONE;%``` fait partie de l’enregistrement d’intégration du fournisseur. </li></li> <li>**Clients** indique le nombre total de membres du personnel et de participants au rendez-vous.</li> <li>**Dans la limite** indique si le rendez-vous est dans la limite d’allocation. </li> </ul> |
|**3**   |Vous pouvez exporter le rapport vers un fichier CSV pour une analyse hors connexion. Sélectionnez **Exporter vers Excel** pour télécharger le rapport. |
|**4**   |Sélectionnez **Filtrer** pour filtrer l’affichage des détails du rapport. |
|**5**   |Sélectionnez **Plein écran** pour afficher le rapport en mode plein écran. |
|**6**   |Sélectionnez **Modifier les colonnes** pour ajouter ou supprimer des colonnes dans la table |

> [!NOTE]
> Pour plus d’analyses sur les rendez-vous virtuels intégrés à la récupération d’urgence Teams, consultez le [rapport d’utilisation des visites virtuelles](virtual-visits-usage-report.md). Avec le rapport d’utilisation des visites virtuelles, vous pouvez afficher des métriques clés telles que le nombre total de rendez-vous, le temps d’attente dans la salle d’attente, la durée des rendez-vous et aucun affichage. Utilisez ces informations pour obtenir des informations sur les tendances d’utilisation afin de vous aider à optimiser les rendez-vous virtuels afin d’obtenir de meilleurs résultats métier.

## <a name="related-articles"></a>Articles connexes

- [Rendez-vous virtuels avec Teams – Intégration à Cerner EHR](ehr-admin-cerner.md)
- [Rendez-vous virtuels avec Teams – Intégration à Epic EHR](ehr-admin-epic.md) 
