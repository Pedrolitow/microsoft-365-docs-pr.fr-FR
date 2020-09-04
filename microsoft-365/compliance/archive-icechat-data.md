---
title: Configuration d’un connecteur pour l’archivage des données de conversation ICE
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données de l’outil de conversation ICE dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 de sorte que vous puissiez utiliser les fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: b6b31c0ef9b083aa6432e35029fc14be1a817733
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358226"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data-preview"></a>Configuration d’un connecteur pour l’archivage des données de conversation ICE (aperçu)

Utilisez un connecteur natif dans le centre de conformité Microsoft 365 pour importer et archiver des données de conversation des services financiers à partir de l’outil de collaboration de conversation ICE. Une fois que vous avez configuré et configuré un connecteur, il se connecte au site ICE chat Secure (SFTP) de votre organisation une fois par jour, convertit le contenu des messages de conversation en format de message électronique, puis importe ces éléments dans des boîtes aux lettres dans Microsoft 365.

Une fois que les données de conversation ICE sont stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la découverte électronique, l’archivage, l’audit, la conformité de la communication et les stratégies de rétention Microsoft 365 aux données de conversation ICE. Par exemple, vous pouvez rechercher des messages de conversation ICE à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données de conversation ICE à un dépositaire dans un cas avancé de découverte électronique. L’utilisation d’un connecteur de conversation ICE pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-ice-chat-data"></a>Vue d’ensemble de l’archivage des données de conversation ICE

La vue d’ensemble suivante décrit le processus d’utilisation d’un connecteur pour archiver les données de conversation ICE dans Microsoft 365.

![Flux de travail d’archivage de conversation ICE](../media/ICEChatConnectorWorkflow.png)

1. Votre organisation travaille avec ICE chat pour configurer un site SFTP chat SFTP. Vous utiliserez également la conversation ICE pour configurer la conversation ICE afin de copier les messages de conversation sur votre site SFTP chat.

2. Une fois toutes les 24 heures, les messages de conversation provenant de ICE chat sont copiés sur votre site SFTP chat SFTP.

3. Le connecteur de conversation ICE que vous créez dans le centre de conformité Microsoft 365 se connecte au site SFTP chat chaque jour et transfère les messages de conversation des dernières 24 heures vers un emplacement de stockage Azure sécurisé dans le Cloud Microsoft. Le connecteur convertit également le contenu d’un massage de conversation au format d’un message électronique.

4. Le connecteur importe les éléments de message de conversation vers les boîtes aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **Ice chat** est créé dans les boîtes aux lettres des utilisateurs et les éléments de message de conversation seront importés dans ce dossier. Le connecteur utilise la valeur des propriétés *SenderEmail* et *RecipientEmail* . Chaque message de conversation contient ces propriétés, qui sont remplies avec l’adresse de messagerie de l’expéditeur et tous les destinataires/participants du message de conversation.

   Outre le mappage utilisateur automatique qui utilise les valeurs de la propriété *SenderEmail* et *RecipientEmail* (ce qui signifie que le connecteur importe un message de conversation dans la boîte aux lettres de l’expéditeur et les boîtes aux lettres de chaque destinataire), vous pouvez également définir un mappage utilisateur personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient le *ImId* de conversation Ice et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur de votre organisation. Si vous activez le mappage utilisateur automatique et fournissez un fichier de mappage personnalisé, pour chaque élément de conversation, le connecteur regarde d’abord le fichier de mappage personnalisé. S’il ne trouve pas de compte d’utilisateur Microsoft 365 valide correspondant au ImId de conversation ICE d’un utilisateur, le connecteur utilise les propriétés *SenderEmail* et *RecipientEmail* de l’élément conversation pour importer l’élément dans les boîtes aux lettres des participants à la conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans les propriétés *SenderEmail* et *RecipientEmail* , l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines étapes de mise en œuvre requises pour archiver les données de conversation ICE sont externes à Microsoft 365 et doivent être terminées avant de pouvoir créer le connecteur dans le centre de conformité.

- Votre organisation doit consentir à autoriser le service d’importation Office 365 à accéder aux données de boîte aux lettres dans votre organisation. Pour accepter cette demande, accédez à [cette page](https://login.microsoftonline.com/common/oauth2/authorize?client_id=570d0bec-d001-4c4e-985e-3ab17fdc3073&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent), connectez-vous à l’aide des informations d’identification d’un administrateur général Office 365, puis acceptez la demande. Vous devez effectuer cette étape avant de pouvoir créer le connecteur de conversation ICE à l’étape 3.

- La conversation ICE facture à ses clients une redevance pour la conformité externe. Votre organisation doit contacter le groupe de ventes ICE chat pour discuter et signer le contrat de services de conversation de ICE, que vous pouvez obtenir à l’adresse [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf) . Le présent contrat se trouve entre ICE chat et votre organisation et n’implique pas Microsoft. Une fois que vous avez configuré un site SFTP chat SFTP à l’étape 2, ICE chat fournit les informations d’identification FTP directement à votre organisation. Ensuite, vous fournissez ces informations d’identification à Microsoft lors de la configuration du connecteur à l’étape 3.

- Vous devez configurer un site SFTP de conversation ICE avant de créer le connecteur à l’étape 3. Après avoir travaillé avec ICE chat pour configurer le site SFTP, les données de la conversation ICE sont chargées sur le site SFTP tous les jours. Le connecteur que vous créez à l’étape 3 se connecte à ce site SFTP et transfère les données de conversation vers des boîtes aux lettres Microsoft 365. SFTP chiffre également les données de conversation ICE qui sont envoyées aux boîtes aux lettres pendant le processus de transfert.

- L’administrateur qui crée le connecteur de conversation ICE à l’étape 3 (et qui télécharge les clés publiques et l’adresse IP à l’étape 1) doit se voir attribuer le rôle d’exportation d’importation de boîte aux lettres dans Exchange Online. Ce rôle est nécessaire pour ajouter des connecteurs sur la page **connecteurs de données** dans le centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle exportation d’importation de boîte aux lettres au groupe de rôles gestion de l’organisation dans Exchange Online. Vous pouvez aussi créer un groupe de rôles, attribuer le rôle d’exportation d’importation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, reportez-vous aux sections [créer des groupes de rôles](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) ou modifier des [groupes](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) de rôles dans l’article « gérer des groupes de rôles dans Exchange Online ».

## <a name="step-1-obtain-ssh-and-pgp-public-keys"></a>Étape 1 : obtenir des clés publiques SSH et PGP

La première étape consiste à obtenir une copie des clés publiques pour le protocole SSH (Secure Shell) et PGP (Pretty bonne confidentialité). Utilisez ces clés à l’étape 2 pour configurer le site SFTP chat SFTP afin d’autoriser le connecteur (que vous créez à l’étape 3) à se connecter au site SFTP et transférer les données de conversation ICE aux boîtes aux lettres Microsoft 365. Vous obtiendrez également une adresse IP dans cette étape, que vous utiliserez lors de la configuration du site SFTP de conversation ICE.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Sur la page **connecteurs de données (aperçu)** sous **chat Ice**, cliquez sur **Afficher**.

3. Sur la page **conversation Ice** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **conditions de service** , cliquez sur **accepter**.

5. Sur la page **Ajouter des informations d’identification pour le site SFTP de conversation Ice** sous étape 1, cliquez sur les liens **Télécharger la clé SSH**, **Télécharger la clé PGP**et **Télécharger l’adresse IP** pour enregistrer une copie de chaque fichier sur votre ordinateur local. Ces fichiers contiennent les éléments suivants qui sont utilisés pour configurer le site SFTP chat SFTP à l’étape 2 :

   - Clé publique SSH : cette clé permet de configurer SSH sécurisé pour activer une connexion à distance sécurisée lorsque le connecteur se connecte au site SFTP de conversation ICE.

   - Clé publique PGP : cette clé permet de configurer le chiffrement des données transférées du site SFTP de conversation ICE vers Microsoft 365.

   - Adresse IP : le site SFTP chat SFTP est configuré pour accepter une demande de connexion uniquement à partir de cette adresse IP, utilisée par le connecteur de conversation ICE que vous créez à l’étape 3.

6. Cliquez sur **Annuler** pour fermer l’Assistant. Vous revenez à cet Assistant à l’étape 3 pour créer le connecteur.

## <a name="step-2-configure-the-ice-chat-sftp-site"></a>Étape 2 : configurer le site SFTP de conversation ICE

L’étape suivante consiste à utiliser les clés publiques SSH et PGP et l’adresse IP que vous avez obtenue à l’étape 1 pour configurer l’authentification SSH et le chiffrement PGP pour le site SFTP chat SFTP. Cela permet au connecteur de conversation ICE que vous créez à l’étape 3 de se connecter au site SFTP chat SFTP et de transférer les données de conversation ICE vers Microsoft 365. Vous devez utiliser le support technique de conversation ICE pour configurer votre site de conversation ICE.

## <a name="step-3-create-an-ice-chat-connector"></a>Étape 3 : créer un connecteur de conversation ICE

La dernière étape consiste à créer un connecteur de conversation ICE dans le centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site SFTP de conversation ICE et transférer les messages de conversation dans les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) , puis cliquez sur **connecteurs de données** dans le volet de navigation de gauche.

2. Sur la page **connecteurs de données** , sous **conversation Ice**, cliquez sur **Afficher**.

3. Sur la page **conversation Ice** , cliquez sur **Ajouter un connecteur**.

4. Sur la page **conditions de service** , cliquez sur **accepter**.

5. Sur la page **Ajouter des informations d’identification pour le site SFTP de conversation Ice** , sous étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **valider la connexion**.

   - **Code de confirmation :** ID de votre organisation, utilisé comme nom d’utilisateur pour le site SFTP chat SFTP.

   - **Mot de passe :** Le mot de passe de votre site SFTP de conversation ICE.

   - **URL sftp :** L’URL du site SFTP de conversation ICE (par exemple, sftp.theice.com).

   - **Port sftp :** Numéro de port du site SFTP de conversation ICE. Le connecteur utilise ce port pour se connecter au site SFTP.

6. Une fois la connexion validée, cliquez sur **suivant**.

7. Sur la page **connecter des utilisateurs externes à des utilisateurs de Microsoft 365** , activez le mappage utilisateur automatique et fournissez les mappages utilisateur personnalisés requis. Vous pouvez télécharger une copie du fichier CSV de mappage d’utilisateurs sur cette page. Vous pouvez ajouter les mappages utilisateur au fichier, puis le télécharger.

   > [!NOTE]
   > Comme expliqué précédemment, le fichier CSV de mappage de fichiers de correspondance contient le Imid de conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et que vous fournissez un mappage personnalisé, pour chaque élément de conversation, le connecteur regarde d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide correspondant au Imid de conversation ICE d’un utilisateur, le connecteur importe l’élément dans les boîtes aux lettres pour les utilisateurs spécifiés dans les propriétés *SenderEmail* et *RecipientEmail* de l’élément conversation. Si le connecteur ne trouve pas d’utilisateur valide de Microsoft 365 par le biais d’un mappage utilisateur automatique ou personnalisé, l’élément n’est pas importé.

8. Cliquez sur **suivant**, vérifiez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

9. Accédez à la page **connecteurs de données** pour voir la progression du processus d’importation pour le nouveau connecteur.
