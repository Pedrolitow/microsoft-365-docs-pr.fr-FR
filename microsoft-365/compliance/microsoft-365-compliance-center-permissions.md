---
title: Autorisations dans le Centre de conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
localization_priority: Normal
description: En savoir plus sur la gestion des autorisations dans le Centre de conformité Microsoft 365.
ms.collection: M365-security-compliance
ms.openlocfilehash: 717b8cd312aad805107536b174b3a9cd58e72a55
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59206195"
---
# <a name="permissions-in-the-microsoft-365-compliance-center"></a>Autorisations dans le Centre de conformité Microsoft 365

Le Centre de conformité Microsoft 365 a été récemment mis à jour et prend désormais en charge la gestion directe des autorisations pour les utilisateurs qui effectuent des tâches de conformité dans Microsoft 365. Cette mise à jour signifie que vous n’aurez plus besoin d’utiliser le Centre Office 365 sécurité et conformité & pour gérer les autorisations pour les solutions de conformité. À l’aide de la nouvelle page Autorisations dans le Centre de conformité Microsoft 365, vous pouvez gérer les autorisations accordées aux utilisateurs pour les tâches de conformité dans des **fonctionnalités telles** que la gestion des appareils, la protection contre la perte de données, eDiscovery, la gestion des risques internes, la rétention, etc. Les utilisateurs peuvent effectuer uniquement les tâches de conformité à qui vous leur accordez explicitement l’accès.

Pour afficher l’onglet Autorisations dans le Centre de conformité Microsoft 365, les utilisateurs doivent être  administrateur général ou avoir le  rôle Gestion des rôles (un rôle est attribué uniquement au groupe de **rôles** Gestion de l’organisation). Le *rôle Gestion des* rôles permet aux utilisateurs d’afficher, de créer et de modifier des groupes de rôles.

![Page Autorisations dans Centre de conformité Microsoft 365.](../media/m365-compliance-center-permissions.png)

Les autorisations dans le Centre de conformité Microsoft 365 sont basées sur le modèle d’autorisations de contrôle d’accès basé sur un rôle (RBAC). Le RBAC est le même modèle d’autorisations que celui utilisé par la plupart des services Microsoft 365. Ainsi, si vous êtes familiarisé avec la structure des autorisations de ces services, l’octroi d’autorisations dans le Centre de conformité Microsoft 365 sera familier. Il est important de se souvenir que les autorisations gérées dans le Centre de conformité Microsoft 365 ne couvrent pas la gestion de toutes les autorisations nécessaires dans chaque service individuel. Vous devrez toujours gérer certaines autorisations spécifiques au service dans le Centre d’administration pour le service spécifique. Par exemple, si vous devez attribuer des autorisations pour les stratégies d’archivage, d’audit et de rétention MRM, vous devez gérer ces autorisations dans le Centre d’administration Exchange.

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation entre les membres, les rôles et les groupes de rôles

Un rôle accorde des autorisations pour effectuer un ensemble de tâches ; Par exemple, le rôle Gestion des cas permet aux utilisateurs de travailler avec des cas eDiscovery.

Un groupe de rôles est un ensemble de rôles qui permettent aux utilisateurs d’assurer leur travail dans les solutions de conformité Centre de conformité Microsoft 365. Par exemple, en ajoutant  des utilisateurs au groupe de rôles Gestion des risques internes, les administrateurs désignés, les analystes, les enquêteurs et les auditeurs sont configurés pour les autorisations de gestion des risques internes nécessaires dans un seul groupe. Le Centre de conformité Microsoft 365 inclut des groupes de rôles par défaut pour les tâches et les fonctions pour chaque solution de conformité à qui vous devez affecter des personnes. En règle générale, nous vous recommandons d’ajouter simplement des utilisateurs individuels en tant que membres aux groupes de rôles de conformité par défaut si nécessaire.

![Diagramme montrant la relation entre les groupes de rôles et les rôles et les membres.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-microsoft-365-compliance-center"></a>Autorisations nécessaires pour utiliser les fonctionnalités du Centre de conformité Microsoft 365

Pour afficher tous les groupes de rôles par défaut qui sont disponibles dans le Centre de conformité Microsoft 365 et les rôles qui sont attribués aux groupes de rôles par défaut, consultez les [autorisations](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)dans le Centre de sécurité & conformité.

La gestion des autorisations dans le Centre de conformité Microsoft 365 permet uniquement aux utilisateurs d’accéder aux fonctionnalités de conformité disponibles dans le Centre de conformité Microsoft 365. Si vous souhaitez accorder des autorisations à d’autres fonctionnalités qui ne sont pas dans le Centre de conformité Microsoft 365, telles que les règles de flux de messagerie Exchange (également appelées règles de transport), vous devez utiliser le Centre d’administration Exchange.

## <a name="azure-roles-in-the-microsoft-365-compliance-center"></a>Rôles Azure dans le Centre de conformité Microsoft 365

Les rôles qui apparaissent dans la section **Rôles Azure AD** de la page  >   **Autorisations** Centre de conformité Microsoft 365 sont Azure Active Directory rôles. Ces rôles sont conçus pour s’aligner sur les fonctions du groupe informatique de votre organisation, ce qui permet de donner à vos utilisateurs les autorisations nécessaires pour accomplir leur travail. Vous pouvez afficher les utilisateurs actuellement affectés à chaque rôle en sélectionnant un rôle d’administrateur et en visualnant les détails du panneau de rôles. Pour gérer les membres d’un rôle Azure AD, sélectionnez Gérer les membres dans Azure AD. Ce choix vous redirige vers le portail de gestion Azure.

|Role|Description|
|:---|:----------|
|**Administrateur général**|Accède à toutes les fonctionnalités d’administration de tous les services Microsoft 365. Seuls les administrateurs généraux peuvent affecter d’autres rôles d’administrateur. Pour plus d’informations, consultez la section [Administrateur Général / Administrateur d’entreprise](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrateur de conformité des données**|Effectue un suivi des données de votre organisation dans Microsoft 365, vérifie qu’elles sont protégées et obtient des informations sur les problèmes liés à l’atténuation des risques. Pour en savoir plus, consultez la section [Administrateur de conformité des données](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrateur de conformité**|Aide votre organisation à respecter les exigences réglementaires, gère les cas de découverte électronique et gère les stratégies de gouvernance des données sur les emplacements, les identités et les applications Microsoft 365. Pour en savoir plus, consultez la section [Administrateur de conformité](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Opérateur de sécurité**|Consulter, examiner et répondre aux menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365. Pour plus d’informations, voir la section [Opérateur de sécurité](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Lecteur de sécurité**|Consulte et examine les menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365, mais, contrairement à l’opérateur de sécurité, il n’est pas autorisé à répondre par une action. Pour plus d’informations, voir la section [Lecteur de sécurité](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrateur de sécurité**|Contrôle la sécurité globale de votre organisation en gérant les stratégies de sécurité, en examinant les analyses de la sécurité et les rapports sur les produits Microsoft 365 et en se tenant à jour sur les menaces. Pour plus d’informations, voir la section [Administrateur de sécurité](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Lecteur général**|Version en lecture seule du rôle **Administrateur général**. Affiche tous les paramètres et informations administratives dans Microsoft 365. Pour plus d’informations, consultez [Lecteur général](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrateur de simulation d’attaque**|Créez et gérez tous les aspects de la créationsimulation d’attaque, le lancement/la planification d’une simulation et l’examen des résultats de la simulation. Pour plus d’informations, consultez [Administrateur de simulation d’attaques](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Auteur de la charge utile d’attaque**|Créez des charges utiles d’attaque, mais ne les lancez pas ou ne planifiez pas réellement. Pour plus d’informations, consultez [Auteur de charge utile d’attaque](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Ajouter des utilisateurs à un groupe de rôles de conformité

Pour ajouter des utilisateurs à un groupe de rôles de conformité, vous pouvez effectuer les étapes suivantes :

1. Connectez-vous à la zone d’autorisations du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Autorisations.** Sélectionnez le lien pour afficher et gérer les rôles de conformité dans Microsoft 365.
3. Développez la section **Centre de conformité** et sélectionnez **Rôles.**
4. Dans la page **Rôles** du Centre de conformité, sélectionnez  un groupe de rôles de conformité à ajouter aux utilisateurs, puis sélectionnez Modifier le groupe de rôles dans le volet d’informations.
5. Sélectionnez **Choisir des membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier.**
6. Sélectionnez **Ajouter,** puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.
7. Sélectionnez **Ajouter**, puis **Terminé**.
8. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="remove-users-from-a-compliance-role-group"></a>Supprimer des utilisateurs d’un groupe de rôles de conformité

Pour supprimer des utilisateurs d’un groupe de rôles de conformité, effectuer les étapes suivantes :

1. Connectez-vous à la zone d’autorisations du [Centre de conformité Microsoft 365](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Autorisations.** Sélectionnez le lien pour afficher et gérer les rôles de conformité dans Microsoft 365.
3. Développez la section Centre de conformité et sélectionnez **Rôles.**
4. Dans la page **Rôles** du Centre de conformité, sélectionnez  un groupe de rôles de conformité dont vous souhaitez supprimer des utilisateurs, puis sélectionnez Modifier le groupe de rôles dans le volet d’informations.
5. Sélectionnez **Choisir des membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier.**
6. Sélectionnez **Supprimer,** puis cochez la case pour tous les utilisateurs que vous souhaitez supprimer du groupe de rôles.
7. Sélectionnez **Supprimer,** puis **Terminé.**
8. Sélectionnez **Enregistrer** pour supprimer les utilisateurs du groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

## <a name="create-a-custom-role-group"></a>Créer un groupe de rôles personnalisé

Pour créer un groupe de rôles personnalisé, vous pouvez effectuer les étapes suivantes :

1. Connectez-vous [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Autorisations.**
3. Dans la page **Autorisations & rôles,** sélectionnez Centre de conformité **> rôles .**
4. Dans la page **Rôles du Centre de** conformité, sélectionnez **Créer.**
5. Dans la page **Nom de votre groupe de rôles,** entrez un nom pour le groupe de rôles personnalisé dans le **champ** Nom. Le nom du groupe de rôles ne peut pas être modifié après la création du groupe de rôles. Si nécessaire, entrez une description pour le groupe de rôles personnalisé dans le **champ Description.** Sélectionnez **Suivant** pour continuer.
6. Dans la page **Choisir des rôles,** **sélectionnez Choisir des rôles.**
7. **Sélectionnez** Ajouter, puis choisissez les rôles à ajouter au groupe de rôles personnalisé. Sélectionnez **Ajouter** pour ajouter le groupe de rôles, puis **sélectionnez Terminé.**
8. Sélectionnez **Suivant** pour continuer.
9. Dans la page **Choisir des membres,** **sélectionnez Choisir les membres.**
10. **Sélectionnez** Ajouter, puis choisissez les membres à ajouter au groupe de rôles personnalisé. Sélectionnez **Ajouter** pour ajouter les membres, puis **sélectionnez Terminé.**
11. Sélectionnez **Suivant** pour continuer.
12. Dans la page **Examiner vos paramètres,** examinez les détails du groupe de rôles personnalisé. Si vous devez modifier les informations, sélectionnez **Modifier** dans la section appropriée. Lorsque tous les paramètres  sont corrects, sélectionnez Créer un groupe de rôles pour créer le groupe de rôles personnalisé ou sélectionnez **Annuler** pour ignorer les modifications et ne pas créer le groupe de rôles personnalisé.

## <a name="update-a-custom-role-group"></a>Mettre à jour un groupe de rôles personnalisé

Pour mettre à jour un groupe de rôles personnalisé, vous suivrez les étapes suivantes :

1. Connectez-vous [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Autorisations.**
3. Dans la page **Autorisations & rôles,** sélectionnez Centre de conformité **> rôles .**
4. Dans la page **Rôles du Centre de** conformité, sélectionnez le groupe de rôles à mettre à jour.
5. Dans le volet d’informations du groupe de rôles sélectionné, sélectionnez **Modifier le groupe de rôles.**
6. Dans la page **Modifier le nom du** groupe de rôles, mettez à jour la description du groupe de rôles personnalisé dans le champ **Description.** Le nom du groupe de rôles personnalisé ne peut pas être modifié.
7. Dans la page **Choisir des rôles,** **sélectionnez Modifier** pour mettre à jour les rôles attribués aux groupes de rôles.
8. **Sélectionnez** Ajouter, puis choisissez les rôles à ajouter au groupe de rôles personnalisé. Sélectionnez **Ajouter** pour ajouter le groupe de rôles, puis **sélectionnez Terminé.**
9. Dans la page **Choisir les membres,** sélectionnez **Modifier.**
10. **Sélectionnez** Ajouter, puis choisissez les membres à ajouter au groupe de rôles personnalisé. Sélectionnez **Ajouter** pour ajouter les membres, puis **sélectionnez Terminé.**
11. Sélectionnez **Enregistrer** pour enregistrer la *description* mise à jour, *les groupes de rôles* et les *valeurs membres.*
12. Dans le volet d’informations du groupe de rôles sélectionné, sélectionnez **Fermer.**

## <a name="delete-a-custom-role-group"></a>Supprimer un groupe de rôles personnalisé

Pour mettre à jour un groupe de rôles personnalisé, vous suivrez les étapes suivantes :

1. Connectez-vous [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Autorisations.**
3. Dans la page **Autorisations & rôles,** sélectionnez Centre de conformité **> rôles .**
4. Dans la page **Rôles du Centre de** conformité, sélectionnez le groupe de rôles à mettre à jour.
5. Dans le volet d’informations du groupe de rôles sélectionné, sélectionnez **Supprimer le groupe de rôles.**
6. Dans la boîte **de dialogue** Avertissement, sélectionnez **Oui** pour supprimer le groupe de rôles ou **non** pour annuler le processus de suppression.
