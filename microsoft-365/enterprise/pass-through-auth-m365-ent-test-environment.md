---
title: Authentification directe pour votre environnement de test Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/13/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Découvrez comment configurer l’authentification directe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: e925f0b48194c94993e7bf3e08f1f18650b19a23
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32290926"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Authentification directe pour votre environnement de test Microsoft 365

Les organisations désireuses d’utiliser directement leur infrastructure d’Active Directory Domain Services (AD DS) en local pour l’authentification aux applications et services sur le cloud Microsoft peuvent utiliser l’authentification directe. Cet article décrit comment configurer l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365. Voici la configuration que vous obtenez:
  
![Environnement de test de l’entreprise simulée avec l’authentification directe](media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Les deux phases de configuration de cet environnement de test sont les suivantes :

1.  Création de l’environnement de test Microsoft 365 de l’entreprise simulée avec la synchronisation de hachage de mot de passe.
2.  Configuration de l’authentification directe pour Azure AD Connect sur APP1.
    
![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions fournies dans l’article [Synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Voici la configuration que vous obtenez.
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants :  
  
- Les abonnements à la version payante ou d’évaluation Office 365 E5 et EMS E5.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine Windows Server AD TESTLAB (Active Directory Domain Services :AD DS) avec le client Azure AD de vos abonnements Office 365 et EMS E5 de manière périodique.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Phase 2 : Configuration de l’authentification directe pour Azure AD Connect sur APP1

Durant cette phase, vous allez configurer Azure AD Connect sur APP1 pour qu’il utilise l’authentification directe, puis vérifier que tout fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1.  Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2.  Sur le bureau d’APP1, exécutez Azure AD Connect.

3.  Sur la page **Bienvenue**, cliquez sur **Configurer**.

4.  Sur la page Tâches supplémentaires, cliquez sur **Modifier la connexion utilisateur**, puis sur **Suivant**.

5.  Sur la page **Connexion à Azure AD**, tapez vos informations d’identification d’administrateur général, puis cliquez sur **Suivant**.

6.  Sur la page **Connexion de l’utilisateur**, cliquez sur **Authentification directe**, puis sur **Suivant**.

7.  Sur la page **Prêt à configurer**, cliquez sur **Configurer**.

8.  Sur la page **Configuration terminée**, cliquez sur **Quitter**.

9.  Sur le Portail Azure, dans le volet gauche, cliquez sur **Azure Active Directory > Azure AD Connect**. Vérifiez que la fonctionnalité **Authentification directe** affiche l’état **Activé**.

10. Cliquez sur **Authentification directe**. Le volet **Authentification directe** répertorie les serveurs où vos agents d’authentification sont installés. APP1 devrait figurer dans la liste. Fermez le volet **Authentification directe**.

Ensuite, vérifiez si vous pouvez vous connecter à votre abonnement Office 365 avec le nom d’utilisateur <strong>utilisateur1@testlab.</strong>\<votre domaine public> du compte Utilisateur1.

1. Dans APP1, déconnectez-vous d’Office 365, puis reconnectez-vous avec un autre compte.

2. Quand vous êtes invité à saisir le nom d’utilisateur et le mot de passe, indiquez <strong>utilisateur1@testlab.</strong>\<votre domaine public> et le mot de passe de l’Utilisateur1. Vous serez connecté en tant qu’Utilisateur1. Vous devez correctement vous connecter en tant qu’ Utilisateur1.

Notez que même si les utilisateurs User1 disposent des autorisations d’administrateur de domaine pour le domaine TESTLAB AD DS, il n’est pas un administrateur général pour Office 365. Par conséquent, vous ne verrez pas l’icône**Administrateur**comme une option.

Voici la configuration obtenue :

![Environnement de test de l’entreprise simulée avec l’authentification directe](media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Cette configuration se compose des éléments suivants : 

- Les abonnements à la version payante ou d’évaluation Office 365 E5 et EMS E5 avec le domaine DNS TESTLAB.\<votre nom de domaine> enregistré.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Un agent d’authentification s’exécute sur APP1 pour traiter les demandes d’authentification directe provenant du client Azure AD de vos abonnements Office 365 et EMS E5.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)


