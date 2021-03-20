---
title: Gérer les licences pour les appareils
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
description: Découvrez comment attribuer des licences à des groupes à utiliser avec des appareils.
ms.custom:
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
ms.openlocfilehash: a316810e3e6ddb1373697dc56b2fccb5a32cf0b1
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50911481"
---
# <a name="manage-licenses-for-devices"></a>Gérer les licences pour les appareils

Si vous avez Microsoft 365 Apps pour entreprise (appareil) ou Microsoft 365 Apps pour Éducation (appareil), vous pouvez attribuer des licences à des appareils à l’aide de groupes Azure AD. Lorsqu’un appareil dispose d’une licence, toute personne utilisant cet appareil peut utiliser les applications Microsoft 365 pour les entreprises (précédemment nommées Office 365 ProPlus). Par exemple, supposons que vous avez 20 ordinateurs portables et tablettes utilisés par les membres de votre organisation. Lorsque vous attribuez une licence à chaque appareil, chaque personne qui se connecte à l’un des appareils utilise Microsoft 365 Apps pour entreprise sans avoir besoin de sa propre licence.

> [!IMPORTANT]
> Les licences basées sur les appareils pour Microsoft 365 Apps pour entreprise sont disponibles uniquement en tant que licences de modules de développement pour certains clients commerciaux et certains clients de l’éducation. Pour les clients commerciaux, la licence *est Microsoft 365 Apps for enterprise (appareil)* et n’est disponible que par le biais d’un abonnement contrat Entreprise/Contrat Entreprise. Pour les clients de l’éducation, la licence *est Microsoft 365 Apps pour l’Éducation (appareil)* et est disponible uniquement par le biais de l’inscription pour les solutions d’éducation (EES). Pour plus d’informations, lisez le billet de blog sur la [disponibilité de l’éducation.](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-device-based-subscription-for-education/) Pour la disponibilité commerciale, contactez votre représentant de compte Microsoft.

Pour commencer, vous créez un groupe dans le Centre d’administration Azure Active Directory, puis attribuez des appareils au groupe. Pour en savoir plus sur la gestion des licences d’appareils, notamment la configuration requise pour les appareils, les types de groupes que vous pouvez utiliser et la configuration des applications Microsoft 365 pour les entreprises pour utiliser la gestion des licences d’appareils, voir Licences basées sur les appareils pour [Microsoft 365 Apps for enterprise.](/deployoffice/device-based-licensing)

> [!IMPORTANT]
> Vous devez être un administrateur global pour effectuer les tâches de cet article.

## <a name="assign-licenses-to-devices"></a>Attribuer des licences à des appareils

Lorsque vous attribuez des licences à un groupe, vous attribuez des licences à tous les appareils du groupe. Vous ne pouvez affecter qu’un seul abonnement à un seul groupe.

1. Dans le Centre d’administration Microsoft 365, allez sur la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation.</a>
2. Dans la page **Licences,** choisissez **Microsoft 365 Apps pour l’Éducation (appareil)** ou **Microsoft 365 Apps pour entreprise (appareil).**
3. Sur la page suivante, choisissez un abonnement, puis **sélectionnez Attribuer des licences.**
4. Dans le **volet Attribuer des licences** à un volet de groupe, commencez à taper un nom de groupe, puis choisissez-le dans les résultats pour l’ajouter à la liste.
5. Choose **Assign,** then choose **Close**.

## <a name="unassign-licenses-from-devices"></a>Désattribuer des licences à des appareils

Lorsque vous désattribuez des licences à un groupe, vous supprimez les licences de tous les appareils du groupe. Toutes les applications et leurs données associées sont ensuite en lecture seule.

1. Dans le Centre d’administration, allez sur la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation.</a>
2. Dans la page **Licences,** choisissez **Microsoft 365 Apps pour l’Éducation (appareil)** ou **Microsoft 365 Apps pour entreprise (appareil).**
3. On the next page, choose a subscription, choose **More actions,** then choose **Unassign licenses**.
4. In the **Unassign licenses** dialog box, choose **Unassign**.