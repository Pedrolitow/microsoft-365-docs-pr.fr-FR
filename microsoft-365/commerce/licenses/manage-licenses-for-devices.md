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
ms.openlocfilehash: c7c747d5f4d2408b717bf16068d23c7882c2d667
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42242323"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous disposez d’Office 365 ProPlus for Education (Device), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, quiconque utilise ce périphérique peut utiliser Office 365. Par exemple, imaginons que vous avez 20 ordinateurs portables et tablettes utilisés par les employés de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise Office 365 sans qu’il soit nécessaire de posséder sa propre licence.

> [!IMPORTANT]
> Office 365 ProPlus for Education (Device) est uniquement disponible pour les clients de licence en volume a3 et a5.

Pour commencer, créez un groupe dans le centre d’administration Azure Active Directory, puis affectez des appareils au groupe. Pour en savoir plus sur les licences d’appareil, notamment les exigences en matière de périphériques, les types de groupes que vous pouvez utiliser et la procédure de configuration d’Office 365 ProPlus pour utiliser les licences d’appareil, voir [device licensing for Office 365 ProPlus for Education Customers](https://go.microsoft.com/fwlink/p/?linkid=2094216).

> [!IMPORTANT]
> Vous devez être un administrateur général pour effectuer les tâches décrites dans cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les périphériques au sein du groupe. Vous ne pouvez attribuer qu’un seul abonnement à un seul groupe.

1. Dans le centre d’administration Microsoft 365, accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de **facturation** > .
2. Sur la page **licences** , sélectionnez **Office 365 ProPlus for Education (Device)**.
3. Sur la page **Office 365 ProPlus for Education (Device)** , sélectionnez un abonnement, puis choisissez **attribuer des licences**.
4. Dans le volet **attribuer des licences à un groupe** , commencez à taper un nom de groupe, puis sélectionnez-le dans les résultats pour l’ajouter à la liste.
6. Sélectionnez **affecter**, puis **Fermer**.

## <a name="unassign-licenses-from-devices"></a>Désaffecter les licences des appareils

Lorsque vous désaffectez des licences à un groupe, vous supprimez les licences de tous les périphériques au sein du groupe. Toutes les applications et leurs données associées sont alors en lecture seule.

1. Dans le centre d’administration, accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de **facturation** > .
2. Sur la page **licences** , sélectionnez **Office 365 ProPlus for Education (Device)**.
3. Sur la page **Office 365 ProPlus for Education (appareil)** , sélectionnez un abonnement, sélectionnez **autres actions**, puis **désaffecter les licences**.
5. Dans la boîte de dialogue **Annuler l’attribution des licences** , sélectionnez Annuler l' **affectation**.