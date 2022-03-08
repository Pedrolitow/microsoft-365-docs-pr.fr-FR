---
title: Images d’un appareil
description: Exigences relatives aux images lors de la commande de nouveaux appareils ou de la réutilisation d’appareils existants
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: f1d00c12512b70ffd62372aaeae787acf1911573
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330284"
---
# <a name="device-images"></a>Images d’un appareil

Que vous commandez de [nouveaux](#new-devices) appareils [](#existing-devices) ou réutilisiez des appareils existants, plusieurs options s’offrent à vous pour vous assurer que l’image de l’appareil répond aux exigences [de l’appareil](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>les nouveaux périphériques et

Lorsque vous commandez un nouvel appareil auprès d’un fabricant [approuvé, suivez](device-requirements.md#minimum-requirements) ces étapes pour vous assurer qu’ils expédient des appareils avec la configuration Microsoft Manged Desktop image et logicielle appropriées.

Chaque fois que vous prévoyez d’inscrire un modèle d’appareil particulier dans le service pour la première fois, vous devez tester un exemple pour vous assurer qu’il offre l’expérience utilisateur que vous attendez. Pour plus d’informations, voir [Valider les nouveaux appareils](/microsoft-365/managed-desktop/get-started/validate-device).

### <a name="dell"></a>Dell

Travaillez directement avec le représentant commercial Dell.

Le représentant s’assure que l’image approuvée par Microsoft Manged Desktop est appliquée aux appareils dans votre ordre. Pour plus d’informations sur les appareils Dell, l’image et le processus de commande, contactez MMD_at_dell@dell.com.

### <a name="hp"></a>HP

Lorsque vous commandez de nouveaux appareils auprès de HP, n’oubliez pas d’utiliser la référence SKU spécifique répertoriée dans la section Exigences supplémentaires pour chaque modèle trouvé dans la page Acheter [Windows Pro appareils métier](https://www.microsoft.com/windows/business/devices#view-all-filter). Filtrez l’affichage pour lister les Microsoft Manged Desktop périphériques.

Si vous commandez un appareil à partir de HP qui a été approuvé à titre [d’exception](customizing.md), mais qui n’est pas répertorié dans la page Liste des appareils, demandez la référence SKU à utiliser pour votre modèle. Nous allons travailler avec HP pour vous obtenir ces informations à l’aide de votre demande d’exception. Vous pouvez également contacter HP directement pour toute question sur les appareils et les instructions de commande des appareils à l’aide des adresses suivantes :

- Amériques : mmd-americas@hp.com
- Europe/Moyen-Orient/Afrique : mmd-emea@hp.com
- Asie-Pacifique/Japon : mmd-apj@hp.com
- Global : mmd@hp.com

### <a name="lenovo"></a>Lenovo

Lorsque vous commandez des appareils à partir de Lenovo, vous devez indiquer un numéro de partie spécifique dans l’ordre. Contactez votre représentant commercial Lenovo ou votre partenaire de canal Lenovo et demandez-lui de créer *un « modèle* d’offre spéciale » avec un système qui répond à nos besoins [en matière d’appareils](device-requirements.md#minimum-requirements).

Pour inclure une image pré-chargée compatible avec Microsoft Manged Desktop, demandez au représentant commercial de faire référence au « numéro de la partie de bloc de construction système *SBB0Q94938 - MmD Enablement* ». Travaillez en partenariat avec votre représentant commercial Lenovo ou votre partenaire de canal Lenovo pour les services recommandés, le support et les services d’imagerie.

### <a name="microsoft"></a>Microsoft

Tous les appareils Microsoft qui répondent aux exigences de l’appareil sont avec une image qui fonctionne avec Microsoft Manged Desktop. Aucune autre étape n’est requise.

Pour obtenir la dernière image disponible dans l’usine sur un appareil Microsoft, faites appel à votre spécialiste Surface pour utiliser le processus « Po à basculement » surface.

## <a name="existing-devices"></a>Appareils existants

Vous pouvez réutiliser des appareils existants tant qu’ils répondent aux deux :

- [Configuration requise de l’appareil](device-requirements.md#minimum-requirements)
- [Configuration logicielle requise](device-requirements.md#installed-software)

Suivez les étapes pertinentes pour votre fabricant.

Vous pouvez réimager des appareils avec une image du fabricant ou à l’aide Microsoft Manged Desktop « image universelle ». Pour obtenir une image de fabricant appropriée, commandez au moins un [nouvel appareil](#new-devices) du modèle que vous reutilisez. Ensuite, vous pouvez obtenir l’image à partir de cet appareil et l’appliquer à d’autres appareils du même modèle.

> [!NOTE]
> Il vous incombe de créer, tester et déployer des images. Nous vous recommandons également d’utiliser les images appropriées fournies par le fabricant autant que possible au lieu d’images personnalisées . cela inclut l'« image universelle ».

### <a name="hp"></a>HP

Les PC commerciaux HP livrés avec HP Corporate Ready Image incluent un `.WIM` fichier pour la récupération. Vous pouvez utiliser cette image pour appliquer l’image de restauration d’usine à d’autres appareils du même modèle.

Les étapes suivantes suppriment toutes les données sur l’appareil. Avant de commencer, vous devez conserver les données que vous souhaitez conserver.

**Pour supprimer des données sur l’appareil :**

1. [Créez un lecteur USB amorçable](/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) avec WinPE.
2. Copiez ces fichiers sur `C:\\SOURCES` le lecteur USB :
    - Fichier WIM de récupération d’usine (par exemple, `HP\_EliteBook\_840\_G7\_Notebook\_PC\_CR\_2004.wim`)
    - `DEPLOY.CMD`
    - `ReCreatePartitions.txt`
3. [Démarrage de l’appareil vers WinPE](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) Lecteur USB.
4. Dans une invite de commandes, [ exécutezDiskpart.exe](/windows-server/administration/windows-commands/diskpart#additional-references).
5. Dans Diskpart, exécutez `list disk`, puis notez le numéro de disque de stockage principal (généralement, Disque 0).
6. Quittez Diskpart en tapant `exit`.
7. Dans l’invite de commandes, `deploy.cmd <sys_disk> <recovery_wim>`exécutez , `sys_disk` où est le numéro de disque du disque de stockage principal que vous avez déterminé, `recovery_wim` `.WIM` et est le nom du fichier que vous avez copié précédemment.
8. Supprimez le lecteur USB, puis redémarrez l’appareil.

### <a name="microsoft"></a>Microsoft

Les appareils Microsoft Surface incluent des [images](https://support.microsoft.com/en-us/surfacerecoveryimage) de « récupération complète » spécifiques à chaque modèle. Vous pouvez utiliser ces images pour réimager des appareils.

Ces images utilisent l’Windows recovery environment (WinRE). Il s’agit d’un processus manuel (non automatisé). Suivez les étapes de [création et d’utilisation d’un lecteur de récupération USB pour Surface](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07).

### <a name="universal-image"></a>Image universelle

Microsoft Manged Desktop a créé une image contenant des Windows Pro et des Microsoft 365 Apps pour Enterprise que vous pouvez utiliser avec Microsoft Manged Desktop.

Toutefois, il est préférable d’utiliser des images adaptées aux Microsoft Manged Desktop fournies par le fabricant autant que possible, même si cela signifie qu’une version Windows plus ancienne doit être mise à jour une fois que l’utilisateur s’est mis en ligne. L’utilisation Microsoft Manged Desktop’image universelle doit être une option finale.

- Nous mettez à jour l’image avec les mises à jour de qualité mensuelles les Windows les plus récentes tous les 30 à 60 jours, et Microsoft 365 Apps les mises à jour Enterprise au moins deux fois par an.
- L’image contient un package d’approvisionnement de récupération pour s’assurer que Microsoft 365 Apps pour Enterprise est restaurée après Windows scénarios de récupération.
- Vous pouvez déployer l’image avec des lecteurs USB. Il contient un processus scriptable pour insérer des pilotes. Ce processus est décrit dans la documentation incluse dans l’image.
- Vous pouvez modifier les scripts et dossiers inclus avec d’autres personnalisations, telles que l’ajout de mises à jour cumulatives spécifiques, le code de copie de fichier ou d’autres vérifications.
- Les pilotes et les mises à jour qualité sont ajoutés à Windows lors du déploiement à partir du lecteur USB.

> [!NOTE]
> Il est de votre responsabilité d’ajouter tous les pilotes nécessaires, d’effectuer tous les tests et de vous assurer qu’il n’y a aucun problème avec l’image finale déployée. Nous fournissons l’image universelle « telle qu’elle est », mais fournissons des conseils techniques et des réponses aux questions. Contactez MMDImage@microsoft.com.

Envoyez des demandes pour le contenu et la documentation de l’image universelle en créant une demande de modification sur le [portail d’administration](../get-started/access-admin-portal.md).
