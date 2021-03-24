---
title: Évaluer l’accès contrôlé aux dossiers
description: Découvrez comment l’accès contrôlé aux dossiers peut aider à empêcher les fichiers d’être modifiés par des applications malveillantes.
keywords: Exploit Protection, windows 10, windows defender, ransomware, protéger, évaluer, tester, démonstration, essayer
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: e5da8ec3e4555af062aad1a4ebfa96d972bee23b
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065873"
---
# <a name="evaluate-controlled-folder-access"></a>Évaluer l’accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)


[L’accès contrôlé aux](controlled-folders.md) dossiers est une fonctionnalité qui permet de protéger vos documents et fichiers contre toute modification par des applications suspectes ou malveillantes. L’accès contrôlé aux dossiers est pris en charge sur les clients Windows Server 2019 et Windows 10.

Il est particulièrement utile pour vous protéger contre les [ransomware](https://www.microsoft.com/wdsi/threats/ransomware) qui tentent de chiffrer vos fichiers et de les maintenir en attente.

Cet article vous aide à évaluer l’accès contrôlé aux dossiers. Il explique comment activer le mode audit afin de pouvoir tester la fonctionnalité directement dans votre organisation.

> [!TIP]
> Vous pouvez également consulter le site web du scénario de démonstration microsoft Defender pour point de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

## <a name="use-audit-mode-to-measure-impact"></a>Utiliser le mode audit pour mesurer l’impact

Activez l’accès contrôlé aux dossiers en  mode audit pour voir un enregistrement de ce qui se serait passé s’il était entièrement activé. Testez le fonctionnement de la fonctionnalité dans votre organisation pour vous assurer qu’elle n’affecte pas vos applications métier. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent généralement sur une certaine période de temps.

Pour activer le mode audit, utilisez l’cmdlet PowerShell suivante :

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Si vous souhaitez auditer entièrement le fonctionnement de l’accès contrôlé aux dossiers dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.
Vous pouvez également utiliser la stratégie de groupe, Intune, la gestion des périphériques mobiles (MDM) ou Microsoft Endpoint Manager pour configurer et déployer le paramètre, comme décrit dans la rubrique principale d’accès contrôlé aux [dossiers.](controlled-folders.md)

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Passer en revue les événements d’accès contrôlé aux dossiers dans l’Observateur d’événements Windows

Les événements d’accès contrôlé aux dossiers suivants apparaissent dans l’Observateur d’événements Windows sous Le dossier Microsoft/Windows/Windows Defender/Opérationnel.

ID de l'événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1124 | Événement d’accès contrôlé aux dossiers audité
 1123 | Événement d’accès contrôlé aux dossiers bloqué

> [!TIP]
> Vous pouvez configurer un abonnement [windows Event Forwarding](https://docs.microsoft.com/windows/win32/wec/setting-up-a-source-initiated-subscription) pour collecter les journaux de manière centralisée. 

## <a name="customize-protected-folders-and-apps"></a>Personnaliser les applications et les dossiers protégés

Au cours de votre évaluation, vous pouvez ajouter des fichiers à la liste des dossiers protégés ou autoriser certaines applications à modifier des fichiers.

Voir [Protéger les dossiers](controlled-folders.md) importants avec un accès contrôlé aux dossiers pour configurer la fonctionnalité à l’aide des outils de gestion, notamment la stratégie de groupe, PowerShell et les fournisseurs de services de configuration (CSP) DE GESTION.

## <a name="see-also"></a>Voir aussi

* [Protéger les dossiers importants avec un accès contrôlé aux dossiers](controlled-folders.md)
* [Évaluer Microsoft Defender pour le point de terminaison](evaluate-atp.md)
* [Utiliser le mode audit](audit-windows-defender.md)
