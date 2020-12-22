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
- m365initiative-defender-office365
description: Utilisez l’Explorateur et les détections en temps réel dans le centre de sécurité &amp; conformité pour examiner et répondre efficacement aux menaces.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8bca8e39029fe041c0bab59e92d8a653647746ef
ms.sourcegitcommit: 0ecac0387be6b49025b79ce8eb949a8cf62481e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "49724413"
---
# <a name="threat-explorer-and-real-time-detections"></a>Explorateur de menaces et détections en temps réel

Si votre organisation dispose [de Microsoft Defender pour Office 365](office-365-atp.md) et que vous disposez des [autorisations nécessaires](#required-licenses-and-permissions), vous avez accès à l' *Explorateur* ou aux *détections en temps réel*, qui étaient auparavant des *rapports en temps réel*. ([Voir what’s New.](#new-features-in-threat-explorer-and-real-time-detections)) Dans le centre de sécurité & conformité, accédez à **gestion des menaces**, puis sélectionnez **Explorateur** _ou_ **détections en temps réel**.

|Avec Microsoft Defender pour Office 365 plan 2, vous voyez les éléments suivants :|Avec Microsoft Defender pour Office 365 plan 1, vous voyez les éléments suivants :|
|---|---|
|![Explorateur de menaces](../../media/threatmgmt-explorer.png)|![Détections en temps réel](../../media/threatmgmt-realtimedetections.png)|
|

L’Explorateur ou les détections en temps réel aident votre équipe chargée des opérations sur la sécurité à examiner et à répondre efficacement aux menaces. L’État ressemble à l’image suivante :

![Accéder à l’Explorateur de gestion des menaces \>](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Ce rapport vous permet d’utiliser les actions suivantes :

- [Voir programmes malveillants détectés par les fonctionnalités de sécurité de Microsoft 365](#see-malware-detected-in-email-by-technology)
- [Afficher l’URL d’hameçonnage et cliquez sur données de verdict](#view-phishing-url-and-click-verdict-data)
- [Démarrer un processus d’enquête et de réponse automatisés à partir d’une vue dans l’Explorateur](#start-automated-investigation-and-response) (Defender pour Office 365 plan 2 uniquement)
- [Enquête sur le courrier électronique malveillant, etc.](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-explorer-and-real-time-detections"></a>Améliorations apportées à l’Explorateur de menaces et aux détections en temps réel

### <a name="tags-in-threat-explorer"></a>Balises dans l’Explorateur de menaces

> [!NOTE]
> La fonctionnalité de balises utilisateur est en *mode aperçu*, n’est pas accessible à tous et peut faire l’objet de modifications. Pour plus d’informations sur le calendrier des publications, consultez la feuille de route Microsoft 365.

Les balises utilisateur identifient des groupes d’utilisateurs spécifiques dans Microsoft Defender pour Office 365. Pour plus d’informations sur les balises, notamment la gestion des licences et la configuration, consultez la rubrique [User Tags](user-tags.md).

Dans l’Explorateur de menaces, vous pouvez voir des informations sur les balises utilisateur dans les expériences suivantes.

#### <a name="email-grid-view"></a>Affichage grille du courrier électronique

La colonne de **balises** dans la grille du courrier électronique contient toutes les balises qui ont été appliquées aux boîtes aux lettres de l’expéditeur ou du destinataire. Par défaut, les balises système telles que les comptes de priorité apparaissent en premier.

> [!div class="mx-imgBorder"]
> ![Balises de filtre dans l’affichage de grille de courrier électronique](../../media/tags-grid.png)

#### <a name="filtering"></a>Filtrage

Vous pouvez utiliser des balises comme filtre. La recherche sur des comptes de priorité ou des balises utilisateur spécifiques. Vous pouvez également exclure les résultats qui ont certaines balises. Associez cette fonctionnalité à d’autres filtres pour affiner votre portée d’enquête.

[![Balises de filtre](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Balises not filter](../../media/tags-filter-not.png)

#### <a name="email-detail-flyout"></a>Menu volant détail du courrier électronique
Pour afficher les balises individuelles de l’expéditeur et du destinataire, sélectionnez l’objet pour ouvrir la fenêtre de sélection des détails du message. Sous l’onglet **Résumé** , les balises sender et Recipient sont affichées séparément, si elles sont présentes pour un e-mail.
Les informations relatives aux balises individuelles pour l’expéditeur et le destinataire s’étendent également aux données CSV exportées, où vous pouvez voir ces détails dans deux colonnes distinctes.

> [!div class="mx-imgBorder"]
> ![Balises de détails de messagerie](../../media/tags-flyout.png)

Les informations sur les balises sont également affichées dans l’URL clique sur mobile. Pour l’afficher, accédez à la vue hameçonnage ou tout le courrier, puis à l’onglet **URL** ou **URL** . Sélectionnez une fenêtre mobile d’URL individuelle pour afficher des détails supplémentaires sur les clics pour cette URL, y compris les balises associées à ce clic.

> [!div class="mx-imgBorder"]
> ![Balises d’URL](../../media/tags-urls.png)

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Améliorations de l’expérience de la chasse aux menaces (à venir)

### <a name="updated-threat-information-for-emails"></a>Informations de menace mises à jour pour les e-mails

Nous avons centré les améliorations de la qualité des données et de la plateforme pour améliorer la précision et la cohérence des données des enregistrements de messagerie. Les améliorations incluent la consolidation des informations de pré-livraison et post-livraison, telles que les actions exécutées sur un message électronique dans le cadre du processus ZAP, dans un seul enregistrement. Des détails supplémentaires comme le verdict du courrier indésirable, les menaces au niveau de l’entité (par exemple, l’URL qui était malveillante) et les emplacements de remise les plus récents sont également inclus.

Après ces mises à jour, vous verrez une seule entrée pour chaque message, quels que soient les différents événements de post-remise qui affectent le message. Les actions peuvent inclure ZAP, la correction manuelle (ce qui signifie l’intervention de l’administrateur), la remise dynamique, etc.

En plus de présenter les programmes malveillants et les menaces de hameçonnage, vous pouvez voir le verdict de courrier indésirable associé à un e-mail. Dans le courrier électronique, consultez toutes les menaces associées au courrier électronique, ainsi que les technologies de détection correspondantes. Un e-mail peut avoir zéro, une ou plusieurs menaces. Vous verrez les menaces actuelles dans la section des **Détails** de la fenêtre mobile de courrier électronique. Pour les différentes menaces (telles que les programmes malveillants et le hameçonnage), le champ **Tech Detection** indique le mappage de détection des menaces, qui est la technologie de détection qui a identifié la menace.

L’ensemble des technologies de détection inclut désormais de nouvelles méthodes de détection, ainsi que des technologies de détection du courrier indésirable. Vous pouvez utiliser le même ensemble de technologies de détection pour filtrer les résultats dans les différentes vues de messagerie (programmes malveillants, hameçons, tout le courrier électronique).

> [!NOTE]
> L’analyse de verdict ne doit pas nécessairement être liée à des entités. Par exemple, un message électronique peut être classé comme hameçonnage ou courrier indésirable, mais aucune URL n’est marquée par un verdict de courrier indésirable/courrier indésirable. Cela est dû au fait que les filtres évaluent également le contenu et d’autres détails pour un message électronique avant d’affecter un verdict.

#### <a name="threats-in-urls"></a>Menaces dans les URL

Vous pouvez maintenant voir la menace spécifique pour une URL sous l’onglet **Détails** de la fenêtre volante de messagerie. La menace peut être un *programme malveillant*, le *hameçonnage*, le *courrier indésirable* ou *aucun*.)

> [!div class="mx-imgBorder"]
> ![Menaces d’URL](../../media/URL_Threats.png)

### <a name="updated-timeline-view-upcoming"></a>Affichage chronologique mis à jour (à venir)

> [!div class="mx-imgBorder"]
> ![Affichage chronologique mis à jour](../../media/Email_Timeline.png)

La vue de chronologie identifie tous les événements de remise et post-remise. Elle inclut des informations sur la menace identifiée à ce moment pour un sous-ensemble de ces événements. La vue de chronologie fournit également des informations sur toute action supplémentaire effectuée (telle que ZAP ou correction manuelle), ainsi que le résultat de cette action. Les informations d’affichage de la chronologie incluent :

- **Source :** Source de l’événement. Il peut s’agir de l’administrateur/système/utilisateur.
- **Événement :** Inclut des événements de niveau supérieur tels que la remise d’origine, la correction manuelle, la préversion, les envois et la remise dynamique.
- **Action :** Action spécifique effectuée dans le cadre de l’action ZAP ou d’administration (par exemple, suppression récupérable).
- **Menaces :** Décrit les menaces (programmes malveillants, hameçons, courrier indésirable) identifiées à ce moment-là.
- **Résultat/Détails :** Plus d’informations sur le résultat de l’action, par exemple si elle a été effectuée dans le cadre de l’action ZAP/admin.

### <a name="original-and-latest-delivery-location"></a>Emplacement de remise d’origine et dernier

Actuellement, nous adressons l’emplacement de remise en surface dans la grille du courrier électronique et dans la fenêtre mobile e-mail. Le champ de l' **emplacement de remise** est renommé **_emplacement de remise d’origine_* _. Et nous introduisons un autre champ, _*_dernier emplacement de remise_*_.

_ *Emplacement de remise d’origine** fournit plus d’informations sur l’endroit où un courrier électronique a été remis initialement. L' **emplacement de remise le plus récent** indique quand un message a été débarqué après des actions système telles que *zap* ou des actions d’administration, telles que le *déplacement vers des éléments supprimés*. L’emplacement de remise le plus récent est destiné à informer les administrateurs de la post-remise du dernier emplacement connu du message ou de toute action système/administrateur. Il n’inclut aucune action de l’utilisateur final sur le courrier électronique. Par exemple, si un utilisateur a supprimé un message ou déplacé le message vers Archive/PST, le message « remise » ne sera pas mis à jour. Toutefois, si une action système a mis à jour l’emplacement (par exemple, ZAP suite à la mise en quarantaine d’un e-mail), l' **emplacement de remise le plus récent** apparaît sous la forme « quarantaine ».

> [!div class="mx-imgBorder"]
> ![Emplacements de remise mis à jour](../../media/Updated_Delivery_Location.png)

> [!NOTE]
> Dans certains cas, l' **emplacement de remise** et l' **action de remise** peuvent apparaître sous la forme « inconnu » :
>
> - Vous pouvez voir l' **emplacement de remise** comme « remis » et l’emplacement de **remise** comme « inconnu » si le message a été remis, mais une règle de boîte de réception a déplacé le message vers un dossier par défaut (par exemple brouillon ou Archive) et non vers le dossier boîte de réception ou courrier indésirable.
>
> - L' **emplacement de remise le plus récent** peut être inconnu si une action administrateur/système (par exemple zap) a été tentée, mais que le message est introuvable. En règle générale, l’action se produit après que l’utilisateur a déplacé ou supprimé le message. Dans ce cas, vérifiez la colonne **résultat** dans l’affichage chronologie. Recherchez l’instruction « le message a été déplacé ou supprimé par l’utilisateur ».

> [!div class="mx-imgBorder"]
> ![Emplacements de remise pour la chronologie](../../media/Updated_Timeline_Delivery_Location.png)

### <a name="additional-actions"></a>Actions supplémentaires

Des *actions supplémentaires* ont été appliquées après la remise du courrier électronique. Ils peuvent inclure *zap*, la *Correction manuelle* (action effectuée par un administrateur tel que la suppression douce), la *remise dynamique* et le *retraitement* (pour un e-mail détecté rétroactivement comme bon).

> [!NOTE]
> - Dans le cadre des modifications en attente, la valeur « supprimé par ZAP » actuellement représentée dans le filtre d’action de remise est rejetée. Vous pouvez rechercher tous les messages électroniques à l’aide de la méthode ZAP via **des actions supplémentaires**.
>
> - Il y aura de nouveaux champs et valeurs pour les **technologies de détection** et **des actions supplémentaires** (en particulier pour les scénarios zap). Vous devrez évaluer vos requêtes sauvegardées existantes et les requêtes suivies pour vous assurer qu’elles fonctionnent avec les nouvelles valeurs.

> [!div class="mx-imgBorder"]

> ![Actions supplémentaires dans l’Explorateur](../../media/Additional_Actions.png)

### <a name="system-overrides"></a>Substitutions système

Les *substitutions du système* vous permettent de définir des exceptions à l’emplacement de remise prévu d’un message. Vous ignorez l’emplacement de remise fourni par le système, en fonction des menaces et autres détections identifiées par la pile de filtrage. Les substitutions système peuvent être définies par le biais de la stratégie client ou utilisateur pour envoyer le message comme indiqué par la stratégie. Les substitutions peuvent identifier la remise non intentionnelle de messages malveillants en raison de configurations incomplètes, telles qu’un ensemble de stratégies d’expéditeur approuvées par un utilisateur. Ces valeurs de remplacement peuvent être les suivantes :

- Autorisé par la stratégie de l’utilisateur : un utilisateur crée des stratégies au niveau de la boîte aux lettres pour autoriser les domaines ou les expéditeurs.
- Bloqué par la stratégie de l’utilisateur : un utilisateur crée des stratégies au niveau de la boîte aux lettres pour bloquer les domaines ou les expéditeurs.
- Autorisé par la stratégie d’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie Exchange (également appelées règles de transport) pour autoriser les expéditeurs et les domaines pour les utilisateurs au sein de leur organisation. Il peut s’agir d’un ensemble d’utilisateurs ou de l’ensemble de l’organisation.
- Bloqué par la stratégie d’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie pour bloquer les expéditeurs, les domaines, les langues de message ou les adresses IP source pour les utilisateurs au sein de leur organisation. Cela peut être appliqué à un ensemble d’utilisateurs ou à l’ensemble de l’organisation.
- Extension de fichier bloquée par la stratégie d’organisation : l’équipe de sécurité d’une organisation bloque une extension de nom de fichier par le biais des paramètres de stratégie anti-programme malveillant. Ces valeurs apparaissent maintenant dans les détails du courrier électronique pour vous aider à effectuer des recherches. Les équipes de secopss peuvent également utiliser la fonctionnalité de filtrage enrichi pour filtrer les extensions de fichiers bloquées.

[![Substitutions système dans l’Explorateur](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Le système remplace la grille dans l’Explorateur](../../media/System_Overrides_Grid.png)

### <a name="improvements-for-the-url-and-clicks-experience"></a>Améliorations pour l’expérience de l’URL et des clics

Les améliorations sont les suivantes :

- Afficher l’URL sur laquelle l’utilisateur a cliqué complète (y compris les paramètres de requête qui font partie de l’URL) dans la section **clics** de la fenêtre mobile d’URL. Actuellement, le domaine d’URL et le chemin d’accès apparaissent dans la barre de titre. Nous étendons ces informations pour afficher l’URL complète.

- Correctifs parmi les filtres d’URL (*URL* et *domaine d’URL* / *domaine d’URL et chemin d’accès*) : les mises à jour affectent la recherche de messages contenant une URL/cliquez sur verdict. Nous avons activé la prise en charge des recherches agnostiques par le protocole, afin que vous puissiez rechercher une URL sans utiliser `http` . Par défaut, la recherche d’URL est mappée sur http, sauf si une autre valeur est explicitement spécifiée. Par exemple :

   -  Recherchez avec et sans le `http://` préfixe dans les champs **URL**, **domaine** d’URL et **domaine d’URL et filtre de chemin d’accès** . Les recherches doivent afficher les mêmes résultats.

   -  Recherchez le `https://` préfixe dans **URL**. Si aucune valeur n’est spécifiée, le `http://` préfixe est supposé.

   - `/` est ignoré au début et à la fin des champs chemin de l' **URL**, **domaine** de l’URL, domaine de l’URL **et chemin d’accès** . `/` à la fin du champ **URL** est ignoré.

### <a name="phish-confidence-level"></a>Niveau de confiance d’hameçonnage

Le niveau de confiance d’hameçonnage permet d’identifier le degré de confiance avec lequel un courrier électronique a été catégorisé comme « hameçon ». Les deux valeurs possibles sont *High* et *normal*. Au cours des étapes initiales, ce filtre n’est disponible que dans la vue de hameçonnage de l’Explorateur de menaces.

[![Niveau de confiance d’hameçonnage dans l’Explorateur](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>Le signal d’URL ZAP

Le signal d’URL ZAP est généralement utilisé pour les scénarios d’alerte de hameçonnage dans la mesure où un e-mail a été identifié comme hameçonnage et supprimé après la remise. Ce signal connecte l’alerte avec les résultats correspondants dans l’Explorateur. Il s’agit de l’une des IOCs de l’alerte.

Pour améliorer le processus de recherche, nous avons mis à jour l’Explorateur de menaces et les détections en temps réel pour rendre l’expérience de la chasse plus cohérente. Les modifications sont décrites ici :

- [Améliorations des fuseaux horaires](#timezone-improvements)
- [Mise à jour dans le processus d’actualisation](#update-in-the-refresh-process)
- [Descente de graphique à ajouter aux filtres](#chart-drilldown-to-add-to-filters)
- [Mises à jour des informations sur les produits](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Filtrer par balise utilisateur

Vous pouvez désormais trier et filtrer les balises d’utilisateur système ou personnalisé pour saisir rapidement l’étendue des menaces. Pour en savoir plus, consultez la rubrique [User Tags](user-tags.md).

> [!IMPORTANT]
> Le filtrage et le tri par les balises utilisateur sont actuellement en préversion publique. Cette fonctionnalité peut être modifiée de manière significative avant d’être publiée dans un commerce. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies à son propos.

![Colonne Tags dans l’Explorateur](../../media/threat-explorer-tags.png)

### <a name="timezone-improvements"></a>Améliorations des fuseaux horaires

Vous verrez le fuseau horaire pour les enregistrements de courrier électronique dans le portail, ainsi que pour les données exportées. Elle sera visible sur les expériences telles que le quadrillage du courrier, la fenêtre de détails, la chronologie du courrier électronique et les E-mails similaires, de sorte que le fuseau horaire du jeu de résultats soit clair.

> [!div class="mx-imgBorder"]
> ![Afficher le fuseau horaire dans l’Explorateur](../../media/TimezoneImprovements.png)

### <a name="update-in-the-refresh-process"></a>Mise à jour dans le processus d’actualisation

Certains utilisateurs ont mis en avant la confusion avec l’actualisation automatique (par exemple, dès que vous modifiez la date, la page est actualisée) et l’actualisation manuelle (pour les autres filtres). De même, la suppression des filtres entraîne l’actualisation automatique. La modification des filtres lors de la modification de la requête peut entraîner des expériences de recherche incohérentes. Pour résoudre ces problèmes, nous passons à un mécanisme de filtrage manuel.

Du point de vue de l’expérience, l’utilisateur peut appliquer et supprimer la plage de filtres différente (à partir du jeu de filtres et de la date), puis sélectionner le bouton Actualiser pour filtrer les résultats après qu’ils ont défini la requête. Le bouton actualiser est également mis en évidence à l’écran. Nous avons également mis à jour les info-bulles associées et la documentation du produit.

> [!div class="mx-imgBorder"]
> ![Sélectionnez Actualiser pour filtrer les résultats](../../media/ManualRefresh.png)

### <a name="chart-drilldown-to-add-to-filters"></a>Descente de graphique à ajouter aux filtres

Vous pouvez désormais graphiquer les valeurs de légende pour les ajouter en tant que filtres. Sélectionnez le bouton **Actualiser** pour filtrer les résultats.

> [!div class="mx-imgBorder"]
> ![Explorer les graphiques pour filtrer](../../media/ChartDrilldown.png)

### <a name="in-product-information-updates"></a>Mises à jour des informations dans le produit

Des informations supplémentaires sont désormais disponibles dans le produit, telles que le nombre total de résultats de recherche dans la grille (voir ci-dessous). Nous avons amélioré les étiquettes, les messages d’erreur et les info-bulles pour fournir plus d’informations sur les filtres, l’expérience de recherche et le jeu de résultats.

> [!div class="mx-imgBorder"]
> ![Afficher les informations sur le produit](../../media/ProductInfo.png)

## <a name="extended-capabilities-in-threat-explorer"></a>Fonctionnalités étendues dans l’Explorateur de menaces

### <a name="top-targeted-users"></a>Principaux utilisateurs ciblés

Nous exposez aujourd’hui la liste des utilisateurs ciblés dans la vue des programmes malveillants pour les messages électroniques, dans la section **Top des programmes malveillants** . Nous allons également développer cette vue dans les affichages du hameçonnage et de tous les messages électroniques. Vous pourrez voir les cinq premiers utilisateurs ciblés, ainsi que le nombre de tentatives pour chaque utilisateur pour la vue correspondante. Par exemple, pour la vue hameçon, vous verrez le nombre de tentatives de hameçonnage.

Vous pourrez exporter la liste des utilisateurs ciblés, jusqu’à une limite de 3 000, ainsi que le nombre de tentatives d’analyse hors ligne pour chaque affichage de courrier électronique. En outre, la sélection du nombre de tentatives (par exemple, 13 tentatives dans l’image ci-dessous) ouvre une vue filtrée dans l’Explorateur de menaces, de sorte que vous puissiez voir plus de détails sur les messages électroniques et les menaces pour cet utilisateur.

> [!div class="mx-imgBorder"]
> ![Principaux utilisateurs ciblés](../../media/Top_Targeted_Users.png)

### <a name="exchange-transport-rules"></a>Règles de transport Exchange

Dans le cadre de l’enrichissement des données, vous pouvez voir toutes les différentes règles de transport Exchange (ETR) qui ont été appliquées à un message. Ces informations seront disponibles dans l’affichage grille du courrier électronique. Pour l’afficher, sélectionnez **options de colonne** dans la grille, puis **Ajouter une règle de transport Exchange** à partir des options de colonne. Il sera également visible sur la fenêtre d’affichage des **Détails** dans le message électronique.

Vous pourrez voir le GUID et le nom des règles de transport qui ont été appliquées au message. Vous pourrez rechercher les messages à l’aide du nom de la règle de transport. Il s’agit d’une recherche « Contains », ce qui signifie que vous pouvez également effectuer des recherches partielles.

#### <a name="important-note"></a>Remarque importante :

La fonction de recherche et de nom ETR dépend du rôle spécifique qui vous a été attribué. Vous devez disposer de l’un des rôles/autorisations suivants pour afficher les noms de ETR et la recherche. Si vous n’avez pas de ces rôles qui vous sont attribués, vous ne pouvez pas voir les noms des règles de transport ou Rechercher des messages à l’aide de noms ETR. Toutefois, vous pouvez voir les informations d’étiquette et de GUID ETR dans les détails du message électronique. Les autres expériences d’affichage des enregistrements dans les grilles de courrier, les lances de messagerie, les filtres et les exportations ne sont pas affectées.

- EXO uniquement-protection contre la perte de données : All
- EXO uniquement-O365SupportViewConfig : All
- Microsoft Azure Active Directory ou EXO-administrateur de la sécurité : tous
- AAD ou EXO-lecteur de sécurité : tous
- EXO uniquement : toutes les règles de transport
- EXO, configuration View-Only : All

Dans la grille du courrier, dans les détails et dans le fichier CSV exporté, le ETR est présenté avec un nom/GUID, comme indiqué ci-dessous.

> [!div class="mx-imgBorder"]
> ![Règles de transport Exchange](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>Connecteurs entrants

Les connecteurs sont une collection d’instructions qui personnalisent le flux de votre courrier vers et depuis votre organisation Microsoft 365 ou Office 365. Elles vous permettent d’appliquer des restrictions de sécurité ou des contrôles. Dans l’Explorateur de menaces, vous pouvez désormais afficher les connecteurs associés à un courrier électronique et Rechercher des courriers électroniques à l’aide de noms de connecteur.

La recherche de connecteurs est « Contains », ce qui signifie que les recherches par Mots-clés partielles doivent également fonctionner. Dans l’affichage de grille principal, le menu volant détails et le fichier CSV exporté, les connecteurs sont affichés dans le format de nom/GUID, comme indiqué ci-dessous :

> [!div class="mx-imgBorder"]
> ![Détails du connecteur](../../media/Connector_Details.png)

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nouvelles fonctionnalités de l’Explorateur de menaces et des détections en temps réel

Trois nouvelles fonctionnalités sont disponibles dans l’Explorateur de menaces et les détections en temps réel :

- [Aperçu de l’en-tête de message et téléchargement du corps du courrier électronique](#preview-email-header-and-download-email-body)
- [Chronologie du courrier électronique](#email-timeline)
- [Exporter l’URL cliquez sur données](#export-url-click-data)

Ces nouvelles fonctionnalités sont décrites ci-dessous.

### <a name="preview-email-header-and-download-email-body"></a>Aperçu de l’en-tête de message et téléchargement du corps du courrier électronique

Vous pouvez désormais afficher un aperçu d’un en-tête de message et télécharger le corps de l’e-mail dans les administrateurs de l’Explorateur de menaces pour analyser les en-têtes/messages électroniques téléchargés contre les menaces. Étant donné que le téléchargement de messages électroniques peut compromettre l’exposition des informations, ce processus est contrôlé par le contrôle d’accès basé sur un rôle (RBAC). Un nouveau rôle, *Aperçu*, doit être ajouté à un autre groupe de rôles (tel que les opérations de sécurité ou administrateur de sécurité) pour accorder la possibilité de télécharger des messages et des en-têtes d’aperçu dans la vue tous les messages électroniques.

L’Explorateur et les détections en temps réel obtiendront également de nouveaux champs qui fournissent une image plus complète de l’emplacement de vos messages électroniques. Ces modifications facilitent la chasse aux opérations de sécurité. Toutefois, le résultat principal est que vous pouvez connaître l’emplacement des messages électroniques problématiques en un clin d’œil.

Comment cela est-il fait ? L’état de remise est désormais divisé en deux colonnes :

- **Action de remise** : état du courrier électronique.
- **Emplacement de remise** : emplacement auquel le courrier électronique a été acheminé.

L' *action de remise* est l’action entreprise sur un courrier électronique en raison de stratégies ou de détections existantes. Voici les actions possibles pour un e-mail :

|Cmds|Courrier indésirable|Blocked|Été|
|---|---|---|---|
|Le courrier électronique a été remis dans la boîte de réception ou dans le dossier d’un utilisateur, et l’utilisateur peut y accéder.|Le courrier électronique a été envoyé au dossier de courrier indésirable ou supprimé de l’utilisateur, et l’utilisateur peut y accéder.|Messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés. Ces messages sont inaccessibles à l’utilisateur.|Le courrier électronique a des pièces jointes malveillantes remplacées par des fichiers. txt qui indiquent que la pièce jointe était malveillante.|

Voici ce que l’utilisateur peut et ne peut pas voir :

|Accessible aux utilisateurs finaux|Inaccessible aux utilisateurs finaux|
|---|---|
|Cmds|Blocked|
|Courrier indésirable|Été|

**Emplacement de remise** : affiche les résultats des stratégies et des détections qui exécutent une post-remise. Il est lié à **_Delivery action_* _. Voici les valeurs possibles :

- _Inbox ou dossier * : le courrier électronique se trouve dans la boîte de réception ou dans un dossier (en fonction de vos règles de messagerie électronique).
- *Local ou externe*: la boîte aux lettres n’existe pas sur le Cloud mais est en local.
- *Dossier de courrier indésirable*: le courrier électronique se trouve dans le dossier de courrier indésirable d’un utilisateur.
- *Dossier éléments supprimés*: le message électronique dans le dossier éléments supprimés d’un utilisateur.
- *Quarantaine*: le courrier électronique est en quarantaine et non dans la boîte aux lettres d’un utilisateur.
- *Échec*: la messagerie n’a pas pu atteindre la boîte aux lettres.
- *Ignoré*: le courrier électronique a été perdu quelque part dans le flux de messagerie.

### <a name="email-timeline"></a>Chronologie du courrier électronique

La **chronologie par courrier électronique** est une nouvelle fonctionnalité d’explorateur qui améliore l’expérience de chasse pour les administrateurs. Il réduit le temps passé à vérifier différents emplacements pour essayer de comprendre l’événement. Lorsque plusieurs événements se produisent ou se referment en même temps lorsqu’un courrier électronique arrive, ces événements sont affichés dans un affichage chronologie. Certains événements qui se produisent lors de la livraison de votre courrier électronique sont capturés dans la colonne **Special action** . Les administrateurs peuvent combiner des informations de la chronologie avec l’action spéciale effectuée lors de la post-livraison du courrier afin de mieux comprendre le fonctionnement de leurs stratégies, où le courrier a été finalement routé et, dans certains cas, ce que l’évaluation finale était.

Pour plus d’informations, consultez la rubrique [enquêter et corriger les messages électroniques malveillants remis dans Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>Exporter l’URL cliquez sur données

Vous pouvez désormais exporter des rapports pour les clics d’URL vers Microsoft Excel pour afficher leur **ID de message réseau** et **cliquer sur verdict**, ce qui permet d’expliquer où votre URL a généré le trafic. Voici comment cela fonctionne : dans gestion des menaces sur la barre de lancement rapide Office 365, suivez la chaîne suivante :

**Explorateur** \> **Afficher le hameçonnage** \> **Clique sur** \> URL **principales** ou **URL** principales \> Sélectionnez un enregistrement pour ouvrir le menu volant d’URL.

Lorsque vous sélectionnez une URL dans la liste, un nouveau bouton **Exporter** est affiché dans le panneau de volant. Utilisez ce bouton pour déplacer des données vers une feuille de calcul Excel pour faciliter la création de rapports.

Suivez ce chemin d’accès pour accéder au même emplacement dans le rapport de détections en temps réel :

**Explorateur** \> Détections en temps **réel** \> **Afficher le hameçonnage** \> **URL** \> **URL principales** ou **clics en haut** \> Sélectionnez un enregistrement pour ouvrir le menu volant d’URL \> Naviguez jusqu’à l’onglet **clics** .

> [!TIP]
> L’ID de message réseau mappe le clic retour à des messages spécifiques lorsque vous recherchez des ID par le biais de l’Explorateur ou des outils tiers associés. De telles recherches identifient les messages électroniques associés à un résultat de clic. L’ID de message réseau corrélé permet une analyse plus rapide et plus puissante.

> [!div class="mx-imgBorder"]
> ![Clique sur l’onglet dans l’Explorateur](../../media/tp_ExportClickResultAndNetworkID.png)

## <a name="see-malware-detected-in-email-by-technology"></a>Voir programmes malveillants détectés dans le courrier électronique par technologie

Supposons que vous voulez voir les programmes malveillants détectés dans les messages triés par la technologie Microsoft 365. Pour ce faire, utilisez l’affichage [courrier > programmes malveillants](threat-explorer-views.md#email--malware) de l’Explorateur (ou des détections en temps réel).

1. Dans le centre de sécurité & conformité ( <https://protection.office.com> ), sélectionnez Explorateur de **gestion des menaces** \>  (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le menu **affichage** , choisissez  \> **programmes malveillants** de messagerie.

   > [!div class="mx-imgBorder"]
   > ![Menu Affichage de l’Explorateur](../../media/ExplorerViewEmailMalwareMenu.png)

3. Cliquez sur **expéditeur**, puis choisissez technologie de détection de **base** \> .

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

   > [!div class="mx-imgBorder"]
   > ![Technologies de détection des programmes malveillants](../../media/ExplorerEmailMalwareDetectionTech.png)

4. Choisissez une option. Ensuite, cliquez sur le bouton **Actualiser** pour appliquer ce filtre.

   > [!div class="mx-imgBorder"]
   > ![Technologie de détection sélectionnée](../../media/ExplorerEmailMalwareDetectionTechATP.png)

Le rapport est actualisé pour afficher les résultats que les programmes malveillants ont détectés dans les messages électroniques à l’aide de l’option de technologie que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus poussée.

## <a name="view-phishing-url-and-click-verdict-data"></a>Afficher l’URL d’hameçonnage et cliquez sur données de verdict

Supposons que vous vouliez voir les tentatives de hameçonnage via des URL dans des e-mails, y compris une liste des URL qui ont été autorisées, bloquées et remplacées. Pour identifier les URL sur lesquelles l’utilisateur a cliqué, les [liens fiables](atp-safe-links.md) doivent être configurés. Assurez-vous de configurer des [stratégies de liens fiables](set-up-atp-safe-links-policies.md) pour la protection du temps de clic et la journalisation des verdicts de clic par les liens fiables.

Pour passer en revue les URL de hameçonnage dans les messages et les clics sur les URL dans les messages hameçons, utilisez l’affichage [  >  **hameçonnage** **par courrier électronique**](threat-explorer-views.md#email--phish) de l’Explorateur ou des détections en temps réel.

1. Dans le centre de sécurité & conformité ( <https://protection.office.com> ), sélectionnez Explorateur de **gestion des menaces** \>  (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le menu **affichage** , choisissez **courrier** \> **hameçon**.

   > [!div class="mx-imgBorder"]
   > ![Menu Affichage pour l’Explorateur dans le contexte de hameçonnage](../../media/ExplorerViewEmailPhishMenu.png)

3. Cliquez sur **expéditeur**, puis sur **URL** , puis \> **cliquez sur verdict**.

4. Sélectionnez une ou plusieurs options, telles que **bloquées** et **bloquer le remplacement**, puis cliquez sur le bouton **Actualiser** sur la même ligne que les options pour appliquer le filtre. (Ne pas actualiser la fenêtre de votre navigateur.)

   > [!div class="mx-imgBorder"]
   > ![URL et cliquez sur verdicts](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

   Le rapport est actualisé pour afficher deux tables d’URL différentes sous l’onglet URL sous le rapport :

   - Les **URL principales** sont les URL dans les messages que vous avez filtrés et l’action de remise de courrier est comptée pour chaque URL. Dans l’affichage courrier de hameçonnage, cette liste contient généralement des URL légitimes. Les agresseurs incluent une combinaison d’URL correctes et incorrectes dans leurs messages pour essayer de les récupérer, mais ils rendent les liens malveillants plus intéressants. Le tableau des URL est trié par nombre total d’e-mails, mais cette colonne est masquée pour simplifier l’affichage.

   - Les **clics en haut** sont les liens approuvés, URL encapsulées, triées par nombre de clics. Cette colonne n’est pas non plus affichée, pour simplifier l’affichage. Nombre total par colonne indique le nombre de liens approuvés cliquez sur nombre de verdicts pour chaque URL sur laquelle vous avez cliqué. Dans l’affichage e-mail de hameçonnage, il s’agit généralement d’URL suspectes ou malveillantes. Toutefois, l’affichage peut inclure des URL qui ne sont pas des menaces, mais qui se trouvent dans des messages hameçons. Les clics d’URL sur les liens non justifiés ne sont pas affichés ici.

   Les deux tableaux d’URL affichent les URL les plus fréquentes dans les messages électroniques de hameçonnage par action et emplacement de remise. Les tableaux indiquent que des clics d’URL ont été bloqués ou visités malgré un avertissement, afin que vous puissiez voir quels liens incorrects potentiels ont été présentés aux utilisateurs et que l’utilisateur a cliqué dessus. À partir de là, vous pouvez effectuer une analyse plus poussée. Par exemple, sous le graphique, vous pouvez voir les URL principales dans les messages électroniques bloqués dans l’environnement de votre organisation.

   > [!div class="mx-imgBorder"]
   > ![URL de l’Explorateur bloquées](../../media/ExplorerPhishClickVerdictURLs.png)

   Sélectionnez une URL pour afficher des informations plus détaillées.

   > [!NOTE]
   > Dans la boîte de dialogue de menu déroulante d’URL, le filtrage des messages électroniques est supprimé pour afficher l’affichage complet de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques que vous vous intéressez dans l’Explorateur, de trouver des URL spécifiques qui constituent des menaces potentielles, et de mieux comprendre l’exposition de l’URL dans votre environnement (via la boîte de dialogue détails de l’URL) sans avoir à ajouter de filtres d’URL à l’affichage Explorateur lui-même.

### <a name="interpretation-of-click-verdicts"></a>Interprétation des verdicts de clic

Dans les lances de messagerie électronique ou d’URL, les clics en tête de message et dans nos expériences de filtrage, vous verrez des valeurs de verdict de clic différentes :

- **Aucun :** Impossible de capturer le verdict de l’URL. L’utilisateur peut avoir cliqué dans l’URL.
- **Autorisé :** L’utilisateur a été autorisé à accéder à l’URL.
- **Bloqué :** L’utilisateur n’a pas pu accéder à l’URL.
- **Verdict en attente :** L’utilisateur s’est présenté avec la page en attente de détonation.
- **Bloqué remplacé :** L’utilisateur n’a pas pu naviguer directement vers l’URL. Mais l’utilisateur overrode le bloc pour accéder à l’URL.
- **Verdict en attente ignoré :** L’utilisateur s’est affiché avec la page de détonation. Mais l’utilisateur overrode le message pour accéder à l’URL.
- **Erreur :** L’utilisateur s’est affiché avec la page d’erreur, ou une erreur s’est produite lors de la capture du verdict.
- **Échec :** Une exception inconnue s’est produite lors de la capture du verdict. L’utilisateur peut avoir cliqué dans l’URL.

## <a name="review-email-messages-reported-by-users"></a>Examiner les messages électroniques signalés par les utilisateurs

Supposons que vous voulez afficher les messages électroniques que les utilisateurs de votre organisation ont signalés comme *légitimes*, *non légitimes* ou le *hameçonnage* via le [complément de message de rapport pour Outlook et Outlook sur le Web](enable-the-report-message-add-in.md). Pour les afficher, utilisez la vue des [   >  **envois** de courrier](threat-explorer-views.md#email--submissions) de l’Explorateur (ou des détections en temps réel).

1. Dans le centre de sécurité & conformité ( <https://protection.office.com> ), sélectionnez Explorateur de **gestion des menaces** \>  (ou **détections en temps réel**). (Cet exemple utilise Explorer.)

2. Dans le menu **affichage** , choisissez  \> **envois** de courrier électronique.

   > [!div class="mx-imgBorder"]
   > ![Menu Affichage pour l’Explorateur des courriers électroniques](../../media/explorer-view-menu-email-user-reported.png)

3. Cliquez sur **expéditeur**, puis sur type de rapport de **base** \> .

4. Sélectionnez une option, par exemple **hameçonnage**, puis le bouton **Actualiser** .

   > [!div class="mx-imgBorder"]
   > ![Hameçonnage signalé par l’utilisateur](../../media/EmailUserReportedReportType.png)

Le rapport est actualisé pour afficher les données relatives aux messages électroniques que les personnes de votre organisation ont signalées comme tentatives de hameçonnage. Vous pouvez utiliser ces informations pour effectuer une analyse plus poussée et, si nécessaire, ajuster vos [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Démarrer une enquête et une réponse automatisées

> [!NOTE]
> Les fonctionnalités d’analyse et de réponse automatisées sont disponibles dans *Microsoft Defender pour office 365 plan 2* et *Office 365 E5*.

L’analyse [et la réponse automatisées](automated-investigation-response-office.md) peuvent enregistrer le temps et les efforts de l’équipe des opérations de sécurité pour examiner et limiter les cyberattaques. En plus de configurer des alertes pouvant déclencher un manuel de sécurité, vous pouvez démarrer un processus d’enquête et de réponse automatisés à partir d’une vue dans l’Explorateur. Pour plus d’informations, voir [example : A Security Administrator déclenche une enquête à partir de l’Explorateur](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Autres méthodes d’utilisation de l’Explorateur et des détections en temps réel

Outre les scénarios décrits dans cet article, vous disposez de nombreuses autres options de création de rapports dans l’Explorateur (ou des détections en temps réel). Consultez les articles suivants :

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Affichage de fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft teams](malicious-files-detected-in-spo-odb-or-teams.md)
- [Obtenir une vue d’ensemble des affichages dans l’Explorateur de menaces (et des détections en temps réel)](threat-explorer-views.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

[Microsoft Defender pour Office 365](office-365-atp.md) doit utiliser l’Explorateur ou les détections en temps réel.

- L’Explorateur est inclus dans Defender pour Office 365 plan 2.
- Le rapport de détections en temps réel est inclus dans Defender pour Office 365 plan 1.
- Prévoyez d’attribuer des licences pour tous les utilisateurs qui doivent être protégés par Defender pour Office 365. L’Explorateur et les détections en temps réel affichent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser l’Explorateur ou les détections en temps réel, vous devez disposer des autorisations appropriées, telles que celles accordées à un administrateur de sécurité ou à un lecteur de sécurité.

- Pour le centre de sécurité & conformité, vous devez disposer de l’un des rôles suivants :

  - Gestion de l’organisation
  - Administrateur de la sécurité (qui peut être affecté dans le centre d’administration Azure Active Directory ( <https://aad.portal.azure.com> )
  - Lecteur de sécurité

- Pour Exchange Online, vous devez disposer de l’un des rôles suivants, qui est affecté dans le centre d’administration Exchange ( <https://admin.protection.outlook.com/ecp/> ) ou [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell):

  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le centre de conformité et de sécurité](permissions-in-the-security-and-compliance-center.md)
- [Autorisations des fonctionnalités dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Différences entre l’Explorateur de menaces et les détections en temps réel

- Le rapport de *détections en temps réel* est disponible dans Defender pour Office 365 plan 1. L' *Explorateur de menaces* est disponible dans Defender pour Office 365 plan 2.
- Le rapport des détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais il fournit également des informations supplémentaires pour une attaque donnée.
- Une vue *tout le courrier* est disponible dans l’Explorateur de menaces, mais pas dans le rapport de détections en temps réel.
- D’autres fonctionnalités de filtrage et les actions disponibles sont incluses dans l’Explorateur de menaces. Pour plus d’informations, reportez-vous à [Microsoft Defender for office 365 Service Description : Feature Availability for Defender for office 365 plans](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).
