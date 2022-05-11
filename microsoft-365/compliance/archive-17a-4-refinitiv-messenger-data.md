---
title: Configurer un connecteur pour archiver les données Refinitiv Ekono Messenger dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Découvrez comment configurer et utiliser un connecteur 17a-4 Refinitiv Ekono Messenger DataParser pour importer et archiver ces données dans Microsoft 365.
ms.openlocfilehash: b875c61160961228960e2f1f3921cc2b55b2fd54
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65316851"
---
# <a name="set-up-a-connector-to-archive-refinitiv-eikon-messenger-data"></a>Configurer un connecteur pour archiver les données Refinitiv Ekono Messenger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez [refinitiv Ekono Messenger DataParser](https://www.17a-4.com/refinitiv-messenger-dataparser/) de 17a-4 LLC pour importer et archiver des données de Refinitiv Ekono Messenger vers les boîtes aux lettres utilisateur de votre organisation Microsoft 365. DataParser inclut un connecteur Refinitiv Ekono Messenger configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur Refinitiv Ekono Messenger DataParser convertit les données Refinitiv Ekono Messenger au format de message électronique, puis importe ces éléments dans des boîtes aux lettres utilisateur dans Microsoft 365.

Une fois que les données Refinitiv Ekono Messenger sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer Microsoft Purview fonctionnalités telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Refinitiv Ekono Messenger pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux politiques gouvernementales et réglementaires.

## <a name="overview-of-archiving-refinitiv-eikon-messenger-data"></a>Vue d’ensemble de l’archivage des données Refinitiv Ekono Messenger

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver des données Refinitiv Ekono Messenger dans Microsoft 365.

![Flux de travail d’archivage pour les données Refinitiv Ekono Messenger de la version 17a-4.](../media/RefinitivMessengerDataParserConnectorWorkflow.png)

1. Votre organisation travaille avec la version 17a-4 pour configurer refinitiv Ekono Messenger DataParser.

2. Régulièrement, les éléments Refinitiv Ekono Messenger sont collectés par dataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur Refinitiv Ekono Messenger DataParser que vous créez dans le portail de conformité Microsoft Purview se connecte à DataParser et transfère les messages à un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier dans le dossier de boîte de réception nommé **Refinitiv Ekono Messenger DataParser** est créé dans les boîtes aux lettres utilisateur, et les éléments Refinitiv Ekono Messenger sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres vers laquelle importer des éléments à l’aide de la valeur de la propriété *Email* . Chaque élément Refinitiv Ekono Messenger contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour créer un compte, contactez [le 17a-4 LLC](https://www.17a-4.com/contact/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Refinitiv Ekono Messenger DataParser à l’étape 1 (et le termine à l’étape 3) doit avoir le rôle Administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données 17a-4 est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-a-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 1 : Configurer un connecteur Refinitiv Ekono Messenger DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le portail de conformité et à créer un connecteur 17a-4 pour les données Refinitiv Ekono Messenger.

1. Accédez à <https://compliance.microsoft.com> **Data connectorsRefinitiv** >  **Ekono Messenger DataParser**, puis cliquez dessus.

2. Dans la page de description du produit **Refinitiv Ekono Messenger DataParser** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte 17a-4 et suivez les étapes de l’Assistant connexion Refinitiv Ekono Messenger DataParser.

## <a name="step-2-configure-the-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 2 : Configurer le connecteur Refinitiv Ekono Messenger DataParser

Collaborez avec le support 17a-4 pour configurer le connecteur Refinitiv Ekono Messenger DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Mapper les utilisateurs

Le connecteur Refinitiv Ekono Messenger DataParser mappe automatiquement les utilisateurs à leurs adresses e-mail Microsoft 365 avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-refinitiv-eikon-messenger-dataparser-connector"></a>Étape 4 : Surveiller le connecteur Refinitiv Ekono Messenger DataParser

Après avoir créé un connecteur Refinitiv Ekono Messenger DataParser, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et <https://compliance.microsoft.com> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur Refinitiv Ekono Messenger DataParser que vous avez créé pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes détectés

Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
