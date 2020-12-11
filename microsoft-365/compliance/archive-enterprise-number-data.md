---
title: Configuration d’un connecteur pour l’archivage des données à partir du programme d’archivage des numéros de télémessages
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données SMS et MMS à partir d’un programme d’archivage des numéros de Télémessage. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 01c2807606449c576e292f8819a861b1193b4723
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620020"
---
# <a name="set-up-a-connector-to-archive-enterprise-number-data"></a>Configuration d’un connecteur pour l’archivage des données de numéro d’entreprise

Utilisez un connecteur de Télémessage dans le centre de conformité Microsoft 365 pour importer et archiver des messages SMS (Short Messaging Service) et MMS (Multimedia Messaging Service), des messages de conversation, des enregistrements d’appels vocaux et des journaux d’appels vocaux à partir de l’archiveur de numéros d’entreprise. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au compte de messagerie de votre organisation une fois par jour et importe les données de communication mobile des employés à l’aide du programme d’archivage de numéros de téléphone pour les boîtes aux lettres de Microsoft 365.

Une fois que les données du connecteur du programme d’archivage de numéro de Télémessage sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que les stratégies de conservation pour litige, de recherche de contenu In-Place, d’archivage, d’audit, de conformité des communications et de rétention Microsoft 365 aux données de l’archiveur d’entreprise. Par exemple, vous pouvez effectuer une recherche dans le contenu de la recherche de contenu d’entreprise de télémessages SMS, MMS et appel vocal à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données du connecteur d’archive de numéro d’entreprise à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur d’archiveur de numéro d’entreprise pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-enterprise-number-data"></a>Vue d’ensemble des données de numéro d’entreprise d’archivage

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données du réseau d’entreprise dans Microsoft 365.

![Flux de travail d’archivage numéro entreprise](../media/EnterpriseNumberConnectorWorkflow.png)

1. Votre organisation utilise le télémessage pour configurer un connecteur d’archivage de numéro d’entreprise. Pour plus d’informations, reportez-vous à [ici](https://www.telemessage.com/office365-activation-for-enterprise-number-archiver/).

2. Le connecteur de l’archiveur de numéro d’entreprise que vous créez dans le centre de conformité Microsoft 365 se connecte au site de Télémessage tous les jours et transfère les messages électroniques des 24 heures précédents vers une zone de stockage Azure sécurisée dans le Cloud Microsoft.

3. Le connecteur importe les éléments de communication mobile vers la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Enterprise Number Archiver est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur effectue le mappage à l’aide de la valeur de la propriété de l' *adresse de messagerie de l’utilisateur* . Chaque message électronique contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message électronique. Outre le mappage utilisateur automatique à l’aide de la valeur de la propriété de l' *adresse de messagerie* de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro de téléphone mobile de l’utilisateur et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et que vous fournissez un mappage personnalisé, pour chaque élément de courrier, le connecteur regarde d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur valide de Microsoft 365 correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse de messagerie de l’utilisateur de l’élément de courrier électronique. Si le connecteur ne trouve pas d’utilisateur valide de Microsoft 365 dans le fichier de mappage personnalisé ou dans la propriété de l’adresse de messagerie de l' *utilisateur* de l’élément de courrier, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines des étapes d’implémentation requises pour archiver les données d’archivage de numéro d’entreprise sont externes à Microsoft 365 et doivent être terminées avant que vous puissiez créer le connecteur dans le centre de conformité.

- Commandez le [service Archive de numéro d’entreprise dans le Télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Inscrivez tous les utilisateurs qui requièrent l’archivage réseau SMS/MMS de numéro d’entreprise dans le compte de Télémessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Installez et activez l’application d’archivage de numéro de télémessage pour les téléphones mobiles de vos employés.

- Le rôle importation/exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur d’archivage de numéro d’entreprise dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="create-an-enterprise-number-archiver-connector"></a>Créer un connecteur d’archivage de numéro de société

Une fois que vous avez terminé les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur d’archive de numéro d’entreprise dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site de Télémessage et transférer les messages d’appel vocal, MMS et SMS dans les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **Data Connectors** \> **archiveur de numéros d’entreprise**.

2. Dans la page Description du produit **Enterprise Number archiver** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Sur la page **connexion à un message** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **suivant**.

   - **Nom d’utilisateur :** Nom d’utilisateur de votre Télémessage.

   - **Mot de passe :** Mot de passe de votre Télémessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et passer à la page suivante.

6. Sur la page mappage de l' **utilisateur** , activez mappage utilisateur automatique. Pour activer le mappage personnalisé, téléchargez un fichier CSV contenant les informations de mappage de l’utilisateur, puis cliquez sur **suivant**.

7. Vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
