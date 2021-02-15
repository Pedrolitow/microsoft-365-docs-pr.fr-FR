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
description: Que vous ajoutiez de nouvelles solutions au centre de conformité, mettiez à jour les fonctionnalités existantes en fonction de vos commentaires ou mettiez en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester informé du paysage de conformité en constante évolution. Découvrez ce que nous avons fait ce mois-ci.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 40140c950bb42078cb1e72ae74762db00a4516b6
ms.sourcegitcommit: a62ac3c01ba700a51b78a647e2301f27ac437c5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50233162"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nouveautés dans la conformité Microsoft 365

Que ce soit en ajoutant de nouvelles solutions au Centre de conformité [Microsoft 365,](microsoft-365-compliance-center.md)en mettant à jour les fonctionnalités existantes en fonction de vos commentaires ou en mettant en place une documentation actualisée et mise à jour, Microsoft 365 vous aide à rester au-dessus du paysage de conformité en constante évolution. Consultez la ci-dessous pour voir les nouveautés de la conformité Microsoft 365 aujourd’hui.

> [!NOTE]
> Certaines fonctionnalités de conformité sont déployées à différentes vitesses pour nos clients. Si vous ne voyez pas encore de fonctionnalité, essayez de vous ajouter à [la version ciblée.](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365)

> [!TIP]
> Vous êtes intéressé par ce qui se passe dans d’autres centres d’administration ? Consultez les articles suivants :<br>[Nouveautés du Centre d’administration Microsoft 365](https://docs.microsoft.com/office365/admin/whats-new-in-preview)<br>[Nouveautés du Centre d’administration SharePoint](https://docs.microsoft.com/sharepoint/what-s-new-in-admin-center)<br>[Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)<br><br>
Consultez la feuille de route [Microsoft 365](https://www.microsoft.com/en-us/microsoft-365/roadmap) pour en savoir plus sur les fonctionnalités de Microsoft 365 qui ont été lancées, sont en cours de déploiement, sont en cours de développement, ont été annulées ou publiées précédemment.

## <a name="january-2021"></a>Janvier 2021

### <a name="support-for-card-content-in-teams"></a>Prise en charge du contenu de carte dans Teams

Les solutions de conformité Microsoft 365 [](https://docs.microsoft.com/microsoftteams/platform/task-modules-and-cards/what-are-cards) suivantes permettent désormais de détecter le contenu de carte généré par le biais d’applications dans les messages Teams :

- **Core et Advanced eDiscovery**. Le contenu de la carte peut désormais [être mis en attente](create-ediscovery-holds.md#preserve-card-content) ou inclus dans les [recherches](https://docs.microsoft.com/microsoftteams/ediscovery-investigation#search-for-card-content) (s’applique également à la recherche de contenu).
- **Audit**. L’activité de carte est [désormais enregistrée dans le journal d’audit.](https://docs.microsoft.com/microsoftteams/audit-log-events#teams-activities)
- **Stratégies de rétention**. Peut désormais utiliser des stratégies de rétention [pour conserver et supprimer le contenu de la carte.](retention-policies-teams.md#whats-included-for-retention-and-deletion)

### <a name="information-governance-and-records-management"></a>Gouvernance des informations et gestion des enregistrements

[Nouvelle évaluation de l’utilisation](retention-regulatory-requirements.md#new-zealand-public-records-act) de la gouvernance des informations et de la gestion des enregistrements pour répondre aux obligations de conformité de la Loi sur les enregistrements publics en Nouvelle-Zélande.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- Les étiquettes de niveau de sensibilité sont désormais pris en charge pour les clients du gouvernement américain (GCC et GCC-H).
- Nouvelle [prise en charge de l’étiquetage](sensitivity-labels-office-apps.md) automatique pour macOS.

## <a name="december-2020"></a>Décembre 2020

### <a name="spotlight-new-content-for-insider-risk-solutions"></a>À la une : nouveau contenu pour les solutions à risque internes

L’équipe de contenu de conformité Microsoft 365 travaille dur à la création de documents « solution de contenu » pour promouvoir la façon dont les fonctionnalités de conformité peuvent être utilisées ensemble pour vous aider à atteindre vos objectifs de conformité.

Tout d’abord, le contenu qui relie nos solutions à risque internes : conformité des communications, gestion des risques internes, obstacles à l’information et gestion des accès privilégiés. Voici un aperçu de ce que vous trouverez :

- [Nouvelle page d’accueil pour les solutions de risques internes.](insider-risk-solution-overview.md) Inclut des détails sur les risques que les solutions peuvent atténuer, les exigences de licence, la séquence de déploiement, les illustrations d’architecture, les ressources de formation, etc.
- Nouveaux articles de présentation pour chaque solution à risque interne. Conseils et liens vers des articles qui vous aident à en savoir plus sur, planifier, déployer et gérer chaque solution :
  - [Conformité des communications](communication-compliance-solution-overview.md)
  - [Gestion des risques internes](insider-risk-management-solution-overview.md)
  - [Obstacles aux informations](information-barriers-solution-overview.md)
  - [Gestion des accès privilégiés](privileged-access-management-solution-overview.md)
  
D’autres documents sur les solutions de contenu seront bientôt disponible !

### <a name="advanced-ediscovery"></a>Advanced eDiscovery

Amélioration du flux de travail et des fonctionnalités pour l’ajout de [dépositaires](add-custodians-to-case.md) et [de sources](non-custodial-data-sources.md) de données non privatives à un cas Advanced eDiscovery.

### <a name="data-connectors"></a>Connecteurs de données

[Quatre nouveaux connecteurs Globanet publiés](archiving-third-party-data.md#third-party-data-connectors): Redtail Speak, Salesforce Queue, ServiceNow et Yieldbroker.

### <a name="encryption"></a>Chiffrement

Présentation de [la clé client pour Microsoft 365 au niveau du client.](customer-key-tenant-level.md) À l’aide des clés que vous fournissez, vous pouvez créer une stratégie de chiffrement de données (DEP) et l’affecter au client. Le PD DEP chiffre les données sur le client pour ces charges de travail :

- Messages de conversation Teams (conversations 1:1, conversations de groupe, conversations de réunion et conversations de canal)
- Messages multimédias Teams (images, extraits de code, vidéos, images wiki)
- Enregistrements d’appels et de réunions Teams stockés dans le stockage Teams
- Notifications de conversation Teams
- Suggestions de conversation Teams par Cortana
- Messages d’état Teams
- Informations sur l’utilisateur et le signal pour Exchange Online

### <a name="records-management"></a>Gestion des enregistrements

Le groupe [de rôles d’administrateur](get-started-with-records-management.md#permissions-required-for-records-management) Gestion des enregistrements accorde désormais des autorisations pour toutes les fonctionnalités de gestion des enregistrements, y compris la révision de la disposition.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

- [Étiqueter automatiquement les données dans Azure Purview (aperçu)](https://docs.microsoft.com/azure/purview/create-sensitivity-label). Vous pouvez désormais créer et appliquer automatiquement des étiquettes de niveau de sensibilité à des ressources dans Azure Purview, telles que des fichiers dans le stockage Blob Azure et des colonnes de base de données dans SQL Server.
- [Exiger que les utilisateurs appliquent une étiquette aux éléments.](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents) Également appelée « étiquetage obligatoire » , cette nouvelle option exige que les utilisateurs choisissent et appliquent une étiquette de niveau de sensibilité dans les scénarios spécifiques.

## <a name="november-2020"></a>Novembre 2020
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

[Prise en charge des languesJCK.](ediscovery-cjk-support.md) Advanced eDiscovery prend désormais en charge les langues de jeu de caractères sur deux caractères, appelées collectivement languesJCK (y compris le chinois simplifié, le chinois traditionnel, le japonais et le coréen). Ceux-ci peuvent être utilisés dans plusieurs scénarios d’ensembles de révision avancés.

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
- [Action de correction « Améliorer la classification](communication-compliance-investigate-remediate.md#step-3-decide-on-a-remediation-action)». Les alertes contenant des éléments qui correspondent à des classifieurs entra mentables peuvent tirer parti des commentaires pour réduire les faux positifs dans votre organisation. **L’option Améliorer la classification** vous permet de fournir des commentaires si les éléments détectés correspondent au classifieur configuré dans la stratégie de conformité des communications associée. Vous pouvez même suggérer d’autres classifieurs à associer à l’élément pour améliorer la précision des correspondances pour les alertes futures.

### <a name="data-connectors"></a>Connecteurs de données

- [Nouveaux connecteurs de données tiers.](archiving-third-party-data.md#third-party-data-connectors) 25 nouveaux connecteurs de données, dont 14 connecteurs globanet et 8 connecteurs de télémessage.
- [Connecteur de badging physique](import-physical-badging-data.md). Importez les données de mauvaise gestion physiques, telles que les événements d’accès physique bruts de l’employé ou les alarmes d’accès physique générées par le système de mauvaise gestion de votre organisation. Par exemple, les entrées des bâtiments, des salles de serveurs ou des centres de données. Les données de mauvais traitement physique peuvent être utilisées par la solution de gestion des risques internes pour protéger votre organisation contre les activités malveillantes ou le vol de données au sein de votre organisation.

### <a name="insider-risk-management"></a>Gestion des risques internes

- [Intégration de Microsoft Teams.](insider-risk-management-settings.md#microsoft-teams-preview) Lorsque l’intégration de Teams est mise en place dans les paramètres de risques internes, vous pouvez coordonner et collaborer avec d’autres parties prenantes dans Teams sur des tâches telles que le partage et le stockage sécurisés de données relatives à des cas individuels, le suivi et l’examen des activités de réponse des analystes et des enquêteurs, et bien plus encore.
- [Flux Power Automate](insider-risk-management-settings.md#power-automate-flows-preview). Configurer des flux pour automatiser les tâches importantes pour les cas et les utilisateurs, telles que la récupération d’utilisateurs, d’alertes et d’informations de cas à partager avec les parties prenantes et d’autres applications, l’automatisation d’actions telles que la publication dans des notes de cas, etc.
- [Activité du contenu](insider-risk-management-alerts.md#activity-explorer-preview). Disponible lors de l’examen des alertes, l’Explorateur d’activités fournit aux enquêteurs et aux analystes un outil analytique complet pour explorer chaque alerte. Examinez rapidement une chronologie des activités à risque détectées et identifiez et filtrez toutes les activités à risque associées aux alertes.

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
> Pour toutes les fonctionnalités, si vous fournissez au moins 30 réponses de commentaires, nous allons créer une version retrainée de ce classifieur que vous pouvez consulter. En cas d’amélioration, vous pouvez republier le classifieur.

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
- Nouvelle expérience de paramètres de conformité des communications qui inclut les paramètres de [confidentialité](communication-compliance-feature-reference.md#privacy) et les [modèles de notification.](communication-compliance-feature-reference.md#notice-templates)
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
- Nouvelle [expérience d’exportation de](export-documents-from-review-set.md)téléchargement direct, ce qui élimine la nécessité d’utiliser Azure Storage Explorer pour télécharger le contenu du cas.
