---
title: Configurer un connecteur pour archiver des données délimitées par du texte Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données délimitées par du texte à partir de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 0d1175c51be57845f39d16b9522862b2d63d666c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313242"
---
# <a name="set-up-a-connector-to-archive-text-delimited-data"></a>Configurer un connecteur pour archiver des données délimitées par du texte

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données délimitées par du texte dans des boîtes aux lettres utilisateur dans Microsoft 365 organisation. Veritas fournit un [](https://globanet.com/text-delimited) connecteur délimité par du texte qui est configuré pour capturer des éléments à partir d’une source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu de la source de données délimitée par du texte au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données délimitées par du texte sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery et les stratégies et étiquettes de rétention. L’utilisation d’un connecteur de données délimité par du texte pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-the-text-delimited-data"></a>Vue d’ensemble de l’archivage des données délimitées par du texte

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des informations sources délimitées par du texte Microsoft 365.

![Flux de travail d’archivage pour les données délimitées par du texte.](../media/TextDelimitedConnectorWorkflow.png)

1. Votre organisation travaille avec la source délimitée par du texte pour configurer un site délimité par du texte.

2. Une fois toutes les 24 heures, les messages de conversation de la source délimitée par du texte sont copiés sur le site Veritas Merge1. Le connecteur convertit également le contenu au format de message électronique.

3. Le connecteur délimité par du texte que vous créez dans le Centre de conformité Microsoft 365 se connecte au site Veritas Merge1 tous les jours et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de message convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape 3. Un nouveau **sous-dossier** dans le dossier Boîte de réception nommé Texte délimité est créé dans les boîtes aux lettres utilisateur et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email* . Chaque message contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez [le support technique Veritas](https://globanet.com/ms-connectors-contact). Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur délimité par du texte à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en prévisualisation publique dans Cloud de la communauté du secteur public environnements dans Microsoft 365 cloud du gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-text-delimited-connector"></a>Étape 1 : Configurer le connecteur délimité par du texte

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 et à créer un connecteur pour les données délimitées par du texte.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click **Data connectorsText-Delimited** > .

2. Dans la page **de description du** produit délimitée par du texte, cliquez **sur Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-text-delimited-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur délimité par du texte sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur délimité par du texte sur le site Merge1. Pour plus d’informations sur la configuration du connecteur délimité par du texte sur le site Veritas Merge1, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20text-delimited%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur Enregistrer &** terminé, **la page** Mappage de l’utilisateur dans l’Assistant connecteur dans la Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page **Mappage des utilisateurs externes Microsoft 365 utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments sources délimités par du texte incluent une propriété appelée *Courrier* électronique, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis consultez la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-text-delimited-connector"></a>Étape 4 : Surveiller le connecteur délimité par du texte

Après avoir créé le connecteur délimité par du texte, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs**, puis  sélectionnez le connecteur délimité par du texte pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **cliquez sur le** lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.