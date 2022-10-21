---
title: Reprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: katmartin
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment reprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse.
ms.openlocfilehash: 9b33f9be3bef3a3ae069866e5c31f724695913ee
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662992"
---
# <a name="reprovision-a-windows-365-cloud-pc-in-microsoft-365-lighthouse"></a>Reprovisionner un Windows 365 PC Cloud dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse prend en charge le reprovisionnement des PC cloud qui ont une stratégie d’approvisionnement. Vous devrez peut-être réapprovisionner un appareil pour un nouvel utilisateur ou si l’appareil ne fonctionne pas correctement. Lorsqu’un reprovisionnement est déclenché, le PC cloud est supprimé et recréé en tant que nouveau PC cloud. Toutes les données utilisateur, les applications et les personnalisations sont supprimées.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur de PC cloud dans le locataire partenaire.

## <a name="reprovision-a-windows-365-cloud-pc"></a>Reprovisionner un Windows 365 PC Cloud

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils** >  **Windows 365**.

2. Sélectionnez l’onglet **Tous les PC cloud** .

3. Dans la liste déroulante **Filtres** , sélectionnez le type de licence.

4. Dans la liste filtrée, sélectionnez un appareil.

5. Dans le volet détails de l’appareil, sélectionnez **Reprovisionner**.

6. Dans la boîte de dialogue de confirmation, sélectionnez **Reprovisionner**.

> [!NOTE]
> L’utilisateur actuel du PC cloud est immédiatement déconnecté et toutes les données utilisateur sont supprimées.

## <a name="check-the-device-action-status"></a>Vérifier l’état de l’action de l’appareil

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils** >  **Windows 365**.

2. Sélectionnez l’onglet **Tous les PC cloud** .

3. Dans la liste des appareils, sélectionnez un appareil.

4. Dans le volet Détails de l’appareil, sélectionnez l’onglet **État de l’action de l’appareil** .

L’onglet affiche toutes les actions actuelles mises en file d’attente pour cet appareil, notamment le type d’action, l’état et l’horodatage.

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de l’approvisionnement](/windows-365/enterprise/provisioning) (article)\
[Modifier les stratégies d’approvisionnement](/windows-365/enterprise/edit-provisioning-policy) (article)
