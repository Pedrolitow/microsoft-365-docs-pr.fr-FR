---
title: Gérer les licences pour les appareils
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: shegu, nicholak
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
description: Découvrez comment attribuer des licences à des groupes à utiliser avec des appareils.
ms.custom:
- AdminSurgePortfolio
- okr_SMB
- commerce_licensing
search.appverid: MET150
ms.date: 03/17/2021
ms.openlocfilehash: c590c2d47699c4c3cbea4b5145bea9e7c9fc79ec
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52535661"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous avez Applications Microsoft 365 pour les grandes entreprises (appareil) ou Microsoft 365 Apps Éducation (appareil), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, toute personne qui l’utilise peut Applications Microsoft 365 pour les grandes entreprises (précédemment Office 365 ProPlus). Par exemple, supposons que vous avez 20 ordinateurs portables et tablettes utilisés par les membres de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise Applications Microsoft 365 pour les grandes entreprises sans avoir besoin de sa propre licence.

> [!IMPORTANT]
> Les licences basées sur l’appareil Applications Microsoft 365 pour les grandes entreprises sont disponibles uniquement sous la mesure d’une licence de modules de développement pour certains clients commerciaux et certains clients de l’éducation. Pour les clients commerciaux, la licence *est Applications Microsoft 365 pour les grandes entreprises (appareil)* et est disponible uniquement par Accord Entreprise/Accord Entreprise abonnement. Pour les clients de l’éducation, la licence est Microsoft 365 Apps éducation *(appareil)* et est disponible uniquement par le biais de l’inscription pour les solutions Éducation (EES). Pour plus d’informations, lisez le billet de blog sur la [disponibilité de l’éducation.](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education) Pour la disponibilité commerciale, contactez votre représentant de compte Microsoft.

Pour commencer, vous créez un groupe dans Azure Active Directory centre d’administration, puis attribuez des appareils au groupe. Pour en savoir plus sur la gestion des licences d’appareils, notamment la configuration requise pour les appareils, les types de groupes que vous pouvez utiliser et comment configurer Applications Microsoft 365 pour les grandes entreprises pour utiliser la gestion des licences d’appareils, voir Licences basées sur les [appareils pour Applications Microsoft 365 pour les grandes entreprises](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Vous devez être un administrateur global pour effectuer les tâches de cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les appareils du groupe. Vous ne pouvez affecter qu’un seul abonnement à un seul groupe.

1. Dans le centre Microsoft 365'administration, allez sur la page  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation.</a>
2. Dans la page **Licences,** choisissez **Microsoft 365 Apps Éducation (appareil)** **ou Applications Microsoft 365 pour les grandes entreprises (appareil).**
3. Sur la page suivante, choisissez un abonnement, puis **sélectionnez Attribuer des licences.**
4. Dans le **volet Attribuer des licences** à un volet de groupe, commencez à taper un nom de groupe, puis choisissez-le dans les résultats pour l’ajouter à la liste.
5. Choose **Assign,** then choose **Close**.

## <a name="unassign-licenses-from-devices"></a>Désattribuer des licences à des appareils

Lorsque vous désattribuez des licences à un groupe, vous supprimez les licences de tous les appareils du groupe. Toutes les applications et leurs données associées sont ensuite en lecture seule.

1. Dans le Centre d’administration, allez sur la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation.</a>
2. Dans la page **Licences,** choisissez **Microsoft 365 Apps Éducation (appareil)** **ou Applications Microsoft 365 pour les grandes entreprises (appareil).**
3. Sur la page suivante, choisissez un abonnement, sélectionnez les trois points (autres actions), puis choisissez **Désattribuer des licences.**
4. In the **Unassign licenses** dialog box, choose **Unassign**.
