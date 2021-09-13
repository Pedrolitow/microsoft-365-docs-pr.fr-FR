---
title: Démarrage avec visibilité et insights
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
description: Démarrage avec visibilité et insights.
ms.openlocfilehash: ac99e9112dc7e0278243121a8530326c88f333dc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181421"
---
# <a name="get-started-with-visibility-and-insights"></a>Démarrage avec visibilité et insights

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Le premier endroit pour commencer est le tableau de bord de gouvernance des applications à [https://aka.ms/appgovernance](https://aka.ms/appgovernance). Notez que votre compte de connexion doit avoir l’un des [ces rôles d’administrateur de gouvernance des applications](app-governance-get-started.md#administrator-roles) pour afficher les données de gouvernance des applications.

![Page vue d’ensemble de la gouvernance des applications dans le Centre de conformité Microsoft 365.](..\media\manage-app-protection-governance\mapg-cc-overview.png)

Vous pouvez également accéder au tableau de bord de gouvernance des applications à partir de **Office 365 > Centre de conformité Microsoft 365 > Gouvernance des applications > Page Vue d’ensemble**.

## <a name="whats-available-on-the-dashboard"></a>Éléments disponibles sur le tableau de bord

Le tableau de bord contient un résumé des composants de l’écosystème d’applications Microsoft 365 dans le client :

- **Résumé du client**: nombre de catégories d’applications et d’alertes clés.
- **Principales alertes** : les 10 alertes actives les plus récentes dans le client
- **Accès aux données et aux ressources** : Placez la souris sur chaque colonne du mois dans le graphique pour voir la valeur correspondante.
  - **Accès aux données au cours des quatre derniers mois** : effectue le suivi du nombre total de données consultées par toutes les applications du client via API Graph au cours des quatre derniers mois calendaires. Inclut uniquement l’utilisation du chargement/du téléchargement de courriers et de fichiers.
  - **Accès aux données des principales ressources au cours des quatre derniers mois** : consommation des données au cours des quatre derniers mois calendaires, répartis par type de ressource. Inclut uniquement l’utilisation du chargement/du téléchargement de courriers et de fichiers
- **Améliorez la protection et la gouvernance de vos applications**: actions recommandées telles que la création d’une stratégie d’utilisation ou d’autorisations d’application.
- **Top des applications par catégories**: les principales applications triées par catégories :
  
  - **Toutes les catégories**: trie toutes les catégories disponibles.
  - **Privilèges élevés**: un privilège élevé est une catégorie déterminée en interne basée sur l’apprentissage automatique et les signaux de la plateforme.
  - **Sur-privilégié**: lorsque la gouvernance des applications reçoit des données de télémétrie qui indiquent qu’une autorisation accordée à une application n’a pas été utilisée au cours des 90 derniers jours, cette application est sur-privilégiée. La gouvernance des applications doit fonctionner pendant au moins 90 jours pour déterminer si une application est sur-privilégiée.  
  - **Non vérifié** : les applications qui n’ont pas reçu de [certification de l’éditeur](/azure/active-directory/develop/publisher-verification-overview) sont considérées comme non vérifiées.
  - **Application uniquement**: [les autorisations d’application](/azure/active-directory/develop/v2-permissions-and-consent#permission-types) sont utilisées par les applications qui peuvent s’exécuter sans utilisateur connecté. Les applications disposant d’autorisations d’accès aux données sur le client sont potentiellement plus risquées.
  - **Nouvelles applications**: nouvelles applications Microsoft 365 qui ont été inscrites au cours des sept derniers jours.  

## <a name="view-app-insights"></a>Afficher les informations sur l’application

L’un des principaux avantages de la gouvernance des applications est la possibilité d’afficher rapidement les alertes et les informations de l’application. Pour afficher des informations pour vos applications :

1. Sur la page du portail de gouvernance de votre application, sélectionnez **Applications**.
1. Utilisez la liste déroulante **Catégories** pour sélectionner l’une des options suivantes :
    - Toutes les applications
    - Privilège élevé
    - Avec trop de privilèges
    - Éditeur non vérifié
    - Application uniquement
    - Nouvelles applications
1. Sélectionnez le nom d’une application pour afficher les détails. Vous pouvez sélectionner plusieurs applications pour les enregistrer en tant que requête enregistrée en plaçant une coche à gauche du nom de l’application. La sélection d’un nom d’application ouvre un volet d’informations à droite, comme le montre le graphique suivant.

:::image type="content" source="../media/manage-app-protection-governance/app-governance-app-insight.png" alt-text="Image illustrant le volet d’informations d’une application sélectionnée.":::

> [!NOTE]
> Les applications répertoriées dépendent des applications présentes dans votre client.

Le volet d’informations vous permet également d’afficher l’utilisation de l’application au cours des 30 derniers jours, les utilisateurs qui ont donné leur consentement à l’application et les autorisations attribuées à l’application. Un administrateur peut examiner l’activité et les autorisations d’une application qui génère des alertes et prendre la décision de désactiver l’application à l’aide du bouton **Désactiver l’application** dans le volet Détails.

## <a name="next-step"></a>Étape suivante

[Obtenez des insights détaillés sur une application spécifique](app-governance-visibility-insights-view-apps.md).
