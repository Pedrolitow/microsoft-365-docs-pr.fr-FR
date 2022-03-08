---
title: Configurer un connecteur pour archiver les données de la base de données MS SQL
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de MS SQL Database. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: f00b76cb2199d1af9daca58e86ad7cd2009c2031
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315692"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>Configurer un connecteur pour archiver les données de la base de données MS SQL

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la base de données MS SQL vers les boîtes aux lettres des utilisateurs de votre organisation Microsoft 365. Veritas vous fournit un connecteur d’importateur de base de données MS SQL configuré pour capturer des éléments d’une base de données à l’aide d’un fichier de configuration XML et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu de la base de données MS SQL au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

Après le contenu de la base de données MS SQL stockée dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur de base de données MS SQL pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-the-ms-sql-data"></a>Vue d’ensemble de l’archivage des données de SQL MS

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données SQL MS dans Microsoft 365.

![Flux de travail d’archivage pour MS SQL données.](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Votre organisation collabore avec un fournisseur de base de données MS SQL pour configurer un site MS SQL Database.

2. Toutes les 24 heures, MS SQL base de données sont copiés sur le site Veritas Merge1. Le connecteur convertit également ce contenu au format de message électronique.

3. Le connecteur d’importateur de base de données MS SQL que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de base de données MS SQL convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **MS SQL Database Importer** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email* . Chaque élément de la base de données SQL MS contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez [le support technique Veritas](https://www.veritas.com/content/support/). Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur d’importateur de base de données MS SQL à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans Autorisations dans le Centre de conformité [Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en prévisualisation publique dans les environnements GCC dans le cloud Microsoft 365 pour le gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements de conformité et de protection des données de Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>Étape 1 : Configurer le connecteur d’importateur de base de données SQL MS

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 et à créer un connecteur pour la base de données MS SQL.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click **Data connectorsMS** >  **SQL Database Importer**.

2. Dans la page **description du produit MS SQL Database Importer** , cliquez **sur Ajouter un nouveau connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur ms SQL importer de base de données sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur ms SQL Importer de base de données sur le site Merge1. Pour plus d’informations sur la configuration de l’importateur SQL base de données MS, consultez le [guide utilisateur Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur Enregistrer &** terminé, **la page** Mappage de l’utilisateur dans l’Assistant Connecteur dans le Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur, suivez les étapes suivantes :

1. Dans la page Ma SQL utilisateurs de l’importateur de base de données aux utilisateurs **Microsoft 365** , activez le mappage automatique des utilisateurs. Les éléments de base de données SQL MS incluent une propriété appelée *Courrier* électronique, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres et consultez la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>Étape 4 : Surveiller le connecteur d’importateur de base de données SQL MS

Après avoir créé le connecteur ms SQL d’importateur de base de données, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs** , puis sélectionnez le connecteur **MS SQL Database** **Importer** pour afficher la page volante, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **cliquez sur le** lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.