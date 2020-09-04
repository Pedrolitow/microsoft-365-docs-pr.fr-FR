---
title: Configuration d’un connecteur pour l’archivage des données mobiles Android
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les administrateurs peuvent configurer un connecteur de télémessage pour importer et archiver des appels SMS, MMS et vocaux à partir de téléphones mobiles Android. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 2284e09b3f04bf135435407a842f3e2c3f0648fa
ms.sourcegitcommit: a6625f76e8f19eebd9353ed70c00d32496ec06eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47362097"
---
# <a name="set-up-a-connector-to-archive-android-mobile-data-preview"></a>Configuration d’un connecteur pour l’archivage des données mobiles Android (aperçu)

Utilisez un connecteur de Télémessage dans le centre de conformité Microsoft 365 pour importer et archiver des messages SMS, MMS, des appels vocaux et des journaux d’appels à partir de téléphones mobiles Android. Une fois que vous avez configuré et configuré un connecteur, celui-ci se connecte au compte de messagerie de votre organisation une fois par jour et importe la communication mobile des employés à l’aide de TeleMessage Android archiver sur des boîtes aux lettres dans Microsoft 365.

Une fois que les données des téléphones mobiles Android sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la recherche de contenu et les stratégies de rétention de Microsoft 365 aux données d’archivage Android. Par exemple, vous pouvez effectuer des recherches dans Android archiver mobile communication à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données du connecteur Android à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur Android archiver pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-android-mobile-data"></a>Vue d’ensemble de l’archivage des données mobiles Android

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver des données mobiles Android dans Microsoft 365.

![Flux de travail du connecteur Android archiver](../media/AndroidArchiverConnectorWorkflow.png)

1. Votre organisation utilise le télémessage pour configurer un connecteur Android archiver. Pour plus d’informations, reportez-vous à la rubrique [Android archiver](https://www.telemessage.com/office365-activation-for-android-archiver/).

2. Une fois toutes les 24 heures, SMS, MMS, appels vocaux et journaux d’appels des téléphones mobiles Android de votre organisation sont copiés sur le site de Télémessage.

3. Le connecteur d’archivage Android que vous créez dans le centre de conformité Microsoft 365 se connecte au site de Télémessage tous les jours et transfère les données Android des 24 heures précédentes vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft. Le connecteur convertit également les données Android au format d’un message électronique.

4. Le connecteur importe les éléments de communication mobile vers la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé Android archiver sera créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y seront importés. Le connecteur effectue le mappage à l’aide de la valeur de la propriété de l' *adresse de messagerie de l’utilisateur* . Chaque message électronique contient cette propriété, qui est renseignée avec l’adresse de messagerie de chaque participant du message électronique. Outre le mappage utilisateur automatique à l’aide de la valeur de la propriété de l' *adresse de messagerie* de l’utilisateur, vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage doit contenir le numéro de téléphone mobile de l’utilisateur et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et que vous fournissez un mappage personnalisé, pour chaque élément de courrier, le connecteur regarde d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur valide de Microsoft 365 correspondant au numéro de téléphone mobile d’un utilisateur, le connecteur utilise la propriété d’adresse de messagerie de l’utilisateur de l’élément de courrier électronique. Si le connecteur ne trouve pas d’utilisateur valide de Microsoft 365 dans le fichier de mappage personnalisé ou dans la propriété de l’adresse de messagerie de l' *utilisateur* de l’élément de courrier, l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines étapes de mise en œuvre requises pour l’archivage des données de communication Android sont externes à Microsoft 365 et doivent être terminées avant que vous puissiez créer le connecteur dans le centre de conformité.

- Commandez le [service d’archivage Android à partir du Télémessage](https://www.telemessage.com/mobile-archiver/order-mobile-archiver-for-o365) et obtenez un compte d’administration valide pour votre organisation. Vous devez vous connecter à ce compte lorsque vous créez le connecteur.

- Inscrivez tous les utilisateurs qui ont besoin du service d’archivage Android dans le compte de Télémessage. Lors de l’inscription des utilisateurs, veillez à utiliser la même adresse de messagerie que celle utilisée pour leur compte Microsoft 365.

- Installez et activez l’application d’archivage de Télémessage Android sur les téléphones mobiles de vos employés.

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Vous devrez fournir ce consentement lors de la création du connecteur. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification de l’administrateur général Microsoft 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer un connecteur réseau AT&T.

- L’utilisateur qui crée un connecteur Android archiver doit se voir attribuer le rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Cela est nécessaire pour ajouter des connecteurs dans la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="create-an-android-archiver-connector"></a>Créer un connecteur d’archivage Android

La dernière étape consiste à créer un connecteur Android archiver dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site de Télémessage et transférer la communication Android dans les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et cliquez sur **Data Connectors**  >  **Android archiver**.

2. Sur la page Description du produit **Android archiver** , cliquez sur **Ajouter un connecteur**.

3. Sur la page **conditions de service** , cliquez sur **accepter**.

4. Sur la page **connexion à un message** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **suivant**.

   - **Nom d’utilisateur :** Nom d’utilisateur de votre Télémessage.

   - **Mot de passe :** Mot de passe de votre Télémessage.

5. Une fois le connecteur créé, fermez la fenêtre contextuelle, puis cliquez sur **suivant**.

6. Sur la page mappage de l' **utilisateur** , activez mappage utilisateur automatique, puis cliquez sur **suivant**. Si vous avez besoin d’un mappage personnalisé, téléchargez un fichier CSV, puis cliquez sur **suivant**.

7. Fournissez le consentement de l’administrateur, puis cliquez sur **suivant**.

   Pour fournir le consentement de l’administrateur, vous devez être connecté avec les informations d’identification d’un administrateur général Office 365, puis accepter la demande de consentement. Si vous n’êtes pas connecté en tant qu’administrateur général, vous pouvez accéder à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) et vous connecter à l’aide des informations d’identification d’administrateur général pour accepter la demande.

8. Vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

9. Accédez à l’onglet Connecteurs de la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.

## <a name="known-issues"></a>Problèmes connus

- Pour le moment, nous ne prenons pas en charge l’importation de pièces jointes d’une taille supérieure à 10 Mo, mais la prise en charge des éléments plus importants sera disponible ultérieurement.
