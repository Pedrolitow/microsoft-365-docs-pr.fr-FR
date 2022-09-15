---
title: Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données
description: Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données pour Microsoft Defender pour point de terminaison
keywords: données, stockage, paramètres, rétention, mise à jour
ms.service: microsoft-365-security
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 3fbcb8b512258b4307cf691ff2b720f78f5d7796
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67709389"
---
# <a name="verify-data-storage-location-and-update-data-retention-settings-for-microsoft-defender-for-endpoint"></a>Vérifier l’emplacement de stockage des données et mettre à jour les paramètres de rétention des données pour Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-gensettings-abovefoldlink)

Pendant le processus d’intégration, un Assistant vous guide dans les paramètres de stockage et de rétention des données de Defender pour point de terminaison. 

Une fois l’intégration terminée, vous pouvez vérifier votre sélection dans la page des paramètres de rétention des données.

## <a name="verify-data-storage-location"></a>Vérifier l’emplacement de stockage des données
Pendant la [phase de configuration](production-deployment.md), vous auriez sélectionné l’emplacement où stocker vos données. 


Vous pouvez vérifier l’emplacement des données en accédant à **Settings** \> **Endpoints** \> **Data retention** (sous **Général**).


## <a name="update-data-retention-settings"></a>Mettre à jour les paramètres de rétention des données

Vous pouvez mettre à jour les paramètres de rétention des données. Par défaut, la période de rétention est de 180 jours. 

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Point de terminaison Conservation **des** \> **données** (sous **Général**).

2. Sélectionnez la durée de rétention des données dans la liste déroulante.

    > [!NOTE]
    > Les autres paramètres ne sont pas modifiables.

3. Cliquez sur **Enregistrer les préférences**.

## <a name="related-topics"></a>Voir aussi
- [Mettre à jour les paramètres de rétention des données](data-retention-settings.md)
- [Configurer des notifications d’alerte dans Defender pour point de terminaison](configure-email-notifications.md)
- [Configurer des fonctionnalités avancées](advanced-features.md)
