---
title: Mettre à niveau vos utilisateurs Microsoft 365 vers le dernier client Office
f1.keywords:
- NOCSH
ms.author: kwekuako
author: kwekuako
manager: scotv
audience: Admin
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom:
- fwlink 824861; CampaignID O365_Comm_SR_UpgradeOffice
ms.assetid: f6b00895-b5fd-4af6-a656-b7788ea20cbb
description: Découvrez comment mettre à niveau vos utilisateurs vers le client Office le plus récent.
ms.openlocfilehash: 148069011784b822c5ce366190afd60bf278772f
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43627533"
---
# <a name="upgrade-your-microsoft-365-for-business-users-to-the-latest-office-client"></a>Mettre à niveau vos utilisateurs Microsoft 365 vers le dernier client Office

## <a name="office-2010-reaches-end-of-support"></a>Office 2010 atteint la fin de l’assistance

Office 2010 atteindra sa fin de support le 13 octobre 2020. Lorsque Office 2010 atteint sa fin de prise en charge, Microsoft ne fournit plus les éléments suivants :

- Support technique pour les problèmes

- Correctifs de bogues pour les problèmes découverts

- Correctifs de sécurité pour les vulnérabilités découvertes

Pour plus d’informations, voir la feuille [de route de fin d’assistance pour Office 2010](https://docs.microsoft.com/deployoffice/office-2010-end-support-roadmap) .

 **Est-ce la bonne rubrique pour vous ?**
  
 Si vous êtes l’administrateur responsable de l’abonnement Microsoft 365 pour les entreprises au sein de votre organisation, vous êtes au bon endroit. Les administrateurs sont généralement responsables des tâches telles que la gestion des utilisateurs, la réinitialisation des mots de passe, la gestion des installations d’Office et l’ajout ou la suppression de licences.

 Si vous n’êtes pas un administrateur et que vous disposez d’un produit de la [famille Microsoft 365](https://support.office.com/article/28cbc8cf-1332-4f04-9123-9b660abb629e.aspx#BKMK_OfficePlans) , consultez [la rubrique Comment mettre à niveau Office](https://support.office.com/article/ee68f6cf-422f-464a-82ec-385f65391350.aspx) pour obtenir des informations sur la mise à niveau de votre ancienne version d’Office.

## <a name="get-ready-to-upgrade"></a>Préparer la mise à niveau

En tant qu’administrateur, vous contrôlez la version des personnes Office de votre organisation pouvant être installées. Nous vous recommandons vivement d’aider les utilisateurs de votre organisation qui exécutent des versions antérieures d’Office, comme Office 2010, Office 2013 ou Office 2016 à effectuer une mise à niveau vers la dernière version, afin de tirer parti de ses améliorations en matière de sécurité et de productivité.

## <a name="upgrade-steps"></a>Étapes de mise à niveau

Les étapes ci-dessous vous guideront tout au long du processus de mise à niveau de vos utilisateurs vers le dernier client de bureau Office. Nous vous recommandons de lire ces étapes avant de commencer le processus de mise à niveau.
  
## <a name="step-1---check-system-requirements"></a>Étape 1 : vérifier la configuration système requise

[Vérifiez la configuration système requise](https://products.office.com/office-system-requirements) pour Office afin de vous assurer que vos appareils sont compatibles avec la dernière version d’Office. Par exemple, les versions plus récentes d’Office ne peuvent pas être installées sur des ordinateurs exécutant Windows XP ou Windows Vista.
  
> [!TIP]
> Si des utilisateurs de votre organisation exécutent des versions antérieures de Windows sur leurs PC ou ordinateurs portables, nous vous recommandons d’effectuer une mise à niveau vers Windows 10. Windows 7 a atteint la fin de la prise en charge. La [prise en charge de Windows 7 se termine au 1er janvier 2020](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support?rtc=1) pour plus d’informations.

Consultez la [Configuration requise pour Windows 10](https://www.microsoft.com/windows/windows-10-specifications) pour savoir si vous pouvez mettre à niveau les systèmes d’exploitation.

### <a name="check-application-compatibility"></a>Vérifier la compatibilité des applications

Pour garantir la réussite de la mise à niveau, nous vous recommandons d’identifier vos applications Office, y compris les scripts VBA, les macros, les compléments tiers et les documents et feuilles de calcul complexes, et d’évaluer leur compatibilité avec la dernière version d’Office.
  
Par exemple, si vous utilisez des compléments tiers avec votre installation d’Office actuelle, contactez le fabricant afin de vous assurer qu’ils sont compatibles avec la dernière version d’Office.
  
## <a name="step-2---check-your-existing-subscription-plan"></a>Étape 2 : vérifier votre plan d’abonnement existant

Certains plans Microsoft 365 n’incluent pas les versions de bureau complètes d’Office et les étapes de mise à niveau sont différentes si votre plan n’inclut pas Office.
  
Vous ne savez pas quel plan d’abonnement vous avez ? Consultez la rubrique [relative à l’abonnement Microsoft 365 pour les entreprises](../admin-overview/what-subscription-do-i-have.md) .
  
Si votre offre existante inclut Office, passez à l' [étape 3 : désinstaller Office](#step-3---uninstall-office).
  
Si votre offre existante n’inclut pas Office, sélectionnez l’une des options ci-dessous :
  
### <a name="upgrade-options-for-plans-that-dont-include-office"></a>Options de mise à niveau pour les plans qui n’incluent pas Office

 **Option 1 : modifier les abonnements Office**

Basculer vers un abonnement qui inclut Office. Voir [basculer vers une autre offre Microsoft 365 for Business](../../commerce/subscriptions/switch-to-a-different-plan.md).

**Option 2 : acheter des achats individuels d’Office, ou acheter Office par le biais d’une licence en volume**

 - Acheter un seul achat d’Office. Voir [Office famille &amp; ](https://products.office.com/home-and-business) ou [Office Professionnel](https://products.office.com/professional)

     OR

 - Acheter plusieurs copies d’Office par le biais d’une licence en volume. Consultez la rubrique [comparer les suites disponibles via le gestionnaire de licences en volume](https://products.office.com/business/microsoft-office-volume-licensing-suites-comparison).

## <a name="step-3---uninstall-office"></a>Étape 3 : désinstaller Office

Avant d’installer la dernière version d’Office, nous vous recommandons de désinstaller toutes les versions antérieures d’Office. Toutefois, si vous changez d’avis sur la mise à niveau d’Office, notez les instances suivantes où vous ne pourrez pas réinstaller Office après l’avoir désinstallé.
  
Nous vous recommandons d’utiliser des compléments tiers, de contacter le fabricant pour voir s’il existe une mise à jour qui fonctionnera avec la dernière version d’Office.

### <a name="select-the-version-of-office-you-want-to-uninstall"></a>Sélectionnez la version d’Office que vous souhaitez désinstaller

- [À partir d’un PC](https://support.office.com/article/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8.aspx)

- [À partir d’un Mac](https://support.office.com/article/eefa1199-5b58-43af-8a3d-b73dc1a8cae3.aspx)
  
### <a name="known-issues-trying-to-reinstall-older-versions-of-office-after-an-uninstall"></a>Problèmes connus lors de la tentative de réinstallation d’anciennes versions d’Office après une désinstallation

 **Office via une licence en volume** Si vous n’avez plus accès aux fichiers sources de ces versions de licence en volume d’Office, vous ne pourrez pas le réinstaller.

 **Office préinstallé sur votre ordinateur** Si vous n’avez plus de disque ni de clé de produit (si Office est fourni avec un), vous ne pourrez pas le réinstaller.

 **Abonnements non pris en charge** Si votre copie d’Office a été obtenue via des abonnements abandonnés, tels qu’Office 365 Small Business Premium ou Office 365 Mid-Size Business, vous ne pourrez pas installer une version antérieure d’Office, sauf si vous disposez de la clé de produit fournie avec votre abonnement.

Si vous préférez installer votre ancienne version d’Office avec la dernière version, vous pouvez consulter la liste des versions dans lesquelles cette version est prise en charge dans, [installer et utiliser différentes versions d’Office sur le même PC](https://support.office.com/article/6ebb44ce-18a3-43f9-a187-b78c513788bf.aspx). Une installation côte à côte peut être le bon choix pour vous, si, par exemple, vous avez installé des compléments tiers que vous utilisez avec votre ancienne version d’Office et que vous n’êtes pas encore sûr qu’ils sont compatibles avec la dernière version.

## <a name="step-4---assign-office-licenses-to-users"></a>Étape 4 : attribuer des licences Office à des utilisateurs

Si vous ne l’avez pas encore fait, attribuez des licences aux utilisateurs de votre organisation qui ont besoin d’installer Office, reportez-vous à [attribuer des licences aux utilisateurs dans Microsoft 365 pour les entreprises](../manage/assign-licenses-to-users.md).
  
## <a name="step-5---install-office"></a>Étape 5 : installer Office

Une fois que vous avez vérifié les utilisateurs que vous souhaitez mettre à niveau, la dernière étape consiste à installer Office, voir [Télécharger et installer ou réinstaller Office sur votre PC ou Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc4716658.aspx).
  
> [!TIP]
> Si vous ne souhaitez pas que vos utilisateurs installent Office eux-mêmes, consultez la rubrique [gérer les paramètres de téléchargement de logiciels dans office 365](https://docs.microsoft.com/DeployOffice/manage-software-download-settings-office-365). Vous pouvez utiliser l' [outil déploiement d’Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) pour télécharger le logiciel Office sur votre réseau local, puis déployer Office à l’aide de la méthode de déploiement de logiciels que vous utilisez généralement.
