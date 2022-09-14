---
title: Synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: 'Résumé : Découvrez comment configurer la connexion et la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 35dcaa6cf4612283a7e1890345c5b5d99ba798e0
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67669978"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

De nombreuses organisations utilisent Azure AD Connect et la synchronisation de hachage de mot de passe pour synchroniser l’ensemble de comptes dans leur forêt Active Directory Domain Services (AD DS) en local avec l’ensemble des comptes dans le client Azure AD de leur abonnement Microsoft 365. 

Cet article explique comment ajouter la synchronisation de hachage de mot de passe à votre environnement de test Microsoft 365, ce qui entraîne cette configuration :
  
![Entreprise simulée avec environnement de test de synchronisation de hachage de mot de passe.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
La configuration de cet environnement de test implique trois phases :
- [Phase 1 : création de l’environnement de test de l’entreprise simulée pour Microsoft 365](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Phase 2 : création et enregistrement du domaine testlab](#phase-2-create-and-register-the-testlab-domain)
- [Phase 3 : installation d’Azure AD Connect sur APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, accédez à [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Phase 1 : création de l’environnement de test de l’entreprise simulée pour Microsoft 365

Suivez les instructions de [la configuration de base d’entreprise simulée pour Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Votre configuration résultante ressemble à ceci :
  
![Configuration de base d’entreprise simulée.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 dans un réseau virtuel Azure. DC1 est un contrôleur de domaine pour testlab.<*votre nom de domaine public*> domaine AD DS.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Phase 2 : création et enregistrement du domaine testlab

Dans cette phase, ajoutez un domaine DNS public, puis ajoutez-le à votre abonnement.

Tout d’abord, collaborez avec votre fournisseur d’inscription DNS public pour créer un nom de domaine DNS public basé sur votre nom de domaine actuel, puis ajoutez-le à votre abonnement. Nous vous recommandons d’utiliser le nom **testlab.<*votre domaine*> public**. Par exemple, si votre nom de domaine public est **<span>contoso.com</span>**, ajoutez le nom de domaine public : **<span>testlab.contoso.com</span>**.
  
Ensuite, ajoutez **testlab.<*votre domaine de domaine*> public** à votre version d’évaluation ou abonnement payant Microsoft 365 en suivant le processus d’inscription du domaine. Il s’agit d’ajouter des enregistrements DNS supplémentaires à **testlab.<*votre domaine de domaine*> public**. Pour plus d’informations, consultez [Ajouter un domaine à Microsoft 365](../admin/setup/add-domain.md).

Votre configuration résultante ressemble à ceci :
  
![Inscription du nom de domaine de votre testlab.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Cette configuration se compose des éléments suivants : 

- Une version d’évaluation Microsoft 365 E5 ou un abonnement payant avec le domaine DNS testlab.<*votre nom de domaine public*> inscrit.
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.

Notez que testlab.<*votre> de nom de domaine public* est maintenant :

- Il est pris en charge par les enregistrements DNS publics.
- Enregistré dans vos abonnements Microsoft 365.
- Le domaine Windows Server AD se trouve sur votre intranet simulé.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Phase 3 : installation d’Azure AD Connect sur APP1

Dans cette phase, installez et configurez l’outil Azure AD Connect sur APP1, puis vérifiez qu’il fonctionne.
  
Tout d’abord, installez et configurez Azure AD Connect sur APP1.

1. Dans le [portail Azure](https://portal.azure.com), connectez-vous avec votre compte d’administrateur général, puis connectez-vous à APP1 avec le compte TESTLAB\\Utilisateur1.
    
2. Sur le bureau d’APP1, ouvrez une invite de commandes Windows PowerShell de niveau administrateur, puis exécutez les commandes suivantes pour désactiver la sécurité renforcée d’Internet Explorer :
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Dans la barre des tâches, sélectionnez **Internet Explorer** et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. Dans la page Microsoft Azure Active Directory Connexion, **sélectionnez Télécharger**, puis **Exécuter**.
    
5. Dans la page **Bienvenue dans Azure AD Connect** , sélectionnez **Je suis d’accord**, puis **sélectionnez Continuer**.
    
6. Dans la page **Paramètres rapides** , sélectionnez **Utiliser les paramètres express**.
    
7. Dans la page **Se connecter à Azure AD** , entrez le nom de votre compte d’administrateur général dans **Nom d’utilisateur,** entrez son mot de passe dans **Mot de passe**, puis sélectionnez **Suivant**.
    
8. Dans la page **Se connecter à AD DS** , entrez **TESTLAB\\User1** dans **Username,** entrez son mot de passe dans **Mot de passe**, puis sélectionnez **Suivant**.
    
9. Dans la page **Prêt à configurer** , sélectionnez **Installer**.
    
10. Dans la page **Configuration terminée** , sélectionnez **Quitter**.
    
11. Dans Internet Explorer, accédez au Centre d’administration Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. Dans le volet de navigation gauche, sélectionnez **Utilisateurs > Utilisateurs actifs**.
    
    Notez le compte nommé **Utilisateur 1**. Ce compte provient du domaine TESTLAB AD DS et prouve que la synchronisation d’annuaires a fonctionné.
    
13. Sélectionnez le compte **User1** , puis les **licences et les applications**.
    
14. Dans **les licences de produit**, sélectionnez votre emplacement (si nécessaire), désactivez la licence **Office 365 E5**, puis activez la licence **Microsoft 365 E5**. 

15. Sélectionnez **Enregistrer** en bas de la page, puis **Fermer**.
    
Ensuite, testez la possibilité de vous connecter à votre abonnement avec le **user1@testlab.<nom d’utilisateur de *votre nom*> de domaine** du compte User1 :

1. Dans APP1, déconnectez-vous, puis reconnectez-vous avec un compte différent.

2. Lorsque vous êtes invité à entrer un nom d’utilisateur et un mot de passe, spécifiez **user1@testlab.<*votre nom*> de domaine** et le mot de passe User1. Vous devez correctement vous connecter en tant qu’ Utilisateur1.
 
Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général. Par conséquent, vous ne verrez pas l’icône **Administrateur** comme une option. 

Votre configuration résultante ressemble à ceci :

![Entreprise simulée avec environnement de test de synchronisation de hachage de mot de passe.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Cette configuration se compose des éléments suivants :  
  
- Microsoft 365 E5 ou Office 365 E5 abonnements d’évaluation ou payants avec le domaine DNS TESTLAB.<*votre nom de domaine*> inscrit.
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine TESTLAB AD DS avec le locataire Azure AD de votre abonnement Microsoft 365.
- Le compte Utilisateur1 dans le domaine TESTLAB  AD DS a été synchronisé avec le client Azure AD.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)