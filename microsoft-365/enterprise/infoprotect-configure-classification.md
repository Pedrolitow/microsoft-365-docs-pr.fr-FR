---
title: 'Étape 2 : Configurer la classification pour votre environnement'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/19/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez différentes méthodes pour classer les données de votre organisation.
ms.openlocfilehash: bee0885eb3f8899560532895d1558723b281ab02
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867037"
---
# <a name="step-2-configure-classification-for-your-environment"></a>Étape 2 : Configurer la classification pour votre environnement

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Dans cette étape, vous travaillez avec vos équipes juridiques et de conformité pour définir un système de classification pour les données de votre organisation.

## <a name="microsoft-classifications"></a>Classifications de Microsoft

Microsoft 365 inclut trois types de classification :

- Types d’informations sensibles pour Office 365
- Étiquettes Office 365
- Étiquettes Azure Information Protection et protection

### <a name="sensitive-information-types-for-office-365"></a>Types d’informations sensibles pour Office 365

Les types d’informations sensibles pour Office 365 définissent la façon dont les processus automatisés tels que la recherche reconnaissent des types d’informations spécifiques (numéros de service de santé et numéros de carte de crédit, par exemple). Les types d’informations sensibles permettent de rechercher des données sensibles et d’appliquer des stratégies et des règles de protection contre la perte de données afin de protéger ces données. Pour plus d’informations, reportez-vous à la rubrique [Vue d’ensemble des stratégies de protection contre la perte de données](https://support.office.com/article/overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e). Par exemple, les types d’informations sensibles sont particulièrement utiles pour la conformité aux exigences de réglementation (pour le RGPD, par exemple).

### <a name="office-365-labels"></a>Étiquettes Office 365
Vous pouvez utiliser des étiquettes Office 365 pour des données personnelles ou pour des fichiers secrets et hautement réglementés stockés dans SharePoint Online et OneDrive Entreprise. Pour plus d’informations, notamment sur leur création, reportez-vous à la rubrique [Vue d’ensemble des étiquettes](https://support.office.com/article/overview-of-labels-af398293-c69d-465e-a249-d74561552d30).

Si vous décidez d’utiliser des étiquettes Office 365, vous devez en configurer au moins une pour chaque niveau de protection. Par exemple, créez trois étiquettes pour :

- Baseline
- Sensible
- Hautement réglementé

### <a name="azure-information-protection-labels-and-protection"></a>Étiquettes Azure Information Protection et protection

Vous pouvez utiliser des étiquettes Azure Information Protection pour classer et éventuellement protéger, les messages électroniques et documents de votre organisation. Ces étiquettes peuvent s’appliquer à des documents stockés en dehors d’Office 365. Ces étiquettes peuvent être appliquées automatiquement par les administrateurs qui définissent les règles et conditions, manuellement par les utilisateurs ou une combinaison des deux lorsque les utilisateurs reçoivent des recommandations.

Pour planifier et déployer des étiquettes Azure Information Protection, procédez comme suit :

1. Revoyez la [configuration requise pour Azure Information Protection](https://docs.microsoft.com/information-protection/get-started/requirements).
2. Suivez la [feuille de route de déploiement pour la classification, l’utilisation d’étiquettes et la protection](https://docs.microsoft.com/information-protection/plan-design/deployment-roadmap#deployment-roadmap-for-classification-labeling-and-protection).

Pour plus d’informations, reportez-vous à la [bibliothèque de documentation Azure Information Protection](https://docs.microsoft.com/information-protection/).

## <a name="classification-for-gdpr"></a>Classification pour le RGPD

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

