---
title: Groupes d’appareils dans Microsoft Defender pour entreprises
description: Les stratégies de sécurité sont appliquées aux appareils par le biais de groupes d’appareils dans Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
ms.date: 07/19/2022
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: 178130ff301f1874b5ebeafdeb6ccb62203519c8
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68098189"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Groupes d’appareils dans Microsoft Defender pour entreprises

Dans Defender entreprise, les stratégies sont appliquées aux appareils par le biais de certaines collections appelées groupes d’appareils. 

**Cet article décrit**:  

- [Ce que sont les groupes d’appareils](#what-is-a-device-group)   
- [Comment créer des groupes d’appareils dans Defender pour Entreprises](#create-a-new-device-group)
- [Comment afficher un groupe d’appareils existant](#view-an-existing-device-group)
- [Ce que fait l’option Ajouter tous les appareils](#what-does-the-add-all-devices-option-do)


## <a name="what-is-a-device-group"></a>Qu’est-ce qu’un groupe d’appareils ?

Un groupe de périphériques est une collection de périphériques qui sont regroupés en raison de certains critères spécifiques, tels que la version du système d'exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. Dans Defender entreprise, les stratégies sont appliquées aux appareils à l’aide de groupes d’appareils.

Defender entreprise inclut des groupes d’appareils par défaut que vous pouvez utiliser. Les groupes d’appareils par défaut incluent tous les appareils intégrés à Microsoft Defender pour les PME. Par exemple, il existe un groupe d’appareils par défaut pour les appareils Windows. Chaque fois que vous intègrez des appareils Windows, ils sont automatiquement ajoutés au groupe d’appareils par défaut.

Vous pouvez également créer des groupes d’appareils pour affecter des stratégies avec des paramètres spécifiques à certains appareils. Par exemple, vous pouvez avoir une stratégie de pare-feu affectée à un ensemble d’appareils Windows et une autre stratégie de pare-feu affectée à un autre ensemble d’appareils Windows. Vous pouvez définir des groupes d’appareils spécifiques à utiliser avec vos stratégies.

> [!NOTE]
> Lorsque vous créez des stratégies dans Defender entreprise, un ordre de priorité est attribué. Si vous appliquez plusieurs stratégies à un ensemble donné d’appareils, ces appareils recevront la première stratégie appliquée uniquement. Pour plus d’informations, consultez [Comprendre l’ordre des stratégies dans Defender entreprise](mdb-policy-order.md).

Tous les groupes d’appareils, y compris vos groupes d’appareils par défaut et tous les groupes d’appareils personnalisés que vous définissez, sont stockés dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Créer un groupe d’appareils

Actuellement, dans Defender Entreprise, vous pouvez créer un groupe d’appareils pendant que vous êtes en train de créer ou de modifier une stratégie, comme décrit dans la procédure suivante : 

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. 

3. Effectuez l’une des opérations suivantes :

    1. Sélectionnez une stratégie existante, puis choisissez **Modifier**.
    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, consultez [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-policies.md).

4. Dans l’étape **Informations générales** , passez en revue les informations, modifiez-les si nécessaire, puis choisissez **Suivant**.

5. Choisissez **+ Créer un nouveau groupe**. 

6. Spécifiez un nom et une description pour le groupe d’appareils, puis choisissez **Suivant**.

7. Sélectionnez les appareils à inclure dans le groupe, puis choisissez **Créer un groupe**.

8. À l’étape **Groupes d’appareils**, passez en revue la liste des groupes d’appareils pour la stratégie. Si nécessaire, supprimez un groupe de la liste. Sélectionnez **Suivant**.

9. Dans la page **Paramètres de configuration** , passez en revue et modifiez les paramètres en fonction des besoins, puis choisissez **Suivant**. Pour plus d’informations sur ces paramètres, consultez [Paramètres de configuration](mdb-next-gen-configuration-settings.md).

10. Dans le **Passez en revue votre stratégie** étape, passez en revue tous les paramètres, apportez les modifications nécessaires, puis choisissez **Créer une stratégie** ou **Mettre à jour la stratégie**.

## <a name="view-an-existing-device-group"></a>Afficher un groupe d’appareils existant

Actuellement, dans Defender entreprise, vous pouvez afficher vos groupes d’appareils existants pendant que vous êtes en train de créer ou de modifier une stratégie, comme décrit dans la procédure suivante : 

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. 

3. Effectuez l’une des opérations suivantes :

    1. Sélectionnez une stratégie existante, puis choisissez **Modifier**.
    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, consultez [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-policies.md).

4. Dans l’étape **Informations générales** , passez en revue les informations, modifiez-les si nécessaire, puis choisissez **Suivant**.

5. Choisissez **Utiliser un groupe existant**. Un menu volant s’ouvre et affiche les groupes d’appareils. Si vous n’avez pas encore de groupes d’appareils, vous êtes invité à créer un groupe d’appareils.

## <a name="what-does-the-add-all-devices-option-do"></a>Que fait l’option Ajouter tous les appareils ?

Lorsque vous créez ou modifiez une stratégie, vous pouvez voir l’option **Ajouter tous les appareils** .

:::image type="content" source="media/add-all-devices-option.png" alt-text="Capture d’écran de l’option Ajouter tous les appareils.":::

Si vous sélectionnez cette option, tous les appareils inscrits dans Microsoft Intune recevront la stratégie que vous créez ou modifiez par défaut. 

## <a name="next-steps"></a>Prochaines étapes

Choisissez une ou plusieurs des tâches suivantes :

- [Afficher ou modifier des stratégies](mdb-view-edit-policies.md)
- [Créer une stratégie](mdb-create-new-policy.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)