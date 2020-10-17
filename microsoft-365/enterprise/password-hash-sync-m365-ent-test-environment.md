---
title: Synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/26/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: 'Résumé : Découvrez comment configurer la connexion et la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 3c20d1997be2ff47f0b449cbba3afb1e6edcd59a
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487457"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

De nombreuses organisations utilisent Azure AD Connect et la synchronisation de hachage de mot de passe pour synchroniser l’ensemble de comptes dans leur forêt Active Directory Domain Services (AD DS) en local avec l’ensemble des comptes dans le client Azure AD de leur abonnement Microsoft 365. 

Cet article explique comment vous pouvez ajouter la synchronisation de hachage de mot de passe à votre environnement de test Microsoft 365, ce qui donne lieu à cette configuration :
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
La configuration de cet environnement de test implique trois phases :
- [Phase 1 : création de l’environnement de test de l’entreprise simulée pour Microsoft 365](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Phase 2 : création et enregistrement du domaine testlab](#phase-2-create-and-register-the-testlab-domain)
- [Phase 3 : installation d’Azure AD Connect sur APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Phase 1 : création de l’environnement de test de l’entreprise simulée pour Microsoft 365

Suivez les instructions de la configuration de base de l' [entreprise simulée pour Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). La configuration obtenue se présente comme suit :
  
![Configuration de base d’une entreprise simulée](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 dans un réseau virtuel Azure. DC1 est un contrôleur de domaine pour le testlab. <*votre nom de domaine public*> domaine AD DS.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Phase 2 : création et enregistrement du domaine testlab

Dans cette phase, ajoutez un domaine DNS public, puis ajoutez-le à votre abonnement.

Tout d’abord, collaborez avec votre fournisseur d’inscription DNS public pour créer un nouveau nom de domaine DNS public basé sur votre nom de domaine actuel, puis ajoutez-le à votre abonnement. Nous vous recommandons d’utiliser le nom **testlab. <*votre domaine* > public**. Par exemple, si votre nom de domaine public est ** <span>contoso</span>. com**, ajoutez le nom de domaine public : ** <span>testlab</span>. contoso.com**.
  
Ensuite, ajoutez **testlab. <votre domaine de *domaine* > public** à votre version d’évaluation de Microsoft 365 ou à votre abonnement payant en passant par le processus d’inscription de domaine. Cela consiste à ajouter des enregistrements DNS supplémentaires à **testlab. <*votre* > domaine de domaine public** . Pour plus d’informations, consultez [la rubrique ajouter un domaine à Microsoft 365](../admin/setup/add-domain.md).

La configuration obtenue se présente comme suit :
  
![Enregistrement de votre nom de domaine testlab](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Cette configuration se compose des éléments suivants : 

- Un abonnement à la version d’évaluation ou payant de Microsoft 365 E5 avec le domaine DNS testlab. <*votre nom de domaine public*> inscrit.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.

Notez la façon dont le testlab. <*votre nom de domaine public*> est maintenant :

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

3. Dans la barre des tâches, sélectionnez **Internet Explorer** et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect) .
    
4. Sur la page Microsoft Azure Active Directory Connect, sélectionnez **Télécharger**, puis **exécuter**.
    
5. Sur la page **Bienvenue dans Azure ad Connect** , sélectionnez **J’accepte**, puis cliquez sur **Continuer**.
    
6. Sur la page **paramètres rapides** , sélectionnez **utiliser les paramètres rapides**.
    
7. Sur la page **connexion à Azure ad** , entrez le nom de votre compte d’administrateur général dans **nom d’utilisateur,** entrez son mot de passe dans **mot de passe**, puis cliquez sur **suivant**.
    
8. Sur la page **connexion à AD DS** , entrez **testlab \\ utilisateur1** dans **nom d’utilisateur,** entrez son mot de passe dans **mot de passe**, puis cliquez sur **suivant**.
    
9. Sur la page **prêt à configurer** , sélectionnez **installer**.
    
10. Sur la page **Configuration terminée** , sélectionnez **quitter**.
    
11. Dans Internet Explorer, accédez au Centre d’administration Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. Dans le volet de navigation de gauche, sélectionnez **utilisateurs > utilisateurs actifs**.
    
    Notez le compte nommé **Utilisateur 1**. Ce compte provient du domaine TESTLAB AD DS et prouve que la synchronisation d’annuaires a fonctionné.
    
13. Sélectionnez le compte **utilisateur1** , puis sélectionnez **licences et applications**.
    
14. Dans **licences de produit**, sélectionnez votre emplacement (si nécessaire), désactivez la licence **Office 365 E5** , puis activez la licence **Microsoft 365 E5** . 

15. Sélectionnez **Enregistrer** en bas de la page, puis cliquez sur **Fermer**.
    
Ensuite, testez la capacité à se connecter à votre abonnement avec le User1@testlab. <nom d’utilisateur de ** *votre nom* > de domaine** du compte utilisateur1 :

1. Dans APP1, déconnectez-vous, puis reconnectez-vous avec un compte différent.

2. Lorsque vous êtes invité à entrer un nom d’utilisateur et un mot de passe, spécifiez **User1@testlab. <*votre nom* > de domaine** et le mot de passe utilisateur1. Vous devez correctement vous connecter en tant qu’ Utilisateur1.
 
Veuillez noter que même si l’utilisateur User1 dispose des autorisations d’administrateur pour le domaine TESTLAB AD DS, il n’est pas un administrateur général. Par conséquent, vous ne verrez pas l’icône**Administrateur**comme une option. 

La configuration obtenue se présente comme suit :

![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Cette configuration se compose des éléments suivants :  
  
- Microsoft 365 E5 ou Office 365 E5 abonnements d’évaluation ou payants avec le domaine DNS TESTLAB. <*votre nom de domaine*> inscrit.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine TESTLAB AD DS avec le client Azure AD de votre abonnement Microsoft 365.
- Le compte Utilisateur1 dans le domaine TESTLAB  AD DS a été synchronisé avec le client Azure AD.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
