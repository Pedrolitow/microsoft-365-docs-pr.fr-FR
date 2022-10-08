---
title: Mettre à niveau votre office 2010 vers Microsoft 365 - Administrateur Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom:
- fwlink 824861; CampaignID
- O365_Comm_SR_UpgradeOffice
- seo-marvel-may2020
- fwlink 824861; CampaignID O365_Comm_SR_UpgradeOffice
- AdminSurgePortfolio
ms.assetid: f6b00895-b5fd-4af6-a656-b7788ea20cbb
description: Découvrez comment mettre à niveau Microsoft Office vers le dernier client Office pour les utilisateurs de votre organisation.
ms.topic: article
ms.openlocfilehash: af36da23a8de502b1ec4377d3477dce9a5eac446
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68199832"
---
# <a name="upgrade-your-microsoft-365-for-business-users-to-the-latest-office-client"></a>Mettre à niveau votre Microsoft 365 pour les utilisateurs professionnels vers le dernier client Office

## <a name="office-2010-reaches-end-of-support"></a>Office 2010 atteint la fin du support

Office 2010 a atteint sa fin de support le 13 octobre 2020. Microsoft ne fournira plus les éléments suivants :

- Support technique pour les problèmes

- Correctifs de bogues pour les problèmes détectés

- Correctifs de sécurité pour les vulnérabilités découvertes

Pour plus d’informations, consultez la [feuille de route de fin du support Office 2010](/deployoffice/endofsupport/office-2010-end-support-roadmap) .

 **Est-ce la bonne rubrique pour vous ?**
  
 Si vous êtes l’administrateur responsable de l’abonnement Microsoft 365 pour les entreprises dans votre organisation, vous êtes au bon endroit. Les administrateurs sont généralement responsables de tâches telles que la gestion des utilisateurs, la réinitialisation des mots de passe, la gestion des installations Office et l’ajout ou la suppression de licences.

 Si vous n’êtes pas administrateur et que vous disposez d’un produit [Microsoft 365 Famille](https://support.microsoft.com/office/28cbc8cf-1332-4f04-9123-9b660abb629e#BKMK_OfficePlans), consultez [Comment faire mettre à niveau Office](https://support.microsoft.com/office/ee68f6cf-422f-464a-82ec-385f65391350) pour plus d’informations sur la mise à niveau de votre ancienne version d’Office à domicile.

## <a name="get-ready-to-upgrade-to-microsoft-365"></a>Préparer la mise à niveau vers Microsoft 365

En tant qu’administrateur, vous contrôlez la version des personnes Office de votre organisation qui peuvent être installées. Nous vous recommandons vivement d’aider les utilisateurs de votre organisation à exécuter des versions antérieures d’Office telles qu’Office 2010, Office 2013 ou Office 2016 à mettre à niveau vers la dernière version pour tirer parti de ses améliorations en matière de sécurité et de productivité.

## <a name="upgrade-steps"></a>Étapes de mise à niveau

Les étapes ci-dessous vous guideront tout au long du processus de mise à niveau de vos utilisateurs vers le dernier client de bureau Office. Nous vous recommandons de lire ces étapes avant de commencer le processus de mise à niveau.
  
## <a name="step-1---check-system-requirements"></a>Étape 1 : Vérifier la configuration système requise

[Vérifiez la configuration système requise](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources) pour Office afin de vous assurer que vos appareils sont compatibles avec la dernière version d’Office. Par exemple, les versions plus récentes d’Office ne peuvent pas être installées sur les ordinateurs exécutant Windows XP ou Windows Vista.
  
> [!TIP]
> Si des utilisateurs de votre organisation exécutent des versions antérieures de Windows sur leurs PC ou ordinateurs portables, nous vous recommandons d’effectuer une mise à niveau vers Windows 10. Windows 7 a atteint la fin du support. Pour plus d’informations, consultez [La prise en charge de Windows 7 se termine en janvier 2020](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support?rtc=1) .

Découvrez la [configuration système requise Windows 10](https://www.microsoft.com/windows/windows-10-specifications) pour voir si vous pouvez mettre à niveau leurs systèmes d’exploitation.

### <a name="check-application-compatibility"></a>Vérifier la compatibilité des applications

Pour garantir la réussite de la mise à niveau, nous vous recommandons d’identifier vos applications Office, notamment les scripts VBA, les macros, les compléments tiers et les documents et feuilles de calcul complexes, et d’évaluer leur compatibilité avec la dernière version d’Office.
  
Par exemple, si vous utilisez des compléments tiers avec votre installation Office actuelle, contactez la fabrique pour vous assurer qu’elles sont compatibles avec la dernière version d’Office.
  
## <a name="step-2---check-your-existing-subscription-plan"></a>Étape 2 : Vérifier votre plan d’abonnement existant

Certains plans Microsoft 365 n’incluent pas les versions complètes d’Office et les étapes de mise à niveau sont différentes si votre plan n’inclut pas Office.
  
Vous ne savez pas quel plan d’abonnement vous avez ? Voir [l’abonnement Microsoft 365 pour les entreprises que j’ai ?](../admin-overview/what-subscription-do-i-have.md)
  
Si votre plan existant inclut Office, passez à [l’étape 3 - Désinstaller Office](#step-3---uninstall-office).
  
Si votre plan existant n’inclut pas Office, sélectionnez parmi les options ci-dessous :
  
### <a name="upgrade-options-for-plans-that-dont-include-office"></a>Options de mise à niveau pour les plans qui n’incluent pas Office

 **Option 1 : Changer d’abonnement Office**

Basculez vers un abonnement qui inclut Office. Voir [Basculer vers un autre plan Microsoft 365 pour les entreprises](../../commerce/subscriptions/switch-to-a-different-plan.md).

**Option 2 : Acheter des achats individuels et uniques d’Office ou acheter Office par le biais d’une licence en volume**

 - Achetez un achat individuel et unique d’Office. Voir [Office Famille &amp; Entreprise](https://www.microsoft.com/microsoft-365/buy/compare-all-microsoft-365-products-b) ou [Office Professionnel](https://www.microsoft.com/microsoft-365/p/office-professional-2019/CFQ7TTC0K7C5/)

     OR

 - Achetez plusieurs copies d’Office via une licence en volume. Voir [, Comparer les suites disponibles via les licences en volume](https://products.office.com/business/microsoft-office-volume-licensing-suites-comparison).

## <a name="step-3---uninstall-office"></a>Étape 3 : Désinstaller Office

Avant d’installer la dernière version d’Office, nous vous recommandons de désinstaller toutes les versions antérieures d’Office. Toutefois, si vous changez d’avis sur la mise à niveau d’Office, notez les instances suivantes où vous ne pourrez pas réinstaller Office après l’avoir désinstallé.
  
Si vous avez des compléments tiers, contactez le fabricant pour voir s’il existe une mise à jour qui fonctionnera avec la dernière version d’Office.

> [!TIP]
> Si vous rencontrez des problèmes lors de la désinstallation d’Office, vous pouvez utiliser l’outil Support Microsoft et l’Assistant Récupération pour vous aider à supprimer Office : [Télécharger et exécuter l’Support Microsoft et l’Assistant Récupération](https://go.microsoft.com/fwlink/?LinkID=2155008).

### <a name="select-the-version-of-office-you-want-to-uninstall"></a>Sélectionnez la version d’Office à désinstaller

- [À partir d’un PC](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8)

- [À partir d’un Mac](https://support.microsoft.com/office/eefa1199-5b58-43af-8a3d-b73dc1a8cae3)
  
### <a name="known-issues-trying-to-reinstall-older-versions-of-office-after-an-uninstall"></a>Problèmes connus lors de la tentative de réinstallation d’anciennes versions d’Office après une désinstallation

 **Office via une licence en volume** Si vous n’avez plus accès aux fichiers sources de ces versions de licence en volume d’Office, vous ne pourrez pas le réinstaller.

 **Office préinstallé sur votre ordinateur** Si vous n’avez plus de disque ou de clé de produit (si Office en a une), vous ne pourrez pas la réinstaller.

 **Abonnements non pris en charge** Si votre copie d’Office a été obtenue par le biais d’abonnements abandonnés, tels que Office 365 Petite Entreprise Premium ou Office 365 Entreprise de taille moyenne, vous ne pourrez pas installer une version antérieure d’Office, sauf si vous disposez de la clé de produit associée à votre abonnement.

Si vous préférez installer votre ancienne version d’Office côte à côte avec la dernière version, vous pouvez voir la liste des versions dans lesquelles cela est pris en charge, [installer et utiliser différentes versions d’Office sur le même PC](https://support.microsoft.com/office/6ebb44ce-18a3-43f9-a187-b78c513788bf). Une installation côte à côte peut être le bon choix pour vous, si, par exemple, vous avez installé des compléments tiers que vous utilisez avec votre ancienne version d’Office et que vous n’êtes pas encore sûr qu’ils sont compatibles avec la dernière version.

## <a name="step-4---assign-office-licenses-to-users"></a>Étape 4 : Attribuer des licences Office aux utilisateurs

Si vous ne l’avez pas déjà fait, attribuez des licences à tous les utilisateurs de votre organisation qui doivent installer Office. Consultez [Attribuer des licences aux utilisateurs dans Microsoft 365 pour les entreprises](../manage/assign-licenses-to-users.md).
  
## <a name="step-5---install-office"></a>Étape 5 : Installer Office

Une fois que vous avez vérifié que les utilisateurs que vous souhaitez mettre à niveau disposent tous de licences, la dernière étape consiste à les faire installer Office, voir [Télécharger et installer ou réinstaller Office sur votre PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658).
  
> [!TIP]
> Si vous ne souhaitez pas que vos utilisateurs installent Office eux-mêmes, consultez [Gérer les paramètres de téléchargement de logiciels dans Office 365](/DeployOffice/manage-software-download-settings-office-365). Vous pouvez utiliser [l’outil déploiement d’Office](/DeployOffice/overview-office-deployment-tool) pour télécharger le logiciel Office sur votre réseau local, puis déployer Office à l’aide de la méthode de déploiement de logiciels que vous utilisez généralement.