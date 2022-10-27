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
- Tier3
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
ms.openlocfilehash: d634c68b810135534f403c76106789b8701aea44
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68725933"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Réinitialiser un appareil mobile dans Mobilité et sécurité de base

Vous pouvez utiliser la mobilité et la sécurité de base intégrées pour Microsoft 365 pour supprimer uniquement les informations organisationnelles, ou pour effectuer une réinitialisation aux paramètres d’usine pour supprimer toutes les informations d’un appareil mobile et les restaurer dans les paramètres d’usine.

## <a name="before-you-begin"></a>Avant de commencer

Les appareils mobiles peuvent stocker des informations organisationnelles sensibles et fournir un accès aux ressources Microsoft 365 de votre organisation. Pour protéger les informations de votre organisation, vous pouvez effectuer une réinitialisation aux paramètres d’usine ou supprimer des données d’entreprise :

- **Réinitialisation aux paramètres d’usine** : supprime toutes les données sur l’appareil mobile d’un utilisateur, y compris les applications installées, les photos et les informations personnelles. Une fois la réinitialisation terminée, l’appareil est restauré à ses paramètres d’usine.

- **Supprimer les données de l’entreprise** : supprime uniquement les données de l’organisation et laisse les applications, photos et informations personnelles installées sur l’appareil mobile d’un utilisateur.

- **Lorsqu’un appareil est réinitialisé (Réinitialisation aux paramètres d’usine ou Suppression des données d’entreprise),** l’appareil est supprimé de la liste des appareils gérés.

- **Réinitialiser automatiquement un appareil** : vous pouvez configurer une stratégie mobilité et sécurité de base qui réinitialise automatiquement les paramètres d’usine d’un appareil après que l’utilisateur n’a pas essayé d’entrer le mot de passe de l’appareil un nombre spécifique de fois. Pour ce faire, suivez les étapes décrites dans [Créer des stratégies de sécurité d’appareil dans la mobilité et la sécurité de base](create-device-security-policies.md).

- **Si vous souhaitez connaître l’expérience utilisateur** lors de la réinitialisation de son appareil, consultez [Quel est l’impact sur l’utilisateur et l’appareil ?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Réinitialiser un appareil mobile

1. Connectez-vous au Centre d'administration Microsoft 365 et accédez à la [page Mobile Gestion des appareils](https://portal.office.com/adminportal/home?#/MifoDevices).

1. Sélectionnez **Gérer les appareils**.

1. Sélectionnez l’appareil que vous voulez réinitialiser.

1. Sélectionnez **Gérer**.

1. Sélectionnez le type de réinitialisation à distance que vous voulez effectuer.

    - Pour effectuer une réinitialisation complète et restaurer les paramètres d’usine de l’appareil, sélectionnez **Réinitialisation aux paramètres d’usine**.
    - Pour effectuer une réinitialisation sélective et supprimer uniquement les informations de l’organisation Microsoft 365, sélectionnez **Supprimer les données de l’entreprise**.
    - Pour supprimer l’appareil de votre organisation, sélectionnez **Supprimer l’appareil**.

1. Cliquez sur **Oui** pour confirmer.

## <a name="how-do-i-know-it-worked"></a>Comment faire savez que ça a fonctionné ?

Vous ne voyez plus l’appareil mobile dans la liste des appareils gérés.

## <a name="why-would-you-want-to-wipe-a-device"></a>Pourquoi souhaitez-vous réinitialiser un appareil ?

Réinitialiser un appareil pour les raisons suivantes :

- Les appareils mobiles comme les smartphones et les tablettes deviennent de plus en plus complets. Cela signifie qu’il est plus facile pour vos utilisateurs de stocker des informations d’entreprise sensibles telles que des informations d’identification personnelles ou des communications confidentielles et d’y accéder en déplacement. Si l’un de ces appareils mobiles est perdu ou volé, la réinitialisation de l’appareil peut aider à empêcher les informations de votre organisation de se retrouver entre de mauvaises mains.
- Lorsqu’un utilisateur quitte l’organisation avec un appareil personnel inscrit à Mobilité et sécurité de base, vous pouvez empêcher les informations organisationnelles d’aller avec cet utilisateur en effectuant une réinitialisation aux paramètres d’usine.
- Si votre organisation fournit des appareils mobiles aux utilisateurs, vous devrez peut-être réaffecter des appareils de temps à autre. Effectuer une réinitialisation aux paramètres d’usine sur un appareil avant de l’attribuer à un nouvel utilisateur permet de s’assurer que toutes les informations sensibles du propriétaire précédent sont supprimées.

## <a name="whats-the-user-and-device-impact"></a>Quel est l’impact sur l’utilisateur et l’appareil ?

La réinitialisation est envoyée immédiatement à l’appareil mobile et l’appareil est marqué comme non conforme dans Azure Active Directory. Bien que toutes les données sont supprimées lorsqu’un appareil est réinitialisé aux paramètres d’usine par défaut, le tableau suivant décrit le contenu supprimé pour chaque type d’appareil lorsqu’un appareil supprime des données d’entreprise.

|Impact sur le contenu|iOS|Android|
|---|---|---|
|Les données de l’application Microsoft 365 sont effacées si l’appareil est protégé par Intune stratégies De protection des applications. Les applications ne sont pas supprimées. Pour les appareils non protégés par les stratégies de gestion des applications mobiles (GAM), Outlook et OneDrive ne suppriment pas les données mises en cache.<br/>**Note** Pour appliquer des stratégies Intune Protection d'applications, vous devez disposer d’une licence Intune.|Oui|Oui|
|Les paramètres de stratégie appliqués par Basic Mobility and Security aux appareils ne sont plus appliqués; les utilisateurs peuvent modifier les paramètres.|Oui|Oui|
|Email profils créés par Basic Mobility and Security sont supprimés et les e-mails mis en cache sur l’appareil sont supprimés.|Oui|N/A|

> [!NOTE]
> Portail d'entreprise application est disponible sur le App Store pour iOS et le Play Store pour les appareils Android.
