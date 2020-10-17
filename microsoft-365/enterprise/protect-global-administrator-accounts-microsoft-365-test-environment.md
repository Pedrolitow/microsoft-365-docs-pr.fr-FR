---
title: Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour les entreprises
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
description: Suivez ces étapes pour protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour les entreprises.
ms.openlocfilehash: 1ae04e4761ed86e087e647464ad522466ed6abef
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487635"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Vous pouvez empêcher les attaques numériques sur votre organisation en vous assurant que les comptes administrateurs sont aussi sécurisés que possible. 

Cet article explique comment utiliser les stratégies d’accès conditionnel Azure Active Directory (Azure AD) pour protéger les comptes d’administrateur général.

La protection des comptes administrateur général dans votre environnement de test Microsoft 365 pour entreprise implique deux phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : configurer les stratégies d’accès conditionnel](#phase-2-configure-conditional-access-policies)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez tester la protection des comptes administrateur générale avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d’administrateur général dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de la protection de compte d’administrateur général ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour les services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester la protection des comptes d’administrateur général et de l’expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Phase 2 : configurer les stratégies d’accès conditionnel

Tout d’abord, créez un compte d’utilisateur en tant qu’administrateur global dédié.

1. Sous un onglet séparé, ouvrez le [Centre d’administration Microsoft 365](https://admin.microsoft.com/).
2. Sélectionnez **utilisateurs**  >  **actifs**, puis **Ajouter un utilisateur**.
3. Dans le volet **Ajouter un utilisateur** , entrez **DedicatedAdmin** dans **les zones Prénom,** **nom d’affichage**et nom **d’utilisateur** .
4. Sélectionnez **mot de passe**, sélectionnez **me laisser créer le mot de**passe, puis entrez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. Sélectionnez **Suivant**.
6. Dans le volet **attribuer des licences de produits** , sélectionnez **Microsoft 365 E5**, puis cliquez sur **suivant**.
7. Dans le volet **paramètres facultatifs** , sélectionnez le centre d’administration **rôles**  >  **Access**  >  **Global admin**  >  **Next**.
8. Dans le volet **vous êtes presque terminé** , sélectionnez **terminer l’ajout**, puis cliquez sur **Fermer**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Sous l’onglet **Centre d’administration 365 de Microsoft** , sélectionnez **groupes** dans le volet de navigation de gauche, puis sélectionnez **groupes**.
2. Sélectionnez **Ajouter un groupe**.
3. Dans le volet **choisir un type de groupe** , sélectionnez **sécurité**, puis **suivant**.
4. Dans le volet **configure the Basics** , sélectionnez **Create Group**, puis **Close**.
5. Dans le volet **vérifier et terminer l’ajout** d’un groupe, entrez **GlobalAdmins**, puis cliquez sur **suivant**.
7. Dans la liste des groupes, sélectionnez le groupe **GlobalAdmins** .
8. Dans le volet **GlobalAdmins** , sélectionnez **membres**, puis **Afficher tous et gérer les membres**.
9. Dans le volet **GlobalAdmins** , sélectionnez **Ajouter des membres**, sélectionnez le compte **DedicatedAdmin** et votre compte d’administrateur général, puis sélectionnez **Enregistrer**  >  **Fermer**  >  **Close**.

Ensuite, créez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général et pour refuser l’authentification si le risque de connexion est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d’administrateur général utilisent l’authentification multifacteur.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com) .
2. Cliquez sur accès conditionnel **Azure Active Directory**  >  **Security**  >  **Conditional Access**.
3. Dans le volet **accès conditionnel – stratégies** , sélectionnez **stratégie de base : exiger l’authentification multifacteur pour les administrateurs (aperçu)**.
4. Dans le volet **stratégie de base** , sélectionnez utiliser la **stratégie immédiatement > enregistrer**.

Cette deuxième stratégie bloque l’accès à l’authentification de compte d’administrateur général lorsque le risque de connexion est moyen ou élevé.

1. Dans le volet **accès conditionnel – stratégies** , sélectionnez **nouvelle stratégie**.
2. Dans le volet **nouveau** , entrez **administrateurs généraux** dans **nom**.
3. Dans la section **affectations** , sélectionnez **utilisateurs et groupes**.
4. Sous l’onglet **inclure** du volet **utilisateurs et groupes** , sélectionnez **Sélectionner des**utilisateurs et des groupes d'  >  **utilisateurs et**  >  **de groupes**.
5. Dans le volet **Sélectionner** , sélectionnez le groupe **GlobalAdmins** , **puis sélectionnez**  >  **Terminer**.
6. Dans la section **affectations** , sélectionnez **conditions**.
7. Dans le volet **conditions** , sélectionnez **risque de connexion**, cliquez sur **Oui** pour **configurer**, sélectionnez **haute** et **moyenne**, puis sélectionnez **Sélectionner** et **Terminer**.
8. Dans la section **contrôles d’accès** du **nouveau** volet, sélectionnez **accorder**.
9. Dans le volet **accorder** , sélectionnez **bloquer l’accès**, puis sélectionnez **Sélectionner**.
10. Dans le volet **nouveau** , sélectionnez **activé** pour **activer la stratégie**, puis **créer**.
11. Fermez les onglets **portail Azure** et **Centre d’administration Microsoft 365** .

Pour tester la première stratégie, déconnectez-vous, puis connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l’authentification multifacteur. Cela démontre que la première stratégie est appliquée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Feuille de route d’identité](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
