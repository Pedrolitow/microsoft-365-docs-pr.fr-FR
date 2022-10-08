---
title: Réinitialiser un appareil mobile dans Mobilité et sécurité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Utilisez la mobilité et la sécurité de base intégrées pour supprimer les informations des appareils inscrits.
ms.openlocfilehash: 314c9dcd4b68a3c809b1f59e60e061b9498e9834
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187380"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Réinitialiser un appareil mobile dans Mobilité et sécurité de base

Vous pouvez utiliser la mobilité et la sécurité de base intégrées pour Microsoft 365 afin de supprimer uniquement les informations organisationnelles, ou d’effectuer une réinitialisation d’usine pour supprimer toutes les informations d’un appareil mobile et les restaurer dans les paramètres d’usine.

## <a name="before-you-begin"></a>Avant de commencer

Les appareils mobiles peuvent stocker des informations d’organisation sensibles et fournir un accès aux ressources Microsoft 365 de votre organisation. Pour protéger les informations de votre organisation, vous pouvez réinitialiser ou supprimer des données d’entreprise :

- **Réinitialisation** d’usine : supprime toutes les données sur l’appareil mobile d’un utilisateur, y compris les applications installées, les photos et les informations personnelles. Une fois la réinitialisation terminée, l’appareil est restauré dans ses paramètres d’usine.

- **Supprimer les données d’entreprise** : supprime uniquement les données d’organisation et laisse les applications installées, les photos et les informations personnelles sur l’appareil mobile d’un utilisateur.

- **Lorsqu’un appareil est réinitialisé (réinitialisation d’usine ou suppression des données d’entreprise),** l’appareil est supprimé de la liste des appareils gérés.

- **Réinitialiser automatiquement un appareil** : vous pouvez configurer une stratégie de mobilité et de sécurité de base qui réinitialise automatiquement un appareil après que l’utilisateur a tenté sans succès d’entrer le mot de passe de l’appareil un nombre spécifique de fois. Pour ce faire, suivez les étapes décrites dans [Créer des stratégies de sécurité des appareils en matière de mobilité et de sécurité de base](create-device-security-policies.md).

- **Si vous souhaitez connaître l’expérience utilisateur** lors de la réinitialisation de son appareil, consultez [Quel est l’impact sur l’utilisateur et l’appareil ?](#whats-the-user-and-device-impact)

## <a name="wipe-a-mobile-device"></a>Réinitialiser un appareil mobile

1. Connectez-vous au Centre d'administration Microsoft 365 et accédez à la [page Mobile Gestion des appareils](https://portal.office.com/adminportal/home?#/MifoDevices).

1. Sélectionnez **Gérer les appareils**.

1. Sélectionnez l’appareil que vous voulez réinitialiser.

1. Sélectionnez **Gérer**.

1. Sélectionnez le type de réinitialisation à distance que vous voulez effectuer.

    - Pour effectuer une réinitialisation complète et restaurer l’appareil dans ses paramètres d’usine, sélectionnez **Réinitialisation d’usine**.
    - Pour effectuer une réinitialisation sélective et supprimer uniquement les informations de l’organisation Microsoft 365, **sélectionnez Supprimer les données d’entreprise**.
    - Pour supprimer l’appareil de votre organisation, **sélectionnez Supprimer l’appareil**.

1. Cliquez sur **Oui** pour confirmer.

## <a name="how-do-i-know-it-worked"></a>Comment faire sais-tu que ça a fonctionné ?

Vous ne voyez plus l’appareil mobile dans la liste des appareils gérés.

## <a name="why-would-you-want-to-wipe-a-device"></a>Pourquoi voulez-vous réinitialiser un appareil ?

Réinitialiser un appareil pour les raisons suivantes :

- Les appareils mobiles tels que les smartphones et les tablettes sont de plus en plus complets en permanence. Cela signifie qu’il est plus facile pour vos utilisateurs de stocker des informations d’entreprise sensibles telles que l’identification personnelle ou les communications confidentielles et d’y accéder en déplacement. Si l’un de ces appareils mobiles est perdu ou volé, la réinitialisation de l’appareil peut empêcher les informations de votre organisation de se retrouver entre de mauvaises mains.
- Lorsqu’un utilisateur quitte l’organisation avec un appareil personnel inscrit dans Mobilité et sécurité de base, vous pouvez empêcher les informations organisationnelles d’aller avec cet utilisateur en effectuant une réinitialisation d’usine.
- Si votre organisation fournit des appareils mobiles aux utilisateurs, vous devrez peut-être réaffecter des appareils de temps à autre. L’exécution d’une réinitialisation d’usine sur un appareil avant de l’affecter à un nouvel utilisateur permet de s’assurer que toutes les informations sensibles du propriétaire précédent sont supprimées.

## <a name="whats-the-user-and-device-impact"></a>Quel est l’impact sur l’utilisateur et l’appareil ?

La réinitialisation est envoyée immédiatement à l’appareil mobile et l’appareil est marqué comme non conforme dans Azure Active Directory. Bien que toutes les données soient supprimées lorsqu’un appareil est réinitialisé aux paramètres d’usine par défaut, le tableau suivant décrit le contenu supprimé pour chaque type d’appareil lorsqu’un appareil est supprimé lorsque vous supprimez des données d’entreprise.

|Impact sur le contenu|iOS|Android|
|---|---|---|
|Les données d’application Microsoft 365 sont réinitialisées si l’appareil est protégé par Intune stratégies App Protection. Les applications ne sont pas supprimées. Pour les appareils non protégés par les stratégies de gestion des applications mobiles (MAM), Outlook et OneDrive ne suppriment pas les données mises en cache.<br/>**Note** Pour appliquer Intune Protection d'applications stratégies, vous devez disposer d’une licence Intune.|Oui|Oui|
|Les paramètres de stratégie appliqués par mobilité et sécurité de base aux appareils ne sont plus appliqués ; les utilisateurs peuvent modifier les paramètres.|Oui|Oui|
|Email profils créés par Mobilité et sécurité de base sont supprimés et les e-mails mis en cache sur l’appareil sont supprimés.|Oui|N/A|

> [!NOTE]
> Portail d'entreprise application est disponible sur le App Store pour iOS et le Play Store pour appareils Android.
