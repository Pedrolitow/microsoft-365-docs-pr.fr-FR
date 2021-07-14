---
title: Démarrage avec visibilité et insights
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
description: Démarrage avec visibilité et insights.
ms.openlocfilehash: 12c1a01667b1bda545b619e931d99132e6611e35
ms.sourcegitcommit: 41c7f7bd5c808ee5ceca0f6efe13d4e67da0262b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2021
ms.locfileid: "53420134"
---
# <a name="get-started-with-visibility-and-insights"></a>Démarrage avec visibilité et insights

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Le premier endroit pour commencer est le tableau de bord de gouvernance des applications à [https://compliance.microsoft.com/appgovernance](https://compliance.microsoft.com/appgovernance). Notez que votre compte de connexion doit avoir l’un des [ces rôles d’administrateur de gouvernance des applications](app-governance-get-started.md#administrator-roles) pour afficher les données de gouvernance des applications.

![Page vue d’ensemble de la gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-overview.png)

Vous pouvez également accéder au tableau de bord de gouvernance des applications à partir de **Centre d’administration Microsoft 365 > Centre de conformité Microsoft 365 > Gouvernance des applications > Page vue d’ensemble**.

## <a name="whats-available-on-the-dashboard"></a>Éléments disponibles sur le tableau de bord

Le tableau de bord contient un résumé des composants de l’écosystème d’applications Microsoft 365 dans le client :

- **Résumé du client**: nombre de catégories d’applications et d’alertes clés.
- **Alertes de détection et de stratégie**: alertes actives les plus récentes dans le client
- **Accès aux données et aux ressources**: agréger l’accès à l’API d’application et l’utilisation globale des ressources principales dans le client. Placez la souris sur chaque colonne du mois dans le graphique pour voir la valeur correspondante.
- **Améliorez la protection et la gouvernance de vos applications**: actions recommandées telles que la création d’une stratégie d’utilisation ou d’autorisations d’application.
- **Top des applications par catégories**: les principales applications triées par catégories :
  
  - **Toutes les catégories**: trie toutes les catégories disponibles.
  - **Privilèges élevés**: un privilège élevé est une catégorie déterminée en interne basée sur l’apprentissage automatique et les signaux de la plateforme.
  - **Sur-privilégié**: lorsque la gouvernance des applications reçoit des données de télémétrie qui indiquent qu’une autorisation accordée à une application n’a pas été utilisée au cours des 90 derniers jours, cette application est sur-privilégiée. La gouvernance des applications doit fonctionner pendant au moins 90 jours pour déterminer si une application est sur-privilégiée.  
  - **Non vérifié** : les applications qui n’ont pas reçu de[certification de l’éditeur](https://docs.microsoft.com/azure/active-directory/develop/publisher-verification-overview) sont considérées comme non vérifiées.
  - **Application uniquement**: [les autorisations d’application](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#permission-types) sont utilisées par les applications qui peuvent s’exécuter sans utilisateur connecté. Les applications disposant d’autorisations d’accès aux données sur le client sont potentiellement plus risquées.
  - **Nouvelles applications**: nouvelles applications Microsoft 365 qui ont été inscrites au cours des sept derniers jours.  

## <a name="next-step"></a>Étape suivante

[Obtenez des insights détaillés sur une application spécifique](app-governance-visibility-insights-view-apps.md).
