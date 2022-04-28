---
title: Configurer un connecteur pour archiver les données du réseau TELUS dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS à partir du réseau TELUS dans Microsoft 365. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 9199c38960cbc3e238f6ea8a47a06935c7867b69
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099694"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>Configurer un connecteur pour archiver les données du réseau TELUS

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez le connecteur TeleMessage dans le portail de conformité Microsoft Purview pour importer et archiver des données sms (Short Messaging Service) à partir du réseau TELUS de votre organisation. Après avoir configuré et configuré un connecteur, il se connecte au réseau TELUS de votre organisation une fois par jour et importe des données SMS dans des boîtes aux lettres dans Microsoft 365.

Une fois les SMS stockés dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu et Microsoft 365 stratégies de rétention aux données TELUS. Par exemple, vous pouvez rechercher des messages SMS TELUS à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant les données TELUS à un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur réseau TELUS pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-telus-network-data"></a>Vue d’ensemble de l’archivage des données du réseau TELUS

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données du réseau TELUS dans Microsoft 365.

![Workflow d’archivage du réseau TELUS.](../media/TelusNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et TELUS pour configurer un connecteur réseau TELUS. Pour plus d’informations, consultez [l’Archiveur réseau TELUS](https://www.telemessage.com/office365-activation-for-telus-network-archiver/).

2. En temps réel, les SMS du réseau TELUS de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau TELUS que vous créez dans le portail de conformité se connecte au site TeleMessage tous les jours et transfère les sms des 24 dernières heures vers un emplacement stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu des SMS au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **ARCHIVEUR RÉSEAU SMS TELUS** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur effectue un mappage à l’aide de la valeur de la propriété *d’adresse e-mail de l’utilisateur* . Chaque SMS contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message SMS.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse e-mail de l’utilisateur* , vous pouvez également implémenter un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse e-mail Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez le mappage automatique des utilisateurs et le mappage personnalisé, pour chaque élément TELUS, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de Microsoft 365 utilisateur valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs dans la propriété d’adresse e-mail de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse e-mail de l’élément TELUS, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données du réseau TELUS sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez le [service ARCHIVEUR RÉSEAU TELUS auprès de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau TELUS et de votre contact de facturation afin de pouvoir remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages auprès de TELUS.

- Inscrivez tous les utilisateurs qui nécessitent l’archivage du réseau SMS TELUS dans le compte TeleMessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse e-mail que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent disposer de téléphones mobiles appartenant à l’entreprise et responsables de l’entreprise sur le réseau mobileTELUS. L’archivage des messages dans Microsoft 365 n’est pas disponible pour les appareils BYOD (Bring Your Own Devices) appartenant aux employés.

- Le rôle Administrateur du connecteur de données doit être attribué à l’utilisateur qui crée un connecteur réseau TELUS. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans Cloud de la communauté du secteur public environnements dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-a-telus-network-connector"></a>Créer un connecteur réseau TELUS

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau TELUS dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour se connecter au site TeleMessage et transférer des sms vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) Data **connectorsTELUS Network**, puis cliquez **dessus** > .

2. Dans la page de description du produit **du réseau TELUS** , cliquez sur **Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Dans la page **Connexion à TeleMessage** , sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d'utilisateur:** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe:** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et accéder à la page suivante.

6. Dans la page **De mappage d’utilisateurs** , activez le mappage automatique des utilisateurs, puis cliquez sur **Suivant**. Si vous avez besoin d’un mappage personnalisé, chargez un fichier CSV, puis cliquez sur **Suivant**.

7. Passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.
