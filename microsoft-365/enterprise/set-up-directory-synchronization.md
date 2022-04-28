---
title: Configurer la synchronisation d’annuaires pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Découvrez comment configurer la synchronisation d’annuaires entre Microsoft 365 et votre Active Directory local.
ms.openlocfilehash: 49240d056520a83c0828440e21c5cf26943bae8e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092886"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Configurer la synchronisation d’annuaires pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 utilise un locataire Azure Active Directory (Azure AD) pour stocker et gérer des identités pour l’authentification et les autorisations d’accès aux ressources cloud. 

Si vous disposez d’un domaine ou d’une forêt AD DS Active Directory local, vous pouvez synchroniser vos comptes d’utilisateur, groupes et contacts AD DS avec le locataire Azure AD de votre abonnement Microsoft 365. Il s’agit d’une identité hybride pour Microsoft 365. Voici ses composants.

![Composants de synchronisation d’annuaires pour Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Connecter s’exécute sur un serveur local et synchronise votre service AD DS avec le locataire Azure AD. En plus de la synchronisation d’annuaires, vous pouvez également spécifier les options d’authentification suivantes :

- Synchronisation de hachage de mot de passe (PHS)

  Azure AD effectue l’authentification elle-même.

- Authentification directe (PTA)

  Azure AD AD DS effectue l’authentification.

- Authentification fédérée

  Azure AD fait référence à l’ordinateur client qui demande l’authentification à un autre fournisseur d’identité.

Pour plus d’informations, consultez [Les identités hybrides](plan-for-directory-synchronization.md) .
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Examiner les prérequis pour Azure AD Connecter

Vous bénéficiez d’un abonnement Azure AD gratuit avec votre abonnement Microsoft 365. Lorsque vous configurez la synchronisation d’annuaires, vous installez Azure AD Connecter sur l’un de vos serveurs locaux.
  
Pour Microsoft 365 vous devez :
  
- Vérifiez votre domaine local. L’Assistant Azure AD Connecter vous guide tout au long de cette procédure.
- Obtenez les noms d’utilisateur et les mots de passe pour les comptes d’administrateur de votre locataire Microsoft 365 et AD DS.

Pour votre serveur local sur lequel vous installez Azure AD Connecter, vous avez besoin des éléments nécessaires :
  
|**Système d’exploitation du serveur**|**Autres logiciels**|
|:-----|:-----|
|Windows Server 2012 R2 et versions ultérieures | - PowerShell est installé par défaut, aucune action n’est requise.  <br> - Net 4.5.1 et versions ultérieures sont proposés via Windows Update. Vérifiez que vous avez installé les dernières mises à jour de Windows Server dans le Panneau de configuration. |
|Windows Server 2008 R2 avec Service Pack 1 (SP1)** ou Windows Server 2012 | - La dernière version de PowerShell est disponible dans Windows Management Framework 4.0. Recherchez-la dans le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - Les versions .Net 4.5.1 et ultérieures sont disponibles dans le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | - La dernière version prise en charge de PowerShell est disponible dans Windows Management Framework 3.0, disponible sur le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - Les versions .Net 4.5.1 et ultérieures sont disponibles dans le [Centre de téléchargement Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Consultez [les prérequis pour Azure Active Directory Connecter](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) pour plus d’informations sur les exigences en matière de matériel, de logiciels, de compte et d’autorisations, les exigences de certificat SSL et les limites d’objets pour Azure AD Connecter.
  
Vous pouvez également consulter [l’historique](/azure/active-directory/hybrid/reference-connect-version-history) des versions Azure AD Connecter pour voir ce qui est inclus et corrigé dans chaque version.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installer Azure AD Connecter et configurer la synchronisation d’annuaires

Avant de commencer, assurez-vous d’avoir :

- Nom d’utilisateur et mot de passe d’un administrateur général Microsoft 365
- Nom d’utilisateur et mot de passe d’un administrateur de domaine AD DS
- Méthode d’authentification (PHS, PTA, fédérée)
- Indique si vous souhaitez utiliser [Azure AD’authentification unique transparente (SSO)](/azure/active-directory/hybrid/how-to-connect-sso)

Procédez comme suit :

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com)et choisissez **Utilisateurs** \> **actifs utilisateurs** dans le volet de navigation de gauche.
2. Dans la page **Utilisateurs actifs**, choisissez **Synchronisation d’annuaires Plus** (trois points). \> 
  
3. Dans la page **de préparation Azure Active Directory**, sélectionnez l’option **Accéder au centre de téléchargement pour obtenir le lien de l’outil Azure AD Connecter** pour commencer. 
4. Suivez les étapes décrites dans [Azure AD Connecter et la feuille de route d’installation de Azure AD Connecter Health](/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Terminer la configuration des domaines

Suivez les étapes décrites dans [Créer des enregistrements DNS pour Microsoft 365 lorsque vous gérez vos enregistrements DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) pour terminer la configuration de vos domaines.

## <a name="next-step"></a>Étape suivante

[Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)