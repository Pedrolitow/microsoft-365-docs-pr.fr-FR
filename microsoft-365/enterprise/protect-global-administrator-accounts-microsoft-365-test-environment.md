---
title: Protéger les comptes d’administrateur global dans votre environnement de test Microsoft 365 pour entreprises
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
description: Suivez ces étapes pour protéger les comptes d’administrateur global dans votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 4d444e217c5a232811701f6519c2eb3ebe86df70
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866862"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-enterprise-test-environment"></a>Protéger les comptes d’administrateur global dans votre environnement de test Microsoft 365 pour entreprises

Vous pouvez empêcher les attaques numériques dans votre organisation en s’assurant que vos comptes d’administrateur sont aussi sécurisés que possible. Cet article décrit comment utiliser les stratégies d’accès conditionnel de sécurité pour application Cloud Microsoft Office 365 et Azure AD pour protéger les comptes d’administrateur global.

Il existe deux phases à protéger les comptes d’administrateur global dans votre environnement de test Microsoft 365 pour entreprises :

1.  Créer l’environnement de test Microsoft 365 pour entreprises.
2.  Protéger votre compte d’administrateur global dédié.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez uniquement tester la protection des comptes d’administrateur global d’une manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la protection des comptes d’administrateur global dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test du compte d’administrateur global de protection ne nécessite pas de l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option de sorte que vous pouvez tester la protection des comptes d’administrateur global et tester dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-configure-cloud-app-security-and-conditional-access-policies"></a>Phase 2 : Configurer la sécurité d’application Cloud et stratégies d’accès conditionnel

Tout d’abord, créez une stratégie de sécurité d’application Office 365 dans le nuage pour surveiller l’activité de compte d’administrateur global et envoyer des alertes à l’adresse de messagerie de votre compte d’administrateur global. 

1. Connectez-vous au portail Office au [http://portal.office.com](http://portal.office.com) à l’aide de votre compte d’administrateur global.
2. Cliquez sur la vignette de **l’administrateur** . Dans l’onglet **Centre d’administration d’Office** , cliquez sur **centres d’administration > sécurité et conformité**.
3. Dans le volet de navigation de gauche, cliquez sur **Alertes > Gérer les alertes avancées**.
4. Sur la page **Gérer les alertes avancées**, cliquez sur **Activer Sécurité des applications cloud Office 365**, puis sur **Atteindre Sécurité des applications cloud Office 365**.
5. Sur le nouvel onglet **Tableau de bord**, cliquez sur **Contrôle > Stratégies**.
6. Sur la page **Stratégies**, cliquez sur **Créer une stratégie**, puis sur **Stratégie d’activité**.
7. Dans **Nom de la stratégie**, saisissez **Activité administrative**.
8. Dans **Gravité de la stratégie**, cliquez sur **Élevée**.
9. Dans **Catégorie**, cliquez sur **Comptes privilégiés**.
10. Dans **Créer des filtres pour la stratégie**, dans **Activités correspondant à tous les critères suivants**, cliquez sur **Activité administrative**.
11. Dans **Alertes**, cliquez sur **Envoyer une alerte par e-mail**. Dans **À**, entrez l’adresse de messagerie de votre compte d’administrateur général.
12. Au bas de la page, cliquez sur **Créer**.
13. Fermez l’onglet **tableau de bord** .
    
Ensuite, créez un nouveau compte d’utilisateur en tant qu’administrateur global dédié.

1. Sous l’onglet **Centre d’administration d’Office** , sous **utilisateurs actifs**, cliquez sur **Ajouter un utilisateur**.
2. Dans la page **nouvel utilisateur** , tapez **DedicatedAdmin** dans **prénom**, **nom complet**et **nom d’utilisateur**.
3. Cliquez sur **le mot de passe**et cliquez sur **me laisser créer le mot de passe**, puis tapez un mot de passe. Enregistrez le mot de passe pour ce compte dans un endroit sûr.
4. Désactivez **rendre cet utilisateur de modifier leur mot de passe lorsqu’ils se connectent tout d’abord**.
5. Cliquez sur **rôles**, puis cliquez sur **administrateur général**.
6. Cliquez sur **les licences de produit**, puis activer la **mobilité d’entreprise + E5 de sécurité** et des **licences Office 365 entreprise E5** .
7. Cliquez sur **Ajouter**.
8. Sur l' **utilisateur a été ajouté page**, désactivez **Envoyer le mot de passe dans le message électronique**, puis cliquez sur **Fermer**.

Ensuite, créez un nouveau groupe nommé GlobalAdmins et ajoutez-y le compte DedicatedAdmin.

1. Sous l’onglet **Centre d’administration d’Office** , cliquez sur l’icône de groupes dans le volet de navigation gauche, puis cliquez sur **groupes**.
2. Cliquez sur **Ajouter un groupe**.
3. Dans la page **Nouveau groupe** , tapez **GlobalAdmins**.
4. Cliquez sur cliquez sur **Sélectionnez propriétaire** de votre compte d’administrateur global, puis cliquez sur **Ajouter > Fermer**.
5. Dans la liste des groupes, cliquez sur le groupe **GlobalAdmins** .
6. Dans la page **GlobalAdmins** , cliquez sur **Modifier pour le membre**, puis cliquez sur **Ajouter des membres**.
7. Dans la liste, cliquez sur le compte **DedicatedAdmin** , puis cliquez sur **Enregistrer > Fermer > Fermer > Centre d’administration**.

Ensuite, créez des stratégies d’accès conditionnel d’exiger l’authentification multifacteur pour les comptes d’administrateur global et refuser l’authentification si le risque de connexion est moyen ou élevé.

Cette stratégie premier requiert que tous les comptes d’administrateur global utilisent MFA.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Azure Active Directory > accès conditionnel**.
3. Sur le serveur lame **accès conditionnel – stratégies** , cliquez sur **stratégie de base : nécessitent un MFA pour les administrateurs (preview)**.
4. Sur le serveur lame **... les stratégies de base** , cliquez sur **utiliser immédiatement la stratégie > Enregistrer**.

Ce deuxième stratégie bloque l’accès à l’authentification de compte administrateur global lorsque le risque de connexion est moyen ou élevé.

1. Sur le serveur lame **accès conditionnel – stratégies** , cliquez sur **nouvelle stratégie**.
2. Sur le serveur lame **New** , tapez **administrateurs globaux** dans **nom**.
3. Dans la section des **affectations** , cliquez sur **utilisateurs et groupes**.
4. Sous l’onglet **inclure** de la lame **utilisateurs et groupes** , cliquez sur **Sélectionnez Utilisateurs et groupes > utilisateurs et groupes > sélectionnez**.
5. Sur le serveur lame **Sélectionnez** , cliquez sur le **GlobalAdmins > sélectionnez > fait**.
6. Dans la section des **affectations** , cliquez sur **Conditions**.
7. Sur le serveur lame **Conditions** , cliquez sur **connexion risque**, cliquez sur **Oui** pour **configurer**, cliquez sur **élevé** et **moyen**, puis cliquez sur **Sélectionnez** et **fait**.
8. Dans la section **contrôle d’accès** de la lame de **Nouveau** , cliquez sur **accorder**.
9. Sur le serveur lame **Grant** , cliquez sur **Bloquer l’accès**, puis cliquez sur **Sélectionner**.
10. Sur le serveur lame **Nouveau** , cliquez **sur** pour **Activer la stratégie**, puis cliquez sur **créer**.
11. Fermez les onglets **Azure portal** et le **Centre d’administration d’Office** .

Pour tester la première stratégie, déconnectez-vous, puis connectez-vous à l’aide du compte DedicatedAdmin. Vous devez être invités à configurer MFA sur le compte d’utilisateur. Cela indique que la première stratégie est appliquée.

Voir l’étape de [comptes d’administrateur global Protect](identity-designate-protect-admin-accounts.md) lors de la phase d’identité pour des informations et des liens pour protéger vos comptes d’administrateur global en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 pour entreprises](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
