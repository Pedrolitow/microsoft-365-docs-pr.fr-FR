---
title: Stratégies de gestion des risques Insiders (aperçu)
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
ms.openlocfilehash: 161118bb8ff8a5c79ee507d329e20bad1421d8fd
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41590615"
---
# <a name="insider-risk-management-policies-preview"></a>Stratégies de gestion des risques Insiders (aperçu)

Les stratégies de gestion des risques internes déterminent les employés qui sont à portée de la responsabilité et les types d’indicateurs de risques configurés pour les alertes. Vous pouvez rapidement créer une stratégie qui s’applique à tous les utilisateurs de votre organisation ou définir des utilisateurs ou des groupes individuels pour la gestion dans une stratégie. Les stratégies prennent en charge les priorités de contenu pour concentrer les conditions de stratégie sur plusieurs ou des équipes Microsoft Teams, des sites SharePoint, des types de sensibilité aux données et des étiquettes de données. À l’aide de modèles, ils incluent des indicateurs de risque spécifiques et la quantité de pondération qu’ils ont affectée au sein d’une stratégie, déterminant ainsi le poids de chaque déclencheur d’alerte dans la stratégie. Les fenêtres stratégies vous permettent de définir le délai d’application de la stratégie aux activités d’alerte et de déterminer la durée de la stratégie une fois activée. La limite de stratégie maximale est de cinq stratégies actives en même temps. Toutefois, vous pouvez configurer des stratégies supplémentaires et activer et désactiver des stratégies en fonction de vos besoins.

## <a name="policy-dashboard"></a>Tableau de bord de stratégie

Le **tableau de bord de stratégie** vous permet d’afficher rapidement les stratégies de votre organisation et l’état actuel des alertes associées à chaque stratégie.

- **Nom**de la stratégie : nom attribué à la stratégie dans l’Assistant stratégie.
- **Alertes actives**: nombre d’alertes actives pour chaque stratégie.
- **Alertes confirmées**: le nombre total d’alertes résultantes dans les cas de la stratégie au cours des 365 derniers jours.
- **Actions effectuées sur les alertes**: nombre total d’alertes confirmées ou rejetées au cours des 365 derniers jours.
- **Efficacité**de la stratégie : pourcentage déterminé par les alertes totales confirmées divisé par les actions effectuées sur les alertes (c’est-à-dire la somme des alertes qui ont été confirmées ou refermées au cours de l’année précédente).
- **Actif**: état de l’incident, soit *Oui* , soit *non*.

![Tableau de bord des stratégies de gestion des risques internes](media/insider-risk-policy-dashboard.png)

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de gestion des risques initiés sont des conditions de stratégie prédéfinies qui définissent les types d’indicateurs de risque surveillés par une stratégie. Chaque stratégie doit avoir un modèle affecté dans l’Assistant de création de stratégie avant la création de la stratégie. Lorsque vous créez une stratégie de risque Insider, vous pouvez choisir l’un des modèles suivants.

### <a name="departing-employee-data-theft"></a>Défaition des vols de données des employés

Lorsque les employés quittent votre organisation, il existe des indicateurs de risque spécifiques généralement associés au vol de données par le fait de sortir des employés. Ce modèle de stratégie donne la priorité à ces indicateurs et concentre la détection et les alertes sur ce domaine à risque. Le vol de données pour le retrait des employés peut inclure le téléchargement de fichiers à partir de SharePoint Online, la copie de fichiers sur des appareils portables tels que des lecteurs USB, l’impression de fichiers et la copie de données vers des services de stockage et de messagerie Cloud personnels à proximité de leur démission de l’emploi et dates de fin. Ce modèle établit la priorité des indicateurs de risque liés à ces activités et la façon dont ils correspondent à l’état d’emploi de l’employé.

>[!IMPORTANT]
>Lors de l’utilisation de ce modèle, vous devez configurer un connecteur RH Microsoft 365 pour importer régulièrement les informations de date de démission et de cessation d’emploi pour les employés de votre organisation. Pour obtenir des conseils détaillés sur la configuration du connecteur RH Microsoft 365 pour votre organisation, voir la rubrique [importer des données avec le connecteur RH](import-hr-data.md) .

### <a name="data-leaks"></a>Fuites de données

La protection des données et la prévention des fuites de données sont des défis constants pour la plupart des organisations, en particulier en ce qui concerne la croissance rapide des nouvelles données créées par les employés, les appareils et les services. Les employés sont habilités à créer, stocker et partager des informations entre les services et les appareils qui rendent la gestion des fuites de données de plus en plus complexe et difficile. Les fuites de données peuvent inclure un partage accidentel d’informations en dehors de votre organisation ou du vol de données à des fins malveillantes. Ce modèle permet de hiérarchiser la détection en temps réel des téléchargements de données SharePoint Online suspects, de partager des fichiers et des dossiers, de copier des fichiers sur des appareils portables tels que des lecteurs USB, d’imprimer des fichiers et de copier des données dans des services de stockage et de messagerie Cloud personnels.

>[!IMPORTANT]
>Lorsque vous utilisez ce modèle, vous devez configurer au moins une stratégie de protection contre la perte de données (DLP) pour définir des informations sensibles dans votre organisation. Consultez la rubrique [créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP pour votre organisation.

### <a name="offensive-language-in-email"></a>Langage choquant dans le courrier électronique

Détecter et prendre des mesures pour empêcher le comportement offensant et abusif est un élément essentiel de la prévention des risques. Les classifieurs de langue injurieux intégrés dans Microsoft 365 peuvent analyser les messages électroniques envoyés à partir de boîtes aux lettres Exchange Online de votre organisation pour différents types de problèmes de conformité. Ces classifieurs utilisent une combinaison d’intelligence artificielle et de mots clés pour identifier la langue du courrier électronique susceptible de violer les stratégies anti-harcèlement. Utilisez ce modèle pour créer rapidement une stratégie qui utilise ces classifieurs pour détecter automatiquement le contenu des messages électroniques qui peut être considéré comme injurieux ou choquant. La gestion des risques internes utilise des classifieurs qui analysent les messages électroniques envoyés pour les termes et les sentiments de langue anglaise pour le langage offensant.

## <a name="monitoring-windows"></a>Surveillance des fenêtres

Les fenêtres de surveillance des stratégies vous permettent de définir des périodes qui déclenchent l’activation de la stratégie en fonction des événements et des activités des modèles de stratégie de gestion des risques inSided. Selon le modèle de stratégie que vous choisissez, les fenêtres de surveillance suivantes sont disponibles :

- **Dans l’étendue TimeSpan**: disponible pour tous les modèles de stratégie, l’option *TimeSpan dans l’étendue* est le nombre de jours défini pendant lesquels la fenêtre est activée **après** un événement déclencheur. La fenêtre est activée entre 1 et 30 jours après qu’un événement déclencheur se produit pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques inSided et défini l' *étendue TimeSpan* sur 30 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active l' *étendue TimeSpan* et la stratégie est active pour cet utilisateur pendant 30 jours après la survenue de l’événement déclencheur.
- **Historique TimeSpan**: disponible pour tous les modèles de stratégie, l' *historique TimeSpan* indique le nombre de jours défini pendant lesquels la fenêtre est activée **avant** un événement déclencheur. La fenêtre est activée entre 0 et 180 jours avant qu’un événement déclencheur se produise pour tout utilisateur affecté à la stratégie. Par exemple, vous avez configuré une stratégie de gestion des risques inSided et défini l' *historique TimeSpan* sur 90 jours. Plusieurs mois se sont écoulés depuis que vous avez configuré la stratégie et un événement déclencheur se produit pour l’un des utilisateurs inclus dans la stratégie. L’événement déclencheur active l' *historique TimeSpan* et la stratégie recueille des activités historiques pour cet utilisateur pendant 90 jours avant l’événement déclencheur.
- **Fenêtre de fin de contrat**: vous verrez ce paramètre dans la préversion publique, mais elle n’est pas appliquée à des stratégies et sera supprimée pour la version de production de cette solution.
- **Fin**de la fenêtre de terminaison : vous verrez ce paramètre dans la préversion publique, mais elle n’est pas appliquée à des stratégies et sera supprimée pour la version de production de cette solution.

## <a name="create-a-new-policy"></a>Créer une stratégie

Pour créer une stratégie de gestion des risques inSided, vous utiliserez l’Assistant stratégie dans la solution de **gestion des risques Insider** dans le centre de conformité Microsoft 365.

Pour créer une stratégie, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Sélectionnez **créer une stratégie** pour ouvrir l’Assistant stratégie.
3. Sur la page **nouvelle stratégie de risque Insider** , renseignez les champs suivants :
    - **Nom (obligatoire)**: entrez un nom convivial pour la stratégie.
    - **Description (facultatif)**: entrez une description pour la stratégie.
    - **Choisir un modèle de stratégie (obligatoire)**: sélectionnez un des [modèles de stratégie](insider-risk-management-policies.md#policy-templates) pour définir les types d’indicateurs de risque sont surveillés par la stratégie.

    >[!IMPORTANT]
    >Si vous sélectionnez le modèle *fuites de données* , vous devez configurer au moins une stratégie DLP que vous allez attribuer ultérieurement dans l’Assistant. Si vous sélectionnez le modèle de *vol de données par employé* , vous devez configurer le connecteur RH pour qu’il utilise les fonctionnalités de détection de signal complètes du modèle de stratégie.

4. Sélectionnez **suivant** pour continuer.
5. Dans la page **utilisateurs** , sélectionnez **Ajouter un utilisateur ou un groupe** pour définir les utilisateurs inclus dans la stratégie ou cochez la case **tous les utilisateurs et les groupes à extension messagerie** . Sélectionnez **suivant** pour continuer.
6. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , vous pouvez affecter les sources à classer par ordre de priorité pour les activités utilisateur à risque :
    - Sites SharePoint : sélectionnez **Ajouter un site SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - Type d’informations sensibles : sélectionnez **Ajouter un type d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - Étiquettes de sensibilité : sélectionnez **Ajouter une étiquette de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
7. Sélectionnez **suivant** pour continuer.
8. Sur la page **choisir les indicateurs d’alerte** , vous verrez les indicateurs inclus dans le modèle que vous avez choisi pour cette stratégie. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
9. Sur la page **Sélectionner la fenêtre d’analyse** , vous définirez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#monitoring-windows) pour la stratégie. Configurez les fenêtres de surveillance comme il convient.
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
6. Dans la page **utilisateurs** , sélectionnez **Ajouter un utilisateur ou un groupe** pour définir les utilisateurs inclus dans la stratégie ou cochez la case **tous les utilisateurs et les groupes à extension messagerie** . Sélectionnez **suivant** pour continuer
7. Sur la page **spécifier le contenu à classer par priorité (facultatif)** , mettez à jour les sources pour définir la priorité des activités utilisateur à risque :
    - Sites SharePoint : sélectionnez **Ajouter un site SharePoint** et sélectionnez les organisations SharePoint dont vous souhaitez définir la priorité. Par exemple, *« Group1@contoso.sharepoint.com/sites/group1 »*.
    - Type d’informations sensibles : sélectionnez **Ajouter un type d’informations sensibles** et sélectionnez les types de critère de diffusion dont vous souhaitez définir la priorité. Par exemple, *« numéro de compte bancaire américain »* et *« numéro de carte de crédit »*.
    - Étiquettes de sensibilité : sélectionnez **Ajouter une étiquette de confidentialité** et sélectionnez les étiquettes dont vous souhaitez définir la priorité. Par exemple, *« confidentiel »* et *« secret »*.
8. Sélectionnez **suivant** pour continuer.
9. Sur la page **choisir les indicateurs d’alerte** , vous verrez les indicateurs inclus dans le modèle que vous avez choisi pour cette stratégie. Si vous avez sélectionné le modèle *fuites de données* au début de l’Assistant, vous devez sélectionner une stratégie DLP dans la liste déroulante **stratégie DLP** .
10. Sur la page **Sélectionner la fenêtre d’analyse** , vous définirez les conditions de la fenêtre de [surveillance](insider-risk-management-policies.md#monitoring-windows) pour la stratégie. Configurez les fenêtres de surveillance comme il convient.
11. Sur la page **révision** , passez en revue les paramètres que vous avez choisis pour la stratégie. Sélectionnez **modifier** pour modifier les valeurs de la stratégie ou sélectionnez **Envoyer** pour mettre à jour et activer les modifications apportées à la stratégie.

## <a name="delete-a-policy"></a>Suppression d’une stratégie

>[!NOTE]
>La suppression d’une stratégie ne supprime pas les alertes actives ou archivées générées à partir de la stratégie.

Pour supprimer une stratégie de gestion des risques initiés existante, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **stratégies** .
2. Dans le tableau de bord de stratégie, sélectionnez la stratégie que vous souhaitez gérer.
3. Sélectionnez **supprimer** dans la barre d’outils Tableau de bord.
4. Dans la boîte de dialogue **supprimer** , sélectionnez **Oui** pour supprimer la stratégie, ou cliquez sur **Annuler** pour fermer la boîte de dialogue.