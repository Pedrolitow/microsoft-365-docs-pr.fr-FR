---
title: Configurer un connecteur pour archiver les données de LivePerson Conversational Cloud dans Microsoft 365
description: Découvrez comment configurer et utiliser un connecteur LivePerson Conversational Cloud DataParser 17a-4 pour importer et archiver des données LivePerson Conversational Cloud dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.openlocfilehash: e470eb57260cbbf037ac3781f6d73a582ac65cbf
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68534605"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>Configurer un connecteur pour archiver les données de LivePerson Conversational Cloud

Utilisez [LivePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) de 17a-4 LLC pour importer et archiver des données de LivePerson Conversational Cloud vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. DataParser inclut un connecteur LivePerson Conversational Cloud configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur LivePerson Conversational Cloud DataParser convertit les données au format d’e-mail, puis importe ces éléments dans des boîtes aux lettres utilisateur dans Microsoft 365.

Une fois les données stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur LivePerson Conversational Cloud pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>Vue d’ensemble de l’archivage des données de LivePerson Conversational Cloud

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver des données LivePerson Conversational Cloud dans Microsoft 365.

![Flux de travail d’archivage des données LivePerson Conversational Cloud de 17a à 4.](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec la version 17a-4 pour configurer livePerson Conversational Cloud DataParser.

2. Régulièrement, les éléments LivePerson Conversational Cloud sont collectés par DataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur LivePerson Conversational Cloud DataParser que vous créez dans le portail de conformité Microsoft Purview se connecte à DataParser et transfère les messages à un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier dans le dossier boîte de réception nommé **LivePerson Conversational Cloud DataParser** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres vers laquelle importer des éléments à l’aide de la valeur de la propriété *Email*. Chaque élément contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [le 17a-4 LLC](https://www.17a-4.com/contact/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur LivePerson Conversational Cloud DataParser à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données 17a-4 est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>Étape 1 : Configurer un connecteur LivePerson Conversational Cloud DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le portail de conformité et à créer un connecteur 17a-4 pour les données LivePerson Conversational Cloud.

1. Accédez, <https://compliance.microsoft.com> puis sélectionnez Data **Connectors** > **LivePerson Conversational Cloud DataParser**.

2. Dans la page de description du produit **LivePerson Conversational Cloud DataParser** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte 17a-4 et suivez les étapes de l’Assistant Connexion LivePerson Conversational Cloud DataParser.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 2 : Configurer le connecteur LivePerson Conversational Cloud DataParser

Utilisez le support 17a-4 pour configurer le connecteur LivePerson Conversational Cloud DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Mapper les utilisateurs

Le connecteur LivePerson Conversational DataParser mappe automatiquement les utilisateurs à leurs adresses e-mail Microsoft 365 avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 4 : Surveiller le connecteur LivePerson Conversational Cloud DataParser

Après avoir créé un connecteur LivePerson Conversational Cloud DataParser, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez aux <https://compliance.microsoft.com> **connecteurs de données** et sélectionnez-les dans le volet de navigation gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur LivePerson Conversational Cloud DataParser que vous avez créé pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **sélectionnez** le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
