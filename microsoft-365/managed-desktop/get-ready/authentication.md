---
title: Préparer l’accès aux ressources locales pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer qu’un Azure AD peut communiquer avec AD local pour fournir l’authentification
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 3db3d469f7b417035e6ae11507c54c6bad871a89
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62520390"
---
# <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Préparer l’accès aux ressources locales pour le Bureau géré Microsoft

Dans Microsoft Manged Desktop, les appareils sont automatiquement joints à Azure Active Directory (Azure AD). Pour cette raison, si vous utilisez un active directory local, vous devez vous assurer que les appareils joints à Azure AD peuvent communiquer avec votre active Directory local.

> [!NOTE]  
> *La joint* Azure AD hybride n’est pas prise en charge par Microsoft Manged Desktop.

Azure Active Directory permet à vos utilisateurs de tirer parti de l’mono-Sign-On (SSO). L’sign-on unique signifie qu’il n’a généralement pas besoin de fournir d’informations d’identification chaque fois qu’il utilise des ressources.

Pour plus d’informations sur la Azure Active Directory, reportez-vous à La façon de [: Planifier votre Azure AD l’implémentation de la jointation](/azure/active-directory/devices/azureadjoin-plan). Pour obtenir des informations d’arrière-plan sur l'Sign-On unique (SSO) sur les appareils joints à Azure AD, voir comment fonctionne l’oD unique pour les ressources sur site [sur Azure AD joints à des appareils](/azure/active-directory/devices/azuread-join-sso#how-it-works).

Cet article explique les éléments que vous devez vérifier pour vous assurer que les applications et les autres ressources qui dépendent de la connectivité Active Directory locale fonctionneront sans problème avec les Microsoft Manged Desktop.

## <a name="single-sign-on-for-on-premises-resources"></a>Une Sign-On pour les ressources sur site

L'Sign-On unique (SSO) à l’aide de l’UPN et du mot de passe est activée par défaut sur Microsoft Manged Desktop périphériques. Toutefois, vos utilisateurs peuvent également utiliser Windows Hello entreprise, ce qui nécessite des étapes de configuration supplémentaires.

### <a name="single-sign-on-by-using-upn-and-password"></a>Un seul Sign-On à l’aide de l’UPN et du mot de passe

Dans la plupart des organisations, vos utilisateurs peuvent utiliser l’authentification unique pour s’authentifier par UPN et mot de passe sur Microsoft Manged Desktop périphériques. Pour vous assurer que cette fonction fonctionne, vérifiez les points suivants :

- Confirmez que Azure AD Connecter est bien installé. Il doit utiliser un serveur Active Directory local exécutant Windows Server 2008 R2 ou ultérieur.
- Confirmez que Azure AD Connecter exécute une version prise en charge. Elle doit être définie pour synchroniser ces trois attributs avec Azure AD :
    - Nom de domaine DNS de l’annuaire Active Directory local (où se trouvent les utilisateurs).
    - NetBIOS de votre active directory local (où se trouvent les utilisateurs).
    - Nom de compte SAM de l’utilisateur.

### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Un seul Sign-On à l’aide de Windows Hello entreprise

Microsoft Manged Desktop’appareils offrent également à vos utilisateurs une expérience sans mot de passe rapide en Windows Hello entreprise. Pour vous assurer que Windows Hello Entreprise fonctionne sans que vos utilisateurs n’ont à fournir respectivement upn et mot de passe, visitez Configurer les appareils [joints à Azure AD pour les Single-Sign](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) sur site à l’aide de Windows Hello for Business pour vérifier les conditions requises, puis suivez les étapes fournies ici.

## <a name="apps-and-resources-that-use-authentication"></a>Applications et ressources qui utilisent l’authentification

Reportez-vous à Comprendre les considérations concernant les applications et les ressources dans l’ensemble de contenu Azure pour obtenir des [instructions complètes](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) sur la configuration des applications à Azure Active Directory. En Résumé :

| Application ou service | Tâche |
| ------ | ------ |
| Applications basées sur le cloud | Si vous utilisez des applications basées sur le **cloud**, telles que celles ajoutées à la galerie d’applications Azure AD, la plupart ne nécessitent aucune préparation supplémentaire pour utiliser Microsoft Manged Desktop. Toutefois, toutes les applications Win32 qui n’utilisent pas le Gestionnaire de comptes Web (WAM) peuvent toujours inciter les utilisateurs à s’authentifier. |
| Applications hébergées en local | Pour les applications hébergées en **local**, n’oubliez pas d’ajouter ces applications à la liste des sites de confiance dans vos navigateurs. Cette étape permet au Windows’authentification de fonctionner en toute transparence, sans que les utilisateurs ne sont invités à obtenir leurs informations d’identification. Pour ajouter des applications, reportez-vous [aux sites](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) de confiance dans la [référence des paramètres configurables](../working-with-managed-desktop/config-setting-ref.md). |
| Services fédérés Active Directory | Si vous utilisez les services fédérés Active Directory, vérifiez que l’utilisateur unique est activé à l’aide des étapes de vérification et de gestion de l’sign-on unique avec [AD FS](/previous-versions/azure/azure-services/jj151809(v=azure.100)). |
| Applications sur site utilisant des protocoles plus anciens | Pour les applications qui sont sur site et utilisent des **protocoles** plus anciens, aucune configuration supplémentaire n’est requise, tant que les appareils ont accès à un contrôleur de domaine local pour s’authentifier. Toutefois, pour fournir un accès sécurisé à ces applications, vous devez déployer Azure AD proxy d’application. Pour plus d’informations, voir [Accès à distance aux applications sur site via Azure Active Directory proxy d’application.](/azure/active-directory/manage-apps/application-proxy) |
| Applications sur site avec authentification sur ordinateur | Les applications qui **s’exécutent en local** et reposent sur l’authentification d’ordinateur ne sont pas pris en charge. Vous devez donc envisager de les remplacer par des versions plus récentes. |

### <a name="network-shares-that-use-authentication"></a>Partages réseau qui utilisent l’authentification

Aucune configuration supplémentaire n’est requise pour que les utilisateurs accèdent aux partages réseau, tant que les appareils ont accès à un contrôleur de domaine local à l’aide d’un chemin UNC.

### <a name="printers"></a>Imprimantes

Microsoft Manged Desktop ne peuvent pas se connecter à des imprimantes publiées sur votre annuaire Active Directory local, sauf si vous avez configuré l’impression [cloud hybride](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).

Bien que les imprimantes ne peuvent pas être découvertes automatiquement dans un environnement cloud uniquement, vos utilisateurs peuvent utiliser des imprimantes locales à l’aide du chemin d’accès de l’imprimante ou de la file d’attente de l’imprimante, tant que les appareils ont accès à un contrôleur de domaine local.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
1. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. Préparer l’accès des utilisateurs aux données (cet article).
1. [Préparer les applications](apps.md).
1. [Préparer les lecteurs mappés](mapped-drives.md).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
