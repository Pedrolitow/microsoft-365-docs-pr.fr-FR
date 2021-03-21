---
title: Configurer un connecteur pour archiver des données Reuters Eikon dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données Reuters Eikon à partir de Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 3d125bb8d0c4481f17f6dfe4c85afd0e30b93e50
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50925126"
---
# <a name="set-up-a-connector-to-archive-reuters-eikon-data"></a>Configurer un connecteur pour archiver les données de Reuters Eikon

Utilisez un connecteur Globanet dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Reuters Eikon vers les boîtes aux lettres des utilisateurs de votre organisation Microsoft 365. Globanet fournit un connecteur [Reuters Eikon](https://globanet.com/eikon/) qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les messages de personne à personne, les conversations de groupe, les pièces jointes et les clauses d’exclusion de responsabilité du compte Reuters Eikon d’un utilisateur en un format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données de Reuters Eikon sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention, ainsi que la conformité des communications. L’utilisation d’un connecteur Reuters Eikon pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-reuters-eikon-data"></a>Vue d’ensemble de l’archivage des données De Reuters Eikon

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données Reuters Eikon dans Microsoft 365.

![Flux de travail d’archivage pour les données Eikon de Reuters](../media/ReutersEikonConnectorWorkflow.png)

1. Votre organisation collabore avec Reuters Eikon pour configurer un site Reuters Eikon.

2. Une fois toutes les 24 heures, les éléments Reuters Eikon sont copiés sur le site Globanet Merge1. Le connecteur convertit également les éléments Reuters Eikon au format de message électronique.

3. Le connecteur Reuters Eikon que vous créez dans le Centre de conformité Microsoft 365 se connecte au site Globanet Merge1 tous les jours et transfère le contenu vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **Reuters Eikon** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément Eikon de Reuters contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le support [technique Globanet.](https://globanet.com/ms-connectors-contact) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur Reuters Eikon à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-reuters-eikon-connector"></a>Étape 1 : Configurer le connecteur Reuters Eikon

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 et à créer un connecteur pour les données Reuters Eikon.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Reuters Eikon**.

2. Dans la page de description **du produit Reuters Eikon,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-reuters-eikon-connector-on-the-globanet-merge1-site"></a>Étape 2 : Configurer le connecteur Reuters Eikon sur le site Globanet Merge1

La deuxième étape consiste à configurer le connecteur Reuters Eikon sur le site Merge1. Pour plus d’informations sur la configuration du connecteur Reuters Eikon sur le site Globanet Merge1, consultez le guide utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Eikon%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur Enregistrer & terminé,** la **page** Mappage de l’utilisateur dans l’Assistant Connecteur dans le Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page Ma mappage des utilisateurs externes aux utilisateurs **De Microsoft 365,** activez le mappage automatique des utilisateurs. Les éléments Reuters Eikon incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-reuters-eikon-connector"></a>Étape 4 : Surveiller le connecteur Reuters Eikon

Après avoir créé le connecteur Reuters Eikon, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **Reuters Eikon** pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.