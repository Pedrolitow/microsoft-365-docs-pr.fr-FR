---
title: Désactiver la mobilité et la sécurité de base
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Supprimez des groupes ou des stratégies pour désactiver la mobilité et la sécurité de base.
ms.openlocfilehash: 0786ac8ebd190b9af3211c211cc6db2ea9e0ea48
ms.sourcegitcommit: 8849dd6f80217c29f427c7f008d918f30c792240
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "49876839"
---
# <a name="turn-off-basic-mobility-and-security"></a>Désactiver la mobilité et la sécurité de base

Pour désactiver efficacement la mobilité et la sécurité de base, vous supprimez des groupes de personnes définis par des groupes de sécurité des stratégies de gestion des appareils ou vous supprimez les stratégies elles-mêmes.

- Supprimez des groupes d’utilisateurs en supprimant des groupes de sécurité d’utilisateurs des stratégies d’appareil que vous avez créées.

- Désactivez la mobilité et la sécurité de base pour tout le monde en supprimant toutes les stratégies d’appareil de mobilité et de sécurité de base.

Ces options suppriment l’application de la mobilité et de la sécurité de base pour les appareils de votre organisation. Malheureusement, vous ne pouvez pas simplement « mettre en service » Basic Mobility and Security après l’avoir installé. 

>[!IMPORTANT]
>N’ignorez pas l’impact sur les appareils des utilisateurs lorsque vous supprimez des groupes de sécurité d’utilisateurs des stratégies ou supprimez les stratégies elles-mêmes. Par exemple, les profils de messagerie et les e-mails mis en cache peuvent être supprimés, en fonction de l’appareil. Pour plus d’informations,  [que se passe-t-il lorsque](https://support.microsoft.com/office/create-device-security-policies-in-basic-mobility-and-security-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6#bkmk_changeimpact) vous supprimez une stratégie ou supprimez un utilisateur de la stratégie ?

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Supprimer des groupes de sécurité utilisateur des stratégies d’appareil de mobilité et de sécurité de base

1. Dans votre type de navigateur :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez une stratégie d’appareil, puis **sélectionnez Modifier la stratégie.** 

3. Dans la page  **Déploiement,**   sélectionnez **Supprimer.**

4. Sous  **Groupes,** sélectionnez un groupe de sécurité.

5. Sélectionnez  **Supprimer,** puis **Enregistrer.**

## <a name="remove-basic-mobility-and-security-device-policies"></a>Supprimer des stratégies d’appareil de mobilité et de sécurité de base

1.  Dans votre type de navigateur :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) . 

2.  Sélectionnez une stratégie d’appareil, puis  **sélectionnez Supprimer la stratégie.**
    
3.  Dans la boîte de dialogue Avertissement, sélectionnez **Oui.**

>[!NOTE]
>Pour plus d’informations sur la procédure de déblocage des appareils si les appareils de votre organisation sont toujours dans un état bloqué, consultez le billet de blog sur la suppression du contrôle d’accès de la gestion des appareils mobiles pour [Office 365.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934)
