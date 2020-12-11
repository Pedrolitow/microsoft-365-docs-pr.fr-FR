---
title: Configuration d’un connecteur pour l’archivage des données CellTrust dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données CellTrust à partir de Globanet vers Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Une fois que vous avez archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: 990f52eb48fcf031bda3c9f17884ff3d384afc55
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620485"
---
# <a name="set-up-a-connector-to-archive-celltrust-data"></a>Configuration d’un connecteur pour l’archivage des données CellTrust

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme CellTrust vers des boîtes aux lettres utilisateur dans votre organisation 365 Microsoft. Globanet fournit un connecteur [CellTrust](https://globanet.com/celltrust/) qui est configuré pour capturer des éléments à partir de la source de données tierce (de manière régulière) et les importer dans Microsoft 365. Le connecteur convertit le contenu des messages SMS des comptes CellTrust en format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois les données CellTrust stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications L’utilisation d’un connecteur CellTrust pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-celltrust-data"></a>Vue d’ensemble des données d’archivage CellTrust

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des données CellTrust dans Microsoft 365.

![Flux de travail d’archivage pour les données CellTrust](../media/CellTrustConnectorWorkflow.png)

1. Votre organisation travaille avec CellTrust pour installer et configurer un site CellTrust.

2. Une fois toutes les 24 heures, les éléments CellTrust sont copiés sur le site Merge1 Globanet. Le connecteur convertit également le contenu d’un message au format d’un message électronique.

3. Le connecteur CellTrust que vous créez dans le centre de conformité Microsoft 365 se connecte au site Globanet Merge1 tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le mappage utilisateur automatique en tant que connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *email* de la décrite à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception nommé **CellTrust** est créé dans les boîtes aux lettres utilisateur, et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *email* . Chaque élément CellTrust contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le [support client Globanet](https://globanet.com/contact-us/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur CellTrust à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-celltrust-connector"></a>Étape 1 : configurer le connecteur CellTrust

La première étape consiste à accéder aux **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données CellTrust.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** \> **CellTrust**.

2. Sur la page Description du produit **CellTrust** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-celltrust-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur CellTrust sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur CellTrust sur le site Merge1 Globanet. Pour plus d’informations sur la configuration du connecteur CellTrust, voir [Merge1 des connecteurs tiers du guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20CellTrust%20User%20Guide%20.pdf)de l’utilisateur.

Une fois que vous avez cliqué sur **enregistrer & terminer**, la page de **mappage utilisateur** de l’Assistant connecteur dans le centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer le connecteur configuré dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **mapper les utilisateurs CellTrust sur les utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments CellTrust incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-celltrust-connector"></a>Étape 4 : surveiller le connecteur CellTrust

Après avoir créé le connecteur CellTrust, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur **CellTrust** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des données qui ont été importées dans Microsoft Cloud.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
