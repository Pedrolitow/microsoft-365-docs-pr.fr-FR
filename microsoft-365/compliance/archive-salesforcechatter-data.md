---
title: Configuration d’un connecteur pour l’archivage des données de la mise en conversation de Salesforce dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de la mise en conversation de Salesforce à partir de Globanet vers Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365. Une fois que vous avez archivé ces données, vous pouvez utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces.
ms.openlocfilehash: 60d86cd01ef8da3a02839d4a3f815be02dc1ee01
ms.sourcegitcommit: a3215cc22faa47e935d22300c481e47ab2680b44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "49722973"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data-preview"></a>Configuration d’un connecteur pour l’archivage des données de la mise en conversation de Salesforce (aperçu)

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme de la Salesforce chatter vers des boîtes aux lettres utilisateur dans votre organisation 365 Microsoft. Globanet fournit un connecteur [Salesforce chatter](http://globanet.com/chatter/) qui capture les éléments de la source de données tierce et importe ces éléments dans Microsoft 365. Le connecteur convertit le contenu tel que les conversations, les pièces jointes et les publications de Salesforce chatter en un format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données de Salesforce chatter sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention. L’utilisation d’un connecteur Salesforce chatter pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Vue d’ensemble des données d’archivage de la force de discussion

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données de la Salesforce chatter dans Microsoft 365.

![Flux de travail d’archivage pour les données de la Salesforce chatter](../media/SalesforceChatterConnectorWorkflow.png)

1. Votre organisation travaille avec Salesforce chatter pour installer et configurer un site de mise en conversation Salesforce.

2. Une fois toutes les 24 heures, les éléments de conversation Salesforce sont copiés sur le site Merge1 Globanet. Le connecteur force également les éléments de conversation à un format de message électronique.

3. Le connecteur de la protection contre les conversations que vous créez dans le centre de conformité Microsoft 365, se connecte au site Merge1 Globanet tous les jours et transfère le contenu du chatter vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le connecteur importe les éléments convertis dans les boîtes aux lettres d’utilisateurs spécifiques en utilisant la valeur de la propriété *email* du mappage utilisateur automatique, comme décrit à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception nommé **Salesforce chatter** est créé dans les boîtes aux lettres utilisateur, et les éléments sont importés dans ce dossier. Le connecteur détermine la boîte aux lettres dans laquelle importer les éléments à l’aide de la valeur de la propriété *email* . Chaque élément chatter contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant de l’élément.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Merge1 pour les connecteurs Microsoft. Pour créer un compte, contactez le [support client Globanet](https://globanet.com/contact-us/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Créez une application Salesforce et obtenez un jeton à l’adresse [https://salesforce.com](https://salesforce.com) . Vous devez vous connecter au compte Salesforce en tant qu’administrateur et obtenir un jeton personnel utilisateur pour importer des données. De plus, les déclencheurs doivent être publiés sur le site de conversation pour capturer les mises à jour, les suppressions et les modifications. Ces déclencheurs créent un post sur un canal, et Merge1 capture les informations à partir du canal. Pour obtenir des instructions pas à pas sur la création de l’application et l’acquisition du jeton, reportez-vous au Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur de la Salesforce chatter à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle exportation d’importation de boîtes aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>Étape 1 : configurer le connecteur de la mise en conversation de Salesforce

La première étape consiste à accéder à la page **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour les données de chatter.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **Data Connectors**  >  **Salesforce chatter**.

2. Sur la page Description du produit **Salesforce chatter** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant**.

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-salesforce-chatter-on-the-globanet-merge1-site"></a>Étape 2 : configurer le chatter de Salesforce sur le site Globanet Merge1

La deuxième étape consiste à configurer le connecteur du chatter Salesforce sur le site Merge1 Globanet. Pour plus d’informations sur la configuration du connecteur de la force chatter, voir [Merge1 tiers](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer,** la page de **mappage utilisateur** de l’Assistant connecteur dans le centre de conformité Microsoft 365 s’affiche.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer l’installation du connecteur dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **mapper les utilisateurs de la mise en conversation Salesforce aux utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments de chatter Salesforce incluent une propriété appelée *courrier électronique*, qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Cliquez sur **suivant**, vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>Étape 4 : surveiller le connecteur de la force de discussion

Après avoir créé le connecteur de la mise en conversation de Salesforce, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sur le connecteur **Salesforce chat** pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source**, cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des données qui ont été importées dans Microsoft Cloud.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
