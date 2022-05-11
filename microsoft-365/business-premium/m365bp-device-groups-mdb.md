---
title: Utilisation de groupes d’appareils dans Microsoft 365 Business Premium
description: En savoir plus sur les groupes d’appareils dans Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/16/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2c218cd2b0f04201f46155a72a916cc7676aaddb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320815"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Groupes d’appareils dans Microsoft 365 Business Premium

Microsoft 365 Business Premium comprend une protection des points de terminaison grâce à Microsoft Defender pour les PME. Les stratégies de protection des appareils sont appliquées aux appareils via certains regroupements appelés groupes d’appareils. 

**Ce guide décrit**:  

- [Ce que sont les groupes d’appareils](#whats-a-device-group)
- [Comment créer un nouveau groupe d’appareils](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Qu’est-ce qu’un groupe d’appareils ?

Un groupe d’appareils est une collection d’appareils qui sont regroupés en raison de certains critères spécifiés, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 

Avec votre abonnement, vous disposez de groupes d’appareils par défaut que vous pouvez utiliser. Les groupes d’appareils par défaut incluent tous les appareils intégrés à Microsoft Defender pour les PME. Toutefois, vous pouvez également créer des groupes d’appareils pour affecter des stratégies de protection des appareils avec des paramètres spécifiques à certains appareils. 

Tous les groupes d’appareils, y compris vos groupes d’appareils par défaut et tous les groupes d’appareils personnalisés que vous définissez, sont stockés dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Comment créer un nouveau groupe d’appareils ?

Vous pouvez créer un groupe d’appareils pendant que vous êtes en train de créer ou de modifier une stratégie de protection des appareils. 

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. 

3. Effectuez l’une des opérations suivantes :

    1. Sélectionnez une stratégie existante, puis choisissez **Modifier**.
    
    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, consultez [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](m365bp-view-edit-create-mdb-policies.md).

4. Dans l’étape **Informations générales** , passez en revue les informations, modifiez-les si nécessaire, puis choisissez **Suivant**.

5. Choisissez **+ Créer un nouveau groupe**. 

6. Spécifiez un nom et une description pour le groupe d’appareils, puis choisissez **Suivant**.

7. Sélectionnez les appareils à inclure dans le groupe, puis choisissez **Créer un groupe**.

8. À l’étape **Groupes d’appareils**, passez en revue la liste des groupes d’appareils pour la stratégie. Si nécessaire, supprimez un groupe de la liste. Sélectionnez **Suivant**.

9. Dans la page **Paramètres de configuration** , passez en revue et modifiez les paramètres en fonction des besoins, puis choisissez **Suivant**. Pour plus d’informations sur ces paramètres, consultez [Comprendre les paramètres de configuration de nouvelle génération dans Microsoft Defender pour les PME](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. Dans le **Passez en revue votre stratégie** étape, passez en revue tous les paramètres, apportez les modifications nécessaires, puis choisissez **Créer une stratégie** ou **Mettre à jour la stratégie**.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez terminé vos missions principales, configurez vos [équipes de réponse ](m365bp-security-incident-management.md) et [gérez votre environnement](m365bp-maintain-environment.md).

