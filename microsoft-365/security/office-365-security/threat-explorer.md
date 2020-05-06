---
title: Explorateur de menaces et détections en temps réel
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
description: Découvrez comment utiliser l’Explorateur et les détections en temps réel dans &amp; le centre de sécurité conformité pour examiner et répondre efficacement aux menaces.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7d540b52a403e43be06fc731590d183d5edfa7f9
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036751"
---
# <a name="threat-explorer-and-real-time-detections"></a>Explorateur de menaces et détections en temps réel

Si votre organisation dispose d' [office 365 Advanced Threat Protection](office-365-atp.md) (Office 365 ATP) et que vous disposez des [autorisations nécessaires](#required-licenses-and-permissions), vous disposez de l' **Explorateur** ou des **détections en temps réel** (auparavant des *rapports en temps réel* ). [see what's new](#new-features-in-threat-explorer-and-real-time-detections) Dans le centre de sécurité & conformité, accédez à **gestion des menaces**, puis choisissez **Explorateur** _ou_ **détections en temps réel**.

|||
|---|---|
|**Avec le plan ATP 2, vous pouvez voir :**|**Avec le plan ATP 1, vous pouvez voir :**|
|![Explorateur de menaces](../../media/threatmgmt-explorer.png)|![Détections en temps réel](../../media/threatmgmt-realtimedetections.png)|
|

Avec l’Explorateur (ou les détections en temps réel), vous disposez d’un puissant rapport qui permet à votre équipe des opérations de sécurité d’examiner et de répondre efficacement aux menaces. L’État ressemble à l’image suivante :

![Accéder à l’Explorateur \> de gestion des menaces](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Ce rapport vous permet d’utiliser les actions suivantes :

- [Voir programmes malveillants détectés par les fonctionnalités de sécurité de Microsoft 365](#see-malware-detected-in-email-by-technology)
- [Afficher les données sur les URL d’hameçonnage et cliquez sur verdict](#view-data-about-phishing-urls-and-click-verdict)
- [Démarrer un processus d’enquête et de réponse automatisés à partir d’une vue dans l’Explorateur](#start-automated-investigation-and-response) (plan ATP 2 uniquement)
- ... [Examinez le courrier électronique malveillant, et bien plus encore](#more-ways-to-use-explorer-or-real-time-detections)!

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nouvelles fonctionnalités de l’Explorateur de menaces et des détections en temps réel

Trois nouvelles fonctionnalités ajoutées à l’Explorateur de menaces et des détections en temps réel :

- [Aperçu de l’en-tête de message et téléchargement du corps du courrier électronique](#preview-email-header-and-download-email-body)
- [Chronologie du courrier électronique](#email-timeline)
- [Exporter l’URL cliquez sur données](#export-url-click-data)

Ces nouvelles fonctionnalités sont décrites ci-dessous.

### <a name="preview-email-header-and-download-email-body"></a>Aperçu de l’en-tête de message et téléchargement du corps du courrier électronique

La possibilité de prévisualiser un en-tête de message et de télécharger le corps du courrier est une nouvelle fonctionnalité disponible dans l’Explorateur de menaces. Les administrateurs pourront analyser les en-têtes/messages électroniques téléchargés contre les menaces. Étant donné que le téléchargement de messages électroniques peut compromettre l’exposition des informations, ce processus est contrôlé par le contrôle d’accès basé sur les rôles (RBAC). Un nouveau rôle, *Aperçu*, doit être ajouté à un autre groupe de rôles (tel que les opérations de sécurité ou administrateur de sécurité) pour accorder la possibilité de télécharger des messages et des en-têtes d’aperçu dans la vue tous les messages électroniques.

Toutefois, l’Explorateur (et les détections en temps réel) ajoute également de nouveaux champs conçus pour vous donner une image plus complète de l’emplacement de vos messages électroniques. Une partie de cette modification est de faciliter la chasse aux personnes qui effectuent des opérations de sécurité, mais le résultat net est de savoir en un clin d’œil l’emplacement des messages électroniques posant problème.

Comment cela est-il fait ? L’état de remise est désormais divisé en deux colonnes :

- **Action de remise** : quel est le statut de ce courrier électronique ?
- **Emplacement de remise** : où ce message électronique a-t-il été routé ?

L’action de remise est l’action entreprise sur un courrier électronique en raison de stratégies ou de détections existantes. Voici les actions possibles qu’un courrier électronique peut effectuer :

|||||
|---|---|---|---|
|**Cmds**|**Courrier indésirable**|**Blocked**|**Été**|
|Le courrier électronique a été remis dans la boîte de réception de l’utilisateur ou dans un autre dossier, et l’utilisateur peut y accéder directement.| Le courrier électronique a été envoyé au dossier de courrier indésirable de l’utilisateur ou au dossier supprimé, et l’utilisateur a accès aux messages électroniques de ces dossiers.| Tous les messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés, et qui ne sont pas accessibles par l’utilisateur.| Tous les messages électroniques pour lesquels des pièces jointes malveillantes ont été remplacées par des fichiers. txt qui indiquent que les pièces jointes étaient malveillantes.|
|

Et voici ce que l’utilisateur peut voir, et ce qu’il ne peut pas faire :

|||
|---|---|
|**Accessible aux utilisateurs finaux**|**Inaccessible aux utilisateurs finaux**|
|Cmds|Blocked|
|Courrier indésirable|Été|
|

Emplacement de remise : affiche les résultats des stratégies et des détections qui exécutent une post-remise. Elle est liée à une action de remise. Ce champ a été ajouté pour permettre de mieux comprendre l’action entreprise lors de la détection d’un message problématique. Voici les valeurs possibles de l’emplacement de remise :

- **Boîte de réception ou dossier**: le courrier électronique est dans la boîte de réception ou dans un dossier (en fonction de vos règles de messagerie électronique).
- **Local ou externe**: la boîte aux lettres n’existe pas sur le Cloud mais est en local.
- **Dossier de courrier indésirable**: le courrier électronique se trouve dans le dossier de courrier indésirable d’un utilisateur.
- **Dossier éléments supprimés**: le courrier électronique dans le dossier éléments supprimés d’un utilisateur.
- **Mise en quarantaine**: le courrier électronique en quarantaine et ne se trouve pas dans la boîte aux lettres d’un utilisateur.
- **Échec**: la messagerie n’a pas pu atteindre la boîte aux lettres.
- **Ignoré**: le courrier électronique est perdu dans le flux de messagerie.

### <a name="email-timeline"></a>Chronologie du courrier électronique

La **chronologie par courrier électronique** est une autre nouvelle fonctionnalité d’explorateur destinée à améliorer l’expérience de la chasse des administrateurs. Il réduit le traitement aléatoire, car il y a moins de temps passé à vérifier différents emplacements pour essayer de comprendre l’événement. Lorsque plusieurs événements se produisent à la même heure ou proches de celle-ci dans un e-mail, ces événements apparaissent dans un affichage chronologie. En fait, certains événements qui ont lieu après la livraison à votre courrier seront capturés dans la colonne « action spéciale ». La combinaison des informations de la chronologie de ce message avec l’action spéciale entreprise lors de la livraison post-remise donnera aux administrateurs un aperçu de la façon dont leurs stratégies fonctionnent, où les messages ont été finalement routés et, dans certains cas, ce qu’étaient l’évaluation finale.

Pour plus d’informations sur la recherche de messages électroniques malveillants, consultez la rubrique [examiner et résoudre les courriers électroniques malveillants remis dans Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>Exporter l’URL cliquez sur données

En outre, vous pouvez exporter des rapports pour les clics d’URL vers Microsoft Excel afin d’afficher à la fois leur ID de message réseau et leur verdict de clic, ce qui vous permet de comprendre où votre URL est à l’origine du trafic. Voici comment cela fonctionne. À partir de la gestion des menaces sur le lancement rapide Office 365, cliquez sur cette chaîne :

\> **Affichage** \> **Explorer** de l’hameçon \> **cliquer sur** les **URL principales ou sur URL en haut clics** \> **cliquez sur un enregistrement pour ouvrir le menu volant d’URL**

Lorsque vous cliquez sur une URL de la liste, vous verrez un nouveau bouton Exporter dans le panneau de débordement. Utilisez ce bouton pour déplacer des données vers une feuille de calcul Excel pour faciliter la création de rapports.

Vous pouvez accéder au même emplacement dans le rapport des détections en temps réel comme suit :

**Explorer** \> **Détections** \> **URLs** \> **View Phish** \> \> **Top URLs or Top Clicks** **Click on any record to open URL flyout** **Navigate to the Clicks Tab.** en temps réel de l’Explorateur afficher les URL de hameçonnage principales ou les clics en haut cliquez sur un enregistrement pour ouvrir le menu volant de l’URL accédez à l’onglet clics. \>

> [!TIP]
> L’ID de message réseau mappe le clic retour à des messages spécifiques lorsque vous recherchez dans l’Explorateur ou des outils tiers associés via l’ID de message réseau. La recherche par le biais de l’ID de message réseau donnera aux administrateurs le message électronique spécifique associé à un résultat de clic. Lors de l’exportation, l’identification de la corrélation de l’ID de message réseau permet une analyse plus rapide et plus puissante.

![tp_ExportClickResultAndNetworkID. png](../../media/tp_ExportClickResultAndNetworkID.png)

## <a name="see-malware-detected-in-email-by-technology"></a>Voir programmes malveillants détectés dans le courrier électronique par technologie

Supposons que vous souhaitez voir les programmes malveillants détectés par les messages électroniques, par la technologie Microsoft 365. Pour ce faire, utilisez l’affichage [courrier > programmes malveillants](threat-explorer-views.md#email--malware) de l’Explorateur (ou des détections en temps réel).

1. Dans le centre de sécurité & conformité[https://protection.office.com](https://protection.office.com)(), sélectionnez**Explorateur** de **gestion** > des menaces (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le menu **affichage** , choisissez **Email** > **programmes malveillants**de messagerie.

   ![Menu Affichage de l’Explorateur](../../media/ExplorerViewEmailMalwareMenu.png)

3. Cliquez sur **expéditeur**, puis choisissez**technologie de détection**de **base** > .

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

   ![Technologies de détection des programmes malveillants](../../media/ExplorerEmailMalwareDetectionTech.png)

4. Sélectionnez une option, puis cliquez sur le bouton **Actualiser** pour appliquer ce filtre.

   ![Technologie de détection sélectionnée](../../media/ExplorerEmailMalwareDetectionTechATP.png)

Le rapport est actualisé pour afficher les résultats de programmes malveillants détectés par courrier électronique, à l’aide de l’option de technologie que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus poussée.

## <a name="view-data-about-phishing-urls-and-click-verdict"></a>Afficher les données sur les URL d’hameçonnage et cliquez sur verdict

Supposons que vous vouliez voir les tentatives de hameçonnage via des URL dans des e-mails, y compris une liste des URL qui ont été autorisées, bloquées et remplacées. L’identification des URL sur lesquelles l’utilisateur a cliqué requiert la configuration de [liens fiables ATP](atp-safe-links.md) . Assurez-vous que vous avez configuré les [stratégies de liens fiables ATP](set-up-atp-safe-links-policies.md) pour la protection du temps de clic et la journalisation des « verdict de clic » par les liens fiables ATP.

Pour consulter les URL de hameçonnage dans les messages et les clics sur les URL dans les messages hameçons, utilisez la vue [courrier > hameçonnage](threat-explorer-views.md#email--phish) de l’Explorateur (ou des détections en temps réel).

1. Dans le centre de sécurité & conformité[https://protection.office.com](https://protection.office.com)(), sélectionnez**Explorateur** de **gestion** > des menaces (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le menu **affichage** , choisissez **courrier** > **hameçon**.

   ![Menu Affichage de l’Explorateur](../../media/ExplorerViewEmailPhishMenu.png)

3. Cliquez sur **expéditeur**, puis sur **URL** > , puis**cliquez sur verdict**.

4. Sélectionnez une ou plusieurs options, telles que **bloquées** et **bloquer le remplacement**, puis cliquez sur le bouton **Actualiser** qui se trouve sur la même ligne que les options pour appliquer le filtre. (Ne pas actualiser la fenêtre de votre navigateur.)

   ![URL et cliquez sur verdicts](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

    Le rapport est actualisé pour afficher deux tables d’URL différentes sous l’onglet URL sous le rapport :

   - Les **URL principales** sont les URL contenues dans les messages que vous avez filtrés vers et l’action de remise de courrier électronique compte pour chaque URL. Dans l’affichage e-mail de hameçonnage, cette liste contient généralement des URL légitimes. Les agresseurs incluent un mélange d’URL correctes et incorrectes dans leurs messages pour essayer de les remettre, mais ils rendent les liens malveillants plus intéressants pour l’utilisateur. Le tableau des URL est trié par nombre total d’e-mails (mais notez que cette colonne est masquée pour simplifier l’affichage).

   - Les **clics en haut** sont les liens fiables les URL sur lesquelles l’utilisateur a cliqué, triées par nombre total de clics (cette colonne ne montre pas non plus comment simplifier l’affichage). Nombre total par colonne indique le nombre de liens approuvés cliquez sur nombre de verdicts pour chaque URL sur laquelle vous avez cliqué. Dans la vue e-mail de hameçonnage, il s’agit plus souvent d’URL suspectes ou malveillantes, mais peut inclure des URL qui ne sont pas des menaces, mais qui se trouvent dans des messages hameçons. Les clics d’URL sur les liens non justifiés ne s’afficheront pas ici.

   Les deux tableaux d’URL affichent les URL les plus fréquentes dans les messages électroniques de hameçonnage par action de remise et par emplacement, et ils affichent des clics d’URL bloqués (ou visités malgré un avertissement) afin que vous puissiez comprendre quels liens incorrects potentiels ont été reçus par les utilisateurs et interagis avec les utilisateurs. À partir de là, vous pouvez effectuer une analyse plus poussée. Par exemple, sous le graphique, vous pouvez voir les URL principales dans les messages électroniques qui ont été bloqués dans l’environnement de votre organisation.

   ![URL de l’Explorateur bloquées](../../media/ExplorerPhishClickVerdictURLs.png)

   Sélectionnez une URL pour afficher des informations plus détaillées.
   
   > [!NOTE]
   > Dans la boîte de dialogue de menu volant d’URL, le filtrage sur les messages électroniques est supprimé pour vous montrer l’affichage complet de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques dans l’Explorateur sur ceux qui vous intéressent, de rechercher des URL spécifiques qui constituent des menaces potentielles, puis de mieux comprendre l’exposition de l’URL dans votre environnement (via la boîte de dialogue détails de l’URL) sans avoir à ajouter de filtres d’URL à l’affichage Explorateur lui-même.

## <a name="review-email-messages-reported-by-users"></a>Examiner les messages électroniques signalés par les utilisateurs

Supposons que vous voulez afficher les messages électroniques que les utilisateurs de votre organisation ont signalés comme courriers indésirables, non légitimes ou le hameçonnage à l’aide du [complément de message de rapport pour Outlook et Outlook sur le Web](enable-the-report-message-add-in.md). Pour ce faire, utilisez l’affichage [courrier > les soumissions](threat-explorer-views.md#email--submissions) de l’Explorateur (ou des détections en temps réel).

1. Dans le centre de sécurité & conformité[https://protection.office.com](https://protection.office.com)(), sélectionnez**Explorateur** de **gestion** > des menaces (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le **menu Affichage** , choisissez**envois**de **courrier électronique** > .

   ![Menu Affichage de l’Explorateur](../../media/explorer-view-menu-email-user-reported.png)

3. Cliquez sur **expéditeur**, puis sur**type de rapport**de **base** > .

4. Sélectionnez une option, par exemple **hameçonnage**, puis cliquez sur le bouton **Actualiser** .

   ![Hameçonnage signalé par l’utilisateur](../../media/EmailUserReportedReportType.png)

Le rapport est actualisé pour afficher les données relatives aux messages électroniques que les personnes de votre organisation ont signalées comme tentatives de hameçonnage. Vous pouvez utiliser ces informations pour effectuer une analyse plus poussée et, si nécessaire, ajuster vos [stratégies anti-hameçonnage ATP](configure-atp-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Démarrer une enquête et une réponse automatisées

> [!NOTE]
> Les fonctionnalités d’analyse et de réponse automatisées sont disponibles dans **office 365 ATP plan 2** et **Office 365 E5**.

(Nouveau !) L’analyse [et la réponse automatisées](automated-investigation-response-office.md) peuvent permettre à l’équipe de votre équipe de sécurité de gagner du temps et de faire des efforts pour examiner et limiter les cyberattaques. En plus de configurer des alertes pouvant déclencher un manuel de sécurité, vous pouvez démarrer un processus d’enquête et de réponse automatisés à partir d’une vue dans l’Explorateur.

Pour plus d’informations, reportez-vous à l' [exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-or-real-time-detections"></a>Autres méthodes d’utilisation de l’Explorateur (ou des détections en temps réel)

Outre les scénarios décrits dans cet article, vous disposez de nombreuses autres options de création de rapports dans l’Explorateur (ou des détections en temps réel).

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Affichage de fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft teams](malicious-files-detected-in-spo-odb-or-teams.md)
- [Obtenir une vue d’ensemble des affichages dans l’Explorateur de menaces (et des détections en temps réel)](threat-explorer-views.md)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez disposer de la protection avancée contre les menaces [Office 365](office-365-atp.md) pour obtenir des détections de l’Explorateur ou en temps réel.

- L’Explorateur est inclus dans Office 365 DAV plan 2.
- Le rapport de détections en temps réel est inclus dans Office 365 DAV plan 1.
- Prévoyez d’attribuer des licences pour tous les utilisateurs qui doivent être protégés par la protection avancée contre les menaces d’Office 365. (L’Explorateur ou les détections en temps réel affichent les données de détection pour les utilisateurs sous licence.)

Pour afficher et utiliser l’Explorateur ou les détections en temps réel, vous devez disposer des autorisations appropriées, telles que celles accordées à un administrateur de sécurité ou à un lecteur de sécurité.

- Pour le centre &amp; de sécurité conformité, vous devez disposer de l’un des rôles suivants :

  - Gestion de l’organisation
  - Administrateur de la sécurité (qui peut être affecté dans le centre d’administration Azure[https://aad.portal.azure.com](https://aad.portal.azure.com)Active Directory ())
  - Lecteur de sécurité

- Pour Exchange Online, vous devez disposer de l’un des rôles suivants, qui est affecté dans le centre[https://outlook.office365.com/ecp](https://outlook.office365.com/ecp)d’administration Exchange () ou avec des applets de commande PowerShell (consultez la rubrique [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)) :

  - Gestion de l’organisation
  - Gestion de l’organisation en affichage seul
  - Rôle Destinataires en affichage uniquement
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le centre &amp; de sécurité conformité](permissions-in-the-security-and-compliance-center.md)
- [Autorisations des fonctionnalités dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)

## <a name="some-differences-between-threat-explorer-and-real-time-detections"></a>Différences entre l’Explorateur de menaces et les détections en temps réel

- Le rapport de **détections en temps réel** est disponible dans Office 365 DAV plan 1, tandis que l' **Explorateur de menaces** est disponible dans Office 365 DAV plan 2.
- Le rapport des **détections en temps réel** vous permet d’afficher les détections en temps réel. L' **Explorateur de menaces** le fait également, mais vous permet également d’afficher des détails supplémentaires pour une attaque donnée.
- Une vue **tout le courrier** est disponible dans l’Explorateur de **menaces** (et n’est pas dans le rapport de **détections en temps réel** ).
- D’autres fonctionnalités de filtrage et les actions disponibles sont incluses dans l' **Explorateur de menaces**.

Pour plus d’informations, reportez-vous à la rubrique [Office 365 ATP Service Description : Feature Availability for Advanced Threat Protection (ATP) plans](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).
