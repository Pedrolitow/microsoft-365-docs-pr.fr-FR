---
title: API de réponse Microsoft Defender pour point de terminaison prises en charge
description: Découvrez les appels d’API Microsoft Defender pour point de terminaison spécifiques liés à la réponse.
keywords: api de réponse, api graphe, api prises en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: 8dd36e06b90726a01168ccd3ebf12886c127b101
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67050955"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>API de requête Microsoft Defender pour point de terminaison prises en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

Découvrez les appels d’API liés à la réponse pris en charge que vous pouvez exécuter et des détails tels que les en-têtes de requête requis et la réponse attendue des appels.

## <a name="in-this-section"></a>Dans cette section

<br>

****

|Rubrique|Description|
|---|---|
|Collecter un package d’examen|Exécutez cette API pour collecter un package d’investigation à partir d’un appareil.|
|Isoler l’appareil|Exécutez cette API pour isoler un appareil du réseau.|
|Appareil Unisolate|Supprimez un appareil de l’isolation.|
|Restreindre l'exécution de code|Exécutez cette API pour contenir une attaque en arrêtant les processus malveillants. Vous pouvez également verrouiller un appareil et empêcher l’exécution de tentatives ultérieures de programmes potentiellement malveillants.|
|Exécution du code Unrestrict|Exécutez cette commande pour inverser la restriction de la stratégie d’applications une fois que vous avez vérifié que l’appareil compromis a été corrigé.|
|Exécuter une analyse antivirus|Lancez à distance une analyse antivirus pour identifier et corriger les programmes malveillants susceptibles d’être présents sur un appareil compromis.|
|Arrêt et fichier mis en quarantaine|Exécutez cet appel pour arrêter l’exécution de processus, mettre en quarantaine des fichiers et supprimer la persistance, comme les clés de Registre.|
|Demander un exemple|Exécutez cet appel pour demander un exemple de fichier à partir d’un appareil spécifique. Le fichier sera collecté à partir de l’appareil et chargé dans un stockage sécurisé.|
|Bloquer le fichier|Exécutez cette API pour empêcher la propagation d’une attaque dans votre organisation en interdisant les fichiers potentiellement malveillants ou les programmes malveillants suspectés.|
|Débloquer le fichier|Autorisez l’exécution d’un fichier dans l’organisation à l’aide de l’antivirus Microsoft Defender.|
|Obtenir l’URI SAS du package|Exécutez cette API pour obtenir un URI qui permet de télécharger un package d’investigation.|
|Obtenir l’objet MachineAction|Exécutez cette API pour obtenir l’objet MachineAction.|
|Obtenir la collection MachineActions|Exécutez cette commande pour obtenir la collection MachineAction.|
|Obtenir la collection FileActions|Exécutez cette API pour obtenir la collection FileActions.|
|Obtenir l’objet FileMachineAction|Exécutez cette API pour obtenir l’objet FileMachineAction.|
|Obtenir la collection FileMachineActions|Exécutez cette API pour obtenir la collection FileMachineAction.|
|
