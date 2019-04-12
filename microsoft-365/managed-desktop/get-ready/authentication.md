---
title: Préparation de l'accès aux ressources locales pour le bureau géré Microsoft
description: Étapes importantes pour vous assurer qu'un Azure AD peut communiquer avec AD sur site pour fournir l'authentification
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 0f9cbe6712b8d16f435cfdf5fd84875656fa9c2e
ms.sourcegitcommit: ef589025820ddf6edb5f454826b1c12c9bcb8e49
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2019
ms.locfileid: "31824464"
---
#  <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Préparation de l'accès aux ressources locales pour le bureau géré Microsoft

Dans Microsoft maNaged Desktop, les appareils sont automatiquement joints à Azure Active Directory. Cela signifie que si vous utilisez un annuaire Active Directory local, vous devrez vérifier certaines choses pour vous assurer que les appareils joints à Azure AD peuvent communiquer avec votre Active Directory local. 

> [!NOTE]  
> *Hybride* La participation à Azure AD n'est pas prise en charge par le bureau géré Microsoft.

Azure Active Directory permet à vos utilisateurs de tirer parti de l'authentification unique (SSO), ce qui signifie qu'ils ne devront généralement pas fournir d'informations d'identification à chaque fois qu'ils veulent effectuer une action. Si vous ne connaissez pas Azure Active Directory, reportez-vous à [la rubrique How to: Planning Your Azure ad Join Implementation](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)--Toutefois, lorsque vous faites référence à Azure Active Directory, gardez à l'esprit que la fonction Join Azure ad *hybride* n'est pas prise en charge par Microsoft. Bureau géré.


Cette rubrique décrit les éléments que vous devez vérifier afin de vous assurer que les applications et autres ressources qui dépendent de la connectivité Active Directory locale fonctionnent correctement avec Microsoft maNaged Desktop.


> [!IMPORTANT]  
> Pour permettre aux utilisateurs d'enregistrer des appareils dans Azure Active Directory et de s'inscrire dans Intune (requis pour le bureau géré Microsoft), suivez la procédure décrite dans la section [configurer les paramètres](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#configure-your-device-settings) de l'appareil avant de poursuivre cette rubrique.


## <a name="single-sign-on-for-on-premises-resources"></a>Authentification unique pour les ressources locales

L'authentification unique (SSO) pour vos appareils à l'aide de l'UPN ou des mots de passe (méthode par défaut) doit déjà fonctionner par défaut. Toutefois, vous pouvez également utiliser Windows Hello entreprise, qui nécessite des étapes de configuration supplémentaires. Pour plus d'informations sur l'authentification unique, consultez la rubrique relative [à l'authentification unique sur les ressources locales sur les appareils Azure ad joints](https://docs.microsoft.com/azure/active-directory/devices/azuread-join-sso#how-it-works).


### <a name="single-sign-on-by-using-upn-and-passwords"></a>Authentification unique à l'aide de l'UPN et des mots de passe

Aucune configuration spéciale n'est requise pour permettre à vos utilisateurs de s'authentifier par nom d'utilisateur et mot de passe: par défaut, Azure. Toutefois, pour vous assurer que cela fonctionne, vous devez vérifier les points suivants:

- Vérifiez que la connexion à Azure Active Directory (AAD) est configurée avec un serveur Active Directory local exécutant Windows Server 2008 R2 ou une version ultérieure.
- AAD Connect exécute une version prise en charge et est configuré pour synchroniser ces trois attributs clés avec Azure AD: 
    - Nom de domaine DNS dans lequel l'utilisateur est présent dans votre annuaire Active Directory local
    - Nom de domaine NetBIOS dans lequel l'utilisateur est présent dans votre annuaire Active Directory local
    - Nom de compte SAM de l'utilisateur


### <a name="sso-by-using-windows-hello-for-business"></a>AUTHENTIFICATION unique à l'aide de Windows Hello entreprise

Vous pouvez également offrir à vos utilisateurs une expérience rapide et avec mot de passe en utilisant Windows Hello entreprise. Pour ce faire, rendez-vous sur [configurer des appareils joints Azure AD pour l'authentification unique locale à l'aide de Windows Hello entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) afin de vérifier la configuration requise, puis suivez les étapes fournies.


## <a name="apps-and-resources-that-use-authentication"></a>Applications et ressources qui utilisent l'authentification

RePortez-vous à la rubrique [comprendre les considérations relatives aux applications et aux ressources](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) dans l'ensemble de contenu Azure pour obtenir des instructions complètes sur la configuration des applications pour qu'elles fonctionnent avec Azure Active Directory. En Résumé:


- Si vous utilisez des **applications en nuage**, telles que celles ajoutées à la Galerie d'applications Azure ad, la plupart n'ont pas besoin d'une préparation supplémentaire pour fonctionner avec Microsoft Managed Desktop. Toutefois, toutes les applications Win32 qui n'utilisent pas le gestionnaire de comptes Web (WAM) {Vérifiez cet acronyme} peuvent toujours inviter les utilisateurs à s'authentifier.

- Pour les applications **hébergées en local**, veillez à ajouter ces applications à la liste des sites de confiance dans vos navigateurs. Cela permet à l'authentification Windows de fonctionner de manière transparente, sans que les utilisateurs ne soient invités à entrer des informations d'identification.

- Si vous utilisez les services fédérés Active Directory, suivez les étapes décrites dans [Verify and Manage Single Sign-On with AD FS](https://docs.microsoft.com/previous-versions/azure/azure-services/jj151809(v=azure.100)). 

- Pour les applications **locales et utilisant des protocoles plus anciens**, aucune configuration supplémentaire n'est requise, à condition que les périphériques aient accès à un contrôleur de domaine local. Toutefois, pour fournir un accès sécurisé à ces applications, vous devez déployer le proxy d'application Azure AD. Pour plus d'informations, reportez-vous à [accès distant aux applications locales via le proxy d'application Azure Active Directory](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- Les applications qui s'exécutent **sur site et s'appuyant sur l'authentification de l'ordinateur** ne sont pas prises en charge; vous devez donc envisager de les remplacer par des versions plus récentes.

## <a name="network-shares-that-use-authentication"></a>Partages réseau qui utilisent l'authentification

Aucune configuration supplémentaire n'est requise pour que les utilisateurs accèdent aux partages réseau, tant que les appareils ont accès à un contrôleur de domaine local à l'aide d'un chemin d'accès UNC.

## <a name="printers"></a>Imprimantes

Bien que les imprimantes ne puissent pas être automatiquement découvertes dans un environnement Cloud uniquement, vos utilisateurs peuvent également utiliser le chemin d'accès UNC des imprimantes pour les ajouter directement.

<!--add fuller material on printers when available-->