---
title: Configurer la synchronisation d’annuaires pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Découvrez comment configurer la synchronisation d’annuaires entre Microsoft 365 et votre annuaire Active Directory local.
ms.openlocfilehash: 308774dcdbaffc1096ab6ad144484e6920accdfa
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48327092"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Configurer la synchronisation d’annuaires pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise un client Azure Active Directory (Azure AD) pour stocker et gérer les identités pour l’authentification et les autorisations pour accéder aux ressources basées sur le cloud. 

Si vous avez un domaine ou une forêt AD DS (Active Directory Domain Services) local, vous pouvez synchroniser vos comptes d’utilisateur, groupes et contacts AD DS avec le client Azure AD de votre abonnement Microsoft 365. Il s’agit de l’identité hybride pour Microsoft 365. Voici ses composants.

![Composants de la synchronisation d’annuaires pour Microsoft 365](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Connect s’exécute sur un serveur local et synchronise vos AD DS avec le client Azure AD. En plus de la synchronisation d’annuaires, vous pouvez également spécifier les options d’authentification ci-après :

- Synchronisation de hachage de mot de passe (PHS)

  Azure AD effectue l’authentification proprement dite.

- Authentification directe (PTA)

  Azure AD dispose d’AD DS qui effectue l’authentification.

- Authentification fédérée

  Azure AD fait référence à l’ordinateur client qui demande l’authentification à un autre fournisseur d’identité.

Pour plus [d’informations, voir Identités](plan-for-directory-synchronization.md) hybrides.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Examiner les conditions préalables pour Azure AD Connect

Vous obtenez un abonnement Azure AD gratuit avec votre abonnement Microsoft 365. Lorsque vous configurerez la synchronisation d’annuaires, vous installez Azure AD Connect sur l’un de vos serveurs locaux.
  
Pour Microsoft 365, vous devez :
  
- Vérifiez votre domaine local. L’Assistant Azure AD Connect vous guide tout au long de cette situation.
- Obtenez les noms d’utilisateur et les mots de passe des comptes d’administrateur de votre client Microsoft 365 et des AD DS.

Pour votre serveur local sur lequel vous installez Azure AD Connect, vous devez :
  
|**Système d’exploitation de serveur**|**Autres logiciels**|
|:-----|:-----|
|Windows Server 2012 R2 et ultérieur | - PowerShell est installé par défaut, aucune action n’est requise.  <br> - Net 4.5.1 et les mises à jour ultérieures sont proposées via Windows Update. Assurez-vous que vous avez installé les dernières mises à jour de Windows Server dans le Panneau de contrôle. |
|Windows Server 2008 R2 avec Service Pack 1 (SP1)** ou Windows Server 2012 | - La dernière version de PowerShell est disponible dans Windows Management Framework 4.0. Recherchez-le dans [le Centre de téléchargement Microsoft.](https://go.microsoft.com/fwlink/p/?LinkId=717996)  <br> - .Net 4.5.1 et les version ultérieures sont disponibles dans le Centre de [téléchargement Microsoft.](https://go.microsoft.com/fwlink/p/?LinkId=717996) |
|Windows Server 2008 | - La dernière version prise en charge de PowerShell est disponible dans Windows Management Framework 3.0, disponible dans le Centre [de téléchargement Microsoft.](https://go.microsoft.com/fwlink/p/?LinkId=717996)  <br> - .Net 4.5.1 et les version ultérieures sont disponibles dans le Centre de [téléchargement Microsoft.](https://go.microsoft.com/fwlink/p/?LinkId=717996) |

Consultez les conditions préalables pour [Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) pour plus d’informations sur les configurations matérielle, logicielle, de compte et d’autorisation requises, les certificats SSL requis et les limites d’objets pour Azure AD Connect.
  
Vous pouvez également consulter l’historique des versions d’Azure AD [Connect](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) pour voir ce qui est inclus et corrigé dans chaque version.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installer Azure AD Connect et configurer la synchronisation d’annuaires

Avant de commencer, assurez-vous que vous avez :

- Nom d’utilisateur et mot de passe d’un administrateur global Microsoft 365
- Nom d’utilisateur et mot de passe d’un administrateur de domaine AD DS
- Quelle méthode d’authentification (PHS, PTA, fédéré)
- Si vous souhaitez utiliser [l' sign-on](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso) unique transparente Azure AD

Procédez comme suit :

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) ( et choisissez Utilisateurs https://admin.microsoft.com)  \> **actifs** sur le navigation de gauche.
2. Dans la page **Utilisateurs** actifs, **sélectionnez Plus** (trois points) \> **Synchronisation d’annuaires.**
  
3. Dans la page **de préparation d’Azure Active Directory,** sélectionnez Le centre de téléchargement pour obtenir le lien de l’outil **Azure AD Connect** pour commencer. 
4. Suivez les étapes de [la feuille de route d’installation Azure AD Connect et Azure AD Connect Health.](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap)

## <a name="3-finish-setting-up-domains"></a>3. Terminer la configuration des domaines

Suivez les étapes de la procédure de création d’enregistrements [DNS pour Microsoft 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) lorsque vous gérez vos enregistrements DNS pour terminer la configuration de vos domaines.

## <a name="next-step"></a>Étape suivante

[Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
