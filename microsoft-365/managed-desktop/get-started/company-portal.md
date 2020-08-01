---
title: Installer le portail d’entreprise Intune sur les appareils
description: Informations sur l’installation de l’application portail d’entreprise sur les appareils de bureau gérés Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, portail d’entreprise
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 371656168f32db86ff32f187736d59dbd5dbe749
ms.sourcegitcommit: 126d22d8abd190beb7101f14bd357005e4c729f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "46529694"
---
# <a name="install-intune-company-portal-on-on-devices"></a>Installer l’application Portail d’entreprise Intune sur les appareils

Microsoft Managed Desktop exige que les administrateurs informatiques installent le portail d’entreprise Intune pour leurs utilisateurs avec des appareils de bureau gérés Microsoft. Voici quelques avantages pour votre organisation :
- Les utilisateurs disposent d’un emplacement unique pour parcourir et installer les applications disponibles. 
- Les administrateurs informatiques peuvent organiser les applications par catégorie pour leurs utilisateurs.  
- Certaines applications (telles que Microsoft Project et Microsoft Visio) ont besoin d’un portail d’entreprise pour déployer avec Microsoft Managed Desktop.
- Les administrateurs informatiques peuvent personnaliser le portail d’entreprise pour leur organisation. Il s’agit notamment de la création d’images de marque, l’ajout de contacts de support local et bien plus encore. Pour plus d’informations, consultez [la rubrique How to configure the Microsoft Intune Company Portal App](https://docs.microsoft.com/intune/company-portal-app).   

Cette rubrique décrit le processus de déploiement du portail d’entreprise Intune sur les utilisateurs de bureau gérés Microsoft. Le processus global se présente comme suit :
1. Acheter un portail d’entreprise à partir de Microsoft Store pour les entreprises et synchroniser avec Intune
2. Affecter un portail d’entreprise à vos utilisateurs
3. Communiquer les modifications à vos utilisateurs

## <a name="step-1---purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>Étape 1 : acheter un portail d’entreprise à partir de Microsoft Store pour les entreprises et synchroniser avec Intune
Pour plus d’informations sur l’achat des applications et sur la synchronisation avec Intune, voir [Microsoft Store for Business Apps](deploy-apps.md#msfb-apps) dans *Deploy Apps to Microsoft Managed Desktop Devices*.

Cette rubrique fournit des informations sur les opérations suivantes : 
- Acheter un portail d’entreprise à partir de Microsoft Store pour les entreprises 
- Forcer la synchronisation entre Intune et Microsoft Store pour les entreprises
- Vérifier la synchronisation active entre Intune et Microsoft Store pour les entreprises 

## <a name="step-2---assign-company-portal-to-your-users"></a>Étape 2 : affecter un portail d’entreprise à vos utilisateurs
Soumettez une demande de support aux opérations de bureau géré Microsoft via le portail d’administration de bureau géré Microsoft. Dans la demande de support, demandez au portail de l’entreprise d’être affecté à vos utilisateurs. Le bureau géré Microsoft déploie le portail d’entreprise vers votre client et installe l’application sur des appareils de bureau gérés Microsoft dans votre organisation.

Pour plus d’informations sur l’envoi de demandes de prise en charge avec le bureau géré Microsoft, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).

## <a name="step-3---communicate-change-to-your-users"></a>Étape 3-communiquer les modifications à vos utilisateurs
En tant qu’administrateur informatique de votre organisation, il est important de permettre à vos utilisateurs de savoir comment utiliser le portail d’entreprise dans votre organisation. Microsoft Managed Desktop recommande :
- Étapes d’installation des applications à partir du portail de l’entreprise. Pour plus d’informations, consultez [la rubrique installer et partager des applications sur votre appareil](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows).
- Comment envoyer des demandes aux administrateurs informatiques pour les applications qui ne sont pas disponibles actuellement. Pour plus d’informations, reportez-vous à la rubrique [demander une application pour les professionnels ou l’école](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school).  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de prise en main de Microsoft Managed Desktop

1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. Déployer le portail d’entreprise Intune (cette rubrique)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer des applications](deploy-apps.md)
