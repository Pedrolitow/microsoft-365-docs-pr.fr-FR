---
title: Configurer un connecteur pour archiver les données EML dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données EML de Veritas dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 5261c30097cf571062d3c125841ac112e0552822
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51164355"
---
# <a name="set-up-a-connector-to-archive-eml-data"></a>Configurer un connecteur pour archiver les données EML

Utilisez un connecteur Veritas dans le centre de conformité Microsoft 365 pour importer et archiver des données EML dans les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. EML est l’extension de fichier pour un message électronique enregistré dans un fichier. Le connecteur convertit le contenu d’un élément du format source au format de message électronique, puis importe l’élément dans une boîte aux lettres utilisateur.

Une fois les messages EML stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery et les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur EML pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-eml-data"></a>Vue d’ensemble de l’archivage des données EML

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données EML dans Microsoft 365.

![Flux de travail d’archivage pour les données EML](../media/EMLConnectorWorkflow.png)

1. Votre organisation travaille avec la source EML pour configurer et configurer un site EML.

2. Toutes les 24 heures, les éléments de contenu de la source EML sont copiés sur le site Veritas Merge1. Au cours de ce processus, le contenu d’un fichier EML est converti au format de message électronique.

3. Le connecteur EML que vous créez dans le centre de conformité Microsoft 365 se connecte au site Veritas Merge1 tous les jours et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de message convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du processus de mappage automatique des utilisateurs décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Au cours de ce processus, un sous-dossier du dossier Boîte de réception nommé **EML** est créé dans les boîtes aux lettres utilisateur et les éléments EML sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque message contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément de contenu.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le support [technique Veritas.](https://globanet.com/ms-connectors-contact) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur EML à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans le centre Microsoft 365 conformité. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-an-eml-connector"></a>Étape 1 : Configurer un connecteur EML

La première étape consiste à accéder à la page **Connecteurs** de données dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données EML.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **EML**.

2. Dans la page de description du produit **EML,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-eml-connector-on-the-veritas-merge1-site"></a>Étape 2 : Configurer le connecteur EML sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur EML sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur EML, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20EML%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur dans le centre Microsoft 365 conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le centre Microsoft 365 conformité, suivez les étapes suivantes :

1. Dans la page **Ma mappage des utilisateurs externes Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs. Les éléments sources EML incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments EML sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-eml-connector"></a>Étape 4 : Surveiller le connecteur EML

Après avoir créé le connecteur EML, vous pouvez afficher l’état du connecteur dans le centre Microsoft 365 conformité.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **EML** pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des informations sur les données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.