---
title: Configurer un connecteur pour archiver les données du cloud conversationnel LivePerson dans Microsoft 365
description: Découvrez comment configurer et utiliser un connecteur 17a-4 LivePerson Conversational Cloud DataParser pour importer et archiver des données LivePerson Conversational Cloud dans Microsoft 365.
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
ms.openlocfilehash: c99762899fb97869413fdb123e93723e6dcca2ff
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68812776"
---
# <a name="set-up-a-connector-to-archive-liveperson-conversational-cloud-data"></a>Configurer un connecteur pour archiver les données du cloud conversationnel LivePerson

Utilisez [livePerson Conversational Cloud DataParser](https://www.17a-4.com/liveperson-dataparser/) de 17a-4 LLC pour importer et archiver des données de LivePerson Conversational Cloud dans les boîtes aux lettres utilisateur de votre organisation Microsoft 365. DataParser inclut un connecteur cloud conversationnel LivePerson configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur LivePerson Conversational Cloud DataParser convertit les données au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

Une fois les données stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention, et la conformité des communications. L’utilisation d’un connecteur de cloud conversationnel LivePerson pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-liveperson-conversational-cloud-data"></a>Vue d’ensemble de l’archivage des données du cloud conversationnel LivePerson

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données pour archiver des données LivePerson Conversational Cloud dans Microsoft 365.

![Flux de travail d’archivage pour les données du cloud conversationnel LivePerson à partir de 17a-4.](../media/LiveEngageDataParserConnectorWorkflow.png)

1. Votre organisation utilise 17a-4 pour configurer le LivePerson Conversational Cloud DataParser.

2. Régulièrement, les éléments du cloud conversationnel LivePerson sont collectés par dataParser. DataParser convertit également le contenu d’un message au format de message électronique.

3. Le connecteur LivePerson Conversational Cloud DataParser que vous créez dans le portail de conformité Microsoft Purview se connecte à DataParser et transfère les messages vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Un sous-dossier dans le dossier Boîte de réception nommé **LivePerson Conversational Cloud DataParser** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *Email*. Chaque élément contient cette propriété, qui est renseignée avec l’adresse e-mail de chaque participant.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte DataParser pour les connecteurs Microsoft. Pour ce faire, contactez [17a-4 LLC](https://www.17a-4.com/contact/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur LivePerson Conversational Cloud DataParser à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données 17a-4 est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui se trouvent en dehors de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune déclaration selon laquelle l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes à FEDRAMP.

## <a name="step-1-set-up-a-liveperson-conversational-cloud-dataparser-connector"></a>Étape 1 : Configurer un connecteur LivePerson Conversational Cloud DataParser

La première étape consiste à accéder à la page Connecteurs de données dans le portail de conformité et à créer un connecteur 17a-4 pour les données du cloud conversationnel LivePerson.

1. Accédez à <https://compliance.microsoft.com> , puis sélectionnez **Connecteurs** >  de données **LivePerson Conversational Cloud DataParser**.

2. Dans la page de description du produit **LivePerson Conversational Cloud DataParser** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte 17a-4 et suivez les étapes décrites dans l’Assistant connexion LivePerson Conversational Cloud DataParser.

## <a name="step-2-configure-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 2 : Configurer le connecteur LivePerson Conversational Cloud DataParser

Utilisez la prise en charge 17a-4 pour configurer le connecteur LivePerson Conversational Cloud DataParser.

## <a name="step-3-map-users"></a>Étape 3 : Mapper les utilisateurs

Le connecteur LivePerson Conversational Cloud DataParser mappera automatiquement les utilisateurs à leurs adresses e-mail Microsoft 365 avant d’importer des données dans Microsoft 365.

## <a name="step-4-monitor-the-liveperson-conversational-cloud-dataparser-connector"></a>Étape 4 : Surveiller le connecteur LivePerson Conversational Cloud DataParser

Après avoir créé un connecteur LivePerson Conversational Cloud DataParser, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur LivePerson Conversational Cloud DataParser que vous avez créé pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec la source**, sélectionnez le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’activité d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments d’une taille supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
