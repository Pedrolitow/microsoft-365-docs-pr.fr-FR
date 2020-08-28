---
title: Bureau géré Microsoft et ITIL
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, ITISM
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.openlocfilehash: 05bd5a2ee36633b7ccf9ae61e601988a7268bb2c
ms.sourcegitcommit: abf63669daf12993ad3353e4b578f41c8910b20f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "47289804"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Bureau géré Microsoft et ITIL

De nombreuses organisations sont précieuses pour structurer leurs services informatiques le long des lignes d’un modèle de service informatique formalisé (ITSM), tel qu' [ITIL](https://www.axelos.com/best-practice-solutions/itil). 

Microsoft Managed Desktop permet à votre organisation de se conformer à de nombreux aspects clés de ces modèles ITSM. À l’aide d’ITIL comme exemple, cette rubrique vous permet de voir les connexions entre les phases et les processus ITIL courants et les fonctionnalités de bureau géré Microsoft équivalentes, le cas échéant. Cela s’applique uniquement à la partie bureau géré Microsoft de votre organisation.

Pour plus d’informations sur ITIL et ses phases et processus, consultez leur [documentation](https://www.axelos.com/best-practice-solutions/itil).


## <a name="service-design"></a>Conception de service

Cette table associe les principales phases et processus ITIL aux fonctionnalités de bureau géré Microsoft, avec des liens vers notre documentation pour plus d’informations :



|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion des niveaux de service     | Les temps de réponse sont définis pour les demandes et les incidents pris en charge par l’administrateur.  |  [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)  |
|Gestion du catalogue de services     | Description du service le détail des composants du service est conservé pour l’état du service, disponible pour tous les clients actuels et intéressés.<br><br>Conditions préalables détaillées pour comprendre ce qui est nécessaire pour exploiter le service.  | - [Description du service Microsoft Managed Desktop](service-description/index.md)<br><br>- [Se préparer à l’enregistrement dans le bureau géré Microsoft](get-ready/index.md)  |
|Gestion de la sécurité des informations     | Informations de sécurité, notamment la sécurité des informations pour le service.<br><br> Stratégies liées à la sécurité et autres informations sur la configuration des appareils.   | - [Sécurité dans le bureau géré Microsoft](service-description/security.md)<br><br>- [Configuration de l’appareil](service-description/device-policies.md)  |
|Gestion de la disponibilité     |  Le bureau géré Microsoft équilibre la responsabilité avec votre organisation pour garantir la disponibilité du service.<br><br>Les administrateurs et les utilisateurs ont des itinéraires vers la prise en charge correspondante en cas de problèmes de service ou de disponibilité. | - [Surveillance et opérations du bureau géré Microsoft](service-description/operations-and-monitoring.md)<br><br>- [Prise en charge des administrateurs pour le bureau géré Microsoft](working-with-managed-desktop/admin-support.md)<br>- [Obtenir de l’aide pour les utilisateurs](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Transition de service


|Processus ITIL |Description  |Documentation |
|---------|---------|---------|
|Gestion des modifications     | Définition du solde de responsabilité, de la présentation du processus et des types liés à la gestion des modifications disponible.  | [Surveillance et opérations du bureau géré Microsoft](service-description/operations-and-monitoring.md#change-management) |
|Gestion de la publication et du déploiement     |  Microsoft Managed Desktop gère les mises à jour des périphériques qui sont apportés au service.  | [Gestion des mises à jour dans le bureau géré Microsoft](service-description/updates.md)        |
|Gestion des ressources et des biens de service     | Les informations relatives au déploiement de bureau géré Microsoft de votre organisation sont disponibles sur le portail d’administration informatique.  | [Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md) |
|Gestion des connaissances     | Les informations sur le service bureau géré Microsoft sont tenues à jour sur ce site.   | [Historique des modifications de la documentation relative au Bureau géré Microsoft](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Opération de service


|Processus ITIL |Description  |Documentation  |
|---------|---------|---------|
|Gestion des événements     |  Des détails sur la surveillance des appareils sont fournis.<br><br>Les procédures de fonctionnement standard du service de bureau géré Microsoft sont détaillées. |  - [Sécurité dans le bureau géré Microsoft](service-description/security.md)<br>- [Surveillance et opérations du bureau géré Microsoft](service-description/operations-and-monitoring.md)       |
|Gestion des incidents  | Microsoft Managed Desktop examinera et agira sur les incidents par définition de gravité définie.  |  [Prendre en charge les définitions de gravité des demandes](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Gestion des demandes d’acceptation de requêtes     |  Processus de définition des demandes d’informations et de demandes de modification relatives au service de bureau géré Microsoft.         |[Aide administrateur pour le Bureau géré Microsoft](working-with-managed-desktop/admin-support.md)         |
|Gestion des problèmes     | Tous les problèmes liés au service doivent être dirigés vers votre équipe de compte local pour le moment. | Documentation en cours de développement |
|Gestion des accès     | Les composants de gestion des accès et les responsabilités du client pour garantir la fonctionnalité sont détaillés.  | [Gestion des identités et des accès](service-description/security.md#identity-and-access-management)        |
