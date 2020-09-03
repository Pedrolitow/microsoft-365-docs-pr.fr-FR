---
title: Gérer les paramètres d’accès aux appareils dans la sécurité et la mobilité de base
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
ms.openlocfilehash: 0d8f4293c45bcc1dc2a71dbc749641cf3791337e
ms.sourcegitcommit: 2179abfe0b7a8bea917eb1c1057ed3795bdf91e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "47336849"
---
# <a name="manage-device-access-settings-in-basic-mobility-and-security"></a>Gérer les paramètres d’accès aux appareils dans la sécurité et la mobilité de base

Si vous utilisez la mobilité et la sécurité de base, il est possible que vous ne puissiez pas gérer les appareils avec la sécurité et la mobilité de base. Si c’est le cas, vous devez bloquer l’accès de l’application Exchange ActiveSync aux courriers électroniques Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par la sécurité et la mobilité de base. Cela permet de sécuriser les informations de votre organisation sur plusieurs appareils.

Procédez comme suit :

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.
    
2. Dans votre navigateur, tapez :  [https://protection.office.com](https://protection.office.com/) .    

    >[!IMPORTANT]
    >S’il s’agit de la première fois que vous utilisez MDM pour Microsoft 365 Business standard, activez-la ici : [activer la gestion des appareils mobiles](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Une fois que vous l’avez activé, gérez vos appareils avec [Office 365 Security & Compliance](https://protection.office.com/).

3. Accédez à protection contre la perte de données >stratégies d’appareil de  **gestion des appareils**   >  **Device policies**et sélectionnez **gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.
    
4. Sélectionnez **bloquer**.

    :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Case à cocher accès aux blocs de sécurité et de mobilité de base":::

5. Sélectionnez **Enregistrer**. 

Pour connaître les appareils pris en charge par la mobilité et la sécurité de base, reportez-vous à la rubrique [fonctionnalités de base et de sécurité](capabilities-of-basic-mobility-and-secruity.md).