---
title: Configurer un connecteur DataParser pour archiver des données dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Découvrez comment configurer et utiliser un connecteur DataParser 17a-4 Sonta-4 Pour importer et archiver des données De la bibliothèque dans Microsoft 365.
ms.openlocfilehash: cc4755c3566a25f659d3fd610157b3a6fa29d0a7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314656"
---
# <a name="set-up-a-connector-to-archive-data-from-symphony"></a>Configurer un connecteur pour archiver des données à partir de Usby

Utilisez [l’analyseur](https://www.17a-4.com/Symphony-dataparser/) de données de 17a-4 LLC pour importer et archiver les données de communications De Lasy dans les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. DataParser inclut un connecteur Deparsy configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur DataParser de TypeMenty convertit les données Deparse au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois les données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la découverte électronique, les stratégies et étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur de Typey pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-symphony-data"></a>Vue d’ensemble de l’archivage des données

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver des données à l’Microsoft 365.

![Flux de travail d’archivage pour les données de 17a-4.](../media/SymphonyDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec le 17a-4 pour configurer l’analyseur de données DeParser.

2. Régulièrement, les éléments de la collection Sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier dans le dossier Boîte de réception **nomméParseur de données DeParser est** créé dans les boîtes aux lettres de l’utilisateur et les éléments Sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email* . Chaque élément Dezy contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC](https://www.17a-4.com/contact/). Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur DataParser à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données 17a-4 est disponible dans les environnements Cloud de la communauté du secteur public dans le cloud Microsoft 365 gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-a-symphony-dataparser-connector"></a>Étape 1 : Configurer un connecteur DataParser de qualité

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour les données de Type.

1. Go to <https://compliance.microsoft.com> and then click **Data connectorsSymphony** >  **DataParser**.

2. Dans la page **de description du produit DataParser** , cliquez **sur Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l’Assistant Connexion DataParser.

## <a name="step-2-configure-the-symphony-dataparser-connector"></a>Étape 2 : Configurer le connecteur DataParser de Type de données

Travaillez avec la prise en charge 17a-4 pour configurer le connecteur DataParser DeParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le connecteur DataParser de TypeMenty maie automatiquement les utilisateurs à leurs adresses Microsoft 365 courrier avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-symphony-dataparser-connector"></a>Étape 4 : Surveiller le connecteur DataParser

Après avoir créé un connecteur DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs** , puis sélectionnez le connecteur Propriétés dataParser que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **cliquez sur le** lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
