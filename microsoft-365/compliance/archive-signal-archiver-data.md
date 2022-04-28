---
title: Configurer un connecteur pour archiver les données de communication de signal dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données de communication signal dans Microsoft 365. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 234587b5c14b73cb16ce1002e7fcee41a98249a1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093128"
---
# <a name="set-up-a-connector-to-archive-signal-communications-data"></a>Configurer un connecteur pour archiver les données de communication de signal

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez le connecteur TeleMessage dans le portail de conformité Microsoft Purview pour importer et archiver les conversations signal, les pièces jointes, les fichiers et les messages et appels supprimés. Après avoir configuré et configuré un connecteur, il se connecte au compte TeleMessage de votre organisation et importe la communication mobile des employés à l’aide de TeleMessage Signal Archiver vers des boîtes aux lettres dans Microsoft 365.

Une fois que les données du connecteur Signal Archiver sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données de communication signal. Par exemple, vous pouvez effectuer une recherche dans la communication de signal à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données du connecteur Signal Archiver à un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur Signal Archiver pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux réglementations et aux stratégies réglementaires de gouvernance d’entreprise.

## <a name="overview-of-archiving-signal-communications-data"></a>Vue d’ensemble de l’archivage des données de communications de signal

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de communication de signal dans Microsoft 365.

![Flux de travail d’archivage des communications de signal.](../media/SignalConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage pour configurer un connecteur Signal Archiver. Pour plus d’informations, consultez [Activation de TeleMessage Signal Archiver pour Microsoft 365](https://www.telemessage.com/microsoft-365-activation-for-signal-archiver/).

2. En temps réel, les données signal de votre organisation sont copiées sur le site TeleMessage.

3. Le connecteur Signal Archiver que vous créez dans le portail de conformité se connecte au site TeleMessage tous les jours et transfère les messages électroniques des 24 dernières heures vers une zone de stockage Azure sécurisée dans le cloud Microsoft.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Signal Archiver sera créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y seront importés. Le connecteur effectue le mappage à l’aide de la valeur de la propriété *d’adresse e-mail de l’utilisateur* . Chaque message électronique contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse e-mail de l’utilisateur* , vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro mobile de l’utilisateur et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de messagerie, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de Microsoft 365 utilisateur valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse e-mail de l’utilisateur de l’élément de messagerie. Si le connecteur ne trouve pas de Microsoft 365 utilisateur valide dans le fichier de mappage personnalisé ou dans la propriété *d’adresse e-mail de l’élément* de courrier, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

- Commandez le [service Signal Archiver à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Inscrivez tous les utilisateurs qui nécessitent l’archivage de signal dans le compte TeleMessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse e-mail que celle utilisée pour leur compte Microsoft 365.

- Installez l’application Signal Archiver sur les téléphones mobiles de vos employés et activez-la. L’application Signal Archiver leur permet de communiquer et de discuter avec d’autres utilisateurs signal.

- L’utilisateur qui crée un connecteur Signal Archiver à l’étape 3 doit disposer du rôle Administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-signal-archiver-connector"></a>Créer un connecteur Signal Archiver

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer le connecteur Signal Archiver dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour se connecter au site TeleMessage et transfère les données de communication signal vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à <https://compliance.microsoft.com> Data **connectorsSignal** >  Archiver, puis cliquez **dessus**.

2. Dans la page de description du produit **Signal Archiver** , cliquez sur **Ajouter un connecteur.**

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Dans la page **Connexion à TeleMessage** , sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

    - **Nom d'utilisateur:** Votre nom d’utilisateur TeleMessage.

    - **Mot de passe:** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et accéder à la page suivante.

6. Dans la page **De mappage d’utilisateurs** , activez le mappage automatique des utilisateurs. Pour activer le mappage personnalisé, chargez un fichier CSV qui contient les informations de mappage utilisateur, puis cliquez sur **Suivant**.

7. Passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
