---
title: Configurer un connecteur pour archiver les données Fx de Reuters dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données Fx De Reuters à partir de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 1252fd1c2f54e08a29c12b19c1cc07791b89a027
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176164"
---
# <a name="set-up-a-connector-to-archive-reuters-fx-data"></a>Configurer un connecteur pour archiver les données FX de Reuters

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme FX De Reuters vers des boîtes aux lettres utilisateur dans votre Microsoft 365 organisation. Veritas vous fournit un connecteur [FX De Reuters](https://globanet.com/reuters-fx/) qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement), puis importer ces éléments dans Microsoft 365. Le connecteur convertit les devises et les taux de change du compte FX De Reuters au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données FX de Reuters sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur FX De Reuters pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-reuters-fx-data"></a>Vue d’ensemble de l’archivage des données FX de Reuters

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Fx De Reuters dans Microsoft 365.

![Flux de travail d’archivage pour les données FX de Reuters.](../media/ReutersFXConnectorWorkflow.png)

1. Votre organisation travaille avec Reuters FX pour configurer un site FX De Reuters.

2. Une fois toutes les 24 heures, les éléments FX de Reuters sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments au format de message électronique.

3. Le connecteur FX De Reuters que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère le contenu vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage utilisateur automatique, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Reuters FX** est créé dans les boîtes aux lettres de l’utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément FX De Reuters contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le support [technique Veritas.](https://globanet.com/contact-us) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Fx De Reuters à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-reuters-fx-connector"></a>Étape 1 : Configurer le connecteur FX De Reuters

La première étape consiste à accéder à la page **Connecteurs** de données dans le Microsoft 365 et à créer un connecteur pour les données FX de Reuters.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Reuters FX**.

2. Dans la page de description du produit **Fx De Reuters,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-reuters-fx-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Fx De Reuters sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur FX De Reuters sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur FX De Reuters, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20FX%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes ci-dessous :

1. Dans la page **Mappage des utilisateurs FX de Reuters Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs.

   Les éléments FX de Reuters incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres et allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-reuters-fx-connector"></a>Étape 4 : Surveiller le connecteur FX De Reuters

Après avoir créé le connecteur FX De Reuters, vous pouvez afficher l’état du connecteur dans la Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **FX De Reuters** pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.