---
title: Utilisation de groupes d’appareils dans Microsoft 365 Business Premium
description: Découvrez les groupes d’appareils et comment appliquer des stratégies avec Intune dans Microsoft 365 Business Premium et renforcer la protection contre les cyberattaques.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e53a2fcaf7420e8581ea310a5d73dada8be3d7c0
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67737541"
---
# <a name="device-groups-and-categories-in-microsoft-365-business-premium"></a>Groupes et catégories d’appareils dans Microsoft 365 Business Premium

Microsoft 365 Business Premium inclut la protection des points de terminaison via Microsoft Defender pour les PME et Microsoft Intune. Les stratégies de protection des appareils sont appliquées aux appareils via certains regroupements appelés groupes d’appareils. Dans Intune, les appareils sont regroupés en catégories d’appareils comme une façon différente de les organiser. 

Le présent article contient les sections suivantes :  

- [Utilisation de groupes d’appareils](#working-with-device-groups)
- [Comment créer un nouveau groupe d’appareils](#create-a-device-group-in-the-microsoft-365-defender-portal)
- [Comment créer une catégorie d’appareils dans Intune](#create-a-device-category-in-intune)

## <a name="working-with-device-groups"></a>Utilisation de groupes d’appareils

Un groupe d’appareils est une collection d’appareils qui sont regroupés en raison de certains critères spécifiés, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez.

Avec Microsoft 365 Business Premium, vous disposez de groupes d’appareils par défaut que vous pouvez utiliser. Les groupes d’appareils par défaut incluent tous les appareils intégrés à Microsoft Defender pour les PME. Toutefois, vous pouvez également créer des groupes d’appareils pour affecter des stratégies de protection des appareils avec des paramètres spécifiques à certains appareils.

Tous les groupes d’appareils, y compris vos groupes d’appareils par défaut et tous les groupes d’appareils personnalisés que vous définissez, sont stockés dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-device-group-in-the-microsoft-365-defender-portal"></a>Créer un groupe d’appareils dans le portail Microsoft 365 Defender

Vous pouvez créer un groupe d’appareils pendant que vous êtes en train de créer ou de modifier une stratégie de protection des appareils.

1. Accédez au [Portail Microsoft 365 Defender](https://security.microsoft.com) et connectez-vous.

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**.

3. Effectuez l’une des opérations suivantes :

    1. Sélectionnez une stratégie existante, puis choisissez **Modifier**.

    2. Choisissez **+ Ajouter** pour créer une stratégie.

    > [!TIP]
    > Pour obtenir de l’aide sur la création ou la modification d’une stratégie, consultez [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](m365bp-view-edit-create-mdb-policies.md).

4. Dans l’étape **Informations générales** , passez en revue les informations, modifiez-les si nécessaire, puis choisissez **Suivant**.

5. Choisissez **Créer un groupe**.

6. Spécifiez un nom et une description pour le groupe d’appareils, puis choisissez **Suivant**.

7. Sélectionnez les appareils à inclure dans le groupe, puis choisissez **Créer un groupe**.

8. À l’étape **Groupes d’appareils**, passez en revue la liste des groupes d’appareils pour la stratégie. Si nécessaire, supprimez un groupe de la liste. Sélectionnez **Suivant**.

9. Dans la page **Paramètres de configuration** , passez en revue et modifiez les paramètres en fonction des besoins, puis choisissez **Suivant**. Pour plus d’informations sur ces paramètres, consultez [Comprendre les paramètres de configuration de nouvelle génération dans Microsoft Defender pour les PME](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. Dans le **Passez en revue votre stratégie** étape, passez en revue tous les paramètres, apportez les modifications nécessaires, puis choisissez **Créer une stratégie** ou **Mettre à jour la stratégie**.

## <a name="create-a-device-category-in-intune"></a>Créer une catégorie d’appareil dans Intune

Créez des catégories d’appareils dans Intune à partir desquelles les utilisateurs doivent choisir quand ils inscrivent un appareil.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com).

2. Choisissez **Appareils** > **Catégories d’appareils** > **Créer une catégorie d’appareil** pour ajouter une nouvelle catégorie.

3. Dans le volet **Créer une catégorie d’appareil**, entrez un nom pour la nouvelle catégorie et une description facultative.

4. Lorsque vous avez terminé, sélectionnez **Créer**. Vous pouvez voir la nouvelle catégorie dans la liste.

Utilisez le nom de catégorie d’appareil lorsque vous créez les groupes de sécurité Azure Active Directory (Azure AD). Lorsque les utilisateurs inscrivent leurs appareils, ils reçoivent une liste des catégories que vous avez configurées dans Intune. Une fois qu’ils ont choisi une catégorie et terminé l’inscription, leur appareil est ajouté au groupe de sécurité Active Directory qui lui est associé.

## <a name="create-dynamic-device-groups-in-azure-active-directory"></a>Créer des groupes d’appareils dynamiques dans Azure Active Directory

Vous pouvez également accéder au portail Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) à partir du centre d’administration Microsoft 365. Dans le centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com/)), choisissez **Tous les centres d’administration**, puis **choisissez Azure Active Directory**.

Dans le portail Azure AD, vous pouvez créer des groupes dynamiques en fonction de la catégorie d’appareil et du nom de catégorie d’appareil. Utilisez des règles de groupe dynamique pour ajouter et supprimer automatiquement des appareils. Si les attributs d’un appareil changent, le système examine vos règles de groupe dynamique pour le répertoire pour voir si l’appareil répond aux exigences de règle (est ajouté) ou ne répond plus aux exigences des règles (est supprimé).

Vous pouvez créer un groupe dynamique pour les appareils ou les utilisateurs, mais pas pour les deux. Vous ne pouvez pas non plus créer un groupe d’appareils en fonction des attributs des propriétaires d’appareils. Les règles d’appartenance d’appareil peuvent uniquement référencer des attributions d’appareils. 

## <a name="after-device-groups-are-created"></a>Une fois les groupes d’appareils créés

Maintenant que les catégories et les groupes d’appareils sont établis, les utilisateurs d’appareils iOS et Android inscrivent leurs appareils et, dans ce cas, ils doivent choisir une catégorie dans la liste des catégories qui ont été configurées. Les utilisateurs de Windows peuvent utiliser le site web Portail d'entreprise ou l’application Portail d'entreprise pour sélectionner une catégorie.

1. Après avoir inscrit l’appareil, accédez au [portail d’entreprise](https://portal.microsoft.com) et choisissez **Mes appareils**.

2. Sélectionnez l’appareil inscrit dans la liste, puis sélectionnez une catégorie.

Après avoir choisi une catégorie, l’appareil est automatiquement ajouté au groupe correspondant. Si un appareil est déjà inscrit avant que vous ne configuriez des catégories, l’utilisateur voit une notification concernant l’appareil sur le site web Portail d’entreprise. Elle l’invite à sélectionner une catégorie la prochaine fois qu’il accédera à l’application Portail d’entreprise sur iOS/iPadOS ou Android.

> [!NOTE]
> - Vous pouvez modifier une catégorie d’appareil dans le portail Azure, mais vous devez manuellement mettre à jour tous les groupes de sécurité Azure AD qui référencent cette catégorie.
> - Si vous supprimez une catégorie, les appareils qui lui ont été affectés affichent le nom de catégorie **Non affecté**.

## <a name="view-the-categories-of-devices-that-you-manage"></a>Voir les catégories d’appareils que vous gérez

1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com), choisissez **Appareils** > **Tous les appareils**.

2. Dans la liste des appareils, examinez la colonne **Catégorie d’appareil**.

3. Si la colonne Catégorie d’appareils n’est pas affichée, sélectionnez **Colonnes** > **Catégorie** > **Appliquer**.

## <a name="change-the-category-of-a-device"></a>Changer la catégorie d’un appareil

1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com), choisissez **Appareils** > **Tous les appareils**. 

2. Sélectionnez la catégorie souhaitée dans la liste pour afficher ses propriétés.

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez terminé vos missions principales, prenez le temps de configurer vos [équipes de réponse](m365bp-security-incident-management.md) et de [gérer votre environnement](m365bp-maintain-environment.md).
