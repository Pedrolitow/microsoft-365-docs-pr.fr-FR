---
title: Gérer les licences pour les appareils
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
description: Découvrez comment attribuer des licences à des groupes en vue de les utiliser avec des appareils.
ms.custom: okr_SMB
search.appverid:
- MET150
ms.openlocfilehash: a29465e9425694f8913cc09d1b8a0c761c79803c
ms.sourcegitcommit: 2859c82b30ae9cbd3a3e4bcdebd65f18444f1a9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "42826278"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous disposez d’Office 365 ProPlus (Device) ou Office 365 ProPlus for Education (Device), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, quiconque utilise ce périphérique peut utiliser Office 365. Par exemple, imaginons que vous avez 20 ordinateurs portables et tablettes utilisés par les employés de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise Office 365 sans qu’il soit nécessaire de posséder sa propre licence.

> [!IMPORTANT]
> La gestion des licences basées sur les appareils pour Office 365 ProPlus est uniquement disponible en tant que licence de module complémentaire pour certains clients commerical et pour certains clients de l’éducation. Pour les clients commerciaux, la licence est *Office 365 ProPlus (appareil)* et est disponible uniquement par le biais d’un abonnement accord entreprise/accord entreprise. Pour les clients de l’éducation, la licence est *Office 365 ProPlus for Education (Device)* et n’est disponible que par le biais de l’inscriptions for Education solutions (EES). Pour plus d’informations, consultez le billet de blog sur la disponibilité de l' [éducation](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-device-based-subscription-for-education/). Pour une disponibilité commerciale, contactez votre représentant Microsoft.

Pour commencer, créez un groupe dans le centre d’administration Azure Active Directory, puis affectez des appareils au groupe. Pour en savoir plus sur les licences des appareils, notamment les exigences en matière de périphériques, les types de groupes que vous pouvez utiliser et la procédure de configuration d’Office 365 ProPlus pour utiliser les licences d’appareil, consultez la rubrique [relative aux licences basées sur les appareils pour Office 365 ProPlus](https://go.microsoft.com/fwlink/p/?linkid=2094216).

> [!IMPORTANT]
> Vous devez être un administrateur général pour effectuer les tâches décrites dans cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les périphériques au sein du groupe. Vous ne pouvez attribuer qu’un seul abonnement à un seul groupe.

1. Dans le centre d’administration Microsoft 365, accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de **facturation** > .
2. Sur la page **licences** , choisissez **Office 365 ProPlus for Education (Device)** ou **Office ProPlus (appareil)**.
3. Sur la page suivante, choisissez un abonnement, puis choisissez **attribuer des licences**.
4. Dans le volet **attribuer des licences à un groupe** , commencez à taper un nom de groupe, puis sélectionnez-le dans les résultats pour l’ajouter à la liste.
5. Sélectionnez **affecter**, puis **Fermer**.

## <a name="unassign-licenses-from-devices"></a>Désaffecter les licences des appareils

Lorsque vous désaffectez des licences à un groupe, vous supprimez les licences de tous les périphériques au sein du groupe. Toutes les applications et leurs données associées sont alors en lecture seule.

1. Dans le centre d’administration, accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de **facturation** > .
2. Sur la page **licences** , choisissez **Office 365 ProPlus for Education (Device)** ou **Office ProPlus (appareil)**.
3. Sur la page suivante, sélectionnez un abonnement, sélectionnez **autres actions**, puis **désaffecter les licences**.
4. Dans la boîte de dialogue **Annuler l’attribution des licences** , sélectionnez Annuler l' **affectation**.