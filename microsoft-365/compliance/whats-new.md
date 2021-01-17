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
description: Que vous ajoutiez de nouvelles solutions au centre de conformité, mettiez à jour les fonctionnalités existantes en fonction de vos commentaires ou mettiez en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 8723171820bb1c089d34b81f5adb6663ecc9b8af
ms.sourcegitcommit: 27cb4591e08f62ba0a08d6dcf224bf2039034fe5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2021
ms.locfileid: "49883713"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Que ce soit en ajoutant de nouvelles solutions au Centre de conformité [Microsoft 365,](microsoft-365-compliance-center.md)en mettant à jour les fonctionnalités existantes en fonction de vos commentaires ou en mettant en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Consultez la ci-dessous pour voir les nouveautés de la conformité Microsoft 365 aujourd’hui. 

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée.](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365)


> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :<br>[Nouveautés du Centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/whats-new-in-preview)<br>[Nouveautés du Centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)<br>[Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)<br><br>
Consultez la feuille de route [Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités de Microsoft 365 qui ont été lancées, sont en cours de déploiement, sont en cours de développement, ont été annulées ou publiées précédemment.

## <a name="november--december-2020"></a>Novembre & décembre 2020
Juste un rappel que nous publions souvent des fonctionnalités nouvelles et mises à jour dans un état d’aperçu pour découvrir comment elles sont utilisées afin de pouvoir les affiner et les améliorer avant de les publier à la disponibilité générale. Vos commentaires sont essentiels pendant la prévisualisation (et au-delà), donc n’oubliez pas de nous faire part de vos commentaires en ouvrant la carte de commentaires en bas à droite du centre de conformité.

![commentaires](../media/Feedback_card_MCC.JPG)

### <a name="spotlight-endpoint-data-loss-prevention-dlp-released"></a>À la une : publication de la protection contre la perte de données (DLP) de point de terminaison

[Le point de terminaison DLP](endpoint-dlp-learn-about.md) étend les fonctionnalités de surveillance et de protection des activités de DLP aux informations sensibles sur les appareils Windows 10. Une fois les [appareils](dlp-configure-endpoints.md) intégrés au Centre de conformité Microsoft 365, vous pouvez configurer des stratégies DLP pour protéger les informations sensibles sur ces appareils.

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, [](ediscovery-decryption.md) les outils de découverte électronique Microsoft 365 intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange. En outre, les documents chiffrés stockés dans SharePoint et OneDrive sont déchiffrés dans Advanced eDiscovery.

### <a name="compliance-manager"></a>Gestionnaire de conformité

- [Prise en charge des abonnements Microsoft 365 Pour le gouvernement.](compliance-manager.md) Le Gestionnaire de conformité est désormais disponible pour les clients modérés et élevés de la communauté du gouvernement américain (GCC).
- [Analyseur de configuration de conformité Microsoft pour le Gestionnaire de conformité.](compliance-manager-mcca.md) Nouvel outil Basé sur PowerShell qui vous aide à démarrer avec le Gestionnaire de conformité en analysant les configurations actuelles de votre organisation et en les validant par rapport aux meilleures pratiques recommandées par Microsoft 365.
- [Nouveaux modèles](compliance-manager-templates-list.md). Ajout de 56 nouveaux modèles, ce qui porte le nombre total de modèles du Gestionnaire de conformité à plus de 230.

### <a name="data-connectors"></a>Connecteurs de données

[Cinq nouveaux connecteurs Globanet en prévisualisation.](archiving-third-party-data.md#third-party-data-connectors) Les nouveaux connecteurs incluent Reuters Dealing, Reuters FX, CellTrust, XIP, generic MS SQL Database.

### <a name="retention-labels-disposition-review"></a>Étiquettes de rétention (révision de la disposition)

Pour afficher les éléments lors d’une révision de disposition, les utilisateurs doivent maintenant être membres des groupes de rôles Visionneuse de contenu de l’Explorateur de contenu et Visionneuse de liste de [l’Explorateur de contenu.](disposition.md#permissions-for-disposition) Bien que requis pour passer en revue les éléments, ces groupes de rôles ne sont pas nécessaires pour terminer la révision de la disposition.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [(Aperçu) Paramètres de partage externe pour les sites SharePoint.](sensitivity-labels-teams-groups-sites.md#how-to-configure-groups-and-site-settings) Lorsque vous créez une étiquette qui sera utilisée pour les groupes et les sites, une option de contrôle du partage externe s’offre à vous pour les sites SharePoint sur qui l’étiquette est appliquée. Vous pouvez spécifier que le partage est autorisé pour tout le monde, les invités nouveaux et existants, les invités existants uniquement ou uniquement les utilisateurs de votre organisation. Lorsque l’étiquette est appliquée, les paramètres d’étiquette remplacent les paramètres de partage externe configurés dans le [Centre d’administration SharePoint.](https://docs.microsoft.com/sharepoint/change-external-sharing-site)
- [Supprimez l’étiquette et le chiffrement d’un document étiqueté.](sensitivity-labels-sharepoint-onedrive-files.md#remove-encryption-for-a-labeled-document) Pour supprimer une étiquette et le chiffrement qu’elle applique à partir d’un document étiqueté dans SharePoint, les administrateurs globaux et les administrateurs SharePoint peuvent exécuter la nouvelle `Unlock-SPOSensitivityLabelEncryptedFile` cmdlet. Cette cmdlet s’exécute même si l’administrateur n’a pas d’autorisations d’accès au site ou au fichier, ou si le service Azure Rights Management n’est pas disponible.

## <a name="october-2020"></a>Octobre 2020

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

[Prise en charge des languesJCK.](ediscovery-cjk-support.md) Advanced eDiscovery prend désormais en charge les langues de jeu de caractères sur deux sur deux caractères, appelées collectivement languesJCK (y compris le chinois simplifié, le chinois traditionnel, le japonais et le coréen). Ceux-ci peuvent être utilisés dans plusieurs scénarios d’ensembles de révision avancés.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Étendue d’étiquette](sensitivity-labels.md#label-scopes). Lorsque vous créez une étiquette de sensibilité, une nouvelle option s’offre à vous pour définir l’étendue de l’étiquette. Cette option vous permet de configurer des étiquettes uniquement pour les fichiers et les e-mails, les conteneurs (tels que les sites SharePoint et Teams) ou les deux.
- [Marquage de contenu dynamique](sensitivity-labels-office-apps.md#dynamic-markings-with-variables). Lors de la configuration du marquage de contenu pour une étiquette de sensibilité, vous pouvez désormais utiliser les variables dynamiques telles que et dans la chaîne de texte pour votre en-tête, pied de page ou `${Item.Label}` `${Item.Location}` filigrane.

## <a name="september-2020"></a>Septembre 2020

### <a name="spotlight-compliance-manager"></a>À la une : Gestionnaire de conformité

Annoncé au ignite cette année, le Score de conformité est renommé Gestionnaire [de conformité.](compliance-manager.md) Cette version termine la transition à partir de l’ancienne page d’accueil du Gestionnaire de conformité dans le portail d’confiance des services et présente une solution de gestion de la conformité de bout en bout dans le Centre de conformité Microsoft 365.

Regardez la vidéo ci-dessous pour découvrir comment le Gestionnaire de conformité peut simplifier la gestion de la conformité par votre organisation.
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4FGYZ]

### <a name="advanced-audit"></a>Audit avancé

- La nouvelle rétention de 10 ans des journaux d’audit permet de prendre en charge les enquêtes de longue durée et de répondre aux obligations réglementaires, juridiques et internes.
- [Trois nouveaux événements essentiels](advanced-audit.md#access-to-crucial-events-for-investigations). Les nouveaux événements suivants peuvent vous aider à examiner les violations possibles et à déterminer l’étendue de la compromission : Send, SearchQueryInitiatedExchange et SearchQueryInitiatedSharePoint.

### <a name="communication-compliance"></a>Conformité des communications

- [Groupes de rôles mis à jour.](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance) Les groupes de rôles de conformité des communications correspondent désormais à la structure de groupes de rôles disponible pour la solution de gestion des risques internes.
- [Tableau de bord rapports](communication-compliance-feature-reference.md#reports-preview). Votre emplacement central pour afficher tous les rapports de conformité des communications. Les widgets de rapport fournissent un aperçu rapide des informations les plus couramment nécessaires pour une évaluation globale de l’état des activités de conformité des communications.
- [Flux Power Automate](communication-compliance-feature-reference.md#power-automate-flows). Configurer des flux pour automatiser les tâches pour les alertes et les utilisateurs, avertir les responsables lorsque les utilisateurs déclenchent une alerte, et bien plus encore.
- [Action de correction «](communication-compliance-investigate-remediate.md#step-3-decide-on-a-remediation-action)Améliorer la classification ». Les alertes contenant des éléments qui correspondent à des classifieurs entraisables peuvent tirer parti des commentaires pour réduire les faux positifs dans votre organisation. **L’option Améliorer la classification** vous permet de fournir des commentaires si les éléments détectés correspondent au classifieur configuré dans la stratégie de conformité des communications associée. Vous pouvez même suggérer d’autres classifieurs à associer à l’élément pour améliorer la précision des correspondances pour les alertes futures.

### <a name="data-connectors"></a>Connecteurs de données

- [Nouveaux connecteurs de données tiers.](archiving-third-party-data.md#third-party-data-connectors) 25 nouveaux connecteurs de données, dont 14 connecteurs globanet et 8 connecteurs de télémessage.
- [Connecteur de badging physique](import-physical-badging-data.md). Importez les données de mauvaise gestion physiques, telles que les événements d’accès physique bruts de l’employé ou les alarmes d’accès physique générées par le système de mauvaise gestion de votre organisation. Les entrées des bâtiments, des salles de serveurs ou des centres de données en sont des exemples. Les données de mauvais traitement physique peuvent être utilisées par la solution de gestion des risques internes pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Intégration de Microsoft Teams.](insider-risk-management-settings.md#microsoft-teams-preview) Lorsque l’intégration de Teams est mise en place dans les paramètres de risques internes, vous pouvez coordonner et collaborer avec d’autres parties prenantes dans Teams sur des tâches telles que le partage et le stockage sécurisés de données relatives à des cas individuels, le suivi et l’examen des activités de réponse des analystes et des enquêteurs, et bien plus encore.
- [Flux Power Automate](insider-risk-management-settings.md#power-automate-flows-preview). Configurer des flux pour automatiser les tâches importantes pour les cas et les utilisateurs, telles que la récupération d’utilisateurs, d’alertes et d’informations de cas à partager avec les parties prenantes et d’autres applications, l’automatisation d’actions telles que la publication dans des notes de cas, etc.
- [Activité du contenu](insider-risk-management-alerts.md#activity-explorer-preview). Disponible lors de l’examen des alertes, l’Explorateur d’activités fournit aux enquêteurs et aux analystes un outil analytique complet pour explorer chaque alerte. Examinez rapidement une chronologie de l’activité à risque détectée et identifiez et filtrez toutes les activités de risque associées aux alertes.

### <a name="retention-policies-and-retention-labels"></a>Stratégies de rétention et étiquettes de rétention.

- [Prise en charge de Yammer](retention-policies-yammer.md). Vous pouvez désormais utiliser des stratégies de rétention pour conserver et supprimer Yammer messages communautaires et privés.
- [Appliquer des étiquettes aux enregistrements de réunions Teams.](apply-retention-labels-automatically.md#microsoft-teams-meeting-recordings) Lors de la création d’une stratégie d’étiquetage automatique, utilisez l’éditeur de requête par mot clé pour identifier les enregistrements de réunion Teams stockés dans les comptes OneDrive des utilisateurs ou dans SharePoint.

### <a name="records-management"></a>Gestion des enregistrements

[Prise en charge des enregistrements réglementaires.](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record) La classification d’une étiquette en tant qu’enregistrement réglementaire augmente les restrictions imposées au contenu auquel l’étiquette est appliquée et limite les actions de gestion disponibles pour l’étiquette elle-même. Par exemple, une fois qu’il est appliqué au contenu, personne, pas même un administrateur global, ne peut supprimer l’étiquette. [En savoir plus](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) sur les actions autorisées et bloquées pour les enregistrements réglementaires.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

[Prise en charge pour les clients du gouvernement des États-Unis.](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description) Les étiquettes de sensibilité sont désormais pris en charge pour les clients GCC, GCC High et DoD, uniquement pour le client et le scanneur d’étiquetage unifié Azure Information Protection.

### <a name="trainable-classifiers"></a>Classifieurs avec capacité d’apprentissage

De nouvelles fonctionnalités de formation et de commentaires permettent d’améliorer la précision et de minimiser les correspondances faux positifs pour tous les classifieurs personnalisés et certains classifieurs pré-formés. Ce flux vous permet d’indiquer si les éléments correspondent à certains classifieurs, de suggérer d’autres classifieurs à associer aux éléments et de former à nouveau les classifieurs pour affiner et améliorer la précision des correspondances.

Cette nouvelle fonctionnalité est incluse dans les fonctionnalités suivantes :

> [!NOTE]
> Pour toutes les fonctionnalités, si vous fournissez au moins 30 réponses de commentaires, nous allons créer une version retrainée de ce classificateur que vous pouvez examiner. En cas d’amélioration, vous pouvez republier le classifieur.

- [Classifieurs avec capacité d’apprentissage](classifier-learn-about.md#retraining-classifiers). Pour améliorer la précision de vos classifieurs publiés, vous pouvez fournir des commentaires sur la correspondance des éléments détectés avec le classifieur.
- [Conformité des communications.](classifier-how-to-retrain-comms-compliance.md) La nouvelle action **de correction** améliorer la classification vous permet de fournir des commentaires si un élément d’une alerte de conformité des communications correspond au classificateur configuré dans la stratégie de conformité des communications.
- [Explorateur de contenu](classifier-how-to-retrain-content-explorer.md). Si vous définissez une stratégie d’étiquetage automatique de rétention pour appliquer automatiquement des étiquettes aux messages électroniques qui correspondent à des classifieurs entra nements, vous pouvez utiliser l’Explorateur de contenu pour examiner les éléments étiquetés et fournir des commentaires si les éléments correspondent au classifieur.

## <a name="august-2020"></a>Août 2020

### <a name="spotlight-insider-risk-and-communication-compliance-updates"></a>À la une : Mises à jour de conformité des risques internes et des communications

Plusieurs fonctionnalités nouvelles et améliorées ont été publiquement prévisualiser ce mois-ci :

**Gestion des risques internes**

- Consultez nos six nouveaux [modèles de stratégie](insider-risk-management-policies.md#policy-templates):
    - Fuites de données par utilisateurs prioritaires
    - Fuites de données par des utilisateurs non régrunts
    - Violations générales de la stratégie de sécurité
    - Violations de la stratégie de sécurité par les utilisateurs qui quittent le site
    - Violations de stratégie de sécurité par les utilisateurs prioritaires
    - Violations de stratégie de sécurité par les utilisateurs non résusés

- L’intégration à [Microsoft Defender pour point](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) de terminaison vous permet d’importer et de filtrer les alertes Microsoft Defender pour les points de terminaison pour les activités détectées par les stratégies créées à partir des nouveaux modèles de stratégie de violation de la sécurité. Il existe également [](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview) un paramètre de risque interne associé dans lequel vous pouvez choisir d’importer des alertes de sécurité pour la gestion des risques internes en fonction de l’état de triage des alertes Microsoft Defender for Endpoint.

    > [!NOTE]
    > Pour tirer parti de l’intégration de Microsoft Defender pour les points de terminaison (y compris les nouveaux modèles de violation de stratégie de sécurité), microsoft Defender pour point de terminaison doit être configuré dans votre organisation. Vous devez également activer Microsoft Defender pour endpoint pour l’intégration de la gestion des risques internes en configurant des fonctionnalités avancées dans [Microsoft Defender pour Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).
 
- Personnaliser les seuils des indicateurs lors [de la création d’une stratégie.](insider-risk-management-policies.md#create-a-new-policy)
- Configurer [](insider-risk-management-settings.md#priority-user-groups-preview) des groupes d’utilisateurs prioritaires pour définir les utilisateurs de votre organisation dont l’activité nécessite une inspection plus approfondie en fonction de facteurs tels que leur position, le niveau d’accès aux informations sensibles ou l’historique des risques.
- Utilisez les API Activité de gestion Office 365 pour exporter les détails des [alertes](insider-risk-management-settings.md#export-alerts-preview) de risques internes vers d’autres applications que votre organisation peut utiliser pour gérer ou agréger les données des risques internes.
- Les nouveaux [paramètres de domaine vous](insider-risk-management-settings.md#domains-preview) aident à définir et contrôler les niveaux de risque d’activité dans des domaines spécifiques.

**Conformité des communications**

- Lorsque [vous examinez des messages dans](communication-compliance-investigate-remediate.md#step-3-decide-on-a-remediation-action)une alerte, vous pouvez désormais supprimer les messages inappropriés dans les canaux Microsoft Teams, 1:1 et les conversations de groupe. Les messages et le contenu supprimés sont remplacés par un conseil de stratégie qui explique qu’il a été supprimé en raison de contenus sensibles.
- Nouveaux [rôles de communication](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance) (ceux-ci seront également inclus dans les nouveaux groupes de rôles de conformité des communications qui seront libérés en septembre).
- Nouvelle expérience de paramètres de conformité des communications qui inclut les paramètres de [confidentialité](communication-compliance-feature-reference.md#privacy) et [les modèles de notification.](communication-compliance-feature-reference.md#notice-templates)
- Nouveaux [classifieurs pour](communication-compliance-feature-reference.md#classifiers) détecter les images adulte, racy et gory.
- La nouvelle notification « Modèle détecté » qui s’affiche lors de l’examen des [messages](communication-compliance-investigate-remediate.md#step-2-examine-the-message-details) d’une alerte vous permet de savoir si un utilisateur récurse des instances du même comportement.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Pour les clients du secteur public des États-Unis (GCC, GCC-HC et DoD), les étiquettes de confidentialité ne sont actuellement prises en charge que pour le client et l’analyseur d’étiquetage unifié d’Azure Information Protection. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Description du service public Azure Information Protection Premium](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).
- Vous pouvez désormais utiliser le Centre de sécurité & conformité [PowerShell](create-sensitivity-labels.md#use-powershell-for-sensitivity-labels-and-their-policies) pour créer et configurer tous les paramètres que vous voyez dans votre centre d’administration de l’étiquetage. Cela signifie qu’en plus d’utiliser PowerShell pour les paramètres qui ne sont pas disponibles dans les centres d’administration d’étiquetage, vous pouvez désormais écrire entièrement un script pour la création et la maintenance des étiquettes de confidentialité et des stratégies d’étiquette de confidentialité.

### <a name="records-management-content-overhaul"></a>Gestion des enregistrements : révision du contenu

Nouveaux documents couvrant les étapes de déploiement, le marquage du contenu en tant qu’enregistrements et le contrôle de version des enregistrements :

- [Prise en main de la gestion des enregistrements](get-started-with-records-management.md)
- [Déclarer des enregistrements à l’aide d’étiquettes de rétention](declare-records.md)
- [Utiliser le contrôle de version des enregistrements pour mettre à jour les enregistrements stockés dans SharePoint ou OneDrive](record-versioning.md)

### <a name="retention-labels--policies"></a>Étiquettes de rétention & stratégies

L’activité d’administrateur liée à la rétention est désormais enregistrée et disponible pour révision dans le journal d’audit. Pour obtenir la liste complète, voir [Politiques de rétention et activités d’étiquette de rétention](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

- Lorsque [vous ajoutez une collection à](add-data-to-review-set.md#define-options-to-scope-your-collection-for-review)un jeu à réviser, vous pouvez désormais inclure des pièces jointes modernes (également appelées « pièces jointes cloud ») et des versions de document SharePoint.
- Nouvelle [expérience d’exportation de](export-documents-from-review-set.md)téléchargement direct, ce qui élimine la nécessité d’utiliser Azure Storage Explorer pour télécharger du contenu de cas.


## <a name="july-2020"></a>Juillet 2020

### <a name="spotlight-on-help-docs"></a>À la une sur les documents d’aide

Pour vous aider à comprendre quelles solutions de conformité sont utilisées pour protéger et régir les données sensibles de votre organisation, nous avons créé deux nouvelles pages d’accueil avec une vue d’ensemble de la façon dont les solutions fonctionnent ensemble pour atteindre ces objectifs, y compris des liens vers des documents connexes pour vous permettre d’aller plus loin.

[Microsoft Information Protection dans Microsoft 365.](information-protection.md)<br>
[Gouvernance des informations dans Microsoft 365](manage-Information-governance.md)

### <a name="advanced-ediscovery-add-non-custodial-data-sources-to-your-cases"></a>Advanced eDiscovery : ajouter des sources de données non privatives à vos cas

Ajoutez des données à un cas sans avoir à les associer à un dépositaire (connu sous le nom de sources de [données non privatives).](non-custodial-data-sources.md) Et si vous devez placer ces données non en attente, vous pourrez le faire à l’aide de notre nouvelle fonctionnalité d’indexation avancée.

### <a name="data-connectors-hr-connector-enhancements"></a>Connecteurs de données : améliorations apportées au connecteur RH

(En prévisualisation) Une nouvelle version du connecteur [RH](import-hr-data.md) vous permet d’importer des données relatives aux changements de niveau de travail, aux révisions de performances et aux plans d’amélioration des performances. Ces données peuvent ensuite être utilisées dans plusieurs stratégies de risque internes [pour](insider-risk-management-policies.md) détecter les activités connexes.

### <a name="retention-labels-new-support-for-email"></a>Étiquettes de rétention : nouvelle prise en charge du courrier électronique

Vous pouvez maintenant créer une étiquette [de rétention](retention.md#retention-labels) pour commencer à conserver les messages électroniques en fonction du moment où les messages ont été étiquetés. Cela ne s’applique pas aux éléments de calendrier, qui seront conservés en fonction du moment où l’élément est envoyé.

### <a name="sensitivity-labels-new-feature-and-an-improvement"></a>Étiquettes de niveau de sensibilité : nouvelle fonctionnalité et amélioration

- (En prévisualisation) Lors de la configuration des paramètres de chiffrement [](encryption-sensitivity-labels.md#double-key-encryption) pour une étiquette, recherchez la nouvelle option d’utilisation du chiffrement à double clé pour protéger davantage les fichiers étiquetés et les e-mails.
- Lors de la création ou de la suppression d’étiquettes de confidentialité, de la création, de la modification ou de la suppression de leurs stratégies d’étiquette, les modifications sont désormais synchronisées dans un délai d’une heure pour tous les utilisateurs, applications et services.

## <a name="june-2020"></a>Juin 2020

### <a name="spotlight-new-data-connectors-hit-preview"></a>À la une : aperçu des nouveaux connecteurs de données

Sur la base de notre promesse d’importer des données à partir de sources tierces dans Microsoft 365, nous sommes heureux d’annoncer la version préliminaire de deux autres connecteurs de données :

- [Message Bloomberg](archive-bloomberg-message-data.md). Importer et archiver des données de messagerie des services financiers à partir de l’outil de collaboration De Bloomberg Message. Une fois les données stockées dans les boîtes aux lettres, vous pouvez accéder aux données et les utiliser dans des fonctionnalités de conformité telles que la conservation pour litige, la recherche de contenu, l’archivage sur place, l’audit, la conformité des communications et les stratégies de rétention.
- [ICE Chat](archive-icechat-data.md). Importer et archiver les données de conversation des services financiers à partir de l’outil de collaboration ICE Chat. Une fois les données stockées dans les boîtes aux lettres, vous pouvez accéder aux données et les utiliser dans des fonctionnalités de conformité telles que la conservation pour litige, eDiscovery, l’archivage, l’audit, la conformité des communications et les stratégies de rétention.

### <a name="compliance-score--compliance-manager-the-hits-keep-coming"></a>Score de conformité & conformité : les résultats sont toujours à venir

Les mises à jour de juin incluent une nouvelle vue d’évaluation dans le [Score de conformité.](compliance-score.md) Surveillez la progression du contrôle, ajoutez, supprimez des évaluations directement du Score de conformité, et bien plus encore.

Vous souhaitez rester informé des mises à jour du Score de conformité et du Gestionnaire de conformité ? Marquez les notes [de publication du Score de](compliance-score-release-notes.md) conformité et retentez-les souvent.

## <a name="may-2020"></a>Mai 2020

### <a name="spotlight-data-classification-is-officially-released"></a>À la une : la classification des données est officiellement publiée

La classification des[](data-classification-overview.md)données, c’est-à-dire « Connaître vos données , les fonctionnalités (analyse, explorateur de contenu et explorateur d’activités) ont été extraites de la phase de prévisualisation et sont disponibles pour toutes les organisations. Des informations et des outils puissants peuvent vous aider à découvrir et évaluer la façon dont les informations sensibles et les étiquettes (rétention et sensibilité) sont utilisées dans le contenu au sein de votre organisation. Examinez le contenu qui contient des informations sensibles ou qui comporte des étiquettes appliquées, explorez l’activité des étiquettes dans les emplacements Microsoft 365, créez des types d’informations sensibles personnalisés, et bien plus encore.

Faites une visite guidée vidéo...

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

### <a name="trainable-classifiers-a-fix-and-a-feature"></a>Classifieurs entra nessables : un correctif et une fonction

Peut apporter d’autres améliorations aux classifieurs entraisables :

- Correctif basé sur vos commentaires : lorsque vous amorçage et formez un classifieur personnalisé, vous n’avez plus besoin d’entrer manuellement les URL de site SharePoint et les chemins d’accès aux dossiers. Vous pouvez désormais choisir parmi une liste pré-remplie de sites et de dossiers.
- Nouvelle fonctionnalité : lors de la création d’une étiquette de sensibilité et de la configuration des paramètres d’étiquetage automatique pour les applications Office, vous pouvez désormais appliquer automatiquement (ou recommander aux utilisateurs d’appliquer) l’étiquette au contenu qui correspond aux classifieurs entraidables. [En savoir plus](apply-sensitivity-label-automatically.md#configuring-trainable-classifiers-for-a-label)

### <a name="communication-compliance-yammer-support-is-here"></a>Conformité des communications : Yammer prise en charge est là

Les messages privés et les conversations de la communauté Yammer sont pris en charge dans les stratégies de conformité des communications. Yammer est un canal facultatif qui doit être en [mode natif](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) pour prendre en charge l’analyse de messages et de pièces jointes.

### <a name="data-loss-prevention-new-sharing-restriction"></a>Protection contre la perte de données : nouvelle restriction de partage

Lorsque vous configurez une stratégie DLP pour protéger le contenu dans SharePoint ou OneDrive, vous pouvez désormais configurer l’action « Restreindre l’accès au contenu » pour bloquer les personnes qui ont reçu l’accès au contenu via l’option « Tout le monde avec le lien ».[](https://support.microsoft.com/office/share-files-outside-your-organization-with-anyone-links-53e91027-fb8e-4a6e-a3e4-5df4be32e38a)

### <a name="insider-risk-management-tailor-your-alert-volume"></a>Gestion des risques internes : personnaliser votre volume d’alertes

Les activités des utilisateurs détectées par les stratégies de risque interne se voit attribuer un score de risque spécifique, qui à son tour détermine la gravité de l’alerte (faible, moyenne, élevée). Par défaut, Microsoft 365 génère une certaine quantité d’alertes de gravité faible, moyenne et élevée, mais avec le nouveau paramètre de [volume](insider-risk-management-settings.md#alert-volume)d’alerte, vous pouvez augmenter ou diminuer le volume en fonction de vos besoins.

### <a name="pst-import-new-region-supported"></a>Importation PST : nouvelle région prise en charge

Le chargement réseau est désormais disponible aux Émirats arabes unis.

### <a name="sensitivity-labels-new-privacy-option"></a>Étiquettes de confidentialité : nouvelle option de confidentialité

Lors de la configuration [des paramètres](sensitivity-labels-teams-groups-sites.md#how-to-configure-groups-and-site-settings) de site et de groupe pour une étiquette, vous pouvez désormais définir l’option de confidentialité sur Aucun : laissez l’utilisateur choisir qui peut **accéder au site.** Cela est utile lorsque vous souhaitez protéger le contenu du conteneur à l’aide d’une étiquette de confidentialité, tout en laisser les utilisateurs configurer eux-mêmes le paramètre de confidentialité.

## <a name="april-2020"></a>Avril 2020

### <a name="records-management-overhauland-a-new-addition"></a>Gestion des enregistrements : révision... et un nouvel ajout

Avril inclut quelques mises à jour clés de notre solution de gestion des enregistrements :

- La section « Gestion des enregistrements » est désormais entièrement disponible dans le centre de conformité. Tirez parti des interfaces utilisateur et des fonctionnalités mises à jour pour le plan de gestion de fichiers, les étiquettes de rétention et les stratégies d’étiquette, les événements et la disposition.
- Concernant la disposition, nous avons également déployé une preuve de [disposition](disposition.md#disposition-of-records) pour les enregistrements dans SharePoint et OneDrive. Vous pouvez maintenant voir une liste des éléments à ces emplacements qui ont été éliminés automatiquement ou après une révision de la disposition.

### <a name="sensitivity-labels-preview-auto-labeling-policies"></a>Étiquettes de confidentialité : afficher un aperçu des stratégies d’étiquetage automatique

Avec les stratégies d’étiquetage automatique, vous pouvez désormais appliquer automatiquement des étiquettes de confidentialité aux documents SharePoint et OneDrive déjà enregistrés (également appelés « données au repos » ) et aux e-mails déjà envoyés ou reçus (également appelés « courrier électronique en transit »). Étant donné que cette étiquetage est appliqué par les services plutôt que par les applications, vous n’avez pas besoin de vous soucier des applications que les utilisateurs ont et de la version.

Cette fonctionnalité étend l’étiquetage côté client existant qui est déjà inclus dans les paramètres « Étiquetage automatique pour les applications Office » lorsque vous créez une étiquette de sensibilité. Pour découvrir rapidement les différences et les avantages des deux options d’étiquetage automatique, consultez [l’article mis à jour.](apply-sensitivity-label-automatically.md)

## <a name="march-2020"></a>Mars 2020

### <a name="introducing-advanced-audit"></a>Présentation de l’audit avancé

[L’audit avancé dans Microsoft 365](advanced-audit.md) introduit de nouvelles fonctionnalités d’audit qui peuvent aider votre organisation à lancer des enquêtes d’investigation et de conformité. Les points forts incluent la rétention à long terme des journaux d’audit, les stratégies de rétention de journal d’audit personnalisées, la nouvelle action d’audit de boîte aux lettres *MailItemsAccessed* et l’introduction d’une nouvelle limite de limitation au niveau du client, qui fournit à votre organisation son propre quota de bande passante entièrement alloué pour accéder à vos données d’audit.

### <a name="compliance-score--compliance-manager-preview-the-latest-enhancements"></a>Score de conformité & conformité : afficher un aperçu des dernières améliorations

Les principales mises à jour de cette version préliminaire sont les suivantes :

- Processus simplifié de création et de modification de modèles
- Avis et contrôle de contrôle de version pour les modèles et les actions
- Synchronisation des actions courantes entre les groupes
- Prise en charge linguistique désormais étendue au chinois (simplifié), chinois (traditionnel), français, allemand, italien, japonais, coréen, portugais (Brésil), russe et espagnol

En savoir plus sur [le Score de conformité et](compliance-score.md) le Gestionnaire de [conformité](compliance-manager-overview.md)

### <a name="sensitivity-labels-support-for-labeling-office-files-in-sharepoint-and-onedrive-preview"></a>Étiquettes de niveau de sensibilité : prise en charge de l’étiquetage des fichiers Office dans SharePoint et OneDrive (aperçu)

L’activation de l’aperçu permet aux utilisateurs d’appliquer des étiquettes de sensibilité dans Office sur le web. Ils pourront voir le  bouton Sensibilité sur le ruban et le nom d’étiquette appliqué dans la barre d’état. En outre, s’il utilise des applications de bureau pour étiqueter puis enregistrer ses fichiers sur SharePoint ou OneDrive, Microsoft 365 peut désormais traiter le contenu de ces fichiers si des paramètres de chiffrement sont appliqués à l’étiquette. La co-horation, eDiscovery, la protection contre la perte de données, la recherche et d’autres fonctionnalités collaboratives sont également pris en charge dans ces circonstances.

[Découvrez comment activer la prévisualisation](sensitivity-labels-sharepoint-onedrive-files.md)

## <a name="february-2020"></a>Février 2020

### <a name="insider-risk-management-is-officially-released"></a>La gestion des risques internes est officiellement publiée

Roll de papier, veuillez...<br>La gestion des risques internes est désormais disponible pour les organisations avec les abonnements suivants :

- [Microsoft 365 E5](https://go.microsoft.com/fwlink/?linkid=2120431) (payant ou d’essai)
- Abonnement Microsoft 365 Entreprise E3 avec le module de [conformité Microsoft E5](https://go.microsoft.com/fwlink/?linkid=2120432)

Nous avons apporté des améliorations depuis la [](insider-risk-management-configure.md#step-1-enable-permissions-for-insider-risk-management) version préliminaire, notamment de nouveaux groupes de rôles et des paramètres à l’échelle [de la solution.](insider-risk-management-configure.md#step-4-configure-insider-risk-settings)

Comme toujours, laissez vos commentaires lorsque vous utilisez la solution afin de continuer à apporter des améliorations.

### <a name="records-management"></a>Gestion des enregistrements

Cette nouvelle solution regroupe toutes les fonctionnalités de gestion des enregistrements sous un même cadre. Les points forts incluent l’introduction du gestion des versions des enregistrements pour SharePoint et OneDrive et la preuve de destruction des enregistrements.

![Page Gestion des enregistrements dans le Centre de conformité Microsoft 365](../media/mcc-records-management-page.png)

[En savoir plus sur la gestion des enregistrements](records-management.md)

### <a name="solution-spotlight-data-connectors-for-facebook-and-twitter"></a>Solution à la une : connecteurs de données pour Facebook et Twitter

Les connecteurs de [données ont](#just-launched) été publiés le mois dernier et nous recherchons votre aide pour tester les connecteurs suivants.

- [Pages d’entreprise Facebook](archive-facebook-data-with-sample-connector.md). Importe et archive les données des pages d’entreprise Facebook vers Microsoft 365. Utile pour les solutions de conformité telles que la gestion des enregistrements et eDiscovery.
- [Twitter](archive-twitter-data-with-sample-connector.md). Importe et archive des données de Twitter vers Microsoft 365. Utile pour les solutions de conformité telles que la gestion des enregistrements et eDiscovery.

Au cours de la mise en place et de la validation de ces connecteurs, laissez-nous des commentaires sur ce qui s’est bien passé, ce qui ne s’est pas passé et ce que nous pouvons faire pour améliorer l’expérience.

## <a name="january-2020"></a>Janvier 2020

L’attente est terminée. Nous sommes heureux d’annoncer que le Centre de conformité Microsoft 365 est disponible pour tous les clients avec les plans Microsoft 365, Office 365, Enterprise Mobility + Security (EMS) et Windows 10 Entreprise. Toutes les données ou stratégies que vous gériez dans le Centre de sécurité et conformité & sont disponibles dans le centre de conformité, il n’est donc pas nécessaire d’aller-retour.

Signet et rendez-vous maintenant pour faire une visite guidée de votre magasin unique pour [https://compliance.microsoft.com](https://compliance.microsoft.com) la gestion de la conformité au sein de votre organisation... ou [lisez cet article](microsoft-365-compliance-center.md) pour en savoir plus.

![Page d’accueil du Centre de conformité Microsoft 365](../media/mcc-home-ga.png)

Nous avons également publié des solutions nouvelles et mises à jour ce mois-ci. Voici un coup d’œil rapide sur les points forts.

### <a name="now-in-preview"></a>Maintenant en prévisualisation

**Gestion des risques internes (aperçu)**

Nous sommes heureux d’annoncer que notre solution de gestion des risques internes est désormais en prévisualisation publique. En résumé, la gestion des risques internes permet à votre organisation d’identifier et d’agir de manière intelligente sur les risques internes en fournissant :

- Contrôles d’anonymité pour garantir la confidentialité de l’utilisateur.
- Modèles de stratégie intelligents avec des indicateurs natifs et tiers qui identifient les menaces internes, telles que les fuites de données.
- Flux de travail d’enquête de bout en bout intégrés qui s’étendent aux équipes juridiques, ressources humaines et it.

Nous aimeriez savoir ce que vous en pensez. Au cours de l’utilisation de la solution, laissez-nous vos commentaires afin de nous assurer que nous nous sommes assurés de répondre à vos besoins alors que nous nous dirigeons vers une disponibilité générale.

[En savoir plus sur la gestion des risques internes](insider-risk-management.md)

### <a name="just-launched"></a>Lancement

**Conformité des communications**

Entre la phase de prévisualisation et la disponibilité totale, la conformité des communications est un composant clé de notre nouvel ensemble de solutions de risques internes. Cette solution robuste permet de réduire les risques de communication à l’aide de flux de travail pour détecter, examiner et prendre des mesures correctives pour les messages qui ne répondent pas aux normes de votre organisation.

Les commentaires des clients pendant la prévisualisation ont été incroyables. Plusieurs améliorations ont été apportées, notamment une première expérience de première expérience de mise en place, des améliorations des actions d’examen et de correction, et bien plus encore.

[En savoir plus sur la conformité des communications](communication-compliance.md)

![Page Conformité des communications dans le Centre de conformité Microsoft 365 affichant la première carte de l’expérience d’accueil](../media/mcc-communication-compliance-page-with-fre.png)

**Connecteurs de données**

Auparavant, partageant de l’espace avec d’autres fonctionnalités « Import » dans le Centre de sécurité & conformité Office 365, les connecteurs de données ont désormais leur propre domicile dans le Centre de conformité Microsoft 365. Utilisez la nouvelle page « Connecteurs de données » pour importer et archiver des données des fichiers de ressources humaines (RH) de votre organisation et de différentes plateformes tierces (comme Facebook, LinkedIn, Twitter et Instant Bloomberg) vers les boîtes aux lettres de votre organisation Microsoft 365. Une fois importées, ces données peuvent être gérées dans plusieurs solutions de conformité, notamment eDiscovery, la gestion des risques internes, la conformité des communications, l’audit, les stratégies de rétention, etc.

[En savoir plus sur les connecteurs de données](archiving-third-party-data.md)

![Page Connecteurs de données dans le Centre de conformité Microsoft 365](../media/mcc-data-connectors-page.png)

### <a name="noteworthy-updates"></a>Mises à jour importantes

**Nouveaux modèles d’évaluation pour le Score de conformité (aperçu)**

Nous mettons tout en œuvre pour vous aider à prendre de l’avance dans le paysage de conformité en constante évolution, notre équipe du Score de conformité a livré un nouvel ensemble de modèles pour vous aider à évaluer la posture de conformité de votre organisation par rapport aux réglementations récentes et obtenir des conseils sur la façon d’implémenter des contrôles plus efficaces. Vous verrez de nouveaux modèles pour :

- ISO/IEC 27701:2019
- California Consumer Privacy Act (CCPA)
- Loi générale sur la protection des données au Brésil (Lei Geral de Proteção de Dados - LGPD)
- SOC 1 Type 2 et SOC 2 Type 2

[En savoir plus sur les modèles de score de conformité](compliance-score.md#templates)