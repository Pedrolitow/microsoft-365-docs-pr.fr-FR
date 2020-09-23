---
title: Configuration d’un connecteur pour l’archivage des données réseau O2 dans Microsoft 365
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
description: Les administrateurs peuvent configurer un connecteur de télémessage pour importer et archiver des données SMS et MMS à partir du réseau mobile O2 dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 39a56e58bd9259b31138a4acf58a5ea5f432bc15
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48196299"
---
# <a name="set-up-a-connector-to-archive-o2-network-data"></a>Configuration d’un connecteur pour l’archivage des données réseau O2

Utilisez un connecteur de Télémessage dans le centre de conformité Microsoft 365 pour importer et archiver des messages SMS (Short Messaging Service) et des appels vocaux à partir du réseau mobile O2. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au réseau O2 de votre organisation une fois par jour et importe des appels SMS et vocaux vers des boîtes aux lettres dans Microsoft 365.

Une fois que les messages SMS et les appels vocaux sont stockés dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention 365 Microsoft pour les données réseau O2. Par exemple, vous pouvez rechercher des messages SMS et des appels vocaux réseau en utilisant la recherche de contenu ou associer la boîte aux lettres contenant des données réseau en O2 à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur réseau O2 pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-o2-network-data"></a>Vue d’ensemble de l’archivage des données réseau O2

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données réseau O2 dans Microsoft 365.

![Flux de travail d’archivage réseau O2](../media/O2NetworkConnectorWorkflow.png)

1. Votre organisation fonctionne avec les télémessages et O2 pour configurer un connecteur réseau O2. Pour plus d’informations, consultez la rubrique [O2 Network archiver](https://www.telemessage.com/office365-activation-for-o2-network-archiver).

2. Une fois toutes les 24 heures, les messages SMS et les appels vocaux du réseau en O2 de votre organisation sont copiés sur le site de Télémessage.

3. Le connecteur réseau O2 que vous créez dans le centre de conformité Microsoft 365 se connecte au site de Télémessage quotidiennement et transfère les messages SMS et les appels vocaux des dernières 24 heures vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft. Le connecteur convertit également le contenu des messages SMS et des appels vocaux au format d’un message électronique.

4. Le connecteur importe les éléments de communication mobile vers la boîte aux lettres d’utilisateurs spécifiques. Un nouveau dossier appelé **O2 SMS et le service d’archivage de réseau vocal** est créé dans la boîte aux lettres d’un utilisateur spécifique et les éléments y sont importés. Le connecteur effectue ce mappage à l’aide de la valeur de la propriété d' *adresse de messagerie* de l’utilisateur. Tous les messages SMS et appels vocaux contiennent cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message.

   Outre le mappage utilisateur automatique à l’aide de la valeur de la propriété de l' *adresse de messagerie* de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le numéro de téléphone mobile et l’adresse de messagerie Microsoft 365 correspondante pour les utilisateurs de votre organisation. Si vous activez le mappage utilisateur et le mappage personnalisés, pour chaque élément O2, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas un utilisateur Microsoft 365 valide correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise les valeurs de la propriété adresse de messagerie de l’élément qu’il tente d’importer. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans la propriété adresse de messagerie de l’élément O2, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines étapes de mise en œuvre requises pour l’archivage des données réseau O2 sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer un connecteur dans le centre de conformité.

- Commandez le [service d’archivage réseau O2 à partir du Télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365/) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur dans le centre de conformité.

- Obtenez votre compte réseau O2 et les détails de votre contact de facturation afin de pouvoir remplir les formulaires d’intégration de Télémessage et commander le service d’archivage de messages à partir de O2.

- Inscrivez tous les utilisateurs qui requièrent l’archivage de réseau vocal et de SMS en O2 dans le compte de Télémessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Vos employés doivent avoir des téléphones mobiles appartenant à une entreprise et appartenant à une entreprise sur le réseau mobile O2. Les messages d’archivage dans Microsoft 365 ne sont pas disponibles pour les appareils appartenant aux employés ou «apportez vos propres périphériques (BYOD).

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Vous devrez fournir ce consentement lors de la création du connecteur. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification de l’administrateur général Microsoft 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer un connecteur réseau O2.

- L’utilisateur qui crée un connecteur réseau O2 doit disposer du rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="create-an-o2-network-connector"></a>Créer un connecteur réseau O2

Une fois que vous avez terminé les conditions préalables décrites dans la section précédente, vous pouvez créer un connecteur réseau O2 dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site de Télémessage et transférer les messages SMS et les appels vocaux vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **connexions de données** \> **O2 réseau**.

2. Sur la page Description du produit **réseau O2** , cliquez sur **Ajouter un connecteur** .

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Sur la page **connexion à un message** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **suivant**.

   - **Nom d’utilisateur :** Nom d’utilisateur de votre Télémessage.

   - **Mot de passe :** Mot de passe de votre Télémessage.

5. Une fois le connecteur créé, vous pouvez fermer la fenêtre contextuelle et passer à la page suivante.

6. Sur la page mappage de l' **utilisateur** , activez mappage utilisateur automatique, puis cliquez sur **suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **suivant**.

7. Fournissez le consentement de l’administrateur, puis cliquez sur **suivant**.

   Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Office 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

8. Vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

9. Accédez à l’onglet Connecteurs de la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes ou d’éléments dont la taille est supérieure à 10 Mo. La prise en charge des éléments plus importants sera disponible ultérieurement.
