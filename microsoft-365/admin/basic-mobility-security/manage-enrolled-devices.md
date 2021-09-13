---
title: Gérer les appareils inscrits à la gestion des appareils mobiles dans Microsoft 365
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
- admindeeplinkMAC
search.appverid:
- MET150
description: Basic Mobility and Security peut vous aider à sécuriser et gérer les appareils mobiles de votre organisation.
ms.openlocfilehash: 3cb5b34d869ae16faa89ced45d54537fbb07a5e2
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176844"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Gérer les appareils inscrits à la gestion des appareils mobiles dans Microsoft 365

La gestion intégrée des appareils mobiles pour Microsoft 365 vous permet de sécuriser et de gérer les appareils mobiles de vos utilisateurs tels que les iPhone, iPad, Android et Windows mobiles. La première étape consiste à vous Microsoft 365 et à configurer Basic Mobility and Security. Pour plus d’informations, voir [Configurer la mobilité et la sécurité de base.](set-up.md)

Une fois que vous l’avez installé, les membres de votre organisation doivent inscrire leurs appareils dans le service. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md).Vous pouvez ensuite utiliser la mobilité et la sécurité de base pour vous aider à gérer les appareils de votre organisation. Par exemple, vous pouvez utiliser des stratégies de sécurité des appareils pour limiter l’accès à la messagerie ou à d’autres services, afficher les rapports des appareils et effacer à distance un appareil. En règle générale, vous allez au Centre de sécurité & conformité pour effectuer ces tâches. Pour plus d’informations, [voir Centre de conformité Microsoft 365](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Pour obtenir le panneau de gestion des appareils, suivez les étapes suivantes :

1. Go to the [Centre d'administration Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Tapez Gestion des appareils mobiles dans le champ de recherche, puis sélectionnez **Gestion des** périphériques mobiles dans la liste   des résultats.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Option de gestion des appareils mobiles.":::

3. Select  **Let’s get started**.

## <a name="manage-mobile-devices"></a>Gérer des appareils mobiles

Une fois la mobilité et la sécurité de base définies, voici quelques méthodes pour gérer les appareils mobiles de votre organisation.

|**Pour**|**Procédez comme suit**|
|:----------------|:------------------------------------------------------------------------------|
|Réinitialiser un appareil |Dans le panneau Gestion des périphériques, sélectionnez le nom de l’appareil, puis effacez complètement pour supprimer toutes les informations ou la suppression sélective pour supprimer uniquement les informations **  ****     ****   organisationnelles sur l’appareil. Pour plus d’informations, voir [Effacer un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md).|
|Bloquer l'accès des appareils non pris en charge à la messagerie Exchange à l'aide d'Exchange ActiveSync |Dans le panneau Gestion des périphériques, sélectionnez  **Bloquer.** |
|Configurer des stratégies d’appareil telles que les exigences de mot de passe et les paramètres de sécurité |Dans le panneau Gestion des appareils, sélectionnez **Stratégies de sécurité des**   >  **appareils Ajouter +**. Pour plus d’informations, voir [Créer des stratégies de sécurité des appareils dans Basic Mobility and Security.](create-device-security-policies.md)|
|Afficher la liste des appareils bloqués  |Dans le panneau Gestion des périphériques, sous  **Sélectionner un affichage,**   sélectionnez  **Bloqué.** |
|Débloquer un appareil non pris en charge ou non conforme pour un utilisateur ou un groupe d'utilisateurs  |Sélectionnez l’une des sélections suivantes pour débloquer les appareils :<br/>- Supprimez l’utilisateur ou les utilisateurs du groupe de sécurité à qui la stratégie a été appliquée. Go to Centre d'administration Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groups,**</a>and then select group name. Sélectionnez **Modifier les membres et les administrateurs.**<br/>- Supprimez le groupe de sécurité dont les utilisateurs sont membres de la stratégie d’appareil. Go to Security & Compliance Center > **Security policies** Device   >  **security policies**. Sélectionnez le nom de la stratégie d’appareil, puis **sélectionnez Modifier**  >  **le déploiement.**<br/>- Débloquer tous les appareils non conformes pour une stratégie d’appareil. Go to Security & Compliance Center > **Security policies** Device   >  **security policies**. Sélectionnez le nom de la stratégie d’appareil, puis **sélectionnez Modifier**  >  **les exigences d’accès.** Sélectionnez  **Autoriser l’accès et signaler une violation.**<br/>- Pour débloquer un appareil non conforme ou non pris en charge pour un utilisateur ou un groupe d’utilisateurs, accédez au Centre de sécurité & conformité > **Stratégies** de sécurité Gestion des périphériques Gérer les paramètres d’accès des   >  ****   >  **** appareils. Ajoutez un groupe de sécurité avec les membres que vous souhaitez exclure de l’accès bloqué aux Microsoft 365. Pour plus d’informations, [voir Créer, modifier ou supprimer](../../admin/email/create-edit-or-delete-a-security-group.md)un groupe de sécurité dans le Centre d'administration Microsoft 365 .|
|Supprimer des utilisateurs afin que leurs appareils ne soient plus gérés par Basic Mobility and Security |Pour supprimer l’utilisateur, modifiez le groupe de sécurité qui dispose de stratégies de gestion des appareils pour basic Mobility and Security. Pour plus d’informations,  [voir Créer, modifier ou supprimer un](../../admin/email/create-edit-or-delete-a-security-group.md)groupe de sécurité dans le Centre d'administration Microsoft 365 .<br/>Pour supprimer Basic Mobility and Security de tous vos utilisateurs Microsoft 365, voir Désactiver la mobilité [et la sécurité de base.](turn-off.md)|

Live (v14)