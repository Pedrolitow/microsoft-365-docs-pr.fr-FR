---
title: Authentification directe pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Découvrez comment configurer l’authentification directe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: c23f5cc99ca11ec19cb555541d798b8b4c74bd71
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68177655"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Authentification directe pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Les organisations désireuses d’utiliser directement leur infrastructure d’Active Directory Domain Services (AD DS) en local pour l’authentification aux applications et services sur le cloud Microsoft peuvent utiliser l’authentification directe. Cet article décrit comment configurer l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365. Voici la configuration que vous obtenez:
  
![Entreprise simulée avec environnement de test d’authentification directe.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Les deux phases de configuration de cet environnement de test sont les suivantes :

1.    Création de l’environnement de test Microsoft 365 de l’entreprise simulée avec la synchronisation de hachage de mot de passe.
2.    Configuration de l’authentification directe pour Azure AD Connect sur APP1.
    
![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](../downloads/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de [synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Voici la configuration finale.
  
![Entreprise simulée avec environnement de test de synchronisation de hachage de mot de passe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants :  
  
- Microsoft 365 E5 d’essai ou d’abonnement payant.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine TESTLAB AD DS avec le client Azure AD de votre abonnement Microsoft 365 de manière périodique.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Phase 2 : Configuration de l’authentification directe pour Azure AD Connect sur APP1

Durant cette phase, vous allez configurer Azure AD Connect sur APP1 pour qu’il utilise l’authentification directe, puis vérifier que tout fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1.    Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2.    Sur le bureau d’APP1, exécutez Azure AD Connect.

3.    Sur la page **Bienvenue**, cliquez sur **Configurer**.

4.    Sur la page Tâches supplémentaires, cliquez sur **Modifier la connexion utilisateur**, puis sur **Suivant**.

5.    Sur la page **Connexion à Azure AD**, tapez vos informations d’identification d’administrateur général, puis cliquez sur **Suivant**.

6.    Sur la page **Connexion de l’utilisateur**, cliquez sur **Authentification directe**, puis sur **Suivant**.

7.    Sur la page **Prêt à configurer**, cliquez sur **Configurer**.

8.    Sur la page **Configuration terminée**, cliquez sur **Quitter**.

9.    From the Azure portal, in the left pane, click **Azure Active Directory > Azure AD Connect**. Verify that the **Pass-through authentication** feature appears as **Enabled**.

10.    Click **Pass-through authentication**. The **Pass-through authentication** pane lists the servers where your Authentication Agents are installed. You should see APP1 in the list. Close the **Pass-through authentication** pane.

Ensuite, testez la possibilité de vous connecter à votre abonnement avec le <strong>user1@testlab.</strong>\<your public domain> nom d’utilisateur du compte utilisateur1.

1. Dans APP1, déconnectez-vous, puis reconnectez-vous avec un compte différent.

2. Quand vous êtes invité à saisir le nom d’utilisateur et le mot de passe, indiquez <strong>utilisateur1@testlab.</strong>\<your public domain> et le mot de passe utilisateur1. Vous devez correctement vous connecter en tant qu’ Utilisateur1.

Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général. Par conséquent, vous ne verrez pas l’icône **Administrateur** comme une option.

Voici la configuration obtenue :

![Entreprise simulée avec environnement de test d’authentification directe.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Cette configuration se compose des éléments suivants : 

- Un Microsoft 365 E5 des abonnements d’évaluation ou payants avec le testlab de domaine DNS.\<your domain name> Inscrit(e).
- A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. An Authentication Agent runs on APP1 to handle pass-through authentication requests from the Azure AD tenant of your Microsoft 365 subscription.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)