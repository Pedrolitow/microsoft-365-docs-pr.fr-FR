---
title: Configurer un connecteur pour archiver les données de Bell SMS/MMS Network
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS et MMS à partir du réseau Bell. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: dc23e3788958270712bab493cd0364a80a0377f9
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992785"
---
# <a name="set-up-a-connector-to-archive-bell-network-data"></a>Configurer un connecteur pour archiver les données du réseau Bell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez un connecteur TeleMessage dans le portail de conformité Microsoft Purview pour importer et archiver les messages MMS (Short Messaging Service) et Multimedia Messaging Service (MMS) à partir du réseau Bell. Une fois que vous avez configuré et configuré un connecteur, il se connecte au réseau Bell de votre organisation une fois par jour et importe des messages SMS et MMS dans des boîtes aux lettres dans Microsoft 365.

Une fois les messages SMS et MMS stockés dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données du réseau Bell. Par exemple, vous pouvez effectuer une recherche par SMS/MMS bell network à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données du connecteur Bell Network à un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur Bell Network pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-bell-network-data"></a>Vue d’ensemble de l’archivage des données de Bell Network

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données du réseau Bell dans Microsoft 365.

![Flux de travail d’archivage de Bell Network.](../media/BellNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et Bell pour configurer un connecteur Bell Network. Pour plus d’informations, consultez [Bell Network Archiver](https://www.telemessage.com/office365-activation-for-bell-network-archiver).

2. En temps réel, les messages SMS et MMS du réseau Bell de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur Bell Network que vous créez dans le portail de conformité se connecte au site TeleMessage tous les jours et transfère les messages SMS et MMS des 24 heures précédentes vers un emplacement stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu des messages SMS et MMS au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **Bell SMS/MMS Network Archiver** est créé dans la boîte aux lettres d’un utilisateur spécifique et les éléments y sont importés. Le connecteur effectue ce mappage à l’aide de la valeur de la propriété Adresse *e-mail de l’utilisateur* . Chaque message SMS et MMS contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse e-mail de l’utilisateur* , vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse e-mail Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez à la fois le mappage automatique des utilisateurs et le mappage personnalisé, pour chaque élément bell network, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de Microsoft 365 utilisateur valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs dans la propriété d’adresse e-mail de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse e-mail de l’élément Réseau Bell, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données du réseau Bell sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez le [service Bell Network Archiver auprès de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte Bell Network et de votre contact de facturation afin de pouvoir remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages auprès de Bell.

- Inscrivez tous les utilisateurs qui nécessitent l’archivage du réseau SMS/MMS Bell dans le compte TeleMessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse e-mail que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent avoir des téléphones mobiles appartenant à l’entreprise et responsables de l’entreprise sur le réseau mobile De Bell. L’archivage des messages dans Microsoft 365 n’est pas disponible pour les appareils BYOD (Bring Your Own Devices) appartenant aux employés.

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée un connecteur Bell Network. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-bell-network-connector"></a>Créer un connecteur Bell Network

La dernière étape consiste à créer un connecteur Bell Network dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour se connecter au site TeleMessage et transférer des messages SMS/MMS vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez, [https://compliance.microsoft.com](https://compliance.microsoft.com) puis cliquez sur **Data connectorsBell** >  **SMS/MMS Network Archiver**.

2. Dans la page de description du produit **Bell Network** , cliquez sur **Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Dans la page **Connexion à TeleMessage** , sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d'utilisateur:** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe:** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et accéder à la page suivante.

6. Dans la page **De mappage d’utilisateurs** , activez le mappage automatique des utilisateurs. Pour activer le mappage personnalisé, chargez un fichier CSV qui contient les informations de mappage utilisateur, puis cliquez sur **Suivant**.

7. Passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet **Connecteurs** de la page **Connecteurs de données** dans le centre de conformité pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
