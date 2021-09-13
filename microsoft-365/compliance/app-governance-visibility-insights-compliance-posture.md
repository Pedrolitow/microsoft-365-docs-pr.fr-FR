---
title: Déterminer la posture de conformité de votre application
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Déterminez la posture de conformité de votre application.
ms.openlocfilehash: 4cc54e5ea0fdaf0a8a196b90b09e2e8be970c7c1
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181426"
---
# <a name="determine-your-app-compliance-posture"></a>Déterminer la posture de conformité de votre application

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gouvernance des applications Microsoft vous permet d’évaluer rapidement la posture de conformité des applications tierces et leur accès aux données de votre client Microsoft 365 à partir de la page Vue d’ensemble de la gouvernance des applications du Centre de conformité Microsoft 365.

![Page vue d’ensemble de la gouvernance des applications dans le Centre de conformité Microsoft 365.](..\media\manage-app-protection-governance\mapg-cc-overview.png)

>[!Note]
> Votre compte de connexion doit avoir l’un des [ces rôles](app-governance-get-started.md#administrator-roles) pour afficher les données de gouvernance des applications.
>

Dans cette page, vous pouvez voir :

- Pour les applications compatibles OAuth qui utilisent l’API Microsoft Graph :

  - Nombre d’éléments dans votre client
  - Combien sont susceptibles d’être privilégiés
  - Combien sont susceptibles d’être hautement privilégiés

  À partir de ces informations, vous pouvez déterminer le niveau de risque pour votre organisation avec les applications sur-privilégiées et à privilèges élevés.

- Pour les alertes :

  - Nombre d’alertes actives de votre client
  - Nombre basé sur les détections de gouvernance des applications (**alertes de menace**)
  - Nombre d’alertes basées sur les stratégies d’application que vous avez en place (**alertes de stratégie**)
  - Les 10 dernières alertes

  À partir de ces informations, vous pouvez déterminer la vitesse à laquelle les alertes sont générées et le nombre relatif d’alertes détectées et basées sur des stratégies.

- Pour l’accès aux données et aux ressources :

  - Nombre total de données consultées par les applications dans le locataire via API Graph au cours des trois mois calendaires actuels et précédents. (Inclut uniquement l’utilisation du chargement et du téléchargement de courriers et de fichiers)
  - Consommation des données sur les trois mois calendaires actuels et précédents, divisés par type de ressource. (Inclut uniquement l’utilisation du chargement et du téléchargement de courriers et de fichiers)

  À partir de ces informations, vous pouvez déterminer s’il existe des pics anormaux d’accès aux données dans votre client Microsoft 365.
