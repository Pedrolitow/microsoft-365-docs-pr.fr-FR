---
title: Utilisation de modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser et gérer des modèles pour générer des évaluations dans le Gestionnaire de conformité Microsoft Purview. Créez et modifiez des modèles à l’aide d’un fichier Excel mis en forme.
ms.openlocfilehash: 009b2d742ab135abcde7c3ab73f9ec15c05c8f29
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972780"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>En savoir plus sur les modèles d’évaluation dans le Gestionnaire de conformité

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Dans cet article :** Découvrez **comment fonctionnent les modèles** et **comment les gérer à** partir de votre page modèles d’évaluation. Obtenez des instructions pour **créer** des modèles, **étendre** et **modifier** des modèles existants, **mettre en forme vos données de modèle avec Excel** et exporter des **rapports** de modèles.

> [!IMPORTANT]
> Les modèles d’évaluation disponibles pour votre organisation dépendent de votre contrat de licence. [Passez en revue les détails](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="templates-overview"></a>Vue d’ensemble des modèles

Un modèle est un framework de contrôles permettant de créer une évaluation dans le Gestionnaire de conformité. Notre ensemble complet de modèles peut aider votre organisation à se conformer aux exigences nationales, régionales et sectorielles régissant la collecte et l’utilisation des données.

## <a name="template-versions-microsoft-and-universal"></a>Versions de modèle : Microsoft et universel

Nous faisons référence à des modèles du même nom que leur certification ou réglementation sous-jacente, comme le modèle RGPD de l’UE et le modèle ISO/CEI 27701:2019.

Le Gestionnaire de conformité peut être utilisé pour évaluer différents types de produits. Tous les modèles en dehors de la base de référence sont fournis dans au moins une version qui s’applique à un produit prédéfini, tel que Microsoft 365, et une version universelle qui peut être adaptée à d’autres produits. Les évaluations à partir de modèles universels sont plus généralisées, mais offrent une polyvalence accrue, car elles peuvent vous aider à suivre facilement la conformité de votre organisation sur plusieurs produits.

Notez que les clients us government Community (Cloud de la communauté du secteur public) Moderate, Cloud de la communauté du secteur public High et Department of Defense (DoD) ne peuvent actuellement pas utiliser de modèles universels.

## <a name="template-availability-and-licensing"></a>Disponibilité et gestion des licences des modèles

Il existe deux catégories de modèles dans le Gestionnaire de conformité : inclus et Premium.

1. **Les modèles inclus sont accordés** par votre licence gestionnaire de conformité et couvrent les principales réglementations et exigences. Pour en savoir plus sur les modèles disponibles dans le cadre de votre contrat de licence, consultez [les détails des licences](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. **Premium modèles** pour couvrir des besoins et des scénarios supplémentaires peuvent être obtenus en achetant des licences de modèle.

Lorsque vous commencez à créer des évaluations, le Gestionnaire de conformité effectue le suivi du nombre de modèles actifs afin de pouvoir surveiller votre utilisation. Pour en savoir plus, consultez [modèles actifs et inactifs](compliance-manager-templates.md#active-and-inactive-templates).

Affichez la [liste complète des modèles disponibles](compliance-manager-templates-list.md) dans le Gestionnaire de conformité.

### <a name="purchase-premium-template-licenses"></a>Acheter des licences de modèle Premium

Les licences de modèle peuvent être obtenues par une ou plusieurs de ces méthodes, en fonction de votre contrat de licence du Gestionnaire de conformité. Une fois votre achat finalisé, les modèles doivent être disponibles dans votre locataire dans les 48 heures.

**Commercial et Cloud de la communauté du secteur public Modéré**

Les comptes commerciaux et Cloud de la communauté du secteur public Modérés peuvent acheter des licences de modèle dans le Centre d’administration ([en savoir plus sur les abonnements, les licences et la facturation](/microsoft-365/commerce/)). Sélectionnez la quantité de licences que vous souhaitez acheter et votre plan de paiement.

Liens d’achat :

- [Commerciale](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [Cloud de la communauté du secteur public modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Vous pouvez également acquérir des licences par le biais de votre participation au [programme fournisseur de solutions Cloud](https://partner.microsoft.com/membership/cloud-solution-provider) ou [à la gestion des licences en volume](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**Cloud de la communauté du secteur public comptes High et DOD**

Cloud de la communauté du secteur public comptes High et DOD doivent acheter des licences de modèle par le biais [de licences en volume](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>Essayer des modèles Premium

Pour tester des modèles Premium avant d’effectuer un achat, vous pouvez également acquérir des versions d’évaluation des licences. Les licences d’évaluation sont valables pour jusqu’à 25 modèles pendant 90 jours. Une fois que vous avez obtenu votre licence d’évaluation, les modèles doivent être disponibles dans votre locataire dans les 48 heures.

Si votre organisation dispose d’une licence commerciale pour le Gestionnaire de conformité, vous pouvez apprendre à démarrer votre version d’évaluation à [l’adresse About the free trial for Microsoft Purview Compliance Manager Premium assessments](compliance-easy-trials-compliance-manager-assessments.md).

Si votre organisation est sous licence Cloud de la communauté du secteur public ou DOD, choisissez le lien d’évaluation approprié pour votre organisation :

- [Cloud de la communauté du secteur public modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC High](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Modèles actifs et inactifs

Les modèles affichent un état d’activation actif ou inactif :

- Un modèle est considéré comme **actif** une fois que vous avez créé une évaluation à partir de ce modèle.
- Un modèle est considéré comme **inactif** si votre organisation ne l’utilise pas pour une évaluation.

Si vous liez des évaluations à un modèle Premium acheté, ce modèle sera actif pendant un an. Votre achat sera automatiquement renouvelé, sauf si vous annulez.

#### <a name="activated-templates-counter"></a>Compteur de modèles activé

Votre page d’évaluation et la page des modèles d’évaluation disposent d’un compteur **de modèles activé** en haut. Le compteur affiche le nombre de modèles utilisés en dehors du nombre que vous pouvez utiliser en fonction de votre contrat de licence. L’utilisation du modèle est comptabilisée au niveau de la certification.

Par exemple, si votre compteur affiche 2/5, cela signifie que votre organisation a activé 2 modèles sur les 5 disponibles à utiliser.

Si votre compteur affiche 5/2, cela indique que votre organisation dépasse ses limites et doit acheter 3 des modèles Premium utilisés.

Les modèles d’un produit prédéfini, tels que Microsoft 365, ont une licence conjointe avec les versions universelles du même modèle. Cela vous permet d’utiliser la même certification sous-jacente sur plusieurs produits. L’utilisation de l’une ou des deux versions du même modèle ne comptera qu’un seul modèle activé.

Pour plus d’informations, consultez les [instructions relatives aux licences du Gestionnaire de conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>Afficher et gérer des modèles

La page Modèles d’évaluation dans le Gestionnaire de conformité affiche une liste de modèles et des détails clés à leur sujet. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle basé sur la certification, l’étendue du produit, le pays, l’industrie, qui l’a créé et si le modèle est activé pour la création de l’évaluation.

Sélectionnez un modèle dans sa ligne pour afficher sa page de détails. Cette page contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. Dans cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

## <a name="create-an-assessment-template"></a>Créer un modèle d’évaluation

Pour créer votre propre modèle pour les évaluations personnalisées dans le Gestionnaire de conformité, vous allez utiliser une feuille de calcul Excel spécialement mise en forme pour assembler les données de contrôle nécessaires. Une fois la feuille de calcul terminée, vous l’importerez dans le Gestionnaire de conformité. Pour plus d’informations, consultez [Créer un modèle d’évaluation](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>Modifier un modèle d’évaluation

Lorsque vous travaillez avec des évaluations dans le Gestionnaire de conformité, vous pouvez modifier un modèle d’évaluation que vous avez créé. Le processus est similaire au processus de création de modèle, en ce que vous allez charger un fichier Excel mis en forme avec vos données de modèle. Pour en savoir plus sur la façon d’apporter des modifications et la conservation des données que vous souhaitez toujours conserver, consultez [Modifier un modèle d’évaluation](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>Étendre un modèle d’évaluation

Le Gestionnaire de conformité offre la possibilité d’ajouter vos propres contrôles et actions d’amélioration à un modèle existant. Ce processus est appelé extension d’un modèle. Pour étendre un modèle, vous allez utiliser des instructions spéciales pour ajouter des données de modèle, selon que vous étendez des modèles d’évaluation Microsoft ou des modèles d’évaluation universels. Pour plus d’informations, consultez [Étendre un modèle d’évaluation](compliance-manager-templates-extend.md).

## <a name="format-assessment-template-data-in-excel"></a>Mettre en forme les données du modèle d’évaluation dans Excel

Lorsque vous créez, modifiez ou étendez des modèles d’évaluation dans le Gestionnaire de conformité, vous travaillez avec Excel feuilles de calcul qui utilisent un format et un schéma spécifiques. Ces spécifications doivent être suivies pour que les fichiers soient importés correctement. Pour en savoir plus, consultez [Formater les données du modèle d’évaluation dans Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>Exporter un modèle

Vous pouvez exporter un fichier Excel qui contient toutes les données d’un modèle. Vous devez exporter un modèle pour le modifier, car il s’agit du fichier Excel que vous modifiez et chargez dans le [processus de modification](compliance-manager-templates-modify.md). Vous pouvez également exporter un modèle pour référence si vous souhaitez utiliser des données à partir de celui-ci lors de la construction d’un nouveau modèle personnalisé.

Pour exporter votre modèle, accédez à la page des détails de votre modèle et sélectionnez le bouton **Exporter vers Excel**.

Notez que lors de l’exportation d’un modèle que vous avez étendu à partir d’un modèle gestionnaire de conformité, le fichier exporté contient uniquement les attributs que vous avez ajoutés au modèle. Le fichier exporté n’inclut pas les données de modèle d’origine fournies par Microsoft. Pour obtenir un tel rapport, consultez les instructions [d’exportation d’un rapport d’évaluation](compliance-manager-assessments.md#export-an-assessment-report).
