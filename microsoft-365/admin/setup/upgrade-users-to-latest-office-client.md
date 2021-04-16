---
title: Mettre à niveau votre Office 2010 vers Microsoft 365 - Administrateur Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
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
- fwlink 824861; CampaignID
- O365_Comm_SR_UpgradeOffice
- seo-marvel-may2020
- fwlink 824861; CampaignID O365_Comm_SR_UpgradeOffice
- AdminSurgePortfolio
ms.assetid: f6b00895-b5fd-4af6-a656-b7788ea20cbb
description: Découvrez comment mettre à niveau Microsoft Office vers le client Office le plus récent pour les utilisateurs de votre organisation.
ms.openlocfilehash: 3d2d5e54506d06662c6c2feef0d142f1e195163f
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51860570"
---
# <a name="upgrade-your-microsoft-365-for-business-users-to-the-latest-office-client"></a>Mettre à niveau vos utilisateurs Microsoft 365 pour les entreprises vers le dernier client Office

## <a name="office-2010-reaches-end-of-support"></a>Office 2010 atteint la fin de la prise en charge

Office 2010 a pris fin le 13 octobre 2020. Microsoft ne fournira plus les informations suivantes :

- Support technique pour les problèmes

- Résolutions de bogues pour les problèmes détectés

- Correctifs de sécurité pour les vulnérabilités découvertes

Pour plus d'informations, voir la feuille de route de fin du support office [2010.](/deployoffice/endofsupport/office-2010-end-support-roadmap)

 **S'agit-il de la rubrique la plus à votre place ?**
  
 Si vous êtes l'administrateur responsable de l'abonnement Microsoft 365 pour les entreprises dans votre organisation, vous êtes au bon endroit. Les administrateurs sont généralement responsables de tâches telles que la gestion des utilisateurs, la réinitialisation des mots de passe, la gestion des installation d'Office et l'ajout ou la suppression de licences.

 Si vous n'êtes pas un administrateur et que vous avez un produit [Microsoft 365 Famille,](https://support.microsoft.com/office/28cbc8cf-1332-4f04-9123-9b660abb629e#BKMK_OfficePlans) voir Comment mettre à niveau [Office](https://support.microsoft.com/office/ee68f6cf-422f-464a-82ec-385f65391350) pour plus d'informations sur la mise à niveau de votre ancienne version à usage personnel d'Office.

## <a name="get-ready-to-upgrade-to-microsoft-365"></a>Se préparer à la mise à niveau vers Microsoft 365

En tant qu'administrateur, vous contrôlez la version d'Office que les membres de votre organisation peuvent installer. Nous vous recommandons vivement d'aider les utilisateurs de votre organisation exécutant des versions antérieures d'Office telles qu'Office 2010, Office 2013 ou Office 2016 à mettre à niveau vers la dernière version pour tirer parti de ses améliorations en matière de sécurité et de productivité.

## <a name="upgrade-steps"></a>Étapes de mise à niveau

Les étapes ci-dessous vous guident tout au long du processus de mise à niveau de vos utilisateurs vers le dernier client de bureau Office. Nous vous recommandons de lire ces étapes avant de commencer le processus de mise à niveau.
  
## <a name="step-1---check-system-requirements"></a>Étape 1 : vérifier la qualité du système

[Vérifiez la version système requise](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources) pour Office pour vous assurer que vos appareils sont compatibles avec la dernière version d'Office. Par exemple, les versions plus récentes d'Office ne peuvent pas être installées sur des ordinateurs exécutant Windows XP ou Windows Vista.
  
> [!TIP]
> Si des utilisateurs de votre organisation exécutent des versions antérieures de Windows sur leurs PC ou ordinateurs portables, nous vous recommandons de mettre à niveau vers Windows 10. Windows 7 a atteint la fin de la prise en charge. La [lecture de la prise en charge de Windows 7 se termine en janvier 2020](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support?rtc=1) pour plus d'informations.

Consultez la version système requise de [Windows 10](https://www.microsoft.com/windows/windows-10-specifications) pour voir si vous pouvez mettre à niveau leurs systèmes d'exploitation.

### <a name="check-application-compatibility"></a>Vérifier la compatibilité des applications

Pour garantir une mise à niveau réussie, nous vous recommandons d'identifier vos applications Office(y compris les scripts VBA, les macros, les macros tierces et les documents et feuilles de calcul complexes) et d'évaluer leur compatibilité avec la dernière version d'Office.
  
Par exemple, si vous utilisez des applications tierces avec votre installation Office actuelle, contactez la fabrique pour vous assurer qu'elles sont compatibles avec la dernière version d'Office.
  
## <a name="step-2---check-your-existing-subscription-plan"></a>Étape 2 : vérifier votre plan d'abonnement existant

Certains plans Microsoft 365 n'incluent pas les versions de bureau complètes d'Office et les étapes de mise à niveau sont différentes si votre plan n'inclut pas Office.
  
Vous ne savez pas quel plan d'abonnement vous avez ? Consultez [l'abonnement Microsoft 365](../admin-overview/what-subscription-do-i-have.md) pour les entreprises dont je suis abonné ?
  
Si votre plan existant inclut Office, passer à l'étape [3 - Désinstaller Office](#step-3---uninstall-office).
  
Si votre plan existant n'inclut pas Office, sélectionnez l'une des options ci-dessous :
  
### <a name="upgrade-options-for-plans-that-dont-include-office"></a>Options de mise à niveau pour les plans qui n'incluent pas Office

 **Option 1 : Changer d'abonnement Office**

Passez à un abonnement qui inclut Office. Voir [Basculer vers une autre offre Microsoft 365 pour les entreprises.](../../commerce/subscriptions/switch-to-a-different-plan.md)

**Option 2 : acheter des achats individuels, à durée seule d'Office ou acheter Office via une licence en volume**

 - Acheter un achat individuel d'Office en une seule fois. Voir [Office Famille &amp; Ou](https://www.microsoft.com/microsoft-365/buy/compare-all-microsoft-365-products-b) [Office Professionnel](https://www.microsoft.com/microsoft-365/p/office-professional-2019/CFQ7TTC0K7C5/)

     Ou

 - Achetez plusieurs copies d'Office via une licence en volume. Voir comparer [les suites disponibles via la gestion des licences en volume.](https://products.office.com/business/microsoft-office-volume-licensing-suites-comparison)

## <a name="step-3---uninstall-office"></a>Étape 3 : Désinstaller Office

Avant d'installer la dernière version d'Office, nous vous recommandons de désinstaller toutes les anciennes versions d'Office. Toutefois, si vous changez d'avis concernant la mise à niveau d'Office, notez les instances suivantes dans laquelle vous ne pourrez pas réinstaller Office après l'avoir désinstallé.
  
Si vous avez des produits tiers, contactez le fabricant pour savoir s'il existe une mise à jour qui fonctionne avec la dernière version d'Office.

> [!TIP]
> Si vous avez des problèmes lors de la désinstallation d'Office, vous pouvez utiliser l'outil Assistant Support et récupération Microsoft pour vous aider à supprimer Office : téléchargez et exécutez l'Assistant Support et récupération [Microsoft.](https://go.microsoft.com/fwlink/?LinkID=2155008)

### <a name="select-the-version-of-office-you-want-to-uninstall"></a>Sélectionnez la version d'Office à désinstaller

- [À partir d'un PC](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8)

- [À partir d'un Mac](https://support.microsoft.com/office/eefa1199-5b58-43af-8a3d-b73dc1a8cae3)
  
### <a name="known-issues-trying-to-reinstall-older-versions-of-office-after-an-uninstall"></a>Problèmes connus lors de la tentative de réinstallation d'anciennes versions d'Office après une désinstallation

 **Office via une licence en volume** Si vous n'avez plus accès aux fichiers sources de ces versions de licence en volume d'Office, vous ne pourrez pas le réinstaller.

 **Office préinstallé sur votre ordinateur** Si vous n'avez plus de disque ou de clé de produit (si Office est arrivé avec une clé), vous ne pourrez plus le réinstaller.

 **Abonnements non pris en charge** Si votre copie d'Office a été obtenue par le biais d'abonnements abandonnés, tels qu'Office 365 Petite Entreprise Premium ou Office 365 Moyenne Entreprise, vous ne pourrez pas installer une version antérieure d'Office, sauf si vous avez la clé de produit qui est arrivée avec votre abonnement.

Si vous préférez installer votre ancienne version d'Office côte à côte avec la dernière version, vous pouvez voir une liste des versions dans laquelle cela est pris en charge, Installer et utiliser différentes versions d'Office sur le même [PC.](https://support.microsoft.com/office/6ebb44ce-18a3-43f9-a187-b78c513788bf) Une installation côte à côte peut être le bon choix pour vous, si, par exemple, vous avez installé des applications tierces que vous utilisez avec votre ancienne version d'Office et que vous n'êtes pas encore certain qu'elles sont compatibles avec la dernière version.

## <a name="step-4---assign-office-licenses-to-users"></a>Étape 4 : attribuer des licences Office aux utilisateurs

Si vous ne l'avez pas déjà fait, attribuez des licences à tous les utilisateurs de votre organisation qui doivent installer Office, voir Attribuer des licences aux utilisateurs dans [Microsoft 365 pour](../manage/assign-licenses-to-users.md)les entreprises.
  
## <a name="step-5---install-office"></a>Étape 5 : installer Office

Une fois que vous avez vérifié que les utilisateurs que vous souhaitez mettre à niveau ont tous des licences, l'étape finale consiste à leur faire installer Office, voir Télécharger et installer ou [réinstaller Office](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658)sur votre PC ou Mac.
  
> [!TIP]
> Si vous ne souhaitez pas que vos utilisateurs installent Office eux-mêmes, voir Gérer les paramètres de téléchargement de [logiciels dans Office 365.](/DeployOffice/manage-software-download-settings-office-365) Vous pouvez utiliser [l'outil Déploiement d'Office](/DeployOffice/overview-office-deployment-tool) pour télécharger le logiciel Office sur votre réseau local, puis déployer Office à l'aide de la méthode de déploiement de logiciels que vous utilisez généralement.