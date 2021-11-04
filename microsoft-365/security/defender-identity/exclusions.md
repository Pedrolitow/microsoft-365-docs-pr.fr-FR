---
title: Microsoft Defender pour les exclusions de détection d’identité dans Microsoft 365 Defender
description: Découvrez comment configurer Microsoft Defender pour les exclusions de détection d’identité dans Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.openlocfilehash: d4a8fb5cb8677acaf574eb25df6e8e32720e4628
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60787802"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender-preview"></a>Configurer Defender pour les exclusions de détection d’identité dans Microsoft 365 Defender (aperçu)

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer Microsoft Defender pour les exclusions de détection [d’identité](/defender-for-identity) [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender for Identity. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

[!INCLUDE [Product long](includes/product-long.md)] permet l’exclusion d’adresses IP, d’ordinateurs, de domaines ou d’utilisateurs spécifiques d’un certain nombre de détections.

Par exemple, une alerte **de reconnaissance DNS** peut être déclenchée par un scanneur de sécurité qui utilise DNS comme mécanisme d’analyse. La création d’une exclusion permet à Defender for Identity d’ignorer ces scanneurs et de réduire les faux positifs.

>[!NOTE]
>Parmi les domaines les plus courants avec une communication suspecte sur les alertes [DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) ouvertes sur ces domaines, nous avons observé les domaines les plus exclus de l’alerte par les clients. Ces domaines sont ajoutés à la liste d’exclusions par défaut, mais vous avez la possibilité de les supprimer facilement.

## <a name="how-to-add-detection-exclusions"></a>Comment ajouter des exclusions de détection

1. In [Microsoft 365 Defender](https://security.microsoft.com/), go to **Paramètres** and then **Identities**.

    ![Go to Paramètres, then Identities.](../../media/defender-identity/settings-identities.png)

1. Vous verrez ensuite les **entités exclues** dans le menu de gauche.

    ![Entités exclues.](../../media/defender-identity/excluded-entities.png)

Vous pouvez ensuite définir des exclusions par deux méthodes : **exclusions par** règle de détection et entités **exclues globales**.

## <a name="exclusions-by-detection-rule"></a>Exclusions par règle de détection

1. Dans le menu de gauche, sélectionnez **Exclusions par règle de détection.** Vous verrez une liste de règles de détection.

    ![Exclusions par règle de détection.](../../media/defender-identity/exclusions-by-detection-rule.png)

1. Pour chaque détection que vous souhaitez configurer, vous devez suivre les étapes suivantes :

    1. Sélectionnez la règle. Vous pouvez rechercher des détections à l’aide de la barre de recherche. Une fois sélectionné, un volet s’ouvre avec les détails de la règle de détection.

        ![Détails de la règle de détection.](../../media/defender-identity/detection-rule-details.png)

    1. Pour ajouter une exclusion, sélectionnez le bouton **Entités exclues,** puis choisissez le type d’exclusion. Différentes entités exclues sont disponibles pour chaque règle. Elles incluent les utilisateurs, les appareils, les domaines et les adresses IP. Dans cet exemple, les choix possibles sont **Exclure des appareils** et **Exclure des adresses IP.**

        ![Exclure les appareils ou les adresses IP.](../../media/defender-identity/exclude-devices-or-ip-addresses.png)

    1. Après avoir choisi le type d’exclusion, vous pouvez ajouter l’exclusion. Dans le volet qui s’ouvre, sélectionnez le **+** bouton pour ajouter l’exclusion.

        ![Ajoutez une exclusion.](../../media/defender-identity/add-exclusion.png)

    1. Ajoutez ensuite l’entité à exclure. Sélectionnez **+ Ajouter** pour ajouter l’entité à la liste.

        ![Ajoutez une entité à exclure.](../../media/defender-identity/add-excluded-entity.png)

    1. Sélectionnez **Ensuite Exclure les adresses IP** (dans cet exemple) pour terminer l’exclusion.

        ![Exclure les adresses IP.](../../media/defender-identity/exclude-ip-addresses.png)

    1. Une fois que vous avez ajouté des exclusions, vous pouvez exporter la liste ou supprimer les exclusions en revenant au bouton **Entités exclues.** Dans cet exemple, nous avons renvoyé à **Exclure les appareils**. Pour exporter la liste, sélectionnez la flèche vers le bas.

        ![Revenir à Exclure les appareils.](../../media/defender-identity/return-to-exclude-devices.png)

    1. Pour supprimer une exclusion, sélectionnez-la et sélectionnez l’icône corbeille.

        ![Supprimez une exclusion.](../../media/defender-identity/delete-exclusion.png)

## <a name="global-excluded-entities"></a>Entités exclues globales

Vous pouvez désormais également configurer des exclusions par des entités **exclues globales.** Les exclusions globales vous permettent de définir certaines entités (adresses IP, sous-réseaux, périphériques ou domaines) à exclure de toutes les détections de Defender for Identity. Par exemple, si vous excluez un appareil, il s’applique uniquement aux détections qui ont une identification d’appareil dans le cadre de la détection.

1. Dans le menu de gauche, sélectionnez **Entités exclues globales.** Vous verrez les catégories d’entités que vous pouvez exclure.

    ![Entités exclues globales.](../../media/defender-identity/global-excluded-entities.png)

1. Choisissez un type d’exclusion. Dans cet exemple, nous avons sélectionné **Exclure des domaines.**

    ![Exclure des domaines.](../../media/defender-identity/exclude-domains.png)

1. Un volet s’ouvre et vous permet d’ajouter un domaine à exclure. Ajoutez le domaine que vous souhaitez exclure.

    ![Ajoutez un domaine à exclure.](../../media/defender-identity/add-excluded-domain.png)

1. Le domaine est ajouté à la liste. Sélectionnez **Exclure des domaines** pour terminer l’exclusion.

    ![Sélectionnez Exclure des domaines.](../../media/defender-identity/select-exclude-domains.png)

1. Vous verrez ensuite le domaine dans la liste des entités à exclure de toutes les règles de détection. Vous pouvez exporter la liste ou supprimer les entités en les sélectionnant et en cliquant sur **le bouton** Supprimer.

    ![Liste des entrées exclues globales.](../../media/defender-identity/global-excluded-entries-list.png)

## <a name="see-also"></a>Articles associés

- [Gérer les alertes de sécurité De Defender pour l’identité](manage-security-alerts.md)
