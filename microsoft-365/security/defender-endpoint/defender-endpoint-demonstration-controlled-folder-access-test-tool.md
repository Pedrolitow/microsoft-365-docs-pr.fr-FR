---
title: Outil de test de démonstration de l’accès contrôlé aux dossiers (CFA) Microsoft Defender pour point de terminaison
description: Découvrez comment les applications malveillantes et les menaces sont évaluées et contrées par Microsoft Defender Antivirus.
keywords: Microsoft Defender pour point de terminaison, accès aux dossiers protégés bloqué, détecter les fichiers suspects, détecter les applications suspectes,
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
ms.openlocfilehash: 50e2b0e00333303a83d60df24ca0b9f8915122a9
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726021"
---
# <a name="controlled-folder-access-cfa-demonstration-test-tool-block-script"></a>Outil de test de démonstration d’accès contrôlé aux dossiers (CFA) (script de bloc)

L’accès contrôlé aux dossiers vous permet de protéger des données précieuses contre les applications malveillantes et les menaces, telles que les rançongiciels. Toutes les applications (tout fichier exécutable, y compris les fichiers .exe, .scr, .dll et autres) sont évaluées par Microsoft Defender Antivirus, qui détermine ensuite si l’application est malveillante ou sécurisée. Si l’application est jugée malveillante ou suspecte, elle ne sera pas autorisée à apporter des modifications à des fichiers dans un dossier protégé.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- Antivirus Microsoft Defender (mode actif)

## <a name="powershell-commands"></a>Commandes PowerShell

```powershell
Set-MpPreference -EnableControlledFolderAccess <State>
```

## <a name="rule-states"></a>États de règle

|État | Mode| Valeur numérique |
|:---|:---|:---|
| Désactivé | = Désactivé | 0 |
| Activé | = Mode bloc | 1 |
| Audit | = Mode d’audit | 2 |

### <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```

## <a name="scenario"></a>Scénario

### <a name="setup"></a>Configuration

Téléchargez et exécutez ce [script d’installation](https://demo.wd.microsoft.com/Content/CFA_SetupScript.zip). Avant d’exécuter la stratégie d’exécution du jeu de scripts sur Non restreint à l’aide de cette commande PowerShell :

```powershell
Set-ExecutionPolicy Unrestricted
```

Vous pouvez effectuer ces étapes manuelles à la place :

1. Activez la fonction CFA à l’aide de la commande powershell :

  ```powershell
  Set-MpPreference -EnableControlledFolderAccess Enabled
  ```

2. Télécharger [l’outil de test](https://demo.wd.microsoft.com/Content/CFAtool.exe) CFA
3. Exécuter les commandes PowerShell ci-dessus

## <a name="scenario-use-the-cfa-test-tool-to-simulate-an-untrusted-process-writing-to-a-protected-folder"></a>Scénario : Utiliser l’outil de test CFA pour simuler un processus non approuvé écrivant dans un dossier protégé

1. Lancer l’outil de test CFA
2. Sélectionnez le dossier souhaité et créez le fichier
- Vous trouverez plus d’informations [ici](/windows/threat-protection/windows-defender-exploit-guard/evaluate-controlled-folder-access.md)

## <a name="clean-up"></a>Nettoyer

Téléchargez et exécutez ce [script de nettoyage](https://demo.wd.microsoft.com/Content/ASR_CFA_CleanupScript.zip). Vous pouvez effectuer ces étapes manuelles à la place :

```powershell
Set-MpPreference -EnableControlledFolderAccess Disabled
```

## <a name="see-also"></a>Voir aussi
[Accès contrôlé aux dossiers](/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard)
