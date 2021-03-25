---
title: Configurer un connecteur pour les données Webex Teams dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir du connecteur Webex Teams de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 654ca53fd4cd7c6091ff74360545ba335f753ffd
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163897"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>Configurer un connecteur pour archiver des données Webex Teams

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données de Webex Teams vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Veritas fournit un [connecteur Webex Teams](https://globanet.com/webex-teams/) qui est configuré pour capturer les éléments de communication Webex Teams et les importer dans Microsoft 365. Le connecteur convertit le contenu de Webex Teams, tel que les conversations 1:1, les conversations de groupe, les conversations de canal et les pièces jointes du compte Webex Teams de votre organisation, au format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données Webex Teams sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Webex Teams pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-webex-teams-data"></a>Vue d’ensemble de l’archivage des données Webex Teams

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Webex Teams dans Microsoft 365.

![Flux de travail d’archivage pour les données Webex Teams](../media/WebexTeamsConnectorWorkflow.png)

1. Votre organisation collabore avec Webex Teams pour configurer et configurer un site Webex Teams.

2. Toutes les 24 heures, les éléments Webex Teams sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments Webex Teams au format de message électronique.

3. Le connecteur Webex Teams que vous créez dans le Centre de conformité Microsoft 365, se connecte à Veritas Merge1 tous les jours et transfère les éléments Webex Teams vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Webex Teams** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque élément Webex Teams contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://globanet.com/ms-connectors-contact) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application à partir de votre compte Webex Teams pour extraire [https://developer.webex.com/](https://developer.webex.com) des données. Pour obtenir des instructions détaillées sur la création de l’application, consultez le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Lorsque vous créez cette application, la plateforme Webex génère un ensemble d’informations d’identification uniques. Ces informations d’identification sont utilisées à l’étape 2 lorsque vous configurez le connecteur Webex Teams sur le site Fusion globale1.

- L’utilisateur qui crée le connecteur Webex Teams à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-webex-teams-connector"></a>Étape 1 : Configurer le connecteur Webex Teams

La première étape consiste à accéder aux **connecteurs de** données et à configurer le [connecteur Webex Teams.](https://globanet.com/webex-teams/)

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Webex Teams**.

2. Dans la page de description du produit **Webex Teams,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur Webex Teams sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur Webex Teams sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Webex Teams, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur Enregistrer & terminé,** la **page** Mappage de l’utilisateur dans l’Assistant Connecteur dans le Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page Ma mappage des utilisateurs Webex Teams aux utilisateurs **Microsoft 365,** activez le mappage automatique des utilisateurs. Les éléments Webex Teams incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-webex-teams-connector"></a>Étape 4 : Surveiller le connecteur Webex Teams

Après avoir créé le connecteur Webex Teams, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le **connecteur Webex Teams** pour afficher la page volante. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.