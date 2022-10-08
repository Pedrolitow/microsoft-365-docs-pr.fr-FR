---
title: Déplacer un domaine vérifié dans un compte non managé
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
description: Découvrez comment joindre un compte non managé pour supprimer le domaine du compte et ajouter le domaine à votre compte.
ms.openlocfilehash: 7b7befdae4279b4b08ff076b88ed552b2bc411c3
ms.sourcegitcommit: c757f434da78bae71d4b476e14836fdf4da9f31e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2022
ms.locfileid: "67884319"
---
# <a name="move-a-domain-verified-in-an-unmanaged-account"></a>Déplacer un domaine vérifié dans un compte non managé

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes administrateur et que vous avez essayé d’ajouter un domaine à votre compte Microsoft 365, mais que vous êtes bloqué, car le domaine est vérifié pour un compte non managé, vous pouvez devenir l’administrateur sur le compte non managé pour supprimer le domaine et l’ajouter à votre compte.

> [!NOTE]
> Une inscription en libre-service à tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD non managé ou « fantôme » et crée un compte non managé. Un compte non managé est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non, consultez [Déterminer le type de locataire](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type).
  
## <a name="before-you-begin"></a>Avant de commencer

Parfois, vous ne pouvez pas ajouter de domaine à votre compte d’organisation, car une autre personne s’est déjà inscrite à Microsoft 365 à l’aide d’une adresse e-mail associée à ce nom de domaine. Toutefois, vous pouvez supprimer le domaine de l’autre compte non managé et l’ajouter à votre compte d’organisation.

Tout d’abord, vous devez joindre le compte non managé et devenir administrateur de ce compte (étapes 1 à 3). Vous pouvez ensuite supprimer le domaine du compte (étape 4), vous connecter à votre compte d’organisation et ajouter le domaine à votre compte (étape 5).

## <a name="step-1-get-an-invitation-to-join-the-unmanaged-account"></a>Étape 1 : Obtenir une invitation à rejoindre le compte non managé

Après avoir essayé d’ajouter un domaine à votre compte, vous pouvez recevoir un message indiquant qu’une personne s’est déjà inscrite à Microsoft 365 à l’aide de l’adresse e-mail. L’étape 1 consiste à demander une invitation à rejoindre l’autre compte et à commencer le processus d’exécution d’une prise de contrôle par l’administrateur.

1. Accédez au Centre d'administration Microsoft 365 > **Paramètres** > **Domaines** > **+ Ajouter un domaine**, puis ajoutez le nom de domaine.

1. Si vous voyez un message indiquant que vous ne pouvez pas ajouter le domaine, car d’autres personnes se sont déjà inscrites à l’aide d’une adresse e-mail pour le domaine, entrez le nom d’utilisateur de votre compte, puis **sélectionnez M’envoyer l’invitation**.

1. Déconnectez-vous de votre compte actuel pour pouvoir vous connecter au compte non managé.

    Vérifiez votre adresse e-mail pour obtenir une invitation pour vous aider à joindre le compte non managé, puis sélectionnez le lien fourni dans l’e-mail.

    Entrez le **code de vérification** à partir de l’e-mail pour valider votre adresse e-mail.

## <a name="step-2-complete-signup-with-email-instructions"></a>Étape 2 : Terminer l’inscription avec des instructions par e-mail

1. Lorsque vous entrez le code de vérification, vous accédez à une page dans laquelle vous pouvez créer un compte.

2. Renseignez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis effectuez les étapes pour créer le compte.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir administrateur

1. Une fois l’étape 2 terminée, sélectionnez l’icône du centre d’administration dans le volet de navigation gauche (vous pouvez également accéder à un navigateur et taper ).`https://admin.microsoft.com`

    Vous êtes redirigé vers l’Assistant Prise de contrôle d’administration.

1. Sélectionnez **Suivant** et vérifiez que vous êtes propriétaire du domaine que vous souhaitez reprendre en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines.

    L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

1. Dans la page **Vous êtes maintenant l’administrateur** , **sélectionnez Accéder au Centre d’administration**.

    Vous disposez désormais des privilèges d’administrateur requis pour supprimer le domaine du compte précédemment non managé.

## <a name="step-4-remove-a-domain-from-the-unmanaged-account"></a>Étape 4 : Supprimer un domaine du compte non managé

1. Accédez à **Utilisateurs** > **actifs** pour le compte que vous avez joint à l’étape 2, puis sélectionnez le nom d’affichage du nom d’utilisateur avec lequel vous êtes connecté.

1. Sous **Nom d’utilisateur**, **sélectionnez Gérer le nom d’utilisateur** et déplacez l’utilisateur vers le domaine onmicrosoft en choisissant le domaine onmicrosoft.com dans la liste déroulante.

1. Déconnectez-vous du compte et connectez-vous à l’aide du nouveau `username@account.onmicrosoft.com`.

1. Sélectionnez **Domaines de paramètres** > , recherchez le domaine que vous souhaitez ajouter à l’autre compte, puis **sélectionnez Supprimer le domaine**.

    Si vous êtes invité à sélectionner un autre domaine comme domaine par défaut, choisissez le domaine onmicrosoft.com.

    Si d’autres utilisateurs utilisent le domaine, vous devez les supprimer. Choisissez parmi les options pour **supprimer automatiquement**, déplacer manuellement les utilisateurs vers votre domaine ou supprimer complètement les utilisateurs.

   > [!NOTE]
   > Vérifiez que la suppression du domaine du compte peut prendre un certain temps. La suppression est terminée lorsque le domaine disparaît du compte.

1. Déconnectez-vous du compte.

## <a name="step-5-add-the-domain-to-your-account"></a>Étape 5 : Ajouter le domaine à votre compte

1. Connectez-vous au compte dans lequel vous souhaitez ajouter le domaine.

1. Sélectionnez **Domaines de paramètres** > **+ Ajouter un domaine**, puis entrez le nom de domaine pour poursuivre les **étapes** >  de l’Assistant pour vérifier la propriété du domaine dans ce compte et terminer l’ajout du domaine à votre compte.
  
## <a name="related-content"></a>Contenu associé

[Effectuer une prise de contrôle d’administrateur interne](become-the-admin.md) (article)
