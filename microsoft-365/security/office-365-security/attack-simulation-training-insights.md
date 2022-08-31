---
title: Insights et rapports Exercice de simulation d'attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Les administrateurs peuvent découvrir comment Exercice de simulation d'attaque dans le portail Microsoft 365 Defender affecte les utilisateurs et peuvent obtenir des insights à partir des résultats de simulation et de formation.
ms.subservice: mdo
ms.openlocfilehash: af3a1e9f7a2b991b7ece6f36595e2f7759eccb9d
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483121"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Insights et rapports pour Exercice de simulation d'attaque dans Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans Exercice de simulation d'attaque dans Microsoft Defender pour Office Plan 2 ou Microsoft 365 E5, Microsoft fournit des insights et des rapports à partir des résultats des simulations et des formations correspondantes. Ces informations vous tiennent informés de la progression de la préparation aux menaces de vos utilisateurs, ainsi que des étapes suivantes recommandées pour mieux préparer vos utilisateurs aux attaques futures.

Les insights et les rapports sont disponibles aux emplacements suivants dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender :

- Onglet **Vue d’ensemble** .
- Détails de la simulation sous l’onglet **Simulations** .

Le reste de cet article décrit les informations disponibles.

Pour obtenir des informations de prise en main sur Exercice de simulation d'attaque, consultez [Prise en main de Exercice de simulation d'attaque](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Insights et rapports sous l’onglet Vue d’ensemble de Exercice de simulation d'attaque

Pour accéder à l’onglet **Vue d’ensemble**, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse **Email &** \> **collaboration Exercice de simulation d'attaque** et vérifiez que l’onglet **Vue d’ensemble** est sélectionné (il s’agit de la valeur par défaut). Pour accéder directement à l’onglet **Vue d’ensemble** de la page **Exercice de simulation d'attaque**, utilisez <https://security.microsoft.com/attacksimulator?viewid=overview>.

Le reste de cette section décrit les informations disponibles sous l’onglet **Vue d’ensemble** de Exercice de simulation d'attaque.

### <a name="recent-simulations-card"></a>Carte simulations récentes

La carte **Simulations récentes** de l’onglet **Vue d’ensemble** affiche les trois dernières simulations que vous avez créées ou exécutées dans votre organisation.

Vous pouvez sélectionner une simulation pour afficher les détails.

Si vous sélectionnez **Afficher toutes les simulations** , vous accédez à l’onglet **Simulations** .

La sélection de **Lancer une simulation** démarre l’Assistant création de simulation. Pour plus d’informations, consultez [Simuler une attaque par hameçonnage dans Defender pour Office 365](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recent-simulations-card.png" alt-text="Carte Simulations récentes sous l’onglet Vue d’ensemble dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-recent-simulations-card.png":::

### <a name="behavior-impact-on-compromise-rate-card"></a>Impact du comportement sur la carte de taux de compromission

**L’impact du comportement sur la carte de taux de compromission** sous l’onglet **Vue d’ensemble** montre comment vos utilisateurs ont répondu à vos simulations par rapport aux données historiques dans Microsoft 365. Vous pouvez utiliser ces insights pour suivre la progression de la préparation des utilisateurs aux menaces en exécutant plusieurs simulations sur les mêmes groupes d’utilisateurs.

Les données du graphique elle-même affichent les informations suivantes :

- Taux <sup>\*</sup>**de compromission prédit** : taux de compromission moyen pour les simulations Exercice de simulation d'attaque qui utilisent le même type de charge utile dans toutes les autres organisations Microsoft 365.
- Taux de <sup>\*</sup>**compromission réel** : pourcentage réel d’utilisateurs qui ont diminué pour la simulation.

Si vous pointez sur un point de données dans le graphique, les valeurs de pourcentage réelles sont affichées.

Les informations récapitulatives suivantes sont également affichées sur la carte :

- **les utilisateurs moins sensibles au hameçonnage** : différence entre le nombre réel d’utilisateurs compromis par l’attaque simulée et le taux de compromission prédit. Ce nombre d’utilisateurs est moins susceptible d’être compromis par des attaques similaires à l’avenir.
- **x % de mieux que le taux prédit** : indique comment les utilisateurs ont fait globalement, contrairement au taux de compromission prédit.

:::image type="content" source="../../media/attack-sim-training-overview-behavior-impact-card.png" alt-text="Impact du comportement sur la carte de taux de compromission sous l’onglet Vue d’ensemble dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-behavior-impact-card.png":::

Pour afficher un rapport plus détaillé, cliquez sur **Afficher les simulations et le rapport d’efficacité de l’entraînement**. Ce rapport est expliqué [plus loin dans cet article](#training-efficacy-tab-for-the-attack-simulation-report).

### <a name="simulation-coverage-card"></a>Carte de couverture de simulation

La carte **de couverture simulation** de l’onglet **Vue d’ensemble** affiche le pourcentage d’utilisateurs de votre organisation qui ont reçu une simulation (**utilisateurs simulés**) par rapport à ceux qui n’ont pas reçu de simulation (**utilisateurs non simulés**). Vous pouvez pointer sur une section du graphique pour voir le nombre réel d’utilisateurs dans chaque catégorie.

La sélection de la **simulation de lancement pour les utilisateurs non simulés** démarre l’Assistant création de simulation où les utilisateurs qui n’ont pas reçu la simulation sont automatiquement sélectionnés sur la page **utilisateur cible** . Pour plus d’informations, consultez [Simuler une attaque par hameçonnage dans Defender pour Office 365](attack-simulation-training.md).

Si vous sélectionnez **Afficher le rapport de couverture de simulation** , vous accédez à [l’onglet Couverture utilisateur du rapport de simulation d’attaque](#user-coverage-tab-for-the-attack-simulation-report).

:::image type="content" source="../../media/attack-sim-training-overview-sim-coverage-card.png" alt-text="Carte de couverture simulation sous l’onglet Vue d’ensemble dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-sim-coverage-card.png":::

### <a name="training-completion-card"></a>Carte d’achèvement de la formation

La carte **d’achèvement** de la formation sous l’onglet **Vue d’ensemble** organise les pourcentages d’utilisateurs ayant reçu des formations en fonction des résultats des simulations dans les catégories suivantes :

- **Terminée**
- **En cours**
- **Incomplète**

Vous pouvez pointer sur une section du graphique pour voir le nombre réel d’utilisateurs dans chaque catégorie.

La sélection du **rapport d’achèvement de la formation d’affichage** vous permet d’accéder à l’onglet [Achèvement de l’apprentissage pour le rapport de simulation d’attaque](#training-completion-tab-for-the-attack-simulation-report).

### <a name="repeat-offenders-card"></a>Carte des récidivistes

La carte **Récidivistes** de l’onglet **Vue d’ensemble** affiche les informations sur les récidivistes. Un _récidiviste_ est un utilisateur qui a été compromis par des simulations consécutives. Le nombre par défaut de simulations consécutives est de deux, mais vous pouvez modifier la valeur sous l’onglet **Paramètres** de Exercice de simulation d'attaque à <https://security.microsoft.com/attacksimulator?viewid=setting>.

Le graphique organise les données des récidivistes par [type de simulation](attack-simulation-training.md#select-a-social-engineering-technique) :

- **All**
- **Pièce jointe de programme malveillant**
- **Lien vers un programme malveillant**
- **Collecte des informations d’identification**
- **Lien dans les pièces jointes**
- **Drive-by URL**

Si vous sélectionnez Afficher le rapport sur les **récidivistes** , vous [accédez à l’onglet Récidifs pour le rapport de simulation d’attaque](#repeat-offenders-tab-for-the-attack-simulation-report).

### <a name="recommendations-card"></a>Carte recommandations

La carte **Recommandations** de l’onglet **Vue d’ensemble** suggère différents types de simulations à exécuter.

La sélection **de Lancer démarre maintenant** l’Assistant création de simulation avec le type de simulation spécifié automatiquement sélectionné sur la page **Sélectionner la technique** . Pour plus d’informations, consultez [Simuler une attaque par hameçonnage dans Defender pour Office 365](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recommendations-card.png" alt-text="Carte Recommandations sous l’onglet Vue d’ensemble dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-overview-recommendations-card.png":::

### <a name="attack-simulation-report"></a>Rapport de simulation d’attaque

Vous pouvez ouvrir le **rapport de simulation d’attaque** à partir de l’onglet **Vue d’ensemble** en cliquant sur l’affichage **...** boutons de rapport disponibles dans la plupart des cartes décrites dans cet article. Pour accéder directement au rapport, utilisez <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Onglet Efficacité de l’entraînement pour le rapport de simulation d’attaque

Dans la page **rapport de simulation d’attaque** , l’onglet **Efficacité de l’entraînement** est sélectionné par défaut. Cet onglet fournit les mêmes informations que celles disponibles dans **l’impact du comportement sur la carte de taux de compromission** , avec un contexte supplémentaire de la simulation elle-même.

:::image type="content" source="../../media/attack-sim-report-training-efficacy-view.png" alt-text="Onglet Efficacité de l’entraînement dans le rapport de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-efficacy-view.png":::

Le graphique montre le **taux de compromission prédit** et le **taux réel compromis**. Si vous pointez sur une section du graphique, les valeurs de pourcentage réelles sont affichées.

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Nom de la simulation**
- **Technique de simulation**
- **Tactiques de simulation**
- **Taux compromis prédit**
- **Taux réel compromis**
- **Nombre total d’utilisateurs ciblés**
- **Nombre d’utilisateurs cliqués**

Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible.

Cliquez sur **Personnaliser les colonnes** pour supprimer les colonnes affichées. Lorsque vous avez terminé, cliquez sur **Appliquer**.

Utilisez ![la zone **de recherche** d’icône](../../media/m365-cc-sc-search-icon.png) de recherche pour filtrer les résultats par **nom de simulation** ou **technique de simulation**. Les caractères génériques ne sont pas pris en charge.

Si vous cliquez sur l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Bouton Exporter le rapport** , la progression de génération du rapport s’affiche sous la forme d’un pourcentage d’achèvement. Dans la boîte de dialogue qui s’ouvre, vous pouvez choisir d’ouvrir le fichier .csv, d’enregistrer le fichier .csv et de mémoriser la sélection.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Onglet Couverture utilisateur pour le rapport de simulation d’attaque

:::image type="content" source="../../media/attack-sim-report-user-coverage-view.png" alt-text="Onglet Couverture utilisateur dans le rapport de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-report-user-coverage-view.png":::

Sous **l’onglet Couverture utilisateur** , le graphique affiche les **utilisateurs simulés** et **les utilisateurs non simulés**. Si vous pointez sur un point de données dans le graphique, les valeurs réelles sont affichées.

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Username**
- **Adresse de messagerie**
- **Inclus dans la simulation**
- **Date de la dernière simulation**
- **Résultat de la dernière simulation**
- **Nombre de clics**
- **Nombre de compromis**

Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible.

Cliquez sur **Personnaliser les colonnes** pour supprimer les colonnes affichées. Lorsque vous avez terminé, cliquez sur **Appliquer**.

Utilisez ![la zone **de recherche** d’icône](../../media/m365-cc-sc-search-icon.png) de recherche pour filtrer les résultats par **nom d’utilisateur** ou **adresse Email**. Les caractères génériques ne sont pas pris en charge.

Si vous cliquez sur l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Bouton Exporter le rapport** , la progression de génération du rapport s’affiche sous la forme d’un pourcentage d’achèvement. Dans la boîte de dialogue qui s’ouvre, vous pouvez choisir d’ouvrir le fichier .csv, d’enregistrer le fichier .csv et de mémoriser la sélection.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Onglet Achèvement de l’entraînement pour le rapport de simulation d’attaque

:::image type="content" source="../../media/attack-sim-report-training-completion-view.png" alt-text="Onglet Formation semi-automatique dans le rapport de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-completion-view.png":::

Sous l’onglet **Achèvement de l’apprentissage** , le graphique affiche le nombre de simulations **terminées**, **en cours** et **incomplètes** . Si vous pointez sur une section du graphique, les valeurs réelles sont affichées.

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Username**
- **Adresse de messagerie**
- **Inclus dans la simulation**
- **Date de la dernière simulation**
- **Résultat de la dernière simulation**
- **Nom de la formation la plus récente terminée**
- **Date de fin**
- **Toutes les formations**

Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible.

Cliquez sur **Personnaliser les colonnes** pour supprimer les colonnes affichées. Lorsque vous avez terminé, cliquez sur **Appliquer**.

Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer le graphique et la table de détails d’une ou plusieurs des valeurs suivantes :

- **Terminée**
- **En cours**
- **All**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Utilisez ![la zone **de recherche** d’icône](../../media/m365-cc-sc-search-icon.png) de recherche pour filtrer les résultats par **nom d’utilisateur** ou **adresse Email**. Les caractères génériques ne sont pas pris en charge.

Si vous cliquez sur l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Bouton Exporter le rapport** , la progression de génération du rapport s’affiche sous la forme d’un pourcentage d’achèvement. Dans la boîte de dialogue qui s’ouvre, vous pouvez choisir d’ouvrir le fichier .csv, d’enregistrer le fichier .csv et de mémoriser la sélection.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Onglet Récidifs pour le rapport de simulation d’attaque

:::image type="content" source="../../media/attack-sim-report-repeat-offenders-view.png" alt-text="Onglet Récidivistes dans le rapport de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-report-repeat-offenders-view.png":::

Un _récidiviste_ est un utilisateur qui a été compromis par des simulations consécutives. Le nombre par défaut de simulations consécutives est de deux, mais vous pouvez modifier la valeur sous l’onglet **Paramètres** de Exercice de simulation d'attaque à <https://security.microsoft.com/attacksimulator?viewid=setting>.

Sous l’onglet **Récidivistes** , le graphique organise les données des récidivistes par [type de simulation](attack-simulation-training.md#select-a-social-engineering-technique) :

- **All**
- **Collecte des informations d’identification**
- **Pièce jointe de programme malveillant**
- **Lien dans la pièce jointe**
- **Lien vers un programme malveillant**
- **Drive-by URL**

Si vous pointez sur un point de données dans le graphique, les valeurs réelles sont affichées.

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Utilisateur**
- **Nombre de répétitions**
- **Types de simulation**
- **Simulations**

Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible.

Cliquez sur **Personnaliser les colonnes** pour supprimer les colonnes affichées. Lorsque vous avez terminé, cliquez sur **Appliquer**.

Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer le graphique et la table de détails en fonction d’une partie ou de la totalité des valeurs de type de simulation :

- **Collecte des informations d’identification**
- **Pièce jointe de programme malveillant**
- **Lien dans la pièce jointe**
- **Lien vers un programme malveillant**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Utilisez ![la zone **de recherche** d’icônes](../../media/m365-cc-sc-search-icon.png) de recherche pour filtrer les résultats selon l’une des valeurs de colonne. Les caractères génériques ne sont pas pris en charge.

Si vous cliquez sur l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Bouton Exporter le rapport** , la progression de génération du rapport s’affiche sous la forme d’un pourcentage d’achèvement. Dans la boîte de dialogue qui s’ouvre, vous pouvez choisir d’ouvrir le fichier .csv, d’enregistrer le fichier .csv et de mémoriser la sélection.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Insights et rapports dans les détails de simulation de Exercice de simulation d'attaque

Pour accéder à l’onglet **Simulations**, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse **Email &** \> **collaboration Exercice de simulation d'attaque**, puis sélectionnez l’onglet **Simulations**. Pour accéder directement à l’onglet **Simulations** de la page **Exercice de simulation d'attaque**, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulations>.

Lorsque vous sélectionnez une simulation dans la liste, une page de détails s’ouvre. Cette page contient les paramètres de configuration de la simulation que vous attendez de voir (état, date de lancement, charge utile utilisée, etc.).

Le reste de cette section décrit les insights et les rapports disponibles dans la page des détails de la simulation.

### <a name="simulation-impact-section"></a>Section Impact de simulation

La section **Simulation impact** sur la page détails de la simulation indique le nombre d’utilisateurs complètement trompés par la simulation et le nombre total d’utilisateurs dans la simulation. Les informations affichées varient en fonction du type de simulation. Par exemple :

- Liens : **informations d’identification entrées** et **non entrées d’informations d’identification**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-links.png" alt-text="Section Impact de la simulation pour plus d’informations sur la simulation liée aux liens" lightbox="../../media/attack-sim-training-sim-details-sim-impact-links.png":::

- Pièces jointes : **pièce jointe ouverte** et **pièce jointe non ouverte**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-attachments.png" alt-text="Section Impact de simulation pour les détails de simulation liés aux pièces jointes" lightbox="../../media/attack-sim-training-sim-details-sim-impact-attachments.png":::

Si vous pointez sur une section du graphique, les nombres réels de chaque catégorie sont affichés.

### <a name="all-user-activity-section"></a>Section Toutes les activités des utilisateurs

La section **Toutes les activités des utilisateurs** de la page détails de la simulation affiche des nombres pour les résultats possibles de la simulation. Les informations affichées varient en fonction du type de simulation. Par exemple :

- **SuccessfullyDeliveredEmail**
- **ReportedEmail** : nombre d’utilisateurs ayant signalé le message de simulation comme suspect.
- Liens:
  - **EmailLinkClicked** : nombre d’utilisateurs qui ont cliqué sur le lien dans le message de simulation.
  - **CredSupplied** : Après avoir cliqué sur le lien, combien d’utilisateurs ont fourni leurs informations d’identification.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-links.png" alt-text="Section Toutes les activités utilisateur pour les détails de simulation liés aux liens" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-links.png":::

- Pièces jointes:
  - **AttachmentOpened** : nombre d’utilisateurs qui ont ouvert la pièce jointe dans le message de simulation.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png" alt-text="Section Toutes les activités utilisateur pour les détails de simulation liés aux pièces jointes" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png":::

### <a name="training-completion-section"></a>Section d’achèvement de la formation

La section **De saisie semi-automatique** de la page détails de la simulation affiche les formations requises pour la simulation et le nombre d’utilisateurs qui ont terminé les formations.

:::image type="content" source="../../media/attack-sim-training-sim-details-training-completed.png" alt-text="Section d’achèvement de la formation pour les détails de simulation liés aux pièces jointes" lightbox="../../media/attack-sim-training-sim-details-training-completed.png":::

## <a name="recommended-actions-section"></a>Section Actions recommandées

La section **Actions recommandées** de la page détails de la simulation affiche les actions de recommandation de [Microsoft Secure Score](../defender/microsoft-secure-score.md) et l’effet de l’action sur votre degré de sécurisation. Ces recommandations sont basées sur la charge utile utilisée dans la simulation et vous aideront à protéger vos utilisateurs et votre environnement. La sélection d’une **action d’amélioration** dans la liste vous amène à l’emplacement où implémenter l’action suggérée.

:::image type="content" source="../../media/attack-sim-training-sim-details-recommended-actions.png" alt-text="Section Actions de recommandation sur Exercice de simulation d'attaque" lightbox="../../media/attack-sim-training-sim-details-recommended-actions.png":::

## <a name="related-links"></a>Liens connexes

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[créer une charge utile pour former vos employés](attack-simulation-training-payloads.md#create-payloads)
