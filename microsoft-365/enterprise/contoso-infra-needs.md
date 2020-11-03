---
title: Infrastructure informatique contoso et besoins de l’entreprise
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez la structure de base de l’infrastructure informatique de contoso sur site et la façon dont les besoins de l’entreprise sont satisfaits par Microsoft 365 pour les entreprises.
ms.openlocfilehash: 0a837a457869fc579d94ee5e5f9bb114cb93f641
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48847129"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Infrastructure informatique contoso et besoins de l’entreprise

Contoso passe d’une infrastructure informatique centralisée locale à une configuration Cloud inclusive qui intègre des charges de travail et des applications de productivité personnelle basées sur le Cloud.

## <a name="existing-contoso-it-infrastructure"></a>Infrastructure informatique contoso existante

Contoso utilise une infrastructure informatique locale centralisée avec des centres de données situés au siège social parisien.

Voici le siège social avec les centres de services d’applications, un DMZ et Internet.

![Infrastructure informatique contoso existante](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Les centres de données d’applications hébergent les éléments suivants : 

- Applications métier personnalisées qui utilisent SQL Server et d’autres bases de données Linux.
- Ensemble d’anciens serveurs SharePoint.
- Serveurs au niveau des équipes et de l’organisation pour le stockage des fichiers.

De plus, chaque bureau central régional prend en charge un ensemble de serveurs possédant un groupe d’applications similaire. Ces serveurs sont contrôlés par les services informatiques régionaux.

Il est toujours compliqué d’effectuer des recherches dans les applications et les données de ces centres de données répartis partout dans le monde.

Dans la zone DMZ du siège social contoso, différents ensembles de serveurs fournissent les éléments suivants :

- Hébergement pour le site Web public contoso, à partir duquel les clients peuvent commander des produits, des composants, des fournitures et des services.
- Hébergement de l’extranet des partenaires de Contoso pour la collaboration et la communication avec les partenaires.
- Accès à distance basé sur un réseau privé virtuel (VPN) à l’intranet et au proxy web de Contoso pour les collaborateurs présents au siège social parisien.

## <a name="contoso-business-needs"></a>Besoins commerciaux de contoso

Les besoins d’entreprise de contoso appartiennent à cinq catégories principales :

**Productivité**

- Faciliter la collaboration

  Remplacement de la messagerie et de la collaboration basée sur des partages de fichiers par un modèle en ligne qui permet des modifications en temps réel sur des documents, des réunions en ligne plus faciles et des threads de conversation capturés.
- Améliorer la productivité pour les travailleurs mobiles et à distance

  Avec de nombreux employés travaillant à la maison ou sur le terrain, remplacez la solution VPN avec un accès performant aux données et ressources Contoso dans le Cloud.
- Accroître la créativité et l’innovation

  Profiter des dernières méthodes de développement d’idées et d’apprentissage visuel, notamment l’entrée manuscrite et la visualisation 3D.

**Sécurité**

- Gestion des identités et des accès

  Appliquer Multifactor et d’autres formes d’authentification et protéger les informations d’identification des utilisateurs et des comptes d’administrateur.

- Protection contre les menaces

  Protéger contre les menaces externes de sécurité, notamment la messagerie et les programmes malveillants basés sur le système d’exploitation.

- Protection des informations

  Verrouiller l’accès aux biens numériques sensibles tels que les données client, les spécifications de conception et de fabrication et les informations des employés, et les chiffrer.

- Gestion de la sécurité

  Surveiller la position de la sécurité et détecter et répondre aux menaces en temps réel.

**Accès mobile et à distance, et partenaires professionnels**

- Améliorer la sécurité pour les utilisateurs distants et mobiles

  Implémentez votre propre appareil (BYOD) et la gestion des périphériques appartenant à votre entreprise pour garantir un accès sécurisé, un comportement d’application correct et la protection des données de l’entreprise.

- Réduire l’infrastructure d’accès distant pour les employés

  Réduisez les coûts de maintenance et de support et améliorez les performances de la solution d’accès à distance en déplacant les ressources fréquemment utilisées dans le Cloud.

- Fournir une meilleure connectivité et réduire les frais généraux pour les transactions B2B (Business-to-susiness)

  Remplacez un extranet de partenaire vieillissant et coûteux par une solution cloud qui utilise l’authentification fédérée.

**Conformité**

- Respecter les exigences réglementaires locales

  Assurer la conformité avec les réglementations sectorielles et régionales relatives au stockage des données, au chiffrement, à la confidentialité des données et aux réglementations relatives aux données personnelles, telles que le règlement général sur la protection des données (RGPD) pour l’Union européenne.

**Gestion**

- Réduction de la charge informatique pour la gestion des logiciels s’exécutant sur les PC et les appareils clients

  Automatisez l’installation des mises à jour sur le système d’exploitation Windows et les applications Microsoft 365 pour les entreprises au sein de l’organisation.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Mappage des besoins de l’entreprise Contoso à Microsoft 365 pour les entreprises

Le service informatique de Contoso a déterminé le mappage suivant des besoins de l’entreprise aux fonctionnalités Microsoft 365 E5 avant le déploiement :


| Catégorie | Besoin métier | Microsoft 365 pour les produits ou les fonctionnalités d’entreprise |
|:-------|:-----|:-----|
| Productivité |  |  |
|  | Faciliter la collaboration | Microsoft Teams, SharePoint, OneDrive |
|  | Améliorer la productivité pour les travailleurs mobiles et à distance | Charges de travail Microsoft 365 et données informatiques |
|  | Accroître la créativité et l’innovation | Windows Ink, Cortana at Work, PowerPoint |
| Sécurité |  |  |
|  | Gestion des identités et des accès | Comptes Administrateur général dédiés avec l’authentification multifacteur (MFA) Azure et Azure AD Privileged Identity Management (PIM) <BR> Authentification multifacteur pour tous les comptes d’utilisateur <BR> Accès conditionnel <BR> Windows Hello <BR> Windows Credential Guard |
|  | Protection contre les menaces | Advanced Threat Analytics <BR> Windows Defender <BR> Defender pour Office 365 <BR> Microsoft Defender pour Office 365 <BR> Enquête et réponse de menace Microsoft 365 <BR> |
|  | Protection des informations | Azure Information Protection <BR> Protection contre la perte de données (DLP) <BR> Protection des informations Windows (WIP) <BR> Microsoft Cloud App Security <BR> Microsoft Intune |
|  | Gestion de la sécurité | Azure Defender *  <BR> Centre de sécurité Windows Defender |
| Accès mobile et à distance, et partenaires professionnels |  |  |
|  | Meilleure sécurité pour les travailleurs mobiles et à distance | Microsoft Intune |
|  | Réduire l’infrastructure d’accès distant pour les employés | Charges de travail Microsoft 365 et données informatiques |
|  | Améliorer la connectivité et réduire les frais généraux pour les transactions B2B | Authentification fédérée et ressources informatiques |
| Conformité |  |  |
|  | Respecter les exigences réglementaires locales | Fonctionnalités RGPD dans Microsoft 365 |
| Gestion |  |  |
|  | Réduire les frais généraux pour l’installation des mises à jour du client | Mises à jour pour Windows 10 Entreprise <BR> Mises à jour pour les Applications Microsoft 365 pour les entreprises |
||||

## <a name="next-step"></a>Étape suivante

Découvrez le réseau Contoso Corporation [sur site](contoso-networking.md) et la façon dont il a été optimisé pour l’accès et la latence aux ressources basées sur le Cloud de Microsoft 365.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
