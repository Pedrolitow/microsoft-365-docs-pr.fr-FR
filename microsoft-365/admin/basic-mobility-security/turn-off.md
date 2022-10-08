---
title: Désactiver l’option Mobility et Security de base
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Supprimez des groupes ou des stratégies pour désactiver la mobilité et la sécurité de base.
ms.openlocfilehash: 282e453c996978e98b12700a499adbaf02a75757
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68190394"
---
# <a name="turn-off-basic-mobility-and-security"></a>Désactiver l’option Mobility et Security de base

Pour désactiver efficacement la mobilité et la sécurité de base, vous supprimez des groupes de personnes définis par des groupes de sécurité des stratégies de gestion des appareils, ou vous supprimez les stratégies elles-mêmes.

- Supprimez des groupes d’utilisateurs en supprimant les groupes de sécurité utilisateur des stratégies d’appareil que vous avez créées.

- Désactivez la mobilité et la sécurité de base pour tout le monde en supprimant toutes les stratégies d’appareil de mobilité et de sécurité de base.

Ces options suppriment l’application de la sécurité et de la mobilité de base pour les appareils de votre organisation. Malheureusement, vous ne pouvez pas simplement « annuler l’approvisionnement » de la mobilité et de la sécurité de base une fois que vous l’avez configurée.

> [!IMPORTANT]
> Tenez compte de l’impact sur les appareils des utilisateurs lorsque vous supprimez des groupes de sécurité utilisateur des stratégies ou supprimez les stratégies elles-mêmes. Par exemple, les profils de messagerie et les e-mails mis en cache peuvent être supprimés, en fonction de l’appareil. Pour plus d’informations, voir [Que se passe-t-il lorsque vous supprimez une stratégie ou supprimez un utilisateur de la stratégie ?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Supprimer des groupes de sécurité utilisateur des stratégies d’appareil mobilité et sécurité de base

1. Dans votre type de navigateur : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez une stratégie d’appareil, puis **modifiez la stratégie**.

3. Dans la page **Déploiement** , **sélectionnez Supprimer**.

4. Sous **Groupes**, sélectionnez un groupe de sécurité.

5. Sélectionnez **Supprimer**, puis **Enregistrer**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Supprimer les stratégies d’appareil mobilité et sécurité de base

1. Dans votre type de navigateur : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez une stratégie d’appareil, puis **sélectionnez Supprimer la stratégie**.

3. Dans la boîte de dialogue Avertissement, sélectionnez **Oui**.

> [!NOTE]
> Pour plus d’étapes pour débloquer des appareils si les appareils de votre organisation sont toujours bloqués, consultez le billet [de blog Supprimant Access Control de Gestion des périphériques mobiles pour Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
