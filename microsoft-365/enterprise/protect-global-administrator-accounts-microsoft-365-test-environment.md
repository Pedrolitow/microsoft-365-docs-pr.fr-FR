---
title: Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 entreprise
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
description: Utilisez ces étapes pour protéger les comptes d’administrateur général dans votre Microsoft 365 environnement de test d’entreprise.
ms.openlocfilehash: 17aca0060501a4df3c694c4c7e4aa2aef98248d54b36d27ff3c99780648274b5
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53904730"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Protéger les comptes d’administrateur général dans votre environnement de test Microsoft 365 entreprise

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Vous pouvez empêcher les attaques numériques sur votre organisation en vous assurant que vos comptes d’administrateur sont aussi sécurisés que possible. 

Cet article explique comment utiliser des stratégies d Azure Active Directory d’accès conditionnel (Azure AD) pour protéger les comptes d’administrateur général.

La protection des comptes d’administrateur général dans votre Microsoft 365 environnement de test d’entreprise implique deux phases :
- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configuration des stratégies d’accès conditionnel](#phase-2-configure-conditional-access-policies)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez tester la protection des comptes d’administrateur général de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez tester la protection des comptes d’administrateur général dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test de la protection des comptes d’administrateur général ne nécessite pas l’environnement de test en entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour les services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous pouvez tester la protection des comptes d’administrateur général et l’expérimenter dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Phase 2 : Configuration des stratégies d’accès conditionnel

Tout d’abord, créez un compte d’utilisateur en tant qu’administrateur général dédié.

1. Sous un onglet distinct, ouvrez [le Centre d’administration Microsoft 365](https://admin.microsoft.com/).
2. Sélectionnez   >  **Utilisateurs actifs,** puis **ajoutez un utilisateur.**
3. Dans le **volet Ajouter un utilisateur,** entrez **DedicatedAdmin** dans les zones **Prénom,** Nom **d’affichage** et **Nom d’utilisateur.**
4. Sélectionnez **Mot** de passe, **Sélectionnez Me laisser créer le** mot de passe, puis entrez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. Sélectionnez **Suivant**.
6. Dans le **volet Attribuer des licences de** produits, **sélectionnez Microsoft 365 E5,** puis sélectionnez **Suivant.**
7. Dans le **volet Paramètres facultatifs,** sélectionnez **Rôles**  >  **Admin Center access** Global  >  **admin**  >  **Next**.
8. Dans le **volet Vous avez presque terminé,** sélectionnez Terminer **l’ajout,** puis **fermez**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Sous **l’onglet Centre d’administration Microsoft 365,** sélectionnez **Groupes** dans le navigation de gauche, puis sélectionnez **Groupes.**
2. Sélectionnez **Ajouter un groupe.**
3. Dans le **volet Choisir un type de groupe,** sélectionnez **Sécurité,** puis Sélectionnez **Suivant**.
4. Dans le **volet Configurer les informations** de base, sélectionnez Créer un groupe, puis **fermez.** 
5. Dans le **volet Révision et fin de l’ajout de** groupes, entrez **GlobalAdmins,** puis sélectionnez **Suivant.**
7. Dans la liste des groupes, sélectionnez le **groupe GlobalAdmins.**
8. Dans le **volet GlobalAdmins,** sélectionnez **Membres,** puis afficher **tout et gérer les membres.**
9. Dans le **volet GlobalAdmins,** sélectionnez Ajouter des **membres,** sélectionnez le compte **DedicatedAdmin** et votre compte d’administrateur global, puis **sélectionnez Enregistrer**  >  **fermer.**  >  

Ensuite, créez des stratégies d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général et refuser l’authentification si le risque de se connecte est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d’administrateur général utilisent l’mf.

1. Dans un nouvel onglet de votre navigateur, allez à [https://portal.azure.com](https://portal.azure.com) .
2. Cliquez **sur Azure Active Directory** accès  >  **conditionnel à** la  >  **sécurité.**
3. Dans le **volet Accès conditionnel – Stratégies,** sélectionnez Stratégie de référence : Exiger l’pertinence de l’élection de l’élection **(prévisualisation) pour les administrateurs.**
4. Dans le **volet Stratégie de** référence, **sélectionnez Utiliser la stratégie immédiatement > Enregistrer.**

Cette deuxième stratégie bloque l’accès à l’authentification de compte d’administrateur général lorsque le risque de se connecte est moyen ou élevé.

1. Dans le **volet Accès conditionnel – Stratégies,** sélectionnez **Nouvelle stratégie.**
2. Dans le **nouveau volet,** entrez **Administrateurs globaux** dans **Nom.**
3. Dans la section **Affectations,** sélectionnez **Utilisateurs et groupes.**
4. Dans **l’onglet**  Inclure du volet Utilisateurs et groupes, sélectionnez Sélectionner des utilisateurs et des **groupes**  >  **Utilisateurs et groupes**  >  **Sélectionner.**
5. Dans le **volet** Sélectionner, sélectionnez le **groupe GlobalAdmins,** puis **sélectionnez**  >  **Terminé.**
6. Dans la section **Affectations,** sélectionnez **Conditions.**
7. Dans le **volet Conditions,** sélectionnez Risque  de se connectez, sélectionnez Oui pour Configurer, Sélectionnez Élevé et **Moyen,** puis Sélectionnez Sélectionner **et** **Terminé.**   
8. Dans la section **Contrôles d’accès** du **nouveau** volet, sélectionnez **Accorder**.
9. Dans le **volet Accorder,** sélectionnez Bloquer **l’accès,** puis sélectionnez **Sélectionner.**
10. Dans le **volet** Nouveau, sélectionnez **Activer** pour **activer** la stratégie, puis sélectionnez **Créer.**
11. Fermez **le portail Azure et** **Centre d’administration Microsoft 365** onglets.

Pour tester la première stratégie, dé connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l’mf. Cela montre que la première stratégie est appliquée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Feuille de route des identités](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)