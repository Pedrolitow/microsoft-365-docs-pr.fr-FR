---
title: Utiliser des modèles d’évaluation dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
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
description: Comprendre comment utiliser et gérer des modèles pour la création d’évaluations dans le Gestionnaire de conformité Microsoft. Créez et modifiez des modèles à l’aide d’un fichier Excel formaté.
ms.openlocfilehash: 74b896f6c0fdd625cf50cc04a31fa79d48dc3a4e
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60587680"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>En savoir plus sur les modèles d’évaluation dans le Gestionnaire de conformité

**Dans cet article :** Comprendre **le fonctionnement des modèles** et comment les **gérer** à partir de votre page de modèles d’évaluation. Obtenez des  instructions pour créer de  nouveaux modèles,  étendre et modifier des modèles existants, mettre en forme vos données de modèle avec **Excel** et exporter des rapports de **modèles.**

> [!IMPORTANT]
> Les modèles d’évaluation disponibles pour votre organisation dépendent de votre contrat de licence. [Examinez les détails.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

## <a name="templates-overview"></a>Vue d’ensemble des modèles

Un modèle est une infrastructure de contrôles permettant de créer une évaluation dans le Gestionnaire de conformité. Notre ensemble complet de modèles peut aider votre organisation à se conformer aux exigences nationales, régionales et propres au secteur qui régissent la collecte et l’utilisation des données.

Nous faisons référence à des modèles du même nom que leur certification ou réglementation sous-jacente, comme le modèle R GDPR de l’UE et le modèle ISO/IEC 27701:2019. Étant donné que le gestionnaire de conformité peut être utilisé pour évaluer différents types de produits, chaque modèle est livré en deux versions : une qui s’applique à Microsoft 365 et une version universelle qui peut être adaptée à votre produit choisi.

Notez que les clients modérés, Cloud de la communauté du secteur public élevés et du département de la Défense (DoD) du gouvernement des États-Unis Community (Cloud de la communauté du secteur public) peuvent actuellement utiliser les versions du modèle Microsoft 365, mais pas universels.

## <a name="template-availability-and-licensing"></a>Disponibilité et gestion des licences des modèles

Il existe deux catégories de modèles dans le Gestionnaire de conformité : incluse et premium.

1. **Les modèles inclus sont accordés** par votre licence du Gestionnaire de conformité et couvrent les principales réglementations et exigences. Pour en savoir plus sur les modèles disponibles dans le cadre de votre contrat de licence, consultez les [détails de la gestion des licences.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)
2. **Premium modèles supplémentaires** pour répondre à d’autres besoins et scénarios peuvent être obtenus par l’achat de licences de modèles.

Lorsque vous commencez à créer des évaluations, le Gestionnaire de conformité suit le nombre de modèles actifs afin de pouvoir surveiller votre utilisation. Pour en savoir plus, [consultez les modèles actifs et inactifs.](compliance-manager-templates.md#active-and-inactive-templates)

Affichez [la liste complète des modèles disponibles](compliance-manager-templates-list.md) dans le Gestionnaire de conformité.

### <a name="purchase-premium-template-licenses"></a>Acheter des licences de modèle premium

Les licences de modèle peuvent être obtenues par une ou plusieurs de ces méthodes, en fonction de votre contrat de licence du Gestionnaire de conformité. Une fois votre achat finalisé, les modèles doivent être disponibles dans votre client dans les 48 heures.

**Commercial et Cloud de la communauté du secteur public Modéré**

Les comptes commerciaux et Cloud de la communauté du secteur public modérés peuvent acheter des licences de modèles dans le Centre d’administration (en savoir plus sur les[abonnements, les licences et la facturation).](/microsoft-365/commerce/) Sélectionnez le nombre de licences que vous souhaitez acheter et votre plan de paiement.

Liens d’achat :

- [Commerciale](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [Cloud de la communauté du secteur public Modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

Vous pouvez également acquérir des licences par le biais de votre participation au [programme fournisseur de solutions Cloud licences](https://partner.microsoft.com/membership/cloud-solution-provider) [en volume ou en volume.](https://www.microsoft.com/licensing/licensing-programs/licensing-programs)

**Cloud de la communauté du secteur public Comptes DOD et élevés**

Cloud de la communauté du secteur public Les comptes DOD et élevés doivent acheter des licences de modèles par le biais [de licences en volume.](https://www.microsoft.com/licensing/licensing-programs/licensing-programs)

### <a name="try-out-premium-templates"></a>Essayer des modèles Premium

Pour tester des modèles premium avant d’effectuer un achat, vous pouvez également acquérir des versions d’essai des licences. Les licences d’essai sont valides pour 25 modèles au plus pendant 90 jours. Une fois que vous avez obtenu votre licence d’essai, les modèles doivent être disponibles dans votre client dans les 48 heures.

Pour démarrer une version d’essai, choisissez le lien approprié pour votre organisation :

- [Commerciale](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/e320704d-b7c9-4012-b6a6-0a2679790360)
- [Cloud de la communauté du secteur public Modéré](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC High](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [DOD](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>Modèles actifs et inactifs

Les modèles affichent un état d’activation comme actif ou inactif :

- Un modèle est considéré **comme actif** une fois que vous avez créé une évaluation à partir de ce modèle.
- Un modèle est considéré **comme inactif** si votre organisation ne l’utilise pas pour une évaluation.

Si vous liez des évaluations à un modèle Premium acheté, ce modèle sera actif pendant un an. Votre achat sera renouvelé automatiquement, sauf si vous annulez.

#### <a name="activated-templates-counter"></a>Compteur de modèles activés

Votre page d’évaluation et votre page de modèles d’évaluation ont un compteur de **modèles** activé dans la partie supérieure. Le compteur affiche le nombre de modèles utilisés en dehors du nombre que vous êtes éligible pour utiliser conformément à votre contrat de licence. L’utilisation des modèles est comptabilisée au niveau de certification.

Par exemple, si votre compteur affiche 2/5, cela signifie que votre organisation a activé 2 modèles sur les 5 disponibles.

Si votre compteur affiche le 5/2, cela indique que votre organisation dépasse ses limites et doit acheter 3 des modèles Premium utilisés.

Microsoft 365 versions universelles et universelles des modèles ont une licence conjointe, afin que vous pouvez utiliser la même certification sous-jacente sur plusieurs produits. L’utilisation de l’une ou des deux versions du même modèle ne compte qu’en tant que modèle activé.

Pour plus d’informations, consultez les conseils de gestion [des licences du Gestionnaire de conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="view-and-manage-templates"></a>Afficher et gérer des modèles

La page modèles d’évaluation dans le Gestionnaire de conformité affiche une liste de modèles et des détails clés les concernant. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle basé sur la certification, l’étendue du produit, le pays, l’industrie, qui l’a créé et si le modèle est activé pour la création d’évaluation.

Sélectionnez un modèle dans sa ligne pour faire monter sa page de détails. Cette page contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

## <a name="create-an-assessment-template"></a>Créer un modèle d’évaluation

Pour créer votre propre modèle pour les évaluations personnalisées dans le Gestionnaire de conformité, vous utiliserez une feuille de calcul spécialement mise en forme Excel pour assembler les données de contrôle nécessaires. Après avoir terminé la feuille de calcul, vous l’importez dans le Gestionnaire de conformité. Pour plus d’informations, voir [Créer un modèle d’évaluation.](compliance-manager-templates-create.md)

## <a name="modify-an-assessment-template"></a>Modifier un modèle d’évaluation

Lorsque vous travaillez avec des évaluations dans le Gestionnaire de conformité, vous pouvez modifier un modèle d’évaluation que vous avez créé. Le processus est similaire au processus de création de modèle dans la façon dont vous allez télécharger un fichier Excel formaté avec vos données de modèle. Pour en savoir plus sur la façon d’apporter des modifications et de conserver les données que vous souhaitez conserver, voir [Modifier un modèle d’évaluation.](compliance-manager-templates-modify.md)

## <a name="extend-an-assessment-template"></a>Étendre un modèle d’évaluation

Le Gestionnaire de conformité offre la possibilité d’ajouter vos propres contrôles et actions d’amélioration à un modèle existant. Ce processus est appelé extension d’un modèle. Pour étendre un modèle, vous utiliserez des instructions spéciales pour l’ajout de données de modèle, selon que vous étendez des modèles d’évaluation Microsoft 365 ou universels. Pour plus d’informations, voir [Étendre un modèle d’évaluation.](compliance-manager-templates-extend.md)

## <a name="format-assessment-template-data-in-excel"></a>Formater les données du modèle d’évaluation Excel

Lorsque vous créez, modifiez ou étendez des modèles d’évaluation dans le Gestionnaire de conformité, vous utiliserez des feuilles de calcul Excel qui utilisent un format et un schéma spécifiques. Ces spécifications doivent être suivies pour que les fichiers soient importés correctement. Pour en savoir plus, consultez les [données du modèle d’évaluation de](compliance-manager-templates-format-excel.md)format dans Excel .

## <a name="export-a-template"></a>Exporter un modèle

Vous pouvez exporter un Excel qui contient toutes les données d’un modèle. Vous devez exporter un modèle pour le modifier, car il s’agit du fichier Excel que vous modifiez et chargez dans le processus [de modification.](compliance-manager-templates-modify.md) Vous pouvez également exporter un modèle pour référence si vous souhaitez utiliser des données à partir de ce modèle lors de la construction d’un nouveau modèle personnalisé.

Pour exporter votre modèle, go to your template details page and select the **Export to Excel** button.

Notez que lors de l’exportation d’un modèle que vous avez étendu à partir d’un modèle gestionnaire de conformité, le fichier exporté contient uniquement les attributs que vous avez ajoutés au modèle. Le fichier exporté n’inclut pas les données de modèle d’origine fournies par Microsoft. Pour obtenir un tel rapport, consultez les instructions d’exportation [d’un rapport d’évaluation.](compliance-manager-assessments.md#export-an-assessment-report)