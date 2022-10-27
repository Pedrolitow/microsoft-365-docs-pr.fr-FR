---
title: Microsoft Defender pour point de terminaison démonstration de la protection fournie par le cloud
description: Découvrez comment la protection fournie par le cloud peut détecter et supprimer automatiquement les fichiers malveillants.
keywords: Microsoft Defender pour point de terminaison, Microsoft Defender ATP, protection antivirus, détection de virus, suppression de virus,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
- demo
ms.topic: article
ms.subservice: mde
ms.date: 10/21/2022
ms.openlocfilehash: 98aeeae72973f0a414b433f73a3ce66b15ef2798
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730246"
---
# <a name="cloud-delivered-protection-demonstration"></a>Démonstration de la protection fournie par le cloud

La protection fournie par le cloud pour Microsoft Defender Antivirus, également appelée Microsoft Advanced Protection Service (MAPS), vous offre une protection forte et rapide en plus de notre protection en temps réel standard.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 7, Windows 8.1, Windows 10, Windows 11
- Microsoft Defender la protection en temps réel est activée
- La protection fournie par le cloud est activée par défaut, mais vous devrez peut-être la réactiver si elle a été désactivée dans le cadre des stratégies organisationnelles précédentes. Pour plus d’informations, consultez [Activer la protection fournie par le cloud dans Microsoft Defender Antivirus](/windows/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus?ocid=wd-av-demo-cloud-middle).
- Vous pouvez également télécharger et utiliser le [script PowerShell](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings/) pour activer ce paramètre et d’autres sur Windows 10 et Windows 11.

### <a name="scenario"></a>Scénario

1. Téléchargez le [fichier de test](https://aka.ms/ioavtest). Important : Le fichier de test n’est pas malveillant, il s’agit simplement d’un fichier inoffensif simulant un virus.

2. Si vous voyez un fichier bloqué par Microsoft Defender SmartScreen, sélectionnez le bouton « Afficher les téléchargements ».

   :::image type="content" source="images/cloud-delivered-protection-smartscreen-block.png" alt-text="SmartScreen bloque un téléchargement non sécurisé et fournit un bouton à sélectionner pour afficher les détails de la liste **Téléchargements**.":::

3. Dans le menu Téléchargements à droite, sélectionnez le fichier bloqué, puis sélectionnez **Télécharger le fichier non sécurisé**.

   :::image type="content" source="images/cloud-delivered-protection-smartscreen-block-view-downloads.png" alt-text="Répertorie le téléchargement comme non sécurisé, mais fournit une option pour poursuivre le téléchargement":::

4. Vous devez voir que « antivirus Microsoft Defender » a trouvé un virus et l’a supprimé.

   > [!NOTE]
   >
   > Dans certains cas, vous pouvez également voir la notification **Threat Found** de Centre de sécurité Microsoft Defender.

   :::image type="content" source="images/cloud-delivered-protection-smartscreen-threat-found-notification.png" alt-text="Microsoft Defender notification menaces antivirus détectées fournit des options pour obtenir des détails":::

5. Si le fichier s’exécute ou s’il a été bloqué par Microsoft Defender SmartScreen, la protection fournie par le cloud ne fonctionne pas. Pour plus d’informations, consultez [Configurer et valider les connexions réseau pour Microsoft Defender Antivirus](/windows/threat-protection/windows-defender-antivirus/configure-network-connections-windows-defender-antivirus?ocid=wd-av-demo-cloud-middle).

## <a name="see-also"></a>Voir aussi

[Utiliser la protection fournie par microsoft dans le cloud dans Microsoft Defender Antivirus](/windows/threat-protection/windows-defender-antivirus/utilize-microsoft-cloud-protection-windows-defender-antivirus?ocid=wd-av-demo-cloud-bottom)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
