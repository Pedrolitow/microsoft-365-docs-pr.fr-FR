---
title: Recommandations en matière de package de test
description: Passer en revue les recommandations relatives au package de test
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
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
# <a name="test-package-guidelines"></a>Recommandations en matière de package de test

## <a name="1-script-referencing"></a>1. Référencement de script

Lorsque vous téléchargez un .zip sur le portail, nous dézipons tout le contenu de ce fichier dans un dossier racine. Vous n’avez pas besoin d’écrire de code pour cette opération de dézipage initiale. Vous pouvez également référencer n’importe quel fichier dans le .zip en utilisant le chemin d’accès relatif au fichier zip téléchargé.

Dans l’exemple ci-dessous, nous montrons comment vous pouvez référencer vos binaires/scripts à partir du champ d’entrée dans l’onglet Tâches. Le texte en bleu doit être entré dans le champ de chemin **d’accès** script **sans les guillemets.**

Il est important de connaître le contenu de votre fichier zip avant de le télécharger. Souvent, lorsque vous compressez un dossier, votre ordinateur local crée un dossier principal sous le fichier zip. Dans ce cas, le référencement sera affiché en **gras** ci-dessous :

**Contoso_App_Folder.zip**:

```console
├── Contoso_App_Folder

│   ├── file1.exe

│   ├── ScriptX.ps1

│   ├── folder1

│      ├── file3.exe

│      ├── script.ps1
```

- ScriptX.ps1 - **« Contoso_App_Folder/ScriptX.ps1 »**
- Script.ps1 - **« Contoso_App_Folder/folder1/script.ps1 »**

Dans d’autres cas, il se peut que vos fichiers ou votre contenu se trouve juste en dessous de votre fichier zip (par exemple, pas de dossier de 2e niveau) :

**Zip_file_uploaded.zip**:

```console
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
```

- ScriptX.ps1 - **« ScriptX.ps1 »**
- Script.ps1 - **« folder1/script.ps1 »**

## <a name="2-script-execution"></a>2. Exécution de script

**Tests out-of-Box :** Le package d’application doit contenir au moins trois scripts PowerShell. Ces scripts exécutent l’installation, le lancement et la fermeture sans surveillance de l’application et de ses dépendances. Chaque script doit gérer la vérification de ses propres conditions préalables, la validation de sa propre réussite et le nettoyage après lui-même (si nécessaire).

**Tests fonctionnels :** Le package d’application doit contenir au moins un script PowerShell. Lorsque plusieurs scripts sont fournis, ils sont exécutés dans une séquence de chargement et un échec dans un script particulier arrête l’exécution des scripts suivants.

### <a name="script-requirements"></a> Conditions requises pour les scripts

- PowerShell Version 5.1+
- Exécution sans surveillance
- Code de retour d’erreur
- Valider la réussite
- Journalisation dans un dossier journal spécifique au script

Chaque script doit s’exécuter sans surveillance (aucune invite de l’utilisateur) pour s’exécuter correctement dans le pipeline de test.

> [!NOTE]
> Les scripts doivent renvoyer « 0 » à l’exécution réussie et un code d’erreur non nul si une erreur se produit pendant l’exécution.

Chaque script doit vérifier qu’il a été correctement lancé. Par exemple, le script d’installation doit vérifier l’existence de certains binaires et/ou clés de Registre sur le système après l’exécution du fichier binaire du programme d’installation. Cette vérification permet de s’assurer avec un degré raisonnable de confiance que l’installation a réussi.

La validation est nécessaire pour diagnostiquer correctement l’endroit où des erreurs se produisent au cours d’une utilisation de test. Par exemple, si le script ne parvient pas à installer l’application ou ne peut pas la lancer.

> [!IMPORTANT]
> **Évitez les problèmes suivants :** Les scripts ne doivent pas redémarrer l’ordinateur, si un redémarrage est nécessaire, veuillez le spécifier lors du chargement de vos scripts.

## <a name="3-log-collection"></a>3. Collection de journaux

Chaque script doit générer tous les journaux qu’il génère dans un dossier nommé `logs`. Tous les dossiers du répertoire nommé `logs` seront copiés et présentés en téléchargement sur la `Test Results` page.

Par exemple, le script d’installation (qui peut se trouver dans le répertoire **App/scripts/install** ) peut obtenir ses journaux dans : **logs/install.log**, de telle telle part que le journal final se trouve à l’emplacement suivant : **Apps/scripts/install/logs/install.log**

Le système sélectionne le fichier ainsi que `install.log` d’autres fichiers `logs` dans d’autres dossiers et le rassemble pour téléchargement.

## <a name="4-application-binaries"></a>4. Binaires d’application

Tous les fichiers binaires et dépendances doivent être inclus dans le fichier zip unique.

Ces binaires doivent inclure tous les éléments nécessaires à l’installation de l’application (par exemple, le programme d’installation de l’application). Si l’application dépend d’une infrastructure, telle que .NET Core/Standard ou .NET Framework, ces frameworks doivent être incluses dans le fichier et correctement référencés dans les scripts fournis.

> [!NOTE]
> Le fichier zip téléchargé ne peut pas avoir d’espaces ou de caractères spéciaux dans son nom

## <a name="5-applicationtest-rules"></a>5. Règles d’application/test

Pour que vos applications/tests s’exécutent correctement dans l’infrastructure de base de test, ils doivent respecter les règles décrites dans les règles [d’application/test ](rules.md). 

## <a name="next-steps"></a>Étapes suivantes

Passer à l’article suivant pour afficher certaines **questions fréquemment posées (FAQ)**
> [!div class="nextstepaction"]
> [Étape suivante](faq.md)
