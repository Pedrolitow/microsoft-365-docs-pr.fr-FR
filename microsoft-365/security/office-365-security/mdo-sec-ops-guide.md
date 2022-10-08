---
title: Guide des opérations de sécurité pour Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
ms.custom: ''
description: Playbook normatif pour le personnel SecOps afin de gérer Microsoft Defender pour Office 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 0e21a534ef438396bb94221df992e8c343dbda4b
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072264"
---
# <a name="microsoft-defender-for-office-365-security-operations-guide"></a>Guide des opérations de sécurité Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article fournit une vue d’ensemble des exigences et des tâches pour le fonctionnement réussi des Microsoft Defender pour Office 365 dans votre organisation. Ces tâches permettent de garantir que votre centre des opérations de sécurité (SOC) offre une approche fiable et de haute qualité pour protéger, détecter et répondre aux menaces de sécurité liées à la messagerie et à la collaboration.

Le reste de ce guide décrit les activités requises pour le personnel SecOps. Les activités sont regroupées en tâches quotidiennes, hebdomadaires, mensuelles et ad hoc.

Un article complémentaire de ce guide fournit une vue d’ensemble de la [gestion des incidents et des alertes à partir de Defender pour Office 365 sur la page Incidents du portail Microsoft 365 Defender](mdo-sec-ops-manage-incidents-and-alerts.md).

Le [Guide des opérations de sécurité Microsoft 365 Defender](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops) contient des informations supplémentaires que vous pouvez utiliser pour la planification et le développement.

Pour obtenir une vidéo sur ces informations, consultez <https://youtu.be/eQanpq9N1Ps>.

## <a name="daily-activities"></a>Activités quotidiennes

### <a name="monitor-the-microsoft-365-defender-incidents-queue"></a>Surveiller la file d’attente des incidents Microsoft 365 Defender

La page **Incidents** du portail <https://security.microsoft.com/incidents-queue> Microsoft 365 Defender (également appelée _file d’attente d’incidents_) vous permet de gérer et de surveiller les événements à partir des sources suivantes dans Defender pour Office 365 :

- [Alertes](../../compliance/alert-policies.md#default-alert-policies).
- [Investigation et réponse automatisées (AIR).](automated-investigation-response-office.md)

Pour plus d’informations sur la file d’attente [d’incidents, consultez Hiérarchiser les incidents dans Microsoft 365 Defender](../defender/incident-queue.md).

Votre plan de triage pour la surveillance de la file d’attente d’incidents doit utiliser l’ordre de priorité suivant pour les incidents :

1. **Un clic d’URL potentiellement malveillant a été détecté**.
2. **L’utilisateur ne peut pas envoyer de courrier électronique**.
3. **Modèles d’envoi de courrier suspect détectés**.
4. **Email signalés par l’utilisateur comme des programmes malveillants ou des hameçonnages**, et **plusieurs utilisateurs ont signalé des courriers électroniques comme des programmes malveillants ou des hameçonnages**.
5. **Email messages contenant un fichier malveillant supprimé après la remise**, **Email messages contenant une URL malveillante supprimée après la remise** et **Email messages d’une campagne supprimés après la remise**.
6. **Phish remis en raison d’un remplacement ETR**, **Phish remis parce que le dossier Courrier indésirable d’un utilisateur est désactivé** et **Phish remis en raison d’une stratégie d’autorisation IP**
7. **Un programme malveillant n’est pas zappé car ZAP est désactivé** et **Phish n’est pas zappé car ZAP est désactivé**.

La gestion des files d’attente d’incidents et les personnages responsables sont décrits dans le tableau suivant :

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Triage des incidents dans la file d’attente incidents à <https://security.microsoft.com/incidents-queue>.|Journalière|Vérifiez que tous les incidents de gravité **moyenne** et **élevée** de Defender pour Office 365 sont triés.|Équipe des opérations de sécurité|
|Examinez et prenez des mesures de réponse sur les incidents.|Journalière|Examinez tous les incidents et effectuez activement les actions de réponse recommandées ou manuelles.|Équipe des opérations de sécurité|
|Résolvez les incidents.|Journalière|Si l’incident a été corrigé, résolvez l’incident. La résolution de l’incident résout toutes les alertes actives liées et associées.|Équipe des opérations de sécurité|
|Classifier les incidents.|Journalière|Classifiez les incidents comme vrai ou faux. Pour les alertes vraies, spécifiez le type de menace. Cette classification permet à votre équipe de sécurité de voir les modèles de menaces et de défendre votre organisation contre elles.|Équipe des opérations de sécurité|

### <a name="manage-false-positive-and-false-negative-detections"></a>Gérer les détections de faux positifs et de faux négatifs

Dans Defender pour Office 365, vous gérez les faux positifs (bon courrier marqué comme mauvais) et les faux négatifs (courrier incorrect autorisé) aux emplacements suivants :

- Portail [soumissions (soumissions d’administrateurs).](admin-submission.md)
- Liste [d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md)
- [Threat Explorer](threat-explorer.md)

Pour plus d’informations, consultez la section [Gérer les détections faux positifs et faux négatifs](#manage-false-positive-and-false-negative-detections) plus loin dans cet article.

La gestion des faux positifs et faux négatifs et les personnages responsables sont décrits dans le tableau suivant :

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Envoyez des faux positifs et des faux négatifs à Microsoft à l’adresse <https://security.microsoft.com/reportsubmission>.|Journalière|Fournissez des signaux à Microsoft en signalant des détections incorrectes d’e-mail, d’URL et de fichiers.|Équipe des opérations de sécurité|
|Analysez les détails de la soumission de l’administrateur.|Journalière|Comprenez les facteurs suivants pour les soumissions que vous faites à Microsoft : <ul><li>Ce qui a provoqué le faux positif ou le faux négatif.</li><li>État de votre configuration Defender pour Office 365 au moment de la soumission.</li><li>Indique si vous devez apporter des modifications à votre configuration Defender pour Office 365.</li></ul>|Équipe des opérations de sécurité <br/><br/> Administration de la sécurité|
|Ajoutez des entrées de bloc dans la liste d’autorisations/de blocs du locataire à l’adresse <https://security.microsoft.com/tenantAllowBlockList>.|Journalière|Utilisez la liste d’autorisation/de blocage du locataire pour ajouter des entrées de bloc pour les détections d’URL, de fichier ou d’expéditeur faux négatifs si nécessaire.|Équipe des opérations de sécurité|
|Libérer le faux positif de la mise en quarantaine.|Journalière|Une fois que le destinataire a confirmé que le message a été mis en quarantaine incorrectement, vous pouvez libérer ou approuver les demandes de mise en production pour les utilisateurs. <br/><br/> Pour contrôler ce que les utilisateurs peuvent faire pour leurs propres messages mis en quarantaine (y compris la mise en production ou la demande de mise en quarantaine), consultez [Stratégies de quarantaine](quarantine-policies.md).|Équipe des opérations de sécurité <br/><br/> Équipe de messagerie|

### <a name="review-phishing-and-malware-campaigns-that-resulted-in-delivered-mail"></a>Passer en revue les campagnes de hameçonnage et de programmes malveillants qui ont abouti à la remise du courrier

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue les campagnes de messagerie.|Journalière|[Passez en revue les campagnes de messagerie](campaigns.md) ciblant votre organisation sur <https://security.microsoft.com/campaigns>. Concentrez-vous sur les campagnes qui ont abouti à la remise des messages aux destinataires. <br/><br/> Supprimez les messages des campagnes qui existent dans les boîtes aux lettres des utilisateurs. Cette action est requise uniquement lorsqu’une campagne contient des e-mails qui n’ont pas déjà été corrigés par des actions d’incidents, un [vidage automatique de zéro heure (ZAP)](zero-hour-auto-purge.md) ou une correction manuelle.|Équipe des opérations de sécurité|

## <a name="weekly-activities"></a>Activités hebdomadaires

### <a name="review-email-detection-trends-in-defender-for-office-365-reports"></a>Examiner les tendances de détection des e-mails dans les rapports Defender pour Office 365

Dans Defender pour Office 365, vous pouvez utiliser les rapports suivants pour passer en revue les tendances de détection des e-mails dans votre organisation :

- Rapport [d’état du flux de courrier](view-mail-flow-reports.md#mailflow-status-report)
- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report)

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue les rapports de détection des e-mails à l’adresse suivante : <ul><li><https://security.microsoft.com/reports/TPSAggregateReportATP></li><li><https://security.microsoft.com/mailflowStatusReport?viewid=type></li></ul>|En semaines|Passez en revue les tendances de détection des courriers malveillants, du hameçonnage et du courrier indésirable par rapport aux bons e-mails. L’observation au fil du temps vous permet de voir les modèles de menace et de déterminer si vous devez ajuster vos stratégies de Defender pour Office 365.|Administration de la sécurité <br/><br/> Équipe des opérations de sécurité|

### <a name="track-and-respond-to-emerging-threats-using-threat-analytics"></a>Suivre et répondre aux menaces émergentes à l’aide de l’analytique des menaces

Utilisez [l’analyse des menaces](/microsoft-365/security/defender-endpoint/threat-analytics) pour passer en revue les menaces actives et à tendance.

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue les menaces dans l’analyse des menaces à l’adresse <https://security.microsoft.com/threatanalytics3>.|En semaines|L’analyse des menaces fournit une analyse détaillée, y compris les éléments suivants : <ul><li>E/S par E/S.</li><li>Requêtes de chasse sur les acteurs de menaces actifs et leurs campagnes.</li><li>Techniques d’attaque populaires et nouvelles.</li><li>Vulnérabilités critiques.</li><li>Surfaces d’attaque courantes.</li><li>Programmes malveillants répandus.</li></ul>|Équipe des opérations de sécurité <br/><br/> Équipe de chasse aux menaces|

### <a name="review-top-targeted-users-for-malware-and-phishing"></a>Examiner les principaux utilisateurs ciblés pour les programmes malveillants et le hameçonnage

Utilisez l’onglet **[Principaux utilisateurs ciblés](threat-explorer.md#top-targeted-users)** dans l’Explorateur de menaces pour découvrir ou confirmer les utilisateurs qui sont les principales cibles pour les programmes malveillants et les e-mails de hameçonnage.

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue l’onglet **Utilisateurs principaux ciblés** dans l’Explorateur de menaces à l’adresse <https://security.microsoft.com/threatexplorer>.|En semaines|Utilisez les informations pour décider si vous devez ajuster les stratégies ou les protections pour ces utilisateurs. Ajoutez les utilisateurs affectés aux [comptes Priority](/microsoft-365/admin/setup/priority-accounts) pour bénéficier des avantages suivants : <ul><li>Visibilité supplémentaire lorsque des incidents les affectent.</li><li>Heuristiques personnalisées pour les modèles de flux de messagerie des cadres (protection prioritaire des comptes).</li><li>[Email problèmes liés au rapport des comptes prioritaires](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)</li></ul>|Administration de la sécurité <br/><br/> Équipe des opérations de sécurité|

### <a name="review-top-malware-and-phishing-campaigns-that-target-your-organization"></a>Passez en revue les principales campagnes de hameçonnage et de programmes malveillants ciblant votre organisation

Les vues de campagne révèlent les attaques par hameçonnage et les programmes malveillants contre votre organisation. Pour plus d’informations, consultez [Affichages de campagne dans Microsoft Defender pour Office 365](campaigns.md).

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Utilisez **les vues de campagne** pour passer en <https://security.microsoft.com/campaigns> revue les attaques par hameçonnage et les programmes malveillants qui vous affectent.|En semaines|Découvrez les attaques et techniques et ce que Defender pour Office 365 a pu identifier et bloquer. <br/><br/> Pour plus d’informations sur une campagne, utilisez télécharger le rapport sur les **menaces** dans les vues de campagne.|Équipe des opérations de sécurité|

## <a name="ad-hoc-activities"></a>Activités ad hoc

### <a name="manual-investigation-and-removal-of-email"></a>Examen manuel et suppression de l’e-mail

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Examinez et supprimez les e-mails incorrects dans l’Explorateur <https://security.microsoft.com/threatexplorer> de menaces en fonction des demandes des utilisateurs.|Ad hoc|Utilisez l’action **Déclencher une enquête** dans l’Explorateur de menaces pour démarrer un playbook d’investigation et de réponse automatisé sur n’importe quel e-mail des 30 derniers jours. Le déclenchement manuel d’une enquête permet de gagner du temps et des efforts en incluant de manière centralisée : <ul><li>Une investigation racine.</li><li>Étapes d’identification et de corrélation des menaces.</li><li>Actions recommandées pour atténuer ces menaces.</li></ul> <br/> Pour plus d’informations, consultez [Exemple : Un message de hameçonnage signalé par l’utilisateur lance un playbook d’investigation](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) <br/><br/> Vous pouvez également utiliser l’Explorateur de menaces pour [examiner manuellement les e-mails](investigate-malicious-email-that-was-delivered.md) avec de puissantes fonctionnalités de recherche et de filtrage et [effectuer une action de réponse manuelle](remediate-malicious-email-delivered-office-365.md) directement à partir du même endroit. Actions manuelles disponibles : <ul><li>Passer à la boîte de réception</li><li>Déplacer vers le courrier indésirable</li><li>Déplacer vers des éléments supprimés</li><li>Supprimer (récupération possible)</li><li>Suppression définitive.</li></ul>|Équipe des opérations de sécurité|

### <a name="proactively-hunt-for-threats"></a>Repérage proactif des menaces

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Recherche régulière et proactive des menaces à l’adresse suivante : <ul><li><https://security.microsoft.com/threatexplorer></li><li><https://security.microsoft.com/v2/advanced-hunting></li></ul>.|Ad hoc|Recherchez des menaces à l’aide de [l’Explorateur de menaces](threat-explorer.md) et de [la chasse avancée](../defender-endpoint/advanced-hunting-overview.md).|Équipe des opérations de sécurité <br/><br/> Équipe de chasse aux menaces|
|Partagez des requêtes de chasse.|Ad hoc|Partagez activement des requêtes fréquemment utilisées et utiles au sein de l’équipe de sécurité pour accélérer la chasse et la correction manuelles des menaces. <br/><br/> Utilisez [des suivis de menaces](threat-trackers.md) et [des requêtes partagées dans la chasse avancée](/microsoft-365/security/defender/advanced-hunting-shared-queries).|Équipe des opérations de sécurité <br/><br/> Équipe de chasse aux menaces|
|Créez des règles de détection personnalisées à l’adresse <https://security.microsoft.com/custom_detection>.|Ad hoc|[Créez des règles de détection personnalisées](../defender/custom-detections-overview.md) pour surveiller de manière proactive les événements, les modèles et les menaces en fonction de Defender pour Office 365 données dans La chasse anticipée. Les règles de détection contiennent des requêtes de chasse avancées qui génèrent des alertes en fonction des critères correspondants.|Équipe des opérations de sécurité <br/><br/> Équipe de chasse aux menaces|

### <a name="review-defender-for-office-365-policy-configurations"></a>Passer en revue les configurations de stratégie Defender pour Office 365

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue la configuration des stratégies Defender pour Office 365 à l’adresse <https://security.microsoft.com/configurationAnalyzer>.|Ad hoc <br/><br/> Mensuelle|Utilisez [l’analyseur de configuration](configuration-analyzer-for-security-policies.md) pour comparer vos paramètres de stratégie existants aux [valeurs Standard ou Strict recommandées pour Defender pour Office 365](recommended-settings-for-eop-and-office365.md). L’analyseur de configuration identifie les modifications accidentelles ou malveillantes qui peuvent réduire la posture de sécurité de votre organisation. <br/><br/> Vous pouvez également utiliser [l’outil ORCA](https://aka.ms/getorca) basé sur PowerShell.|Administration de la sécurité <br/><br/> Équipe de messagerie|
|Passez en revue les remplacements de détection dans Defender pour Office 365 à<https://security.microsoft.com/reports/TPSMessageOverrideReportATP>|Ad hoc <br/><br/> Mensuelle|Utilisez les [données view by System override \> Chart breakdown by Reason view](view-email-security-reports.md#view-data-by-system-override-and-chart-breakdown-by-reason) dans le **rapport d’état threat protection** pour passer en revue les e-mails détectés comme hameçonnage mais remis en raison des paramètres de stratégie ou de remplacement de l’utilisateur. <br/><br/> Examinez activement, supprimez ou ajustez les remplacements pour éviter la remise de courriers électroniques qui ont été jugés malveillants.|Administration de la sécurité <br/><br/> Équipe de messagerie|

### <a name="review-spoof-and-impersonation-detections"></a>Examiner les détections d’usurpation d’identité et d’emprunt d’identité

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue les **insights d’intelligence** sur l’usurpation d’identité et **les insights de détection d’emprunt d’identité** à l’adresse <ul><li><<https://security.microsoft.com/spoofintelligence>></li><li><https://security.microsoft.com/impersonationinsight></li></ul>.|Ad hoc <br/><br/> Mensuelle|Utilisez [l’insight d’intelligence de l’usurpation](learn-about-spoof-intelligence.md) d’identité et [l’insight d’emprunt](impersonation-insight.md) d’identité pour ajuster le filtrage des détections d’usurpation d’identité et d’emprunt d’identité.|Administration de la sécurité <br/><br/> Équipe de messagerie|

### <a name="review-priority-account-membership"></a>Passer en revue l’appartenance au compte prioritaire

|Activité|Cadence|Description|Persona|
|---|---|---|---|
|Passez en revue les personnes définies comme compte prioritaire à l’adresse <https://security.microsoft.com/securitysettings/userTags>.|Ad hoc|Maintenez l’appartenance des [comptes prioritaires](/microsoft-365/admin/setup/priority-accounts) à jour avec les modifications apportées à l’organisation afin d’obtenir les avantages suivants pour ces utilisateurs : <ul><li>Meilleure visibilité dans les rapports.</li><li>Filtrage dans les incidents et les alertes.</li><li>Heuristiques personnalisées pour les modèles de flux de messagerie des cadres (protection prioritaire des comptes).</li></ul> <br/> Utilisez [des balises utilisateur personnalisées](user-tags.md) pour que d’autres utilisateurs obtiennent : <ul><li>Meilleure visibilité dans les rapports.</li><li>Filtrage dans les incidents et les alertes.</li></ul>|Équipe des opérations de sécurité|

## <a name="appendix"></a>Annexe

### <a name="learn-about-microsoft-defender-for-office-365-tools-and-processes"></a>En savoir plus sur Microsoft Defender pour Office 365 outils et processus

Les membres de l’équipe chargée des opérations de sécurité et de la réponse doivent intégrer Defender pour Office 365 outils et fonctionnalités aux processus d’investigation et de réponse existants. L’apprentissage des nouveaux outils et fonctionnalités peut prendre du temps, mais il s’agit d’une partie essentielle du processus d’intégration. Le moyen le plus simple pour SecOps et les membres de l’équipe de sécurité de messagerie d’en savoir plus sur Defender pour Office 365 consiste à utiliser le contenu de formation disponible dans le cadre du contenu de formation Ninja à <https://aka.ms/mdoninja>.

Le contenu est structuré pour différents niveaux de connaissances (fondamentaux, intermédiaires et avancés) avec plusieurs modules par niveau.

De courtes vidéos pour des tâches spécifiques sont également disponibles dans la [Microsoft Defender pour Office 365 chaîne YouTube](https://www.youtube.com/playlist?list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf).

### <a name="permissions-for-defender-for-office-365-activities-and-tasks"></a>Autorisations pour les activités et tâches Defender pour Office 365

Les autorisations de gestion des Defender pour Office 365 dans le portail Microsoft 365 Defender et PowerShell sont basées sur le modèle d’autorisations de contrôle d’accès en fonction du rôle (RBAC). RBAC est le même modèle d’autorisations que celui utilisé par la plupart des services Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

> [!NOTE]
> Privileged Identity Management (PIM) dans Azure AD est également un moyen d’attribuer les autorisations requises au personnel SecOps. Pour plus d’informations, consultez [Privileged Identity Management (PIM) et pourquoi l’utiliser avec Microsoft Defender pour Office 365](use-privileged-identity-management-in-defender-for-office-365.md).

Les autorisations suivantes (rôles et groupes de rôles) sont disponibles dans Defender pour Office 365 et peuvent être utilisées pour accorder l’accès aux membres de l’équipe de sécurité :

- **Rôles Azure AD** : rôles centralisés qui attribuent des autorisations pour _tous les_ services Microsoft 365, y compris Defender pour Office 365. Vous pouvez afficher les rôles Azure AD et les utilisateurs affectés dans le portail Microsoft 365 Defender, mais vous ne pouvez pas les gérer directement là-bas. Au lieu de cela, vous gérez les rôles et les membres Azure AD dans <https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RolesAndAdministrators>. Les rôles les plus fréquents utilisés par les équipes de sécurité sont les suivants :
  - **Administrateur de sécurité**
  - **Opérateur de sécurité**
  - **Lecteur de sécurité**

- **Email & rôles de collaboration** : rôles et groupes de rôles qui accordent des autorisations spécifiques à Microsoft Defender pour Office 365. Les rôles suivants ne sont pas disponibles dans Azure AD, mais peuvent être importants pour les équipes de sécurité :

  - **Rôle d’aperçu** : attribuez ce rôle aux membres de l’équipe qui doivent afficher un aperçu ou télécharger des messages électroniques dans le cadre des activités d’investigation. Permet aux utilisateurs [d’afficher un aperçu et de télécharger](investigate-malicious-email-that-was-delivered.md#preview-role-permissions) des messages électroniques dans des boîtes aux lettres cloud à l’aide de la [page d’entité de messagerie](mdo-email-entity-page.md#email-preview-for-cloud-mailboxes).

    Par défaut, ce rôle est attribué uniquement aux groupes de rôles suivants :

    - Enquêteur de données
    - Le gestionnaire eDiscovery

    Pour attribuer ce rôle à un groupe de rôles nouveau ou existant, consultez [Modifier Email & l’appartenance au rôle de collaboration dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md#modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal).

  - **Rôle de recherche et de vidage** : approuvez la suppression des messages malveillants comme recommandé par AIR ou effectuez des actions manuelles sur les messages dans des expériences de chasse telles que l’Explorateur de menaces.

    Par défaut, ce rôle est attribué uniquement aux groupes de rôles suivants :

    - Enquêteur de données
    - Gestion de l’organisation

    Pour attribuer ce rôle à un groupe de rôles nouveau ou existant, consultez [Modifier Email & l’appartenance au rôle de collaboration dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md#modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal).

  - **Gestionnaire AllowBlockList du locataire** : gérez les entrées d’autorisation et de blocage dans la [liste d’autorisations/de blocs du locataire](manage-tenant-allow-block-list.md). Le blocage des URL, des fichiers (à l’aide du hachage de fichier) ou des expéditeurs est une action de réponse utile à effectuer lors de l’examen des e-mails malveillants qui ont été remis.

    Par défaut, ce rôle est attribué uniquement au groupe de **rôles Opérateur de sécurité** . Toutefois, les membres des **groupes de rôles Administrateurs de sécurité** et Gestion de l’organisation peuvent également gérer les entrées dans la liste d’autorisation/de blocage du locataire.

### <a name="siemsoar-integration"></a>Intégration de SIEM/SOAR

Defender pour Office 365 expose la plupart de ses données via un ensemble d’API programmatiques. Ces API vous aident à automatiser les flux de travail et à tirer pleinement profit des fonctionnalités de Defender pour Office 365. Les données sont disponibles via les [API Microsoft 365 Defender](/microsoft-365/security/defender/api-overview) et peuvent être utilisées pour intégrer Defender pour Office 365 dans des solutions SIEM/SOAR existantes.

- [API d’incident](/microsoft-365/security/defender/api-incident) : les alertes Defender pour Office 365 et les enquêtes automatisées sont des parties actives des incidents dans Microsoft 365 Defender. Les équipes de sécurité peuvent se concentrer sur ce qui est essentiel en regroupant l’étendue complète des attaques et toutes les ressources impactées.

- [API de streaming d’événements](/microsoft-365/security/defender/streaming-api) : autorise l’envoi d’événements et d’alertes en temps réel dans un flux de données unique au fur et à mesure. Les types d’événements Defender pour Office 365 pris en charge sont les suivants :
  - [EmailEvents](/microsoft-365/security/defender/advanced-hunting-emailevents-table)
  - [EmailUrlInfo](/microsoft-365/security/defender/advanced-hunting-emailurlinfo-table)
  - [EmailAttachmentInfo](/microsoft-365/security/defender/advanced-hunting-emailattachmentinfo-table)
  - [EmailPostDeliveryEvents](/microsoft-365/security/defender/advanced-hunting-emailpostdeliveryevents-table)

  Les événements contiennent des données provenant du traitement de tous les e-mails (y compris les messages intra-organisationnels) au cours des 30 derniers jours.

- [API de chasse avancée](/microsoft-365/security/defender/api-advanced-hunting) : autorise la chasse contre les menaces inter-produits.

- [API d’évaluation des menaces](/graph/api/resources/threatassessment-api-overview) : peut être utilisée pour signaler le courrier indésirable, les URL de hameçonnage ou les pièces jointes de programmes malveillants directement à Microsoft.

Pour connecter des incidents Defender pour Office 365 et des données brutes à Microsoft Sentinel, vous pouvez utiliser le [connecteur Microsoft 365 Defender (M365D)](/azure/sentinel/connect-microsoft-365-defender?tabs=MDO)

Vous pouvez utiliser cet exemple « Hello World » simple pour tester l’accès d’API aux API Microsoft Defender : [Hello World pour Microsoft 365 Defender’API REST](/microsoft-365/security/defender/api-hello-world).

Pour plus d’informations sur l’intégration de l’outil SIEM, consultez [Intégrer vos outils SIEM à Microsoft 365 Defender](/microsoft-365/security/defender/configure-siem-defender).

## <a name="address-false-positives-and-false-negatives-in-defender-for-office-365"></a>Résoudre les faux positifs et les faux négatifs dans Defender pour Office 365

Les envois d’utilisateurs et d’administrateurs de messages électroniques sont des signaux de renforcement positifs critiques pour nos systèmes de détection de Machine Learning. Les soumissions nous aident à examiner, trier, apprendre rapidement et atténuer les attaques. Le signalement actif de faux positifs et de faux négatifs est une activité importante qui fournit des commentaires aux Defender pour Office 365 lorsque des erreurs sont commises lors de la détection.

Les organisations disposent de plusieurs options pour configurer les soumissions d’utilisateurs. Selon la configuration, les équipes de sécurité peuvent être plus actives lorsque les utilisateurs envoient des faux positifs ou des faux négatifs à Microsoft :

- Les soumissions d’utilisateurs sont envoyées à Microsoft pour analyse lorsque les [paramètres de message signalés par l’utilisateur sont configurés](user-submission.md) avec l’un des paramètres suivants :
  - Envoyez les messages signalés à : Microsoft.
  - Envoyez les messages signalés à la boîte aux lettres de Microsoft et de mon organisation.

  Les membres des équipes de sécurité doivent effectuer [des soumissions d’administrateurs complémentaires lorsque des](admin-submission.md) faux positifs ou des faux négatifs qui n’ont pas été signalés par les utilisateurs ont été découverts par les équipes d’opérations.

- Lorsque les messages signalés par l’utilisateur sont configurés pour envoyer des messages uniquement à la boîte aux lettres de l’organisation, les équipes de sécurité doivent envoyer activement les faux positifs signalés par l’utilisateur et les faux négatifs à Microsoft via des soumissions d’administrateur.

Chaque fois qu’un utilisateur signale un message comme hameçonnage, Defender pour Office 365 génère une alerte et l’alerte déclenche un playbook AIR. Si possible, la logique d’incident met en corrélation ces informations avec d’autres alertes et événements. Cette consolidation des informations permet aux équipes de sécurité de trier, d’examiner et de répondre aux e-mails signalés par l’utilisateur.

Les soumissions d’utilisateurs et d’administrateurs sont gérées par le pipeline de soumission par Microsoft, qui suit un processus étroitement intégré. Ce processus comprend les éléments suivants :

- Réduction du bruit.
- Triage automatisé.
- Notation par les analystes de sécurité et les solutions basées sur l’apprentissage automatique en partenariat humain.

Pour plus d’informations, consultez [Signaler un e-mail dans Defender pour Office 365 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/reporting-an-email-in-microsoft-defender-for-office-365/ba-p/2870231).

Les membres de l’équipe de sécurité peuvent effectuer des soumissions à partir de plusieurs emplacements dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>suivante :

- [Administration soumission](admin-submission.md) : utilisez le portail d’envoi pour envoyer des courriers indésirables, du hameçonnage, des URL et des fichiers suspects à Microsoft.
- Directement à partir de l’Explorateur de menaces à l’aide de l’une des actions de message suivantes :
  - Nettoyer le rapport
  - Signaler le hameçonnage
  - Signaler un programme malveillant
  - Signaler le courrier indésirable

  Vous pouvez sélectionner jusqu’à 10 messages pour effectuer une soumission en bloc. Administration les soumissions créées de cette façon sont également visibles dans le portail de soumission.

Pour l’atténuation à court terme des faux négatifs, les équipes de sécurité peuvent gérer directement les entrées de bloc pour les fichiers, LES URL et les domaines ou les adresses e-mail dans la [liste d’autorisation/de blocage du locataire](manage-tenant-allow-block-list.md).

Pour l’atténuation à court terme des faux positifs, les équipes de sécurité ne peuvent pas gérer directement les entrées d’autorisation pour les domaines et les adresses e-mail dans la liste d’autorisation/de blocage du locataire. Au lieu de cela, ils doivent utiliser [les soumissions d’administrateur](admin-submission.md) pour signaler le message électronique sous la forme d’un faux positif. Pour obtenir des instructions, consultez [Utiliser le portail Microsoft 365 Defender pour créer des entrées d’autorisation pour les domaines et les adresses e-mail dans le portail Soumissions](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal).

[La mise en quarantaine](manage-quarantined-messages-and-files.md) dans Defender pour Office 365 contient des messages et fichiers potentiellement dangereux ou indésirables. Les équipes de sécurité peuvent afficher, libérer et supprimer tous les types de messages mis en quarantaine pour tous les utilisateurs. Cette fonctionnalité permet aux équipes de sécurité de répondre efficacement lorsqu’un message ou un fichier faux positif est mis en quarantaine.

## <a name="integrate-third-party-reporting-tools-with-defender-for-office-365-user-submission"></a>Intégrer des outils de création de rapports tiers à Defender pour Office 365 soumission d’utilisateurs

Si votre organisation utilise un outil de création de rapports tiers qui permet aux utilisateurs de signaler en interne les e-mails suspects, vous pouvez intégrer l’outil aux fonctionnalités d’envoi d’utilisateurs de Defender pour Office 365. Cette intégration offre les avantages suivants aux équipes de sécurité :

- Intégration aux fonctionnalités AIR de Defender pour Office 365.
- Tri simplifié.
- Réduction du temps d’investigation et de réponse.

Désignez la boîte aux lettres personnalisée dans laquelle les messages signalés par l’utilisateur sont envoyés sur la page **Soumissions de l’utilisateur** dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com/userSubmissionsReportMessage>. Pour plus d’informations, consultez [paramètres de message signalés par l’utilisateur](user-submission.md).

> [!NOTE]
>
> - La boîte aux lettres personnalisée est une boîte aux lettres Exchange Online.
> - L’outil de création de rapports tiers doit inclure le message signalé d’origine en tant que message non compressé. EML ou . Pièce jointe MSG dans le message envoyé à la boîte aux lettres personnalisée (ne vous contentez pas de transférer le message d’origine à la boîte aux lettres personnalisée).
> - La boîte aux lettres personnalisée requiert des prérequis spécifiques pour permettre la remise de messages potentiellement incorrects. Pour plus d’informations, consultez [configuration requise pour la boîte aux lettres des soumissions d’utilisateurs](user-submission.md#configuration-requirements-for-the-user-submissions-mailbox).

Lorsque l’utilisateur a signalé l’arrivée d’e-mails dans la boîte aux lettres personnalisée, Defender pour Office 365 génère automatiquement l’alerte nommée **Email signalée par l’utilisateur comme un programme malveillant ou un hameçonnage**. Cette alerte lance un [playbook AIR](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook). Le playbook effectue une série d’étapes d’investigation automatisée :

- Collectez des données sur l’e-mail spécifié.
- Collectez des données sur les menaces et les entités liées à cet e-mail. Les entités peuvent inclure des fichiers, des URL et des destinataires.
- Fournissez des actions recommandées à l’équipe SecOps en fonction des résultats de l’enquête.

**Email signalés par l’utilisateur comme des alertes de programmes malveillants ou de hameçonnage**, les enquêtes automatisées et leurs actions recommandées sont automatiquement corrélées aux incidents dans Microsoft 365 Defender. Cette corrélation simplifie davantage le processus de triage et de réponse pour les équipes de sécurité. Si plusieurs utilisateurs signalent les mêmes messages ou des messages similaires, tous les utilisateurs et messages sont corrélés dans le même incident.

Les données provenant d’alertes et d’investigations dans Defender pour Office 365 sont automatiquement comparées aux alertes et aux investigations dans les autres produits Microsoft 365 Defender :

- Microsoft Defender pour point de terminaison
- Microsoft Defender for Cloud Apps
- Microsoft Defender pour l’identité

Si une relation est découverte, le système crée un incident qui donne une visibilité pour l’ensemble de l’attaque.
