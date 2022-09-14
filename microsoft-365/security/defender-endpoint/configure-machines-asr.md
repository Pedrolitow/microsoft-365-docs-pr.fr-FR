---
title: Optimiser le déploiement et les détections des règles ASR
description: Optimisez vos règles de réduction de la surface d’attaque (ASR) pour identifier et empêcher les attaques de programmes malveillants classiques.
keywords: intégration, gestion Intune, Microsoft Defender pour point de terminaison, Microsoft Defender, Windows Defender, réduction de la surface d’attaque, ASR, base de référence de sécurité
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: 40cca1fbda7ebb2d161e51a679a7e1e4afbf95af
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67679204"
---
# <a name="optimize-asr-rule-deployment-and-detections"></a>Optimiser le déploiement et les détections des règles ASR

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

[Les règles de réduction de la surface d’attaque (ASR)](./attack-surface-reduction.md) identifient et empêchent les attaques de programmes malveillants classiques. Ils contrôlent quand et comment le code potentiellement malveillant peut s’exécuter. Par exemple, ils peuvent empêcher JavaScript ou VBScript de lancer un exécutable téléchargé, bloquer les appels d’API Win32 à partir de macros Office et bloquer les processus qui s’exécutent à partir de lecteurs USB.


:::image type="content" source="../../media/attack-surface-mgmt.png" alt-text="Carte de gestion de la surface d’attaque" lightbox="../../media/attack-surface-mgmt.png":::
<br>
*Carte de gestion de la surface d’attaque*

La *carte de gestion de la surface d’attaque* est un point d’entrée des outils dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> que vous pouvez utiliser pour :

* Découvrez comment les règles ASR sont actuellement déployées dans votre organisation.
* Passez en revue les détections ASR et identifiez les détections incorrectes possibles.
* Analysez l’impact des exclusions et générez la liste des chemins de fichiers à exclure.

Sélectionnez **Accéder aux rapports de gestion de** \> la surface d’attaque **Les** \> règles \> de **réduction de la surface** **d’attaque ajoutent des exclusions**. À partir de là, vous pouvez accéder à d’autres sections du portail Microsoft 365 Defender.

:::image type="content" source="images/secconmgmt_asr_m365exlusions.png" alt-text="Onglet Ajouter des exclusions dans la page Règles de réduction de la surface d’attaque dans le portail Microsoft 365 Defender" lightbox="images/secconmgmt_asr_m365exlusions.png":::<br>
Onglet ***Ajouter des exclusions** dans la page Règles de réduction de la surface d’attaque dans Microsoft 365 Defender portail*

> [!NOTE]
> Pour accéder à Microsoft 365 Defender portail, vous avez besoin d’une licence Microsoft 365 E3 ou E5 et d’un compte qui a certains rôles sur Azure Active Directory. [Découvrez les licences et autorisations requises](/office365/securitycompliance/microsoft-security-and-compliance#required-licenses-and-permissions).

Pour plus d’informations sur le déploiement de règles ASR dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a>, consultez [Surveiller et gérer le déploiement et les détections de règles ASR](/office365/securitycompliance/monitor-devices#monitor-and-manage-asr-rule-deployment-and-detections).

**Rubriques connexes**

* [Vérifier que vos appareils sont correctement configurés](configure-machines.md)
* [Intégrer des appareils à Microsoft Defender pour point de terminaison](configure-machines-onboarding.md)
* [Surveiller la conformité à la base de référence de sécurité Microsoft Defender pour point de terminaison](configure-machines-security-baseline.md)
