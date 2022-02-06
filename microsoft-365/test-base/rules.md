---
title: Règles d’application/test
description: Règles à suivre lors du chargement d’une application/test
search.appverid: MET150
author: andreicsibi-msft
ms.author: ancsibi
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: null
ms.reviewer: mapatel
f1.keywords: NOCSH
---
# <a name="applicationtest-rules"></a>Règles d’application/test

Toutes les applications ou tests de la Base de test doivent respecter les règles suivantes :

## <a name="test-base-folders"></a>Tester les dossiers de base 

Les dossiers suivants sont utilisés par l’infrastructure de base de test :
* %SYSTEMDRIVE%\USL
* %SYSTEMDRIVE%\EtlExport
* %SYSTEMDRIVE%\Ffmpeg
* %SYSTEMDRIVE%\Monitoring
* %SYSTEMDRIVE%\powershell-yaml
* %SYSTEMDRIVE%\ProcMon
* %SYSTEMDRIVE%\PSTools
* %SYSTEMDRIVE%\TokenProviderTool
* %SYSTEMDRIVE%\USLPowershellModules
* %SYSTEMDRIVE%\UtcUtil
* %SYSTEMDRIVE%\WPT
* %SYSTEMDRIVE%\WULogs

> [!IMPORTANT]
> **Évitez les problèmes suivants** :
> * Blocage de l’exécution de tout processus à partir de ces dossiers. Si votre application est un logiciel anti-programme malveillant, configurez l’installation de votre application pour autoriser l’exécution sans programme malveillant de tous les processus de ces dossiers.
> * Falsification de l’un de ces dossiers.

## <a name="test-base-registry-keys"></a>Tester les clés de Registre de base

Les applications/tests ne doivent pas supprimer ou modifier les clés de Registre liées aux éléments :
* Windows télémétrie
* Suppression de TLS 1.2
