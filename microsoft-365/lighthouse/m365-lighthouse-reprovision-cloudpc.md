---
title: Réapprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment réapprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse.
ms.openlocfilehash: c896724a86241c19c6f44e4c59d7c2e927f100a7
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438945"
---
# <a name="reprovision-a-windows-365-cloud-pc-in-microsoft-365-lighthouse"></a>Réapprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse prend en charge le reprovisionnement des PC cloud qui ont une stratégie d’approvisionnement. Vous devrez peut-être réapprovisionner un appareil pour un nouvel utilisateur ou si l’appareil ne fonctionne pas correctement. Quand un reprovisionnement est déclenché, le PC cloud est supprimé puis recréé en tant que nouveau PC cloud.L’ensemble des données utilisateur, des applications, des personnalisations, etc., seront supprimées.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur de PC cloud dans le locataire partenaire.

## <a name="reprovision-a-windows-365-cloud-pc"></a>Réapprovisionner un Windows 365 PC Cloud

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Windows 365**.

2. Sélectionnez l’onglet **Tous les PC cloud** .

3. Dans la liste déroulante **Filtres** , sélectionnez le type de licence.

4. Dans la liste filtrée, sélectionnez un appareil.

5. Dans le volet détails de l’appareil, sélectionnez **Reprovisionner**.

6. Dans la boîte de dialogue de confirmation, sélectionnez **Reprovisionner**.

> [!NOTE]
> L’utilisateur actuel du PC cloud est immédiatement déconnecté et toutes les données utilisateur sont supprimées.

## <a name="check-the-device-action-status"></a>Vérifier l’état de l’action de l’appareil

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Windows 365**.

2. Sélectionnez l’onglet **Tous les PC cloud** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet d’informations de l’appareil, sélectionnez l’onglet **État de l’action de l’appareil** .

L’onglet affiche toutes les actions actuelles mises en file d’attente pour cet appareil, y compris le type d’action, l’état et l’horodatage.

## <a name="related-content"></a>Contenu connexe

[Vue d’ensemble de l’approvisionnement](/windows-365/enterprise/provisioning) (article)\
[Modifier les stratégies d’approvisionnement](/windows-365/enterprise/edit-provisioning-policy) (article)