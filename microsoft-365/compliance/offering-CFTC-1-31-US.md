---
title: 1.31 (c-d) de la règle de négociation des perspectives de marchandises (CFTC) pour les États-Unis
description: Une entreprise d’évaluation indépendante a validé que Azure et Office 365 peuvent aider les entreprises financières à respecter la règle CFTC 1,31 enregistrer les besoins en matière de conservation et de stockage non modifiable.
keywords: Offres pour la conformité Microsoft 365
localization_priority: None
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: M365-security-compliance
hideEdit: true
ms.openlocfilehash: db357418b87e98ee0f649e48b1c00f9073d5e5de
ms.sourcegitcommit: eb0f255baff1f2856621cbc64a3f34a04be37be3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "39860064"
---
# <a name="commodity-futures-trading-commission-cftc-rule-131c-d-united-states"></a>1.31 (c-d) de la règle de négociation des perspectives de marchandises (CFTC) pour les États-Unis

## <a name="about-cftc-rule-13c-d"></a>À propos de la règle CFTC 1.3 (c-d)

La [Commission de négociation futures des produits](https://www.cftc.gov/) de la CFTC, une Agence américaine fédérale américaine, réglemente les futures marchés de produits et options et, plus récemment, le marché des swaps.  
  
La règle CFTC de longue durée 1,31 définit les exigences de rétention des enregistrements établies par la règle 17A -4 (f). En outre, il spécifie que les enregistrements électroniques doivent être conservés pendant cinq ans et que les originaux restent « facilement accessibles » pendant les deux premières années et mis à disposition pour inspection par la Commission ou le ministère américain de la justice pendant toute la durée période de rétention.  
  
Dans 2017, le [CFTC a modifié sa règle](https://www.cftc.gov/sites/default/files/idc/groups/public/@lrfederalregister/documents/file/2017-11014a.pdf), modifiant et modernisant son règlement d’archivage pour adopter des normes moins normatives et fondées sur des principes qui offrent une plus grande flexibilité dans la façon dont les enregistrements peuvent être maintenus. Cela rend la règle plus indépendante de la technologie, ce qui permet aux entités réglementées de choisir la technologie la mieux adaptée à leur activité tout en conservant les protections qui « garantissent la fiabilité du processus d’archivage ». La règle révisée supprime la nécessité pour les organisations de maintenir les enregistrements originaux pendant deux ans, mais conserve la période de maintenance de cinq ans, ce qui harmonise les pratiques pour les entreprises réglementées par les CFTC et la SEC.

## <a name="microsoft-and-cftc-rule-131c-d"></a>1.31 de règles Microsoft et CFTC (c-d)

Les clients des services financiers, représentant l’un des secteurs les plus réglementés du monde, sont soumis à des dispositions complexes telles que la rétention des transactions financières et des communications associées dans un État non effaçable et non modifiable. Il s’agit de la règle 1,31 de la Commission de négociation à venir (CFTC), qui stipule des exigences rigoureuses pour les entités réglementées qui choisissent de conserver des livres et des enregistrements sur des supports de stockage électroniques. Les enregistrements stockés doivent être inviolable sans possibilité de les modifier ou de les supprimer jusqu’à la fin de la période de rétention désignée. Microsoft Azure inmutable le stockage des objets BLOB avec verrou de stratégie et Microsoft Office 365 avec verrouillage de la conservation peuvent aider les établissements financiers à répondre aux exigences de stockage de la règle CFTC (c-d).

### <a name="microsoft-azure"></a>Microsoft Azure

Pour évaluer la conformité Azure à l’aide de la règle CFTC 1.31 (c-d), Microsoft a conservé une entreprise d’évaluation indépendante spécialisée dans la gestion des enregistrements et la gouvernance des informations, Cohasset Associates. Dans le rapport obtenu, [CFTC 1,31 (c) – (d) évaluation de la conformité : Microsoft Azure Storage](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=19b08fd4-d276-43e8-9461-715981d0ea20&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_GRC_Assessment_Reports), Cohasset validée que le [stockage d’objets BLOB Azure inaltérables](https://docs.microsoft.com/azure/storage/blobs/storage-blob-immutable-storage) avec l’option de verrouillage de stratégie, lorsqu’il est utilisé pour conserver les objets BLOB basés sur l’heure dans un format non effaçable et non réinscriptible (Worm), répond aux exigences de la règle CFTC. La modification, l’écrasement ou la suppression de chaque objet BLOB (enregistrement) est protégée jusqu’à ce que la période de rétention requise ait expiré et que toutes les suspensions juridiques associées aient été publiées. Les fournisseurs de logiciels et les partenaires avec des charges de travail sensibles peuvent désormais compter sur le stockage d’objets BLOB Azure inaltérables en tant que solution Cloud de magasin unique pour la rétention des enregistrements. Les établissements financiers peuvent désormais créer leurs propres applications en tirant parti de ces fonctionnalités tout en restant conformes.

### <a name="microsoft-office-365"></a>Microsoft Office 365

Pour évaluer la conformité d’Office 365 avec la règle CFTC 1.31 (c-d), Microsoft a engagé un cabinet d’avocats indépendant spécialisé dans la réglementation, Covington & Burling, LLP. Dans le rapport obtenu, l' [archivage dans Microsoft Office 365, la rétention des données et la réglementation 17A -4](https://go.microsoft.com/fwlink/?linkid=830440), Covington validée que [Office 365 avec verrouillage de conservation](https://docs.microsoft.com/office365/securitycompliance/retention-policies#locking-a-retention-policy) inclut des fonctionnalités d’archivage permettant aux clients réglementés de stocker les données d’une manière qui les aide à respecter les exigences CFTC pour la rétention des enregistrements.

L’archivage dans Office 365 permet de conserver une large gamme de données, notamment la messagerie électronique, la messagerie vocale, les documents partagés, les messages instantanés et les données tierces. En particulier, l’archivage dans Office 365 permet aux clients de définir des stratégies de rétention de messagerie globales ou granulaires pour stocker des données pendant une période définie et au-delà dans un format non réinscriptible et non effaçable.

## <a name="microsoft-in-scope-cloud-services"></a>Services Cloud Microsoft dans le périmètre

- [Azure](https://aka.ms/AzureCompliance)
- [Office 365](https://aka.ms/o365-compliance-framework)

## <a name="audits-reports-and-certificates"></a>Audits, rapports et certificats

[Azure & CFTC règle 1,31 — SEC 17A -4 (f) & CFTC 1.31 (c) évaluation de la conformité d’Azure Storage

[Office 365 & règle CFTC 1,31 — archivage dans Office 365, rétention des données et conformité de la règle SEC 17A -4

## <a name="how-to-implement"></a>Modalités de mise en œuvre

- [Réglementation des services financiers](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5b483567-00b0-4d86-96ae-ee887dadb61c&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_Compliance_Guides): plan de conformité des principes de réglementation des clés américaines pour le Cloud Computing et Microsoft Online Services.
- [Guide d'évaluation des risques et de conformité](https://aka.ms/RiskGovernanceGuide): créez un modèle de gouvernance pour l'évaluation des risques des services de cloud computing Microsoft et la notification aux autorités de réglementation.
- [Cas d'utilisation financière](https://docs.microsoft.com/azure/industry/financial/) : utilisez des aperçus de cas, des didacticiels et d'autres ressources pour créer des solutions Azure pour services financiers.

## <a name="resources"></a>Ressources

- [Programme de mise en conformité destiné au secteur des services financiers Microsoft](https://aka.ms/FSCP-Print)
- [Services commerciaux cloud computing et services financiers Microsoft](https://www.microsoft.com/trustcenter/cloudservices/financialservices)
- [Conformité des services financiers dans Azure](https://azure.microsoft.com/resources/videos/azurecon-2015-financial-services-compliance-in-azure/)
- [Outil d’évaluation des risques dans le Cloud Azure Financial Services](https://aka.ms/FFIEC-CSDT)
- [Stratégies de rétention de Microsoft Office 365](https://docs.microsoft.com/office365/securitycompliance/retention-policies)
- [Blog Microsoft Financial Services](https://techcommunity.microsoft.com/t5/Financial-Services-Blog/bg-p/FinancialServicesBlog)
- [Conformité sur le site Microsoft Trust Center](https://www.microsoft.com/trust-center/compliance/compliance-overview)

## <a name="download-the-offering-backgrounder"></a>Téléchargez la fiche d'information sur l'offre

Avez-vous besoin du document d’information pour cette offre ? Téléchargez le fichier [PDF](https://download.microsoft.com/download/9/A/9/9A9847FE-164A-4321-8112-50719D9EA877/CFTC1.31-Compliance.pdf).
