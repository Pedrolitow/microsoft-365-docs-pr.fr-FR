---
title: Qu’est-ce que l’accès conditionnel ?
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
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment exiger une mf et configurer des stratégies d’accès conditionnel pour Microsoft 365 pour les entreprises.
ms.openlocfilehash: dcb79ed060dd15fd288cdcfb9e3739a788f5fbc2
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50912185"
---
# <a name="require-multi-factor-authentication-and-set-up-conditional-access-policies"></a>Exiger une authentification multifacteur et configurer des stratégies d’accès conditionnel

Vous protégez l’accès à vos données à l’aide de stratégies d’authentification multifacteur et d’accès conditionnel. Celles-ci ajoutent une sécurité supplémentaire substantielle. Microsoft fournit un ensemble de stratégies d’accès conditionnel de base recommandées pour tous les clients. Les stratégies de base sont un ensemble de stratégies prédéfines qui aident à protéger les organisations contre de nombreuses attaques courantes. Ces attaques courantes peuvent inclure la pulvérisation de mot de passe, la relecture et le hameçonnage.

Ces stratégies exigent que les administrateurs et les utilisateurs entrent dans un second formulaire d’authentification (appelé authentification multifacteur, ou authentification multifacteur) dans certaines conditions. Par exemple, si un utilisateur de votre organisation tente de se connecter à Microsoft 365 à partir d’un autre pays ou d’un appareil inconnu, la sign-in peut être considérée comme risquée. L’utilisateur doit fournir une forme supplémentaire d’authentification (par exemple, une empreinte digitale ou un code) pour prouver son identité.

Actuellement, les stratégies de référence incluent les stratégies suivantes :

- Configurer dans le Centre d’administration Microsoft 365 :
  - **Exiger l’authentification multifacteur pour** les administrateurs : nécessite une authentification multifacteur pour les rôles d’administrateur les plus privilégiés, y compris l’administrateur général.
  - **Protection de l’utilisateur final**: nécessite une authentification multifacteur pour les utilisateurs uniquement lorsqu’une authentification est risquée. 
- Configurer dans le portail Azure Active Directory :
  - **Bloquer l’authentification** héritée : les applications clientes plus anciennes et certaines nouvelles applications n’utilisent pas de protocoles d’authentification plus anciens, plus sécurisés. Ces anciennes applications peuvent contourner les stratégies d’accès conditionnel et obtenir un accès non autorisé à votre environnement. Cette stratégie bloque l’accès des clients qui ne la prisent pas en charge de l’accès conditionnel. 
  - **Exiger l’authentification** multifacteur pour la gestion des services : nécessite une authentification multifacteur pour l’accès aux outils de gestion, y compris au portail Azure (où vous configurez les stratégies de référence).

Nous vous recommandons d’activer toutes ces stratégies de référence. Une fois ces stratégies activées, les administrateurs et les utilisateurs sont invités à s’inscrire à l’authentification multifacteur Azure AD.

Pour plus d’informations sur ces stratégies, voir [Quelles sont les stratégies de base](/azure/active-directory/conditional-access/concept-baseline-protection)?

## <a name="require-mfa"></a>Exiger une authentification multifacteur

Pour exiger que tous les utilisateurs se connectent avec un deuxième formulaire d’ID :

1. Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> and choose **Setup**.

2. Dans la page Installation, **sélectionnez Afficher** dans la carte **de configuration plus** sécurisée.

    ![Rendre la carte de se connectez plus sécurisée.](../media/setupmfa.png)
3. On the Make sign-in more secure page, choose **Get started**.

4. Dans le volet Renforcer la sécurité de la signature, cochez les cases en regard de Exiger une authentification **multifacteur** pour les administrateurs et demander aux utilisateurs de s’inscrire à l’authentification **multifacteur** et de bloquer l’accès si des risques sont détectés.
    N’oubliez [](m365-campaigns-protect-admin-accounts.md#create-an-emergency-admin-account) pas d’exclure le compte d’administrateur d’urgence ou de « pause-arrêt » de l’exigence de l’mf dans la zone Rechercher **des utilisateurs.**

    ![Renforcer la page de sécurité du sing-in.](../media/requiremfa.png)

5. Choisissez **Créer une stratégie** en bas de la page.

## <a name="set-up-baseline-policies"></a>Configurer des stratégies de référence

1. Accédez au [portail Azure,](https://portal.azure.com)puis accédez à **l’accès** conditionnel de sécurité Azure Active Directory \>  \>  pour créer **une stratégie.**

Consultez les instructions spécifiques suivantes pour chaque stratégie : <br>
    - [Exiger l’mf pour les administrateurs](/azure/active-directory/conditional-access/howto-baseline-protect-administrators) <br>
    - [Exiger l’mf pour les utilisateurs](/azure/active-directory/conditional-access/howto-baseline-protect-end-users) <br>
    - [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-baseline-protect-legacy-auth) <br>
    - [Exiger l’mf pour la gestion des services](/azure/active-directory/conditional-access/howto-baseline-protect-azure)

> [!NOTE]
> Les stratégies d’aperçu n’existent plus et les utilisateurs doivent créer leurs propres stratégies.

Vous pouvez configurer des stratégies supplémentaires, telles que l’obligation d’applications clientes approuvées. Pour plus d’informations, voir la [documentation relative à l’accès conditionnel.](/azure/active-directory/conditional-access/)