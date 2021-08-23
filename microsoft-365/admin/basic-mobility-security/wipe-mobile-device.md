---
title: Effacement d’un appareil mobile dans Basic Mobility and Security
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
- admindeeplinkMAC
search.appverid:
- MET150
description: Utilisez la mobilité et la sécurité de base intégrées pour supprimer des informations des appareils inscrits.
ms.openlocfilehash: d9c31a037dfce1ad2a13cce8b384ebdbcc5164b9
ms.sourcegitcommit: a7b289b8cc3a2eb79d5e46f20f2968adc0237da1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2021
ms.locfileid: "58394311"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Effacement d’un appareil mobile dans Basic Mobility and Security

Vous pouvez utiliser la mobilité et la sécurité de base intégrées pour Microsoft 365 pour supprimer uniquement les informations organisationnelles, ou pour effectuer une réinitialisation aux paramètres d’usine pour supprimer toutes les informations d’un appareil mobile et les restaurer aux paramètres d’usine.

## <a name="before-you-begin"></a>Avant de commencer

Les appareils mobiles peuvent stocker des informations organisationnelles sensibles et fournir l’accès aux ressources Microsoft 365 de votre organisation. Pour protéger les informations de votre organisation, vous pouvez réinitialiser ou supprimer des données d’entreprise aux usine :

- **Réinitialisation** aux usine : supprime toutes les données sur l’appareil mobile d’un utilisateur, y compris les applications installées, les photos et les informations personnelles. Une fois l’effacement terminé, l’appareil est rétabli à ses paramètres d’usine.

- **Supprimer des données d’entreprise**: supprime uniquement les données de l’organisation et laisse les applications installées, les photos et les informations personnelles sur l’appareil mobile d’un utilisateur.

- **Lorsqu’un appareil est** réinitialisé (réinitialisation d’usine ou suppression des données d’entreprise), l’appareil est supprimé de la liste des appareils gérés.
    
- **Réinitialiser** automatiquement un appareil : vous pouvez configurer une stratégie de mobilité et de sécurité de base qui réinitialise automatiquement un appareil après que l’utilisateur a tenté sans succès d’entrer le mot de passe de l’appareil un certain nombre de fois. Pour ce faire, suivez les étapes de la procédure de création de stratégies de sécurité des appareils [dans la mobilité et la sécurité de base.](create-device-security-policies.md)
    
- **Si vous souhaitez connaître l’expérience** utilisateur lorsque vous effacez son appareil, voir   [quel est l’impact sur l’utilisateur et l’appareil ?](#whats-the-user-and-device-impact)

## <a name="wipe-a-mobile-device"></a>Effacer un appareil mobile

1. Go to the [Centre d’administration Microsoft 365](../../admin/admin-overview/about-the-admin-center.md).

2. Tapez Gestion des appareils mobiles dans le champ de recherche, puis sélectionnez **Gestion des** périphériques mobiles dans la liste des résultats.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Option de gestion des appareils mobiles Basic Mobility and Secruity":::

3. Sélectionnez **Gérer les appareils.**

4. Sélectionnez l’appareil que vous voulez réinitialiser.

5. Sélectionnez **Gérer**.

6. Sélectionnez le type de réinitialisation à distance que vous voulez effectuer.

    - Pour réinitialiser entièrement l’appareil et restaurer ses paramètres d’usine, sélectionnez **Réinitialisation aux paramètres d’usine.**
    - Pour faire une effacement sélective et supprimer uniquement Microsoft 365'organisation, **sélectionnez Supprimer les données de l’entreprise.**
    - Pour supprimer l’appareil de votre organisation, **sélectionnez Supprimer l’appareil.**

7. Cliquez sur **Oui** pour confirmer.

## <a name="how-do-i-know-it-worked"></a>Comment savoir si cela a fonctionné ?

L’appareil mobile ne figure plus dans la liste des appareils gérés.

## <a name="why-would-you-want-to-wipe-a-device"></a>Pourquoi voulez-vous effacer un appareil ?

Effacez un appareil pour les raisons suivantes :

- Les appareils mobiles tels que les smartphones et les tablettes sont toujours plus complets. Cela signifie qu’il est plus facile pour vos utilisateurs de stocker des informations d’entreprise sensibles, telles que des informations d’identification personnelle ou des communications confidentielles, et d’y accéder en libre-service. Si l’un de ces appareils mobiles est perdu ou volé, la wiping de l’appareil peut aider à empêcher que les informations de votre organisation ne se terminent entre de mauvaises mains.
- Lorsqu’un utilisateur quitte l’organisation avec un appareil personnel inscrit à Basic Mobility and Security, vous pouvez empêcher les informations organisationnelles de passer avec cet utilisateur en réinitialisation d’usine.
- Si votre organisation fournit des appareils mobiles aux utilisateurs, vous devrez peut-être réaffecter des appareils de temps à autre. La réinitialisation d’usine sur un appareil avant de l’affecter à un nouvel utilisateur permet de s’assurer que toutes les informations sensibles du propriétaire précédent sont supprimées.

## <a name="whats-the-user-and-device-impact"></a>Quel est l’impact sur l’utilisateur et l’appareil ?

La effacement est envoyée immédiatement à l’appareil mobile et l’appareil est marqué comme non conforme dans Azure Active Directory. Bien que toutes les données sont supprimées lorsqu’un appareil est réinitialisé aux paramètres d’usine par défaut, le tableau suivant décrit le contenu supprimé pour chaque type d’appareil lorsqu’un appareil est supprimé lorsque vous supprimez des données d’entreprise.

|**Impact sur le contenu**|**iOS 10 et les ultérieures**|**Android 5 et version ultérieure**|
|:-----|:-----|:-----|
|Microsoft 365 données d’application sont effacées si l’appareil est protégé par les stratégies Intune App Protection. Les applications ne sont pas supprimées. Pour les appareils non protégés par les stratégies de gestion des applications mobiles (MAM), Outlook et OneDrive ne suppriment pas les données mises en cache.<br/>**Remarque** Pour appliquer des stratégies intune App Protection, vous devez avoir une licence Intune.|Oui|Oui|
|Les paramètres de stratégie appliqués par Basic Mobility and Security aux appareils ne sont plus appliqués ; les utilisateurs peuvent modifier les paramètres.|Oui|Oui|
|Les profils de messagerie créés par Basic Mobility and Security sont supprimés et les messages électroniques mis en cache sur l’appareil sont supprimés.|Oui|N/D|

> [!NOTE]
> Portail d’entreprise’application est disponible dans l’App Store pour iOS et le Play Store pour les appareils Android.
