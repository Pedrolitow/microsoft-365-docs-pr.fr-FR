---
title: Archiver les données eDiscovery de Slack Microsoft 365 à l’aide d’un connecteur de données fourni par Microsoft
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
description: Découvrez comment configurer et utiliser un connecteur de données de découverte électronique Slack fourni par Microsoft pour importer et archiver des données de messagerie instantanée.
ms.openlocfilehash: 7882524bb01a1d28c0f4f7c564472961d04baa07
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501198"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Configurer un connecteur pour archiver des données de découverte électronique Slack (aperçu)

Le connecteur de données de découverte électronique Slack fourni par Microsoft vous permet d’importer et d’archiver des données de messagerie instantanée (telles que des messages, des pièces jointes, des liens et des révisions) des espaces de travail Slack de votre organisation vers Microsoft 365. Le connecteur de données tire les données de l’API Slack, les convertit au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs Microsoft 365. Une fois les données Slack importées, vous pouvez appliquer des solutions de conformité, telles que la conservation pour litige, la Advanced eDiscovery, la conformité des communications et les paramètres de rétention au contenu Slack. L’utilisation d’un connecteur de données de découverte électronique Slack pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Vue d’ensemble de l’archivage des données eDiscovery de Slack

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur de données Microsoft pour archiver les données Slack dans Microsoft 365.

![Flux de travail d’archivage de slack eDiscovery.](../media/SlackMSFTConnectorWorkflow.png)

1. Votre organisation collabore avec Slack pour configurer un espace de travail Slack.

2. Une fois le connecteur de données installé, les messages des espaces de travail Slack de votre organisation sont copiés dans les boîtes aux lettres des utilisateurs Microsoft 365. Le connecteur de données convertit également le contenu d’un message de conversation au format de message électronique.

3. Le connecteur importe les messages de conversation convertis dans les boîtes aux lettres d’utilisateurs spécifiques. Un sous-dossier du dossier Boîte de réception nommé **Slack eDiscovery** est créé dans les boîtes aux lettres utilisateur et les éléments de message de conversation sont importés dans ce dossier.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Votre organisation a besoin de l’abonnement Enterprise Grid pour Slack. Pour plus d’informations, voir [Abonnements et fonctionnalités Slack](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- L’utilisateur qui crée le connecteur de données doit avoir le rôle **d’application Propriétaires** de l’organisation dans son organisation Slack. Pour plus d’informations, voir [Types de rôles dans Slack](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Obtenez le nom d’utilisateur et le mot de passe du compte d’entreprise Slack de votre organisation. Vous utilisez ces informations d’identification pour vous inscrire à ce compte lorsque vous créez le connecteur de données. Il est également recommandé que l’approvisionnement automatisé des utilisateurs dans votre organisation Slack soit configuré pour utiliser l’sign-on unique (SSO). [Rôles dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- L’utilisateur qui crée le connecteur slack eDiscovery doit avoir le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-a-slack-ediscovery-connector"></a>Étape 1 : Créer un connecteur de découverte électronique Slack

1. Go to <https://compliance.microsoft.com> and click **Data connectors** on the left navigation pane.

2. Sous **l’onglet** Vue d’ensemble, cliquez sur **Filtrer** et sélectionnez Par **Microsoft**, puis appliquez le filtre.

3. Cliquez **sur Slack eDiscovery (aperçu).**

4. Dans la page de description du produit **Slack eDiscovery (aperçu** ), cliquez **sur Ajouter un connecteur**.

5. Dans la page **Assistant Conditions d’utilisation** , cliquez sur **Accepter**.

6. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**. Le nom que vous entrez identifie le connecteur sur la page **Connecteurs de données** après sa création.

## <a name="step-2-sign-into-your-slack-organization"></a>Étape 2 : Connectez-vous à votre organisation Slack

1. Dans la page **Assistant Se connectez-vous à Slack** , cliquez sur **Se connectez-vous à Slack** pour vous inscrire à l’espace de travail Slack de votre organisation.

2. Dans la page Se **connectez à votre** espace de travail Slack, tapez le nom de l’espace de travail à partir de qui vous souhaitez archiver les données, puis cliquez sur **Continuer**.

   Une page s’affiche avec le nom de votre espace de travail Slack et une invite de se connecte.

3. Cliquez sur le lien dans la chaîne que les propriétaires de **l’organisation peuvent également se connecter ici**.

4. Dans la page de connectez-vous à l’espace de travail, entrez l’adresse e-mail et le mot de passe du compte d’entreprise Slack de votre organisation, puis cliquez sur **Se connectez**.

   Une fois que vous êtes connecté, une page s’affiche pour demander l’autorisation d’accès à votre organisation Slack par l’application connecteur.

5. Cliquez **sur Autoriser** pour autoriser l’application à administrer votre organisation.

   Une **fois que vous** avez cliqué sur Autoriser, la page Slack se ferme et les utilisateurs **eDiscovery de Slack** Microsoft 365 page utilisateurs dans l’Assistant Connecteur s’affiche.

## <a name="step-3-specify-the-users-to-import-data-for"></a>Étape 3 : spécifier les utilisateurs pour qui importer des données

Sélectionnez l’une des options suivantes pour spécifier les utilisateurs dont vous souhaitez importer des données de découverte électronique Slack.

- **Tous les utilisateurs de votre organisation**. Sélectionnez cette option pour importer des données pour tous les utilisateurs.

- **Uniquement les utilisateurs en attente pour litige**. Sélectionnez cette option pour importer des données uniquement pour les utilisateurs dont les boîtes aux lettres sont placées en attente pour litige. Cette option importe les données dans les boîtes aux lettres utilisateur dont la propriété LitigationHoldEnabled a la valeur True. Pour plus d’informations, [voir Créer une attente pour litige](create-a-litigation-hold.md).

## <a name="step-4-map-users-and-select-data-types-to-import"></a>Étape 4 : Ma cartographier les utilisateurs et sélectionner les types de données à importer

1. Configurez l’une des options suivantes ou les deux pour ma besoins des utilisateurs de Slack Microsoft 365 boîtes aux lettres.

   - **Mappage utilisateur automatique**. Sélectionnez cette option pour maser automatiquement les noms d’utilisateurs Slack Microsoft 365 boîtes aux lettres. Le connecteur utilise la valeur de la propriété *Email* , que contient chaque message ou élément Slack. Cette propriété est remplie avec l’adresse e-mail de chaque participant du message. Si le connecteur peut associer les adresses e-mail aux utilisateurs Microsoft 365 correspondants, l’élément est importé dans la boîte Microsoft 365 aux lettres de ces utilisateurs. Pour utiliser cette option, vous devez avoir configuré l’sso pour votre organisation Slack.

   - **Mappage utilisateur personnalisé**. Vous avez également la possibilité d’utiliser le mappage utilisateur personnalisé à la place (ou en plus) du mappage utilisateur automatique. Avec cette option, vous devez créer, puis télécharger un fichier CSV qui masgue l’ID de membre Slack des utilisateurs à leur adresse Microsoft 365 courrier électronique. Pour ce faire, cliquez sur Télécharger le modèle de mappage **CSV**, remplir le fichier CSV avec l’ID de membre Slack et l’adresse de messagerie Microsoft 365 pour tous les utilisateurs de votre organisation, puis sélectionnez et téléchargez le fichier CSV dans l’Assistant. N’oubliez pas de ne pas modifier les en-tête de colonne dans le fichier CSV. Voici un exemple de fichier de mappage CSV :

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Les ID de membre des utilisateurs peuvent être obtenus en cliquant sur ... Bouton Plus dans le profil d’un utilisateur, puis sélection de **l’ID du membre Copier**. Vous pouvez également utiliser la méthode API Slack [users.list](https://api.slack.com/methods/users.list) pour obtenir les ID de tous les membres d’une équipe Slack.

   Si vous activez le mappage utilisateur automatique et fournissez un fichier de mappage personnalisé, le connecteur recherche d’abord le fichier de mappage personnalisé pour ma mappage de l’utilisateur Slack à une boîte aux lettres Microsoft 365 personnalisée. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide qui correspond à l’utilisateur Slack, le connecteur utilise la propriété *Email* de l’élément Slack. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété *Email* de l’élément de message, l’élément n’est pas importé.

2. Dans la page **Sélectionner des types de données à importer** , sélectionnez les types de données Slack que vous souhaitez importer. Si vous souhaitez importer des messages de tous les canaux, sélectionnez toutes les options. Dans le cas contraire, sélectionnez uniquement les types de données que vous souhaitez importer.

     Outre les messages Slack, vous pouvez également spécifier d’autres types de contenu Slack à importer dans Microsoft 365. 

3. Après avoir configuré les types de données à importer, cliquez sur **Suivant**, examinez les paramètres du connecteur, puis cliquez sur **Terminer** pour créer le connecteur.

## <a name="step-5-monitor-the-slack-ediscovery-connector"></a>Étape 5 : Surveiller le connecteur de découverte électronique Slack

Après avoir créé le connecteur de découverte électronique Slack, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs** , puis sélectionnez le connecteur **slack eDiscovery** pour afficher la page de présentation, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **cliquez sur le** lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
