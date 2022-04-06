---
title: Balises d’entité Microsoft Defender pour l’identité dans Microsoft 365 Defender
description: Découvrez comment appliquer des balises d’entité d’identité Microsoft Defender dans Microsoft 365 Defender
ms.date: 06/08/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: c960f0cc1726155e733a0e88386fa7788cfc35e0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468058"
---
# <a name="defender-for-identity-entity-tags-in-microsoft-365-defender"></a>Balises d’entité Defender for Identity dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment appliquer des [balises d’entité d’identité Microsoft Defender](/defender-for-identity) [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender pour l’identité. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="entity-tags"></a>Balises d'entités

Dans Microsoft 365 Defender, vous pouvez définir trois types de balises d’entité Defender pour l’identité : les balises sensibles **, les** balises **Honeytoken** et les balises Exchange **serveur.**

Pour définir ces balises, dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, **Paramètres puis** **Identités**.

:::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités sous la colonne Nom dans la Paramètres page" lightbox="../../media/defender-identity/settings-identities.png":::

Les paramètres de balise s’affichent sous les **balises Entity**.

:::image type="content" source="../../media/defender-identity/tag-settings.png" alt-text="Volet Des balises d’entité" lightbox="../../media/defender-identity/tag-settings.png":::

Pour définir chaque type de balise, suivez les instructions ci-dessous.

## <a name="sensitive--tags"></a>Balises sensibles

La **balise Sensitive permet** d’identifier les ressources à valeur élevée. Le chemin de déplacement latéral s’appuie également sur l’état de sensibilité d’une entité. Certaines entités sont considérées comme sensibles automatiquement par Defender for Identity. Pour obtenir la liste de ces biens, voir [Entités sensibles](/defender-for-identity/manage-sensitive-honeytoken-accounts#sensitive-entities).

Vous pouvez également marquer manuellement les utilisateurs, les appareils ou les groupes comme sensibles.

1. Sélectionnez **Sensible**. Vous verrez ensuite les utilisateurs **, périphériques** et groupes sensibles **existants**.

   :::image type="content" source="../../media/defender-identity/sensitive-entities.png" alt-text="Onglet Appareils dans l’élément de menu Entités sensibles" lightbox="../../media/defender-identity/sensitive-entities.png":::

1. Sous chaque catégorie, **sélectionnez Balise...** pour baliser ce type d’entité. Par exemple, sous **Groupes**, sélectionnez **Groupes de balises.** Un volet s’ouvre avec les groupes que vous pouvez sélectionner pour baliser. Pour rechercher un groupe, entrez son nom dans la zone de recherche.

   :::image type="content" source="../../media/defender-identity/add-groups.png" alt-text="Option d’ajout d’un groupe" lightbox="../../media/defender-identity/add-groups.png":::

1. Sélectionnez votre groupe, puis cliquez sur **Ajouter une sélection.**

   :::image type="content" source="../../media/defender-identity/add-selection.png" alt-text="Option Ajouter une sélection" lightbox="../../media/defender-identity/add-selection.png":::

## <a name="honeytoken-tags"></a>Balises Honeytoken

Les entités honeytoken sont utilisées comme des captures pour les acteurs malveillants. Toute authentification associée à ces entités honeytoken déclenche une alerte.

Vous pouvez marquer des utilisateurs ou des appareils avec **la balise Honeytoken** de la même façon que vous balisez des comptes sensibles.

1. **Sélectionnez Honeytoken**. Vous verrez ensuite les utilisateurs et périphériques **honeytoken** **existants**.

    ![Entités Honeytoken.](../../media/defender-identity/honeytoken-entities.png)

1. Sous chaque catégorie, **sélectionnez Balise...** pour baliser ce type d’entité. Par exemple, sous **Utilisateurs**, sélectionnez **Utilisateurs de balise.** Un volet s’ouvre avec les groupes que vous pouvez sélectionner pour baliser. Pour rechercher un groupe, entrez son nom dans la zone de recherche.

   :::image type="content" source="../../media/defender-identity/add-users.png" alt-text="Option d’ajout d’utilisateurs" lightbox="../../media/defender-identity/add-users.png":::

1. Sélectionnez votre utilisateur, puis cliquez sur **Ajouter une sélection.**

   :::image type="content" source="../../media/defender-identity/add-selected-user.png" alt-text="Option d’ajout d’un utilisateur sélectionné" lightbox="../../media/defender-identity/add-selected-user.png":::

## <a name="exchange-server-tags"></a>Exchange balises de serveur

Defender pour l’identité considère Exchange serveurs comme des ressources à valeur élevée et les balise automatiquement comme **sensibles**. Vous pouvez également marquer manuellement les appareils comme Exchange serveurs.

1. **Sélectionnez Exchange serveur.** Vous verrez ensuite les appareils existants étiquetés avec la **balise Exchange serveur**.

   :::image type="content" source="../../media/defender-identity/exchange-servers.png" alt-text="L’Exchange de menu du serveur" lightbox="../../media/defender-identity/exchange-servers.png":::

1. Pour marquer un appareil comme un serveur Exchange, sélectionnez **Balises**.  Un volet s’ouvre avec les appareils que vous pouvez sélectionner pour baliser. Pour rechercher un appareil, entrez son nom dans la zone de recherche.

   :::image type="content" source="../../media/defender-identity/add-devices.png" alt-text="Option d’ajout d’un appareil" lightbox="../../media/defender-identity/add-devices.png":::

1. Sélectionnez votre appareil, puis cliquez sur **Ajouter une sélection.**

   :::image type="content" source="../../media/defender-identity/select-device.png" alt-text="Sélection d’un appareil" lightbox="../../media/defender-identity/select-device.png":::

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité De Defender pour l’identité](manage-security-alerts.md)
