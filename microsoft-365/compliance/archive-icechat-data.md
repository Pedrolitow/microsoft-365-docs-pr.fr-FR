---
title: Configurer un connecteur pour archiver les données de conversation ICE
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
description: Les administrateurs peuvent configurer un connecteur pour importer et archiver des données à partir de l’outil ice Chat dans Microsoft 365. Cela vous permet d’archiver les données de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
ms.openlocfilehash: 55af0567fc5cb8dbdeb571209fb7d9f863561900
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001695"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>Configurer un connecteur pour archiver les données de conversation ICE

[!include[Purview banner](../includes/purview-rebrand-banner.md)]C

Utilisez un connecteur natif dans le portail de conformité Microsoft Purview pour importer et archiver les données de conversation des services financiers à partir de l’outil ice Chat Collaboration. Après avoir configuré et configuré un connecteur, il se connecte au site ICE Chat secure FTP (SFTP) de votre organisation une fois par jour, convertit le contenu des messages de conversation au format de message électronique, puis importe ces éléments dans des boîtes aux lettres dans Microsoft 365.

Une fois les données de conversation ICE stockées dans des boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation des litiges, la découverte électronique, l’archivage, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données ice Chat. Par exemple, vous pouvez rechercher des messages ice Chat à l’aide d’une recherche de contenu ou associer la boîte aux lettres qui contient les données ice Chat à un consignateur dans un cas eDiscovery (Premium). L’utilisation d’un connecteur ICE Chat pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

## <a name="overview-of-archiving-ice-chat-data"></a>Vue d’ensemble de l’archivage des données ice Chat

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de conversation ICE dans Microsoft 365.

![Flux de travail d’archivage des conversations ICE.](../media/ICEChatConnectorWorkflow.png)

1. Votre organisation travaille avec ICE Chat pour configurer un site ICE Chat SFTP. Vous travaillerez également avec ICE Chat pour configurer ICE Chat afin de copier les messages de conversation sur votre site ICE Chat SFTP.

2. Une fois toutes les 24 heures, les messages de conversation ice Chat sont copiés sur votre site ICE Chat SFTP.

3. Le connecteur ICE Chat que vous créez dans le portail de conformité se connecte au site ICE Chat SFTP tous les jours et transfère les messages de conversation des 24 dernières heures vers un emplacement stockage Azure sécurisé dans le cloud Microsoft. Le connecteur convertit également le contenu d’un massage de conversation en format de message électronique.

4. Le connecteur importe des éléments de message de conversation dans les boîtes aux lettres d’utilisateurs spécifiques. Un nouveau dossier nommé **ICE Chat** est créé dans les boîtes aux lettres utilisateur et les éléments de message de conversation sont importés dans ce dossier. Le connecteur utilise la valeur des propriétés *SenderEmail* et *RecipientEmail* . Chaque message de conversation contient ces propriétés, qui sont remplies avec l’adresse e-mail de l’expéditeur et de chaque destinataire/participant du message de conversation.

   Outre le mappage automatique des utilisateurs qui utilise les valeurs des propriétés *SenderEmail* et *RecipientEmail* (ce qui signifie que le connecteur importe un message de conversation dans la boîte aux lettres de l’expéditeur et les boîtes aux lettres de chaque destinataire), vous pouvez également définir le mappage utilisateur personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient *l’ID de* conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur de votre organisation. Si vous activez le mappage automatique des utilisateurs et fournissez un fichier de mappage personnalisé, pour chaque élément de conversation, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de compte d’utilisateur Microsoft 365 valide qui correspond à l’ID de conversation ICE d’un utilisateur, le connecteur utilise les propriétés *SenderEmail* et *RecipientEmail* de l’élément de conversation pour importer l’élément dans les boîtes aux lettres des participants à la conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou dans les propriétés *SenderEmail* et *RecipientEmail*, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données ice Chat sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer le connecteur dans le centre de conformité.

- Ice Chat facture à ses clients des frais de conformité externe. Votre organisation doit contacter le groupe de ventes ICE Chat pour discuter et signer le contrat de services de données ICE Chat, que vous pouvez obtenir à l’adresse [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf). Cet accord est conclu entre ICE Chat et votre organisation et n’implique pas Microsoft. Après avoir configuré un site ICE Chat SFTP à l’étape 2, ICE Chat fournit les informations d’identification FTP directement à votre organisation. Ensuite, vous qui fourniriez ces informations d’identification à Microsoft lors de la configuration du connecteur à l’étape 3.

- Vous devez configurer un site ICE Chat SFTP avant de créer le connecteur à l’étape 3. Après avoir travaillé avec ICE Chat pour configurer le site SFTP, les données de ICE Chat sont chargées sur le site SFTP tous les jours. Le connecteur que vous créez à l’étape 3 se connecte à ce site SFTP et transfère les données de conversation aux boîtes aux lettres Microsoft 365. SFTP chiffre également les données ice Chat envoyées aux boîtes aux lettres pendant le processus de transfert.

- Pour configurer un connecteur ICE Chat, vous devez utiliser des clés et des phrases secrètes clés pour la confidentialité pretty good (PGP) et Secure Shell (SSH). Ces clés sont utilisées pour configurer le site ICE Chat SFTP et utilisées par le connecteur pour se connecter au site ICE Chat SFTP afin d’importer des données dans Microsoft 365. La clé PGP est utilisée pour configurer le chiffrement des données transférées du site ICE Chat SFTP vers Microsoft 365. La clé SSH est utilisée pour configurer l’interpréteur de commandes sécurisé afin d’activer une connexion à distance sécurisée lorsque le connecteur se connecte au site ICE Chat SFTP.

  Lors de la configuration d’un connecteur, vous avez la possibilité d’utiliser des clés publiques et des phrases secrètes de clé fournies par Microsoft, ou vous pouvez utiliser vos propres clés privées et phrases secrètes. Nous vous recommandons d’utiliser les clés publiques fournies par Microsoft. Toutefois, si votre organisation a déjà configuré un site ICE Chat SFTP à l’aide de clés privées, vous pouvez créer un connecteur à l’aide de ces mêmes clés privées.

- Le connecteur ICE Chat peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments sur le site SFTP, aucun de ces éléments n’est importé dans Microsoft 365.

- L’administrateur qui crée le connecteur ICE Chat à l’étape 3 (et qui télécharge les clés publiques et l’adresse IP à l’étape 1) doit disposer du rôle Administrateur du connecteur de données. Ce rôle est requis pour ajouter des connecteurs sur la page **Connecteurs de données** dans le portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les centres de sécurité et de conformité » dans [Autorisations dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle Administrateur du connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Configurer un connecteur à l’aide de clés publiques

Les étapes de cette section vous montrent comment configurer un connecteur ICE Chat à l’aide des clés publiques pour Pretty Good Privacy (PGP) et Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Étape 1 : Obtenir des clés publiques PGP et SSH

La première étape consiste à obtenir une copie des clés publiques pour Pretty Good Privacy (PGP) et Secure Shell (SSH). Vous utilisez ces clés à l’étape 2 pour configurer le site ICE Chat SFTP afin d’autoriser le connecteur (que vous créez à l’étape 3) à se connecter au site SFTP et transférer les données ice Chat vers Microsoft 365 boîtes aux lettres. Vous obtenez également une adresse IP dans cette étape, que vous utilisez lors de la configuration du site ICE Chat SFTP.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Dans la page **Connecteurs de données** sous **ICE Chat**, cliquez sur **Affichage**.

3. Dans la page **de conversation ICE** , cliquez sur **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , cliquez sur **Je veux utiliser les clés publiques PGP et SSH fournies par Microsoft**.

   ![Sélectionnez l’option permettant d’utiliser des clés publiques.](../media/ICEChatPublicKeysOption.png)

6. À l’étape 1, cliquez sur la **clé Télécharger SSH**, **téléchargez la clé PGP** et téléchargez les liens d’adresse **IP** pour enregistrer une copie de chaque fichier sur votre ordinateur local.

   ![Liens vers le téléchargement des clés publiques et de l’adresse IP.](../media/ICEChatPublicKeyDownloadLinks.png)

   Ces fichiers contiennent les éléments suivants qui sont utilisés pour configurer le site ICE Chat SFTP à l’étape 2 :

   - Clé publique PGP : cette clé est utilisée pour configurer le chiffrement des données transférées du site ICE Chat SFTP vers Microsoft 365.

   - Clé publique SSH : cette clé est utilisée pour configurer Secure SSH afin d’activer une connexion à distance sécurisée lorsque le connecteur se connecte au site ICE Chat SFTP.

   - Adresse IP : le site ICE Chat SFTP est configuré pour accepter une demande de connexion uniquement à partir de cette adresse IP, qui est utilisée par le connecteur ICE Chat que vous créez à l’étape 3.

7. Cliquez sur **Annuler** pour fermer l’Assistant. Vous revenez à cet Assistant à l’étape 3 pour créer le connecteur.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>Étape 2 : Configurer le site ICE Chat SFTP

L’étape suivante consiste à utiliser les clés publiques PGP et SSH et l’adresse IP que vous avez obtenues à l’étape 1 pour configurer le chiffrement PGP et l’authentification SSH pour le site ICE Chat SFTP. Cela permet au connecteur ICE Chat que vous créez à l’étape 3 de se connecter au site ICE Chat SFTP et de transférer les données ice Chat vers Microsoft 365. Vous devez travailler avec le support client ICE Chat pour configurer votre site ICE Chat SFTP.

### <a name="step-3-create-an-ice-chat-connector"></a>Étape 3 : Créer un connecteur ICE Chat

La dernière étape consiste à créer un connecteur ICE Chat dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour se connecter au site ICE Chat SFTP et transférer des messages de conversation vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez et [https://compliance.microsoft.com](https://compliance.microsoft.com) cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Dans la page **Connecteurs de données** sous **ICE Chat**, cliquez sur **Affichage**.

3. Dans la page **de conversation ICE** , cliquez sur **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , cliquez sur **Je veux utiliser les clés publiques PGP et SSH**.

6. À l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Valider la connexion**.

   - **Code ferme :** ID de votre organisation, qui est utilisé comme nom d’utilisateur pour le site ICE Chat SFTP.

   - **Mot de passe:** Mot de passe de votre site ICE Chat SFTP.

   - **URL SFTP :** URL du site ICE Chat SFTP (par exemple, `sftp.theice.com`). Vous pouvez également utiliser une adresse IP pour cette valeur.

   - **Port SFTP :** Numéro de port pour le site ICE Chat SFTP. Le connecteur utilise ce port pour se connecter au site SFTP.

7. Une fois la connexion validée, cliquez sur **Suivant**.

8. Dans la page **Définir l’utilisateur** , spécifiez les utilisateurs pour lequel importer des données.

     - **Tous les utilisateurs de votre organisation**. Sélectionnez cette option pour importer des données pour tous les utilisateurs.

     - **Seuls les utilisateurs en attente de litige**. Sélectionnez cette option pour importer des données uniquement pour les utilisateurs dont les boîtes aux lettres sont mises en attente pour litige. Cette option importe des données vers des boîtes aux lettres utilisateur dont la propriété LitigationHoldEnabled a la valeur True. Pour plus d’informations, consultez [Créer une conservation de litige](create-a-litigation-hold.md).

9. Dans la page **Mapper des utilisateurs externes à Microsoft 365 page Utilisateurs**, activez le mappage automatique des utilisateurs et fournissez le mappage d’utilisateurs personnalisés en fonction des besoins. Vous pouvez télécharger une copie du fichier CSV de mappage utilisateur sur cette page. Vous pouvez ajouter les mappages utilisateur au fichier, puis le charger.

   > [!NOTE]
   > Comme expliqué précédemment, le fichier CSV du fichier de mappage personnalisé contient l’ID de conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de conversation, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de Microsoft 365 utilisateur valide qui correspond à l’ID de conversation ICE d’un utilisateur, le connecteur importe l’élément dans les boîtes aux lettres pour les utilisateurs spécifiés dans les propriétés *SenderEmail* et *RecipientEmail* de l’élément de conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide par mappage automatique ou personnalisé, l’élément n’est pas importé.

10. Cliquez sur **Suivant**, passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

11. Accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur.

## <a name="set-up-a-connector-using-private-keys"></a>Configurer un connecteur à l’aide de clés privées

Les étapes de cette section vous montrent comment configurer un connecteur ICE Chat à l’aide de clés privées PGP et SSH. Cette option de configuration de connecteur est destinée aux organisations qui ont déjà configuré un site ICE Chat SFTP à l’aide de clés privées.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>Étape 1 : Obtenir une adresse IP pour configurer le site ICE Chat SFTP

Si votre organisation a utilisé des clés privées PGP et SSH pour configurer un site ICE Chat SFTP, vous devez obtenir une adresse IP et la fournir au support client ICE Chat. Le site ICE Chat SFTP doit être configuré pour accepter les demandes de connexion provenant de cette adresse IP. La même adresse IP est utilisée par le connecteur ICE Chat pour se connecter au site SFTP et transférer des données ice Chat vers Microsoft 365.

Pour obtenir l’adresse IP :

1. Accédez et <https://compliance.microsoft.com> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Dans la page **Connecteurs de données** sous **ICE Chat**, cliquez sur **Affichage**.

3. Dans la page de description du produit **ICE Chat** , cliquez sur **Ajouter un connecteur**

4. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , cliquez sur **Je veux utiliser des clés privées PGP et SSH**.

   ![Sélectionnez l’option permettant d’utiliser des clés privées.](../media/ICEChatPrivateKeysOption.png)

6. À l’étape 1, cliquez sur **Télécharger l’adresse IP** pour enregistrer une copie du fichier d’adresse IP sur votre ordinateur local.

   ![Téléchargez l’adresse IP.](../media/ICEChatConnectorIPAddress.png)

7. Cliquez sur **Annuler** pour fermer l’Assistant. Vous revenez à cet Assistant à l’étape 2 pour créer le connecteur.

Vous devez travailler avec le support client ICE Chat pour configurer votre site ICE Chat SFTP afin d’accepter les demandes de connexion à partir de cette adresse IP.

### <a name="step-2-create-an-ice-chat-connector"></a>Étape 2 : Créer un connecteur ICE Chat

Une fois votre site ICE Chat SFTP configuré, l’étape suivante consiste à créer un connecteur ICE Chat dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour se connecter au site ICE Chat SFTP et transférer des messages électroniques vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365. Pour effectuer cette étape, veillez à avoir des copies des mêmes clés privées et phrases secrètes clés que celles que vous avez utilisées pour configurer votre site ICE Chat SFTP.

1. Accédez et <https://compliance.microsoft.com> cliquez sur **Connecteurs de données** dans le volet de navigation gauche.

2. Dans la page **Connecteurs de données** sous **ICE Chat**, cliquez sur **Affichage**.

3. Dans la page de description du produit **ICE Chat** , cliquez sur **Ajouter un connecteur**

4. Dans la page **Conditions d’utilisation** , cliquez sur **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , cliquez sur **Je veux utiliser des clés privées PGP et SSH**.

6. À l’étape 3, entrez les informations requises dans les zones suivantes, puis cliquez sur **Valider la connexion**.

      - **Nom:** Nom du connecteur. Il doit être unique dans votre organisation.

      - **Code ferme :** ID de votre organisation utilisé comme nom d’utilisateur pour le site ICE Chat SFTP.

      - **Mot de passe:** Mot de passe du site ICE Chat SFTP de votre organisation.

      - **URL SFTP :** URL du site ICE Chat SFTP (par exemple, `sftp.theice.com`). Vous pouvez également utiliser une adresse IP pour cette valeur.

      - **Port SFTP :** Numéro de port pour le site ICE Chat SFTP. Le connecteur utilise ce port pour se connecter au site SFTP.

      - **Clé privée PGP :** Clé privée PGP pour le site ICE Chat SFTP. Veillez à inclure la valeur de clé privée entière, y compris les lignes de début et de fin du bloc de clé.

      - **Phrase secrète de clé PGP :** Phrase secrète pour la clé privée PGP.

      - **Clé privée SSH :** Clé privée SSH pour le site ICE Chat SFTP. Veillez à inclure la valeur de clé privée entière, y compris les lignes de début et de fin du bloc de clé.

      - **Phrase secrète de clé SSH :** Phrase secrète pour la clé privée SSH.

7. Une fois la connexion validée, cliquez sur **Suivant**.

8. Dans la page **Définir l’utilisateur** , spécifiez les utilisateurs pour lequel importer des données.

     - **Tous les utilisateurs de votre organisation**. Sélectionnez cette option pour importer des données pour tous les utilisateurs.

     - **Seuls les utilisateurs en attente de litige**. Sélectionnez cette option pour importer des données uniquement pour les utilisateurs dont les boîtes aux lettres sont mises en attente pour litige. Cette option importe des données vers des boîtes aux lettres utilisateur dont la propriété LitigationHoldEnabled a la valeur True. Pour plus d’informations, consultez [Créer une conservation de litige](create-a-litigation-hold.md).

9. Dans la page **Mapper les utilisateurs de conversation ICE pour Microsoft 365 utilisateurs**, activez le mappage automatique des utilisateurs et fournissez un mappage d’utilisateur personnalisé en fonction des besoins.

   > [!NOTE]
   > Comme expliqué précédemment, le fichier CSV du fichier de mappage personnalisé contient l’ID de conversation ICE et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de conversation, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas de Microsoft 365 utilisateur valide qui correspond à l’ID de conversation ICE d’un utilisateur, le connecteur importe l’élément dans les boîtes aux lettres pour les utilisateurs spécifiés dans les propriétés *SenderEmail* et *RecipientEmail* de l’élément de conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide par mappage automatique ou personnalisé, l’élément n’est pas importé.

10. Cliquez sur **Suivant**, passez en revue vos paramètres, puis cliquez sur **Terminer** pour créer le connecteur.

11. Accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur. Cliquez sur le connecteur pour afficher la page de menu volant, qui contient des informations sur le connecteur.
