---
title: 'Étape 4 : Configurer la protection des informations Windows'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et déployez la protection des informations Windows dans Microsoft 365.
ms.openlocfilehash: e32b09c20e86ff927748f7aedd8b8d769e07916e
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34073559"
---
# <a name="step-4-configure-windows-information-protection"></a>Étape 4 : Configurer la protection des informations Windows

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

L’augmentation du nombre d’appareils personnels utilisés au travail entraîne un risque accru de fuite de données. Par exemple, un employé risque de diffuser par inadvertance l’image d’un plan marketing de futur produit sur un site de réseau social ou d’enregistrer un fichier contenant des informations hautement confidentielles sur son stockage cloud public. 

La Protection des informations Windows contribue à protéger contre ces types de fuites de données sur des appareils Windows 10. Pour plus d’informations, voir [Protéger vos données d’entreprise à l’aide de Protection des informations Windows](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).

Dans Microsoft 365 Entreprise, la Protection des informations Windows est une combinaison de Windows 10 Entreprise et de Microsoft Intune, fournie avec Enterprise Mobility + Security dans le cadre de votre abonnement. 

Pour déployer la Protection des informations Windows dans votre organisation avec Microsoft 365 Entreprise :

1. Inscrivez vos appareils Windows dans Intune. Vous devez avoir effectué cette opération à l’[Étape 5 : Gestion des appareils mobiles](mobility-infrastructure.md).
2. Créez une [stratégie Intune pour la Protection des informations Windows](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure).
  - Vérifiez que vous avez rempli votre liste d’applications protégées.
  - Choisissez votre niveau de Protection des informations Windows.

Vous pouvez également utiliser la Protection des informations Windows avec [System Center Configuration Manager](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/overview-create-wip-policy-sccm). 

Pour plus d’informations, voir [Meilleures pratiques de Protection des informations Windows]( https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/guidance-and-best-practices-wip).

Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step4) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante


|||
|:-------|:-----|
|![](./media/stepnumbers/Step5.png)|[Configurer la protection contre la perte de données d’Office 365](infoprotect-data-loss-prevention.md)|


