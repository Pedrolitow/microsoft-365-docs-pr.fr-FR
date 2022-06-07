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
description: Découvrez comment vérifier votre adresse e-mail et votre propriété de domaine pour prendre en charge un compte non managé créé par une inscription d’utilisateur libre-service dans Microsoft 365.
ms.openlocfilehash: b930e9d4774dc9271d4bcbd93ffb9e5ced577dab
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922128"
---
# <a name="internal-admin-takeover"></a>Prise de contrôle de l’administrateur interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes administrateur et souhaitez prendre en charge un compte non managé créé par une inscription d’utilisateur libre-service, vous pouvez effectuer une prise de contrôle d’administrateur interne en suivant les étapes décrites dans cet article.

> [!NOTE]
> Une inscription en libre-service à tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD non managé ou « fantôme » et crée un compte non managé. Un compte non managé est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non, consultez [Déterminer le type de locataire](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Avant de commencer

Lorsqu’un utilisateur s’inscrit aux services Microsoft 365 à l’aide d’une adresse e-mail, un compte est automatiquement créé pour lui. Si un administrateur souhaite gérer les utilisateurs sur le compte ou acheter des services Microsoft 365 supplémentaires, il doit devenir administrateur sur le compte en suivant ces étapes pour effectuer une prise de contrôle d’administrateur.

## <a name="step-1-verify-your-email-address"></a>Étape 1 : Vérifier votre adresse e-mail

> [!NOTE]
> Si le libre-service est activé dans votre compte, les utilisateurs peuvent s’abonner eux-mêmes à des services gratuits tels que Power BI. Ces services sont spécifiquement utilisés dans les cas où un abonnement utilisateur libre-service a créé le compte non managé que vous souhaitez prendre en charge en tant qu’administrateur. À l’étape 1, vous créez un compte d’utilisateur pour le domaine que vous souhaitez supprimer à l’aide de Power BI pour lancer l’Assistant de prise de contrôle d’administration afin de devenir l’administrateur du compte de domaine non managé.

1. Pour vous inscrire à Power BI, accédez au [site Power BI](https://powerbi.com) et **sélectionnez Démarrer la****version d’évaluation gratuite du démarrage gratuit** >  (dans la zone Partager avec Power BI Pro). 

2. Inscrivez-vous avec un compte d’utilisateur qui utilise le nom de domaine de votre organisation (par exemple `powerbiadmin@contoso.com`). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Recherchez le code de **vérification** dans votre courrier électronique et entrez le code pour valider votre adresse e-mail.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Étape 2 : Créer un compte pour l’accès administrateur

1. Lorsque vous entrez le code de vérification, vous accédez à une page dans laquelle vous pouvez créer un compte.

2. Renseignez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis effectuez les étapes de création du compte.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir administrateur

1. Une fois l’étape 2 terminée, sélectionnez l’icône du centre d’administration dans le volet de navigation gauche (vous pouvez également accéder à un navigateur et taper ).`https://admin.microsoft.com`

    Vous êtes redirigé vers l’Assistant Prise de contrôle d’administration.

2. Sélectionnez **Suivant** et vérifiez que vous êtes propriétaire du domaine que vous souhaitez reprendre en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines.

    L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

3. Dans la page **Vous êtes maintenant l’administrateur** , **sélectionnez Accéder au Centre d’administration**.

    Vous disposez des privilèges d’administrateur requis pour gérer le compte dans le Centre d’administration. Par exemple, vous pouvez gérer les utilisateurs et les groupes de comptes, acheter de nouveaux abonnements et effectuer des affectations d’utilisateurs, et gérer les domaines de compte.

    Si vous souhaitez supprimer votre domaine de ce compte afin de pouvoir l’ajouter à un autre compte, consultez [Supprimer un domaine d’un autre compte](remove-a-domain-from-another-account.md).
  
## <a name="related-content"></a>Contenu connexe

YouTube : [Trois étapes pour effectuer une prise de contrôle d’administrateur informatique pour Power BI et Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk) (vidéo)\
[Prise de contrôle de l’administrateur dans Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (article)\
[Utilisation de l’inscription en libre-service dans votre organisation](self-service-sign-up.md) (article)\
[Présentation du rôle d’administrateur de service Power BI](/power-bi/service-admin-role) (article)