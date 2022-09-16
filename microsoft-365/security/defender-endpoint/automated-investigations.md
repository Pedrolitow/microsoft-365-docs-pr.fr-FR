---
title: Utiliser des investigations automatisées pour examiner et corriger les menaces
description: Comprendre le flux d’investigation automatisé dans Pertahanan Microsoft untuk Titik Akhir.
keywords: automatisé, investigation, détection, Pertahanan Microsoft untuk Titik Akhir
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
ms.date: 08/31/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
search.appverid: met150
ms.openlocfilehash: ded37b41a4b4c4ec2245edc2a677cf1c0a891fbd
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736781"
---
# <a name="overview-of-automated-investigations"></a>Vue d’ensemble des enquêtes automatisées

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

**Plateformes**
- Windows

Souhaitez-vous découvrir comment cela fonctionne ? Regardez la vidéo suivante :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bOeh]

La technologie d’investigation automatisée utilise différents algorithmes d’inspection et est basée sur des processus utilisés par les analystes de sécurité. Les fonctionnalités AIR sont conçues pour examiner les alertes et prendre des mesures immédiates pour résoudre les violations. Les fonctionnalités AIR réduisent considérablement le volume d’alertes, ce qui permet aux opérations de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives de grande valeur. Toutes les actions de correction, qu’elles soient en attente ou terminées, sont suivies dans le [Centre d’actions](auto-investigation-action-center.md). Dans le Centre d’actions, les actions en attente sont approuvées (ou rejetées) et les actions terminées peuvent être annulées si nécessaire.

Cet article fournit une vue d’ensemble d’AIR et inclut des liens vers les étapes suivantes et des ressources supplémentaires.

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-automated-investigations-abovefoldlink)

## <a name="how-the-automated-investigation-starts"></a>Démarrage de l’enquête automatisée

Une enquête automatisée peut démarrer lorsqu’une alerte est déclenchée ou lorsqu’un opérateur de sécurité lance l’enquête.

|Situation|Action exécutée|
|---|---|
|Une alerte est déclenchée|En général, une enquête automatisée démarre lorsqu’une [alerte](review-alerts.md) est déclenchée et qu’un [incident](view-incidents-queue.md) est créé. Par exemple, supposons qu’un fichier malveillant réside sur un appareil. Lorsque ce fichier est détecté, une alerte est déclenchée et un incident est créé. Un processus d’investigation automatisé commence sur l’appareil. Comme d’autres alertes sont générées en raison du même fichier sur d’autres appareils, elles sont ajoutées à l’incident associé et à l’investigation automatisée.|
|Une enquête est démarrée manuellement|Une enquête automatisée peut être démarrée manuellement par votre équipe des opérations de sécurité. Par exemple, supposons qu’un opérateur de sécurité examine une liste d’appareils et remarque qu’un appareil présente un niveau de risque élevé. L’opérateur de sécurité peut sélectionner l’appareil dans la liste pour ouvrir son menu volant, puis sélectionner **Lancer l’investigation automatisée**.|

## <a name="how-an-automated-investigation-expands-its-scope"></a>Comment une enquête automatisée étend son étendue

Pendant l’exécution d’une enquête, toutes les autres alertes générées à partir de l’appareil sont ajoutées à une enquête automatisée en cours jusqu’à ce que cette enquête soit terminée. En outre, si la même menace est visible sur d’autres appareils, ces appareils sont ajoutés à l’enquête.

Si une entité incriminée est vue dans un autre appareil, le processus d’investigation automatisé étend son étendue pour inclure cet appareil, et un playbook de sécurité général démarre sur cet appareil. Si 10 appareils ou plus sont trouvés pendant ce processus d’expansion à partir de la même entité, cette action d’extension nécessite une approbation et est visible sous l’onglet **Actions en attente** .

## <a name="how-threats-are-remediated"></a>Comment les menaces sont corrigées

À mesure que des alertes sont déclenchées et qu’une enquête automatisée s’exécute, un verdict est généré pour chaque élément de preuve examiné. Les verdicts peuvent être :

- *Malveillants* ;
- *Suspect;* Ou
- *Aucune menace trouvée*.

À mesure que les verdicts sont rendus, les enquêtes automatisées peuvent entraîner une ou plusieurs actions correctives. Parmi les actions de correction, citons l’envoi d’un fichier en quarantaine, l’arrêt d’un service, la suppression d’une tâche planifiée, etc. Pour en savoir plus, consultez [Actions de correction](manage-auto-investigation.md#remediation-actions).

Selon le [niveau d’automatisation](automation-levels.md) défini pour votre organisation, ainsi que d’autres paramètres de sécurité, les actions de correction peuvent se produire automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Les paramètres de sécurité supplémentaires qui peuvent affecter la correction automatique incluent la [protection contre les applications potentiellement indésirables](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus) (PUA).

Toutes les actions de correction, qu’elles soient en attente ou terminées, sont suivies dans le [Centre d’actions](auto-investigation-action-center.md). Si nécessaire, votre équipe des opérations de sécurité peut annuler une action de correction. Pour en savoir plus, consultez [Examiner et approuver les actions de correction à la suite d’une enquête automatisée](/microsoft-365/security/defender-endpoint/manage-auto-investigation).

> [!TIP]
> Consultez la nouvelle page d’investigation unifiée dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez la [page d’enquête unifiée](/microsoft-365/security/defender/m365d-autoir-results#new-unified-investigation-page).

## <a name="requirements-for-air"></a>Configuration requise pour AIR

Votre abonnement doit inclure [Defender pour point de terminaison](microsoft-defender-endpoint.md) ou [Defender Entreprise](../defender-business/mdb-overview.md).

> [!NOTE]
> L’investigation et la réponse automatisées nécessitent l’antivirus Microsoft Defender pour l’exécution en mode passif ou actif. Si l’antivirus Microsoft Defender est désactivé ou désinstallé, l’investigation et la réponse automatisées ne fonctionnent pas correctement.

Actuellement, AIR prend uniquement en charge les versions de système d’exploitation suivantes :

- Windows Server 2012 R2 (préversion)
- Windows Server 2016 (préversion)
- Windows Server 2019
- Windows Server 2022
- Windows 10, version 1709 (build du système d’exploitation 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) ou ultérieure
- Windows 10, version 1803 (build du système d’exploitation 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) ou ultérieure
- Windows 10, version [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) ou ultérieure
- Windows 11

> [!NOTE]
> L’examen et la réponse automatisés sur Windows Server 2012 R2 et Windows Server 2016 nécessitent l’installation de [l’agent unifié](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution). 

## <a name="next-steps"></a>Prochaines étapes

- [Mer informasjon sur les niveaux d’automatisation](automation-levels.md)
- [Consultez le guide interactif : Examiner et corriger les menaces avec Pertahanan Microsoft untuk Titik Akhir](https://aka.ms/MDATP-IR-Interactive-Guide)
- [Configurer des fonctionnalités d’investigation et de correction automatisées dans Pertahanan Microsoft untuk Titik Akhir](configure-automated-investigations-remediation.md)

## <a name="see-also"></a>Voir aussi

- [Protection PUA](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Investigation et réponse automatisées dans Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/office-365-air)
- [Enquête et réponse automatisées dans Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
