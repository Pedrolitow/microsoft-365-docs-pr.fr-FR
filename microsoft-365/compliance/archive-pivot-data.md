---
title: Configurer un connecteur pour archiver les données de tableau croisé dynamique dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de tableau croisé dynamique à partir de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: baf4c781462fa27b39f7c6432ccef32cc7c80fec
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180052"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Configurer un connecteur pour archiver des données de tableau croisé dynamique

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Pivot vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. Veritas vous fournit [](https://globanet.com/pivot/) un connecteur de tableau croisé dynamique qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement), puis importer ces éléments dans Microsoft 365. Pivot est une plateforme de messagerie instantanée qui permet la collaboration avec les participants aux marchés financiers. Le connecteur convertit des éléments tels que des messages de conversation, des comptes Pivot d’un utilisateur au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

Une fois les données Pivot stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur pivot pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-pivot-data"></a>Vue d’ensemble des données du tableau croisé dynamique d’archivage

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de tableau croisé dynamique Microsoft 365.

![Flux de travail d’archivage pour les données pivot.](../media/PivotConnectorWorkflow.png)

1. Votre organisation travaille avec Pivot pour configurer et configurer un site source De tableau croisé dynamique.

2. Toutes les 24 heures, les éléments pivot sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Pivot au format de message électronique.

3. Le connecteur de tableau croisé dynamique que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère les éléments pivot vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments pivot dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage utilisateur automatique, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Pivot** est créé dans les boîtes aux lettres de l’utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque élément pivot contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://www.veritas.com/content/support/) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur de tableau croisé dynamique à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page Connecteurs de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-pivot-connector"></a>Étape 1 : Configurer le connecteur pivot

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft et à créer un connecteur pour les données pivot.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Pivot**.

2. Dans la page description du produit **Pivot,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-pivot-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur pivot sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur pivot sur le site Merge1. Pour plus d’informations sur la configuration du connecteur de tableau croisé dynamique sur le site Veritas Merge1, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 356, suivez les étapes suivantes :

1. Dans la page Ma mappage des utilisateurs **Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs. Les éléments pivot incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres et allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-pivot-connector"></a>Étape 4 : Surveiller le connecteur de tableau croisé dynamique

Après avoir créé le connecteur de tableau croisé dynamique, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **de tableau croisé** dynamique pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.