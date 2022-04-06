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
ms.openlocfilehash: d2bf9a6fa1f874e7d550d0d0f7a42742a07665eb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468256"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optimiser le déploiement et les détections des règles ASR

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Les règles de réduction de la surface](./attack-surface-reduction.md) d’attaque identifient et empêchent les attaques de programmes malveillants classiques. Ils contrôlent quand et comment du code potentiellement malveillant peut s’exécuter. Par exemple, ils peuvent empêcher JavaScript ou VBScript de lancer un exécutable téléchargé, bloquer les appels d’API Win32 à partir de macros Office et bloquer les processus qui s’exécutent à partir de lecteurs USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Carte de gestion de la surface d’attaque" lightbox="../../media/attack-surface-mgmt.png":::
<br>
*Carte de gestion de la surface d’attaque*

La *carte de gestion de la surface d’attaque* est un point d’entrée <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">vers les outils Microsoft 365 Defender portail que</a> vous pouvez utiliser pour :

* Comprendre comment les règles de la asr. sont actuellement déployées dans votre organisation.
* Passer en revue les détections de la résurv et identifier les détections incorrectes possibles.
* Analysez l’impact des exclusions et générez la liste des chemins d’accès aux fichiers à exclure.

Sélectionnez **Go to attack surface management** \> **Reports** \> **Attack surface reduction rules** \> **Add exclusions**. À partir de là, vous pouvez accéder à d’autres sections de Microsoft 365 Defender portail.

:::image type="content" source="images/secconmgmt_asr_m365exlusions.png" alt-text="Onglet Ajouter des exclusions dans la page Règles de réduction de la surface d’attaque du portail Microsoft 365 Defender attaque" lightbox="images/secconmgmt_asr_m365exlusions.png":::<br>
Onglet ***Ajouter des exclusions** dans la page Règles de réduction de la surface d’attaque Microsoft 365 Defender portail*

> [!NOTE]
> Pour accéder Microsoft 365 Defender portail, vous avez besoin d’une licence Microsoft 365 E3 ou E5 et d’un compte qui a certains rôles sur Azure Active Directory. [En savoir plus sur les licences et autorisations requises](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Pour plus d’informations sur le déploiement de règles asr dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> voir Surveiller et gérer le déploiement et les [détections de règles asr](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**Rubriques connexes**

* [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
* [Obtenir des appareils intégrés à Microsoft Defender pour le point de terminaison](configure-machines-onboarding.md)
* [Surveiller la conformité à la ligne de base de sécurité microsoft Defender pour les points de terminaison](configure-machines-security-baseline.md)
