---
title: Analyse des applications & rapports - Centre de sécurité
description: Découvrez comment obtenir plus d’informations sur l’utilisation des applications cloud dans votre organisation. Inclut différents types d’applications, leur niveau de risque et les alertes.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, applications
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: ed5fcfc16c08272a6a1d55af210ab48528538048
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930521"
---
# <a name="app-monitoring-and-reporting-in-the-microsoft-365-security-center"></a>Surveillance des applications et rapports dans le Centre de sécurité Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Ces rapports fournissent plus d’informations sur la façon dont les applications cloud sont utilisées dans votre organisation. Inclut différents types d’applications, leur niveau de risque et les alertes.

## <a name="monitor-email-accounts-at-risk"></a>Surveiller les comptes de messagerie à risque

**La protection de la** messagerie affiche les comptes de messagerie à risque. Vous pouvez sélectionner un compte à examiner plus en détail dans le Centre de sécurité Microsoft Defender.

![Carte de protection du courrier électronique](../../media/email-protection.png)

## <a name="monitor-app-permissions-granted-by-users"></a>Surveiller les autorisations d’application accordées par les utilisateurs

Sécurité des applications cloud : les applications **OAuth** répertorient les applications découvertes par Cloud App Security qui ont obtenu des autorisations par les utilisateurs. Le catalogue de risques de Cloud App Security inclut plus de 16 000 applications évaluées à l’aide de plus de 70 facteurs de risque.

Les facteurs de risque commencent par des informations générales, telles que l’éditeur d’application. Il passe ensuite aux mesures et contrôles de sécurité, par exemple si l’application prend en charge le chiffrement au repos ou fournit un journal d’audit de l’activité des utilisateurs.

![Carte d’application OAuth Cloud App Security](../../media/cloud-app-security-oauth-apps.png)

## <a name="monitor-cloud-app-user-accounts"></a>Surveiller les comptes d’utilisateur d’application cloud

**Les comptes d’application cloud pour la révision** répertorient les comptes qui peuvent nécessiter une attention particulière.

![Comptes d’application cloud pour la carte de révision](../../media/cloud-app-accounts-for-review.png)

## <a name="understand-which-cloud-apps-are-used"></a>Comprendre quelles applications cloud sont utilisées

**Les applications cloud découvertes (catégories)** indiquent les types d’applications utilisés dans votre organisation. Il est lié au tableau de bord de découverte cloud dans Cloud App Security. Pour plus d’informations, [voir Démarrage rapide : Travailler avec les applications découvertes.](https://docs.microsoft.com/cloud-app-security/discovered-apps)  

![Carte des catégories d’applications cloud découvertes](../../media/discovered-cloud-apps-categories.png)

## <a name="monitor-where-users-access-cloud-apps"></a>Surveiller l’endroit où les utilisateurs accèdent aux applications cloud

**Les emplacements d’activité des applications cloud** indiquent où les utilisateurs accèdent aux applications cloud.

![Carte d’emplacements d’activité de l’application cloud](../../media/cloud-app-activity-locations.png)

## <a name="monitor-health-for-infrastructure-workloads"></a>Surveiller l’état des charges de travail d’infrastructure

**L’état de l’infrastructure** affiche des alertes d’état pour les charges de travail d’infrastructure dans Azure Defender.

Azure Defender fournit une gestion unifiée de la sécurité et Defender pour Office 365 sur les charges de travail sur site et dans le cloud. Vous pouvez collecter, rechercher et analyser des données de sécurité à partir de différentes sources, y compris des pare-feux et d’autres solutions partenaires.

Pour plus d’informations, [voir la documentation d’Azure Defender.](https://docs.microsoft.com/azure/security-center/)

![Carte d’état de l’infrastructure](../../media/infrastructure-health.png)
