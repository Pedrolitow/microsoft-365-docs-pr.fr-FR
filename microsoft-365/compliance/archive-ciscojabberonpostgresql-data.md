---
title: Configurer un connecteur pour archiver Cisco Jabber sur les données PostgreSQL dans Microsoft 365
description: Découvrez comment configurer et utiliser un connecteur dans le portail de conformité Microsoft Purview pour importer et archiver des données de Cisco Jabber sur PostgreSQL vers Microsoft 365.
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
search.appverid:
- MET150
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e4fc54a55402cc39a3897fb1416d7c6d6b595b3f
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68534231"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>Configurer un connecteur pour archiver Cisco Jabber sur les données PostgreSQL

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de la plateforme Cisco Jabber vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [Cisco Jabber sur PostgreSQL](https://www.veritas.com/insights/merge1/jabber) configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les messages, les conversations et le contenu partagé de Cisco Jabber sur PostgreSQL au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données Cisco Jabber sur PostgreSQL sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Cisco Jabber sur PostgreSQL pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>Vue d’ensemble de l’archivage de Cisco Jabber sur les données PostgreSQL

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données Cisco Jabber sur PostgreSQL dans Microsoft 365.

![Flux de travail d’archivage pour Cisco Jabber sur les données PostgreSQL.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Votre organisation travaille avec Cisco Jabber sur PostgreSQL pour configurer et configurer un site Cisco Jabber sur PostgreSQL.

2. Une fois toutes les 24 heures, les éléments Cisco Jabber sur PostgreSQL sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Cisco Jabber sur PostgreSQL au format de message électronique.

3. Le connecteur Cisco Jabber sur PostgreSQL que vous créez dans le portail de conformité, se connecte au site Veritas Merge1 tous les jours et transfère le contenu Jabber vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier dans le dossier Boîte de réception nommé **Cisco Jabber sur PostgreSQL** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email*. Chaque élément Jabber contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour ce faire, contactez le [support technique veritas](https://www.veritas.com/content/support/en_US). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Cisco Jabber sur PostgreSQL à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>Étape 1 : Configurer le connecteur Cisco Jabber sur PostgreSQL

La première étape consiste à accéder à la page **Connecteurs de données** dans le portail de conformité et à créer un connecteur pour les données Jabber.

1. Accédez, <https://compliance.microsoft.com> puis sélectionnez **les connecteurs** &gt; **de données Cisco Jabber sur PostgreSQL**.

2. Dans la page de description du produit **Cisco Jabber sur PostgreSQL** , sélectionnez **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , sélectionnez **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis sélectionnez **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>Étape 2 : Configurer Cisco Jabber sur PostgreSQL sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Cisco Jabber sur PostgreSQL sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur Cisco Jabber sur PostgreSQL, consultez le [Guide utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

Une fois que vous avez sélectionné **Enregistrer & Terminer**, la page de **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans la page **Map Cisco Jabber sur PostgreSQL users to Microsoft 365 users** , activez le mappage automatique des utilisateurs. Les éléments Cisco Jabber sur PostgreSQL incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sélectionnez **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>Étape 4 : Surveiller le connecteur Cisco Jabber sur PostgreSQL

Après avoir créé le connecteur Cisco Jabber sur PostgreSQL, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez aux <https://compliance.microsoft.com/> **connecteurs de données** et sélectionnez-les dans le volet de navigation gauche.

2. Sélectionnez l’onglet **Connecteurs** , puis sélectionnez le connecteur **Cisco Jabber sur PostgreSQL** pour afficher la page de menu volant, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, **sélectionnez** le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft. Pour plus d’informations, consultez [Afficher les journaux d’administration pour les connecteurs de données](data-connector-admin-logs.md).

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
