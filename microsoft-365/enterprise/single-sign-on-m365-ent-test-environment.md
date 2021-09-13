---
title: Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
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
description: 'Résumé : Configurez et testez l’authentification unique transparente Azure AD pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: f6fb0ac24f571c329070dd1667f6370c2067d4fd
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59179700"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les environnements Microsoft 365'entreprise et Office 365 Entreprise test.*

Azure AD Seamless Single Sign-On (Seamless SSO) connecte automatiquement les utilisateurs lorsqu’ils se connectent à leur PC ou appareils connectés au réseau de leur organisation. Azure AD Seamless SSO fournit aux utilisateurs un accès facile aux applications basées sur le cloud sans avoir besoin de composants locaux supplémentaires.

Cet article explique comment configurer votre environnement de test Microsoft 365 pour l' sso transparente Azure AD.

La configuration de l' ssO transparente Azure AD implique deux phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de synchronisation [de hachage de](password-hash-sync-m365-ent-test-environment.md)mot de passe pour Microsoft 365 . 

La configuration qui en résulte ressemble à ceci :
  
![Environnement de test de l’entreprise simulée avec synchronisation de hachage de mot de passe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connecter s’exécute sur APP1 pour synchroniser périodiquement le domaine des services de domaine Active Directory (AD DS) TESTLAB avec le client Azure AD de votre abonnement Microsoft 365 client.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1

Dans cette phase, configurez Azure AD Connecter sur APP1 pour azure AD Seamless SSO, puis vérifiez qu’elle fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1. Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. À partir du bureau APP1, exécutez Azure AD Connecter.

3. Dans la **page d’accueil,** **sélectionnez Configurer.**

4. Dans la page **Tâches supplémentaires,** sélectionnez Modifier la **connectez-vous** de l’utilisateur, puis sélectionnez **Suivant**.

5. Sur la page **Connecter azure AD,** entrez vos informations d’identification de compte d’administrateur général, puis sélectionnez **Suivant.**

6. Dans la page **De la page De l’utilisateur,** **sélectionnez Activer l' sign-on unique,** puis sélectionnez **Suivant**.

7. Dans la page **Activer l' sign-on unique,** **sélectionnez Entrer les informations d’identification.**

8. Dans la **boîte Sécurité Windows** dialogue, entrez **user1** et le mot de passe du compte user1, **sélectionnez OK,** puis sélectionnez **Suivant**.

9. Dans la page **Prêt à configurer,** sélectionnez **Configurer.**

10. Dans la page **Configuration terminée,** sélectionnez **Quitter.**

11. Dans le portail Azure, dans le volet gauche, sélectionnez Azure Active Directory  >  **azure AD Connecter**. Vérifiez que la **fonctionnalité d' sign-on unique** transparente apparaît comme **activée.**

Ensuite, testez la possibilité de vous inscrire à votre abonnement avec le <strong>user1@testlab.</strong>\<*your public domain*> nom d’utilisateur du compte utilisateur1.

1. Dans Internet Explorer sur APP1, sélectionnez l’icône paramètres, puis sélectionnez **Options Internet.**
 
2. Dans **Options Internet,** sélectionnez **l’onglet** Sécurité.

3. Sélectionnez **Intranet local,** puis **Sites**.

4. Dans **l’intranet local,** sélectionnez **Avancé**.

5. Dans **Ajouter ce site web à la zone,** entrez **https <span>://</span>autologon.microsoftazuread-sso.com**, **sélectionnez Ajouter**  >  **Fermer**  >    >  **OK**.

6. Déconnectez-vous, puis reconnectez-vous avec un compte différent.

7. Lorsque vous y sont invités, spécifiez <strong>user1@testlab.</strong>\<*your public domain*> nom, puis sélectionnez **Suivant**. Vous devez correctement vous connecter en tant que User1 sans entrer un mot de passe. Cela prouve qu’ Azure AD transparente SSO fonctionne.

Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général pour Azure AD. Par conséquent, vous ne verrez pas l’icône **Administrateur** comme une option.

Voici la configuration obtenue :

![Environnement de test de l’entreprise simulée avec authentification directe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Un Microsoft 365 E5 d’essai ou payant avec le domaine DNS testlab.\<*your domain name*> Inscrit(e).
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 au domaine TESTLAB AD DS.
- Azure AD Seamless SSO is enabled so that computers on the simulated intranet can sign in to Microsoft 365 cloud resources without specifying a user account password.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)