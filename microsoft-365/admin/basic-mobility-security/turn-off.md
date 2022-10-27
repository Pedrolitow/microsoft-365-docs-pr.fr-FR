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
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
description: Supprimez des groupes ou des stratégies pour désactiver mobilité et sécurité de base.
ms.openlocfilehash: fe2e0fe8ba8a38890441316454a5b8ac4f6603ba
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719071"
---
# <a name="turn-off-basic-mobility-and-security"></a>Désactiver l’option Mobility et Security de base

Pour désactiver efficacement mobilité et sécurité de base, vous supprimez les groupes de personnes définis par les groupes de sécurité des stratégies de gestion des appareils ou supprimez les stratégies elles-mêmes.

- Supprimez des groupes d’utilisateurs en supprimant les groupes de sécurité d’utilisateurs des stratégies d’appareil que vous avez créées.

- Désactivez Mobilité et sécurité de base pour tout le monde en supprimant toutes les stratégies d’appareil Mobilité et Sécurité de base.

Ces options suppriment l’application mobilité et sécurité de base pour les appareils de votre organisation. Malheureusement, vous ne pouvez pas simplement « déprovisionner » mobilité et sécurité de base une fois que vous l’avez configuré.

> [!IMPORTANT]
> Tenez compte de l’impact sur les appareils des utilisateurs lorsque vous supprimez des groupes de sécurité d’utilisateurs des stratégies ou supprimez les stratégies elles-mêmes. Par exemple, les profils de messagerie et les e-mails mis en cache peuvent être supprimés, en fonction de l’appareil. Pour plus d’informations, consultez [Que se passe-t-il lorsque vous supprimez une stratégie ou supprimez un utilisateur de la stratégie ?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Supprimer des groupes de sécurité utilisateur des stratégies d’appareil Mobilité et Sécurité de base

1. Dans votre navigateur, tapez : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez une stratégie d’appareil, puis **Sélectionnez Modifier la stratégie**.

3. Dans la page **Déploiement** , sélectionnez **Supprimer**.

4. Sous **Groupes**, sélectionnez un groupe de sécurité.

5. Sélectionnez **Supprimer**, puis **Enregistrer**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Supprimer les stratégies d’appareil mobilité et sécurité de base

1. Dans votre navigateur, tapez : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez une stratégie d’appareil, puis **sélectionnez Supprimer la stratégie**.

3. Dans la boîte de dialogue Avertissement, sélectionnez **Oui**.

> [!NOTE]
> Pour plus d’informations sur le déblocage des appareils si les appareils de votre organisation sont toujours bloqués, consultez le billet [de blog Suppression de Access Control de Gestion des périphériques mobiles pour Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
