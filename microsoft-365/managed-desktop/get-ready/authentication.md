---
title: Préparer l’accès aux ressources locales pour le Bureau géré Microsoft
description: Étapes importantes pour vous assurer qu’un Azure AD peut communiquer avec AD sur site pour fournir l’authentification
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 7181e81a2db94ce26fb8601f8b9156c65084c439
ms.sourcegitcommit: abf63669daf12993ad3353e4b578f41c8910b20f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "47289578"
---
#  <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Préparer l’accès aux ressources locales pour le Bureau géré Microsoft

Dans le bureau géré Microsoft, les appareils sont automatiquement joints à Azure Active Directory (Azure AD). Cela signifie que si vous utilisez un annuaire Active Directory local, vous devrez vérifier certaines choses pour vous assurer que les appareils joints à Azure AD peuvent communiquer avec votre Active Directory local. 

> [!NOTE]  
> *Hybride* La participation à Azure AD n’est pas prise en charge par le bureau géré Microsoft.

Azure Active Directory permet à vos utilisateurs de tirer parti de l’authentification unique (SSO), ce qui signifie qu’ils ne devront généralement pas fournir d’informations d’identification à chaque fois qu’ils utilisent des ressources.

Pour plus d’informations sur la jonction d’Azure Active Directory, consultez [la rubrique How to : plan Your Azure ad Join Implementation](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan). Pour obtenir des informations générales sur l’authentification unique (SSO) sur les appareils joints à Azure AD, consultez la rubrique relative [à l’authentification unique des ressources locales sur des appareils Azure ad joints](https://docs.microsoft.com/azure/active-directory/devices/azuread-join-sso#how-it-works).


Cette rubrique décrit les éléments que vous devez vérifier afin de vous assurer que les applications et autres ressources qui dépendent de la connectivité Active Directory locale fonctionnent correctement avec Microsoft Managed Desktop.


## <a name="single-sign-on-for-on-premises-resources"></a>Authentification unique pour les ressources locales

L’authentification unique (SSO) à l’aide de l’UPN et du mot de passe est activée par défaut sur les appareils de bureau géré Microsoft. Toutefois, vos utilisateurs peuvent également utiliser Windows Hello entreprise, ce qui nécessite des étapes de configuration supplémentaires. 

### <a name="single-sign-on-by-using-upn-and-password"></a>Authentification unique à l’aide de l’UPN et du mot de passe

Dans la plupart des organisations, vos utilisateurs peuvent utiliser l’authentification unique pour s’authentifier par nom d’utilisateur et mot de passe sur les appareils de bureau gérés Microsoft. Toutefois, pour vous assurer que cela fonctionne, vous devez vérifier les points suivants :

- Vérifiez qu’Azure AD Connect est configuré et qu’il utilise un serveur Active Directory local exécutant Windows Server 2008 R2 ou une version ultérieure.
- Vérifiez qu’Azure AD Connect exécute une version prise en charge et qu’il est configuré pour synchroniser ces trois attributs avec Azure AD : 
    - Nom de domaine DNS de l’annuaire Active Directory local (où se trouvent les utilisateurs)
    - NetBIOS de votre Active Directory local (où se trouvent les utilisateurs)
    - Nom de compte SAM de l’utilisateur


### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Authentification unique à l’aide de Windows Hello entreprise

Les appareils de bureau gérés par Microsoft offrent également à vos utilisateurs une expérience rapide et avec mot de passe en utilisant Windows Hello entreprise. Pour vous assurer que Windows Hello entreprise fonctionnera sans que vos utilisateurs aient à fournir un nom d’utilisateur principal et un mot de passe respectifs, rendez-vous [sur configurer des appareils joints Azure AD pour l’authentification unique locale à l’aide de Windows Hello entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) pour vérifier la configuration requise, puis suivez les étapes fournies.


## <a name="apps-and-resources-that-use-authentication"></a>Applications et ressources qui utilisent l’authentification

Reportez-vous à la rubrique [comprendre les considérations relatives aux applications et aux ressources](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) dans l’ensemble de contenu Azure pour obtenir des instructions complètes sur la configuration des applications pour qu’elles fonctionnent avec Azure Active Directory. En Résumé :


- Si vous utilisez des **applications en nuage**, telles que celles ajoutées à la Galerie d’applications Azure ad, la plupart n’ont pas besoin d’une préparation supplémentaire pour fonctionner avec Microsoft Managed Desktop. Toutefois, les applications Win32 qui n’utilisent pas le gestionnaire de comptes Web (WAM) peuvent toujours inviter les utilisateurs à s’authentifier.

- Pour les applications **hébergées en local**, veillez à ajouter ces applications à la liste des sites de confiance dans vos navigateurs. Cela permet à l’authentification Windows de fonctionner de manière transparente, sans que les utilisateurs ne soient invités à entrer des informations d’identification. Pour ce faire, reportez-vous à la rubrique [sites de confiance](https://docs.microsoft.com/microsoft-365/managed-desktop/working-with-managed-desktop/config-setting-ref#trusted-sites) dans la [référence des paramètres configurables](https://docs.microsoft.com/microsoft-365/managed-desktop/working-with-managed-desktop/config-setting-ref).

- Si vous utilisez les services fédérés Active Directory, vérifiez que l’authentification unique est activée à l’aide des étapes décrites dans [Verify and Manage Single Sign-On with AD FS](https://docs.microsoft.com/previous-versions/azure/azure-services/jj151809(v=azure.100)). 

- Pour les applications **locales et utilisant des protocoles plus anciens**, aucune configuration supplémentaire n’est requise, à condition que les périphériques aient accès à un contrôleur de domaine local pour s’authentifier. Toutefois, pour fournir un accès sécurisé à ces applications, vous devez déployer le proxy d’application Azure AD. Pour plus d’informations, reportez-vous à [accès distant aux applications locales via le proxy d’application Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- Les applications qui s’exécutent **sur site et s’appuyant sur l’authentification de l’ordinateur** ne sont pas prises en charge ; vous devez donc envisager de les remplacer par des versions plus récentes.

### <a name="network-shares-that-use-authentication"></a>Partages réseau qui utilisent l’authentification

Aucune configuration supplémentaire n’est requise pour que les utilisateurs accèdent aux partages réseau, tant que les appareils ont accès à un contrôleur de domaine local à l’aide d’un chemin d’accès UNC.

### <a name="printers"></a>Imprimantes

Les appareils de bureau gérés Microsoft ne peuvent pas se connecter aux imprimantes qui sont publiées sur votre environnement Active Directory local, sauf si vous avez configuré l’impression dans le [Cloud hybride](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).

Bien que les imprimantes ne puissent pas être automatiquement découvertes dans un environnement Cloud uniquement, vos utilisateurs peuvent utiliser des imprimantes locales à l’aide du chemin d’accès de l’imprimante ou de la file d’attente de l’imprimante, à condition que les périphériques aient accès à un contrôleur de domaine local.

<!--add fuller material on printers when available-->
