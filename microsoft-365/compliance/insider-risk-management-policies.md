---
title: Stratégies de gestion des risques internes
description: En savoir plus sur les stratégies de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: e135ceec2ac4abcd0bfd5183fb19089a97dc4bb4
ms.sourcegitcommit: e55e4747d3b838baacab8985aefc24aac245c431
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44043295"
---
# <a name="insider-risk-management-policies"></a>Stratégies de gestion des risques internes

Les stratégies de gestion des risques internes déterminent les employés qui sont à portée de la responsabilité et les types d’indicateurs de risques configurés pour les alertes. Vous pouvez rapidement créer une stratégie qui s’applique à tous les utilisateurs de votre organisation ou définir des utilisateurs ou des groupes individuels pour la gestion dans une stratégie. Les stratégies prennent en charge les priorités de contenu pour concentrer les conditions de stratégie sur plusieurs ou des équipes Microsoft Teams, des sites SharePoint, des types de sensibilité aux données et des étiquettes de données. À l’aide de modèles, ils incluent des indicateurs de risque spécifiques et la quantité de pondération qu’ils ont affectée au sein d’une stratégie, déterminant ainsi le poids de chaque déclencheur d’alerte dans la stratégie. Les fenêtres stratégies vous permettent de définir le délai d’application de la stratégie aux activités d’alerte et de déterminer la durée de la stratégie une fois activée. La limite de stratégie maximale est de cinq stratégies actives en même temps. Toutefois, vous pouvez configurer des stratégies supplémentaires et activer et désactiver des stratégies en fonction de vos besoins.

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **tableau de bord de stratégie** vous permet d’afficher rapidement les stratégies de votre organisation et l’état actuel des alertes associées à chaque stratégie.

- **Nom**de la stratégie : nom attribué à la stratégie dans l’Assistant stratégie.
- **Alertes actives**: nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées**: le nombre total d’alertes résultantes dans les cas de la stratégie au cours des 365 derniers jours.
- **Actions effectuées sur les alertes**: nombre total d’alertes confirmées ou rejetées au cours des 365 derniers jours.
- **Efficacité**de la stratégie : pourcentage déterminé par les alertes totales confirmées divisé par les actions effectuées sur les alertes (c’est-à-dire la somme des alertes qui ont été confirmées ou refermées au cours de l’année précédente).
- **Actif**: état de l’incident, soit *Oui* , soit *non*.

![Tableau de bord des stratégies de gestion des risques internes](../media/insider-risk-policy-dashboard.png)

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques initiés sont des conditions de stratégie prédéfinies qui définissent les types d’indicateurs de risque surveillés par une stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de la stratégie. Lorsque vous créez une stratégie de risque Insider, vous pouvez choisir l’un des modèles suivants.

### <a name="departing-employee-data-theft"></a>Défaition des vols de données des employés

Lorsque les employés quittent votre organisation, il existe des indicateurs de risque spécifiques généralement associés au vol de données par le fait de sortir des employés. Ce modèle de stratégie donne la priorité à ces indicateurs et concentre la détection et les alertes sur ce domaine à risque. Le vol de données pour le retrait des employés peut inclure le téléchargement de fichiers à partir de SharePoint Online, la copie de fichiers sur des appareils portables tels que des lecteurs USB, l’impression de fichiers et la copie de données vers des services de stockage et de messagerie Cloud personnels à proximité de leurs dates de démission et de fin d’emploi. Ce modèle établit la priorité des indicateurs de risque liés à ces activités et la façon dont ils correspondent à l’état d’emploi de l’employé.

>[!IMPORTANT]
>Lors de l’utilisation de ce modèle, vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement les informations de date de démission et de cessation d’emploi pour les employés de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir la rubrique [importer des données avec le connecteur RH](import-hr-data.md) .

### <a name="data-leaks"></a>Fuites de données

La protection des données et la prévention des fuites de données sont des défis constants pour la plupart des organisations, en particulier en ce qui concerne la croissance rapide des nouvelles données créées par les employés, les appareils et les services. Les employés sont habilités à créer, stocker et partager des informations entre les services et les appareils qui rendent la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure un partage accidentel d’informations en dehors de votre organisation ou du vol de données à des fins malveillantes. Ce modèle permet de hiérarchiser la détection en temps réel des téléchargements de données SharePoint Online suspects, de partager des fichiers et des dossiers, de copier des fichiers sur des appareils portables tels que des lecteurs USB, d’imprimer des fichiers et de copier des données dans des services de stockage et de messagerie Cloud personnels.

>[!IMPORTANT]
>Lorsque vous utilisez ce modèle, vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation. Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation.

### <a name="offensive-language-in-email"></a>Langage choquant dans le courrier électronique

Détecter et prendre des mesures pour empêcher le comportement offensant et abusif est un élément essentiel de la prévention des risques. Les classifieurs de langue injurieux intégrés dans Microsoft 365 peuvent analyser les messages électroniques envoyés à partir de boîtes aux lettres Exchange Online de votre organisation pour différents types de problèmes de conformité. Ces classifieurs utilisent une combinaison d’intelligence artificielle et de mots clés pour identifier la langue du courrier électronique susceptible de violer les stratégies anti-harcèlement. Utilisez ce modèle pour créer rapidement une stratégie qui utilise ces classifieurs pour détecter automatiquement le contenu des messages électroniques qui peut être considéré comme injurieux ou choquant. La gestion des risques internes utilise des classifieurs qui analysent les messages électroniques envoyés pour les termes et les sentiments de langue anglaise pour le langage offensant.

## <a name="policy-settings"></a>Paramètres de stratégie

Les paramètres des risques internes s’appliquent à toutes les stratégies de gestion des risques internes, quel que soit le modèle que vous avez choisi lors de la création d’une stratégie. Les paramètres sont configurés à l’aide du contrôle des **paramètres des risques Insiders** situé en haut de tous les onglets de gestion des risques Insiders. Ces paramètres contrôlent la confidentialité, les indicateurs, les fenêtres de surveillance et les détections intelligentes.

### <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs qui ont des correspondances de stratégie est importante et peut contribuer à promouvoir l’objection en matière d’analyse des données et d’analyse des alertes relatives aux risques internes. Pour les utilisateurs disposant d’une stratégie de risque Insider, vous pouvez choisir l’un des paramètres suivants :

- **Afficher les versions anonymes des**noms d’utilisateur : les noms d’utilisateur sont rendus anonymes pour empêcher les administrateurs, les investigateurs de données et les relecteurs de voir qui est associé à des alertes de stratégie. Par exemple, un utilisateur « gracieuses Taylor » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans tous les domaines de l’expérience de gestion des risques inSided. Le choix de ce paramètre anonymizes tous les utilisateurs avec des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans les détails des alertes de risque et des cas d’Insider ne seront pas disponibles lorsque cette option est sélectionnée. Toutefois, les noms d’utilisateur sont affichés lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelle ou passée.
- **Ne pas afficher les versions anonymes des noms d’utilisateur**: les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelle et passée pour les alertes et les incidents. Les informations de profil utilisateur (nom, titre, alias, organisation ou service) s’affichent pour l’utilisateur pour toutes les alertes et les incidents liés à la gestion des risques Insiders.

### <a name="indicators"></a>Confirme

Les modèles de stratégie de risque initié définissent le type d’activités de risque que vous souhaitez détecter et examiner. Chaque modèle de stratégie est basé sur des indicateurs spécifiques qui correspondent à des activités de risque spécifiques et les alertes sont déclenchées par des stratégies lorsque les utilisateurs effectuent des activités liées à ces indicateurs. Dans certains cas, vous souhaiterez peut-être limiter les indicateurs appliqués aux stratégies de risque des initiés au sein de votre organisation. Vous pouvez désactiver les indicateurs pour des zones spécifiques en les désactivant de toutes les stratégies de risque d’initié.

Pour définir les indicateurs activés dans toutes les stratégies, accédez à > **indicateurs** de **paramètres des risques internes**et sélectionnez un ou plusieurs indicateurs. Les indicateurs sélectionnés sur la page Paramètres des **indicateurs** ne peuvent pas être configurés individuellement lors de la création ou de la modification d’une stratégie de risque initié dans l’Assistant stratégie.

>[!IMPORTANT]
>Pour recevoir des alertes relatives aux activités à risque définies dans vos stratégies, vous devez sélectionner un ou plusieurs indicateurs avant de configurer une stratégie d’Insider Risk.

### <a name="policy-timeframes"></a>Périodes de stratégie

Les périodes de stratégie vous permettent de définir des périodes passées et futures qui sont déclenchées après la mise en correspondance de la stratégie basée sur les événements et les activités des modèles de stratégie de gestion des risques inSided. Selon le modèle de stratégie que vous choisissez, les délais de stratégie suivants sont disponibles :

- **Fenêtre d’activation**: disponible pour tous les modèles de stratégie, la *fenêtre d’activation* est le nombre de jours défini pendant lesquels la fenêtre est activée **après** un événement déclencheur. La fenêtre est activée entre 1 et 30 jours après qu’un événement déclencheur se produit pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques inSided et vous avez défini la *fenêtre d’activation* sur 30 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active la *fenêtre d’activation* et la stratégie est active pour cet utilisateur pendant 30 jours après la survenue de l’événement déclencheur.
- **Détection de l’activité passée**: disponible pour tous les modèles de stratégie, la *détection d’activité passée* est le nombre de jours défini pendant lesquels la fenêtre est activée **avant** un événement déclencheur. La fenêtre est activée entre 0 et 180 jours avant qu’un événement déclencheur se produise pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques inSided et défini la détection de l' *activité passée* sur 90 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active la *détection d’activité passée* et la stratégie recueille des activités historiques pour cet utilisateur pendant 90 jours avant l’événement déclencheur.

### <a name="intelligent-detections"></a>Détections intelligentes

Les paramètres de détection intelligents permettent d’affiner la manière dont les détections d’activités à risque sont traitées pour les alertes. Dans certains cas, vous devrez peut-être définir des types de fichiers à ignorer ou vous souhaitez appliquer un niveau de détection pour les fichiers afin de définir une barre minimale pour les alertes. Lorsque vous utilisez des stratégies de langue offensantes, vous devrez peut-être augmenter ou diminuer la sensibilité de la détection pour contrôler la quantité de correspondances de stratégie signalées. Utilisez ces paramètres pour contrôler les exclusions de types de fichiers, les limites de volume de fichiers et la sensibilité de détection de langue offensant.

#### <a name="anomaly-detections"></a>Détections d’anomalies

Les détections anormales incluent des paramètres pour les exclusions de types de fichiers et les limites de volume de fichiers.

- **Exclusions**de types de fichiers : pour exclure des types de fichiers spécifiques de toutes les correspondances de stratégie de gestion des risques Insider, entrez les extensions de types de fichiers séparées par des virgules. Par exemple, pour exclure certains types de fichiers musicaux de la stratégie, vous pouvez entrer *AAC, mp3, WAV, WMA* dans le champ **type de fichier exclusions** . Les fichiers avec ces extensions seront ignorés par toutes les stratégies de gestion des risques Insiders.
- **Limite de volume de fichiers dépassée**: pour définir un niveau de fichier minimal avant que les alertes d’activité soient consignées dans les stratégies de risque initié, entrez le nombre de fichiers. Par exemple, vous devez entrer « 10 » si vous ne souhaitez pas générer d’alertes relatives aux risques initiés lorsqu’un utilisateur télécharge 10 fichiers ou moins, même si les stratégies considèrent cette activité comme une anomalie.

#### <a name="offensive-language-detections"></a>Détections de langue choquantes

Pour ajuster la sensibilité du classificateur de langue offensant aux stratégies utilisant le *langage offensant dans le modèle de courrier électronique* , choisissez l’un des paramètres suivants :

- **Faible**: niveau de sensibilité le plus élevé avec la plage la plus large pour la détection du langage offensant et des sentiments. La probabilité de faux positifs pour une correspondance choquante est élevée.
- **Moyenne**: niveau de confidentialité de milieu de gamme avec une plage équilibrée pour la détection du langage offensant et des sentiments. La probabilité de faux positifs pour une mise en correspondance choquante est moyenne.
- **Élevé**: niveau de sensibilité le plus élevé avec une plage étroite pour la détection du langage offensant et des sentiments. La probabilité de faux positifs pour une mise en correspondance choquante est faible.

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques inSided, vous utiliserez l’Assistant stratégie dans la solution de **gestion des risques Insider** dans le centre de conformité Microsoft 365.

Pour créer une stratégie, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Sélectionnez **créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Dans la page **nommer votre stratégie et choisir un modèle** , renseignez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultatif)**: entrez une description pour la stratégie.
    - **Choisir un modèle de stratégie (obligatoire)**: sélectionnez un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) pour définir les types d’indicateurs de risque sont surveillés par la stratégie.

    >[!IMPORTANT]
    >Si vous sélectionnez le modèle *fuites de données* , vous devez configurer au moins une stratégie DLP que vous allez attribuer ultérieurement dans l’Assistant. Si vous sélectionnez le modèle de *vol de données par employé* , vous devez configurer le connecteur RH pour qu’il utilise les fonctionnalités de détection de signal complètes du modèle de stratégie.

4. Sélectionnez **suivant** pour continuer.
5. Sur la page **choisir les utilisateurs et les groupes** , sélectionnez **choisir les utilisateurs ou les groupes** pour définir les utilisateurs qui sont inclus dans la stratégie ou activez la case à cocher tous les **utilisateurs et les groupes à extension messagerie** . Sélectionnez **suivant** pour continuer.
6. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , vous pouvez attribuer des notes à risque plus élevées à l’activité détectée en fonction de l’emplacement du contenu associé, des informations sensibles incluses et des étiquettes de confidentialité appliquées :
    - Sites SharePoint : sélectionnez **choisir les sites SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - Type d’informations sensibles : sélectionnez **choisir les types d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - Étiquettes de sensibilité : sélectionnez **choisir les étiquettes de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
7. Sélectionnez **suivant** pour continuer.
8. Sur la **page indicateurs d’alerte** , vous verrez les indicateurs que vous avez définis sur la page**indicateurs** de paramètres > de **risque inSided**. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
9. Sur la page **Sélectionner la fenêtre d’analyse** , vous verrez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#policy-timeframes) pour la stratégie que vous avez configurée dans les paramètres des risques initiés. Si vous avez sélectionné le modèle de stratégie de *vol de données par employé* , vous pouvez activer la case à cocher valider l’activité après *arrêt* pour détecter toute activité postérieure à la date d’expiration importée du connecteur RH de Microsoft 365.
10. Sélectionnez **suivant** pour continuer.
11. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour créer et activer la stratégie.

## <a name="update-a-policy"></a>Mettre à jour une stratégie

Pour mettre à jour une stratégie de gestion des risques inSided existante, vous allez utiliser l’Assistant stratégie dans la solution de **gestion des risques inSided** dans le centre de conformité Microsoft 365.

Pour gérer une stratégie existante, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie que vous souhaitez gérer.
3. Sur la page Détails de stratégie, sélectionnez **modifier la stratégie** .
4. Dans l’Assistant stratégie, vous ne pouvez pas modifier les champs suivants :
    - **Name**: nom convivial de la stratégie
    - **Sélectionnez le manuel**: le modèle utilisé pour définir les types d’indicateurs de risque surveillés par la stratégie.
5. Entrez une nouvelle description pour la stratégie dans le champ **Description** . Sélectionnez **suivant** pour continuer.
6. Sur la page **choisir les utilisateurs et les groupes** , sélectionnez **choisir les utilisateurs ou les groupes** pour définir les utilisateurs qui sont inclus dans la stratégie ou activez la case à cocher tous les **utilisateurs et les groupes à extension messagerie** . Sélectionnez **suivant** pour continuer
7. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , mettez à jour les sources pour définir la priorité des activités utilisateur à risque :
    - Sites SharePoint : sélectionnez **choisir les sites SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - Type d’informations sensibles : sélectionnez **choisir les types d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - Étiquettes de sensibilité : sélectionnez **choisir les étiquettes de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
8. Sélectionnez **suivant** pour continuer.
9. Sur la **page indicateurs d’alerte** , vous verrez les indicateurs que vous avez définis sur la page**indicateurs** de paramètres > de **risque inSided**. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
10. Sur la page **Sélectionner la fenêtre d’analyse** , vous verrez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#policy-timeframes) pour la stratégie que vous avez configurée dans les paramètres des risques initiés. Si vous avez sélectionné le modèle de stratégie de *vol de données par employé* , vous pouvez activer la case à cocher valider l’activité après *arrêt* pour détecter toute activité postérieure à la date d’expiration importée du connecteur RH de Microsoft 365.
11. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour mettre à jour et activer les modifications apportées à la stratégie.

## <a name="delete-a-policy"></a>Suppression d’une stratégie

>[!NOTE]
>La suppression d’une stratégie ne supprime pas les alertes actives ou archivées générées à partir de la stratégie.

Pour supprimer une stratégie de gestion des risques initiés existante, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie que vous souhaitez gérer.
3. Sélectionnez **supprimer** dans la barre d’outils Tableau de bord.
4. Dans la boîte de dialogue **supprimer** , sélectionnez **Oui** pour supprimer la stratégie, ou cliquez sur **Annuler** pour fermer la boîte de dialogue.
