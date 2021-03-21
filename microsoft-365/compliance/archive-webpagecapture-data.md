---
title: Configurer un connecteur pour archiver des données de page web dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de capture de pages Web à partir de Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: de1e181670f1efc2e758b666dc3a26337a294ee2
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920798"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Configurer un connecteur pour archiver des données de page web

Utilisez un connecteur Globanet dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de pages web vers des boîtes aux lettres utilisateur dans votre organisation Microsoft 365. Globanet fournit un [connecteur de capture](https://globanet.com/webpage-capture) de pages Web qui capture des pages web spécifiques (et tous les liens sur ces pages) dans un site web spécifique ou un domaine entier. Le connecteur convertit le contenu de la page web au format PDF, PNG ou personnalisé, puis joint les fichiers convertis à un message électronique, puis importe ces éléments de courrier dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

Une fois que le contenu de la page web est stocké dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery et les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur de capture de pages Web pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-webpage-data"></a>Vue d’ensemble des données de page web d’archivage

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver le contenu de la page web dans Microsoft 365.

![Flux de travail d’archivage pour les données de page web](../media/WebPageCaptureConnectorWorkflow.png)

1. Votre organisation travaille avec la source de la page web pour configurer un site de capture de pages Web.

2. Une fois toutes les 24 heures, les éléments sources de la page web sont copiés sur le site Globanet Merge1. Le connecteur convertit et joint également le contenu d’une page web à un message électronique.

3. Le connecteur de capture de page web que vous créez dans le Centre de conformité Microsoft 365 se connecte au site Globanet Merge1 tous les jours et transfère les éléments de page web vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments de page web convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage utilisateur automatique, comme décrit à l’étape [3.](#step-3-map-users-and-complete-the-connector-setup) Un sous-dossier du dossier Boîte de réception nommé Capture de page **web** est créé dans les boîtes aux lettres de l’utilisateur et les éléments de page web sont importés dans ce dossier. Pour ce faire, le connecteur utilise la valeur de la *propriété Email.* Chaque élément de page web contient cette propriété, qui est remplie avec les adresses de messagerie fournies lorsque vous configurez le connecteur de capture de page web à [l’étape 2](#step-2-configure-the-webpage-capture-connector-on-the-globanet-merge1-site).

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Globanet.](https://globanet.com/ms-connectors-contact/) Vous vous connectez à ce compte lorsque vous créez le connecteur à l’étape 1.

- Vous devez travailler avec la prise en charge globanet pour configurer un format de fichier personnalisé pour convertir les éléments de page web. Pour plus d’informations, consultez le guide utilisateur Merge1 Third-Party Connectors dans 

- L’utilisateur qui crée le connecteur de capture de page web à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est pas attribué à un groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-webpage-capture-connector"></a>Étape 1 : Configurer le connecteur de capture de page web

La première étape consiste à accéder aux **connecteurs** de données et à créer un connecteur pour les données sources de page Web.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **Webpage Capture**.

2. Dans la page de description du produit **de** capture web, cliquez sur Ajouter **un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-globanet-merge1-site"></a>Étape 2 : Configurer le connecteur de capture de pages web sur le site Globanet Merge1

La deuxième étape consiste à configurer le connecteur de capture de pages web sur le site Globanet Merge1. Pour plus d’informations sur la configuration du connecteur de capture de pages web, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Une fois que vous avez **cliqué sur Enregistrer & terminé,** la **page** Mappage de l’utilisateur dans l’Assistant Connecteur dans le Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour ma cartographier les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes ci-dessous :

1. Dans la page **Mappage Capture users to Microsoft 365 users** page, enable automatic user mapping. Les éléments de capture de page Web incluent une propriété appelée *Courrier* électronique, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres et allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>Étape 4 : Surveiller le connecteur de capture de pages web

Après avoir créé le connecteur de capture de pages Web, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur de **capture de** page web pour afficher la page volante. Cette page contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.