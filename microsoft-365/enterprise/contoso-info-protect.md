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
ms.openlocfilehash: 51740db9a0bb2e770e959fe8d9dcde15c042f5b8
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48637234"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Protection des informations de Contoso Corporation

Contoso est sérieusement en matière de sécurité des informations. La fuite ou la destruction de la propriété intellectuelle décrivant les conceptions de produits et les techniques de fabrication propriétaires les placerait à un désavantage compétitif.

Avant de transférer leurs biens numériques sensibles vers le Cloud, Contoso a fait en sorte que leurs besoins en matière de protection et de classification des informations étaient pris en charge par les services en nuage de Microsoft 365 pour entreprises.

## <a name="contoso-data-security-classification"></a>Classification de la sécurité des données contoso

Contoso a effectué une analyse de ses données et déterminé les niveaux de classification suivants.

| Niveau 1 : ligne de base | Niveau 2 : Sensible | Niveau 3 : hautement réglementé |
|:-------|:-----|:-----|
| Les données sont chiffrées et uniquement accessibles par des utilisateurs authentifiés.<BR> <BR> Fourni pour toutes les données stockées sur site et dans le stockage et les charges de travail basées sur le Cloud. Les données sont chiffrées lorsqu’elles résident dans le service et en transit entre le service et les appareils clients. <BR><BR>Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique. | Niveau 1 avec une authentification et une protection renforcées contre la perte de données.<BR> <BR> Une authentification forte comporte une authentification multi-facteur Azure (MFA) avec validation SMS. La protection contre la perte de données garantit que les informations sensibles ou critiques ne transitent pas en dehors du Cloud Microsoft.<BR><BR>Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits. | Niveau 2 avec des niveaux de chiffrement, d’authentification et d’audit plus élevés.<BR><BR>Niveaux de chiffrement des données au repos et dans le cloud les plus élevés, conformes aux réglementations locales, associés à une authentification multi-facteur avec cartes à puce et fonctionnalités d’audit et d’alerte granulaires.<BR> <BR>Des exemples de données de niveau 3 sont les informations personnelles des clients et des partenaires, les spécifications d’ingénierie de produit et les techniques de fabrication propriétaires.  |
||||

## <a name="contoso-information-policies"></a>Stratégies d’informations contoso
Le tableau suivant répertorie les stratégies d’informations contoso.


| Valeur | Access | Rétention des données | Protection des informations |
|:-------|:-----|:-----|:-----|
| Valeur commerciale faible (Niveau 1: Ligne de base) | Autoriser l’accès à tous.  | 6 mois | Utiliser le chiffrement. |
| Valeur commerciale moyenne (Niveau 2: Sensible) | Autoriser l’accès aux employés de contoso, aux sous-traitants et aux partenaires. <BR><BR> Utiliser l’authentification multi-facteur (MFA), le chiffrement TLS (Transport Layer Security) et la gestion des applications mobiles (MAM). | 2 ans  | Utiliser les valeurs de hachage pour l’intégrité des données.  |
| Valeur commerciale élevée (Niveau 3 : hautement réglementé) | Autoriser l’accès aux cadres et aux responsables des équipes techniques et de fabrication. <BR> <BR> Système de gestion des droits (RMS) avec les appareils réseau gérés seulement.  | 7 ans  | Utiliser des signatures numériques pour le non-reniement.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Le chemin d’accès contoso vers la protection des informations avec Microsoft 365 pour les entreprises

Contoso a suivi les étapes suivantes pour préparer Microsoft 365 pour les entreprises en fonction de leurs besoins en matière de protection des informations :

1. Identifier les informations à protéger

   Contoso a fait un examen approfondi de ses biens numériques existants situés sur des sites SharePoint locaux et des partages de fichiers, et a classé chaque ressource.

2. Déterminer les stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé la configuration requise détaillée en matière de stratégie, utilisée pour protéger les biens numériques existants lors de leur migration vers le cloud.

3. Créer des étiquettes de confidentialité et leurs paramètres pour les différents niveaux d’informations

   Contoso a créé des étiquettes de confidentialité pour ses niveaux de données dont les étiquettes hautement réglementées incluent chiffrement, autorisations et filigranes.

4.  Déplacer des données à partir de sites SharePoint locaux et de partages de fichiers vers leurs nouveaux sites SharePoint

    Les fichiers ayant migré vers les nouveaux sites SharePoint ont hérité des étiquettes de rétention par défaut attribuées au site.

5.  Former les employés à l’utilisation d’étiquettes de confidentialité pour les nouveaux documents, comment interagir avec les utilisateurs de contoso lors de la création de nouveaux sites SharePoint et pour toujours stocker des biens numériques sur des sites SharePoint

    Modification des informations du travailleur incorrect-les habitudes de stockage sont souvent considérées comme la partie la plus difficile de la transition de protection des informations pour le Cloud. Les services informatiques et de gestion de contoso devaient toujours étiqueter et stocker leurs biens numériques dans le Cloud, s’abstenir d’utiliser des partages de fichiers locaux, mais pas d’utiliser des services de stockage cloud tiers ou des lecteurs USB.

## <a name="conditional-access-policies-for-information-protection"></a>Stratégies d’accès conditionnel régissant la protection des informations

Dans le cadre de leur déploiement d’Exchange Online et de SharePoint, Contoso a configuré l’ensemble suivant de stratégies d’accès conditionnel et les a appliquées aux groupes appropriés :

- [Stratégies d’accès aux applications gérées et non gérées sur les périphériques](../security/office-365-security/identity-access-policies.md)
- [Stratégies d’accès à Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)
- [Stratégies d’accès SharePoint](../security/office-365-security/sharepoint-file-access-policies.md)

Voici le jeu de stratégies contoso pour la protection des informations.

![Stratégies d’accès conditionnel à SharePoint, à Exchange Online et aux appareils](../media/contoso-info-protect/contoso-info-protect-fig1.png)

>[!Note]
>Contoso a également configuré d’autres stratégies d’accès conditionnel pour l’identité et la connexion. Consultez l’[Identité de Contoso Corporation](contoso-identity.md#conditional-access-policies-for-identity-and-device-access).
>

Ces stratégies vous assurent que :

- Les applications autorisées et les actions qu’elles peuvent effectuer avec les données de l’organisation sont définies par les stratégies de protection des applications.
- les PC et les périphériques mobiles sont conformes ;
- Exchange Online utilise le chiffrement de messages Office 365 (OME) pour Exchange Online.
- SharePoint utilise des restrictions appliquées par l’application.
- SharePoint utilise les stratégies de contrôle d’accès pour assurer un accès réservé au navigateur et bloquer l’accès aux matériels non gérés.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Mappage de Microsoft 365 pour les fonctionnalités d’entreprise aux niveaux de données contoso

Le tableau suivant établit une correspondance entre les niveaux de données Contoso et les fonctionnalités de protection des informations dans Microsoft 365 pour les entreprises.

| Niveau | Services Cloud Microsoft 365 | Windows 10 et Microsoft 365 Apps for enterprise | Sécurité et conformité |
|:-------|:-----|:-----|:-----|
| Niveau 1 : ligne de base  | Stratégies d’accès conditionnel à SharePoint et à Exchange Online <BR> Autorisations sur les sites SharePoint | Étiquettes de confidentialité <BR> BitLocker <BR> Protection des informations Windows | Stratégies d’accès conditionnel aux matériels et stratégies de gestion des applications mobiles |
| Niveau 2 : Sensible | Niveau 1 plus : <BR> <BR> Étiquettes de confidentialité <BR> Étiquettes de rétention Microsoft 365 sur les sites SharePoint <BR> Protection contre la perte de données pour SharePoint et Exchange Online <BR> Sites SharePoint isolés  | Niveau 1 plus : <BR> <BR> Étiquettes de sensibilité sur les biens numériques  | Niveau 1 |
| Niveau 3 : hautement réglementé | Niveau 2 plus : <BR><BR> Mettre en place votre propre chiffrement (BYOK) et protéger les informations de secret commercial <BR> Coffre-fort de clés Azure pour les applications métier qui interagissent avec les services Microsoft 365 | Niveau 2 | Niveau 1 |
|||||

Voici la configuration de protection des informations contoso résultante.

![Configuration de la protection des informations obtenue par Contoso.](../media/contoso-info-protect/contoso-info-protect-fig2.png)

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-security-summary.md) comment Contoso utilise les fonctionnalités de sécurité dans Microsoft 365 pour Enterprise pour la gestion des identités et des accès, la protection contre les menaces, la protection des informations et la gestion de la sécurité.

## <a name="see-also"></a>Voir aussi

[Feuille de route de sécurité](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
