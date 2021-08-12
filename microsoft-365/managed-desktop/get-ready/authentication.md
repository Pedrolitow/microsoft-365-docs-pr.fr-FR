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
audience: Admin
ms.openlocfilehash: 22d49a85ae4d89e3d596a00a0d47468ed213788c1b46d850914d2eaecef56ec1
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53819234"
---
#  <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Préparer l’accès aux ressources locales pour le Bureau géré Microsoft

Dans Microsoft Manged Desktop, les appareils sont automatiquement joints à Azure Active Directory (Azure AD). Pour cette raison, si vous utilisez un active directory local, vous devez vérifier certains éléments pour vous assurer que les appareils joints à Azure AD peuvent communiquer avec votre active Directory local. 

> [!NOTE]  
> *Hybride* Azure AD join is not supported by Microsoft Manged Desktop.

Azure Active Directory permet à vos utilisateurs de tirer parti de l' mono-Sign-On (SSO), ce qui signifie qu’ils n’ont généralement pas à fournir d’informations d’identification chaque fois qu’ils utilisent des ressources.

Pour plus d’informations sur la Azure Active Directory, voir Comment : Planifier l’implémentation de votre jointage [Azure AD.](/azure/active-directory/devices/azureadjoin-plan) Pour obtenir des informations d’arrière-plan sur l' mono-Sign-On (SSO) sur les appareils joints à Azure AD, voir comment fonctionne l' sso aux ressources sur site sur les appareils joints à [Azure AD.](/azure/active-directory/devices/azuread-join-sso#how-it-works)


Cet article explique les éléments que vous devez vérifier afin de vous assurer que les applications et autres ressources qui dépendent de la connectivité Active Directory locale fonctionneront sans problème avec les Microsoft Manged Desktop.


## <a name="single-sign-on-for-on-premises-resources"></a>Une Sign-On pour les ressources sur site

L'Sign-On unique (SSO) à l’aide de l’UPN et du mot de passe est activée par défaut sur Microsoft Manged Desktop périphériques. Toutefois, vos utilisateurs peuvent également utiliser Windows Hello entreprise, ce qui nécessite des étapes de configuration supplémentaires. 

### <a name="single-sign-on-by-using-upn-and-password"></a>Un seul Sign-On à l’aide de l’UPN et du mot de passe

Dans la plupart des organisations, vos utilisateurs pourront utiliser l’authentification unique pour s’authentifier par upN et mot de passe sur Microsoft Manged Desktop périphériques. Toutefois, pour vous assurer que cette fonction fonctionne, vérifiez les points suivants :

- Confirmez qu’Azure AD Connecter est installé et utilise un serveur Active Directory local exécutant Windows Server 2008 R2 ou ultérieur.
- Confirmez qu’Azure AD Connecter exécute une version prise en charge et est définie pour synchroniser ces trois attributs avec Azure AD : 
    - Nom de domaine DNS de l’annuaire Active Directory local (où se trouvent les utilisateurs)
    - NetBIOS de votre annuaire Active Directory local (où se trouvent les utilisateurs)
    - Nom de compte SAM de l’utilisateur


### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Un seul Sign-On à l’aide de Windows Hello entreprise

Microsoft Manged Desktop offrent également à vos utilisateurs une expérience rapide et sans mot de passe en Windows Hello entreprise. Pour vous assurer que Windows Hello Entreprise fonctionne sans que vos utilisateurs n’ont à fournir respectivement upn et mot de passe, visitez Configurer les appareils [joints à Azure AD pour l'Single-Sign](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) local à l’aide de Windows Hello for Business pour vérifier les conditions requises, puis suivez les étapes fournies ici.


## <a name="apps-and-resources-that-use-authentication"></a>Applications et ressources qui utilisent l’authentification

Reportez-vous à Comprendre les considérations concernant les applications et les ressources dans l’ensemble de contenu Azure pour obtenir des [instructions complètes](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) sur la configuration des applications à Azure Active Directory. En Résumé :


- Si vous utilisez des applications basées sur le **cloud,** telles que celles ajoutées à la galerie d’applications Azure AD, la plupart d’entre elles ne nécessitent aucune préparation supplémentaire pour fonctionner avec Microsoft Manged Desktop. Toutefois, toutes les applications Win32 qui n’utilisent pas le Gestionnaire de comptes Web (WAM) peuvent toujours inviter les utilisateurs à s’authentifier.

- Pour les applications **hébergées** en local, n’oubliez pas d’ajouter ces applications à la liste des sites de confiance dans vos navigateurs. Cette étape permet aux utilisateurs Windows l’authentification de fonctionner en toute transparence, sans que les utilisateurs ne sont invités à leur donner d’informations d’identification. Pour ajouter des applications, reportez-vous [aux sites](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) de confiance dans la référence [des paramètres configurables.](../working-with-managed-desktop/config-setting-ref.md)

- Si vous utilisez les services fédérés Active Directory, vérifiez que l' utilisateur unique est activé à l’aide des étapes de la procédure de vérification et de gestion de l' sign-on unique avec [AD FS](/previous-versions/azure/azure-services/jj151809(v=azure.100)). 

- Pour les applications qui sont sur site et utilisent des **protocoles** plus anciens, aucune configuration supplémentaire n’est requise, tant que les appareils ont accès à un contrôleur de domaine local pour s’authentifier. Toutefois, pour fournir un accès sécurisé à ces applications, vous devez déployer le proxy d’application Azure AD. Pour plus d’informations, voir Accès à distance aux applications sur site [via Azure Active Directory proxy d’application.](/azure/active-directory/manage-apps/application-proxy)

- Les applications qui **s’exécutent** en local et reposent sur l’authentification de l’ordinateur ne sont pas pris en charge. Vous devez donc envisager de les remplacer par des versions plus récentes.

### <a name="network-shares-that-use-authentication"></a>Partages réseau qui utilisent l’authentification

Aucune configuration supplémentaire n’est requise pour que les utilisateurs accèdent aux partages réseau, tant que les appareils ont accès à un contrôleur de domaine local à l’aide d’un chemin UNC.

### <a name="printers"></a>Imprimantes

Microsoft Manged Desktop ne peuvent pas se connecter à des imprimantes publiées sur votre annuaire Active Directory local, sauf si vous avez configuré l’impression [cloud hybride.](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy)

Bien que les imprimantes ne peuvent pas être découvertes automatiquement dans un environnement cloud uniquement, vos utilisateurs peuvent utiliser des imprimantes locales à l’aide du chemin d’accès de l’imprimante ou de la file d’attente de l’imprimante, tant que les appareils ont accès à un contrôleur de domaine local.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready"></a>Étapes pour vous préparer

1. Examiner [les conditions préalables pour Microsoft Manged Desktop](prerequisites.md).
2. Utiliser [les outils d’évaluation de la préparation.](readiness-assessment-tool.md)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources sur site pour Microsoft Manged Desktop](authentication.md) (Cet article)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs mappés pour le Bureau géré Microsoft](mapped-drives.md)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
