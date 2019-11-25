---
title: Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/21/2019
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
description: 'Résumé : Configurez et testez l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: f263ab507e392c1172d28b5d6ef111d8d9f40682
ms.sourcegitcommit: fb3815ee186b2b3ec790ee32a9d7b1628d623b0b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "39202235"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365

*Ce Guide de Laboratoire Test peut être utilisé pour les environnements de test Microsoft 365 Entreprise et Office 365 Entreprise*.

L’authentification unique (SSO) transparente Azure AD connecte automatiquement les utilisateurs quand ils sont sur un PC ou un appareil connecté au réseau de leur organisation. L’authentification unique transparente Azure AD permet aux utilisateurs d’accéder facilement aux applications informatiques sans avoir besoin de composants locaux supplémentaires.

Cet article décrit comment configurer l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365.

Il existe deux phases de configuration :

1.  Création de l’environnement de test Microsoft 365 de l’entreprise simulée avec la synchronisation de hachage de mot de passe.
2.  Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1.
    
![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions fournies dans l’article [Synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Voici la configuration que vous obtenez.
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants :  
  
- Abonnements d’évaluation ou payants Microsoft 365 E5 ou Office 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. 
- Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine Windows Server AD TESTLAB (Active Directory Domain Services : AD DS) avec le client Azure AD de votre abonnement Microsoft 365 ou Office 365 de manière périodique.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1

Durant cette phase, vous allez configurer Azure AD Connect sur APP1 pour qu’il utilise l’authentification unique transparente Azure AD, puis vérifier que tout fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1. Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. Sur le bureau d’APP1, exécutez Azure AD Connect.

3. Sur la page**Bienvenue**, cliquez sur**Configurer**.

4. Sur la page **Tâches supplémentaires**, cliquez sur **Modifier la connexion utilisateur**, puis sur **Suivant**.

5. Sur la page **Connexion à Azure AD**, tapez vos informations d’identification d’administrateur général, puis cliquez sur **Suivant**.

6. Sur la page **Connexion utilisateur**, sélectionnez **Activer l’authentification unique**, puis cliquez sur **Suivant**.

7. Sur la page **Activer l’authentification unique**, cliquez sur **Entrer les informations d’identification**.

8. Dans la boîte de dialogue **Sécurité Windows**, tapez **user1** et le mot de passe du compte Utilisateur1, puis cliquez sur **OK**. Cliquez sur **Suivant**.

9. Sur la page **Prêt à configurer**, cliquez sur **Configurer**.

10. Sur la page **Configuration terminée**, cliquez sur **Quitter**.

11. Sur le Portail Azure, dans le volet gauche, cliquez sur **Azure Active Directory > Azure AD Connect**. Vérifiez que la fonctionnalité **Authentification unique transparente** affiche l’état **Activé**.

Vérifiez ensuite si vous pouvez vous connecter à votre abonnement avec le nom d’utilisateur <strong>utilisateur1@testlab.</strong>\<votre domaine public> du compte Utilisateur1.

1. Dans Internet Explorer sur APP1, cliquez sur l’icône Paramètres, puis cliquez sur **Options Internet**.
 
2. Dans **Options Internet**, cliquez sur l’onglet **Sécurité**.

3. Cliquez sur **Intranet local**, puis sur **Sites**.

4. Dans **Intranet Local**, cliquez sur **Avancé**.

5. Dans **Ajouter ce site web à la zone**, tapez **https<span>://</span>autologon.microsoftazuread-sso.com**, cliquez sur **Ajouter > Fermer > OK > OK**.

6. Déconnectez-vous, puis reconnectez-vous avec un compte différent.

7. Lorsque vous êtes invité à vous connecter, spécifiez<strong>user1@testlab.</strong>\<votre domaine public > nom, puis cliquez sur **suivant**. Vous devez correctement vous connecter en tant que User1 sans entrer un mot de passe. Cela prouve qu’ Azure AD transparente SSO fonctionne.

Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général pour Azure AD. Par conséquent, vous ne verrez pas l’icône**Administrateur**comme une option.

Voici la configuration obtenue :

![Environnement de test de l’entreprise simulée avec l’authentification directe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)

 
Cette configuration se compose des éléments suivants : 

- Les abonnements à la version payante ou d’évaluation Microsoft 365 E5 et Office 365 E5 avec le domaine DNS TESTLAB.\<votre nom de domaine> enregistré.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. 
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 ou Office 365 au domaine TESTLAB AD DS. 
- L’authentification unique transparente Azure AD est activée pour permettre aux ordinateurs sur l’intranet simulé de se connecter aux ressources cloud Microsoft 365 sans avoir à spécifier le mot de passe du compte d’utilisateur.

Consultez l’étape [Simplifier la connexion de l’utilisateur](identity-secure-your-passwords.md#identity-sso) de la phase d’identité pour obtenir des informations et des liens pour configurer l’authentification unique transparente Azure AD en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)


