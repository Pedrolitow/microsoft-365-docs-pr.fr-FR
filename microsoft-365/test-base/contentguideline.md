---
title: Instructions relatives aux packages de test
description: Passer en revue les instructions relatives au package de test
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
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
ms.openlocfilehash: eea9d04f2a50ce7a9a858a302eeef2c9feef8868
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67315545"
---
# <a name="test-package-guidelines"></a>Instructions relatives aux packages de test

## <a name="1-script-referencing"></a>1. Référencement de script

Lorsque vous chargez un fichier .zip sur le portail, nous décompressons tout le contenu de ce fichier dans un dossier racine. Vous n’avez pas besoin d’écrire de code pour effectuer cette opération initiale de décompression. Vous pouvez également référencer n’importe quel fichier dans le .zip à l’aide du chemin d’accès relatif au fichier zip chargé.

Dans l’exemple ci-dessous, nous montrons comment vous pouvez référencer vos fichiers binaires/scripts à partir du champ d’entrée dans l’onglet Tâches. Le texte en bleu doit être entré dans le champ **Chemin d’accès** du script **sans guillemets.**

Il est important que vous connaissiez le contenu de votre fichier zip avant de le charger. Souvent, lorsque vous compressez un dossier, votre ordinateur local crée un dossier principal sous le fichier zip. Dans ce cas, le référencement sera affiché en **gras** ci-dessous :

**Contoso_App_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 : **« Contoso_App_Folder/ScriptX.ps1 »**
- Script.ps1 - **« Contoso_App_Folder/folder1/script.ps1 »**

Dans d’autres cas, votre fichier zip peut contenir vos fichiers ou contenus juste en dessous (par exemple, aucun dossier de deuxième niveau) :

**Zip_file_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 - **« ScriptX.ps1 »**
- Script.ps1 - **« folder1/script.ps1 »**

## <a name="2-script-execution"></a>2. Exécution de script

**Tests out-of-box :** Le package d’application doit contenir au moins trois scripts PowerShell. Ces scripts exécutent l’installation, le lancement et la fermeture sans assistance de l’application et de ses dépendances. Chaque script doit gérer la vérification de ses propres prérequis, la validation de sa propre réussite et le nettoyage après lui-même (si nécessaire).

**Tests fonctionnels :** Le package d’application doit contenir au moins un script PowerShell. Lorsque plusieurs scripts sont fournis, les scripts sont exécutés dans la séquence de chargement et un échec dans un script particulier empêche l’exécution des scripts suivants.

### <a name="script-requirements"></a> Conditions requises pour les scripts

- PowerShell version 5.1+
- Exécution sans assistance
- Code de retour d’erreur
- Valider la réussite
- Journalisation dans un dossier de journal spécifique au script

Chaque script doit s’exécuter sans assistance (aucune invite utilisateur) pour s’exécuter correctement dans le pipeline de test.

> [!NOTE]
> Les scripts doivent retourner « 0 » une fois l’exécution réussie et un code d’erreur différent de zéro si une erreur se produit pendant l’exécution.

Chaque script doit vérifier qu’il s’est exécuté correctement. Par exemple, le script d’installation doit vérifier l’existence de certains fichiers binaires et/ou clés de Registre sur le système une fois le fichier binaire du programme d’installation terminé. Cette vérification permet de s’assurer avec un degré raisonnable de confiance que l’installation a réussi.

La validation est nécessaire pour diagnostiquer correctement l’endroit où des erreurs se produisent pendant une série de tests. Par exemple, si le script ne parvient pas à installer correctement l’application plutôt qu’à ne pas pouvoir la lancer.

> [!IMPORTANT]
> **Évitez les éléments suivants :** Les scripts ne doivent pas redémarrer l’ordinateur. Si un redémarrage est nécessaire, spécifiez-le lors du chargement de vos scripts.

## <a name="3-log-collection"></a>3. Collecte des journaux

Chaque script doit générer les journaux qu’il génère dans un dossier nommé `logs`. Tous les dossiers du répertoire nommé `logs` seront copiés et présentés pour téléchargement sur la `Test Results` page.

Par exemple, le script d’installation (qui peut se trouver dans le répertoire **App/scripts/install** ) peut générer ses journaux vers : **logs/install.log**, de sorte que le journal final se trouve à : **Apps/scripts/install/logs/install.log.**

Le système récupère le `install.log` fichier avec d’autres fichiers dans d’autres `logs` dossiers et le rassemble pour téléchargement.

## <a name="4-application-binaries"></a>4. Fichiers binaires d’application

Tous les fichiers binaires et dépendances doivent être inclus dans le fichier zip unique.

Ces fichiers binaires doivent inclure tout ce qui est nécessaire pour l’installation de l’application (par exemple, le programme d’installation de l’application). Si l’application a une dépendance vis-à-vis des frameworks, tels que .NET Core/Standard ou .NET Framework, ces frameworks doivent être inclus dans le fichier et référencés correctement dans les scripts fournis.

> [!NOTE]
> Le fichier zip chargé ne peut pas contenir d’espaces ou de caractères spéciaux dans son nom

## <a name="5-applicationtest-rules"></a>5. Règles d’application/test

Pour que vos applications/tests s’exécutent correctement sous l’infrastructure de base de test, ils doivent se conformer aux règles décrites dans les [règles d’application/test ](rules.md). 

## <a name="next-steps"></a>Prochaines étapes

Passez à l’article suivant pour afficher certaines **questions fréquentes (FAQ)**
> [!div class="nextstepaction"]
> [Étape suivante](faq.md)
