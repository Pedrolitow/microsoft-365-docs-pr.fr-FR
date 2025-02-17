---
title: Configurer un connecteur pour archiver les données des messages Bloomberg
description: Les administrateurs peuvent configurer un connecteur de données pour importer et archiver des données à partir de l’outil de messagerie de message Bloomberg dans Microsoft 365. Cela vous permet d’archiver des données à partir de sources de données tierces dans Microsoft 365 afin de pouvoir utiliser des fonctionnalités de conformité telles que la conservation légale, la recherche de contenu et les stratégies de rétention pour gérer les données tierces de votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier3
- purview-compliance
- data-connectors
ms.openlocfilehash: bed05cc323e7c5fe2e0ffc9e74f4dd75fcebd218
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68813788"
---
# <a name="set-up-a-connector-to-archive-bloomberg-message-data"></a>Configurer un connecteur pour archiver les données des messages Bloomberg

Utilisez un connecteur de données dans le portail de conformité Microsoft Purview pour importer et archiver les données de messagerie des services financiers à partir de l’outil de collaboration [de message Bloomberg](https://www.bloomberg.com/professional/product/collaboration/). Une fois que vous avez configuré et configuré un connecteur, il se connecte au site FTP sécurisé (SFTP) Bloomberg de votre organisation une fois par jour et importe les éléments de courrier électronique dans les boîtes aux lettres dans Microsoft 365.

Une fois les données des messages Bloomberg stockées dans les boîtes aux lettres utilisateur, vous pouvez appliquer des fonctionnalités Microsoft Purview telles que la conservation pour litige, la recherche de contenu, l’archivage sur place, l’audit, la conformité des communications et les stratégies de rétention Microsoft 365 aux données de message Bloomberg. Par exemple, vous pouvez rechercher des e-mails de message Bloomberg à l’aide de l’outil de recherche de contenu ou associer la boîte aux lettres qui contient les données du message Bloomberg à un consignataire dans un cas eDiscovery (Premium). L’utilisation d’un connecteur Bloomberg Message pour importer et archiver des données dans Microsoft 365 peut aider votre organisation à rester conforme aux stratégies gouvernementales et réglementaires.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="overview-of-archiving-bloomberg-message-data"></a>Vue d’ensemble de l’archivage des données de message Bloomberg

La vue d’ensemble suivante explique le processus d’utilisation d’un connecteur pour archiver les données de message Bloomberg dans Microsoft 365.

![Processus d’importation et d’archivage des messages Bloomberg.](../media/BloombergMessageArchiving.png)

1. Votre organisation travaille avec Bloomberg pour configurer un site Bloomberg SFTP. Vous allez également travailler avec Bloomberg pour configurer Bloomberg Message afin de copier les messages électroniques sur le site Bloomberg SFTP.

2. Une fois toutes les 24 heures, les messages électroniques de Bloomberg Message sont copiés sur le site Bloomberg SFTP.

3. Le connecteur Bloomberg Message que vous créez dans le portail de conformité se connecte au site Bloomberg SFTP tous les jours et transfère les messages électroniques des 24 heures précédentes vers une zone de stockage Azure sécurisée dans le cloud Microsoft.

4. Le connecteur importe les éléments de message électronique dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé BloombergMessage est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés.

   Pour ce faire, le connecteur utilise la valeur de la propriété CorporateEmailAddress. Chaque e-mail contient cette propriété, qui est remplie avec l’adresse e-mail de chaque participant du message électronique. En plus du mappage automatique des utilisateurs à l’aide de la valeur de la propriété *CorporateEmailAddress* , vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Ce fichier de mappage contient un UUID Bloomberg et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur de votre organisation. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément d’e-mail, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond à l’UUID Bloomberg d’un utilisateur, le connecteur utilise la propriété *CorporateEmailAddress* de l’élément de courrier électronique. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou la propriété *CorporateEmailAddress* de l’élément de messagerie, l’élément n’est pas importé.

## <a name="before-you-set-up-a-connector"></a>Avant de configurer un connecteur

Certaines des étapes d’implémentation requises pour archiver les données de message Bloomberg sont externes à Microsoft 365 et doivent être effectuées avant de pouvoir créer le connecteur dans le centre de conformité.

- Pour configurer un connecteur de message Bloomberg, vous devez utiliser des clés et des phrases secrètes de clé pour Pretty Good Privacy (PGP) et Secure Shell (SSH). Ces clés sont utilisées pour configurer le site Bloomberg SFTP et utilisées par le connecteur pour se connecter au site Bloomberg SFTP afin d’importer des données dans Microsoft 365. La clé PGP est utilisée pour configurer le chiffrement des données transférées du site Bloomberg SFTP vers Microsoft 365. La clé SSH est utilisée pour configurer l’interpréteur de commandes sécurisé afin d’activer une connexion à distance sécurisée lorsque le connecteur se connecte au site SFTP Bloomberg.

  Lors de la configuration d’un connecteur, vous avez la possibilité d’utiliser des clés publiques et des phrases secrètes fournies par Microsoft, ou vous pouvez utiliser vos propres clés privées et phrases secrètes. Nous vous recommandons d’utiliser les clés publiques fournies par Microsoft. Toutefois, si votre organisation a déjà configuré un site Bloomberg SFTP à l’aide de clés privées, vous pouvez créer un connecteur à l’aide de ces mêmes clés privées.

- Abonnez-vous à [Bloomberg Anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Cela est nécessaire pour vous permettre de vous connecter à Bloomberg Anywhere pour accéder au site Bloomberg SFTP que vous devez configurer et configurer.

- Configurez un site Bloomberg SFTP (Secure File Transfer Protocol). Après avoir travaillé avec Bloomberg pour configurer le site SFTP, les données de Bloomberg Message sont téléchargées sur le site SFTP tous les jours. Le connecteur que vous créez à l’étape 2 se connecte à ce site SFTP et transfère les données de messagerie vers les boîtes aux lettres Microsoft 365. SFTP chiffre également les données de message Bloomberg envoyées aux boîtes aux lettres pendant le processus de transfert.

  Pour plus d’informations sur Bloomberg SFTP (également appelé *BB-SFTP*) :

  - Consultez le document « Normes de connectivité SFTP » sur [le support Bloomberg](https://www.bloomberg.com/professional/support/documentation/).

  - Contactez le [support technique Bloomberg](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

- Une fois que vous avez travaillé avec Bloomberg pour configurer un site SFTP, Bloomberg vous fournira des informations après avoir répondu à l’e-mail d’implémentation de Bloomberg. Enregistrez une copie des informations suivantes. Vous l’utilisez pour configurer un connecteur à l’étape 3.

  - Code d’entreprise, qui est un ID pour votre organisation et est utilisé pour se connecter au site Bloomberg SFTP.

  - Mot de passe de votre site Bloomberg SFTP

  - URL du site Bloomberg SFTP (par exemple, sftp.bloomberg.com). En outre, Bloomberg peut également fournir une adresse IP correspondante pour le site Bloomberg SFTP, qui peut également être utilisée pour configurer le connecteur.

  - Numéro de port du site Bloomberg SFTP

- Le connecteur Bloomberg Message peut importer un total de 200 000 éléments en une seule journée. S’il y a plus de 200 000 éléments sur le site SFTP, aucun de ces éléments n’est importé dans Microsoft 365.

- L’utilisateur qui crée un connecteur de message Bloomberg à l’étape 3 (et qui télécharge les clés publiques et l’adresse IP à l’étape 1) doit se voir attribuer le rôle de Administration connecteur de données. Ce rôle est requis pour ajouter des connecteurs dans la page **Connecteurs de données** du portail de conformité. Ce rôle est ajouté par défaut à plusieurs groupes de rôles. Pour obtenir la liste de ces groupes de rôles, consultez la section « Rôles dans les portails defender et de conformité » dans [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-defender-and-compliance-portals). Un administrateur de votre organisation peut également créer un groupe de rôles personnalisé, attribuer le rôle de Administration connecteur de données, puis ajouter les utilisateurs appropriés en tant que membres. Pour obtenir des instructions, consultez la section « Créer un groupe de rôles personnalisé » dans [Autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Configurer un connecteur à l’aide de clés publiques

Les étapes de cette section vous montrent comment configurer un connecteur de message Bloomberg à l’aide des clés publiques pour Pretty Good Privacy (PGP) et Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Étape 1 : Obtenir des clés publiques PGP et SSH

La première étape consiste à obtenir une copie des clés publiques PGP et SSH. Vous utilisez ces clés à l’étape 2 pour configurer le site Bloomberg SFTP afin d’autoriser le connecteur (que vous créez à l’étape 3) à se connecter au site SFTP et à transférer les données d’e-mail du message Bloomberg vers les boîtes aux lettres Microsoft 365. Vous obtenez également une adresse IP dans cette étape, que vous utilisez lors de la configuration du site Bloomberg SFTP.

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Dans la page **Connecteurs de données** sous **Message Bloomberg**, sélectionnez **Afficher**.

3. Dans la page de description du produit **Bloomberg Message**, sélectionnez **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , sélectionnez **Je souhaite utiliser les clés publiques PGP et SSH fournies par Microsoft**.

   ![Sélectionnez l’option permettant d’utiliser des clés publiques.](../media/BloombergMessagePublicKeysOption.png)

6. À l’étape 1, sélectionnez les liens **Télécharger la clé SSH**, **Télécharger la clé PGP** et **Télécharger l’adresse IP** pour enregistrer une copie de chaque fichier sur votre ordinateur local.

   ![Liens pour télécharger les clés publiques et l’adresse IP.](../media/BloombergMessagePublicKeyDownloadLinks.png)

   Ces fichiers contiennent les éléments suivants utilisés pour configurer le site Bloomberg SFTP à l’étape 2 :

   - Clé publique PGP : cette clé est utilisée pour configurer le chiffrement des données transférées du site SFTP Bloomberg vers Microsoft 365.

   - Clé publique SSH : cette clé est utilisée pour configurer l’interpréteur de commandes sécurisé afin d’activer une connexion à distance sécurisée lorsque le connecteur se connecte au site Bloomberg SFTP.

   - Adresse IP : le site Bloomberg SFTP est configuré pour accepter les demandes de connexion à partir de cette adresse IP. La même adresse IP est utilisée par le connecteur Bloomberg Message pour se connecter au site SFTP et transférer les données du message Bloomberg vers Microsoft 365.

7. Sélectionnez **Annuler** pour fermer l’Assistant. Vous revenez à cet Assistant à l’étape 3 pour créer le connecteur.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>Étape 2 : Configurer le site SFTP Bloomberg

> [!NOTE]
> Si votre organisation a précédemment configuré un site SFTP Bloomberg pour archiver les données Instant Bloomberg à l’aide de clés PGP et SSH publiques, vous n’avez pas besoin d’en configurer un autre. Vous pouvez spécifier le même site SFTP lorsque vous créez le connecteur à l’étape 3.

L’étape suivante consiste à utiliser les clés publiques PGP et SSH et l’adresse IP que vous avez obtenue à l’étape 1 pour configurer le chiffrement PGP et l’authentification SSH pour le site Bloomberg SFTP. Cela permet au connecteur Bloomberg Message que vous créez à l’étape 3 de se connecter au site Bloomberg SFTP et de transférer les données du message Bloomberg vers Microsoft 365. Vous devez travailler avec le support technique Bloomberg pour configurer votre site Bloomberg SFTP. Contactez le [support technique bloomberg](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) pour obtenir de l’aide.

> [!IMPORTANT]
> Bloomberg vous recommande de joindre les trois fichiers que vous avez téléchargés à l’étape 1 à un e-mail et de les envoyer à l’équipe de support client quand vous travaillez avec eux pour configurer votre site Bloomberg SFTP.

### <a name="step-3-create-a-bloomberg-message-connector"></a>Étape 3 : Créer un connecteur de message Bloomberg

La dernière étape consiste à créer un connecteur de message Bloomberg dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour vous connecter au site Bloomberg SFTP et transférer des messages électroniques vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365.

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Dans la page **Connecteurs de données** sous **Message Bloomberg**, sélectionnez **Afficher**.

3. Dans la page de description du produit **Bloomberg Message**, sélectionnez **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , sélectionnez **Je souhaite utiliser les clés publiques PGP et SSH fournies par Microsoft**.

6. Sous Étape 3, entrez les informations requises dans les zones suivantes, puis sélectionnez **Valider la connexion**.

      - **Nom:** Nom du connecteur. Il doit être unique dans votre organisation.

      - **Code de l’entreprise :** ID de votre organisation utilisé comme nom d’utilisateur pour le site SFTP Bloomberg.

      - **Mot de passe:** Mot de passe du site Bloomberg SFTP de votre organisation.

      - **URL SFTP :** URL du site Bloomberg SFTP (par exemple, `sftp.bloomberg.com`). Vous pouvez également utiliser une adresse IP pour cette valeur.

      - **Port SFTP :** Numéro de port du site SFTP Bloomberg. Le connecteur utilise ce port pour se connecter au site SFTP.

7. Une fois la connexion validée, sélectionnez **Suivant**.

8. Dans la page **Définir l’utilisateur** , spécifiez les utilisateurs pour qui importer des données.

     - **Tous les utilisateurs de votre organisation**. Sélectionnez cette option pour importer des données pour tous les utilisateurs.

     - **Seuls les utilisateurs en attente d’un litige**. Sélectionnez cette option pour importer des données uniquement pour les utilisateurs dont les boîtes aux lettres sont placées en attente pour litige. Cette option importe les données dans les boîtes aux lettres utilisateur dont la propriété LitigationHoldEnabled a la valeur True. Pour plus d’informations, consultez [Créer une conservation pour litige](create-a-litigation-hold.md).

9. Dans la page **Mapper les utilisateurs du message Bloomberg aux utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs et fournissez un mappage d’utilisateurs personnalisé en fonction des besoins.

   > [!NOTE]
   > Le connecteur importe les éléments de message dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **BloombergMessage** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur utilise la valeur de la propriété *CorporateEmailAddress* . Chaque message de conversation contient cette propriété, et la propriété est remplie avec l’adresse e-mail de chaque participant du message de conversation. Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *CorporateEmailAddress* , vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Le fichier de mappage doit contenir l’UUID Bloomberg et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de message, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond à l’UUID Bloomberg d’un utilisateur, le connecteur utilise la propriété *CorporateEmailAddress* de l’élément de conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou la propriété *CorporateEmailAddress* de l’élément de message, l’élément n’est pas importé.

10. Sélectionnez **Suivant**, passez en revue vos paramètres, puis sélectionnez **Terminer** pour créer le connecteur.

11. Accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur. Sélectionnez le connecteur pour afficher la page de menu volant, qui contient des informations sur le connecteur.

## <a name="set-up-a-connector-using-private-keys"></a>Configurer un connecteur à l’aide de clés privées

Les étapes décrites dans cette section vous montrent comment configurer un connecteur De message Bloomberg à l’aide de clés privées PGP et SSH. Cette option de configuration de connecteur est destinée aux organisations qui ont déjà configuré un site Bloomberg SFTP à l’aide de clés privées.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>Étape 1 : Obtenir une adresse IP pour configurer le site Bloomberg SFTP

> [!NOTE]
> Si votre organisation a déjà configuré un site SFTP Bloomberg pour archiver des données Bloomberg instantanées à l’aide de clés privées PGP et SSH, vous n’avez pas besoin d’en configurer une autre. Vous pouvez spécifier le même site SFTP lorsque vous créez le connecteur à l’étape 2.

Si votre organisation a utilisé des clés privées PGP et SSH pour configurer un site Bloomberg SFTP, vous devez obtenir une adresse IP et la fournir au support client Bloomberg. Le site Bloomberg SFTP doit être configuré pour accepter les demandes de connexion à partir de cette adresse IP. La même adresse IP est utilisée par le connecteur Bloomberg Message pour se connecter au site SFTP et transférer les données du message Bloomberg vers Microsoft 365.

Pour obtenir l’adresse IP :

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Dans la page **Connecteurs de données** sous **Message Bloomberg**, sélectionnez **Afficher**.

3. Dans la page de description du produit **Bloomberg Message**, sélectionnez **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , sélectionnez **Je veux utiliser des clés privées PGP et SSH**.

6. À l’étape 1, sélectionnez **Télécharger l’adresse IP** pour enregistrer une copie du fichier d’adresse IP sur votre ordinateur local.

   ![Téléchargez l’adresse IP.](../media/BloombergMessageConnectorIPAddress.png)

7. Sélectionnez **Annuler** pour fermer l’Assistant. Vous revenez à cet Assistant à l’étape 2 pour créer le connecteur.

Vous devez travailler avec le support technique Bloomberg pour configurer votre site Bloomberg SFTP afin qu’il accepte les demandes de connexion à partir de cette adresse IP. Contactez le [support technique bloomberg](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) pour obtenir de l’aide.

### <a name="step-2-create-a-bloomberg-message-connector"></a>Étape 2 : Créer un connecteur de message Bloomberg

Une fois votre site Bloomberg SFTP configuré, l’étape suivante consiste à créer un connecteur De message Bloomberg dans le portail de conformité. Le connecteur utilise les informations que vous fournissez pour vous connecter au site Bloomberg SFTP et transférer des messages électroniques vers les boîtes aux lettres utilisateur correspondantes dans Microsoft 365. Pour effectuer cette étape, veillez à disposer de copies des mêmes clés privées et phrases secrètes que celles que vous avez utilisées pour configurer votre site SFTP Bloomberg.

1. Accédez à <https://compliance.microsoft.com> et sélectionnez **Connecteurs de données** dans la navigation de gauche.

2. Dans la page **Connecteurs de données** sous **Message Bloomberg**, sélectionnez **Afficher**.

3. Dans la page de description du produit **Bloomberg Message**, sélectionnez **Ajouter un connecteur**.

4. Dans la page **Conditions d’utilisation du service** , sélectionnez **Accepter**.

5. Dans la page **Ajouter des informations d’identification pour la source de contenu** , sélectionnez **Je veux utiliser des clés privées PGP et SSH**.

   ![Sélectionnez l’option pour utiliser des clés privées.](../media/BloombergMessagePrivateKeysOption.png)

6. Sous Étape 3, entrez les informations requises dans les zones suivantes, puis sélectionnez **Valider la connexion**.

      - **Nom:** Nom du connecteur. Il doit être unique dans votre organisation.

      - **Code de l’entreprise :** ID de votre organisation utilisé comme nom d’utilisateur pour le site SFTP Bloomberg.

      - **Mot de passe:** Mot de passe du site Bloomberg SFTP de votre organisation.

      - **URL SFTP :** URL du site Bloomberg SFTP (par exemple, `sftp.bloomberg.com`). Vous pouvez également utiliser une adresse IP pour cette valeur.

      - **Port SFTP :** Numéro de port du site SFTP Bloomberg. Le connecteur utilise ce port pour se connecter au site SFTP.

      - **Clé privée PGP :** Clé privée PGP pour le site Bloomberg SFTP. Veillez à inclure la valeur de la clé privée entière, y compris les lignes de début et de fin du bloc de clé.

      - **Phrase secrète de clé PGP :** Phrase secrète de la clé privée PGP.

      - **Clé privée SSH :** Clé privée SSH pour le site SFTP Bloomberg. Veillez à inclure la valeur de la clé privée entière, y compris les lignes de début et de fin du bloc de clé.

      - **Phrase secrète de clé SSH :** Phrase secrète pour la clé privée SSH.

7. Une fois la connexion validée, sélectionnez **Suivant**.

8. Dans la page **Définir l’utilisateur** , spécifiez les utilisateurs pour qui importer des données

     - **Tous les utilisateurs de votre organisation**. Sélectionnez cette option pour importer des données pour tous les utilisateurs.

     - **Seuls les utilisateurs en attente d’un litige**. Sélectionnez cette option pour importer des données uniquement pour les utilisateurs dont les boîtes aux lettres sont placées en attente pour litige. Cette option importe les données dans les boîtes aux lettres utilisateur dont la propriété LitigationHoldEnabled a la valeur True. Pour plus d’informations, consultez [Créer une conservation pour litige](create-a-litigation-hold.md).

9. Dans la page **Mapper les utilisateurs du message Bloomberg aux utilisateurs Microsoft 365** , activez le mappage automatique des utilisateurs et fournissez un mappage d’utilisateurs personnalisé en fonction des besoins.

   > [!NOTE]
   > Le connecteur importe les éléments de message dans la boîte aux lettres d’un utilisateur spécifique. Un nouveau dossier nommé **BloombergMessage** est créé dans la boîte aux lettres de l’utilisateur spécifique et les éléments y sont importés. Le connecteur utilise la valeur de la propriété *CorporateEmailAddress* . Chaque message de conversation contient cette propriété, et la propriété est remplie avec l’adresse e-mail de chaque participant du message de conversation. Outre le mappage automatique des utilisateurs à l’aide de la valeur de la propriété *CorporateEmailAddress* , vous pouvez également définir un mappage personnalisé en chargeant un fichier de mappage CSV. Le fichier de mappage doit contenir l’UUID Bloomberg et l’adresse de boîte aux lettres Microsoft 365 correspondante pour chaque utilisateur. Si vous activez le mappage automatique des utilisateurs et fournissez un mappage personnalisé, pour chaque élément de message, le connecteur examine d’abord le fichier de mappage personnalisé. S’il ne trouve pas d’utilisateur Microsoft 365 valide qui correspond à l’UUID Bloomberg d’un utilisateur, le connecteur utilise la propriété *CorporateEmailAddress* de l’élément de conversation. Si le connecteur ne trouve pas d’utilisateur Microsoft 365 valide dans le fichier de mappage personnalisé ou la propriété *CorporateEmailAddress* de l’élément de message, l’élément n’est pas importé.

10. Sélectionnez **Suivant**, passez en revue vos paramètres, puis sélectionnez **Terminer** pour créer le connecteur.

11. Accédez à la page **Connecteurs de données** pour voir la progression du processus d’importation du nouveau connecteur. Sélectionnez le connecteur pour afficher la page de menu volant, qui contient des informations sur le connecteur.

## <a name="known-issues"></a>Problèmes connus

- Le thread d’e-mail de message Bloomberg importé dans Microsoft 365 n’est pas pris en charge. Les messages individuels envoyés à une personne sont importés, mais ils ne sont pas présentés dans une conversation à threads. Microsoft travaille à la prise en charge du thread dans les versions ultérieures du connecteur de données de message Bloomberg.
