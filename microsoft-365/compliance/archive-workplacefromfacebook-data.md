---
title: Configurer un connecteur pour archiver l’espace de travail à partir de données Facebook dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de Workplace à partir de Facebook, qui est archivé sur le site Merge1 de Veritas, dans Microsoft 365. La configuration d’un connecteur nécessite que vous travailliez avec Veritas Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 0d2db469186469759226f59775a30bac78fe8daa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60179438"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Configurer un connecteur pour archiver l’espace de travail à partir de données Facebook

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de l’espace de travail à partir de Facebook vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. Veritas fournit un espace de travail à partir d’un connecteur [Facebook](https://globanet.com/workplace/) qui est configuré pour capturer des éléments à partir de la source de données tierce (régulièrement) et importer ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les conversations, les pièces jointes, les publications et les vidéos à partir de Workplace au format de message électronique, puis importe ces éléments dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

Une fois les données de l’espace de travail stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies et étiquettes de rétention et la conformité des communications. L’utilisation de Workplace à partir d’un connecteur Facebook pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Vue d’ensemble de l’archivage de l’espace de travail à partir des données Facebook

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de l’espace de travail Microsoft 365.

![Flux de travail d’archivage pour Workplace à partir de données Facebook.](../media/WorkplaceConnectorWorkflow.png)

1. Votre organisation travaille avec Workplace à partir de Facebook pour configurer un site Workplace.

2. Toutes les 24 heures, les éléments de Workplace sont copiés sur le site Veritas Merge1. Le connecteur convertit également le contenu de ces éléments au format de message électronique.

3. Le connecteur Workplace à partir de Facebook que vous créez dans le Centre de conformité Microsoft 365, se connecte à Veritas Merge1 tous les jours et transfère les éléments Workplace vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape 3. Un sous-dossier du dossier Boîte de réception nommé Espace de travail à partir de **Facebook** est créé et les éléments Workplace sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque élément Workplace contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de conversation ou de publication.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://globanet.com/ms-connectors-contact) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une intégration personnalisée pour récupérer des données à partir de Workplace via des API à des fins de conformité https://my.workplace.com/work/admin/apps/ et eDiscovery.

   Lors de la création de l’intégration, la plateforme Workplace génère un ensemble d’informations d’identification uniques utilisées pour générer des jetons utilisés pour l’authentification. Ces jetons sont utilisés dans l’Assistant Configuration du connecteur Facebook workplace à l’étape 2. Pour obtenir des instructions détaillées sur la création des applications, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- L’utilisateur qui crée l’espace de travail à partir du connecteur Facebook à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>Étape 1 : Configurer l’espace de travail à partir du connecteur Facebook

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 et à créer un connecteur pour les données de l’espace de travail.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Workplace from Facebook**.

2. Dans la page de description du produit Espace de travail **à partir de Facebook,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer l’espace de travail à partir du connecteur Facebook sur le site Veritas Merge1

La deuxième étape consiste à configurer l’espace de travail à partir du connecteur Facebook sur le site Merge1. Pour plus d’informations sur la configuration de l’espace de travail à partir du connecteur Facebook, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page **Ma mappage des utilisateurs externes Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs. Les éléments Workplace incluent une propriété appelée *Email* qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>Étape 4 : Surveiller l’espace de travail à partir du connecteur Facebook

Après avoir créé l’espace de travail à partir du connecteur Facebook, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez **l’espace de** travail à partir du connecteur Facebook pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.