---
title: Norme de sécurité des données (DSS) d’industrie de carte de paiement (PCI)
description: Azure, SharePoint Online et OneDrive Entreprise sont conformes aux normes de sécurité des données de carte de paiement niveau 1 version 3.2.
keywords: Offres pour la conformité Microsoft 365
localization_priority: Priority
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: M365-security-compliance
hideEdit: true
titleSuffix: Microsoft Compliance
ms.openlocfilehash: cb4d1a4c4632763506fd2d3b05431acb9233f744
ms.sourcegitcommit: d333d82fd5e4f3265e8b9372094e85875bee6fe5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071962"
---
# <a name="payment-card-industry-pci-data-security-standard-dss"></a>Norme de sécurité des données (DSS) d’industrie de carte de paiement (PCI)

## <a name="pci-dss-overview"></a>Présentation du PCI DSS

Les normes de sécurité des données (DSS) de l’industrie des cartes de paiement (PCI) sont une norme mondiale de sécurité des informations conçue pour prévenir la fraude grâce à un contrôle accru des données des cartes de crédit. Toutes les organisations doivent respecter les normes PCI DSS si elles acceptent les cartes de paiement des cinq principales marques de cartes de crédit : Visa, MasterCard, American Express, Discover et le Japan Credit Bureau (JCB). Les organisations doivent se conformer à la norme PCI DSS si elles stockent, traitent ou transmettent des données de paiement et de titulaire de carte.

## <a name="microsoft-and-pci-dss"></a>Microsoft et la norme PCI DSS

Microsoft a effectué une évaluation PCI DSS annuelle à l’aide d’un évaluateur de sécurité qualifié (QSA) agréé. Les auditeurs ont examiné les environnements Microsoft Azure, Microsoft OneDrive Entreprise et Microsoft SharePoint Online, ce qui incluent la validation de l’infrastructure, le développement, les opérations, la gestion, le support et les services dans le champ d’application. La norme PCI DSS désigne quatre niveaux de conformité en fonction du volume des transactions. Azure, OneDrive Entreprise et SharePoint Online sont certifiés conformes à la version 3.2 de la norme PCI DSS au niveau 1 des fournisseurs de services (le plus grand volume de transactions c’est-à-dire plus de six millions par an).

L’évaluation donne lieu à une attestation de conformité (AoC), qui est à la disposition des clients, et à un rapport de conformité (RoC) émis par la QSA. La période effective de conformité commence lors de la validation de l’audit et de la réception de l’AoC de l’évaluateur et se termine un an après, à compter de la date de signature de l’AoC. 

Les clients qui souhaitent développer un environnement de titulaire de carte ou un service de traitement de carte peuvent utiliser ces validations dans de nombreuses parties sous-jacentes, réduisant ainsi les efforts et les coûts associés à l’obtention de leur propre certification PCI DSS.

Il est important de comprendre que l’état de conformité PCI DSS pour Azure, OneDrive Entreprise et SharePoint Online ne se traduit pas automatiquement par la certification PCI DSS pour les services que les clients créent ou hébergent sur ces plateformes. Les clients sont responsables de s’assurer qu’ils sont conformes aux exigences PCI DSS.

## <a name="microsoft-in-scope-cloud-services"></a>Services Cloud Microsoft concernés

- [Azure et Azure Government](https://azure.microsoft.com/global-infrastructure/government/)
- Microsoft Cloud App Security
- Service cloud Flow, soit en service autonome, soit tel qu’inclus dans un plan ou une suite Office 365 ou Dynamics 365
- Microsoft Graph
- Intune
- [Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- Service Cloud PowerApps, soit en service autonome, soit inclus dans un plan ou une suite Office 365 ou Dynamics 365
- Service Cloud Power BI soit en service autonome, soit inclus dans un plan ou une suite Office 365
- OneDrive Entreprise et SharePoint Online (États-Unis uniquement)

## <a name="audit-reports-and-certificates"></a>Rapports, audit et certificats

- [Attestation de conformité (AoC) Azure PCI DSS](https://aka.ms/azure-pci)
- [Attestation de conformité (AoC)PCI DSS OneDrive Entreprise et SharePoint Online ](https://aka.ms/spo-pci)

## <a name="get-your-pci-dss-solution-running-on-azure"></a>Faire fonctionner votre solution DSS PCI sur Azure

Créez et déployez votre solution PCI DSS dans le cloud encore plus rapidement avec le Blueprint de sécurité et de conformité Azure. Obtenez des architectures de référence, des conseils de déploiement, des mappages d’implémentation de contrôle, des scripts automatisés, etc. [Commencez à utiliser le Blueprint de sécurité et de conformité Azure](https://aka.ms/pciblueprint).

## <a name="frequently-asked-questions"></a>Foire aux questions

**Pourquoi la page de couverture de l’Attestation de Conformité (AoC) indique t-elle « juin 2018 » ?**

La date (juin 2018) indiquée sur la page de couverture correspond à la date de publication du modèle AoC. Reportez-vous à la section 2 pour connaître la date de l’évaluation.

**Pourquoi existe-t-il plusieurs attestations de conformité Azure (AoC) ?**

Le package AoC Azure possède des AoC correspondant au cloud Azure Public, Allemagne et Government. Les clients doivent utiliser l’AoC qui correspond à leur environnement Azure.  

**Quelle est la relation entre PA DSS et PCI DSS ?**

La norme de sécurité des données d’application de paiement (PA DSS) est un ensemble d’exigences conformes à la norme PCI DSS et remplace les meilleures pratiques de l’application de paiement Visa et consolide les obligations de conformité des autres émetteurs de cartes principaux. Le PA DSS aide les éditeurs de logiciels à développer des applications tierces qui stockent, traitent ou transmettent les données de paiement des titulaires de carte dans le cadre d’un processus d’autorisation ou de règlement par carte. Les détaillants doivent utiliser des applications certifiées PA DSS pour atteindre plus efficacement leur conformité PCI DSS. Le PA DSS ne s’applique pas à Azure.

**Qu’est-ce qu’un acquéreur et Azure en utilise-t-il un ?**

Un acquéreur est une banque ou une autre entité qui traite les transactions par carte de paiement. Azure n’offre pas de traitement des cartes de paiement en tant que service et n’utilise donc pas d’acquéreur.

**À quelles organisations et à quels marchands la PCI DSS s’applique-t-elle ?**

La norme PCI DSS s’applique à toutes les entreprises, quelle que soit leur taille ou leur nombre de transactions, qui acceptent, transmettent ou stockent les données des titulaires de carte. Autrement dit, si un client paie une entreprise avec une carte de crédit ou de débit, les obligations PCI DSS s’appliquent. Les entreprises sont validées par l’un des quatre niveaux en fonction du volume total des transactions réalisées sur une période de 12 mois. Le niveau 1 est destiné aux entreprises qui traitent plus de six millions de transactions par an. Le niveau 2 concerne les entreprises qui traitent entre un et six millions de transactions par an. Le niveau 3 concerne les entreprises qui traitent entre 20 000 et un million de transactions par an. Le niveau 4 concerne les entreprises qui traitent moins de 20 000 transactions par an.

**Où dois-je commencer les efforts de conformité PCI DSS de mon organisation pour une solution déployée sur Azure ?**

Les informations mises à disposition par le Conseil des normes de sécurité PCI sont idéales pour en savoir plus sur les obligations de conformité spécifiques. Le conseil publie le [Guide de référence rapide sur la norme PCI DSS](https://www.pcisecuritystandards.org/documents/PCISSC%20QRG%20August%202014%20-print.pdf) pour les commerçants et les autres personnes impliquées dans le traitement des cartes de paiement. Le guide explique comment la norme PCI DSS peut aider à protéger un environnement de transaction par carte de paiement et comment l’appliquer.

La conformité implique plusieurs facteurs, notamment l’évaluation des systèmes et des processus non hébergés sur Azure. Les exigences individuelles varient en fonction des services Azure utilisés et de la manière dont ils sont utilisés dans la solution.

**Existe-t-il des offres pour OneDrive Entreprise et SharePoint Online compatibles avec la norme PCI DSS en dehors des États-Unis ?**

Actuellement, OneDrive Entreprise et SharePoint Online sont conformes à la norme PCI-DSS uniquement aux États-Unis (US). Microsoft évaluera les exigences et les délais pour les régions en dehors des États-Unis et fournira des mises à jour si d’autres régions sont ajoutées à la feuille de route.

**Quelle est l’étendue de OneDrive Entreprise et de SharePoint Online ?**

Pour l’instant, seuls les fichiers et documents téléchargés sur OneDrive Entreprise et SharePoint Online seront conformes au standard PCI DSS.

## <a name="use-microsoft-compliance-manager-to-assess-your-risk"></a>Utilisez le Gestionnaire de conformité Microsoft pour évaluer vos risques

Le [Gestionnaire de conformité Microsoft](compliance-manager.md) est une fonctionnalité du [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md) qui vous permet de comprendre l’état de conformité de votre organisation et de prendre des mesures pour réduire les risques. Le Gestionnaire de conformité propose un modèle premium pour créer une évaluation pour ce règlement. Recherchez le modèle dans la page des **modèles d’évaluation** dans le Gestionnaire de conformité. Découvrez comment [créer des évaluations dans le Gestionnaire de conformité](compliance-manager-assessments.md).

## <a name="resources"></a>Ressources

- [Conseil normes de sécurité PCI](https://www.pcisecuritystandards.org/)
- [Norme de sécurité des données PCI](https://www.pcisecuritystandards.org/documents/PCI_DSS_v3-1.pdf)
- [Blueprint Azure PCI DSS 3.2.1](https://docs.microsoft.com/azure/governance/blueprints/samples/pci-dss-3.2.1/)
- [Guide de référence rapide PCI DSS](https://www.pcisecuritystandards.org/documents/PCISSC%20QRG%20August%202014%20-print.pdf)
- [Conformité sur le site Microsoft Trust Center](https://www.microsoft.com/trust-center/compliance/compliance-overview)
