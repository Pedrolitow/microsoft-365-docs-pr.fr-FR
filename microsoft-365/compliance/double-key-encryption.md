---
title: Chiffrement à double clé (DKE)
description: DKE vous permet de protéger les données hautement sensibles tout en conservant le contrôle total de votre clé.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 631df77a6f10c15dafcb78e58a715a029d32bb73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627544"
---
# <a name="double-key-encryption"></a>Chiffrement à double clé

> *S’applique à : Microsoft Purview Double Key Encryption, [Microsoft Purview](https://www.microsoft.com/microsoft-365/business/compliance-management), [Azure Information Protection](https://azure.microsoft.com/pricing/)*
>
> *Instructions pour : [Azure Information Protection client d’étiquetage unifié pour Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> *Description du service pour : [Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Double Key Encryption (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure, et vous détenez l’autre clé. Vous conservez le contrôle total de l’une de vos clés à l’aide du service de chiffrement à double clé. Vous appliquez une protection à l’aide d’Azure Information Protection client d’étiquetage unifié à votre contenu hautement sensible.

Double Key Encryption prend en charge les déploiements cloud et locaux. Ces déploiements permettent de garantir que les données chiffrées restent opaques partout où vous stockez les données protégées.

Pour plus d’informations sur les clés racine de locataire basées sur le cloud par défaut, consultez [Planification et implémentation de votre clé de locataire Azure Information Protection](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Quand votre organisation doit adopter DKE

Double Key Encryption est destiné à vos données les plus sensibles qui sont soumises aux exigences de protection les plus strictes. DKE n’est pas destiné à toutes les données. En général, vous allez utiliser le chiffrement à double clé pour protéger uniquement une petite partie de vos données globales. Vous devez faire preuve de diligence raisonnable pour identifier les données appropriées à couvrir avec cette solution avant de déployer. Dans certains cas, vous devrez peut-être limiter votre étendue et utiliser d’autres solutions pour la plupart de vos données, telles que Protection des données Microsoft Purview avec des clés gérées par Microsoft ou BYOK. Ces solutions sont suffisantes pour les documents qui ne sont pas soumis à des protections améliorées et à des exigences réglementaires. En outre, ces solutions vous permettent d’utiliser les services de Office 365 les plus puissants , des services que vous ne pouvez pas utiliser avec du contenu chiffré DKE. Par exemple :

- Règles de transport, notamment anti-programme malveillant et courrier indésirable qui nécessitent une visibilité sur la pièce jointe
- Microsoft Delve
- eDiscovery
- Recherche et indexation de contenu
- Office Web Apps y compris la fonctionnalité de co-création

Toutes les applications ou services externes qui ne sont pas intégrés à DKE via le SDK Protection des données Microsoft (MIP) ne peuvent pas effectuer d’actions sur les données chiffrées.

Le SDK Protection des données Microsoft 1.7+ prend en charge le chiffrement à double clé. Les applications qui s’intègrent à notre Kit de développement logiciel (SDK) peuvent raisonner ces données avec des autorisations et intégrations suffisantes en place.

Utilisez Protection des données Microsoft Purview fonctionnalités (classification et étiquetage) pour protéger la plupart de vos données sensibles et utiliser uniquement DKE pour vos données stratégiques. Double Key Encryption s’applique aux données sensibles dans des secteurs hautement réglementés tels que les services financiers et les soins de santé.

Si vos organisations ont l’une des exigences suivantes, vous pouvez utiliser DKE pour sécuriser votre contenu :

- Vous souhaitez vous assurer que *seul vous* pouvez déchiffrer le contenu protégé, en toutes circonstances.
- Vous ne souhaitez pas que Microsoft ait accès aux données protégées par elle-même.
- Vous avez des exigences réglementaires pour conserver les clés dans une limite géographique. Toutes les clés que vous conservez pour le chiffrement et le déchiffrement des données sont conservées dans votre centre de données.

## <a name="system-and-licensing-requirements-for-dke"></a>Configuration système et licence requise pour DKE

**Double Key Encryption** est fourni avec Microsoft 365 E5. Si vous n’avez pas de licence Microsoft 365 E5, vous pouvez vous inscrire pour une [version d’évaluation](https://aka.ms/M365E5ComplianceTrial). Pour plus d’informations sur ces licences, consultez les [conseils de licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. DKE fonctionne avec des étiquettes de confidentialité et nécessite Azure Information Protection.

Les étiquettes de confidentialité DKE sont mises à la disposition des utilisateurs finaux par le biais du bouton de confidentialité dans le client DIP Unified Labeling dans Office Desktop Apps. Installez ces prérequis sur chaque ordinateur client sur lequel vous souhaitez protéger et consommer des documents protégés.

**Microsoft Office Apps pour entreprise** version 2009 ou ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

**Azure Information Protection client d’étiquetage unifié** versions 2.7.93.0 ou ultérieures. Téléchargez et installez le client d’étiquetage unifié à partir du [centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Environnements pris en charge pour le stockage et l’affichage du contenu protégé par DKE

**Applications prises en charge**. [Applications Microsoft 365 pour les grandes entreprises](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) clients sur Windows, notamment Word, Excel et PowerPoint.

**Prise en charge du contenu en ligne**. Vous pouvez stocker des documents et des fichiers protégés par le chiffrement à double clé en ligne dans Microsoft SharePoint et OneDrive Entreprise. Vous devez étiqueter et protéger des documents et des fichiers avec DKE par les applications prises en charge avant de charger vers ces emplacements. Vous pouvez partager du contenu chiffré par e-mail, mais vous ne pouvez pas afficher les documents et fichiers chiffrés en ligne. Au lieu de cela, vous devez afficher le contenu protégé à l’aide des applications de bureau et des clients pris en charge sur votre ordinateur local.

## <a name="overview-of-deploying-dke"></a>Vue d’ensemble du déploiement de DKE

Vous allez suivre ces étapes générales pour configurer DKE. Une fois que vous avez effectué ces étapes, vos utilisateurs finaux peuvent protéger vos données hautement sensibles avec double chiffrement à clé.

1. Déployez le service DKE comme décrit dans cet article.

2. Créez une étiquette avec chiffrement à double clé. Dans le portail de conformité Microsoft Purview, accédez à **Information Protection** et créez une étiquette avec double chiffrement à clé. Consultez [Restreindre l’accès au contenu à l’aide d’étiquettes de confidentialité pour appliquer le chiffrement](./encryption-sensitivity-labels.md).

3. Utilisez des étiquettes de chiffrement à double clé. Protégez les données en sélectionnant l’étiquette Double Key Encrypted dans le ruban Confidentialité dans Microsoft Office.

Il existe plusieurs façons d’effectuer certaines des étapes de déploiement du chiffrement à double clé. Cet article fournit des instructions détaillées afin que les administrateurs moins expérimentés déploient le service avec succès. Si vous êtes à l’aise, vous pouvez choisir d’utiliser vos propres méthodes.

## <a name="deploy-dke"></a>Déployer DKE

Cet article et la vidéo de déploiement utilisent Azure comme destination de déploiement pour le service DKE. Si vous effectuez un déploiement vers un autre emplacement, vous devez fournir vos propres valeurs.


Vous allez suivre ces étapes générales pour configurer le chiffrement à double clé pour votre organisation.

1. [Installer les prérequis logiciels pour le service DKE](#install-software-prerequisites-for-the-dke-service)
1. [Cloner le référentiel GitHub Double Key Encryption](#clone-the-dke-github-repository)
1. [Modifier les paramètres de l’application](#modify-application-settings)
1. [Générer des clés de test](#generate-test-keys)
1. [Générez le projet.](#build-the-project)
1. [Déployer le service DKE et publier le magasin de clés](#deploy-the-dke-service-and-publish-the-key-store)
1. [Validation du déploiement](#validate-your-deployment)
1. [Inscrire votre magasin de clés](#register-your-key-store)
1. [Créer des étiquettes de confidentialité à l’aide de DKE](#create-sensitivity-labels-using-dke)
1. [Activer DKE dans votre client](#enable-dke-in-your-client)
1. [Migrer des fichiers protégés à partir d’étiquettes HYOK vers des étiquettes DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Lorsque vous avez terminé, vous pouvez chiffrer des documents et des fichiers à l’aide de DKE. Pour plus d’informations, consultez [Appliquer des étiquettes de confidentialité à vos fichiers et e-mail dans Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>Installer les prérequis logiciels pour le service DKE

Installez ces prérequis sur l’ordinateur sur lequel vous souhaitez installer le service DKE.

**Kit de développement logiciel (SDK) .NET Core 3.1**. Téléchargez et installez le Kit de développement logiciel (SDK) à partir de [Télécharger .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. Téléchargez Visual Studio Code à partir de [https://code.visualstudio.com/](https://code.visualstudio.com). Une fois installé, exécutez Visual Studio Code et sélectionnez **Afficher** \> **les extensions**. Installez ces extensions.

- C# pour Visual Studio Code

- Gestionnaire de package NuGet

**Ressources Git**. Téléchargez et installez l’une des options suivantes.

- [Git](https://git-scm.com/downloads)

- [GitHub Desktop](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**Openssl** [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) doit être installé pour [générer des clés de test](#generate-test-keys) après avoir déployé DKE. Assurez-vous de l’appeler correctement à partir du chemin des variables d’environnement. Par exemple, pour plus d’informations, consultez « Ajouter le répertoire d’installation à [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) PATH ».

### <a name="clone-the-dke-github-repository"></a>Cloner le référentiel GitHub DKE

Microsoft fournit les fichiers sources DKE dans un référentiel GitHub. Vous clonez le référentiel pour générer le projet localement pour l’utilisation de votre organisation. Le référentiel GitHub DKE se trouve à l’adresse [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

Les instructions suivantes sont destinées aux utilisateurs git ou Visual Studio Code inexpérimentés :

1. Dans votre navigateur, accédez à : [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. Vers le côté droit de l’écran, sélectionnez **Code**. Votre version de l’interface utilisateur peut afficher un bouton **Cloner ou télécharger** . Ensuite, dans la liste déroulante qui s’affiche, sélectionnez l’icône de copie pour copier l’URL dans votre Presse-papiers.

    Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Clonez le référentiel de service Double Key Encryption à partir de GitHub.](../media/dke-clone.png)

3. Dans Visual Studio Code, sélectionnez **Afficher** \> la **palette de commandes** , puis **Git : Cloner**. Pour accéder à l’option dans la liste, commencez à taper `git: clone` pour filtrer les entrées, puis sélectionnez-la dans la liste déroulante. Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Option GIT:Clone de Visual Studio Code.](../media/dke-vscode-clone.png)

4. Dans la zone de texte, collez l’URL que vous avez copiée à partir de Git et sélectionnez **Cloner à partir de GitHub**.

5. Dans la boîte **de dialogue Sélectionner un dossier** qui s’affiche, recherchez et sélectionnez un emplacement pour stocker le référentiel. À l’invite, sélectionnez **Ouvrir**.

    Le référentiel s’ouvre dans Visual Studio Code et affiche la branche Git actuelle en bas à gauche. Par exemple, la branche doit être **principale**. Par exemple :

   ![Capture d’écran du référentiel DKE dans Visual Studio Code affichant la branche principale.](../media/dke-vscode-main-branch.jpg)

6. Si vous n’êtes pas sur la branche principale, vous devez la sélectionner. Dans Visual Studio Code, sélectionnez la branche et choisissez **la branche principale** dans la liste des branches qui s’affiche.

   > [!IMPORTANT]
   > La sélection de la branche principale garantit que vous disposez des fichiers appropriés pour générer le projet. Si vous ne choisissez pas la branche appropriée, votre déploiement échouera.

Votre référentiel source DKE est maintenant configuré localement. Ensuite, [modifiez les paramètres d’application](#modify-application-settings) pour votre organisation.

### <a name="modify-application-settings"></a>Modifier les paramètres de l’application

Pour déployer le service DKE, vous devez modifier les types de paramètres d’application suivants :

- [Paramètres d’accès aux clés](#key-access-settings)
- [Paramètres de locataire et de clé](#tenant-and-key-settings)

Vous modifiez les paramètres d’application dans le fichier appsettings.json. Ce fichier se trouve dans le référentiel DoubleKeyEncryptionService que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store. Par exemple, dans Visual Studio Code, vous pouvez accéder au fichier comme illustré dans l’image suivante.

![Localisation du fichier appsettings.json pour DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Paramètres d’accès aux clés

Choisissez d’utiliser l’autorisation par e-mail ou par rôle. DKE ne prend en charge qu’une seule de ces méthodes d’authentification à la fois.

- **Autorisation par e-mail**. Permet à votre organisation d’autoriser l’accès aux clés en fonction des adresses e-mail uniquement.

- **Autorisation de rôle**. Permet à votre organisation d’autoriser l’accès aux clés en fonction des groupes Active Directory et exige que le service web puisse interroger le protocole LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>Pour définir les paramètres d’accès aux clés pour DKE à l’aide de l’autorisation par e-mail

1. Ouvrez le fichier **appsettings.json** et recherchez le `AuthorizedEmailAddress` paramètre.

2. Ajoutez l’adresse e-mail ou les adresses que vous souhaitez autoriser. Séparez plusieurs adresses e-mail par des guillemets doubles et des virgules. Par exemple :

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Recherchez le `LDAPPath` paramètre et supprimez le texte `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` entre les guillemets doubles. Laissez les guillemets doubles en place. Lorsque vous avez terminé, le paramètre doit ressembler à ceci.

   ```json
   "LDAPPath": ""
   ```

4. Recherchez le `AuthorizedRoles` paramètre et supprimez la ligne entière.

Cette image montre le fichier **appsettings.json** correctement mis en forme pour l’autorisation par e-mail.

   ![Fichier appsettings.json montrant la méthode d’autorisation par e-mail.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Pour définir des paramètres d’accès clés pour DKE à l’aide de l’autorisation de rôle

1. Ouvrez le fichier **appsettings.json** et recherchez le `AuthorizedRoles` paramètre.

2. Ajoutez les noms de groupe Active Directory que vous souhaitez autoriser. Séparez plusieurs noms de groupes avec des guillemets doubles et des virgules. Par exemple :

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Recherchez le `LDAPPath` paramètre et ajoutez le domaine Active Directory. Par exemple :

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Recherchez le `AuthorizedEmailAddress` paramètre et supprimez la ligne entière.

Cette image montre le fichier **appsettings.json** correctement mis en forme pour l’autorisation de rôle.

   ![fichier appsettings.json montrant la méthode d’autorisation de rôle.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Paramètres de locataire et de clé

Le locataire DKE et les paramètres de clé se trouvent dans le fichier **appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>Pour configurer les paramètres de locataire et de clé pour DKE

1. Ouvrez le fichier **appsettings.json** .

2. Recherchez le paramètre et remplacez-le `ValidIssuers` par `<tenantid>` votre ID de locataire. Vous pouvez localiser votre ID de locataire en accédant à la Portail Azure et en affichant les [propriétés du locataire](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Par exemple :

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Si vous souhaitez activer l’accès B2B externe à votre magasin de clés, vous devez également inclure ces locataires externes dans la liste des émetteurs valides.

Localisez le `JwtAudience`. Remplacez `<yourhostname>` par le nom d’hôte de l’ordinateur sur lequel le service DKE s’exécutera. Par exemple : «https://dkeservice.contoso.com »

  > [!IMPORTANT]
  > La valeur doit `JwtAudience` correspondre *exactement* au nom de votre hôte.  

- `TestKeys:Name`. Entrez un nom pour votre clé. Par exemple : `TestKey1`
- `TestKeys:Id`. Créez un GUID et entrez-le `TestKeys:ID` comme valeur. Par exemple : `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Vous pouvez utiliser un site comme [le générateur de GUID en ligne](https://guidgenerator.com/) pour générer de manière aléatoire un GUID.

Cette image montre le format approprié pour les paramètres de locataire et de clés dans **appsettings.json**. `LDAPPath` est configuré pour l’autorisation de rôle.

![Affiche les paramètres de locataire et de clé corrects pour DKE dans le fichier appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Générer des clés de test

Une fois les paramètres de votre application définis, vous êtes prêt à générer des clés de test publiques et privées.

Pour générer des clés :

1. Dans le menu Démarrer de Windows, exécutez l’invite de commandes OpenSSL.

1. Accédez au dossier dans lequel vous souhaitez enregistrer les clés de test. Les fichiers que vous créez en effectuant les étapes de cette tâche sont stockés dans le même dossier.

1. Générez la nouvelle clé de test.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Générez la clé privée.

   Si vous avez installé OpenSSL version 3 ou ultérieure, exécutez la commande suivante :
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  Sinon, exécutez la commande suivante :
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. Générez la clé publique.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. Dans un éditeur de texte, ouvrez **pubkeyonly.pem**. Copiez tout le contenu du fichier **pubkeyonly.pem** , à l’exception des première et dernière lignes, dans la `PublicPem` section du fichier **appsettings.json** .

1. Dans un éditeur de texte, ouvrez **privkeynopass.pem**. Copiez tout le contenu du fichier **privkeynopass.pem** , à l’exception des première et dernière lignes, dans la `PrivatePem` section du fichier **appsettings.json** .

1. Supprimez tous les espaces vides et les sauts de ligne dans les sections et `PrivatePem` les `PublicPem` sections.

    > [!IMPORTANT]
    > Lorsque vous copiez ce contenu, ne supprimez aucune des données PEM.

1. Dans Visual Studio Code, accédez au fichier **Startup.cs** . Ce fichier se trouve dans le dépôt DoubleKeyEncryptionService que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store\.

1. Localisez les lignes suivantes :

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

1. Remplacez ces lignes par le texte suivant :

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    Les résultats finaux doivent ressembler à ce qui suit.

    ![fichier startup.cs pour la préversion publique.](../media/dke-startupcs-usetestkeys.png)

Vous êtes maintenant prêt à [générer votre projet DKE](#build-the-project).

### <a name="build-the-project"></a>Générez le projet.

Utilisez les instructions suivantes pour générer le projet DKE localement :

1. Dans Visual Studio Code, dans le référentiel de service DKE, sélectionnez **Afficher** \> la **palette de commandes** , puis tapez **build** à l’invite.

2. Dans la liste, choisissez **Tâches : Exécuter la tâche de génération**.

   Si aucune tâche de génération n’est trouvée, sélectionnez **Configurer la tâche de génération** et créez-en une pour .NET Core comme suit.

   ![Configurer la tâche de génération manquante pour .NET.](../media/dke-configurebuildtask.png)

   1. Choisissez **Créer tasks.json dans le modèle**.

      ![Créez un fichier tasks.json à partir du modèle pour DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. Dans la liste des types de modèles, sélectionnez **.NET Core**.

      ![Sélectionnez le modèle approprié pour DKE.](../media/dke-tasksjsontemplate.png)

   3. Dans la section build, recherchez le chemin d’accès au fichier **customerkeystore.csproj** . Si ce n’est pas le cas, ajoutez la ligne suivante :

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Exécutez à nouveau la build.

3. Vérifiez qu’il n’y a pas d’erreur rouge dans la fenêtre de sortie.

   S’il y a des erreurs rouges, vérifiez la sortie de la console. Vérifiez que vous avez correctement effectué toutes les étapes précédentes et que les versions de build correctes sont présentes.


Votre installation est maintenant terminée. Avant de publier le magasin de clés, dans appsettings.json, pour le paramètre JwtAudience, vérifiez que la valeur du nom d’hôte correspond exactement à votre nom d’hôte App Service. 

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Déployer le service DKE et publier le magasin de clés

Pour les déploiements de production, déployez le service dans un cloud tiers ou [publiez sur un système local](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Vous pouvez préférer d’autres méthodes pour déployer vos clés. Sélectionnez la méthode qui convient le mieux à votre organisation.

Pour les déploiements pilotes, vous pouvez déployer dans Azure et commencer immédiatement.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>Pour créer une instance Azure Web App pour héberger votre déploiement DKE

Pour publier le magasin de clés, vous allez créer une instance Azure App Service pour héberger votre déploiement DKE. Ensuite, vous allez publier vos clés générées sur Azure.

1. Dans votre navigateur, connectez-vous à [Microsoft Portail Azure](https://ms.portal.azure.com) et accédez à **App Services** > **Add**.

2. Sélectionnez votre abonnement et votre groupe de ressources, puis définissez les détails de votre instance.

   - Entrez le nom d’hôte de l’ordinateur sur lequel vous souhaitez installer le service DKE. Assurez-vous qu’il s’agit du même nom que celui défini pour le paramètre JwtAudience dans le fichier [**appsettings.json**](#tenant-and-key-settings) . La valeur que vous fournissez pour le nom est également webAppInstanceName.

   - Pour **Publier**, sélectionnez **du code** et, pour la **pile Runtime**, sélectionnez **.NET Core 3.1**.

   Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Ajoutez votre App Service.](../media/dke-azure-add-app-service.png)

3. En bas de la page, **sélectionnez Vérifier + créer**, puis **Ajouter**.

4. Effectuez l’une des opérations suivantes pour publier vos clés générées :

   - [Publier via ZipDeployUI](#publish-via-zipdeployui)
   - [Publier via FTP](#publish-via-ftp)
   - [Publier via Visual Studio 2019 ou version ultérieure](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publier via ZipDeployUI

1. Accédez à `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   Par exemple : `https://dkeservice.contoso.scm.azurewebsites.net/ZipDeployUI`

2. Dans la base de code du magasin de clés, accédez au dossier **customer-key-store\src\customer-key-store** et vérifiez que ce dossier contient le fichier **customerkeystore.csproj** .

3. Exécution : **dotnet publish**

   La fenêtre de sortie affiche le répertoire dans lequel la publication a été déployée.

   Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Envoyez tous les fichiers du répertoire de publication à un fichier .zip. Lors de la création du fichier .zip, assurez-vous que tous les fichiers du répertoire se trouvent au niveau racine du fichier .zip.

5. Faites glisser et déposez le fichier .zip que vous créez sur le site ZipDeployUI que vous avez ouvert ci-dessus. Par exemple : `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

DKE est déployé et vous pouvez accéder aux clés de test que vous avez créées. Continuez à [valider votre déploiement](#validate-your-deployment) ci-dessous.

#### <a name="publish-via-ftp"></a>Publier via FTP

1. Connectez-vous au App Service que vous avez créé [ci-dessus](#deploy-the-dke-service-and-publish-the-key-store).

   Dans votre navigateur, accédez à : **Portail Azure** >  **App Service** >  **Deployment Center** > **Manual Deployment** > **FTP** > **Dashboard**.

2. Copiez les chaînes de connexion affichées dans un fichier local. Vous allez utiliser ces chaînes pour vous connecter au App Service web et charger des fichiers via FTP.

   Par exemple :

   ![Copiez les chaînes de connexion à partir du tableau de bord FTP.](../media/dke-ftp-dashboard.png)

3. Dans la base de code du stockage de clés, accédez au **répertoire customer-key-store\src\customer-key-store**.

4. Vérifiez que ce répertoire contient le fichier **customerkeystore.csproj** .

5. Exécution : **dotnet publish**

   La sortie contient le répertoire dans lequel la publication a été déployée.

   Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Envoyez tous les fichiers du répertoire de publication à un fichier zip. Lors de la création du fichier .zip, assurez-vous que tous les fichiers du répertoire se trouvent au niveau racine du fichier .zip.

7. À partir de votre client FTP, utilisez les informations de connexion que vous avez copiées pour vous connecter à votre App Service. Chargez le fichier .zip que vous avez créé à l’étape précédente dans le répertoire racine de votre application web.

DKE est déployé et vous pouvez accéder aux clés de test que vous avez créées. Ensuite, [validez votre déploiement](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Validation du déploiement

Après avoir déployé DKE à l’aide de l’une des méthodes décrites ci-dessus, validez le déploiement et les paramètres du magasin de clés.

Courir:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Par exemple :

```powershell
key_store_tester.ps1 https://dkeservice.contoso.com/TestKey1
```

Vérifiez qu’aucune erreur n’apparaît dans la sortie. Lorsque vous êtes prêt, [inscrivez votre magasin de clés](#register-your-key-store).

Le nom de la clé respecte la casse. Entrez le nom de clé tel qu’il apparaît dans le fichier appsettings.json.

## <a name="register-your-key-store"></a>Inscrire votre magasin de clés

Les étapes suivantes vous permettent d’inscrire votre service DKE. L’inscription de votre service DKE est la dernière étape du déploiement de DKE avant de commencer à créer des étiquettes.

Pour inscrire le service DKE :

1. Dans votre navigateur, ouvrez microsoft [Portail Azure](https://ms.portal.azure.com/) et accédez à **Toutes les** **inscriptions d’applications** **d’identité** \> des services\>.

2. Sélectionnez **Nouvelle inscription**, puis entrez un nom explicite.

3. Sélectionnez un type de compte dans les options affichées.

    Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Nouvelle inscription d’application.](../media/dke-app-registration.png)

4. En bas de la page, **sélectionnez Inscrire** pour créer l’inscription d’application.

5. Dans votre nouvelle inscription d’application, dans le volet gauche, sous **Gérer**, sélectionnez **Authentification**.

6. Sélectionnez **Ajouter une plateforme**.

7. Dans la fenêtre contextuelle **Configurer les plateformes** , sélectionnez **Web**.

8. Sous **URI de redirection**, entrez l’URI de votre service de chiffrement à double clé. Entrez l’URL App Service, y compris le nom d’hôte et le domaine.

   Par exemple : `https://mydkeservicetest.com`

   - L’URL que vous entrez doit correspondre au nom d’hôte où votre service DKE est déployé.
   - Le domaine doit être un [domaine vérifié](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
    - Dans tous les cas, le schéma doit être **https**.

   Vérifiez que le nom d’hôte correspond exactement à votre nom d’hôte App Service.

9. Sous **Octroi implicite**, cochez la case **jetons d’ID** .

10. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

11. Dans le volet gauche, sélectionnez **Exposer une API**, en regard de l’URI d’ID d’application, entrez votre URL App Service, y compris le nom d’hôte et le domaine, puis sélectionnez **Définir**.

12. Toujours dans la page **Exposer une API** , dans les **étendues définies par cette zone d’API** , sélectionnez **Ajouter une étendue**. Dans la nouvelle étendue :

    1. Définissez le nom de l’étendue comme **user_impersonation**.

    2. Sélectionnez les administrateurs et les utilisateurs qui peuvent donner leur consentement.

    3. Définissez les valeurs restantes requises.

    4. Sélectionnez **Ajouter une étendue**.

    5. Sélectionnez **Enregistrer** en haut pour enregistrer vos modifications.

13. Toujours dans la page **Exposer une API** , dans la zone **Applications clientes autorisées** , sélectionnez **Ajouter une application cliente**.

    Dans la nouvelle application cliente :

    1. Définissez l’ID client en tant que `d3590ed6-52b3-4102-aeff-aad2292ab01c`. Cette valeur est l’ID client Microsoft Office et permet à Office d’obtenir un jeton d’accès pour votre magasin de clés.

    2. Sous **Étendues autorisées**, sélectionnez **l’étendue user_impersonation** .

    3. Sélectionnez **Ajouter une application**.

    4. Sélectionnez **Enregistrer** en haut pour enregistrer vos modifications.

    5. Répétez ces étapes, mais cette fois, définissez l’ID client comme `c00e9d32-3c8d-4a7d-832b-029040e7db99`. Cette valeur est l’ID client d’étiquetage unifié Azure Information Protection.

Votre service DKE est maintenant inscrit. Continuez en [créant des étiquettes à l’aide de DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Créer des étiquettes de confidentialité à l’aide de DKE

Dans le portail de conformité Microsoft Purview, créez une étiquette de confidentialité et appliquez le chiffrement comme vous le feriez autrement. Sélectionnez **Utiliser le chiffrement à double clé** et entrez l’URL du point de terminaison de votre clé. Vous devez inclure le nom de clé que vous avez fourni dans la section « TestKeys » du fichier appsettings.json dans l’URL.

Par exemple : `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Sélectionnez Utiliser le chiffrement à double clé dans le portail de conformité Microsoft Purview.](../media/dke-use-dke.png)

Toutes les étiquettes DKE que vous ajoutez commencent à apparaître pour les utilisateurs dans les dernières versions de Applications Microsoft 365 pour les grandes entreprises.

> [!NOTE]
> L’actualisation des nouvelles étiquettes peut prendre jusqu’à 24 heures.

### <a name="enable-dke-in-your-client"></a>Activer DKE dans votre client

Si vous êtes un Office Insider, DKE est activé pour vous. Sinon, activez DKE pour votre client en ajoutant les clés de Registre suivantes :

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Migrer des fichiers protégés à partir d’étiquettes HYOK vers des étiquettes DKE

Si vous le souhaitez, une fois que vous avez terminé la configuration de DKE, vous pouvez migrer du contenu que vous avez protégé à l’aide d’étiquettes HYOK vers des étiquettes DKE. Pour migrer, vous allez utiliser le scanneur AIP. Pour commencer à utiliser le scanneur, consultez [Qu’est-ce qu’Azure Information Protection scanneur d’étiquetage unifié ?](/azure/information-protection/deploy-aip-scanner)

Si vous ne migrez pas de contenu, votre contenu protégé par HYOK ne sera pas affecté.

## <a name="other-deployment-options"></a>Autres options de déploiement

Nous sommes conscients que pour certains clients des secteurs hautement réglementés, cette implémentation de référence standard utilisant des clés logicielles peut ne pas être suffisante pour répondre à leurs obligations et besoins de conformité améliorés. Nous nous sommes associés à des fournisseurs tiers de modules de sécurité matériel (HSM) pour prendre en charge les options améliorées de gestion des clés dans le service DKE, notamment :

- [Entrust](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Contactez directement ces fournisseurs pour plus d’informations et de conseils sur leurs solutions HSM DKE sur le marché.
