---
title: Comprendre le rapport HTML de l’analyseur client
description: Découvrez comment analyser le rapport HTML de Microsoft Defender for Endpoint Client Analyzer
keywords: rapport de l’analyseur client, rapport HTML, analyseur client
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 735b2a0331e399fa7bf3444ff8e5326898c038b4
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569392"
---
# <a name="understand-the-client-analyzer-html-report"></a>Comprendre le rapport HTML de l’analyseur client

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)

L’analyseur client produit un rapport au format HTML. Découvrez comment consulter le rapport pour identifier les problèmes potentiels de capteur afin de pouvoir les résoudre.

Utilisez l’exemple suivant pour comprendre le rapport.

 Exemple de sortie de l’analyseur sur un ordinateur intégré à l’ID d’organisation expiré et ne parvient pas à atteindre l’une des URL de point de terminaison Microsoft Defender requises :

![Image du résultat de l’analyseur client.](images/147cbcf0f7b6f0ff65d200bf3e4674cb.png)

- En haut, la version de script et le runtime du script sont répertoriés pour référence
- La section **Informations sur l’appareil** fournit des identificateurs de système d’exploitation et d’appareil de base pour identifier de manière unique l’appareil sur lequel l’analyseur s’est exécuté.
- Les **détails de sécurité des** points de terminaison fournissent des informations générales sur Microsoft Defender pour les processus liés aux points de terminaison, notamment les Antivirus Microsoft Defender et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur est rouge.

  ![Image du résultat détaillé de l’analyseur client](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   Les **détails de sécurité des** points de terminaison fournissent des informations générales sur Microsoft Defender pour les processus liés aux points de terminaison, notamment les Antivirus Microsoft Defender et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur est rouge.

![Image du résultat détaillé de l’analyseur client.](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   Lors **de la vérification du résumé** des résultats, vous aurez un nombre agrégé d’erreurs, d’avertissements ou d’événements d’information détectés par l’analyseur.

-   Dans les **résultats détaillés,** vous verrez une liste (triée par gravité) avec les résultats et les instructions basées sur les observations réalisées par l’analyseur.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Ouvrir un ticket de support pour Microsoft et inclure les résultats de l’analyseur

Pour inclure les fichiers de résultats de l’analyseur lors de l’ouverture d’un [ticket de support,](contact-support.md#open-a-service-request)veillez à utiliser la section **Pièces jointes** et à inclure le `MDEClientAnalyzerResult.zip` fichier :

![Image de l’invite de pièce jointe.](images/508c189656c3deb3b239daf811e33741.png)

> [!NOTE]
> Si la taille du fichier est supérieure à 25 Mo, l’ingénieur du support technique affecté à votre cas fournira un espace de travail sécurisé dédié pour charger des fichiers volumineux pour analyse.
