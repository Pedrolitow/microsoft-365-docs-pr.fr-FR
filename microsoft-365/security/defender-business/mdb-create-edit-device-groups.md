---
title: Groupes d’appareils dans Microsoft Defender entreprise
description: En savoir plus sur les groupes d’appareils dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b13275a68a80cee52a756ef9b9464b5402749c27
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62464967"
---
# <a name="device-groups-in-microsoft-defender-for-business-preview"></a>Groupes d’appareils dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Dans Microsoft Defender pour Entreprises (prévisualisation), les stratégies sont appliquées aux appareils via certaines collections appelées groupes d’appareils. 

**Cet article décrit** :  

- [Quels sont les groupes d’appareils ?](#what-is-a-device-group)   
- [Comment créer des groupes d’appareils dans Defender for Business](#create-a-new-device-group)

## <a name="what-is-a-device-group"></a>Qu’est-ce qu’un groupe d’appareils ?

Un groupe d’appareils est un ensemble d’appareils regroupés en raison de certains critères spécifiés, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. Dans Microsoft Defender entreprise (prévisualisation), les stratégies sont appliquées aux appareils à l’aide de groupes d’appareils. 

Defender for Business (aperçu) inclut des groupes d’appareils par défaut que vous pouvez utiliser. Les groupes d’appareils par défaut incluent tous les appareils intégrés à Defender pour Entreprise (prévisualisation). Toutefois, vous pouvez également créer des groupes d’appareils pour affecter des stratégies avec des paramètres spécifiques à certains appareils. 

Tous les groupes d’appareils, y compris vos groupes d’appareils par défaut et tous les groupes d’appareils personnalisés que vous définissez, sont stockés dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Créer un groupe d’appareils

Actuellement, dans Defender pour Entreprises (prévisualisation), vous pouvez créer un groupe d’appareils pendant que vous êtes en train de créer ou de modifier une stratégie, comme décrit dans la procédure suivante : 

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. 

3. Prenez l’une des actions suivantes :

    1. Sélectionnez une stratégie existante, puis sélectionnez **Modifier**.
    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, voir Afficher ou modifier des stratégies [dans Microsoft Defender entreprise](mdb-view-edit-policies.md).

4. Dans **l’étape Informations générales** , examinez les informations, modifiez si nécessaire, puis choisissez **Suivant**.

5. Choisissez **+ Créer un groupe**. 

6. Spécifiez un nom et une description pour le groupe d’appareils, puis choisissez **Suivant**.

7. Sélectionnez les appareils à inclure dans le groupe, puis choisissez **Créer un groupe**.

8. À **l’étape Groupes d’appareils** , examinez la liste des groupes d’appareils pour la stratégie. Si nécessaire, supprimez un groupe de la liste. Sélectionnez **Suivant**.

9. Dans la page **Paramètres de configuration** , examinez et modifiez les paramètres selon vos besoins, puis choisissez **Suivant**. Pour plus d’informations sur ces paramètres, voir [Paramètres de configuration](mdb-next-gen-configuration-settings.md).

10. À **l’étape Examiner votre stratégie** , examinez tous les paramètres, a apporter les modifications nécessaires, puis choisissez Créer une **stratégie ou mettre** **à jour la stratégie**.

## <a name="next-steps"></a>Prochaines étapes

Choisissez une ou plusieurs des tâches suivantes :

- [Afficher ou modifier des stratégies](mdb-view-edit-policies.md)

- [Créer une stratégie](mdb-create-new-policy.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)