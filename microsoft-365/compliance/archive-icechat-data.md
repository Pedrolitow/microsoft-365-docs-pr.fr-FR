---
title: Configurer un connecteur pour archiver les données ICE Chat
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de l’outil ICE Chat dans Microsoft 365. Cela vous permet d’archiver des données provenant de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 79a18017ce7aa3c646fa6c7230bde4b001ddc4c8
ms.sourcegitcommit: 7d4aa58ae9fc893825b6e648fa3f072c3ac59628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "49790168"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>Configurer un connecteur pour archiver les données ICE Chat

Utilisez un connecteur natif dans le Centre de conformité Microsoft 365 pour importer et archiver les données de conversation des services financiers à partir de l’outil de collaboration ICE Chat. Après avoir configuré et configuré un connecteur, il se connecte au site FTP sécurisé (SFTP) ICE Chat (SFTP) de votre organisation une fois par jour, convertit le contenu des messages de conversation au format de message électronique, puis importe ces éléments dans les boîtes aux lettres dans Microsoft 365.

Une fois les données de conversation ICE stockées dans les boîtes aux lettres des utilisateurs, vous pouvez appliquer des fonctionnalités de conformité Microsoft 365 telles que la conservation pour litige, eDiscovery, l’archivage, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données ICE Chat. Par exemple, vous pouvez rechercher des messages ICE Chat à l’aide de la recherche de contenu ou associer la boîte aux lettres qui contient les données ICE Chat à un dépositaire dans un cas Advanced eDiscovery. L’utilisation d’un connecteur de conversation ICE pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-ice-chat-data"></a>Vue d’ensemble de l’archivage des données ICE Chat

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de conversation ICE dans Microsoft 365.

![Flux de travail d’archivage ICE Chat](../media/ICEChatConnectorWorkflow.png)

1. Votre organisation travaille avec ICE Chat pour configurer un site ICE Chat SFTP. Vous allez également travailler avec ICE Chat pour configurer ICE Chat afin de copier les messages de conversation sur votre site ICE Chat SFTP.

2. Une fois toutes les 24 heures, les messages de conversation de ICE Chat sont copiés sur votre site ICE Chat SFTP.

3. Le connecteur de conversation ICE que vous créez dans le Centre de conformité Microsoft 365 se connecte au site ICE Chat SFTP tous les jours et transfère les messages de conversation des 24 heures précédentes vers un emplacement de stockage Azure sécurisé dans microsoft cloud. Le connecteur convertit également le contenu d’une conversation en format de message électronique.

4. Le connecteur importe des éléments de message de conversation dans les boîtes aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **ICE Chat** est créé dans les boîtes aux lettres utilisateur et les éléments de message de conversation sont importés dans ce dossier. Le connecteur utilise la valeur des propriétés *SenderEmail* et *RecipientEmail.* Chaque message de conversation contient ces propriétés, qui sont remplies avec l’adresse e-mail de l’expéditeur et chaque destinataire/participant du message de conversation.

   Outre le mappage automatique des utilisateurs qui utilise les valeurs des *propriétés SenderEmail* et *RecipientEmail* (ce qui signifie que le connecteur importe un message de conversation dans la boîte aux lettres de l’expéditeur et les boîtes aux lettres de chaque destinataire), vous pouvez également définir un mappage utilisateur personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient *l’ID* de conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur de votre organisation. Si vous activez le mappage automatique des utilisateurs et fournissez un fichier de mappage personnalisé, pour chaque élément de conversation, le connecteur examinera d’abord le fichier de mappage personnalisé. S’il ne trouve pas de compte d’utilisateur Microsoft 365 valide correspondant à l’ID de conversation ICE d’un utilisateur, le connecteur utilise les propriétés *SenderEmail* et *RecipientEmail* de l’élément de conversation pour importer l’élément dans les boîtes aux lettres des participants de la conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans les propriétés *SenderEmail* et *RecipientEmail,* l’élément n’est pas importé.

## <a name="before-you-begin"></a>Avant de commencer

Certaines des étapes d’implémentation requises pour archiver les données ICE Chat sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer le connecteur dans le centre de conformité.

- ICE Chat facture à ses clients des frais de conformité externe. Votre organisation doit contacter le groupe ventes ICE Chat pour discuter et signer le contrat de services de données ICE Chat, que vous pouvez obtenir à l’aide de [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf) . Ce contrat est entre ICE Chat et votre organisation et n’implique pas Microsoft. Après avoir installé un site ICE Chat SFTP à l’étape 2, ICE Chat fournit les informations d’identification FTP directement à votre organisation. Ensuite, vous qui fourniriez ces informations d’identification à Microsoft lors de la configuration du connecteur à l’étape 3.

- Vous devez configurer un site ICE Chat SFTP avant de créer le connecteur à l’étape 3. Après avoir travaillé avec ICE Chat pour configurer le site SFTP, les données de ICE Chat sont téléchargées sur le site SFTP tous les jours. Le connecteur que vous créez à l’étape 3 se connecte à ce site SFTP et transfère les données de conversation vers les boîtes aux lettres Microsoft 365. SFTP chiffre également les données ICE Chat envoyées aux boîtes aux lettres pendant le processus de transfert.

- Le connecteur ICE Chat peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments sur le site SFTP, aucun de ces éléments ne sera importé dans Microsoft 365.

- L’administrateur qui crée le connecteur de conversation ICE à l’étape 3 (et qui télécharge les clés publiques et l’adresse IP à l’étape 1) doit se voir attribuer le rôle Importation/Exportation de boîte aux lettres dans Exchange Online. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de** données dans le Centre de conformité Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation dans Exchange Online. Vous pouvez également créer un groupe de rôles, attribuer le rôle Importation/Exportation de boîte aux lettres, puis ajouter les utilisateurs appropriés en tant que membres. Pour plus d’informations, voir les [sections](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups) [Créer](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#create-role-groups) des groupes de rôles ou Modifier des groupes de rôles dans l’article « Gérer les groupes de rôles dans Exchange Online ».

## <a name="step-1-obtain-ssh-and-pgp-public-keys"></a>Étape 1 : Obtenir des clés publiques SSH et PGP

La première étape consiste à obtenir une copie des clés publiques pour Le Shell sécurisé (SSH) et PGP (Pretty Good Privacy). Vous utilisez ces clés à l’étape 2 pour configurer le site ICE Chat SFTP afin d’autoriser le connecteur (que vous créez à l’étape 3) à se connecter au site SFTP et à transférer les données ICE Chat vers les boîtes aux lettres Microsoft 365. Vous obtenez également une adresse IP à cette étape, que vous utiliserez lors de la configuration du site SFTP ICE Chat.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **ICE Chat,** cliquez sur **Afficher.**

3. Dans la page **CONVERSATION ICE,** cliquez sur **Ajouter un connecteur.**

4. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

5. Dans la page Ajouter des informations d’identification pour le **site SFTP ICE Chat** sous l’étape 1, cliquez sur la clé Télécharger **SSH**, télécharger la clé **PGP** et télécharger les liens d’adresse **IP** pour enregistrer une copie de chaque fichier sur votre ordinateur local. Ces fichiers contiennent les éléments suivants qui sont utilisés pour configurer le site SFTP ICE Chat à l’étape 2 :

   - Clé publique SSH : cette clé est utilisée pour configurer le SSH sécurisé afin d’activer une connexion à distance sécurisée lorsque le connecteur se connecte au site SFTP ICE Chat.

   - Clé publique PGP : cette clé est utilisée pour configurer le chiffrement des données transférées du site SFTP ICE Chat vers Microsoft 365.

   - Adresse IP : le site ICE Chat SFTP est configuré pour accepter une demande de connexion uniquement à partir de cette adresse IP, qui est utilisée par le connecteur ICE Chat que vous créez à l’étape 3.

6. Cliquez **sur Annuler** pour fermer l’Assistant. Vous revenir à cet Assistant à l’étape 3 pour créer le connecteur.

## <a name="step-2-configure-the-ice-chat-sftp-site"></a>Étape 2 : Configurer le site ICE Chat SFTP

L’étape suivante consiste à utiliser les clés publiques SSH et PGP et l’adresse IP obtenue à l’étape 1 pour configurer l’authentification SSH et le chiffrement PGP pour le site ICE Chat SFTP. Cela permet au connecteur ICE Chat que vous créez à l’étape 3 de se connecter au site ICE Chat SFTP et de transférer les données ICE Chat à Microsoft 365. Vous devez travailler avec le support technique ICE Chat pour configurer votre site ICE Chat SFTP.

## <a name="step-3-create-an-ice-chat-connector"></a>Étape 3 : Créer un connecteur de conversation ICE

La dernière étape consiste à créer un connecteur ICE Chat dans le Centre de conformité Microsoft 365. Le connecteur utilise les informations que vous fournissez pour vous connecter au site ICE Chat SFTP et transférer des messages de conversation vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and click **Data connectors** in the left nav.

2. Dans la page **Connecteurs de données** sous **ICE Chat,** cliquez sur **Afficher.**

3. Dans la page **CONVERSATION ICE,** cliquez sur **Ajouter un connecteur.**

4. Dans la page **Conditions d’utilisation,** cliquez sur **Accepter.**

5. Dans la page Ajouter des informations d’identification pour le **site ICE Chat SFTP,** sous l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur Valider **la connexion.**

   - **Code d’entreprise :** ID de votre organisation, qui est utilisé comme nom d’utilisateur pour le site ICE Chat SFTP.

   - **Mot de passe :** Mot de passe de votre site ICE Chat SFTP.

   - **URL SFTP :** URL du site ICE Chat SFTP (par exemple, sftp.theice.com).

   - **Port SFTP :** Numéro de port du site ICE Chat SFTP. Le connecteur utilise ce port pour se connecter au site SFTP.

6. Une fois la connexion validée, cliquez sur **Suivant.**

7. Dans la page Mapage des utilisateurs externes aux utilisateurs **de Microsoft 365,** activez le mappage automatique des utilisateurs et fournissez un mappage utilisateur personnalisé selon les besoins. Vous pouvez télécharger une copie du fichier CSV de mappage utilisateur sur cette page. Vous pouvez ajouter les mappages utilisateur au fichier, puis le télécharger.

   > [!NOTE]
   > Comme indiqué précédemment, le fichier CSV du fichier de mappage personnalisé contient l’ID de conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage utilisateur automatique et fournissez un mappage personnalisé, pour chaque élément de conversation, le connecteur examinera d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond à l’identit de conversation ICE d’un utilisateur, le connecteur importe l’élément dans les boîtes aux lettres des utilisateurs spécifiés dans les propriétés *SenderEmail* et *RecipientEmail* de l’élément de conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide par mappage utilisateur automatique ou personnalisé, l’élément n’est pas importé.

8. Cliquez **sur** Suivant, examinez vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

9. Go to the **Data connectors** page to see the progress of the import process for the new connector.
