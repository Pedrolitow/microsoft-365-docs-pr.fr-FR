---
title: Supprimer des appareils
description: Supprimer des appareils de la gestion Bureau géré Microsoft gestion
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: fa1cb7307fddd815a2a9249c5a98739d21bd2418
ms.sourcegitcommit: 55791ddab9ae484f76b30f0470eec8a4cf7b46d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51893733"
---
# <a name="remove-devices"></a>Supprimer des appareils

Vous pouvez supprimer des appareils de Bureau géré Microsoft gestion à l’aide du portail d’administration. Cette action est permanente, mais vous pouvez les inscrire à nouveau auprès Bureau géré Microsoft en suivant les étapes [d’inscription.](../get-started/register-devices-self.md)

Lorsque vous supprimez un appareil, toutes les choses suivantes se produisent :

- Nous ôtons l’appareil d’Autopilot.
- Nous ôtons l’appareil de tous les groupes d’appareils « Espace de travail moderne ».
- Nous ôtons l’appareil du panneau **Périphériques** dans le portail d’administration.

Lorsque vous supprimez un appareil, vous pouvez également le supprimer de Azure Active Directory (Azure AD) et de Microsoft Intune.
 
> [!CAUTION]
> La suppression des objets liés à un appareil d’Azure AD et Microsoft Intune est permanente. Si vous supprimez les objets, vous ne pourrez pas afficher ou gérer les appareils à partir des portails Intune et Azure. Les appareils ne pourront pas accéder aux ressources d’entreprise de leur entreprise. Les données d’entreprise peuvent être supprimées si les appareils tentent de se connecter après leur suppression.

1. Dans [Microsoft Endpoint Manager,](https://endpoint.microsoft.com/) **sélectionnez Appareils** dans le volet de navigation de gauche.
2. Recherchez la **Bureau géré Microsoft** section du menu et sélectionnez **Appareils.**
3. Dans l Bureau géré Microsoft de travail Appareils, sélectionnez les appareils que vous souhaitez supprimer.
4. Sélectionnez **Actions** de l’appareil, puis **Supprimez l’appareil** qui ouvre un écran volant pour supprimer les appareils.
5. Dans le fly-in, examinez les appareils sélectionnés, puis sélectionnez **Supprimer des appareils.** Si vous souhaitez également supprimer les objets Azure AD et Intune en même temps, cochez la case. La suppression de l’appareil peut prendre quelques minutes.

> [!NOTE]
> Vous ne pouvez pas supprimer les appareils dont l’état d’inscription **est** en attente.