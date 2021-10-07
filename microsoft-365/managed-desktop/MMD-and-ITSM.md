---
title: Bureau géré Microsoft et ITIL
description: Met en corrélation les phases ITIL avec Microsoft Manged Desktop et articles
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, ITISM
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ced0b27b5d9a47923b9738a3db50c2a8df0a5cbf
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60205760"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Bureau géré Microsoft et ITIL

De nombreuses organisations trouvent utile de structurer leurs services itaux sur les lignes d’un modèle de service itatérisé (ITSM), tel [qu’ITIL](https://www.axelos.com/best-practice-solutions/itil). 

Microsoft Manged Desktop permet à votre organisation de se conformer à de nombreux aspects clés de ces modèles ITSM formalisés. En utilisant ITIL comme exemple, cet article vous aide à voir les connexions entre les phases et processus ITIL courants et les fonctionnalités de Microsoft Manged Desktop, le cas échéant. Ces informations s’appliquent uniquement à Microsoft Manged Desktop partie de votre organisation.

Pour plus d’informations sur ITIL et ses phases et processus, consultez leur [documentation.](https://www.axelos.com/best-practice-solutions/itil)


## <a name="service-design"></a>Conception de service

Ce tableau est lié aux phases et processus ITIL clés pour Microsoft Manged Desktop fonctionnalités, avec des liens vers notre documentation pour plus d’informations :



|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion au niveau du service     | Les temps de réponse sont définis pour les demandes de support et les incidents de l’administrateur.  |  [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)  |
|Gestion du catalogue de services     | La description du service détaillant les composants du service reste vraie selon l’état du service, disponible pour tous les clients actuels et intéressés.<br><br>Conditions préalables détaillées pour comprendre ce qui est nécessaire au fonctionnement du service.  | - [Microsoft Manged Desktop description du service](service-description/index.md)<br><br>- [Préparez-vous à l’inscription dans Microsoft Manged Desktop](get-ready/index.md)  |
|Gestion de la sécurité des informations     | Informations de sécurité, y compris la sécurité des informations pour le service.<br><br> Stratégies liées à la sécurité et autres informations sur la configuration des appareils.   | - [Sécurité dans Microsoft Manged Desktop](service-description/security.md)<br><br>- [Configuration de l’appareil](service-description/device-policies.md)  |
|Gestion de la disponibilité     |  Microsoft Manged Desktop équilibre la responsabilité avec votre organisation pour garantir la disponibilité du service.<br><br>Les administrateurs et les utilisateurs ont des itinéraires vers le support respectif en cas de problèmes de service ou de disponibilité. | - [Microsoft Manged Desktop et surveillance](service-description/operations-and-monitoring.md)<br><br>- [Prise en charge des administrateurs pour Microsoft Manged Desktop](working-with-managed-desktop/admin-support.md)<br>- [Obtenir de l’aide pour les utilisateurs](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Transition de service


|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion des modifications     | Équilibre de responsabilité défini, vue d’ensemble des processus et types liés à la gestion des changements disponibles.  | [Microsoft Manged Desktop et surveillance](service-description/operations-and-monitoring.md#change-management) |
|Gestion des publication et du déploiement     |  Microsoft Manged Desktop gère les mises à jour pour les appareils inscrits au service.  | [Comment les mises à jour sont gérées dans Microsoft Manged Desktop](service-description/updates.md)        |
|Gestion des ressources de service et de la configuration     | Des informations sur le déploiement de Microsoft Manged Desktop organisation sont disponibles sur le portail d’administration informatique.  | [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md) |
|Gestion des connaissances     | Les informations sur Microsoft Manged Desktop service sont tenues à jour sur ce site.   | [Historique des modifications de la documentation relative au Bureau géré Microsoft](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Opération de service


|Processus ITIL |Description  |Documentation  |
|---------|---------|---------|
|Gestion des événements     |  Des informations détaillées sur la surveillance des appareils sont fournies.<br><br>Les procédures d’exploitation standard pour Microsoft Manged Desktop service sont détaillées. |  - [Sécurité dans Microsoft Manged Desktop](service-description/security.md)<br>- [Microsoft Manged Desktop et surveillance](service-description/operations-and-monitoring.md)       |
|Gestion des incidents  | Microsoft Manged Desktop examiner et agir sur les incidents par définition de gravité définie.  |  [Définitions de gravité des demandes de prise en charge](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Gestion de l’enrichissement des demandes     |  Le processus des demandes d’informations et des demandes de modification liées au service Microsoft Manged Desktop est défini.         |[Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)         |
|Gestion des problèmes     | Tout problème avec le service doit être dirigé vers votre équipe de compte locale pour le moment. | Documentation en cours de développement |
|Gestion des accès     | Les composants et responsabilités de gestion des accès pour le client afin de s’assurer que les fonctionnalités sont détaillées.  | [Gestion des identités et des accès](service-description/security.md#identity-and-access-management)        |
