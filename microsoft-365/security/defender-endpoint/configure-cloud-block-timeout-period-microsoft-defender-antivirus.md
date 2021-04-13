---
title: Configurer le délai d'attente du blocage du cloud de l'Antivirus Microsoft Defender
description: Vous pouvez configurer la durée pendant combien de temps l'Antivirus Microsoft Defender bloquera l'exécution d'un fichier en attendant une détermination du cloud.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender, cloud, délai d'attente, bloc, période, secondes
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7ec134c2861b0185f66a08257fbc410b7a475b5a
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690451"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Configurer le délai d'attente du blocage du cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Lorsque l'Antivirus Microsoft Defender trouve un fichier suspect, il peut empêcher l'exécution du fichier pendant qu'il interroge le service cloud de [l'Antivirus Microsoft Defender.](cloud-protection-microsoft-defender-antivirus.md)

La période par défaut de blocage [du](configure-block-at-first-sight-microsoft-defender-antivirus.md) fichier est de 10 secondes. Vous pouvez spécifier une période supplémentaire d'attente avant que le fichier ne soit autorisé à s'exécuter. Cela permet de s'assurer qu'il y a suffisamment de temps pour recevoir une détermination appropriée du service cloud de l'Antivirus Microsoft Defender.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Conditions préalables à l'utilisation du délai d'accès au blocage étendu du cloud

[Bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md) et ses conditions préalables doivent être activées avant de pouvoir spécifier un délai d'attente étendu.

## <a name="specify-the-extended-timeout-period"></a>Spécifier le délai d'attente étendu

Vous pouvez utiliser la stratégie de groupe pour spécifier un délai d'accès étendu pour les vérifications dans le cloud.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, cliquez sur **Configuration** ordinateur et cliquez **sur Modèles d'administration.**

3. Développez l'arborescence **des composants Windows > l'Antivirus Microsoft Defender > MpEngine**

4. Double-cliquez **sur Configurer la vérification cloud étendue** et assurez-vous que l'option est activée. Spécifiez la durée supplémentaire pour empêcher l'exécution du fichier en attendant une détermination du cloud. Vous pouvez spécifier la durée supplémentaire, en secondes, entre 1 seconde et 50 secondes. Cette durée est ajoutée aux 10 secondes par défaut.

5. Cliquez sur **OK**.

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Utiliser les technologies antivirus de nouvelle génération par le biais d'une protection cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Configurer bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Activer la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)