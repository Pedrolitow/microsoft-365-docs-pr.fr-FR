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
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment configurer les paramètres centraux de protection contre la perte de données (DLP) des points de terminaison.
ms.openlocfilehash: 99598880515dd14bc453ebd61a633be7eb66a9fc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629946"
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

## <a name="dlp-settings"></a>Paramètres DLP

Avant de commencer, vous devez configurer vos paramètres DLP. 

### <a name="endpoint-dlp-windows-1011-and-macos-settings"></a>Paramètres de point de terminaison DLP Windows 10/11 et macOS

|Setting |Windows 10, 1809 et ultérieures, Windows 11  |macOS Catalina 10.15 ou version ultérieure |Notes  |
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

Lorsque la classification avancée est activée, le contenu est envoyé de l’appareil local aux services cloud à des fins d’analyse et de classification. Si l’utilisation de la bande passante est un problème, vous pouvez définir une limite sur la quantité pouvant être utilisée sur une plage de 24 heures. La limite est configurée dans les paramètres DLP du point de terminaison et est appliquée par appareil. Si vous définissez une limite d’utilisation de la bande passante et qu’elle est dépassée, DLP cesse d’envoyer le contenu utilisateur au cloud. À ce stade, la classification des données se poursuit localement sur l’appareil, mais la classification utilisant la correspondance exacte des données, les entités nommées et les classificateurs pouvant être entraînés n’est pas disponible. Lorsque l’utilisation cumulative de la bande passante redevient inférieure à la limite définie sur la plage de 24 heures, la communication avec les services cloud reprend.

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

- Chemin d’accès au fichier valide qui se termine par `\*`, ce qui signifie uniquement les fichiers sous sous-dossiers, en plus des fichiers directement sous dossier. <br/>Par exemple : `C:\Temp\*`

- Chemin d’accès au fichier valide qui se termine sans `\` ou `\*`, ce qui signifie tous les fichiers directement sous dossier et tous les sous-dossiers. <br/>Par exemple : `C:\Temp`

- Chemin d’accès avec caractère générique entre `\` de chaque côté. <br/>Par exemple : `C:\Users\*\Desktop\`

- Chemin d’accès avec caractère générique entre `\` de chaque côté et avec `(number)` pour donner le nombre exact de sous-dossiers. <br/>Par exemple : `C:\Users\*(1)\Downloads\`

- Un chemin d’accès avec des variables d’environnement système. <br/>Par exemple : `%SystemDrive%\Test\*`

- Un mélange de tous les éléments ci-dessus. <br/>Par exemple : `%SystemDrive%\Users\*\Documents\*(2)\Sub\`

#### <a name="macos-devices"></a>appareils macOS

Semblable aux appareils Windows 10, vous pouvez ajouter vos propres exclusions pour les appareils macOS.

- Les définitions de chemin de fichier sont insensibles à la casse, c'est `User` donc la même chose que `user`.

- Les valeurs génériques sont prises en charge. Ainsi, une définition de chemin d’accès peut contenir un `*` au milieu du chemin d’accès ou à la fin du chemin d’accès. Par exemple : `/Users/*/Library/Application Support/Microsoft/Teams/*`

#####  <a name="recommended-file-path-exclusions-preview"></a>Exclusions de chemin de fichier recommandées (préversion)

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

Les groupes d’applications restreintes sont des collections d’applications que vous créez dans les paramètres DLP, puis que vous ajoutez à une règle dans une stratégie. Lorsque vous ajoutez un groupe d’applications restreintes à une stratégie, vous pouvez prendre les mesures définies dans ce tableau.

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

Si Notepad.exe est ajouté à **Applications restreintes** et que **Activités de fichier pour toutes les applications** est configuré pour **Appliquer des restrictions à des activité spécifiques** et les deux sont configurés comme suit :

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

Si une application ne figure pas dans **les activités de fichier pour les applications dans des groupes d’applications restreints** ou ne figure pas dans la liste **des activités d’application restreintes** ou se trouve dans la liste **des activités d’application restreintes** avec une action de `Audit only`ou « Bloquer avec remplacement », toutes **les restrictions définies dans les activités de fichier pour toutes les applications** sont appliquées dans la même règle.  

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

Pour les appareils Windows vous ajoutez des navigateurs, identifiés par leur nom exécutable, qui ne pourront pas accéder aux fichiers qui correspondent aux conditions d’une stratégie DLP appliquée dans laquelle la restriction de téléchargement vers les services cloud est définie pour bloquer ou bloquer le remplacement. Lorsque ces navigateurs ne peuvent pas accéder à un fichier, les utilisateurs finaux voient une notification toast leur demandant d’ouvrir le fichier via Microsoft Edge.

Pour les appareils macOS, vous devez ajouter le chemin d’accès complet au fichier. Pour trouver le chemin complet des applications Mac :

1. Sur l'appareil macOS, ouvrez **Activity Monitor**. Recherchez et double-cliquez sur le processus que vous souhaitez restreindre

2. Choisissez l'onglet **Ouvrir les fichiers et les ports**.
  
3. Pour les applications macOS, vous avez besoin du nom complet du chemin d’accès, notamment le nom de l’application.

#### <a name="service-domains"></a>Domaines de service

> [!NOTE]
> Le paramètre **Domaines de service** s’applique uniquement aux fichiers téléchargés à l’aide de Microsoft Edge ou de Google Chrome avec l’[extension Microsoft Purview](dlp-chrome-learn-about.md#learn-about-the-microsoft-purview-extension) installée.

Vous pouvez déterminer si les fichiers sensibles protégés par vos stratégies peuvent être téléchargés vers des domaines de service spécifiques à partir de Microsoft Edge.

Si le mode de liste est paramétré sur **Bloquer**, l’utilisateur ne peut pas télécharger des éléments sensibles dans ces domaines. Lorsqu’une action de téléchargement est bloquée parce qu’un élément correspond à une stratégie DLP, DLP génère un avertissement ou bloque le téléchargement de l’élément sensible.

Si le mode liste est défini sur **Autoriser**, les utilisateurs peuvent charger des éléments sensibles **_uniquement_** vers ces domaines, et l’accès au chargement vers tous les autres domaines n’est pas autorisé.

> [!IMPORTANT]
> Lorsque le mode de restriction de service est configuré sur « Autoriser », vous devez configurer au moins un domaine de service avant l’application des restrictions.

Utiliser le format de nom de domaine complet du domaine de service sans la fin `.` 

Par exemple :

 `www.contoso.com` 

Les caractères génériques ne sont pas pris en charge.

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
