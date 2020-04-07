---
title: Configurer des stratégies d’accès conditionnel pour les campagnes Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment configurer des stratégies d’accès conditionnel pour les campagnes Microsoft 365 afin d’ajouter une sécurité supplémentaire substantielle.
ms.openlocfilehash: 26fadecc69486d7931dac069d8f53061592f397f
ms.sourcegitcommit: e525bcf073a61e1350484719a0c3ceb6ff0d8db1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "43153763"
---
# <a name="set-up-conditional-access-policies"></a>Configurer des stratégies d’accès conditionnel

Les stratégies d' [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) ajoutent une sécurité supplémentaire importante. Microsoft fournit un ensemble de stratégies d’accès conditionnel de base qui sont recommandées pour tous les clients. Les stratégies de référence sont un ensemble de stratégies prédéfinies qui permettent de protéger les organisations contre de nombreuses attaques courantes. Ces attaques courantes peuvent inclure le pulvérisation de mot de passe, la relecture et le hameçonnage.

Ces stratégies exigent que les administrateurs et les utilisateurs entrent une deuxième forme d’authentification (appelée authentification multifacteur ou MFA) lorsque certaines conditions sont remplies. Par exemple, si un utilisateur se connecte à partir d’un autre pays, la connexion peut être considérée comme risquée et l’utilisateur doit fournir une forme supplémentaire d’authentification. 

Actuellement, les stratégies de base sont les suivantes :
- **Exiger** &ndash; l’authentification multifacteur pour les administrateurs nécessite l’authentification multifacteur pour les rôles d’administrateur les plus privilégiés, y compris l’administrateur général.
- La **protection** &ndash; des utilisateurs finaux nécessite une authentification multifacteur pour les utilisateurs uniquement lorsqu’une connexion est risquée. 
- **Bloquer l’authentification** &ndash; héritée les anciennes applications clientes et certaines nouvelles applications n’utilisent pas de protocoles d’authentification plus récents et plus sécurisés. Ces anciennes applications peuvent contourner des stratégies d’accès conditionnel et obtenir un accès non autorisé à votre environnement. Cette stratégie bloque l’accès à partir des clients qui ne prennent pas en charge l’accès conditionnel. 
- **Exiger MFA pour la gestion** &ndash; de service nécessite l’authentification multifacteur pour l’accès aux outils de gestion, y compris le portail Azure (où vous configurez les stratégies de base). 

Microsoft vous recommande d’activer toutes ces stratégies de base. Une fois ces stratégies activées, les administrateurs et les utilisateurs sont invités à s’inscrire pour l’authentification Azure Multi-Factor.

Pour plus d’informations sur ces stratégies, voir [qu’est-ce qu’une stratégie de base](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-baseline-protection)?


## <a name="set-up-baseline-policies"></a>Configurer des stratégies de base

1. Accédez au [portail Azure](https://portal.azure.com), puis accédez à **Azure Active Directory** \> **accès conditionnel**.
    
    Les stratégies de base sont répertoriées sur la page. <br/> <br/>
    ![Page répertoriant les stratégies de base pour l’accès conditionnel.](../media/baslinepolicies.png)
1. Consultez les instructions spécifiques suivantes pour chaque stratégie :

  - [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-administrators)
- [Exiger l’authentification multifacteur pour les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-end-users)  
 - [Bloquer l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)
  - [Exiger MFA pour la gestion des services](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-azure)

Vous pouvez configurer de nombreuses stratégies supplémentaires, telles que la nécessité d’applications clientes approuvées. Pour plus d’informations, consultez la documentation sur l' [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/).
