---
title: Effectuer une prise de contrôle d’administrateur interne
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
description: Découvrez comment vérifier la propriété de votre courrier électronique et de votre domaine pour prendre le contrôle d’un compte non pris en charge créé par une inscription d’utilisateur en libre-service dans Microsoft 365.
ms.openlocfilehash: 06197bb5326cbd19fcd9174554007577e7086dc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320156"
---
# <a name="perform-an-internal-admin-takeover"></a>Effectuer une prise de contrôle d’administrateur interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes un administrateur et que vous souhaitez prendre le contrôle d’un compte non pris en charge créé par une inscription d’utilisateur libre-service, vous pouvez effectuer une prise de contrôle d’administrateur interne en suivant les étapes de cet article.

> [!NOTE]
> Une inscription en libre-service pour tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD non gestion ou « shadow » et crée un compte nonmanaté. Un compte non gérant est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non, voir [Déterminer le type de client](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Avant de commencer

Lorsqu’un utilisateur s’Microsoft 365 services à l’aide d’une adresse de messagerie, un compte est automatiquement créé pour lui. Si un administrateur souhaite gérer les utilisateurs sur le compte ou acheter des services Microsoft 365 supplémentaires, il doit devenir administrateur sur le compte en suivant ces étapes pour effectuer une prise de contrôle par l’administrateur.

## <a name="step-1-verify-your-email-address"></a>Étape 1 : Vérifier votre adresse de messagerie

> [!NOTE]
> Si le libre-service est activé dans votre compte, les utilisateurs peuvent s’abonner à des services gratuits tels que Power BI, eux-mêmes. Ces services sont spécifiquement utilisés dans les cas où un abonnement utilisateur libre-service a créé le compte non pris en compte que vous souhaitez prendre en tant qu’administrateur. À l’étape 1, vous créez un compte d’utilisateur pour le domaine que vous souhaitez supprimer à l’aide de Power BI pour lancer l’Assistant Prise de contrôle de l’administrateur afin de pouvoir devenir l’administrateur du compte de domaine non utilisé.

1. Pour vous inscrire à Power BI, allez sur le [site](https://powerbi.com) >  Power BI et sélectionnez Démarrer l’essai **gratuit gratuit (** dans la zone Partager avec Power BI Pro). 

2. Inscrivez-vous avec un compte d’utilisateur qui utilise le nom de domaine de votre organisation (comme `powerbiadmin@contoso.com`). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Recherchez le **code de vérification dans votre** courrier électronique et entrez-le pour valider votre adresse de messagerie.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Étape 2 : Créer un compte pour l’accès administrateur

1. Lorsque vous entrez le code de vérification, vous êtes amené à une page dans laquelle vous pouvez créer un compte.

2. Remplissez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis complétez les étapes de création du compte.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir l’administrateur

1. Après avoir terminé l’étape 2, sélectionnez l’icône du Centre d’administration dans le volet de navigation de gauche (vous pouvez également vous rendre dans un navigateur et taper).`https://admin.microsoft.com`

    Vous êtes redirigé vers l’Assistant Prise de contrôle de l’administrateur.

2. **Sélectionnez Suivant** et vérifiez que vous êtes propriétaire du domaine à prendre en compte en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines.

    L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

3. Dans la **page Vous êtes maintenant l’administrateur** , **sélectionnez Aller au Centre d’administration**.

    Vous avez les privilèges d’administrateur requis pour gérer le compte dans le Centre d’administration. Par exemple, vous pouvez gérer les utilisateurs et les groupes de comptes, acheter de nouveaux abonnements, effectuer des affectations d’utilisateurs et gérer les domaines de compte.

    Si vous souhaitez supprimer votre domaine de ce compte afin de pouvoir l’ajouter à un autre compte, voir [Supprimer un domaine d’un autre compte](remove-a-domain-from-another-account.md).
  
## <a name="related-content"></a>Contenu associé

YouTube : [trois étapes pour une](https://www.youtube.com/watch?v=xt5EsrQBZZk) prise de contrôle d’administrateur informatique pour Power BI et Microsoft 365 (vidéo)\
[Prise de contrôle par l’administrateur dans Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (article)\
[Utilisation de l’inscription en libre-service dans votre organisation](self-service-sign-up.md) (article)\
[Understanding the Power BI service administrator role](/power-bi/service-admin-role) (article)