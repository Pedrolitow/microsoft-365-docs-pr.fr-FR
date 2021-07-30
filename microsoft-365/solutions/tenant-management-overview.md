---
title: Gestion des locataires pour Microsoft 365 entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- m365solution-overview
- tenant-management
ms.custom:
- Ent_Solutions
description: Vue d’ensemble de la planification, du déploiement et du fonctionnement continu de vos Microsoft 365 client.
ms.openlocfilehash: 7cc7ead75781ab2d8ac4776e3f6075de89fef8db
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53649828"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Gestion des locataires pour Microsoft 365 entreprise

La création d’un chemin d’accès à la transformation numérique de votre organisation avec le cloud computing nécessite une base solide sur laquelle vos employés peuvent compter pour la productivité, la collaboration, les performances, la confidentialité, la conformité et la sécurité.

Une configuration correcte de vos clients Microsoft 365 constitue cette base, laissant vos employés se concentrer sur leur travail et votre service informatique pour se concentrer sur les solutions de bout en bout qui fournissent une valeur commerciale supplémentaire.

Cette solution vous permet de suivre la configuration de ces bases dans les étapes suivantes :

1. Déterminer vos locataires
2. Optimiser votre réseau
3. Synchroniser vos identités et appliquer des sign-ins sécurisées
4. Migrer vos Windows, vos clients Office, ainsi que vos serveurs et données Office locaux
5. Déployer la gestion des appareils et des applications

Mais tout d’abord, nous allons prendre un moment pour comprendre ce qu’est un client et ce à quoi ressemble un client qui fournit une base solide.

## <a name="a-microsoft-365-tenant-defined"></a>Un Microsoft 365 défini

Un Microsoft 365 client est une instance dédiée des services de Microsoft 365 et des données de votre organisation stockées dans un emplacement par défaut spécifique, comme l’Europe ou l’Amérique du Nord. Cet emplacement est spécifié lorsque vous créez le client pour votre organisation. Chaque Microsoft 365 client est distinct, unique et distinct de tous les autres Microsoft 365 client. Vous créez un Microsoft 365 client lorsque vous achetez un ou plusieurs produits Microsoft, tels que Microsoft 365 E3 ou E5, et un ensemble de licences pour chacun d’eux.

Votre client Microsoft 365 inclut également un client Azure Active Directory (Azure AD), qui est une instance dédiée d’Azure AD pour les comptes d’utilisateur, les groupes et d’autres objets. Chaque client Azure AD est distinct, unique et distinct de tous les autres locataires Azure AD. Bien que votre organisation puisse avoir plusieurs locataires Azure AD que vous pouvez configurer avec des abonnements Azure, les locataires Microsoft 365 ne peuvent utiliser qu’un seul client Azure AD, celui qui a été créé lors de la création du client.

Voici un exemple :

![Exemple de Microsoft 365 client avec son client Azure AD](../media/tenant-management-overview/tenant-management-example-tenant.png)

*La gestion des* locataires est la planification, le déploiement et le fonctionnement continu de vos Microsoft 365 client.

## <a name="attributes-of-a-well-designed-and-operating-tenant"></a>Attributs d’un client bien conçu et opérationnel

Au-delà du nom et de l’emplacement corrects pour votre client, il existe des éléments supplémentaires à planifier, déployer et gérer pour vous assurer que vos expériences utilisateur avec les applications de productivité cloud telles que Microsoft Teams et Exchange Online sont efficaces, sécurisées et &mdash; &mdash; performantes.

Voici les éléments :

- Vous avez l’ensemble correct de produits (abonnements) et de licences.
  - L’ensemble de produits correspond à vos besoins d’entreprise, informatique et de sécurité.
  - Il existe un nombre adéquat de licences pour vos employés et les modifications prévues dans le personnel.
- Pour la mise en réseau :
  - Vous avez configuré les noms de domaine DNS corrects.
  - Pour les réseaux d’entreprise, vous avez optimisé le trafic réseau vers le réseau Microsoft pour les travailleurs sur site.
  - Vous avez optimisé le trafic réseau pour les travailleurs à distance qui utilisent un client VPN.
- Vous avez synchronisé vos comptes, groupes et autres objets des services de domaine Active Directory (AD DS).
  - Vos comptes de client Azure AD sont Exchange Online boîtes aux lettres avec les domaines DNS corrects pour les adresses de messagerie.
  - Les licences correctes des produits achetés corrects ont été attribuées à vos comptes d’utilisateurs (par exemple, Microsoft 365 E3 ou E5).
- Vous avez configuré une gestion forte des identités et des accès.
  - Vous avez besoin d’une authentification utilisateur sécurisée avec authentification sans mot de passe ou multifacteur (MFA).
  - Vous avez des stratégies d’accès conditionnel qui appliquent des exigences et des restrictions de connect pour des niveaux de sécurité plus élevés.
- Les serveurs Office locaux et leurs données ont été migrés vers des applications cloud ou sont utilisés dans une configuration hybride.
- Vous êtes en train d’assurer la gestion des appareils avec Intune ou Basic Mobility and Security intégré à Microsoft 365.
  - Les appareils de votre organisation sont inscrits et gérés.
  - Les applications pour les appareils personnels sont gérées.

Voici un exemple de client Microsoft 365 avec tous ces éléments en place.

![Exemple de Microsoft 365 client](../media/tenant-management-overview/tenant-management-tenant-config.png)

Dans cette illustration, le client Microsoft 365 inclut :

- Produits et licences pour Microsoft 365 E3 et E5.
- Microsoft 365 applications de productivité.
- Intune avec les appareils inscrits et les stratégies d’appareil et d’application.
- Un client Azure AD qui a synchronisé un compte d’utilisateur (les groupes et autres objets d’annuaire ne sont pas affichés), les domaines et les stratégies d’accès conditionnel.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Fonctionnalités client pour Microsoft 365 entreprise

Les sections et le tableau suivants listent les fonctionnalités clés et la gestion des licences pour les étapes de cette solution.

### <a name="tenant"></a>Tenant

|Fonctionnalité|Description|Licence|
|---|---|---|
|Plusieurs clients|Chaque Microsoft 365 client est distinct, unique et distinct de tous les autres Microsoft 365 client. Avec plusieurs clients, il existe des restrictions et des considérations supplémentaires lors de leur gestion et de la fourniture de services à vos utilisateurs.|Microsoft 365 E3 ou E5|
|Migration de boîtes aux lettres inter-clients|Les administrateurs client peuvent déplacer des boîtes aux lettres entre des locataires avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela supprime la nécessité de supprimer les boîtes aux lettres d’intégration et d’intégration.|Microsoft 365 E3 ou E5|
|Multi-Géo|Votre client peut stocker des données au repos dans les autres emplacements géographiques de centres de données que vous avez choisis pour répondre aux exigences de résidence des données.|Microsoft 365 E3 ou E5|
|Déplacer les données principales vers une nouvelle géo de centres de données|Lorsque Microsoft ajoute de nouvelles géos de centres de données pour des ressources de calcul et de capacité supplémentaires, vous pouvez demander un déplacement géographique de centre de données pour la résidence des données dans la zone géographique pour vos données client principales.|Microsoft 365 E3 ou E5|
||||

### <a name="networking"></a>Réseau

|Fonctionnalité|Description|Licence|
|---|---|---|
|Réseau Informations|Mesures de performances réseau collectées à partir de votre client Microsoft 365 pour vous aider à concevoir des périmètres réseau pour vos emplacements de bureau.|Microsoft 365 E3 ou E5|
|Automatiser les mises à jour des points de terminaison|Automatisez la configuration et les mises à jour en cours Microsoft 365 points de terminaison dans vos fichiers PAC clients, ainsi que les périphériques et services réseau.|Microsoft 365 E3 ou E5|
||||

### <a name="identity"></a>Identité

|Fonctionnalité|Description|Licence|
|---|---|---|
|Synchroniser les services de domaine Active Directory (AD DS) locaux avec votre client Azure AD|Tirez parti de votre fournisseur d’identité local pour les comptes d’utilisateur, les groupes et d’autres objets.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec paramètres de sécurité par défaut|Protégez-vous contre les identités compromises et les appareils en imposant une deuxième forme d’authentification pour les connexions. La sécurité par défaut nécessite l’authentification multifacteur pour tous les comptes d’utilisateurs.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel|Exiger l' approbation de la MFA en fonction des attributs de la connectez-vous avec les stratégies d’accès conditionnel.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel basé sur les risques|Requiert une authentification multifacteur basée sur le risque de connexion de l’utilisateur avec Microsoft Defender pour identité.|Microsoft 365 E5 ou E3 avec les licences Azure AD Premium P2|
|Réinitialisation du mot de passe libre-service (SSPR)|Autoriser vos utilisateurs à réinitialiser ou déverrouiller leur mot de passe ou leur compte.|Microsoft 365 E3 ou E5|
||||

### <a name="migration"></a>Migration

|Fonctionnalité|Description|Licence|
|---|---|---|
|Mettre à jour vers Windows 10|Migrez vos appareils qui exécutent Windows 7 ou Windows 8.1 vers Windows 10 Entreprise.|Windows 10 Entreprise licences incluses avec Microsoft 365 E3 ou E5|
|Migrer vers Applications Microsoft 365 pour les grandes entreprises|Migrez Office applications clientes telles que Word et PowerPoint vers les versions installées à partir du cloud qui sont mises à jour avec de nouvelles fonctionnalités.|Microsoft 365 E3 ou E5|
|Migrer les données et les serveurs locaux vers Microsoft 365|Migrez Exchange boîtes aux lettres, SharePoint sites et Skype Entreprise Online vers Microsoft 365 services cloud.|Microsoft 365 E3 ou E5|
||||

### <a name="device-and-app-management"></a>Données de gestion des appareils et des applications

|Fonctionnalité|Description|Licence|
|---|---|---|
|Microsoft Intune|Service basé sur le cloud qui fournit la gestion des périphériques mobiles (MDM) et la gestion des applications mobiles (MAM) pour contrôler la façon dont l’application de votre organisation et les appareils sont utilisés, y compris les téléphones mobiles, les tablettes et les ordinateurs portables.|Microsoft 365 E3 ou E5|
|Mobility + Security de Base|Sécuriser et gérer les appareils mobiles de vos utilisateurs tels que les iPhone, iPad, Android et Windows avec ce service intégré.|Microsoft 365 E3 ou E5|
||||

## <a name="next-steps"></a>Étapes suivantes

Utilisez ces étapes pour configurer et gérer vos Microsoft 365 client.

1. [Déterminer vos locataires](tenant-management-tenants.md)
2. [Optimiser votre réseau](tenant-management-networking.md)
3. [Synchroniser vos identités et appliquer des sign-ins sécurisées](tenant-management-identity.md)
4. [Migrer vos serveurs et données Office locaux](tenant-management-migration.md)
5. [Déployer la gestion des appareils et des applications](tenant-management-device-management.md)

[![Étapes de déploiement et de gestion d’un Microsoft 365 client](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

Chaque étape décrit les options de déploiement, résume les résultats et les tâches de maintenance en cours.

Pour comprendre comment une organisation multinationale fictive mais représentative a déployé les éléments de son client Microsoft 365, consultez l’étude de [cas Contoso.](../enterprise/contoso-case-study.md)
