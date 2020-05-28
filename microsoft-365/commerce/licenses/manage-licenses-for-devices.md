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
ms.custom:
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
ms.openlocfilehash: ce3c8f7d669f2fe5d19c48d7a1fb1f224aaec7f4
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44402869"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous avez Microsoft 365 Apps for Enterprise (Device) ou Microsoft 365 Apps for Education (Device), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, quiconque utilise ce périphérique peut utiliser les applications Microsoft 365 pour entreprise (précédemment nommé Office 365 ProPlus). Par exemple, imaginons que vous avez 20 ordinateurs portables et tablettes utilisés par les employés de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise les applications Microsoft 365 pour Enterprise sans avoir à utiliser sa propre licence.

> [!IMPORTANT]
> La gestion des licences basées sur les appareils pour les applications Microsoft 365 pour Enterprise est uniquement disponible en tant que licence de complément pour certains clients commerciaux et de formation. Pour les clients commerciaux, la licence est *Microsoft 365 apps pour entreprise (appareil)* et est disponible uniquement via un abonnement accord entreprise/accord entreprise. Pour les clients de l’éducation, la licence est *Microsoft 365 Apps for Education (Device)* et n’est disponible que par le biais de l’inscriptions for Education solutions (EES). Pour plus d’informations, consultez le billet de blog sur la disponibilité de l' [éducation](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-device-based-subscription-for-education/). Pour une disponibilité commerciale, contactez votre représentant Microsoft.

Pour commencer, créez un groupe dans le centre d’administration Azure Active Directory, puis affectez des appareils au groupe. Pour en savoir plus sur les licences des appareils, notamment les exigences en matière de périphériques, les types de groupes que vous pouvez utiliser et comment configurer les applications Microsoft 365 pour entreprise afin d’utiliser la gestion des licences d’appareil, consultez la rubrique [relative aux licences basées sur les appareils pour les applications microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?linkid=2094216).

> [!IMPORTANT]
> Vous devez être un administrateur général pour effectuer les tâches décrites dans cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les périphériques au sein du groupe. Vous ne pouvez attribuer qu’un seul abonnement à un seul groupe.

1. Dans le centre d’administration Microsoft 365, accédez à **Billing**la  >  page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de facturation.
2. Sur la page **licences** , choisissez **Microsoft 365 Apps for Education (Device)** ou **Microsoft 365 apps pour entreprise (appareil)**.
3. Sur la page suivante, choisissez un abonnement, puis choisissez **attribuer des licences**.
4. Dans le volet **attribuer des licences à un groupe** , commencez à taper un nom de groupe, puis sélectionnez-le dans les résultats pour l’ajouter à la liste.
5. Sélectionnez **affecter**, puis **Fermer**.

## <a name="unassign-licenses-from-devices"></a>Désaffecter les licences des appareils

Lorsque vous désaffectez des licences à un groupe, vous supprimez les licences de tous les périphériques au sein du groupe. Toutes les applications et leurs données associées sont alors en lecture seule.

1. Dans le centre d’administration, accédez à **Billing**la  >  page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de facturation.
2. Sur la page **licences** , choisissez **Microsoft 365 Apps for Education (Device)** ou **Microsoft 365 apps pour entreprise (appareil)**.
3. Sur la page suivante, sélectionnez un abonnement, sélectionnez **autres actions**, puis **désaffecter les licences**.
4. Dans la boîte de dialogue **Annuler l’attribution des licences** , sélectionnez Annuler l' **affectation**.