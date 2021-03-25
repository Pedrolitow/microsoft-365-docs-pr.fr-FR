---
title: Images d’appareil
description: Exigences relatives aux images lors de la commande de nouveaux appareils ou de la réutilisation d’appareils existants
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 9a263cbc6bdd0d521e835f086967a6f7236c6948
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166659"
---
# <a name="device-images"></a>Images d’appareil


Que vous order [new devices](#new-devices) or reuse [existing](#existing-devices) ones, you have several options to ensure the image on the device meets our [device requirements](device-requirements.md#check-hardware-requirements).

## <a name="new-devices"></a>les nouveaux périphériques et
Lorsque vous commandez un nouvel appareil auprès d’un fabricant [approuvé,](device-requirements.md#minimum-requirements)suivez ces étapes pour vous assurer qu’ils expédient des appareils avec l’image bureau géré Microsoft et la configuration logicielle appropriées.

### <a name="dell"></a>Dell
Travaillez directement avec le représentant commercial Dell, qui s’assure que l’image approuvée par Bureau géré Microsoft est appliquée aux appareils pour votre commande. Pour plus de questions sur les appareils Dell, l’image et le processus de commande, contactez MMD_at_dell@dell.com.

### <a name="hp"></a>HP 
Lorsque vous commandez de nouveaux appareils à partir de HP, n’oubliez pas d’utiliser la référence SKU spécifique répertoriée dans la section Exigences supplémentaires pour chaque modèle, comme illustré dans les [appareils du programme.](device-list.md#hp)

Si vous commandez un appareil à partir de HP qui a été approuvé comme [exception](customizing.md) mais qui n’est pas répertorié dans la page Liste des appareils, n’oubliez pas de demander la référence SKU à utiliser pour votre modèle. Nous allons travailler avec HP pour vous obtenir ces informations à l’aide de votre demande d’exception. Vous pouvez également contacter HP directement pour toute question sur les appareils et les instructions de commande des appareils à l’aide des adresses suivantes :
 
- Amériques : mmd-americas@hp.com
- Europe/Moyen-Orient/Afrique : mmd-emea@hp.com
- Asie-Pacifique/Japon : mmd-apj@hp.com
- Global : mmd@hp.com

### <a name="lenovo"></a>Lenovo
Lorsque vous commandez des appareils à partir de Lenovo pour une utilisation dans Bureau géré Microsoft, vous devez indiquer un numéro de partie spécifique inclus dans la commande. Contactez votre représentant commercial Lenovo ou votre partenairede canal Lenovo et demandez-lui de créer un « modèle d’offre spéciale » avec un système qui répond à nos besoins [en matière d’appareils.](device-requirements.md#minimum-requirements) Pour inclure une image pré-chargée compatible avec bureau géré Microsoft, demandez au représentant commercial de référencer « Numéro de la partie du bloc de construction système *SBB0Q94938 – MMD Enablement*».

Les produits suivants sont actuellement activés pour la prise en charge du Bureau géré Microsoft :

- L13 Génération 1
- L13 Gen 1
- L14 Gen 1 (Intel)
- L14 Gen 1 (AMD)
- L15 Gen 1 (Intel)
- L15 Gen 1 (AMD)
- X1 Génération carbone 8
- X1 Monde, génération 5
- T14 Gen 1 (Intel)
- T14 Gen 1 (AMD)
- T15 Génération 1
- X13 Génération 1 (Intel)


### <a name="microsoft"></a>Microsoft
Tous les appareils Microsoft qui répondent aux exigences de l’appareil sont avec une image qui fonctionne avec bureau géré Microsoft. Aucune autre étape n’est requise.

Pour obtenir la dernière image disponible dans l’usine sur un appareil Microsoft, faites appel à votre spécialiste Surface pour utiliser le processus « Po à basculement » surface.

## <a name="existing-devices"></a>Appareils existants

Vous pouvez réutiliser des appareils existants [](device-requirements.md#minimum-requirements) tant qu’ils répondent à la fois aux exigences de l’appareil et aux [logiciels.](device-requirements.md#installed-software) Suivez les étapes pertinentes pour votre fabricant.

Vous pouvez réimager des appareils avec une image du fabricant ou à l’aide de l'« image universelle » du Bureau géré Microsoft. Pour obtenir une image de fabricant appropriée, vous pouvez commander au moins un nouvel [appareil](#new-devices) du modèle que vous reutilisez. Vous pouvez ensuite obtenir l’image à partir de cet appareil et l’appliquer à d’autres appareils du même modèle.

> [!NOTE]
> Il vous incombe de créer, tester et déployer des images. Nous vous recommandons également d’utiliser les images appropriées fournies par le fabricant autant que possible au lieu d’images personnalisées, y compris l'« image universelle ».

### <a name="hp"></a>HP

Les PC commerciaux HP livrés avec l’image hp Corporate Ready incluent un . Fichier WIM pour la récupération. Vous pouvez utiliser cette image pour appliquer l’image de restauration d’usine à d’autres appareils du même modèle.

Ces étapes suppriment toutes les données sur l’appareil. Avant de commencer, vous devez donc les conserver.

1. [Créez un lecteur USB amorçable](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive) avec WinPE.
2. Copiez ces fichiers de C: \\ SOURCES sur le lecteur USB :
    - Fichier WIM de récupération d’usine (par exemple, HP \_ EliteBook \_ 840 \_ G7 \_ Notebook PC CR \_ \_ \_ 2004.wim)
    - DÉPLOYER. CMD
    - ReCreatePartitions.txt
3. [Démarrage de l’appareil vers WinPE](https://store.hp.com/us/en/tech-takes/how-to-boot-from-usb-drive-on-windows-10-pcs) Lecteur USB.
4. Dans une invite de commandes, exécutez [Diskpart.exe](https://docs.microsoft.com/windows-server/administration/windows-commands/diskpart#additional-references).
5. Dans Diskpart, exécutez, puis notez le numéro de disque de stockage `list disk` principal (généralement, Disque 0).
6. Quittez Diskpart en tapant `exit` .
7. Dans l’invite de commandes, exécutez , où sys_disk est le numéro de disque du disque de stockage principal que vous avez déterminé et recovery_wim est le nom de fichier `deploy.cmd <sys_disk> <recovery_wim>` du .   Fichier WIM que vous avez copié précédemment.
8. Supprimez le lecteur USB, puis redémarrez l’appareil.

### <a name="microsoft"></a>Microsoft 

Les appareils Microsoft Surface incluent des [images](https://support.microsoft.com/en-us/surfacerecoveryimage) de « récupération complète » spécifiques à chaque modèle. Vous pouvez utiliser ces images pour réimager des appareils.

Ces images utilisent l’environnement de récupération Windows (WinRE) et il s’agit d’un processus manuel (non automatisé). Suivez les étapes de [création et d’utilisation d’un lecteur de récupération USB pour Surface.](https://support.microsoft.com/surface/creating-and-using-a-usb-recovery-drive-for-surface-677852e2-ed34-45cb-40ef-398fc7d62c07)


### <a name="universal-image"></a>Image universelle
Bureau géré Microsoft a créé une image contenant Windows 10 Professionnel et Microsoft 365 Apps for Enterprise que vous pouvez utiliser avec Bureau géré Microsoft. Toutefois, il est préférable d’utiliser des images adaptées au Bureau géré Microsoft fourni par le fabricant chaque fois que possible, même si cela signifie une version antérieure de Windows qui doit ensuite être mise à jour une fois que l’utilisateur se signe. L’utilisation de l’image universelle bureau géré Microsoft doit être une option finale.

- Nous mettez à jour l’image avec les dernières mises à jour qualité mensuelles de Windows tous les 30 à 60 jours et les mises à jour de Microsoft 365 Apps for Enterprise au moins deux fois par an.
- L’image contient un package d’approvisionnement de récupération pour garantir la restauration de Microsoft 365 Apps for Enterprise à la suite de scénarios de récupération Windows.
- Vous pouvez déployer l’image avec des lecteurs USB. Il contient un processus scriptable pour insérer des pilotes (décrit dans la documentation incluse dans l’image).
- Vous pouvez modifier les scripts et dossiers inclus pour les utiliser avec d’autres personnalisations, telles que l’ajout de mises à jour cumulatives spécifiques, le code de copie de fichier ou d’autres vérifications.
- Les pilotes et les mises à jour qualité sont ajoutés à Windows lors du déploiement à partir du lecteur USB.

> [!NOTE]
> Il est de votre responsabilité d’ajouter tous les pilotes nécessaires, d’effectuer tous les tests et de vous assurer qu’il n’y a aucun problème avec l’image finale déployée. Nous fournissons l’image universelle « telle qu’elle est », mais fournissons des conseils techniques et des réponses aux questions. Contactez MMDImage@microsoft.com.

Envoyez des demandes pour le contenu et la documentation de l’image universelle en créant une demande de modification sur le [portail d’administration.](../get-started/access-admin-portal.md)


