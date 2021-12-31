---
title: Configurer un connecteur pour archiver les données de communications Der dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver les données de communications Der dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: e241cd087b16e6b07902eae39c1cb9e7c0e6818b
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2021
ms.locfileid: "61646090"
---
# <a name="set-up-a-connector-to-archive-telegram-communications-data"></a>Configurer un connecteur pour archiver les données de communications Der

Utilisez le connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver des conversations, des pièces jointes, des fichiers et des messages et appels supprimés. Une fois que vous avez configuré et configuré un connecteur, il se connecte au compte TeleMessage de votre organisation et importe la communication mobile des employés à l’aide de l’archiveur Archiver Archiver dans les boîtes aux lettres de Microsoft 365.

Une fois que les données du connecteur Archiveur Archiveur Sont stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données de communication de Contrôle. Par exemple, vous pouvez effectuer une recherche dans la communication à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données du connecteur Archiver archiveur à un dépositaire dans Advanced eDiscovery cas. L’utilisation d’un connecteur Archiveur Archiver pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux réglementations de gouvernance d’entreprise et aux stratégies réglementaires.

## <a name="overview-of-archiving-telegram-communications-data"></a>Vue d’ensemble de l’archivage des données de communications de Communications Communications

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de communications Der dans Microsoft 365.

![Flux de travail d’archivage des communications de Domaine.](../media/TelegramConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage pour configurer un connecteur Archiver archiveur archiveur. Pour plus d’informations, voir [Activating the TeleMessage Archiver for Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-telegram-archiver/).

2. En temps réel, les données de votre organisation sont copiées sur le site TeleMessage.

3. Le connecteur Archiveur archiveur archiveur que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages électroniques des 24 heures précédentes vers une zone stockage Azure sécurisée dans Microsoft Cloud.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Archiver Archiver sera créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y seront importés. Le connecteur fait ce mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque message électronique contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique.

> Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également définir un mappage personnalisé en téléchargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro mobile de l’utilisateur et l’adresse Microsoft 365 boîte aux lettres correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et fournissez un mappage personnalisé, pour chaque élément de courrier électronique, le connecteur examinera d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse de messagerie de l’utilisateur de l’élément de courrier. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de *l’utilisateur* de l’élément de courrier, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Commandez [le service d’archivage Deoe à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous inscrire à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Enregistrez tous les utilisateurs qui ont besoin de l’archivage Archiver Dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour Microsoft 365 compte.

- Installez l’application Archiver Archiver sur les téléphones mobiles de vos employés et activez-la. L’application Archiver archiveur permet aux utilisateurs de communiquer et de discuter avec d’autres utilisateurs de l’archive.

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur Archiveur Archiveur archiveur à l’étape 3 Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs** de données dans la Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](/Exchange/permissions-exo/role-groups#modify-role-groups) Créer des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ». [](/Exchange/permissions-exo/role-groups#create-role-groups)

- Ce connecteur de données TeleMessage est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-telegram-archiver-connector"></a>Créer un connecteur archiveur archiveur

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer le connecteur Archiver archiveur dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transfère les données de communication De Lass aux boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to <https://compliance.microsoft.com> and then click Data **connectors** > T **elegram Archiver**.

2. Dans la page **description du produit Archiver Archiver,** cliquez **sur Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

    - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

    - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs,** activez le mappage utilisateur automatique. Pour activer le mappage personnalisé, téléchargez un fichier CSV qui contient les informations de mappage utilisateur, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the Connectors tab in **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
