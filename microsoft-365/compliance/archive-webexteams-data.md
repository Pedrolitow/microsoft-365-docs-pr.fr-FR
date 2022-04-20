---
title: Configurer un connecteur pour les données webex Teams dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir du connecteur Webex Teams de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 1aa1a0ddd94aa2308c4884921138b12b0c152bab
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942862"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Configurer un connecteur pour archiver des données webex Teams

Utilisez un connecteur Veritas dans le portail de conformité Microsoft Purview pour importer et archiver des données de Webex Teams vers des boîtes aux lettres utilisateur de votre organisation Microsoft 365. Veritas fournit un connecteur [Webex Teams](https://globanet.com/webex-teams/) configuré pour capturer les éléments de communication Webex Teams et les importer dans Microsoft 365. Le connecteur convertit le contenu des Teams Webex, tels que les conversations 1:1, les conversations de groupe, les conversations de canal et les pièces jointes du compte Webex Teams de votre organisation, en un format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que Webex Teams données sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, eDiscovery, les stratégies de rétention et les étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Webex Teams pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-webex-teams-data"></a>Vue d’ensemble de l’archivage des données webex Teams

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Webex Teams dans Microsoft 365.

![Flux de travail d’archivage pour les données webex Teams.](../media/WebexTeamsConnectorWorkflow.png)

1. Votre organisation travaille avec Webex Teams pour configurer et configurer un site Webex Teams.

2. Toutes les 24 heures, Webex Teams éléments sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments webex Teams au format de message électronique.

3. Webex Teams connecteur que vous créez dans le portail de conformité, se connecte au Veritas Merge1 tous les jours et transfère les éléments webex Teams à un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique d’utilisateurs, comme décrit à [l’étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Webex Teams** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la propriété *Email* . Chaque élément webex Teams contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le [support technique Veritas](https://globanet.com/ms-connectors-contact). Vous vous connecterez à ce compte lorsque vous créerez le connecteur à l’étape 1.

- Créez une application pour [https://developer.webex.com/](https://developer.webex.com) extraire des données de votre compte Webex Teams. Pour obtenir des instructions pas à pas sur la création de l’application, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Lorsque vous créez cette application, la plateforme Webex génère un ensemble d’informations d’identification uniques. Ces informations d’identification sont utilisées à l’étape 2 lorsque vous configurez le connecteur Webex Teams sur le site Global Merge1.

- L’utilisateur qui crée le connecteur Webex Teams à l’étape 1 (et le termine à l’étape 3) doit se faire attribuer le rôle Administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données Veritas est en préversion publique dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="step-1-set-up-the-webex-teams-connector"></a>Étape 1 : Configurer le connecteur Webex Teams

La première étape consiste à accéder aux **connecteurs de données** et à configurer le connecteur [Webex Teams](https://globanet.com/webex-teams/).

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) **data connectorsWebex** >  Teams, puis cliquez **dessus**.

2. Dans la page **webex Teams** description du produit, cliquez sur **Ajouter un connecteur**.

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Webex Teams sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Webex Teams sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Webex Teams, consultez le [Guide d’utilisation des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **Enregistrer & Terminer**, la page De **mappage utilisateur** de l’Assistant Connecteur dans le portail de conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Mapper les utilisateurs et terminer la configuration du connecteur

Pour mapper les utilisateurs et terminer la configuration du connecteur dans le portail de conformité, procédez comme suit :

1. Dans Map **Webex Teams utilisateurs à Microsoft 365 page utilisateurs**, activez le mappage automatique des utilisateurs. Les éléments webex Teams incluent une propriété appelée *Email*, qui contient des adresses e-mail pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **Suivant**, passez en revue vos paramètres, puis accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Étape 4 : Surveiller le connecteur Webex Teams

Après avoir créé le connecteur Webex Teams, vous pouvez afficher l’état du connecteur dans le portail de conformité.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Cliquez sur l’onglet **Connecteurs**, puis sélectionnez le connecteur **Webex Teams** pour afficher la page de menu volant. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’état du connecteur. Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.