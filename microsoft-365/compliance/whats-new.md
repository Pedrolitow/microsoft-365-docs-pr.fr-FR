---
title: Nouveautés dans la conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: brendonb
author: brendonb
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Qu’il s’agisse d’ajouter de nouvelles solutions au centre de conformité, de mettre à jour des fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et actualisée, Microsoft 365 vous aide à rester informé de la mise en conformité en perpétuelle évolution. Découvrez ce que nous avons fait dans ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c33e136be55ea60f1e5954d4713b219045b1f0eb
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48398525"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Qu’il s’agisse d’ajouter de nouvelles solutions au [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md), de mettre à jour des fonctionnalités existantes en fonction de vos commentaires ou de déployer une documentation actualisée et actualisée, Microsoft 365 vous aide à rester informé de la mise en conformité en perpétuelle évolution. Jetez un œil aux nouveautés de la conformité de Microsoft 365 dès aujourd’hui. 

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à des vitesses différentes à nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à la [version ciblée](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365).


> [!TIP]
> Que se passe-t-il dans d’autres centres d’administration ? Consultez les articles suivants :<br>[Nouveautés du centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/whats-new-in-preview?view=o365-worldwide)<br>[Nouveautés du centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)<br>[Nouveautés de la protection Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)<br><br>
Consultez la feuille de [route de microsoft 365](https://www.microsoft.com/en-us/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités de Microsoft 365 qui ont été lancées, qui sont déployées, qui sont en cours de développement, qui ont été annulées ou qui ont déjà été publiées.

## <a name="august-2020"></a>Août 2020

### <a name="spotlight-insider-risk-and-communication-compliance-updates"></a>Actualités : mises à jour de la conformité des communications et des risques internes

Plusieurs fonctionnalités nouvelles et améliorées ont atteint la préversion publique ce mois-ci :

**Gestion des risques initiés**

- Consultez nos six nouveaux [modèles de stratégie](insider-risk-management-policies.md#policy-templates):
    - Fuites de données par les utilisateurs prioritaires
    - Fuites de données par les utilisateurs mécontents
    - Violations de stratégie de sécurité générale
    - Violations de stratégie de sécurité en faisant départion des utilisateurs
    - Violations de stratégie de sécurité par utilisateurs prioritaires
    - Violations de stratégie de sécurité par des utilisateurs mécontents

- L’intégration à [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) vous permet d’importer et de filtrer les alertes Microsoft Defender ATP pour les activités détectées par les stratégies créées à partir des nouveaux modèles de stratégie de violation de sécurité. Il existe également un [paramètre de risque d’initié](insider-risk-management-settings.md#microsoft-defender-advanced-threat-protection-preview) connexe dans lequel vous pouvez choisir d’importer des alertes de sécurité vers la gestion des risques initiés en fonction de l’état de triage des alertes Microsoft Defender ATP.

    > [!NOTE]
    > Pour tirer parti de l’intégration de Microsoft Defender ATP (y compris les nouveaux modèles de violation de la stratégie de sécurité), vous devez disposer de Microsoft Defender ATP configuré dans votre organisation. Vous devrez également activer Microsoft Defender ATP pour l’intégration de la gestion des risques initiés en [configurant des fonctionnalités avancées dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).
 
- Personnaliser les seuils des indicateurs lors [de la création d’une stratégie](insider-risk-management-policies.md#create-a-new-policy).
- Configurez des [groupes d’utilisateurs prioritaires](insider-risk-management-settings.md#priority-user-groups-preview) pour définir les utilisateurs de votre organisation dont l’activité nécessite un examen plus approfondi en fonction de facteurs tels que leur position, le niveau d’accès aux informations sensibles ou l’historique des risques.
- Utilisez les API activité de gestion d’Office 365 pour exporter les détails de l' [alerte de risque Insider](insider-risk-management-settings.md#export-alerts-preview) vers d’autres applications que votre organisation peut utiliser pour gérer ou agréger des données sur les risques internes.
- Les nouveaux [paramètres de domaine](insider-risk-management-settings.md#domains-preview) vous permettent de définir et de contrôler les niveaux de risque de l’activité dans des domaines spécifiques.

**Conformité des communications**

- Lors [de l’examen des messages d’une alerte](communication-compliance-investigate-remediate.md#step-3-decide-on-a-remediation-action), vous pouvez supprimer les messages inappropriés dans les canaux Microsoft Teams, 1:1 et les conversations de groupe. Les messages supprimés et le contenu sont remplacés par un Conseil de stratégie qui explique qu’il a été supprimé en raison du contenu sensible.
- Nouveaux [rôles de communication](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance) (ceux-ci seront également inclus dans les nouveaux groupes de rôles de conformité de communication publié en septembre).
- Nouvelle expérience des paramètres de conformité de la communication incluant les paramètres des modèles de [confidentialité](communication-compliance-feature-reference.md#privacy-preview) et d' [avis](communication-compliance-feature-reference.md#notice-templates).
- De nouveaux [classifieurs](communication-compliance-feature-reference.md#classifiers) pour vous aider à détecter les images adultes, racy et Gory.
- Nouvelle notification « pattern detected » qui s’affiche lors [de l’examen des messages d’une alerte](communication-compliance-investigate-remediate.md#step-2-examine-the-message-details) vous informe des instances qui se produisent de même comportement par un utilisateur.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Pour les clients du secteur public des États-Unis (GCC, GCC-HC et DoD), les étiquettes de confidentialité ne sont actuellement prises en charge que pour le client et l’analyseur d’étiquetage unifié d’Azure Information Protection. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Description du service public Azure Information Protection Premium](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).
- Vous pouvez désormais [utiliser la sécurité & Centre de conformité PowerShell](create-sensitivity-labels.md#use-powershell-for-sensitivity-labels-and-their-policies) pour créer et configurer tous les paramètres que vous voyez dans votre centre d’administration d’étiquetage. Cela signifie que, en plus de l’utilisation de PowerShell pour les paramètres qui ne sont pas disponibles dans le centre d’administration d’étiquetage, vous pouvez désormais entièrement créer un script pour la création et la maintenance des étiquettes de sensibilité et des stratégies d’étiquette de sensibilité.

### <a name="records-management-content-overhaul"></a>Gestion des enregistrements : révision du contenu

Nouveaux documents couvrant les étapes de déploiement, le marquage de contenu en tant qu’enregistrements et la gestion des versions des enregistrements :

- [Prise en main de la gestion des enregistrements](get-started-with-records-management.md)
- [Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md)
- [Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md)

### <a name="retention-labels--policies"></a>Étiquettes de rétention & stratégies

L’activité d’administration liée à la rétention est désormais enregistrée et disponible dans le journal d’audit. Pour obtenir la liste complète, voir [Politiques de rétention et activités d’étiquette de rétention](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

- Lors [de l’ajout d’une collection à un ensemble de vérification](add-data-to-review-set.md#define-options-to-scope-your-collection-for-review), vous pouvez désormais inclure des pièces jointes modernes (également appelées « pièces jointes dans le Cloud ») et des versions de document SharePoint.
- Nouvelle [expérience d’exportation de téléchargement direct](export-documents-from-review-set.md), éliminant la nécessité d’utiliser l’Explorateur de stockage Azure pour télécharger du contenu de cas.


## <a name="july-2020"></a>Juillet 2020

### <a name="spotlight-on-help-docs"></a>Actualités sur les documents d’aide

Pour vous aider à comprendre quelles solutions de conformité sont utilisées pour protéger et régir les données sensibles de votre organisation, nous avons créé deux nouvelles pages d’accueil présentant la façon dont les solutions fonctionnent ensemble pour atteindre ces objectifs, notamment des liens vers des documents connexes afin que vous puissiez approfondir votre travail.

[Microsoft information protection dans Microsoft 365](protect-information.md)<br>
[Microsoft information Governance dans Microsoft 365](manage-Information-governance.md)

### <a name="advanced-ediscovery-add-non-custodial-data-sources-to-your-cases"></a>Découverte électronique avancée : ajout de sources de données non-privatives à vos cas

Ajouter des données à un cas sans avoir à l’associer à un dépositaire (connu sous le nom de [sources de données non privatives de cœur](non-custodial-data-sources.md)). Si vous devez placer ces données non privatives de place, vous pourrez le faire à l’aide de notre nouvelle fonctionnalité d’indexation avancée.

### <a name="data-connectors-hr-connector-enhancements"></a>Connecteurs de données : améliorations du connecteur RH

(En mode Aperçu) Une nouvelle version du [connecteur RH](import-hr-data.md) vous permet d’importer des données relatives aux modifications de niveau de travail, aux évaluations de performances et aux plans d’amélioration des performances. Ces données peuvent ensuite être utilisées dans plusieurs [stratégies de risque d’initié](insider-risk-management-policies.md) pour détecter les activités associées.

### <a name="retention-labels-new-support-for-email"></a>Étiquettes de rétention : nouvelle prise en charge pour le courrier électronique

Vous pouvez désormais créer une [étiquette de rétention](retention.md#retention-labels) pour commencer à conserver des messages électroniques en fonction de la façon dont les messages ont été étiquetés. Ceci ne s’applique pas aux éléments de calendrier, qui seront conservés en fonction de la date d’envoi de l’élément.

### <a name="sensitivity-labels-new-feature-and-an-improvement"></a>Étiquettes de sensibilité : nouvelle fonctionnalité et amélioration

- (En mode Aperçu) Lors de la configuration des paramètres de chiffrement pour une étiquette, recherchez la nouvelle option permettant d’utiliser le [chiffrement à double clé](encryption-sensitivity-labels.md#double-key-encryption) pour protéger davantage les fichiers étiquetés et les e-mails.
- Lors de la création ou de la suppression d’étiquettes de confidentialité ou la création, la modification ou la suppression de leurs stratégies d’étiquette, les modifications sont synchronisées dans une heure à l’ensemble des utilisateurs, des applications et des services.

## <a name="june-2020"></a>Juin 2020

### <a name="spotlight-new-data-connectors-hit-preview"></a>Spotlight : la nouvelle version d’évaluation des connecteurs de données

En s’appuyant sur notre promesse pour vous aider à importer des données de plusieurs sources tierces dans Microsoft 365, nous sommes heureux d’annoncer la version préliminaire de deux connecteurs de données supplémentaires :

- [Message Bloomberg](archive-bloomberg-message-data.md). Importez et archivez les données de messagerie électronique des services financiers à partir de l’outil de collaboration message Bloomberg. Une fois que les données sont stockées dans des boîtes aux lettres, vous pouvez accéder aux données et les utiliser dans des fonctionnalités de conformité telles que la conservation pour litige, la recherche de contenu, l’archivage inaltérable, l’audit, la conformité de la communication et les stratégies de rétention.
- [Chat Ice](archive-icechat-data.md). Importez et archivez les données de conversation des services financiers à partir de l’outil de collaboration chat ICE. Une fois que les données sont stockées dans des boîtes aux lettres, vous pouvez accéder aux données et les utiliser dans des fonctionnalités de conformité telles que la mise en attente pour litige, eDiscovery, l’archivage, l’audit, la conformité de la communication et les stratégies de rétention.

### <a name="compliance-score--compliance-manager-the-hits-keep-coming"></a>Score de conformité & le gestionnaire de conformité : les accès continuent de venir

Les mises à jour de juin incluent une nouvelle vue d’analyse de l’évaluation dans le [score de conformité](compliance-score.md). Surveiller la progression du contrôle, ajouter, supprimer des évaluations directement à partir du score de conformité, et bien plus encore.

Vous souhaitez rester informé des mises à jour du score de conformité et du gestionnaire de conformité ? Ajoutez un signet aux [notes de publication du score de conformité](compliance-score-release-notes.md) et vérifiez-le régulièrement.

## <a name="may-2020"></a>Mai 2020

### <a name="spotlight-data-classification-is-officially-released"></a>Actualités : la classification des données est officiellement publiée

La classification des données, appelée «[connaissance de vos données](data-classification-overview.md)», les fonctionnalités (analyse, Explorateur de contenu et Explorateur d’activités) ont été graduées de la phase d’évaluation et sont disponibles pour toutes les organisations. Des éléments et des outils puissants peuvent vous aider à découvrir et à évaluer la façon dont les informations et les étiquettes sensibles (rétention et sensibilité) sont utilisées dans le contenu au sein de votre organisation. Passez en revue le contenu qui contient des informations sensibles ou des étiquettes sont appliquées, Explorez l’activité des étiquettes dans les emplacements Microsoft 365, créez des types d’informations sensibles personnalisés, et bien plus encore.

Effectuez une visite vidéo...

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

### <a name="trainable-classifiers-a-fix-and-a-feature"></a>Classifieur de formation : un correctif et une fonctionnalité

Peut apporter davantage d’améliorations aux classifieurs en formation :

- Un correctif en fonction de vos commentaires : lorsque vous amorcez et que vous exercez un classificateur personnalisé, vous n’avez plus besoin d’entrer manuellement les URL de site et les chemins d’accès aux dossiers SharePoint. Vous pouvez désormais choisir parmi une liste pré-renseignée de sites et de dossiers.
- Nouvelle fonctionnalité : lors de la création d’une étiquette de sensibilité et de la configuration des paramètres d’étiquetage automatique pour les applications Office, vous pouvez désormais appliquer automatiquement (ou recommander aux utilisateurs d’appliquer) l’étiquette au contenu qui correspond aux classifieurs pouvant être formés. [En savoir plus](apply-sensitivity-label-automatically.md#configuring-trainable-classifiers-for-a-label)

### <a name="communication-compliance-yammer-support-is-here"></a>Conformité de la communication : la prise en charge de Yammer est ici

Les messages privés et les conversations de la communauté publique dans Yammer sont pris en charge dans les stratégies de conformité de communication. Yammer est un canal facultatif qui doit être en [mode natif](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) pour prendre en charge l’analyse de messages et de pièces jointes.

### <a name="data-loss-prevention-new-sharing-restriction"></a>Protection contre la perte de données : nouvelle restriction de partage

Lors de la configuration d’une stratégie DLP pour protéger le contenu dans SharePoint ou OneDrive, vous pouvez désormais configurer l’action « restreindre l’accès au contenu » pour bloquer les personnes qui ont accès au contenu via l’option «[tout le monde avec le lien](https://support.microsoft.com/office/share-files-outside-your-organization-with-anyone-links-53e91027-fb8e-4a6e-a3e4-5df4be32e38a)».

### <a name="insider-risk-management-tailor-your-alert-volume"></a>Gestion des risques initiés : personnaliser le volume des alertes

Les activités de l’utilisateur détectées par les stratégies de risque d’initié se voient attribuer une note de risque spécifique, qui détermine à son tour la gravité de l’alerte (faible, moyenne, haute). Par défaut, Microsoft 365 génère une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais avec le nouveau [paramètre de volume d’alerte](insider-risk-management-settings.md#alert-volume), vous pouvez augmenter ou diminuer le volume en fonction de vos besoins.

### <a name="pst-import-new-region-supported"></a>Importation des fichiers PST : nouvelle région prise en charge

Le chargement réseau est désormais disponible dans les Émirats Arabes Unis.

### <a name="sensitivity-labels-new-privacy-option"></a>Étiquettes de sensibilité : nouvelle option de confidentialité

Lors de la configuration des [paramètres de site et de groupe](sensitivity-labels-teams-groups-sites.md#how-to-configure-site-and-group-settings) pour une étiquette, vous pouvez maintenant définir l’option de confidentialité sur **aucune-laisser l’utilisateur choisir qui peut accéder au site**. Cela est utile lorsque vous souhaitez protéger le contenu du conteneur à l’aide d’une étiquette de sensibilité, tout en laissant les utilisateurs configurer eux-mêmes le paramètre de confidentialité.

## <a name="april-2020"></a>Avril 2020

### <a name="records-management-overhauland-a-new-addition"></a>Gestion des enregistrements : révision... et un nouvel ajout

April inclut quelques mises à jour clés de notre solution de gestion des enregistrements :

- La section « gestion des enregistrements » est désormais entièrement disponible dans le centre de conformité. Tirez parti des interfaces utilisateur et des fonctionnalités mises à jour pour le plan de fichiers, les étiquettes de rétention et les stratégies d’étiquette, les événements et la destruction.
- En parlant de disposition, nous avons également déployé des [preuves d’imposition](disposition.md#disposition-of-records) pour les enregistrements dans SharePoint et OneDrive. Vous pouvez maintenant voir une liste d’éléments dans les emplacements qui ont été supprimés automatiquement ou après une révision de destruction.

### <a name="sensitivity-labels-preview-auto-labeling-policies"></a>Étiquettes de sensibilité : aperçu des stratégies d’étiquetage automatique

Avec les stratégies d’étiquetage automatique, vous pouvez désormais appliquer automatiquement des étiquettes de confidentialité aux documents SharePoint et OneDrive qui sont déjà enregistrés (« données sur REST ») et aux courriers électroniques déjà envoyés ou reçus (« courrier électronique en transit »). Étant donné que cette étiquette est appliquée par les services plutôt que par les applications, vous n’avez pas à vous soucier des applications dont disposent les utilisateurs et de la version.

Cette fonctionnalité étend le marquage côté client existant qui est déjà inclus dans les paramètres « étiquetage automatique pour les applications Office » lorsque vous créez une étiquette de critère de diffusion. Pour vous familiariser avec les différences et les avantages des deux options d’étiquetage automatique, consultez l' [article mis à jour](apply-sensitivity-label-automatically.md).

## <a name="march-2020"></a>Mars 2020

### <a name="introducing-advanced-audit"></a>Présentation de l’audit avancé

[L’audit avancé dans Microsoft 365](advanced-audit.md) introduit de nouvelles fonctionnalités d’audit qui peuvent aider votre organisation à effectuer des recherches d’investigation et de conformité. Les points forts incluent la rétention à long terme des journaux d’audit, des stratégies de rétention de journal d’audit personnalisées, une nouvelle action d’audit de boîte aux lettres *MailItemsAccessed* et l’introduction d’une nouvelle limite de limitation au niveau du client, qui fournit à votre organisation son propre quota de bande passante entièrement alloué pour accéder à vos données d’audit.

### <a name="compliance-score--compliance-manager-preview-the-latest-enhancements"></a>Score de conformité & le gestionnaire de conformité : aperçu des dernières améliorations

Les mises à jour de clés pour cette version d’évaluation incluent :

- Processus simplifié de création et de modification de modèles
- Notification de versioning et contrôle pour les modèles et les actions
- Synchronisation des actions courantes entre les groupes
- Prise en charge des langues désormais étendues au chinois (simplifié), chinois (traditionnel), français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol

En savoir plus sur le [score de conformité](compliance-score.md) et le [Gestionnaire de conformité](compliance-manager-overview.md)

### <a name="sensitivity-labels-support-for-labeling-office-files-in-sharepoint-and-onedrive-preview"></a>Étiquettes de sensibilité : prise en charge des fichiers Office d’étiquetage dans SharePoint et OneDrive (aperçu)

L’activation de l’aperçu permet aux utilisateurs d’appliquer des étiquettes de confidentialité dans Office sur le Web. Ils pourront voir le bouton **sensibilité** sur le ruban et le nom d’étiquette appliqué sur la barre d’État. En outre, s’ils utilisent des applications de bureau pour étiqueter et enregistrer leurs fichiers sur SharePoint ou OneDrive, Microsoft 365 sera en mesure de traiter le contenu de ces fichiers si les paramètres de chiffrement de l’étiquette sont appliqués. La co-création, la découverte électronique, la protection contre la perte de données, la recherche et d’autres fonctionnalités de collaboration seront également prises en charge dans ces circonstances.

[Découvrez comment activer l’aperçu](sensitivity-labels-sharepoint-onedrive-files.md)

## <a name="february-2020"></a>Février 2020

### <a name="insider-risk-management-is-officially-released"></a>La gestion des risques initiés est officiellement publiée

Rouleau à tambour, veuillez...<br>La gestion des risques initiés est désormais disponible pour les organisations disposant des abonnements suivants :

- [Microsoft 365 E5](https://go.microsoft.com/fwlink/?linkid=2120431) (payant ou d’évaluation)
- Abonnement Microsoft 365 entreprise E3 avec le [complément de conformité Microsoft E5](https://go.microsoft.com/fwlink/?linkid=2120432)

Nous avons apporté des améliorations depuis la version d’évaluation, notamment [de nouveaux groupes de rôles](insider-risk-management-configure.md#step-1-enable-permissions-for-insider-risk-management) et de nouveaux [paramètres à l’échelle](insider-risk-management-configure.md#step-4-configure-insider-risk-settings)de la solution.

Comme toujours, n’hésitez pas à nous faire part de vos commentaires lorsque vous utilisez la solution afin que nous puissions continuer à apporter des améliorations.

### <a name="records-management"></a>Gestion des enregistrements

Cette nouvelle solution offre toutes les fonctionnalités de gestion des enregistrements sous un seul parasol. Les points forts incluent l’introduction de la gestion des versions des enregistrements pour SharePoint et OneDrive et la preuve de la destruction des enregistrements.

![Page gestion des enregistrements dans le centre de conformité Microsoft 365](../media/mcc-records-management-page.png)

[En savoir plus sur la gestion des enregistrements](records-management.md)

### <a name="solution-spotlight-data-connectors-for-facebook-and-twitter"></a>Galerie de solutions : connecteurs de données pour Facebook et Twitter

Connecteurs de données [publiés le mois dernier](#just-launched) et nous recherchons votre aide pour tester les connecteurs suivants.

- [Pages d’entreprise Facebook](archive-facebook-data-with-sample-connector.md). Importe et archive les données des pages d’entreprise Facebook dans Microsoft 365. Avantages pour les solutions de conformité telles que la gestion des enregistrements et la découverte électronique.
- [Twitter](archive-twitter-data-with-sample-connector.md). Importe et archive les données de Twitter vers Microsoft 365. Avantages pour les solutions de conformité telles que la gestion des enregistrements et la découverte électronique.

Lors de la configuration et de la validation de ces connecteurs, n’hésitez pas à nous faire part de vos commentaires sur ce qui s’est passé, ce qui n’a pas fonctionné et ce que nous pouvons faire pour améliorer l’expérience.

## <a name="january-2020"></a>Janvier 2020

L’attente est terminée. Nous sommes heureux de vous annoncer que le centre de conformité Microsoft 365 est disponible pour tous les clients avec les plans Microsoft 365, Office 365, Enterprise Mobility + Security (EMS) et Windows 10 entreprise. Toutes les données ou stratégies gérées dans le centre de sécurité & conformité sont disponibles dans le centre de conformité, il n’est donc pas nécessaire de passer à la rubrique.

> [!TIP]
> Découvrez de nouveau la mise à jour du mois dernier pour un actualisateur sur certaines des [nouvelles solutions](#new-compliance-solutions) que nous avons consultées récemment, ainsi qu’une feuille de [route](#updated-compliance-solutions) illustrant l’emplacement des fonctionnalités de conformité du centre de sécurité & conformité dans Microsoft 365.

Créer un signet et des en-têtes maintenant pour parcourir [https://compliance.microsoft.com](https://compliance.microsoft.com) votre atelier pour gérer la conformité dans votre organisation... ou [Lisez cet article](microsoft-365-compliance-center.md) pour approfondir vos recherches.

![Page d’accueil du centre de conformité Microsoft 365](../media/mcc-home-ga.png)

Nous avons également publié des solutions nouvelles et mises à jour ce mois-ci. Voici un aperçu rapide des points forts.

### <a name="now-in-preview"></a>Maintenant en aperçu

**Gestion des risques initiés (aperçu)**

Nous sommes heureux de vous annoncer que notre solution de gestion des risques inSided est désormais en version préliminaire publique. En bref, la gestion des risques des Insiders aide votre organisation à identifier et à prendre intelligemment les risques d’initiés en fournissant :

- Contrôles d’anonymat pour garantir la confidentialité de l’utilisateur.
- Modèles de stratégie intelligents avec des indicateurs natifs et tiers qui identifient les menaces pour les utilisateurs, telles que les fuites de données.
- Des flux de travail d’enquête de bout en bout intégrés qui s’étendent au sein de l’informatique, des RH et des équipes juridiques.

Nous serions ravis d’entendre ce que vous pensez. Lors de l’utilisation de la solution, laissez-nous vos commentaires pour nous permettre de nous assurer que nous répondons à vos besoins, car nous sommes en tête de disponibilité générale.

[En savoir plus sur la gestion des risques internes](insider-risk-management.md)

### <a name="just-launched"></a>Venez de lancer

**Conformité des communications**

Le diplôme de la phase d’évaluation à la disponibilité complète, la conformité de la communication est un élément clé de notre nouvelle solution Insider Risk. Cette solution robuste permet de réduire les risques de communication à l’aide de flux de travail pour détecter, examiner et prendre des mesures correctives pour les messages qui ne répondent pas aux normes de votre organisation.

Les commentaires des clients pendant l’aperçu sont fantastiques. Plusieurs améliorations ont été apportées, notamment une première expérience d’utilisation pour vous aider à démarrer, les améliorations apportées aux actions d’enquête et de correction, et bien plus encore.

[En savoir plus sur la conformité des communications](communication-compliance.md)

![Page conformité de la communication dans le centre de conformité Microsoft 365 affichant la première carte de l’expérience d’accueil](../media/mcc-communication-compliance-page-with-fre.png)

**Connecteurs de données**

Avant de partager de l’espace avec d’autres fonctionnalités d’importation dans le centre de conformité Office 365 Security &, les connecteurs de données ont désormais leur propre domicile dans le centre de conformité Microsoft 365. Utilisez la nouvelle page « connecteurs de données » pour importer et archiver des données à partir des fichiers de ressources humaines (RH) de votre organisation et de différentes plateformes tierces (comme Facebook, LinkedIn, Twitter et instant Bloomberg) vers des boîtes aux lettres de votre organisation Microsoft 365. Une fois importées, ces données peuvent être gérées dans plusieurs solutions de conformité, notamment eDiscovery, la gestion des risques internes, la conformité des communications, l’audit, les stratégies de rétention, etc.

[En savoir plus sur les connecteurs de données](archiving-third-party-data.md)

![Page connecteurs de données dans le centre de conformité Microsoft 365](../media/mcc-data-connectors-page.png)

### <a name="noteworthy-updates"></a>Mises à jour intéressantes

**Nouveaux modèles d’évaluation pour le score de conformité (aperçu)**

Toujours opérationnel pour vous aider à anticiper le contexte de conformité en perpétuelle évolution, notre équipe de score de conformité a publié un nouvel ensemble de modèles pour vous aider à évaluer la conformité de votre organisation par rapport aux réglementations récentes et obtenir des conseils sur la façon d’implémenter des contrôles plus efficaces. Vous verrez de nouveaux modèles pour les éléments suivants :

- ISO/IEC 27701:2019
- California Consumer Privacy Act (CCPA)
- Loi du Brésil général sur la protection des données (lei Geral de Proteção de Dados-LGPD)
- SOC 1 type 2 et SOC 2 type 2

[En savoir plus sur les modèles de score de conformité](compliance-score.md#templates)

## <a name="november--december-2019"></a>Novembre & décembre 2019

Pendant les congés, nous avons commencé à déployer toutes les solutions de conformité de qualité qui étaient à l’allumage. La plupart sont dans un état d’aperçu, donc testez-les et n’hésitez pas à nous faire part de vos suggestions en ouvrant la carte de commentaires en bas à droite du centre de conformité.

![commentaires](../media/Feedback_card_MCC.JPG)

### <a name="get-to-know-the-new-neighborhood"></a>Familiarisation avec le nouveau voisinage

Le nouveau centre de conformité Microsoft 365 comprend de nouvelles solutions, ainsi que les fonctionnalités de conformité que vous avez connues et apprécier du centre de sécurité & de la sécurité Office 365. Examinons un peu plus...

#### <a name="new-compliance-solutions"></a>Nouvelles solutions de conformité

Vous pouvez vous demander ce qu’est une *solution* . Dans la mesure où le Cloud a révolutionné le mode d’activité, il a également ouvert le volet des nouvelles méthodes de vol de données et de fraude et de nouvelles réglementations. Nos solutions de conformité sont des collections de fonctionnalités intégrées qui peuvent vous aider à gérer ces exigences de conformité évolutives. Les fonctionnalités d’une solution peuvent inclure une combinaison de stratégies, d’alertes, de rapports et bien plus encore.

Voici un résumé des nouvelles solutions que vous trouverez. Restez un oeil pour les autres personnes bientôt disponibles.

> [!NOTE]
> Ces solutions se trouvent uniquement dans le centre de conformité Microsoft 365. Elles ne peuvent pas être gérées dans le centre de conformité Office 365 Security &.
<br/>

|**Nouvelle solution**|**Description**|**En savoir plus**|
|:-----|:-----|:-----|
|Score de conformité Microsoft (aperçu) <br/>|Créé à partir du [Gestionnaire de conformité](compliance-manager-overview.md), le score de conformité est une fonctionnalité autonome avec une conception plus conviviale et plus conviviale qui vous aide à comprendre et à améliorer la position de conformité de votre organisation. Il calcule un score basé sur les risques mesurant votre progression dans la réalisation d’actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires. <br/>|[Vue d’ensemble du score de conformité Microsoft (aperçu)](compliance-score.md)|
|Catalogue de solutions (aperçu) <br/>|Le catalogue de solutions vous permet de découvrir et de vous familiariser rapidement avec nos solutions de conformité et de gestion des risques. Le catalogue est organisé en trois catégories de conformité, chacune contenant des détails sur les solutions qui composent cette catégorie. Les catégories incluent la protection des informations & la gouvernance, la gestion des risques initiés et la détection & réponse <br/>|[Vue d’ensemble du catalogue de solutions (aperçu)](microsoft-365-solution-catalog.md)|
|Conformité de la communication (aperçu) <br/>|La conformité des communications fait partie de la nouvelle catégorie de gestion des risques Insider qui permet de réduire les risques de communication en vous aidant à détecter, capturer et prendre des mesures correctives pour les messages inappropriés dans votre organisation. La solution étend les fonctionnalités des stratégies de surveillance dans Office 365 en introduisant plusieurs nouvelles améliorations, telles que des modèles intelligents, des flux de travail de correction flexibles et des informations exploitables. <br/>|[Conformité de la communication dans Microsoft 365 (version d’évaluation)](communication-compliance.md)|
|Classification des données (aperçu) <br/>|Notre nouvelle page classification des données contient des informations puissantes et des outils qui vous permettent de découvrir et d’évaluer la façon dont les informations et les étiquettes sensibles (rétention et sensibilité) sont utilisées dans le contenu au sein de votre organisation. Passer en revue le contenu qui contient des informations sensibles ou des étiquettes appliquées, explorer l’activité des étiquettes dans les emplacements Microsoft 365, créer des types d’informations sensibles personnalisés et bien plus encore.<br/>|[Vue d’ensemble de la classification des données (aperçu)](data-classification-overview.md)|
|Classifieurs de formation (préversion) <br/>|Ce nouvel outil puissant utilise notre moteur d’apprentissage automatique pour identifier des catégories de contenu dans votre organisation, telles que des documents réglementaires ou des contrats d’employés. Une fois créés, les classifieurs peuvent être utilisés dans plusieurs solutions de conformité pour détecter le contenu associé et le classer, le protéger, le conserver et bien plus encore.<br/>|[Découvrez les classificateurs de formation (préversion)](classifier-learn-about.md)|

#### <a name="updated-compliance-solutions"></a>Mise à jour des solutions de conformité

Si vous avez utilisé le centre de sécurité & conformité d’Office 365 pour répondre à vos besoins en matière de conformité, vous pouvez vous demander où certaines fonctionnalités se trouvent désormais dans le nouveau centre de conformité Microsoft 365. Voici une feuille de route rapide permettant de trouver ses nouvelles maisons.

> [!NOTE]
> Certaines fonctionnalités ne sont toujours disponibles que dans le centre de sécurité & Office 365 Security (en anglais), comme indiqué ci-dessous. Mais nous travaillons difficilement pour les préversions dans le centre de conformité Microsoft 365, donc restez informé des mises à jour. 
<br/>

|**Fonctionnalité**|**Centre de sécurité et conformité Office 365**|**Centre de conformité Microsoft 365**|**En savoir plus**|
|:-----|:-----|:-----|:-----|
|Advanced eDiscovery|eDiscovery > Advanced eDiscovery <br/> https://protection.office.com/advancedediscoverycases |Découverte électronique > avancée <br/> https://compliance.microsoft.com/advancedediscovery | [Vue d’ensemble de la solution avancée eDiscovery dans Microsoft 365](overview-ediscovery-20.md) |
|Stratégies d’alerte|Alertes > les stratégies d’alerte <br/> https://protection.office.com/alertpolicies |Pour l’instant, les stratégies d’alerte sont gérées uniquement dans le centre de conformité & Office 365 Security. |[Stratégies d’alerte dans le Centre de sécurité et de conformité](alert-policies.md) |
|Alertes|Alertes > afficher les alertes <br/> https://protection.office.com/viewalerts |Alertes <br/> https://compliance.microsoft.com/compliancealerts |[Affichage des alertes](alert-policies.md#viewing-alerts)|
|Archiver|Archive de > de gouvernance des informations <br/> https://protection.office.com/archiving |Onglet Archive de > de gouvernance des informations <br/> https://compliance.microsoft.com/informationgovernance?viewid=archive |[Activer des boîtes aux lettres d’archivage](enable-archive-mailboxes.md)|
|Recherche de journal d’audit|Recherche dans le journal d’audit > <br/> https://protection.office.com/unifiedauditlog |Audit <br/> https://compliance.microsoft.com/auditlogsearch | [Effectuer des recherches dans le journal d’audit depuis le Centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md)|
|Recherche de contenu|Recherche > recherche de contenu <br/> https://protection.office.com/contentsearchbeta?ContentOnly=1 | Recherche de contenu <br/> https://compliance.microsoft.com/contentsearch |[Rechercher du contenu dans Office 365](search-for-content.md) |
|Connecteurs de données|Gestion des informations > archivage des données tierces <br/> https://protection.office.com/nativeconnector | Connecteurs de données <br/> https://compliance.microsoft.com/connectorlanding |[Archiver des données tierces](archiving-third-party-data.md)|
|Protection contre la perte de données|Protection contre la perte de données <br/> https://protection.office.com/datalossprevention |Protection contre la perte de données <br/> https://compliance.microsoft.com/datalossprevention |[Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)|
|Demandes des personnes concernées |Confidentialité des données > demandes des personnes concernées <br/> https://protection.office.com/dsrcases |Demandes des personnes concernées <br/> https://compliance.microsoft.com/datasubjectrequest |[Gérer les demandes des personnes associées aux données RGPD avec l’outil de cas DSR](manage-gdpr-data-subject-requests-with-the-dsr-case-tool.md)|
|eDiscovery|découverte électronique > eDiscovery <br/> https://protection.office.com/ediscoveryv1 |> de découverte électronique <br/> https://compliance.microsoft.com/classicediscovery |[Gérer des cas eDiscovery](ediscovery-cases.md) |
|Événements|Événements de > de la gestion des enregistrements <br/> https://protection.office.com/events |Onglet > des événements de gestion des enregistrements <br/> https://compliance.microsoft.com/recordsmanagement?viewid=events |[Débuter la rétention lorsqu’un événement se produit](event-driven-retention.md)|
|Plan de gestion de fichiers|Gestion des enregistrements > plan de gestion des fichiers <br/> https://protection.office.com/fileplan |Onglet gestion des enregistrements > plan de fichiers <br/> https://compliance.microsoft.com/recordsmanagement?viewid=fileplan |[Utiliser le plan de gestion de fichiers pour gérer les étiquettes de rétention](file-plan-manager.md)|
|Importer des fichiers PST|Gouvernance des informations > importer des fichiers PST <br/> https://protection.office.com/importV2 |Onglet > d’importation de la gouvernance des informations <br/> https://compliance.microsoft.com/informationgovernance?viewid=import |[Vue d’ensemble de l’importation des fichiers PST de votre organisation](importing-pst-files-to-office-365.md)|
|Explorateur d’activité des étiquettes|Explorateur d’informations > d’activité des étiquettes <br/> https://protection.office.com/labelexplorer |Onglet Explorateur d’activités > classification des données <br/> https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer |[Afficher l’activité sur votre contenu étiqueté (aperçu)](data-classification-activity-explorer.md)|
|Étiquettes de rétention et stratégies d’étiquette |Étiquettes de rétention > étiquettes de rétention > des étiquettes et des stratégies d’étiquette <br/> https://protection.office.com/retentionlabels |Onglets de gouvernance des informations > des étiquettes et des stratégies d’étiquette <br/> https://compliance.microsoft.com/informationgovernance?viewid=labels <br/> https://compliance.microsoft.com/informationgovernance?viewid=labelpolicies | [Vue d’ensemble des étiquettes de rétention](retention.md)|
|Stratégies de rétention|Conservation des > de gouvernance des informations <br/> https://protection.office.com/retention |Onglet rétention > de gouvernance des informations <br/> https://compliance.microsoft.com/informationgovernance?viewid=retention |[En savoir plus sur les stratégies et les balises de rétention](retention.md)|
|Types d’informations sensibles|Classification > types d’informations sensibles <br/> https://protection.office.com/sensitivetypes |Classification des données > onglet types d’informations sensibles <br/> https://compliance.microsoft.com/dataclassification?viewid=sensitiveinfotypes |[Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)|
|Étiquettes de confidentialité et stratégies d’étiquette|Étiquettes de sensibilité > de classification > les étiquettes et les onglets stratégies d’étiquette <br/> https://protection.office.com/sensitivity |Onglets de protection des informations > des étiquettes et des stratégies d’étiquette <br/> https://compliance.microsoft.com/informationprotection?viewid=sensitivitylabels <br/> https://compliance.microsoft.com/informationprotection?viewid=sensitivitylabelpolicies |[En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md) |
|Certification de service|Certification de service <br/> https://protection.office.com/serviceassurance/dashboard |Pour l’instant, les ressources de service assurance ne sont accessibles que dans le centre de conformité & Office 365 Security. |[Certification de service dans le Centre de sécurité et conformité](service-assurance.md)|
|Surveillance|Surveillance <br/> https://protection.office.com/supervisoryreviewv2 |Conformité des communications <br/> https://compliance.microsoft.com/supervisoryreview |[Conformité de la communication dans Microsoft 365 (version d’évaluation)](communication-compliance.md) |

## <a name="september-2019"></a>Septembre 2019

Vous vous demandez pourquoi il est calme sur la sortie ce mois-ci ? Nous sommes en tête de création de nouvelles solutions de conformité innovantes qui seront dévoilées chez [Microsoft enflamme](https://www.microsoft.com/ignite) en novembre. Restez informé !

### <a name="new-encryption-options-for-sensitivity-labels"></a>Nouvelles options de chiffrement pour les étiquettes de sensibilité 

Lors de la configuration du chiffrement pour une étiquette de sensibilité, vous disposez de deux options qui permettent aux utilisateurs d’attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à la messagerie et aux documents :<br>
- Lors de l’application de l’étiquette à la **messagerie Outlook**, les utilisateurs peuvent appliquer des restrictions équivalentes à celles de l’option ne pas transférer. Les destinataires seront en mesure de lire le message, mais pas de transférer, imprimer ou copier le contenu.
- Lors de l’application de l’étiquette à des **fichiers Word, PowerPoint et Excel**, les utilisateurs sont invités à attribuer des autorisations d’accès à des utilisateurs et des groupes spécifiques.

Accédez à [restreindre l’accès au contenu à l’aide des étiquettes de confidentialité pour appliquer le chiffrement](encryption-sensitivity-labels.md#let-users-assign-permissions) pour en savoir plus.
