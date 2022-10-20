---
title: Configurer les paramètres DLP du point de terminaison
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- tier1
- purview-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment configurer les paramètres centraux de protection contre la perte de données (DLP) des points de terminaison.
ms.openlocfilehash: d3b38a9125979f33e4d22277b8967f4f3d37c349
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621359"
---
# <a name="configure-endpoint-data-loss-prevention-settings"></a>Configurer les paramètres de protection contre la perte de données de point de terminaison

De nombreux aspects du comportement de protection contre la perte de données (DLP) des points de terminaison sont contrôlés par des paramètres configurés de manière centralisée. Les paramètres sont appliqués à toutes les stratégies DLP pour les appareils.

![Paramètres DLP du point de terminaison](../media/endpoint-dlp-1-using-dlp-settings.png)

Vous devez configurer ces paramètres si vous envisagez de contrôler :

- les restrictions de sortie cloud
- les différents types d’actions restrictives sur les activités des utilisateurs par application.
- les exclusions de chemins d’accès pour les appareils Windows et macOS.
- les restrictions de navigateur et de domaine.
- la manière dont es justifications de l’entreprise pour le remplacement de stratégies apparaissent dans les conseils de stratégie.
- si les activités sur Office, PDF et CSV sont automatiquement auditées.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="dlp-settings"></a>Paramètres DLP

Avant de commencer, vous devez configurer vos paramètres DLP. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Paramètres de point de terminaison DLP Windows 10/11 et macOS

|Setting |Windows 10, 1809 et ultérieures, Windows 11  |macOS (trois dernières versions publiées) |Notes  |
|---------|---------|---------|---------|
|Exclusions de chemin d’accès de fichier     |Pris en charge         |Pris en charge         |macOS inclut une liste recommandée d'exclusions activée par défaut          |
|Applications restreintes     |Pris en charge         |Pris en charge         |         |
|Groupes d’applications restreintes |Pris en charge |Non pris en charge
|Applications Bluetooth non autorisées    |Pris en charge         |Non pris en charge         |         |
|Restrictions de navigateur et de domaine aux éléments sensibles      |Pris en charge         |Pris en charge         |         |
|Paramètres supplémentaires pour Endpoint DLP     |Pris en charge         |Pris en charge         |Seules les justifications commerciales par défaut sont prises en charge pour les appareils macOS         |
|Toujours auditer l’activité des fichiers pour les appareils     |Pris en charge         |Pris en charge         |         |
|Mise en quarantaine automatique des fichiers provenant d'applications non autorisées | Pris en charge | Non pris en charge| |
|Classification avancée | Pris en charge | Non pris en charge| |
|Justification métier dans les conseils de stratégie | Pris en charge | Pris en charge| |

### <a name="advanced-classification-scanning-and-protection"></a>Analyse et protection avancées de la classification

L’analyse et la protection de classification avancées permettent au service de classification de données basé sur le cloud Microsoft Purview, plus avancé, d’analyser les éléments, de les classer et de renvoyer les résultats à la machine locale. Cela signifie que vous pouvez tirer parti des techniques de classification telles que la classification de [correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) et des [entités nommées](named-entities-learn.md) dans vos stratégies DLP.

Lorsque la classification avancée est activée, le contenu est envoyé de l’appareil local aux services cloud à des fins d’analyse et de classification. Si l’utilisation de la bande passante est un problème, vous pouvez définir une limite sur la quantité pouvant être utilisée sur une plage de 24 heures. La limite est configurée dans les paramètres DLP du point de terminaison et est appliquée par appareil. Si vous définissez une limite d’utilisation de la bande passante et qu’elle est dépassée, DLP cesse d’envoyer le contenu utilisateur au cloud. À ce stade, la classification des données se poursuit localement sur l’appareil, mais la classification utilisant la correspondance exacte des données, les entités nommées et les classificateurs pouvant être entraînés n’est pas disponible. Lorsque l'utilisation cumulée de la bande passante tombe en dessous de la limite de 24 heures glissantes, la communication avec les services cloud reprendra.

Si l’utilisation de la bande passante n’est pas un problème, vous sélectionnez **Aucune limite** pour autoriser une utilisation illimitée de la bande passante.

Ces versions Windows la prise en charge de l’analyse et de la protection avancées de la classification :

- Windows 10 versions 20H1/20H2/21H1 (KB 5006738)
- Windows 10 versions 19H1/19H2 (KB 5007189)
- Windows 10 RS5 (KB 5006744)

> [!NOTE]
> La prise en charge de la classification avancée est disponible pour les types de Office (Word, Excel, PowerPoint) et PDF.

> [!NOTE]
> L'évaluation de la stratégie DLP se produit toujours dans le cloud, même si le contenu utilisateur n'est pas envoyé.

### <a name="file-path-exclusions"></a>Exclusions de chemin d’accès de fichier

Ouvrez le [portail de conformité Microsoft Purview](https://compliance.microsoft.com) > **protection contre la perte de données** > **Paramètres DLP des** > **terminaux Exclusions de chemin de fichier**.

Vous pouvez exclure certains chemins d’accès de la surveillance DLP, des alertes DLP et de l’application de la stratégie DLP sur vos appareils, car ils sont trop bruyants ou ne contiennent pas de fichiers qui vous intéressent. Les fichiers de ces emplacements ne seront pas audités et les fichiers créés ou modifiés dans ces emplacements ne seront pas soumis à l’application de la stratégie DLP. Vous pouvez configurer les exclusions de chemin d’accès dans les paramètres DLP.

#### <a name="windows-10-devices"></a>Appareils Windows 10

Vous pouvez utiliser cette logique pour créer vos chemins d'exclusion pour les appareils Windows 10 :

- Chemin d’accès au fichier valide qui se termine par `\`, ce qui signifie uniquement les fichiers directement sous dossier. <br/>Par exemple : `C:\Temp\`

- Chemin d’accès de fichier valide qui se termine par `\*`, ce qui signifie uniquement les fichiers sous les sous-dossiers. Les fichiers directement sous le dossier ne sont pas exclus. <br/>Par exemple : `C:\Temp\*`

- Chemin d’accès au fichier valide qui se termine sans `\` ou `\*`, ce qui signifie tous les fichiers directement sous dossier et tous les sous-dossiers. <br/>Par exemple : `C:\Temp`

- Chemin d’accès avec caractère générique entre `\` de chaque côté. <br/>Par exemple : `C:\Users\*\Desktop\`

- Chemin d’accès avec caractère générique entre `\` de chaque côté et avec `(number)` pour donner le nombre exact de sous-dossiers. <br/>Par exemple : `C:\Users\*(1)\Downloads\`

- Un chemin d’accès avec des variables d’environnement système. <br/>Par exemple : `%SystemDrive%\Test\*`

- Un mélange de tous les éléments ci-dessus. <br/>Par exemple : `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices"></a>appareils macOS

Semblable aux appareils Windows 10, vous pouvez ajouter vos propres exclusions pour les appareils macOS.

- Les définitions de chemin de fichier sont insensibles à la casse, c'est `User` donc la même chose que `user`.

- Wildcard values are supported. So a path definition can contain a `*` in the middle of the path or at the end of the path. For example: `/Users/*/Library/Application Support/Microsoft/Teams/*`

##### <a name="recommended-file-path-exclusions-preview"></a>Exclusions de chemin de fichier recommandées (préversion)

Pour des raisons de performances, Endpoint DLP inclut une liste d'exclusions de chemins de fichiers recommandées pour les appareils macOS. Ces exclusions sont activées par défaut. Vous pouvez les désactiver si vous le souhaitez en activant la bascule **Inclure les exclusions de chemin de fichier recommandées pour Mac**. La liste inclut :

- /Applications/*
- /System/*
- /usr/*
- /Library/*
- /private/*
- /opt/*
- /Users/*/Library/Application Support/Microsoft/Teams/*

### <a name="restricted-apps-and-app-groups"></a>Applications restreintes et groupes d’applications

#### <a name="restricted-apps"></a>Applications restreintes

**Applications restreintes** (précédemment appelée **Applications non autorisées**) est une liste d’applications que vous créez. Vous configurez les actions que DLP effectuera lorsqu’un utilisateur utilise une application sur la liste pour **_accéder_** un fichier protégé par DLP sur un appareil. Il est disponible pour les appareils Windows 10 et macOS.

Lorsque **Accès par des applications restreintes** est sélectionné dans une stratégie et qu’un utilisateur utilise une application figurant dans la liste des applications restreintes pour accéder à un fichier protégé, l’activité est `audited`, `blocked`ou `blocked with override` en fonction de la façon dont vous l’avez configurée. À moins que la même application ne soit membre d’un **Groupe d’applications restreintes**, les actions configurées pour les activités du **Groupe d’applications restreintes** remplacer les actions configurées pour l’activité d’accès pour la liste **Applications restreintes**. Toutes les activités sont auditées et disponibles pour révision dans l’Explorateur d’activités.

> [!IMPORTANT]
> N’incluez pas le chemin d’accès du fichier exécutable, mais uniquement le nom du fichier exécutable (par exemple, browser.exe).

> [!IMPORTANT]
> L’action (`audit`, `block with override`ou `block`) définie pour les applications figurant dans la liste des applications restreintes s’applique uniquement lorsqu’un utilisateur tente d'***accéder*** à un élément protégé. 

#### <a name="file-activities-for-apps-in-restricted-app-groups"></a>Activités de fichiers pour les applications dans les groupes d'applications restreints

Les groupes d’applications restreintes sont des collections d’applications que vous créez dans les paramètres DLP, puis que vous ajoutez à une règle dans une stratégie. Lorsque vous ajoutez un groupe d’applications restreint à une stratégie, vous pouvez effectuer les actions définies dans ce tableau.

|Option de groupe d’applications restreintes  |Ce qu’il vous permet de faire  |
|---------|---------|
|Ne restreignez pas l'activité des fichiers     |Indique à DLP d’autoriser les utilisateurs à accéder aux éléments protégés par DLP à l’aide d’applications du groupe d’applications et n’effectue aucune action lorsque l’utilisateur tente de **Copier dans le Presse-papiers**, **Copier sur un lecteur USB amovible**, **Copier sur un lecteur réseau**, ou d’**Imprimer** à partir de l’application.          |
|Appliquer une restriction à toutes les activités     |Indique DLP de `Audit only`, `Block with override` ou `Block` lorsqu’un utilisateur tente d’accéder à un élément protégé par DLP à l’aide d’une application qui se trouverait dans ce groupe d’applications         |
|Appliquer des restrictions à une activité spécifique     |Ce paramètre permet à un utilisateur d’accéder à un élément protégé par DLP à l’aide d’une application qui se trouve dans le groupe d’applications et vous permet de sélectionner une action par défaut (`Audit only`, `Block`ou `Block with override`) que la DLP doit effectuer lorsqu’un utilisateur tente de **Copier dans le Presse-papiers**, **Copier sur un lecteur USB amovible**, **Copier sur un lecteur réseau** ou d’**Imprimer**.          |

> [!IMPORTANT]
> Les paramètres d’un groupe d’applications restreintes remplacent toutes les restrictions définies dans la liste des applications restreintes lorsqu’ils se trouvent dans la même règle. Par conséquent, si une application figure dans la liste des applications restreintes et est membre d’un groupe d’applications restreintes, les paramètres du groupe d’applications restreintes sont appliqués.

#### <a name="how-dlp-applies-restrictions-to-activities"></a>Comment la DLP applique des restrictions aux activités

Les interactions entre **les activités de fichier pour les applications dans les groupes d’applications restreints**, **les activités de fichier pour toutes les applications** et la liste **des activités d’application restreintes** sont limitées à la même règle.

##### <a name="restricted-app-groups-overrides"></a>Remplacements de groupes d’applications restreintes

Les configurations définies dans **les activités de fichier pour les applications dans des groupes d’applications restreints** remplacent les configurations de la liste **des activités d’application restreintes** et **des activités de fichier pour toutes les applications** de la même règle.

##### <a name="restricted-app-activities-and-file-activities-for-all-apps"></a>Activités d’application restreintes et activités de fichier pour toutes les applications

Les configurations des **activités d’application restreintes** et les **activités de fichier pour toutes les applications** fonctionnent de concert si l’action définie pour **Activités d’application restreintes** est `Audit only`ou `Block with override` dans la même règle. Cela est dû au fait que les actions définies pour **Activités d’application restreintes** s’appliquent uniquement lorsqu’un utilisateur accède à un fichier à l’aide d’une application figurant dans la liste. Une fois que l’utilisateur a accès, les actions définies pour les activités dans **Activités de fichier pour toutes les applications** s’appliquent. 

Voici un exemple :

Si Notepad.exe est ajouté aux **applications restreintes** et **aux activités de fichiers pour toutes les applications** est configuré pour **appliquer des restrictions à une activité spécifique** et les deux sont configurés comme suit :

|Paramètre dans la stratégie  |Nom de l'application  |Activité utilisateur  |Action DLP à effectuer  |
|---------|---------|---------|---------|
|Activités d'application restreintes     |Bloc-notes        |Accéder à un élément protégé par DLP         |Auditer uniquement         |
|Activités de fichiers pour toutes les applications   |Toutes les applications        | Copier dans le Presse-papiers        |Auditer uniquement         |
|Activités de fichiers pour toutes les applications     |Toutes les applications         |Copier sur un périphérique USB amovible | Bloquer       |
|Activités de fichiers pour toutes les applications     |Toutes les applications         |Copier vers un partage réseau         |Auditer uniquement         |
|Activités de fichiers pour toutes les applications   |Toutes les applications         |Imprimer         |Bloquer         |
|Activités de fichiers pour toutes les applications     |Toutes les applications         |Copier ou déplacer à l'aide d'une application Bluetooth non autorisée         |Blocked         |
|Activités de fichiers pour toutes les applications     |Toutes les applications         |Services de bureau à distance         |Bloc avec remplacement         |

L’utilisateur A ouvre un fichier protégé par DLP à l’aide Bloc-notes. DLP autorise l’accès et audite l’activité. Toujours dans le Bloc-notes, l’utilisateur A tente ensuite de copier dans le Presse-papiers à partir de l’élément protégé, ce qui fonctionne et la DLP audite l’activité. L’utilisateur A tente ensuite d’imprimer l’élément protégé à partir Bloc-notes et l’activité est bloquée.

> [!NOTE]
> Lorsque l’action DLP à entreprendre dans **Activités d’application restreintes** est définie sur `block`, tous les accès sont bloqués et l’utilisateur ne peut effectuer aucune activité sur le fichier.
   
##### <a name="file-activities-for-all-apps-only"></a>Activités de fichier pour toutes les applications uniquement

Si une application ne figure pas dans **les activités de fichier pour les applications dans des groupes d’applications restreints** ou ne figure pas dans la liste **des activités d’application restreintes** ou se trouve dans la liste **des activités d’application restreintes** avec une action `Audit only`, ou « Bloquer avec remplacement », toutes **les restrictions définies dans les activités fichier pour toutes les applications** sont appliquées dans la même règle.  

#### <a name="macos-devices"></a>appareils macOS

Tout comme sur les appareils Windows, vous pouvez désormais empêcher les applications macOS d’accéder aux données sensibles en les définissant dans la liste **Activités d’application restreintes**. 

> [!NOTE]
> Notez que les applications multiplateformes doivent être saisies avec leurs chemins uniques respectifs au système d'exploitation sur lequel elles s'exécutent.

Pour trouver le chemin complet des applications Mac :

1. Sur l'appareil macOS, ouvrez **Activity Monitor**. Recherchez et double-cliquez sur le processus que vous souhaitez restreindre

2. Choisissez l'onglet **Ouvrir les fichiers et les ports**.
  
3. Pour les applications macOS, vous avez besoin du nom complet du chemin d’accès, notamment le nom de l’application.

#### <a name="protect-sensitive-data-from-cloud-synchronization-apps"></a>Protéger les données sensibles des applications de synchronisation cloud

Pour empêcher la synchronisation d’éléments sensibles avec le cloud par des applications de synchronisation cloud, comme *onedrive.exe*, ajoutez l’application de synchronisation cloud à la liste **Applications non autorisées** . Lorsqu'une application de synchronisation cloud non autorisée tente d'accéder à un élément protégé par une stratégie DLP bloquante, DLP peut générer des notifications répétées. Vous pouvez éviter ces notifications répétées en activant l’option de **Mise en quarantaine automatique** sous **Applications non autorisées**.  

##### <a name="auto-quarantine-preview"></a>Mise en quarantaine automatique (préversion)

> [!NOTE]
> La quarantaine automatique est prise en charge dans Windows 10 uniquement

Lorsqu’elle est activée, la mise en quarantaine automatique se déclenche lorsqu’une application non autorisée tente d’accéder à un élément sensible protégé par DLP. La mise en quarantaine automatique déplace l’élément sensible vers un dossier configuré par l’administrateur et peut laisser un fichier **.txt** espace réservé à la place de l’original. Vous pouvez configurer le texte dans le fichier d’espace réservé pour indiquer aux utilisateurs où l’élément a été déplacé et d’autres informations pertinentes.  

Vous pouvez utiliser la mise en quarantaine automatique pour empêcher une chaîne infinie de notifications DLP pour l’utilisateur et les administrateurs. Consultez le [Scénario 4 : Éviter les boucles de notifications DLP à partir d’applications de synchronisation cloud avec mise en quarantaine automatique (préversion)](endpoint-dlp-using.md#scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview).

### <a name="unallowed-bluetooth-apps"></a>Applications Bluetooth non autorisées

Empêchez les utilisateurs de transférer des fichiers protégés par vos stratégies via des applications Bluetooth spécifiques.

### <a name="browser-and-domain-restrictions-to-sensitive-data"></a>Restrictions de navigateurs et de domaines vers des données sensibles

Empêchez les fichiers sensibles, qui correspondent à vos stratégies, d’être partagés avec des domaines de service cloud sans restriction.

#### <a name="unallowed-browsers"></a>Navigateurs non autorisés

Pour les appareils Windows, vous ajoutez des navigateurs, identifiés par leurs noms exécutables, qui ne pourront pas accéder aux fichiers qui correspondent aux conditions d’une stratégie DLP appliquée où la restriction de chargement vers les services cloud est définie sur bloquer ou bloquer le remplacement. Lorsque ces navigateurs ne peuvent pas accéder à un fichier, les utilisateurs finaux voient une notification toast leur demandant d’ouvrir le fichier via Microsoft Edge.

Pour les appareils macOS, vous devez ajouter le chemin d’accès complet au fichier. Pour trouver le chemin complet des applications Mac :

1. Sur l'appareil macOS, ouvrez **Activity Monitor**. Recherchez et double-cliquez sur le processus que vous souhaitez restreindre

2. Choisissez l'onglet **Ouvrir les fichiers et les ports**.
  
3. Pour les applications macOS, vous avez besoin du nom complet du chemin d’accès, notamment le nom de l’application.

#### <a name="service-domains"></a>Domaines de service

> [!NOTE]
> Le paramètre **Domaines de service** s’applique uniquement aux fichiers téléchargés à l’aide de Microsoft Edge ou de Google Chrome avec l’[extension Microsoft Purview](dlp-chrome-learn-about.md#learn-about-the-microsoft-purview-extension) installée.

Vous pouvez contrôler si les fichiers sensibles protégés par vos stratégies peuvent être chargés vers des domaines de service spécifiques à partir de Microsoft Edge.

##### <a name="allow"></a>Autoriser

Lorsque la liste **des domaines de service** est définie sur **Autoriser**, les stratégies DLP ne sont pas appliquées lorsqu’un utilisateur tente de charger un fichier sensible dans l’un des domaines de la liste.

Si le mode liste est défini sur **Autoriser**, toute activité utilisateur impliquant un élément sensible et un domaine figurant dans la liste est auditée. L’activité est autorisée. Lorsqu’un utilisateur tente une activité impliquant un élément sensible et un domaine qui *ne figure pas* dans la liste, les stratégies DLP et les actions définies dans les stratégies sont appliquées.

Par exemple, avec cette configuration :

- Le mode de liste **des domaines de** service est défini sur **Autoriser**.
    - Contoso.com est sur la liste.
-  Une stratégie DLP est définie sur **Bloquer** le chargement d’éléments sensibles qui contiennent des numéros de carte de crédit.
 
L’utilisateur tente de :

- Chargez un fichier sensible avec des numéros de carte de crédit sur contoso.com.
    - L’activité utilisateur est autorisée, auditée, un événement est généré, mais elle ne répertorie pas le nom de la stratégie ou le nom de la règle de déclenchement dans les détails de l’événement, et aucune alerte n’est générée. 

mais si un utilisateur tente de : 

- Chargez un fichier sensible avec des numéros de carte de crédit sur wingtiptoys.com (qui ne figure pas dans la liste).
    - La stratégie est appliquée et l’activité de l’utilisateur est bloquée. Un événement est généré et une alerte est générée. 
 
##### <a name="block"></a>Bloquer
 
Lorsque la liste **des domaines de service** est définie sur **Bloquer**, les stratégies DLP sont appliquées lorsqu’un utilisateur tente de charger un fichier sensible dans l’un des domaines de la liste.

Si le mode liste est défini sur **Bloquer**, lorsqu’un utilisateur tente une activité impliquant un élément sensible et un domaine figurant dans la liste, les stratégies DLP et les actions définies dans les stratégies de police sont appliquées. Toute activité impliquant un élément sensible et un domaine qui ne figure pas dans la liste est auditée et l’activité utilisateur est autorisée.

Par exemple, avec cette configuration :

- Le mode de liste **des domaines de** service est défini sur **Bloquer**.
    - Contoso.com est sur la liste.
-  Une stratégie DLP est définie sur **Bloquer avec remplacement** pour le chargement d’éléments sensibles qui contiennent des numéros de carte de crédit.
 
L’utilisateur tente de :

- Chargez un fichier sensible avec des numéros de carte de crédit sur contoso.com.
    - L’activité de l’utilisateur est bloquée, mais l’utilisateur peut remplacer le bloc, un événement est généré et une alerte est déclenchée.

mais si un utilisateur tente de : 

- Chargez un fichier sensible avec des numéros de carte de crédit sur wingtiptoys.com (qui ne figure pas dans la liste).
    - La stratégie *n’est pas* appliquée et l’activité de l’utilisateur est auditée. Un événement est généré, mais il ne répertorie pas le nom de la stratégie ou le nom de la règle de déclenchement dans les détails de l’événement, et aucune alerte n’est générée. 

> [!IMPORTANT]
> Lorsque le mode de restriction de service est configuré sur « Autoriser », vous devez configurer au moins un domaine de service avant l’application des restrictions.

Utilisez le format FQDN du domaine de service sans fin `.` lorsque vous ajoutez un domaine à la liste.

Par exemple :

| Input | Comportement de correspondance des URL |
|---|---|
| **CONTOSO.COM** |**Correspond au nom de domaine spécifié et à tout sous-site** : <p>*://contoso.com<p>*://contoso.com/ <p>*://contoso.com/anysubsite1 <p>*:/ /contoso.com/anysubsite1/anysubsite2 (etc.) <p>**Ne correspond pas aux sous-domaines ou aux domaines non spécifiés** : <p>*://toutsousdomaine.contoso.com <p>*://toutsousdomaine.contoso.com.AU |
| ***.CONTOSO.COM** |**Correspond au nom de domaine spécifié, à tout sous-domaine et à tout site** : <p>*://contoso.com <p>*://contoso.com/toutsoussite <p>*://contoso.com/toutsoussite1/toutsoussite2 <p>*://toutsousdomaine.contoso.com/ <p>*://toutsousdomaine.contoso.com/toutsoussite/ <p>*://toutsousdomaine1.toutsousdomaine2.contoso.com/toutsoussite/ <p>*://anysubdomain1.anysubdomain2.contoso.com/anysubsite1/anysubsite2 (etc.) <p>**Ne correspond pas aux domaines non spécifiés** <p>*://toutsousdomaine.contoso.com.AU/ |
| **`www.contoso.com`** |**Correspond au nom de domaine spécifié** : <p>`www.contoso.com` <p>**Ne correspond pas à des domaines ou sous-domaines non spécifiés** <p>*://toutsousdomaine.contoso.com/, dans ce cas, vous devez placer le nom de domaine FQDN lui-même `www.contoso.com`|

#### <a name="sensitive-service-domains"></a>Domaines de service sensibles

Lorsque vous répertoriez un site web dans des domaines de services sensibles, vous pouvez auditer, bloquer avec remplacement ou bloquer les utilisateurs lorsqu’ils tentent d’effectuer les opérations suivantes :

- imprimer à partir d’un site web
- copier des données à partir d’un site web
- enregistrer un site web en tant que fichiers locaux
- charger un fichier sensible sur un site web exclu (ceci est configuré dans la stratégie)

Pour les actions d’impression, de copie de données et d’enregistrement, chaque site web doit être répertorié dans un groupe de sites web et l’utilisateur doit accéder au site web via Microsoft Edge. Pour l’action de chargement, l’utilisateur peut utiliser Microsoft Edge ou Google Chrome avec l’extension Purview. Les domaines de service sensibles sont utilisés conjointement avec une stratégie DLP pour les appareils. Vous pouvez également définir des groupes de sites web auxquels vous souhaitez affecter des actions de stratégie différentes des actions de groupe de sites web globales. Pour plus d’informations, consultez le [scénario 6 Surveiller ou restreindre les activités des utilisateurs sur des domaines de service sensibles](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains) .


### <a name="additional-settings-for-endpoint-dlp"></a>Paramètres supplémentaires pour le point de terminaison DLP

#### <a name="business-justification-in-policy-tips"></a>Justification métier dans les conseils de stratégie

Vous pouvez contrôler l’interaction des utilisateurs avec l’option de justification métier dans les notifications de conseil de stratégie DLP. Cette option s’affiche lorsque les utilisateurs effectuent une activité protégée par le paramètre **Bloquer avec remplacement** dans une stratégie DLP. Il s’agit d’un paramètre global. Vous pouvez choisir l’une des options suivantes :

- **Afficher les options par défaut et la zone de texte personnalisée** : par défaut, les utilisateurs peuvent sélectionner une justification intégrée ou entrer leur propre texte.
- **Afficher uniquement les options par défaut** : les utilisateurs peuvent uniquement sélectionner une justification intégrée.
- **Afficher uniquement la zone de texte personnalisée** : les utilisateurs peuvent uniquement entrer leur propre justification. Seule la zone de texte apparaîtra dans la notification de conseil de politique d'utilisateur final. 

##### <a name="customizing-the-options-in-the-drop-down-menu"></a>Personnalisation des options dans le menu déroulant

Vous pouvez créer jusqu’à cinq options personnalisées qui s’affichent lorsque les utilisateurs interagissent avec le conseil de notification de stratégie en sélectionnant le **menu déroulant Personnaliser les options**. 


|Option |Texte par défaut  |
|---------|---------|
|Option 1    | **Cela fait partie d’un flux de travail métier établi**  ou vous pouvez entrer un texte personnalisé        |
|Option 2  |**Mon responsable a approuvé cette action** ou vous pouvez entrer un texte personnalisé         |
|Option 3   |**Accès urgent requis ; Je notifierai mon responsable séparément** ou vous pourrez entrer un texte personnalisé          |
|Afficher l’option de faux positif     |**Les informations de ces fichiers ne sont pas sensibles** ou vous pouvez entrer un texte personnalisé          |
|Option 5    |**Autre** ou vous pouvez entrer un texte personnalisé         |

### <a name="always-audit-file-activity-for-devices"></a>Toujours auditer l’activité des fichiers pour les appareils

Lors de l’intégration d’appareils, l’activité DLP pour les fichiers Office, PDF et CSV est automatiquement auditée par défaut et peut être consultée dans l’explorateur d’activité. Activez cette fonctionnalité si vous souhaitez que cette activité soit auditée uniquement lorsque des appareils intégrés sont inclus dans une stratégie active.

L’activité des fichiers est toujours auditée pour les appareils intégrés, qu’ils soient inclus dans une stratégie active ou non.

> [!IMPORTANT]
> Avant de pouvoir utiliser des [groupes d’imprimantes (préversion),](#printer-groups-preview) des [groupes d’appareils de stockage amovibles](#removable-storage-device-groups-preview), des [groupes de partage réseau](#network-share-groups-preview) et [des paramètres VPN](#vpn-settings-preview) , vous devez vous inscrire [ici](https://forms.office.com/r/GNVTFvxuZv).

### <a name="printer-groups-preview"></a>Groupes d’imprimantes (préversion)

Utilisez ce paramètre pour définir des groupes d’imprimantes auxquels vous souhaitez affecter des actions de stratégie différentes des actions d’impression globales. Par exemple, supposons que vous souhaitez que votre stratégie DLP bloque l’impression des contrats sur toutes les imprimantes, à l’exception des imprimantes qui se trouvent dans le service juridique.

Cette fonctionnalité est disponible pour les appareils exécutant l’une des versions windows suivantes :  

- Windows 10 et versions ultérieures (20H2, 21H1, 21H2) 
- Win 11 21H2, 22H2
- Windows Server 2022

Vous définissez une imprimante en fonction des paramètres suivants :

- Nom convivial de l’imprimante : obtenez la valeur du nom de l’imprimante conviviale à partir des détails de la propriété de l’appareil d’imprimante dans le gestionnaire d’appareils.
- ID de produit USB : obtenez la valeur du chemin d’accès de l’instance d’appareil à partir des détails de la propriété de l’appareil d’imprimante dans le gestionnaire d’appareils. Convertissez-le au format ID de produit et ID de fournisseur. Consultez [les identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers).
- ID du fournisseur USB : obtenez la valeur du chemin d’accès de l’instance d’appareil à partir des détails de la propriété de l’appareil d’imprimante dans le gestionnaire d’appareils. Convertissez-le au format ID de produit et ID de fournisseur. Consultez [les identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers).
- Plage d’adresses IP
- Imprimer dans un fichier : par exemple, Microsoft Print au format PDF ou Microsoft XPS Document Writer.
- Impression universelle déployée sur une imprimante - Voir, [configurer l’impression universelle](/universal-print/fundamentals/universal-print-getting-started.md) pour plus d’informations sur les imprimantes universelles
- Imprimante d’entreprise : est une file d’attente d’impression partagée via le serveur d’impression Windows local dans votre domaine. Son chemin d’accès peut ressembler  \\à print-server\contoso.com\legal_printer_001
- Imprimer sur local

Vous attribuez un **nom d’affichage** à chaque imprimante du groupe. Le nom apparaît uniquement dans la console Purview. Ainsi, en continuant avec l’exemple, vous allez créer un groupe d’imprimantes nommé **Imprimantes légales** et ajouter des imprimantes individuelles (avec un alias) par leur nom convivial, comme `legal_printer_001`, `legal_printer_002` et `legal_color_printer`.

Vous pouvez sélectionner plusieurs paramètres pour vous aider à identifier sans ambiguïté une imprimante spécifique.

Vous pouvez affecter ces actions de stratégie au groupe dans une stratégie DLP :

- Autoriser (auditer sans notifications ou alertes utilisateur)
- Auditer uniquement (vous pouvez ajouter des notifications et des alertes)
- Bloquer avec remplacement (bloque l’action, mais l’utilisateur peut le remplacer)
- Bloquer (blocs, quoi qu’il arrive)

#### <a name="create-a-printer-group"></a>Créer un groupe d’imprimantes

1. Ouvrez [portail de conformité Microsoft Purview](https://compliance.microsoft.com) >  **Data loss prevention** > **Endpoint DLP settings** > **Printer groups**.
1. Sélectionnez **Créer un groupe d’imprimantes**.
1. Donnez un nom au groupe.
1. Sélectionnez **Ajouter une imprimante**.
1. Donnez à l’imprimante un **Alias qui n’apparaîtra qu’ici.
1. Sélectionnez les paramètres et fournissez les valeurs pour identifier sans ambiguïté l’imprimante spécifique.
1. Sélectionnez **Ajouter**.
1. Ajoutez d’autres imprimantes en fonction des besoins.
1. Sélectionnez **Fermer**.

Le cas d’usage le plus courant consiste à utiliser des groupes d’imprimantes comme liste verte, comme dans l’exemple ci-dessus, pour autoriser l’impression de contrats uniquement sur les imprimantes qui se trouvent dans le service juridique. Une fois que vous avez défini un groupe d’imprimantes ici, il est disponible pour être utilisé dans vos stratégies qui sont limitées aux **appareils**. Consultez le [scénario 7 Groupes d’autorisation](endpoint-dlp-using.md#scenario-7-authorization-groups-preview) pour plus d’informations sur la configuration des actions de stratégie pour utiliser des groupes d’autorisation.

### <a name="removable-storage-device-groups-preview"></a>Groupes d’appareils de stockage amovibles (préversion)

Utilisez ce paramètre pour définir des groupes d’appareils de stockage amovibles, tels que les lecteurs usb, auxquels vous souhaitez affecter des actions de stratégie différentes des actions d’impression globales. Par exemple, supposons que votre stratégie DLP bloque la copie d’éléments avec des spécifications d’ingénierie sur tous les périphériques de stockage amovibles, à l’exception des disques durs connectés à USB qui sont utilisés pour sauvegarder des données et qui sont ensuite envoyés hors site.

Cette fonctionnalité est disponible pour les appareils exécutant l’une des versions windows suivantes :  

- Windows 10 et versions ultérieures (20H2, 21H1, 21H2) 
- Win 11 21H2, 22H2
- Windows 10 RS5 (KB 5006744) et Windows Server 2022 

Vous pouvez définir des périphériques de stockage amovibles en fonction des paramètres suivants :

- Nom convivial de l’appareil de stockage : obtenez la valeur du nom convivial à partir des détails de la propriété de l’appareil de stockage dans le gestionnaire d’appareils.
- ID de produit USB : obtenez la valeur du chemin d’accès de l’instance d’appareil à partir des détails de la propriété de l’appareil d’imprimante dans le gestionnaire d’appareils. Convertissez-le au format ID de produit et ID de fournisseur. Consultez [les identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers).
- ID du fournisseur USB : obtenez la valeur du chemin d’accès de l’instance d’appareil à partir des détails de la propriété de l’appareil d’imprimante dans le gestionnaire d’appareils. Convertissez-le au format ID de produit et ID de fournisseur. Consultez [les identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers).
- ID de numéro de série : obtenez la valeur d’ID de numéro de série à partir des détails de la propriété de l’appareil de stockage dans le gestionnaire d’appareils.
- ID d’appareil : obtenez la valeur de l’ID de l’appareil à partir des détails de la propriété de l’appareil de stockage dans le gestionnaire d’appareils.
- ID de chemin d’accès de l’instance : obtenez la valeur de l’ID de l’appareil à partir des détails de la propriété de l’appareil de stockage dans le gestionnaire d’appareils.
- ID matériel : obtenez la valeur de l’ID matériel à partir des détails de la propriété de l’appareil de stockage dans le gestionnaire d’appareils.

Vous attribuez un **alias** à chaque périphérique de stockage amovible du groupe. L’alias est un nom qui apparaît uniquement dans la console Purview. Ainsi, en continuant avec l’exemple, vous allez créer un groupe d’appareils de stockage amovible nommé **Sauvegarde** et ajouter des appareils individuels (avec un alias) par leur nom convivial, par exemple `backup_drive_001`, et `backup_drive_002`.

Vous pouvez sélectionner plusieurs paramètres et le groupe d’imprimantes inclut tous les appareils qui répondent à ces paramètres.

Vous pouvez affecter ces actions de stratégie au groupe dans une stratégie DLP :

- Autoriser (auditer sans notifications ou alertes utilisateur)
- Auditer uniquement (vous pouvez ajouter des notifications et des alertes)
- Bloquer avec remplacement (bloque l’action, mais l’utilisateur peut le remplacer)
- Bloquer (blocs, quoi qu’il arrive)

#### <a name="create-a-removable-storage-device-group"></a>Créer un groupe d’appareils de stockage amovible

1. Ouvrez [portail de conformité Microsoft Purview](https://compliance.microsoft.com) >  **Data loss prevention** > **Endpoint DLP settings** > **Removable storage device groups**.
1. Sélectionnez **Créer un groupe d’appareils de stockage amovible**.
1. Indiquez un **nom de groupe**.
1. Sélectionnez **Ajouter un périphérique de stockage amovible**.
1. Indiquez un **alias**.
1. Sélectionnez les paramètres et fournissez les valeurs pour identifier sans ambiguïté l’appareil spécifique.
1. Sélectionnez **Ajouter**.
1. Ajoutez d’autres appareils au groupe en fonction des besoins.
1. Sélectionnez **Fermer**.

Le cas d’usage le plus courant consiste à utiliser des groupes d’appareils de stockage amovibles comme liste verte, comme dans l’exemple ci-dessus, pour autoriser la copie de fichiers uniquement sur les appareils qui se trouvent dans le groupe **Sauvegarde** . Une fois que vous avez défini un groupe d’appareils de stockage amovible ici, il est disponible pour être utilisé dans vos stratégies qui sont limitées aux **appareils**. Consultez le [scénario 7 Groupes d’autorisation](endpoint-dlp-using.md#scenario-7-authorization-groups-preview) pour plus d’informations sur la configuration des actions de stratégie pour utiliser des groupes d’autorisation. Bien que le scénario 7 utilise des groupes d’autorisation d’imprimante comme exemple, les principes sont identiques. La seule chose qui change sont les noms des groupes et les actions que vous sélectionnez.

### <a name="network-share-groups-preview"></a>Groupes de partage réseau (préversion)

Utilisez ce paramètre pour définir des groupes de chemins d’accès de partage réseau auxquels vous souhaitez affecter des actions de stratégie différentes des actions de chemin de partage réseau globales. Par exemple, supposons que votre stratégie DLP soit bloquée lorsque les utilisateurs tentent d’enregistrer ou de copier des fichiers protégés sur des partages réseau, à l’exception des partages réseau de ce groupe.


Cette fonctionnalité est disponible pour les appareils exécutant l’une des versions windows suivantes :  

- Windows 10 et versions ultérieures (20H2, 21H1, 21H2) 
- Win 11 21H2, 22H2
- Windows 10 RS5 (KB 5006744) et Windows Server 2022 


Vous incluez des chemins de partage réseau en définissant le préfixe avec lequel ils commencent tous. Par exemple :

- '\\Library' correspondra à :
    -  Dossier \Library et tous ses sous-dossiers.

- Vous pouvez utiliser des caractères génériques, par exemple «\\ Users\*\Desktop » correspond à :
    - '\\USers\user1\Desktop'
    - '\\USers\user1\user2\Desktop'
    - '\\Users\*\Desktop'

- Vous pouvez utiliser des variables environnementales, par exemple :
    - %AppData%\app123

Vous pouvez affecter ces actions de stratégie au groupe dans une stratégie DLP :

- Autoriser (auditer sans notifications ou alertes utilisateur)
- Auditer uniquement (vous pouvez ajouter des notifications et des alertes)
- Bloquer avec remplacement (bloque l’action, mais l’utilisateur peut le remplacer)
- Bloquer (blocs, quoi qu’il arrive)

#### <a name="create-a-network-share-group"></a>Créer un groupe de partage réseau

1. Ouvrez [portail de conformité Microsoft Purview](https://compliance.microsoft.com) >  **Data loss prevention** > **Endpoint DLP settings** > **Network share groups**.
1. Sélectionnez **Créer un groupe de partage réseau**.
1. Indiquez un **nom de groupe**.
1. Ajoutez le chemin d’accès au fichier au partage.
1. Sélectionnez **Ajouter**.
1. Ajoutez d’autres chemins d’accès de partage au groupe en fonction des besoins.
1. Sélectionnez **Fermer**.


Le cas d’usage le plus courant consiste à utiliser le groupe de partages réseau comme liste verte, comme dans l’exemple ci-dessus, pour permettre aux utilisateurs d’enregistrer ou de copier des fichiers protégés uniquement sur les partages réseau définis dans le groupe. Une fois que vous avez défini un groupe de partage de réseaux ici, il est disponible pour être utilisé dans vos stratégies qui sont limitées aux **appareils**. Consultez le [scénario 7 Groupes d’autorisation](endpoint-dlp-using.md#scenario-7-authorization-groups-preview) pour plus d’informations sur la configuration des actions de stratégie pour utiliser des groupes d’autorisation.

### <a name="vpn-settings-preview"></a>Paramètres VPN (préversion)

Utilisez la liste VPN pour contrôler uniquement les actions qui sont effectuées sur ce VPN.

Cette fonctionnalité est disponible pour les appareils exécutant l’une des versions suivantes de Windows :  
    
- Windows 10 et versions ultérieures (20H2, 21H1, 21H2) 
- Windows 11 21H2, 22H2
- Windows 10 RS5 (KB 5006744)

Lorsque vous répertoriez un VPN dans **les paramètres VPN** , vous pouvez leur affecter ces actions de stratégie :

- Autoriser (auditer sans notifications ou alertes utilisateur)
- Auditer uniquement (vous pouvez ajouter des notifications et des alertes)
- Bloquer avec remplacement (bloque l’action, mais l’utilisateur peut le remplacer)
- Bloquer (blocs, quoi qu’il arrive)

Ces actions peuvent être appliquées individuellement ou collectivement à ces activités utilisateur :

- Copier dans le Presse-papiers
- Copier sur un appareil amovible USB
- Copier vers un partage réseau
- Imprimer
- Copier ou déplacer à l'aide d'une application Bluetooth non autorisée
- Copier ou déplacer à l’aide de RDP

Lors de la configuration d’une stratégie DLP pour restreindre l’activité sur les appareils, vous pouvez contrôler ce qui se passe pour chaque activité effectuée lorsque les utilisateurs sont connectés à votre organisation dans l’un des VPN répertoriés.

Vous définissez vpN par ces paramètres Adresse **de serveur** ou **adresse réseau**. 

#### <a name="get-the-server-address-or-network-address"></a>Obtenir l’adresse du serveur ou l’adresse réseau

1. Sur un appareil Windows surveillé par DLP, ouvrez une fenêtre **Windows PowerShell** en tant qu’administrateur.
1. Exécuter cette applet de commande

```powershell-interactive
Get-VpnConnection
```
3. L’exécution de cette applet de commande retourne plusieurs champs et valeurs.
1. Recherchez le champ **ServerAddress** et enregistrez cette valeur. Vous l’utiliserez lorsque vous créerez une entrée VPN dans la liste VPN.
1. Recherchez le champ **Nom** et enregistrez cette valeur. Le champ **Nom** correspond au champ **Adresse réseau** lorsque vous créez une entrée VPN dans la liste VPN.

#### <a name="add-a-vpn"></a>Ajouter un VPN

1. Ouvrez [portail de conformité Microsoft Purview](https://compliance.microsoft.com) >  **Paramètres VPN des paramètres** >  DLP du point de terminaison de **protection contre la** >  perte **de données**.
1. Sélectionnez **Ajouter ou modifier des adresses VPN**.
1. Indiquez **l’adresse du serveur** ou **l’adresse réseau** à partir de l’exécution de Get-VpnConnection.
1. Sélectionnez **Enregistrer**.
1. Fermez l’élément.

> [!IMPORTANT]
> Lorsque vous utilisez la liste VPN pour définir les actions d’une stratégie, vous voyez également le **réseau d’entreprise** comme option. Les connexions **réseau d’entreprise** sont toutes des connexions aux ressources de votre organisation. Ces connexions peuvent inclure des VPN. 

Consultez le [scénario 8 Exceptions réseau](endpoint-dlp-using.md#scenario-8-network-exceptions-preview)pour plus d’informations sur la configuration des actions de stratégie pour utiliser des exceptions réseau.

## <a name="see-also"></a>Voir aussi

- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Intégrer les appareils Windows 10 et Windows 11 dans la vue d’ensemble de Microsoft Purview](/microsoft-365/compliance/device-onboarding-overview)
- [Abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (ADD) adhésion](/azure/active-directory/devices/concept-azure-ad-join)
- [Télécharger le nouveau Microsoft Edge sur la base de chrome](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
