---
title: Configurer un connecteur pour archiver les données réseau O2 dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS et MMS à partir du réseau mobile O2 dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: cf3e7f42f8497b2bbba06ccda4e84956b731ede2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313256"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Configurer un connecteur pour archiver les données réseau O2

Utilisez un connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver des messages SMS (Short Messaging Service) et des appels vocaux à partir du réseau mobile O2. Après avoir configuré et configuré un connecteur, il se connecte au réseau O2 de votre organisation une fois par jour et importe des SMS et des appels vocaux vers des boîtes aux lettres dans Microsoft 365.

Une fois que les messages SMS et les appels vocaux sont stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux données réseau O2. Par exemple, vous pouvez rechercher des messages SMS réseau O2 et des appels vocaux à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient des données réseau O2 à un dépositaire dans un cas Advanced eDiscovery dossier. L’utilisation d’un connecteur réseau O2 pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-o2-network-data"></a>Vue d’ensemble de l’archivage des données réseau O2

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données réseau O2 dans Microsoft 365.

![Flux de travail d’archivage réseau O2.](../media/O2NetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et O2 pour configurer un connecteur réseau O2. Pour plus d’informations, [voir Archiveur réseau O2](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Une fois toutes les 24 heures, les messages SMS et les appels vocaux provenant du réseau O2 de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau O2 que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages SMS et les appels vocaux des 24 heures précédentes vers un emplacement stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu des messages SMS et des appels vocaux au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **SMS O2** et l’archiveur du réseau vocal est créé dans la boîte aux lettres d’un utilisateur spécifique et les éléments y sont importés. Le connecteur fait ce mappage à l’aide de la valeur de la propriété *d’adresse de messagerie de l’utilisateur* . Chaque message SMS et appel vocal contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse de messagerie de l’utilisateur* , vous pouvez également définir un mappage personnalisé en téléchargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse Microsoft 365 courrier électronique correspondante pour les utilisateurs de votre organisation. Si vous activez à la fois le mappage utilisateur automatique et le mappage personnalisé, pour chaque élément O2, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété d’adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de l’élément O2, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données réseau O2 sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez [le service d’archivage réseau O2 à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous inscrire à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau O2 et de votre contact de facturation pour remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages à partir d’O2.

- Enregistrez tous les utilisateurs qui nécessitent l’archivage des SMS et du réseau vocal O2 dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour Microsoft 365 compte.

- Vos employés doivent avoir des téléphones mobiles d’entreprise et de responsabilité d’entreprise sur le réseau mobile O2. L’archivage des messages Microsoft 365 n’est pas disponible pour les appareils byoD (Bring Your Own Devices) ou « Apportez vos propres appareils ».

- L’utilisateur qui crée un connecteur réseau O2 doit avoir le rôle d’administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le Centre de conformité Microsoft 365. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et conformité » dans Autorisations dans le Centre de sécurité [& conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Ce connecteur de données TeleMessage est disponible dans Cloud de la communauté du secteur public environnements dans Microsoft 365 cloud du gouvernement américain. Les applications et services tiers peuvent impliquer le stockage, la transmission et le traitement des données client de votre organisation sur des systèmes tiers qui sont en dehors de l’infrastructure Microsoft 365 et qui, par conséquent, ne sont pas couverts par les engagements en matière de conformité et de protection des données Microsoft 365. Microsoft ne fait aucune représentation que l’utilisation de ce produit pour se connecter à des applications tierces implique que ces applications tierces sont conformes FEDRAMP.

## <a name="create-an-o2-network-connector"></a>Créer un connecteur réseau O2

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau O2 dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer des messages SMS et des appels vocaux vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click **Data connectors** \> **O2 Network**.

2. Dans la page description **du produit réseau O2** , cliquez sur **Ajouter un connecteur**

3. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

4. Dans la page **Connexion à TeleMessage** , sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des utilisateurs** , activez le mappage utilisateur automatique et cliquez sur **Suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the Connectors tab in **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes détectés

- Pour l’instant, nous ne ons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.