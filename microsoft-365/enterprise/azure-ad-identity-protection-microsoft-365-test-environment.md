---
title: Azure AD Identity Protection pour votre environnement de test Microsoft 365 pour entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez Azure AD Identity Protection et analysez les comptes actuels dans votre environnement de test Microsoft 365 pour entreprise.
ms.openlocfilehash: e60115623f63417175594e76f58fde616d2698b7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185664"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Azure AD Identity Protection pour votre environnement de test Microsoft 365 pour entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Vous pouvez utiliser Azure Active Directory (Azure AD) Identity Protection pour détecter les vulnérabilités potentielles qui affectent les identités de votre organisation, configurer des réponses automatisées et examiner les incidents. Cet article explique comment utiliser Azure AD Identity Protection pour afficher l’analyse de vos comptes d’environnement de test.

La configuration d’Azure AD Identity Protection dans votre environnement de test Microsoft 365 pour entreprise implique deux phases :

- [Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Utiliser Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise

Si vous souhaitez tester Azure AD Identity Protection de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester Azure AD Identity Protection dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test d’Azure AD Identity Protection ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous puissiez tester Azure AD Identity Protection et l’expérimenter dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Phase 2 : Utiliser Azure AD Identity Protection

1. Ouvrez une instance privée de votre navigateur et connectez-vous au Portail Azure à [https://portal.azure.com](https://portal.azure.com) l’aide du compte d’administrateur général de votre environnement de test Microsoft 365 pour entreprise.
2. Dans le Portail Azure, tapez **la protection d’identité** dans la zone de recherche, puis sélectionnez **Azure AD Identity Protection**.
3. Dans le panneau **Protection des identités - Vue d’ensemble** , sélectionnez chaque rapport pour voir ce qu’il signale.
4. Sous **Notifier**, sélectionnez **Les utilisateurs à risque détectés**.
5. Dans le volet **Utilisateurs à risque détectés** , sélectionnez **Moyenne**.
6. Pour **les e-mails sont envoyés aux utilisateurs suivants**, **sélectionnez Inclus** et vérifiez que votre compte d’administrateur général figure dans la liste des membres sélectionnés.
7. Sélectionnez **Enregistrer**.

Sous **Protéger**, sélectionnez différentes stratégies pour voir comment les configurer. Si vous créez et activez une stratégie, assurez-vous qu’elle ne bloque pas l’accès pour tous les utilisateurs, ou que vous ne pourrez peut-être pas vous connecter. Pour éviter cela, excluez des comptes d’utilisateur spécifiques, tels que des administrateurs généraux.

Pour d’autres tests et expérimentations, consultez [Simulation d’événements à risque](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Déployer une identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)