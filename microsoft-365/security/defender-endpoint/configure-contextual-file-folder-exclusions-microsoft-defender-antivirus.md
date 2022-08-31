---
title: Exclusions de fichiers et de dossiers contextuels
description: Décrit la fonctionnalité d’exclusions de fichiers et de dossiers contextuelles pour l’antivirus Microsoft Defender sur Windows. Cette fonctionnalité vous permet d’être plus spécifique lorsque vous définissez dans quel contexte l’Antivirus Microsoft Defender ne doit pas analyser un fichier ou un dossier, en appliquant des restrictions
keywords: Antivirus Microsoft Defender, processus, exclusion, fichiers, analyses
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
ms.date: 08/25/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 0868250b04120a4eed0cf254e4a9d3692eb661fa
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67477954"
---
# <a name="contextual-file-and-folder-exclusions"></a>Exclusions de fichiers et de dossiers contextuels

Cet article/section décrit la fonctionnalité d’exclusions de fichiers et de dossiers contextuelles pour l’antivirus Microsoft Defender sur Windows. Cette fonctionnalité vous permet d’être plus précis lorsque vous définissez dans quel contexte l’Antivirus Microsoft Defender ne doit pas analyser un fichier ou un dossier, en appliquant des restrictions.

## <a name="overview"></a>Vue d’ensemble

Les exclusions sont principalement destinées à atténuer les effets sur les performances. Ils sont passibles d’une réduction de la valeur de protection. Ces restrictions vous permettent de limiter cette réduction de protection en spécifiant les circonstances dans lesquelles l’exclusion doit s’appliquer. Les exclusions contextuelles ne conviennent pas pour traiter les faux positifs de manière fiable. Si vous rencontrez un faux positif, vous pouvez envoyer des fichiers à des fins d’analyse par le biais du portail [Microsoft 365 Defender](https://security.microsoft.com/) (abonnement requis) ou du site web [Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission). Pour une méthode de suppression temporaire, envisagez de créer un indicateur _d’autorisation_ personnalisé dans [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/indicator-file).

Vous pouvez appliquer quatre restrictions pour limiter l’applicabilité d’une exclusion :

- **Restriction du type de chemin d’accès au fichier/dossier**. Vous pouvez limiter les exclusions à appliquer uniquement si la cible est un fichier ou un dossier en définissant l’intention spécifique. Si la cible est un fichier mais que l’exclusion est spécifiée comme dossier, elle ne s’applique pas. Inversement, si la cible est un dossier mais que l’exclusion est spécifiée comme un fichier, l’exclusion s’applique.
- **Restriction de type d’analyse**. Vous permet de définir le type d’analyse requis pour une exclusion à appliquer. Par exemple, vous souhaitez uniquement exclure un certain dossier des analyses complètes, mais pas d’une analyse « ressource » (analyse ciblée).
- **Restriction du type de déclencheur d’analyse**. Vous pouvez utiliser cette restriction pour spécifier que l’exclusion ne doit s’appliquer que lorsque l’analyse a été lancée par un événement spécifique :
  - à la demande
  - sur l’accès
  - ou provenant de la surveillance comportementale
- **Restriction de processus**. Vous permet de définir qu’une exclusion ne doit s’appliquer que lorsqu’un fichier ou un dossier est accessible par un processus spécifique.

## <a name="configuring-restrictions"></a>Configuration des restrictions

Les restrictions sont généralement appliquées en ajoutant le type de restriction au chemin d’exclusion de fichier ou de dossier.  

| Restriction | TypeName | valeur |
|:---|:---|:---|
| Fichier/dossier  | PathType  | file <br> folder |
| Type d’analyse | ScanType | Rapide <br> Plein |
| Déclencheur d’analyse | ScanTrigger | Ondemand <br> OnAccess <br> Bm |
| Processus | Processus | « <image_path> » |

### <a name="requirements"></a>Conditions requises

Cette fonctionnalité nécessite l’antivirus Microsoft Defender :

- Plateforme : **4.18.2205.7** ou version ultérieure
- Moteur : **1.1.19300.2** ou version ultérieure

### <a name="syntax"></a>Syntaxe

À titre de point de départ, vous pouvez déjà avoir des exclusions en place que vous souhaitez rendre plus spécifiques. Pour former la chaîne d’exclusion, commencez par définir le chemin d’accès au fichier ou au dossier à exclure, puis ajoutez le nom de type et la valeur associée, comme indiqué dans l’exemple suivant.

`<PATH>\:{TypeName:value,TypeName:value}`

Gardez à l’esprit que _tous les_ **types** et **valeurs** respectent la casse.

> [!NOTE]  
> Les conditions à l’intérieur `{}` DOIVENT être remplies pour que la restriction corresponde. Par exemple, si vous spécifiez deux déclencheurs d’analyse, cela ne peut pas être vrai et l’exclusion ne s’applique pas. Pour spécifier deux restrictions du même type, créez deux exclusions distinctes.


### <a name="examples"></a>Exemples

La chaîne suivante exclut « c:\documents\design.doc » uniquement s’il s’agit d’un fichier et uniquement dans les analyses d’accès :

`c:\documents\design.doc\:{PathType:file,ScanTrigger:OnAccess}`

La chaîne suivante exclut « c:\documents\design.doc » uniquement si elle est analysée (sur accès) car elle est accessible par un processus portant le nom d’image « winword.exe » :

`c:\documents\design.doc\:{Process:"winword.exe"}`

Le chemin d’accès de l’image de processus peut contenir des caractères génériques, comme dans l’exemple suivant :

`c:\documents\design.doc\:{Process:"C:\Program Files*\Microsoft Office\root\Office??\winword.exe"}`

### <a name="filefolder-restriction"></a>Restriction de fichier/dossier

Vous pouvez limiter les exclusions à appliquer uniquement si la cible est un fichier ou un dossier en rendant l’intention spécifique. Si la cible est un fichier, mais que l’exclusion est spécifiée comme un dossier, l’exclusion ne s’applique pas. Inversement, si la cible est un dossier mais que l’exclusion est spécifiée comme un fichier, l’exclusion s’applique.

#### <a name="filefolder-exclusions-default-behavior"></a>Comportement par défaut des exclusions de fichiers/dossiers

Si vous ne spécifiez aucune autre option, le fichier/dossier est exclu de tous les types d’analyses _, et_ l’exclusion s’applique, que la cible soit un fichier ou un dossier. Pour plus d’informations sur la personnalisation des exclusions pour qu’elle s’applique uniquement à un type d’analyse spécifique, consultez [restriction de type d’analyse](#scan-type-restriction).

#### <a name="folders"></a>Folders

Pour vous assurer qu’une exclusion s’applique uniquement si la cible est un dossier, et non un fichier, vous pouvez utiliser la restriction **PathType:folder** . Par exemple :

`C:\documents\:{PathType:folder}`

#### <a name="files"></a>Fichiers

Pour vous assurer qu’une exclusion s’applique uniquement si la cible est un fichier, et non un dossier, vous pouvez utiliser la restriction PathType: file.

Exemple :

`C:\documents\database.mdb\:{PathType:file}`

### <a name="scan-type-restriction"></a>Restriction de type d’analyse

Par défaut, les exclusions s’appliquent à tous les types d’analyse :  

- **ressource** : un seul fichier ou dossier est analysé de manière ciblée (par exemple, cliquer avec le bouton droit, analyser)
- **rapide** : emplacements de démarrage courants utilisés par les programmes malveillants, la mémoire et certaines clés de Registre
- **complet** : inclut des emplacements d’analyse rapide et un système de fichiers complet (tous les fichiers et dossiers)

Pour atténuer les problèmes de performances, vous pouvez exclure un dossier ou un ensemble de fichiers d’être analysés par un type d’analyse spécifique. Vous pouvez également définir le type d’analyse requis pour une exclusion à appliquer.  

Pour empêcher l’analyse d’un dossier uniquement pendant une analyse complète, spécifiez un type de restriction avec l’exclusion de fichier ou de dossier, comme dans l’exemple suivant :

`C:\documents\:{ScanType:full}`

Pour empêcher l’analyse d’un dossier uniquement lors d’une analyse rapide, spécifiez un type de restriction avec l’exclusion de fichier ou de dossier :

`C:\program.exe\:{ScanType:quick}`

Si vous souhaitez vous assurer que cette exclusion s’applique uniquement à un fichier spécifique et non à un dossier (c:\foo.exe peut être un dossier), appliquez également la restriction PathType :

`C:\program.exe\:{ScanType:quick,PathType:file}`

### <a name="scan-trigger-restriction"></a>Restriction du déclencheur d’analyse

Par défaut, les exclusions de base s’appliquent à tous les déclencheurs d’analyse. La restriction ScanTrigger vous permet de spécifier que l’exclusion ne doit s’appliquer que lorsque l’analyse a été lancée par un événement spécifique ; à la demande (y compris les analyses rapides, complètes et ciblées), sur l’accès ou provenant de la surveillance comportementale (y compris les analyses de mémoire).

- **OnDemand** : une analyse a été déclenchée par une commande ou une action d’administration. N’oubliez pas que les analyses rapides et complètes planifiées appartiennent également à cette catégorie.
- **OnAccess** : un fichier ou un dossier est ouvert/écrit/lu/modifié (généralement considéré comme une protection en temps réel)
- **BM** : un déclencheur comportemental entraîne l’analyse comportementale d’un fichier spécifique

Pour empêcher l’analyse d’un fichier ou d’un dossier et de son contenu uniquement lorsque le fichier est analysé après avoir été consulté, définissez une restriction de déclencheur d’analyse telle que l’exemple suivant :

`c:\documents\:{ScanTrigger:OnAccess}`

### <a name="process-restriction"></a>Restriction de processus

Cette restriction vous permet de définir qu’une exclusion ne doit s’appliquer que lorsqu’un fichier ou un dossier est accessible par un processus spécifique. Un scénario courant consiste à éviter d’exclure le processus, car cette prévention entraînerait l’exclusion d’autres opérations de l’Antivirus Defender par ce processus.

> [!NOTE]  
>
> L’utilisation d’une grande quantité de restrictions d’exclusion de processus sur un ordinateur peut nuire aux performances.  
> En outre, étant donné que vous avez restreint l’exclusion à un certain processus ou processus, d’autres processus actifs (tels que l’indexation, la sauvegarde, les mises à jour) peuvent toujours déclencher des analyses de fichiers.

Pour exclure un fichier ou un dossier uniquement lorsqu’un processus spécifique y accède, créez une exclusion de fichier ou de dossier normale et ajoutez le processus pour limiter l’exclusion aux éléments suivants :  

`c:\documents\design.doc\:{Process:"winword.exe", Process:"msaccess.exe"}`

### <a name="how-to-configure"></a>Procédure de configuration

Après avoir construit les exclusions contextuelles souhaitées, vous pouvez utiliser votre outil de gestion existant pour configurer les exclusions de fichiers et de dossiers à l’aide de la chaîne que vous avez créée.

Voir : [Configurer et valider les exclusions pour les analyses antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
