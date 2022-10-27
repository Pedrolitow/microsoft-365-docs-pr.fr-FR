---
title: Détections en temps réel et de l’Explorateur de menaces
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 82ac9922-939c-41be-9c8a-7c75b0a4e27d
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Utilisez l’Explorateur et les détections en temps réel dans le portail Microsoft 365 Defender pour examiner les menaces et y répondre efficacement.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: b4b9ca9903918a1e84361471ce5041aaf0dbf100
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729058"
---
# <a name="threat-explorer-and-real-time-detections"></a>Détections en temps réel et de l’Explorateur de menaces

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si votre organisation a [Microsoft Defender pour Office 365](defender-for-office-365.md) et que vous disposez [des autorisations nécessaires](#required-licenses-and-permissions), vous disposez de détections **explorer** ou en **temps réel** (anciennement *rapports en temps réel* ; [découvrez les nouveautés](#new-features-in-threat-explorer-and-real-time-detections)!). Accédez à **Gestion des** menaces, puis choisissez **Explorateur** _ou_ **Détections en temps réel**.

|Avec Microsoft Defender pour Office 365 Plan 2, vous voyez :|Avec Microsoft Defender pour Office 365 Plan 1, vous voyez :|
|---|---|
|![Explorateur de menaces.](../../media/threatmgmt-explorer.png)|![Détections en temps réel](../../media/threatmgmt-realtimedetections.png)|

Les détections d’explorateur ou en temps réel permettent à votre équipe des opérations de sécurité d’examiner et de répondre efficacement aux menaces. Avec ce rapport, vous pouvez :

- [Voir les programmes malveillants détectés par les fonctionnalités de sécurité de Microsoft 365](#see-malware-detected-in-email-by-technology)
- [Afficher l’URL de hameçonnage et cliquer sur les données de verdict](#view-phishing-url-and-click-verdict-data)
- [Démarrer un processus automatisé d’investigation et de réponse à partir d’une vue dans l’Explorateur](#start-automated-investigation-and-response) (Defender pour Office 365 Plan 2 uniquement)
- [Examiner les e-mails malveillants, et bien plus encore](#more-ways-to-use-explorer-and-real-time-detections)

## <a name="improvements-to-threat-hunting-experience"></a>Améliorations apportées à l’expérience de chasse aux menaces

### <a name="introduction-of-alert-id-for-defender-for-office-365-alerts-within-explorerreal-time-detections"></a>Introduction de l’ID d’alerte pour les alertes Defender pour Office 365 dans l’Explorateur/Détections en temps réel

Aujourd’hui, si vous naviguez d’une alerte vers l’Explorateur de menaces, une vue filtrée s’ouvre dans l’Explorateur, la vue étant filtrée par ID de stratégie d’alerte (l’ID de stratégie étant un identificateur unique pour une stratégie d’alerte).
Nous rendons cette intégration plus pertinente en introduisant l’ID d’alerte (voir un exemple d’ID d’alerte ci-dessous) dans l’Explorateur de menaces et les détections en temps réel afin que vous voyiez les messages pertinents pour l’alerte spécifique, ainsi qu’un nombre d’e-mails. Vous serez également en mesure de voir si un message faisait partie d’une alerte, ainsi que de naviguer de ce message vers l’alerte spécifique.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtrage de l’ID d’alerte" lightbox="../../media/AlertID-Filter.png":::

### <a name="extending-the-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants-from-7-to-30-days"></a>Extension de la durée de conservation et de recherche des données de l’Explorateur (et des détections en temps réel) pour les locataires d’essai de 7 à 30 jours

Dans le cadre de cette modification, vous serez en mesure de rechercher et de filtrer les données d’e-mail sur 30 jours (une augmentation par rapport aux 7 jours précédents) dans l’Explorateur de menaces/Détections en temps réel pour les locataires d’évaluation Defender pour Office P1 et P2.
Cela n’affecte pas les locataires de production pour les clients P1 et P2/E5, qui disposent déjà des fonctionnalités de conservation et de recherche des données de 30 jours.

### <a name="updated-limits-for-export-of-records-for-threat-explorer"></a>Limites mises à jour pour l’exportation d’enregistrements pour l’Explorateur de menaces

Dans le cadre de cette mise à jour, le nombre de lignes pour Email enregistrements pouvant être exportés à partir de l’Explorateur de menaces passe de 9990 à 200 000 enregistrements. L’ensemble de colonnes qui peuvent être exportées reste le même, mais le nombre de lignes augmente à partir de la limite actuelle.

### <a name="tags-in-threat-explorer"></a>Étiquettes dans l’Explorateur de menaces

> [!NOTE]
> La fonctionnalité d’étiquettes utilisateur est en *préversion*, n’est pas disponible pour tout le monde et est susceptible d’être modifiée. Pour plus d’informations sur la planification des versions, consultez la feuille de route Microsoft 365.

Les étiquettes utilisateur identifient des groupes spécifiques d’utilisateurs dans Microsoft Defender pour Office 365. Pour plus d’informations sur les étiquettes, y compris la gestion des licences et la configuration, consultez [Balises utilisateur](user-tags.md).

Dans l’Explorateur de menaces, vous pouvez voir des informations sur les balises utilisateur dans les expériences suivantes.

#### <a name="email-grid-view"></a>Email affichage grille

La colonne **Étiquettes** dans la grille d’e-mail contient toutes les balises qui ont été appliquées aux boîtes aux lettres de l’expéditeur ou du destinataire. Par défaut, les balises système comme les comptes prioritaires sont affichées en premier.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Étiquettes de filtre dans l’affichage Grille de messagerie" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrage

Vous pouvez utiliser des balises comme filtre. Recherchez des comptes prioritaires ou des scénarios de balises utilisateur spécifiques. Vous pouvez également exclure les résultats qui ont certaines balises. Combinez cette fonctionnalité avec d’autres filtres pour limiter votre étendue d’investigation.

[![Filtrer les balises.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="Balises qui ne sont pas filtrées" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>menu volant de détails Email

Pour afficher les étiquettes individuelles de l’expéditeur et du destinataire, sélectionnez l’objet pour ouvrir le menu volant des détails du message. Sous l’onglet **Résumé** , les balises expéditeur et destinataire sont affichées séparément, s’ils sont présents pour un e-mail.
Les informations sur les étiquettes individuelles pour l’expéditeur et le destinataire s’étendent également aux données CSV exportées, où vous pouvez voir ces détails dans deux colonnes distinctes.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Balises de détails Email" lightbox="../../media/tags-flyout.png":::

Les informations sur les étiquettes sont également affichées dans le menu volant des clics d’URL. Pour l’afficher, accédez à Phish ou Tous les Email, puis à l’onglet **URL** ou **Clics d’URL**. Sélectionnez un menu volant d’URL individuel pour afficher des détails supplémentaires sur les clics de cette URL, y compris les balises associées à ce clic.

### <a name="updated-timeline-view"></a>Affichage chronologie mis à jour

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="Balises d’URL" lightbox="../../media/tags-urls.png":::
>
Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="improvements-to-the-threat-hunting-experience-upcoming"></a>Améliorations apportées à l’expérience de repérage des menaces (à venir)

### <a name="updated-threat-information-for-emails"></a>Informations sur les menaces mises à jour pour les e-mails

Nous nous sommes concentrés sur les améliorations de la plateforme et de la qualité des données pour améliorer la précision et la cohérence des données pour les enregistrements de courrier électronique. Les améliorations incluent la consolidation des informations avant et après la remise, telles que les actions exécutées sur un e-mail dans le cadre du processus ZAP, en un seul enregistrement. Des détails supplémentaires tels que le verdict du courrier indésirable, les menaces au niveau de l’entité (par exemple, l’URL qui était malveillante) et les derniers emplacements de remise sont également inclus.

Après ces mises à jour, vous verrez une entrée unique pour chaque message, quels que soient les différents événements post-remise qui affectent le message. Les actions peuvent inclure zap, correction manuelle (ce qui signifie action de l’administrateur), [livraison dynamique](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies), etc.

En plus d’afficher les programmes malveillants et les menaces d’hameçonnage, vous voyez le verdict de courrier indésirable associé à un e-mail. Dans l’e-mail, consultez toutes les menaces associées à l’e-mail, ainsi que les technologies de détection correspondantes. Un e-mail peut comporter zéro, une ou plusieurs menaces. Vous verrez les menaces actuelles dans la section **Détails** du menu volant de l’e-mail. Pour plusieurs menaces (telles que les programmes malveillants et le hameçonnage), le champ **technique Détection** affiche le mappage de détection des menaces, qui est la technologie de détection qui a identifié la menace.

L’ensemble des technologies de détection comprend désormais de nouvelles méthodes de détection, ainsi que des technologies de détection du courrier indésirable. Vous pouvez utiliser le même ensemble de technologies de détection pour filtrer les résultats sur les différents affichages d’e-mail (Programmes malveillants, Hameçonnage, Tous les Email).

> [!NOTE]
> L’analyse de verdict n’est pas nécessairement liée aux entités. Par exemple, un e-mail peut être classé comme hameçonnage ou courrier indésirable, mais aucune URL n’est marquée d’un verdict de hameçonnage/courrier indésirable. Cela est dû au fait que les filtres évaluent également le contenu et d’autres détails d’un e-mail avant d’attribuer un verdict.

#### <a name="threats-in-urls"></a>Menaces dans les URL

Vous pouvez maintenant voir la menace spécifique pour une URL dans l’onglet **Détails** du menu volant de l’e-mail. La menace peut être *un programme malveillant*, *une hameçonnage*, un *courrier indésirable* ou *aucune*.)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/URL_Threats.png" alt-text="Menaces d’URL" lightbox="../../media/URL_Threats.png":::

### <a name="updated-timeline-view-upcoming"></a>Affichage chronologie mis à jour (à venir)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Email_Timeline.png" alt-text="Affichage chronologie mis à jour" lightbox="../../media/Email_Timeline.png":::

La vue Chronologie identifie tous les événements de remise et de post-remise. Il inclut des informations sur la menace identifiée à ce moment-là pour un sous-ensemble de ces événements. La vue Chronologie fournit également des informations sur toute action supplémentaire effectuée (par exemple, ZAP ou correction manuelle), ainsi que le résultat de cette action. Les informations de l’affichage chronologie incluent :

- **Source:** Source de l’événement. Il peut s’agir d’administrateur/système/utilisateur.
- **Événement:** Inclut des événements de niveau supérieur tels que la remise d’origine, la correction manuelle, le ZAP, les soumissions et la remise dynamique.
- **Action:** Action spécifique qui a été effectuée dans le cadre d’une action ZAP ou d’administrateur (par exemple, suppression réversible).
- **Menaces:** Couvre les menaces (programmes malveillants, hameçonnage, courrier indésirable) identifiées à ce moment-là.
- **Résultat/Détails :** Plus d’informations sur le résultat de l’action, par exemple si elle a été effectuée dans le cadre de l’action ZAP/admin.

### <a name="original-and-latest-delivery-location"></a>Emplacement de livraison d’origine et le dernier

Actuellement, nous présentons l’emplacement de livraison dans la grille d’e-mail et le menu volant des e-mails. Le champ **Emplacement de** remise est renommé **_Emplacement de remise d’origine_*_. Et nous introduisons un autre champ, _*_Dernier emplacement de livraison_**.

**L’emplacement de livraison d’origine** donne plus d’informations sur l’endroit où un e-mail a été remis initialement. **L’emplacement de remise le plus récent** indique l’emplacement où un e-mail a atterri après des actions système telles que *ZAP* ou des actions d’administrateur telles que *Déplacer vers des éléments supprimés*. L’emplacement de remise le plus récent est destiné à indiquer aux administrateurs le dernier emplacement connu du message après la remise ou toute action système/administrateur. Il n’inclut aucune action de l’utilisateur final sur l’e-mail. Par exemple, si un utilisateur a supprimé un message ou déplacé le message vers archive/pst, l’emplacement de remise du message n’est pas mis à jour. Toutefois, si une action système a mis à jour l’emplacement (par exemple, ZAP entraînant le déplacement d’un e-mail en quarantaine), **l’emplacement de remise le plus récent** s’affiche sous la forme « quarantaine ».

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Delivery_Location.png" alt-text="Les emplacements de livraison mis à jour" lightbox="../../media/Updated_Delivery_Location.png":::

> [!NOTE]
> Dans certains cas, **l’emplacement de remise** et **l’action de remise** peuvent apparaître comme « inconnus » :
>
> - Vous pouvez voir **l’emplacement de** remise comme « remis » et **l’emplacement de remise** comme « inconnu » si le message a été remis, mais une règle de boîte de réception a déplacé le message vers un dossier par défaut (tel que Brouillon ou Archive) au lieu du dossier Boîte de réception ou Courrier indésirable Email.
>
> - **L’emplacement de remise le plus récent** peut être inconnu si une action administrateur/système (telle que ZAP) a été tentée, mais que le message n’a pas été trouvé. En règle générale, l’action se produit après que l’utilisateur a déplacé ou supprimé le message. Dans ce cas, vérifiez la colonne **Résultat/Détails** en mode Chronologie. Recherchez l’instruction « Message déplacé ou supprimé par l’utilisateur ».

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Updated_Timeline_Delivery_Location.png" alt-text="Les emplacements de livraison pour la chronologie" lightbox="../../media/Updated_Timeline_Delivery_Location.png":::

### <a name="additional-actions"></a>Actions supplémentaires

*Des actions supplémentaires* ont été appliquées après la remise de l’e-mail. Elles peuvent inclure *zap*, *correction manuelle* (action effectuée par un Administration comme la suppression réversible), *remise dynamique* et *retraitement* (pour un e-mail qui a été détecté rétroactivement comme bon).

> [!NOTE]
> Dans le cadre des modifications en attente, la valeur « Supprimé par ZAP » actuellement exposée dans le filtre Action de remise disparaît. Vous disposez d’un moyen de rechercher tous les e-mails avec la tentative ZAP par le biais **d’actions supplémentaires**.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Additional_Actions.png" alt-text="Actions supplémentaires dans l’Explorateur" lightbox="../../media/Additional_Actions.png":::

### <a name="system-overrides"></a>Remplacements système

*Les remplacements système* vous permettent d’effectuer des exceptions à l’emplacement de remise prévu d’un message. Vous remplacez l’emplacement de remise fourni par le système, en fonction des menaces et autres détections identifiées par la pile de filtrage. Les remplacements système peuvent être définis par le biais d’une stratégie de locataire ou d’utilisateur pour remettre le message comme suggéré par la stratégie. Les remplacements peuvent identifier la remise involontaire de messages malveillants en raison d’écarts de configuration, comme une stratégie d’expéditeur approuvé trop large définie par un utilisateur. Ces valeurs de remplacement peuvent être les suivantes :

- Autorisé par la stratégie utilisateur : un utilisateur crée des stratégies au niveau de la boîte aux lettres pour autoriser les domaines ou les expéditeurs.

- Bloqué par la stratégie utilisateur : un utilisateur crée des stratégies au niveau de la boîte de messagerie pour bloquer les domaines ou les expéditeurs.

- Autorisé par la stratégie de l’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie Exchange (également appelées règles de transport) pour autoriser les expéditeurs et les domaines pour les utilisateurs de leur organisation. Il peut s’agir d’un ensemble d’utilisateurs ou de l’ensemble de l’organisation.

- Bloqué par la stratégie de l’organisation : les équipes de sécurité de l’organisation définissent des stratégies ou des règles de flux de messagerie pour bloquer les expéditeurs, les domaines, les langues de message ou les adresses IP sources pour les utilisateurs de leur organisation. Cela peut être appliqué à un ensemble d’utilisateurs ou à l’ensemble de l’organisation.

- Extension de fichier bloquée par la stratégie de l’organisation : l’équipe de sécurité d’une organisation bloque une extension de nom de fichier via les paramètres de stratégie anti-programme malveillant. Ces valeurs s’affichent désormais dans les détails de l’e-mail pour faciliter les investigations. Les équipes Secops peuvent également utiliser la fonctionnalité de filtrage enrichi pour filtrer sur les extensions de fichiers bloquées.

[![Remplacements système dans l’Explorateur.](../../media/System_Overrides.png)](../../media/System_Overrides.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/System_Overrides_Grid.png" alt-text="Grille des remplacements du système dans l’Explorateur" lightbox="../../media/System_Overrides_Grid.png":::

### <a name="improvements-for-the-url-and-clicks-experience"></a>Améliorations de l’expérience URL et clics

Les améliorations sont les suivantes :

- Affichez l’URL avec clic complet (y compris les paramètres de requête qui font partie de l’URL) dans la section **Clics** du menu volant URL. Actuellement, le domaine et le chemin d’URL s’affichent dans la barre de titre. Nous étendons ces informations pour afficher l’URL complète.

- Correctifs entre les filtres d’URL (*URL* ou *domaine d’URL* ou *domaine et chemin d’URL*) : les mises à jour affectent la recherche de messages qui contiennent un verdict URL/clic. Nous avons activé la prise en charge des recherches indépendantes du protocole, ce qui vous permet de rechercher une URL sans utiliser `http`. Par défaut, la recherche d’URL est mappée à http, sauf si une autre valeur est explicitement spécifiée. Par exemple :
  - Recherchez avec et sans préfixe `http://` dans les champs de filtre **URL**, **Domaine d’URL** **et Domaine d’URL et Chemin d’accès** . Les recherches doivent afficher les mêmes résultats.
  - Recherchez le `https://` préfixe dans **URL**. Lorsqu’aucune valeur n’est spécifiée, le `http://` préfixe est supposé.
  - `/` est ignoré au début et à la fin du **chemin d’URL**, du **domaine d’URL**, du **domaine d’URL et du chemin d’accès** . `/` à la fin du champ **URL** est ignoré.

### <a name="phish-confidence-level"></a>Niveau de confiance des hameçonnages

Le niveau de confiance des hameçonnages permet d’identifier le degré de confiance avec lequel un e-mail a été classé comme « hameçonnage ». Les deux valeurs possibles sont *High* et *Normal*. Dans les phases initiales, ce filtre sera disponible uniquement dans la vue Hameçonnage de l’Explorateur de menaces.

[![Niveau de confiance d’hameçonnage dans l’Explorateur.](../../media/Phish_Confidence_Level.png)](../../media/Phish_Confidence_Level.png#lightbox)

### <a name="zap-url-signal"></a>Signal d’URL ZAP

Le signal d’URL ZAP est généralement utilisé pour les scénarios d’alerte DE hameçonnage ZAP où un e-mail a été identifié comme hameçonnage et supprimé après la remise. Ce signal connecte l’alerte aux résultats correspondants dans l’Explorateur. Il s’agit de l’un des E/S de l’alerte.

Pour améliorer le processus de chasse, nous avons mis à jour l’Explorateur de menaces et les détections en temps réel pour rendre l’expérience de chasse plus cohérente. Les modifications sont décrites ici :

- [Améliorations apportées au fuseau horaire](#timezone-improvements)
- [Mettre à jour dans le processus d’actualisation](#update-in-the-refresh-process)
- [Exploration du graphique à ajouter aux filtres](#chart-drilldown-to-add-to-filters)
- [Mises à jour des informations sur le produit](#in-product-information-updates)

### <a name="filter-by-user-tags"></a>Filtrer par étiquettes d’utilisateur

Vous pouvez désormais trier et filtrer sur les balises système ou utilisateur personnalisées pour saisir rapidement l’étendue des menaces. Pour plus [d’informations, consultez Balises utilisateur](user-tags.md).

> [!IMPORTANT]
> Le filtrage et le tri par étiquettes utilisateur sont actuellement en préversion publique. Cette fonctionnalité peut être considérablement modifiée avant sa publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, concernant les informations fournies à son sujet.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-tags.png" alt-text="Colonne Étiquettes dans l’Explorateur" lightbox="../../media/threat-explorer-tags.png":::

### <a name="timezone-improvements"></a>Améliorations apportées au fuseau horaire

Vous verrez le fuseau horaire des enregistrements de courrier électronique dans le portail ainsi que pour les données exportées. Il sera visible dans les expériences telles que Email Grid, le menu volant Détails, la chronologie Email et les e-mails similaires, de sorte que le fuseau horaire du jeu de résultats est clair.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/TimezoneImprovements.png" alt-text="Fuseau horaire d’affichage dans l’Explorateur" lightbox="../../media/TimezoneImprovements.png":::

### <a name="update-in-the-refresh-process"></a>Mettre à jour dans le processus d’actualisation

Certains utilisateurs ont commenté la confusion entre l’actualisation automatique (par exemple, dès que vous modifiez la date, l’actualisation de la page) et l’actualisation manuelle (pour d’autres filtres). De même, la suppression des filtres entraîne une actualisation automatique. La modification des filtres lors de la modification de la requête peut entraîner des expériences de recherche incohérentes. Pour résoudre ces problèmes, nous passons à un mécanisme de filtrage manuel.

Du point de vue de l’expérience, l’utilisateur peut appliquer et supprimer les différentes plages de filtres (du jeu de filtres et de la date), puis sélectionner le bouton Actualiser pour filtrer les résultats après avoir défini la requête. Le bouton Actualiser est également mis en évidence à l’écran. Nous avons également mis à jour les info-bulles associées et la documentation intégrée au produit.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ManualRefresh.png" alt-text="Bouton Actualiser pour filtrer les résultats" lightbox="../../media/ManualRefresh.png":::

### <a name="chart-drilldown-to-add-to-filters"></a>Exploration du graphique à ajouter aux filtres

Vous pouvez désormais graphiquer des valeurs de légende pour les ajouter en tant que filtres. Sélectionnez le bouton **Actualiser** pour filtrer les résultats.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ChartDrilldown.png" alt-text="Descendre dans les graphiques pour filtrer" lightbox="../../media/ChartDrilldown.png":::

### <a name="in-product-information-updates"></a>Mises à jour des informations sur le produit

Des détails supplémentaires sont désormais disponibles dans le produit, tels que le nombre total de résultats de recherche dans la grille (voir ci-dessous). Nous avons amélioré les étiquettes, les messages d’erreur et les info-bulles pour fournir plus d’informations sur les filtres, l’expérience de recherche et le jeu de résultats.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/ProductInfo.png" alt-text="Informations intégrées au produit à afficher" lightbox="../../media/ProductInfo.png":::

## <a name="extended-capabilities-in-threat-explorer"></a>Fonctionnalités étendues dans l’Explorateur de menaces

### <a name="top-targeted-users"></a>Principaux utilisateurs ciblés

Aujourd’hui, nous exposons la liste des principaux utilisateurs ciblés dans la vue Programmes malveillants pour les e-mails, dans la section **Top Malware Families** . Nous allons également étendre cette vue dans les vues Phish et All Email. Vous serez en mesure de voir les cinq principaux utilisateurs ciblés, ainsi que le nombre de tentatives pour chaque utilisateur pour la vue correspondante. Par exemple, pour la vue Hameçonnage, vous verrez le nombre de tentatives de hameçonnage.

Vous pourrez exporter la liste des utilisateurs ciblés, jusqu’à une limite de 3 000, ainsi que le nombre de tentatives d’analyse hors connexion pour chaque affichage de courrier électronique. En outre, la sélection du nombre de tentatives (par exemple, 13 tentatives dans l’image ci-dessous) ouvre une vue filtrée dans l’Explorateur de menaces, afin que vous puissiez voir plus de détails sur les e-mails et les menaces pour cet utilisateur.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="Les utilisateurs les plus ciblés" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Règles de transport Exchange

Dans le cadre de l’enrichissement des données, vous serez en mesure de voir toutes les différentes règles de transport Exchange (ETR) qui ont été appliquées à un message. Ces informations seront disponibles dans l’affichage grille Email. Pour l’afficher, sélectionnez **Options de colonne** dans la grille, puis **Ajouter une règle de transport Exchange** à partir des options de colonne. Il sera également visible dans le menu volant **Détails** dans l’e-mail.

Vous pouvez voir à la fois le GUID et le nom des règles de transport appliquées au message. Vous pouvez rechercher les messages en utilisant le nom de la règle de transport. Il s’agit d’une recherche « Contient », ce qui signifie que vous pouvez également effectuer des recherches partielles.

> [!IMPORTANT]
> La recherche ETR et la disponibilité des noms dépendent du rôle spécifique qui vous est attribué. Vous devez disposer de l’un des rôles/autorisations suivants pour afficher les noms ETR et effectuer la recherche. Si aucun de ces rôles ne vous est attribué, vous ne pouvez pas voir les noms des règles de transport ou rechercher des messages à l’aide de noms ETR. Toutefois, vous pouvez voir l’étiquette ETR et les informations GUID dans la Email Details. Les autres expériences d’affichage d’enregistrements dans Email Grids, Email les menus volants, les filtres et l’exportation ne sont pas affectées.
>
> - EXO uniquement - Protection contre la perte de données : Tous
> - EXO uniquement - O365SupportViewConfig : All
> - Microsoft Azure Active Directory ou EXO - Administration de sécurité : Tout
> - AAD ou EXO - Lecteur sécurité : Tout
> - EXO uniquement - Règles de transport : Tous
> - EXO uniquement - configuration View-Only : Tout
>
> Dans la grille d’e-mail, le menu volant Détails et le FICHIER CSV exporté, les ETR sont présentés avec un nom/GUID, comme indiqué ci-dessous.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Règles de transport Exchange" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Connecteurs entrants

Les connecteurs sont une collection d’instructions qui personnalisent la façon dont vos e-mails circulent vers et depuis votre organisation Microsoft 365 ou Office 365. Ils vous permettent d’appliquer des restrictions ou des contrôles de sécurité. Dans l’Explorateur de menaces, vous pouvez désormais afficher les connecteurs liés à un e-mail et rechercher des e-mails à l’aide de noms de connecteurs.

La recherche de connecteurs est « contains » par nature, ce qui signifie que les recherches partielles par mot clé doivent également fonctionner. Dans la vue Grille principale, le menu volant Détails et le fichier CSV exporté, les connecteurs sont affichés au format Nom/GUID, comme indiqué ici :

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Détails du connecteur" lightbox="../../media/Connector_Details.png":::

## <a name="new-features-in-threat-explorer-and-real-time-detections"></a>Nouvelles fonctionnalités de l’Explorateur de menaces et détections en temps réel

- [Afficher les e-mails d’hameçonnage envoyés à des utilisateurs et des domaines usurpés d’identité](#view-phishing-emails-sent-to-impersonated-users-and-domains)
- [Afficher un aperçu de l’en-tête d’e-mail et télécharger le corps de l’e-](#preview-email-header-and-download-email-body)
- [chronologie Email](#email-timeline)
- [Exporter les données de clic d’URL](#export-url-click-data)

### <a name="view-phishing-emails-sent-to-impersonated-users-and-domains"></a>Afficher les e-mails d’hameçonnage envoyés à des utilisateurs et des domaines usurpés d’identité

Pour identifier les tentatives d’hameçonnage contre les utilisateurs et les domaines qui sont usurpés d’identité, les utilisateurs doivent être ajoutés à la liste des *utilisateurs à protéger*. Pour les domaines, les administrateurs doivent activer les *domaines de l’organisation* ou ajouter un nom de domaine aux *domaines à protéger*. Les domaines à protéger se trouvent dans la *page Stratégie anti-hameçonnage* de la section *Emprunt d’identité* .

Pour passer en revue les messages de hameçonnage et rechercher des utilisateurs ou des domaines dont l’identité a été empruntée, utilisez la [vue Email > Hameçonnage](threat-explorer-views.md) de l’Explorateur.

Cet exemple utilise l’Explorateur de menaces.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Explorateur** **gestion des** >  menaces (ou **Détections en temps réel**).

2. Dans le menu Affichage, choisissez Email > Hameçon.

   Ici, vous pouvez choisir **le domaine emprunté** ou **l’utilisateur qui a emprunté l’identité**.

3. **Sélectionnez** **Domaine emprunté**, puis tapez un domaine protégé dans la zone de texte.

   Par exemple, recherchez des noms de domaine protégés comme *contoso*, *contoso.com* ou *contoso.com.au*.

4. Sélectionnez l’objet d’un message sous l’onglet Email > onglet Détails pour afficher des informations d’emprunt d’identité supplémentaires telles que Domaine d’emprunt d’identité/Emplacement détecté.

    **OU**

    Sélectionnez **Utilisateur emprunt d’identité** et tapez l’adresse e-mail d’un utilisateur protégé dans la zone de texte.

    > [!TIP]
    > **Pour de meilleurs résultats**, utilisez *des adresses e-mail complètes* pour rechercher des utilisateurs protégés. Vous trouverez votre utilisateur protégé plus rapidement et plus correctement si vous recherchez *firstname.lastname@contoso.com*, par exemple, lors de l’examen de l’emprunt d’identité de l’utilisateur. Lors de la recherche d’un domaine protégé, la recherche prend le domaine racine (contoso.com, par exemple) et le nom de domaine (*contoso*). La recherche du domaine racine *contoso.com* renvoie à la fois les emprunts d’identité de *contoso.com* et le nom de domaine *contoso*.

5. Sélectionnez **l’objet** d’un message sous **Email onglet** > **Détails** pour afficher des informations d’emprunt d’identité supplémentaires sur l’utilisateur ou le domaine, ainsi que *l’emplacement détecté*.

    :::image type="content" source="../../media/threat-ex-views-impersonated-user-image.png" alt-text="Le volet d’informations de l’Explorateur de menaces pour un utilisateur protégé affichant l’emplacement de détection et la menace détectée (ici l’usurpation d’identité d’un utilisateur)" lightbox="../../media/threat-ex-views-impersonated-user-image.png":::

> [!NOTE]
> À l’étape 3 ou 5, si vous choisissez **Technologie de détection** **et sélectionnez Domaine** d’emprunt d’identité ou **Utilisateur d’emprunt d’identité** respectivement, les informations de l’onglet  > **Email****onglet Détails** sur l’utilisateur ou le domaine, et l’emplacement *détecté* s’affichent uniquement sur les messages liés à l’utilisateur ou au domaine répertoriés dans la page *Stratégie anti-hameçonnage*.

### <a name="preview-email-header-and-download-email-body"></a>Afficher un aperçu de l’en-tête d’e-mail et télécharger le corps de l’e-

Vous pouvez maintenant afficher un aperçu d’un en-tête d’e-mail et télécharger le corps de l’e-mail dans l’Explorateur des menaces. Les administrateurs peuvent analyser les en-têtes/messages électroniques téléchargés pour détecter les menaces. Étant donné que le téléchargement de messages électroniques peut risquer l’exposition d’informations, ce processus est contrôlé par le contrôle d’accès en fonction du rôle (RBAC). Un nouveau rôle, *Préversion*, est nécessaire pour permettre de télécharger des messages électroniques dans l’affichage de tous les messages électroniques. Toutefois, l’affichage de l’en-tête d’e-mail ne nécessite aucun rôle supplémentaire (autre que celui requis pour afficher les messages dans l’Explorateur de menaces). Pour créer un groupe de rôles avec le rôle Préversion :

1. Sélectionnez un groupe de rôles intégré qui n’a que le rôle Préversion, par exemple Enquêteur de données ou Gestionnaire eDiscovery.
2. Sélectionnez **Copier le groupe de rôles**.
3. Choisissez un nom et une description pour votre nouveau groupe de rôles, puis sélectionnez **Suivant**.
4. Modifiez les rôles en ajoutant et en supprimant des rôles si nécessaire, mais en laissant le rôle Aperçu.
5. Ajoutez des membres, puis sélectionnez **Créer un groupe de rôles**.

Les détections d’explorateur et en temps réel obtiendront également de nouveaux champs qui fournissent une image plus complète de l’emplacement de vos messages électroniques. Ces modifications facilitent la chasse pour les opérations de sécurité. Mais le résultat principal est que vous pouvez connaître l’emplacement des messages électroniques problématiques en un coup d’œil.

Comment cela se passe-t-il ? L’état de remise est maintenant divisé en deux colonnes :

- **Action de remise** : état de l’e-mail.
- **Emplacement de remise** : emplacement où l’e-mail a été routé.

*L’action de remise* est l’action effectuée sur un e-mail en raison de stratégies ou de détections existantes. Voici les actions possibles pour un e-mail :

|Livré|Jetés|Blocked|Remplacé|
|---|---|---|---|
|Email a été remis à la boîte de réception ou au dossier d’un utilisateur, et l’utilisateur peut y accéder.|Email a été envoyé au dossier Courrier indésirable ou Supprimé de l’utilisateur, et l’utilisateur peut y accéder.|E-mails mis en quarantaine, qui ont échoué ou qui ont été supprimés. Ces messages sont inaccessibles à l’utilisateur.|Email avait des pièces jointes malveillantes remplacées par des fichiers .txt qui indiquent que la pièce jointe était malveillante.|

Voici ce que l’utilisateur peut et ne peut pas voir :

|Accessible aux utilisateurs finaux|Inaccessible aux utilisateurs finaux|
|---|---|
|Livré|Blocked|
|Jetés|Remplacé|

**L’emplacement de remise** affiche les résultats des stratégies et des détections qui s’exécutent après la remise. Il est lié à **_l’action de remise_**. Voici les valeurs possibles :

- *Boîte de réception ou dossier* : l’e-mail se trouve dans la boîte de réception ou un dossier (selon vos règles de messagerie).
- *Localement ou externe* : la boîte aux lettres n’existe pas dans le cloud, mais est locale.
- *Dossier indésirable* : l’e-mail se trouve dans le dossier Courrier indésirable d’un utilisateur.
- *Dossier éléments supprimés* : e-mail dans le dossier Éléments supprimés d’un utilisateur.
- *Quarantaine* : l’e-mail est en quarantaine et non dans la boîte aux lettres d’un utilisateur.
- *Échec* : l’e-mail n’a pas pu atteindre la boîte aux lettres.
- *Supprimé* : l’e-mail a été perdu quelque part dans le flux de courrier.

### <a name="email-timeline"></a>chronologie Email

La **chronologie Email** est une nouvelle fonctionnalité d’Explorateur qui améliore l’expérience de chasse pour les administrateurs. Il réduit le temps passé à vérifier les différents emplacements pour essayer de comprendre l’événement. Lorsque plusieurs événements se produisent au même moment ou à proximité de l’arrivée d’un e-mail, ces événements sont affichés dans une vue de chronologie. Certains événements qui se produisent après la remise de votre e-mail sont capturés dans la colonne **Action spéciale** . Les administrateurs peuvent combiner les informations de la chronologie avec l’action spéciale entreprise sur le courrier post-remise pour obtenir des informations sur le fonctionnement de leurs stratégies, l’emplacement où le courrier a finalement été acheminé et, dans certains cas, l’évaluation finale.

Pour plus d’informations, consultez [Examiner et corriger les e-mails malveillants qui ont été remis dans Office 365](investigate-malicious-email-that-was-delivered.md).

### <a name="export-url-click-data"></a>Exporter les données de clic d’URL

Vous pouvez désormais exporter des rapports pour les clics d’URL vers Microsoft Excel afin d’afficher leur **ID de message réseau** et **leur verdict de clic**, ce qui permet d’expliquer d’où provient votre trafic de clic d’URL. Voici comment cela fonctionne : dans Gestion des menaces dans la barre de lancement rapide Office 365, suivez cette chaîne :

**Explorateur** \> **Afficher le hameçonnage** \> **Clics** \> **Les URL principales** ou les **clics du haut de l’URL** \> sélectionnent n’importe quel enregistrement pour ouvrir le menu volant d’URL.

Lorsque vous sélectionnez une URL dans la liste, un nouveau bouton **Exporter** s’affiche dans le panneau volant. Utilisez ce bouton pour déplacer des données vers une feuille de calcul Excel pour faciliter la création de rapports.

Suivez ce chemin pour accéder au même emplacement dans le rapport détections en temps réel :

**Explorateur** \> **Détections** \> en temps réel **Afficher le hameçonnage** \> **Url** \> **URL principales** ou **clics** \> principaux Sélectionnez n’importe quel enregistrement pour ouvrir le menu \> volant d’URL, accédez à l’onglet **Clics** .

> [!TIP]
> L’ID de message réseau mappe le clic vers des messages spécifiques lorsque vous effectuez une recherche sur l’ID via l’Explorateur ou les outils tiers associés. Ces recherches identifient l’e-mail associé à un résultat de clic. Le fait d’avoir l’ID de message réseau corrélé permet une analyse plus rapide et plus puissante.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tp_ExportClickResultAndNetworkID.png" alt-text="Onglet Clics dans l’Explorateur" lightbox="../../media/tp_ExportClickResultAndNetworkID.png":::

## <a name="see-malware-detected-in-email-by-technology"></a>Voir les programmes malveillants détectés dans les e-mails par la technologie

Supposons que vous souhaitiez voir les programmes malveillants détectés dans les e-mails triés par la technologie Microsoft 365. Pour ce faire, utilisez la [vue Email > Programmes malveillants](threat-explorer-views.md#email--malware) de l’Explorateur (ou détections en temps réel).

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Explorateur** **gestion des** \> menaces (ou **Détections en temps réel**). (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage**, choisissez **Email** \> **Programmes malveillants**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailMalwareMenu.png" alt-text="Menu Affichage de l’Explorateur" lightbox="../../media/ExplorerViewEmailMalwareMenu.png":::

3. Cliquez sur **Expéditeur**, puis choisissez **Technologie de détection de** **base**\>.

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTech.png" alt-text="Technologies de détection des programmes malveillants" lightbox="../../media/ExplorerEmailMalwareDetectionTech.png":::

4. Choisissez une option. Sélectionnez ensuite le bouton **Actualiser** pour appliquer ce filtre.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerEmailMalwareDetectionTechATP.png" alt-text="Technologie de détection sélectionnée" lightbox="../../media/ExplorerEmailMalwareDetectionTechATP.png":::

Le rapport s’actualise pour afficher les résultats détectés par les programmes malveillants dans les e-mails, à l’aide de l’option de technologie que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus approfondie.

## <a name="view-phishing-url-and-click-verdict-data"></a>Afficher l’URL de hameçonnage et cliquer sur les données de verdict

Supposons que vous souhaitiez voir les tentatives d’hameçonnage via des URL dans les e-mails, y compris une liste d’URL autorisées, bloquées et remplacées. Pour identifier les URL qui ont été cliquées, [les liens fiables](safe-links.md) doivent être configurés. Veillez à configurer des stratégies [de liens fiables](set-up-safe-links-policies.md) pour la protection de l’heure de clic et la journalisation des verdicts de clic par les liens fiables.

Pour passer en revue les URL de hameçonnage dans les messages et cliquer sur les URL dans les messages de hameçonnage, utilisez la vue [**Email** >  **Phish**](threat-explorer-views.md#email--phish) de l’Explorateur ou détections en temps réel.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Explorateur** **gestion des** \> menaces (ou **Détections en temps réel**). (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage**, choisissez **Email** \> **Hameçon**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menu Affichage de l’Explorateur dans le contexte d’hameçonnage" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Cliquez sur **Expéditeur**, puis choisissez **URL** \> **Cliquez sur Verdict**.

4. Sélectionnez une ou plusieurs options, telles que **Bloqué** et **Bloquer remplacé**, puis sélectionnez le bouton **Actualiser** sur la même ligne que les options pour appliquer ce filtre. (N’actualisez pas la fenêtre de votre navigateur.)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png" alt-text="Les URL et les verdicts de clic" lightbox="../../media/ThreatExplorerEmailPhishClickVerdictOptions.png":::

   Le rapport s’actualise pour afficher deux tables d’URL différentes sous l’onglet URL sous le rapport :

   - **Les URL principales** sont les URL dans les messages vers lesquels vous avez filtré et l’action de remise d’e-mail compte pour chaque URL. Dans l’affichage Courrier hameçonnage, cette liste contient généralement des URL légitimes. Les attaquants incluent un mélange d’URL bonnes et mauvaises dans leurs messages pour essayer de les obtenir remis, mais ils rendent les liens malveillants plus intéressants. La table des URL est triée par nombre total d’e-mails, mais cette colonne est masquée pour simplifier l’affichage.

   - **Les clics les plus hauts** sont les URL encapsulées de liens fiables qui ont été cliquées, triées par nombre total de clics. Cette colonne n’est pas non plus affichée, pour simplifier l’affichage. Le nombre total de clics par colonne indique le nombre de clics de liens fiables pour chaque URL cliquée. Dans l’affichage Courrier hameçonnage, il s’agit généralement d’URL suspectes ou malveillantes. Toutefois, la vue peut inclure des URL qui ne sont pas des menaces, mais qui se trouvent dans des messages de hameçonnage. Les clics d’URL sur les liens non activés ne s’affichent pas ici.

   Les deux tableaux d’URL affichent les URL principales dans les messages électroniques de hameçonnage par action de remise et emplacement. Les tableaux affichent les clics d’URL qui ont été bloqués ou visités en dépit d’un avertissement, afin que vous puissiez voir quels liens incorrects potentiels ont été présentés aux utilisateurs et que l’utilisateur a cliqué. À partir de là, vous pouvez effectuer une analyse plus approfondie. Par exemple, sous le graphique, vous pouvez voir les URL principales dans les messages électroniques qui ont été bloqués dans l’environnement de votre organisation.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="URL de l’Explorateur qui ont été bloquées" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Sélectionnez une URL pour afficher des informations plus détaillées.

   > [!NOTE]
   > Dans la boîte de dialogue volant URL, le filtrage des messages électroniques est supprimé pour afficher l’affichage complet de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques qui vous préoccupent dans l’Explorateur, de rechercher des URL spécifiques qui constituent des menaces potentielles, puis d’étendre votre compréhension de l’exposition des URL dans votre environnement (via la boîte de dialogue Détails de l’URL) sans avoir à ajouter des filtres d’URL à la vue Explorateur elle-même.

### <a name="interpretation-of-click-verdicts"></a>Interprétation des verdicts de clic

Dans les menus volants Email ou URL, les clics du haut ainsi que dans nos expériences de filtrage, vous verrez différentes valeurs de verdict de clic :

- **Aucun:** Impossible de capturer le verdict pour l’URL. L’utilisateur a peut-être cliqué sur l’URL.
- **Autorisé:** L’utilisateur a été autorisé à accéder à l’URL.
- **Bloqué:** L’utilisateur n’a pas pu accéder à l’URL.
- **Verdict en attente :** La page en attente de détonation a été présentée à l’utilisateur.
- **Remplacement bloqué :** L’utilisateur n’a pas pu accéder directement à l’URL. Mais l’utilisateur a dépassé le bloc pour accéder à l’URL.
- **Verdict en attente ignoré :** La page de détonation a été présentée à l’utilisateur. Mais l’utilisateur a dépassé le message pour accéder à l’URL.
- **Erreur:** La page d’erreur a été présentée à l’utilisateur ou une erreur s’est produite lors de la capture du verdict.
- **Échec:** Une exception inconnue s’est produite lors de la capture du verdict. L’utilisateur a peut-être cliqué sur l’URL.

## <a name="review-email-messages-reported-by-users"></a>Passer en revue les messages électroniques signalés par les utilisateurs

Supposons que vous souhaitiez voir les messages électroniques signalés par les utilisateurs de votre organisation comme *courrier indésirable*, *non indésirable* ou *hameçonnage* via le [complément Signaler un message](enable-the-report-message-add-in.md) ou le [complément Signaler l’hameçonnage](enable-the-report-phish-add-in.md). Pour les afficher, utilisez la vue [**Email** >  **Sousmissions**](threat-explorer-views.md#email--submissions) de l’Explorateur (ou détections en temps réel).

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Explorateur** **gestion des** \> menaces (ou **Détections en temps réel**). (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage**, choisissez **Email** \> **Soumissions**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/explorer-view-menu-email-user-reported.png" alt-text="Menu Affichage de l’Explorateur pour les e-mails" lightbox="../../media/explorer-view-menu-email-user-reported.png":::

3. Cliquez sur **Expéditeur**, puis choisissez **Type de rapport** **de base**\>.

4. Sélectionnez une option, telle que **Phish**, puis sélectionnez le bouton **Actualiser** .

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/EmailUserReportedReportType.png" alt-text="Hameçonnage signalé par l’utilisateur" lightbox="../../media/EmailUserReportedReportType.png":::

Le rapport s’actualise pour afficher les données relatives aux messages électroniques signalés par des membres de votre organisation comme tentative d’hameçonnage. Vous pouvez utiliser ces informations pour effectuer une analyse plus approfondie et, si nécessaire, ajuster vos [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="start-automated-investigation-and-response"></a>Démarrer l’examen et la réponse automatisés

> [!NOTE]
> Les fonctionnalités d’investigation et de réponse automatisées sont disponibles dans *Microsoft Defender pour Office 365 Plan 2* et *Office 365 E5*.

[L’investigation et la réponse automatisées](automated-investigation-response-office.md) peuvent faire gagner du temps et des efforts à votre équipe chargée des opérations de sécurité pour examiner et atténuer les cyberattaques. En plus de configurer des alertes qui peuvent déclencher un playbook de sécurité, vous pouvez démarrer un processus automatisé d’investigation et de réponse à partir d’une vue dans l’Explorateur. Pour plus d’informations, consultez [Exemple : Un administrateur de la sécurité déclenche une investigation à partir de l’Explorateur](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="more-ways-to-use-explorer-and-real-time-detections"></a>Autres façons d’utiliser l’Explorateur et les détections en temps réel

Outre les scénarios décrits dans cet article, vous disposez de nombreuses autres options de création de rapports disponibles avec l’Explorateur (ou les détections en temps réel). Consultez les articles suivants :

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](./mdo-for-spo-odb-and-teams.md)
- [Obtenir une vue d’ensemble des vues dans l’Explorateur de menaces (et les détections en temps réel)](threat-explorer-views.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Enquête et réponse automatisées dans Microsoft 365 Defender](../defender/m365d-autoir.md)

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour Office 365](defender-for-office-365.md) pour utiliser les détections d’Explorateur ou en temps réel.

- L’Explorateur est inclus dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.
- Prévoyez d’attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365. Les détections d’explorateur et en temps réel affichent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser les détections d’Explorateur ou en temps réel, vous devez disposer des autorisations appropriées, telles que celles accordées à un administrateur de sécurité ou à un lecteur de sécurité.

- Pour le portail Microsoft 365 Defender, vous devez disposer de l’un des rôles suivants :

  - Gestion de l’organisation
  - Administrateur de la sécurité (vous pouvez l’affecter dans le Centre d’administration Azure Active Directory (<https://aad.portal.azure.com>)
  - Lecteur de sécurité

- Par Exchange Online, vous devez disposer de l’un des rôles suivants attribués dans le Centre d’administration Exchange (EAC) ou [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell) :

  - Gestion de l’organisation
  - Gestion de l'organisation en affichage seul
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations des fonctionnalités dans Exchange Online](/exchange/permissions-exo/feature-permissions)

## <a name="differences-between-threat-explorer-and-real-time-detections"></a>Différences entre l’Explorateur de menaces et les détections en temps réel

- Le rapport *détections en temps réel* est disponible dans Defender pour Office 365 Plan 1. *L’Explorateur de* menaces est disponible dans Defender pour Office 365 Plan 2.
- Le rapport Détections en temps réel vous permet d’afficher les détections en temps réel. L’Explorateur de menaces le fait également, mais il fournit également des détails supplémentaires pour une attaque donnée.
- Un affichage *Tous les e-mails* est disponible dans l’Explorateur de menaces, mais pas dans le rapport Détections en temps réel.
- Davantage de fonctionnalités de filtrage et d’actions disponibles sont incluses dans l’Explorateur de menaces. Pour plus d’informations, consultez [Microsoft Defender pour Office 365 Description du service : Disponibilité des fonctionnalités entre Defender pour Office 365 plans](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

## <a name="other-articles"></a>Autres articles

[Examiner les e-mails avec la page d’entité Email](mdo-email-entity-page.md)
