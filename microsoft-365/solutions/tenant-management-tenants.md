---
title: Étape 1. Votre Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Déployez et gérez un ou plusieurs locataires Microsoft 365, avec des options pour les emplacements multigéographiques et mobiles.
ms.openlocfilehash: 39f7a2d4fb8f41366d5e18b6e95b15aaf81a7931
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585001"
---
# <a name="step-1-your-microsoft-365-for-enterprise-tenants"></a>Étape 1. Votre Microsoft 365 pour les locataires d’entreprise

L’une de vos premières décisions de locataire est le nombre à avoir. Chaque locataire Microsoft 365 est distinct, unique et distinct de tous les autres locataires Microsoft 365. Son locataire Azure AD correspondant est également distinct, unique et distinct de tous les autres locataires Microsoft 365.

## <a name="single-tenant"></a>Locataire unique
Le fait d’avoir un seul locataire simplifie de nombreux aspects de l’utilisation de Microsoft 365 par votre organisation. Un seul locataire signifie un seul locataire Azure AD avec un seul ensemble de comptes, de groupes et de stratégies. Les autorisations et le partage des ressources au sein de votre organisation peuvent être effectués via ce fournisseur d’identité central.

Un seul locataire offre à vos utilisateurs l’expérience de collaboration et de productivité la plus riche et la plus simplifiée.

Voici un exemple montrant l’emplacement par défaut et le locataire Azure AD d’un locataire Microsoft 365.

![Un seul locataire Microsoft 365 avec son locataire Azure AD.](../media/tenant-management-overview/tenant-management-example-tenant.png)

## <a name="multiple-tenants"></a>Plusieurs clients

Il existe de nombreuses raisons pour lesquelles votre organisation peut avoir plusieurs locataires :

- Isolation administrative
- Informatique décentralisée
- Décisions historiques
- Fusions, acquisitions ou cessions
- Séparation claire de la personnalisation pour les organisations conglomérates
- Locataires de préproduction, de test ou de bac à sable

Voici un exemple d’organisation qui a deux locataires (locataire A et locataire B) dans la même zone géographique de centre de données par défaut. Chaque locataire en tant que locataire Azure AD distinct.

![Plusieurs locataires Microsoft 365 avec leurs propres locataires Azure AD.](../media/tenant-management-overview/tenant-management-example-multi-tenant.png)

Lorsque vous avez plusieurs locataires, il existe des restrictions et des considérations supplémentaires lors de leur gestion et de la fourniture de services à vos utilisateurs.

### <a name="inter-tenant-collaboration"></a>Collaboration inter-clients

Si vous souhaitez que vos utilisateurs collaborent plus efficacement entre différents locataires Microsoft 365 de manière sécurisée, les options de collaboration entre locataires incluent l’utilisation d’un emplacement central pour les fichiers et les conversations, le partage de calendriers, l’utilisation de la messagerie instantanée, des appels audio/vidéo pour la communication et la sécurisation de l’accès aux ressources et aux applications.

Pour plus d’informations, consultez [la collaboration entre locataires Microsoft 365](../enterprise/microsoft-365-inter-tenant-collaboration.md).

### <a name="cross-tenant-mailbox-migration-preview"></a>Migration de boîte aux lettres entre locataires (préversion)

Avant la migration de boîtes aux lettres entre locataires (en préversion), lors du déplacement de Exchange Online boîtes aux lettres entre les locataires, vous devez déconnecter complètement une boîte aux lettres utilisateur de son locataire actuel (le locataire source) vers un locataire local, puis les intégrer à un nouveau locataire (le locataire cible). Avec la nouvelle fonctionnalité de migration de boîtes aux lettres entre locataires, les administrateurs de locataires des locataires source et cible peuvent déplacer des boîtes aux lettres entre les locataires avec des dépendances d’infrastructure minimales dans leurs systèmes locaux. Cela supprime la nécessité de désintégger et d’intégrer des boîtes aux lettres.

Voici deux exemples de locataires et leurs boîtes aux lettres avant la migration de boîtes aux lettres entre locataires.

![Plusieurs locataires Microsoft 365 et leurs boîtes aux lettres.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-before.png)

Dans cette illustration, deux locataires distincts ont leurs propres domaines et ensemble de boîtes aux lettres Exchange.

Voici le locataire cible (locataire A) après la migration de boîte aux lettres entre locataires.

![Locataire cible après la migration de boîtes aux lettres entre locataires.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-after.png)

Dans cette illustration, un seul locataire a à la fois des domaines et les deux ensembles de boîtes aux lettres Exchange.

Pour plus d’informations, consultez [migration de boîtes aux lettres entre locataires](../enterprise/cross-tenant-mailbox-migration.md).

### <a name="tenant-to-tenant-migrations"></a>Migrations client vers client

Il existe plusieurs approches architecturales pour les fusions, les acquisitions, les cessions et d’autres scénarios qui peuvent vous amener à migrer un locataire Microsoft 365 existant vers un nouveau locataire. 

Pour obtenir des conseils détaillés, consultez [les migrations de locataire à locataire De Microsoft 365](../enterprise/microsoft-365-tenant-to-tenant-migrations.md).

## <a name="multi-geo-for-a-tenant"></a>Multigéographique pour un locataire

Avec Microsoft 365 Multi-Geo, vous pouvez provisionner et stocker des données au repos dans les autres emplacements géographiques de centre de données que vous avez choisis pour répondre aux exigences de résidence des données, tout en déverrouillez votre déploiement global d’expériences de productivité modernes pour vos employés.

Dans un environnement multigéographique, votre locataire Microsoft 365 se compose d’un emplacement par défaut ou central où votre abonnement Microsoft 365 a été créé à l’origine et d’un ou plusieurs emplacements satellites. Dans un locataire multigéographique, les informations sur les emplacements géographiques, les groupes et les informations utilisateur sont maîtrisées dans un locataire Azure AD global. Étant donné que les informations de votre locataire sont maîtrisées de manière centralisée et synchronisées dans chaque emplacement géographique, les expériences de collaboration impliquant toute personne de votre entreprise sont partagées entre les emplacements.

Voici un exemple d’organisation qui a son emplacement par défaut en Europe et un emplacement satellite dans Amérique du Nord. Les deux emplacements partagent le même locataire Azure AD global pour le seul locataire Microsoft 365.

![Exemple de locataire Microsoft 365 multigéographique.](../media/tenant-management-overview/tenant-management-example-multi-geo.png)

Pour en savoir plus, consultez [Microsoft 365 Multigéographie](../enterprise/microsoft-365-multi-geo.md).

## <a name="moving-core-data-to-a-new-datacenter-geo"></a>Déplacement de données de base vers une nouvelle zone géographique de centre de données

Microsoft continue d’ouvrir de nouvelles zones géographiques de centre de données pour les services Microsoft 365. Ces nouvelles régions de centre de données permettent d'accroître la capacité et le nombre de ressources de calcul pour prendre en charge la demande continue des clients et l'augmentation de l'utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Bien que l’ouverture d’une nouvelle zone géographique de centre de données n’ait pas d’impact sur vous et vos données principales stockées dans une zone géographique de centre de données déjà existante, Microsoft vous permet de demander une migration anticipée des données client principales de votre organisation au repos vers une nouvelle zone géographique de centre de données.

Voici un exemple dans lequel un locataire Microsoft 365 a été déplacé de la zone géographique du centre de données de l’Union européenne (UE) vers celui situé au Royaume-Uni (Royaume-Uni).

![Exemple de déplacement d’un locataire Microsoft 365 entre les zones géographiques du centre de données.](../media/tenant-management-overview/tenant-management-example-tenant-move.png)

Pour plus d’informations, consultez [Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365](../enterprise/moving-data-to-new-datacenter-geos.md).

## <a name="products-and-licenses-for-a-tenant"></a>Produits et licences pour un locataire

Votre locataire Microsoft 365 est créé lorsque vous achetez votre premier produit, par exemple Microsoft 365 E3. Avec le produit sont des licences, qui sont facturés des frais mensuels ou annuels. Un administrateur attribue ensuite une licence disponible à partir de l’un de vos produits à un compte d’utilisateur, directement ou par le biais de l’appartenance au groupe. En fonction des besoins métier de votre organisation, vous pouvez avoir un ensemble de produits, chacun avec son propre pool de licences. 

La détermination de l’ensemble de produits et du nombre de licences pour chacun d’eux nécessite une planification pour :

- Vérifiez que vous disposez de suffisamment de licences pour les comptes d’utilisateur qui ont besoin de fonctionnalités avancées.
- Empêchez-vous de manquer de licences ou d’avoir trop de licences non attribuées, en fonction des modifications apportées au personnel de votre organisation.


## <a name="results-of-step-1"></a>Résultats de l’étape 1

Pour votre Microsoft 365 pour les locataires d’entreprise, vous avez déterminé :

- Nombre de locataires dont vous avez besoin ou dont vous avez besoin.
- Pour chaque locataire, quels produits et licences doivent être achetés.
- Indique si un locataire doit être multigéographique pour se conformer aux exigences de résidence des données.
- Indique si vous devez configurer la collaboration entre locataires.
- Indique si vous devez migrer un locataire vers un autre.
- Indique si vous devez déplacer des données de base d’une zone géographique de centre de données vers une nouvelle.

Voici un exemple de nouveau locataire.

![Exemple de nouveau locataire.](../media/tenant-management-overview/tenant-management-tenant-build-step1.png)

Dans cette illustration, le locataire a :

- Emplacement par défaut correspondant à une zone géographique de centre de données Microsoft 365.
- Ensemble de produits et de licences.
- Ensemble d’applications de productivité cloud, dont certaines sont spécifiques aux produits.
- Un locataire Azure AD qui contient des comptes d’administrateur général et un nom de domaine DNS initial.

À mesure que nous parcourons les étapes supplémentaires de cette solution, nous allons créer ce chiffre.

## <a name="ongoing-maintenance-for-tenants"></a>Maintenance en cours pour les locataires

De façon continue, vous devrez peut-être :

- Ajoutez un nouveau locataire.
- Ajoutez de nouveaux produits à un locataire avec un nombre initial de licences.
- Modifiez l’ensemble des licences d’un produit dans un locataire afin de l’ajuster en fonction de l’évolution des exigences du personnel.
- Déplacez vos données principales d’un locataire vers un nouvel emplacement géographique de centre de données.
- Ajoutez multigéographique pour les exigences de résidence des données.
- Configurez la collaboration entre locataires.

## <a name="next-step"></a>Étape suivante

[![Étape 2. Optimisez votre locataire pour le réseau pour l’accès.](../media/tenant-management-overview/tenant-management-step-grid-networking.png)](tenant-management-networking.md)

Continuez avec [la mise en réseau](tenant-management-networking.md) pour fournir une mise en réseau optimale de vos employés vers les services cloud Microsoft 365.
