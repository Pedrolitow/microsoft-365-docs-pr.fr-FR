---
title: Configurer un connecteur pour archiver les données réseau O2 dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS et MMS à partir du réseau mobile O2 dans Microsoft 365. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 92782baff80a5b783a88f412af0ecec45ba40423
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67823582"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Configurer un connecteur pour archiver les données réseau O2

Utilisez un connecteur TeleMessage dans le portail de conformité Microsoft Purview pour importer et archiver des messages sms et des appels vocaux à partir du réseau mobile O2. Une fois que vous avez configuré et configuré un connecteur, il se connecte au réseau O2 de votre organisation une fois par jour et importe des sms et des appels vocaux aux boîtes aux lettres dans Microsoft 365.

Une fois que les sms et les appels vocaux sont stockés dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données réseau O2. Par exemple, vous pouvez rechercher des messages SMS et des appels vocaux réseau O2 à l’aide de la recherche de contenu ou associer la boîte aux lettres contenant des données réseau O2 à un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur réseau O2 pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-o2-network-data"></a>Vue d’ensemble de l’archivage des données réseau O2

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données du réseau O2 dans Microsoft 365.

![Flux de travail d’archivage réseau O2.](../media/O2NetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et O2 pour configurer un connecteur réseau O2. Pour plus d’informations, consultez [L’Archiveur réseau O2](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Une fois toutes les 24 heures, les SMS et les appels vocaux du réseau O2 de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau O2 que vous créez dans le portail de conformité se connecte au site TeleMessage tous les jours et transfère les sms et les appels vocaux des 24 dernières heures vers un emplacement de stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu des SMS et des appels vocaux au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **O2 SMS et Voice Network Archiver** est créé dans la boîte aux lettres d’un utilisateur spécifique et les éléments y sont importés. Le connecteur effectue ce mappage à l’aide de la valeur de la propriété *d’adresse Email de l’utilisateur*. Chaque sms et appel vocal contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse Email de l’utilisateur*, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse e-mail Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez le mappage automatique des utilisateurs et le mappage personnalisé, pour chaque élément O2, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs dans la propriété d’adresse e-mail de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse e-mail de l’élément O2, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données du réseau O2 sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez le [service O2 Network Archiver auprès de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau O2 et de votre contact de facturation pour pouvoir remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages à partir d’O2.

- Inscrivez tous les utilisateurs qui nécessitent l’archivage des SMS et des réseaux vocaux O2 dans le compte TeleMessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse e-mail que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent disposer de téléphones mobiles appartenant à l’entreprise et responsables de l’entreprise sur le réseau mobile O2. L’archivage des messages dans Microsoft 365 n’est pas disponible pour les appareils BYOD (Bring Your Own Devices) appartenant aux employés.

- L’utilisateur qui crée un connecteur réseau O2 doit se faire attribuer le rôle de connecteur de données Administration. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans les environnements GCC dans le cloud Microsoft 365 US Government. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui ne font pas partie de l’infrastructure Microsoft 365 et ne sont donc pas couverts par les engagements de Microsoft Purview et de protection des données. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-an-o2-network-connector"></a>Créer un connecteur réseau O2

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau O2 dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer des sms et des appels vocaux vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez au [https://compliance.microsoft.com](https://compliance.microsoft.com/) **réseau O2** **des connecteurs de données**, puis cliquez dessus\>.

2. Dans la page de description du produit **réseau O2** , cliquez sur **Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Dans la page **Connexion à TeleMessage** , sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d'utilisateur:** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe:** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et accéder à la page suivante.

6. Dans la page **De mappage d’utilisateurs** , activez le mappage automatique des utilisateurs, puis cliquez sur **Suivant**. Si vous avez besoin d’un mappage personnalisé, chargez un fichier CSV, puis cliquez sur **Suivant**.

7. Passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Accédez à l’onglet Connecteurs de la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments supérieurs à 10 Mo. La prise en charge des éléments plus volumineux sera disponible ultérieurement.