---
title: Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/16/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Suivez ces étapes pour protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 89985f99f5471aab87189e78035062add2c6bad9
ms.sourcegitcommit: 9ee873c6a2f738a0c99921e036894b646742e706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38673330"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-enterprise-test-environment"></a>Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise

*Ce guide de laboratoire de test ne peut être utilisé que pour les environnements de test Microsoft 365 entreprise.*

Vous pouvez empêcher les attaques numériques sur votre organisation en vous assurant que les comptes administrateurs sont aussi sécurisés que possible. Cet article explique comment utiliser les stratégies d’accès conditionnel Azure Active Directory (Azure AD) pour protéger les comptes d’administrateur général.

Il existe deux phases pour la protection des comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise :

1.  Créer l’environnement de test Microsoft 365 Entreprise.
2.  Protégez votre compte d’administrateur général dédié.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester la protection de compte d’administrateur général de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d’administrateur général dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).

  
> [!NOTE]
> Le test de la protection de compte d’administrateur général ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour les services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des comptes d’administrateur général et de l’expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Phase 2 : configurer les stratégies d’accès conditionnel

Tout d’abord, créez un compte d’utilisateur en tant qu’administrateur global dédié.

1. Sous un onglet séparé, ouvrez le [Centre d’administration Microsoft 365](https://admin.microsoft.com/).
2. Sous **utilisateurs actifs**, cliquez sur **Ajouter un utilisateur**.
3. Sur la page **nouvel utilisateur** , tapez **DedicatedAdmin** dans **prénom**, **nom d’affichage**et nom **d’utilisateur**.
4. Cliquez sur **mot de passe**, sur **me laisser créer le mot de**passe, puis tapez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. Décochez **faire en sorte que cet utilisateur modifie son mot de passe lors de sa première connexion**.
6. Cliquez sur **rôles**, puis sur **administrateur général**.
7. Cliquez sur **licences de produit**, puis activez les licences **Enterprise Mobility + Security e5** et **Office 365 entreprise E5** sur.
8. Cliquez sur **Ajouter**.
9. Dans la **page l’utilisateur a été ajouté**, effacez le **mot de passe Envoyer un message électronique**, puis cliquez sur **Fermer**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Dans l’onglet **Centre d’administration Microsoft 365** , cliquez sur l’icône groupes dans le volet de navigation de gauche, puis cliquez sur **groupes**.
2. Cliquez sur **Ajouter un groupe**.
3. Sur la page **nouveau groupe** , tapez **GlobalAdmins**.
4. Cliquez sur **Sélectionner le propriétaire** , cliquez sur votre compte d’administrateur général, puis cliquez sur **Ajouter > fermer**.
5. Dans la liste des groupes, cliquez sur le groupe **GlobalAdmins** .
6. Sur la page **GlobalAdmins** , cliquez sur modifier le membre, puis sur **Ajouter** **des**membres.
7. Dans la liste, cliquez sur le compte **DedicatedAdmin** , puis cliquez sur **enregistrer > fermer > fermer le centre d’administration >**.

Ensuite, créez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général et pour refuser l’authentification si le risque de connexion est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d’administrateur général utilisent l’authentification multifacteur.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Azure Active Directory > accès conditionnel**.
3. Dans le panneau **accès conditionnel – stratégies** , cliquez sur **stratégie de base : exiger MFA pour les administrateurs (aperçu)**.
4. Sur les **stratégies de base...** , cliquez sur **utiliser la stratégie immédiatement > enregistrer**.

Cette deuxième stratégie bloque l’accès à l’authentification de compte d’administrateur général lorsque le risque de connexion est moyen ou élevé.

1. Dans le panneau **accès conditionnel – stratégies** , cliquez sur **nouvelle stratégie**.
2. Sur la **nouvelle** Blade, tapez **administrateurs globaux** dans **nom**.
3. Dans la section **affectations** , cliquez sur **utilisateurs et groupes**.
4. Sous l’onglet **inclure** du panneau **utilisateurs et groupes** , cliquez sur **Sélectionner les utilisateurs et les groupes > utilisateurs et groupes > sélectionner**.
5. Dans la Blade de **sélection** , cliquez sur l' **GlobalAdmins > sélectionnez > terminée**.
6. Dans la section **affectations** , cliquez sur **conditions**.
7. Dans le volet **conditions** , cliquez sur **risque de connexion**, cliquez sur **Oui** pour **configurer**, **sur haute** et **moyenne**, puis sur **sélection** et **fin**.
8. Dans la section **contrôles d’accès** de la **nouvelle** Blade, cliquez sur **accorder**.
9. Dans le panneau **accorder** , cliquez sur **bloquer l’accès**, puis sur **Sélectionner**.
10. Sur la **nouvelle** Blade, cliquez **sur** activer pour **activer la stratégie**, puis cliquez sur **créer**.
11. Fermez les onglets **portail Azure** et **Centre d’administration Microsoft 365** .

Pour tester la première stratégie, déconnectez-vous, puis connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l’authentification multifacteur sur le compte d’utilisateur. Cela démontre que la première stratégie est appliquée.

Consultez l’étape [protéger les comptes administrateur général](identity-create-protect-global-admins.md#identity-global-admin) dans la phase d’identité pour obtenir des informations et des liens afin de protéger vos comptes d’administrateur général en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
