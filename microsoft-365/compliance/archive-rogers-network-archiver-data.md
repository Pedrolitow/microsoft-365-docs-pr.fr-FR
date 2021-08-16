---
title: Configurer un connecteur pour archiver les données réseau de Base de données dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver les données réseau de Contrôle dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: c17b81095e9113cdd0948c33ec2e2b7e4909fe73
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58257538"
---
# <a name="set-up-a-connector-to-archive-rogers-network-data-preview"></a>Configurer un connecteur pour archiver les données réseau de Archive (prévisualisation)

Utilisez le connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver des données SMS et MMS à partir du réseau mobile deCope. Une fois que vous avez configuré et configuré un connecteur Archiveur réseau [Dec,](https://www.telemessage.com/mobile-archiver/network-archiver/rogers/)il se connecte au réseau mobile de Votre organisation, puis importe les données SMS et MMS dans les boîtes aux lettres dans Microsoft 365.

Une fois que les données du réseau mobile de Contrôle sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données. Par exemple, vous pouvez rechercher des MESSAGES SMS et MMS à partir du réseau mobile dePata à l’aide de la recherche de contenu ou d’une recherche associée à un cas core eDiscovery. L’utilisation d’un connecteur Archiveur réseau de Contrôle pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux réglementations de gouvernance d’entreprise et aux stratégies réglementaires.

## <a name="overview-of-archiving-rogers-mobile-network-data"></a>Vue d’ensemble de l’archivage des données du réseau mobile de Lasa

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver des données SMS et MMS Dans Microsoft 365.

![Flux de travail d’archivage du réseau DeNte](../media/RogersNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage pour configurer un connecteur d’archivage réseau DeNter. Pour plus d’informations, voir [Activating the TeleMessage Archiver network archiver for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-the-rogers-network-archiver/).

2. En temps réel, les données du réseau mobile de Votre organisation sont copiées sur le site TeleMessage.

3. Le connecteur Archiveur réseau DeNte que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages électroniques des 24 heures précédentes vers une zone stockage Azure sécurisée dans Microsoft Cloud.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Archiveur réseau SMS/MMS Sera créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y seront importés. Le connecteur fait le mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque message électronique contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro mobile de l’utilisateur et l’adresse Microsoft 365 boîte aux lettres correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et fournissez un mappage personnalisé, pour chaque élément de courrier électronique, le connecteur examinera d’abord le fichier de mappage personnalisé. S’il ne trouve pas un utilisateur Microsoft 365 valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse de messagerie de l’utilisateur de l’élément de courrier. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de *l’utilisateur* de l’élément de courrier, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Commandez [le service Archiver réseau DeNter à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous connectez à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Enregistrez tous les utilisateurs qui ont besoin de l’archivage réseau DeNter dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour Microsoft 365 compte.

- Vos employés doivent avoir des téléphones mobiles d’entreprise et responsables sur le réseau mobile O2. L’archivage des messages Microsoft 365 n’est pas disponible pour les appareils byoD (Bring Your Own Devices) ou « Apportez vos propres appareils ».

- Obtenez les coordonnées du compte Et du contact de facturation de votre organisation afin que vous pouvez remplir les formulaires d’intégration et commander le service d’archivage des messages auprès de Domaine.

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur d’archivage réseau à l’étape 3 Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

## <a name="create-a-rogers-network-archiver-connector"></a>Créer un connecteur Archiveur réseau DeNter

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer le connecteur Archiveur réseau DeNtres dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer les données SMS/MMS de Type Sms vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors**  >  **Archiver Network Archiver**.

2. Dans la page description du produit Archiveur réseau **de Archiveur** de réseau, cliquez sur **Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

    - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

    - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs,** activez le mappage utilisateur automatique. Pour activer le mappage personnalisé, téléchargez un fichier CSV qui contient les informations de mappage utilisateur, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the Connectors tab in **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
