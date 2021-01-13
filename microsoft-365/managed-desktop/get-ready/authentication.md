---
title: Préparer l’accès aux ressources locales pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer qu’azure AD peut communiquer avec AD local pour fournir l’authentification
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: c1732dc17188427f9a181d1c47abe71bb8f39584
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49841410"
---
#  <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Préparer l’accès aux ressources locales pour le Bureau géré Microsoft

Dans bureau géré Microsoft, les appareils sont automatiquement joints à Azure Active Directory (Azure AD). Pour cette raison, si vous utilisez un active directory local, vous devez vérifier certains éléments pour vous assurer que les appareils joints à Azure AD peuvent communiquer avec votre active Directory local. 

> [!NOTE]  
> *Hybride* Azure AD join is not supported by Microsoft Managed Desktop.

Azure Active Directory permet à vos utilisateurs de tirer parti de l' mono-Sign-On (SSO), ce qui signifie qu’ils n’ont généralement pas à fournir d’informations d’identification chaque fois qu’ils utilisent des ressources.

Pour plus d’informations sur l’adhésion à Azure Active Directory, reportez-vous à La façon de : Planifier votre implémentation de jointage [Azure AD.](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan) Pour obtenir des informations d’arrière-plan sur l'Sign-On unique (SSO) sur les appareils joints à Azure AD, voir comment fonctionne l' sso aux ressources sur site sur les appareils joints à [Azure AD.](https://docs.microsoft.com/azure/active-directory/devices/azuread-join-sso#how-it-works)


Cet article explique les éléments que vous devez vérifier afin de vous assurer que les applications et autres ressources qui dépendent de la connectivité Active Directory locale fonctionneront sans problème avec bureau géré Microsoft.


## <a name="single-sign-on-for-on-premises-resources"></a>Une Sign-On pour les ressources sur site

LSign-On (SSO) à l’aide de l’UPN et du mot de passe est activé par défaut sur les appareils de bureau gérés Microsoft. Toutefois, vos utilisateurs peuvent également utiliser Windows Hello Entreprise, ce qui nécessite des étapes de configuration supplémentaires. 

### <a name="single-sign-on-by-using-upn-and-password"></a>Un seul Sign-On à l’aide de l’UPN et du mot de passe

Dans la plupart des organisations, vos utilisateurs peuvent utiliser l’authentification unique pour s’authentifier par upn et mot de passe sur les appareils de bureau gérés Microsoft. Toutefois, pour vous assurer que cette fonction fonctionne, vérifiez les points suivants :

- Confirmez qu’Azure AD Connect est installé et utilise un serveur Active Directory local exécutant Windows Server 2008 R2 ou une ultérieure.
- Confirmez qu’Azure AD Connect exécute une version prise en charge et est définie pour synchroniser ces trois attributs avec Azure AD : 
    - Nom de domaine DNS de l’annuaire Active Directory local (où se trouvent les utilisateurs)
    - NetBIOS de votre annuaire Active Directory local (où se trouvent les utilisateurs)
    - Nom de compte SAM de l’utilisateur


### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Un seul Sign-On à l’aide de Windows Hello Entreprise

Les appareils de bureau géré Microsoft offrent également à vos utilisateurs une expérience rapide et sans mot de passe en employant Windows Hello Entreprise. Pour vous assurer que Windows Hello Entreprise fonctionne sans que vos utilisateurs n’ont à fournir respectivement upn et mot de passe, visitez Configurer les appareils [joints à Azure AD](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) pour les Single-Sign Sur l’utilisation de Windows Hello Entreprise pour vérifier les conditions requises, puis suivez les étapes fournies ici.


## <a name="apps-and-resources-that-use-authentication"></a>Applications et ressources qui utilisent l’authentification

Reportez-vous à Comprendre les considérations concernant les applications et les ressources dans l’ensemble de contenu Azure pour obtenir des [instructions complètes](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) sur la configuration des applications pour qu’ils fonctionnent avec Azure Active Directory. En Résumé :


- Si vous utilisez des applications basées sur le **cloud,** telles que celles ajoutées à la galerie d’applications Azure AD, la plupart d’entre elles ne nécessitent aucune préparation supplémentaire pour fonctionner avec le Bureau géré Microsoft. Toutefois, toutes les applications Win32 qui n’utilisent pas le Gestionnaire de comptes Web (WAM) peuvent toujours inviter les utilisateurs à s’authentifier.

- Pour les applications **hébergées** en local, n’oubliez pas d’ajouter ces applications à la liste des sites de confiance dans vos navigateurs. Cette étape permet à l’authentification Windows de fonctionner en toute transparence, sans que les utilisateurs ne sont invités à obtenir d’informations d’identification. Pour ajouter des applications, reportez-vous [aux sites](https://docs.microsoft.com/microsoft-365/managed-desktop/working-with-managed-desktop/config-setting-ref#trusted-sites) de confiance dans la référence [des paramètres configurables.](https://docs.microsoft.com/microsoft-365/managed-desktop/working-with-managed-desktop/config-setting-ref)

- Si vous utilisez les services fédérés Active Directory, vérifiez que l' utilisateur unique est activé à l’aide des étapes de la procédure de vérification et de gestion de l' sign-on unique avec [AD FS](https://docs.microsoft.com/previous-versions/azure/azure-services/jj151809(v=azure.100)). 

- Pour les applications qui sont sur site et utilisent des **protocoles** plus anciens, aucune configuration supplémentaire n’est requise, tant que les appareils ont accès à un contrôleur de domaine local pour s’authentifier. Toutefois, pour fournir un accès sécurisé à ces applications, vous devez déployer le proxy d’application Azure AD. Pour plus d’informations, voir Accès à distance aux applications sur site via le [proxy d’application d’Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)

- Les applications qui **s’exécutent** en local et reposent sur l’authentification de l’ordinateur ne sont pas pris en charge. Vous devez donc envisager de les remplacer par des versions plus récentes.

### <a name="network-shares-that-use-authentication"></a>Partages réseau qui utilisent l’authentification

Aucune configuration supplémentaire n’est requise pour que les utilisateurs accèdent aux partages réseau, tant que les appareils ont accès à un contrôleur de domaine local à l’aide d’un chemin UNC.

### <a name="printers"></a>Imprimantes

Les appareils Bureau géré Microsoft ne peuvent pas se connecter aux imprimantes publiées sur votre environnement Active Directory local, sauf si vous avez configuré l’impression [cloud hybride.](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy)

Bien que les imprimantes ne peuvent pas être découvertes automatiquement dans un environnement cloud uniquement, vos utilisateurs peuvent utiliser des imprimantes locales à l’aide du chemin d’accès de l’imprimante ou de la file d’attente de l’imprimante, tant que les appareils ont accès à un contrôleur de domaine local.

<!--add fuller material on printers when available-->
