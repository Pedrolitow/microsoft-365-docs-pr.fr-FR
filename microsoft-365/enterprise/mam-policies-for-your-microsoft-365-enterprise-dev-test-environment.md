---
title: Stratégies GAM pour votre environnement de test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce Guide de laboratoire de Test pour ajouter l’environnement de test des stratégies de gestion (MAM) Intune application mobile à votre entreprise de 365 Microsoft.
ms.openlocfilehash: f00379a5e70dce5e07c031a7647b27041d3fa9d1
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867468"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-test-environment"></a>Stratégies GAM pour votre environnement de test Microsoft 365 Entreprise

Avec les instructions de cet article, vous ajoutez d’environnement de test des stratégies de gestion (MAM) Intune application mobile à votre entreprise de 365 Microsoft.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement configurer des stratégies MAM de manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test automatisé de gestion des licences et l’appartenance au groupe ne nécessite pas de l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 
>  

## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a>Phase 2 : Créer et déployer des stratégies de gestion des applications mobiles pour les appareils iOS et Android

Dans cette phase, vous créez et déployez deux stratégies de gestion des applications mobiles différentes : une pour les appareils iOS et une pour les appareils Android.
  
1. Accédez au portail Office 365 à ([https://portal.office.com](https://portal.office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. Sur un nouvel onglet de votre navigateur, ouvrez le portail Azure à [https://portal.azure.com](https://portal.azure.com).

3. Sous l’onglet portail Azure dans Internet Explorer, dans le volet de navigation, cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
    
4. Si vous voyez un message **vous n’avez pas activé la gestion de périphérique encore** sur le serveur lame **Intune Microsoft** , cliquez dessus. Sur la **Gestion des périphériques mobiles autorité** blade, cliquez sur **L’autorité Intune Mobile Device Manager**, puis cliquez sur **Choisir**. Actualisez votre onglet du navigateur.
    
5. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
6. Sur le serveur lame **groupes de groupes** , cliquez sur **+ Nouveau groupe**.
    
7. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **gérées les utilisateurs d’appareils iOS** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**et puis cliquez sur **créer**. 
    
8. Fermez le volet **Groupe**.
    
9. Sur le serveur lame **groupes de groupes** , cliquez sur **Ajouter**.
    
10. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **utilisateur d’un appareil Android gérés** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**, puis cliquez sur **créer**.
    
11. Fermez la lame de **groupes de groupes** .
    
12. Dans le volet **Intune**, dans la liste **Tâches rapides**, cliquez sur **Créer une stratégie de conformité**.
    
13. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
14. Dans le volet **Créer une stratégie**, dans **Nom**, tapez **iOS**. Dans **Plateforme**, sélectionnez **iOS**, cliquez sur **OK** dans le volet **Stratégie de conformité iOS**, puis cliquez sur **Créer**.
    
15. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
16. Dans le volet **Créer une stratégie**, dans **Nom**, tapez **Android**. Dans **Plateforme**, sélectionnez **Android**, cliquez sur **OK** dans le volet **Stratégie de conformité Android**, puis cliquez sur **Créer**.
    
17. Dans le volet **Profils de stratégie de conformité**, cliquez sur le nom de la stratégie **Android**.
    
18. Dans la barre de navigation de gauche du volet **Android - Propriétés**, cliquez sur **Affectations**, puis cliquez sur **Sélectionner des groupes**.
    
19. Dans le volet **Sélectionner des groupes**, sélectionnez le groupe **Utilisateurs d’appareils Android partagés**, puis cliquez sur **Sélectionner**.
    
20. Cliquez sur **Enregistrer**, puis fermez la lame **Android - affectations** .
    
21. Dans le volet **Profils de stratégie de conformité**, cliquez sur le nom de la stratégie **iOS**.
    
22. Dans la barre de navigation de gauche du volet **iOS - Propriétés**, cliquez sur **Affectations**, puis cliquez sur **Sélectionner des groupes**.
    
23. Dans le volet **Sélectionner des groupes**, sélectionnez le groupe **Utilisateurs d’appareils iOS gérés**, puis cliquez sur **Sélectionner**.
    
24. Cliquez sur **Enregistrer**, puis fermez la lame **iOS - affectations** .
    
25. Fermez le volet **Profils de stratégie de conformité**.
    
26. Dans le volet **Intune**, cliquez sur **Gérer les applications** dans le volet de navigation de gauche.
    
27. Dans le volet **Applications mobiles**, cliquez sur **Applications**.
    
28. Dans la liste des applications, cliquez sur **PowerPoint**.  
    
29. Dans le volet **Présentation PowerPoint**, cliquez sur **Affectations > Sélectionner des groupes > Appareils iOS gérés > Sélectionner**. Dans **Type**, sélectionnez **Disponible**, puis cliquez sur **Enregistrer**.
    
30. Répétez l’étape 29 pour les applications suivantes :
    
    - Outlook pour Android
    
    - Word pour iOS
    
    - Excel pour iOS
    
    - Outlook pour iOS
    
    - Microsoft Dynamics CRM sur iPad pour iOS
    
    - Microsoft Dynamics CRM sur iPhone pour iOS
    
    - Dynamics CRM pour les téléphones Android
    
    - Dynamics CRM pour les tablettes Android
    
    - Excel pour Android
    
    - Word pour Android
    
    - OneNote pour iOS
    
31. Fermez le volet **Applications mobiles - Applications**.
    
32. Dans le volet **Applications mobiles**, cliquez sur **Stratégies de protection de l’application**.
    
33. Dans le volet **Stratégies de protection de l’application**, cliquez sur **Ajouter une stratégie**.
    
34. Dans le volet **Ajouter une stratégie**, tapez **iOS**, puis cliquez sur **Sélectionner les applications requises**.
    
35. Dans le volet **Applications**, cliquez sur **PowerPoint**, **Microsoft Dynamics CRM sur iPhone**, **Excel**, **Microsoft Dynamics CRM sur iPhone**, **Word**, **OneNote** et **Outlook**, puis cliquez sur **Sélectionner**.
    
36. Dans le volet **Ajouter une stratégie**, cliquez sur **Créer**.
    
37. Dans le volet **Stratégies de protection de l’application**, cliquez sur **Ajouter une stratégie**.
    
38. Dans le volet **Ajouter une stratégie**, tapez **Android**, sélectionnez **Android** dans **Plateforme**, puis cliquez sur **Sélectionner les applications requises**.
    
39. Dans le volet **Applications**, cliquez sur **PowerPoint**, **Dynamics CRM pour tablettes**, **Excel**, **Word**, **Outlook**, et **Dynamics CRM pour téléphones**, puis cliquez sur **Sélectionner**.
    
40. Dans le volet **Ajouter une stratégie**, cliquez sur **Créer**.
    
Vous avez deux stratégies de gestion des applications mobiles : une pour les appareils iOS et l’autre pour les appareils Android. Vous souhaitez tester les paramètres pour les applications sélectionnées. 
  
## <a name="next-step"></a>Étape suivante

Explorez des fonctionnalités de [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Microsoft Enterprise 365](m365-enterprise-test-lab-guides.md).
  
[Inscription d’appareils iOS et Android dans votre environnement de test Microsoft 365 Entreprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
