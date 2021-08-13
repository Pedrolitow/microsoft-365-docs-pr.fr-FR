---
title: Configurer un connecteur pour archiver les données livePerson Conversational Cloud dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur LivePerson Conversational Cloud DataParser 17a-4 pour importer et archiver des données LivePerson Conversational Cloud dans Microsoft 365.
ms.openlocfilehash: a06de3699c46a57074d125c74c777c4ea8a8a1e6f87aafbbc8c2364acb82c49c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53808826"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>Configurer un connecteur pour archiver les données LivePerson Conversational Cloud

Utilisez [LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) de 17a-4 LLC pour importer et archiver des données de LivePerson Conversational Cloud vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. DataParser inclut un connecteur LivePerson Conversational Cloud configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur LivePerson Conversational Cloud DataParser convertit les données au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois les données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la découverte électronique, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur LivePerson Conversational Cloud pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>Vue d’ensemble de l’archivage des données du cloud conversationnel LivePerson

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver des données LivePerson Conversational Cloud dans Microsoft 365.

![Flux de travail d’archivage pour les données LivePerson Conversational Cloud de 17a-4](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec 17a-4 pour configurer LivePerson Conversational Cloud DataParser.

2. Régulièrement, les éléments LivePerson Conversational Cloud sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur LivePerson Conversational Cloud DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier du dossier Boîte de réception nommé **LivePerson Conversational Cloud DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC.](https://www.17a-4.com/contact/) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur LivePerson Conversational Cloud DataParser à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>Étape 1 : Configurer un connecteur LivePerson Conversational Cloud DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour les données LivePerson Conversational Cloud.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **LivePerson Conversational Cloud DataParser**.

2. Dans la page de description du produit **LivePerson Conversational Cloud DataParser,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l’Assistant Connexion LivePerson Conversational Cloud DataParser.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 2 : Configurer le connecteur LivePerson Conversational Cloud DataParser

Travaillez avec la prise en charge 17a-4 pour configurer le connecteur LivePerson Conversational Cloud DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le connecteur LivePerson Conversational Cloud DataParser maîtra automatiquement les utilisateurs à leurs adresses Microsoft 365 messagerie avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 4 : Surveiller le connecteur LivePerson Conversational Cloud DataParser

Après avoir créé un connecteur LivePerson Conversational Cloud DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur l’onglet **Connecteurs,** puis sélectionnez le connecteur LivePerson Conversational Cloud DataParser que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
