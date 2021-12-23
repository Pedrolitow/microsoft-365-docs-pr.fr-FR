---
title: Configurer un connecteur pour archiver des données Twitter dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données Twitter de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, eDiscovery et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 04730353ae6b99e79cdb280307759900804db925
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2021
ms.locfileid: "61587101"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Configurer un connecteur pour archiver les données Twitter (aperçu)

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Twitter vers des boîtes aux lettres utilisateur dans Microsoft 365 organisation. Veritas fournit un connecteur [Twitter](https://www.veritas.com/insights/merge1/twitter) qui est configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur convertit du contenu tel que des tweet, des retweets et des commentaires de Twitter au format de message électronique, puis importe ces éléments dans les boîtes aux lettres de l’utilisateur Microsoft 365.

Une fois les données Twitter stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Twitter pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-twitter-data"></a>Vue d’ensemble de l’archivage des données Twitter

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Twitter dans Microsoft 365.

![Flux de travail d’archivage pour les données Twitter.](../media/VeritasTwitterConnectorWorkflow.png)

1. Votre organisation travaille avec Twitter pour configurer un site Twitter. Votre organisation collabore également avec Veritas pour configurer un site Merge1.

2. Une fois toutes les 24 heures, les éléments Twitter sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Twitter au format de message électronique.

3. Le connecteur Twitter que vous créez dans le Centre de conformité Microsoft 365 se connecte au site Veritas Merge1 tous les jours et transfère le contenu Twitter vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Twitter** est créé dans les boîtes aux lettres de l’utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément Twitter contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://www.veritas.com/form/requestacall/ms-connectors-contact) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application Twitter pour <https://developer.twitter.com> récupérer des données à partir de votre compte Twitter. Pour obtenir des instructions détaillées sur la création de l’application, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

- L’utilisateur qui crée le connecteur YouTube à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-twitter-connector"></a>Étape 1 : Configurer le connecteur Twitter

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 créer un connecteur pour les données Twitter.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **Twitter**.

2. Dans la page de description du produit **Twitter,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-twitter-on-the-veritas-merge1-site"></a>Étape 2 : Configurer Twitter sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Twitter sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Twitter, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

Une fois que vous avez **cliqué sur & terminé,** la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page **Mappage des utilisateurs Twitter Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs. Les éléments Twitter incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-twitter-connector"></a>Étape 4 : Surveiller le connecteur Twitter

Après avoir créé le connecteur Twitter, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **Twitter** pour afficher la page volante, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.