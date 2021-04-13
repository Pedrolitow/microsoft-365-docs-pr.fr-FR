---
title: Créer et gérer des groupes d’appareils dans Microsoft Defender ATP
description: Créer des groupes d’appareils et définir des niveaux de correction automatisés sur ces derniers en confint les règles qui s’appliquent au groupe
keywords: groupes d’appareils, groupes, correction, niveau, règles, groupe aad, rôle, attribuer, classement
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: dfc7c04bbde2b7061c92f5a25115b75a2f5b47b5
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066302"
---
# <a name="create-and-manage-device-groups"></a>Créer et gérer des groupes d’appareils

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Azure Active Directory
- Office 365

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Dans un scénario d’entreprise, un ensemble d’appareils est généralement affecté aux équipes chargées des opérations de sécurité. Ces appareils sont regroupés en fonction d’un ensemble d’attributs tels que leurs domaines, noms d’ordinateur ou balises désignées.

Dans Microsoft Defender for Endpoint, vous pouvez créer des groupes d’appareils et les utiliser pour :
- Limiter l’accès aux alertes et données associées à des groupes d’utilisateurs Azure AD spécifiques avec [des rôles RBAC attribués](rbac.md) 
- Configurer différents paramètres de correction automatique pour différents ensembles d’appareils
- Affecter des niveaux de correction spécifiques à appliquer lors d’examens automatisés
- Dans le cas d’un examen, filtrez la liste **Périphériques** sur des groupes d’appareils spécifiques à l’aide du **filtre** Groupe.

Vous pouvez créer des groupes d’appareils dans le contexte de l’accès basé sur les rôles (RBAC) pour contrôler qui peut prendre des mesures spécifiques ou voir les informations en attribuant le ou les groupes d’appareils à un groupe d’utilisateurs. Pour plus d’informations, voir [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur les rôles.](rbac.md)

>[!TIP]
> Pour une vue d’ensemble de l’application RBAC, lisez : votre SOC fonctionne-t-il [à plat avec RBAC](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Is-your-SOC-running-flat-with-limited-RBAC/ba-p/320015).

Dans le cadre du processus de création d’un groupe d’appareils, vous devez :
- Définissez le niveau de correction automatisé pour ce groupe. Pour plus d’informations sur les niveaux de correction, voir [Utiliser l’examen automatisé pour examiner et corriger les menaces.](automated-investigations.md)
- Spécifiez la règle correspondante qui détermine quel groupe d’appareils appartient au groupe en fonction du nom de l’appareil, du domaine, des balises et de la plateforme du système d’exploitation. Si un appareil est également en correspondance avec d’autres groupes, il est ajouté uniquement au groupe d’appareils le plus élevé.
- Sélectionnez le groupe d’utilisateurs Azure AD qui doit avoir accès au groupe d’appareils.
- Classer le groupe d’appareils par rapport aux autres groupes après sa création.

>[!NOTE]
>Un groupe d’appareils est accessible à tous les utilisateurs si vous n’y affectez aucun groupe Azure AD.

## <a name="create-a-device-group"></a>Créer un groupe d’appareils

1. Dans le volet de navigation, sélectionnez **Groupes d’appareils**  >  **Paramètres.**

2. Cliquez **sur Ajouter un groupe d’appareils.**

3. Entrez le nom du groupe et les paramètres d’automatisation et spécifiez la règle correspondante qui détermine quels appareils appartiennent au groupe. Découvrez [comment l’enquête automatisée démarre.](automated-investigations.md#how-the-automated-investigation-starts)

    >[!TIP]
    >Si vous souhaitez grouper des appareils par unité d’organisation, vous pouvez configurer la clé de Registre pour l’affiliation au groupe. Pour plus d’informations sur le marquage des appareils, voir [Créer et gérer des balises d’appareil.](machine-tags.md)

4. Affichez un aperçu de plusieurs appareils qui seront en correspondance avec cette règle. Si vous êtes satisfait de la règle, cliquez sur **l’onglet Accès** utilisateur.

5. Affectez les groupes d’utilisateurs qui peuvent accéder au groupe d’appareils que vous avez créé.

    >[!NOTE]
    >Vous pouvez uniquement accorder l’accès aux groupes d’utilisateurs Azure AD affectés à des rôles RBAC.

6. Cliquez sur **Fermer**. Les modifications de configuration sont appliquées.

## <a name="manage-device-groups"></a>Gérer les groupes d’appareils

Vous pouvez promouvoir ou rétrograder le rang d’un groupe d’appareils afin qu’il soit prioritaire ou inférieur lors de la mise en correspondance. Lorsqu’un appareil est en correspondance avec plusieurs groupes, il est ajouté uniquement au groupe le plus élevé. Vous pouvez également modifier et supprimer des groupes.

>[!WARNING]
>La suppression d’un groupe d’appareils peut affecter les règles de notification par courrier électronique. Si un groupe d’appareils est configuré sous une règle de notification par courrier électronique, il sera supprimé de cette règle. Si le groupe d’appareils est le seul groupe configuré pour une notification par courrier électronique, cette règle de notification par courrier électronique est supprimée avec le groupe d’appareils.

Par défaut, les groupes d’appareils sont accessibles à tous les utilisateurs ayant accès au portail. Vous pouvez modifier le comportement par défaut en attribuant des groupes d’utilisateurs Azure AD au groupe d’appareils.

Les appareils qui ne correspondent à aucun groupe sont ajoutés au groupe Appareils non regroupés (par défaut). Vous ne pouvez pas modifier le rang de ce groupe ou le supprimer. Toutefois, vous pouvez modifier le niveau de correction de ce groupe et définir les groupes d’utilisateurs Azure AD qui peuvent accéder à ce groupe.

>[!NOTE]
> L’application de modifications à la configuration du groupe d’appareils peut prendre jusqu’à plusieurs minutes.

## <a name="related-topics"></a>Voir aussi

- [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur un rôle](rbac.md)
- [Créer et gérer des balises d’appareil](machine-tags.md)
- [Obtenir la liste des groupes d’appareils client à l’aide de l’API Graph](https://docs.microsoft.com/graph/api/device-list-memberof)