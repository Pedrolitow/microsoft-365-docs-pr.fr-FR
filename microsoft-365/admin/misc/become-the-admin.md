---
title: Effectuer un rachat administratif interne
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
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
description: Découvrez comment vérifier la propriété de votre messagerie et de votre domaine pour prendre le relais d’un locataire non géré dans Microsoft 365
ms.openlocfilehash: 9c1d98616b10737553060bcbad62df9b3b4c0c9a
ms.sourcegitcommit: 167c05cc6a776f62f0a0c2de5f3ffeb68c4a27ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "46814467"
---
# <a name="perform-an-internal-admin-takeover"></a>Effectuer un rachat administratif interne

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 

Si vous êtes un administrateur et que vous souhaitez prendre le relais d’un client non géré créé par un abonnement d’utilisateur libre-service, vous pouvez effectuer cette opération avec un test administratif interne.

> [!NOTE]
> Un self-service s’abonner à un service Cloud qui utilise Azure AD ajoute l’utilisateur à un annuaire Azure AD non géré ou « Ombré » et crée un locataire non géré. Un locataire non géré est un répertoire sans administrateur global. Pour déterminer si un client est géré ou non géré, consultez la rubrique [Determining client type](https://docs.microsoft.com/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="step-1-verify-your-email-address"></a>Étape 1 : vérifier votre adresse de messagerie

> [!NOTE]
> Si le self-service est activé dans votre client, les utilisateurs peuvent s’abonner à des services gratuits, comme Power BI, de leur côté. Ces étapes supposent qu’un abonnement d’utilisateur libre-service a créé le locataire non géré que vous souhaitez prendre en compte en tant qu’administrateur. La première étape consiste à créer un contexte utilisateur dans le locataire non géré à l’aide de Power BI pour illustrer le chemin de la prise en compte de l’administrateur.

1. Pour vous inscrire à Power bi, accédez au [site Power bi](https://powerbi.com) et sélectionnez **Démarrer**la  >  **version d’évaluation** gratuite de démarrage gratuit (dans la zone partager avec Power bi Pro). 

2. Inscrivez-vous à l’aide d’un compte d’utilisateur qui utilise le nom de domaine de votre organisation (par exemple `powerbiadmin@contoso.com` ). Si votre compte est déjà utilisé, connectez-vous à l’aide de votre mot de passe actuel.

3. Consultez votre courrier électronique pour obtenir le **Code de vérification** et entrez le code permettant de valider votre adresse e-mail.
    
## <a name="step-2-create-a-new-account"></a>Étape 2 : créer un compte

1. Lorsque vous entrez le code de vérification, vous accédez à une page où vous pouvez créer un compte. 
    
2. Renseignez les champs nom d’utilisateur et mot de passe avec le compte que vous souhaitez utiliser, puis sélectionnez **Démarrer**. 
    
## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Étape 3 : vérifier la propriété du domaine et devenir administrateur

1. L’Assistant d' **administration** s’ouvre. Si l’Assistant ne démarre pas, recherchez la vignette **administrateur** et sélectionnez-la. 

2. Sélectionnez **Oui, je veux être l’administrateur**.

3. Vérifiez que vous êtes propriétaire du domaine que vous souhaitez prendre en charge en ajoutant un enregistrement TXT à votre bureau d’enregistrement de domaines. L’Assistant vous donnera l’enregistrement TXT à ajouter, ainsi qu’un lien vers le site Web de votre registraire, ainsi qu’un lien vers des instructions pas à pas.
    
4. Une fois que vous avez ajouté l’enregistrement TXT à votre site de serveur d’inscriptions, revenez à l’Assistant et sélectionnez **OK, j’ai ajouté l’enregistrement**.
    
> [!NOTE]
> La prise en charge du client de cliché instantané n’a aucun impact sur les informations ou services existants. Toutefois, si un utilisateur du domaine s’est inscrit à des services nécessitant une licence, vous serez invité à acheter des licences pour ceux-ci dans le cadre de la prise en charge du rôle d’administrateur. Vous pouvez acheter ou supprimer des licences une fois le processus d’installation administratif terminé.
  
## <a name="related-articles"></a>Articles connexes

YouTube : [3 étapes pour effectuer une prise en compte de l’administrateur informatique pour Power bi et Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk)

[Prise en compte de l’administrateur dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover)

[Utilisation de l’inscription en libre-service au sein de votre organisation](self-service-sign-up.md)
  
[Présentation du rôle d’administrateur de service Power BI](https://docs.microsoft.com/power-bi/service-admin-role)

