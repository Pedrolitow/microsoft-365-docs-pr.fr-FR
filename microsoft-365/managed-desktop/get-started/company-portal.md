---
title: Installer les Portail d’entreprise Intune sur les appareils
description: Informations sur l’installation de l’application portail d’entreprise Microsoft Manged Desktop appareils
keywords: Microsoft Manged Desktop, Microsoft 365, Portail d’entreprise
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 2686ec818fd2c4c912e12df76bf35f2435e2625cf95b53f1bd5a24be4f93c1e8
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53898682"
---
# <a name="install-intune-company-portal-on-devices"></a>Installer les Portail d’entreprise Intune sur les appareils

Microsoft Manged Desktop nécessite que les administrateurs informatiques installent les Portail d’entreprise Intune pour leurs utilisateurs avec Microsoft Manged Desktop appareils. Voici quelques avantages pour votre organisation :
- Les utilisateurs disposent d’un seul endroit pour parcourir et installer les applications disponibles. 
- Les administrateurs informatiques peuvent organiser les applications par catégories pour leurs utilisateurs.  
- Certaines applications (comme Microsoft Project et Microsoft Visio) nécessitent Portail d’entreprise déployer avec Microsoft Manged Desktop.
- Les administrateurs informatiques peuvent personnaliser Portail d’entreprise pour leur organisation. Cela inclut la création d’images de marque, l’ajout de contacts de support local, etc. Pour plus d’informations, [voir How to Configure the Microsoft Intune Portail d’entreprise app](/intune/company-portal-app).   

Cette rubrique documente le processus de déploiement des Portail d’entreprise Intune à vos utilisateurs Microsoft Manged Desktop utilisateurs. Le processus global ressemble à ceci :
1. Acheter Portail d’entreprise de Microsoft Store pour Entreprises et synchroniser avec Intune
2. Affecter des Portail d’entreprise à vos utilisateurs
3. Communiquer les changements à vos utilisateurs

## <a name="step-1---purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>Étape 1 : acheter des Portail d’entreprise auprès Microsoft Store pour Entreprises et synchroniser avec Intune
Pour plus d’informations sur l’achat des applications et la synchronisation avec Intune, voir Microsoft Store pour Entreprises [applications dans](deploy-apps.md#msfb-apps) Deploy apps to *Microsoft Manged Desktop devices*.

Cette rubrique fournit des informations sur la façon de : 
- Acheter des Portail d’entreprise auprès Microsoft Store pour Entreprises 
- Forcer la synchronisation entre Intune et Microsoft Store pour Entreprises
- Vérifier la synchronisation active entre Intune et Microsoft Store pour Entreprises 

## <a name="step-2---assign-company-portal-to-your-users"></a>Étape 2 : affecter des Portail d’entreprise à vos utilisateurs
Après votre inscription dans Microsoft Manged Desktop, nous allons déployer automatiquement Portail d’entreprise sur votre client et installer l’application sur Microsoft Manged Desktop appareils de votre organisation.

## <a name="step-3---communicate-change-to-your-users"></a>Étape 3 : communiquer les changements à vos utilisateurs
En tant qu’administrateur informatique de votre organisation, il est important de faire savoir à vos utilisateurs comment utiliser les Portail d’entreprise votre organisation. Microsoft Manged Desktop recommande :
- Étapes d’installation des applications à partir du Portail d’entreprise. Pour plus d’informations, voir [Installer et partager des applications sur votre appareil.](/intune-user-help/install-apps-cpapp-windows)
- Comment envoyer des demandes aux administrateurs informatiques pour les applications qui ne sont pas actuellement disponibles. Pour plus d’informations, voir [Demander une application pour le travail ou l’école.](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school)  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. Déployer Portail d’entreprise Intune (cette rubrique)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)
