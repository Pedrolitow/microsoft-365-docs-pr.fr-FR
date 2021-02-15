---
title: Configurer un connecteur pour archiver les données réseau SMS/MMS de Bell
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS et MMS à partir du réseau Bell. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: d615488e5f6441efd828a6b91c187e7a8f5ca2c8
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620475"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Configurer un connecteur pour archiver les données du réseau Bell

Utilisez un connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver des messages SMS (Short Messaging Service) et MMS (Multimedia Messaging Service) à partir du réseau Bell. Une fois que vous avez configuré et configuré un connecteur, il se connecte au réseau Bell de votre organisation une fois par jour et importe les messages SMS et MMS dans les boîtes aux lettres dans Microsoft 365.

Une fois que les messages SMS et MMS sont stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données du réseau Bell. Par exemple, vous pouvez effectuer une recherche SMS/MMS sur le réseau Bell à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données du connecteur du réseau Bell à un dépositaire dans un cas advanced eDiscovery. L’utilisation d’un connecteur réseau Bell pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les politiques gouvernementales et réglementaires.

## <a name="overview-of-archiving-bell-network-data"></a>Vue d’ensemble de l’archivage des données du réseau Bell

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données du réseau Bell dans Microsoft 365.

![Flux de travail d’archivage du réseau Bell](../media/BellNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et Bell pour configurer un connecteur de réseau Dent. Pour plus d’informations, voir [l’Archiveur du réseau Bell.](https://www.telemessage.com/office365-activation-for-bell-network-archiver)

2. Une fois toutes les 24 heures, les messages SMS et MMS du réseau Bell de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau Bell que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages SMS et MMS des 24 heures précédentes vers un emplacement de stockage Azure sécurisé dans Microsoft Cloud. Le connecteur convertit également le contenu des messages SMS et MMS au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé Archiveur réseau **SMS/MMS De Bell** est créé dans la boîte aux lettres d’un utilisateur spécifique et les éléments y sont importés. Le connecteur fait ce mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque MESSAGE SMS et MMS contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse de messagerie Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez à la fois le mappage d’utilisateurs automatique et le mappage personnalisé, pour chaque élément réseau De Lat; le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété d’adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété de l’adresse de messagerie de l’élément Réseau De Latte, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines des étapes d’implémentation requises pour archiver les données du réseau Bell sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez [le service d’archivage du réseau Bell à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous connectez à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau Et de votre contact de facturation pour remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages auprès de Bell.

- Enregistrez tous les utilisateurs qui nécessitent l’archivage réseau SMS/MMS de Bell dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent avoir des téléphones mobiles d’entreprise et de responsabilité d’entreprise sur le réseau mobile De l’entreprise. Les messages d’archivage dans Microsoft 365 ne sont pas disponibles pour les appareils de l’employé ou « Apportez vos propres appareils (BYOD).

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur de réseau Bell dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

## <a name="create-a-bell-network-connector"></a>Créer un connecteur de réseau Bell

La dernière étape consiste à créer un connecteur réseau Bell dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer des messages SMS/MMS vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and then click Data **connectors**  >  **Bell SMS/MMS Network Archiver**.

2. Dans la page description du produit du réseau **Bell,** cliquez **sur Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs,** activez le mappage utilisateur automatique. Pour activer le mappage personnalisé, téléchargez un fichier CSV qui contient les informations de mappage utilisateur, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the **Connectors** tab on the **Data connectors** page in the compliance center to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
