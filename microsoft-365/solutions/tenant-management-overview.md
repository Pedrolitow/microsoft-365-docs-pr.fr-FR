---
title: Gestion des clients pour Microsoft 365 pour entreprise
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
description: Vue d’ensemble de la planification, du déploiement et du fonctionnement continu de vos clients Microsoft 365.
ms.openlocfilehash: 42bde00fbd4ddc1cf92236f099a22b2260dbb980
ms.sourcegitcommit: 070724118be25cd83418d2a56863da95582dae65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "50405677"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Gestion des clients pour Microsoft 365 pour entreprise

La création d’un chemin d’accès à la transformation numérique de votre organisation avec le cloud computing nécessite une base solide sur laquelle vos employés peuvent compter pour la productivité, la collaboration, les performances, la confidentialité, la conformité et la sécurité.

Une configuration correcte de vos clients Microsoft 365 constitue cette base, laissant vos employés se concentrer sur leur travail et votre service informatique afin de se concentrer sur les solutions de bout en bout qui fournissent une valeur commerciale supplémentaire. 

Cette solution vous permet de suivre la configuration de ces bases dans les étapes suivantes :

1. Déterminer vos locataires
2. Optimiser votre réseau
3. Synchroniser vos identités et appliquer des sign-ins sécurisées
4. Migrer vos appareils Windows, clients Office, serveurs et données Office locaux
5. Déployer la gestion des appareils et des applications

Mais tout d’abord, nous allons prendre le temps de comprendre ce qu’est un client et ce à quoi ressemble un client qui fournit une base solide.

## <a name="a-microsoft-365-tenant-defined"></a>Un client Microsoft 365 défini

Un client Microsoft 365 est une instance dédiée des services de Microsoft 365 et des données de votre organisation stockées dans un emplacement par défaut spécifique, comme l’Europe ou l’Amérique du Nord. Cet emplacement est spécifié lorsque vous créez le client pour votre organisation. Chaque client Microsoft 365 est distinct, unique et distinct de tous les autres clients Microsoft 365. Vous créez un client Microsoft 365 lorsque vous achetez un ou plusieurs produits microsoft, tels que Microsoft 365 E3 ou E5, et un ensemble de licences pour chacun d’eux.

Votre client Microsoft 365 inclut également un client Azure Active Directory (Azure AD), qui est une instance dédiée d’Azure AD pour les comptes d’utilisateurs, les groupes et d’autres objets. Chaque client Azure AD est distinct, unique et distinct de tous les autres locataires Azure AD. Bien que votre organisation puisse avoir plusieurs clients Azure AD que vous pouvez configurer avec des abonnements Azure, les clients Microsoft 365 ne peuvent utiliser qu’un seul client Azure AD, celui qui a été créé lors de la création du client. 

Voici un exemple :

![Exemple de client Microsoft 365 avec son client Azure AD](../media/tenant-management-overview/tenant-management-example-tenant.png)

*La gestion des* clients est la planification, le déploiement et le fonctionnement continu de vos clients Microsoft 365. 

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
- Vous avez synchronisé vos comptes, groupes et autres objets active Directory Domain Services (AD DS).
  - Vos comptes de client Azure AD sont mappés aux boîtes aux lettres Exchange Online avec les domaines DNS corrects pour les adresses de messagerie.
  - Les licences correctes des produits achetés corrects ont été attribuées à vos comptes d’utilisateurs (par exemple, Microsoft 365 E3 ou E5).
- Vous avez configuré une gestion forte des identités et des accès.
  - Vous avez besoin d’une authentification utilisateur sécurisée avec authentification sans mot de passe ou multifacteur (MFA).
  - Vous avez des stratégies d’accès conditionnel qui appliquent des exigences et des restrictions de connect pour des niveaux de sécurité plus élevés.
- Les serveurs Office locaux et leurs données ont été migrés vers des applications cloud ou sont utilisés dans une configuration hybride.
- Vous êtes en train d’assurer la gestion des appareils avec Intune ou Basic Mobility and Security intégré à Microsoft 365.
  - Les appareils de votre organisation sont inscrits et gérés.
  - Les applications pour les appareils personnels sont gérées.

Voici un exemple de client Microsoft 365 avec tous ces éléments en place.

![Exemple de client Microsoft 365](../media/tenant-management-overview/tenant-management-tenant-config.png)

Dans cette illustration, le client Microsoft 365 inclut :

- Produits et licences pour Microsoft 365 E3 et E5.
- Applications de productivité Microsoft 365.
- Intune avec les appareils inscrits et les stratégies d’appareil et d’application.
- Un client Azure AD qui a synchronisé un compte d’utilisateur (les groupes et autres objets d’annuaire ne sont pas affichés), les domaines et les stratégies d’accès conditionnel.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Fonctionnalités client pour Microsoft 365 pour entreprise

Les sections et le tableau suivants listent les fonctionnalités clés et la gestion des licences pour les étapes de cette solution.

### <a name="tenant"></a>Tenant

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Plusieurs clients | Chaque client Microsoft 365 est distinct, unique et distinct de tous les autres clients Microsoft 365. Avec plusieurs clients, il existe des restrictions et des considérations supplémentaires lors de leur gestion et de la fourniture de services à vos utilisateurs. | Microsoft 365 E3 ou E5 | 
| Migration de boîtes aux lettres inter-clients | Les administrateurs client peuvent déplacer des boîtes aux lettres entre des locataires avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela supprime la nécessité de supprimer les boîtes aux lettres d’intégration et d’intégration. | Microsoft 365 E3 ou E5 | 
| Multi-Géo | Votre client peut stocker des données au repos dans les autres emplacements géographiques de centres de données que vous avez choisis pour répondre aux exigences de résidence des données. | Microsoft 365 E3 ou E5 | 
| Déplacer les données principales vers une nouvelle géo de centres de données | Lorsque Microsoft ajoute de nouvelles géos de centres de données pour des ressources de calcul et de capacité supplémentaires, vous pouvez demander un déplacement géographique de centre de données pour la résidence des données dans la zone géographique pour vos données client principales. | Microsoft 365 E3 ou E5 | 
||||

### <a name="networking"></a>Réseau

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Informations réseau | Mesures de performances réseau collectées auprès de votre client Microsoft 365 pour vous aider à concevoir des périmètres réseau pour vos emplacements de bureau. | Microsoft 365 E3 ou E5 | 
| Automatiser les mises à jour des points de terminaison | Automatisez la configuration et les mises à jour en cours pour les points de terminaison Microsoft 365 dans vos fichiers PAC clients, ainsi que les périphériques et services réseau. | Microsoft 365 E3 ou E5 | 
||||

### <a name="identity"></a>Identité

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Synchroniser les services de domaine Active Directory (AD DS) locaux avec votre client Azure AD    | Tirez parti de votre fournisseur d’identité local pour les comptes d’utilisateur, les groupes et d’autres objets. | Microsoft 365 E3 ou E5 |
| Authentification multifacteur appliquée avec paramètres de sécurité par défaut   | Protégez-vous contre les identités compromises et les appareils en imposant une deuxième forme d’authentification pour les connexions. La sécurité par défaut nécessite l’authentification multifacteur pour tous les comptes d’utilisateurs.   | Microsoft 365 E3 ou E5 |
| Authentification multifacteur appliquée avec accès conditionnel| Exiger l' approbation de la MFA en fonction des attributs de la connectez-vous avec les stratégies d’accès conditionnel.    | Microsoft 365 E3 ou E5 | 
| Authentification multifacteur appliquée avec accès conditionnel basé sur les risques   | Requiert une authentification multifacteur basée sur le risque de connexion de l’utilisateur avec Microsoft Defender pour identité. | Microsoft 365 E5 ou E3 avec les licences Azure AD Premium P2 | 
| Réinitialisation du mot de passe libre-service (SSPR)    | Autoriser vos utilisateurs à réinitialiser ou déverrouiller leur mot de passe ou leur compte.  | Microsoft 365 E3 ou E5 |
||||

### <a name="migration"></a>Migration

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Mettre à jour vers Windows 10 | Migrez vos appareils qui exécutent Windows 7 ou Windows 8.1 vers Windows 10 Entreprise. | Licences Windows 10 Entreprise incluses dans Microsoft 365 E3 ou E5 | 
| Migrer vers Microsoft 365 Apps for enterprise | Migrez vos applications clientes Office telles que Word et PowerPoint vers les versions installées à partir du cloud qui sont mises à jour avec de nouvelles fonctionnalités. | Microsoft 365 E3 ou E5 | 
| Migrer des serveurs et des données locaux vers Microsoft 365 | Migrez vos boîtes aux lettres Exchange, vos sites SharePoint et Skype Entreprise Online vers les services cloud de Microsoft 365. | Microsoft 365 E3 ou E5 | 
||||

### <a name="device-and-app-management"></a>Données de gestion des appareils et des applications

| Fonctionnalité | Description | Licence |
|:-------|:-----|:-------|
| Microsoft Intune | Service basé sur le cloud qui fournit la gestion des périphériques mobiles (MDM) et la gestion des applications mobiles (MAM) pour contrôler la façon dont l’application de votre organisation et les appareils sont utilisés, y compris les téléphones mobiles, les tablettes et les ordinateurs portables. | Microsoft 365 E3 ou E5 | 
| Mobility + Security de Base | Sécuriser et gérer les appareils mobiles de vos utilisateurs tels que les iPhone, les iPad, les Android et les téléphones Windows avec ce service intégré.  | Microsoft 365 E3 ou E5 | 
||||

## <a name="next-steps"></a>Étapes suivantes

Utilisez ces étapes pour configurer et gérer vos clients Microsoft 365.

1. [Déterminer vos locataires](tenant-management-tenants.md)
2. [Optimiser votre réseau](tenant-management-networking.md)
3. [Synchroniser vos identités et appliquer des sign-ins sécurisées](tenant-management-identity.md)
4. [Migrer vos serveurs et données Office locaux](tenant-management-migration.md)
5. [Déployer la gestion des appareils et des applications](tenant-management-device-management.md)

[![Étapes de déploiement et de gestion d’un client Microsoft 365](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

Chaque étape décrit les options de déploiement, résume les résultats et les tâches de maintenance en cours.

Pour comprendre comment une organisation multinationale fictive mais représentative a déployé les éléments de son client Microsoft 365, consultez l’étude de [cas Contoso.](../enterprise/contoso-case-study.md)
