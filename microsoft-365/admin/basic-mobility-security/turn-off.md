---
title: Désactivation de la mobilité et de la sécurité de base
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
description: Supprimez des groupes ou des stratégies pour désactiver la sécurité et la mobilité de base.
ms.openlocfilehash: 54f78cc30e5259ad5244ce3a8fc6d0f46a395d7c
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430150"
---
# <a name="turn-off-basic-mobility-and-security"></a>Désactivation de la mobilité et de la sécurité de base

Pour désactiver efficacement la mobilité et la sécurité de base, vous supprimez les groupes de personnes définies par les groupes de sécurité des stratégies de gestion des appareils ou vous supprimez les stratégies elles-mêmes.

- Supprimez des groupes d’utilisateurs en supprimant les groupes de sécurité des utilisateurs des stratégies d’appareil que vous avez créées.
    
- Désactivez la mobilité et la sécurité de base pour tout le monde en supprimant toutes les stratégies de périphérique de mobilité et de sécurité de base.
    
Ces options suppriment la sécurité de base et l’application de sécurité pour les appareils de votre organisation. Malheureusement, vous ne pouvez pas simplement « mettre hors service » la mobilité et la sécurité de base une fois que vous l’avez configurée. 

>[!IMPORTANT]
>Tenez compte de l’impact sur les appareils des utilisateurs lorsque vous supprimez des groupes de sécurité des utilisateurs des stratégies ou que vous supprimez les stratégies elles-mêmes. Par exemple, les profils de messagerie et les e-mails mis en cache peuvent être supprimés, en fonction de l’appareil. Pour plus d’informations, voir  [que se passe-t-il lorsque vous supprimez une stratégie ou que vous supprimez un utilisateur de la stratégie ?](https://support.microsoft.com/office/create-device-security-policies-in-basic-mobility-and-security-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6#bkmk_changeimpact)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Supprimer les groupes de sécurité des utilisateurs des stratégies de périphérique de mobilité et de sécurité de base

1. Dans votre navigateur, tapez :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez une stratégie d’appareil, puis sélectionnez **modifier la stratégie**. 

3. Sur la page  **déploiement**   , sélectionnez **supprimer**.
    
4. Sous  **groupes**, sélectionnez un groupe de sécurité.

5. Sélectionnez  **supprimer**, puis **Enregistrer**.
    

## <a name="remove-basic-mobility-and-security-device-policies"></a>Supprimer des stratégies de mobilité et de périphérique de sécurité de base

1.  Dans votre navigateur, tapez :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) . 

2.  Sélectionnez une stratégie d’appareil, puis sélectionnez  **Supprimer la stratégie**.
    
3.  Dans la boîte de dialogue d’avertissement, sélectionnez **Oui**.

>[!NOTE] 
>Pour plus d’informations sur le blocage des appareils si les périphériques de votre organisation sont toujours bloqués, consultez le billet [de blog suppression du contrôle d’accès de la gestion des appareils mobiles pour Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
