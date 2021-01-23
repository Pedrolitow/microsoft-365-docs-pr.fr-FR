---
title: Installer le portail d’entreprise Intune sur les appareils
description: Informations sur l’installation de l’application portail d’entreprise sur les appareils de bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, Portail d’entreprise
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: bddf46e451408e4f17e58cc62186b7cd6cefb382
ms.sourcegitcommit: ba830e85899f247e5a1e117d63e09e4d5b8a8020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49939283"
---
# <a name="install-intune-company-portal-on-devices"></a>Installer le portail d’entreprise Intune sur les appareils

Bureau géré Microsoft nécessite que les administrateurs informatiques installent le portail d’entreprise Intune pour leurs utilisateurs avec les appareils bureau géré Microsoft. Voici quelques avantages pour votre organisation :
- Les utilisateurs disposent d’un seul endroit pour parcourir et installer les applications disponibles. 
- Les administrateurs informatiques peuvent organiser les applications par catégories pour leurs utilisateurs.  
- Certaines applications (telles que Microsoft Project et Microsoft Visio) nécessitent le déploiement du Portail d’entreprise avec Bureau géré Microsoft.
- Les administrateurs informatiques peuvent personnaliser le portail d’entreprise pour leur organisation. Cela inclut la création d’images de marque, l’ajout de contacts de support local, etc. Pour plus d’informations, [voir Comment configurer l’application Portail d’entreprise Microsoft Intune.](https://docs.microsoft.com/intune/company-portal-app)   

Cette rubrique documente le processus de déploiement du portail d’entreprise Intune sur vos utilisateurs de bureau géré Microsoft. Le processus global ressemble à ceci :
1. Acheter le portail d’entreprise à partir du Microsoft Store pour Entreprises et synchroniser avec Intune
2. Affecter le portail d’entreprise à vos utilisateurs
3. Communiquer les changements à vos utilisateurs

## <a name="step-1---purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>Étape 1 : acheter le portail d’entreprise à partir du Microsoft Store pour Entreprises et synchroniser avec Intune
Pour plus d’informations sur l’achat des applications et la synchronisation avec Intune, voir [applications du Microsoft Store](deploy-apps.md#msfb-apps) pour Entreprises dans Déployer des applications sur des appareils de bureau géré *Microsoft.*

Cette rubrique fournit des informations sur la façon de : 
- Acheter le portail d’entreprise à partir du Microsoft Store pour Entreprises 
- Forcer la synchronisation entre Intune et Microsoft Store pour Entreprises
- Vérifier la synchronisation active entre Intune et Microsoft Store pour Entreprises 

## <a name="step-2---assign-company-portal-to-your-users"></a>Étape 2 : affecter le portail d’entreprise à vos utilisateurs
Après votre inscription au Bureau géré Microsoft, les opérations bureau géré Microsoft déploient automatiquement le portail d’entreprise sur votre client et installent l’application sur les appareils bureau géré Microsoft de votre organisation.

## <a name="step-3---communicate-change-to-your-users"></a>Étape 3 : communiquer les changements à vos utilisateurs
En tant qu’administrateur informatique de votre organisation, il est important de faire savoir à vos utilisateurs comment utiliser le portail d’entreprise dans votre organisation. Bureau géré Microsoft recommande :
- Étapes d’installation des applications à partir du portail d’entreprise. Pour plus d’informations, voir [Installer et partager des applications sur votre appareil.](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows)
- Comment envoyer des demandes aux administrateurs informatiques pour les applications qui ne sont pas actuellement disponibles. Pour plus d’informations, voir [Demander une application pour le travail ou l’école.](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school)  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en place du Bureau géré Microsoft

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. Déployer le portail d’entreprise Intune (cette rubrique)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)
