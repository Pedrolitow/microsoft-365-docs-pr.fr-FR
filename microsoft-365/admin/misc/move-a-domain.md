---
title: Déplacer un domaine vérifié dans un compte nonmanaté
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
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
description: Découvrez comment joindre un compte nonmana pour supprimer le domaine du compte et ajouter le domaine à votre compte.
ms.openlocfilehash: 3902853ea070f09e975b16a730d2b58209858853
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2022
ms.locfileid: "62156584"
---
# <a name="move-a-domain-verified-in-an-unmanaged-account"></a>Déplacer un domaine vérifié dans un compte nonmanaté

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

Si vous êtes un administrateur et que vous avez essayé d’ajouter un domaine à votre compte Microsoft 365, mais que vous êtes bloqué car le domaine est vérifié pour un compte nonmanaté, vous pouvez devenir l’administrateur sur le compte nonmanaté pour supprimer le domaine et l’ajouter à votre compte.

> [!NOTE]
> Une inscription en libre-service pour tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD non gestion ou « shadow » et crée un compte nonmanaté. Un compte non gérant est un répertoire sans administrateur général. Pour déterminer si un compte est géré ou non, voir [Déterminer le type de client.](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type)
  
## <a name="before-you-begin"></a>Avant de commencer

Parfois, vous ne pouvez pas ajouter un domaine à votre compte d’organisation, car quelqu’un d’autre s’est déjà inscrit à Microsoft 365 à l’aide d’une adresse de messagerie associée à ce nom de domaine. Toutefois, vous pouvez supprimer le domaine de l’autre compte nonmanaté et l’ajouter à votre compte d’organisation.

Tout d’abord, vous devez joindre le compte nonmana et devenir administrateur de ce compte (étapes 1 à 3). Ensuite, vous pouvez supprimer le domaine du compte (étape 4), vous revenir au compte de votre organisation et ajouter le domaine à votre compte (étape 5).

## <a name="step-1-get-an-invitation-to-join-the-unmanaged-account"></a>Étape 1 : Obtenir une invitation à rejoindre le compte nonmanaté

Après avoir essayé d’ajouter un domaine à votre compte, il se peut que vous receviez un message vous faisant savoir qu’une personne s’est déjà inscrite Microsoft 365 l’adresse e-mail. L’étape 1 consiste à demander une invitation à rejoindre l’autre compte et à lancer le processus de prise de contrôle par l’administrateur.

1. Go to the Centre d'administration Microsoft 365 > **Paramètres**  >  **Domains**  >  **+ Add domain**, and add the domain name.

1. Si un message vous demande de ne pas ajouter le domaine, car d’autres personnes se sont déjà inscrites à l’aide d’une adresse de messagerie pour le domaine, entrez le nom d’utilisateur de votre compte, puis sélectionnez M’envoyer **l’invitation.**

1. Dé sign out of your current account, so you can sign into the unmanaged account.

    Consultez votre courrier électronique pour obtenir une invitation pour vous aider à joindre le compte nonmanaté, puis sélectionnez le lien fourni dans l’e-mail.

    Entrez le **code de vérification à** partir de l’e-mail pour valider votre adresse e-mail.

## <a name="step-2-complete-signup-with-email-instructions"></a>Étape 2 : Terminer l’inscription avec des instructions par courrier électronique

1. Lorsque vous entrez le code de vérification, vous êtes amené à une page dans laquelle vous pouvez créer un compte.

2. Remplissez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis complétez les étapes de création du compte.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir l’administrateur

1. Après avoir terminé l’étape 2, sélectionnez l’icône du Centre d’administration dans le volet de navigation de gauche (vous pouvez également vous rendre dans un navigateur et `https://admin.microsoft.com` taper).

    Vous êtes redirigé vers l’Assistant Prise de contrôle de l’administrateur.

1. Sélectionnez **Suivant** et vérifiez que vous êtes propriétaire du domaine à prendre en compte en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines.

    L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.

1. On the **You’re now the admin** page, select **Go to the admin center**.

    Vous avez maintenant les privilèges d’administrateur requis pour supprimer le domaine du compte qui n’était auparavant pas gestion.

## <a name="step-4-remove-a-domain-from-the-unmanaged-account"></a>Étape 4 : Supprimer un domaine du compte nonmanaté

1. Go to **Users**  >  **Active users** for the account you joined in Step 2, and then select the Display name for the username you’re logged in with.

1. Sous Nom  **d’utilisateur,** sélectionnez Gérer le nom d’utilisateur et déplacez l’utilisateur vers le domaine onmicrosoft en choisissant le domaine onmicrosoft.com dans la liste liste.

1. Sign out of the account and sign back in using the new `username@account.onmicrosoft.com` .

1. Sélectionnez **Paramètres** domaines, recherchez le domaine que vous souhaitez ajouter à l’autre compte  >  et **sélectionnez Supprimer le domaine.**

    Si vous êtes invité à sélectionner un autre domaine par défaut, choisissez le onmicrosoft.com domaine.

    Si d’autres utilisateurs utilisent le domaine, vous devez les supprimer. Choisissez parmi les options pour **supprimer automatiquement,** déplacer manuellement les utilisateurs vers votre domaine ou supprimer complètement les utilisateurs.

   > [!NOTE]
   > Vérifiez à nouveau car la suppression du domaine du compte peut prendre un certain temps. La suppression est terminée lorsque le domaine disparaît du compte.

1. Se connectez au compte.

## <a name="step-5-add-the-domain-to-your-account"></a>Étape 5 : Ajouter le domaine à votre compte

1. Connectez-vous au compte où vous souhaitez ajouter le domaine.

1. Sélectionnez **Paramètres** Domaines + Ajouter un domaine, puis entrez le nom de domaine pour poursuivre les étapes de l’Assistant pour vérifier la propriété du domaine dans ce compte et terminer l’ajout du domaine à  >    >  votre compte.
  
## <a name="related-content"></a>Contenu associé

[Effectuer une prise de contrôle d’administrateur](become-the-admin.md) interne (article)
