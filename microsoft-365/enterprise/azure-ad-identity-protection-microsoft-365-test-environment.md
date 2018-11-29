---
title: Environnement de test Azure Protection d’identité AD pour votre entreprise 365 de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/21/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
description: Configurer la Protection d’identité Azure AD et analyser les comptes en cours dans votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 165667ad2122839336ef0790ab5661cff53ca32b
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866923"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-enterprise-test-environment"></a>Environnement de test Azure Protection d’identité AD pour votre entreprise 365 de Microsoft

Azure Protection d’identité AD vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation, configurer des réponses automatiques et examiner les incidents. Cet article décrit comment activer la Protection d’identité Azure AD et afficher l’analyse de vos comptes d’environnement de test.

Il existe deux phases de configuration de la Protection d’Azure AD identité dans votre environnement de test Microsoft 365 pour entreprises :

1. Créer l’environnement de test Microsoft 365 pour entreprises.
2. Activer et utiliser la Protection d’identité Azure AD.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez uniquement tester Protection Azure AD Identity dans une solution légère avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester Protection Azure AD Identity dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test de la Protection d’Azure AD identité ne nécessite pas l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option de sorte que vous pouvez tester la Protection d’identité Azure AD et tester dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-use-azure-ad-identity-protection"></a>Phase 2 : Activer et utiliser la Protection d’identité Azure AD

1. Ouvrez une instance privée de votre navigateur et connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) avec le compte d’administrateur global de votre environnement de test Microsoft 365 pour entreprises.
2. Dans le portail Azure, cliquez sur **tous les services > Marketplace**.
3. Tapez **Azure AD identité Protection** , puis cliquez dessus.
4. Sur le serveur lame **Mise en route** , cliquez sur **Onboard** sous **paramètres**, cliquez sur **Ajouter au tableau de bord**, puis cliquez sur **créer**.
5. Dans le portail Azure, cliquez sur **la Protection d’Azure AD identité** sur le tableau de bord. 

   Vous devez voir une lame **Azure AD identité Protection-vue d’ensemble** avec un tableau de bord. Sous **les failles**, notez qu’il déterminé le nombre de comptes d’utilisateurs sans l’inscription de l’authentification multifacteur. Ce nombre varie en fonction précédente Microsoft 365 entreprise Test Guides de laboratoire que vous avez effectuées.

6. Cliquez sur les catégories pour **examiner** voir s’il existe des utilisateurs ou des événements qui ont été détectés.

Pour davantage de test et l’expérimentation, voir [événements risque de simulation](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-playbook).

Voir l’étape de [protection contre les informations d’identification de compromettre](identity-azure-ad-identity-protection.md) lors de la phase d’identité pour des informations et des liens pour déployer la Protection d’Azure AD identité en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 pour entreprises](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
