---
title: Configurer un connecteur pour archiver les données Twitter dans Microsoft 365
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données Twitter de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, l’eDiscovery et les stratégies de rétention pour gérer les données tierces.
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
ms.openlocfilehash: d46b60dd355200e16cb65e90ae7c200b979ad3e7
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68813289"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Configurer un connecteur pour archiver les données Twitter (préversion)

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de la plateforme Twitter dans les boîtes aux lettres des utilisateurs de votre organisation Microsoft 365. Veritas fournit un connecteur [Twitter](https://www.veritas.com/insights/merge1/twitter) configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les tweets, les retweets et les commentaires de Twitter au format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois les données Twitter stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Twitter pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-twitter-data"></a>Vue d’ensemble de l’archivage des données Twitter

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Twitter dans Microsoft 365.

![Flux de travail d’archivage pour les données Twitter.](../media/VeritasTwitterConnectorWorkflow.png)

1. Votre organisation travaille avec Twitter pour configurer et configurer un site Twitter. Votre organisation travaille également avec Veritas pour configurer un site Merge1.

2. Une fois toutes les 24 heures, les éléments Twitter sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Twitter au format de message électronique.

3. Le connecteur Twitter que vous créez dans le portail de conformité se connecte au site Veritas Merge1 tous les jours et transfère le contenu Twitter vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier dans le dossier Boîte de réception nommé **Twitter** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *Email*. Chaque élément Twitter contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application Twitter sur <https://developer.twitter.com> pour récupérer des données à partir de votre compte Twitter. Pour obtenir des instructions pas à pas sur la création de l’application, consultez [Merge1 Third-Party Connectors User Guide ( Guide de l’utilisateur de Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf)).

- L’utilisateur qui crée le connecteur YouTube à l’étape 1 (et le termine à l’étape 3) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui se trouvent en dehors de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune déclaration selon laquelle l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes à FEDRAMP.

## <a name="step-1-set-up-the-twitter-connector"></a>Étape 1 : Configurer le connecteur Twitter

La première étape consiste à accéder à la page **Connecteurs de données** dans le portail de conformité et à créer un connecteur pour les données Twitter.

1. Accédez à<https://compliance.microsoft.com>, puis sélectionnez **Connecteurs** >  de données **Twitter**.

2. Dans la page de description du produit **Twitter** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-twitter-on-the-veritas-merge1-site"></a>Étape 2 : Configurer Twitter sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Twitter sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Twitter, consultez [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

Une fois que vous avez sélectionné **Enregistrer & Terminer,** la page **Mappage de l’utilisateur** dans l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Mapper les utilisateurs Twitter aux utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs. Les éléments Twitter incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sélectionnez **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-twitter-connector"></a>Étape 4 : Surveiller le connecteur Twitter

Après avoir créé le connecteur Twitter, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez à <https://compliance.microsoft.com/> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur **Twitter** pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec la source**, sélectionnez le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’activité d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments d’une taille supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
