---
title: Écriture différée de mot de passe pour votre environnement de test Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Résumé: Configurez l’écriture différée du mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 98838bd61fb5664e0b8c8aed4f4b20dee39e0dec
ms.sourcegitcommit: 7ae0389cf06e2f481ee646556720ab3f3e93ea32
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "38757681"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Écriture différée de mot de passe pour votre environnement de test Microsoft 365

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

La réinitialisation du mot de passe permet aux utilisateurs de mettre à jour leur mot de passe via Azure Active Directory (Azure AD), qui est ensuite copié sur votre instance Active Directory Domain Services (AD DS) locale. Avec l’écriture différée de mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leur mot de passe localement via AD DS où les comptes d’utilisateurs et leurs attributs sont stockés. Cette étape est utile aux utilisateurs itinérants ou distants qui ne disposent pas d’une connexion d’accès à distance au réseau local.

Cet article décrit comment configurer l’écriture différée Azure AD pour votre environnement de test Microsoft 365.

Il existe deux phases de configuration :

1.  Création de l’environnement de test Microsoft 365 de l’entreprise simulée avec la synchronisation de hachage de mot de passe.
2.  Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.
    
![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Tout d’abord, suivez les instructions fournies dans l’article [Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md). Voici la configuration que vous obtenez.
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants :  
  
- Abonnement d’évaluation ou payant Microsoft 365 E5 ou Office 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. 
- Azure AD Connect s’exécute sur APP1 pour synchroniser périodiquement le domaine TESTLAB AD DS avec le client Azure AD de votre abonnement Microsoft 365 ou Office 365.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Phase 2 : Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.

Tout d’abord, configurez le compte utilisateur 1 avec le rôle d’administrateur général.

1. À partir du [Centre d’administration Microsoft 365](https://portal.microsoft.com), connectez-vous avec votre compte d’administrateur général.

2. Cliquez sur **Utilisateurs actifs**.
 
3. Sur la page**Activer les utilisateurs**, cliquez sur le compte**Utilisateur1**,

4. Sur le volet**user1**, cliquez sur **Modifier** près de**Rôles**.

5. Sur le volet pour user1**Modifier les rôles d’utilisateur**, cliquez sur**Administrateur général**. Cliquez sur **Enregistrer**, puis cliquez sur**Fermer**.

Configurez ensuite le compte utilisateur 1 en lui attribuant les paramètres de sécurité qui lui permettent de modifier le mot de passe pour le compte d’autres utilisateurs dans le domaine TESTLAB AD DS.

1. À partir du[Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2.  À partir du bureau du APP1, cliquez sur**Démarrer**, tapez **actif**, puis cliquez sur **Utilisateurs et ordinateurs Active Directory**.

3. Cliquez sur **Affichage** dans la barre de menu. Si**Fonctionnalités avancées** n’est ne pas activée, cliquez dessus pour l’activer.

4. Dans le volet d’arborescence, cliquez sur votre domaine avec le bouton droit, cliquez sur**Propriétés**, puis cliquez sur l’onglet**Sécurité**.

5. Cliquez sur**Avancé**.

6. Sous l'onglet**Autorisations**, cliquez sur**Ajouter**.

7. Cliquez sur**Sélectionnez un principal**, tapez**Utilisateur1**, puis cliquez sur**OK**.

8. Dans**S’applique à**, sélectionnez **Objets utilisateur Descendant**.

9. Sous**Autorisations**, sélectionnez les options suivantes :

    - Modifier le mot de passe
    - Réinitialiser le mot de passe

10. Sous**Propriétés**, sélectionnez les options suivantes :
    - Écrire lockoutTime
    - Écrire pwdLastSet

11. Cliquez trois fois sur **OK** pour enregistrer les modifications.

12. Fermer**Utilisateurs et Ordinateurs Active Directory**.

Ensuite, configurez de la Connexion Azure AD Connect sur APP1 pour écriture différée.

1. Si nécessaire, connectez-vous à APP1 avec le compte TESTLAB\User1.

2. À partir du bureau d’APP1, double-cliquez sur **Azure AD Connect**.

3. Sur la page**Bienvenue**, cliquez sur**Configurer**.

4. Sur la page**Tâches supplémentaires**, sélectionnez sur**Personnaliser les options de synchronisation**, puis cliquez sur**Suivant**.

5. Sur la page **Connexion à Azure AD**, tapez vos informations d’identification d’administrateur général, puis cliquez sur **Suivant**.

6. Sur les pages**Connecter les répertoires** et **Domaine/Filtrage**, cliquez sur**Suivant**.

7. Sur la page** Fonctionnalités facultatives**, sélectionnez **Écriture différée de mot de passe** et cliquez sur **Suivan**t. 

8. Sur la page**Prêt à configurer**, cliquez sur**Configurer** et attendez que le processus se termine.

9. Lorsque vous voyez que la configuration se termine, cliquez sur **Sortie**.

Vous êtes maintenant prêt à tester l’écriture différée de mot de passe pour les utilisateurs sur des ordinateurs sur lesquels vous n’êtes pas connecté au réseau virtuel de votre intranet simulé.

Voici la configuration obtenue :

![Environnement de test de l’entreprise simulée avec l’authentification directe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Les abonnements en version payante ou d’évaluation Microsoft 365 E5 et Office 365 E5 avec le domaine DNS TESTLAB.\<votre nom de domaine> enregistré.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. 
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 ou Office 365 au domaine TESTLAB AD DS. 
- L’écriture différée de mot de passe est activée afin que les utilisateurs puissent modifier leur mot de passe via Azure AD sans avoir à se connecter à l’intranet simplifiée.

Consultez l’étape [Simplifier les réinitialisations de mot de passe](identity-add-user-accounts.md#identity-pw-writeback) de la phase d’identification pour obtenir des informations et des liens qui vous permettront de configurer l’écriture différée de mot de passe en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)


