---
title: Administration rôles pour Intune dans le Centre d'administration Microsoft 365
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.collection:
- tier1
description: Le Centre d’administration Microsoft 365 vous permet de gérer certains rôles Microsoft Intune, qui sont mappés aux fonctions métier et donnent des autorisations pour effectuer des tâches spécifiques.
ms.openlocfilehash: b00547a4f89d5e1b64dfbfab4a5cb5aa6c9a0c0a
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097465"
---
# <a name="admin-roles-for-intune-in-the-microsoft-365-admin-center"></a>Administration rôles pour Intune dans le Centre d'administration Microsoft 365

Votre abonnement à Microsoft 365 ou Office 365 s'accompagne d'un ensemble de rôles d'administrateur que vous pouvez attribuer à tous les utilisateurs de votre organisation à l'aide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centre d'administration Microsoft 365 </a>. Chaque rôle d’administrateur correspond à des fonctions d’entreprise courantes et donne aux personnes concernées dans votre organisation des autorisations pour effectuer des tâches spécifiques dans les centres d’administration. Par conséquent, ces rôles ne sont qu'un sous-ensemble de tous les rôles disponibles dans le centre d'administration d' Intune, qui comprend des rôles supplémentaires spécifiques à Intune lui-même.

Avant d'ajouter des rôles Intune spécifiques, les rôles doivent être attribués dans Azure AD. Pour voir ces rôles, choisissez **gestionnaire Endpoint > Administration du locataire > Rôles > Tous les rôles >**. Vous pouvez gérer le rôle sur les pages suivantes :

- Propriétés : nom, description, autorisations et balises d’étendue pour le rôle.
- Affectations : Une liste d'affectations de rôles définissant quels utilisateurs ont accès à quels utilisateurs ou appareils. Un rôle peut avoir plusieurs attributions, et un utilisateur peut figurer dans plusieurs attributions.

## <a name="about-roles-based-access-control-in-intune"></a>À propos du contrôle d'accès basé sur les rôles dans Intune

Le contrôle d'accès basé sur les rôles (RBAC) vous aide à gérer les personnes qui ont accès aux ressources de votre organisation et ce qu'elles peuvent faire avec ces ressources. En attribuant des rôles à vos utilisateurs Intune, vous pouvez limiter ce qu’ils peuvent voir et modifier. Il existe des rôles intégrés et personnalisés, et chaque rôle est assorti d'un ensemble de permissions qui déterminent ce à quoi les utilisateurs dotés de ce rôle peuvent accéder ou modifier au sein de votre organisation. Les informations suivantes couvrent les deux types de rôles dans Intune.

Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :

- **Administrateur général**
- **Administrateur de services Intune** (également connu **sous le nom d'administrateur** système Intune, mais à ne pas confondre avec le rôle intégré **d'administrateur de rôles** Intune).

Trouvez plus d'informations sur les rôles [Azure Active Directory et RBAC ](/azure/active-directory/roles/permissions-reference.md).

## <a name="microsoft-intune-built-in-roles"></a>Rôles intégrés de Microsoft Intune

Les rôles intégrés utilisent des règles prédéfinies basées sur des scénarios Intune courants. Par ailleurs, les rôles personnalisés sont construits sur la base de règles strictement définies par vous. 

Voici les rôles intégrés que vous pouvez attribuer :

|Rôle d’administrateur     |À qui doit être affecté ce rôle ?  |
|---------|---------|
|**Gestionnaire d’applications**     |   Attribuez le rôle de gestionnaire d'applications aux utilisateurs qui gèrent le cycle de vie des applications pour les applications mobiles, qui configurent les applications gérées par des stratégies et qui affichent les informations sur les appareils et les profils de configuration.  |
|**Opérateur du support technique**     |   Attribuez le rôle d’opérateur du support technique aux utilisateurs qui attribuent des applications et des stratégies aux utilisateurs et aux appareils. |
|**Administrateur de rôle Intune**    |   Attribuez le rôle d'administrateur de rôle Intune aux utilisateurs qui peuvent attribuer des autorisations Intune à d'autres administrateurs et gérer des rôles Intune personnalisés et intégrés.   |
|**Gestionnaire des stratégies et des profils**     |   Attribuez le rôle de gestionnaire des stratégies et des profils aux utilisateurs qui gèrent la stratégie de conformité, les profils de configuration et l'inscription Apple.   |
|**Opérateur en lecture seule**     |   Attribuez le rôle d’opérateur en lecture seule aux utilisateurs qui peuvent uniquement consulter les utilisateurs, les appareils, les détails d’inscription et les configurations.   |
|**Administrateur scolaire**     |   Attribuez le rôle d'administrateur scolaire aux utilisateurs pour un accès complet à la gestion des appareils, des applications et des configurations Windows 10-11 et iOS dans Intune pour l'éducation.   |
|**Administrateur de PC en cloud**     |   Un administrateur de PC en cloud computing a un accès en lecture et en écriture à toutes les fonctionnalités de PC en cloud computing situées dans la lame de PC en cloud computing.   |
|**Lecteur PC en cloud**     |   Un lecteur de PC en cloud computing a un accès en lecture à toutes les fonctionnalités du PC en cloud computing situées dans la lame du PC en cloud computing.   |

## <a name="microsoft-intune-custom-roles"></a>Rôles personnalisés de Microsoft Intune

Vous pouvez créer des rôles personnalisés dans Intune qui incluent toutes les autorisations requises pour une fonction spécifique. Par exemple, si un groupe du service informatique gère les applications, les stratégies et les profils de configuration, vous pouvez ajouter toutes ces autorisations ensemble à un même rôle personnalisé. Après avoir créé un rôle personnalisé, vous pouvez l’attribuer à tout utilisateur ayant besoin de ces autorisations.

Comme pour les rôles intégrés, pour pouvoir créer, modifier ou attribuer des rôles, votre compte doit disposer de l'une des autorisations suivantes dans Azure AD :

- **Administrateur général**
- **Administrateur de services Intune** (également connu sous le nom **d'administrateur Intune**, mais à ne pas confondre avec le rôle intégré **d'administrateur de rôles Intune**).

Pour créer un rôle personnalisé :

1. Dans le centre d'administration de Microsoft Endpoint Manager, choisissez **Tenant administration > Rôles > Tous les rôles > Créer**.

1. Dans la page **De base**, entrez un nom et une description pour le nouveau rôle, puis choisissez **Suivant**.

1. Dans la page **Autorisations**, choisissez les autorisations que vous voulez utiliser avec ce rôle.

1. Dans la page **Étendue (balises)**, choisissez les balises pour ce rôle. Lorsque ce rôle est attribué à un utilisateur, celui-ci peut accéder à des ressources ayant également ces balises. Cliquez sur **Suivant**.

1. Dans la page **Vérifier + créer**, quand vous avez terminé, choisir **Créer**. Le nouveau rôle s’affiche dans la liste du panneau **Rôles Intune - Tous les rôles**.

Pour copier un rôle :

1. Dans le centre d'administration du gestionnaire Microsoft Endpoint Manager, choisissez Administration du locataire > Rôles >**Tous les rôles >** cochez la case d'un rôle dans la liste >**Dupliquer**.

1. Dans la page **De base**, entrez un nom. Veillez à utiliser un nom unique.

1. Toutes les autorisations et balises d’étendue du rôle d’origine sont déjà sélectionnées. Vous pouvez ensuite modifier le **nom, la description, les autorisations et le champ d'application (balises)** du rôle dupliqué.

1. Une fois que vous avez apporté toutes les modifications souhaitées, choisissez Suivant pour accéder à la page Vérifier + créer. Sélectionnez **Créer**.

> [!Note]
>Pour pouvoir administrer Intune, une licence Intune doit vous être attribuée. Vous pouvez également autoriser les utilisateurs sans licence à administrer Intune en définissant l'option **Autoriser l'accès aux administrateurs** sans licence sur **Oui**.

## <a name="how-to-assign-a-role"></a>Comment attribuer un rôle

Vous pouvez attribuer un rôle intégré ou personnalisé à un utilisateur d’Intune. Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :

- **Administrateur général**
- **Administrateur de services Intune** (également connu sous le nom **d'administrateur Intune**, mais à ne pas confondre avec le rôle intégré **d'administrateur de rôles Intune**).

1. Dans le centre d'administration de Microsoft Endpoint Manager, choisissez **Tenant administration > Rôles > Tous les rôles**.

1. Sur la lame **Rôles de Endpoint Manager** – Tous les rôles, choisissez le rôle intégré que vous voulez attribuer > Attributions > + Attribuer.

1. Sur la page Principes de **base**, saisissez un nom d'affectation et une description facultative de l'affectation, puis sélectionnez **Suivant**.

1. Dans la page **Groupes d'administrateurs**, sélectionnez le groupe contenant l’utilisateur à qui vous voulez accorder les autorisations. Cliquez sur **Suivant**.

1. Sur la page **Scope (Groupes)**, choisissez un groupe contenant les utilisateurs et les dispositifs que le membre ci-dessus sera autorisé à gérer. Vous avez également la possibilité de choisir tous les utilisateurs ou tous les appareils. Cliquez sur **Suivant**.

> [!Note]
> **Tous les utilisateurs** et **tous les appareils** sont **des groupes virtuels Intune** et non des groupes Azure Active Directory (Azure AD). Par conséquent, pour l'attribution de **l'étendue (groupes)**, vous ne pouvez pas les utiliser comme parents de groupes de sécurité Azure AD. Si vous avez besoin à la fois de **Tous les utilisateurs** et **Tous les dispositifs** et de groupes de sécurité Azure AD spécifiques pour les affectations **d'étendue (Groupes)**, vous devez les ajouter séparément avec des affectations distinctes. Sinon, même si l'affectation de la portée (groupes) d'un rôle est définie sur **Tous les utilisateurs**, l'administrateur dans ce rôle n'aura pas accès à des groupes d'utilisateurs Azure AD spécifiques. Pour les groupes de sécurité Azure AD, l'imbrication est prise en charge.

6. Dans la page **Étendue (balises)**, choisissez des balises où cette attribution de rôle s’appliquera. Cliquez sur **Suivant**.

7. Dans la page **Vérifier + créer**, quand vous avez terminé, choisissez **Créer**. La nouvelle affectation s’affiche dans la liste des affectations.

> [!Note]
> Lorsque vous créez des groupes d’étendue et affectez une balise d’étendue, vous ne pouvez cibler que les groupes répertoriés dans l’étendue (groupes) de votre attribution de rôle.

## <a name="delegated-administration-for-microsoft-partners"></a>Administration déléguée pour les partenaires Microsoft

If you're working with a Microsoft partner, you can assign them admin roles. They, in turn, can assign users in your company - or their company - admin roles. You might want them to do this, for example, if they're setting up and managing your online organization for you.
  
Un partenaire peut attribuer ces rôles : 
  
- Administration complète, qui dispose de privilèges équivalents à un administrateur général, à l’exception de la gestion de l’authentification multifacteur via l’Espace partenaires.

- Administration limitée, dont les privilèges sont équivalents à ceux d’un administrateur du support technique.

Before the partner can assign these roles to users, you must add the partner as a delegated admin to your account. This process is initiated by an authorized partner. The partner sends you an email to ask you if you want to give them permission to act as a delegated admin. For instructions, see [Authorize or remove partner relationships](../admin/misc/add-partner.md).
  
## <a name="related-content"></a>Contenu associé

[À propos des rôles d’administrateur Microsoft 365](../admin/add-users/about-admin-roles.md) (article)\
[Attribuer des rôles administrateur](../admin/add-users/assign-admin-roles.md) (article)\
[Rapports d’activité dans le Centre d’administration Microsoft 365](../admin/activity-reports/activity-reports.md) (article)
