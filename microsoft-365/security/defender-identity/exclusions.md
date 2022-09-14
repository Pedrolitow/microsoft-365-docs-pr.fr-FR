---
title: Microsoft Defender pour Identity exclusions de détection dans Microsoft 365 Defender
description: Découvrez comment configurer des exclusions de détection Microsoft Defender pour Identity dans Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 66b9de2b9ab8d1a6026647f527495ed2f178fd58
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67682644"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Configurer les exclusions de détection Defender pour Identity dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer [Microsoft Defender pour Identity](/defender-for-identity) exclusions de détection dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé à partir de leur emplacement dans le portail Defender pour Identity. Lisez les détails ci-dessous pour découvrir où trouver les fonctionnalités familières et nouvelles.

[!INCLUDE [Product long](includes/product-long.md)] permet d’exclure des adresses IP, des ordinateurs, des domaines ou des utilisateurs spécifiques d’un certain nombre de détections.

Par exemple, une alerte **de reconnaissance DNS** peut être déclenchée par un scanneur de sécurité qui utilise DNS comme mécanisme d’analyse. La création d’une exclusion permet à Defender pour Identity d’ignorer ces scanneurs et de réduire les faux positifs.

>[!NOTE]
>Parmi les domaines les plus courants avec [une communication suspecte sur les alertes DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) ouvertes sur eux, nous avons observé les domaines que les clients ont le plus exclus de l’alerte. Ces domaines sont ajoutés à la liste d’exclusions par défaut, mais vous avez la possibilité de les supprimer facilement.

## <a name="how-to-add-detection-exclusions"></a>Ajout d’exclusions de détection

1. Dans [Microsoft 365 Defender](https://security.microsoft.com/), accédez aux **paramètres**, puis **aux identités**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la colonne Nom" lightbox="../../media/defender-identity/settings-identities.png":::

1. Vous verrez ensuite **les entités exclues** dans le menu de gauche.

   :::image type="content" source="../../media/defender-identity/excluded-entities.png" alt-text="Volet Entités exclues" lightbox="../../media/defender-identity/excluded-entities.png":::

Vous pouvez ensuite définir des exclusions par deux méthodes : **exclusions par règle de détection** et **entités globales exclues**.

## <a name="exclusions-by-detection-rule"></a>Exclusions par règle de détection

1. Dans le menu de gauche, sélectionnez **Exclusions par règle de détection**. Vous verrez une liste de règles de détection.

   :::image type="content" source="../../media/defender-identity/exclusions-by-detection-rule.png" alt-text="Option Exclusions par règle de détection dans l’élément Entités exclues dans le volet gauche" lightbox="../../media/defender-identity/exclusions-by-detection-rule.png":::

1. Pour chaque détection que vous souhaitez configurer, procédez comme suit :

    1. Sélectionnez la règle. Vous pouvez rechercher des détections à l’aide de la barre de recherche. Une fois sélectionné, un volet s’ouvre avec les détails de la règle de détection.

       :::image type="content" source="../../media/defender-identity/detection-rule-details.png" alt-text="Détails d’une règle de détection" lightbox="../../media/defender-identity/detection-rule-details.png":::

    1. Pour ajouter une exclusion, sélectionnez le bouton **Entités exclues** , puis choisissez le type d’exclusion. Différentes entités exclues sont disponibles pour chaque règle. Elles incluent les utilisateurs, les appareils, les domaines et les adresses IP. Dans cet exemple, les choix sont **Exclure les appareils** et **Exclure les adresses IP**.

       :::image type="content" source="../../media/defender-identity/exclude-devices-or-ip-addresses.png" alt-text="Option permettant d’exclure des appareils ou des adresses IP" lightbox="../../media/defender-identity/exclude-devices-or-ip-addresses.png":::

    1. Après avoir choisi le type d’exclusion, vous pouvez l’ajouter. Dans le volet qui s’ouvre, sélectionnez le **+** bouton pour ajouter l’exclusion.

       :::image type="content" source="../../media/defender-identity/add-exclusion.png" alt-text="Option permettant d’ajouter une exclusion" lightbox="../../media/defender-identity/add-exclusion.png":::

    1. Ajoutez ensuite l’entité à exclure. Sélectionnez **+ Ajouter** pour ajouter l’entité à la liste.

       :::image type="content" source="../../media/defender-identity/add-excluded-entity.png" alt-text="Option permettant d’ajouter une entité à exclure" lightbox="../../media/defender-identity/add-excluded-entity.png":::

    1. Sélectionnez Ensuite **Exclure les adresses IP** (dans cet exemple) pour terminer l’exclusion.

       :::image type="content" source="../../media/defender-identity/exclude-ip-addresses.png" alt-text="Option permettant d’exclure les adresses IP" lightbox="../../media/defender-identity/exclude-ip-addresses.png":::

    1. Une fois que vous avez ajouté des exclusions, vous pouvez exporter la liste ou supprimer les exclusions en retournant au bouton **Entités exclues** . Dans cet exemple, nous sommes retournés à **Exclure les appareils**. Pour exporter la liste, sélectionnez le bouton flèche vers le bas.

       :::image type="content" source="../../media/defender-identity/return-to-exclude-devices.png" alt-text="Option Retour à l’exclusion des appareils" lightbox="../../media/defender-identity/return-to-exclude-devices.png":::

    1. Pour supprimer une exclusion, sélectionnez l’exclusion et sélectionnez l’icône corbeille.

       :::image type="content" source="../../media/defender-identity/delete-exclusion.png" alt-text="Option Supprimer une exclusion" lightbox="../../media/defender-identity/delete-exclusion.png":::

## <a name="global-excluded-entities"></a>Entités globales exclues

Vous pouvez désormais également configurer des exclusions par **des entités globales exclues**. Les exclusions globales vous permettent de définir certaines entités (adresses IP, sous-réseaux, appareils ou domaines) à exclure de toutes les détections dont Dispose Defender pour Identity. Par exemple, si vous excluez un appareil, il s’applique uniquement aux détections qui ont l’identification de l’appareil dans le cadre de la détection.

1. Dans le menu de gauche, sélectionnez **Entités globales exclues**. Vous verrez les catégories d’entités que vous pouvez exclure.

   :::image type="content" source="../../media/defender-identity/global-excluded-entities.png" alt-text="Élément de sous-menu Entités exclues globales" lightbox="../../media/defender-identity/global-excluded-entities.png":::

1. Choisissez un type d’exclusion. Dans cet exemple, nous avons sélectionné **Exclure des domaines**.

   :::image type="content" source="../../media/defender-identity/exclude-domains.png" alt-text="Onglet Domaines" lightbox="../../media/defender-identity/exclude-domains.png":::

1. Un volet s’ouvre dans lequel vous pouvez ajouter un domaine à exclure. Ajoutez le domaine à exclure.

   :::image type="content" source="../../media/defender-identity/add-excluded-domain.png" alt-text="Option d’ajout d’un domaine à exclure" lightbox="../../media/defender-identity/add-excluded-domain.png":::

1. Le domaine est ajouté à la liste. Sélectionnez **Exclure des domaines** pour terminer l’exclusion.

   :::image type="content" source="../../media/defender-identity/select-exclude-domains.png" alt-text="Option permettant de sélectionner des domaines à exclure" lightbox="../../media/defender-identity/select-exclude-domains.png":::

1. Vous verrez ensuite le domaine dans la liste des entités à exclure de toutes les règles de détection. Vous pouvez exporter la liste ou supprimer les entités en les sélectionnant et en cliquant sur le bouton **Supprimer** .

   :::image type="content" source="../../media/defender-identity/global-excluded-entries-list.png" alt-text="Liste des entrées globales exclues" lightbox="../../media/defender-identity/global-excluded-entries-list.png":::

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité Defender pour Identity](manage-security-alerts.md)
