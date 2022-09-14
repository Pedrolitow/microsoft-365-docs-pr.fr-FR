---
title: Évaluer l’accès contrôlé aux dossiers
description: Découvrez comment l’accès contrôlé aux dossiers peut aider à empêcher les fichiers d’être modifiés par des applications malveillantes.
keywords: Exploit Protection, windows 10, windows 11, windows defender, ransomware, protéger, évaluer, tester, démonstration, essayer
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: conceptual
author: dansimp
ms.author: dansimp
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.subservice: mde
ms.collection: m365-security-compliance
ms.date: ''
search.appverid: met150
ms.openlocfilehash: 489c6df191e9c132c43c47e9e42b76b54f7a990b
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67697098"
---
# <a name="evaluate-controlled-folder-access"></a>Évaluer l’accès contrôlé aux dossiers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)


[L’accès contrôlé aux dossiers](controlled-folders.md) est une fonctionnalité qui permet de protéger vos documents et fichiers contre les modifications apportées par des applications suspectes ou malveillantes. L’accès contrôlé aux dossiers est pris en charge sur les clients Windows Server 2019, Windows Server 2022, Windows 10 et Windows 11.

Il est particulièrement utile pour vous protéger contre les [ransomwares](https://www.microsoft.com/wdsi/threats/ransomware) qui tentent de chiffrer vos fichiers et de les garder en otage.

Cet article vous aide à évaluer l’accès contrôlé aux dossiers. Il explique comment activer le mode audit afin de pouvoir tester la fonctionnalité directement dans votre organisation.

## <a name="use-audit-mode-to-measure-impact"></a>Utiliser le mode audit pour mesurer l’impact

Activez l’accès contrôlé aux dossiers en mode audit pour afficher un enregistrement de ce qui *se serait* passé s’il était entièrement activé. Testez le fonctionnement de la fonctionnalité dans votre organisation pour vous assurer qu’elle n’affecte pas vos applications métier. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent généralement sur une certaine période de temps.

Pour activer le mode audit, utilisez l’applet de commande PowerShell suivante :

```PowerShell
Set-MpPreference -EnableControlledFolderAccess AuditMode
```

> [!TIP]
> Si vous souhaitez auditer entièrement le fonctionnement de l’accès contrôlé aux dossiers dans votre organisation, vous devez utiliser un outil de gestion pour déployer ce paramètre sur les appareils de votre réseau.
Vous pouvez également utiliser stratégie de groupe, Intune, la gestion des appareils mobiles (GPM) ou Microsoft Endpoint Manager pour configurer et déployer le paramètre, comme décrit dans la [rubrique principale d’accès contrôlé aux dossiers](controlled-folders.md).

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>Passer en revue les événements d’accès contrôlé aux dossiers dans Windows observateur d'événements

Les événements d’accès contrôlé aux dossiers suivants apparaissent dans windows observateur d'événements sous le dossier Microsoft/Windows/Windows Defender/Operational.

ID d’événement | Description
-|-
 5007 | Événement lorsque les paramètres sont modifiés
 1124 | Événement d’accès contrôlé aux dossiers audité
 1123 | Événement d’accès contrôlé aux dossiers bloqué

> [!TIP]
> Vous pouvez configurer un [abonnement Windows Event Forwarding](/windows/win32/wec/setting-up-a-source-initiated-subscription) pour collecter les journaux de manière centralisée. 

## <a name="customize-protected-folders-and-apps"></a>Personnaliser des dossiers et des applications protégés

Pendant votre évaluation, vous pouvez ajouter à la liste des dossiers protégés ou autoriser certaines applications à modifier des fichiers.

Consultez [Protéger les dossiers importants avec un accès contrôlé aux dossiers](controlled-folders.md) pour configurer la fonctionnalité avec des outils de gestion, notamment stratégie de groupe, PowerShell et les fournisseurs de services de configuration GPM.

## <a name="see-also"></a>Voir aussi

* [Protéger les dossiers importants avec accès contrôlé aux dossiers](controlled-folders.md)
* [Évaluer Microsoft Defender pour point de terminaison](evaluate-mde.md)
* [Utiliser le mode Audit](audit-windows-defender.md)
