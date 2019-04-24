---
title: Préparation des applications pour le bureau géré Microsoft
description: ''
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: be28760fc3facdb21643943ace11deda378d437c
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32289063"
---
# <a name="preparing-apps-for-microsoft-managed-desktop"></a>Préparation des applications pour le bureau géré Microsoft

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
Microsoft et les clients de bureau gérés Microsoft ont des responsabilités aussi importantes que les applications utilisées avec le bureau géré Microsoft.

## <a name="microsoft-responsibilities"></a>Responsabilités de Microsoft
**Applications Office 365** Microsoft fournira un service complet pour le déploiement, la mise à jour et la prise en charge d'applications Office 365 spécifiques. Tous les utilisateurs recevront le jeu de base d'Office 365 Click to Run, 64 bit version des applications incluses dans l'image de l'appareil afin qu'un utilisateur puisse devenir rapidement productif. Le projet et les applications Visio de la suite Office 365 sont titulaires d'une licence distincte.  Microsoft maNaged Desktop fournit des groupes de déploiement qui permettent à l'administrateur informatique de gérer des licences et de déployer ces applications de manière appropriée pour leur organisation. Microsoft prend en charge les utilisateurs finaux de ces applications par le biais des canaux de support de bureau géré Microsoft.

**Applications métiers** Microsoft offre aux administrateurs informatiques des outils permettant de gérer et de déployer leurs applications métiers (LOB) pour les utilisateurs finaux dans le cadre du produit Intune. Microsoft prend en charge les problèmes de déploiement d'applications, comme indiqué dans les [applications métiers](#line-of-business-applications) . 

**Déployer avec Intune** Intune sera lié à **Microsoft Store pour les entreprises lors de** l'intégration de bureau géré Microsoft, ce qui permet le déploiement d'applications achetées via Intune. Microsoft déploiera également l'application portail d'entreprise de Microsoft Store vers les utilisateurs finaux pour permettre aux administrateurs informatiques de fournir une expérience en libre-service pour leurs utilisateurs finaux.

**Gestion des applications** Microsoft peut identifier les applications restreintes qui ne conviennent pas à l'espace de travail moderne en raison de leur impact sur le système. Lorsqu'une telle application est identifiée, Microsoft avertit le client et cette application doit être supprimée du client. 

Pour plus d'informations sur les comportements d'application restreinte et les exigences des applications, voir [Microsoft Managed Desktop App Requirements](../service-description/mmd-app-requirements.md) .

## <a name="customer-responsibilities"></a>Responsabilités du client
La suite Office 365 est essentielle aux offres de productivité de Microsoft et est incluse dans la licence Microsoft 365 pour tous les utilisateurs de bureau géré Microsoft. Pendant que Microsoft déploie, met à jour et prend en charge les applications Office sur des appareils de bureau gérés par Microsoft, il existe toujours des zones dont le client est responsable.
- **Attribuer des licences** : les clients sont responsables de l'attribution des licences appropriées aux utilisateurs finaux pour Office 365. 
- **Ajouter des utilisateurs à des groupes de sécurité** : pour les clients avec des utilisateurs qui ont besoin de Project ou de Visio, l'administrateur informatique doit ajouter ces utilisateurs aux groupes de déploiement appropriés. Les administrateurs informatiques sont également responsables de la gestion de la fin de vie de ces utilisateurs. 
- **Deploy office 365 Add ons** : les clients sont responsables du déploiement de tous les plug-ins dans la suite Office 365 jugés nécessaires. 

Étant donné que les applications métier sont uniques pour chaque client, les clients sont responsables de la gestion de toutes les applications de leur organisation qui ne sont pas déployées par Microsoft. Cela inclut les opérations suivantes :
- Choisir les applications nécessaires et celles qui en ont besoin
- Affectation d'applications à ces utilisateurs
- Créer et gérer des groupes Azure Active Directory (AD) pour la gestion des affectations d'application 

Le client doit charger les applications métier vers Intune. Ils sont ensuite responsables du déploiement, de la mise à jour et de la mise en service de ces applications par rapport à leurs cycles de vie respectifs, ainsi que la gestion de la prise en charge de ces applications pour leurs utilisateurs.

## <a name="office-applications"></a>Applications Office
Dans le cadre de la licence Microsoft 365 E5, Office 365 standard suite (64 bits) est déployé par Microsoft. 

Pour plus d'informations, consultez la rubrique [Microsoft Managed Desktop Technologies](../intro/technologies.md) <!--- and the other applications licensed under Office 365 E5 may be deployed by the customer using Intune’s deployment tools.-->

## <a name="line-of-business-applications"></a>Applications métiers
Ce tableau résume les responsabilités dans les différentes phases pour les applications métiers (LOB). 

Éléments de travail de l'application |    Client    | Microsoft
--- | --- | ---
**Applications d'intégration** |  |
Identifier les applications nécessaires pour les groupes d'utilisateurs ciblés   | ![Oui](images/checkmark.png)  |
Créer et gérer des groupes Azure AD pour le déploiement d'applications | ![Oui](images/checkmark.png) |   
**EmPaquetage d'applications** |  |
Applications de package pour répondre aux normes de déploiement Intune |  ![Oui](images/checkmark.png) |  
Télécharger des applications vers Intune | ![Oui](images/checkmark.png)     |
Applications de test dans un environnement de bureau géré Microsoft |    ![Oui](images/checkmark.png) |  
Applications de test avec les utilisateurs finaux    | ![Oui](images/checkmark.png) |    
**Déploiement** | |
Gérer les utilisateurs et les affecter aux applications  | ![Oui](images/checkmark.png)  |
Les outils de déploiement Intune fournissent une application à des clients distants| |   ![Oui](images/checkmark.png)
Identifier et déployer les mises à jour des applications via Intune | ![Oui](images/checkmark.png)    |
Désinstaller et supprimer les applications lorsqu'elles ont été retirées    | ![Oui](images/checkmark.png) |    
**Gestion** | |
Obtention et attribution de licences |   ![Oui](images/checkmark.png)     |
Fournir une assistance aux utilisateurs finaux pour les applications métiers  | ![Oui](images/checkmark.png) |
Gérer les paramètres de l'application à distance    | ![Oui](images/checkmark.png) |

Pour plus d'informations sur les exigences de l'application métier, voir [Microsoft Managed Desktop application Requirements](../service-description/mmd-app-requirements.md) .


## <a name="intune-application-deployment"></a>Déploiement d'applications Intune
La gestion des applications peut être gérée via le portail d'administration de bureau géré Microsoft ou via le portail Intune. Le portail de gestion des applications Intune affiche les applications déployées pour Windows, Android et iOS. Le portail d'administration de bureau géré Microsoft limite l'affichage aux applications Windows 10. Les deux sont disponibles via le portail Azure. 
* [Notions de base sur la gestion des applications Intune](https://docs.microsoft.com/intune/app-management)
* [Ajouter des applications à Intune](https://docs.microsoft.com/intune/app-management)
   * [Ajouter une application métier](https://docs.microsoft.com/intune/lob-apps-windows)
   * [Ajouter des applications Win32 à Intune](https://docs.microsoft.com/intune/apps-win32-app-management)
   * [Ajouter des applications Web](https://docs.microsoft.com/intune/web-app)
* [Déployer des applications](https://docs.microsoft.com/intune/apps-deploy)
   * [Déployer des applications vers Windows 10](https://docs.microsoft.com/intune/apps-windows-10-app-deploy)
* Portail d'entreprise
   * [Déployer le portail d'entreprise](https://docs.microsoft.com/intune/store-apps-company-portal-app)
   * [Configurer l'application portail d'entreprise](https://docs.microsoft.com/intune/company-portal-app)
