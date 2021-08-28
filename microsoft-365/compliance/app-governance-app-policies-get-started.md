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
ms.openlocfilehash: 2f22e56195b94f07a6b8499bd69c60d65f37cce8
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58572238"
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

## <a name="next-step"></a>Étape suivante

[Créez une stratégie d’application.](app-governance-app-policies-create.md)
