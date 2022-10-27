---
title: Supprimer un domaine d’un autre compte
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Découvrez comment rejoindre un compte non managé créé par une inscription d’utilisateur libre-service dans Microsoft 365.
ms.openlocfilehash: 3f8a508f799e845c56584b32af294df69eaba330
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718675"
---
# <a name="perform-an-internal-admin-takeover"></a>Effectuer une prise de contrôle de l’administrateur interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes administrateur et que vous souhaitez prendre le contrôle d’un compte non géré créé par une inscription d’utilisateur libre-service, vous pouvez le faire en effectuant une prise de contrôle de l’administrateur interne.

> [!NOTE]
> Une inscription en libre-service pour n’importe quel service cloud qui utilise Azure AD ajoute l’utilisateur à un annuaire Azure AD non managé ou « fantôme » et crée un compte non managé. Un compte non managé est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non géré, consultez [Détermination du type de locataire](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Avant de commencer

Parfois, vous ne pouvez pas ajouter un domaine à votre compte d’organisation, car une autre personne s’est déjà inscrite à Microsoft 365 à l’aide d’une adresse e-mail associée à ce nom de domaine. Toutefois, vous pouvez supprimer le domaine de l’autre compte non managé et l’ajouter au compte géré par votre organisation.

Avant de pouvoir supprimer le domaine de l’autre compte et l’ajouter à votre compte, vous devez rejoindre le compte non managé et devenir administrateur pour ce compte. Ensuite, vous allez supprimer le domaine du compte non managé, vous reconnecter à votre compte et ajouter le domaine à votre compte managé.

Les étapes décrites dans cet article décrivent uniquement comment rejoindre l’autre compte (étapes 1 et 2) et suivre les étapes de l’Assistant Prise de contrôle de l’administrateur pour devenir l’administrateur sur le compte non géré (étape 3).

Une fois que vous êtes devenu administrateur pour le compte non managé, vous pouvez supprimer le domaine du compte non managé et l’ajouter à votre compte. 

## <a name="step-1-verify-your-email-address"></a>Étape 1 : Vérifier votre adresse e-mail

> [!NOTE]
> Si le libre-service est activé dans votre compte, les utilisateurs peuvent s’abonner à des services gratuits tels que Power BI, par eux-mêmes. Ces services sont spécifiquement utilisés dans les cas où un abonnement utilisateur libre-service a créé le compte non managé que vous souhaitez prendre en charge en tant qu’administrateur. À l’étape 1, vous créez un compte d’utilisateur pour le domaine que vous souhaitez supprimer à l’aide de Power BI pour lancer l’Assistant Prise de contrôle de l’administrateur afin de pouvoir devenir l’administrateur du compte de domaine non géré.

1. Pour vous inscrire à Power BI, accédez au [site Power BI](https://powerbi.com) et sélectionnez **Démarrer l’essai****gratuit de démarrage gratuit** >  (dans la zone Partager avec Power BI Pro). 

2. Inscrivez-vous avec un compte d’utilisateur qui utilise le nom de domaine de votre organisation (comme `powerbiadmin@contoso.com`). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Vérifiez le code de **vérification** dans votre adresse e-mail et entrez le code pour valider votre adresse e-mail.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Étape 2 : Créer un compte pour l’accès administrateur

1. Lorsque vous entrez le code de vérification, vous accédez à une page dans laquelle vous pouvez créer un compte.

2. Renseignez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis sélectionnez **Démarrer**.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir l’administrateur

1. Une fois l’étape 2 terminée, sélectionnez l’icône centre d’administration dans le volet de navigation gauche (vous pouvez également accéder à un navigateur et taper `https://admin.microsoft.com`).

    Vous êtes redirigé vers l’Assistant Prise de contrôle de l’administrateur.

1. Sélectionnez **Suivant** et vérifiez que vous êtes propriétaire du domaine que vous souhaitez prendre en charge en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines. 

    L’Assistant vous donne l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

1. Dans la page **Vous êtes maintenant l’administrateur** , sélectionnez **Accéder au centre d’administration**.

    Vous disposez maintenant des privilèges d’administrateur nécessaires pour supprimer le domaine de l’autre compte. 
## <a name="related-content"></a>Contenu associé

YouTube : [3 étapes pour effectuer une prise de contrôle Administration informatique pour Power BI et Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk) (vidéo)\
[Administration prise de contrôle dans Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (article)\
[Utilisation de l’inscription en libre-service dans votre organisation](self-service-sign-up.md) (article)\
[Présentation du rôle administrateur service Power BI](/power-bi/service-admin-role) (article)
