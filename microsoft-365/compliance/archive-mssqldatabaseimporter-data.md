---
title: Configurer un connecteur pour archiver les données à partir de la base de données MS SQL
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de la base de données MS SQL. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Une fois que vous avez archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: 576ba38616b9a6a9c1b0e7c78c5e8d03c5a0e9df
ms.sourcegitcommit: 95b85a1fdf43e3f0839483fa22e279262703f15f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "49407298"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>Configurer un connecteur pour archiver les données à partir de la base de données MS SQL

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de bases de données MS SQL vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Globanet fournit un connecteur d’importateur de base de données MS SQL qui est configuré pour capturer des éléments à partir d’une base de données à l’aide d’un fichier de configuration XML et les importer dans Microsoft 365. Le connecteur convertit le contenu de la base de données MS SQL en format de message électronique, puis importe ces éléments dans les boîtes aux lettres utilisateur dans Microsoft 365.

Une fois le contenu de la base de données MS SQL stocké dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de conservation L’utilisation d’un connecteur de base de données MS SQL pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-the-ms-sql-data"></a>Vue d’ensemble de l’archivage des données MS SQL

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des données MS SQL dans Microsoft 365.

![Flux de travail d’archivage pour les données MS SQL](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Votre organisation travaille avec un fournisseur de base de données MS SQL pour installer et configurer un site de base de données MS SQL.

2. Une fois toutes les 24 heures, les éléments de base de données MS SQL sont copiés sur le site Globanet Merge1. Le connecteur convertit également ce contenu au format d’un message électronique.

3. Le connecteur de l’importateur de base de données MS SQL que vous créez dans le centre de conformité 365 de Microsoft, se connecte au site Merge1 Globanet tous les jours et transfère les messages vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments de base de données MS SQL convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception appelé **MS SQL Database importateur** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *email* . Chaque élément de la base de données MS SQL contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour créer un compte, contactez le [support client Globanet](https://globanet.com/contact-us/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur d’importateur de base de données MS SQL à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page connecteurs de données dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>Étape 1 : configurer le connecteur d’importateur de base de données MS SQL

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft365 et à créer un connecteur pour la base de données MS SQL.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs**  >  **de données MS SQL Database importateur**.

2. Sur la page Description du produit **MS SQL Database importer** , cliquez sur **Ajouter un nouveau connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur d’importateur de base de données MS SQL sur le site Merge1 Globanet

La deuxième étape consiste à configurer le connecteur d’importateur de base de données MS SQL sur le site Merge1. Pour plus d’informations sur la configuration de l’importateur de bases de données MS SQL, reportez-vous au [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer**, la page de **mappage utilisateur** de l’Assistant connecteur dans le centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur, procédez comme suit :

1. Sur la page **mapper MS SQL Database importateur users to Microsoft 365 Users** , activez le mappage automatique des utilisateurs. Les éléments de base de données MS SQL incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur le bouton **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.

   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>Étape 4 : surveiller le connecteur d’importateur de base de données MS SQL

Après avoir créé le connecteur d’importateur de base de données MS SQL, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à <https://compliance.microsoft.com/> , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le connecteur **MS SQL Database** **Importer** Connector pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des données qui ont été importées dans Microsoft Cloud.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
