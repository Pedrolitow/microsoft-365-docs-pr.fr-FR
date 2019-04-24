---
title: Protéger les comptes d'administrateur général dans votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/16/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Suivez ces étapes pour protéger les comptes d'administrateur général dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: cded424188447f96e5614f31d3e207bb541d438e
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32290857"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-enterprise-test-environment"></a>Protéger les comptes d'administrateur général dans votre environnement de test Microsoft 365 Enterprise

Vous pouvez empêcher les attaques numériques sur votre organisation en vous assurant que les comptes administrateurs sont aussi sécurisés que possible. Cet article explique comment utiliser la sécurité des applications Cloud Office 365 et les stratégies d'accès conditionnel Azure AD pour protéger les comptes d'administrateur général.

Il existe deux phases pour la protection des comptes d'administrateur général dans votre environnement de test Microsoft 365 Enterprise:

1.  Créez l'environnement de test Microsoft 365 entreprise.
2.  Protégez votre compte d'administrateur général dédié.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

> [!NOTE]
> L'environnement de test Microsoft 365 entreprise utilise les versions E5 d'Office 365 et Enterprise Management + Security (EMS). La fonctionnalité de sécurité des applications Cloud Office 365 est uniquement disponible dans la version E5 Office 365. 

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1: créer votre environnement de test Microsoft 365 Enterprise

Si vous souhaitez simplement tester la protection de compte d'administrateur général de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d'administrateur général dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).

  
> [!NOTE]
> Le test de la protection de compte d'administrateur général ne nécessite pas l'environnement de test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour les services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu'option pour vous permettre de tester la protection des comptes d'administrateur général et de l'expérimenter dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-configure-cloud-app-security-and-conditional-access-policies"></a>Phase 2: configurer la sécurité des applications Cloud et les stratégies d'accès conditionnel

Tout d'abord, créez une stratégie de sécurité d'application Cloud Office 365 pour surveiller l'activité de compte d'administrateur général et envoyer des alertes à l'adresse de messagerie de votre compte d'administrateur général. 

1. Connectez-vous au [portail de conformité d'Office 365 Security &](https://protection.office.com/) à l'aide de votre compte d'administrateur général.
2. Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.
3. Sur la page **Gérer les alertes avancées**, cliquez sur **Activer Sécurité des applications cloud Office 365**, puis sur **Atteindre Sécurité des applications cloud Office 365**.
4. Sur le nouvel onglet **Tableau de bord**, cliquez sur **Contrôle > Stratégies**.
5. Sur la page **Stratégies**, cliquez sur **Créer une stratégie**, puis sur **Stratégie d’activité**.
6. Dans **Nom de la stratégie**, saisissez **Activité administrative**.
7. Dans **Gravité de la stratégie**, cliquez sur **Élevée**.
8. Dans **Catégorie**, cliquez sur **Comptes privilégiés**.
9. Dans **Créer des filtres pour la stratégie**, dans **Activités correspondant à tous les critères suivants**, cliquez sur **Activité administrative**.
10. Dans **Alertes**, cliquez sur **Envoyer une alerte par e-mail**. Dans **À**, entrez l’adresse de messagerie de votre compte d’administrateur général.
11. Au bas de la page, cliquez sur **Créer**.
12. Fermez l'onglet **tableau de bord** .
    
Ensuite, créez un compte d'utilisateur en tant qu'administrateur global dédié.

1. Sous un onglet séparé, ouvrez le [Centre d'administration Microsoft 365](https://admin.microsoft.com/).
2. Sous **utilisateurs actifs**, cliquez sur **Ajouter un utilisateur**.
3. Sur la page **nouvel utilisateur** , tapez **DedicatedAdmin** dans **prénom**, **nom d'affichage**et nom **d'utilisateur**.
4. Cliquez sur **mot de passe**, sur **me laisser créer le mot de**passe, puis tapez un mot de passe fort. Enregistrez le mot de passe de ce nouveau compte dans un emplacement sécurisé.
5. DéCochez **faire en sorte que cet utilisateur modifie son mot de passe lors de sa première connexion**.
6. Cliquez sur **rôles**, puis sur **administrateur général**.
7. Cliquez sur **licences de produit**, puis activez les licences **Enterprise Mobility + Security e5** et **Office 365 entreprise E5** sur.
8. Cliquez sur **Ajouter**.
9. Dans la **page l'utilisateur a été ajouté**, effacez le **mot de passe Envoyer un message électronique**, puis cliquez sur **Fermer**.

Ensuite, créez un groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Dans l'onglet **Centre d'administration Microsoft 365** , cliquez sur l'icône groupes dans le volet de navigation de gauche, puis cliquez sur **groupes**.
2. Cliquez sur **Ajouter un groupe**.
3. Sur la page **nouveau groupe** , tapez **GlobalAdmins**.
4. Cliquez sur **Sélectionner le propriétaire** , cliquez sur votre compte d'administrateur général, puis cliquez sur **Ajouter > fermer**.
5. Dans la liste des groupes, cliquez sur le groupe **GlobalAdmins** .
6. Sur la page **GlobalAdmins** , cliquez sur modifier le membre, puis sur **Ajouter** **des**membres.
7. Dans la liste, cliquez sur le compte **DedicatedAdmin** , puis cliquez sur **Enregistrer _GT_ fermer > fermer _GT_ Centre d'administration**.

Ensuite, créez des stratégies d'accès conditionnel pour exiger l'authentification multifacteur pour les comptes d'administrateur général et pour refuser l'authentification si le risque de connexion est moyen ou élevé.

Cette première stratégie nécessite que tous les comptes d'administrateur général utilisent l'authentification multiFACTEUR.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Azure Active Directory > accès conditionnel**.
3. Dans le panneau **accès conditionnel – stratégies** , cliquez sur **stratégie de base: exiger MFA pour les administrateurs (aperçu)**.
4. Sur les **stratégies de base...** , cliquez sur **utiliser la stratégie immédiatement _GT_ enregistrer**.

Cette deuxième stratégie bloque l'accès à l'authentification de compte d'administrateur général lorsque le risque de connexion est moyen ou élevé.

1. Dans le panneau **accès conditionnel – stratégies** , cliquez sur **nouvelle stratégie**.
2. Sur la **nouvelle** Blade, tapez **administrateurs globaux** dans **nom**.
3. Dans la **** section affectations, cliquez sur **utilisateurs et groupes**.
4. Sous l'onglet **inclure** du panneau **utilisateurs et groupes** , cliquez sur Sélectionner des utilisateurs et des groupes **> les utilisateurs et les groupes > sélectionner**.
5. Sur la Blade de **sélection** , cliquez sur le **GlobalAdmins > sélectionnez >**.
6. Dans la **** section affectations, cliquez sur **conditions**.
7. Dans le volet **conditions** , cliquez sur **risque de connexion**, cliquez sur **Oui** pour **configurer**, **sur haute** et **moyenne**, puis sur **sélection** et **fin**.
8. Dans la section **contrôles d'accès** de la **nouvelle** Blade, cliquez sur **accorder**.
9. Dans le panneau **accorder** , cliquez sur **bloquer l'accès**, puis sur **Sélectionner**.
10. Sur la **nouvelle** Blade, cliquez **** sur **activer pour activer la stratégie**, puis cliquez sur **créer**.
11. Fermez les onglets **portail Azure** et **Centre d'administration Microsoft 365** .

Pour tester la première stratégie, déconnectez-vous, puis connectez-vous avec le compte DedicatedAdmin. Vous devez être invité à configurer l'authentification multiFACTEUR sur le compte d'utilisateur. Cela démontre que la première stratégie est appliquée.

Consultez l'étape [protéger les comptes administrateur général](identity-designate-protect-admin-accounts.md#identity-global-admin) dans la phase d'identité pour obtenir des informations et des liens afin de protéger vos comptes d'administrateur général en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement d'entreprise Microsoft 365](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
