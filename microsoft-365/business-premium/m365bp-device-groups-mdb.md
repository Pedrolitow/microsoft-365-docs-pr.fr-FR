---
title: Utiliser des groupes d’appareils dans Microsoft 365 Business Premium
description: En savoir plus sur les groupes d’appareils Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2cc874580dad24e1b3d5349d6075956a9e518704
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634644"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Groupes d’appareils dans Microsoft 365 Business Premium

Microsoft 365 Business Premium la protection des points de terminaison via Microsoft Defender pour les PME. Les stratégies de protection des appareils sont appliquées aux appareils via certaines collections appelées groupes d’appareils. 

**Cet article décrit** :  

- [Quels sont les groupes d’appareils ?](#whats-a-device-group)
- [Comment créer un groupe d’appareils](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Qu’est-ce qu’un groupe d’appareils ?

Un groupe d’appareils est un ensemble d’appareils regroupés en raison de certains critères spécifiés, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 

Avec votre abonnement, vous avez des groupes d’appareils par défaut que vous pouvez utiliser. Les groupes d’appareils par défaut incluent tous les appareils intégrés à Defender for Business. Toutefois, vous pouvez également créer des groupes d’appareils pour affecter des stratégies de protection des appareils avec des paramètres spécifiques à certains appareils. 

Tous les groupes d’appareils, y compris vos groupes d’appareils par défaut et tous les groupes d’appareils personnalisés que vous définissez, sont stockés dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Comment faire créer un groupe d’appareils ?

Vous pouvez créer un groupe d’appareils pendant que vous êtes en train de créer ou de modifier une stratégie de protection des appareils. 

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. 

3. Prenez l’une des actions suivantes :

    1. Sélectionnez une stratégie existante, puis sélectionnez **Modifier**.
    
    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, voir Afficher ou modifier des [stratégies dans Microsoft Defender pour les PME](m365bp-view-edit-create-mdb-policies.md).

4. Dans **l’étape Informations générales** , examinez les informations, modifiez si nécessaire, puis choisissez **Suivant**.

5. Choisissez **+ Créer un groupe**. 

6. Spécifiez un nom et une description pour le groupe d’appareils, puis choisissez **Suivant**.

7. Sélectionnez les appareils à inclure dans le groupe, puis choisissez **Créer un groupe**.

8. À **l’étape Groupes d’appareils** , examinez la liste des groupes d’appareils pour la stratégie. Si nécessaire, supprimez un groupe de la liste. Sélectionnez **Suivant**.

9. Dans la page **Paramètres de configuration** , examinez et modifiez les paramètres selon vos besoins, puis choisissez **Suivant**. Pour plus d’informations sur ces paramètres, voir [Comprendre les paramètres de configuration nouvelle génération dans Microsoft Defender pour les PME](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. À **l’étape Examiner votre stratégie** , examinez tous les paramètres, a apporter les modifications nécessaires, puis choisissez Créer une **stratégie ou mettre** **à jour la stratégie**.


