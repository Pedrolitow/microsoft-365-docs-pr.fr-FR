---
title: Infrastructure informatique et besoins métier de Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre la structure de base de l’infrastructure informatique locale de Contoso et la façon dont Microsoft 365 pour les entreprises répond aux besoins de l’entreprise.
ms.openlocfilehash: 6dff78cd3cbc7a4c1e27a647f98b0573a4ea3947
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68186744"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Infrastructure informatique et besoins métier de Contoso

Contoso passe d’une infrastructure informatique centralisée locale à une configuration cloud inclusive qui intègre des charges de travail et des applications de productivité personnelle basées sur le cloud.

## <a name="existing-contoso-it-infrastructure"></a>Infrastructure informatique Contoso existante

Contoso utilise une infrastructure informatique locale centralisée avec des centres de données situés au siège social parisien.

Voici le bureau du siège social avec des centres de données d’application, une zone DMZ et Internet.

![Infrastructure informatique Contoso existante.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Les centres de données d’applications hébergent les éléments suivants : 

- Applications métier personnalisées qui utilisent SQL Server et d’autres bases de données Linux.
- Ensemble d’anciens serveurs SharePoint.
- Serveurs au niveau des équipes et de l’organisation pour le stockage des fichiers.

De plus, chaque bureau central régional prend en charge un ensemble de serveurs possédant un groupe d’applications similaire. Ces serveurs sont contrôlés par les services informatiques régionaux.

Il est toujours compliqué d’effectuer des recherches dans les applications et les données de ces centres de données répartis partout dans le monde.

Dans la DMZ du siège de Contoso, différents ensembles de serveurs fournissent :

- Hébergement pour le site web public Contoso, à partir duquel les clients peuvent commander des produits, des pièces, des fournitures et des services.
- Hébergement de l’extranet des partenaires de Contoso pour la collaboration et la communication avec les partenaires.
- Accès à distance basé sur un réseau privé virtuel (VPN) à l’intranet et au proxy web de Contoso pour les collaborateurs présents au siège social parisien.

## <a name="contoso-business-needs"></a>Besoins métier de Contoso

Les besoins métier de Contoso se répartissent en cinq catégories principales :

**Productivité**

- Faciliter la collaboration

  Remplacez la collaboration basée sur le partage de fichiers et les e-mails par un modèle en ligne qui permet des modifications en temps réel sur des documents, des réunions en ligne plus faciles et des threads de conversation capturés.
- Améliorer la productivité pour les travailleurs mobiles et à distance

  Avec de nombreux employés travaillant à domicile ou sur le terrain, remplacez la solution VPN en goulot d’étranglement par un accès performant aux données et ressources Contoso dans le cloud.
- Accroître la créativité et l’innovation

  Profiter des dernières méthodes de développement d’idées et d’apprentissage visuel, notamment l’entrée manuscrite et la visualisation 3D.

**Sécurité**

- Gestion des identités et des accès

  Appliquez des formes d’authentification multifacteur et autres et protégez les informations d’identification des comptes d’utilisateur et d’administrateur.

- Protection contre les menaces

  Protéger contre les menaces externes de sécurité, notamment la messagerie et les programmes malveillants basés sur le système d’exploitation.

- Protection des informations

  Verrouiller l’accès aux biens numériques sensibles tels que les données client, les spécifications de conception et de fabrication et les informations des employés, et les chiffrer.

- Gestion de la sécurité

  Surveillez la posture de sécurité et détectez et répondez aux menaces en temps réel.

**Accès mobile et à distance, et partenaires professionnels**

- Améliorer la sécurité des travailleurs à distance et mobiles

  Implémentez BYOD (Apportez votre propre appareil) et la gestion des appareils appartenant à l’entreprise pour garantir un accès sécurisé, un comportement correct de l’application et la protection des données d’entreprise.

- Réduire l’infrastructure d’accès distant pour les employés

  Réduisez les coûts de maintenance et de support et améliorez les performances de la solution d’accès à distance en déplaçant les ressources couramment accessibles vers le cloud.

- Fournir une meilleure connectivité et réduire la surcharge pour les transactions B2B (business-to-business)

  Remplacez un extranet de partenaire vieillissant et coûteux par une solution cloud qui utilise l’authentification fédérée.

**Conformité**

- Respecter les exigences réglementaires locales

  Garantir la conformité avec les réglementations sectorielles et régionales relatives au stockage des données, au chiffrement, à la confidentialité des données et aux réglementations relatives aux données personnelles, telles que le Règlement général sur la protection des données (RGPD) pour l’Union européenne.

**Gestion**

- Réduction de la surcharge informatique pour la gestion des logiciels exécutés sur les PC et appareils clients

  Automatiser l’installation des mises à jour du système d’exploitation Windows et Applications Microsoft 365 pour les grandes entreprises au sein de l’organisation.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Mappage des besoins de l’entreprise Contoso à Microsoft 365 pour les entreprises

Le service informatique de Contoso a déterminé le mappage suivant des besoins métier pour Microsoft 365 E5 fonctionnalités avant le déploiement :


| Catégorie | Besoin métier | Microsoft 365 pour les produits ou fonctionnalités d’entreprise |
|:-------|:-----|:-----|
| Productivité |  |  |
|  | Faciliter la collaboration | Microsoft Teams, SharePoint, OneDrive |
|  | Améliorer la productivité pour les travailleurs mobiles et à distance | Charges de travail Microsoft 365 et données informatiques |
|  | Accroître la créativité et l’innovation | Windows Ink, Cortana at Work, PowerPoint |
| Sécurité |  |  |
|  | Gestion des identités et des accès | Comptes d’administrateur général dédiés avec Azure AD Multi-Factor Authentication (MFA) et Azure AD Privileged Identity Management (PIM) <br> Authentification multifacteur pour tous les comptes d’utilisateur <br> Accès conditionnel <br> Lecteur de sécurité <br> Windows Hello <br> Windows Credential Guard |
|  | Protection contre les menaces | Advanced Threat Analytics <br> Windows Defender <br> Defender pour Office 365 <br> Microsoft Defender pour Office 365 <br> Investigation et réponse aux menaces Microsoft 365 <br> |
|  | Protection des informations | Azure Information Protection <br> Protection contre la perte de données (DLP) <br> Protection des informations Windows (WIP) <br> Microsoft Defender for Cloud Apps <br> Microsoft Intune |
|  | Gestion de la sécurité | Microsoft Defender pour le cloud  <br> Centre de sécurité Windows Defender |
| Accès mobile et à distance, et partenaires professionnels |  |  |
|  | Meilleure sécurité pour les travailleurs mobiles et à distance | Microsoft Intune |
|  | Réduire l’infrastructure d’accès distant pour les employés | Charges de travail Microsoft 365 et données informatiques |
|  | Améliorer la connectivité et réduire la surcharge pour les transactions B2B | Authentification fédérée et ressources informatiques |
| Conformité |  |  |
|  | Respecter les exigences réglementaires locales | Fonctionnalités RGPD dans Microsoft 365 |
| Gestion |  |  |
|  | Réduction de la surcharge informatique pour l’installation des mises à jour client | Mises à jour pour Windows 10 Entreprise <br> Mises à jour pour les Applications Microsoft 365 pour les entreprises |
||||

## <a name="next-step"></a>Étape suivante

Découvrez le [réseau local](contoso-networking.md) de Contoso Corporation et comment il a été optimisé pour l’accès et la latence aux ressources cloud Microsoft 365.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
