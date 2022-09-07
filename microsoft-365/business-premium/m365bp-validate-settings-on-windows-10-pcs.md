---
title: Valider les paramètres de protection des applications pour Windows 10 PC
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: Découvrez comment vérifier que Microsoft 365 Business Premium paramètres de protection des applications ont pris effet sur les appareils Windows 10 de vos utilisateurs.
ms.openlocfilehash: bab1eea1bff77d559e160b8c363ad7c0a91b4100
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67614261"
---
# <a name="validate-device-protection-settings-for-windows-10-or-11-pcs"></a>Valider les paramètres de protection des appareils pour Windows 10 ou 11 PC

## <a name="verify-that-windows-10-or-11-device-policies-are-set"></a>Vérifier que Windows 10 ou 11 stratégies d’appareil sont définies

Après avoir configuré les stratégies d’appareil, l’application de la stratégie sur les appareils des [utilisateurs](../business-premium/m365bp-protection-settings-for-windows-10-devices.md) peut prendre jusqu’à quelques heures. Vous pouvez vérifier que les stratégies ont pris effet en examinant différents écrans paramètres Windows sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres de l’antivirus Windows Update et Microsoft Defender sur leurs Windows 10 ou 11 appareils, de nombreuses options seront grisées.
  
1. Accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Update** \> **Options de redémarrage** et vérifiez que tous les paramètres sont grisés.

    ![Toutes les options de redémarrage sont grisées.](../business-premium/media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Update** \> **Options avancées** et vérifiez que tous les paramètres sont grisés.

    ![Les options de mises à jour Avancées Windows sont toutes grisées.](../business-premium/media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Accédez à La sécurité \> des mises **à jour &amp;** **des paramètres** \> **Windows Update** \> **Options** \> avancées **Choisir la façon dont les mises à jour sont remises**.

    Vérifiez que vous pouvez voir le message (en rouge) indiquant que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.

    ![Choisissez la façon dont la page de remise des mises à jour indique que les paramètres sont masqués ou gérés par votre organisation.](../business-premium/media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le centre de sécurité Windows Defender, accédez à **Paramètres** \> **mettre à jour &amp; la sécurité** \> **Windows Defender** \> cliquez sur Ouvrir Windows Defender **paramètres de protection &amp;**\> antivirus contre les menaces virus **de Security Center** \> **&amp;**.

5. Vérifiez que toutes les options sont grisées.

    ![Les paramètres virus et protection contre les menaces sont grisés.](../business-premium/media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Contenu associé

[Documentation et ressources Microsoft 365 pour les entreprises](/admin)

[Définir des configurations d’appareil pour Windows 10 PC](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
[Meilleures pratiques pour la sécurisation de Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Objectif suivant

[Examiner et modifier les stratégies de protection](m365bp-view-edit-create-mdb-policies.md)
