---
title: Utiliser des enquêtes automatisées pour examiner et corriger les menaces
description: Comprendre le flux d’examen automatisé dans Microsoft Defender pour point de terminaison.
keywords: automatisé, examen, détection, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.date: 02/02/2021
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: fc69992139235dd0e99a0c22e92f87c8447dab43
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53655898"
---
# <a name="overview-of-automated-investigations"></a>Vue d’ensemble des enquêtes automatisées

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Vous voulez voir comment cela fonctionne ? Regardez la vidéo suivante :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

La technologie d’investigation automatisée utilise divers algorithmes d’inspection et repose sur des processus utilisés par les analystes de sécurité. Les fonctionnalités AIR sont conçues pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. Les fonctionnalités AIR réduisent considérablement le volume d’alertes, ce qui permet aux opérations de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives à valeur élevée. Toutes les actions de correction, en attente ou terminées, sont suivis dans le centre [de correction.](auto-investigation-action-center.md) Dans le centre de traitement des actions, les actions en attente sont approuvées (ou rejetées) et les actions terminées peuvent être annulées si nécessaire.

Cet article fournit une vue d’ensemble d’AIR et inclut des liens vers les étapes suivantes et des ressources supplémentaires.

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Comment l’examen automatisé démarre

Une enquête automatisée peut commencer lorsqu’une alerte est déclenchée ou lorsqu’un opérateur de sécurité lance l’enquête.

|Situation|Action exécutée|
|---|---|
|Une alerte est déclenchée|En règle générale, une enquête automatisée démarre [lorsqu’une](review-alerts.md) alerte est déclenchée et qu’un [incident](view-incidents-queue.md) est créé. Par exemple, supposons qu’un fichier malveillant réside sur un appareil. Lorsque ce fichier est détecté, une alerte est déclenchée et un incident est créé. Un processus d’examen automatisé commence sur l’appareil. Comme d’autres alertes sont générées en raison du même fichier sur d’autres appareils, elles sont ajoutées à l’incident associé et à l’examen automatisé.|
|Une enquête est démarrée manuellement|Une enquête automatisée peut être lancée manuellement par votre équipe des opérations de sécurité. Par exemple, supposons qu’un opérateur de sécurité examine une liste d’appareils et remarque qu’un appareil présente un niveau de risque élevé. L’opérateur de sécurité peut sélectionner l’appareil dans la liste pour ouvrir son volant, puis sélectionner **Lancer une enquête automatisée.**|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Comment un examen automatisé étend son étendue

Pendant l’exécution d’un examen, toutes les autres alertes générées à partir de l’appareil sont ajoutées à un examen automatisé en cours jusqu’à ce que l’enquête soit terminée. En outre, si la même menace est vue sur d’autres appareils, ces appareils sont ajoutés à l’examen.

Si une entité incriminée est vue dans un autre appareil, le processus d’examen automatisé étend son étendue pour inclure cet appareil, et un manuel de sécurité général démarre sur cet appareil. Si au moins 10 appareils sont trouvés au cours de ce processus d’expansion à partir de la même entité, cette action d’expansion nécessite une approbation et est visible sous l’onglet **Actions** en attente.

## <a name="how-threats-are-remediated"></a>Comment les menaces sont-elles corrigés ?

Lorsque des alertes sont déclenchées et qu’une enquête automatisée s’exécute, un verdict est généré pour chaque élément de preuve examiné. Les verdicts peuvent être :

- *Malveillant*;
- *Suspect*; ou
- *Aucune menace trouvée.*

À mesure que les verdicts sont atteints, des enquêtes automatisées peuvent entraîner une ou plusieurs actions de correction. L’envoi d’un fichier en quarantaine, l’arrêt d’un service, la suppression d’une tâche programmée, etc. sont des exemples d’actions de correction. Pour plus d’informations, voir [Actions de correction.](manage-auto-investigation.md#remediation-actions)  

Selon le niveau [d’automatisation](automation-levels.md) définie pour votre organisation, ainsi que d’autres paramètres de sécurité, des actions de correction peuvent se produire automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Les paramètres de sécurité supplémentaires pouvant affecter la correction automatique incluent la protection contre les [applications potentiellement](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) indésirables (PUA). 

Toutes les actions de correction, en attente ou terminées, sont suivis dans le centre [de correction.](auto-investigation-action-center.md) Si nécessaire, votre équipe des opérations de sécurité peut annuler une action de correction. Pour plus d’informations, voir [Examiner et approuver les actions de correction à la suite d’un examen automatisé.](/microsoft-365/security/defender-endpoint/manage-auto-investigation)

> [!TIP]
> Consultez la nouvelle page d’examen unifié dans le centre Microsoft 365 sécurité. Pour en savoir plus, [voir (NOUVEAU!) Page d’examen unifié](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Conditions requises pour AIR

Votre organisation doit avoir Defender pour le point de terminaison (voir [Minimum requirements for Microsoft Defender for Endpoint](minimum-requirements.md)).

Actuellement, AIR prend uniquement en charge les versions de système d’exploitation suivantes :

- Windows Server 2019
- Windows 10, version 1709 (os Build 16299.1085 avec [KB4493441)](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)ou version ultérieure
- Windows 10, version 1803 (os Build 17134.704 avec [KB4493464)](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)ou version ultérieure
- Windows 10, version [1803 ou](/windows/release-information/status-windows-10-1809-and-windows-server-2019) ultérieure

## <a name="next-steps"></a>Étapes suivantes

- [En savoir plus sur les niveaux d’automatisation](automation-levels.md)
- [Consultez le guide interactif : Examiner et corriger les menaces avec Microsoft Defender pour le point de terminaison](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Configurer les fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour le point de terminaison](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Voir aussi

- [Protection PUA](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Examen et réponse automatisés dans Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Examen et réponse automatisés dans Microsoft 365 Defender](/microsoft-365/security/defender/mtp-autoir)
