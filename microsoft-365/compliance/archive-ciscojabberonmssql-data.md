---
title: Configuration d’un connecteur pour l’archivage de Cisco Jabber sur les données MS SQL dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données Cisco Jabber à partir de Globanet dans Microsoft 365. Ce connecteur vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: c93e0e702fba5a8232f3d41b3b6a32ab12216b3c
ms.sourcegitcommit: 16cbac5eacadd7b30cbca1fd2435ba9098de5e1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "48785548"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-data"></a>Configuration d’un connecteur pour l’archivage des données Cisco Jabber

Utilisez un connecteur Globanet dans le centre de conformité Microsoft 365 pour importer et archiver des données à partir de la plateforme Jabber Cisco vers des boîtes aux lettres utilisateur dans votre organisation 365 Microsoft. Globanet fournit un connecteur [Cisco Jabber](https://globanet.com/jabber/) qui est configuré pour capturer des éléments à partir de la base de données MS SQL de Jabber, tels que des messages de conversation de 1:1 et des conversations de groupe, puis pour importer ces éléments dans Microsoft 365. Le connecteur extrait des données de la base de données MS SQL de Cisco Jabber, les traite, puis convertit le contenu du compte Cisco Jabber d’un utilisateur en format de message électronique, puis importe ces éléments dans la boîte aux lettres de l’utilisateur dans Microsoft 365.

Une fois que les données Cisco Jabber sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, eDiscovery, les stratégies de rétention et les étiquettes de rétention et la conformité des communications. L’utilisation d’un connecteur Cisco Jabber pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Vue d’ensemble de l’archivage des données Cisco Jabber

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données Cisco Jabber dans Microsoft 365.

![Flux de travail d’archivage pour les données Cisco Jabber](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Votre organisation travaille avec Cisco pour installer et configurer une base de données Cisco Jabber sur MS SQL.

2. Une fois toutes les 24 heures, les éléments Cisco Jabber sont copiés de la base de données MS SQL vers le site Globanet Merge1. Le connecteur convertit également le contenu des messages de conversation au format d’un message électronique.

3. Le connecteur Cisco Jabber que vous créez dans le centre de conformité Microsoft 365 se connecte au site Globanet Merge1 tous les jours et transfère les éléments vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft.

4. Le mappage utilisateur automatique en tant que connecteur importe des éléments dans les boîtes aux lettres d’utilisateurs spécifiques à l’aide de la valeur de la propriété *email* de la décrite à l' [étape 3](#step-3-map-users-and-complete-the-connector-setup). Un sous-dossier du dossier boîte de réception nommé **Cisco Jabber sur MS SQL** est créé dans les boîtes aux lettres utilisateur, et les éléments de message sont importés dans ce dossier. Le connecteur effectue cette opération à l’aide de la valeur de la propriété *email* . Chaque élément Jabber de Cisco contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant des messages.

## <a name="before-you-begin"></a>Avant de commencer

- Créez un compte Globanet Merge1 pour Microsoft Connectors. Pour ce faire, contactez le [support client Globanet](https://globanet.com/ms-connectors-contact/). Vous devez vous connecter à ce compte lorsque vous créez le connecteur à l’étape 1.

- Vous devez configurer une base de données MS SQL pour extraire les éléments Jabber avant de créer le connecteur à l’étape 1. Vous devez spécifier les paramètres de connexion pour la base de données MS SQL lors de la configuration du connecteur Cisco Jabber à l’étape 2. Pour plus d’informations, consultez le Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- L’utilisateur qui crée le connecteur Cisco Jabber à l’étape 1 (et le termine à l’étape 3) doit être affecté au rôle exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-set-up-the-cisco-jabber-connector"></a>Étape 1 : configurer le connecteur Cisco Jabber

La première étape consiste à accéder aux **connecteurs de données** dans le centre de conformité Microsoft 365 et à créer un connecteur pour Cisco Jabber sur des données MS SQL.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connecteurs**  >  **de données Cisco Jabber sur MS SQL** .

2. Sur la page Description du produit **Cisco Jabber sur MS SQL** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter** .

4. Entrez un nom unique qui identifie le connecteur, puis cliquez sur **suivant** .

5. Connectez-vous à votre compte Merge1 pour configurer le connecteur.

## <a name="step-2-configure-the-cisco-jabber-connector-on-the-globanet-merge1-site"></a>Étape 2 : configurer le connecteur Cisco Jabber sur le site Merge1 Globanet

La deuxième étape consiste à configurer le Cisco Jabber sur MS SQL Connector sur le site Merge1 Globanet. Pour plus d’informations sur la configuration de Cisco Jabber sur MS SQL Connector, consultez le Guide de l' [utilisateur des connecteurs tiers Merge1](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Une fois que vous avez cliqué sur **enregistrer & terminer** , vous êtes redirigé vers le centre de conformité Microsoft 365, sur la page **mappage utilisateur** de l’Assistant connecteur.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>Étape 3 : mapper les utilisateurs et terminer l’installation du connecteur

Pour mapper les utilisateurs et terminer le connecteur configuré dans le centre de conformité Microsoft 365, procédez comme suit :

1. Sur la page **mapper les utilisateurs Cisco Jabber sur MS SQL aux utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique. Les éléments Cisco Jabber sur MS SQL incluent une propriété appelée *email* , qui contient des adresses de messagerie pour les utilisateurs de votre organisation. Si le connecteur peut associer cette adresse à un utilisateur de Microsoft 365, les éléments sont importés dans la boîte aux lettres de cet utilisateur.

2. Sur la page consentement de l' **administrateur** , cliquez sur **fournir le consentement** . Vous serez redirigé vers le site Microsoft. Cliquez sur **accepter** pour fournir le consentement.

   Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Microsoft 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

3. Cliquez sur **suivant** , vérifiez vos paramètres, puis accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>Étape 4 : analyse du connecteur Cisco Jabber

Une fois que vous avez créé le Cisco Jabber sur MS SQL Connector, vous pouvez afficher l’état du connecteur dans le centre de conformité Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Cliquez sur l’onglet **connecteurs** , puis sélectionnez le **Cisco Jabber sur MS SQL** Connector pour afficher la page de menu volant, qui contient les propriétés et les informations relatives au connecteur.

3. Sous **État du connecteur avec source** , cliquez sur le lien **Télécharger le journal** pour ouvrir (ou enregistrer) le journal d’État du connecteur. Ce journal contient des données qui ont été importées dans Microsoft Cloud.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
