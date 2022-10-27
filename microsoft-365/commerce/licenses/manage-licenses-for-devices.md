---
title: Gérer les licences pour les appareils
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
description: Découvrez comment attribuer des licences à des groupes à utiliser avec des appareils.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 05/12/2022
ms.openlocfilehash: 1bf28a879fc90a797dd5e42c54258f494ed40368
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735372"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous avez Applications Microsoft 365 pour les grandes entreprises (appareil) ou Microsoft 365 Apps éducation (appareil), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, toute personne qui l’utilise peut utiliser Applications Microsoft 365 pour les grandes entreprises (précédemment nommée Office 365 ProPlus). Par exemple, supposons que vous disposez de 20 ordinateurs portables et tablettes utilisés par des personnes de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise Applications Microsoft 365 pour les grandes entreprises sans avoir besoin de sa propre licence.

> [!IMPORTANT]
> Les licences basées sur les appareils pour Applications Microsoft 365 pour les grandes entreprises sont disponibles uniquement en tant que licence d’extension pour certains clients commerciaux et certains clients de l’éducation. Pour les clients commerciaux, la licence est *Applications Microsoft 365 pour les grandes entreprises (appareil)* et est disponible uniquement via Accord Entreprise/Accord Entreprise Abonnement. Pour les clients de l’éducation, la licence est *Microsoft 365 Apps pour l’éducation (appareil)* et est disponible uniquement via l’inscription aux solutions d’éducation (EES). Pour plus d’informations, consultez le billet de blog sur [la disponibilité de l’éducation](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). Pour une disponibilité commerciale, contactez votre représentant de compte Microsoft.

Pour commencer, vous créez un groupe dans le Centre d’administration Azure Active Directory, puis attribuez des appareils au groupe. Pour en savoir plus sur la gestion des licences des appareils, notamment sur la configuration requise des appareils, sur les types de groupes que vous pouvez utiliser et sur la façon de configurer Applications Microsoft 365 pour les grandes entreprises pour utiliser la gestion des [licences des appareils, consultez Licences basées sur les appareils pour Applications Microsoft 365 pour les grandes entreprises](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Vous devez être administrateur général pour effectuer les tâches décrites dans cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les appareils du groupe. Vous ne pouvez attribuer qu’un seul abonnement à un seul groupe.

1. Dans la Centre d'administration Microsoft 365, accédez à la page **Licences de facturation** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Dans la page **Licences**, choisissez **Microsoft 365 Apps éducation (appareil)** ou **Applications Microsoft 365 pour les grandes entreprises (appareil).**
3. Sur la page suivante, choisissez un abonnement, puis **choisissez Attribuer des licences**.
4. Dans le volet **Attribuer des licences à un groupe** , commencez à taper un nom de groupe, puis choisissez-le dans les résultats pour l’ajouter à la liste.
5. Choisissez **Attribuer**, puis **Fermer**.

## <a name="unassign-licenses-from-devices"></a>Annuler l’attribution de licences à partir d’appareils

Lorsque vous annulez l’affectation de licences d’un groupe, vous supprimez les licences de tous les appareils du groupe. Toutes les applications et leurs données associées sont ensuite en lecture seule.

1. Dans le Centre d’administration, accédez à la page **Licences de facturation** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Dans la page **Licences**, choisissez **Microsoft 365 Apps éducation (appareil)** ou **Applications Microsoft 365 pour les grandes entreprises (appareil).**
3. Sur la page suivante, choisissez un abonnement, sélectionnez les trois points (autres actions), puis choisissez **Annuler l’attribution des licences**.
4. Dans la boîte de dialogue **Annuler l’attribution de licences** , choisissez **Annuler l’attribution**.
