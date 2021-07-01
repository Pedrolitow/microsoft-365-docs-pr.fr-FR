---
title: Désactiver l’option Mobility et Security de base
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Supprimez des groupes ou des stratégies pour désactiver la mobilité et la sécurité de base.
ms.openlocfilehash: 7ec4ec0d47668c21824d8e01e3845d637b9b0922
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53228134"
---
# <a name="turn-off-basic-mobility-and-security"></a>Désactiver l’option Mobility et Security de base

Pour désactiver efficacement la mobilité et la sécurité de base, vous supprimez des groupes de personnes définis par des groupes de sécurité des stratégies de gestion des appareils ou supprimez les stratégies elles-mêmes.

- Supprimez des groupes d’utilisateurs en supprimant des groupes de sécurité utilisateur des stratégies d’appareil que vous avez créées.

- Désactivez la mobilité et la sécurité de base pour tout le monde en supprimant toutes les stratégies d’appareil de mobilité et de sécurité de base.

Ces options suppriment l’application de la mobilité et de la sécurité de base pour les appareils de votre organisation. Malheureusement, vous ne pouvez pas simplement « mettre en service » Basic Mobility and Security après l’avoir installé.

> [!IMPORTANT]
> N’ignorez pas l’impact sur les appareils des utilisateurs lorsque vous supprimez des groupes de sécurité utilisateur des stratégies ou supprimez les stratégies elles-mêmes. Par exemple, les profils de messagerie et les e-mails mis en cache peuvent être supprimés, en fonction de l’appareil. Pour plus d’informations,  [voir que se passe-t-il lorsque](../../admin/basic-mobility-security/create-device-security-policies.md) vous supprimez une stratégie ou supprimez un utilisateur de la stratégie ?

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Supprimer des groupes de sécurité utilisateur des stratégies d’appareil de mobilité et de sécurité de base

1. Dans votre type de navigateur :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez une stratégie d’appareil, puis **sélectionnez Modifier la stratégie.**

3. Dans la page  **Déploiement,**   sélectionnez **Supprimer.**

4. Sous  **Groupes,** sélectionnez un groupe de sécurité.

5. Sélectionnez  **Supprimer,** puis **Enregistrer.**

## <a name="remove-basic-mobility-and-security-device-policies"></a>Supprimer des stratégies d’appareil de mobilité et de sécurité de base

1. Dans votre type de navigateur :  [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez une stratégie d’appareil, puis  **sélectionnez Supprimer la stratégie.**

3. Dans la boîte de dialogue Avertissement, sélectionnez **Oui.**

> [!NOTE]
> Pour plus d’informations sur la procédure de déblocage des appareils si les appareils de votre organisation sont toujours dans un état [bloqué,](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934)consultez le billet de blog sur la suppression du contrôle d’accès Gestion des périphériques mobiles pour Office 365 .
