---
title: Gérer les appareils inscrits dans mobile Gestion des appareils dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: La mobilité et la sécurité de base peuvent vous aider à sécuriser et gérer les appareils mobiles de votre organisation.
ms.openlocfilehash: cb724a4f7d5b4118bb50b0aeaf1138a4a1aebfb6
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129131"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Gérer les appareils inscrits dans mobile Gestion des appareils dans Microsoft 365

La gestion intégrée des appareils mobiles pour Microsoft 365 vous permet de sécuriser et de gérer les appareils mobiles de vos utilisateurs, tels que les iPhone, les iPad, les Android et les téléphones Windows. La première étape consiste à se connecter à Microsoft 365 et à configurer la mobilité et la sécurité de base. Pour plus d’informations, consultez [Configurer la mobilité et la sécurité de base](set-up.md).

Une fois que vous l’avez configuré, les membres de votre organisation doivent inscrire leurs appareils dans le service. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md).Vous pouvez ensuite utiliser Mobilité et sécurité de base pour gérer les appareils de votre organisation. Par exemple, vous pouvez utiliser des stratégies de sécurité des appareils pour limiter l’accès aux e-mails ou d’autres services, afficher les rapports des appareils et réinitialiser à distance un appareil. Vous accédez généralement au Centre de sécurité & conformité pour effectuer ces tâches. Pour plus d’informations, consultez [le portail de conformité Microsoft Purview](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Pour accéder au panneau de gestion des appareils, procédez comme suit :

1. Accédez au [Centre d’administration Microsoft 365](../../admin/admin-overview/admin-center-overview.md).

2. Tapez Mobile Gestion des appareils dans le champ de recherche, puis sélectionnez **Mobile Gestion des appareils** dans la liste des résultats.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Option de gestion des appareils mobiles.":::

3. Sélectionnez **Prise en main**.

## <a name="manage-mobile-devices"></a>Gérer des appareils mobiles

Une fois la mobilité et la sécurité de base configurées, voici quelques façons de gérer les appareils mobiles de votre organisation.

|Pour effectuer cette action|Procédez comme suit|
|---|---|
|Réinitialiser un appareil|Dans le panneau Gestion des appareils, sélectionnez *le nom de l’appareil*, puis **réinitialisation complète** pour supprimer toutes les informations ou **réinitialisation sélective** pour supprimer uniquement les informations d’organisation sur l’appareil. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).|
|Bloquer l'accès des appareils non pris en charge à la messagerie Exchange à l'aide d'Exchange ActiveSync|Dans le panneau Gestion des appareils, sélectionnez **Bloquer**.|
|Configurer des stratégies d’appareil telles que les exigences de mot de passe et les paramètres de sécurité|Dans le panneau Gestion des appareils, sélectionnez **Stratégies de sécurité** >  **des appareilsAdd +**. Pour plus d’informations, consultez [Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base](create-device-security-policies.md).|
|Afficher la liste des appareils bloqués|Dans le panneau Gestion des appareils, sous **Sélectionner une vue**, **sélectionnez Bloquer**.|
|Débloquer un appareil non pris en charge ou non conforme pour un utilisateur ou un groupe d'utilisateurs|Choisissez l’une des options suivantes pour débloquer les appareils :<br/>- Supprimez l’utilisateur ou les utilisateurs du groupe de sécurité auquel la stratégie a été appliquée. Accédez à Centre d'administration Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>, puis sélectionnez le nom du groupe. Sélectionnez **Modifier les membres et les administrateurs**.<br/>- Supprimez le groupe de sécurité dont les utilisateurs sont membres de la stratégie d’appareil. Accédez au Centre de sécurité & conformité > **stratégies** >  de **sécuritéDevice**. Sélectionnez le nom de la stratégie d’appareil, puis **sélectionnez** **EditDeployment** > .<br/>- Débloquer tous les appareils non conformes pour une stratégie d’appareil. Accédez au Centre de sécurité & conformité > **stratégies** >  de **sécuritéDevice**. Sélectionnez le nom de la stratégie d’appareil, puis sélectionnez **la configuration requise pour EditAccess** > . Sélectionnez **Autoriser l’accès et signaler une violation**.<br/>- Pour débloquer un appareil non conforme ou non pris en charge pour un utilisateur ou un groupe d’utilisateurs, accédez au Centre de sécurité & conformité > **paramètres d’accès aux appareils** **Security policiesDevice** >  **managementManage** > . Ajoutez un groupe de sécurité avec les membres que vous souhaitez exclure de l’accès bloqué à Microsoft 365. Pour plus d’informations, consultez [Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Supprimer des utilisateurs afin que leurs appareils ne soient plus gérés par mobilité et sécurité de base|Pour supprimer l’utilisateur, modifiez le groupe de sécurité qui a des stratégies de gestion des appareils pour la mobilité et la sécurité de base. Pour plus d’informations, consultez [Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Pour supprimer la mobilité et la sécurité de base de tous vos utilisateurs Microsoft 365, consultez [Désactiver la mobilité et la sécurité de base](turn-off.md).|

Live (v14)
