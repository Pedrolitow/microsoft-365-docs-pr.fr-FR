---
title: Détections en temps réel et de l’Explorateur de menaces
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Utilisez les détections De l’Explorateur et en temps réel dans Microsoft 365 centre de sécurité pour examiner et répondre efficacement aux menaces.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4a9a364f82b7f7836c2f0177dfbde80171b9c36f
ms.sourcegitcommit: cd55fe6abe25b1e4f5fbe8295d3a99aebd97ce66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2021
ms.locfileid: "53083223"
---
# <a name="threat-explorer-and-real-time-detections"></a>Détections en temps réel et de l’Explorateur de menaces

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si votre organisation dispose de Microsoft Defender pour [Office 365](defender-for-office-365.md)et que vous  disposez des autorisations nécessaires, vous disposez de détections Explorer ou En temps réel (anciennement rapports en temps réel — découvrez les  [nouveautés](#required-licenses-and-permissions)!).  [](#new-features-in-threat-explorer-and-real-time-detections) Dans le Centre de sécurité & conformité, sélectionnez Gestion des menaces, puis sélectionnez **Explorer** _ou_ **Détections en temps réel.**

<br>

****

|Avec Microsoft Defender pour Office 365 Plan 2, vous pouvez voir :|Avec Microsoft Defender pour Office 365 Plan 1, vous pouvez voir :|
|---|---|
|![Explorateur de menaces](../../media/threatmgmt-explorer.png)|![Détections en temps réel](../../media/threatmgmt-realtimedetections.png)|
|

Les détections d’explorateur ou en temps réel aident votre équipe des opérations de sécurité à examiner les menaces et à y répondre efficacement. Le rapport ressemble à l’image suivante :

![Accès à l’Explorateur de gestion des \> menaces](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Avec ce rapport, vous pouvez :

- [Consulter les programmes malveillants détectés par les fonctionnalités Microsoft 365 sécurité](#see-malware-detected-in-email-by-technology)
- [Afficher l’URL de hameçonnage et cliquer sur les données de verdict](#view-phishing-url-and-click-verdict-data)
- [Démarrer un processus d’examen et de](#start-automated-investigation-and-response) réponse automatisé à partir d’un affichage dans l’Explorateur (Defender pour Office 365 Plan 2 uniquement)
- [Examiner les e-mails malveillants, et bien plus encore](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Améliorations de l’expérience de recherche de menaces

### <a name="introduction-of-alert-id-for-mdo-alerts-within-explorerreal-time-detections-preview"></a>Introduction de l’ID d’alerte pour les alertes MDO dans l’Explorateur/Détections en temps réel (Aperçu)

Aujourd’hui, si vous naviguez d’une alerte vers l’Explorateur de menaces, il ouvre une vue filtrée dans l’Explorateur, avec l’affichage filtré par l’ID de stratégie d’alerte (ID de stratégie étant un identificateur unique pour une stratégie d’alerte).
Nous rendons cette intégration plus pertinente en introduisant l’ID d’alerte (voir un exemple d’ID d’alerte ci-dessous) dans l’Explorateur de menaces et les détections en temps réel afin que vous voyez les messages qui sont pertinents pour l’alerte spécifique, ainsi qu’un nombre de messages électroniques. Vous pourrez également voir si un message faisait partie d’une alerte, ainsi que naviguer de ce message vers l’alerte spécifique.

L’ID d’alerte est disponible dans l’URL lorsque vous affichez une alerte individuelle . exemple `https://protection.office.com/viewalerts?id=372c9b5b-a6c3-5847-fa00-08d8abb04ef1` :

> [!div class="mx-imgBorder"]
> ![Filtrage de l’ID d’alerte](../../media/AlertID-Filter.png)

> [!div class="mx-imgBorder"]
> ![ID d’alerte dans le volant de détails](../../media/AlertID-DetailsFlyout.png)

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days-preview"></a>Extension de la limite de rétention et de recherche des données de l’Explorateur (et des détections en temps réel) pour les clients d’essai de 7 à 30 jours (prévisualisation)

Dans le cadre de cette modification, vous pourrez rechercher et filtrer des données de courrier électronique sur 30 jours (une augmentation par rapport aux 7 jours précédents) dans l’Explorateur de menaces/Détections en temps réel pour Defender pour les clients d’essai Office P1 et P2.
Cela n’a aucun impact sur les clients de production pour les clients P1 et P2/E5, qui disposent déjà des fonctionnalités de rétention et de recherche de données de 30 jours.

### <a name="updated-limits-for-export-of-records-for-threat-explorer-preview"></a>Limites mises à jour pour l’exportation des enregistrements pour l’Explorateur de menaces (aperçu)

Dans le cadre de cette mise à jour, le nombre de lignes pour les enregistrements de courrier électronique qui peuvent être exportés à partir de l’Explorateur de menaces est passé de 9990 à 200 000. Le jeu de colonnes qui peut être exporté actuellement reste le même, mais le nombre de lignes augmente par rapport à la limite actuelle.

### <a name="tags-in-threat-explorer"></a>Balises dans l’Explorateur de menaces

> [!NOTE]
> La fonctionnalité de balises utilisateur est en prévisualisation, n’est pas disponible pour tout le monde et est sujette à modification. Pour plus d’informations sur la planification de publication, consultez la feuille de Microsoft 365 de publication.

Les balises utilisateur identifient des groupes spécifiques d’utilisateurs dans Microsoft Defender Office 365. Pour plus d’informations sur les balises, notamment la gestion des licences et la configuration, voir [Balises utilisateur.](user-tags.md)

Dans l’Explorateur de menaces, vous pouvez voir les informations sur les balises utilisateur dans les expériences suivantes.

#### <a name="email-grid-view"></a>Affichage Grille du courrier électronique

La **colonne Balises** de la grille de courrier contient toutes les balises qui ont été appliquées aux boîtes aux lettres de l’expéditeur ou du destinataire. Par défaut, les balises système telles que les comptes de priorité sont affichées en premier.

> [!div class="mx-imgBorder"]
> ![Filtrer les balises dans l’affichage Grille du courrier électronique](../../media/tags-grid.png)

#### <a name="filtering"></a>Filtrage

Vous pouvez utiliser des balises comme filtre. Recherchez uniquement les comptes prioritaires ou des scénarios de balises utilisateur spécifiques. Vous pouvez également exclure les résultats qui ont certaines balises. Combinez cette fonctionnalité avec d’autres filtres pour affiner votre portée d’examen.

[![Balises de filtre](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> ![Balises non filtrées](../../media/tags-filter-not.png)

#### <a name="email-detail-flyout"></a>Flyout des détails des e-mails

Pour afficher les balises individuelles de l’expéditeur et du destinataire, sélectionnez l’objet pour ouvrir le flyout des détails du message. Sous **l’onglet** Résumé, les balises de l’expéditeur et du destinataire sont affichées séparément, si elles sont présentes pour un e-mail.
Les informations sur les balises individuelles pour l’expéditeur et le destinataire s’étendent également aux données CSV exportées, où vous pouvez voir ces détails dans deux colonnes distinctes.

> [!div class="mx-imgBorder"]
> ![Balises de détails du courrier électronique](../../media/tags-flyout.png)

Les informations sur les balises sont également affichées dans le volant des clics d’URL. Pour l’afficher, consultez l’affichage Hameçonnage ou Tous les e-mails, puis l’onglet Url **ou Clics d’URL.**  Sélectionnez un volant d’URL individuel pour afficher des détails supplémentaires sur les clics pour cette URL, y compris les balises associées à ce clic.

### <a name="updated-timeline-view"></a>Affichage de chronologie mis à jour

> [!div class="mx-imgBorder"]
> ![Balises d’URL](../../media/tags-urls.png)
>
Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Améliorations apportées à l’expérience de recherche de menaces (à venir)

### <a name="updated-threat-information-for-emails"></a>Informations sur les menaces mises à jour pour les e-mails

Nous nous sommes concentrés sur les améliorations de la plateforme et de la qualité des données afin d’améliorer la précision et la cohérence des données pour les enregistrements de courrier électronique. Les améliorations incluent la consolidation des informations de pré-remise et de post-remise, telles que les actions exécutées sur un e-mail dans le cadre du processus ZAP, dans un enregistrement unique. Des détails supplémentaires tels que le verdict du courrier indésirable, les menaces au niveau de l’entité (par exemple, l’URL malveillante) et les derniers emplacements de remise sont également inclus.

Après ces mises à jour, une seule entrée s’affiche pour chaque message, quels que soient les différents événements post-remise qui affectent le message. Les actions peuvent inclure ZAP, la correction manuelle (ce qui signifie une action de l’administrateur), la remise dynamique, etc.

Outre l’affichage des programmes malveillants et des menaces de hameçonnage, le verdict de courrier indésirable associé à un e-mail s’affiche. Dans l’e-mail, consultez toutes les menaces associées à l’e-mail, ainsi que les technologies de détection correspondantes. Un e-mail peut avoir zéro, une ou plusieurs menaces. Vous verrez les menaces actuelles dans la section **Détails** du volant de courrier électronique. Pour plusieurs menaces (telles que  les programmes malveillants et le hameçonnage), le champ technique de détection affiche le mappage de la détection des menaces, qui est la technologie de détection qui a identifié la menace.

L’ensemble des technologies de détection inclut désormais de nouvelles méthodes de détection, ainsi que des technologies de détection du courrier indésirable. Vous pouvez utiliser le même ensemble de technologies de détection pour filtrer les résultats dans les différents affichages de courrier électronique (programmes malveillants, hameçonnage, tous les e-mails).

> [!NOTE]
> L’analyse du verdict peut ne pas nécessairement être liée à des entités. Par exemple, un e-mail peut être classé comme hameçonnage ou courrier indésirable, mais aucune URL n’est marqué avec un verdict de hameçonnage/courrier indésirable. Cela est dû au fait que les filtres évaluent également le contenu et d’autres détails d’un e-mail avant d’attribuer un verdict.

#### <a name="threats-in-urls"></a>Menaces dans les URL

Vous pouvez maintenant voir la menace spécifique pour une URL sous l’onglet **Détails** du volant de courrier électronique. La menace peut être *un programme malveillant,* *un hameçonnage,* un *courrier indésirable* ou *aucun*.)

> [!div class="mx-imgBorder"]
> ![Menaces d’URL](../../media/URL_Threats.png)

### <a name="updated-timeline-view-upcoming"></a>Affichage chronologique mis à jour (à venir)

> [!div class="mx-imgBorder"]
> ![Affichage de chronologie mis à jour](../../media/Email_Timeline.png)

L’affichage Chronologie identifie tous les événements de remise et de post-remise. Il inclut des informations sur la menace identifiée à ce moment-là pour un sous-ensemble de ces événements. L’affichage Chronologie fournit également des informations sur toute action supplémentaire prise (par exemple, ZAP ou la correction manuelle), ainsi que le résultat de cette action. Les informations d’affichage de chronologie incluent :

- **Source :** Source de l’événement. Il peut s’y trouver en administrateur/système/utilisateur.
- **Événement :** Inclut les événements de niveau supérieur tels que la remise d’origine, la correction manuelle, ZAP, les soumissions et la remise dynamique.
- **Action :** Action spécifique qui a été prise dans le cadre de l’action ZAP ou de l’administrateur (par exemple, suppression possible).
- **Menaces :** Couvre les menaces (programme malveillant, hameçonnage, courrier indésirable) identifiées à ce moment-là.
- **Résultat/détails :** Plus d’informations sur le résultat de l’action, par exemple si elle a été effectuée dans le cadre de l’action ZAP/administrateur.

### <a name="original-and-latest-delivery-location"></a>Emplacement de remise d’origine et le plus récent

Actuellement, nous faisons surface de l’emplacement de remise dans la grille de courrier électronique et le volant du courrier électronique. Le **champ Emplacement de remise** est renommé Emplacement de remise **_d’origine_*_. Et nous introduisons un autre champ, _*_Emplacement de remise le plus récent_**.

**L’emplacement de remise d’origine** fournit plus d’informations sur l’endroit où un e-mail a été remis initialement. **L’emplacement de remise le** plus récent état où un e-mail a été envoyé après des actions système telles que *ZAP* ou des actions d’administrateur telles que Déplacer *vers les éléments supprimés*. L’emplacement de remise le plus récent est destiné à indiquer aux administrateurs le dernier emplacement connu après la remise du message ou toute action système/administrateur. Il n’inclut aucune action de l’utilisateur final dans le courrier électronique. Par exemple, si un utilisateur a supprimé un message ou déplacé le message vers l’archive/pst, l’emplacement de « remise » du message ne sera pas mis à jour. Toutefois, si une action du système a mis à jour l’emplacement (par exemple, ZAP et qu’un e-mail est mis en **quarantaine),** l’emplacement de remise le plus récent s’affiche comme « quarantaine ».

> [!div class="mx-imgBorder"]
> ![Emplacements de remise mis à jour](../../media/Updated_Delivery_Location.png)

> [!NOTE]
> Dans certains cas, l’emplacement **de** remise et l’action de **remise** peuvent s’afficher comme « inconnus » :
>
> - Vous pouvez  voir l’emplacement de  remise comme « remis » et l’emplacement de remise comme « inconnu » si le message a été remis, mais une règle de boîte de réception a déplacé le message vers un dossier par défaut (par exemple, Brouillon ou Archive) au lieu du dossier Boîte de réception ou Courrier indésirable.
>
> - **L’emplacement de remise** le plus récent peut être inconnu si une tentative d’action d’administrateur/système (telle que ZAP) a été tentée, mais que le message n’a pas été trouvé. En règle générale, l’action se produit après que l’utilisateur a déplacé ou supprimé le message. Dans ce cas, vérifiez la colonne **Résultat/Détails** dans l’affichage chronologie. Recherchez l’instruction « Message déplacé ou supprimé par l’utilisateur ».

> [!div class="mx-imgBorder"]
> ![Emplacements de remise pour la chronologie](../../media/Updated_Timeline_Delivery_Location.png)

### <a name="additional-actions"></a>Actions supplémentaires

*Des actions supplémentaires ont* été appliquées après la remise du courrier électronique. Elles peuvent inclure *zap* *,* correction manuelle (action entreprise par un administrateur telle que la suppression *possible),* remise dynamique et *retrait* (pour un e-mail détecté comme bon).

> [!NOTE]
> Dans le cadre des modifications en attente, la valeur « Supprimé par ZAP » actuellement mise en avant dans le filtre Action de remise va disparaître. Vous pouvez rechercher tous les e-mails avec la tentative ZAP via des **actions supplémentaires.**

> [!div class="mx-imgBorder"]
> ![Actions supplémentaires dans l’Explorateur](../../media/Additional_Actions.png)

### <a name="system-overrides"></a>Remplacements système

*Les substitutions système* vous permettent d’effectuer des exceptions à l’emplacement de remise prévu d’un message. Vous remplacez l’emplacement de remise fourni par le système, en fonction des menaces et autres détections identifiées par la pile de filtrage. Les substitutions système peuvent être définies par le biais d’une stratégie de client ou d’utilisateur pour remettre le message comme suggéré par la stratégie. Les remplacements peuvent identifier la remise involontaire de messages malveillants en raison de lacunes de configuration, telles qu’une stratégie d’expéditeur de Coffre trop large définie par un utilisateur. Ces valeurs de remplacement peuvent être :

- Autorisé par la stratégie utilisateur : un utilisateur crée des stratégies au niveau de la boîte aux lettres pour autoriser les domaines ou les expéditeurs.

- Bloqué par la stratégie utilisateur : un utilisateur crée des stratégies au niveau de la boîte de messagerie pour bloquer les domaines ou les expéditeurs.

- Autorisé par la stratégie d’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie Exchange (également appelées règles de transport) pour autoriser les expéditeurs et les domaines pour les utilisateurs de leur organisation. Il peut s’agit d’un ensemble d’utilisateurs ou de l’ensemble de l’organisation.

- Bloqué par la stratégie d’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie pour bloquer les expéditeurs, les domaines, les langues de message ou les adresses IPS sources pour les utilisateurs de leur organisation. Cela peut être appliqué à un ensemble d’utilisateurs ou à l’ensemble de l’organisation.

- Extension de fichier bloquée par la stratégie d’organisation : l’équipe de sécurité d’une organisation bloque une extension de nom de fichier via les paramètres de stratégie anti-programme malveillant. Ces valeurs s’affichent désormais dans les détails de l’e-mail pour faciliter les enquêtes. Les équipes Secops peuvent également utiliser la fonctionnalité de filtrage enrichi pour filtrer les extensions de fichier bloquées.

[![Remplacements système dans l’Explorateur](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> ![System Overrides Grid in Explorer](../../media/System_Overrides_Grid.png)

### <a name="improvements-for-the-url-and-clicks-experience"></a>Améliorations de l’URL et expérience de clics

Les améliorations sont les suivantes :

- Affichez l’URL sur le clic complet (y compris les paramètres de requête qui font partie de l’URL) dans la section **Clics** du volant d’URL. Actuellement, le domaine et le chemin d’accès de l’URL apparaissent dans la barre de titre. Nous étendons ces informations pour afficher l’URL complète.

- Correctifs entre les filtres d’URL *(URL* par rapport au domaine et au chemin d’accès de l’URL) : les mises à jour affectent la recherche de messages contenant un verdict URL/clic.   Nous avons activé la prise en charge des recherches non spécifiques au protocole, afin que vous pouvez rechercher une URL sans utiliser `http` . Par défaut, la recherche d’URL est m’indique http, sauf si une autre valeur est explicitement spécifiée. Par exemple :
  - Recherchez avec et sans le préfixe dans les champs de filtre URL, Domaine d’URL et Domaine `http://` **d’URL et** Chemin d’accès.   Les recherches doivent afficher les mêmes résultats.
  - Recherchez le `https://` préfixe dans **l’URL.** Lorsqu’aucune valeur n’est spécifiée, le `http://` préfixe est supposé.
  - `/`est ignoré au début et à la fin du chemin **d’URL,** du domaine **d’URL,** du domaine **d’URL et des champs de chemin d’accès.** `/` à la fin du champ **URL** est ignoré.

### <a name="phish-confidence-level"></a>Niveau de confiance du hameçonnage

Le niveau de confiance du hameçonnage permet d’identifier le degré de confiance avec lequel un e-mail a été classé comme « hameçonnage ». Les deux valeurs possibles sont *High et* *Normal*. Dans les étapes initiales, ce filtre sera disponible uniquement dans l’affichage Hameçonnage de l’Explorateur de menaces.

[![Niveau de confiance du hameçonnage dans l’Explorateur](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>Signal d’URL ZAP

Le signal d’URL ZAP est généralement utilisé pour les scénarios d’alerte de hameçonnage ZAP dans lequel un e-mail a été identifié comme hameçonnage et supprimé après la remise. Ce signal connecte l’alerte aux résultats correspondants dans l’Explorateur. Il s’agit de l’un des IOCs de l’alerte.

Pour améliorer le processus de repérage, nous avons mis à jour l’Explorateur de menaces et les détections en temps réel pour rendre l’expérience de repérage plus cohérente. Les modifications sont décrites ici :

- [Améliorations apportées au fuseau horaire](#timezone-improvements)
- [Mise à jour dans le processus d’actualisation](#update-in-the-refresh-process)
- [Chart drilldown to add to filters](#chart-drilldown-to-add-to-filters)
- [Dans les mises à jour des informations sur le produit](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Filtrer par balises utilisateur

Vous pouvez désormais trier et filtrer des balises utilisateur système ou personnalisées pour saisir rapidement l’étendue des menaces. Pour en savoir plus, consultez [balises utilisateur.](user-tags.md)

> [!IMPORTANT]
> Le filtrage et le tri par balises utilisateur sont actuellement en prévisualisation publique. Cette fonctionnalité peut être considérablement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, en ce qui concerne les informations fournies à son sujet.

> [!div class="mx-imgBorder"]
> ![Colonne Balises dans l’Explorateur](../../media/threat-explorer-tags.png)

### <a name="timezone-improvements"></a>Améliorations apportées au fuseau horaire

Vous verrez le fuseau horaire pour les enregistrements de courrier dans le portail, ainsi que pour les données exportées. Il sera visible entre les expériences telles que la grille de courrier électronique, le flyout détails, la chronologie des e-mails et les e-mails similaires, afin que le fuseau horaire du jeu de résultats soit clair.

> [!div class="mx-imgBorder"]
> ![Afficher le fuseau horaire dans l’Explorateur](../../media/TimezoneImprovements.png)

### <a name="update-in-the-refresh-process"></a>Mise à jour dans le processus d’actualisation

Certains utilisateurs ont commenté la confusion avec l’actualisation automatique (par exemple, dès que vous modifiez la date, la page est actualisée) et l’actualisation manuelle (pour d’autres filtres). De même, la suppression de filtres entraîne l’actualisation automatique. La modification des filtres lors de la modification de la requête peut entraîner des expériences de recherche incohérentes. Pour résoudre ces problèmes, nous allons passer à un mécanisme de filtrage manuel.

Du point de vue de l’expérience, l’utilisateur peut appliquer et supprimer la plage de filtres différente (du jeu de filtres et de la date) et sélectionner le bouton d’actualisation pour filtrer les résultats après avoir défini la requête. Le bouton Actualiser est désormais mis en avant à l’écran. Nous avons également mis à jour les informations d’outils associées et la documentation sur le produit.

> [!div class="mx-imgBorder"]
> ![Sélectionnez Actualiser pour filtrer les résultats](../../media/ManualRefresh.png)

### <a name="chart-drilldown-to-add-to-filters"></a>Chart drilldown to add to filters

Vous pouvez désormais graphiquer les valeurs de légende pour les ajouter en tant que filtres. Sélectionnez le **bouton** Actualiser pour filtrer les résultats.

> [!div class="mx-imgBorder"]
> ![Descendre dans les graphiques pour filtrer](../../media/ChartDrilldown.png)

### <a name="in-product-information-updates"></a>Mises à jour des informations sur le produit

Des détails supplémentaires sont désormais disponibles dans le produit, tels que le nombre total de résultats de recherche dans la grille (voir ci-dessous). Nous avons amélioré les étiquettes, les messages d’erreur et les info-bulles pour fournir plus d’informations sur les filtres, l’expérience de recherche et le jeu de résultats.

> [!div class="mx-imgBorder"]
> ![Afficher les informations dans le produit](../../media/ProductInfo.png)

## <a name="extended-capabilities-in-threat-explorer"></a>Fonctionnalités étendues dans l’Explorateur de menaces

### <a name="top-targeted-users"></a>Utilisateurs les plus ciblés

Aujourd’hui, nous exposons la liste des utilisateurs les plus ciblés dans l’affichage Programmes malveillants pour les e-mails, dans la section Familles de programmes malveillants **les plus ciblées.** Nous étendrons également cette vue dans les affichages Hameçonnage et Tous les messages électroniques. Vous pourrez voir les cinq premiers utilisateurs ciblés, ainsi que le nombre de tentatives pour chaque utilisateur pour l’affichage correspondant. Par exemple, pour l’affichage hameçonnage, vous verrez le nombre de tentatives d’hameçonnage.

Vous pourrez exporter la liste des utilisateurs ciblés, jusqu’à une limite de 3 000, ainsi que le nombre de tentatives d’analyse hors connexion pour chaque affichage de courrier électronique. En outre, la sélection du nombre de tentatives (par exemple, 13 tentatives dans l’image ci-dessous) ouvre une vue filtrée dans l’Explorateur de menaces, afin que vous pouvez voir plus de détails sur les messages électroniques et les menaces pour cet utilisateur.

> [!div class="mx-imgBorder"]
> ![Utilisateurs les plus ciblés](../../media/Top_Targeted_Users.png)

### <a name="exchange-transport-rules"></a>Exchange transport

Dans le cadre de l’enrichissement de données, vous pourrez voir toutes les différentes règles de transport Exchange qui ont été appliquées à un message. Ces informations seront disponibles dans l’affichage Grille de courrier électronique. Pour l’afficher, sélectionnez **Options** de colonne dans la grille, puis Exchange règle de **transport à** partir des options de colonne. Il sera également visible dans le volant **Détails** de l’e-mail.

Vous pourrez voir le GUID et le nom des règles de transport qui ont été appliquées au message. Vous pourrez rechercher les messages à l’aide du nom de la règle de transport. Il s’agit d’une recherche « Contient », ce qui signifie que vous pouvez également effectuer des recherches partielles.

> [!IMPORTANT]
> La recherche ETR et la disponibilité des noms dépendent du rôle spécifique qui vous est attribué. Vous devez avoir l’un des rôles/autorisations suivants pour afficher les noms ETR et la recherche. Si aucun de ces rôles ne vous est attribué, vous ne pouvez pas voir les noms des règles de transport ou rechercher des messages à l’aide de noms ETR. Toutefois, vous pouvez voir l’étiquette ETR et les informations guid dans les détails de l’e-mail. Les autres expériences d’affichage d’enregistrement dans les grilles de courrier électronique, les volants de courrier électronique, les filtres et l’exportation ne sont pas affectées.
>
> - EXO uniquement - Protection contre la perte de données : tous
> - EXO uniquement - O365SupportViewConfig : tous
> - Microsoft Azure Active Directory ou EXO - Administrateur de sécurité : tous
> - AAD ou EXO - Lecteur sécurité : tous
> - EXO uniquement - Règles de transport : tous
> - EXO uniquement - configuration View-Only : tous
>
> Dans la grille de courrier électronique, le volant Détails et le CSV exporté, les ETR sont présentés avec un nom/GUID, comme illustré ci-dessous.
>
> > [!div class="mx-imgBorder"]
> > ![Exchange Règles de transport](../../media/ETR_Details.png)

### <a name="inbound-connectors"></a>Connecteurs entrants

Les connecteurs sont un ensemble d’instructions qui personnalisent la façon dont vos messages électroniques circulent vers et depuis Microsoft 365 ou Office 365 organisation. Elles vous permettent d’appliquer des restrictions ou des contrôles de sécurité. Dans l’Explorateur de menaces, vous pouvez désormais afficher les connecteurs associés à un e-mail et rechercher des e-mails à l’aide de noms de connecteur.

La recherche de connecteurs est de nature « contient », ce qui signifie que les recherches partielles par mots clés doivent également fonctionner. Dans l’affichage Grille principale, le volant Détails et le fichier CSV exporté, les connecteurs sont affichés au format Nom/GUID, comme illustré ici :

> [!div class="mx-imgBorder"]
> ![Détails du connecteur](../../media/Connector_Details.png)

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nouvelles fonctionnalités dans l’Explorateur de menaces et détections en temps réel

- [Afficher les e-mails de hameçonnage envoyés à des utilisateurs et domaines usurpés](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [Afficher un aperçu de l’en-tête du courrier électronique et télécharger le corps de l’e-mail](#preview-email-header-and-download-email-body)
- [Chronologie de l’e-mail](#email-timeline)
- [Exporter les données de clic d’URL](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Afficher les e-mails de hameçonnage envoyés à des utilisateurs et domaines usurpés

Pour identifier les tentatives de hameçonnage sur les utilisateurs et les domaines dont l’identité est usurpée, vous devez être ajouté à la liste des utilisateurs *à protéger.* Pour les domaines, les administrateurs doivent activer *les* domaines de l’organisation ou ajouter un nom de domaine aux domaines *à protéger.* Les domaines à protéger se trouvent dans la page stratégie *anti-hameçonnage* de la section Emprunt *d’identité.*

Pour passer en revue les messages d’hameçonnage et rechercher des domaines ou des utilisateurs usurpés d’identité, utilisez [l’affichage](threat-explorer-views.md) Hameçonnage > de l’Explorateur.

Cet exemple utilise l’Explorateur de menaces.

1. Dans le [Centre de sécurité & conformité](https://protection.office.com) ( , choisissez Gestion des menaces > Explorer https://protection.office.com) (ou Détections en temps réel).

2. Dans le menu Affichage, sélectionnez Courrier électronique > Hameçonnage.

   Ici, vous pouvez choisir **un domaine usurpé d’identité** ou **un utilisateur dont l’identité est usurpée.**

3. **Sélectionnez** **le domaine dont l’identité est** emprunt d’identité, puis tapez un domaine protégé dans la boîte de texte.

   Par exemple, recherchez des noms de domaine protégés tels que *contoso,* *contoso.com* ou *contoso.com.au*.

4. Sélectionnez l’objet d’un message sous l’onglet Courrier > onglet Détails pour voir des informations supplémentaires sur l’emprunt d’identité, telles que l’emprunt d’identité domaine /emplacement détecté.

    **OR**

    Sélectionnez **Utilisateur dont l’identité** est usurpée et tapez l’adresse e-mail d’un utilisateur protégé dans la boîte de texte.

    > [!TIP]
    > **Pour obtenir de meilleurs résultats,** utilisez *des adresses de messagerie complètes* pour rechercher des utilisateurs protégés. Vous trouverez votre utilisateur protégé plus rapidement et plus efficacement si vous recherchez *firstname.lastname@contoso.com,* par exemple, lors de l’enquête sur l’emprunt d’identité d’utilisateur. Lorsque vous recherchez un domaine protégé, la recherche prend le domaine racine (contoso.com, par exemple) et le nom de domaine (*contoso*). La recherche de  l’contoso.com de domaine racine retournera les emprunts d’identité de *contoso.com* et le nom de *domaine contoso*.

5. Sélectionnez **l’objet d’un** message sous l’onglet Détails de l’onglet Courrier électronique pour voir des informations supplémentaires sur l’emprunt d’identité sur l’utilisateur ou le domaine, ainsi que  >   *l’emplacement détecté.*

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Volet d’informations de l’Explorateur de menaces pour un utilisateur protégé affichant l’emplacement de détection et la menace détectée (ici l’emprunt d’identité par hameçonnage d’un utilisateur).":::

> [!NOTE]
> À l’étape 3 ou 5,  si vous choisissez  la technologie de détection et sélectionnez respectivement le domaine d’emprunt d’identité ou l’utilisateur de l’emprunt d’identité, les informations de l’onglet Courrier électronique sur l’utilisateur ou le domaine et l’emplacement détecté s’afficheront uniquement sur les messages relatifs à l’utilisateur ou au domaine répertoriés dans la page stratégie   >    *anti-hameçonnage.*

### <a name="preview-email-header-and-download-email-body"></a>Afficher un aperçu de l’en-tête du courrier électronique et télécharger le corps de l’e-mail

Vous pouvez désormais afficher un aperçu d’un en-tête d’e-mail et télécharger le corps de l’e-mail dans l’Explorateur de menaces. Les administrateurs peuvent analyser les en-têtes/messages électroniques téléchargés pour les menaces. Étant donné que le téléchargement de messages électroniques peut risque d’exposer des informations, ce processus est contrôlé par le contrôle d’accès basé sur un rôle (RBAC). Un nouveau rôle, *Preview,* doit être ajouté à un autre groupe de rôles (par exemple, Opérations de sécurité ou Administrateur de la sécurité) pour accorder la possibilité de télécharger des messages électroniques dans l’affichage des messages électroniques. Toutefois, l’affichage de l’en-tête de courrier électronique ne nécessite aucun rôle supplémentaire (autre que celui requis pour afficher les messages dans l’Explorateur de menaces).

Les détections de l’explorateur et du temps réel obtiennent également de nouveaux champs qui fournissent une image plus complète de l’endroit où vos messages électroniques sont envoyés. Ces modifications facilitent le recherche pour les opérations de sécurité. Mais le résultat principal est que vous pouvez connaître l’emplacement des messages électroniques problématiques en un coup d’œil.

Comment cela se fait-il ? L’état de remise est maintenant divisé en deux colonnes :

- **Action de remise** : état de l’e-mail.
- **Emplacement de remise** : emplacement où le courrier a été acheminé.

*L’action de* remise est l’action entreprise sur un e-mail en raison de stratégies ou de détections existantes. Voici les actions possibles pour un e-mail :

<br>

****

|Remis|Junked|Blocked|Remplacé|
|---|---|---|---|
|Le courrier électronique a été remis à la boîte de réception ou au dossier d’un utilisateur, et l’utilisateur peut y accéder.|Le courrier électronique a été envoyé au dossier Courrier indésirable ou Supprimé de l’utilisateur, et l’utilisateur peut y accéder.|Messages électroniques mis en quarantaine, qui ont échoué ou ont été supprimés. Ces messages ne sont pas accessibles à l’utilisateur.|Le courrier électronique avait des pièces jointes malveillantes remplacées .txt fichiers qui d’état de la pièce jointe était malveillant.|
|

Voici ce que l’utilisateur peut et ne peut pas voir :

<br>

****

|Accessible aux utilisateurs finaux|Inaccessible aux utilisateurs finaux|
|---|---|
|Remis|Blocked|
|Junked|Remplacé|
|

**L’emplacement de** remise affiche les résultats des stratégies et des détections qui s’exécutent après la remise. Il est lié à **_l’action de remise._** Voici les valeurs possibles :

- *Boîte de réception ou dossier*: l’e-mail se trouve dans la boîte de réception ou un dossier (conformément à vos règles de messagerie).
- *Local ou externe*: la boîte aux lettres n’existe pas sur le cloud mais est en local.
- *Dossier de courrier indésirable*: le courrier électronique se trouve dans le dossier Courrier indésirable d’un utilisateur.
- *Dossier Éléments supprimés*: courrier électronique dans le dossier Éléments supprimés d’un utilisateur.
- *Quarantaine :* le courrier électronique est en quarantaine et non dans la boîte aux lettres d’un utilisateur.
- *Échec :* l’e-mail n’a pas pu atteindre la boîte aux lettres.
- *L’e-mail* a été perdu quelque part dans le flux de messagerie.

### <a name="email-timeline"></a>Chronologie de l’e-mail

La **chronologie de la messagerie** est une nouvelle fonctionnalité de l’Explorateur qui améliore l’expérience de recherche pour les administrateurs. Cela réduit le temps passé à vérifier les différents emplacements pour essayer de comprendre l’événement. Lorsque plusieurs événements se produisent au même moment ou presque à l’arrivée d’un message électronique, ces événements sont affichés dans un affichage chronologique. Certains événements qui se produisent après la remise de votre courrier électronique sont capturés dans la **colonne Action** spéciale. Les administrateurs peuvent combiner les informations de la chronologie avec l’action spéciale entreprise sur la post-remise du courrier pour obtenir des informations sur le fonctionnement de leurs stratégies, l’endroit où le courrier a été finalement acheminé et, dans certains cas, l’évaluation finale.

Pour plus d’informations, voir [Examiner et corriger les](investigate-malicious-email-that-was-delivered.md)messages malveillants qui ont été remis dans Office 365 .

### <a name="export-url-click-data"></a>Exporter les données de clic d’URL

Vous pouvez maintenant exporter des rapports pour les clics d’URL vers Microsoft Excel pour afficher leur **ID** de message réseau et cliquer sur **verdict,** ce qui permet d’expliquer l’origine du trafic de clic de votre URL. Voici comment cela fonctionne : dans la gestion des menaces sur Office 365 barre de lancement rapide, suivez cette chaîne :

**Explorateur** \> **Afficher le hameçonnage** \> **Clics** \> **Les URL les plus fréquentes** ou **les clics** principaux de l’URL sélectionnent n’importe quel \> enregistrement pour ouvrir le volant d’URL.

Lorsque vous sélectionnez une URL dans la  liste, un nouveau bouton Exporter s’affichera dans le panneau volant. Utilisez ce bouton pour déplacer des données vers une feuille de calcul Excel plus facile à créer.

Suivez ce chemin d’accès pour vous rendre au même emplacement dans le rapport de détections en temps réel :

**Explorateur** \> **Détections en temps réel** \> **Afficher le hameçonnage** \> **URL** \> **URL principales ou** **Clics** principaux : sélectionnez n’importe quel enregistrement pour ouvrir le volant d’URL et accédez \> à \> **l’onglet Clics.**

> [!TIP]
> L’ID de message réseau maie le clic à des messages spécifiques lorsque vous recherchez sur l’ID via l’Explorateur ou des outils tiers associés. Ces recherches identifient l’e-mail associé à un résultat de clic. La mise en corrélation de l’ID de message réseau permet une analyse plus rapide et plus puissante.

> [!div class="mx-imgBorder"]
> ![Clique sur l’onglet dans l’Explorateur](../../media/tp_ExportClickResultAndNetworkID.png)

## <a name="see-malware-detected-in-email-by-technology"></a>Voir les programmes malveillants détectés dans la messagerie électronique par la technologie

Supposons que vous vouliez voir les programmes malveillants détectés dans les messages électroniques triés par Microsoft 365 technologie. Pour ce faire, utilisez la vue [Courrier > programmes](threat-explorer-views.md#email--malware) malveillants de l’Explorateur (ou détections en temps réel).

1. Dans le Centre de sécurité & conformité ( ), choisissez l’Explorateur de gestion des <https://protection.office.com>  \>  menaces (ou **détections en temps réel).** (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage,** sélectionnez **Programme** malveillant de \> **messagerie.**

   > [!div class="mx-imgBorder"]
   > ![Menu Afficher pour l’Explorateur](../../media/ExplorerViewEmailMalwareMenu.png)

3. Cliquez **sur Expéditeur,** puis choisissez **Technologie de** détection de \> **base.**

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

   > [!div class="mx-imgBorder"]
   > ![Technologies de détection de programmes malveillants](../../media/ExplorerEmailMalwareDetectionTech.png)

4. Choisissez une option. Sélectionnez ensuite **le bouton Actualiser** pour appliquer ce filtre.

   > [!div class="mx-imgBorder"]
   > ![Technologie de détection sélectionnée](../../media/ExplorerEmailMalwareDetectionTechATP.png)

Le rapport est actualisé pour afficher les résultats détectés par les programmes malveillants détectés dans le courrier électronique, à l’aide de l’option technologique que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus approfondie.

## <a name="view-phishing-url-and-click-verdict-data"></a>Afficher l’URL de hameçonnage et cliquer sur les données de verdict

Supposons que vous vouliez voir les tentatives de hameçonnage par le biais d’URL dans le courrier électronique, y compris une liste d’URL qui ont été autorisées, bloquées et bloquées. Pour identifier les URL sur qui vous avez cliqué, [Coffre liens](safe-links.md) doivent être configurés. Veillez à configurer [](set-up-safe-links-policies.md) des stratégies Coffre liens pour la protection au moment du clic et la journalisation des verdicts de clic en Coffre liens.

Pour passer en revue les URL de hameçonnage dans les [   >   ](threat-explorer-views.md#email--phish) messages et cliquer sur les URL des messages d’hameçonnage, utilisez l’affichage Hameçonnage de l’Explorateur ou les détections en temps réel.

1. Dans le Centre de sécurité & conformité ( ), choisissez l’Explorateur de gestion des <https://protection.office.com>  \>  menaces (ou **détections en temps réel).** (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage,** sélectionnez  \> **Hameçonnage de messagerie.**

   > [!div class="mx-imgBorder"]
   > ![Afficher le menu de l’Explorateur dans le contexte de hameçonnage](../../media/ExplorerViewEmailPhishMenu.png)

3. Cliquez **sur Expéditeur,** puis choisissez **URL Verdict** de \> **clic.**

4. Sélectionnez une ou plusieurs  options, telles que Blocked  et **Block overridden,** puis sélectionnez le bouton Actualiser sur la même ligne que les options à appliquer à ce filtre. (N’actualisez pas la fenêtre de votre navigateur.)

   > [!div class="mx-imgBorder"]
   > ![URL et verdicts de clic](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

   Le rapport est actualisé pour afficher deux tables d’URL différentes sous l’onglet URL sous le rapport :

   - **Les URL principales sont** les URL des messages que vous avez filtrés vers le bas et le nombre d’actions de remise de courrier pour chaque URL. Dans l’affichage de courrier d’hameçonnage, cette liste contient généralement des URL légitimes. Les attaquants incluent un mélange d’URL bonnes et mauvaises dans leurs messages pour essayer de les remettre, mais ils rendent les liens malveillants plus intéressants. Le tableau des URL est trié par nombre total de messages électroniques, mais cette colonne est masquée pour simplifier l’affichage.

   - **Les clics les** plus fréquents Coffre URL wrapped links qui ont été cliquées, triées par nombre total de clics. Cette colonne n’est pas non plus affichée, pour simplifier l’affichage. Le nombre total par colonne indique le nombre Coffre nombre de verdicts de clics de liens pour chaque URL cliquée. Dans l’affichage courrier d’hameçonnage, il s’agit généralement d’URL suspectes ou malveillantes. Toutefois, l’affichage peut inclure des URL qui ne sont pas des menaces mais qui figurent dans des messages d’hameçonnage. Les clics d’URL sur les liens déballés ne s’affiche pas ici.

   Les deux tableaux d’URL indiquent les PRINCIPALES URL des messages électroniques de hameçonnage par action de remise et emplacement. Les tableaux indiquent les clics d’URL qui ont été bloqués ou visités malgré un avertissement, afin que vous pouvez voir quels liens de mauvaises adresses ont été présentés aux utilisateurs et que l’utilisateur a cliqué. À partir de là, vous pouvez effectuer une analyse plus approfondie. Par exemple, sous le graphique, vous pouvez voir les URL les plus fréquentes dans les messages électroniques bloqués dans l’environnement de votre organisation.

   > [!div class="mx-imgBorder"]
   > ![URL d’explorateur qui ont été bloquées](../../media/ExplorerPhishClickVerdictURLs.png)

   Sélectionnez une URL pour afficher des informations plus détaillées.

   > [!NOTE]
   > Dans la boîte de dialogue du volant d’URL, le filtrage des messages électroniques est supprimé pour afficher la vue complète de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques qui vous préoccupent dans l’Explorateur, de rechercher des URL spécifiques qui sont des menaces potentielles, puis d’étendre votre compréhension de l’exposition des URL dans votre environnement (via la boîte de dialogue Détails de l’URL) sans avoir à ajouter de filtres d’URL à l’affichage Explorateur lui-même.

### <a name="interpretation-of-click-verdicts"></a>Interprétation des verdicts de clic

Dans les volants d’e-mail ou d’URL, les clics principaux ainsi que dans nos expériences de filtrage, vous verrez différentes valeurs de verdict de clic :

- **Aucun :** Impossible de capturer le verdict pour l’URL. L’utilisateur a peut-être cliqué sur l’URL.
- **Autorisé :** L’utilisateur a été autorisé à accéder à l’URL.
- **Bloqué :** L’accès à l’URL a été bloqué pour l’utilisateur.
- **Verdict en attente :** La page en attente de détonation s’est présentée à l’utilisateur.
- **Blocked overridden:** L’utilisateur ne peut pas accéder directement à l’URL. Toutefois, l’utilisateur a overrode le bloc pour accéder à l’URL.
- **Verdict en attente contourné :** La page de détonation s’est présentée à l’utilisateur. Toutefois, l’utilisateur a overrode le message pour accéder à l’URL.
- **Erreur :** La page d’erreur s’est présentée à l’utilisateur, ou une erreur s’est produite lors de la capture du verdict.
- **Échec :** Une exception inconnue s’est produite lors de la capture du verdict. L’utilisateur a peut-être cliqué sur l’URL.

## <a name="review-email-messages-reported-by-users"></a>Passer en revue les messages électroniques signalés par les utilisateurs

Supposons que vous vouliez voir les messages électroniques signalés  par les utilisateurs de votre organisation comme courrier *indésirable,* non indésirable ou hameçonnage via le [add-in Signaler](enable-the-report-message-add-in.md) un message ou le module de signalement du [hameçonnage.](enable-the-report-phish-add-in.md) Pour les afficher, utilisez [ **l’affichage**  >  **Envois**](threat-explorer-views.md#email--submissions) de courrier de l’Explorateur (ou détections en temps réel).

1. Dans le Centre de sécurité & conformité ( ), choisissez l’Explorateur de gestion des <https://protection.office.com>  \>  menaces (ou **détections en temps réel).** (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage,** sélectionnez  \> **Envois de courrier électronique.**

   > [!div class="mx-imgBorder"]
   > ![Afficher le menu de l’Explorateur pour les e-mails](../../media/explorer-view-menu-email-user-reported.png)

3. Cliquez **sur Expéditeur,** puis choisissez **Type de** rapport de \> **base.**

4. Sélectionnez une option, telle que **Hameçonnage,** puis sélectionnez le **bouton Actualiser.**

   > [!div class="mx-imgBorder"]
   > ![Hameçonnage signalé par l’utilisateur](../../media/EmailUserReportedReportType.png)

Le rapport est actualisé pour afficher les données sur les messages électroniques signalés par les membres de votre organisation comme tentative de hameçonnage. Vous pouvez utiliser ces informations pour effectuer une analyse plus approfondie et, si nécessaire, ajuster vos stratégies [anti-hameçonnage](configure-mdo-anti-phishing-policies.md)dans Microsoft Defender pour Office 365 .

## <a name="start-automated-investigation-and-response"></a>Démarrer un examen et une réponse automatisés

> [!NOTE]
> Des fonctionnalités automatisées d’examen et de réponse sont disponibles dans *Microsoft Defender pour Office 365 Plan 2* et *Office 365 E5*.

[L’examen et la réponse automatisés](automated-investigation-response-office.md) peuvent faire gagner du temps et des efforts à votre équipe en matière d’opérations de sécurité pour examiner et atténuer les cyberattaques. En plus de configurer des alertes qui peuvent déclencher un manuel de sécurité, vous pouvez démarrer un processus automatisé d’examen et de réponse à partir d’une vue dans l’Explorateur. Pour plus d’informations, [voir l’exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur.](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Autres façons d’utiliser l’Explorateur et les détections en temps réel

Outre les scénarios décrits dans cet article, de nombreuses autres options de rapport sont disponibles avec l’Explorateur (ou détections en temps réel). Consultez les articles suivants :

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](./mdo-for-spo-odb-and-teams.md)
- [Obtenir une vue d’ensemble des affichages dans l’Explorateur de menaces (et détections en temps réel)](threat-explorer-views.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponse automatisés dans Microsoft 365 Defender](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour que Office 365](defender-for-office-365.md) utiliser les détections en temps réel ou l’Explorateur.

- L’Explorateur est inclus dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.
- Prévoyez d’attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender Office 365. Les détections d’explorateur et en temps réel montrent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser les détections de l’Explorateur ou en temps réel, vous devez avoir les autorisations appropriées, telles que celles accordées à un administrateur de sécurité ou à un lecteur de sécurité.

- Pour le Centre de sécurité & conformité, l’un des rôles suivants doit vous être attribué :

  - Gestion de l’organisation
  - Administrateur de sécurité (peut être affecté dans le centre d’administration Azure Active Directory de sécurité ( <https://aad.portal.azure.com> )
  - Lecteur de sécurité

- Pour Exchange Online, vous devez avoir l’un des rôles suivants attribués dans le Centre d’administration Exchange () ou <https://admin.protection.outlook.com/ecp/> [dans Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell):

  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations des fonctionnalités dans Exchange Online](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Différences entre l’Explorateur de menaces et les détections en temps réel

- Le *rapport détections en* temps réel est disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de* menaces est disponible dans Defender pour Office 365 Plan 2.
- Le rapport de détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais fournit également des détails supplémentaires pour une attaque donnée.
- Un *affichage de courrier tout* est disponible dans l’Explorateur de menaces, mais pas dans le rapport de détections en temps réel.
- D’autres fonctionnalités de filtrage et actions disponibles sont incluses dans l’Explorateur de menaces. Pour plus d’informations, voir Microsoft Defender pour la description Office 365 service : disponibilité des fonctionnalités dans [Defender pour Office 365 plans.](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans)

## <a name="other-articles"></a>Autres articles

[Examiner les e-mails avec la page Entité de messagerie](mdo-email-entity-page.md)
