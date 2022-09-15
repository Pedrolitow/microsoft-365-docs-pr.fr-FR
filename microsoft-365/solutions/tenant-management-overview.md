---
title: Gestion des locataires pour Microsoft 365 pour les entreprises
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- m365solution-overview
- tenant-management
ms.custom:
- Ent_Solutions
description: Vue d’ensemble de la planification, du déploiement et du fonctionnement continu de vos locataires Microsoft 365.
ms.openlocfilehash: 11f0e0306788a48eaa67796030972727969692d8
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730592"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Gestion des locataires pour Microsoft 365 pour les entreprises

La création d’un chemin d’accès à la transformation numérique de votre organisation avec le cloud computing nécessite une base solide sur laquelle vos employés peuvent compter pour la productivité, la collaboration, les performances, la confidentialité, la conformité et la sécurité.

Une configuration correcte de vos locataires Microsoft 365 fournit cette base, ce qui permet à vos employés de se concentrer sur la réalisation de leur travail et votre service informatique de se concentrer sur des solutions de bout en bout qui fournissent une valeur métier supplémentaire.

Cette solution vous guide tout au long de la configuration de cette base dans les étapes suivantes :

1. Déterminer vos locataires
2. Optimiser votre réseau
3. Synchroniser vos identités et appliquer des connexions sécurisées
4. Migrer vos appareils Windows, clients Office et serveurs et données Office locaux
5. Déployer la gestion des appareils et des applications

Mais tout d’abord, prenons un moment pour comprendre ce qu’est un locataire et à quoi ressemble un locataire qui fournit une base ferme.

## <a name="a-microsoft-365-tenant-defined"></a>Un locataire Microsoft 365 défini

Un locataire Microsoft 365 est une instance dédiée des services de Microsoft 365 et des données de votre organisation stockées dans un emplacement par défaut spécifique, tel que l’Europe ou 北米. Cet emplacement est spécifié lorsque vous créez le locataire pour votre organisation. Chaque locataire Microsoft 365 est distinct, unique et distinct de tous les autres locataires Microsoft 365. Vous créez un locataire Microsoft 365 lorsque vous achetez un ou plusieurs produits auprès de Microsoft, tels que Microsoft 365 E3 ou E5, ainsi qu’un ensemble de licences pour chacun d’eux.

Votre locataire Microsoft 365 inclut également un locataire Azure Active Directory (Azure AD), qui est une instance dédiée d’Azure AD pour les comptes d’utilisateur, les groupes et d’autres objets. Chaque locataire Azure AD est distinct, unique et distinct de tous les autres locataires Azure AD. Bien que votre organisation puisse avoir plusieurs locataires Azure AD que vous pouvez configurer avec des abonnements Azure, les locataires Microsoft 365 ne peuvent utiliser qu’un seul locataire Azure AD, celui qui a été créé lors de la création du locataire.

Voici un exemple :

![Exemple de locataire Microsoft 365 avec son locataire Azure AD.](../media/tenant-management-overview/tenant-management-example-tenant.png)

*La gestion des locataires* est la planification, le déploiement et le fonctionnement continu de vos locataires Microsoft 365.

## <a name="attributes-of-a-well-designed-and-operating-tenant"></a>Attributs d’un locataire bien conçu et opérationnel

Au-delà du nom et de l’emplacement appropriés pour votre locataire, il existe des éléments supplémentaires à planifier, déployer et gérer pour vous assurer que vos expériences utilisateur avec des applications&mdash;de productivité cloud telles que Microsoft Teams et Exchange Online&mdash; sont efficaces, sécurisées et performantes.

Voici les éléments :

- Vous disposez de l’ensemble correct de produits (abonnements) et de licences.
  - L’ensemble de produits correspond à vos besoins métier, informatique et de sécurité.
  - Il y a un nombre suffisant de licences pour vos travailleurs et des changements prévus dans le personnel.
- Pour la mise en réseau :
  - Vous avez configuré les noms de domaine DNS corrects.
  - Pour les réseaux d’entreprise, vous avez optimisé le trafic réseau vers le réseau Microsoft pour les travailleurs sur site.
  - Vous avez optimisé le trafic réseau pour les travailleurs distants qui utilisent un client VPN.
- Vous avez synchronisé vos comptes, groupes et autres objets Active Directory 域服务 (AD DS).
  - Vos comptes de locataire Azure AD sont mappés à Exchange Online boîtes aux lettres avec les domaines DNS appropriés pour les adresses e-mail.
  - Les licences appropriées ont été attribuées à vos comptes d’utilisateur à partir des produits achetés corrects (par exemple, Microsoft 365 E3 ou E5).
- Vous avez configuré une gestion forte des identités et des accès.
  - Vous avez besoin d’une connexion utilisateur sécurisée avec une authentification multifacteur (MFA) sans mot de passe ou multifacteur.
  - Vous disposez de stratégies d’accès conditionnel qui appliquent des exigences et des restrictions de connexion pour des niveaux de sécurité plus élevés.
- Les serveurs Office locaux et leurs données ont été migrés vers des applications cloud ou sont utilisés dans une configuration hybride.
- Vous effectuez la gestion des appareils avec Intune ou mobilité et sécurité de base intégrés à Microsoft 365.
  - Les appareils appartenant à votre organisation sont inscrits et gérés.
  - Les applications pour les appareils personnels sont gérées.

Voici un exemple de locataire Microsoft 365 avec tous ces éléments en place.

![Exemple de locataire Microsoft 365.](../media/tenant-management-overview/tenant-management-tenant-config.png)

Dans cette illustration, le locataire Microsoft 365 inclut :

- Produits et licences pour Microsoft 365 E3 et E5.
- Applications de productivité Microsoft 365.
- Intune avec les appareils inscrits et les stratégies d’appareil et d’application.
- Un locataire Azure AD qui a synchronisé un compte d’utilisateur (les groupes et autres objets d’annuaire ne sont pas affichés), les domaines et les stratégies d’accès conditionnel.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Fonctionnalités de locataire pour Microsoft 365 pour les entreprises

Les sections et le tableau suivants répertorient les fonctionnalités clés et les licences pour les étapes de cette solution.

### <a name="tenant"></a>Tenant

|Fonctionnalité|Description|Licence|
|---|---|---|
|Plusieurs clients|Chaque locataire Microsoft 365 est distinct, unique et distinct de tous les autres locataires Microsoft 365. Avec plusieurs locataires, il existe des restrictions et des considérations supplémentaires lors de leur gestion et de la fourniture de services à vos utilisateurs.|Microsoft 365 E3 ou E5|
|Migration de boîtes aux lettres inter-clients|Les administrateurs de locataires peuvent déplacer des boîtes aux lettres entre des locataires avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela supprime la nécessité de désintégger et d’intégrer des boîtes aux lettres.|Microsoft 365 E3 ou E5|
|Multi-Géo|Votre locataire peut stocker des données au repos dans les autres emplacements géographiques du centre de données que vous avez choisis pour répondre aux exigences de résidence des données.|Microsoft 365 E3 ou E5|
|Déplacer des données de base vers une nouvelle zone géographique de centre de données|À mesure que Microsoft ajoute de nouvelles zones géographiques de centre de données pour des ressources de capacité et de calcul supplémentaires, vous pouvez demander un déplacement géographique du centre de données pour la résidence des données en zone géographique pour vos données client principales.|Microsoft 365 E3 ou E5|
||||

### <a name="networking"></a>Réseau

|Fonctionnalité|Description|Licence|
|---|---|---|
|Insights réseau|Métriques de performances réseau collectées auprès de votre locataire Microsoft 365 pour vous aider à concevoir des périmètres réseau pour vos emplacements de bureau.|Microsoft 365 E3 ou E5|
|Automatiser les mises à jour des points de terminaison|Automatiser la configuration et les mises à jour en cours pour les points de terminaison Microsoft 365 dans vos fichiers PAC clients et les appareils et services réseau.|Microsoft 365 E3 ou E5|
||||

### <a name="identity"></a>Identité

|Fonctionnalité|Description|Licence|
|---|---|---|
|Synchroniser жергілікті Active Directory Domain Services (AD DS) avec votre locataire Azure AD|Tirez parti de votre fournisseur d’identité local pour les comptes d’utilisateur, les groupes et d’autres objets.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec paramètres de sécurité par défaut|Protégez-vous contre les identités compromises et les appareils en imposant une deuxième forme d’authentification pour les connexions. La sécurité par défaut nécessite l’authentification multifacteur pour tous les comptes d’utilisateurs.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel|Exiger l’authentification multifacteur en fonction des attributs de la connexion avec des stratégies d’accès conditionnel.|Microsoft 365 E3 ou E5|
|Authentification multifacteur appliquée avec accès conditionnel basé sur les risques|Requiert une authentification multifacteur basée sur le risque de connexion de l’utilisateur avec Microsoft Defender pour identité.|Microsoft 365 E5 ou E3 avec les licences Azure AD Premium P2|
|Réinitialisation du mot de passe libre-service (SSPR)|Autoriser vos utilisateurs à réinitialiser ou déverrouiller leur mot de passe ou leur compte.|Microsoft 365 E3 ou E5|
||||

### <a name="migration"></a>Migration

|Fonctionnalité|Description|Licence|
|---|---|---|
|Mettre à jour vers Windows 10|Migrez vos appareils qui exécutent Windows 7 ou Windows 8.1 vers Windows 10 Entreprise.|Windows 10 Entreprise licences incluses avec Microsoft 365 E3 ou E5|
|Migrer vers Applications Microsoft 365 pour les grandes entreprises|Migrez vos applications clientes Office telles que Word et PowerPoint vers les versions installées à partir du cloud qui sont mises à jour avec de nouvelles fonctionnalités.|Microsoft 365 E3 ou E5|
|Migrer des serveurs et des données locaux vers Microsoft 365|Migrez vos boîtes aux lettres Exchange, vos sites SharePoint et Skype Entreprise Online vers les services cloud Microsoft 365.|Microsoft 365 E3 ou E5|
||||

### <a name="device-and-app-management"></a>Données de gestion des périphériques et des applications

|Fonctionnalité|Description|Licence|
|---|---|---|
|Microsoft Intune|Service cloud qui fournit la gestion des appareils mobiles (GPM) et la gestion des applications mobiles (MAM) pour contrôler la façon dont l’application et les appareils de votre organisation sont utilisés, notamment les téléphones mobiles, les tablettes et les ordinateurs portables.|Microsoft 365 E3 ou E5|
|Mobility + Security de Base|Sécurisez et gérez les appareils mobiles de vos utilisateurs tels que les iPhone, iPad, Android et téléphones Windows avec ce service intégré.|Microsoft 365 E3 ou E5|
||||

## <a name="next-steps"></a>Prochaines étapes

Procédez comme suit pour configurer et gérer vos locataires Microsoft 365.

1. [Déterminer vos locataires](tenant-management-tenants.md)
2. [Optimiser votre réseau](tenant-management-networking.md)
3. [Synchroniser vos identités et appliquer des connexions sécurisées](tenant-management-identity.md)
4. [Migrer vos serveurs et données Office locaux](tenant-management-migration.md)
5. [Déployer la gestion des appareils et des applications](tenant-management-device-management.md)

[![Étapes de déploiement et de gestion d’un locataire Microsoft 365.](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

Chaque étape décrit les options de déploiement, résume les résultats et les tâches de maintenance en cours.

Pour comprendre comment une organisation multinationale fictive mais représentative a déployé les éléments de son locataire Microsoft 365, consultez l’étude de [cas contoso](../enterprise/contoso-case-study.md).
