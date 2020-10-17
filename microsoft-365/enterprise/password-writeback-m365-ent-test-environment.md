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
ms.openlocfilehash: b999d50b0e98b11638199327bd7ffe7269b261ce
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487127"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Écriture différée de mot de passe pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les utilisateurs peuvent utiliser l’écriture différée de mot de passe pour mettre à jour leurs mots de passe via Azure Active Directory (Azure AD), qui est ensuite répliqué sur vos services de domaine Active Directory (AD DS) locaux. Avec l’écriture différée du mot de passe, les utilisateurs n’ont pas besoin de mettre à jour leurs mots de passe via le service AD DS local où leurs comptes d’utilisateur d’origine sont stockés. Cela permet aux utilisateurs itinérants ou distants qui n’ont pas de connexion d’accès à distance à leur réseau local.

Cet article explique comment configurer votre environnement de test Microsoft 365 pour l’écriture différée de mot de passe.

La configuration de votre environnement de test pour l’écriture différée de mot de passe implique deux phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Guides de Laboratoire de Test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Tout d’abord, suivez les instructions de la [synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md). La configuration obtenue se présente comme suit :
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine TESTLAB AD DS avec le client Azure AD de vos abonnements Microsoft 365.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Phase 2 : Activer l’écriture différée de mot de passe pour le domaine TESTLAB AD DS.

Tout d’abord, configurez le compte utilisateur 1 avec le rôle d’administrateur général.

1. À partir du [Centre d’administration Microsoft 365](https://portal.microsoft.com), connectez-vous avec votre compte d’administrateur général.

2. Sélectionnez **utilisateurs actifs**.
 
3. Sur la page **utilisateurs actifs** , sélectionnez le compte **utilisateur1** ,

4. Dans le volet **utilisateur1** , sélectionnez **modifier** en regard de **rôles**.

5. Dans le volet **modifier les rôles d’utilisateur** pour utilisateur1, sélectionnez **administrateur général**, sélectionnez **Enregistrer**, puis **Fermer**.

Configurez ensuite le compte utilisateur 1 en lui attribuant les paramètres de sécurité qui lui permettent de modifier le mot de passe pour le compte d’autres utilisateurs dans le domaine TESTLAB AD DS.

1. À partir du[Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. À partir du Bureau d’APP1, sélectionnez **Démarrer**, entrez **actif**, puis sélectionnez **utilisateurs et ordinateurs Active Directory**.

3. Dans la barre de menus, sélectionnez **affichage**. Si les **fonctionnalités avancées** ne sont pas activées, sélectionnez-la pour l’activer.

4. Dans le volet de l’arborescence, sélectionnez et maintenez (ou cliquez avec le bouton droit) votre domaine, sélectionnez **Propriétés**, puis sélectionnez l’onglet **sécurité** .

5. Sélectionnez **Avancé**.

6. Sous l’onglet **autorisations** , sélectionnez **Ajouter**.

7. Sélectionnez **Sélectionner un principal**, entrez **utilisateur1**, puis sélectionnez **OK**.

8. Dans**S’applique à**, sélectionnez **Objets utilisateur Descendant**.

9. Sous**Autorisations**, sélectionnez les options suivantes :

    - **Modifier le mot de passe**
    - **Réinitialiser le mot de passe**

10. Sous**Propriétés**, sélectionnez les options suivantes :
    - **Écrire lockoutTime**
    - **Écrire pwdLastSet**

11. Cliquez trois fois sur **OK** pour enregistrer les modifications.

12. Fermer**Utilisateurs et Ordinateurs Active Directory**.

Ensuite, configurez de la Connexion Azure AD Connect sur APP1 pour écriture différée.

1. Si nécessaire, connectez-vous à APP1 avec le compte TESTLAB\User1.

2. À partir du bureau d’APP1, double-cliquez sur **Azure AD Connect**.

3. Sur la **page Bienvenue**, sélectionnez **configurer**.

4. Sur la page **tâches supplémentaires** , sélectionnez **personnaliser les options de synchronisation**, puis **suivant**.

5. Sur la page **connexion à Azure ad** , entrez les informations d’identification de votre compte d’administrateur général, puis cliquez sur **suivant**.

6. Sur les pages de filtrage des **annuaires** et du **domaine/UO** , sélectionnez **suivant**.

7. Sur la page **fonctionnalités facultatives** , sélectionnez **écriture différée du mot de passe**, puis cliquez sur **suivant**.

8. Sur la page **prêt pour la configuration** , sélectionnez **configurer** et patientez jusqu’à ce que le processus se termine.

9. Lorsque la configuration est terminée, sélectionnez **quitter**.

Vous êtes maintenant prêt à tester l’écriture différée de mot de passe pour les utilisateurs sur des ordinateurs qui ne sont pas connectés au réseau virtuel de votre intranet simulé.

La configuration obtenue se présente comme suit :

![Environnement de test de l’entreprise simulée avec l’authentification directe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Un abonnement d’évaluation ou payant Microsoft 365 E5 avec le domaine DNS TESTLAB.\<*your domain name*> Inscrit(e).
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 au domaine TESTLAB AD DS.
- L’écriture différée de mot de passe est activée afin que les utilisateurs puissent modifier leur mot de passe via Azure AD sans avoir à se connecter à l’intranet simplifiée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)


