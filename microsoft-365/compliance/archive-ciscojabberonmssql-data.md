---
title: Configurer un connecteur pour archiver cisco Jabber sur MS SQL données dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver cisco Jabber sur MS SQL données de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 01899e4142d6e60fb10a101f7af8e9b4143a38c8
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51764299"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Configurer un connecteur pour archiver cisco Jabber sur MS SQL données

Utilisez un connecteur Veritas dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Cisco Jabber vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. Veritas vous fournit un connecteur [Cisco Jabber](https://globanet.com/jabber/) qui est configuré pour capturer des éléments du SQL Database MS de Jabber, tels que les messages de conversation 1:1 et les conversations de groupe, puis importer ces éléments dans Microsoft 365. Le connecteur récupère les données du SQL Database MS de Cisco Jabber, les traite et convertit le contenu du compte Cisco Jabber d’un utilisateur au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois les données Cisco Jabber stockées dans les boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Cisco Jabber pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Vue d’ensemble de l’archivage des données Cisco Jabber

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver Cisco Jabber sur MS SQL données dans Microsoft 365.

![Flux de travail d’archivage pour les données Cisco Jabber](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Votre organisation collabore avec Cisco pour configurer un Cisco Jabber sur MS SQL Database.

2. Une fois toutes les 24 heures, les éléments Cisco Jabber sont copiés du SQL Database MS vers le site Veritas Merge1. Le connecteur convertit également le contenu des messages de conversation au format de message électronique.

3. Le connecteur Cisco Jabber que vous créez dans le centre de conformité Microsoft 365 se connecte au site Veritas Merge1 tous les jours et transfère les éléments vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le mappage automatique des utilisateurs en tant que connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* de l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Cisco Jabber sur MS SQL** est créé dans les boîtes aux lettres utilisateur et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément Cisco Jabber contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://www.veritas.com/content/support/) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- Configurer une SQL Database MS pour récupérer des éléments Jabber avant de créer le connecteur à l’étape 1. Vous spécifiez les paramètres de connexion pour le SQL Database MS lors de la configuration du connecteur Cisco Jabber à l’étape 2. Pour plus d’informations, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur Cisco Jabber à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans le centre Microsoft 365 conformité. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Étape 1 : Configurer le connecteur Cisco Jabber sur MS SQL

La première étape consiste à accéder aux **connecteurs** de données dans le centre de conformité Microsoft 365 et à créer un connecteur pour Cisco Jabber sur MS SQL données.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Cisco Jabber on MS SQL**.

2. Dans la page de description du produit **Cisco Jabber SQL MS,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Cisco Jabber sur MS SQL sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Cisco Jabber sur MS SQL sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Cisco Jabber sur MS SQL, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur dans le centre Microsoft 365 conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la mise en place du connecteur dans le centre Microsoft 365 conformité, suivez les étapes suivantes :

1. Sur la carte **Cisco Jabber sur MS,** SQL aux utilisateurs Microsoft 365 la page Utilisateurs, activez le mappage automatique des utilisateurs. Les éléments de SQL Cisco Jabber sur MS incluent une propriété appelée *Email*, qui contient les adresses e-mail des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres et allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Étape 4 : Surveiller le connecteur Cisco Jabber

Après avoir créé le connecteur Cisco Jabber sur MS SQL, vous pouvez afficher l’état du connecteur dans le centre Microsoft 365 conformité.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur Cisco Jabber sur **MS SQL** pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
