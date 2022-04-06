---
title: Comprendre le rapport HTML de l’analyseur client
description: Découvrez comment analyser le rapport HTML de Microsoft Defender for Endpoint Client Analyzer
keywords: rapport de l’analyseur client, rapport HTML, analyseur client
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
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1f843c62d44ed7c25f07568cc0ee92709fb080a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468896"
---
# <a name="understand-the-client-analyzer-html-report"></a>Comprendre le rapport HTML de l’analyseur client

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

L’analyseur client produit un rapport au format HTML. Découvrez comment consulter le rapport pour identifier les problèmes potentiels de capteur afin de pouvoir les résoudre.

Utilisez l’exemple suivant pour comprendre le rapport.

 Exemple de sortie de l’analyseur sur un ordinateur intégré à l’ID d’organisation expiré et ne parvient pas à atteindre l’une des URL de point de terminaison Microsoft Defender requises :

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="Page Résultats de l’analyseur de client MDE" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- En haut, la version de script et le runtime de script sont répertoriés pour référence
- La section **Informations sur l’appareil** fournit des identificateurs de système d’exploitation et d’appareil de base pour identifier de manière unique l’appareil sur lequel l’analyseur s’est exécuté.
- Les **détails de sécurité des** points de terminaison fournissent des informations générales sur Microsoft Defender pour les processus liés aux points de terminaison, notamment les Antivirus Microsoft Defender et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur est rouge.
  
-   Les **détails de sécurité des** points de terminaison fournissent des informations générales sur Microsoft Defender pour les processus liés aux points de terminaison, notamment les Antivirus Microsoft Defender et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur est rouge.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="Page Résumé des résultats de vérification" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   Dans **le résumé des** résultats de vérification, vous aurez un nombre agrégé d’erreurs, d’avertissements ou d’événements d’information détectés par l’analyseur.

-   Dans **résultats détaillés**, vous verrez une liste (triée par gravité) avec les résultats et les instructions basées sur les observations réalisées par l’analyseur.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Ouvrir un ticket de support pour Microsoft et inclure les résultats de l’analyseur

Pour inclure les fichiers de résultats de l’analyseur lors de l’ouverture d’un [ticket de support](contact-support.md#open-a-service-request), veillez à utiliser la section **Pièces jointes** et à inclure le `MDEClientAnalyzerResult.zip` fichier :

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="Une invite de pièce jointe" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> Si la taille du fichier est supérieure à 25 Mo, l’ingénieur du support technique affecté à votre cas fournira un espace de travail sécurisé dédié pour charger des fichiers volumineux pour analyse.
