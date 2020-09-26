---
title: Chiffrement à double clé (DKE)
description: DKE vous permet de protéger les données hautement sensibles tout en conservant le contrôle total de votre clé.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 09/22/2020
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
localization_priority: Normal
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 39d7933014f1dc71f8c94e467954d36ede4fb451
ms.sourcegitcommit: 1423e08a02d30f0a2b993fb99325c3f499c31787
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "48277538"
---
# <a name="double-key-encryption-for-microsoft-365"></a>Chiffrement à double clé pour Microsoft 365

> *S’applique à : chiffrement à double clé pour Microsoft 365, [conformité microsoft 365](https://www.microsoft.com/microsoft-365/business/compliance-management), [Azure information protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Instructions pour : [client d’étiquetage unifié Azure information protection pour Windows](https://docs.microsoft.com/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*
>
> *Description du service : [conformité Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Le chiffrement à clé double (DKE) utilise deux clés ensemble pour accéder au contenu protégé. Microsoft stocke une clé dans Microsoft Azure et vous conservez l’autre clé. Vous conservez le contrôle total de l’une de vos clés à l’aide du service de chiffrement à clé double. Vous appliquez la protection à l’aide du client d’étiquetage unifié Azure information protection à votre contenu hautement sensible.

Le chiffrement à double clé prend en charge les déploiements sur le Cloud et sur site. Ces déploiements permettent de s’assurer que les données chiffrées restent opaques, où que vous stockez les données protégées.

Pour plus d’informations sur les clés de racine de client par défaut, consultez la rubrique [planification et implémentation de votre clé de client Azure information protection](https://docs.microsoft.com/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Quand votre organisation doit adopter DKE

Le chiffrement à double clé est destiné à vos données les plus sensibles, sujettes aux exigences de protection les plus strictes. DKE n’est pas destiné à toutes les données. En règle générale, vous utiliserez le chiffrement à double clé pour ne protéger qu’une très petite partie de vos données globales. Vous devez faire diligence pour identifier les bonnes données à traiter avec cette solution avant de procéder au déploiement. Dans certains cas, vous devrez peut-être affiner votre portée et utiliser d’autres solutions pour la majorité de vos données, telles que la protection des informations Microsoft avec des clés gérées par Microsoft ou BYOK. Ces solutions sont suffisantes pour les documents qui ne sont pas soumis à des protections améliorées et aux exigences réglementaires. De plus, ces solutions vous permettent d’utiliser les services Office 365 les plus puissants ; services que vous ne pouvez pas utiliser avec du contenu chiffré DKE. Par exemple :

- Règles de transport incluant le blocage des programmes malveillants et le courrier indésirable qui nécessitent une visibilité dans la pièce jointe
- Microsoft Delve
- eDiscovery
- Recherche et indexation de contenu
- Office Web Apps, y compris la fonctionnalité de co-création

Les applications ou services externes qui ne sont pas intégrés à DKE via le kit de développement logiciel MIP ne seront pas en mesure d’effectuer des actions sur les données chiffrées.

Le kit de développement logiciel (SDK) Microsoft information protection 1.7 + prend en charge le chiffrement à double clé ; les applications qui s’intègrent à notre kit de développement logiciel (SDK) seront en mesure de le faire sur ces données avec des autorisations et des intégrations suffisantes.

Nous recommandons aux organisations d’utiliser les fonctionnalités de protection des informations Microsoft (classification et étiquetage) pour protéger la plupart de leurs données sensibles et utiliser DKE pour leurs données critiques. Le chiffrement à double clé est particulièrement pertinent pour les données extrêmement sensibles dans les secteurs hautement réglementés, tels que les services financiers et le secteur de la santé.

Si votre organisation dispose de l’une des conditions suivantes, vous pouvez utiliser DKE pour sécuriser votre contenu :

- Vous souhaitez vous assurer que *vous* êtes le seul à pouvoir déchiffrer le contenu protégé, dans toutes les circonstances.
- Vous ne souhaitez pas que Microsoft ait accès aux données protégées de façon autonome.
- Vous avez des exigences réglementaires à maintenir des clés dans une limite géographique. Toutes les clés que vous mettez en attente pour le chiffrement et le déchiffrement des données sont conservées dans votre centre de données.

## <a name="system-and-licensing-requirements-for-dke"></a>Exigences en matière de système et de licence pour DKE

Le **chiffrement à double clé pour microsoft 365** est fourni avec Microsoft 365 E5 et Office 365 E5. Si vous n’avez pas de licence Microsoft 365 E5, vous pouvez vous inscrire pour obtenir une [version d’évaluation](https://aka.ms/M365E5ComplianceTrial). Pour plus d’informations sur ces licences, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure information protection**. DKE fonctionne avec les étiquettes de confidentialité et nécessite Azure information protection.

Les étiquettes de sensibilité DKE sont mises à la disposition des utilisateurs finaux via le ruban de confidentialité dans les applications de bureau Office. Installez ces éléments prérequis sur chaque ordinateur client sur lequel vous souhaitez protéger et consommer des documents protégés.

**Microsoft Office apps pour Enterprise** version *. 12711 ou version ultérieure (versions de bureau de Word, PowerPoint et Excel) sur Windows.

Versions du **client d’étiquetage unifié Azure information protection** 2.7.93.0 ou version ultérieure. Téléchargez et installez le client d’étiquetage unifié à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Environnements pris en charge pour le stockage et l’affichage du contenu protégé par DKE

**Applications prises en charge**. [Applications Microsoft 365 pour](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) les clients d’entreprise sur Windows, y compris Word, Excel et PowerPoint.

**Prise en charge du contenu en ligne**. Les documents et les fichiers stockés en ligne dans Microsoft SharePoint et OneDrive entreprise sont pris en charge. Vous pouvez partager le contenu chiffré par courrier électronique, mais vous ne pouvez pas afficher les documents et fichiers chiffrés en ligne. Au lieu de cela, vous devez afficher le contenu protégé à l’aide des applications de bureau sur votre ordinateur local.

## <a name="overview-of-deploying-dke"></a>Vue d’ensemble du déploiement de DKE

Suivez les étapes générales suivantes pour configurer DKE. Une fois que vous aurez effectué ces étapes, vos utilisateurs finaux seront en mesure de protéger vos données hautement sensibles à l’aide du chiffrement à double clé.

1. Déployez le service DKE comme décrit dans cet article.

2. Créez une étiquette avec un chiffrement à clé double. Accédez à protection des informations sous le [Centre de conformité Microsoft 365](https://compliance.microsoft.com) et créez une nouvelle étiquette avec le chiffrement à clé double. [Pour appliquer le chiffrement, voir restreindre l’accès au contenu à l’aide des étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels).

3. Utilisez des étiquettes de chiffrement à double clé. Protégez les données en sélectionnant une étiquette chiffrée à double clé dans le ruban de sensibilité de Microsoft Office.

Il existe plusieurs façons de procéder pour déployer le chiffrement à double clé. Cet article fournit des instructions détaillées afin que les administrateurs moins expérimentés déploient correctement le service. Si vous êtes familiarisé, vous pouvez choisir d’utiliser vos propres méthodes.

## <a name="deploy-dke"></a>Déployer DKE

Cet article et la vidéo de déploiement utilisent Azure comme destination de déploiement pour le service DKE. Si vous effectuez le déploiement vers un autre emplacement, vous devez fournir vos propres valeurs.

Regardez la [vidéo sur le déploiement de chiffrement à double clé](https://youtu.be/vDWfHN_kygg) pour voir une présentation détaillée des concepts présentés dans cet article. La vidéo prend environ 18 minutes.

Suivez ces étapes générales pour configurer le chiffrement à double clé pour votre organisation.

1. [Installer les composants logiciels requis pour le service DKE](#install-software-prerequisites-for-the-dke-service)
1. [Cloner le référentiel GitHub de chiffrement à double clé](#clone-the-dke-github-repository)
1. [Modifier les paramètres d’application](#modify-application-settings)
1. [Générer des clés de test](#generate-test-keys)
1. [Générez le projet.](#build-the-project)
1. [Déployer le service DKE et publier le magasin de clés](#deploy-the-dke-service-and-publish-the-key-store)
1. [Valider votre déploiement](#validate-your-deployment)
1. [Enregistrer votre magasin de clés](#register-your-key-store)
1. [Créer des étiquettes de confidentialité à l’aide de DKE](#create-sensitivity-labels-using-dke)
1. [Activer DKE dans votre client](#enable-dke-in-your-client)
1. [Migrer des fichiers protégés des étiquettes HYOK vers les étiquettes DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Lorsque vous avez fini, vous pouvez chiffrer des documents et des fichiers à l’aide de DKE. Pour plus d’informations, consultez [la rubrique appliquer des étiquettes de confidentialité à vos fichiers et à votre messagerie électronique dans Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>Installer les composants logiciels requis pour le service DKE

Installez ces éléments prérequis sur l’ordinateur sur lequel vous souhaitez installer le service DKE.

**.Net Core 3,1 SDK**. Téléchargez et installez le kit de développement logiciel (SDK) à partir de [Télécharger .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio code**. Téléchargez Visual Studio code à partir de [https://code.visualstudio.com/](https://code.visualstudio.com) . Une fois installé, exécutez Visual Studio code et sélectionnez **Afficher** les \> **Extensions**. Installez ces extensions.

- C# pour Visual Studio code

- Gestionnaire de package NuGet

**Ressources git**. Téléchargez et installez l’un des éléments suivants.

- [Git](https://git-scm.com/downloads)

- [Bureau GitHub](https://desktop.github.com/)

- [GitHub entreprise](https://github.com/enterprise)

**OpenSSL** [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) doit être installé pour [générer des clés de test](#generate-test-keys) une fois que vous avez déployé DKE. Vérifiez que vous l’appelez correctement à partir de votre chemin d’accès aux variables d’environnement. Par exemple, pour plus d’informations, consultez la section « ajouter le répertoire d’installation au chemin d’accès » [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) .

### <a name="clone-the-dke-github-repository"></a>Cloner le référentiel DKE GitHub

Microsoft fournit les fichiers source DKE dans un référentiel GitHub. Vous clonez le référentiel pour créer le projet localement pour l’utilisation de votre organisation. Le référentiel DKE GitHub se trouve à l’emplacement [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService) .

Les instructions suivantes sont destinées aux utilisateurs de git ou de code Visual Studio inexpérimentés :

1. Dans votre navigateur, accédez à : [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService) .

2. Dans la partie droite de l’écran, sélectionnez **code**. Votre version de l’interface utilisateur peut afficher un bouton **Clone ou télécharger** . Ensuite, dans la liste déroulante qui apparaît, sélectionnez l’icône copier pour copier l’URL dans votre presse-papiers.

    Par exemple :

   ![Cloner le référentiel du service de chiffrement à clé double à partir de GitHub](../media/dke-clone.png)

3. Dans Visual Studio code, sélectionnez **Afficher** la \> **palette de commandes** et sélectionnez **git : Clone**. Pour accéder à l’option dans la liste, commencez `git: clone` à taper pour filtrer les entrées, puis sélectionnez-la dans la liste déroulante. Par exemple :

   ![Option GIT : clone de Visual Studio code](../media/dke-vscode-clone.png)

4. Dans la zone de texte, collez l’URL que vous avez copiée à partir de git et sélectionnez **Clone dans GitHub**.

5. Dans la boîte de dialogue **Sélectionner un dossier** qui s’affiche, accédez à l’emplacement où vous souhaitez stocker le référentiel et sélectionnez-le. À l’invite, sélectionnez **ouvrir**.

    Le référentiel s’ouvre dans Visual Studio code et affiche la branche git actuelle en bas à gauche. La branche doit être **Master**.

    Par exemple :

   ![Branche Visual Studio code Master](../media/dke-vscode-master.png)

6. Sélectionnez le **masque** de mots dans la liste des branches.

   > [!IMPORTANT]
   > La sélection de la branche principale garantit que vous disposez des fichiers appropriés pour générer le projet. Si vous ne sélectionnez pas la branche appropriée, votre déploiement échouera.

Votre référentiel source DKE est maintenant configuré localement. Ensuite, [Modifiez les paramètres d’application](#modify-application-settings) pour votre organisation.

### <a name="modify-application-settings"></a>Modifier les paramètres d’application

Pour déployer le service DKE, vous devez modifier les types de paramètres d’application suivants :

- [Paramètres d’accès clés](#key-access-settings)
- [Paramètres de client et de clé](#tenant-and-key-settings)

Vous modifiez les paramètres de l’application dans le fichier appsettings.js. Ce fichier se trouve dans le DoubleKeyEncryptionService référentiel que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store. Par exemple, dans Visual Studio code, vous pouvez accéder au fichier comme indiqué dans l’image suivante.

![Recherche de la appsettings.jssur le fichier pour DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Paramètres d’accès clés

Choisissez d’utiliser ou non l’autorisation de messagerie ou de rôle. DKE ne prend en charge qu’une seule de ces méthodes d’authentification à la fois.

- **Autorisation de messagerie**. Permet à votre organisation d’autoriser l’accès aux clés en fonction des adresses de messagerie uniquement.

- **Autorisation de rôle**. Permet à votre organisation d’autoriser l’accès aux clés en fonction des groupes Active Directory et exige que le service Web interroge LDAP.

**Pour définir les paramètres d’accès clés pour DKE à l’aide de l’autorisation de messagerie**

1. Ouvrez le fichier **appsettings.js** et localisez le `AuthorizedEmailAddress` paramètre.

2. Ajoutez l’adresse ou les adresses de messagerie que vous souhaitez autoriser. Séparez les adresses de messagerie par des guillemets et des virgules. Par exemple :

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Recherchez le `LDAPPath` paramètre et supprimez le texte `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` entre guillemets doubles. Laissez les guillemets doubles en place. Lorsque vous avez terminé, le paramètre doit ressembler à ce qui suit.

   ```json
   "LDAPPath": ""
   ```

4. Localisez le `AuthorizedRoles` paramètre et supprimez la ligne entière.

Cette image montre le **appsettings.jssur** un fichier correctement mis en forme pour l’autorisation de messagerie.

   ![appsettings.jssur le fichier affichant la méthode d’autorisation de messagerie](../media/dke-email-accesssetting.png)

**Pour définir les paramètres d’accès clés pour DKE à l’aide de l’autorisation de rôle**

1. Ouvrez le fichier **appsettings.js** et localisez le `AuthorizedRoles` paramètre.

2. Ajoutez les noms de groupe Active Directory que vous souhaitez autoriser. Séparez les noms de plusieurs groupes par des guillemets et des virgules. Par exemple :

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Localisez le `LDAPPath` paramètre et ajoutez le domaine Active Directory. Par exemple :

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Localisez le `AuthorizedEmailAddress` paramètre et supprimez la ligne entière.

Cette image montre le **appsettings.jssur** un fichier correctement mis en forme pour l’autorisation de rôle.

   ![appsettings.jssur le fichier affichant la méthode d’autorisation de rôle](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Paramètres de client et de clé

Les paramètres de client et de clé DKE se trouvent dans le fichier **appsettings.js** .

**Pour configurer les paramètres de client et de clé pour DKE**

1. Ouvrez le fichier **appsettings.js** .

2. Recherchez le `ValidIssuers` paramètre et remplacez-le `<tenantid>` par votre ID de client. Vous pouvez localiser votre ID de locataire en accédant au portail Azure et en affichant les [Propriétés du client](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Par exemple :

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

Localisez le `JwtAudience` . Remplacez `<yourhostname>` par le nom d’hôte de l’ordinateur sur lequel le service DKE s’exécutera. Par exemple :

  > [!IMPORTANT]
  > La valeur de `JwtAudience` doit correspondre *exactement*au nom de votre hôte. Vous pouvez utiliser **localhost : 5001** lors du débogage. Toutefois, lorsque vous avez fini de déboguer, veillez à mettre à jour cette valeur sur le nom d’hôte du serveur.

- `TestKeys:Name`. Entrez un nom pour votre clé. Par exemple : `TestKey1`
- `TestKeys:Id`. Créez un GUID et entrez-le en tant que `TestKeys:ID` valeur. Par exemple, `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Vous pouvez utiliser un site comme le [Générateur de GUID en ligne](https://guidgenerator.com/) pour générer un GUID de manière aléatoire.

Cette image indique le format correct pour les paramètres de client et de clé dans **appsettings.jsactivé**. `LDAPPath` est configuré pour l’autorisation de rôle.

![Indique les paramètres client et clé corrects pour DKE dans le fichier appsettings.js.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Générer des clés de test

Une fois que vous avez défini les paramètres de votre application, vous êtes prêt à générer des clés de test publiques et privées.

Pour générer des clés :

1. Dans le menu Démarrer de Windows, exécutez l’invite de commandes OpenSSL.

2. Accédez au dossier dans lequel vous souhaitez enregistrer les clés de test. Les fichiers que vous créez en suivant les étapes de cette tâche sont stockés dans le même dossier.

3. Générez la nouvelle clé de test.

   ```dos
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

4. Générez la clé privée.

   ```dos
   openssl rsa -in key.pem -out privkeynopass.pem
   ```

5. Générez la clé publique.

   ```dos
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

6. Dans un éditeur de texte, ouvrez **pubkeyonly. pem**. Copiez tout le contenu du fichier **pubkeyonly. pem** , à l’exception de la première et de la dernière ligne, dans la `PublicPem` section du fichier **appsettings.js** .

7. Dans un éditeur de texte, ouvrez **privkeynopass. pem**. Copiez tout le contenu du fichier **privkeynopass. pem** , à l’exception de la première et de la dernière ligne, dans la `PrivatePem` section du fichier **appsettings.js** .

8. Supprimez tous les espaces et lignes de nouvelle ligne dans les `PublicPem` `PrivatePem` sections et.

    > [!IMPORTANT]
    > Lorsque vous copiez ce contenu, ne supprimez pas les données du PEM.

9. Dans Visual Studio code, accédez au fichier **Startup.cs** . Ce fichier se trouve dans le DoubleKeyEncryptionService référentiel que vous avez cloné localement sous DoubleKeyEncryptionService\src\customer-key-store\.

10. Recherchez les lignes suivantes :

   ```c#
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
   ```

11. Remplacez ces lignes par le texte suivant :

   ```csharp
   services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
   ```

   Les résultats finaux doivent ressembler à ce qui suit.

   ![fichier startup.cs pour la préversion publique](../media/dke-startupcs-usetestkeys.png)

Vous êtes maintenant prêt à [créer votre projet DKE](#build-the-project).

### <a name="build-the-project"></a>Générez le projet.

Suivez les instructions ci-dessous pour générer le projet DKE localement :

1. Dans Visual Studio code, dans le référentiel du service DKE, sélectionnez **Afficher** la \> **palette de commandes** , puis tapez **générer** à l’invite.

2. Dans la liste, choisissez **tâches : exécuter la tâche de génération**.

   Si aucune tâche de génération n’a été trouvée, sélectionnez **configurer la tâche de génération** et créez-en une pour .net Core comme suit.

   ![Configurer une tâche de génération manquante pour .NET](../media/dke-configurebuildtask.png)

   1. Choisissez **create tasks.json from template**.

      ![Créer tasks.jssur le fichier à partir du modèle pour DKE](../media/dke-createtasksjsonfromtemplate.png)

   2. Dans la liste des types de modèles, sélectionnez **.net Core**.

      ![Sélectionnez le modèle approprié pour DKE](../media/dke-tasksjsontemplate.png)

   3. Dans la section générer, recherchez le chemin d’accès au fichier **customerkeystore. csproj** . Si ce n’est pas le cas, ajoutez la ligne suivante :

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Exécutez de nouveau la génération.

3. Vérifiez qu’il n’y a pas d’erreurs rouges dans la fenêtre sortie.

   S’il y a des erreurs rouges, vérifiez la sortie de la console. Assurez-vous que vous avez effectué toutes les étapes précédentes correctement et que les versions de build correctes sont présentes.

4. Sélectionnez **exécuter** \> **Démarrer le débogage** pour déboguer le processus. Si vous êtes invité à sélectionner un environnement, sélectionnez **.net Core**.

Le débogueur .NET Core se lance généralement vers `https://localhost:5001` . Pour afficher votre clé de test, accédez à `https://localhost:5001` et ajoutez une barre oblique (/) et le nom de votre clé. Par exemple :

```https
https://localhost:5001/TestKey1
```

La clé doit s’afficher au format JSON.

Votre installation est maintenant terminée. Avant de publier le keystore, dans appsettings.jsactivé, pour le paramètre JwtAudience, vérifiez que la valeur de hostname correspond exactement au nom de l’hôte de service de l’application. Vous pouvez l’avoir remplacée par localhost pour dépanner la Build.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Déployer le service DKE et publier le magasin de clés

Pour les déploiements de production, déployez le service dans un nuage tiers ou [publiez-le sur un système local](https://docs.microsoft.com/aspnet/core/tutorials/publish-to-iis?view=aspnetcore-3.1&preserve-view=true&tabs=netcore-cli).

Vous pouvez préférer d’autres méthodes de déploiement de vos clés. Sélectionnez la méthode qui convient le mieux à votre organisation.

Pour les déploiements pilotes, vous pouvez déployer dans Azure et commencer immédiatement.

**Pour créer une instance Azure Web App afin d’héberger votre déploiement DKE**

Pour publier le magasin de clés, vous allez créer une instance de service d’application Azure pour héberger votre déploiement DKE. Ensuite, vous allez publier vos clés générées dans Azure.

1. Dans votre navigateur, connectez-vous au [portail Microsoft Azure](https://ms.portal.azure.com)et accédez à **app services**  >  **Add**.

2. Sélectionnez votre abonnement et le groupe de ressources, puis définissez les détails de votre instance.

    - Entrez le nom d’hôte de l’ordinateur sur lequel vous souhaitez installer le service DKE. Assurez-vous qu’il s’agit du même nom que celui défini pour le paramètre JwtAudience dans le fichier [**appsettings.js**](#tenant-and-key-settings) . La valeur que vous fournissez pour le nom est également WebAppInstanceName.

    - Pour **publier**, sélectionner le **code**et pour la **pile Runtime**, sélectionnez **.net Core 3,1**.

    Par exemple :

   ![Ajouter votre service d’application](../media/dke-azure-add-app-service.png)

3. Au bas de la page, sélectionnez **révision + créer**, puis **Ajouter**.

4. Effectuez l’une des opérations suivantes pour publier vos clés générées :

    - [Publier via ZipDeployUI](#publish-via-zipdeployui)
    - [Publier via FTP](#publish-via-ftp)
    - [Publier via Visual Studio 2019 ou version ultérieure](https://docs.microsoft.com/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publier via ZipDeployUI

1. Accédez à `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

    Par exemple : https://dkeservice.scm.azurewebsites.net/ZipDeployUI

2. Dans la base de code pour le magasin de clés, accédez au dossier **Customer-Key-store\src\customer-Key-Store** et vérifiez que ce dossier contient le fichier **customerkeystore. csproj** .

3. Exécuter : **publication dotnet**

     La fenêtre sortie affiche le répertoire dans lequel la publication a été déployée.

    Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Envoyez tous les fichiers du répertoire de publication dans un fichier. zip. Lors de la création du fichier. zip, assurez-vous que tous les fichiers du répertoire sont au niveau racine du fichier. zip.

5. Faites glisser et déposez le fichier. zip que vous créez sur le site ZipDeployUI que vous avez ouvert ci-dessus. Par exemple : https://dkeservice.scm.azurewebsites.net/ZipDeployUI

DKE est déployé et vous pouvez accéder aux clés de test que vous avez créées. Poursuivez [la validation de votre déploiement](#validate-your-deployment) ci-dessous.

#### <a name="publish-via-ftp"></a>Publier via FTP

1. Connectez-vous au service d’application que vous avez créé [ci-dessus](#deploy-the-dke-service-and-publish-the-key-store).

    Dans votre navigateur, accédez à : **Azure portal**  >  **App Service**  >  **Centre de déploiement**de  >  **déploiement manuel**  >  **FTP**  >  **Dashboard**du centre de déploiement Azure Portal App.

2. Copiez les chaînes de connexion affichées dans un fichier local. Vous utiliserez ces chaînes pour vous connecter au service d’application Web et télécharger des fichiers via FTP.

    Par exemple :

   ![Copier des chaînes de connexion à partir du tableau de bord FTP](../media/dke-ftp-dashboard.png)

3. Dans la base de code pour le stockage de clés, accédez au **répertoire Customer-Key-store\src\customer-Key-Store**

4. Vérifiez que ce répertoire contient le fichier **customerkeystore. csproj** .

5. Exécuter : **publication dotnet**

    La sortie contient le répertoire dans lequel la publication a été déployée.

    Par exemple : `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Envoyez tous les fichiers du répertoire de publication dans un fichier zip. Lors de la création du fichier. zip, assurez-vous que tous les fichiers du répertoire sont au niveau racine du fichier. zip.

7. À partir de votre client FTP, utilisez les informations de connexion que vous avez copiées pour vous connecter à votre service d’application. Téléchargez le fichier. zip que vous avez créé à l’étape précédente dans le répertoire racine de votre application Web.

DKE est déployé et vous pouvez accéder aux clés de test que vous auriez créées. Ensuite, [validez votre déploiement](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Valider votre déploiement

Après avoir déployé DKE à l’aide de l’une des méthodes décrites ci-dessus, validez les principaux paramètres de déploiement et de magasin de clés.

Générer

src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/MyKey

Par exemple :

key_store_tester.ps1 https://mydkeservice.com/mykey

Assurez-vous qu’aucune erreur ne s’affiche dans la sortie. Lorsque vous êtes prêt, [Enregistrez votre magasin de clés](#register-your-key-store).

## <a name="register-your-key-store"></a>Enregistrer votre magasin de clés

Les étapes suivantes vous permettent d’enregistrer votre service DKE. L’inscription de votre service DKE est la dernière étape du déploiement de DKE avant de pouvoir commencer à créer des étiquettes.

Pour enregistrer le service DKE :

1. Dans votre navigateur, ouvrez le [portail Microsoft Azure](https://ms.portal.azure.com/), puis accédez à **toutes les** \> **Identity** \> **inscriptions des applications d'** identité des services.

2. Sélectionnez **nouvelle inscription**, puis entrez un nom explicite.

3. Sélectionnez un type de compte parmi les options affichées.

    Si vous utilisez Microsoft Azure avec un domaine non personnalisé, tel que **onmicrosoft.com**, sélectionnez **comptes dans cet annuaire d’organisation uniquement (Microsoft uniquement-client unique).**

    Par exemple :

   ![Inscription de l’application](../media/dke-app-registration.png)

4. Au bas de la page, sélectionnez **Enregistrer** pour créer la nouvelle inscription de l’application.

5. Dans la nouvelle inscription de l’application, dans le volet gauche, sous **gérer**, sélectionnez **authentification**.

6. Sélectionnez **Ajouter une plateforme**.

7. Dans la fenêtre contextuelle **configurer les plateformes** , sélectionnez **Web**.

8. Sous **URI de redirection**, entrez l’URI de votre service de chiffrement à double clé. Entrez l’URL du service d’application, y compris le nom d’hôte et le domaine.

    Par exemple : https://mydkeservicetest.com

    - L’URL que vous entrez doit correspondre au nom d’hôte dans lequel votre service DKE est déployé.
    - Si vous testez localement avec Visual Studio, utilisez **https://localhost:5001** .
    - Dans tous les cas, le modèle doit être **https**.

    Vérifiez que le nom d’hôte correspond exactement au nom d’hôte de votre service d’application. Vous pouvez l’avoir modifié sur `localhost` pour dépanner la Build. Dans **appsettings.jsactivé**, cette valeur est le nom d’hôte que vous avez défini pour `JwtAudience` .

9. Sous **attribution implicite**, activez la case à cocher **jetons d’ID** .

10. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

11. Dans le volet de gauche, sélectionnez **exposer une API**, puis en regard de l’ID d’application URI, sélectionnez **Set**.

12. Toujours sur la page **exposer une API** , dans la zone **étendues définies par cette API** , sélectionnez **Ajouter une étendue**. Dans la nouvelle étendue :

    1. Définissez le nom de l’étendue en tant que **user_impersonation**.

    2. Sélectionnez les administrateurs et les utilisateurs qui peuvent consentir.

    3. Définissez les valeurs restantes requises.

    4. Sélectionnez **Ajouter une étendue**.

    5. Sélectionnez **Enregistrer** dans la partie supérieure pour enregistrer vos modifications.

13. Toujours sur la page **exposer une API** , dans la zone **applications clientes autorisées** , sélectionnez **Ajouter une application cliente**.

    Dans la nouvelle application cliente :

    1. Définissez l’ID client comme **d3590ed6-52b3-4102-Aeff-aad2292ab01c**. Cette valeur est l’ID client Microsoft Office et permet à Office d’obtenir un jeton d’accès pour votre magasin de clés.

    2. Sous **étendues autorisées**, sélectionnez l’étendue **user_impersonation** .

    3. Sélectionnez **Ajouter une application**.

    4. Sélectionnez **Enregistrer** dans la partie supérieure pour enregistrer vos modifications.

Votre service DKE est maintenant enregistré. Continuez en [créant des étiquettes à l’aide de DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Créer des étiquettes de confidentialité à l’aide de DKE

Dans le centre de conformité Microsoft 365, créez une étiquette de sensibilité et appliquez le chiffrement comme vous le feriez autrement. Sélectionnez **utiliser le chiffrement à double clé** et entrez l’URL du point de terminaison de votre clé.

Par exemple :

![Sélectionnez utiliser le chiffrement à double clé dans le centre de conformité Microsoft 365](../media/dke-use-dke.png)

Toutes les étiquettes DKE que vous ajoutez commencent à apparaître pour les utilisateurs dans les versions les plus récentes des applications Microsoft 365 pour entreprises.

> [!NOTE]
> L’actualisation des clients avec les nouvelles étiquettes peut prendre jusqu’à 24 heures.

### <a name="enable-dke-in-your-client"></a>Activer DKE dans votre client

Si vous êtes un Office Insider, DKE est activé pour vous. Dans le cas contraire, activez DKE pour votre client en ajoutant les clés de Registre suivantes :

```properties
    [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
    "DoubleKeyProtection"=dword:00000001

    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
    "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Migrer des fichiers protégés des étiquettes HYOK vers les étiquettes DKE

Si vous le souhaitez, une fois que vous avez terminé la configuration de DKE, vous pouvez migrer le contenu que vous avez protégé à l’aide des étiquettes HYOK vers les étiquettes DKE. Pour effectuer la migration, vous utiliserez le scanneur AIP. Pour commencer à utiliser le scanneur, voir [qu’est-ce que le scanneur d’étiquetage unifié Azure information protection ?](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner).

Si vous ne migrez pas le contenu, votre contenu protégé HYOK restera non affecté.
