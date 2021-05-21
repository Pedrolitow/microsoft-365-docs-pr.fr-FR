---
title: Effectuer une prise de contrôle d’administrateur interne
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Découvrez comment vérifier la propriété de votre courrier électronique et de votre domaine pour prendre le contrôle d’un client non pris en charge créé par une inscription utilisateur en libre-service dans Microsoft 365.
ms.openlocfilehash: c37bf153edf39f53b5c10f020b0cbb8d630eb4a6
ms.sourcegitcommit: b0d3abbccf4dd37e32d69664d3ebc9ab8dea760d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2021
ms.locfileid: "52593932"
---
# <a name="perform-an-internal-admin-takeover"></a>Effectuer une prise de contrôle d’administrateur interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 

Si vous êtes un administrateur et que vous souhaitez prendre le contrôle d’un client non pris en charge créé par une inscription d’utilisateur libre-service, vous pouvez le faire avec une prise de contrôle d’administrateur interne.

> [!NOTE]
> Une inscription en libre-service pour tout service cloud qui utilise Azure AD ajoute l’utilisateur à un répertoire Azure AD nonmanaté ou « shadow » et crée un client non pris en compte. Un client non gérant est un répertoire sans administrateur général. Pour déterminer si un client est géré ou non, voir [Déterminer le type de client.](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type) 
  
## <a name="step-1-verify-your-email-address"></a>Étape 1 : Vérifier votre adresse de messagerie

> [!NOTE]
> Si le libre-service est activé dans votre client, les utilisateurs peuvent s’abonner à des services gratuits, tels que Power BI, eux-mêmes. Ces étapes supposent qu’un abonnement utilisateur libre-service a créé le client non pris en compte que vous souhaitez prendre en tant qu’administrateur. Dans la première étape, vous créez un contexte utilisateur dans le client non Power BI pour illustrer le chemin d’accès de prise de contrôle de l’administrateur.

1. Pour vous inscrire à Power BI, allez sur le site  [Power BI et](https://powerbi.com) sélectionnez Démarrer l’essai gratuit gratuit (dans la zone Partager  >   avec Power BI Pro). 

2. Inscrivez-vous avec un compte d’utilisateur qui utilise le nom de domaine de votre organisation (comme `powerbiadmin@contoso.com` ). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Recherchez le **code de vérification dans votre** courrier électronique et entrez le code pour valider votre adresse de messagerie.
    
## <a name="step-2-create-a-new-account"></a>Étape 2 : Créer un compte

1. Lorsque vous entrez le code de vérification, vous êtes amené à une page dans laquelle vous pouvez créer un compte. 
    
2. Remplissez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis sélectionnez **Démarrer.** 
    
## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : Vérifier la propriété du domaine et devenir l’administrateur

1. **L’Assistant Devenir administrateur** s’ouvre. Si l’Assistant ne démarre pas, recherchez la vignette **Administrateur** et sélectionnez-la. 

2. Sélectionnez **Oui, je veux être l’administrateur.**

3. Vérifiez que vous êtes propriétaire du domaine à prendre en compte en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines. L’Assistant vous fournira l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site web de votre bureau d’enregistrement et un lien vers des instructions pas à pas.
    
4. Une fois que vous avez ajouté l’enregistrement TXT à votre site de bureau d’enregistrement, revenir à l’Assistant et sélectionnez **Ok, j’ai ajouté l’enregistrement**.
    
> [!NOTE]
> Le fait de prendre le contrôle du client de secours n’aura aucun impact sur les informations ou les services existants. Toutefois, si des utilisateurs du domaine se sont inscrits aux services qui nécessitent une licence, vous serez invité à acheter des licences pour eux dans le cadre de la prise de contrôle du rôle d’administrateur. Vous pouvez acheter ou supprimer des licences une fois le processus de configuration de l’administrateur terminé.
  
## <a name="related-content"></a>Contenu associé

YouTube : [3 étapes pour une](https://www.youtube.com/watch?v=xt5EsrQBZZk) prise de contrôle d’administrateur informatique pour Power BI et Microsoft 365 (vidéo)

[Prise de contrôle par l’administrateur dans Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (article)

[Utilisation de l’inscription en libre-service dans votre organisation](self-service-sign-up.md) (article)
  
[Understanding the Power BI service administrator role](/power-bi/service-admin-role) (article)