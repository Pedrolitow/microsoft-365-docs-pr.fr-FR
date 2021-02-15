---
title: Bureau géré Microsoft et ITIL
description: Met en corrélation les phases ITIL avec les informations et articles du Bureau géré Microsoft
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

Bureau géré Microsoft permet à votre organisation de se conformer à de nombreux aspects clés de ces modèles ITSM formalisés. En utilisant ITIL comme exemple, cet article vous aide à voir les connexions entre les phases et processus ITIL courants et les fonctionnalités de Bureau géré Microsoft équivalentes, le cas échéant. Ces informations s’appliquent uniquement à la partie Bureau géré Microsoft de votre organisation.

Pour plus d’informations sur ITIL et ses phases et processus, consultez leur [documentation.](https://www.axelos.com/best-practice-solutions/itil)


## <a name="service-design"></a>Conception de service

Ce tableau lie les phases et processus ITIL clés aux fonctionnalités du Bureau géré Microsoft, avec des liens vers notre documentation pour plus d’informations :



|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion au niveau du service     | Les temps de réponse sont définis pour les demandes de support et les incidents de l’administrateur.  |  [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)  |
|Gestion du catalogue de services     | La description de service détaillant les composants du service reste vraie pour l’état du service, disponible pour tous les clients actuels et intéressés.<br><br>Conditions préalables détaillées pour comprendre ce qui est nécessaire au fonctionnement du service.  | - [Description du service Bureau géré Microsoft](service-description/index.md)<br><br>- [Préparez-vous à l’inscription dans Bureau géré Microsoft](get-ready/index.md)  |
|Gestion de la sécurité des informations     | Informations de sécurité, y compris la sécurité des informations pour le service.<br><br> Stratégies de sécurité et autres informations sur la configuration des appareils.   | - [Sécurité dans le Bureau géré Microsoft](service-description/security.md)<br><br>- [Configuration de l’appareil](service-description/device-policies.md)  |
|Gestion de la disponibilité     |  Bureau géré Microsoft équilibre la responsabilité avec votre organisation pour garantir la disponibilité du service.<br><br>Les administrateurs et les utilisateurs ont des itinéraires vers le support respectif en cas de problèmes de service ou de disponibilité. | - [Surveillance et opérations du Bureau géré Microsoft](service-description/operations-and-monitoring.md)<br><br>- [Prise en charge par l’administrateur du Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)<br>- [Obtenir de l’aide pour les utilisateurs](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Transition de service


|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion des modifications     | Équilibre de responsabilité défini, vue d’ensemble des processus et types liés à la gestion des changements disponibles.  | [Surveillance et opérations du Bureau géré Microsoft](service-description/operations-and-monitoring.md#change-management) |
|Gestion des publication et du déploiement     |  Bureau géré Microsoft gère les mises à jour pour les appareils inscrits au service.  | [Gestion des mises à jour dans Le Bureau géré Microsoft](service-description/updates.md)        |
|Gestion des ressources de service et de la configuration     | Des informations sur le déploiement du Bureau géré Microsoft de votre organisation sont disponibles sur le portail d’administration informatique.  | [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md) |
|Gestion des connaissances     | Les informations sur le service Bureau géré Microsoft sont tenues à jour sur ce site.   | [Historique des modifications de la documentation relative au Bureau géré Microsoft](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Opération de service


|Processus ITIL |Description  |Documentation  |
|---------|---------|---------|
|Gestion des événements     |  Des informations détaillées sur la surveillance des appareils sont fournies.<br><br>Les procédures d’exploitation standard pour le service Bureau géré Microsoft sont détaillées. |  - [Sécurité dans le Bureau géré Microsoft](service-description/security.md)<br>- [Surveillance et opérations du Bureau géré Microsoft](service-description/operations-and-monitoring.md)       |
|Gestion des incidents  | Bureau géré Microsoft examine et agit sur les incidents selon les définitions de gravité définies.  |  [Définitions de gravité des demandes de prise en charge](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Gestion de l’enrichissement des demandes     |  Le processus des demandes d’informations et des demandes de modification liées au service Bureau géré Microsoft est défini.         |[Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)         |
|Gestion des problèmes     | Tout problème avec le service doit être dirigé vers votre équipe de compte locale pour le moment. | Documentation en cours de développement |
|Gestion des accès     | Les composants et responsabilités de gestion des accès pour le client afin de s’assurer que les fonctionnalités sont détaillées.  | [Gestion des identités et des accès](service-description/security.md#identity-and-access-management)        |
