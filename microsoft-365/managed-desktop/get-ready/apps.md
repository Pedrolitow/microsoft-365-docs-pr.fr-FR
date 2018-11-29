---
title: Préparation des applications pour Microsoft géré du bureau
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: ebeb54bd5d1f50cbb6f78b1c8ad4a624c449b8c2
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867042"
---
# <a name="preparing-apps-for-microsoft-managed-desktop"></a>Préparation des applications pour Microsoft géré du bureau

<!--This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.-->

<!--Applications: supported/onboard/deployment -->
 
Les clients Microsoft et de bureau Microsoft ont également critique, encore différentes des responsabilités autour d’applications utilisées avec l’ordinateur de bureau Microsoft.

## <a name="microsoft-responsibilites"></a>Responsabilités de Microsoft
**Applications Office 365** Microsoft fournit un service complet pour le déploiement, la mise à jour et la prise en charge des applications Office 365 spécifiques. Tous les utilisateurs recevront l’ensemble de base d’Office 365 cliquez sur Exécuter, la version 64 bits d’applications inclus dans l’image du périphérique afin qu’un utilisateur peut être rapidement productif. Les applications de Project et Visio dans de la suite Office 365 sont une licence séparée.  Ordinateur de bureau Microsoft fournira des groupes de déploiement, l’administrateur informatique gérer les licences et déployer ces applications appropriées pour leur organisation. Microsoft prendra en charge les utilisateurs finaux de ces applications via les canaux Microsoft gérés bureau prennent en charge.

**Applications Line-of-business** Microsoft fournit des outils pour les administrateurs informatiques à gérer et à déployer leurs applications métier aux utilisateurs finaux dans le cadre du produit Intune. Microsoft prend en charge les problèmes de déploiement des applications comme indiqué dans les [applications métier de](#line-of-business-applications) 

**Déployer avec Intune** Intune sera liée au cours de bureau Microsoft embarquement permettant d’applications approvisionnées être déployé par le biais de Intune dans le **Magasin de Microsoft pour les entreprises** . Microsoft sera également déployer la version basée sur le web du portail d’entreprise pour les utilisateurs finaux afin que les administrateurs informatiques peuvent fournir une expérience en libre service pour les utilisateurs finaux.

**Gestion des applications** Microsoft peut identifier restreint les applications qui ne sont pas appropriées pour l’espace de travail moderne en raison de leur impact système. Lorsque ce type d’application est identifiée Microsoft avertit le client et cette application devront être supprimées à partir du client. 

## <a name="customer-responsibilities"></a>Responsabilités des clients
La Suite de 365 Office est au cœur des offres de productivité de Microsoft et est incluse dans la licence de 365 Microsoft pour tous les utilisateurs de l’ordinateur de bureau Microsoft. Alors que Microsoft déploie, met à jour et prend en charge les Applications Office pour les périphériques de bureau gérés Microsoft il y a encore des zones pour lequel le client est chargé.
- **Attribution de licences** - les clients sont chargés d’assigner les licences appropriés pour les utilisateurs finaux à Office 365. 
- **Ajouter des utilisateurs aux groupes de sécurité** - pour les clients avec des utilisateurs qui ont besoin de projet ou Visio, l’administrateur doit ajouter ces utilisateurs aux groupes de déploiement appropriée. Les administrateurs informatiques sont également chargés de gérer la fin de vie pour les utilisateurs. 
- **Déployer les modules Office 365 complémentaires** - les clients sont chargés de déployer un plug-in à la suite Office 365 qui sont jugés nécessaires. 

Étant donné que les applications de métier (LOB) sont uniques pour chaque client, les clients sont chargés de gérer toutes les applications au sein de leur organisation ne pas déployé par Microsoft. Cela inclut :
- Choisir les applications qui sont nécessaires, et qui a besoin
- Attribution d’applications à ces utilisateurs
- Créer et gérer des groupes d’Azure Active Directory (AD) pour la gestion des affectations de l’application 

Une fois que l’ensemble des applications métier a été identifié le client sera se procurer, attribuer une licence, empaqueter et tester ces applications dans l’environnement de bureau Microsoft. Le client doit télécharger et déployer des applications pour Intune à déployer, de mettre à jour et de mettre hors service leurs applications métier. Les clients sont chargés de gérer la prise en charge des applications métier pour leurs utilisateurs.
 

## <a name="office-applications"></a>Applications Office
Dans le cadre de la licence Microsoft 365 E5, Office 365 Standard Suite (64 bits) est déployée par Microsoft. 

Pour plus d’informations, voir [technologies Microsoft de bureau](../intro/technologies.md)<!--- and the other applications licensed under Office 365 E5 may be deployed by the customer using Intune’s deployment tools.-->

## <a name="line-of-business-applications"></a>Applications Line-of-business
Ce tableau récapitule les responsabilités entre les différentes phases pour les applications de métier (LOB). 

Éléments de travail d’application |    Client    | Microsoft
--- | --- | ---
**Applications d’intégration** |  |
Identifier les applications nécessaires pour les groupes d’utilisateurs ciblés   | ![Oui](images/checkmark.png)  |
Créer et gérer des groupes d’Azure AD pour le déploiement d’applications | ![Oui](images/checkmark.png) |   
**Empaquetage de l’application** |  |
Applications de package pour répondre aux normes de déploiement Intune |  ![Oui](images/checkmark.png) |  
Télécharger des applications pour Intune | ![Oui](images/checkmark.png)     |
Tester les applications dans un environnement de bureau Microsoft |    ![Oui](images/checkmark.png) |  
Applications de test avec les utilisateurs finaux    | ![Oui](images/checkmark.png) |    
**Déploiement** | |
Gérer et affecter des utilisateurs aux applications  | ![Oui](images/checkmark.png)  |
Outils de déploiement Intune propose application aux clients distants| |   ![Oui](images/checkmark.png)
Identifier et déployer des mises à jour de l’application via Intune | ![Oui](images/checkmark.png)    |
Désinstaller et supprimer des applications lorsqu’ils ont été supprimés    | ![Oui](images/checkmark.png) |    
**Gestion** | |
Se procurer et attribuer des licences |   ![Oui](images/checkmark.png)     |
Fournir la prise en charge de l’utilisateur final pour les applications métier de  | ![Oui](images/checkmark.png) |
Gérer les paramètres d’application à distance    | ![Oui](images/checkmark.png) |

Pour plus d’informations sur les conditions requises des applications métier, consultez [conditions requises des applications de bureau Microsoft](../service-description/mmd-app-requirements.md)

## <a name="resources"></a>Ressources
Alors que de nombreux services sont hors de portée pour les opérations de l’ordinateur de bureau Microsoft services sont les offres de Microsoft qui peuvent aider les clients à gérer leurs applications.

### <a name="windows-upgrade-readiness"></a>Préparation de mise à niveau de Windows
Un élément clé de la configuration de nouveaux périphériques Microsoft géré est de comprendre les applications qui sont nécessaires pour les utilisateurs d’appareils. Préparation de mise à niveau de Windows est un outil de Microsoft qui permet aux entreprises de comprendre le paysage de l’application à l’intérieur de leur entreprise et permet de consulter les données clées sur les applications, telles que :

- **Utilisation de l’application** : données de télémétrie est utilisée pour surveiller l’utilisation de l’application.
- **Compatibilité des applications** - préparation de mise à niveau examine chaque application et voit façon générale dont il a été déployé sur la dernière version de Windows 10 et évalue comment identifier s’il est « Prêt pour Windows ». Ces données vous aide à effectuer les tests d’efforts sur les applications qui ne sont pas déjà largement adoptées.

### <a name="intune-application-deployment"></a>Déploiement d’applications Intune
Gestion des applications peut être gérée via le portail d’administration de bureau géré Microsoft ou par le biais du portail Intune. Portail de gestion d’application de Intune montre applications déployées pour iOS, Android et Windows. Portail d’administration de bureau géré Microsoft limite l’affichage aux applications Windows 10. Les deux sont disponibles via le portail Azure. 
- [Concepts de base Intune application Gestion](https://docs.microsoft.com/intune/app-management)
- [Ajouter une application Windows 32](https://docs.microsoft.com/intune/lob-apps-windows)
- [Ajouter des applications web](https://docs.microsoft.com/intune/web-app)
- [Attribuer et déployer des applications à des groupes](https://docs.microsoft.com/intune/apps-deploy)

### <a name="application-packaging-standards"></a>Normes de création d’un package d’application
Pour déployer des applications Windows 32 via Intune, ils doivent être empaqueté en tant qu’un seul. MSI, un .aspx, ou. MSIX. Le type de package les plus courants pour Intune n’existe actuellement. MSI.
