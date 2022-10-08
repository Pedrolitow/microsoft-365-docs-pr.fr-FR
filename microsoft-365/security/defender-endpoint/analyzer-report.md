---
title: Comprendre le rapport HTML de l’analyseur client
description: Découvrez comment analyser le rapport HTML de l’analyseur client Microsoft Defender pour point de terminaison
keywords: rapport de l’analyseur client, rapport html, analyseur client
ms.service: microsoft-365-security
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
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 4628f6bdc5bd3b38665fa044150e38c756db0059
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68145774"
---
# <a name="understand-the-client-analyzer-html-report"></a>Comprendre le rapport HTML de l’analyseur client

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

L’analyseur client produit un rapport au format HTML. Découvrez comment examiner le rapport pour identifier les problèmes potentiels de capteur afin de pouvoir les résoudre.

Utilisez l’exemple suivant pour comprendre le rapport.

 Exemple de sortie de l’analyseur sur un ordinateur intégré à l’ID d’organisation expiré et ayant échoué à atteindre l’une des URL Microsoft Defender pour point de terminaison requises :

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="Page Résultats de l’analyseur client MDE" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- En haut, la version du script et le runtime de script sont répertoriés pour référence.
- La section **Informations** sur l’appareil fournit des identificateurs de système d’exploitation et d’appareil de base pour identifier de manière unique l’appareil sur lequel l’analyseur s’est exécuté.
- Les **détails de sécurité** du point de terminaison fournissent des informations générales sur les processus liés à Microsoft Defender pour point de terminaison, notamment Microsoft Defender Antivirus et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur passe en rouge.
  
-   Les **détails de sécurité** du point de terminaison fournissent des informations générales sur les processus liés à Microsoft Defender pour point de terminaison, notamment Microsoft Defender Antivirus et le processus de capteur. Si les processus importants ne sont pas en ligne comme prévu, la couleur passe en rouge.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="Page Résumé des résultats de la vérification" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   Dans **Le résumé des résultats** de la vérification, vous avez un nombre agrégé d’événements d’erreur, d’avertissement ou d’informations détectés par l’analyseur.

-   Dans **Les résultats détaillés**, vous verrez une liste (triée par gravité) avec les résultats et les conseils basés sur les observations effectuées par l’analyseur.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Ouvrez un ticket de support pour Microsoft et incluez les résultats de l’analyseur

Pour inclure les fichiers de résultats de l’analyseur [lors de l’ouverture d’un ticket de support](contact-support.md#open-a-service-request), veillez à utiliser la section **Pièces jointes** et à inclure le `MDEClientAnalyzerResult.zip` fichier :

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="Une invite de pièces jointes" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> Si la taille du fichier est supérieure à 25 Mo, l’ingénieur du support technique affecté à votre cas fournit un espace de travail sécurisé dédié pour charger des fichiers volumineux à des fins d’analyse.
