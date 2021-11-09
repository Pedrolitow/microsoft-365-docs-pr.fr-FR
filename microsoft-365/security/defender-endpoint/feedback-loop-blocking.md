---
title: Blocage de la boucle de commentaires
description: Le blocage de boucle de commentaires, également appelé protection rapide, fait partie des fonctionnalités de blocage du comportement et de blocage de contenu dans Microsoft Defender pour point de terminaison
keywords: blocage comportemental, protection rapide, blocage des commentaires, Microsoft Defender pour point de terminaison
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 30e1fdb8baede9506af52ae844f456baed1097a9
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60882680"
---
# <a name="feedback-loop-blocking"></a>Blocage de la boucle de commentaires

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

## <a name="overview"></a>Vue d’ensemble

Le blocage de boucle de commentaires, également appelé [](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) protection rapide, est un composant des fonctionnalités de blocage comportemental et de blocage de contenu dans [Microsoft Defender pour point de terminaison.](/windows/security/threat-protection/) Avec le blocage de la boucle de commentaires, les appareils au sein de votre organisation sont mieux protégés contre les attaques. 

## <a name="how-feedback-loop-blocking-works"></a>Fonctionnement du blocage de la boucle de commentaires

Lorsqu’un comportement ou un fichier suspect est détecté, par exemple par [Antivirus Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), les informations sur cet artefact sont envoyées à plusieurs classifieurs. Le moteur de boucle de protection rapide inspecte et met en corrélation les informations avec d’autres signaux pour déterminer s’il faut bloquer un fichier. La vérification et la classification des artefacts se produisent rapidement. Cela entraîne un blocage rapide des programmes malveillants confirmés et entraîne la protection dans l’ensemble de l’écosystème. 

Grâce à une protection rapide, une attaque peut être arrêtée sur un appareil, d’autres appareils de l’organisation et des appareils d’autres organisations, à mesure qu’une attaque tente d’élargir sa position.


## <a name="configuring-feedback-loop-blocking"></a>Configuration du blocage de boucle de commentaires

Si votre organisation utilise Defender pour endpoint, le blocage de la boucle de commentaires est activé par défaut. Toutefois, une protection rapide se produit par le biais d’une combinaison des fonctionnalités de Defender for Endpoint, des fonctionnalités de protection de l’apprentissage automatique et du partage de signal entre les services de sécurité Microsoft. Assurez-vous que les fonctionnalités suivantes de Defender for Endpoint sont activées et configurées :

- [Lignes de base de Microsoft Defender pour les points de terminaison](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Appareils intégrés à Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboard-configure)

- [PEPT en mode blocage](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Réduction de la surface d’attaque](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Protection nouvelle génération](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (antivirus)

## <a name="related-articles"></a>Articles connexes

- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)

- [(Blog) Blocage et contenu comportementaux : transformation de l’optique en protection](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Ressources Utiles de Microsoft Defender pour les points de terminaison](/microsoft-365/security/defender-endpoint/helpful-resources)
