---
title: Bureau géré Microsoft et ITIL
description: Met en corrélation les phases ITIL avec Bureau géré Microsoft et articles
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation, ITISM
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.openlocfilehash: e545b64670bb92c40465f1c50b2cb46b9fd7a8d8
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49841434"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Bureau géré Microsoft et ITIL

De nombreuses organisations trouvent utile de structurer leurs services itaux sur les lignes d’un modèle de service itatérisé (ITSM), tel [qu’ITIL](https://www.axelos.com/best-practice-solutions/itil). 

Bureau géré Microsoft permet à votre organisation de se conformer à de nombreux aspects clés de ces modèles ITSM formalisés. À l’aide de l’exemple ITIL, cet article vous aide à voir les connexions entre les phases et processus ITIL courants et les fonctionnalités d’Bureau géré Microsoft, le cas échéant. Ces informations s’appliquent uniquement à Bureau géré Microsoft partie de votre organisation.

Pour plus d’informations sur ITIL et ses phases et processus, consultez leur [documentation.](https://www.axelos.com/best-practice-solutions/itil)


## <a name="service-design"></a>Conception de service

Ce tableau présente les phases et processus ITIL clés pour Bureau géré Microsoft fonctionnalités, avec des liens vers notre documentation pour plus d’informations :



|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion au niveau du service     | Les délais de réponse sont définis pour les demandes de support et les incidents de l’administrateur.  |  [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)  |
|Gestion du catalogue de services     | La description du service détaillant les composants du service reste vraie selon l’état du service, disponible pour tous les clients actuels et intéressés.<br><br>Conditions préalables détaillées pour comprendre ce qui est nécessaire au fonctionnement du service.  | - [Bureau géré Microsoft de service](service-description/index.md)<br><br>- [Préparez-vous à l’inscription dans Bureau géré Microsoft](get-ready/index.md)  |
|Gestion de la sécurité des informations     | Informations de sécurité, y compris la sécurité des informations pour le service.<br><br> Stratégies de sécurité et autres informations sur la configuration des appareils.   | - [Sécurité dans Bureau géré Microsoft](service-description/security.md)<br><br>- [Configuration de l’appareil](service-description/device-policies.md)  |
|Gestion de la disponibilité     |  Bureau géré Microsoft équilibre la responsabilité avec votre organisation pour garantir la disponibilité du service.<br><br>Les administrateurs et les utilisateurs ont des itinéraires vers le support respectif en cas de problèmes de service ou de disponibilité. | - [Bureau géré Microsoft et surveillance](service-description/operations-and-monitoring.md)<br><br>- [Prise en charge des administrateurs pour Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)<br>- [Obtenir de l’aide pour les utilisateurs](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Transition de service


|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion des modifications     | Équilibre de responsabilité défini, vue d’ensemble des processus et types liés à la gestion des changements disponibles.  | [Bureau géré Microsoft et surveillance](service-description/operations-and-monitoring.md#change-management) |
|Gestion des publication et du déploiement     |  Bureau géré Microsoft gère les mises à jour pour les appareils inscrits au service.  | [Comment les mises à jour sont gérées dans Bureau géré Microsoft](service-description/updates.md)        |
|Gestion des ressources de service et de la configuration     | Des informations sur le déploiement de Bureau géré Microsoft organisation sont disponibles sur le portail d’administration informatique.  | [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md) |
|Gestion des connaissances     | Les informations sur Bureau géré Microsoft service sont tenues à jour sur ce site.   | [Historique des modifications de la documentation relative au Bureau géré Microsoft](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Opération de service


|Processus ITIL |Description  |Documentation  |
|---------|---------|---------|
|Gestion des événements     |  Des détails sur la surveillance des appareils sont fournis.<br><br>Les procédures d’exploitation standard pour Bureau géré Microsoft service sont détaillées. |  - [Sécurité dans Bureau géré Microsoft](service-description/security.md)<br>- [Bureau géré Microsoft et surveillance](service-description/operations-and-monitoring.md)       |
|Gestion des incidents  | Bureau géré Microsoft examiner et agir sur les incidents selon les définitions de gravité définies.  |  [Définitions de gravité des demandes de prise en charge](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Gestion de l’enrichissement des demandes     |  Le processus des demandes d’informations et des demandes de modification liées au service Bureau géré Microsoft est défini.         |[Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)         |
|Gestion des problèmes     | Tout problème avec le service doit être dirigé vers votre équipe de compte locale pour le moment. | Documentation en cours de développement |
|Gestion des accès     | Les composants et responsabilités de gestion des accès pour le client afin de s’assurer que les fonctionnalités sont détaillées.  | [Gestion des identités et des accès](service-description/security.md#identity-and-access-management)        |
