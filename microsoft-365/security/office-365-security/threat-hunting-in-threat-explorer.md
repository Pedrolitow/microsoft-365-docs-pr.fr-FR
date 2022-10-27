---
title: Repérage des menaces dans l’Explorateur de menaces pour Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Utilisez l’Explorateur de menaces ou les détections en temps réel dans le portail Microsoft 365 Defender pour examiner les menaces et y répondre efficacement.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: a52743453c25d37c73294ff8c7a310f5a2e82623
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728948"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Repérage des menaces dans l’Explorateur de menaces pour Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Contenu de cet article :

- [Procédure pas à pas de l’Explorateur des menaces](#threat-explorer-walk-through)
- [Email enquête](#email-investigation)
- [correction Email](#email-remediation)
- [Améliorations apportées à l’expérience de chasse aux menaces](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Il fait partie d’une série de 3 articles sur **l’Explorateur de menaces (Explorateur),** la **sécurité des e-mails** et les **détections de l’Explorateur et en temps réel** (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont [Email la sécurité avec l’Explorateur de menaces](email-security-in-microsoft-defender.md) et [l’Explorateur de menaces et les détections en temps réel](real-time-detections.md).

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si votre organisation dispose [de Microsoft Defender pour Office 365](defender-for-office-365.md) et que vous disposez [des autorisations](#required-licenses-and-permissions) nécessaires, vous pouvez utiliser les détections **explorer** ou **en temps réel** pour détecter et corriger les menaces.

Dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>, accédez à **Email & collaboration**, puis choisissez **Explorateur** ou **Détections en temps réel**. Pour accéder directement à la page, utilisez <https://security.microsoft.com/threatexplorer> ou <https://security.microsoft.com/realtimereports>.

Avec ces outils, vous pouvez :

- Voir les programmes malveillants détectés par les fonctionnalités de sécurité de Microsoft 365
- Afficher l’URL de hameçonnage et cliquer sur les données de verdict
- Démarrer un processus automatisé d’investigation et de réponse à partir d’une vue dans l’Explorateur
- Examiner les e-mails malveillants, et bien plus encore

Pour plus d’informations, consultez [Email sécurité avec l’Explorateur de menaces](email-security-in-microsoft-defender.md).

Regardez cette courte vidéo pour découvrir comment rechercher et examiner les menaces basées sur les e-mails et la collaboration à l’aide de Microsoft Defender pour Office 365. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyPRU]

## <a name="threat-explorer-walk-through"></a>Procédure pas à pas de l’Explorateur des menaces

Dans Microsoft Defender pour Office 365, il existe deux plans d’abonnement : Plan 1 et Plan 2. Les outils de repérage des menaces gérés manuellement existent dans les deux plans, sous des noms différents et avec des fonctionnalités différentes.

Defender pour Office 365 Plan 1 utilise *des détections en temps réel*, qui sont un sous-ensemble de l’outil de repérage de *l’Explorateur* de menaces (également appelé Explorateur) dans Plan 2. Dans cette série d’articles, la plupart des exemples ont été créés à l’aide de l’Explorateur de menaces complet. Les administrateurs doivent tester toutes les étapes des détections en temps réel pour voir où elles s’appliquent.

Une fois que vous accédez à **l’Explorateur**, par défaut, vous accédez à la page **Programmes malveillants** , mais utilisez la liste déroulante **Affichage** pour vous familiariser avec vos options. Si vous chassez phish ou si vous creusez dans une campagne de menace, choisissez ces vues.

:::image type="content" source="../../media/view-drop-down.png" alt-text="Liste déroulante Affichage dans l’Explorateur des menaces" lightbox="../../media/view-drop-down.png":::

Une fois qu’une personne chargée des opérations de sécurité (sec ops) sélectionne les données qu’elle souhaite voir, qu’il s’agisse d’une vue étroite comme **les soumissions** utilisateur, ou d’une vue plus large, comme **Tous les e-mails**, elle peut utiliser le bouton **Expéditeur** pour filtrer davantage. N’oubliez pas de sélectionner Actualiser pour effectuer vos actions de filtrage.

:::image type="content" source="../../media/sender-drop-down.png" alt-text="Bouton Expéditeur dans l’Explorateur de menaces" lightbox="../../media/sender-drop-down.png":::

L’affinement du focus dans l’Explorateur ou la détection en temps réel peut être pensé dans les couches. Le premier est **View**. La seconde peut être considérée comme un *focus filtré*. Par exemple, vous pouvez retracer les étapes que vous avez effectuées pour trouver une menace en enregistrant vos décisions comme suit : Pour trouver le problème dans l’Explorateur, **j’ai choisi l’affichage des programmes malveillants avec un focus de filtre destinataire**. Cela facilite le suivi de vos étapes.

> [!TIP]
> Si sec ops utilise **des étiquettes** pour marquer les comptes qu’ils considèrent comme des cibles à valeur élevée, ils peuvent effectuer des sélections telles que *Phish View avec un focus de filtre Balises (inclure une plage de dates si utilisée)*. Cela leur montrera toutes les tentatives d’hameçonnage dirigées vers leurs cibles utilisateur de valeur élevée pendant un intervalle de temps (comme les dates où certaines attaques par hameçonnage se produisent beaucoup pour leur secteur d’activité).

Les affinements peuvent être effectués sur des plages de dates à l’aide des contrôles de plage de dates. Ici, vous pouvez voir l’Explorateur dans la vue **Programmes malveillants** , avec un focus de filtre **Technologie de détection** . Mais c’est le bouton **Filtre avancé** qui permet aux équipes Sec Ops de creuser en profondeur.

:::image type="content" source="../../media/advanced-filter.png" alt-text="Filtre Avancé dans l’Explorateur de menaces" lightbox="../../media/advanced-filter.png":::

Cliquez sur le **filtre Avancé** pour afficher un panneau qui permet aux chasseurs Sec Ops de créer eux-mêmes des requêtes, ce qui leur permet d’inclure ou d’exclure les informations qu’ils doivent voir. Le graphique et le tableau de la page Explorateur reflètent leurs résultats.

:::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="Résultats d’une requête" lightbox="../../media/threat-explorer-chart-table.png":::

Utilisez le bouton **Options de colonne** pour obtenir sur la table le type d’informations qui serait le plus utile :

:::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="Bouton Options de colonne mis en surbrillance" lightbox="../../media/threat-explorer-column-options.png":::

:::image type="content" source="../../media/column-options.png" alt-text="Options disponibles dans colonnes" lightbox="../../media/column-options.png":::

Dans le même mien, veillez à tester vos options d’affichage. Différents publics réagissent bien aux différentes présentations des mêmes données. Pour certains téléspectateurs, la carte **Email Origines** peut montrer qu’une menace est répandue ou discrète plus rapidement que l’option **d’affichage campagne** juste à côté. Les sec ops peuvent utiliser ces écrans pour mieux faire des points qui soulignent le besoin de sécurité et de protection, ou pour une comparaison ultérieure, afin de démontrer l’efficacité de leurs actions.

:::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="Carte origines Email" lightbox="../../media/threat-explorer-email-origin-map.png":::

:::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="Options d’affichage de campagne" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>Email enquête

Lorsque vous voyez un e-mail suspect, cliquez sur le nom pour développer le menu volant à droite. Ici, la bannière qui permet à Sec Ops de voir la [page d’entité de messagerie](mdo-email-entity-page.md) est disponible.

La page d’entité e-mail rassemble le contenu qui se trouve sous **Détails**, **Pièces jointes**, **Appareils**, mais inclut des données plus organisées. Cela inclut des éléments tels que les résultats DMARC, l’affichage en texte brut de l’en-tête d’e-mail avec une option de copie, les informations de verdict sur les pièces jointes qui ont été déclenchées de manière sécurisée et les fichiers dont les détonations ont été supprimées (peuvent inclure des adresses IP contactées et des captures d’écran de pages ou de fichiers). Les URL et leurs verdicts sont également répertoriés avec des détails similaires signalés.

Lorsque vous atteignez cette étape, la page d’entité e-mail est essentielle à l’étape finale, à savoir la *correction*.

:::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="Page d’entité de messagerie" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> Pour en savoir plus sur la page d’entité de messagerie enrichie (voir ci-dessous sous l’onglet **Analyse**), notamment les résultats des pièces jointes détonées, les résultats des URL incluses et l’aperçu Email sécurisé, cliquez [ici](mdo-email-entity-page.md).

:::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="Onglet Analyse de la page d’entité de messagerie" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>correction Email

Une fois qu’une personne Sec Ops détermine qu’un e-mail est une menace, l’étape de détection en temps réel ou de l’Explorateur suivante consiste à traiter la menace et à la corriger. Pour ce faire, revenez à l’Explorateur de menaces, cochez la case correspondant à l’e-mail problématique et utilisez le bouton **Actions** .

:::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="Bouton Actions dans l’Explorateur de menaces" lightbox="../../media/threat-explorer-email-actions-button.png":::

Ici, l’analyste peut prendre des mesures comme signaler le courrier comme courrier indésirable, hameçonnage ou programme malveillant, contacter les destinataires ou d’autres enquêtes qui peuvent inclure le déclenchement de playbooks d’investigation et de réponse automatisées (ou AIR) (si vous avez plan 2). Ou bien, le courrier peut également être signalé comme propre.

:::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="Liste déroulante Actions" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>Améliorations apportées à l’expérience de chasse aux menaces

### <a name="alert-id"></a>ID d’alerte

Lorsque vous naviguez à partir d’une alerte dans l’Explorateur de menaces, **l’affichage** est filtré par **ID d’alerte**. Cela s’applique également à la détection en temps réel. Les messages pertinents pour l’alerte spécifique et un total d’e-mails (un nombre) sont affichés. Vous serez en mesure de voir si un message faisait partie d’une alerte, ainsi que de naviguer de ce message vers l’alerte associée.

Enfin, l’ID d’alerte est inclus dans l’URL, par exemple : `https://https://security.microsoft.com/viewalerts`

:::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtre pour l’ID d’alerte" lightbox="../../media/AlertID-Filter.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Extension de la conservation et de la limite de recherche des données de l’Explorateur (et des détections en temps réel) pour les locataires d’évaluation

Dans le cadre de cette modification, les analystes pourront rechercher et filtrer les données de courrier électronique sur une période de 30 jours (ce qui est passé de sept jours) dans l’Explorateur de menaces et les détections en temps réel pour les locataires d’évaluation Defender pour Office P1 et P2. Cela n’affecte pas les locataires de production pour les clients P1 et P2 E5, où la valeur par défaut de rétention est déjà de 30 jours.

### <a name="updated-export-limit"></a>Mise à jour de la limite d’exportation

Le nombre d’enregistrements d’e-mails pouvant être exportés à partir de l’Explorateur de menaces est maintenant de 200 000 (il s’agissait de 9990). L’ensemble des colonnes qui peuvent être exportées est inchangé.

### <a name="tags-in-threat-explorer"></a>Étiquettes dans l’Explorateur de menaces

> [!NOTE]
> La fonctionnalité d’étiquettes utilisateur est en préversion et peut ne pas être disponible pour tout le monde. En outre, les préversions sont susceptibles d’être modifiées. Pour plus d’informations sur la planification des versions, consultez la feuille de route Microsoft 365.

Les étiquettes utilisateur identifient des groupes spécifiques d’utilisateurs dans Microsoft Defender pour Office 365. Pour plus d’informations sur les étiquettes, y compris la gestion des licences et la configuration, consultez [Balises utilisateur](user-tags.md).

Dans l’Explorateur de menaces, vous pouvez voir des informations sur les balises utilisateur dans les expériences suivantes.

#### <a name="email-grid-view"></a>Email affichage grille

Lorsque les analystes examinent la colonne **Étiquettes** dans la grille de courrier électronique, ils voient toutes les étiquettes qui ont été appliquées aux boîtes aux lettres de l’expéditeur ou du destinataire. Par défaut, les balises système comme les *comptes prioritaires* sont affichées en premier.

:::image type="content" source="../../media/tags-grid.png" alt-text="Étiquettes de filtre dans l’affichage Grille de messagerie" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrage

Les balises peuvent être utilisées comme filtres. Recherchez uniquement parmi les comptes prioritaires ou utilisez des scénarios de balises utilisateur spécifiques de cette façon. Vous pouvez également exclure les résultats qui ont certaines balises. Combinez des balises avec d’autres filtres et plages de dates pour limiter votre étendue d’investigation.

:::image type="content" source="../../media/tags-filter-normal.png" alt-text="Filtrer les balises." lightbox="../../media/tags-filter-normal.png":::

:::image type="content" source="../../media/tags-filter-not.png" alt-text="Balises qui n’ont pas été filtrées" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>menu volant de détails Email

Pour afficher les étiquettes individuelles de l’expéditeur et du destinataire, sélectionnez un e-mail pour ouvrir le menu volant des détails du message. Sous l’onglet **Résumé** , les balises expéditeur et destinataire sont affichées séparément. Les informations sur les étiquettes individuelles de l’expéditeur et du destinataire peuvent être exportées en tant que données CSV.

:::image type="content" source="../../media/tags-flyout.png" alt-text="Balises de détails Email" lightbox="../../media/tags-flyout.png":::

Les informations sur les étiquettes sont également affichées dans le menu volant des clics d’URL. Pour l’afficher, accédez à Phish ou Tous les Email >'onglet **URL** ou **Clics d’URL**. Sélectionnez un menu volant d’URL individuel pour afficher des détails supplémentaires sur les clics de cette URL, y compris les balises associées à ce clic.

### <a name="updated-timeline-view"></a>Affichage chronologie mis à jour

:::image type="content" source="../../media/tags-urls.png" alt-text="Balises d’URL" lightbox="../../media/tags-urls.png":::

Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Fonctionnalités étendues

### <a name="top-targeted-users"></a>Principaux utilisateurs ciblés

Top Malware Families affiche les **principaux utilisateurs ciblés** dans la section Programmes malveillants. Les utilisateurs les plus ciblés seront également étendus via les vues Phish et All Email. Les analystes pourront voir les cinq principaux utilisateurs ciblés, ainsi que le nombre de tentatives pour chaque utilisateur dans chaque vue.

Les utilisateurs des opérations de sécurité peuvent exporter la liste des utilisateurs ciblés, jusqu’à une limite de 3 000, ainsi que le nombre de tentatives effectuées, pour l’analyse hors connexion pour chaque affichage de courrier électronique. En outre, la sélection du nombre de tentatives (par exemple, 13 tentatives dans l’image ci-dessous) ouvre une vue filtrée dans l’Explorateur de menaces, afin que vous puissiez voir plus de détails sur les e-mails et les menaces pour cet utilisateur.

:::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="Les utilisateurs les plus ciblés" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Règles de transport Exchange

L’équipe des opérations de sécurité peut voir toutes les règles de transport Exchange (ou règles de flux de courrier) appliquées à un message, dans l’affichage grille Email. Sélectionnez **Options de colonne** dans la grille, puis **Ajouter une règle de transport Exchange** dans les options de colonne. L’option Règles de transport Exchange est également visible dans le menu volant **Détails** dans l’e-mail.

Les noms et GUID des règles de transport appliquées au message s’affichent. Les analystes pourront rechercher des messages en utilisant le nom de la règle de transport. Il s’agit d’une recherche CONTAINS, ce qui signifie que vous pouvez également effectuer des recherches partielles.

> [!IMPORTANT]
> La recherche de règles de transport Exchange et la disponibilité des noms dépendent du rôle spécifique qui vous est attribué. Vous devez disposer de l’un des rôles ou autorisations suivants pour afficher les noms des règles de transport et effectuer la recherche. Toutefois, même sans les rôles ou autorisations ci-dessous, un analyste peut voir l’étiquette de règle de transport et les informations GUID dans le Email Details. Les autres expériences d’affichage d’enregistrements dans Email Grids, Email les menus volants, les filtres et l’exportation ne sont pas affectées.
>
> - Exchange Online uniquement - Protection contre la perte de données : Tous
> - Exchange Online uniquement - O365SupportViewConfig : Tout
> - Microsoft Azure Active Directory ou Exchange Online - Administration de sécurité : Tous
> - Azure Active Directory ou Exchange Online - Lecteur sécurité : Tous
> - Exchange Online uniquement - Règles de transport : Tout
> - Exchange Online uniquement - Configuration View-Only : Tout
>
> Dans la grille d’e-mail, le menu volant Détails et le FICHIER CSV exporté, les ETR sont présentés avec un nom/GUID, comme indiqué ci-dessous.
>
> :::image type="content" source="../../media/ETR_Details.png" alt-text="Règles dans le transport Exchange" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Connecteurs entrants

Les connecteurs sont une collection d’instructions qui personnalisent la façon dont vos e-mails circulent vers et depuis votre organisation Microsoft 365 ou Office 365. Ils vous permettent d’appliquer des restrictions ou des contrôles de sécurité. Dans l’Explorateur de menaces, vous pouvez afficher les connecteurs liés à un e-mail et rechercher des e-mails à l’aide de noms de connecteurs.

La recherche de connecteurs est une requête CONTAINS, ce qui signifie que les recherches partielles par mot clé peuvent fonctionner :

:::image type="content" source="../../media/Connector_Details.png" alt-text="Détails du connecteur" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour Office 365](defender-for-office-365.md) pour utiliser les détections d’Explorateur ou en temps réel.

- L’Explorateur est inclus dans Defender pour Office 365 Plan 2.
- Le rapport détections en temps réel est inclus dans Defender pour Office 365 Plan 1.
- Prévoyez d’attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365. Les détections d’explorateur et en temps réel affichent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser les détections d’Explorateur ou en temps réel, vous devez disposer des autorisations suivantes :

- Dans le portail Microsoft 365 Defender :
  - Gestion de l’organisation
  - Administrateur de la sécurité (vous pouvez l’affecter dans le Centre d’administration Azure Active Directory (<https://aad.portal.azure.com>)
  - Lecteur de sécurité
- Dans Exchange Online :
  - Gestion de l’organisation
  - Gestion de l'organisation en affichage seul
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Plus d’informations

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Obtenir une vue d’ensemble des vues dans l’Explorateur de menaces (et les détections en temps réel)](threat-explorer-views.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)
- [Examiner les e-mails avec la page d’entité Email](mdo-email-entity-page.md)
