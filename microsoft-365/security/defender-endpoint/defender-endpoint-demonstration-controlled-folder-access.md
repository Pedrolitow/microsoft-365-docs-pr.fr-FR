---
title: démonstrations Microsoft Defender pour point de terminaison’accès contrôlé aux dossiers (CFA)
description: Montre comment l’accès contrôlé aux dossiers protège les données précieuses contre les applications malveillantes et les menaces, telles que les ransomwares.
keywords: Microsoft Defender pour point de terminaison, protection d’accès contrôlé aux dossiers, démonstration de l’accès contrôlé aux dossiers
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
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: d3898738f5030b626180d318eaa6137ad7e7f5ba
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634407"
---
# <a name="controlled-folder-access-cfa-demonstrations-block-ransomware"></a>Démonstrations d’accès contrôlé aux dossiers (CFA) (block ransomware)

L’accès contrôlé aux dossiers vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomwares. Toutes les applications (tout fichier exécutable, y compris les fichiers .exe, .scr, .dll et autres) sont évaluées par Microsoft Defender Antivirus, qui détermine ensuite si l’application est malveillante ou sécurisée. Si l’application est déterminée comme malveillante ou suspecte, elle ne sera pas autorisée à apporter des modifications à des fichiers dans un dossier protégé.

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- antivirus Microsoft Defender (mode actif)

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
| AuditMode | = Mode Audit | 2 |
| Activé | = Mode bloc | 1 |
| Désactivé | = Désactivé | 0 |

## <a name="verify-configuration"></a>Vérifier la configuration

```powershell
Get-MpPreference
```

## <a name="test-file"></a>Fichier de test

[Fichier de test ransomware CFA](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe)

## <a name="scenarios"></a>Scénarios

### <a name="setup"></a>Configuration

Téléchargez et exécutez ce [script d’installation](https://demo.wd.microsoft.com/Content/CFA_SetupScript.zip). Avant d’exécuter la stratégie d’exécution du script, définissez La stratégie d’exécution sur Unrestricted à l’aide de cette commande PowerShell : 

```powershell
Set-ExecutionPolicy Unrestricted
```

Vous pouvez effectuer ces étapes manuelles à la place :

1. Créer un dossier sous c : démonstration nommée, « c:\demo »
2. Enregistrez ce [fichier propre](https://demo.wd.microsoft.com/Content/testfile_safe.txt) dans c:\demo (nous avons besoin de quelque chose pour chiffrer)
3. Exécuter des commandes PowerShell ci-dessus

### <a name="scenario-1-cfa-blocks-ransomware-test-file"></a>Scénario 1 : LE CFA bloque le fichier de test ransomware

1. Activez CFA à l’aide de la commande PowerShell : 
  
```powershell
Set-MpPreference -EnableControlledFolderAccess Enabled
```

2. Ajoutez le dossier de démonstration à la liste des dossiers protégés à l’aide de la commande PowerShell :

```powershell
Set-MpPreference -ControlledFolderAccessProtectedFolders C:\demo\
```

3. Télécharger le [fichier de test](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe) ransomware
4. Exécuter le fichier de test ransomware *ce n’est pas ransomware, il tente simplement de chiffrer c:\demo

#### <a name="scenario-1-expected-results"></a>Résultats attendus du scénario 1

5 secondes après l’exécution du fichier de test ransomware, vous devriez voir une notification CFA bloquer la tentative de chiffrement.

### <a name="scenario-2-what-would-happen-without-cfa"></a>Scénario 2 : Que se passerait-il sans CFA ?

1. Désactivez CFA à l’aide de cette commande PowerShell : 

```powershell
Set-MpPreference -EnableControlledFolderAccess Disabled
```

2. Exécuter le [fichier de test](https://demo.wd.microsoft.com/Content/ransomware_testfile_unsigned.exe) ransomware

#### <a name="scenario-2-expected-results"></a>Résultats attendus du scénario 2

- Les fichiers dans c:\demo seront chiffrés et vous devriez recevoir un message d’avertissement
- Réexécutez le fichier de test ransomware pour déchiffrer les fichiers

## <a name="clean-up"></a>Nettoyer

Téléchargez et [exécutez ce script de nettoyage](https://demo.wd.microsoft.com/Content/ASR_CFA_CleanupScript.zip). Vous pouvez effectuer ces étapes manuelles à la place :

```powershell
Set-MpPreference -EnableControlledFolderAccess Disabled
```

Nettoyer c:\demo encryption exécuter le [fichier de chiffrement/déchiffrement](https://demo.wd.microsoft.com/Content/ransomware_cleanup_encrypt_decrypt.exe)

## <a name="see-also"></a>Voir aussi
[Accès contrôlé aux dossiers](/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard?ocid=wd-av-demo-cfa-bottom)
