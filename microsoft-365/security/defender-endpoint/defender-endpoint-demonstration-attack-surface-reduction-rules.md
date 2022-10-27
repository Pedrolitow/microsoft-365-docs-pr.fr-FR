---
title: démonstrations des règles de réduction de la surface d’attaque Microsoft Defender pour point de terminaison
description: Découvrez comment les règles de réduction de la surface d’attaque bloquent différents types de menaces connus.
keywords: démonstration Microsoft Defender pour point de terminaison, démonstration des règles de réduction de la surface d’attaque, règles ASR, démonstration
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
ms.openlocfilehash: b0c57f4fc094d8efbcd2fd13f4c4835536dceb21
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729850"
---
# <a name="attack-surface-reduction-rules-demonstrations"></a>Démonstrations des règles de réduction de la surface d’attaque

Les règles de réduction de la surface d’attaque (ASR) ciblent des comportements spécifiques qui sont généralement utilisés par des programmes malveillants et des applications malveillantes pour infecter des machines, par exemple :

- Fichiers exécutables et scripts utilisés dans les applications Office ou la messagerie web qui tentent de télécharger ou d’exécuter des fichiers
- Scripts obfusqués ou suspects
- Comportements que les applications effectuent et qui ne sont pas initiés pendant le travail quotidien normal

## <a name="scenario-requirements-and-setup"></a>Configuration requise et configuration du scénario

- Windows 10 1709 build 16273
- build Windows 10 1803 (règles 1803)
- Microsoft Defender AV
- Microsoft Office (requis pour les règles et l’exemple Office)
- [Télécharger les scripts PowerShell ASR](https://demo.wd.microsoft.com/Content/WindowsDefender_ASR_scripts.zip)

## <a name="powershell-commands"></a>Commandes PowerShell

```powershell
Add-MpPreference -AttackSurfaceReductionRules_Ids BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EfC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 3B576869-A4EC-4529-8536-B80A7769E899 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D3E037E1-3EB8-44C8-A917-57927947596D -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 5BEB7EFE-FD9A-4556-801D-275E5FFC04CC -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D1E49AAC-8F56-4280-B9BA-993A6D77406C -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids B2B3F03D-6A65-4F7B-A9C7-1C7EF74A9BA4 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids C1DB55AB-C21A-4637-BB3F-A12568109D35 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 01443614-CD74-433A-B99E-2ECDC07BFC25 -AttackSurfaceReductionRules_Actions Enabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 26190899-1602-49E8-8B27-EB1D0A1CE869 -AttackSurfaceReductionRules_Actions AuditMode
Add-MpPreference -AttackSurfaceReductionRules_Ids 7674BA52-37EB-4A4F-A9A1-F0F9A1619A2C -AttackSurfaceReductionRules_Actions AuditMode
```

### <a name="rule-states"></a>États de règle

|État | Mode| Valeur numérique |
|:---|:---|:---|
| Désactivé | = Désactivé | 0 |
| Activé | = Mode bloc | 1 |
| Audit | = Mode d’audit | 2 |

### <a name="verify-configuration"></a>Vérifier la configuration

```powershell

Get-MpPreference
```

## <a name="test-files"></a>Fichiers de test

Remarque : certains fichiers de test ont plusieurs attaques incorporées et déclenchent plusieurs règles

| Nom de la règle | GUID de règle | Version de Windows |
|:---|:---|:---|
| Bloquer le contenu exécutable du client de messagerie et de la messagerie web | BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550 | 1709 |
| [Empêcher les applications Office de créer des processus enfants](https://demo.wd.microsoft.com/Content/TestFile_OfficeChildProcess_D4F940AB-401B-4EFC-AADC-AD5F3C50688A.docm) | D4F940AB-401B-4EFC-AADC-AD5F3C50688A | 1709 |
| [Empêcher les applications Office de créer du contenu exécutable](https://demo.wd.microsoft.com/Content/TestFile_Block_Office_applications_from_creating_executable_content_3B576869-A4EC-4529-8536-B80A7769E899.docm) | 3B576869-A4EC-4529-8536-B80A7769E899 | 1709 |
| Empêcher les applications Office de s’injecter dans d’autres processus | 75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84 | 1709 |
| [Empêcher JavaScript et VBScript de lancer des exécutables](https://demo.wd.microsoft.com/Content/TestFile_Impede_JavaScript_and_VBScript_to_launch_executables_D3E037E1-3EB8-44C8-A917-57927947596D.js) | D3E037E1-3EB8-44C8-A917-57927947596D | 1709 |
| Bloquer l’exécution de scripts potentiellement obfusqués | 5BEB7EFE-FD9A-4556-801D-275E5FFC04CC | 1709 |
| [Bloquer les importations Win32 à partir du code macro dans Office](https://demo.wd.microsoft.com/Content/Block_Win32_imports_from_Macro_code_in_Office_92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B.docm) | 92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B | 1709 |
|[{Bloquer les créations de processus provenant de PSExec & commandes WMI](https://demo.wd.microsoft.com/Content/TestFile_PsexecAndWMICreateProcess_D1E49AAC-8F56-4280-B9BA-993A6D77406C.vbs) | D1E49AAC-8F56-4280-B9BA-993A6D77406C | 1803 |
| [Bloquer l’exécution d’exécutables non approuvés ou non signés à l’intérieur d’un support USB amovible](https://demo.wd.microsoft.com/Content/UNSIGNED_ransomware_test_exe.exe) | B2B3F03D-6A65-4F7B-A9C7-1C7EF74A9BA4 | 1803 |
| Prévention agressive contre les ransomwares | C1DB55AB-C21A-4637-BB3F-A12568109D35 | 1803 |
| Bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de liste de confiance | 01443614-CD74-433A-B99E-2ECDC07BFC25 | 1803 |
| Empêcher Adobe Reader de créer des processus enfants | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c | 1803 |

## <a name="scenarios"></a>Scénarios

### <a name="setup"></a>Configuration

Téléchargez et exécutez ce [script d’installation](https://demo.wd.microsoft.com/Content/ASR_SetupScript.zip). Avant d’exécuter la stratégie d’exécution du jeu de scripts sur Non restreint à l’aide de cette commande PowerShell :

```powershell
Set-ExecutionPolicy Unrestricted

```

Vous pouvez effectuer ces étapes manuelles à la place :

1. Créez un dossier sous c: named demo, « c:\demo »
2. Enregistrez ce [fichier propre](https://demo.wd.microsoft.com/Content/testfile_safe.txt) dans c:\demo.
3. Activez toutes les règles à l’aide des commandes powershell ci-dessus.

### <a name="scenario-1-asr-blocks-a-test-file-with-multiple-vulnerabilities"></a>Scénario 1 : ASR bloque un fichier de test avec plusieurs vulnérabilités

1. Activer toutes les règles en mode bloc à l’aide des commandes PowerShell ci-dessus (vous pouvez copier-coller tout)
2. Téléchargez et ouvrez l’un des fichiers/documents de test liés ci-dessus, puis activez la modification et le contenu si vous y êtes invité.

#### <a name="scenario-1-expected-results"></a>Résultats attendus du scénario 1

Vous devez immédiatement voir une notification « Action bloquée ».

### <a name="scenario-2-asr-rule-blocks-the-test-file-with-the-corresponding-vulnerability"></a>Scénario 2 : la règle ASR bloque le fichier de test avec la vulnérabilité correspondante

1. Configurez la règle que vous souhaitez tester à l’aide de la commande PowerShell ci-dessus.
2. Exemple : `Add-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EfC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions Enabled`
3. Téléchargez et ouvrez le fichier/document de test pour la règle que vous souhaitez tester liée ci-dessus, activez la modification et le contenu si vous y êtes invité
4. Exemple : [Empêcher les applications Office de créer des processus enfants](https://demo.wd.microsoft.com/Content/ransomware_testfile_doc.docm) D4F940AB-401B-4EFC-AADC-AD5F3C50688A

#### <a name="scenario-2-expected-results"></a>Résultats attendus du scénario 2

Vous devez immédiatement voir une notification « Action bloquée ».

### <a name="scenario-3-1803-asr-rule-blocks-unsigned-usb-content-from-executing"></a>Scénario 3 (1803) : la règle ASR empêche l’exécution du contenu USB non signé

1. Configurez la règle de protection USB (B2B3F03D-6A65-4F7B-A9C7-1C7EF74A9BA4).

```powershell
Add-MpPreference -AttackSurfaceReductionRules_Ids B2B3F03D-6A65-4F7B-A9C7-1C7EF74A9BA4 -AttackSurfaceReductionRules_Actions Enabled
```

3. Téléchargez le fichier et placez-le sur une clé USB et [exécutez-le Bloquer l’exécution d’exécutables non approuvés ou non signés à l’intérieur d’un support USB amovible](https://demo.wd.microsoft.com/Content/UNSIGNED_ransomware_test_exe.exe)

#### <a name="scenario-3-expected-results"></a>Résultats attendus du scénario 3

Vous devez immédiatement voir une notification « Action bloquée ».

### <a name="scenario-4-what-would-happen-without-asr"></a>Scénario 4 : Que se passerait-il sans ASR

1. Désactiver toutes les règles ASR à l’aide des commandes PowerShell ci-dessous dans la section nettoyage
2. Téléchargez n’importe quel fichier/document de test lié ci-dessus, activez la modification et le contenu si vous y êtes invité

#### <a name="scenario-4-expected-results"></a>Résultats attendus du scénario 4

- Les fichiers dans c:\demo seront chiffrés et vous devriez recevoir un message d’avertissement
- Réexécuter le fichier de test pour déchiffrer les fichiers

## <a name="clean-up"></a>Nettoyer

Télécharger et exécuter ce [script de nettoyage](https://demo.wd.microsoft.com/Content/ASR_CFA_CleanupScript.zip)

Vous pouvez également effectuer ces étapes manuelles :

```powershell
Add-MpPreference -AttackSurfaceReductionRules_Ids BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D4F940AB-401B-4EfC-AADC-AD5F3C50688A -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 3B576869-A4EC-4529-8536-B80A7769E899 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D3E037E1-3EB8-44C8-A917-57927947596D -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 5BEB7EFE-FD9A-4556-801D-275E5FFC04CC -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 92E97FA1-2EDF-4476-BDD6-9DD0B4DDDC7B -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids D1E49AAC-8F56-4280-B9BA-993A6D77406C -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids B2B3F03D-6A65-4F7B-A9C7-1C7EF74A9BA4 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids C1DB55AB-C21A-4637-BB3F-A12568109D35 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 01443614-CD74-433A-B99E-2ECDC07BFC25 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 26190899-1602-49E8-8B27-EB1D0A1CE869 -AttackSurfaceReductionRules_Actions Disabled
Add-MpPreference -AttackSurfaceReductionRules_Ids 7674BA52-37EB-4A4F-A9A1-F0F9A1619A2C -AttackSurfaceReductionRules_Actions Disabled
```

Nettoyer le chiffrement c:\demo exécuter le [fichier chiffre/déchiffrer](https://demo.wd.microsoft.com/Content/ransomware_cleanup_encrypt_decrypt.exe)

## <a name="see-also"></a>Voir aussi

[Guide de déploiement des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-deployment.md)

[Informations de référence sur les règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)

[Microsoft Defender pour point de terminaison - scénarios de démonstration](defender-endpoint-demonstrations.md)
