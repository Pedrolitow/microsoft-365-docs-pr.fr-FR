---
title: Protection des identités Azure AD pour votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez Azure AD identity protection et analysez les comptes actuels dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: c0d364eaef9cfd37531d9f9e1803db66739a7984
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40802099"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-enterprise-test-environment"></a>Protection des identités Azure AD pour votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

Azure Active Directory (Azure AD) Identity Protection vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation, de configurer des réponses automatiques et d’examiner les incidents. Cet article explique comment utiliser Azure AD Identity Protection pour afficher l’analyse de vos comptes d’environnement de test.

Il existe deux phases de configuration de la protection des identités Azure AD dans votre environnement de test Microsoft 365 Enterprise :

1. Créer l’environnement de test Microsoft 365 Entreprise.
2. Utiliser Azure AD identity protection.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester la protection des identités Azure AD avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des identités Azure AD dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de la protection des identités Azure AD n’exige pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des identités Azure AD et de l’expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Phase 2 : utiliser Azure AD Identity Protection

1. Ouvrez une instance privée de votre navigateur et connectez-vous au portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide du compte d’administrateur général de votre environnement de test Microsoft 365 Enterprise.
2. Dans le portail Azure, tapez **protection des identités** dans la zone de recherche, puis cliquez sur **protection des identités Azure ad**.
3. Dans le panneau **identity protection-Overview** , cliquez sur chacun des rapports pour voir ce qu’ils signalent.
4. Sous **avertir**, cliquez sur **utilisateurs à risque-alertes détectées**.
5. Dans le volet des **alertes détection des utilisateurs à risque** , sélectionnez **moyen**.
6. Pour les **messages électroniques envoyés aux utilisateurs suivants**, cliquez sur **inclus** et vérifiez que votre compte d’administrateur global figure dans la liste des membres sélectionnés.
7. Cliquez sur **Enregistrer**.

Cliquez sur les différentes stratégies sous **protéger** pour voir comment les configurer. Si vous créez et activez une stratégie, assurez-vous qu’elle ne bloque pas l’accès pour une étendue de conditions trop large, ou que vous ne parvenez pas à vous connecter, même en tant qu’administrateur général.

Pour des tests et des expériences supplémentaires, consultez la rubrique [simulationing Risk Events](https://docs.microsoft.com/azure/active-directory/active-directory-identityprotection-playbook).

Consultez l’étape [protéger contre la compromission des informations d’identification](identity-secure-user-sign-ins.md#identity-ident-prot) dans la phase d’identité pour obtenir des informations et des liens permettant de déployer la protection des identités Azure AD en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
