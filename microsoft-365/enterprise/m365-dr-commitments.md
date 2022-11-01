---
title: Engagements Data Residency avancés
description: Engagements Data Residency avancés
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: e08e2a0df9c5a6a711d565c04aeb8fe6e16b0415
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805465"
---
# <a name="advanced-data-residency-commitments"></a>Engagements Data Residency avancés

>[!NOTE]
>Si vous avez acheté un abonnement multigéographique, Microsoft stocke certaines données client au repos dans plusieurs zones géographiques en fonction de votre configuration, même si vous avez acheté le module complémentaire Microsoft 365 Advanced Data Residency (« ADR »).  

Microsoft s’engage à stocker certaines données client au repos dans la _zone géographique de la région locale_ ou de la _zone géographique de la région locale étendue_ applicable pour les [clients éligibles](advanced-data-residency.md#eligibility) qui achètent une ADR.  Les engagements sont spécifiés ci-dessous.  

## <a name="exchange-online"></a>Exchange Online

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Exchange Online contenu de la boîte aux lettres (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes de courrier électronique stockées dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ associée.

## <a name="sharepoint-onlineonedrive-for-business"></a>SharePoint Online/OneDrive Entreprise

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Le contenu du site SharePoint Online et les fichiers stockés dans ce site, ainsi que les fichiers chargés sur OneDrive Entreprise.

## <a name="microsoft-teams"></a>Microsoft Teams

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Messages de conversation Microsoft Teams (y compris les messages privés, les messages de canal, les messages de réunion et les images utilisés dans les conversations) et, pour les clients utilisant Microsoft Stream (sur SharePoint), les enregistrements de réunion.

## <a name="microsoft-defender-for-office-p1"></a>Microsoft Defender pour Office P1

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- MDO P1 ne stocke aucune donnée client au sein de son service.
- Exchange Online Protection (EOP). Les données client suivantes sont stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ : données et stratégies de configuration du service, e-mail et pièces jointes mis en quarantaine, courrier indésirable, analyse de notation, listes de blocage (URL, locataire, utilisateur), domaines de courrier indésirable, rapports et alertes

## <a name="office-for-the-web"></a>Office pour le web

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Office pour le Web stocke les fichiers sur un hôte de stockage qui a ses promesses applicables à _la région locale Géographie_/_étendue Géographie locale étendue_.

## <a name="viva-connections"></a>Viva Connections

Les données client suivantes seront stockées dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Viva Connections tableau de bord et le flux peuvent avoir du contenu provenant de SharePoint Online, Exchange Online et Microsoft Teams. Toutes les données client provenant de ces services couverts par les engagements de résidence des données seront stockées dans la _zone géographique de la région locale_ ou dans la _zone géographique de la région locale étendue_. Pour plus [d’informations](m365-dr-workload-exo.md), reportez-vous aux pages de résidence des données de charge de travail Exchange Online, [SharePoint Online](m365-dr-workload-spo.md) et [Microsoft Teams](m365-dr-workload-teams.md).

## <a name="viva-topics"></a>Sujets Viva

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Toutes les rubriques et extraits de données client découverts sont stockés dans les _zones géographiques_ appropriées dans Exchange Online Substrate (boîtes aux lettres de site ou d’arbitrage, et Substrate). Toutes les données client de rubrique sont partitionnée en fonction de la _région géographique_ ou de la _région locale étendue géographique_ d’où proviennent les données au sein de votre locataire.
- Les modèles Machine Learning (« ML ») sont formés sur des données web publiques et, par conséquent, ne contiennent aucune donnée client de votre locataire. À l’avenir, il est possible que nous utilisions les données client pour améliorer la précision des modèles ML, auquel cas la gestion des données des modèles ML suivra les mêmes stratégies que tout autre contenu client (y compris la résidence des données, la rétention, le contrôle d’accès, la sensibilité)
- La mise en surbrillance des rubriques est calculée dynamiquement lorsque la page SharePoint Online est rendue en exécutant un modèle de langage sur le contenu de la page et en le liant à la base de connaissances de Rubriques. Les données Topics proviennent du substrat dans la _zone géographique de la région locale_ ou de la _zone géographique de la région locale étendue_.
- Les données de configuration d’administration sont stockées dans la _zone géographique de la région locale_ ou dans la _zone géographique de la région locale développée_.

## <a name="purview-audit-standard"></a>Audit Purview (Standard)

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Données de configuration de service, activités auditées, enregistrements d’audit et autorisations de requête de journal d’audit.

## <a name="purview-audit-premium"></a>Audit Purview (Premium)

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- En plus des données client stockées dans le cadre de l’audit Purview (Standard), la configuration et les données client liées aux événements cruciaux de grande valeur.

## <a name="data-lifecycle-management---data-retention"></a>Gestion du cycle de vie des données - Conservation des données

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Paramètres de stratégie de rétention, définitions d’étiquette de rétention
- Données client stockées à des emplacements d’origine pour les services suivants :
  - E-mails Exchange
  - Site SharePoint
  - Comptes OneDrive
  - Groupes Microsoft 365
  - Dossiers publics Exchange
  - Conversations et messages de canal Microsoft Teams
- Données client copiées et stockées dans Exchange Online boîtes aux lettres masquées
  - Messages du canal Teams
  - Conversations Teams
  - Messages du canal privé Teams
  - SharePoint Online, OneDrive Entreprise, Exchange Online et Microsoft Teams suivent les engagements de résidence des données pour ces services. Pour plus [d’informations](m365-dr-workload-exo.md), reportez-vous aux pages de résidence des données de charge de travail Exchange Online, [SharePoint Online](m365-dr-workload-spo.md) et [Microsoft Teams](m365-dr-workload-teams.md).
- Classifieurs d’entraînement
- Données de destruction
- Mappages entre les étiquettes de rétention et les stratégies de protection contre la perte de données (DLP).

## <a name="data-lifecycle-management---records-management"></a>Gestion du cycle de vie des données - Gestion des enregistrements

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Définitions d’étiquettes de rétention des enregistrements, définitions de plan de fichiers, paramètres de stratégie de rétention basée sur les événements, enregistrements de révision de destruction et enregistrements de suppression

## <a name="information-protection---sensitivity-labels"></a>Information Protection - Étiquettes de confidentialité

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Configuration des étiquettes
- Définition des étiquettes
- Stratégies d’étiquette
- Page d’aide personnalisée
- Explorateur d’activités et journaux d’audit unifiés Microsoft 365
- Enregistrements de justification des modifications d’étiquette.

## <a name="information-protection---data-loss-prevention-dlp"></a>Information Protection - Protection contre la perte de données (DLP)

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Configuration de l’administrateur DLP, stratégies DLP dans le Centre de conformité, activités supervisées par DLP, historique des violations, journaux d’audit unifiés Microsoft 365 et Explorateur d’activités, stockage en quarantaine, alertes DLP et tableau de bord de gestion des alertes DLP.

## <a name="information-protection---office-message-encryption"></a>Information Protection - Chiffrement des messages Office

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Stratégies de chiffrement, paramètres d’administration et messages chiffrés.

## <a name="insider-risk-management---information-barriers"></a>Gestion des risques internes - Obstacles à l’information

Les données client suivantes seront stockées au repos dans la _zone géographique de la région locale_ ou la _zone géographique de la région locale étendue_ :

- Paramètres de stratégie, indicateurs de risque et paramètres d’administration.
