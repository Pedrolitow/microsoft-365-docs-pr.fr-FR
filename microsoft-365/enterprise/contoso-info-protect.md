---
title: Protection des informations de Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso utilise les fonctionnalités de protection des informations de Microsoft 365 pour entreprise pour sécuriser ses biens numériques dans le Cloud.
ms.openlocfilehash: 1966fdec3de246ca54fd99ab018485b9ee817281
ms.sourcegitcommit: cd17328baa58448214487e3e68c37590ab9fd08d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48399240"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Protection des informations de Contoso Corporation

Contoso prend la protection et la sécurité de ses informations très au sérieux. Par exemple, la fuite ou la destruction de sa propriété intellectuelle comprenant les conceptions de produits et les techniques de fabrication propriétaires placerait la société dans une situation de désavantage compétitif.

Avant de migrer leurs biens numériques sensibles et les plus précieux vers le Cloud, ils ont fait en sorte que leurs exigences en matière de protection et de classification des informations étaient prises en charge et implémentées dans les services en nuage de Microsoft 365 pour les entreprises.

## <a name="contosos-data-security-classification"></a>Classification de la sécurité des données selon Contoso

Contoso a effectué une analyse de ses données et déterminé les niveaux suivants :

| Niveau 1 : ligne de base | Niveau 2 : Sensible | Niveau 3 : hautement réglementé |
|:-------|:-----|:-----|
| Les données sont chiffrées et uniquement accessibles par des utilisateurs authentifiés. <BR> <BR> Fourni pour toutes les données stockées sur site et dans le stockage et les charges de travail basées sur le Cloud. Les données sont chiffrées lorsqu’elles résident dans le service et en transit entre le service et les appareils clients. <BR><BR> Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique. | Niveau 1 avec une authentification et une protection renforcées contre la perte de données. <BR> <BR> Une authentification forte comporte une authentification multi-facteur Azure (MFA) avec validation SMS. La protection contre la perte de données permet de s’assurer que les informations sensibles ou cruciales ne circulent pas à l’extérieur de Microsoft cloud. <BR><BR> Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits. | Niveau 2 avec des niveaux de chiffrement, d’authentification et d’audit plus élevés. <BR> <BR>  Niveaux de chiffrement des données au repos et dans le cloud les plus élevés, conformes aux réglementations locales, associés à une authentification multi-facteur avec cartes à puce et fonctionnalités d’audit et d’alerte granulaires. <BR> <BR> Les données de niveau 3 concernent, par exemple, les informations d’identification personnelle des clients et des partenaires, les spécifications techniques de produits et les techniques de fabrication propriétaires.  |
||||

## <a name="contosos-information-policies"></a>Stratégies de traitement des informations de Contoso
Le tableau suivant répertorie les stratégies de traitement des informations de Contoso.


| Valeur | Access | Rétention des données | Protection des informations |
|:-------|:-----|:-----|:-----|
| Valeur commerciale faible (Niveau 1: Ligne de base) | Autoriser l’accès pour tous  | 6 mois | Utiliser le chiffrement. |
| Valeur commerciale moyenne (Niveau 2: Sensible) | Autoriser l’accès aux collaborateurs, aux sous-traitants et aux partenaires de Contoso <BR> <BR> Utiliser l’authentification multi-facteur (MFA), le chiffrement TLS (Transport Layer Security) et la gestion des applications mobiles (MAM). | 2 ans  | Utiliser les valeurs de hachage pour l’intégrité des données.  |
| Valeur commerciale élevée (Niveau 3 : hautement réglementé) | Autoriser l’accès aux cadres et aux responsables des équipes techniques et de fabrication. <BR> <BR> Système de gestion des droits (RMS) avec les appareils réseau gérés seulement.  | 7 ans  | Utiliser des signatures numériques pour le non-reniement.  |
|||||

## <a name="contosos-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Chemin d’accès de contoso à la protection des informations avec Microsoft 365 pour les entreprises

Contoso a utilisé les étapes suivantes pour préparer Microsoft 365 pour les entreprises pour leurs besoins en matière de protection des informations :

1. Identification des informations à protéger

   Contoso a réalisé un examen approfondi de ses biens numériques existants situés sur des partages de fichiers et des sites SharePoint locaux avant de classer chacun d’eux.

2. Définition des stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé la configuration requise détaillée en matière de stratégie, utilisée pour protéger les biens numériques existants lors de leur migration vers le cloud.

3. Création des étiquettes Azure Information Protection et de leurs paramètres pour différents niveaux d’informations

   Contoso a créé des étiquettes de confidentialité pour ses niveaux de données dont les étiquettes hautement réglementées incluent chiffrement, autorisations et filigranes.

4.  Migration des données des sites SharePoint locaux et des partages de fichiers vers leurs nouveaux sites SharePoint

    Les fichiers ayant migré vers les nouveaux sites SharePoint ont hérité des étiquettes de rétention par défaut attribuées au site.

5.  Formation des employés sur la façon d’utiliser les étiquettes de confidentialité pour les nouveaux documents, d’interagir avec les services informatiques Contoso lors de la création de nouveaux sites SharePoint et de constamment stocker les biens numériques sur les sites SharePoint

    Cette partie étant considérée comme la plus difficile au niveau de la transition en protection des informations pour le cloud, les services informatiques et de gestion de Contoso ont dû modifier les mauvaises habitudes de stockage d’information des employés de l’organisation pour systématiquement étiqueter leurs biens numériques dans le cloud, renoncer au partage de fichiers sur site et ne jamais utiliser les services de stockage cloud de tiers ou de clés USB.

## <a name="conditional-access-policies-for-information-protection"></a>Stratégies d’accès conditionnel régissant la protection des informations

Conjointement avec son identité et son infrastructure de gestion des appareils mobiles, et dans le cadre de son déploiement d’Exchange Online et de SharePoint, Contoso a configuré l’ensemble suivant de stratégies d’accès conditionnel qu’il a appliquées aux groupes appropriés :

- [Stratégies d’accès aux applications gérées et non gérées sur les périphériques](../security/office-365-security/identity-access-policies.md)
- [Stratégies d’accès à Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)
- [Stratégies d’accès SharePoint](../security/office-365-security/sharepoint-file-access-policies.md)

Voici le résultat des stratégies de protection des informations de Contoso.

![Stratégies d’accès conditionnel à SharePoint, à Exchange Online et aux appareils](../media/contoso-info-protect/contoso-info-protect-fig1.png)

>[!Note]
>Contoso a également configuré d’autres stratégies d’accès conditionnel pour l’identité et la connexion. Consultez l’[Identité de Contoso Corporation](contoso-identity.md#conditional-access-policies-for-identity-and-device-access).
>

Ces stratégies vous assurent que :

- Les applications sont permises et les stratégies de protection des applications définissent les applications autorisées et les actions qu’elles peuvent effectuer avec les données de votre organisation.
- les PC et les périphériques mobiles sont conformes ;
- Exchange Online utilise le chiffrement de messages Office 365 (OME) pour Exchange Online.
- SharePoint utilise des restrictions d’application imposées.
- SharePoint utilise les stratégies de contrôle d’accès pour assurer un accès réservé au navigateur et bloquer l’accès aux matériels non gérés.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contosos-data-levels"></a>Mappage de Microsoft 365 pour les fonctionnalités d’entreprise aux niveaux de données de contoso

Le tableau suivant établit une correspondance entre les niveaux de données de contoso et les fonctionnalités de protection des informations dans Microsoft 365 pour les entreprises.

| Niveau | Services Cloud Microsoft 365 | Windows 10 et Microsoft 365 Apps for enterprise | Sécurité et conformité |
|:-------|:-----|:-----|:-----|
| Niveau 1 : ligne de base  | Stratégies d’accès conditionnel à SharePoint et à Exchange Online <BR> Autorisations sur les sites SharePoint | Étiquettes de confidentialité <BR> BitLocker <BR> Protection des informations Windows | Stratégies d’accès conditionnel aux matériels et stratégies de gestion des applications mobiles |
| Niveau 2 : Sensible | Niveau 1 plus : <BR> <BR> Étiquettes de confidentialité <BR> Étiquettes de rétention Microsoft 365 sur les sites SharePoint <BR> Protection contre la perte de données pour SharePoint et Exchange Online <BR> Sites SharePoint isolés  | Niveau 1 plus : <BR> <BR> Étiquettes de sensibilité sur les biens numériques  | Niveau 1 |
| Niveau 3 : hautement réglementé | Niveau 2 plus : <BR><BR> Chiffrement Bring Your Own Key (BYOK) et protection des informations commerciales secrètes <BR> Azure Key Vault pour les applications métier qui interagissent avec les services Microsoft 365 | Niveau 2 | Niveau 1 |
|||||

Voici les résultats de la configuration de la protection des informations de Contoso.

![Configuration de la protection des informations obtenue par Contoso.](../media/contoso-info-protect/contoso-info-protect-fig2.png)

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-security-summary.md) comment Contoso a utilisé les fonctionnalités de sécurité dans Microsoft 365 pour Enterprise pour la gestion des identités et des accès, la protection contre les menaces, la protection des informations et la gestion de la sécurité.

## <a name="see-also"></a>Voir aussi

[Feuille de route de sécurité](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)


