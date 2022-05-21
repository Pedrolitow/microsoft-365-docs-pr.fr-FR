---
title: Valider les paramètres de protection des applications pour Windows 10 PC
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
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
description: Découvrez comment vérifier que les paramètres de protection des applications Microsoft 365 pour les entreprises ont pris effet sur les appareils Windows 10 de vos utilisateurs.
ms.openlocfilehash: daaf9f03b9b4abdac25076ca6e6fcd42d0982bb6
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623724"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>Valider les paramètres de protection des appareils pour Windows 10 PC

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>Vérifier que Windows 10 stratégies d’appareil sont définies

Après avoir configuré les stratégies d’appareil, l’application de la stratégie sur les appareils des [utilisateurs](../business-premium/m365bp-protection-settings-for-windows-10-devices.md) peut prendre jusqu’à quelques heures. Vous pouvez vérifier que les stratégies ont pris effet en examinant différents écrans Windows Paramètres sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres Windows Update et Antivirus Microsoft Defender sur leurs appareils Windows 10, de nombreuses options seront grisées.
  
1. Accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Update** \> **les options de redémarrage** et vérifiez que tous les paramètres sont grisés.

    ![Toutes les options de redémarrage sont grisées.](../business-premium/media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Update** \> **options avancées** et vérifiez que tous les paramètres sont grisés.

    ![Windows Les options de mises à jour avancées sont toutes grisées.](../business-premium/media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Update** \> Options \> **avancées** **Choisir la façon dont les mises à jour sont remises**.

    Vérifiez que vous pouvez voir le message (en rouge) indiquant que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.

    ![Choisissez la façon dont la page de remise des mises à jour indique que les paramètres sont masqués ou gérés par votre organisation.](../business-premium/media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le centre de sécurité Windows Defender, accédez à **Paramètres** \> **Mettre à jour &amp; la sécurité** \> **Windows Defender** \> cliquez sur Ouvrir Windows Defender paramètres de **protection antivirus contre les virus de Security Center &amp;**  \> \> **&amp;**.

5. Vérifiez que toutes les options sont grisées.

    ![Les paramètres virus et protection contre les menaces sont grisés.](../business-premium/media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Contenu connexe

[Microsoft 365 pour les ressources et la documentation métier](/admin)

[Définir des configurations d’appareil pour Windows 10 pratiques PCSBest](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [pour la sécurisation des Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)
