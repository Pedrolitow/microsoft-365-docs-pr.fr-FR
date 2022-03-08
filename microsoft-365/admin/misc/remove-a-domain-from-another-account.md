---
title: Supprimer un domaine d’un autre compte
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Découvrez comment joindre un compte nonmana créé par une inscription d’utilisateur libre-service dans Microsoft 365.
ms.openlocfilehash: 0a7cf07a70e241c0b40f28159f31b0c86766bc1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325668"
---
# <a name="perform-an-internal-admin-takeover"></a>Effectuer une prise de contrôle d’administrateur interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes un administrateur et que vous souhaitez prendre le contrôle d’un compte non pris en charge créé par une inscription d’utilisateur libre-service, vous pouvez le faire en faisant une prise de contrôle d’administrateur interne.

> [!NOTE]
> Une inscription en libre-service pour tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD non gestion ou « shadow » et crée un compte nonmanaté. Un compte non gérant est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non, voir [Déterminer le type de client](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Avant de commencer

Parfois, vous ne pouvez pas ajouter un domaine à votre compte d’organisation, car quelqu’un d’autre s’est déjà inscrit à Microsoft 365 à l’aide d’une adresse de messagerie associée à ce nom de domaine. Toutefois, vous pouvez supprimer le domaine de l’autre compte non géré et l’ajouter au compte géré de votre organisation.

Avant de pouvoir supprimer le domaine de l’autre compte et de l’ajouter à votre compte, vous devez joindre le compte nonmanaté et devenir administrateur de ce compte. Ensuite, vous supprimez le domaine du compte non géré, vous vous connectez à votre compte et vous ajoutez le domaine à votre compte géré.

Les étapes décrites dans cet article décrivent uniquement comment rejoindre l’autre compte (étapes 1 et 2) et suivre les étapes de l’Assistant Prise de contrôle de l’administrateur pour devenir l’administrateur sur le compte nonmanaté (étape 3).

Une fois que vous êtes devenu administrateur du compte nonmana, vous pouvez supprimer le domaine du compte nonmanaté et l’ajouter à votre compte. 

## <a name="step-1-verify-your-email-address"></a>Étape 1 : Vérifier votre adresse de messagerie

> [!NOTE]
> Si le libre-service est activé dans votre compte, les utilisateurs peuvent s’abonner à des services gratuits tels que Power BI, eux-mêmes. Ces services sont spécifiquement utilisés dans les cas où un abonnement utilisateur libre-service a créé le compte non pris en compte que vous souhaitez prendre en tant qu’administrateur. À l’étape 1, vous créez un compte d’utilisateur pour le domaine que vous souhaitez supprimer à l’aide de Power BI pour lancer l’Assistant Prise de contrôle de l’administrateur afin de pouvoir devenir l’administrateur du compte de domaine non utilisé.

1. Pour vous inscrire à Power BI, allez sur le [site](https://powerbi.com) >  Power BI et sélectionnez Démarrer l’essai **gratuit gratuit (** dans la zone Partager avec Power BI Pro). 

2. Inscrivez-vous avec un compte d’utilisateur qui utilise le nom de domaine de votre organisation (comme `powerbiadmin@contoso.com`). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Recherchez le **code de vérification dans votre** courrier électronique et entrez-le pour valider votre adresse de messagerie.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Étape 2 : Créer un compte pour l’accès administrateur

1. Lorsque vous entrez le code de vérification, vous êtes amené à une page dans laquelle vous pouvez créer un compte.

2. Remplissez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis sélectionnez **Démarrer**.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir l’administrateur

1. Après avoir terminé l’étape 2, sélectionnez l’icône du Centre d’administration dans le volet de navigation de gauche (vous pouvez également vous rendre dans un navigateur et taper).`https://admin.microsoft.com`

    Vous êtes redirigé vers l’Assistant Prise de contrôle de l’administrateur.

1. **Sélectionnez Suivant** et vérifiez que vous êtes propriétaire du domaine à prendre en compte en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines. 

    L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

1. Dans la **page Vous êtes maintenant l’administrateur** , **sélectionnez Aller au Centre d’administration**.

    Vous avez maintenant les privilèges d’administrateur requis pour supprimer le domaine de l’autre compte. 
## <a name="related-content"></a>Contenu associé

YouTube : [3 étapes pour une](https://www.youtube.com/watch?v=xt5EsrQBZZk) prise de contrôle d’administrateur informatique pour Power BI et Microsoft 365 (vidéo)\
[Prise de contrôle par l’administrateur dans Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (article)\
[Utilisation de l’inscription en libre-service dans votre organisation](self-service-sign-up.md) (article)\
[Understanding the Power BI service administrator role](/power-bi/service-admin-role) (article)
