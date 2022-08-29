---
title: Hello World pour l’API Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Créez un appel d’API de type « Hello World » pratique à l’API Microsoft Defender pour point de terminaison.
keywords: api, api prises en charge, repérage avancé, requête, microsoft defender atp, microsoft defender pour point de terminaison
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 2805736c3d612716f3b99ba0f97fc74a0070bc68
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67328033"
---
# <a name="microsoft-defender-for-endpoint-api---hello-world"></a>API Microsoft Defender pour point de terminaison - Hello World

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


>Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="get-alerts-using-a-simple-powershell-script"></a>Obtenir des alertes à l’aide d’un script PowerShell simple

### <a name="how-long-it-takes-to-go-through-this-example"></a>Combien de temps faut-il pour suivre cet exemple ?

Cela ne prend que 5 minutes en deux étapes :

- Inscription de l’application
- Utiliser des exemples : nécessite uniquement le copier/coller d’un script PowerShell court

### <a name="do-i-need-a-permission-to-connect"></a>Ai-je besoin d’une autorisation pour me connecter ?

Pour l’étape d’inscription de l’application, vous devez avoir un rôle **Administrateur général** dans votre locataire Azure Active Directory (Azure AD).

### <a name="step-1---create-an-app-in-azure-active-directory"></a>Étape 1 : créer une application dans Azure Active Directory

1. Connectez-vous à [Azure](https://portal.azure.com) avec votre utilisateur **Administrateur général**.

2. Accédez à **Azure Active Directory** \> **inscriptions d'applications** \> **Nouvelle inscription**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Option inscriptions d'applications sous le volet Gérer dans le portail Azure Active Directory"  lightbox="images/atp-azure-new-app2.png":::

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis cliquez sur **Inscrire**.

4. Autorisez votre application à accéder à Defender pour point de terminaison et attribuez-lui l’autorisation **« Lire toutes les alertes »** :

   - Dans la page de votre application, cliquez sur **Autorisations d’API Ajouter des** \> API **d’autorisation** \> **que mon organisation utilise** > type **WindowsDefenderATP** , puis cliquez sur **WindowsDefenderATP**.

     > [!NOTE]
     > WindowsDefenderATP n’apparaît pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour l’afficher.

     :::image type="content" source="images/add-permission.png" alt-text="Option d’autorisations d’API sous le volet Gérer dans le portail Azure Active Directory" lightbox="images/add-permission.png":::

   - Choisissez **Autorisations** \> d’application **Alert.Read.All** > Cliquez sur **Ajouter des autorisations**.

     :::image type="content" source="images/application-permissions.png" alt-text="Le type d’autorisation et les volets de paramètres dans la page Demander des autorisations d’API" lightbox="images/application-permissions.png":::

     > [!IMPORTANT]
     > Vous devez sélectionner les autorisations appropriées. « Lire toutes les alertes » n’est qu’un exemple !

     Par exemple :

     - Pour [exécuter des requêtes avancées](run-advanced-query-api.md), sélectionnez l’autorisation « Exécuter des requêtes avancées ».
     - Pour [isoler un ordinateur](isolate-machine.md), sélectionnez l’autorisation « Isoler l’ordinateur ».
     - Pour déterminer l’autorisation dont vous avez besoin, consultez la section **Autorisations** de l’API que vous souhaitez appeler.

5. Cliquez sur **Accorder le consentement**.

   > [!NOTE]
   > Chaque fois que vous ajoutez une autorisation, vous devez cliquer sur **Accorder le consentement** pour que la nouvelle autorisation prenne effet.

   :::image type="content" source="images/grant-consent.png" alt-text="Option d’octroi de consentement d’autorisation dans le portail Azure Active Directory" lightbox="images/grant-consent.png":::

6. Ajoutez un secret à l’application.

    Cliquez sur **Certificats & secrets**, ajoutez une description au secret, puis cliquez sur **Ajouter**.

    > [!IMPORTANT]
    > Après avoir cliqué sur Ajouter, **copiez la valeur de secret générée**. Vous ne pourrez pas récupérer après votre départ !

    :::image type="content" source="images/webapp-create-key2.png" alt-text="L’élément de menu Certificats & secrets dans le volet Gérer dans le portail Azure Active Directory" lightbox="images/webapp-create-key2.png":::

7. Notez votre ID d’application et votre ID de locataire.

   Dans la page de votre application, accédez à **Vue d’ensemble** et copiez les éléments suivants :

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Volet Détails de l’application sous l’élément de menu Vue d’ensemble dans le portail Azure Active Directory" lightbox="images/app-and-tenant-ids.png":::

Terminé ! Vous avez inscrit une application avec succès !

### <a name="step-2---get-a-token-using-the-app-and-use-this-token-to-access-the-api"></a>Étape 2 : obtenez un jeton à l’aide de l’application et utilisez ce jeton pour accéder à l’API.

- Copiez le script ci-dessous dans PowerShell ISE ou dans un éditeur de texte, puis enregistrez-le **en tant queGet-Token.ps1**.
- L’exécution de ce script génère un jeton et l’enregistre dans le dossier de travail sous le nom **Latest-token.txt**.

   ```powershell
   # That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
   # Paste below your Tenant ID, App ID and App Secret (App key).

   $tenantId = '' ### Paste your tenant ID here
   $appId = '' ### Paste your Application ID here
   $appSecret = '' ### Paste your Application secret here

   $resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
   $oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
   $authBody = [Ordered] @{
       resource = "$resourceAppIdUri"
       client_id = "$appId"
       client_secret = "$appSecret"
       grant_type = 'client_credentials'
   }
   $authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
   $token = $authResponse.access_token
   Out-File -FilePath "./Latest-token.txt" -InputObject $token
   return $token
   ```

- Vérification de l’intégrité :
  - Exécutez le script.
  - Dans votre navigateur, accédez à : <https://jwt.ms/>.
  - Copiez le jeton (contenu du fichier Latest-token.txt).
  - Collez dans la zone supérieure.
  - Recherchez la section « rôles ». Recherchez le rôle _Alert.Read.All_ .

  :::image type="content" source="images/api-jwt-ms.png" alt-text="Volet Jeton décodé pour jwt.ms" lightbox="images/api-jwt-ms.png":::

### <a name="lets-get-the-alerts"></a>Permet d’obtenir les alertes!

- Le script ci-dessous utilise **Get-Token.ps1** pour accéder à l’API et obtient les dernières 48 heures d’alertes.
- Enregistrez ce script dans le dossier que vous avez enregistré le script précédent **Get-Token.ps1**.
- Le script crée deux fichiers (json et csv) avec les données dans le même dossier que les scripts.

  ```powershell
  # Returns Alerts created in the past 48 hours.

  $token = ./Get-Token.ps1       #run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-Token.ps1

  # Get Alert from the last 48 hours. Make sure you have alerts in that time frame.
  $dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

  # The URL contains the type of query and the time filter we create above
  # Read more about other query options and filters at   Https://TBD- add the documentation link
  $url = "https://api.securitycenter.microsoft.com/api/alerts?`$filter=alertCreationTime ge $dateTime"

  # Set the WebRequest headers
  $headers = @{
      'Content-Type' = 'application/json'
      Accept = 'application/json'
      Authorization = "Bearer $token"
  }

  # Send the webrequest and get the results.
  $response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

  # Extract the alerts from the results.
  $alerts =  ($response | ConvertFrom-Json).value | ConvertTo-Json

  # Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
  $dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

  # Save the result as json and as csv
  $outputJsonPath = "./Latest Alerts $dateTimeForFileName.json"
  $outputCsvPath = "./Latest Alerts $dateTimeForFileName.csv"

  Out-File -FilePath $outputJsonPath -InputObject $alerts
  ($alerts | ConvertFrom-Json) | Export-CSV $outputCsvPath -NoTypeInformation
  ```

Vous avez terminé ! Vous venez de réussir :

- Créé et inscrit et application
- Autorisation accordée à cette application pour lire les alertes
- Connexion de l’API
- Utilisation d’un script PowerShell pour retourner des alertes créées au cours des dernières 48 heures

## <a name="related-topic"></a>Rubrique connexe

- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder Microsoft Defender pour point de terminaison avec le contexte d’application](exposed-apis-create-app-webapp.md)
- [Accéder Microsoft Defender pour point de terminaison avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md)
