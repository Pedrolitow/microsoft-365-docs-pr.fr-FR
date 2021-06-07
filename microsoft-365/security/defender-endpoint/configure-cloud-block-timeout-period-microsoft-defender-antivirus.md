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
ms.date: 06/04/2021
ms.openlocfilehash: dfb75b77119d9550931c3e476323bde67a3b148f
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52789086"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Configurer le délai de blocage du cloud

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Lorsque Antivirus Microsoft Defender trouve un fichier suspect, il peut empêcher l’exécution du fichier pendant qu’il interroge [Antivirus Microsoft Defender service cloud.](cloud-protection-microsoft-defender-antivirus.md)

La période par défaut de blocage [du](configure-block-at-first-sight-microsoft-defender-antivirus.md) fichier est de 10 secondes. Si vous êtes administrateur de sécurité, vous pouvez spécifier plus de temps d’attente avant que le fichier ne soit autorisé à s’exécuter. L’extension du délai d’attente du blocage du cloud permet de s’assurer qu’il y a suffisamment de temps pour recevoir une détermination appropriée du service cloud Antivirus Microsoft Defender cloud.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Conditions préalables à l’utilisation du délai d’accès au blocage étendu du cloud

[Bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md) et ses conditions préalables doivent être activées avant de pouvoir spécifier un délai d’attente étendu.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Spécifier le délai d’attente étendu à l’aide Microsoft Endpoint Manager

Vous pouvez spécifier le délai d’attente de blocage du cloud avec une stratégie de sécurité de point de terminaison [dans Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Go to the Endpoint Manager admin center ( [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/) ) and sign in.

2. Sélectionnez **Sécurité du point de** terminaison, puis sous **Gérer**, choisissez **Antivirus**.

3. Sélectionnez (ou créez) une stratégie antivirus.

4. Dans la **section Paramètres de** configuration, développez **Protection cloud.** Ensuite, dans la zone Délai d’out étendu de **Defender Cloud** en secondes, spécifiez la durée, en secondes, entre 1 seconde et 50 secondes. Tout ce que vous spécifiez est ajouté aux 10 secondes par défaut.

5. (Cette étape est facultative) A apporter d’autres modifications à votre stratégie antivirus. (Vous avez besoin d’aide ? Voir [Paramètres la stratégie Antivirus Microsoft Defender dans Microsoft Intune.)](/mem/intune/protect/antivirus-microsoft-defender-settings-windows)

6. Choisissez **Suivant** et terminez la configuration de votre stratégie.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Spécifier le délai d’attente étendu à l’aide de la stratégie de groupe

Vous pouvez utiliser la stratégie de groupe pour spécifier un délai d’accès étendu pour les vérifications dans le cloud.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [console de gestion des stratégies de groupe.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

3. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur, puis sélectionnez **Modèles d’administration.**

3. Développez l’arborescence **Windows composants**  >  **Antivirus Microsoft Defender**  >  **MpEngine**.

4. Double-cliquez **sur Configurer la vérification cloud étendue** et assurez-vous que l’option est activée. 

   Spécifiez la durée supplémentaire pour empêcher l’exécution du fichier en attendant une détermination du cloud. Spécifiez le temps supplémentaire, en secondes, entre 1 seconde et 50 secondes. Tout ce que vous spécifiez est ajouté aux 10 secondes par défaut.

5. Sélectionnez **OK**.

 