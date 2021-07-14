---
title: Déterminer la posture de conformité de votre application
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: 2fde19e385d4797e04c8f991efa673d33cea3b58
ms.sourcegitcommit: 997a21b83795789cda0a6b4a77f9985a3233d0c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2021
ms.locfileid: "53430671"
---
# <a name="determine-your-app-compliance-posture"></a>Déterminer la posture de conformité de votre application

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gouvernance des applications Microsoft vous permet d’évaluer rapidement la posture de conformité des applications tierces et leur accès aux données de votre client Microsoft 365 à partir de la page Vue d’ensemble de la gouvernance des applications du [Centre de conformité Microsoft 365](https://aka.ms/appgovernance).

![Page vue d’ensemble de la gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-overview.png)

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

  - Accès aux données de l’API d’application au cours des 90 derniers jours
  - Utilisation des principales ressources au cours des 90 derniers jours

  À partir de ces informations, vous pouvez déterminer s’il existe des pics anormaux d’accès aux données dans votre client Microsoft 365.
