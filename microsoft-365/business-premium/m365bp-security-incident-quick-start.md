---
title: Un guide des opérations de sécurité pour Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 80bdae57-f8bc-4e40-a58c-956007117ecb
description: 'Ensemble de suggestions sur lesquelles concentrer vos efforts dans le portail Defender lorsqu’il s’agit d’opérations quotidiennes, hebdomadaires ou mensuelles. '
ms.openlocfilehash: e97176eab4d846709fb51dbab0f6d6122e45b7f5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634890"
---
# <a name="microsoft-365-business-premium-security-operations-guide"></a>Guide des opérations de sécurité Microsoft 365 Business Premium

Si vous débutez avec Microsoft 365 Business Premium ou si vous ne disposez pas encore d'un guide des opérations de sécurité, cet article peut servir de point de départ. Si vous disposez déjà d'un guide des opérations de sécurité, lisez-le par rapport aux recommandations de cet article.

Vous pouvez utiliser ces conseils pour prendre des décisions concernant les priorités des incidents de sécurité et les tâches que votre équipe de sécurité effectuera dans le portail Microsoft Defender ([https://security.microsoft.com](https://security.microsoft.com)).

| Fréquence suggérée | Tâches  |
|---------|---------|
| En jours  | [Vérifier votre vulnérabilité aux menaces](#check-your-threat-vulnerability).<br/>[Examiner les actions en attente dans le centre d'action](#review-pending-actions-in-the-action-center).<br/>[Examiner les appareils avec des détections de menaces](#review-devices-with-threat-detections).<br/>[En savoir plus sur les nouveaux incidents ou alertes](#learn-about-new-incidents-or-alerts). |
| En semaines | [Surveiller et améliorer votre score Microsoft Secure](#monitor-and-improve-your-microsoft-secure-score).<br/>[Examiner le score de sécurité des appareils](#review-the-secure-score-for-devices).<br/>[Améliorer votre score de sécurité pour les appareils](#improve-your-secure-score-for-devices). |
| Mensuelle | [Exécuter les rapports](#run-reports).<br/>[Exécuter un didacticiel de simulation](#run-a-simulation-tutorial).<br/>[Explorer le centre d'apprentissage](#explore-the-learning-hub). |
| Selon vos besoins | [Utiliser le tableau de bord d'analyse des menaces](#use-the-threat-analytics-dashboard).<br/>[Exécuter une analyse ou une enquête automatisée](#run-a-scan-or-automated-investigation).<br/>[Corriger un élément](#remediate-an-item). | 

Les sections suivantes fournissent plus de détails sur chaque tâche.
  
## <a name="suggested-daily-tasks"></a>Tâches quotidiennes suggérées

Voici quelques suggestions pour les tâches de sécurité à effectuer quotidiennement.

- [Vérifier votre vulnérabilité aux menaces](#check-your-threat-vulnerability).
- [Examiner les actions en attente dans le centre d'action](#review-pending-actions-in-the-action-center).
- [Examiner les appareils avec des détections de menaces](#review-devices-with-threat-detections).
- [En savoir plus sur les nouveaux incidents ou alertes](#learn-about-new-incidents-or-alerts).

### <a name="check-your-threat-vulnerability"></a>Vérifier votre vulnérabilité aux menaces

En bref, vous pouvez obtenir un instantané de la vulnérabilité de menace en consultant le tableau de bord de gestion des vulnérabilités. Il reflète la vulnérabilité de votre organisation face aux menaces de cybersécurité. Un score d’exposition élevé signifie que vos appareils sont plus vulnérables à l’exploitation.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Gestion des vulnérabilités > Tableau de bord**.

2. Jetez un coup d’œil au score d’exposition de votre organisation. S’il est dans l’acceptable ou » Haut » plage, vous pouvez passer à autre chose. Si ce n'est pas le cas, sélectionnez **Améliorer le score** pour voir plus de détails et des recommandations de sécurité pour améliorer ce score.

Connaître votre score d’exposition vous aide à :

- Comprendre et identifier rapidement les points importants sur l’état de la sécurité dans votre organisation
- Détecter et répondre aux zones qui nécessitent une investigation ou une action pour améliorer l’état actuel
- Communiquer avec les pairs et la direction sur l’impact des efforts de sécurité

### <a name="review-pending-actions-in-the-action-center"></a>Examiner les actions en attente dans le centre d'action

Au fur et à mesure que des menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, les actions de correction peuvent être effectuées automatiquement ou uniquement lors de l’approbation, c’est pourquoi elles doivent être surveillées régulièrement. Les exemples d’actions de correction incluent l’envoi d’un fichier en quarantaine, l’arrêt de l’exécution d’un processus et la suppression d’une tâche planifiée. Toutes les actions de correction sont suivies dans le Centre de notifications.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Centre d'action**.

2. Sélectionnez l’onglet **En attente** pour afficher et approuver (ou rejeter) les actions en attente. Ces actions peuvent provenir d’une protection antivirus ou anti-programme malveillant, d’investigations automatisées, d’activités de réponse manuelles ou de sessions de réponse en direct.

3. Sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées.

### <a name="review-devices-with-threat-detections"></a>Examiner les appareils avec des détections de menaces

Pour savoir si vous avez des appareils qui ont été exposés à des menaces, procédez comme suit.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Rapports > Général > Rapport de sécurité**.

2. Faites défiler jusqu’à la ligne Appareils vulnérables. Si des menaces ont été détectées sur les appareils, vous verrez ces informations dans cette ligne.

### <a name="learn-about-new-incidents-or-alerts"></a>En savoir plus sur les nouveaux incidents ou alertes

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le menu de navigation, sélectionnez **Incidents**. Les incidents sont affichés sur la page avec les alertes associées.

2. Sélectionnez une alerte pour ouvrir son volet volant, où vous pouvez en savoir plus sur l’alerte.

3. Dans le menu volant, vous pouvez voir le titre de l’alerte, afficher une liste des ressources (telles que les points de terminaison ou les comptes d’utilisateur) qui ont été affectées, effectuer des actions disponibles et utiliser des liens pour afficher plus d’informations et même ouvrir la page de détails de l’alerte sélectionnée.

### <a name="run-a-scan-or-automated-investigation"></a>Exécuter une analyse ou une enquête automatisée

1. Dans le portail Microsoft 365 Defender (https://security.microsoft.com), dans le volet de navigation, choisissez Inventaire de l’appareil.

2. Sélectionnez un appareil pour ouvrir son panneau volant et passez en revue les informations affichées.

3. Sélectionnez les points de suspension (...) pour ouvrir le menu Actions.

4. Sélectionnez une action, telle que **Exécuter l’analyse antivirus** ou **Lancer une investigation automatisée**.

## <a name="suggested-weekly-tasks"></a>Tâches hebdomadaires suggérées

Voici quelques suggestions de tâches de sécurité importantes à effectuer au moins une fois par semaine.

- [Surveiller et améliorer votre score Microsoft Secure](#monitor-and-improve-your-microsoft-secure-score).
- [Examiner le score de sécurité des appareils](#review-the-secure-score-for-devices).
- [Améliorer votre score de sécurité pour les appareils](#improve-your-secure-score-for-devices).

### <a name="monitor-and-improve-your-microsoft-secure-score"></a>Surveiller et améliorez votre score Microsoft Secure

Le niveau de sécurité Microsoft est une mesure de la posture de sécurité d’une organisation, avec un nombre plus élevé indiquant que moins d’actions d’amélioration sont nécessaires.

Le degré de sécurisation aide les organisations :

- Rapport sur l'état actuel de la posture de sécurité de l'organisation.
- Améliorer leur posture de sécurité en leur offrant des possibilités de découverte, de visibilité, de guide et de contrôle.
- Comparer avec des critères de référence et établir des indicateurs de performance clés (KPI).

1. Pour vérifier votre score de sécurité, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Score de sécurité**. 

2. Examiner et prendre des décisions concernant les corrections et les actions afin d'améliorer votre score global de sécurité Microsoft.

### <a name="review-the-secure-score-for-devices"></a>Passer en revue le degré de sécurisation des appareils

Le tableau de bord de gestion des vulnérabilités se trouve également dans la carte Score de sécurité Microsoft pour les appareils. Cette carte affiche votre score actuel et un score plus élevé indique que vos points de terminaison sont plus résilients aux cyberattaques. Il reflète l’état de sécurité de tous les appareils, collectivement.

Les données de cette carte sont le produit d’un processus de découverte des vulnérabilités en cours et en cours. Il est agrégé avec des évaluations de découverte de configuration qui s’appliquent en permanence :

- Comparer les configurations collectées aux tests d’évaluation collectés pour découvrir les ressources mal configurées
- Mapper les configurations aux vulnérabilités qui peuvent être corrigées ou partiellement corrigées (réduction des risques)
- Collecter et tenir à jour les benchmarks de configuration des meilleures pratiques (fournisseurs, flux de sécurité, équipes de recherche internes)
- Collecter et surveiller les modifications de l’état de configuration du contrôle de sécurité à partir de toutes les ressources

### <a name="improve-your-secure-score-for-devices"></a>Améliorer votre degré de sécurisation pour les appareils

Améliorez votre configuration de sécurité en corrigeant les problèmes à l’aide de la liste des recommandations de sécurité. Dans ce cas, votre degré de sécurisation Microsoft pour les appareils s’améliore et votre organisation devient plus résiliente contre les menaces et vulnérabilités de cybersécurité à l’avenir. Cela vaut toujours la peine de passer en revue et d’améliorer votre score.

1. Pour vérifier votre score de sécurité, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Niveau de sécurité**.

2. Dans la carte **Microsoft Secure Score for Devices** du tableau de bord Defender Vulnerability Management, sélectionnez l'une des catégories. Une liste de recommandations relatives à cette catégorie s’affiche, ainsi que des recommandations.

3. Sélectionnez un élément dans la liste pour afficher les détails liés à la recommandation.

4. Sélectionnez **options de correction**.

5. Lisez la description pour comprendre le contexte du problème et ce qu’il faut faire ensuite. Choisissez une date d’échéance, ajoutez des notes, puis sélectionnez Exporter toutes les données d’activité de correction vers CSV afin de pouvoir les joindre à un e-mail pour le suivi. Un message de confirmation vous indique que la tâche de correction a été créée.

6. Envoyez un e-mail de suivi à votre administrateur informatique et laissez le temps que vous avez alloué à la propagation de la correction dans le système.

7. Revenez à la carte Score de sécurité Microsoft pour les appareils sur le tableau de bord. Le nombre de recommandations de contrôles de sécurité a diminué suite à vos actions.

8. Sélectionnez **Contrôles de sécurité** pour revenir à la page Recommandations de sécurité. L'élément que vous avez abordé n'y est plus répertorié, ce qui entraîne une amélioration de votre score de sécurité Microsoft.

## <a name="suggested-monthly-tasks"></a>Tâches mensuelles suggérées

Ces tâches doivent être effectuées au moins une fois par mois, sinon plus souvent. 

- [Exécuter les rapports](#run-reports).
- [Exécuter un didacticiel de simulation](#run-a-simulation-tutorial).
- [Explorer le centre d'apprentissage](#explore-the-learning-hub).

### <a name="run-reports"></a>Exécuter des rapports

Plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Rapports**.

2. Choisissez un rapport à examiner. Chaque rapport affiche de nombreuses catégories pertinentes pour ce rapport.

3. Sélectionnez **Afficher les détails** pour afficher des informations plus détaillées sur chaque catégorie.

4. Sélectionnez le titre d’une menace particulière pour afficher les détails qui lui sont propres.

### <a name="run-a-simulation-tutorial"></a>Exécuter un didacticiel de simulation

Il est toujours judicieux d’augmenter la préparation à la sécurité pour vous et votre équipe par le biais de la formation. Vous pouvez accéder à des didacticiels de simulation dans le portail Microsoft 365 Defender. Les didacticiels couvrent plusieurs types de cybermenaces. 

Pour commencer :

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Tutoriels**.

2. Lisez la procédure pas à pas d’un didacticiel qui vous intéresse, puis téléchargez le fichier ou copiez le script nécessaire pour exécuter la simulation conformément aux instructions.

### <a name="explore-the-learning-hub"></a>Explorer le hub d’apprentissage

Il existe de nombreux domaines dans le centre d'apprentissage grâce auxquels vous pouvez approfondir vos connaissances sur de nombreuses menaces qui existent et sur la manière de les traiter. Nous vous recommandons, à vous et à vos équipes, de passer du temps à explorer les ressources proposées, en particulier dans les sections Microsoft 365 Defender et Endpoints.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Learning hub**.

2. Sélectionnez une zone, telle que **Microsoft 365 Defender** ou **Endpoints**.

3. Sélectionnez un élément pour en savoir plus sur chaque concept. 

> [!NOTE]
> Certaines ressources du hub d'apprentissage peuvent couvrir des fonctionnalités qui ne sont pas réellement incluses dans Microsoft 365 Business Premium. Par exemple, les fonctionnalités de recherche avancées sont incluses dans les abonnements d'entreprise, tels que Defender pour Endpoint Plan 2 ou Microsoft 365 Defender, mais pas dans Microsoft 365 Business Premium. [Comparez les fonctionnalités de sécurité dans les plans de Microsoft 365 pour les petites et moyennes entreprises](../security/defender-business/compare-mdb-m365-plans.md).

## <a name="as-needed"></a>Selon vos besoins

Effectuez ces tâches au besoin ou selon le cas :

- [Utiliser le tableau de bord d'analyse des menaces](#use-the-threat-analytics-dashboard).
- [Exécuter une analyse ou une enquête automatisée](#run-a-scan-or-automated-investigation).
- [Corriger un élément](#remediate-an-item).

### <a name="use-the-threat-analytics-dashboard"></a>Utiliser le tableau de bord Analyse des menaces

Utilisez le tableau de bord Analyse des menaces pour obtenir une vue d’ensemble du paysage actuel des menaces en mettant en évidence les rapports les plus pertinents pour votre organisation. 

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, sélectionnez **Analyse des menaces** pour afficher le tableau de bord Analyse des menaces. 

   Le tableau de bord récapitule les menaces dans les sections suivantes :

   - Les dernières menaces—répertorient les rapports de menaces les plus récemment publiés ou mis à jour, ainsi que le nombre d’alertes actives et résolues.
   - Menaces à fort impact—répertorie les menaces qui ont le plus d’impact sur votre organisation. Cette section répertorie d’abord les menaces avec le plus grand nombre d’alertes actives et résolues.
   - Exposition la plus élevée—répertorie d’abord les menaces avec les niveaux d’exposition les plus élevés. Le niveau d’exposition d’une menace est calculé à l’aide de deux informations : la gravité des vulnérabilités associées à la menace et le nombre d’appareils de votre organisation qui pourraient être exploités par ces vulnérabilités.

2. Sélectionnez le titre de celui que vous souhaitez étudier et lisez le rapport associé. 

3. Vous pouvez également consulter le rapport complet de l'analyste pour plus de détails ou sélectionner d'autres rubriques pour afficher les incidents associés, les actifs concernés, ainsi que l'exposition et les mesures d'atténuation.

### <a name="remediate-an-item"></a>Corriger un élément

Microsoft 365 Business Premium inclut plusieurs actions de correction. Ces actions incluent des actions de réponse manuelles, des actions qui suivent une investigation automatisée et des actions de réponse dynamique.

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), dans le volet de navigation, choisissez **Inventaire des appareils**.

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory.png" alt-text="Capture d'écran de l'inventaire des appareils":::

2. Sélectionnez un appareil, tel qu'un appareil présentant un niveau de risque ou d'exposition élevé. Un volet déroulant s'ouvre et affiche plus d'informations sur les alertes et les incidents générés pour cet élément, comme illustré dans l'image suivante :  

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Capture d'écran du volet déroulant pour un appareil sélectionné":::

3. Sur le menu déroulant, affichez les informations affichées. Sélectionnez les points de suspension (...) pour ouvrir un menu qui répertorie les actions disponibles, comme illustré dans l'image suivante : 

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Capture d'écran des actions disponibles pour un appareil sélectionné":::

4. Sélectionnez une action disponible. Par exemple, vous pouvez choisir **Exécuter une analyse antivirus**, ce qui entraînera le lancement d'une analyse rapide de l'antivirus Microsoft Defender sur l'appareil. Vous pouvez également sélectionner **Lancer une enquête automatisée** pour déclencher une enquête automatisée sur l'appareil.

#### <a name="remediation-actions-in-microsoft-365-business-premium"></a>Actions correctives dans Microsoft 365 Business Premium

Le tableau suivant récapitule les actions de correction disponibles dans Microsoft 365 Business Premium :

| Source  | Actions  |
|---------|---------|
| Enquêtes automatisées      | - Mettre en quarantaine un fichier <br/>- Supprimer une clé de Registre <br/>- Tuer un processus <br/>- Arrêter un service <br/>- Désactiver un pilote <br/>- Supprimer une tâche planifiée        |
| Actions de réponse manuelle   | - Exécuter une analyse antivirus <br/>- Isoler l’appareil <br/>- Arrêter et mettre en quarantaine <br/>- Ajoutez des indicateurs pour bloquer ou autoriser un fichier.       |
| Réponse en direct  | - Collecter des données légales <br/>- Analyser un fichier <br/>- Exécuter un script <br/>- Envoyer une entité suspecte à Microsoft pour analyse <br/>- Corriger un fichier <br/>- Repérage proactif des menaces  |




## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)