---
title: Créer et gérer des groupes d’appareils dans Microsoft Defender pour le point de terminaison
description: Créer des groupes d’appareils et définir des niveaux de correction automatisés sur ces derniers en confirmant les règles qui s’appliquent au groupe
keywords: groupes d’appareils, groupes, correction, niveau, règles, groupe aad, rôle, attribuer, rang
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 95f377992c745045667a016fcf7dae1b391f2323
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60554071"
---
# <a name="create-and-manage-device-groups"></a>Créer et gérer des groupes d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- Azure Active Directory
- Office 365

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dans un scénario d’entreprise, un ensemble d’appareils est généralement affecté aux équipes chargées des opérations de sécurité. Ces appareils sont regroupés en fonction d’un ensemble d’attributs tels que leurs domaines, noms d’ordinateur ou balises désignées.

Dans Microsoft Defender for Endpoint, vous pouvez créer des groupes d’appareils et les utiliser pour :

- Limiter l’accès aux alertes et données associées à des groupes d Azure AD utilisateurs spécifiques avec [des rôles RBAC attribués](rbac.md)
- Configurer différents paramètres de correction automatique pour différents ensembles d’appareils
- Affecter des niveaux de correction spécifiques à appliquer lors d’examens automatisés
- Dans un examen, filtrez la liste **Appareils** sur des groupes d’appareils spécifiques à l’aide du **filtre** de groupe.

Vous pouvez créer des groupes d’appareils dans le contexte de l’accès basé sur les rôles (RBAC) pour contrôler qui peut prendre des mesures spécifiques ou voir les informations en attribuant le ou les groupes d’appareils à un groupe d’utilisateurs. Pour plus d’informations, voir [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur les rôles.](rbac.md)

> [!TIP]
> Pour une vue d’ensemble de l’application RBAC, lisez : votre SOC fonctionne-t-il [à plat avec RBAC](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015).

Dans le cadre du processus de création d’un groupe d’appareils, vous devez :

- Définissez le niveau de correction automatisé pour ce groupe. Pour plus d’informations sur les niveaux de correction, voir [Utiliser l’examen automatisé pour examiner et corriger les menaces.](automated-investigations.md)
- Spécifiez la règle correspondante qui détermine quel groupe d’appareils appartient au groupe en fonction du nom de l’appareil, du domaine, des balises et de la plateforme du système d’exploitation. Si un appareil est également en correspondance avec d’autres groupes, il est ajouté uniquement au groupe d’appareils le mieux classé.
- Sélectionnez le Azure AD d’utilisateurs qui doit avoir accès au groupe d’appareils.
- Classer le groupe d’appareils par rapport aux autres groupes après sa création.

> [!NOTE]
> Un groupe d’appareils est accessible à tous les utilisateurs si vous n’affectez Azure AD groupes.

## <a name="create-a-device-group"></a>Créer un groupe d’appareils

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **groupes d’appareils** \> **Endpoints Permissions.** \> 

2. Cliquez **sur Ajouter un groupe d’appareils.**

3. Entrez le nom du groupe et les paramètres d’automatisation et spécifiez la règle correspondante qui détermine quels appareils appartiennent au groupe. Découvrez [comment l’enquête automatisée démarre.](automated-investigations.md#how-the-automated-investigation-starts)

    > [!TIP]
    > Si vous souhaitez grouper des appareils par unité d’organisation, vous pouvez configurer la clé de Registre pour l’affiliation au groupe. Pour plus d’informations sur le marquage des appareils, voir [Créer et gérer des balises d’appareil.](machine-tags.md)

4. Affichez un aperçu de plusieurs appareils qui seront en correspondance avec cette règle. Si vous êtes satisfait de la règle, cliquez sur **l’onglet Accès** utilisateur.

5. Affectez les groupes d’utilisateurs qui peuvent accéder au groupe d’appareils que vous avez créé.

    > [!NOTE]
    > Vous pouvez uniquement accorder l’accès Azure AD groupes d’utilisateurs qui ont été affectés à des rôles RBAC.

6. Cliquez sur **Fermer**. Les modifications de configuration sont appliquées.

## <a name="manage-device-groups"></a>Gérer les groupes d’appareils

Vous pouvez promouvoir ou rétrograder le rang d’un groupe d’appareils afin qu’il soit plus ou moins prioritaire lors de la mise en correspondance. Lorsqu’un appareil est en correspondance avec plusieurs groupes, il est ajouté uniquement au groupe le plus élevé. Vous pouvez également modifier et supprimer des groupes.

> [!WARNING]
> La suppression d’un groupe d’appareils peut affecter les règles de notification par courrier électronique. Si un groupe d’appareils est configuré sous une règle de notification par courrier électronique, il sera supprimé de cette règle. Si le groupe d’appareils est le seul groupe configuré pour une notification par courrier électronique, cette règle de notification par courrier électronique est supprimée avec le groupe d’appareils.

Par défaut, les groupes d’appareils sont accessibles à tous les utilisateurs ayant accès au portail. Vous pouvez modifier le comportement par défaut en attribuant Azure AD groupes d’utilisateurs au groupe d’appareils.

Les appareils qui ne correspondent à aucun groupe sont ajoutés au groupe Appareils non regroupés (par défaut). Vous ne pouvez pas modifier le rang de ce groupe ni le supprimer. Toutefois, vous pouvez modifier le niveau de correction de ce groupe et définir les groupes Azure AD utilisateurs qui peuvent accéder à ce groupe.

> [!NOTE]
> L’application de modifications à la configuration du groupe d’appareils peut prendre jusqu’à plusieurs minutes.

### <a name="add-device-group-definitions"></a>Ajouter des définitions de groupe d’appareils

Les définitions de groupe d’appareils peuvent également inclure plusieurs valeurs pour chaque condition. Vous pouvez définir plusieurs balises, noms d’appareils et domaines sur la définition d’un seul groupe d’appareils.

1. Créez un groupe d’appareils, puis sélectionnez **Onglet** Appareils.
2. Ajoutez la première valeur pour l’une des conditions.
3. Sélectionnez `+` pour ajouter d’autres lignes du même type de propriété.

> [!TIP]
> Utilisez l’opérateur « OR » entre les lignes du même type de condition, qui autorise plusieurs valeurs par propriété.
> Vous pouvez ajouter jusqu’à 10 lignes (valeurs) pour chaque type de propriété : balise, nom de l’appareil, domaine.

Pour plus d’informations sur la liaison aux définitions de groupes d’appareils, voir [Groupes d’appareils - Microsoft 365 sécurité.](https://sip.security.microsoft.com/homepage)

## <a name="related-topics"></a>Voir aussi

- [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur un rôle](rbac.md)
- [Créer et gérer des balises d’appareils](machine-tags.md)
- [Obtenir la liste des groupes d’appareils client à l’aide Graph API](/graph/api/device-list-memberof)
