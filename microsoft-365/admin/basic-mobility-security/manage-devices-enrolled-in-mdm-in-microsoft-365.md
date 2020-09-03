---
title: Gérer les appareils intégrés dans la gestion des appareils mobiles dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: La sécurité et la mobilité de base peuvent vous aider à sécuriser et gérer les appareils mobiles.
ms.openlocfilehash: 36ea0d12becca2e97a56aceea107fa1f5bf6ded4
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336861"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Gérer les appareils intégrés dans la gestion des appareils mobiles dans Microsoft 365

La gestion des appareils mobiles intégrée pour Microsoft 365 vous aide à sécuriser et gérer les appareils mobiles de vos utilisateurs, tels que les iPhone, les iPad, les Android et les téléphones Windows. La première étape consiste à se connecter à Microsoft 365 et à configurer la sécurité et la mobilité de base. Pour plus d’informations, consultez la rubrique [Set Up Basic Mobility and Security](set-up-basic-mobility-and-security.md).

Une fois que vous l’avez configurée, les personnes de votre organisation doivent inscrire leurs appareils dans le service. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device-using-basic-mobility-and-security.md).Vous pouvez ensuite utiliser la mobilité et la sécurité de base pour faciliter la gestion des appareils dans votre organisation. Par exemple, vous pouvez utiliser des stratégies de sécurité d’appareil pour limiter l’accès à la messagerie électronique ou d’autres services, afficher des rapports sur les appareils et réinitialiser un appareil à distance. Pour effectuer ces tâches, vous accédez généralement au centre de sécurité & conformité. Pour plus d’informations, consultez le [Centre de conformité Microsoft 365](https://support.microsoft.com/office/7e696a40-b86b-4a20-afcc-559218b7b1b8).

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Pour accéder au panneau de configuration de l’appareil, procédez comme suit :

1. Accédez au [Centre d’administration Microsoft 365](https://support.microsoft.com/office/758befc4-0888-4009-9f14-0d147402fd23).
    
2. Tapez gestion des appareils mobiles dans le champ de recherche, puis sélectionnez **gestion des appareils mobiles**   dans la liste des résultats.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Option de gestion des appareils mobiles":::

3. Sélectionnez  **gérer les appareils**.

## <a name="manage-mobile-devices"></a>Gérer des appareils mobiles
    
Une fois la configuration de la sécurité et de la mobilité de base terminée, voici quelques façons de gérer les appareils mobiles de votre organisation.

|**Pour**|**Procédez comme suit**|
|:----------------|:------------------------------------------------------------------------------|
|Réinitialiser un appareil |Dans le panneau de gestion des périphériques, sélectionnez *nom du périphérique*, puis  **effacement complet**   pour supprimer toutes les informations ou  **balayage sélectif**   pour supprimer uniquement les informations organisationnelles sur l’appareil. Pour plus d’informations, reportez-vous à [la rubrique essuyage d’un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md).|
|Bloquer l'accès des appareils non pris en charge à la messagerie Exchange à l'aide d'Exchange ActiveSync |Dans le panneau de gestion des périphériques, sélectionnez  **bloquer**. |
|Configurer des stratégies d’appareil telles que les exigences de mot de passe et les paramètres de sécurité |Dans le panneau de gestion des périphériques, sélectionnez Ajouter des **stratégies de sécurité des appareils**   >  **+**. Pour plus d’informations, consultez la rubrique [créer des stratégies de sécurité de périphérique dans Basic Mobility and Security](create-device-security-policies-in-basic-mmobility-and-security.md).|
|Afficher la liste des appareils bloqués  |Dans le panneau de gestion des appareils, sous  **Sélectionnez un affichage** ,   sélectionnez  **bloqué**. |
|Débloquer un appareil non pris en charge ou non conforme pour un utilisateur ou un groupe d'utilisateurs  |Choisissez l’une des options suivantes pour débloquer les appareils :<br/>-Supprimez le ou les utilisateurs du groupe de sécurité auquel la stratégie a été appliquée. Accédez au centre d’administration Microsoft 365 > **groupes**, puis sélectionnez nom du groupe. Sélectionnez **modifier les membres et les administrateurs**.<br/>-Supprimez le groupe de sécurité dont les utilisateurs sont membres à partir de la stratégie d’appareil. Accédez au centre de sécurité & conformité  **>**   >  **stratégies de sécurité des périphériques**de sécurité. Sélectionnez nom de la stratégie de périphérique, puis **modifier**le  >  **déploiement**.<br/>-Débloquer tous les appareils non conformes pour une stratégie d’appareil. Accédez au centre de sécurité & conformité  **>**   >  **stratégies de sécurité des périphériques**de sécurité. Sélectionnez nom de la stratégie de l’appareil, puis **modifier**les  >  **conditions d’accès**. Sélectionnez  **autoriser l’accès et la violation de rapport**.<br/>-Pour débloquer un périphérique non conforme ou non pris en charge pour un utilisateur ou un groupe d’utilisateurs, accédez au centre de sécurité & conformité > **stratégies de sécurité**   >  **gestion des périphériques**   >  **Manage device access settings**. Ajoutez un groupe de sécurité dont les membres doivent être exclus de l’accès bloqué à Microsoft 365. Pour plus d’informations, consultez [la rubrique créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration 365 de Microsoft](https://support.microsoft.com/office/55c96b32-e086-4c9e-948b-a018b44510cb).|
|Obtenir des détails sur les appareils de votre organisation  |Pour plus d’informations, par exemple, quels sont les appareils qui sont déployés et conformes aux stratégies de sécurité des appareils, reportez-vous à [obtenir des détails sur les périphériques gérés de mobilité et de sécurité de base](get-details-about-basic-mobility-and-security-managed-devices.md).|
|Supprimer des utilisateurs afin que leurs appareils ne soient plus gérés par la sécurité et la mobilité de base |Pour supprimer l’utilisateur, modifiez le groupe de sécurité qui dispose des stratégies de gestion des périphériques pour la sécurité et la mobilité de base. Pour plus d’informations, consultez  [la rubrique créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration 365 de Microsoft](https://support.microsoft.com/office/55c96b32-e086-4c9e-948b-a018b44510cb).<br/>Pour supprimer la mobilité et la sécurité de base de tous les utilisateurs de Microsoft 365, consultez la rubrique [désactiver la sécurité et la mobilité de base](turn-off-basic-mobility-and-security.md).|

Live (v14)