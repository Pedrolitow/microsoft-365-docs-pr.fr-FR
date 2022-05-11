---
title: Configurer un connecteur pour archiver Cisco Jabber sur les données de SQL MS dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver Cisco Jabber sur MS SQL données à partir de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver les données de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: 8df9c0b0ec7f69a45578ac91d14315730059d864
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320215"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>Configurer un connecteur pour archiver Cisco Jabber sur des données de SQL MS

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de la plateforme Cisco Jabber vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas vous fournit un connecteur [Cisco Jabber](https://globanet.com/jabber/) configuré pour capturer des éléments à partir du SQL Database MS de Jabber, tels que des messages de conversation 1:1 et des conversations de groupe, puis importer ces éléments dans Microsoft 365. Le connecteur récupère les données du SQL Database MS de Cisco Jabber, les traite et convertit le contenu du compte Cisco Jabber d’un utilisateur au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données Cisco Jabber sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer Microsoft Purview fonctionnalités telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Cisco Jabber pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Vue d’ensemble de l’archivage des données Cisco Jabber

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver Cisco Jabber sur les données de SQL MS dans Microsoft 365.

![Flux de travail d’archivage pour les données Cisco Jabber.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Votre organisation travaille avec Cisco pour configurer un Cisco Jabber sur MS SQL Database.

2. Une fois toutes les 24 heures, les éléments Cisco Jabber sont copiés du SQL Database MS vers le site Veritas Merge1. Le connecteur convertit également le contenu des messages de conversation au format de message électronique.

3. Le connecteur Cisco Jabber que vous créez dans le portail de conformité se connecte au site Veritas Merge1 tous les jours et transfère les éléments à un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le mappage automatique d’utilisateurs en tant que connecteur importe des éléments dans les boîtes aux lettres de certains utilisateurs à l’aide de la valeur de la propriété *Email* de [l’étape 3](#step-3-map-users-and-complete-the-connector-setup) décrite. Un sous-dossier du dossier Boîte de réception nommé **Cisco Jabber sur MS SQL** est créé dans les boîtes aux lettres de l’utilisateur et les éléments de message sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres vers laquelle importer des éléments à l’aide de la valeur de la propriété *Email* . Chaque élément Cisco Jabber contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://www.veritas.com/content/support/). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Configurez un SQL Database MS pour récupérer les éléments Jabber avant de créer le connecteur à l’étape 1. Vous spécifiez les paramètres de connexion pour le SQL Database MS lors de la configuration du connecteur Cisco Jabber à l’étape 2. Pour plus d’informations, consultez le [Guide de l’utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée le connecteur Cisco Jabber à l’étape 1 (et le termine à l’étape 3). Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>Étape 1 : Configurer le connecteur Cisco Jabber sur MS SQL

La première étape consiste à accéder aux **connecteurs de données** dans le portail de conformité et à créer un connecteur pour Cisco Jabber sur les données MS SQL.

1. Accédez, [https://compliance.microsoft.com](https://compliance.microsoft.com/)puis cliquez sur **Data connectorsCisco** >  **Jabber sur MS SQL**.

2. Dans la page **Cisco Jabber sur MS SQL** description du produit, cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Cisco Jabber sur MS SQL sur le site Veritas Merge1

La deuxième étape consiste à configurer cisco jabber sur MS SQL connecteur sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Cisco Jabber sur MS SQL, consultez le [Guide utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Map Cisco Jabber sur MS SQL utilisateurs à Microsoft 365 page utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments Cisco Jabber sur MS SQL incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres et accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Étape 4 : Surveiller le connecteur Cisco Jabber

Après avoir créé Cisco Jabber sur MS SQL connecteur, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs**, puis sélectionnez **Cisco Jabber sur MS SQL** connecteur pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
