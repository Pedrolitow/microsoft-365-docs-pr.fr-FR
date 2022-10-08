---
title: Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365
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
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Configurez et testez l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 47fd4209a271875a1ae046a7315eda5ada6b7edf
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68190922"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Azure AD Seamless Single Sign-On (Seamless SSO) connecte automatiquement les utilisateurs lorsqu’ils se trouvent sur leurs PC ou appareils connectés à leur réseau d’organisation. L’authentification unique transparente Azure AD offre aux utilisateurs un accès facile aux applications cloud sans avoir besoin de composants locaux supplémentaires.

Cet article explique comment configurer votre environnement de test Microsoft 365 pour l’authentification unique transparente Azure AD.

La configuration de l’authentification unique transparente Azure AD implique deux phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de [synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Votre configuration résultante ressemble à ceci :
  
![Entreprise simulée avec environnement de test de synchronisation de hachage de mot de passe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine TESTLAB services de domaine Active Directory (AD DS) avec le locataire Azure AD de votre abonnement Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1

Dans cette phase, configurez Azure AD Connect sur APP1 pour l’authentification unique transparente Azure AD, puis vérifiez qu’elle fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1. Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. À partir du bureau APP1, exécutez Azure AD Connect.

3. Dans la **page d’accueil**, **sélectionnez Configurer**.

4. Dans la page **Tâches supplémentaires** , **sélectionnez Modifier la connexion de l’utilisateur**, puis **sélectionnez Suivant**.

5. Dans la page **Se connecter à Azure AD** , entrez les informations d’identification de votre compte d’administrateur général, puis sélectionnez **Suivant**.

6. Dans la page **de connexion de l’utilisateur** , **sélectionnez Activer l’authentification unique**, puis **sélectionnez Suivant**.

7. Dans la page **Activer l’authentification unique** , **sélectionnez Entrer les informations d’identification**.

8. Dans la **boîte de dialogue Sécurité Windows**, entrez **user1** et le mot de passe du compte user1, sélectionnez **OK**, puis **sélectionnez Suivant**.

9. Dans la page **Prêt à configurer** , **sélectionnez Configurer**.

10. Dans la page **Configuration terminée** , sélectionnez **Quitter**.

11. Dans le Portail Azure, dans le volet gauche, sélectionnez **Azure Active Directory** > **Azure AD Connect**. Vérifiez que la fonctionnalité **d’authentification unique transparente** s’affiche comme **activée**.

Ensuite, testez la possibilité de vous connecter à votre abonnement avec le <strong>user1@testlab.</strong>\<*your public domain*> nom d’utilisateur du compte utilisateur1.

1. Dans Internet Explorer sur APP1, sélectionnez l’icône paramètres, puis sélectionnez **Options Internet**.
 
2. Dans **Options Internet**, sélectionnez l’onglet **Sécurité** .

3. Sélectionnez **Intranet local**, puis **Sites**.

4. Dans **l’intranet local**, sélectionnez **Avancé**.

5. Dans **Ajouter ce site web à la zone**, entrez **https <span>://</span>autologon.microsoftazuread-sso.com**, sélectionnez **Ajouter** > **fermer** > **OK** > **.**

6. Déconnectez-vous, puis reconnectez-vous avec un compte différent.

7. Lorsque vous êtes invité à vous connecter, spécifiez <strong>user1@testlab.</strong>\<*your public domain*> nom, puis sélectionnez **Suivant**. Vous devez correctement vous connecter en tant que User1 sans entrer un mot de passe. Cela prouve qu’ Azure AD transparente SSO fonctionne.

Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général pour Azure AD. Par conséquent, vous ne verrez pas l’icône **Administrateur** comme une option.

Voici la configuration obtenue :

![Entreprise simulée avec environnement de test d’authentification directe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Un Microsoft 365 E5 des abonnements d’évaluation ou payants avec le testlab de domaine DNS.\<*your domain name*> Inscrit(e).
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 au domaine TESTLAB AD DS.
- L’authentification unique transparente Azure AD est activée afin que les ordinateurs sur l’intranet simulé puissent se connecter aux ressources cloud Microsoft 365 sans spécifier de mot de passe de compte d’utilisateur.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)