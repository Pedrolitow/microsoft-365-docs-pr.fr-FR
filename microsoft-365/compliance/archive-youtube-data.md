---
title: Configurer un connecteur pour archiver les données YouTube dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données YouTube de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver les données de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, eDiscovery et des stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 7f67269c979b6ef6c5e83e29cfd833cf98f1561f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001478"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>Configurer un connecteur pour archiver les données YouTube

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de YouTube vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur configuré pour capturer des éléments à partir d’une source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les conversations, les pièces jointes, les tâches, les notes et les publications de YouTube au format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois que les données YouTube sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur YouTube pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux politiques gouvernementales et réglementaires.

## <a name="overview-of-archiving-youtube-data"></a>Vue d’ensemble de l’archivage des données YouTube

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données YouTube dans Microsoft 365.

![Flux de travail d’archivage pour les données YouTube.](../media/YouTubeConnectorWorkflow.png)

1. Votre organisation travaille avec YouTube pour configurer un site YouTube.

2. Toutes les 24 heures, les éléments YouTube sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments YouTube au format de message électronique.

3. Le connecteur YouTube que vous créez dans le portail de conformité se connecte au site Veritas Merge1 tous les jours et transfère le contenu YouTube vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email du mappage* automatique des utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **YouTube** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres vers laquelle importer des éléments à l’aide de la valeur de la propriété *Email* . Chaque élément YouTube contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://www.veritas.com/form/requestacall/ms-connectors-contact). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application YouTube pour extraire des données de votre compte YouTube. Pour obtenir des instructions pas à pas sur la création de l’application, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée le connecteur YouTube à l’étape 1 (et le termine à l’étape 3). Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>Étape 1 : Configurer le connecteur YouTube

La première étape consiste à accéder à la page **Connecteurs de données** dans le portail de conformité et à créer un connecteur pour les données YouTube.

1. Accédez, <https://compliance.microsoft.com> puis cliquez sur **Data connectorsYouTube** > .

2. Dans la page de description du produit **YouTube** , cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>Étape 2 : Configurer YouTube sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur YouTube sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur YouTube, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer,** la page de **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Carte des utilisateurs YouTube pour Microsoft 365 utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments YouTube incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-youtube-connector"></a>Étape 4 : Surveiller le connecteur YouTube

Après avoir créé le connecteur YouTube, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et <https://compliance.microsoft.com/> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs** , puis sélectionnez le connecteur **YouTube** pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
