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
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: 6a3878e0326fdcfe1ea9d35997e6a605457fcbf7
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67316487"
---
# <a name="applicationtest-rules"></a>Règles d’application/test

Toutes les applications ou tests de la base de test doivent respecter les règles suivantes :

## <a name="test-base-folders"></a>Dossiers de base de test 

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
> **Évitez les éléments suivants :**
> * Blocage de l’exécution d’un processus à partir de ces dossiers. Si votre application est un logiciel anti-programme malveillant, configurez l’installation de votre application pour permettre l’exécution sans entrave de tous les processus de ces dossiers.
> * Falsification de l’un de ces dossiers.

## <a name="test-base-registry-keys"></a>Tester les clés de Registre de base

Les applications/tests ne doivent pas supprimer ou modifier les clés de Registre liées aux éléments suivants :
* Niveau de télémétrie Windows
* Suppression de TLS 1.2
