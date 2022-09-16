---
title: Analyse des menaces dans Microsoft 365 Defender
ms.reviewer: ''
description: Découvrez les menaces émergentes et les techniques d’attaque et comment les arrêter. Évaluez leur impact sur votre organisation et évaluez la résilience de votre organisation.
keywords: analyse des menaces, évaluation des risques, Microsoft 365 Defender, M365D, état d’atténuation, configuration sécurisée, Microsoft Defender pour Office 365, Microsoft Defender pour l’analyse des menaces Office 365, analytique des menaces MDO, données MDE et MDO d’analyse des menaces intégrées, intégration des données d’analyse des menaces, intégration intégrée Microsoft 365 Defender analyse des menaces
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
search.appverid: met150
ms.openlocfilehash: 951fd10307b1ceff61285f2a006845339d9d90d4
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67740019"
---
# <a name="threat-analytics-in-microsoft-365-defender"></a>Analyse des menaces dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

[!INCLUDE [Prerelease](../includes/prerelease.md)]

L’analytique des menaces est notre solution de renseignement sur les menaces dans le produit de la part d’experts en sécurité Microsoft. Il est conçu pour aider les équipes de sécurité à être aussi efficaces que possible face aux menaces émergentes, telles que :

- Acteurs de menaces actifs et leurs campagnes
- Techniques d’attaque populaires et nouvelles
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

Regardez cette courte vidéo pour en savoir plus sur la façon dont l’analytique des menaces peut vous aider à suivre les dernières menaces et à les arrêter.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWwJfU]

Vous pouvez accéder à l’analytique des menaces à partir du côté supérieur gauche de la barre de navigation du portail de sécurité Microsoft 365, ou à partir d’une carte de tableau de bord dédiée qui affiche les principales menaces pour votre organisation, à la fois en termes d’impact et en termes d’exposition.

:::image type="content" source="../../media/threat-analytics/ta_inlandingpage_mtp.png" alt-text="Page d’accueil de l’analyse des menaces" lightbox="../../media/threat-analytics/ta_inlandingpage_mtp.png":::

Les menaces à fort impact ont le plus grand potentiel de causer des dommages, tandis que les menaces à exposition élevée sont celles auxquelles vos ressources sont les plus vulnérables. Obtenir une visibilité sur les campagnes actives ou en cours et savoir quoi faire par le biais de l’analyse des menaces peut aider votre équipe chargée des opérations de sécurité à prendre des décisions éclairées.

_Où accéder à l’analytique des menaces_

Avec des adversaires plus sophistiqués et de nouvelles menaces qui apparaissent fréquemment et de manière répandue, il est essentiel de pouvoir rapidement :

- Identifier et réagir aux menaces émergentes
- Découvrez si vous êtes actuellement attaqué
- Évaluer l’impact de la menace sur vos ressources
- Passer en revue votre résilience ou votre exposition aux menaces
- Identifier les mesures d’atténuation, de récupération ou de prévention que vous pouvez prendre pour arrêter ou contenir les menaces

Chaque rapport fournit une analyse d’une menace suivie et des conseils détaillés sur la façon de se défendre contre cette menace. Il incorpore également des données de votre réseau, indiquant si la menace est active et si des protections applicables sont en place.

## <a name="view-the-threat-analytics-dashboard"></a>Afficher le tableau de bord Analyse des menaces

Le tableau de bord Analyse des menaces ([security.microsoft.com/threatanalytics3](https://security.microsoft.com/threatanalytics3)) met en évidence les rapports les plus pertinents pour votre organisation. Il récapitule les menaces dans les sections suivantes :

- **Menaces** les plus récentes : répertorie les derniers rapports sur les menaces publiés ou mis à jour, ainsi que le nombre d’alertes actives et résolues.
- **Menaces à fort impact** : répertorie les menaces qui ont le plus d’impact sur votre organisation. Cette section répertorie d’abord les menaces avec le plus grand nombre d’alertes actives et résolues.
- **Exposition la plus élevée** : répertorie d’abord les menaces présentant les niveaux d’exposition les plus élevés. Le niveau d’exposition d’une menace est calculé à l’aide de deux informations : la gravité des vulnérabilités associées à la menace et le nombre d’appareils de votre organisation qui peuvent être exploités par ces vulnérabilités.

Sélectionnez une menace dans le tableau de bord pour afficher le rapport correspondant à cette menace.

:::image type="content" source="../../media/threat-analytics/ta_dashboard_mtp.png" alt-text="Tableau de bord Analyse des menaces" lightbox="../../media/threat-analytics/ta_dashboard_mtp.png":::

_Tableau de bord Analyse des menaces. Vous pouvez également sélectionner le champ De recherche à clé dans un mot clé lié au rapport d’analyse des menaces que vous souhaitez lire._

## <a name="view-a-threat-analytics-report"></a>Afficher un rapport d’analyse des menaces

Chaque rapport d’analyse des menaces fournit des informations dans plusieurs sections :

- [**Vue d’ensemble**](#overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses)
- [**Rapport d’analystes**](#analyst-report-get-expert-insight-from-microsoft-security-researchers)
- [**Incidents connexes**](#related-incidents-view-and-manage-related-incidents)
- [**Ressources impactées**](#impacted-assets-get-list-of-impacted-devices-and-mailboxes)
- [**Tentatives d’e-mail empêchées**](#prevented-email-attempts-view-blocked-or-junked-threat-emails)
- [**Atténuations de l’exposition &**](#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices)

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Vue d’ensemble : comprendre rapidement la menace, évaluer son impact et examiner les défenses

La section **Vue d’ensemble** fournit un aperçu du rapport détaillé de l’analyste. Il fournit également des graphiques qui mettent en évidence l’impact de la menace sur votre organisation et votre exposition par le biais d’appareils mal configurés et non corrigés.

:::image type="content" source="../../media/threat-analytics/ta_overview_mtp.png" alt-text="Section Vue d’ensemble d’un rapport d’analyse des menaces" lightbox="../../media/threat-analytics/../../media/threat-analytics/ta_overview_mtp.png":::

_Section Vue d’ensemble d’un rapport d’analyse des menaces_

#### <a name="assess-impact-on-your-organization"></a>Évaluer l’impact sur votre organisation

Chaque rapport comprend des graphiques conçus pour fournir des informations sur l’impact organisationnel d’une menace :

- **Incidents connexes** : fournit une vue d’ensemble de l’impact de la menace suivie sur votre organisation avec les données suivantes :
  - Nombre d’alertes actives et nombre d’incidents actifs auxquels elles sont associées
  - Gravité des incidents actifs
- **Alertes au fil du temps** : indique le nombre d’alertes **actives** et **résolues** associées au fil du temps. Le nombre d’alertes résolues indique la rapidité avec laquelle votre organisation répond aux alertes associées à une menace. Dans l’idéal, le graphique doit afficher les alertes résolues en quelques jours.
- **Ressources affectées** : indique le nombre d’appareils distincts et de comptes de messagerie (boîtes aux lettres) qui ont actuellement au moins une alerte active associée à la menace suivie. Des alertes sont déclenchées pour les boîtes aux lettres qui ont reçu des e-mails de menace. Passez en revue les stratégies au niveau de l’organisation et de l’utilisateur pour les remplacements qui provoquent la remise des e-mails de menace.
- **Tentatives d’e-mail empêchées** : indique le nombre d’e-mails des sept derniers jours qui ont été bloqués avant la remise ou remis au dossier courrier indésirable.

#### <a name="review-security-resilience-and-posture"></a>Passer en revue la résilience et la posture de sécurité

Chaque rapport comprend des graphiques qui fournissent une vue d’ensemble de la résilience de votre organisation face à une menace donnée :

- **État de configuration sécurisé** : indique le nombre d’appareils avec des paramètres de sécurité mal configurés. Appliquez les paramètres de sécurité recommandés pour atténuer la menace. Les appareils sont considérés comme **sécurisés** s’ils ont appliqué _tous les_ paramètres suivis.
- **État de mise à jour corrective des vulnérabilités** : indique le nombre d’appareils vulnérables. Appliquez des mises à jour de sécurité ou des correctifs pour résoudre les vulnérabilités exploitées par la menace.

#### <a name="view-reports-per-threat-tags"></a>Afficher les rapports par balises de menace

Vous pouvez filtrer la liste des rapports sur les menaces et afficher les rapports les plus pertinents en fonction d’une balise de menace spécifique (catégorie) ou d’un type de rapport.

- **Balises de menace** : vous aider à afficher les rapports les plus pertinents en fonction d’une catégorie de menaces spécifique. Par exemple, tous les rapports liés aux ransomwares.
- **Types de** rapports : vous aider à afficher les rapports les plus pertinents en fonction d’un type de rapport spécifique. Par exemple, tous les rapports qui couvrent les outils et les techniques.
- **Filtres** : vous aident à examiner efficacement la liste des rapports sur les menaces et à filtrer la vue en fonction d’une balise de menace ou d’un type de rapport spécifique. Par exemple, passez en revue tous les rapports sur les menaces liés à la catégorie de ransomware ou les rapports de menaces qui couvrent les vulnérabilités.

##### <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

L’équipe Microsoft Threat Intelligence a ajouté des balises de menace à chaque rapport sur les menaces :

- Quatre balises de menace sont désormais disponibles :
  - Rançongiciel
  - Hameçonnage
  - Vulnérabilité
  - Groupe d’activités
- Les balises de menace sont présentées en haut de la page Analyse des menaces. Il existe des compteurs pour le nombre de rapports disponibles sous chaque balise.

  :::image type="content" source="../../media/threat-analytics/ta-threattags-mtp.png" alt-text="Balises de menace" lightbox="../../media/threat-analytics/ta-threattags-mtp.png":::

- La liste peut également être triée par balises de menace :

  :::image type="content" source="../../media/threat-analytics//ta-taglist-mtp.png" alt-text="Section Balises de menace" lightbox="../../media/threat-analytics//ta-taglist-mtp.png":::

- Les filtres sont disponibles par balise de menace et type de rapport :

  :::image type="content" source="../../media/threat-analytics/ta-threattag-filters-mtp.png" alt-text="Page Filtres" lightbox="../../media/threat-analytics/ta-threattag-filters-mtp.png":::

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Rapport d’analyste : Obtenir des insights d’experts auprès des chercheurs en sécurité Microsoft

Dans la section **Rapport de l’analyste** , lisez l’écriture détaillée d’experts. La plupart des rapports fournissent des descriptions détaillées des chaînes d’attaque, notamment des tactiques et des techniques mappées à l’infrastructure MITRE ATT&CK, des listes exhaustives de recommandations et de puissants conseils sur [la chasse aux menaces](advanced-hunting-overview.md) .

[Mer informasjon sur le rapport d’analyste](threat-analytics-analyst-reports.md)

### <a name="related-incidents-view-and-manage-related-incidents"></a>Incidents connexes : afficher et gérer les incidents associés

L’onglet **Incidents connexes** fournit la liste de tous les incidents liés à la menace suivie. Vous pouvez attribuer des incidents ou gérer des alertes liées à chaque incident. 

:::image type="content" source="../../media/threat-analytics/ta_related_incidents_mtp.png" alt-text="Section Incidents connexes d’un rapport d’analyse des menaces" lightbox="../../media/threat-analytics/ta_related_incidents_mtp.png":::

_Section Incidents connexes d’un rapport d’analyse des menaces_

### <a name="impacted-assets-get-list-of-impacted-devices-and-mailboxes"></a>Ressources impactées : obtenir la liste des appareils et boîtes aux lettres impactés

Une ressource est considérée comme affectée si elle est affectée par une alerte active non résolue. **L’onglet Ressources affectées répertorie** les types de ressources impactés suivants :

- **Appareils affectés** : points de terminaison qui ont des alertes Pertahanan Microsoft untuk Titik Akhir non résolues. Ces alertes se déclenchent généralement sur les observations d’indicateurs et d’activités de menace connus.
- **Boîtes aux lettres impactées** : boîtes aux lettres qui ont reçu des messages électroniques qui ont déclenché Microsoft Defender pour Office 365 alertes. Bien que la plupart des messages qui déclenchent des alertes soient généralement bloqués, les stratégies au niveau de l’utilisateur ou de l’organisation peuvent remplacer les filtres.

:::image type="content" source="../../media/threat-analytics/ta_impacted_assets_mtp.png" alt-text="Section Ressources affectées d’un rapport d’analyse des menaces" lightbox="../../media/threat-analytics/ta_impacted_assets_mtp.png":::

_Section Ressources impactées d’un rapport d’analyse des menaces_

### <a name="prevented-email-attempts-view-blocked-or-junked-threat-emails"></a>Tentatives d’e-mail empêchées : afficher les e-mails de menace bloqués ou indésirables

Microsoft Defender pour Office 365 bloque généralement les e-mails avec des indicateurs de menace connus, y compris des liens malveillants ou des pièces jointes. Dans certains cas, les mécanismes de filtrage proactifs qui vérifient le contenu suspect envoient à la place des e-mails de menace au dossier courrier indésirable. Dans les deux cas, les chances que la menace lance du code malveillant sur l’appareil sont réduites.

L’onglet **Tentatives d’e-mail empêchées** répertorie tous les e-mails qui ont été bloqués avant la remise ou envoyés au dossier courrier indésirable par Microsoft Defender pour Office 365.

:::image type="content" source="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png" alt-text="Section Tentatives d’e-mail empêchées d’un rapport d’analyse des menaces" lightbox="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png":::

_Section Tentatives d’e-mail empêchées d’un rapport d’analyse des menaces_

### <a name="exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Exposition et atténuations : passez en revue la liste des atténuations et l’état de vos appareils

Dans la section **Atténuations de l’exposition &** , passez en revue la liste des recommandations actionnables spécifiques qui peuvent vous aider à accroître la résilience de votre organisation face à la menace. La liste des atténuations suivies comprend :

- **Mises à jour de sécurité** : déploiement de mises à jour de sécurité logicielle prises en charge pour les vulnérabilités détectées sur les appareils intégrés
- **Configurations de sécurité prises en charge**
  - Protection fournie par le cloud  
  - Protection des applications potentiellement indésirables (PUA)
  - Protection en temps réel

Les informations d’atténuation contenues dans cette section incorporent des données de [Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt), qui fournissent également des informations détaillées d’exploration à partir de divers liens du rapport.

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp.png" alt-text="Section atténuations d’un rapport d’analyse des menaces montrant les détails de la configuration sécurisée" lightbox="../../media/threat-analytics/ta_mitigations_mtp.png":::

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp2.png" alt-text="Section atténuations d’un rapport d’analyse des menaces montrant les détails de la vulnérabilité" lightbox="../../media/threat-analytics/ta_mitigations_mtp2.png":::

_Section Sur l’exposition & atténuations d’un rapport d’analyse des menaces_

## <a name="set-up-email-notifications-for-report-updates"></a>Configurer des notifications par e-mail pour les mises à jour de rapport

Vous pouvez configurer des notifications par e-mail qui vous envoieront des mises à jour sur les rapports d’analyse des menaces.

Pour configurer des notifications par e-mail pour les rapports d’analyse des menaces, procédez comme suit :

1. Sélectionnez **Paramètres** dans la barre latérale Microsoft 365 Defender. Sélectionnez **Microsoft 365 Defender** dans la liste des paramètres.
 
![Capture d’écran avec « Paramètres » et « Microsoft 365 Defender » mis en évidence en rouge](../../media/threat-analytics/ta_create_notification_0.png)

2. Choisissez **Email notifications Analyse des menaces** > , puis sélectionnez le bouton **+ Créer une règle de notification**. Un menu volant s’affiche.

![Capture d’écran avec « + Créer une règle de notification » en rouge](../../media/threat-analytics/ta_create_notification_1.png)

3. Suivez les étapes répertoriées dans le menu volant. Tout d’abord, donnez un nom à votre nouvelle règle. Le champ de description est facultatif, mais un nom est requis. Vous pouvez activer ou désactiver la règle à l’aide de la case à cocher sous le champ de description.

> [!NOTE]
> Les champs nom et description d’une nouvelle règle de notification acceptent uniquement les lettres et les chiffres en anglais. Ils n’acceptent pas les espaces, les tirets, les traits de soulignement ou toute autre ponctuation.

![Capture d’écran de l’écran d’affectation de noms, avec tous les champs renseignés et la case à cocher « Activer la règle » cochée](../../media/threat-analytics/ta_create_notification_2.png)

4. Choisissez le type de rapport dont vous souhaitez être averti. Vous pouvez choisir entre être mis à jour sur tous les rapports nouvellement publiés ou mis à jour, ou uniquement sur les rapports qui ont une balise ou un type spécifique.

![Capture d’écran de l’écran de notification, avec des balises ransomware sélectionnées et un menu déroulant pour les types ouverts](../../media/threat-analytics/ta_create_notification_3.png)

5. Ajoutez au moins un destinataire pour recevoir les e-mails de notification. Vous pouvez également utiliser cet écran pour vérifier comment les notifications seront reçues, en envoyant un e-mail de test.

![Capture d’écran de l’écran des destinataires. 3 destinataires sont répertoriés et un e-mail de test a été envoyé, comme indiqué par une coche verte](../../media/threat-analytics/ta_create_notification_4.png)

6. Passez en revue votre nouvelle règle. Si vous souhaitez modifier quelque chose, **sélectionnez** le bouton Modifier à la fin de chaque sous-section. Une fois votre révision terminée, sélectionnez le bouton **Créer une règle** .

![Capture d’écran de l’écran de révision. Un bouton d’édition est mis en surbrillance en rouge](../../media/threat-analytics/ta_create_notification_5.png)

7. Félicitations ! Votre nouvelle règle a été créée avec succès. Sélectionnez le bouton **Terminé** pour terminer le processus et fermez le menu volant.

![Capture d’écran de l’écran de création de la règle. Une règle créée avec succès affiche des coches vertes le long de la barre latérale et un grand contrôle vert dans la zone principale de l’écran](../../media/threat-analytics/ta_create_notification_6.png)

8. Votre nouvelle règle s’affiche désormais dans la liste des notifications par e-mail Threat Analytics.

![Capture d’écran de la liste des règles de notification par e-mail dans l’écran Paramètres](../../media/threat-analytics/ta_create_notification_7.png)

## <a name="additional-report-details-and-limitations"></a>Détails et limitations supplémentaires du rapport

> [!NOTE]
> Dans le cadre de l’expérience de sécurité unifiée, l’analytique des menaces est désormais disponible non seulement pour Pertahanan Microsoft untuk Titik Akhir, mais également pour les titulaires de licences Microsoft Defender pour Office E5.
>
> Si vous n’utilisez pas le portail de sécurité Microsoft 365 (Microsoft 365 Defender), vous pouvez également voir les détails du rapport (sans les données Microsoft Defender pour Office) dans le portail Centre de sécurité Microsoft Defender ( Pertahanan Microsoft untuk Titik Akhir).

Pour accéder aux rapports d’analyse des menaces, vous avez besoin de certains rôles et autorisations. Pour plus d’informations, consultez [rôles personnalisés dans le contrôle d’accès en fonction du rôle pour Microsoft 365 Defender](custom-roles.md).

- Pour afficher les alertes, les incidents ou les données de ressources impactées, vous devez disposer d’autorisations sur Microsoft Defender pour Office ou Pertahanan Microsoft untuk Titik Akhir données d’alertes, ou les deux.
- Pour afficher les tentatives d’e-mail empêchées, vous devez disposer d’autorisations sur les données de repérage Microsoft Defender pour Office.
- Pour afficher les atténuations, vous devez disposer d’autorisations sur les données de gestion des vulnérabilités Defender dans Pertahanan Microsoft untuk Titik Akhir.

Lorsque vous examinez les données d’analyse des menaces, n’oubliez pas les facteurs suivants :

- Les graphiques reflètent uniquement les atténuations suivies. Consultez la vue d’ensemble du rapport pour obtenir des atténuations supplémentaires qui ne sont pas affichées dans les graphiques.
- Les atténuations ne garantissent pas une résilience complète. Les atténuations fournies reflètent les meilleures actions possibles nécessaires pour améliorer la résilience.
- Les appareils sont considérés comme « indisponibles » s’ils n’ont pas transmis de données au service.
- Les statistiques relatives aux antivirus sont basées sur les paramètres de l’Antivirus Microsoft Defender. Les appareils avec des solutions antivirus tierces peuvent apparaître comme étant « exposés ».

## <a name="related-articles"></a>Articles connexes

- [Rechercher de manière proactive les menaces avec la chasse avancée](advanced-hunting-overview.md)
- [Comprendre la section rapport de l’analyste](threat-analytics-analyst-reports.md)
- [Évaluer et résoudre les failles de sécurité et les expositions](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
