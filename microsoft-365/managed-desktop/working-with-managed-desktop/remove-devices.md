---
title: Supprimer des appareils
description: Supprimer des appareils de la gestion Microsoft Manged Desktop gestion
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 82e14fbd2bc991505c84d219c0624f52791376d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324576"
---
# <a name="remove-devices"></a>Supprimer des appareils

Vous pouvez supprimer des appareils de Microsoft Manged Desktop gestion à l’aide du portail d’administration. Cette action est permanente, mais vous pouvez les inscrire à nouveau auprès Microsoft Manged Desktop en suivant les étapes [d’inscription manuelles](../get-started/manual-registration.md).

Lorsque vous supprimez un appareil, toutes les choses suivantes se produisent :

- Nous ôtons l’appareil d’Autopilot.
- Nous ôtons l’appareil de tous les groupes d’appareils « Espace de travail moderne ».
- Nous ôtons l’appareil du panneau **Appareils** dans le portail d’administration.

Lorsque vous supprimez un appareil, vous pouvez également le supprimer des Azure Active Directory (Azure AD) et Microsoft Intune.
  
> [!CAUTION]
> La suppression des objets liés à un appareil de Azure AD et Microsoft Intune est permanente. Si vous supprimez les objets, vous ne pourrez pas afficher ou gérer les appareils à partir des portails Intune et Azure. Les appareils ne pourront pas accéder aux ressources d’entreprise de leur entreprise. Les données d’entreprise peuvent leur être supprimées si les appareils tentent de se connecter après leur suppression.

**Pour supprimer un appareil :**

1. Dans [Microsoft Endpoint Manager](https://endpoint.microsoft.com/), sélectionnez **Appareils dans** le volet de navigation de gauche.
2. Dans la **section Microsoft Manged Desktop**, sélectionnez **Appareils**.
3. Dans l **Microsoft Manged Desktop de travail Périphériques**, sélectionnez les appareils que vous souhaitez supprimer.
4. **Sélectionnez Actions** de l’appareil, puis **Supprimez l’appareil** qui ouvre un écran volant pour supprimer les appareils.
5. Dans le fly-in, examinez les appareils sélectionnés, puis sélectionnez **Supprimer des appareils**. Si vous souhaitez également supprimer les objets Azure AD et Intune en même temps, cochez la case. La suppression de l’appareil peut prendre quelques minutes.

> [!NOTE]
> Vous ne pouvez pas supprimer les appareils dont l’état d’inscription **est** en attente.
