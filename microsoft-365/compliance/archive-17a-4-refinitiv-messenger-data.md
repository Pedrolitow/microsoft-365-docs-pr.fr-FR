---
title: Configurer un connecteur pour archiver les données Refinitiv Eikon Messenger dans Microsoft 365
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
description: Découvrez comment configurer et utiliser un connecteur 17a-4 Refinitiv Eikon Messenger DataParser pour importer et archiver des données Refinitiv Eikon Messenger dans Microsoft 365.
ms.openlocfilehash: ec3a32a1fcf08747e8ad67983ae0c0aff2650673
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59178059"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>Configurer un connecteur pour archiver les données Refinitiv Eikon Messenger

Utilisez [Refinitiv Eikon Messenger DataParser](https://www.17a-4.com/refinitiv-messenger-dataparser/) de 17a-4 LLC pour importer et archiver des données de Refinitiv Eikon Messenger vers les boîtes aux lettres des utilisateurs de votre organisation Microsoft 365. DataParser inclut un connecteur Refinitiv Eikon Messenger configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur Refinitiv Eikon Messenger DataParser convertit les données Refinitiv Eikon Messenger au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365.

Une fois que les données Refinitiv Eikon Messenger sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Refinitiv Eikon Messenger pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>Vue d’ensemble de l’archivage des données Refinitiv Eikon Messenger

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver les données Refinitiv Eikon Messenger dans Microsoft 365.

![Flux de travail d’archivage pour les données Refinitiv Eikon Messenger de 17a-4.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec 17a-4 pour configurer refinitiv Eikon Messenger DataParser.

2. Régulièrement, les éléments Refinitiv Eikon Messenger sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur Refinitiv Eikon Messenger DataParser que vous créez dans le Centre de conformité Microsoft 365 se connecte à DataParser et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier du dossier Boîte de réception nommé **Refinitiv Eikon Messenger DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments Refinitiv Eikon Messenger sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément Refinitiv Eikon Messenger contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC.](https://www.17a-4.com/contact/) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Refinitiv Eikon Messenger DataParser à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 1 : Configurer un connecteur Refinitiv Eikon Messenger DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le Centre de conformité Microsoft 365 et à créer un connecteur 17a-4 pour les données Refinitiv Eikon Messenger.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **Refinitiv Eikon Messenger DataParser**.

2. Dans la page de description du produit **Refinitiv Eikon Messenger DataParser,** cliquez sur **Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et complétez les étapes de l’Assistant Connexion à Refinitiv Eikon Messenger DataParser.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 2 : Configurer le connecteur Refinitiv Eikon Messenger DataParser

Utiliser la prise en charge 17a-4 pour configurer le connecteur Refinitiv Eikon Messenger DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Ma cartographier les utilisateurs

Le connecteur Refinitiv Eikon Messenger DataParser maie automatiquement les utilisateurs à leurs adresses de messagerie Microsoft 365 avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 4 : Surveiller le connecteur Refinitiv Eikon Messenger DataParser

Après avoir créé un connecteur Refinitiv Eikon Messenger DataParser, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com> and click **Data connectors** in the left nav.

2. Cliquez sur l’onglet **Connecteurs,** puis sélectionnez le connecteur Refinitiv Eikon Messenger DataParser que vous avez créé pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
