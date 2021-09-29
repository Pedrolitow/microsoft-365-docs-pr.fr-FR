---
title: Démarrage avec des stratégies d’application
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
description: Démarrage avec En savoir plus sur les stratégies d’application.
ms.openlocfilehash: 72702dfb8962750a3e6161eaefa360f6189870e6
ms.sourcegitcommit: 835dcaf5d5e0b485dc3ac485ded8943046afe36c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2021
ms.locfileid: "59941990"
---
# <a name="get-started-with-app-policies"></a>Démarrage avec des stratégies d’application

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Les stratégies d’application pour la gouvernance des applications Microsoft vous permettent d’implémenter des conditions plus proactives ou réactives pour créer des alertes ou corriger automatiquement vos besoins spécifiques en matière de conformité des applications au sein de votre organisation.

Pour afficher la liste des stratégies d’application actuelles, accédez à **Centre de conformité Microsoft 365 > Gouvernance d’applications > Stratégies**.

![Page récapitulative des stratégies MAPG dans le Centre de conformité Microsoft 365.](..\media\manage-app-protection-governance\mapg-cc-policies.png)

## <a name="whats-available-on-the-app-policies-dashboard"></a>Éléments disponibles dans le tableau de bord des stratégies d’application

Vous pouvez voir le nombre de stratégies actives, inactives et d’audit, ainsi que les informations suivantes pour chaque stratégie :

- **Nom de la stratégie**
- **État**

  - **Actif**: toutes les actions et évaluations de stratégie sont actives.
  - **Inactif**: toutes les actions et l’évaluation de la stratégie sont désactivées.
  - **Mode d’audit**: l’évaluation de la stratégie est active (les alertes se déclenchent), mais les actions de stratégie sont désactivées.

- **Gravité**: niveau de gravité défini sur toutes les alertes déclenchées en raison de l’évaluation de cette stratégie comme true, qui fait partie de la configuration de la stratégie.
- **Nombre d’alertes actives**: alertes générées par la stratégie qui ont un statut **En cours** ou **Nouveau** .
- **Nombre total d’alertes**: alertes actives et alertes résolues pour cette stratégie.
- **Date de la dernière alerte**: date de la dernière alerte générée en raison de cette stratégie.
- **Dernière modification**: date de la dernière modification de cette stratégie.

La liste de stratégies est triée par **Dernière modification** par défaut. Pour trier la liste en fonction d’un autre attribut, sélectionnez le nom de l’attribut.

Lorsque vous sélectionnez une stratégie, vous obtenez un volet de stratégie détaillé avec les détails supplémentaires suivants :

- **Description**: explication plus détaillée de l’objectif de la stratégie.
- **Créé par**: nom d’utilisateur principal (UPN) du compte qui a créé la stratégie.
- Liste des alertes totales et actives générées par cette stratégie.

Vous pouvez modifier ou supprimer une stratégie d’application en sélectionnant **Modifier** ou **Supprimer** dans le volet de stratégie détaillé ou en sélectionnant les points de suspension verticaux de la stratégie dans la liste des stratégies.

Vous pouvez également :

- Créez une stratégie. Vous pouvez commencer par une stratégie d’utilisation d’application ou une stratégie d’autorisations.
- Exportez la liste de stratégies dans un fichier de valeurs séparées par des virgules (CSV). Par exemple, vous pouvez ouvrir le fichier CVS dans Microsoft Excel et trier les stratégies par **Gravité**, puis **Nombre total d’alertes**.
- Recherchez dans la liste des stratégies.

## <a name="edit-an-existing-policy"></a>Modifier une stratégie existante

1. Dans le portail de gouvernance des applications, sélectionnez l’onglet **Stratégies**.
1. Sélectionnez la stratégie que vous souhaitez modifier. Un panneau s’ouvrira sur le côté droit avec les détails de la stratégie existante.
1. Sélectionnez **Modifier**.
1. Vous ne pouvez pas modifier le nom de la stratégie une fois créée, mais vous pouvez modifier la description et la gravité de la stratégie. Sélectionnez **Suivant**.
1. Choisissez si vous souhaitez continuer à utiliser les paramètres de stratégie existants ou les personnaliser. Sélectionnez **Non. Je souhaite personnaliser la stratégie** pour apporter des modifications. Sélectionnez **Suivant**.
1. Choisissez si cette stratégie s’appliquera à toutes les applications ou aux applications que vous spécifiez dans la liste. Sélectionnez **Ajouter des applications** pour ajouter d’autres applications à la liste si vous appliquez la stratégie à des applications spécifiques. Sélectionnez **Suivant**.
1. Choisissez s’il faut modifier ou non les conditions existantes de la stratégie. Si vous choisissez de modifier les conditions, sélectionnez **Modifier les conditions**. Sélectionnez **Suivant**.
1. Choisissez s’il faut désactiver ou non l’application si elle déclenche les conditions de stratégie. Sélectionnez **Suivant**.
1. Définissez l’état de la stratégie sur Audit, Actif ou Inactif. Sélectionnez **Suivant**.
1. Passez en revue vos choix de paramètres pour la stratégie et si tout est comme vous le souhaitez, sélectionnez **Envoyer**.

## <a name="next-step"></a>Étape suivante

[Créez une stratégie d’application.](app-governance-app-policies-create.md)
