---
title: Corriger les menaces liées aux applications
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
description: Corrigez les menaces liées aux applications.
ms.openlocfilehash: 3b84594aa990516b6ecb340d6b8ffbd8d6d1a544c9c1e3dddeb691044e221424
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53836432"
---
# <a name="remediate-app-threats"></a>Corriger les menaces liées aux applications

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Vous corrigez les menaces d’application pour votre client Microsoft 365 via la page **Alertes** de la section Gouvernance des applications Microsoft du Centre de conformité Microsoft 365.

![Page récapitulative des alertes de gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-alerts.png)

La page **Alertes** répertorie par défaut les nouvelles alertes de menace générées par la gouvernance des applications et les alertes basées sur des stratégies générées par des stratégies d’application actives. Vous pouvez afficher les détails d’une alerte spécifique en la sélectionnant, ce qui ouvre un volet d’alerte avec des informations supplémentaires sur l’alerte et la possibilité de modifier son état.

![Page de détails de l’alerte de gouvernance des applications dans le Centre de conformité Microsoft 365](..\media\manage-app-protection-governance\mapg-cc-alerts-alert.png)

Dans ce volet, vous pouvez obtenir ces informations supplémentaires :

- Détails supplémentaires sur l’alerte à partir du champ **Description**.
- Nom de la stratégie d’application qui a généré l’alerte à partir du champ **Nom de stratégie**. Vous pouvez également sélectionner **Afficher la stratégie** pour accéder à la stratégie d’application qui a généré l’alerte.

Les stratégies d’application que vous avez configurées pour la correction automatique à partir de **Action** ont l’état **Résolu**.

Vous pouvez corriger une alerte d’application en procédant comme suit :

1. Investigation : examinez les informations de l’alerte et remplacez son état par **Marque en cours**.
2. Résolution : après votre examen et, si nécessaire, la détermination des modifications apportées à la stratégie d’application ou de la prise en charge continue des applications dans votre client, remplacez son état par **Résolu**.

En fonction des modèles d’alerte d’application, vous pouvez mettre à jour la stratégie d’application appropriée et modifier son paramètre **Action** pour effectuer une correction automatique. Cela supprime votre besoin d’examiner et de résoudre manuellement les futures alertes générées par la stratégie d’application. Pour plus d’informations, consultez [Gérer vos stratégies d’application](app-governance-app-policies-manage.md).
