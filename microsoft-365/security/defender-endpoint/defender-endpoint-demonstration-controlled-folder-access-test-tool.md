---
title: Microsoft Defender pour point de terminaison outil de test de démonstration d’accès contrôlé aux dossiers (CFA)
description: Découvrez comment les applications malveillantes et les menaces sont évaluées et contre-évaluées par Microsoft Defender Antivirus.
keywords: Microsoft Defender pour point de terminaison, l’accès aux dossiers protégés est bloqué, détecte les fichiers suspects, détecte les applications suspectes,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: evaluation
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: a1b5548b47c9bd60764d988235999f76349e7db6
ms.sourcegitcommit: 55672e44de74209f2e23b4bd9ca74a2ee7e88cd9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2022
ms.locfileid: "68319362"
---
# <a name="controlled-folder-access-cfa-demonstration-test-tool-block-script"></a>Outil de test de démonstration d’accès contrôlé aux dossiers (CFA) (script de bloc)

L’accès contrôlé aux dossiers vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomwares. Toutes les applications (tout fichier exécutable, y compris les fichiers .exe, .scr, .dll et autres) sont évaluées par Microsoft Defender Antivirus, qui détermine ensuite si l’application est malveillante ou sécurisée. Si l’application est déterminée comme malveillante ou suspecte, elle ne sera pas autorisée à apporter des modifications à des fichiers dans un dossier protégé.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- antivirus Microsoft Defender (mode actif)

## <a name="powershell-commands"></a>Commandes PowerShell

```powershell
Set-MpPreference -EnableControlledFolderAccess <State>
```

États:
- Activé = Mode bloc (1)
- AuditMode = Mode Audit (2)
- Disabled = Off (0)

### <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```
## <a name="scenario"></a>Scénario

### <a name="setup"></a>Configuration

Téléchargez et exécutez ce [script d’installation](https://demo.wd.microsoft.com/Content/CFA_SetupScript.zip). Avant d’exécuter la stratégie d’exécution du script, définissez La stratégie d’exécution sur Unrestricted à l’aide de cette commande PowerShell : Set-ExecutionPolicy Unrestricted

Vous pouvez effectuer ces étapes manuelles à la place :
1. Activer CFA à l’aide de la commande powershell : Set-MpPreference -EnableControlledFolderAccess Enabled
2. Télécharger [l’outil de test](https://demo.wd.microsoft.com/Content/CFAtool.exe) CFA
3. Exécuter les commandes PowerShell ci-dessus


## <a name="scenario-use-the-cfa-test-tool-to-simulate-an-untrusted-process-writing-to-a-protected-folder"></a>Scénario : Utiliser l’outil de test CFA pour simuler l’écriture d’un processus non approuvé dans un dossier protégé
1. Lancer l’outil de test CFA
2. Sélectionnez le dossier souhaité et créez un fichier
- Vous trouverez plus d’informations [ici](/windows/threat-protection/windows-defender-exploit-guard/evaluate-controlled-folder-access.md)

## <a name="clean-up"></a>Nettoyer

Téléchargez et [exécutez ce script de nettoyage](https://demo.wd.microsoft.com/Content/ASR_CFA_CleanupScript.zip). Vous pouvez effectuer ces étapes manuelles à la place :

- Set-MpPreference -EnableControlledFolderAccess Désactivé

## <a name="see-also"></a>Voir aussi
[Accès contrôlé aux dossiers](/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard)
