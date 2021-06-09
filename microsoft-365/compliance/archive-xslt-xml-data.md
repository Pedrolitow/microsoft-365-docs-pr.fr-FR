---
title: Configurer un connecteur pour archiver les données XSLT/XML dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données XSLT/XML à partir de Veritas Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 51b05f83c51626bc60dc19b5ec9a63750903281c
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51163756"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>Configurer un connecteur pour archiver les données XSLT/XML

Utilisez un connecteur Veritas dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la source de page Web vers les boîtes aux lettres des utilisateurs de Microsoft 365 organisation. Veritas vous fournit un connecteur [XSLT/XML](https://globanet.com/xslt-xml) qui permet le développement rapide de fichiers créés à l’aide de XSLT (Extensible Style sheet Language Transformations) pour transformer des fichiers XML dans d’autres formats de fichiers (tels que html ou texte) qui peuvent être importés dans Microsoft 365. Le connecteur convertit le contenu d’un élément de la source XSLT/XML au format de message électronique, puis importe l’élément converti dans Microsoft 365 boîtes aux lettres.

Une fois que les données XSLT/XML sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery et les stratégies et étiquettes de rétention. L’utilisation d’un connecteur XSLT/XML pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-xsltxml-data"></a>Vue d’ensemble de l’archivage des données XSLT/XML

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données sources XSLT/XML Microsoft 365.

![Flux de travail d’archivage pour les données XSLT/XML](../media/XSLT-XMLConnectorWorkflow.png)

1. Votre organisation travaille avec la source XSLT/XML pour configurer un site XSLT/XML.

2. Une fois toutes les 24 heures, les messages de conversation de la source XSLT/XML sont copiés sur le site Veritas Merge1. Le connecteur convertit également le contenu au format de message électronique.

3. Le connecteur XSLT/XML que vous créez dans le centre de conformité Microsoft 365 se connecte au site Veritas Merge1 tous les jours et transfère les messages vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de message convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape 3. Un nouveau sous-dossier dans le dossier boîte de réception nommé **XSLT/XML** est créé dans les boîtes aux lettres utilisateur et les éléments de message sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque message contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Veritas Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://www.veritas.com/content/support/) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- L’utilisateur qui crée le connecteur XSLT/XML à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans le centre Microsoft 365 conformité. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-an-xsltxml-connector"></a>Étape 1 : Configurer un connecteur XSLT/XML

La première étape consiste à accéder aux **connecteurs** de données dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données XSLT/XML.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **XSLT/XML**.

2. Dans la page de description **du produit XSLT/XML,** cliquez **sur Ajouter un nouveau connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-an-xsltxml-connector"></a>Étape 2 : Configurer un connecteur XSLT/XML

La deuxième étape consiste à configurer le connecteur XSLT/XML sur le site Merge1. Pour plus d’informations sur la configuration du connecteur XSLT/XML sur le site Veritas Merge1, consultez le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur &** terminé, la **page** Mappage de l’utilisateur dans l’Assistant connecteur dans le centre Microsoft 365 conformité s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

1. Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le centre Microsoft 365 conformité, suivez les étapes ci-dessous :

2. Dans la page **Mappage des utilisateurs XSLT/XML Microsoft 365** aux utilisateurs, activez le mappage automatique des utilisateurs. Les éléments XSLT/XML incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

3. Cliquez **sur** Suivant, examinez vos paramètres et allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-xsltxml-connector"></a>Étape 4 : Surveiller le connecteur XSLT/XML

Après avoir créé le connecteur XSLT/XML, vous pouvez afficher l’état du connecteur dans le centre Microsoft 365 conformité.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le **connecteur XSLT/XML** pour afficher la page de présentation. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.