---
title: Configurer un connecteur pour archiver les données RingCentral dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données RingCentral de Veritas vers Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces Microsoft 365. Après avoir archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, eDiscovery et les stratégies de rétention pour gérer des données tierces.
ms.openlocfilehash: 35acb27e1d98738c6fb916db97cf75ab293f15d4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60188288"
---
# <a name="set-up-a-connector-to-archive-ringcentral-data"></a>Configurer un connecteur pour archiver les données RingCentral

Utilisez un connecteur Veritas dans le Centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme RingCentral vers des boîtes aux lettres utilisateur dans Microsoft 365 organisation. Veritas fournit un [connecteur RingCentral](https://www.veritas.com/insights/merge1/ringcentral) qui est configuré pour capturer des éléments à partir de la source de données tierce et importer ces éléments dans Microsoft 365. Le connecteur convertit du contenu tel que des conversations, des pièces jointes, des tâches, des notes et des publications à partir de RingCentral au format de message électronique, puis importe ces éléments dans les boîtes aux lettres de l’utilisateur Microsoft 365.

Une fois les données RingCentral stockées dans les boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur RingCentral pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-ringcentral-data"></a>Vue d’ensemble des données ringcentral d’archivage

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données RingCentral dans Microsoft 365.

![Flux de travail d’archivage pour les données RingCentral.](../media/RingCentralConnectorWorkflow.png)

1. Votre organisation collabore avec RingCentral pour configurer un site RingCentral.

2. Toutes les 24 heures, les éléments RingCentral sont copiés sur le site Veritas Merge1. Le connecteur convertit également les éléments RingCentral au format de message électronique.

3. Le connecteur RingCentral que vous créez dans le Centre de conformité Microsoft 365, se connecte au site Veritas Merge1 tous les jours et transfère le contenu RingCentral vers un emplacement stockage Azure sécurisé dans le cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *Email* du mappage automatique des utilisateurs, comme décrit à l’étape [3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier Boîte de réception nommé **RingCentral** est créé dans les boîtes aux lettres utilisateur et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer des éléments à l’aide de la valeur de la *propriété Email.* Chaque élément RingCentral contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant de l’élément.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer ce compte, contactez le support [technique Veritas.](https://www.veritas.com/form/requestacall/ms-connectors-contact) Vous devez vous inscrire à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application RingCentral pour extraire des données de votre compte RingCentral. Pour obtenir des instructions détaillées sur la création de l’application, voir le Guide de l’utilisateur [Merge1 Third-Party Connectors](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

- L’utilisateur qui crée le connecteur RingCentral à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="step-1-set-up-the-ringcentral-connector"></a>Étape 1 : Configurer le connecteur RingCentral

La première étape consiste à accéder à la page **Connecteurs** de données dans le Centre de conformité Microsoft 365 créer un connecteur pour les données RingCentral.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **RingCentral**.

2. Dans la page de description **du produit RingCentral,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **Suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-ringcentral-on-the-veritas-merge1-site"></a>Étape 2 : Configurer ringCentral sur le site Veritas Merge1

La deuxième étape consiste à configurer le connecteur RingCentral sur le site Veritas Merge1. Pour plus d’informations sur la configuration du connecteur RingCentral, voir [merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

Une fois que vous avez **cliqué sur & terminé,** la **page** Mappage de l’utilisateur dans l’Assistant connecteur du Centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : Masons les utilisateurs et terminez la configuration du connecteur

Pour maîtr les utilisateurs et terminer la configuration du connecteur dans le Centre de conformité Microsoft 365, suivez les étapes suivantes :

1. Dans la page **Mappage des utilisateurs ringcentral Microsoft 365 utilisateurs,** activez le mappage automatique des utilisateurs. Les éléments RingCentral incluent une propriété appelée *Email*, qui contient les adresses de messagerie des utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez **sur** Suivant, examinez vos paramètres, puis allez à la page **Connecteurs** de données pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-ringcentral-connector"></a>Étape 4 : Surveiller le connecteur RingCentral

Après avoir créé le connecteur RingCentral, vous pouvez afficher l’état du connecteur dans le Centre de conformité Microsoft 365.

1. Go to <https://compliance.microsoft.com/> and click **Data connectors** in the left nav.

2. Cliquez sur **l’onglet Connecteurs,** puis sélectionnez le connecteur **RingCentral** pour afficher la page volante, qui contient les propriétés et les informations sur le connecteur.

3. Sous **État du connecteur avec source,** cliquez sur le lien Télécharger le journal pour ouvrir (ou enregistrer) le journal d’état du connecteur.  Ce journal contient des données qui ont été importées dans le cloud Microsoft.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
