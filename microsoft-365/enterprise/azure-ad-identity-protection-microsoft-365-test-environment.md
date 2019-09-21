---
title: Protection des identités Azure AD pour votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/21/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez Azure AD identity protection et analysez les comptes actuels dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 97530dcec9c32882bbe3b66eb53eaa6d4668a838
ms.sourcegitcommit: 1162d676b036449ea4220de8a6642165190e3398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37071713"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-enterprise-test-environment"></a>Protection des identités Azure AD pour votre environnement de test Microsoft 365 Enterprise

Azure AD Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation, de configurer des réponses automatiques et de rechercher des incidents. Cet article explique comment activer la protection des identités Azure AD et afficher l’analyse de vos comptes d’environnement de test.

Il existe deux phases de configuration de la protection des identités Azure AD dans votre environnement de test Microsoft 365 Enterprise :

1. Créer l’environnement de test Microsoft 365 Entreprise.
2. Activer et utiliser Azure AD identity protection.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 Enterprise

Si vous souhaitez simplement tester la protection des identités Azure AD avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des identités Azure AD dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de la protection des identités Azure AD n’exige pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des identités Azure AD et de l’expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-enable-and-use-azure-ad-identity-protection"></a>Phase 2 : activer et utiliser Azure AD Identity Protection

1. Ouvrez une instance privée de votre navigateur et connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide du compte d’administrateur général de votre environnement de test Microsoft 365 Enterprise.
2. Dans le portail Azure, cliquez sur **tous les services > Marketplace**.
3. Tapez **Azure ad Identity Protection** , puis cliquez sur celui-ci.
4. Dans le **volet mise** en route, cliquez sur **intégré** sous **paramètres**, cliquez sur **Épingler au tableau de bord**, puis cliquez sur **créer**.
5. Dans le portail Azure, cliquez sur **protection des identités Azure ad** dans le tableau de bord. 

   Vous devriez voir une lame **Azure ad Identity Protection-Overview** avec un tableau de bord. Sous **vulnérabilités**, Notez que le nombre de comptes d’utilisateurs est déterminé sans l’enregistrement d’authentification multifacteur. Ce nombre varie en fonction des guides de laboratoire de test Microsoft 365 Enterprise que vous avez effectués.

6. Cliquez sur les catégories pour vérifier si des utilisateurs **ou des événements** ont été détectés.

Pour des tests et des expériences supplémentaires, consultez la rubrique [simulationing Risk Events](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-playbook).

Consultez l’étape [protéger contre la compromission des informations d’identification](identity-secure-user-sign-ins.md#identity-ident-prot) dans la phase d’identité pour obtenir des informations et des liens permettant de déployer la protection des identités Azure AD en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
