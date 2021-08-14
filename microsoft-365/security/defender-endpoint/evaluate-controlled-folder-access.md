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
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: b727fca2dbf5dcd3131f508cabe7d466424c88145d603e505c4f21f4e6feebfb
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53811277"
---
# <a name="evaluate-controlled-folder-access"></a>Évaluer l’accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[L’accès contrôlé aux](controlled-folders.md) dossiers est une fonctionnalité qui permet de protéger vos documents et fichiers contre toute modification par des applications suspectes ou malveillantes. L’accès contrôlé aux dossiers est pris en charge Windows Server 2019 et Windows 10 clients.

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
Vous pouvez également utiliser une stratégie de groupe, Intune, la gestion des périphériques mobiles (MDM) ou des Microsoft Endpoint Manager pour configurer et déployer le paramètre, comme décrit dans la rubrique principale d’accès contrôlé aux [dossiers.](controlled-folders.md)

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Passer en revue les événements d’accès contrôlé aux dossiers dans Windows’observateur d’événements

Les événements d’accès contrôlé aux dossiers suivants apparaissent dans Windows’Observateur d’événements sous Microsoft/Windows/Windows Defender/Opérationnel.

ID d’événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1124 | Événement d’accès contrôlé aux dossiers audité
 1123 | Événement d’accès contrôlé aux dossiers bloqué

> [!TIP]
> Vous pouvez configurer un abonnement [au Windows de](/windows/win32/wec/setting-up-a-source-initiated-subscription) l’événement pour collecter les journaux de manière centralisée. 

## <a name="customize-protected-folders-and-apps"></a>Personnaliser les applications et les dossiers protégés

Au cours de votre évaluation, vous pouvez ajouter des fichiers à la liste des dossiers protégés ou autoriser certaines applications à modifier des fichiers.

Voir [Protéger les dossiers](controlled-folders.md) importants avec accès contrôlé aux dossiers pour configurer la fonctionnalité à l’aide d’outils de gestion, y compris la stratégie de groupe, PowerShell et les fournisseurs de services de configuration (CSP) DE GESTION.

## <a name="see-also"></a>Voir aussi

* [Protéger les dossiers importants avec accès contrôlé aux dossiers](controlled-folders.md)
* [Évaluer Microsoft Defender pour point de terminaison](evaluate-mde.md)
* [Utiliser le mode Audit](audit-windows-defender.md)
