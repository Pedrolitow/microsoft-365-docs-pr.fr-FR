---
title: Chiffrement à double clé (DKE)
description: DKE vous permet de protéger les données hautement sensibles tout en conservant un contrôle total de votre clé.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 01/29/2021
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 813658fa7b67a45643531febb5a7591f688a8e3a
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61372923"
---
# <a name="double-key-encryption-for-microsoft-365"></a>Chiffrement à double clé pour Microsoft 365

> *S’applique à : Chiffrement à double clé pour Microsoft 365, [Microsoft 365 conformité,](https://www.microsoft.com/microsoft-365/business/compliance-management) [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Instructions pour : Client [d’étiquetage unifié Azure Information Protection pour Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


> *Description du service pour : [Microsoft 365 conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Le chiffrement à double clé (DKE) utilise deux clés pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure et vous maintenez l’autre clé. Vous conservez le contrôle total de l’une de vos clés à l’aide du service de chiffrement à double clé. Vous appliquez la protection à votre contenu hautement sensible à l’aide du client d’étiquetage unifié Azure Information Protection.

Le chiffrement à double clé prend en charge les déploiements sur site et dans le cloud. Ces déploiements permettent de s’assurer que les données chiffrées restent opaques partout où vous stockez les données protégées.

Pour plus d’informations sur les clés racines de client basées sur le cloud par défaut, voir Planification et mise en œuvre de votre clé [de client Azure Information Protection.](/azure/information-protection/plan-implement-tenant-key)

## <a name="when-your-organization-should-adopt-dke"></a>Quand votre organisation doit adopter DKE

Le chiffrement à double clé est destiné à vos données les plus sensibles soumises aux exigences de protection les plus strictes. DKE n’est pas destiné à toutes les données. En règle générale, vous utiliserez le chiffrement à double clé pour protéger uniquement une petite partie de vos données globales. Vous devez faire preuve de diligence pour identifier les données à couvrir avec cette solution avant de déployer. Dans certains cas, vous devrez peut-être affiner votre étendue et utiliser d’autres solutions pour la plupart de vos données, telles que Protection des données Microsoft avec des clés gérées par Microsoft ou BYOK. Ces solutions sont suffisantes pour les documents qui ne sont pas soumis à des protections améliorées et à des exigences réglementaires. En outre, ces solutions vous permettent d’utiliser les services Office 365 les plus puissants; les services que vous ne pouvez pas utiliser avec du contenu chiffré DKE. Par exemple :

- Règles de transport, y compris les logiciels anti-programme malveillant et le courrier indésirable qui nécessitent une visibilité dans la pièce jointe
- Microsoft Delve
- eDiscovery
- Recherche et indexation de contenu
- Office Web Apps, y compris la fonctionnalité de co-auteur

Les applications ou services externes qui ne sont pas intégrés au DKE via le SDK MIP ne pourront pas effectuer d’actions sur les données chiffrées.

Le SDK Protection des données Microsoft 1.7+ prend en charge le chiffrement à double clé ; les applications qui s’intègrent à notre SDK pourront raisonner sur ces données avec des autorisations et des intégrations suffisantes en place.

Nous recommandons aux organisations d’utiliser les fonctionnalités de protection des informations Microsoft (classification et étiquetage) pour protéger la plupart de leurs données sensibles et utiliser uniquement DKE pour leurs données critiques. Le chiffrement à double clé est pertinent pour les données sensibles dans les secteurs hautement réglementés tels que les services financiers et la santé.

Si vos organisations ont l’une des exigences suivantes, vous pouvez utiliser DKE pour sécuriser votre contenu :

- Vous souhaitez vous assurer *que seul vous* pouvez déchiffrer du contenu protégé, dans toutes les circonstances.
- Vous ne souhaitez pas que Microsoft accède lui-même aux données protégées.
- Vous avez des exigences réglementaires pour contenir des clés à l’intérieur d’une limite géographique. Toutes les clés que vous conservez pour le chiffrement et le déchiffrement des données sont conservées dans votre centre de données.

## <a name="system-and-licensing-requirements-for-dke"></a>Exigences relatives au système et aux licences pour le DKE

**Le chiffrement à double clé Microsoft 365** est livré avec Microsoft 365 E5. Si vous n’avez pas de licence Microsoft 365 E5, vous pouvez vous inscrire à une [version d’essai.](https://aka.ms/M365E5ComplianceTrial) Pour plus d’informations sur ces licences, voir Microsoft 365 [licences pour la sécurité et & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**Azure Information Protection**. DKE fonctionne avec les étiquettes de sensibilité et nécessite Azure Information Protection.

Les étiquettes de sensibilité DKE sont disponibles pour les utilisateurs finaux via le bouton de sensibilité dans le client d’étiquetage unifié AIP dans Office applications de bureau. Installez ces éléments prérequis sur chaque ordinateur client sur lequel vous souhaitez protéger et utiliser des documents protégés.

**Microsoft Office Apps pour** entreprise version 2009 ou ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

**Client d’étiquetage unifié Azure Information Protection** version 2.7.93.0 ou ultérieure. Téléchargez et installez le client d’étiquetage unifié à partir du [Centre de téléchargement Microsoft.](https://www.microsoft.com/download/details.aspx?id=53018)

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Environnements pris en charge pour le stockage et l’affichage de contenu protégé par le DKE

**Applications pris en charge.** [Applications Microsoft 365 pour les grandes entreprises](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) clients sur Windows, notamment Word, Excel et PowerPoint.

**Prise en charge du contenu en ligne.** Vous pouvez stocker des documents et des fichiers protégés par chiffrement à double clé en ligne dans Microsoft SharePoint et OneDrive Entreprise. Vous devez étiqueter et protéger les documents et les fichiers avec DKE par les applications pris en charge avant de les télécharger vers ces emplacements. Vous pouvez partager du contenu chiffré par courrier électronique, mais vous ne pouvez pas afficher les documents et fichiers chiffrés en ligne. Au lieu de cela, vous devez afficher le contenu protégé à l’aide des applications de bureau et des clients pris en charge sur votre ordinateur local.

## <a name="overview-of-deploying-dke"></a>Vue d’ensemble du déploiement du DKE

Vous devez suivre ces étapes générales pour configurer DKE. Une fois ces étapes effectuées, vos utilisateurs finaux peuvent protéger vos données hautement sensibles avec le chiffrement à double clé.

1. Déployez le service DKE comme décrit dans cet article.

2. Créez une étiquette avec le chiffrement à double clé. Accédez à Protection des informations sous <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">le Centre de conformité Microsoft 365</a> et créez une étiquette avec chiffrement à double clé. Voir [Restreindre l’accès au contenu à l’aide d’étiquettes de sensibilité pour appliquer le chiffrement.](./encryption-sensitivity-labels.md)

3. Utilisez des étiquettes de chiffrement à double clé. Protégez les données en sélectionnant l’étiquette Chiffrement à double clé à partir du ruban Niveau de Microsoft Office.

Il existe plusieurs façons d’effectuer certaines des étapes de déploiement du chiffrement à double clé. Cet article fournit des instructions détaillées pour que les administrateurs moins expérimentés déploient correctement le service. Si vous êtes à l’aise avec cette méthode, vous pouvez choisir d’utiliser vos propres méthodes.

## <a name="deploy-dke"></a>Déployer DKE

Cet article et la vidéo de déploiement utilisent Azure comme destination de déploiement pour le service DKE. Si vous déployez vers un autre emplacement, vous devez fournir vos propres valeurs.

Regardez la [vidéo de déploiement](https://youtu.be/vDWfHN_kygg) du chiffrement à double clé pour voir une vue d’ensemble pas à pas des concepts présentés dans cet article. La vidéo prend environ 18 minutes.

Vous devez suivre ces étapes générales pour configurer le chiffrement à double clé pour votre organisation.

1. [Installer les logiciels requis pour le service DKE](#install-software-prerequisites-for-the-dke-service)
1. [Cloner le référentiel de chiffrement GitHub double clé](#clone-the-dke-github-repository)
1. [Modifier les paramètres de l’application](#modify-application-settings)
1. [Générer des clés de test](#generate-test-keys)
1. [Générez le projet.](#build-the-project)
1. [Déployer le service DKE et publier le magasin de clés](#deploy-the-dke-service-and-publish-the-key-store)
1. [Validation du déploiement](#validate-your-deployment)
1. [Inscrire votre magasin de clés](#register-your-key-store)
1. [Créer des étiquettes de niveau de sensibilité à l’aide du DKE](#create-sensitivity-labels-using-dke)
1. [Activer le DKE dans votre client](#enable-dke-in-your-client)
1. [Migrer des fichiers protégés des étiquettes HYOK vers des étiquettes DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Lorsque vous avez terminé, vous pouvez chiffrer des documents et des fichiers à l’aide de la DKE. Pour plus d’informations, voir Appliquer des étiquettes [de niveau de sensibilité](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)à vos fichiers et messages électroniques dans Office .

### <a name="install-software-prerequisites-for-the-dke-service"></a>Installer les logiciels requis pour le service DKE

Installez ces éléments prérequis sur l’ordinateur sur lequel vous souhaitez installer le service DKE.

**SDK .NET Core 3.1**. Téléchargez et installez le SDK à partir [de Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. Téléchargez Visual Studio Code à partir [https://code.visualstudio.com/](https://code.visualstudio.com) de . Une fois installé, exécutez Visual Studio Code et **sélectionnez** \> **Afficher les extensions.** Installez ces extensions.

- C# pour Visual Studio Code

- NuGet Gestionnaire de package

**Ressources Git**. Téléchargez et installez l’une des applications suivantes.

- [Git](https://git-scm.com/downloads)

- [GitHub Bureau](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** [OpenSSL doit être](https://slproweb.com/products/Win32OpenSSL.html) installé pour générer des clés [de test](#generate-test-keys) après avoir déployé DKE. Assurez-vous que vous l’voquer correctement à partir du chemin d’accès de vos variables d’environnement. Par exemple, pour plus d’informations, voir « Ajouter le répertoire d’installation à PATH [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) ».

### <a name="clone-the-dke-github-repository"></a>Cloner le référentiel de GitHub DKE

Microsoft fournit les fichiers sources DKE dans un GitHub de données. Vous clonez le référentiel pour créer le projet localement pour l’utilisation de votre organisation. Le référentiel GitHub DKE se trouve à [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService) l’emplacement .

Les instructions suivantes sont destinées aux utilisateurs git ou Visual Studio Code inexpérimentés :

1. Dans votre navigateur, allez à : [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService) .

2. Vers le côté droit de l’écran, sélectionnez **Code**. Votre version de l’interface utilisateur peut afficher un **bouton Clone ou** télécharger. Ensuite, dans la liste liste qui s’affiche, sélectionnez l’icône copier pour copier l’URL dans votre Presse-papiers.

    Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Clonez le référentiel du service de chiffrement à double clé à partir GitHub.](../media/dke-clone.png)

3. In Visual Studio Code, select **View** \> **Command Palette** and select **Git: Clone**. Pour passer à l’option dans la liste, commencez à taper pour filtrer les entrées, puis sélectionnez-la dans `git: clone` la liste. Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Code’option GIT:Clone.](../media/dke-vscode-clone.png)

4. Dans la zone de texte, collez l’URL que vous avez copiée à partir de Git et sélectionnez **Cloner à partir GitHub**.

5. Dans la **boîte de dialogue** Sélectionner un dossier qui s’affiche, recherchez et sélectionnez un emplacement pour stocker le référentiel. À l’invite, sélectionnez **Ouvrir.**

    Le référentiel s’ouvre Visual Studio Code et affiche la branche Git actuelle en bas à gauche. Par exemple, la branche doit être **principale.** Par exemple :

   ![Capture d’écran du repo DKE Visual Studio Code afficher la branche principale.](../media/dke-vscode-main-branch.jpg)

6. Si vous n’êtes pas sur la branche principale, vous devez la sélectionner. Dans Visual Studio Code, sélectionnez la branche et choisissez **principal** dans la liste des branches qui s’affiche.

   > [!IMPORTANT]
   > La sélection de la branche principale garantit que vous avez les fichiers corrects pour créer le projet. Si vous ne choisissez pas la branche correcte, votre déploiement échouera.

Votre référentiel de source DKE est maintenant installé localement. Ensuite, [modifiez les paramètres d’application](#modify-application-settings) de votre organisation.

### <a name="modify-application-settings"></a>Modifier les paramètres de l’application

Pour déployer le service DKE, vous devez modifier les types de paramètres d’application suivants :

- [Paramètres d’accès aux clés](#key-access-settings)
- [Paramètres de client et de clé](#tenant-and-key-settings)

Vous modifiez les paramètres de l’application dans le fichier appsettings.json. Ce fichier se trouve dans le dépôt DoubleKeyEncryptionService que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store. Par exemple, dans Visual Studio Code, vous pouvez parcourir le fichier comme illustré dans l’image suivante.

![Recherche du fichier appsettings.json pour DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Paramètres d’accès aux clés

Choisissez si vous souhaitez utiliser l’autorisation de messagerie ou de rôle. DKE ne prend en charge qu’une seule de ces méthodes d’authentification à la fois.

- **Autorisation de messagerie** électronique . Permet à votre organisation d’autoriser l’accès aux clés en fonction des adresses de messagerie uniquement.

- **Autorisation de rôle**. Permet à votre organisation d’autoriser l’accès aux clés basées sur des groupes Active Directory et nécessite que le service web puisse interroger LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>Pour définir des paramètres d’accès clés pour DKE à l’aide de l’autorisation de messagerie

1. Ouvrez **le fichier appsettings.json** et recherchez le `AuthorizedEmailAddress` paramètre.

2. Ajoutez l’adresse de messagerie ou les adresses que vous souhaitez autoriser. Séparez les adresses de messagerie par des guillemets et des virgules. Par exemple :

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Recherchez `LDAPPath` le paramètre et supprimez le texte entre `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` guillemets doubles. Laissez les guillemets doubles en place. Lorsque vous avez terminé, le paramètre doit ressembler à ceci.

   ```json
   "LDAPPath": ""
   ```

4. Recherchez `AuthorizedRoles` le paramètre et supprimez la ligne entière.

Cette image montre le **fichier appsettings.json** correctement formaté pour l’autorisation de messagerie.

   ![Fichier appsettings.json montrant la méthode d’autorisation de messagerie.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Pour définir des paramètres d’accès clés pour DKE à l’aide de l’autorisation de rôle

1. Ouvrez **le fichier appsettings.json** et recherchez le `AuthorizedRoles` paramètre.

2. Ajoutez les noms de groupe Active Directory que vous souhaitez autoriser. Séparez les noms de groupes par des guillemets et des virgules. Par exemple :

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Recherchez `LDAPPath` le paramètre et ajoutez le domaine Active Directory. Par exemple :

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Recherchez `AuthorizedEmailAddress` le paramètre et supprimez la ligne entière.

Cette image montre le **fichier appsettings.json** correctement formaté pour l’autorisation de rôle.

   ![Fichier appsettings.json montrant la méthode d’autorisation de rôle.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Paramètres de client et de clé

Les paramètres de clé et de client DKE se trouvent dans le **fichier appsettings.json.**

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>Pour configurer les paramètres de client et de clé pour DKE

1. Ouvrez **le fichier appsettings.json.**

2. Recherchez `ValidIssuers` le paramètre et `<tenantid>` remplacez-le par votre ID de client. Vous pouvez localiser votre ID de client en allant sur le portail Azure et en visualisant les [propriétés du client.](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties) Par exemple :

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Si vous souhaitez activer l’accès B2B externe à votre magasin de clés, vous devez également inclure ces locataires externes dans la liste des émetteurs valides.

Recherchez `JwtAudience` le . Remplacez `<yourhostname>` par le nom d’hôte de l’ordinateur sur lequel le service DKE s’exécutera. Par exemple :

  > [!IMPORTANT]
  > La valeur doit `JwtAudience` correspondre exactement au nom de votre *hôte.* Vous pouvez utiliser **localhost:5001 lors** du débogage. Toutefois, lorsque vous avez terminé le débogage, veillez à mettre à jour cette valeur sur le nom d’hôte du serveur.

- `TestKeys:Name`. Entrez un nom pour votre clé. Par exemple : `TestKey1`
- `TestKeys:Id`. Créez un GUID et entrez-le comme `TestKeys:ID` valeur. Par exemple, `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Vous pouvez utiliser un site tel que [le Générateur de GUID en](https://guidgenerator.com/) ligne pour générer un GUID de manière aléatoire.

Cette image montre le format correct pour les paramètres de client et de clés **dans appsettings.json**. `LDAPPath` est configuré pour l’autorisation de rôle.

![Affiche les paramètres de client et de clé corrects pour DKE dans le fichier appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Générer des clés de test

Une fois que vous avez défini vos paramètres d’application, vous êtes prêt à générer des clés de test publiques et privées.

Pour générer des clés :

1. À partir Windows menu Démarrer, exécutez l’invite de commandes OpenSSL.

2. Modifiez le dossier dans lequel vous souhaitez enregistrer les clés de test. Les fichiers que vous créez en effectuant les étapes de cette tâche sont stockés dans le même dossier.

3. Générez la nouvelle clé de test.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

4. Générer la clé privée.

   Si vous avez installé OpenSSL version 3 ou ultérieure, exécutez la commande suivante :
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  Sinon, exécutez la commande suivante :
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

5. Générer la clé publique.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

6. Dans un éditeur de texte, ouvrez **pubkeyonly.pem**. Copiez tout le contenu du fichier **pubkeyonly.pem,** à l’exception des première et dernière lignes, dans la section du fichier `PublicPem` **appsettings.json.**

7. Dans un éditeur de texte, ouvrez **privkeynopass.pem**. Copiez tout le contenu du fichier **privkeynopass.pem,** à l’exception des première et dernière lignes, dans la section du fichier `PrivatePem` **appsettings.json.**

8. Supprimez tous les espaces vides et les nouvelles lignes dans les `PublicPem` `PrivatePem` sections et les espaces.

    > [!IMPORTANT]
    > Lorsque vous copiez ce contenu, ne supprimez aucune donnée PEM.

9. Dans Visual Studio Code, accédez au **fichier Startup.cs.** Ce fichier se trouve dans le dépôt DoubleKeyEncryptionService que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store\.

10. Recherchez les lignes suivantes :

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

11. Remplacez ces lignes par le texte suivant :

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    Les résultats finaux doivent ressembler à ce qui suit.

    ![fichier startup.cs pour la prévisualisation publique.](../media/dke-startupcs-usetestkeys.png)

Vous êtes maintenant prêt à [créer votre projet DKE.](#build-the-project)

### <a name="build-the-project"></a>Générez le projet.

Utilisez les instructions suivantes pour créer le projet DKE localement :

1. Dans Visual Studio Code, dans le référentiel du service DKE, sélectionnez **Afficher** la palette de commandes, puis \>  tapez **build** à l’invite.

2. Dans la liste, choisissez **Tâches : Exécuter la tâche de build.**

   Si aucune tâche de build n’est trouvée, sélectionnez **Configurer** la tâche de création et créez-en une pour .NET Core comme suit.

   ![Configurez la tâche de build manquante pour .NET.](../media/dke-configurebuildtask.png)

   1. Choose **Create tasks.json from template**.

      ![Créez un fichier tasks.json à partir d’un modèle pour DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. Dans la liste des types de modèles, **sélectionnez .NET Core**.

      ![Sélectionnez le modèle correct pour DKE.](../media/dke-tasksjsontemplate.png)

   3. Dans la section build, recherchez le chemin d’accès au **fichier customerkeystore.csproj.** Si ce n’est pas le cas, ajoutez la ligne suivante :

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Exécutez à nouveau la build.

3. Vérifiez qu’il n’y a aucune erreur rouge dans la fenêtre de sortie.

   En cas d’erreur rouge, vérifiez la sortie de la console. Assurez-vous que toutes les étapes précédentes ont été correctement effectuées et que les versions de build correctes sont présentes.

4. Sélectionnez  \> **Exécuter le débogage démarrer** pour déboguer le processus. Si vous êtes invité à sélectionner un environnement, sélectionnez **.NET Core**.

   Le débogger principal .NET est généralement lancé sur `https://localhost:5001` . Pour afficher votre clé de test, consultez et affichez une barre oblique (/) et le nom `https://localhost:5001` de votre clé. Par exemple :

   ```https
   https://localhost:5001/TestKey1
   ```

   La clé doit s’afficher au format JSON.

Votre configuration est maintenant terminée. Avant de publier le keystore, dans appsettings.json, pour le paramètre JwtAudience, assurez-vous que la valeur du nom d’hôte correspond exactement au nom d’hôte de votre service d’application. Vous l’avez peut-être changé en localhost pour résoudre les problèmes de build.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Déployer le service DKE et publier le magasin de clés

Pour les déploiements de production, déployez le service dans un cloud tiers ou publiez-le sur [un système local.](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1)

Vous pouvez préférer d’autres méthodes pour déployer vos clés. Sélectionnez la méthode qui fonctionne le mieux pour votre organisation.

Pour les déploiements pilotes, vous pouvez déployer dans Azure et commencer immédiatement.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>Pour créer une instance Azure Web App pour héberger votre déploiement DKE

Pour publier le magasin de clés, vous allez créer une instance Azure App Service pour héberger votre déploiement DKE. Ensuite, vous allez publier vos clés générées dans Azure.

1. Dans votre navigateur, connectez-vous au [portail Microsoft Azure,](https://ms.portal.azure.com)puis allez sur Ajouter des **services**  >  **d’application.**

2. Sélectionnez votre abonnement et votre groupe de ressources et définissez les détails de votre instance.

   - Entrez le nom d’hôte de l’ordinateur sur lequel vous souhaitez installer le service DKE. Assurez-vous qu’il s’agit du même nom que celui défini pour le paramètre JwtAudience dans le fichier [**appsettings.json.**](#tenant-and-key-settings) La valeur que vous fournissez pour le nom est également WebAppInstanceName.

   - Pour **publier**, sélectionner **du code** et pour la pile **Runtime**, **sélectionnez .NET Core 3.1**.

   Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Ajoutez votre service d’application.](../media/dke-azure-add-app-service.png)

3. Au bas de la page, sélectionnez **Révision + créer,** puis sélectionnez **Ajouter**.

4. Pour publier vos clés générées, faites l’une des choses suivantes :

   - [Publier via ZipDeployUI](#publish-via-zipdeployui)
   - [Publier via FTP](#publish-via-ftp)
   - [Publier via Visual Studio 2019 ou ultérieure](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publier via ZipDeployUI

1. Accédez à `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   Par exemple : https://dkeservice.scm.azurewebsites.net/ZipDeployUI

2. Dans le codebase du magasin de clés, allez dans le dossier **customer-key-store\src\customer-key-store** et vérifiez que ce dossier contient le fichier **customerkeystore.csproj.**

3. Run: **dotnet publish**

   La fenêtre de sortie affiche le répertoire dans lequel la publication a été déployée.

   Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Envoyez tous les fichiers du répertoire de publication vers un .zip de publication. Lorsque vous créez .zip fichier, assurez-vous que tous les fichiers du répertoire sont au niveau racine du .zip fichier.

5. Faites glisser et déposez .zip fichier que vous créez sur le site ZipDeployUI que vous avez ouvert ci-dessus. Par exemple : https://dkeservice.scm.azurewebsites.net/ZipDeployUI

DKE est déployé et vous pouvez parcourir les clés de test que vous avez créées. Continuez à [valider votre déploiement ci-dessous.](#validate-your-deployment)

#### <a name="publish-via-ftp"></a>Publier via FTP

1. Connecter service d’application que vous avez créé [ci-dessus.](#deploy-the-dke-service-and-publish-the-key-store)

   Dans votre navigateur, go to: **Azure portal**  >  **App Service** Deployment  >  **Center**  >  **Manual Deployment**  >  **FTP**  >  **Dashboard**.

2. Copiez les chaînes de connexion affichées dans un fichier local. Vous utiliserez ces chaînes pour vous connecter au service Web App Et charger des fichiers via FTP.

   Par exemple :

   ![Copiez les chaînes de connexion à partir du tableau de bord FTP.](../media/dke-ftp-dashboard.png)

3. Dans le codebase du stockage de clés, allez dans le répertoire **customer-key-store\src\customer-key-store.**

4. Vérifiez que ce répertoire contient le **fichier customerkeystore.csproj.**

5. Run: **dotnet publish**

   La sortie contient le répertoire dans lequel la publication a été déployée.

   Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Envoyez tous les fichiers du répertoire de publication vers un fichier zip. Lorsque vous créez .zip fichier, assurez-vous que tous les fichiers du répertoire sont au niveau racine du .zip fichier.

7. À partir de votre client FTP, utilisez les informations de connexion que vous avez copiées pour vous connecter à votre service d’application. Télécharger le .zip que vous avez créé à l’étape précédente vers le répertoire racine de votre application Web.

DKE est déployé et vous pouvez naviguer jusqu’aux clés de test que vous avez créées. Ensuite, [validez votre déploiement.](#validate-your-deployment)

### <a name="validate-your-deployment"></a>Validation du déploiement

Après avoir déployé DKE à l’aide de l’une des méthodes décrites ci-dessus, validez le déploiement et les paramètres du magasin de clés.

Exécuter : 

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Par exemple :

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

Assurez-vous qu’aucune erreur n’apparaît dans la sortie. Lorsque vous êtes prêt, inscrivez [votre magasin de clés.](#register-your-key-store)

Le nom de la clé est sensible à la cas. Entrez le nom de la clé tel qu’il apparaît dans le fichier appsettings.json.

## <a name="register-your-key-store"></a>Inscrire votre magasin de clés

Les étapes suivantes vous permettent d’inscrire votre service DKE. L’inscription de votre service DKE est la dernière étape du déploiement du DKE avant de commencer à créer des étiquettes.

Pour inscrire le service DKE :

1. Dans votre navigateur, ouvrez [le portail Microsoft Azure,](https://ms.portal.azure.com/)puis allez à **All Services** \> **Identity** \> **App Registrations**.

2. Sélectionnez **Nouvelle inscription,** puis entrez un nom significatif.

3. Sélectionnez un type de compte dans les options affichées.

   Si vous utilisez Microsoft Azure avec un domaine non personnalisé, tel que **onmicrosoft.com**, sélectionnez Comptes dans cet annuaire d’organisation uniquement **(Microsoft uniquement -** Client unique).

   Par exemple :

   > [!div class="mx-imgBorder"]
   > ![Nouvelle inscription d’application.](../media/dke-app-registration.png)

4. En bas de la page, sélectionnez **Enregistrer** pour créer la nouvelle inscription d’application.

5. Dans votre nouvelle inscription d’application, dans le volet gauche, sous **Gérer**, sélectionnez **Authentification.**

6. Sélectionnez **Ajouter une plateforme.**

7. Dans la **fenêtre popup Configurer les plateformes,** sélectionnez **Web.**

8. Sous **URI de redirection,** entrez l’URI de votre service de chiffrement à double clé. Entrez l’URL du service d’application, y compris le nom d’hôte et le domaine.

   Par exemple : https://mydkeservicetest.com

   - L’URL que vous entrez doit correspondre au nom d’hôte où votre service DKE est déployé.
   - Si vous testez localement avec Visual Studio, utilisez **https://localhost:5001** .
   - Dans tous les cas, le schéma doit être **https**.

   Assurez-vous que le nom d’hôte correspond exactement au nom d’hôte de votre service d’application. Vous l’avez peut-être modifié `localhost` pour résoudre les problèmes de la build. Dans **appsettings.json**, cette valeur est le nom d’hôte que vous avez définie pour `JwtAudience` .

9. Sous **Octroi implicite,** cochez la **case des jetons d’ID.**

10. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

11. Dans le volet gauche, sélectionnez **Exposer une API,** puis en de côté de l’URI ID d’application, sélectionnez **Définir**.

12. Toujours dans la page **Exposer une API,** dans les étendues définies par cette **zone d’API,** **sélectionnez Ajouter une étendue.** Dans la nouvelle étendue :

    1. Définissez le nom de **l’étendue comme user_impersonation**.

    2. Sélectionnez les administrateurs et les utilisateurs qui peuvent donner leur consentement.

    3. Définissez les valeurs restantes requises.

    4. Sélectionnez **Ajouter une étendue**.

    5. Sélectionnez **Enregistrer** en haut pour enregistrer vos modifications.

13. Toujours dans la page **Exposer une API,** dans la zone **Applications clientes** autorisées, **sélectionnez Ajouter une application cliente.**

    Dans la nouvelle application cliente :

    1. Définissez l’ID client comme `d3590ed6-52b3-4102-aeff-aad2292ab01c` . Cette valeur est l Microsoft Office client principal et permet Office obtenir un jeton d’accès pour votre magasin de clés.

    2. Sous **Étendues autorisées,** sélectionnez **l’user_impersonation** étendue.

    3. Sélectionnez **Ajouter une application**.

    4. Sélectionnez **Enregistrer** en haut pour enregistrer vos modifications.

    5. Répétez ces étapes, mais cette fois, définissez l’ID client comme `c00e9d32-3c8d-4a7d-832b-029040e7db99` . Cette valeur est l’ID client d’étiquetage unifié Azure Information Protection.

Votre service DKE est maintenant inscrit. Continuez en [créant des étiquettes à l’aide de DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Créer des étiquettes de niveau de sensibilité à l’aide du DKE

Dans la Centre de conformité Microsoft 365, créez une étiquette de niveau de sensibilité et appliquez le chiffrement comme vous le feriez autrement. Sélectionnez **Utiliser le chiffrement à double** clé et entrez l’URL du point de terminaison de votre clé. Vous devez inclure le nom de clé que vous avez fourni dans la section « TestKeys » du fichier appsettings.json dans l’URL. 

Par exemple : https://testingdke1.azurewebsites.net/ **KEYNAME**


> [!div class="mx-imgBorder"]
> ![Sélectionnez Utiliser le chiffrement à double clé dans la Centre de conformité Microsoft 365.](../media/dke-use-dke.png)

Les étiquettes DKE que vous ajoutez commenceront à apparaître pour les utilisateurs dans les dernières versions de Applications Microsoft 365 pour les grandes entreprises.

> [!NOTE]
> L’actualisation des clients avec les nouvelles étiquettes peut prendre jusqu’à 24 heures.

### <a name="enable-dke-in-your-client"></a>Activer le DKE dans votre client

Si vous êtes un Office Insider, DKE est activé pour vous. Sinon, activez DKE pour votre client en ajoutant les clés de Registre suivantes :

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Migrer des fichiers protégés des étiquettes HYOK vers des étiquettes DKE

Si vous le souhaitez, une fois que vous avez terminé la configuration du DKE, vous pouvez migrer le contenu que vous avez protégé à l’aide d’étiquettes HYOK vers des étiquettes DKE. Pour migrer, vous allez utiliser le scanneur AIP. Pour commencer à utiliser le scanneur, voir [Qu’est-ce](/azure/information-protection/deploy-aip-scanner)que le scanneur d’étiquetage unifié Azure Information Protection ?

Si vous ne migrez pas de contenu, votre contenu protégé HYOK reste inchangé.

## <a name="other-deployment-options"></a>Autres options de déploiement

Nous sommes conscients que pour certains clients dans des secteurs hautement réglementés, cette implémentation de référence standard à l’aide de clés logicielles peut ne pas être suffisante pour répondre à leurs obligations et besoins de conformité renforcées.
Nous avons mis en place un partenariat avec différents fournisseurs de modules de sécurité matérielle (HSM) tiers pour prendre en charge les options de gestion améliorée des clés au service DKE, notamment :

 - [Entrust](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.) 

- [Tsézé](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption) 

Pour plus d’informations et de conseils sur leurs solutions HSM DKE sur le marché, contactez directement ces fournisseurs. 

