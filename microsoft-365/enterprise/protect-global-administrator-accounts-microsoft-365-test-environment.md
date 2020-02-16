---
title: Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Suivez ces étapes pour protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 9452ac7bafec416833ece9cbcb645bd7eeee21cc
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42084323"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-enterprise-test-environment"></a>Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

Vous pouvez empêcher les attaques numériques sur votre organisation en vous assurant que les comptes administrateurs sont aussi sécurisés que possible. Cet article explique comment utiliser les stratégies d’accès conditionnel Azure Active Directory (Azure AD) pour protéger les comptes d’administrateur général.

Il existe deux phases pour la protection des comptes d’administrateur général dans votre environnement de test Microsoft 365 Enterprise :

1.  Créer l’environnement de test Microsoft 365 Entreprise.
2.  Protégez votre compte d’administrateur général dédié.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester la protection de compte d’administrateur général de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d’administrateur général dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de la protection de compte d’administrateur général ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour les services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des comptes d’administrateur général et de l’expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Phase 2 : configurer les stratégies d’accès conditionnel

Tout d’abord, créez un compte d’utilisateur en tant qu’administrateur global dédié.

1. Sous un onglet séparé, ouvrez le [Centre d’administration Microsoft 365](https://admin.microsoft.com/).
2. Cliquez sur **utilisateurs > utilisateurs actifs**, puis cliquez sur **Ajouter un utilisateur**.
3. Dans le **volet ajouter un utilisateur** , tapez **DedicatedAdmin** dans **prénom**, **nom d’affichage**et nom **d’utilisateur**.
4. Cliquez sur **mot de passe**, sur **me laisser créer le mot de**passe, puis tapez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. Cliquez sur **Suivant**.
6. Dans le **volet attribuer des licences de produits** , sélectionnez **Microsoft 365 e5** ou **Office 365 E5**, puis cliquez sur **suivant**.
7. Dans le volet **paramètres facultatifs** , cliquez sur **rôles**, puis sélectionnez **accès au centre d’administration** et **administrateur global**. Cliquez sur **suivant**.
8. Dans le volet **vous êtes presque terminé** , cliquez sur **terminer l’ajout**, puis cliquez sur **Fermer**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Dans l’onglet **Centre d’administration Microsoft 365** , cliquez sur **groupes** dans le volet de navigation de gauche, puis cliquez sur **groupes**.
2. Cliquez sur **Ajouter un groupe**.
3. Dans le volet **choisir un type de groupe** , sélectionnez **sécurité**, puis cliquez sur **suivant**.
4. Dans le volet **configurer les concepts de base** , cliquez sur **créer un groupe**, puis cliquez sur **Fermer**.
5. Dans le volet **vérifier et terminer l’ajout** d’un groupe, tapez **GlobalAdmins**, puis cliquez sur **suivant**.
7. Dans la liste des groupes, cliquez sur le groupe **GlobalAdmins** .
8. Dans le volet **GlobalAdmins** , cliquez sur **membres**, puis sur **Afficher tout et gérer les membres**.
9. Dans le volet **GlobalAdmins** , cliquez sur **Ajouter des membres**, sélectionnez le compte **DedicatedAdmin** et votre compte d’administrateur général, puis cliquez sur **Enregistrer > fermer > fermer**.

Ensuite, créez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général et pour refuser l’authentification si le risque de connexion est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d’administrateur général utilisent l’authentification multifacteur.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Azure Active Directory > sécurité > accès conditionnel**.
3. Dans le volet **accès conditionnel – stratégies** , cliquez sur **stratégie de base : exiger l’authentification multifacteur pour les administrateurs (aperçu)**.
4. Dans le volet **stratégie de base** , cliquez sur utiliser la **stratégie immédiatement > enregistrer**.

Cette deuxième stratégie bloque l’accès à l’authentification de compte d’administrateur général lorsque le risque de connexion est moyen ou élevé.

1. Dans le volet **accès conditionnel – stratégies** , cliquez sur **nouvelle stratégie**.
2. Dans le volet **nouveau** , tapez **administrateurs globaux** dans **nom**.
3. Dans la section **affectations** , cliquez sur **utilisateurs et groupes**.
4. Sous l’onglet **inclure** du volet **utilisateurs et groupes** , cliquez sur Sélectionner des utilisateurs et des groupes **> utilisateurs et des groupes > sélectionner**.
5. Dans le volet **Sélectionner** , cliquez sur le groupe **GlobalAdmins** , puis cliquez sur **Sélectionner > terminée**.
6. Dans la section **affectations** , cliquez sur **conditions**.
7. Dans le volet **conditions** , cliquez sur **risque de connexion**, cliquez sur **Oui** pour **configurer**, **sur haute** et **moyenne**, puis sur **sélection** et **fin**.
8. Dans la section **contrôles d’accès** du **nouveau** volet, cliquez sur **accorder**.
9. Dans le volet **accorder** , cliquez sur **bloquer l’accès**, puis sur **Sélectionner**.
10. Dans le volet **nouveau** , cliquez sur **activé** pour **activer la stratégie**, puis cliquez sur **créer**.
11. Fermez les onglets **portail Azure** et **Centre d’administration Microsoft 365** .

Pour tester la première stratégie, déconnectez-vous, puis connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l’authentification multifacteur. Cela démontre que la première stratégie est appliquée.

Consultez l’étape [protéger les comptes administrateur général](identity-create-protect-global-admins.md#identity-global-admin) dans la phase d’identité pour obtenir des informations et des liens afin de protéger vos comptes d’administrateur général en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
