---
title: Effectuer des actions de réponse sur un appareil dans Microsoft Defender pour point de terminaison
description: Effectuez des actions de réponse sur un appareil, telles que l’isolation des appareils, la collecte d’un package d’investigation, la gestion des balises, l’exécution d’une analyse av et la restriction de l’exécution de l’application.
keywords: répondre, isoler, isoler l’appareil, collecter le package d’investigation, centre d’actions, restreindre, gérer les balises, analyser av, restreindre l’application
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 2f5ef49d9b8fd1d558fb0b646295615d9352b915
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67728645"
---
# <a name="take-response-actions-on-a-device"></a>Prendre des mesures de réponse sur un appareil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Plans 1 et 2 de Microsoft Defender pour points de terminaison](defender-endpoint-plan-1-2.md)
- [Microsoft Defender pour les PME](/microsoft-365/security/defender-business/mdb-overview)

[!INCLUDE [Prerelease information](../../includes/prerelease.md)]

Répondez rapidement aux attaques détectées en isolant les appareils ou en collectant un package d’investigation. Après avoir pris des mesures sur les appareils, vous pouvez vérifier les détails de l’activité sur le Centre d’actions.

Les actions de réponse s’exécutent en haut d’une page d’appareil spécifique et incluent :

- Gérer des balises
- Lancer une enquête automatisée
- Lancer une session de réponse en direct
- Collecter un package d’examen
- Exécuter une analyse antivirus
- Restreindre l’exécution des applications
- Isoler l’appareil
- Contenir un appareil
- Consulter un spécialiste des menaces
- Centre de notifications

[![Image des actions de réponse.](images/response-actions.png)](images/response-actions.png#lightbox)

> [!IMPORTANT]
> [Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md) et [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md) inclure uniquement les actions de réponse manuelle suivantes :
> - Exécuter une analyse antivirus
> - Isoler l’appareil
> - Arrêter et mettre en quarantaine un fichier
> - Ajouter un indicateur pour bloquer ou autoriser un fichier Votre abonnement doit inclure Defender pour point de terminaison Plan 2 pour que toutes les actions de réponse soient décrites dans cet article.

 Vous pouvez trouver des pages d’appareil à partir de l’une des vues suivantes :

- **Tableau de bord des opérations de sécurité** : sélectionnez un nom d’appareil dans la carte Appareils à risque.
- **File d’attente des alertes** : sélectionnez le nom de l’appareil en regard de l’icône de l’appareil dans la file d’attente des alertes.
- **Liste des appareils** : sélectionnez l’en-tête du nom de l’appareil dans la liste des appareils.
- **Zone de recherche** : sélectionnez Appareil dans le menu déroulant et entrez le nom de l’appareil.

> [!IMPORTANT]
> - Ces actions de réponse sont disponibles uniquement pour les appareils sur Windows 10, version 1703 ou ultérieure, Windows 11, Windows Server 2019 et Windows Server 2022.
> - Pour les plateformes non Windows, les fonctionnalités de réponse (telles que l’isolation des appareils) dépendent des fonctionnalités tierces.
> - Pour les agents internes Microsoft, reportez-vous au lien « Plus d’informations » sous chaque fonctionnalité pour connaître la configuration minimale requise du système d’exploitation.

## <a name="manage-tags"></a>Gérer des balises

Ajoutez ou gérez des balises pour créer une affiliation de groupe logique. Les balises d’appareil prennent en charge le mappage approprié du réseau, ce qui vous permet d’attacher différentes balises pour capturer le contexte et d’activer la création de liste dynamique dans le cadre d’un incident.

Pour plus d’informations sur l’étiquetage des appareils, consultez [Créer et gérer des balises d’appareil](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Lancer une enquête automatisée

Vous pouvez démarrer une nouvelle enquête automatisée à usage général sur l’appareil si nécessaire. Pendant l’exécution d’une enquête, toute autre alerte générée à partir de l’appareil est ajoutée à une enquête automatisée en cours jusqu’à ce que cette enquête soit terminée. En outre, si la même menace est visible sur d’autres appareils, ces appareils sont ajoutés à l’enquête.

Pour plus d’informations sur les enquêtes automatisées, consultez [Vue d’ensemble des enquêtes automatisées](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Lancer la session de réponse en direct

La réponse en direct est une fonctionnalité qui vous donne un accès instantané à un appareil à l’aide d’une connexion d’interpréteur de commandes distante. Cela vous donne le pouvoir d’effectuer des travaux d’investigation approfondis et de prendre des mesures de réponse immédiates pour contenir rapidement les menaces identifiées en temps réel.

La réponse dynamique est conçue pour améliorer les investigations en vous permettant de collecter des données légales, d’exécuter des scripts, d’envoyer des entités suspectes à des fins d’analyse, de corriger les menaces et de rechercher de manière proactive les menaces émergentes.

Pour plus d’informations sur la réponse en direct, consultez [Examiner les entités sur les appareils à l’aide de la réponse dynamique](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Collecter le package d’investigation à partir d’appareils

Dans le cadre du processus d’investigation ou de réponse, vous pouvez collecter un package d’investigation à partir d’un appareil. En collectant le package d’investigation, vous pouvez identifier l’état actuel de l’appareil et mieux comprendre les outils et techniques utilisés par l’attaquant.

> [!IMPORTANT]
> Ces actions ne sont actuellement pas prises en charge pour les appareils exécutant macOS ou Linux. Utilisez la réponse en direct pour exécuter l’action. Pour plus d’informations sur la réponse en direct, consultez [Examiner les entités sur les appareils à l’aide de la réponse dynamique](live-response.md)

Pour télécharger le package (fichier zip) et examiner les événements qui se sont produits sur un appareil

1. Sélectionnez **Collecter le package d’investigation** dans la ligne des actions de réponse en haut de la page de l’appareil.

2. Spécifiez dans la zone de texte pourquoi vous souhaitez effectuer cette action. Sélectionner **Confirmer**.

3. Le fichier zip sera téléchargé

Autre méthode :

1. Sélectionnez **Centre d’actions** dans la section Actions de réponse de la page de l’appareil.

   :::image type="content" source="images/action-center-package-collection.png" alt-text="Option Centre d’actions" lightbox="images/action-center-package-collection.png":::

2. Dans le menu volant du Centre d’actions, sélectionnez **package de collection de packages disponible** pour télécharger le fichier zip.

   :::image type="content" source="images/collect-package.png" alt-text="Option de package de téléchargement" lightbox="images/collect-package.png":::

Le package contient les dossiers suivants :

|Folder|Description|
|---|---|
|Autoruns|Contient un ensemble de fichiers qui représentent chacun le contenu du registre d’un point d’entrée de démarrage automatique connu (ASEP) pour aider à identifier la persistance de l’attaquant sur l’appareil. <p> <div class="alert"><b>NOTE:</b> Si la clé de Registre est introuvable, le fichier contient le message suivant : « ERREUR : Le système n’a pas trouvé la clé ou la valeur de Registre spécifiée ».<div>|
|Programmes installés|Ce fichier .CSV contient la liste des programmes installés qui peuvent vous aider à identifier ce qui est actuellement installé sur l’appareil. Pour plus d’informations, consultez [Win32_Product classe](https://go.microsoft.com/fwlink/?linkid=841509).|
|Connexions réseau|Ce dossier contient un ensemble de points de données liés aux informations de connectivité qui peuvent aider à identifier la connectivité aux URL suspectes, l’infrastructure de commande et de contrôle (C&C) de l’attaquant, tout déplacement latéral ou les connexions à distance. <ul><li>ActiveNetConnections.txt : affiche les statistiques de protocole et les connexions réseau TCP/IP actuelles. Permet de rechercher une connectivité suspecte établie par un processus.</li><li>Arp.txt : affiche les tables de cache ARP (Address Resolution Protocol) actuelles pour toutes les interfaces. Le cache ARP peut révéler d’autres hôtes sur un réseau qui a été compromis ou des systèmes suspects sur le réseau qui ont pu être utilisés pour exécuter une attaque interne.</il><li>DnsCache.txt : affiche le contenu du cache du programme de résolution du client DNS, qui inclut les deux entrées préchargées à partir du fichier Hosts local et tous les enregistrements de ressources récemment obtenus pour les requêtes de nom résolues par l’ordinateur. Cela peut aider à identifier les connexions suspectes.</li><li>IpConfig.txt : affiche la configuration TCP/IP complète pour toutes les cartes. Les cartes peuvent représenter des interfaces physiques, telles que des cartes réseau installées, ou des interfaces logiques, telles que des connexions rendez-vous.</li><li>FirewallExecutionLog.txt et pfirewall.log</li></ul><p><div class="alert"><b>NOTE:</b> Le fichier pfirewall.log doit exister dans %windir%\system32\logfiles\firewall\pfirewall.log, afin qu’il soit inclus dans le package d’investigation. Pour plus d’informations sur la création du fichier journal du [pare-feu, consultez Configurer le pare-feu Windows Defender avec le journal de sécurité avancée](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Fichiers de prérécupération|Les fichiers Prérécupération Windows sont conçus pour accélérer le processus de démarrage de l’application. Il peut être utilisé pour suivre tous les fichiers récemment utilisés dans le système et rechercher des traces pour les applications qui ont peut-être été supprimées, mais qui se trouvent toujours dans la liste des fichiers de prérécupération. <ul><li>Dossier de prérécupération : contient une copie des fichiers de prérécupération à partir de `%SystemRoot%\Prefetch`. REMARQUE : Il est suggéré de télécharger une visionneuse de fichiers de prérécupération pour afficher les fichiers de prérécupération.</li><li>PrefetchFilesList.txt : contient la liste de tous les fichiers copiés qui peuvent être utilisés pour effectuer le suivi en cas d’échec de copie dans le dossier de prérécupération.</li></ul>|
|Processus|Contient un fichier .CSV répertoriant les processus en cours d’exécution et permet d’identifier les processus en cours d’exécution sur l’appareil. Cela peut être utile lors de l’identification d’un processus suspect et de son état.|
|Tâches planifiées|Contient un fichier .CSV répertoriant les tâches planifiées, qui peut être utilisé pour identifier les routines exécutées automatiquement sur un appareil choisi afin de rechercher le code suspect qui a été configuré pour s’exécuter automatiquement.|
|Journal des événements de sécurité|Contient le journal des événements de sécurité, qui contient des enregistrements d’activité de connexion ou de déconnexion, ou d’autres événements liés à la sécurité spécifiés par la stratégie d’audit du système. <p><div class="alert"><b>NOTE:</b> Ouvrez le fichier journal des événements à l’aide de l’Observateur d’événements.</div>|
|Services|Contient un fichier .CSV qui répertorie les services et leurs états.|
|Sessions SMB (Windows Server Message Block)|Répertorie l’accès partagé aux fichiers, imprimantes et ports série et communications diverses entre les nœuds d’un réseau. Cela peut aider à identifier l’exfiltration de données ou le mouvement latéral. <p> Contient des fichiers pour SMBInboundSessions et SMBOutboundSession. <p> <div class="alert"><b>NOTE:</b> S’il n’existe aucune session (entrante ou sortante), vous obtenez un fichier texte qui vous indique qu’aucune session SMB n’a été trouvée.</div>|
|Informations système|Contient un fichier SystemInformation.txt qui répertorie les informations système telles que la version du système d’exploitation et les cartes réseau.|
|Répertoires temporaires|Contient un ensemble de fichiers texte qui répertorie les fichiers situés dans %Temp% pour chaque utilisateur du système. <p> Cela peut aider à suivre les fichiers suspects qu’un attaquant peut avoir déposés sur le système. <p> <div class="alert"><b>NOTE:</b> Si le fichier contient le message suivant : « Le système ne trouve pas le chemin spécifié », cela signifie qu’il n’y a pas de répertoire temporaire pour cet utilisateur, et peut-être parce que l’utilisateur ne s’est pas connecté au système.</div>|
|Utilisateurs et groupes|Fournit une liste de fichiers qui représentent chacun un groupe et ses membres.|
|WdSupportLogs|Fournit les MpCmdRunLog.txt et les MPSupportFiles.cab  <p> <div class="alert"><b>NOTE:</b> Ce dossier ne sera créé que le Windows 10, version 1709 ou ultérieure, avec le correctif cumulatif de février 2020 ou une version plus récente installée : <ul><li>Win10 1709 (RS3) Build 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Build 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Win10 1809 (RS5) Build 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Builds 18362.693 et 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Ce fichier est un résumé de la collection de packages d’investigation, il contient la liste des points de données, la commande utilisée pour extraire les données, l’état d’exécution et le code d’erreur en cas d’échec. Vous pouvez utiliser ce rapport pour suivre si le package inclut toutes les données attendues et identifier s’il y a eu des erreurs.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Exécuter l’analyse antivirus Microsoft Defender sur les appareils

Dans le cadre du processus d’investigation ou de réponse, vous pouvez lancer à distance une analyse antivirus pour identifier et corriger les programmes malveillants susceptibles d’être présents sur un appareil compromis.

> [!IMPORTANT]
> - Cette action n’est actuellement pas prise en charge pour macOS et Linux. Utilisez la réponse en direct pour exécuter l’action. Pour plus d’informations sur la réponse en direct, consultez [Examiner les entités sur les appareils à l’aide de la réponse dynamique](live-response.md)
> - Une analyse antivirus Microsoft Defender peut s’exécuter en même temps que d’autres solutions antivirus, que l’antivirus Microsoft Defender soit ou non la solution antivirus active. L’Antivirus Microsoft Defender peut être en mode passif. Pour plus d’informations, consultez [Compatibilité de l’antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

Vous avez sélectionné **Exécuter l’analyse antivirus**, sélectionnez le type d’analyse que vous souhaitez exécuter (rapide ou complet) et ajoutez un commentaire avant de confirmer l’analyse.

:::image type="content" source="images/run-antivirus.png" alt-text="Notification pour sélectionner l’analyse rapide ou l’analyse complète et ajouter un commentaire" lightbox="images/run-antivirus.png":::

Le Centre d’action affiche les informations d’analyse et la chronologie de l’appareil inclut un nouvel événement, ce qui indique qu’une action d’analyse a été envoyée sur l’appareil. Les alertes de l’Antivirus Microsoft Defender reflètent toutes les détections qui ont été signalées pendant l’analyse.

> [!NOTE]
> Lors du déclenchement d’une analyse à l’aide de l’action de réponse Defender pour point de terminaison, la valeur « ScanAvgCPULoadFactor » de l’antivirus Microsoft Defender s’applique toujours et limite l’impact de l’analyse sur le processeur.
> Si ScanAvgCPULoadFactor n’est pas configuré, la valeur par défaut est une limite de 50 % de charge maximale de l’UC pendant une analyse.
> Pour plus d’informations, consultez [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Restreindre l’exécution des applications

En plus de contenir une attaque en arrêtant des processus malveillants, vous pouvez également verrouiller un appareil et empêcher les tentatives ultérieures de programmes potentiellement malveillants de s’exécuter.

> [!IMPORTANT]
> - Cette action est disponible pour les appareils sur Windows 10, version 1709 ou ultérieure, Windows 11 et Windows Server 2019 ou version ultérieure. 
> - Cette fonctionnalité est disponible si votre organisation utilise l’antivirus Microsoft Defender.
> - Cette action doit répondre aux Windows Defender formats de stratégie d’intégrité du code Application Control et aux exigences de signature. Pour plus d’informations, consultez [les formats de stratégie d’intégrité du code et la signature](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)).

Pour empêcher l’exécution d’une application, une stratégie d’intégrité du code est appliquée qui autorise uniquement l’exécution des fichiers s’ils sont signés par un certificat émis par Microsoft. Cette méthode de restriction peut aider à empêcher un attaquant de contrôler les appareils compromis et d’effectuer d’autres activités malveillantes.

> [!NOTE]
> Vous serez en mesure d’inverser la restriction de l’exécution des applications à tout moment. Le bouton de la page de l’appareil change pour indiquer **Supprimer les restrictions d’application**, puis vous effectuez les mêmes étapes que la restriction de l’exécution de l’application.

Une fois que vous avez sélectionné **Restreindre l’exécution de l’application** sur la page de l’appareil, tapez un commentaire, puis sélectionnez **Confirmer**. Le Centre d’action affiche les informations d’analyse et la chronologie de l’appareil inclut un nouvel événement.

:::image type="content" source="images/restrict-app-execution.png" alt-text="Notification de restriction d’application" lightbox="images/restrict-app-execution.png":::

### <a name="notification-on-device-user"></a>Notification sur l’utilisateur de l’appareil

Lorsqu’une application est restreinte, la notification suivante s’affiche pour informer l’utilisateur qu’une application n’est pas en cours d’exécution :

:::image type="content" source="images/atp-app-restriction.png" alt-text="Message de restriction d’application" lightbox="images/atp-app-restriction.png":::

> [!NOTE]
> La notification n’est pas disponible sur Windows Server 2016 et Windows Server 2012 R2.

## <a name="isolate-devices-from-the-network"></a>Isoler les appareils du réseau

Selon la gravité de l’attaque et la sensibilité de l’appareil, vous pouvez isoler l’appareil du réseau. Cette action peut aider à empêcher l’attaquant de contrôler l’appareil compromis et d’effectuer d’autres activités telles que l’exfiltration de données et le mouvement latéral.

> [!IMPORTANT]
> - L’isolation des appareils du réseau n’est actuellement pas prise en charge pour les appareils exécutant macOS ou Linux. Pour macOS, utilisez la réponse en direct pour exécuter l’action. Pour plus d’informations sur la réponse en direct, consultez [Examiner les entités sur les appareils à l’aide de la réponse dynamique](live-response.md).
> - L’isolation complète est disponible pour les appareils exécutant Windows 11, Windows 10, version 1703 ou ultérieure, Windows Server 2022, Windows Server 2019 et Windows Server 2016.
> - L’isolation sélective est disponible pour les appareils exécutant Windows 10, version 1709 ou ultérieure et Windows 11.
> - Lors de l’isolation d’un appareil, seuls certains processus et destinations sont autorisés. Par conséquent, les appareils qui se trouvent derrière un tunnel VPN complet ne pourront pas atteindre le service cloud Microsoft Defender pour point de terminaison une fois l’appareil isolé. Nous vous recommandons d’utiliser un VPN de tunneling fractionné pour Microsoft Defender pour point de terminaison et le trafic lié à la protection cloud de l’Antivirus Microsoft Defender.

Cette fonctionnalité d’isolation de l’appareil déconnecte l’appareil compromis du réseau tout en conservant la connectivité au service Defender pour point de terminaison, qui continue de surveiller l’appareil.

Sur Windows 10, version 1709 ou ultérieure, vous aurez plus de contrôle sur le niveau d’isolation réseau. Vous pouvez également choisir d’activer la connectivité Outlook, Microsoft Teams et Skype Entreprise (c’est-à-dire « isolation sélective »).

> [!NOTE]
> Vous pourrez reconnecter l’appareil au réseau à tout moment. Le bouton de la page de l’appareil change pour indiquer **Libérer de l’isolation**, puis vous effectuez les mêmes étapes que l’isolation de l’appareil.

Une fois que vous avez sélectionné **Isoler l’appareil** sur la page de l’appareil, tapez un commentaire, puis sélectionnez **Confirmer**. Le Centre d’action affiche les informations d’analyse et la chronologie de l’appareil inclut un nouvel événement.

:::image type="content" source="images/isolate-device.png" alt-text="Page détails d’un appareil isolé" lightbox="images/isolate-device.png":::

> [!NOTE]
> L’appareil reste connecté au service Defender pour point de terminaison même s’il est isolé du réseau. Si vous avez choisi d’activer Outlook et Skype Entreprise communication, vous pourrez communiquer avec l’utilisateur pendant que l’appareil est isolé.

### <a name="notification-on-device-user"></a>Notification sur l’utilisateur de l’appareil

Lorsqu’un appareil est isolé, la notification suivante s’affiche pour informer l’utilisateur que l’appareil est isolé du réseau :

:::image type="content" source="images/atp-notification-isolate.png" alt-text="Message d’absence de connexion réseau" lightbox="images/atp-notification-isolate.png":::

## <a name="contain-devices-from-the-network"></a>Contenir des appareils à partir du réseau
 
> [!NOTE]
> Les fonctionnalités de contenu sont actuellement en préversion publique. Pour en savoir plus sur les nouvelles fonctionnalités de la préversion Microsoft 365 Defender et être parmi les premiers à essayer les fonctionnalités à venir en activant l’expérience de préversion, consultez [les fonctionnalités en préversion dans Micrsoft 365 Defender](../defender/preview.md).

Lorsque vous avez identifié un appareil non managé compromis ou potentiellement compromis, vous souhaiterez peut-être le contenir à partir du réseau. Lorsque vous avez un appareil, un Microsoft Defender pour point de terminaison appareil intégré bloque la communication entrante et sortante avec cet appareil. Cette action peut aider à empêcher les appareils voisins de se compromettre pendant que l’analyste des opérations de sécurité localise, identifie et corrige la menace sur l’appareil compromis.

> [!NOTE]
> Le blocage des communications entrantes et sortantes avec un appareil « autonome » est pris en charge sur les appareils intégrés Microsoft Defender pour point de terminaison Windows 10 et Windows Server 2019+.

### <a name="how-to-contain-a-device"></a>Comment contenir un appareil
 
1. Accédez à la page **Inventaire des appareils** et sélectionnez l’appareil à contenir.

2. Sélectionnez **Contenir l’appareil** dans le menu actions du menu volant de l’appareil.

:::image type="content" alt-text="Capture d’écran du message contextuel contenant l’appareil." source="../../media/defender-endpoint/contain_device.png" lightbox="../../media/defender-endpoint/contain_device.png":::

3. Dans la fenêtre contextuelle contenir l’appareil, tapez un commentaire, puis sélectionnez **Confirmer**.

:::image type="content" alt-text="Capture d’écran de l’élément de menu contenir l’appareil." source="../../media/defender-endpoint/contain_device_popup.png" lightbox="../../media/defender-endpoint/contain_device_popup.png":::

### <a name="contain-a-device-from-the-device-page"></a>Contenir un appareil à partir de la page de l’appareil

Un appareil peut également être contenu à partir de la page de l’appareil en sélectionnant **Contenir l’appareil** dans la barre d’action :

:::image type="content" alt-text="Capture d’écran de l’élément de menu contenir l’appareil sur la page de l’appareil." source="../../media/defender-endpoint/contain_device_page.png" lightbox="../../media/defender-endpoint/contain_device_page.png":::

> [!NOTE]
> Les détails sur un appareil nouvellement contenu peuvent prendre jusqu’à 5 minutes pour atteindre Microsoft Defender pour point de terminaison appareils intégrés.

> [!IMPORTANT]
> - Si un appareil autonome modifie son adresse IP, tous les appareils intégrés Microsoft Defender pour point de terminaison le reconnaissent et commencent à bloquer les communications avec la nouvelle adresse IP. L’adresse IP d’origine ne sera plus bloquée (il peut prendre jusqu’à 5 minutes pour voir ces modifications).  
> - Dans les cas où l’adresse IP de l’appareil contenu est utilisée par un autre appareil sur le réseau, un avertissement s’affiche lors du conteneur de l’appareil, avec un lien vers la chasse avancée (avec une requête préremplie). Cela offre une visibilité aux autres appareils utilisant la même adresse IP pour vous aider à prendre une décision consciente si vous souhaitez continuer à contenir l’appareil.
> - Dans les cas où l’appareil contenu est un appareil réseau, un avertissement s’affiche avec un message indiquant que cela peut entraîner des problèmes de connectivité réseau (par exemple, contenant un routeur qui agit comme une passerelle par défaut). À ce stade, vous pouvez choisir de contenir ou non l’appareil.

Une fois que vous avez contenu un appareil, si le comportement n’est pas comme prévu, vérifiez que le service du moteur de filtrage de base (BFE) est activé sur les appareils intégrés Defender pour point de terminaison.

### <a name="stop-containing-a-device"></a>Arrêter de contenir un appareil

Vous pourrez arrêter de contenir un appareil à tout moment.

1. Sélectionnez l’appareil dans **l’inventaire** des appareils ou ouvrez la page de l’appareil.

2. Sélectionnez **Libérer à partir de l’endiguement** dans le menu d’action. Cette action restaure la connexion de cet appareil au réseau.

## <a name="consult-a-threat-expert"></a>Consulter un spécialiste des menaces

Vous pouvez consulter un expert microsoft en matière de menaces pour obtenir plus d’informations sur un appareil potentiellement compromis ou déjà compromis. Spécialistes des menaces Microsoft peut être engagée directement à partir de l’Microsoft 365 Defender pour obtenir une réponse rapide et précise. Les experts fournissent des insights non seulement sur un appareil potentiellement compromis, mais également pour mieux comprendre les menaces complexes, les notifications d’attaque ciblées que vous recevez, ou si vous avez besoin de plus d’informations sur les alertes, ou un contexte de renseignement sur les menaces que vous voyez sur le tableau de bord de votre portail.

Pour plus [d’informations, consultez un expert Microsoft sur les menaces](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) .

## <a name="check-activity-details-in-action-center"></a>Vérifier les détails de l’activité dans le Centre de notifications

Le **Centre d’actions** fournit des informations sur les actions qui ont été effectuées sur un appareil ou un fichier. Vous serez en mesure d’afficher les détails suivants :

- Collection de packages d’investigation
- Analyse antivirus
- Restriction d’application
- Isolation de l’appareil

Tous les autres détails connexes sont également affichés, par exemple, la date/l’heure de soumission, l’envoi de l’utilisateur et si l’action a réussi ou échoué.

:::image type="content" source="images/action-center-details.png" alt-text="Centre d’action avec des informations" lightbox="images/action-center-details.png":::


## <a name="see-also"></a>Voir aussi

- [Prendre des mesures de réponse sur un fichier](respond-file-alerts.md)
- [Actions de réponse manuelles dans Microsoft Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
- [Erreur de rapport](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
