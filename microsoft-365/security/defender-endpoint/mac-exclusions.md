---
title: Configurer et valider les exclusions pour Microsoft Defender pour point de terminaison sur Mac
description: Fournissez et validez des exclusions pour Microsoft Defender pour point de terminaison sur Mac. Des exclusions peuvent être définies pour les fichiers, les dossiers et les processus.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, exclusions, analyses, antivirus
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 3efc1d4b6beea3c2fe63bcea8de86534ec95de02
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67692338"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-macos"></a>Configurer et valider des exclusions pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article fournit des informations sur la définition des exclusions qui s’appliquent aux analyses à la demande, ainsi que sur la protection et la surveillance en temps réel.

> [!IMPORTANT]
> Les exclusions décrites dans cet article ne s’appliquent pas à d’autres fonctionnalités de Defender pour point de terminaison sur Mac, notamment la détection et la réponse des points de terminaison (EDR). Les fichiers que vous excluez à l’aide des méthodes décrites dans cet article peuvent toujours déclencher des alertes EDR et d’autres détections.

Vous pouvez exclure certains fichiers, dossiers, processus et fichiers ouverts par processus à partir des analyses Defender pour point de terminaison sur Mac.

Les exclusions peuvent être utiles pour éviter les détections incorrectes sur les fichiers ou les logiciels qui sont uniques ou personnalisés pour votre organisation. Ils peuvent également être utiles pour atténuer les problèmes de performances causés par Defender pour point de terminaison sur Mac.

> [!WARNING]
> La définition d’exclusions réduit la protection offerte par Defender pour point de terminaison sur Mac. Vous devez toujours évaluer les risques associés à l’implémentation d’exclusions, et vous ne devez exclure que les fichiers dont vous êtes certain qu’ils ne sont pas malveillants.

## <a name="supported-exclusion-types"></a>Types d’exclusion pris en charge

Le tableau suivant présente les types d’exclusion pris en charge par Defender pour point de terminaison sur Mac.

Exclusion|Définition|Exemples
---|---|---
Extension de fichier|Tous les fichiers avec l’extension, n’importe où sur l’ordinateur|`.test`
File|Un fichier spécifique identifié par le chemin d’accès complet|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`
Folder|Tous les fichiers sous le dossier spécifié (de manière récursive)|`/var/log/` <p> `/var/*/`
Processus|Un processus spécifique (spécifié par le chemin d’accès complet ou le nom du fichier) et tous les fichiers ouverts par celui-ci|`/bin/cat` <p> `cat` <p> `c?t`

Les exclusions de fichiers, de dossiers et de processus prennent en charge les caractères génériques suivants :

Caractère générique|Description|Exemple|Matchs|Ne correspond pas
---|---|---|---|---
\*|Correspond à n’importe quel nombre de caractères, y compris aucun (notez que lorsque ce caractère générique est utilisé dans un chemin d’accès, il ne remplace qu’un seul dossier)|`/var/*/*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|Correspond à n’importe quel caractère unique|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`

> [!NOTE]
> Le produit tente de résoudre les liens fermes lors de l’évaluation des exclusions. La résolution de liens fermes ne fonctionne pas lorsque l’exclusion contient des caractères génériques ou que le fichier cible (sur le `Data` volume) n’existe pas.

## <a name="how-to-configure-the-list-of-exclusions"></a>Comment configurer la liste des exclusions

### <a name="from-the-management-console"></a>À partir de la console de gestion

Pour plus d’informations sur la configuration des exclusions de JAMF, de Intune ou d’une autre console de gestion, consultez [Définir les préférences pour Defender pour point de terminaison sur Mac](mac-preferences.md).

### <a name="from-the-user-interface"></a>À partir de l’interface utilisateur

Ouvrez l’application Defender pour point de terminaison et accédez à **Gérer les paramètres** \> **Ajouter ou Supprimer l’exclusion...**, comme illustré dans la capture d’écran suivante :

:::image type="content" source="images/mdatp-37-exclusions.png" alt-text="Page Gérer les exclusions" lightbox="images/mdatp-37-exclusions.png":::

Sélectionnez le type d’exclusion que vous souhaitez ajouter et suivez les invites.

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider les listes d’exclusions avec le fichier de test EICAR

Vous pouvez vérifier que vos listes d’exclusion fonctionnent en téléchargeant `curl` un fichier de test.

Dans l’extrait de code Bash suivant, remplacez-le par `test.txt` un fichier conforme à vos règles d’exclusion. Par exemple, si vous avez exclu l’extension`.testing`, remplacez `test.testing``test.txt` par . Si vous testez un chemin d’accès, veillez à exécuter la commande dans ce chemin d’accès.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

Si Defender pour point de terminaison sur Mac signale des programmes malveillants, la règle ne fonctionne pas. S’il n’existe aucun rapport de programmes malveillants et que le fichier téléchargé existe, l’exclusion fonctionne. Vous pouvez ouvrir le fichier pour vérifier que le contenu est le même que celui décrit sur le [site web du fichier de test EICAR](http://2016.eicar.org/86-0-Intended-use.html).

Si vous n’avez pas accès à Internet, vous pouvez créer votre propre fichier de test EICAR. Écrivez la chaîne EICAR dans un nouveau fichier texte avec la commande Bash suivante :

```bash
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > test.txt
```

Vous pouvez également copier la chaîne dans un fichier texte vide et tenter de l’enregistrer avec le nom du fichier ou dans le dossier que vous tentez d’exclure.

## <a name="allow-threats"></a>Autoriser les menaces

En plus d’exclure certains contenus de l’analyse, vous pouvez également configurer le produit pour ne pas détecter certaines classes de menaces (identifiées par le nom de la menace). Vous devez faire preuve de prudence lors de l’utilisation de cette fonctionnalité, car elle peut laisser votre appareil non protégé.

Pour ajouter un nom de menace à la liste autorisée, exécutez la commande suivante :

```bash
mdatp threat allowed add --name [threat-name]
```

Le nom de menace associé à une détection sur votre appareil peut être obtenu à l’aide de la commande suivante :

```bash
mdatp threat list
```

Par exemple, pour ajouter `EICAR-Test-File (not a virus)` (le nom de menace associé à la détection EICAR) à la liste autorisée, exécutez la commande suivante :

```bash
mdatp threat allowed add --name "EICAR-Test-File (not a virus)"
```
