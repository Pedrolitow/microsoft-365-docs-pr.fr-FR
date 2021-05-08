---
title: Configurer le délai d’Antivirus Microsoft Defender cloud
description: Vous pouvez configurer la durée pendant Antivirus Microsoft Defender’exécution d’un fichier en attendant une détermination du cloud.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender, cloud, délai d’attente, bloc, période, secondes
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 02b8ee1c73116718d771847a43d6334e0723bd5c
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275305"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Configurer le délai de blocage du cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Lorsque Antivirus Microsoft Defender trouve un fichier suspect, il peut empêcher l’exécution du fichier pendant qu’il interroge [Antivirus Microsoft Defender service cloud.](cloud-protection-microsoft-defender-antivirus.md)

La période par défaut de blocage [du](configure-block-at-first-sight-microsoft-defender-antivirus.md) fichier est de 10 secondes. Vous pouvez spécifier une période supplémentaire d’attente avant que le fichier ne soit autorisé à s’exécuter. Cela permet de s’assurer qu’il y a suffisamment de temps pour recevoir une détermination appropriée du service Antivirus Microsoft Defender cloud.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Conditions préalables à l’utilisation du délai d’accès au blocage étendu du cloud

[Bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md) et ses conditions préalables doivent être activées avant de pouvoir spécifier un délai d’attente étendu.

## <a name="specify-the-extended-timeout-period"></a>Spécifier le délai d’attente étendu

Vous pouvez utiliser la stratégie de groupe pour spécifier un délai d’accès étendu pour les vérifications dans le cloud.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d’administration.**

3. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender > MpEngine**

4. Double-cliquez **sur Configurer la vérification cloud étendue** et assurez-vous que l’option est activée. Spécifiez la durée supplémentaire pour empêcher l’exécution du fichier en attendant une détermination du cloud. Vous pouvez spécifier la durée supplémentaire, en secondes, entre 1 seconde et 50 secondes. Cette durée est ajoutée aux 10 secondes par défaut.

5. Cliquez sur **OK**.

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Utiliser les technologies antivirus de nouvelle génération par le biais d’une protection cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Configurer bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Activer la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)