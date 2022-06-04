---
title: Valider les paramètres de protection des applications pour les PC Windows 10
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
description: Découvrez comment vérifier que les paramètres de protection des applications Microsoft 365 Business Premium ont pris effet sur les appareils Windows 10 de vos utilisateurs.
ms.openlocfilehash: 5ce28946c5df84ffe2bfac9d4cc52d4178996936
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893244"
---
# <a name="validate-device-protection-settings-for-windows-10-or-11-pcs"></a>Valider les paramètres de protection des appareils pour les PC Windows 10 ou 11

> [!NOTE]
> Microsoft Defender pour les PME est déployée pour les clients Microsoft 365 Business Premium, à compter du 1er mars 2022. Cette offre fournit des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-or-11-device-policies-are-set"></a>Vérifier que les stratégies d’appareil Windows 10 ou 11 sont définies

Après avoir configuré les stratégies d’appareil, l’application de la stratégie sur les appareils des [utilisateurs](../business-premium/m365bp-protection-settings-for-windows-10-devices.md) peut prendre jusqu’à quelques heures. Vous pouvez vérifier que les stratégies ont pris effet en examinant différents écrans paramètres Windows sur les appareils des utilisateurs. Étant donné que les utilisateurs ne pourront pas modifier les paramètres de Windows Update et de l’Antivirus Microsoft Defender sur leurs appareils Windows 10 ou 11, de nombreuses options seront grisées.
  
1. Accédez aux **options de redémarrage** de **sécurité de La mise à jour** **&amp;** \> **des paramètres** \> Windows Update \> et vérifiez que tous les paramètres sont grisés.

    ![Toutes les options de redémarrage sont grisées.](../business-premium/media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. Accédez aux **options** avancées de sécurité \> de la **mise à jour &amp;** **des paramètres** \> **Windows Update** \> et vérifiez que tous les paramètres sont grisés.

    ![Les options de mises à jour Avancées Windows sont toutes grisées.](../business-premium/media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. Accédez aux **options** \> avancées de sécurité \> de La mise à **jour &amp;** **des paramètres** \> **Windows Update** \> **. Choisissez la façon dont les mises à jour sont remises**.

    Vérifiez que vous pouvez voir le message (en rouge) indiquant que certains paramètres sont masqués ou gérés par votre organisation, et que toutes les options sont grisées.

    ![Choisissez la façon dont la page de remise des mises à jour indique que les paramètres sont masqués ou gérés par votre organisation.](../business-premium/media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. Pour ouvrir le Centre de sécurité Windows Defender, accédez à **Paramètres** **Mettre à jour &amp; la sécurité** \> **Windows Defender** \> en cliquant sur Ouvrir **les paramètres de protection &amp;**\> antivirus contre les virus **du Centre** \> **&amp;** de sécurité Windows Defender.\>

5. Vérifiez que toutes les options sont grisées.

    ![Les paramètres virus et protection contre les menaces sont grisés.](../business-premium/media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>Contenu connexe

[Documentation et ressources Microsoft 365 pour les entreprises](/admin)

[Définir les configurations d’appareil pour les PC](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 Windows 10 [Meilleures pratiques pour la sécurisation de Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Objectif suivant

[Examiner et modifier les stratégies de protection](m365bp-view-edit-create-mdb-policies.md)
