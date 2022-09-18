---
title: Créer et gérer des groupes d’appareils dans Microsoft Defender pour point de terminaison
description: Créer des groupes d’appareils et définir des niveaux de correction automatisés sur ces groupes en confirmant les règles qui s’appliquent au groupe
keywords: groupes d’appareils, groupes, correction, niveau, règles, groupe aad, rôle, attribution, classement
ms.service: microsoft-365-security
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 55bb0d81199755dc92899a477ce165388704ffce
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67799227"
---
# <a name="create-and-manage-device-groups"></a>Créer et gérer des groupes d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Azure Active Directory
- Office 365
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dans un scénario d’entreprise, les équipes d’opérations de sécurité se voient généralement attribuer un ensemble d’appareils. Ces appareils sont regroupés en fonction d’un ensemble d’attributs tels que leurs domaines, noms d’ordinateurs ou balises désignées.

Dans Microsoft Defender pour point de terminaison, vous pouvez créer des groupes d’appareils et les utiliser pour :

- Limiter l’accès aux alertes et données associées à des groupes d’utilisateurs Azure AD spécifiques avec des [rôles RBAC attribués](rbac.md)
- Configurer différents paramètres de correction automatique pour différents ensembles d’appareils
- Affecter des niveaux de correction spécifiques à appliquer pendant les investigations automatisées
- Dans une enquête, filtrez la **liste des appareils** sur des groupes d’appareils spécifiques à l’aide du filtre **De** groupe.

Vous pouvez créer des groupes d’appareils dans le contexte d’un accès en fonction du rôle (RBAC) pour contrôler qui peut prendre des mesures spécifiques ou afficher des informations en affectant le ou les groupes d’appareils à un groupe d’utilisateurs. Pour plus d’informations, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

> [!TIP]
> Pour une présentation complète de l’application RBAC, consultez : [votre SOC est-il en cours d’exécution à plat avec RBAC](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015)?

Dans le cadre du processus de création d’un groupe d’appareils, vous allez :

- Définissez le niveau de correction automatisé pour ce groupe. Pour plus d’informations sur les niveaux de correction, consultez [Utiliser l’investigation automatisée pour examiner et corriger les menaces](automated-investigations.md).
- Spécifiez la règle de correspondance qui détermine le groupe d’appareils qui appartient au groupe en fonction du nom de l’appareil, du domaine, des balises et de la plateforme du système d’exploitation. Si un appareil est également mis en correspondance avec d’autres groupes, il est ajouté uniquement au groupe d’appareils le mieux classé.
- Sélectionnez le groupe d’utilisateurs Azure AD qui doit avoir accès au groupe d’appareils.
- Classez le groupe d’appareils par rapport à d’autres groupes après sa création.

> [!NOTE]
> Un groupe d’appareils est accessible à tous les utilisateurs si vous ne lui affectez aucun groupe Azure AD.

## <a name="create-a-device-group"></a>Créer un groupe d'appareils

1. Dans le volet de navigation, sélectionnez **Paramètres Points** \> de **terminaison Autorisations** \>  \> Groupes **d’appareils**.

2. Cliquez sur **Ajouter un groupe d’appareils**.

3. Entrez le nom du groupe et les paramètres d’automatisation, puis spécifiez la règle de correspondance qui détermine les appareils qui appartiennent au groupe. Découvrez [comment l’enquête automatisée démarre](automated-investigations.md#how-the-automated-investigation-starts).

    > [!TIP]
    > Si vous souhaitez utiliser le balisage pour regrouper des appareils, consultez [Créer et gérer des balises d’appareil](machine-tags.md).

4. Affichez un aperçu de plusieurs appareils qui seront mis en correspondance par cette règle. Si vous êtes satisfait de la règle, cliquez sur **l’onglet Accès utilisateur** .

5. Affectez les groupes d’utilisateurs qui peuvent accéder au groupe d’appareils que vous avez créé.

    > [!NOTE]
    > Vous pouvez uniquement accorder l’accès aux groupes d’utilisateurs Azure AD qui ont été affectés à des rôles RBAC.

6. Cliquez sur **Fermer**. Les modifications de configuration sont appliquées.

## <a name="manage-device-groups"></a>Gérer les groupes d’appareils

Vous pouvez promouvoir ou rétrograder le rang d’un groupe d’appareils afin qu’il reçoit une priorité supérieure ou inférieure lors de la correspondance. Un groupe d’appareils avec le rang 1 est le groupe le plus élevé. Lorsqu’un appareil est mis en correspondance avec plusieurs groupes, il est ajouté uniquement au groupe le mieux classé. Vous pouvez également modifier et supprimer des groupes.

> [!WARNING]
> La suppression d’un groupe d’appareils peut affecter les règles de notification par e-mail. Si un groupe d’appareils est configuré sous une règle de notification par e-mail, il est supprimé de cette règle. Si le groupe d’appareils est le seul groupe configuré pour une notification par e-mail, cette règle de notification par e-mail est supprimée avec le groupe d’appareils.

Par défaut, les groupes d’appareils sont accessibles à tous les utilisateurs disposant d’un accès au portail. Vous pouvez modifier le comportement par défaut en affectant des groupes d’utilisateurs Azure AD au groupe d’appareils.

Les appareils qui ne correspondent à aucun groupe sont ajoutés au groupe d’appareils non groupés (par défaut). Vous ne pouvez pas modifier le rang de ce groupe ou le supprimer. Toutefois, vous pouvez modifier le niveau de correction de ce groupe et définir les groupes d’utilisateurs Azure AD qui peuvent accéder à ce groupe.

> [!NOTE]
> L’application des modifications à la configuration du groupe d’appareils peut prendre jusqu’à plusieurs minutes.

### <a name="add-device-group-definitions"></a>Ajouter des définitions de groupe d’appareils

Les définitions de groupe d’appareils peuvent également inclure plusieurs valeurs pour chaque condition. Vous pouvez définir plusieurs balises, noms d’appareils et domaines sur la définition d’un seul groupe d’appareils.

1. Créez un groupe d’appareils, puis sélectionnez **l’onglet Appareils** .
2. Ajoutez la première valeur pour l’une des conditions.
3. Sélectionnez `+` cette option pour ajouter d’autres lignes du même type de propriété.

> [!TIP]
> Utilisez l’opérateur « OR » entre les lignes du même type de condition, ce qui autorise plusieurs valeurs par propriété.
> Vous pouvez ajouter jusqu’à 10 lignes (valeurs) pour chaque type de propriété ( balise, nom d’appareil, domaine).

Pour plus d’informations sur la liaison aux définitions de groupes d’appareils, consultez [Groupes d’appareils - Sécurité Microsoft 365](https://sip.security.microsoft.com/homepage).

## <a name="related-topics"></a>Voir aussi

- [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md)
- [Créer et gérer des balises d’appareils](machine-tags.md)
- [Obtenir la liste des groupes d’appareils locataires à l’aide de API Graph](/graph/api/device-list-memberof)
