---
title: Optimiser le déploiement et les détections des règles ASR
description: Optimisez vos règles de réduction de la surface d’attaque (ASR) pour identifier et empêcher les attaques de programmes malveillants classiques.
keywords: intégré, gestion Intune, Microsoft Defender pour le point de terminaison, Microsoft Defender, Windows Defender, réduction de la surface d’attaque, réduction de la surface d’attaque, réduction de la surface d’attaque, ligne de base de sécurité
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 612a68e4b0804ed6419511ee7505ed13a49883bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60205666"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optimiser le déploiement et les détections des règles ASR

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Les règles de réduction de la surface](./attack-surface-reduction.md) d’attaque identifient et empêchent les attaques de programmes malveillants classiques. Ils contrôlent quand et comment du code potentiellement malveillant peut s’exécuter. Par exemple, ils peuvent empêcher JavaScript ou VBScript de lancer un exécutable téléchargé, bloquer les appels d’API Win32 à partir de macros Office et bloquer les processus qui s’exécutent à partir de lecteurs USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Carte de gestion de la surface d’attaque.":::
<br>
*Carte de gestion de la surface d’attaque*

La *carte de gestion de la surface* d’attaque est un point d’entrée des outils Microsoft 365 centre de sécurité que vous pouvez utiliser pour :

* Comprendre comment les règles de la asr. sont actuellement déployées dans votre organisation.
* Passer en revue les détections de la résurv et identifier les détections incorrectes possibles.
* Analysez l’impact des exclusions et générez la liste des chemins d’accès aux fichiers à exclure.

Sélectionnez **Go to attack surface management** \> **Reports** Attack surface \> **reduction rules** Add \> **exclusions**. À partir de là, vous pouvez accéder à d’autres sections du centre Microsoft 365 sécurité.

![Ajoutez l’onglet Exclusions dans la page Règles de réduction de la surface d’attaque Microsoft 365 centre de sécurité.](images/secconmgmt_asr_m365exlusions.png)<br>
Onglet ***Ajouter des exclusions** dans la page Règles de réduction de la surface d’attaque Microsoft 365 centre de sécurité*

> [!NOTE]
> Pour accéder Microsoft 365 centre de sécurité, vous avez besoin d’une licence Microsoft 365 E3 ou E5 et d’un compte qui a certains rôles sur Azure Active Directory. [En savoir plus sur les licences et autorisations requises.](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions)

Pour plus d’informations sur le déploiement de règles asr dans Microsoft 365 sécurité, voir Surveiller et gérer le déploiement et les détections de règles [asr.](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections)

**Rubriques connexes**

* [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
* [Obtenir des appareils intégrés à Microsoft Defender pour le point de terminaison](configure-machines-onboarding.md)
* [Surveiller la conformité à la ligne de base de sécurité microsoft Defender pour les points de terminaison](configure-machines-security-baseline.md)
