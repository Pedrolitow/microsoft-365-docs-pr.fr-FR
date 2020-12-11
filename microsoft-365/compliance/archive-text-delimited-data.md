---
title: Configurer un connecteur pour archiver des données délimitées par du texte dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données délimitées par du texte à partir de Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Une fois que vous avez archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: 1c06a1220e597dbf8e278222347a5a5e9c46567e
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49619900"
---
# <a name="set-up-a-connector-to-archive-text-delimited-data"></a>Configurer un connecteur pour archiver des données délimitées par du texte

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données délimitées par du texte dans des boîtes aux lettres utilisateur dans votre organisation 365 Microsoft. Globanet fournit un [connecteur texte délimité](https://globanet.com/text-delimited) configuré pour capturer des éléments provenant d’une source de données tierce (de manière régulière) et les importer dans Microsoft 365. Le connecteur convertit le contenu de la source de données délimitée par du texte en format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Lorsque les données de texte délimité sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la découverte électronique, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur de données délimité par du texte pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-the-text-delimited-data"></a>Vue d’ensemble de l’archivage des données délimitées par le texte

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des informations de source délimitées par du texte dans Microsoft 365.

![Flux de travail d’archivage pour les données délimitées par du texte](../media/TextDelimitedConnectorWorkflow.png)

1. Votre organisation utilise la source délimitée par le texte pour installer et configurer un site délimité par du texte.

2. Une fois toutes les 24 heures, les messages de conversation provenant de la source délimitée par le texte sont copiés sur le site Globanet Merge1. Le connecteur convertit également le contenu au format d’un message électronique.

3. Le connecteur délimité par du texte que vous créez dans le centre de conformité Microsoft 365 se connecte au site Merge1 Globanet tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de message convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier boîte de réception nommé **texte-délimité** est créé dans les boîtes aux lettres utilisateur, et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *email* . Chaque message contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour créer ce compte, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact). Vous vous connecterez à ce compte lors de la création du connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur texte délimité à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle exportation d’importation de boîtes aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas affecté à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-text-delimited-connector"></a>Étape 1 : configurer le connecteur texte-délimité

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données délimitées par du texte.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données**  >  **texte** délimité.

2. Sur la page Description du produit **délimité** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-text-delimited-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur délimité par du texte sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur délimité par du texte sur le site Merge1. Pour plus d’informations sur la configuration du connecteur délimité par des textes sur le site Merge1 Globanet, voir [Merge1 le Guide de l’utilisateur des connecteurs tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20text-delimited%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, la page de **mappage utilisateur** de l’Assistant connecteur dans le centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments de source délimités de texte incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-text-delimited-connector"></a>Étape 4 : Surveillez le connecteur texte-délimité

Après avoir créé le connecteur délimité par du texte, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur **texte (délimité par des caractères)** pour afficher la page de menu volant. Cette page contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le Cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
