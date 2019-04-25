---
title: 'Étape 2 : Configurer la classification pour votre environnement'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/10/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez différentes méthodes pour classer les données de votre organisation.
ms.openlocfilehash: ca64b98bceb6f969adc964e93a6a1cc872763199
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32286973"
---
# <a name="step-2-configure-classification-for-your-environment"></a>Étape 2 : Configurer la classification pour votre environnement

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Dans cette étape, vous travaillez avec vos équipes juridiques et de conformité pour définir un système de classification pour les données de votre organisation.

## <a name="microsoft-365-classification-types"></a>Types de classification de Microsoft 365

Microsoft 365 inclut quatre types de classification :

- Types d’informations sensibles
- Étiquettes de rétention
- Étiquettes de niveau de confidentialité
- Étiquettes Azure Information Protection et protection

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Les types d’informations sensibles pour Microsoft 365 définissent comment les processus automatisés tels que la recherche reconnaissent les types d’informations spécifiques. Celles-ci incluent les données sensibles employé ou client tels que les numéros de sécurité sociale et les numéros de carte bancaire. Vous utilisez les types d’informations sensibles pour trouver des données sensibles et appliquer des règles de prévention contre la perte de données et des stratégies pour protéger ces données. Pour plus d’informations, voir [ce que contient une stratégie DLP](https://docs.microsoft.com/office365/securitycompliance/data-loss-prevention-policies#what-a-dlp-policy-contains). 

Les types d’informations sensibles sont particulièrement utiles pour se plier aux exigences de conformité et réglementation, comme pour la Protection générale des données (RGPD).

### <a name="retention-labels"></a>Étiquettes de rétention

Une partie de définir une stratégie de gouvernance des données consiste à décider combien de temps des types spécifiques de documents ou des documents avec contenu spécifique doivent être conservés, conformément aux stratégies de l’organisation et aux réglementations régionales. Par exemple, certains types de documents doivent être conservés pendant une durée définie avant d’être supprimés et d’autres doivent être conservés indéfiniment.

Pour les documents stockés dans Microsoft 365, définir et appliquer des étiquettes de rétention à des documents et données stockées dans la messagerie Exchange, SharePoint Online, OneDrive Entreprise et messages de conversation et canal Teams. Pour plus d’informations, notamment comment les créer, voir [vue d’ensemble des étiquettes de rétention](https://docs.microsoft.com/office365/securitycompliance/labels).

Si vous utilisez des étiquettes de rétention, vous devez configurer une étiquette pour chaque catégorie de fichier qui doit disposer d’une stratégie de rétention appliquée. Au sein de l’étiquette de rétention, vous pouvez spécifier :

- Un ensemble de descriptifs pour les fichiers (par exemple, par département d’entreprise, catégorie de fichier ou règlement).

- Les paramètres de rétention pour les fichiers qui ont l’étiquette de rétention, tels que les heures de conservation et comportements après que la durée de conservation a été atteinte.

Vous pouvez également appliquer automatiquement une étiquette de rétention aux fichiers en configurant un site SharePoint Online pour appliquer une étiquette de rétention par défaut pour tous les nouveaux documents dans le site. 

Pour plus d’informations, voir[Vue d’ensemble d’étiquettes de rétention](https://docs.microsoft.com/office365/securitycompliance/labels).

### <a name="sensitivity-labels"></a>Étiquettes de niveau de confidentialité

Une partie de protection et implémentation de sécurité pour des types de documents ou des documents avec contenu spécifique consiste en les marquer d’une étiquette de sorte que la sécurité supplémentaire puisse être appliquée. Avec des étiquettes de niveau de confidentialité dans Microsoft 365, vous pouvez :

- Appliquer des paramètres de protection comme le chiffrement, autorisations ou ajouter un filigrane.

- Empêcher les contenus sensibles de sortir de votre organisation sur les appareils exécutant Windows, à l’aide de la protection de point de terminaison dans Microsoft Intune. 

- Utiliser la protection de point de terminaison Protection des Informations Windows (WIP) permet d’empêcher que le contenu soit copié à une application tierce, par exemple, Twitter ou Gmail, ou copié sur un stockage amovible, par exemple, un lecteur USB.

- Utiliser Microsoft Cloud App Security pour protéger le contenu dans les services tiers et les applications tierces. 

- Classifier du contenu sans utiliser les paramètres de protection.

Si vous utilisez des étiquettes de niveau de confidentialité, vous devez configurer une étiquette pour chaque niveau de protection d’information et de sécurité. Par exemple, créer trois étiquettes sensibilité pour :

- Baseline

- Sensible

- Hautement réglementé

Pour plus d’informations, voir[Vue d’ensemble des étiquettes de sensibilité](https://docs.microsoft.com/office365/securitycompliance/sensitivity-labels).

### <a name="azure-information-protection-labels-and-protection"></a>Étiquettes Azure Information Protection et protection

Vous pouvez utiliser des étiquettes Azure Information Protection pour classifier et également protéger les messages électroniques et documents de votre organisation. Ces étiquettes peuvent s’appliquer à des documents qui sont stockés en dehors de Microsoft 365. Ces opérations peuvent être effectuées automatiquement par les administrateurs qui définissent des règles et des conditions ou manuellement par les utilisateurs, ou une combinaison où les utilisateurs peuvent recevoir des recommandations.

Pour planifier et déployer des étiquettes Azure Information Protection, procédez comme suit :

1. Revoyez la [configuration requise pour Azure Information Protection](https://docs.microsoft.com/information-protection/get-started/requirements).
2. Suivez la [feuille de route de déploiement pour la classification, l’utilisation d’étiquettes et la protection](https://docs.microsoft.com/information-protection/plan-design/deployment-roadmap#deployment-roadmap-for-classification-labeling-and-protection).

Pour plus d’informations, reportez-vous à la [bibliothèque de documentation Azure Information Protection](https://docs.microsoft.com/information-protection/).

Fonctionnement des étiquettes de niveau de confidentialité avec les étiquettes Protection Information Existante Azure. Par exemple, vous pouvez maintenir vos étiquettes Azure Information Protection existantes et les étiquettes qui sont appliquées aux documents et courriers électroniques.

Si vous avez des étiquettes sensibilité et Azure Information Protection, vous devez [migrer vos étiquettes Azure Information Protection aux étiquettes sensibilité](https://docs.microsoft.com/office365/securitycompliance/sensitivity-labels#how-sensitivity-labels-work-with-existing-azure-information-protection-labels).

## <a name="example-classification-for-gdpr"></a>Exemple : Classification pour RGPD

Pour consulter un exemple de système de classification qui comprend des données personnelles pour le RGPD, reportez-vous à la rubrique [Création d’un schéma de classification pour les données personnelles](https://docs.microsoft.com/office365/enterprise/architect-a-classification-schema-for-personal-data).

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide de Laboratoire de Test : Classification des données](data-classification-microsoft-365-enterprise-dev-test-environment.md) |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step3) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step3.png)|[Configurez une sécurité accrue pour Office 365](infoprotect-configure-increased-security-office-365.md)|

