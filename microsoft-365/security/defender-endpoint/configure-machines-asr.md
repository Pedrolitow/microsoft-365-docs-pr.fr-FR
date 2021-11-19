---
title: Optimiser le déploiement et les détections des règles ASR
description: Optimisez vos règles de réduction de la surface d’attaque (ASR) pour identifier et empêcher les attaques de programmes malveillants classiques.
keywords: intégré, gestion Intune, Microsoft Defender pour le point de terminaison, Microsoft Defender, Windows Defender, réduction de la surface d’attaque, réduction de la surface d’attaque, réduction de la surface d’attaque, ligne de base de sécurité
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 75e17dbeff38fd7e40c9a8f22217407773981c96
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111818"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optimiser le déploiement et les détections des règles ASR

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Les règles de réduction de la surface](./attack-surface-reduction.md) d’attaque identifient et empêchent les attaques de programmes malveillants classiques. Ils contrôlent quand et comment du code potentiellement malveillant peut s’exécuter. Par exemple, ils peuvent empêcher JavaScript ou VBScript de lancer un exécutable téléchargé, bloquer les appels d’API Win32 à partir de macros Office et bloquer les processus qui s’exécutent à partir de lecteurs USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Carte de gestion de la surface d’attaque.":::
<br>
*Carte de gestion de la surface d’attaque*

La *carte de gestion de la surface* d’attaque est un point d’entrée vers les outils Microsoft 365 Defender portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">que</a> vous pouvez utiliser pour :

* Comprendre comment les règles de la asr. sont actuellement déployées dans votre organisation.
* Passer en revue les détections de la résurv et identifier les détections incorrectes possibles.
* Analysez l’impact des exclusions et générez la liste des chemins d’accès aux fichiers à exclure.

Sélectionnez **Go to attack surface management** \> **Reports** Attack surface \> **reduction rules** Add \> **exclusions**. À partir de là, vous pouvez accéder à d’autres sections de Microsoft 365 Defender portail.

![Onglet Ajouter des exclusions dans la page Règles de réduction de la surface d’attaque Microsoft 365 Defender portail.](images/secconmgmt_asr_m365exlusions.png)<br>
Onglet ***Ajouter des exclusions** dans la page Règles de réduction de la surface d’attaque Microsoft 365 Defender portail*

> [!NOTE]
> Pour accéder Microsoft 365 Defender portail, vous avez besoin d’une licence Microsoft 365 E3 ou E5 et d’un compte qui a certains rôles sur Azure Active Directory. [En savoir plus sur les licences et autorisations requises.](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions)

Pour plus d’informations sur le déploiement de règles asr dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail,</a>voir Surveiller et gérer le déploiement et les détections de règles [asr.](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections)

**Rubriques connexes**

* [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
* [Obtenir des appareils intégrés à Microsoft Defender pour le point de terminaison](configure-machines-onboarding.md)
* [Surveiller la conformité à la ligne de base de sécurité microsoft Defender pour les points de terminaison](configure-machines-security-baseline.md)
