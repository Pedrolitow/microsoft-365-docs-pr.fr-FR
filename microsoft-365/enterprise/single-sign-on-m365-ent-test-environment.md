---
title: Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: f98f82de50feb2a9f92d1ecc4775c5307b314a72
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487599"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Authentification unique transparente Azure AD pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

La Sign-On unique transparente Azure AD (authentification unique transparente) se connecte automatiquement aux utilisateurs lorsqu’ils se trouvent sur leurs PC ou appareils connectés au réseau de leur organisation. L’authentification unique transparente Azure AD permet aux utilisateurs d’accéder facilement aux applications basées sur le Cloud sans avoir besoin de composants locaux supplémentaires.

Cet article explique comment configurer l’authentification unique transparente pour Azure AD pour votre environnement de test Microsoft 365.

La configuration de l’authentification unique transparente Azure AD implique deux phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de la [synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

La configuration obtenue se présente comme suit :
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine des services de domaine Active Directory (AD DS) TESTLAB avec le client Azure AD de votre abonnement Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Phase 2 : Configuration de l’authentification unique transparente Azure AD pour Azure AD Connect sur APP1

Dans cette phase, configurez Azure AD Connect sur APP1 for Azure AD transparent SSO, puis vérifiez qu’elle fonctionne.

### <a name="configure-azure-ad-connect-on-app1"></a>Configuration d’Azure AD Connect sur APP1

1. Dans le [Portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\Utilisateur1.

2. À partir du Bureau APP1, exécutez Azure AD Connect.

3. Sur la **page Bienvenue**, sélectionnez **configurer**.

4. Sur la page **tâches supplémentaires** , sélectionnez **modifier la connexion de l’utilisateur**, puis cliquez sur **suivant**.

5. Sur la page **connexion à Azure ad** , entrez les informations d’identification de votre compte d’administrateur général, puis cliquez sur **suivant**.

6. Sur la page de connexion de l' **utilisateur** , sélectionnez **activer l’authentification unique**, puis cliquez sur **suivant**.

7. Sur la page **activer l’authentification unique** , sélectionnez **entrer les informations d’identification**.

8. Dans la boîte de dialogue **sécurité Windows** , entrez **utilisateur1** et le mot de passe du compte User1, sélectionnez **OK**, puis **suivant**.

9. Sur la page **prêt à configurer** , sélectionnez **configurer**.

10. Sur la page **Configuration terminée** , sélectionnez **quitter**.

11. À partir du portail Azure, dans le volet de gauche, sélectionnez **Azure Active Directory**  >  **Azure ad Connect**. Vérifiez que la fonctionnalité **d’authentification unique transparente** apparaît comme **activée**.

Ensuite, testez la capacité à se connecter à votre abonnement avec le <strong>User1@testlab.</strong>\<*your public domain*> nom d’utilisateur du compte utilisateur1.

1. À partir d’Internet Explorer sur APP1, sélectionnez l’icône Paramètres, puis sélectionnez **Options Internet**.
 
2. Dans **Options Internet**, sélectionnez l’onglet **sécurité** .

3. Sélectionnez **Intranet local**, puis **sites**.

4. Dans **Intranet local**, sélectionnez **avancé**.

5. Dans **ajouter ce site Web à la zone**, entrez **https<span>://</span>AutoLogon.microsoftazuread-SSO.com**, sélectionnez **Ajouter**  >  **Fermer**  >  **OK**  >  **OK**.

6. Déconnectez-vous, puis reconnectez-vous avec un compte différent.

7. Lorsque vous êtes invité à vous connecter, spécifiez <strong>User1@testlab.</strong>\<*your public domain*> nom, puis cliquez sur **suivant**. Vous devez correctement vous connecter en tant que User1 sans entrer un mot de passe. Cela prouve qu’ Azure AD transparente SSO fonctionne.

Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général pour Azure AD. Par conséquent, vous ne verrez pas l’icône**Administrateur**comme une option.

Voici la configuration obtenue :

![Environnement de test de l’entreprise simulée avec l’authentification directe](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Cette configuration se compose des éléments suivants : 

- Un abonnement d’évaluation ou payant Microsoft 365 E5 avec le domaine DNS testlab.\<*your domain name*> Inscrit(e).
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes et des groupes du client Azure AD de votre abonnement Microsoft 365 au domaine TESTLAB AD DS.
- L’authentification unique transparente Azure AD est activée afin que les ordinateurs de l’intranet simulé puissent se connecter aux ressources cloud de Microsoft 365 sans spécifier de mot de passe de compte d’utilisateur.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
