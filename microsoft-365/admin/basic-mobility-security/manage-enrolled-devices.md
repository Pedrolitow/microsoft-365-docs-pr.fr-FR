---
title: Gérer les appareils inscrits dans Mobile Gestion des appareils dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Connectez-vous à Microsoft 365 et configurez Mobilité et sécurité de base pour utiliser la gestion intégrée des appareils mobiles pour sécuriser et gérer les appareils mobiles de vos utilisateurs.
ms.openlocfilehash: 019acc8db1c3ae4293aeed78d7cdd105366c1e7c
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728101"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Gérer les appareils inscrits dans Mobile Gestion des appareils dans Microsoft 365

La gestion intégrée des appareils mobiles pour Microsoft 365 vous permet de sécuriser et de gérer les appareils mobiles de vos utilisateurs, tels que les iPhones, les iPads, les androids et les téléphones Windows. La première étape consiste à se connecter à Microsoft 365 et à configurer Mobilité et sécurité de base. Pour plus d’informations, consultez [Configurer la mobilité et la sécurité de base](set-up.md).

Une fois que vous l’avez configuré, les membres de votre organisation doivent inscrire leurs appareils dans le service. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md). Vous pouvez ensuite utiliser Mobilité et sécurité de base pour vous aider à gérer les appareils de votre organisation. Par exemple, vous pouvez utiliser des stratégies de sécurité d’appareil pour limiter l’accès à la messagerie ou à d’autres services, afficher les rapports des appareils et réinitialiser à distance un appareil. Vous allez généralement accéder au Centre de conformité & sécurité pour effectuer ces tâches. Pour plus d’informations, consultez [portail de conformité Microsoft Purview](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Tâches de gestion des appareils

Pour accéder au panneau de gestion des appareils, procédez comme suit :

1. Connectez-vous au Centre d'administration Microsoft 365 et accédez à la [page Mobile Gestion des appareils](https://portal.office.com/adminportal/home?#/MifoDevices).

1. Sélectionnez **Commençons**.

## <a name="manage-mobile-devices"></a>Gérer des appareils mobiles

Une fois la mobilité de base et la sécurité configurées, voici quelques façons de gérer les appareils mobiles de votre organisation.

|Pour effectuer cette action|Procédez comme suit|
|---|---|
|Réinitialiser un appareil|Dans le panneau Gestion des appareils, sélectionnez *Nom de l’appareil*, puis **Réinitialisation complète** pour supprimer toutes les informations ou **Réinitialisation sélective** pour supprimer uniquement les informations organisationnelles sur l’appareil. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).|
|Bloquer l'accès des appareils non pris en charge à la messagerie Exchange à l'aide d'Exchange ActiveSync|Dans le panneau Gestion des appareils, sélectionnez **Bloquer**.|
|Configurer des stratégies d’appareil telles que les exigences de mot de passe et les paramètres de sécurité|Dans le volet Gestion des appareils, sélectionnez Stratégies de **sécurité de** >  l’appareil **Ajouter +**. Pour plus d’informations, consultez [Créer des stratégies de sécurité d’appareil dans Mobilité et sécurité de base](create-device-security-policies.md).|
|Afficher la liste des appareils bloqués|Dans le panneau Gestion des appareils, sous **Sélectionner une vue**, sélectionnez **Bloqué**.|
|Débloquer un appareil non pris en charge ou non conforme pour un utilisateur ou un groupe d'utilisateurs|Choisissez l’une des options suivantes pour débloquer les appareils :<br/>- Supprimez le ou les utilisateurs du groupe de sécurité auquel la stratégie a été appliquée. Accédez à Centre d'administration Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>, puis sélectionnez nom du groupe. Sélectionnez **Modifier les membres et les administrateurs**.<br/>- Supprimez du groupe de sécurité dont les utilisateurs sont membres de la stratégie d’appareil. Accédez à Centre de sécurité & conformité > **Stratégies de sécurité Stratégies** >  de **sécurité des appareils**. Sélectionnez nom de la stratégie d’appareil, puis **sélectionnez Modifier le** > **déploiement**.<br/>- Débloquer tous les appareils non conformes pour une stratégie d’appareil. Accédez à Centre de sécurité & conformité > **Stratégies de sécurité Stratégies** >  de **sécurité des appareils**. Sélectionnez nom de la stratégie d’appareil, puis **Modifier les** > **exigences d’accès**. Sélectionnez **Autoriser l’accès et signaler la violation**.<br/>- Pour débloquer un appareil non conforme ou non pris en charge pour un utilisateur ou un groupe d’utilisateurs, accédez à Centre de conformité sécurité & > Stratégies  > **de sécurité****Gestion des** > **appareils Gérer les paramètres d’accès aux appareils**. Ajoutez un groupe de sécurité avec les membres que vous souhaitez exclure du blocage de l’accès à Microsoft 365. Pour plus d’informations, consultez [Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Supprimer des utilisateurs afin que leurs appareils ne soient plus gérés par Mobilité et sécurité de base|Pour supprimer l’utilisateur, modifiez le groupe de sécurité qui a des stratégies de gestion des appareils pour Mobilité et sécurité de base. Pour plus d’informations, consultez [Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Pour supprimer mobilité et sécurité de base de tous vos utilisateurs Microsoft 365, consultez [Désactiver la mobilité et la sécurité de base](turn-off.md).|

Live (v14)
