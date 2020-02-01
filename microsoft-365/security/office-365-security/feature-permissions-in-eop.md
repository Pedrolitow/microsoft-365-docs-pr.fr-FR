---
title: Autorisations des fonctionnalités dans EOP
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 1/30/2018
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 34674847-a6b7-4a7e-9eaa-b64f22bc150d
description: Les autorisations nécessaires à l'exécution de tâches de gestion de Microsoft Exchange Online Protection (EOP) varient selon les fonctionnalités gérées.
ms.openlocfilehash: 2129df7faaa977d59f8af8082291520d33bc9cc7
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599311"
---
# <a name="feature-permissions-in-eop"></a>Autorisations des fonctionnalités dans EOP

Les autorisations requises pour effectuer des tâches de gestion d’Exchange Online Protection (EOP) varient en fonction de la fonctionnalité que vous gérez.

Pour configurer EOP, vous devez être un administrateur global Office 365 ou un administrateur d'entreprise Exchange (le groupe de rôles Gestion de l'organisation).

## <a name="exchange-online-protection-permissions"></a>Autorisations Exchange Online Protection

Consultez le tableau suivant afin de déterminer les autorisations requises pour gérer les fonctionnalités EOP. Si une fonctionnalité affiche plusieurs groupes de rôles, seul l’un de ces groupes de rôles doit vous être attribué pour que vous puissiez exploiter cette même fonctionnalité.

|**Fonctionnalité**|**Autorisations requises**|
|:-----|:-----|
|Anti-programme malveillant|Gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Anti-spam|Gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Règles de flux de messagerie|Gestion de l’organisation <br/><br/> Gestion des enregistrements|
|Domaines|Gestion de l’organisation <br/><br/> Afficher uniquement la gestion de l’organisation|
|Protection avancée contre les menaces (ATP)|Gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Connecteurs Office 365|Gestion de l’organisation|
|Suivi des messages|Gestion de l’organisation <br/><br/> Afficher uniquement la gestion de l’organisation|
|Configuration de l'organisation|Gestion de l’organisation|
|Quarantaine|Gestion de l’organisation <br/><br/> Afficher uniquement la gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Utilisateurs, contacts et groupes de rôles|Gestion de l’organisation <br/><br/> Afficher uniquement la gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Groupes de sécurité et groupes de distribution|Gestion de l’organisation <br/><br/> Afficher uniquement la gestion de l’organisation <br/><br/> Gestion de l’hygiène|
|Affichage des rapports|Gestion de l’Organisation : accès aux rapports de protection du courrier électronique. <br/><br/> Destinataires en affichage seul : accès aux rapports de protection du courrier électronique.  <br/><br/> Gestion de la conformité : accès aux rapports de protection de messagerie et aux rapports de protection contre la perte de données (si votre abonnement dispose de fonctionnalités DLP).|
