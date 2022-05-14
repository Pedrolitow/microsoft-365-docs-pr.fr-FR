---
title: Repérage des menaces dans l’Explorateur de menaces pour Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Utilisez l’Explorateur de menaces ou les détections en temps réel dans le portail Microsoft 365 Defender pour examiner et répondre efficacement aux menaces.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: efeaf3fadfed0032da90db15a6bb57f5a1fc822a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418015"
---
# <a name="threat-hunting-in-threat-explorer-for-microsoft-defender-for-office-365"></a>Repérage des menaces dans l’Explorateur de menaces pour Microsoft Defender pour Office 365

Contenu de cet article :

- [Présentation pas à pas de l’Explorateur de menaces](#threat-explorer-walk-through)
- [Enquête sur les e-mails](#email-investigation)
- [Correction de l’e-mail](#email-remediation)
- [Améliorations apportées à l’expérience de repérage des menaces](#improvements-to-threat-hunting-experience)

> [!NOTE]
> Cela fait partie d’une série de 3 articles sur **l’Explorateur de menaces,** la **sécurité des e-mails** et **les détections de l’Explorateur et en temps réel** (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont [la sécurité des e-mails avec l’Explorateur de menaces](email-security-in-microsoft-defender.md) et [l’Explorateur de menaces et les détections en temps réel](real-time-detections.md).

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si votre organisation dispose [d’Microsoft Defender pour Office 365](defender-for-office-365.md) et que vous disposez [des autorisations](#required-licenses-and-permissions), vous pouvez utiliser des détections **Explorer** ou **en temps réel** pour détecter et corriger les menaces.

Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration**, puis choisissez **Explorer** ou **Détections en temps réel**. Pour accéder directement à la page, utilisez <https://security.microsoft.com/threatexplorer> ou <https://security.microsoft.com/realtimereports>.

Avec ces outils, vous pouvez :

- Voir les programmes malveillants détectés par les fonctionnalités de sécurité Microsoft 365
- Afficher l’URL de hameçonnage et cliquer sur les données de verdict
- Démarrer un processus d’investigation et de réponse automatisé à partir d’une vue dans l’Explorateur
- Examiner les e-mails malveillants, et bien plus encore

Pour plus d’informations, consultez [Sécurité de l’e-mail avec l’Explorateur de menaces](email-security-in-microsoft-defender.md).

Regardez cette courte vidéo pour découvrir comment chasser et examiner les menaces basées sur les e-mails et la collaboration à l’aide de Microsoft Defender pour Office 365. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyPRU]

## <a name="threat-explorer-walk-through"></a>Présentation pas à pas de l’Explorateur de menaces

Dans Microsoft Defender pour Office 365, il existe deux plans d’abonnement : Plan 1 et Plan 2. Les outils de chasse aux menaces gérés manuellement existent dans les deux plans, sous des noms différents et avec des fonctionnalités différentes.

Defender pour Office 365 Plan 1 utilise des *détections en temps réel*, qui est un sous-ensemble de l’outil de chasse de *l’Explorateur de menaces* (également appelé *Explorateur*) dans plan 2. Dans cette série d’articles, la plupart des exemples ont été créés à l’aide de l’Explorateur de menaces complet. Les administrateurs doivent tester toutes les étapes des détections en temps réel pour voir où ils s’appliquent.

Une fois que vous êtes passé à **l’Explorateur**, par défaut, vous arrivez sur la page **Programmes malveillants** , mais utilisez la liste déroulante **Affichage** pour vous familiariser avec vos options. Si vous chassez phish ou si vous vous plongez dans une campagne de menaces, choisissez ces vues.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/view-drop-down.png" alt-text="Liste déroulante Affichage dans l’Explorateur de menaces" lightbox="../../media/view-drop-down.png":::

Une fois qu’une personne chargée des opérations de sécurité (Sec Ops) sélectionne les données qu’elle souhaite voir, si l’étendue est étroite comme les **soumissions d’utilisateurs** ou une vue plus large, comme **Tous les e-mails**, elle peut utiliser le bouton **Expéditeur pour filtrer** davantage. N’oubliez pas de sélectionner Actualiser pour effectuer vos actions de filtrage.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/sender-drop-down.png" alt-text="Bouton Expéditeur dans l’Explorateur de menaces" lightbox="../../media/sender-drop-down.png":::

Le focus d’affinement dans l’Explorateur ou la détection en temps réel peut être pensé en couches. La première est **Affichage**. La seconde peut être considérée comme un *focus filtré*. Par exemple, vous pouvez retracer les étapes que vous avez suivies pour rechercher une menace en enregistrant vos décisions comme suit : pour trouver le problème dans l’Explorateur, **j’ai choisi l’affichage Programmes malveillants avec un focus de filtre destinataire**. Cela facilite la retracation de vos étapes.

> [!TIP]
> Si Sec Ops utilise des **balises** pour marquer les comptes qu’ils considèrent comme des cibles à valeur élevée, ils peuvent effectuer des sélections telles que *Phish View avec un focus de filtre Balises (inclure une plage de dates si elle est utilisée).* Cela leur montrera toutes les tentatives de hameçonnage dirigées vers leurs cibles d’utilisateurs à valeur élevée pendant un intervalle de temps (comme les dates où certaines attaques par hameçonnage se produisent beaucoup pour leur industrie).

Des affinements peuvent être effectués sur des plages de dates à l’aide des contrôles de plage de dates. Ici, vous pouvez voir l’Explorateur en mode **Programmes malveillants** , avec un focus de filtre **de technologie de détection** . Mais c’est le bouton **Filtre avancé** qui permet aux équipes Sec Ops d’explorer en profondeur.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/advanced-filter.png" alt-text="Filtre avancé dans l’Explorateur de menaces" lightbox="../../media/advanced-filter.png":::

Le fait de cliquer sur le **filtre avancé** affiche un panneau qui permet aux chasseurs sec ops de créer eux-mêmes des requêtes, ce qui leur permet d’inclure ou d’exclure les informations dont ils ont besoin pour voir. Le graphique et le tableau de la page Explorateur reflètent leurs résultats.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-chart-table.png" alt-text="Résultats d’une requête" lightbox="../../media/threat-explorer-chart-table.png":::

Utilisez le bouton **Options de colonne** pour obtenir le type d’informations sur la table qui serait le plus utile :

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-column-options.png" alt-text="Bouton Options de colonne mis en surbrillance" lightbox="../../media/threat-explorer-column-options.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/column-options.png" alt-text="Options disponibles dans colonnes" lightbox="../../media/column-options.png":::

Dans la même mien, veillez à tester vos options d’affichage. Différents publics réagiront bien aux différentes présentations des mêmes données. Pour certains observateurs, la carte **Origines de l’e-mail** peut montrer qu’une menace est généralisée ou discrète plus rapidement que l’option d’affichage **Campagne** juste à côté. Sec Ops peut utiliser ces affichages pour mieux faire ressortir les points qui soulignent le besoin de sécurité et de protection, ou pour une comparaison ultérieure, pour démontrer l’efficacité de leurs actions.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-origin-map.png" alt-text="Carte Origines de l’e-mail" lightbox="../../media/threat-explorer-email-origin-map.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-campaign-display.png" alt-text="Options d’affichage de la campagne" lightbox="../../media/threat-explorer-campaign-display.png":::

### <a name="email-investigation"></a>Enquête sur les e-mails

Lorsque vous voyez un e-mail suspect, cliquez sur le nom pour développer le menu volant à droite. Ici, la bannière qui permet aux opérations sec de voir la [page d’entité de messagerie](mdo-email-entity-page.md) est disponible.

La page d’entité d’e-mail rassemble le contenu qui se trouve sous **Détails**, **Pièces jointes**, **Appareils**, mais inclut des données plus organisées. Cela inclut des éléments tels que les résultats DMARC, l’affichage en texte brut de l’en-tête d’e-mail avec une option de copie, les informations de verdict sur les pièces jointes qui ont été détonées en toute sécurité et les fichiers supprimés (peuvent inclure les adresses IP qui ont été contactées et les captures d’écran de pages ou de fichiers). Les URL et leurs verdicts sont également répertoriés avec des détails similaires.

Lorsque vous atteignez cette étape, la page de l’entité de messagerie est critique pour la dernière étape : *la correction*.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-entity-page.png" alt-text="Page d’entité d’e-mail" lightbox="../../media/threat-explorer-email-entity-page.png":::

> [!TIP]
> Pour en savoir plus sur la page d’entité de messagerie enrichie (voir ci-dessous sous l’onglet **Analyse** ), notamment les résultats des pièces jointes détonées, les résultats des URL incluses et la préversion de l’e-mail sécurisé, cliquez [ici](mdo-email-entity-page.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-analysis-tab.png" alt-text="Onglet Analyse de la page d’entité d’e-mail" lightbox="../../media/threat-explorer-analysis-tab.png":::

### <a name="email-remediation"></a>Correction de l’e-mail

Une fois qu’une personne d’opérations sec détermine qu’un e-mail est une menace, l’étape suivante de détection de l’Explorateur ou en temps réel traite de la menace et la corrige. Pour ce faire, revenez à l’Explorateur de menaces, activez la case à cocher correspondant à l’e-mail du problème et utilisez le bouton **Actions** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-button.png" alt-text="Bouton Actions dans l’Explorateur de menaces" lightbox="../../media/threat-explorer-email-actions-button.png":::

Ici, l’analyste peut prendre des mesures telles que signaler le courrier comme courrier indésirable, hameçonnage ou programme malveillant, contacter des destinataires ou effectuer des investigations supplémentaires qui peuvent inclure le déclenchement de playbooks d’investigation et de réponse automatisées (ou AIR) (si vous avez le plan 2). Ou, le courrier peut également être signalé comme propre.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/threat-explorer-email-actions-drop-down.png" alt-text="Liste déroulante Actions" lightbox="../../media/threat-explorer-email-actions-drop-down.png":::

## <a name="improvements-to-threat-hunting-experience"></a>Améliorations apportées à l’expérience de repérage des menaces

### <a name="alert-id"></a>ID d’alerte

Lorsque vous naviguez à partir d’une alerte vers l’Explorateur de menaces, la **vue** est filtrée par **ID d’alerte**. Cela s’applique également dans la détection en temps réel. Les messages pertinents pour l’alerte spécifique et un total d’e-mails (un nombre) sont affichés. Vous pourrez voir si un message faisait partie d’une alerte, ainsi que naviguer entre ce message et l’alerte associée.

Enfin, l’ID d’alerte est inclus dans l’URL, par exemple : `https://https://security.microsoft.com/viewalerts`

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-Filter.png" alt-text="Filtre pour l’ID d’alerte" lightbox="../../media/AlertID-Filter.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/AlertID-DetailsFlyout.png" alt-text="L’ID d’alerte dans le menu volant détaillé" lightbox="../../media/AlertID-DetailsFlyout.png":::

### <a name="extending-explorer-and-real-time-detections-data-retention-and-search-limit-for-trial-tenants"></a>Extension de la conservation des données de l’Explorateur (et des détections en temps réel) et de la limite de recherche pour les locataires d’essai

Dans le cadre de cette modification, les analystes pourront rechercher et filtrer les données de courrier électronique sur 30 jours (au nombre de sept jours) dans l’Explorateur de menaces et les détections en temps réel pour les clients d’essai Defender pour Office P1 et P2. Cela n’a aucun impact sur les locataires de production pour les clients P1 et P2 E5, où la rétention par défaut est déjà de 30 jours.

### <a name="updated-export-limit"></a>Limite d’exportation mise à jour

Le nombre d’enregistrements d’e-mails pouvant être exportés à partir de l’Explorateur de menaces est désormais de 200 000 (9990). L’ensemble des colonnes pouvant être exportées est inchangé.

### <a name="tags-in-threat-explorer"></a>Balises dans l’Explorateur de menaces

> [!NOTE]
> La fonctionnalité de balises utilisateur est en préversion et peut ne pas être disponible pour tout le monde. En outre, les préversions sont susceptibles d’être modifiées. Pour plus d’informations sur la planification de publication, consultez la feuille de route Microsoft 365.

Les balises utilisateur identifient des groupes d’utilisateurs spécifiques dans Microsoft Defender pour Office 365. Pour plus d’informations sur les balises, notamment les licences et la configuration, consultez [Balises utilisateur](user-tags.md).

Dans l’Explorateur de menaces, vous pouvez voir des informations sur les balises utilisateur dans les expériences suivantes.

#### <a name="email-grid-view"></a>Affichage grille des e-mails

Lorsque les analystes examinent la colonne **Étiquettes** dans la grille de messagerie, ils voient toutes les balises qui ont été appliquées aux boîtes aux lettres des expéditeurs ou des destinataires. Par défaut, les balises système telles que les *comptes de priorité* sont affichées en premier.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-grid.png" alt-text="Balises de filtre dans l’affichage grille du courrier électronique" lightbox="../../media/tags-grid.png":::

#### <a name="filtering"></a>Filtrage

Les balises peuvent être utilisées comme filtres. Recherchez uniquement parmi les comptes prioritaires ou utilisez des scénarios de balises utilisateur spécifiques de cette façon. Vous pouvez également exclure les résultats qui ont certaines balises. Combinez des balises avec d’autres filtres et plages de dates pour affiner votre étendue d’investigation.

[![Filtrer les balises.](../../media/tags-filter-normal.png)](../../media/tags-filter-normal.png#lightbox)

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-filter-not.png" alt-text="Balises qui n’ont pas été filtrées" lightbox="../../media/tags-filter-not.png":::

#### <a name="email-detail-flyout"></a>Menu volant des détails de l’e-mail

Pour afficher les balises individuelles de l’expéditeur et du destinataire, sélectionnez un e-mail pour ouvrir le menu volant des détails du message. Sous l’onglet **Résumé** , les balises d’expéditeur et de destinataire sont affichées séparément. Les informations sur les balises individuelles pour l’expéditeur et le destinataire peuvent être exportées en tant que données CSV.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-flyout.png" alt-text="Balises Détails de l’e-mail" lightbox="../../media/tags-flyout.png":::

Les informations de balises sont également affichées dans le menu volant des clics d’URL. Pour le voir, accédez à Phish ou Tous les e-mails > **url ou** l’onglet **Clics d’URL** . Sélectionnez un menu volant d’URL individuel pour afficher des détails supplémentaires sur les clics pour cette URL, y compris les balises associées à ce clic.

### <a name="updated-timeline-view"></a>Affichage chronologie mis à jour

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/tags-urls.png" alt-text="Balises d’URL" lightbox="../../media/tags-urls.png":::
>
Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=UoVzN0lYbfY&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=4).

## <a name="extended-capabilities"></a>Fonctionnalités étendues

### <a name="top-targeted-users"></a>Principaux utilisateurs ciblés

Les principales familles de programmes malveillants affichent les **utilisateurs les plus ciblés** dans la section Programmes malveillants. Les utilisateurs les plus ciblés seront également étendus via phish et toutes les vues e-mail. Les analystes pourront voir les cinq premiers utilisateurs ciblés, ainsi que le nombre de tentatives pour chaque utilisateur dans chaque vue.

Les personnes chargées des opérations de sécurité peuvent exporter la liste des utilisateurs ciblés, jusqu’à une limite de 3 000, ainsi que le nombre de tentatives effectuées, pour l’analyse hors connexion pour chaque affichage de messagerie. En outre, la sélection du nombre de tentatives (par exemple, 13 tentatives dans l’image ci-dessous) ouvre une vue filtrée dans l’Explorateur de menaces, afin que vous puissiez voir plus de détails sur les e-mails et les menaces pour cet utilisateur.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Top_Targeted_Users.png" alt-text="Les utilisateurs les plus ciblés" lightbox="../../media/Top_Targeted_Users.png":::

### <a name="exchange-transport-rules"></a>Exchange règles de transport

L’équipe chargée des opérations de sécurité pourra voir toutes les règles de transport Exchange (ou règles de flux de courrier) appliquées à un message, dans la vue Grille e-mail. Sélectionnez **Options de colonne** dans la grille, puis **ajoutez Exchange règle de transport** à partir des options de colonne. L’option Exchange règles de transport est également visible dans le menu volant **Détails** dans l’e-mail.

Les noms et guidons des règles de transport appliquées au message s’affichent. Les analystes pourront rechercher des messages à l’aide du nom de la règle de transport. Il s’agit d’une recherche CONTAINS, ce qui signifie que vous pouvez également effectuer des recherches partielles.

> [!IMPORTANT]
> Exchange la recherche de règles de transport et la disponibilité des noms dépendent du rôle spécifique qui vous est attribué. Vous devez disposer de l’un des rôles ou autorisations suivants pour afficher les noms des règles de transport et effectuer une recherche. Toutefois, même sans les rôles ou autorisations ci-dessous, un analyste peut voir l’étiquette de règle de transport et les informations GUID dans les détails de l’e-mail. Les autres expériences d’affichage des enregistrements dans les grilles d’e-mail, les menus volants d’e-mail, les filtres et l’exportation ne sont pas affectées.
>
> - Exchange Online uniquement - Protection contre la perte de données : Tout
> - Exchange Online uniquement - O365SupportViewConfig: All
> - Microsoft Azure Active Directory ou Exchange Online - Administrateur de sécurité : tout
> - Azure Active Directory ou Exchange Online - Lecteur sécurité : tout
> - Exchange Online uniquement - Règles de transport : tous
> - Exchange Online uniquement - Configuration View-Only : tout
>
> Dans la grille d’e-mail, le menu volant Détails et le fichier CSV exporté, les ETR sont présentés avec un nom/GUID, comme indiqué ci-dessous.
>
> > [!div class="mx-imgBorder"]
> > :::image type="content" source="../../media/ETR_Details.png" alt-text="Règles dans Exchange Transport" lightbox="../../media/ETR_Details.png":::

### <a name="inbound-connectors"></a>Connecteurs entrants

Les connecteurs sont une collection d’instructions qui personnalisent la façon dont vos e-mails circulent vers et depuis votre Microsoft 365 ou Office 365 organisation. Ils vous permettent d’appliquer des restrictions ou des contrôles de sécurité. Dans l’Explorateur de menaces, vous pouvez afficher les connecteurs liés à un e-mail et rechercher des e-mails à l’aide de noms de connecteurs.

La recherche de connecteurs est une requête CONTAINS, ce qui signifie que les recherches de mots clés partiels peuvent fonctionner :

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/Connector_Details.png" alt-text="Détails du connecteur" lightbox="../../media/Connector_Details.png":::

## <a name="required-licenses-and-permissions"></a>Licences et autorisations requises

Vous devez avoir [Microsoft Defender pour Office 365](defender-for-office-365.md) pour utiliser des détections d’Explorateur ou en temps réel.

- L’Explorateur est inclus dans Defender pour Office 365 Plan 2.
- Le rapport de détections en temps réel est inclus dans Defender pour Office 365 Plan 1.
- Prévoyez d’attribuer des licences à tous les utilisateurs qui doivent être protégés par Defender pour Office 365. Les détections d’explorateur et en temps réel affichent les données de détection pour les utilisateurs sous licence.

Pour afficher et utiliser des détections d’Explorateur ou en temps réel, vous devez disposer des autorisations suivantes :

- Dans le portail Microsoft 365 Defender :
  - Gestion de l’organisation
  - Administrateur de sécurité (cela peut être attribué dans le centre d’administration Azure Active Directory (<https://aad.portal.azure.com>)
  - Lecteur de sécurité
- Dans Exchange Online :
  - Gestion de l’organisation
  - Afficher uniquement la gestion de l’organisation
  - Afficher uniquement les destinataires
  - Gestion de la conformité

Pour en savoir plus sur les rôles et les autorisations, consultez les ressources suivantes :

- [Autorisations dans le Portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md)
- [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)

## <a name="more-information"></a>Informations supplémentaires

- [Rechercher et d’examiner l’e-mail malveillant qui a été distribué](investigate-malicious-email-that-was-delivered.md)
- [Afficher les fichiers malveillants détectés dans SharePoint Online, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)
- [Obtenir une vue d’ensemble des vues dans l’Explorateur de menaces (et les détections en temps réel)](threat-explorer-views.md)
- [Rapport sur l’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)
- [Examen et réponses automatisés dans Protection Microsoft contre les menaces](automated-investigation-response-office.md)
- [Examiner les e-mails à l’aide de la page Entité de messagerie](mdo-email-entity-page.md)
