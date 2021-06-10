---
title: Écriture différée de mot de passe pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Résumé: Configurez l’écriture différée du mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: f1118c22ad1f65ea29bb14afacb7506a60d1fe1a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50921479"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Écriture différée de mot de passe pour votre environnement de test Microsoft 365

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les utilisateurs peuvent utiliser l’écriture écriture par mot de passe pour mettre à jour leurs mots de passe via Azure Active Directory (Azure AD), qui est ensuite répliqué vers vos services de domaine Active Directory (AD DS) locaux. Avec l’écriture écriture par mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leur mot de passe via les AD DS sur site où leurs comptes d’utilisateur d’origine sont stockés. Cela aide les utilisateurs itinérants ou distants qui n’ont pas de connexion d’accès à distance à leur réseau local.

Cet article explique comment configurer votre environnement de test Microsoft 365 pour l’écriture par mot de passe.

La configuration de votre environnement de test pour l’écriture par mot de passe implique deux phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Tout d’abord, suivez les instructions de la synchronisation [de hachage de mot de passe.](password-hash-sync-m365-ent-test-environment.md) La configuration qui en résulte ressemble à ceci :
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine TESTLAB AD DS avec le client Azure AD de vos abonnements Microsoft 365.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Phase 2 : Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.

Tout d’abord, configurez le compte utilisateur 1 avec le rôle d’administrateur général.

1. À partir du [Centre d’administration Microsoft 365](https://portal.microsoft.com), connectez-vous avec votre compte d’administrateur général.

2. Sélectionnez **Utilisateurs actifs.**
 
3. Dans la page **Utilisateurs** actifs, sélectionnez le **compte utilisateur1,**

4. Dans le **volet utilisateur 1,** **sélectionnez Modifier** à côté des **rôles.**

5. Dans le **volet Modifier les rôles d’utilisateur** pour user1, sélectionnez Administrateur **général,** **Sélectionnez Enregistrer,** puis **Fermer**.

Configurez ensuite le compte utilisateur 1 en lui attribuant les paramètres de sécurité qui lui permettent de modifier le mot de passe pour le compte d’autres utilisateurs dans le domaine TESTLAB AD DS.

1. À partir du[Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. Sur le bureau d’APP1, **sélectionnez Démarrer,** entrez **actif,** puis sélectionnez Utilisateurs **et ordinateurs Active Directory.**

3. Dans la barre de menus, sélectionnez **Afficher.** Si **les fonctionnalités avancées** ne sont pas activées, sélectionnez-la pour l’activer.

4. Dans le volet d’arborescence, sélectionnez et maintenez (ou cliquez avec le bouton droit) votre domaine, sélectionnez Propriétés, puis sélectionnez **l’onglet** Sécurité.

5. Sélectionnez **Avancé**.

6. Sous **l’onglet Autorisations,** sélectionnez **Ajouter.**

7. Sélectionnez **un principal,** entrez **User1,** puis **sélectionnez OK.**

8. Dans **S’applique à**, sélectionnez **Objets utilisateur Descendant**.

9. Sous **Autorisations**, sélectionnez les options suivantes :

    - **Modifier le mot de passe**
    - **Réinitialiser le mot de passe**

10. Sous **Propriétés**, sélectionnez les options suivantes :
    - **Écrire lockoutTime**
    - **Écrire pwdLastSet**

11. Sélectionnez **OK** trois fois pour enregistrer les modifications.

12. Fermer **Utilisateurs et Ordinateurs Active Directory**.

Ensuite, configurez de la Connexion Azure AD Connect sur APP1 pour écriture différée.

1. Si nécessaire, connectez-vous à APP1 avec le compte TESTLAB\User1.

2. À partir du bureau d’APP1, double-cliquez sur **Azure AD Connect**.

3. Dans la **page d’accueil,** **sélectionnez Configurer.**

4. Dans la page **Tâches supplémentaires,** sélectionnez **Personnaliser les options** de synchronisation, puis sélectionnez **Suivant.**

5. Sur la page **Connecter azure AD,** entrez vos informations d’identification de compte d’administrateur général, puis sélectionnez **Suivant.**

6. Dans les **Connecter et** les pages de filtrage **domaine/ou,** sélectionnez **Suivant**.

7. Dans la page **Fonctionnalités facultatives,** sélectionnez **Écriture écriture par** mot de passe, puis sélectionnez **Suivant**.

8. Dans la page **Prêt à configurer,** sélectionnez **Configurer** et attendez la fin du processus.

9. Lorsque vous voyez la configuration se terminer, sélectionnez **Quitter.**

Vous êtes maintenant prêt à tester l’écriture écriture par mot de passe pour les utilisateurs sur des ordinateurs qui ne sont pas connectés au réseau virtuel de votre intranet simulé.

La configuration qui en résulte ressemble à ceci :

![Environnement de test de l’entreprise simulée avec l’authentification directe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Un Microsoft 365 E5 d’essai ou payant avec le domaine DNS TESTLAB.\<*your domain name*> Inscrit(e).
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 au domaine TESTLAB AD DS.
- L’écriture différée de mot de passe est activée afin que les utilisateurs puissent modifier leur mot de passe via Azure AD sans avoir à se connecter à l’intranet simplifiée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)