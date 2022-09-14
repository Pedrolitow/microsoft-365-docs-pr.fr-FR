---
title: Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Utilisez ces étapes pour protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour entreprise.
ms.openlocfilehash: 2f4802529947d7f39545af7e8a54ba366a8cfcba
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67673104"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 pour entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Vous pouvez empêcher les attaques numériques sur votre organisation en veillant à ce que vos comptes d’administrateur soient aussi sécurisés que possible. 

Cet article explique comment utiliser des stratégies d’accès conditionnel Azure Active Directory (Azure AD) pour protéger les comptes d’administrateur général.

La protection des comptes d’administrateur général dans votre environnement de test Microsoft 365 pour entreprise implique deux phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configurer des stratégies d’accès conditionnel](#phase-2-configure-conditional-access-policies)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 pour entreprise

Si vous souhaitez tester la protection des comptes d’administrateur général de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d’administrateur général dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de la protection des comptes d’administrateur général ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour un services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option pour vous permettre de tester la protection des comptes d’administrateur général et de l’expérimenter dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Phase 2 : Configurer des stratégies d’accès conditionnel

Tout d’abord, créez un compte d’utilisateur en tant qu’administrateur général dédié.

1. Sous un onglet distinct, ouvrez le [Centre d'administration Microsoft 365](https://admin.microsoft.com/).
2. Sélectionnez **Utilisateurs** > **actifs**, puis **Ajouter un utilisateur**.
3. Dans le volet **Ajouter un utilisateur** , entrez **DedicatedAdmin** dans les zones **Prénom**, **Nom d’affichage** et **Nom d’utilisateur** .
4. Sélectionnez **Mot de passe**, **laissez-moi créer le mot de passe**, puis entrez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. Sélectionnez **Suivant**.
6. Dans le volet **Attribuer des licences de produit**, sélectionnez **Microsoft 365 E5**, puis **Suivant**.
7. Dans le volet **Paramètres facultatifs**, sélectionnez **Rôles** >  **Administration centrez l’accès** > **à l’administrateur** >  général **Suivant**.
8. Dans le volet **Vous avez presque terminé** , **sélectionnez Terminer l’ajout**, puis **Fermez**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Sous l’onglet **Centre d'administration Microsoft 365**, sélectionnez **Groupes** dans le volet de navigation gauche, puis **Groupes**.
2. Sélectionnez **Ajouter un groupe**.
3. Dans le volet **Choisir un type de groupe** , sélectionnez **Sécurité**, puis **Suivant**.
4. Dans le volet **Configurer les informations de base** , **sélectionnez Créer un groupe**, puis **Fermez**.
5. Dans le volet **Révision et fin de l’ajout de groupe** , entrez **GlobalAdmins**, puis sélectionnez **Suivant**.
7. Dans la liste des groupes, sélectionnez le groupe **GlobalAdmins** .
8. Dans le volet **GlobalAdmins** , sélectionnez **Membres**, puis sélectionnez **Afficher tout et gérer les membres**.
9. Dans le volet **GlobalAdmins**, sélectionnez **Ajouter des membres**, sélectionnez le compte **DedicatedAdmin** et votre compte d’administrateur général, puis **sélectionnez Enregistrer** > **fermer** > .

Ensuite, créez des stratégies d’accès conditionnel pour exiger une authentification multifacteur pour les comptes d’administrateur général et pour refuser l’authentification si le risque de connexion est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d’administrateur général utilisent l’authentification multifacteur.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Accès conditionnel** **de sécurité** >  **Azure Active Directory** > .
3. Dans le volet **Accès conditionnel – Stratégies**, sélectionnez **Stratégie de base : Exiger l’authentification multifacteur pour les administrateurs (préversion).**
4. Dans le volet **Stratégie de référence** , sélectionnez **Utiliser la stratégie immédiatement > Enregistrer**.

Cette deuxième stratégie bloque l’accès à l’authentification du compte administrateur général lorsque le risque de connexion est moyen ou élevé.

1. Dans le volet **Accès conditionnel – Stratégies** , sélectionnez **Nouvelle stratégie**.
2. Dans le volet **Nouveau** , entrez **Administrateurs généraux** dans **Nom**.
3. Dans la section **Affectations** , sélectionnez **Utilisateurs et groupes**.
4. Sous l’onglet **Inclure** du volet **Utilisateurs et groupes** , **sélectionnez Sélectionner les utilisateurs et les groupes** > **Utilisateurs et groupes** > **Sélectionner**.
5. Dans le volet **Sélectionner** , sélectionnez le groupe **GlobalAdmins** , puis **sélectionnez Sélectionner** > **terminé**.
6. Dans la section **Affectations** , sélectionnez **Conditions**.
7. Dans le volet **Conditions** , sélectionnez **Risque de** connexion, **Oui** pour **Configurer**, **Haut** et **Moyen**, puis **Sélectionnez Sélectionner** et **Terminé**.
8. Dans la section **Contrôles d’accès** du **volet Nouveau** , sélectionnez **Accorder**.
9. Dans le volet **Accorder** , sélectionnez **Bloquer l’accès**, puis **Sélectionnez Sélectionner**.
10. Dans le volet **Nouveau** , sélectionnez **Activé** pour **activer la stratégie**, puis **sélectionnez Créer**.
11. Fermez les onglets **Portail Azure** et **Centre d'administration Microsoft 365**.

Pour tester la première stratégie, déconnectez-vous et connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l’authentification multifacteur. Cela montre que la première stratégie est appliquée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Déployer une identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)