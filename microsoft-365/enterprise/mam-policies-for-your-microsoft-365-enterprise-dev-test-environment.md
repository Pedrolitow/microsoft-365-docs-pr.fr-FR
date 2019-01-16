---
title: Environnement de test des stratégies de conformité de périphérique pour votre entreprise 365 de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Utilisez ce Guide de laboratoire de Test pour ajouter l’environnement de test des stratégies de conformité d’appareil Intune à votre entreprise de 365 Microsoft.
ms.openlocfilehash: 1d957c5cdc888251224bbca43fe82ab0a15e7a93
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867468"
---
# <a name="device-compliance-policies-for-your-microsoft-365-enterprise-test-environment"></a>Environnement de test des stratégies de conformité de périphérique pour votre entreprise 365 de Microsoft

Avec les instructions de cet article, vous ajoutez une stratégie de conformité de périphérique Intune dans votre environnement de test Microsoft 365 pour entreprises.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement configurer des stratégies MAM de manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer des stratégies MAM dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test automatisé de gestion des licences et l’appartenance au groupe ne nécessite pas de l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Phase 2 : Créer une stratégie de conformité de périphérique pour les périphériques Windows 10

Dans cette phase, vous créez une stratégie de conformité de périphérique pour les périphériques Windows 10.
  
1. Accédez au portail Office au ([https://office.com](https://office.com)) et se connecter à votre abonnement d’évaluation d’Office 365 avec votre compte d’administrateur global.
    
2. Sur un nouvel onglet de votre navigateur, ouvrez le portail Azure à [https://portal.azure.com](https://portal.azure.com).

3. Sous l’onglet portail Azure dans votre navigateur, dans le volet de navigation, cliquez sur **tous les services**, tapez **Intune**, puis cliquez sur **Intune**.
    
4. Si vous voyez un message **vous n’avez pas activé la gestion de périphérique encore** sur le serveur lame **Intune Microsoft** , cliquez dessus. Sur la **Gestion des périphériques mobiles autorité** blade, cliquez sur **L’autorité Intune Mobile Device Manager**, puis cliquez sur **Choisir**. Actualisez votre onglet du navigateur.
    
5. Dans le volet de navigation gauche, cliquez sur **Groupes**.
    
6. Sur le serveur lame **groupes de groupes** , cliquez sur **+ Nouveau groupe**.
    
7. Dans la **groupe** lame, sélectionnez **Office 365** pour **type de groupe ?**, tapez **les utilisateurs d’appareils gérées Windows 10** dans **nom**, sélectionnez **assigné** dans le **type d’appartenance**et puis cliquez sur **créer**. 
    
8. Fermez le volet **Groupe**.
    
11. Fermez la lame de **groupes de groupes** .
    
12. Sur la blade **Intune Microsoft** , dans la liste de **tâches rapides** , cliquez sur **créer une stratégie de conformité**.
    
13. Dans le volet **Profils de stratégie de conformité**, cliquez sur **Créer une stratégie**.
    
14. Sur le serveur lame **Créer une stratégie** , dans **nom**, tapez **Windows 10**. Dans la **plateforme**, sélectionnez **Windows 10 et les versions ultérieures**, cliquez sur **OK** dans la **stratégie de conformité Windows 10** lame, puis cliquez sur **créer**. Fermez la lame **Windows 10** .
    
15. Sur le serveur lame **Profils de stratégie de conformité** , cliquez sur le nom de la stratégie **Windows 10** .
    
16. Sur le serveur lame **10 Windows** , cliquez sur **les affectations**, puis cliquez sur **Sélectionner les groupes à inclure**.
    
17. Sur le serveur lame **Sélectionnez groupes à inclure** , cliquez sur le groupe **d’utilisateurs d’appareils gérées Windows 10** , puis cliquez sur **Sélectionner**.
    
18. Cliquez sur **Enregistrer**, puis fermez la lame **Windows 10 - affectations** .
    
19. Fermez le volet **Profils de stratégie de conformité**.
    
20. Sur le serveur lame **Intune Microsoft** , cliquez sur **applications clientes** dans le volet de navigation gauche.
    
21. Sur le serveur lame **Applications clientes** , cliquez sur **applications**, puis cliquez sur **Ajouter**. 

22. Dans **l’application Add** lame, sélectionnez **type d’application**, puis sélectionnez **Windows 10** sous **Office 365 Suite**.

23. Cliquez sur **Configurer la Suite application**, puis cliquez sur **OK**.

24. Cliquez sur **Informations Suite d’application**, tapez des **applications Office pour Windows 10** dans **Nom de la Suite**, **les applications Office pour Windows 10** dans la **Description de la Suite**, puis cliquez sur **OK**.

25. Cliquez sur **Paramètres de Suite de l’application**, sélectionnez **annuel séparées** dans le **canal de mise à jour**, puis cliquez sur **OK**.

26. Dans **l’application Add** lame, cliquez sur **Ajouter**.

Vous disposez maintenant d’une stratégie de conformité de périphérique pour tester les applications sélectionnées dans la stratégie de conformité de périphérique **Windows 10** et pour les membres du groupe **utilisateurs d’appareils gérées Windows 10** . 
  
## <a name="next-step"></a>Étape suivante

Explorez des fonctionnalités de [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Microsoft Enterprise 365](m365-enterprise-test-lab-guides.md).
  
[Inscription d’appareils iOS et Android dans votre environnement de test Microsoft 365 Entreprise](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Mobilité d’entreprise + sécurité (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
