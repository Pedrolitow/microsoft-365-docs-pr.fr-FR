---
title: Microsoft Defender pour point de terminaison démonstrations d’accès contrôlé aux dossiers (CFA)
description: Montre comment l’accès contrôlé aux dossiers protège les données précieuses contre les applications malveillantes et les menaces, telles que les rançongiciels.
keywords: Microsoft Defender pour point de terminaison, Protection de l’accès contrôlé aux dossiers, Démonstration de l’accès contrôlé aux dossiers
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
ms.openlocfilehash: 561d36ebd04076e93b47b2679b3b236009f94c2d
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732776"
---
# <a name="controlled-folder-access-cfa-demonstrations-block-ransomware"></a>Démonstrations d’accès contrôlé aux dossiers (CFA) (bloquer les rançongiciels)

L’accès contrôlé aux dossiers vous permet de protéger des données précieuses contre les applications malveillantes et les menaces, telles que les rançongiciels. Toutes les applications (tout fichier exécutable, y compris les fichiers .exe, .scr, .dll et autres) sont évaluées par Microsoft Defender Antivirus, qui détermine ensuite si l’application est malveillante ou sécurisée. Si l’application est jugée malveillante ou suspecte, elle ne sera pas autorisée à apporter des modifications à des fichiers dans un dossier protégé.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- Antivirus Microsoft Defender (mode actif)

## <a name="powershell-commands"></a>Commandes PowerShell

```powershell
Set-MpPreference -EnableControlledFolderAccess (State)
```

```powershell
Set-MpPreference -ControlledFolderAccessProtectedFolders C:\demo\
```

## <a name="rule-states"></a>États de règle

|État | Mode| Valeur numérique |
|:---|:---|:---|
| Désactivé | = Désactivé | 0 |
| Activé | = Mode bloc | 1 |
| Audit | = Mode d’audit | 2 |

## <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```

## <a name="test-file"></a>Fichier de test

[Fichier de test de ransomware CFA](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe)

## <a name="scenarios"></a>Scénarios

### <a name="setup"></a>Configuration

Téléchargez et exécutez ce [script d’installation](https://demo.wd.microsoft.com/Content/CFA_SetupScript.zip). Avant d’exécuter la stratégie d’exécution du jeu de scripts sur Non restreint à l’aide de cette commande PowerShell : 

```powershell
Set-ExecutionPolicy Unrestricted
```

Vous pouvez effectuer ces étapes manuelles à la place :

1. Créez un dossier sous c: named demo, « c:\demo »
2. Enregistrez ce [fichier propre](https://demo.wd.microsoft.com/Content/testfile_safe.txt) dans c:\demo (nous avons besoin d’un élément à chiffrer)
3. Exécuter les commandes PowerShell ci-dessus

### <a name="scenario-1-cfa-blocks-ransomware-test-file"></a>Scénario 1 : CFA bloque le fichier de test de ransomware

1. Activez la fonction CFA à l’aide de la commande PowerShell :
  
```powershell
Set-MpPreference -EnableControlledFolderAccess Enabled
```

2. Ajoutez le dossier de démonstration à la liste des dossiers protégés à l’aide de la commande PowerShell :

```powershell
Set-MpPreference -ControlledFolderAccessProtectedFolders C:\demo\
```

3. Télécharger le [fichier de test](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe) de ransomware
4. Exécutez le fichier de test de ransomware *ce n’est pas un ransomware, il tente simplement de chiffrer c:\demo

#### <a name="scenario-1-expected-results"></a>Résultats attendus du scénario 1

5 secondes après l’exécution du fichier de test de ransomware, vous devriez voir une notification CFA bloqué la tentative de chiffrement.

### <a name="scenario-2-what-would-happen-without-cfa"></a>Scénario 2 : Que se passerait-il sans la CFA

1. Désactivez la fonctionnalité CFA à l’aide de cette commande PowerShell :

```powershell
Set-MpPreference -EnableControlledFolderAccess Disabled
```

2. Exécuter le [fichier de test](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe) de ransomware

#### <a name="scenario-2-expected-results"></a>Résultats attendus du scénario 2

- Les fichiers dans c:\demo seront chiffrés et vous devriez recevoir un message d’avertissement
- Réexécuter le fichier de test de ransomware pour déchiffrer les fichiers

## <a name="clean-up"></a>Nettoyer

Téléchargez et exécutez ce [script de nettoyage](https://demo.wd.microsoft.com/Content/ASR_CFA_CleanupScript.zip). Vous pouvez effectuer ces étapes manuelles à la place :

```powershell
Set-MpPreference -EnableControlledFolderAccess Disabled
```

Nettoyer le chiffrement c:\demo exécuter le [fichier chiffre/déchiffrer](https://demo.wd.microsoft.com/Content/ransomware_cleanup_encrypt_decrypt.exe)

## <a name="see-also"></a>Voir aussi
[Accès contrôlé aux dossiers](/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard?ocid=wd-av-demo-cfa-bottom)
