---
title: Démarrage avec la détection et la correction des menaces d’application
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
description: Démarrage avec la détection et la correction des menaces d’application.
ms.openlocfilehash: 11084e54706f0c83faadf58048c205ba6ffee83e
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541236"
---
# <a name="get-started-with-app-threat-detection-and-remediation"></a>Démarrage avec la détection et la correction des menaces d’application

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

La gouvernance des applications Microsoft collecte les alertes de menace générées par des méthodes intégrées de détection de gouvernance des applications basées sur des activités d’application malveillantes et des alertes basées sur des stratégies générées par des stratégies d’application actives que vous créez.

Le premier emplacement pour afficher les alertes d’application est le tableau de bord de gouvernance des applications à [https://aka.ms/appgovernance](https://aka.ms/appgovernance).

![Page vue d’ensemble de la gouvernance des applications dans le Centre de conformité Microsoft 365 avec la section Détection et alertes de stratégie mise en évidence](..\media\manage-app-protection-governance\mapg-cc-overview-alerts.png)

Dans cette page de vue d’ensemble, la section **Détection et alertes de stratégie** répertorie les dernières alertes. Vous pouvez l’utiliser pour voir rapidement l’activité d’alerte d’application actuelle pour votre client.

Pour afficher toutes les alertes, sélectionnez l’onglet **Alertes** .

## <a name="whats-available-on-the-alerts-page"></a>Éléments disponibles sur la page Alertes

La page **Alertes** répertorie toutes les alertes basées sur la gouvernance des applications pour votre client.

![Page récapitulative des alertes de gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-alerts.png)

Chaque alerte répertoriée contient les informations suivantes :

- **Nom de l’alerte**: type de comportement anormal.
- **Nom de l’application**: l’application qui a généré l’alerte.
- **Gravité**: gravité attribuée par la gouvernance des applications pour les alertes qu’elle crée ou la gravité de la stratégie d’application qui a généré l’alerte.
- **Source**: origine de l’alerte, qui peut être le résultat d’une stratégie (stratégies créées par l’utilisateur), d’une détection (stratégies de détection intégrées) ou de MCAS.
- **État**: **Nouveau** indique une alerte qui n’a pas reçu d’état. Une fois attribué, l’état est **En cours** pendant l’examen ou **Résolu** pour les alertes qui ont été traitées par le biais d’une correction automatique ou manuelle.
- **Date de création**: date à laquelle l’alerte a été générée par la détection de la gouvernance des applications ou par le biais d’une stratégie d’application. Toutes les dates affichées sont indiquées dans le fuseau horaire local du Centre de conformité Microsoft 365.
- **Dernière activité**: date de la dernière modification de l’état de l’alerte. Toutes les dates affichées sont indiquées dans le fuseau horaire local du Centre de conformité Microsoft 365.

La liste d’alertes est triée par **Date de création** par défaut. Pour trier la liste en fonction d’un autre attribut, sélectionnez le nom de l’attribut.

Vous pouvez également exporter la liste d’alertes actuelle dans un fichier de valeurs séparées par des virgules (CSV). Par exemple, vous pouvez ouvrir le fichier CVS dans Microsoft Excel et trier la liste des alertes par **Gravité**, puis **Date de création**.

## <a name="next-step"></a>Étape suivante

[Examiner les alertes de détection d’anomalie](app-governance-anomaly-detection-alerts.md)
