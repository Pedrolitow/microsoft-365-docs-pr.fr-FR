---
title: Configurer des stratégies d’accès conditionnel
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
- M365-Campaigns
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment exiger l’authentification MFA et configurer des stratégies d’accès conditionnel pour Microsoft 365 Business.
ms.openlocfilehash: 08e9365e8aad37e2412a6d739b41f2328c1aa277
ms.sourcegitcommit: c452413dff5d5388c9725f38871246237c313e65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "35183280"
---
# <a name="require-multi-factor-authentication-and-set-up-conditional-access-policies"></a>Exiger l’authentification multifacteur et configurer des stratégies d’accès conditionnel

Vous protégez l’accès à vos données à l’aide de l’authentification multifacteur et des stratégies d’accès conditionnel. Ces éléments ajoutent une sécurité supplémentaire importante. Microsoft fournit un ensemble de stratégies d’accès conditionnel de base qui sont recommandées pour tous les clients. Les stratégies de référence sont un ensemble de stratégies prédéfinies qui permettent de protéger les organisations contre de nombreuses attaques courantes. Ces attaques courantes peuvent inclure le pulvérisation de mot de passe, la relecture et le hameçonnage.

Ces stratégies exigent que les administrateurs et les utilisateurs entrent une deuxième forme d’authentification (appelée authentification multifacteur ou MFA) lorsque certaines conditions sont remplies. Par exemple, si un utilisateur de votre organisation tente de se connecter à Microsoft 365 à partir d’un autre pays ou d’un appareil inconnu, la connexion peut être considérée comme risquée. L’utilisateur doit fournir une forme supplémentaire d’authentification (par exemple, une empreinte digitale ou un code) pour prouver son identité. 

Actuellement, les stratégies de base sont les suivantes:
- Configurer dans le centre d’administration Microsoft 365:
    - **Exiger MFA pour les administrateurs** : nécessite une authentification multifacteur pour les rôles d’administrateur les plus privilégiés, y compris l’administrateur général.
    - **Protection** des utilisateurs finaux: nécessite l’authentification multifacteur pour les utilisateurs uniquement lorsqu’une connexion est risquée. 
- Configurer dans le portail Azure Active Directory:
    - **Bloquer l’authentification héritée** : les applications clientes plus anciennes et certaines nouvelles applications n’utilisent pas de protocoles d’authentification plus récents et plus sécurisés. Ces anciennes applications peuvent contourner des stratégies d’accès conditionnel et obtenir un accès non autorisé à votre environnement. Cette stratégie bloque l’accès à partir des clients qui ne prennent pas en charge l’accès conditionnel. 
    - **Exiger MFA pour la gestion des services** : nécessite l’authentification multifacteur pour l’accès aux outils de gestion, y compris le portail Azure (où vous configurez les stratégies de base). 

Microsoft vous recommande d’activer toutes ces stratégies de base. Une fois ces stratégies activées, les administrateurs et les utilisateurs sont invités à s’inscrire pour l’authentification multifacteur Azure.

Pour plus d’informations sur ces stratégies, voir [qu’est-ce qu’une stratégie de base](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-baseline-protection)?


## <a name="require-mfa"></a>Exiger MFA

Pour exiger que tous les utilisateurs se connectent avec une deuxième forme d’ID:

1. Accédez au centre d’administration à <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> l’adresse et sélectionnez **configuration**.

2. Sur la page de configuration, choisissez **Afficher** dans la carte de **connexion plus sécurisée** .


    ![Créer une carte plus sécurisée de connexion.](media/setupmfa.png)
3. Sur la page effectuer la connexion de façon plus sécurisée, sélectionnez **prise en main**.
 
4. Dans le volet sécurité de connexion renforcée, activez les cases à cocher en regard de **exiger l’authentification multifacteur pour les administrateurs** et **obliger les utilisateurs à s’inscrire pour l’authentification multifacteur et à bloquer l’accès si le risque est détecté**.
    N’oubliez pas d’exclure le compte administrateur d' [urgence](m365-campaigns-protect-admin-accounts.md#create-an-emergency-admin-account) ou de «disjoncteur» de l’exigence MFA dans la zone **Rechercher des utilisateurs** .
    
    ![Renforcer la page de sécurité à connexion unique.](media/requiremfa.png)

5. Sélectionnez **créer une stratégie** au bas de la page.

## <a name="set-up-baseline-policies"></a>Configurer des stratégies de base

1. Accédez au [portail Azure](https://portal.azure.com), puis accédez à **Azure Active Directory** \> **accès conditionnel**.
    
    Les stratégies de base sont répertoriées sur la page, et vous pouvez voir que l’authentification MFA pour les administrateurs et la protection des utilisateurs finaux sont déjà activées une fois que vous avez effectué les étapes de la rubrique [require MFA](#require-mfa).

    ![Page répertoriant les stratégies de base pour l’accès conditionnel.](media/casettings.png)
2. Consultez les instructions spécifiques suivantes pour chaque stratégie:

    - [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-baseline-protect-administrators)

       
    -   [Exiger l’authentification multifacteur pour les utilisateurs](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-baseline-protect-end-users)  
    - [Bloquer l’authentification héritée](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth)
    - [Exiger MFA pour la gestion des services](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-baseline-protect-azure)

Vous pouvez configurer des stratégies supplémentaires, telles que la demande d’applications clientes approuvées. Pour plus d’informations, reportez-vous à la documentation sur l' [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/) .
