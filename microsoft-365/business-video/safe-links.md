---
title: Gérer les liens fiables
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment gérer les liens fiables afin de protéger votre entreprise contre les sites malveillants.
ms.openlocfilehash: eabb2c1f71b1183867ffcb005ba4f7e44ed6e4b7
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702066"
---
# <a name="manage-safe-links"></a>Gérer les liens fiables

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender pour Office 365, anciennement Microsoft 365 ATP, ou Advanced Threat Protection, permet de protéger votre entreprise contre les sites malveillants lorsque des personnes cliquent sur des liens dans les applications Office.

## <a name="try-it"></a>Essayez !

1. Accédez au [Centre d’administration](https://admin.microsoft.com), puis sélectionnez **configuration**.
1. Faites défiler vers le bas pour **augmenter la protection contre les menaces avancées**. Sélectionnez **Afficher**, **gérer**, puis **DAV liens approuvés**.
1. Sous **stratégies qui s’appliquent à l’ensemble de l’organisation**, choisissez la stratégie **par défaut** , puis sélectionnez l’icône **modifier** .
1. Entrez l’URL que vous souhaitez bloquer.
1. Sélectionnez **utiliser les liens fiables dans les applications Office, Office pour iOS et Android**; Sélectionnez **ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables**; Sélectionnez **ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine**. Ces éléments peuvent déjà être sélectionnés si vous configurez la stratégie par défaut. Sélectionnez **Enregistrer**.
1. Sous **stratégies qui s’appliquent à des destinataires spécifiques**, choisissez **règle de liens approuvés recommandés**, puis sélectionnez l’icône **modifier** .
1. Sélectionnez **paramètres**, faites défiler vers le bas, entrez l’URL que vous ne souhaitez pas vérifier, puis sélectionnez l’icône **Ajouter** .
1. Sélectionnez **appliqué à**, puis sélectionnez votre nom de domaine. Sélectionnez les domaines supplémentaires auxquels la règle doit s’appliquer. Sélectionnez **Ajouter**, **OK**, puis **Enregistrer**.

Les liens fiables ATP sont désormais configurés. Autorisez jusqu’à 30 minutes pour que vos modifications prennent effet.

Lorsqu’un utilisateur reçoit un message électronique avec des liens, les liens sont analysés. Si les liens sont jugés fiables, ils seront cliquables. Toutefois, si le lien se trouve sur la liste bloquée, les utilisateurs verront un message indiquant qu’il a été bloqué.