---
title: Configuration d’un connecteur pour l’archivage des données WhatsApp dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur de télémessage pour importer et archiver des données WhatsApp dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 573316f262295cce417876ef77510da14b877c67
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620180"
---
# <a name="set-up-a-connector-to-archive-whatsapp-data"></a>Configuration d’un connecteur pour l’archivage des données WhatsApp

Utilisez le connecteur de Télémessage dans le centre de conformité Microsoft 365 pour importer et archiver des appels WhatsApp, des conversations, des pièces jointes, des fichiers et des messages supprimés. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au compte de messagerie de votre organisation une fois par jour et importe la communication mobile des employés à l’aide de l’archiveur téléphonique des télémessages WhatsApp ou de l’archivage de Cloud WhatsApp sur les boîtes aux lettres de Microsoft 365.

Une fois que les données WhatsApp sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention 365 Microsoft aux données WhatsApp. Par exemple, vous pouvez rechercher des messages WhatsApp à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient des messages WhatsApp à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur WhatsApp pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-whatsapp-data"></a>Vue d’ensemble des données d’archivage WhatsApp

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des données WhatsApp dans Microsoft 365.

![Flux de travail d’archivage WhatsApp](../media/WhatsAppConnectorWorkflow.png)

1. Votre organisation utilise le télémessage pour configurer un connecteur d’archivage WhatsApp. Pour plus d’informations, consultez la rubrique [WhatsApp archiver](https://www.telemessage.com/office365-activation-for-whatsapp-archiver).

2. Une fois toutes les 24 heures, les données WhatsApp de votre organisation sont copiées sur le site de Télémessage.

3. Le connecteur WhatsApp que vous créez dans le centre de conformité Microsoft 365 se connecte au site de Télémessage quotidiennement et transfère les données WhatsApp des dernières 24 heures vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft. Le connecteur convertit également les données de WhatsApp de contenu au format d’un message électronique.

4. Le connecteur importe les données WhatsApp vers la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **WhatsApp archiver** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur effectue ce mappage à l’aide de la valeur de la propriété d' *adresse de messagerie* de l’utilisateur. Chaque message WhatsApp contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message.

   Outre le mappage utilisateur automatique à l’aide de la valeur de la propriété d' *adresse de messagerie* de l’utilisateur, vous pouvez également implémenter un mappage personnalisé en téléchargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse de messagerie Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez le mappage utilisateur et le mappage personnalisés, pour chaque élément WhatsApp, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas un utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété adresse de messagerie de l’élément WhatsApp, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines des étapes d’implémentation requises pour archiver les données de communication WhatsApp sont externes à Microsoft 365 et doivent être terminées avant de pouvoir créer le connecteur dans le centre de conformité.

- Commandez le [service archiver WhatsApp à partir du Télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Inscrivez tous les utilisateurs qui requièrent l’archivage WhatsApp dans le compte de Télémessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Installez l’application d' [archivage de téléphone WhatsApp](https://www.telemessage.com/mobile-archiver/whatsapp-phone-archiver-2/) TeleMessage sur les téléphones mobiles de vos employés et activez-la. Vous pouvez également installer les applications métier WhatsApp ou WhatsApp normales sur les téléphones mobiles de vos employés et activer le service WhatsApp Cloud archiver en numérisant un code QR sur le site Web des télémessages. Pour plus d’informations, consultez la rubrique [WhatsApp Cloud archiver](https://www.telemessage.com/mobile-archiver/whatsapp-archiver/whatsapp-cloud-archiver/).

- L’utilisateur qui crée un connecteur réseau Verizon doit disposer du rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="create-a-whatsapp-archiver-connector"></a>Créer un connecteur d’archivage WhatsApp

Une fois que vous avez terminé les conditions préalables décrites dans la section précédente, vous pouvez créer le connecteur WhatsApp dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site de Télémessage et transférer les données WhatsApp vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **Data Connectors**  >  **WhatsApp archiver**.

2. Sur la page Description du produit **WhatsApp archiver** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Sur la page **connexion à un message** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **suivant**.

   - **Nom d’utilisateur :** Nom d’utilisateur de votre Télémessage.

   - **Mot de passe :** Mot de passe de votre Télémessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et passer à la page suivante.

6. Sur la page mappage de l' **utilisateur** , activez mappage utilisateur automatique, puis cliquez sur **suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **suivant**.

7. Vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
