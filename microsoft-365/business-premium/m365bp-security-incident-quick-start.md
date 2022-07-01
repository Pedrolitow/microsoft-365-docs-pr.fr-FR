---
title: Guide des opérations d’incident de sécurité
f1.keywords:
- NOCSH
ms.author: v-kcirillo
author: cirilk
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
ms.openlocfilehash: 5ab0d8ec21ffeac7f8b68a5169641bb9191d3438
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574328"
---
# <a name="microsoft-365-business-premium-security-operations-guide"></a>Guide des opérations de sécurité Microsoft 365 Business Premium

Les conseils suivants constituent un point de départ pour vous aider à prendre des décisions sur les priorités des incidents de sécurité dans le portail Microsoft Defender.
  
## <a name="suggested-daily-tasks"></a>Tâches quotidiennes suggérées

Voici quelques suggestions pour les tâches de sécurité à effectuer quotidiennement.

### <a name="review-for-devices-with-threat-detections"></a>Examiner les appareils avec détections de menaces

Pour savoir si vous avez des appareils qui ont été exposés à des menaces, procédez comme suit.

1. Accédez au portail Microsoft 365 Defender (https://security.microsoft.com) et connectez-vous.

1. Dans le volet de navigation, choisissez **Rapports > Général > Sécurité**.

1. Faites défiler jusqu’à la ligne Appareils vulnérables. Si des menaces ont été détectées sur les appareils, vous verrez ces informations dans cette ligne.

### <a name="new-incidents-or-alerts"></a>Nouveaux incidents ou alertes

1. Accédez au portail Microsoft 365 Defender (https://security.microsoft.com) et connectez-vous.

1. Dans le menu Navigation, sélectionnez **Incidents**. Les incidents sont affichés sur la page avec les alertes associées.

1. Sélectionnez une alerte pour ouvrir son volet volant, où vous pouvez en savoir plus sur l’alerte.

1. Dans le menu volant, vous pouvez voir le titre de l’alerte, afficher une liste des ressources (telles que les points de terminaison ou les comptes d’utilisateur) qui ont été affectées, effectuer des actions disponibles et utiliser des liens pour afficher plus d’informations et même ouvrir la page de détails de l’alerte sélectionnée.

### <a name="run-a-scan-or-investigation"></a>Exécuter une analyse ou une investigation

1. Dans le portail Microsoft 365 Defender (https://security.microsoft.com), dans le volet de navigation, choisissez Inventaire de l’appareil.

1. Sélectionnez un appareil pour ouvrir son panneau volant et passez en revue les informations affichées.

1. Sélectionnez les points de suspension (...) pour ouvrir le menu Actions.

1. Sélectionnez une action, telle que **Exécuter l’analyse antivirus** ou **Lancer une investigation automatisée**.

## <a name="suggested-weekly-tasks"></a>Tâches hebdomadaires suggérées

Voici quelques suggestions de tâches de sécurité importantes à effectuer au moins une fois par semaine.

### <a name="monitor-and-respond-to-your-microsoft-secure-score"></a>Surveiller et répondre à votre degré de sécurisation Microsoft

Le niveau de sécurité Microsoft est une mesure de la posture de sécurité d’une organisation, avec un nombre plus élevé indiquant que moins d’actions d’amélioration sont nécessaires.

Le degré de sécurisation aide les organisations :

- Rapport sur l'état actuel de la posture de sécurité de l'organisation.
- Améliorer leur posture de sécurité en leur offrant des possibilités de découverte, de visibilité, de guide et de contrôle.
- Comparer avec des critères de référence et établir des indicateurs de performance clés (KPI).

Pour vérifier votre degré de sécurisation, dans le volet de navigation, choisissez **Degré de sécurisation**. Passez en revue et prenez des décisions concernant les corrections et les actions afin d’améliorer votre degré de sécurisation Microsoft global.

### <a name="look-at-threat-vulnerability"></a>Examiner la vulnérabilité de menace

En bref, vous pouvez obtenir un instantané de la vulnérabilité de menace en consultant le tableau de bord de gestion des vulnérabilités. Il reflète la vulnérabilité de votre organisation face aux menaces de cybersécurité. Un score d’exposition élevé signifie que vos appareils sont plus vulnérables à l’exploitation.

1. Dans le volet de navigation, sélectionnez **Gestion des vulnérabilités > Tableau de bord**.

1. Jetez un coup d’œil au score d’exposition de votre organisation. S’il est dans l’acceptable ou » Haut » plage, vous pouvez passer à autre chose. Si ce n’est pas le cas, cliquez sur **Améliorer le score** pour afficher des détails supplémentaires et des recommandations de sécurité pour améliorer ce score.

Connaître votre score d’exposition vous aide à :

- Comprendre et identifier rapidement les points importants sur l’état de la sécurité dans votre organisation
- Détecter et répondre aux zones qui nécessitent une investigation ou une action pour améliorer l’état actuel
- Communiquer avec les pairs et la direction sur l’impact des efforts de sécurité

### <a name="review-the-secure-score-for-devices"></a>Passer en revue le degré de sécurisation des appareils

Le tableau de bord de gestion des vulnérabilités se trouve également dans la carte Score de sécurité Microsoft pour les appareils. Cette carte affiche votre score actuel et un score plus élevé indique que vos points de terminaison sont plus résilients aux cyberattaques. Il reflète l’état de sécurité de tous les appareils, collectivement.

Les données de cette carte sont le produit d’un processus de découverte des vulnérabilités en cours et en cours. Il est agrégé avec des évaluations de découverte de configuration qui s’appliquent en permanence :

- Comparer les configurations collectées aux tests d’évaluation collectés pour découvrir les ressources mal configurées
- Mapper les configurations aux vulnérabilités qui peuvent être corrigées ou partiellement corrigées (réduction des risques)
- Collecter et tenir à jour les benchmarks de configuration des meilleures pratiques (fournisseurs, flux de sécurité, équipes de recherche internes)
- Collecter et surveiller les modifications de l’état de configuration du contrôle de sécurité à partir de toutes les ressources

### <a name="improve-your-secure-score-for-devices"></a>Améliorer votre degré de sécurisation pour les appareils

Améliorez votre configuration de sécurité en corrigeant les problèmes à l’aide de la liste des recommandations de sécurité. Dans ce cas, votre degré de sécurisation Microsoft pour les appareils s’améliore et votre organisation devient plus résiliente contre les menaces et vulnérabilités de cybersécurité à l’avenir. Cela vaut toujours la peine de passer en revue et d’améliorer votre score.

1. Pour vérifier votre degré de sécurisation, dans le volet de navigation, sélectionnez **Degré de sécurisation**.

1. Dans la carte Degré de sécurisation Microsoft pour les appareils du tableau de bord Gestion des vulnérabilités Defender, sélectionnez l’une des catégories. Une liste de recommandations relatives à cette catégorie s’affiche, ainsi que des recommandations.

1. Sélectionnez un élément dans la liste pour afficher les détails liés à la recommandation.

1. Sélectionnez **options de correction**.

1. Lisez la description pour comprendre le contexte du problème et ce qu’il faut faire ensuite. Choisissez une date d’échéance, ajoutez des notes, puis sélectionnez Exporter toutes les données d’activité de correction vers CSV afin de pouvoir les joindre à un e-mail pour le suivi. Un message de confirmation vous indique que la tâche de correction a été créée.

1. Envoyez un e-mail de suivi à votre administrateur informatique et laissez le temps que vous avez alloué à la propagation de la correction dans le système.

1. Revenez à la carte Score de sécurité Microsoft pour les appareils sur le tableau de bord. Le nombre de recommandations de contrôles de sécurité a diminué suite à vos actions.

1. Sélectionnez **Contrôles de sécurité** pour revenir à la page Recommandations de sécurité. L’élément que vous avez traité n’y figure plus, ce qui améliore votre degré de sécurisation Microsoft.

## <a name="suggested-monthly-tasks"></a>Tâches mensuelles suggérées

Il s’agit de tâches que vous devez effectuer mensuellement, si ce n’est plus souvent. 

### <a name="use-the-threat-analytics-dashboard"></a>Utiliser le tableau de bord Analyse des menaces

Utilisez le tableau de bord Analyse des menaces pour obtenir une vue d’ensemble du paysage actuel des menaces en mettant en évidence les rapports les plus pertinents pour votre organisation. 

Sélectionnez **Analyse des menaces** dans le volet de navigation pour afficher le tableau de bord Analyse des menaces. Le tableau de bord récapitule les menaces dans les sections suivantes :

- Les dernières menaces—répertorient les rapports de menaces les plus récemment publiés ou mis à jour, ainsi que le nombre d’alertes actives et résolues.
- Menaces à fort impact—répertorie les menaces qui ont le plus d’impact sur votre organisation. Cette section répertorie d’abord les menaces avec le plus grand nombre d’alertes actives et résolues.
- Exposition la plus élevée—répertorie d’abord les menaces avec les niveaux d’exposition les plus élevés. Le niveau d’exposition d’une menace est calculé à l’aide de deux informations : la gravité des vulnérabilités associées à la menace et le nombre d’appareils de votre organisation qui pourraient être exploités par ces vulnérabilités.

Cliquez sur le titre de celui que vous souhaitez examiner, puis lisez le rapport associé. Vous pouvez également consulter le rapport d’analyse complet pour plus de détails, ou sélectionner d’autres titres pour afficher les incidents connexes, les ressources impactées, ainsi que l’exposition et les atténuations.

### <a name="review-pending-items-in-action-center"></a>Examiner les éléments en attente dans le Centre de notifications

Au fur et à mesure que des menaces sont détectées, des actions de correction entrent en jeu. En fonction de la menace particulière et de la façon dont vos paramètres de sécurité sont configurés, les actions de correction peuvent être effectuées automatiquement ou uniquement lors de l’approbation, c’est pourquoi elles doivent être surveillées régulièrement. Les exemples d’actions de correction incluent l’envoi d’un fichier en quarantaine, l’arrêt de l’exécution d’un processus et la suppression d’une tâche planifiée. Toutes les actions de correction sont suivies dans le Centre de notifications.

1. Dans le volet de navigation, choisissez **Centre de notifications**.

2. Sélectionnez l’onglet **En attente** pour afficher et approuver (ou rejeter) les actions en attente. Ces actions peuvent provenir d’une protection antivirus ou anti-programme malveillant, d’investigations automatisées, d’activités de réponse manuelles ou de sessions de réponse en direct.

3. Sélectionnez l’onglet **Historique** pour afficher la liste des actions terminées.

### <a name="remediate-an-item"></a>Corriger un élément

Microsoft Defender entreprise inclut plusieurs actions de correction. Ces actions incluent des actions de réponse manuelles, des actions qui suivent une investigation automatisée et des actions de réponse dynamique.

### <a name="run-reports"></a>Exécuter des rapports

Plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender.

1. Sélectionnez **Rapports** dans le volet de navigation.

2. Choisissez un rapport à examiner. Chaque rapport affiche un certain nombre de catégories pertinentes pour ce rapport.

3. Cliquez sur **Afficher les détails** pour afficher des informations plus détaillées pour chaque catégorie.

4. Sélectionnez le titre d’une menace particulière pour afficher les détails qui lui sont propres.

### <a name="run-a-simulation-tutorial"></a>Exécuter un didacticiel de simulation

Il est toujours judicieux d’augmenter la préparation à la sécurité pour vous et votre équipe par le biais de la formation. Inclus dans le menu de navigation de Defender, il existe des didacticiels couvrant plusieurs types de cyber menaces. 

Pour commencer :

1. Choisissez **Didacticiels** dans le volet de navigation.

2. Lisez la procédure pas à pas d’un didacticiel qui vous intéresse, puis téléchargez le fichier ou copiez le script nécessaire pour exécuter la simulation conformément aux instructions.

### <a name="explore-the-learning-hub"></a>Explorer le hub d’apprentissage

Il existe un certain nombre de domaines dans le Hub d’apprentissage par le biais desquels vous pouvez améliorer votre connaissance de la plupart des menaces qui existent et de la façon de les résoudre. Nous vous recommandons, vous et vos équipes, de consacrer beaucoup de temps à l’exploration des sujets proposés, en particulier dans les sections Microsoft 365 Defender et points de terminaison.

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)