---
title: Gérer les paramètres d’accès aux appareils dans Mobilité et sécurité de base
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
search.appverid:
- MET150
description: La mobilité et la sécurité de base peuvent vous aider à sécuriser et à gérer les appareils mobiles.
ms.openlocfilehash: aa5c6bb757604763e9ba7348d1d4f952a6555865
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935256"
---
# <a name="manage-device-access-settings-in-basic-mobility-and-security"></a>Gérer les paramètres d’accès aux appareils dans Mobilité et sécurité de base

Si vous utilisez la mobilité et la sécurité de base, il peut y avoir des appareils que vous ne pouvez pas gérer avec la mobilité et la sécurité de base. Si c’est le cas, vous devez bloquer Exchange ActiveSync’accès de l’application à Microsoft 365 courrier électronique pour les appareils mobiles qui ne sont pas pris en charge par la mobilité et la sécurité de base. Cela permet de sécuriser les informations de votre organisation sur d’autres appareils.

Procédez comme suit :

1. Connectez-vous à Microsoft 365 avec votre compte d’administrateur général.

2. Dans votre navigateur, tapez : [https://protection.office.com](https://protection.office.com/).

    > [!IMPORTANT]
    > S’il s’agit de la première fois que vous utilisez la mobilité et la sécurité de base pour Microsoft 365 Business Standard, [activez-la ici : Activer la sécurité et la mobilité de base](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Une fois que vous l’avez activé, gérez vos appareils avec [Office 365 Sécurité & Conformité](https://protection.office.com/).

3. Accédez aux stratégies  **managementDevice managementDevice** **** > de  **protection contre la** > perte de données et sélectionnez  **Paramètres d’accès aux appareils à l’échelle de l’organisation**.

4. Sélectionnez **Bloquer**. 

    :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Case à cocher Mobilité et sécurité de base pour bloquer l’accès.":::

5. Sélectionnez **Enregistrer**.

Pour savoir quels appareils la mobilité et la sécurité de base prennent en charge, consultez [Fonctionnalités de mobilité et de sécurité de base](capabilities.md).
