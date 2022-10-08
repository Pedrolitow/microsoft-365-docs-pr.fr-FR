---
title: Protection des informations de Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
ms.date: 10/02/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-security-compliance
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez comment Contoso utilise les fonctionnalités de protection des informations dans Microsoft 365 pour les entreprises afin de sécuriser leurs ressources numériques dans le cloud.
ms.openlocfilehash: f63a0b7992602acc873350714cc68ab40f905fb7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68209181"
---
# <a name="information-protection-for-the-contoso-corporation"></a>Protection des informations de Contoso Corporation

Contoso est sérieux quant à la sécurité de ses informations. Les fuites ou destructions de propriété intellectuelle qui décrivent leurs conceptions de produits et leurs techniques de fabrication propriétaires les placeraient dans un désavantage concurrentiel.

Avant de déplacer leurs ressources numériques sensibles vers le cloud, Contoso s’est assuré que ses exigences de protection et de classification des informations locales étaient prises en charge par les services cloud de Microsoft 365 pour les entreprises.

## <a name="contoso-data-security-classification"></a>Classification de la sécurité des données Contoso

Contoso a effectué une analyse de ses données et déterminé les niveaux de classification suivants.

| Niveau 1 : ligne de base | Niveau 2 : Sensible | Niveau 3 : hautement réglementé |
|:-------|:-----|:-----|
| Les données sont chiffrées et uniquement accessibles par des utilisateurs authentifiés.<BR> <BR> Fourni pour toutes les données stockées localement et dans le stockage cloud et les charges de travail. Les données sont chiffrées pendant qu’elles résident dans le service et en transit entre le service et les appareils clients. <BR><BR>Les données de niveau 1 incluent, par exemple, les communications d’entreprise normales (courrier électronique) et les fichiers des collaborateurs de l’administration, des ventes et du support technique. | Niveau 1 avec une authentification et une protection renforcées contre la perte de données.<BR> <BR> L’authentification forte inclut Azure AD Multi-Factor Authentication (MFA) avec validation SMS. Protection contre la perte de données Microsoft Purview garantit que les informations sensibles ou critiques ne se déplacent pas en dehors du cloud Microsoft.<BR><BR>Les données de niveau 2 sont, par exemple, des informations financières et juridiques ainsi que les données de recherche et de développement de nouveaux produits. | Niveau 2 avec des niveaux de chiffrement, d’authentification et d’audit plus élevés.<BR><BR>Niveaux de chiffrement des données au repos et dans le cloud les plus élevés, conformes aux réglementations locales, associés à une authentification multi-facteur avec cartes à puce et fonctionnalités d’audit et d’alerte granulaires.<BR> <BR>Les informations personnelles du client et du partenaire, les spécifications d’ingénierie de produit et les techniques de fabrication propriétaires sont des exemples de données de niveau 3.  |
||||

## <a name="contoso-information-policies"></a>Stratégies d’informations Contoso
Le tableau suivant répertorie les stratégies d’informations Contoso.


| Valeur | Access | Rétention des données | Protection des informations |
|:-------|:-----|:-----|:-----|
| Valeur commerciale faible (Niveau 1: Ligne de base) | Autorisez l’accès à tous.  | 6 mois | Utiliser le chiffrement. |
| Valeur commerciale moyenne (Niveau 2: Sensible) | Autorisez l’accès aux employés, sous-traitants et partenaires de Contoso. <BR><BR> Utiliser l’authentification multi-facteur (MFA), le chiffrement TLS (Transport Layer Security) et la gestion des applications mobiles (MAM). | 2 ans  | Utiliser les valeurs de hachage pour l’intégrité des données.  |
| Valeur commerciale élevée (Niveau 3 : hautement réglementé) | Autoriser l’accès aux cadres et aux responsables des équipes techniques et de fabrication. <BR> <BR> Système de gestion des droits (RMS) avec les appareils réseau gérés seulement.  | 7 ans  | Utiliser des signatures numériques pour le non-reniement.  |
|||||

## <a name="the-contoso-path-to-information-protection-with-microsoft-365-for-enterprise"></a>Chemin Contoso vers la protection des informations avec Microsoft 365 pour les entreprises

Contoso a suivi ces étapes pour préparer Microsoft 365 pour les entreprises à leurs exigences de protection des informations :

1. Identifier les informations à protéger

   Contoso a effectué un examen approfondi de ses ressources numériques existantes situées sur des sites Et partages de fichiers SharePoint locaux, et a classé chaque ressource.

2. Déterminer les stratégies d’accès, de rétention et de protection des informations pour les niveaux de données

   En fonction des niveaux de données, Contoso a déterminé la configuration requise détaillée en matière de stratégie, utilisée pour protéger les biens numériques existants lors de leur migration vers le cloud.

3. Créer des étiquettes de confidentialité et leurs paramètres pour les différents niveaux d’informations

   Contoso a créé des étiquettes de confidentialité pour ses niveaux de données dont les étiquettes hautement réglementées incluent chiffrement, autorisations et filigranes.

4. Déplacer des données à partir de sites SharePoint locaux et de partages de fichiers vers leurs nouveaux sites SharePoint

    Les fichiers ayant migré vers les nouveaux sites SharePoint ont hérité des étiquettes de rétention par défaut attribuées au site.

5. Former les employés à l’utilisation d’étiquettes de confidentialité pour les nouveaux documents, à interagir avec l’informatique Contoso lors de la création de sites SharePoint et à toujours stocker des ressources numériques sur des sites SharePoint

    La modification des mauvaises habitudes de stockage des informations de travail est souvent considérée comme la partie la plus difficile de la transition de la protection des informations pour le cloud. L’informatique et la gestion de Contoso devaient amener les employés à toujours étiqueter et stocker leurs ressources numériques dans le cloud, à s’abstenir d’utiliser des partages de fichiers locaux et à ne pas utiliser de services de stockage cloud tiers ou de lecteurs USB.

## <a name="conditional-access-policies-for-information-protection"></a>Stratégies d’accès conditionnel régissant la protection des informations

Dans le cadre de leur déploiement de Exchange Online et SharePoint, Contoso a configuré l’ensemble suivant de stratégies d’accès conditionnel et les a appliquées aux groupes appropriés :

- [Stratégies d’accès aux applications gérées et non gérées sur les périphériques](../security/office-365-security/identity-access-policies.md)
- [Stratégies d’accès à Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)
- [Stratégies d’accès SharePoint](../security/office-365-security/sharepoint-file-access-policies.md)

Voici un ensemble de stratégies Contoso pour la protection des informations.

:::image type="content" alt-text="Stratégies d’accès conditionnel d’appareil, Exchange Online et SharePoint." source="../media/contoso-info-protect/contoso-info-protect-fig1.png" lightbox="../media/contoso-info-protect/contoso-info-protect-fig1.png":::

>[!Note]
>Contoso a également configuré d’autres stratégies d’accès conditionnel pour l’identité et la connexion. Consultez l’[Identité de Contoso Corporation](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).
>

Ces stratégies vous assurent que :

- Les applications autorisées et les actions qu’elles peuvent effectuer avec les données de l’organisation sont définies par des stratégies de protection des applications.
- les PC et les périphériques mobiles sont conformes ;
- Exchange Online utilise Office 365 chiffrement de message (OME) pour Exchange Online.
- SharePoint utilise des restrictions appliquées par l’application.
- SharePoint utilise les stratégies de contrôle d’accès pour assurer un accès réservé au navigateur et bloquer l’accès aux matériels non gérés.

## <a name="mapping-microsoft-365-for-enterprise-features-to-contoso-data-levels"></a>Mappage de Microsoft 365 pour les fonctionnalités d’entreprise aux niveaux de données Contoso

Le tableau suivant mappe les niveaux de données Contoso aux fonctionnalités de protection des informations dans Microsoft 365 pour les entreprises.

| Niveau | Services cloud Microsoft 365 | Windows 10 et Microsoft 365 Apps for enterprise | Sécurité et conformité |
|:-------|:-----|:-----|:-----|
| Niveau 1 : ligne de base  | Stratégies d’accès conditionnel à SharePoint et à Exchange Online <BR> Autorisations sur les sites SharePoint | Étiquettes de confidentialité <BR> BitLocker <BR> Protection des informations Windows | Stratégies d’accès conditionnel aux matériels et stratégies de gestion des applications mobiles |
| Niveau 2 : Sensible | Niveau 1 plus : <BR> <BR> Étiquettes de confidentialité <BR> Étiquettes de rétention Microsoft 365 sur les sites SharePoint <BR> Protection contre la perte de données pour SharePoint et Exchange Online <BR> Sites SharePoint isolés  | Niveau 1 plus : <BR> <BR> Étiquettes de sensibilité sur les biens numériques  | Niveau 1 |
| Niveau 3 : hautement réglementé | Niveau 2 plus : <BR><BR> Chiffrement et protection BYOK (Bring your own key) pour les informations de secret commercial <BR> Azure Key Vault pour les applications métier qui interagissent avec les services Microsoft 365 | Niveau 2 | Niveau 1 |
|||||

Voici la configuration de protection des informations Contoso qui en résulte.

:::image type="content" alt-text="Configuration de la protection des informations résultante de Contoso." source="../media/contoso-info-protect/contoso-info-protect-fig2.png":::

## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso utilise les [fonctionnalités de sécurité de Microsoft 365 pour les entreprises pour](contoso-security-summary.md) la gestion des identités et des accès, la protection contre les menaces, la protection des informations et la gestion de la sécurité.

## <a name="see-also"></a>Voir aussi

[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/overview)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)