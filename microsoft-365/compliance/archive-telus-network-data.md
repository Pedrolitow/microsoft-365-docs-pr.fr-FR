---
title: Configurer un connecteur pour archiver les données réseau DE LASER dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur TeleMessage pour importer et archiver des données SMS à partir du réseau DE DISTRIBUTION dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 8df1d7d9787e118144cb9e0a55c66bdd1e766194
ms.sourcegitcommit: 6fc6aaa2b7610e148f41018abd229e3c55b2f3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49620270"
---
# <a name="set-up-a-connector-to-archive-telus-network-data"></a>Configurer un connecteur pour archiver les données réseau DE LASO

Utilisez le connecteur TeleMessage dans le Centre de conformité Microsoft 365 pour importer et archiver des données SMS (Short Messaging Service) à partir du réseau GSM de votre organisation. Une fois que vous avez configuré et configuré un connecteur, il se connecte au réseau CAS DE votre organisation une fois par jour et importe les données SMS dans les boîtes aux lettres dans Microsoft 365.

Une fois que les messages SMS sont stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention Microsoft 365 aux donnéesIEZ. Par exemple, vous pouvez effectuer une recherche dans les messages SMS DE LA RECHERCHE DE CONTENU à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données DE LASV à un dépositaire dans un cas Advanced eDiscovery. L’utilisation d’un connecteur réseau DE DISTRIBUTION pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-telus-network-data"></a>Vue d’ensemble de l’archivage des données réseau DE LASV

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données réseau DUTN dans Microsoft 365.

![Flux de travail d’archivage réseau TORS](../media/TelusNetworkConnectorWorkflow.png)

1. Votre organisation travaille avec TeleMessage et LASUS pour configurer un connecteur réseau WORKS. Pour plus d’informations, voir [l’Archiveur réseau DE LASV.](https://www.telemessage.com/office365-activation-for-telus-network-archiver/)

2. Une fois toutes les 24 heures, les messages SMS provenant du réseau RETN de votre organisation sont copiés sur le site TeleMessage.

3. Le connecteur réseau RECUR que vous créez dans le Centre de conformité Microsoft 365 se connecte au site TeleMessage tous les jours et transfère les messages SMS des 24 heures précédentes vers un emplacement de stockage Azure sécurisé dans microsoft cloud. Le connecteur convertit également le contenu des messages SMS au format de message électronique.

4. Le connecteur importe les éléments de communication mobile dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **ARCHIVEur réseau SMS CAS** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur est mappage à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur. Chaque message SMS contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message SMS.

   Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *d’adresse* de messagerie de l’utilisateur, vous pouvez également implémenter un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse de messagerie Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez à la fois le mappage utilisateur automatique et le mappage personnalisé, pour chaque élément MAPPING, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété d’adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété d’adresse de messagerie de l’élément PDF, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines des étapes d’implémentation requises pour archiver les données réseau DUTN sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez [le service d’archivage réseau DE LASV à partir de TeleMessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devrez vous connectez à ce compte lorsque vous créerez le connecteur dans le centre de conformité.

- Obtenez les détails de votre compte réseau ET de votre contact de facturation POUR pouvoir remplir les formulaires d’intégration TeleMessage et commander le service d’archivage des messages à partir de LASV.

- Enregistrez tous les utilisateurs qui nécessitent l’archivage réseau SMS DE LASV dans le compte TeleMessage. Lors de l’inscription des utilisateurs, n’oubliez pas d’utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent avoir des téléphones mobiles d’entreprise et de responsabilité d’entreprise sur le réseau mobileTELUS. Les messages d’archivage dans Microsoft 365 ne sont pas disponibles pour les appareils BYOD (Bring Your Own Devices) ou d’employés.

- Le rôle Importation/Exportation de boîte aux lettres doit être attribué à l’utilisateur qui crée un connecteur réseau LIEN DANS Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

## <a name="create-a-telus-network-connector"></a>Créer un connecteur réseau DE DISTRIBUTION

Une fois que vous avez rempli les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau CAS DANS le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site TeleMessage et transférer des messages SMS vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Data **connectors**  >  **CLICK Network**.

2. Dans la page **description du produit RÉSEAU DE DISTRIBUTION,** cliquez sur Ajouter un **connecteur**

3. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

4. Dans la page **Connexion à TeleMessage,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Suivant**.

   - **Nom d’utilisateur :** Votre nom d’utilisateur TeleMessage.

   - **Mot de passe :** Votre mot de passe TeleMessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre pop-up et passer à la page suivante.

6. Dans la page **Mappage des** utilisateurs, activez le mappage utilisateur automatique et cliquez sur **Suivant.** Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **Suivant**.

7. Examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

8. Go to the Connectors tab in **Data connectors** page to see the progress of the import process for the new connector.

## <a name="known-issues"></a>Problèmes connus

- Pour l’instant, l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo n’est pas prise en charge. La prise en charge des éléments plus volumineux sera disponible à une date ultérieure.
