---
title: API REST Hello World pour Microsoft 365 Defender web
description: Découvrez comment créer une application et utiliser un jeton pour accéder aux API Microsoft 365 Defender’application
keywords: application, jeton, accès, aad, application, inscription d’application, powershell, script, administrateur général, autorisation, microsoft 365 defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 50316659caf811410b9422151e47feb17fbead8055bec08a3e4e342d61f2d83b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53888850"
---
# <a name="hello-world-for-microsoft-365-defender-rest-api"></a>API REST Hello World pour Microsoft 365 Defender web

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

## <a name="get-incidents-using-a-simple-powershell-script"></a>Obtenir des incidents à l’aide d’un script PowerShell simple

La réalisation de ce projet doit prendre entre 5 et 10 minutes. Cette estimation de temps inclut l’inscription de l’application et l’application du code à partir de l’exemple de script PowerShell.

### <a name="register-an-app-in-azure-active-directory"></a>Inscrire une application dans Azure Active Directory

1. Connectez-vous [à Azure](https://portal.azure.com) en tant qu’utilisateur avec le **rôle d’administrateur** général.

2. Accédez à **Azure Active Directory**  >  **inscription de l’application Nouvelle**  >  **inscription.**

   ![Image de la Microsoft Azure et de la navigation vers l’inscription de l’application](../../media/atp-azure-new-app2.png)

3. Dans le formulaire d’inscription, choisissez un nom pour votre application, puis sélectionnez **Enregistrer**. La sélection d’un URI de redirection est facultative. Vous n’en aurez pas besoin pour compléter cet exemple.

4. Dans la page de votre application, sélectionnez **Autorisations API** Ajouter des API d’autorisation que mon organisation utilise >, tapez Protection Microsoft contre les menaces, puis sélectionnez  >    >   Protection **Microsoft contre les menaces.**  Votre application peut désormais accéder à Microsoft 365 Defender.

   > [!TIP]
   > *La Protection Microsoft contre les* menaces est un ancien nom Microsoft 365 Defender et n’apparaîtra pas dans la liste d’origine. Vous devez commencer à écrire son nom dans la zone de texte pour qu’il apparaisse.
   ![Image de la sélection des autorisations d’API](../../media/apis-in-my-org-tab.PNG)

   - Sélectionnez **Application permissions**  >  **Incident.Read.All** et **sélectionnez Ajouter des autorisations.**

   ![Image de l’accès à l’API et de la sélection d’API](../../media/request-api-permissions.PNG)

5. Sélectionnez **Accorder le consentement de l’administrateur.** Chaque fois que vous ajoutez une autorisation, vous devez sélectionner Accorder le **consentement de l’administrateur** pour qu’elle prenne effet.

    ![Image de l’octroi d’autorisations](../../media/grant-consent.PNG)

6. Ajoutez un secret à l’application. Select **Certificates & secrets,** add a description to the secret, then select **Add**.

    > [!TIP]
    > Après avoir sélectionné **Ajouter,** **sélectionnez copier la valeur de secret générée.** Vous ne pourrez pas récupérer la valeur secrète après votre départ.

    ![Image de la clé de création d’application](../../media/webapp-create-key2.png)

7. Enregistrez votre ID d’application et votre ID de client dans un endroit sûr. Ils sont répertoriés sous Vue **d’ensemble** sur la page de votre application.

   ![Image de l’ID d’application créé](../../media/app-and-tenant-ids.png)

### <a name="get-a-token-using-the-app-and-use-the-token-to-access-the-api"></a>Obtenir un jeton à l’aide de l’application et utiliser le jeton pour accéder à l’API

Pour plus d’informations Azure Active Directory jetons, voir le [didacticiel Azure AD.](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

> [!IMPORTANT]
> Bien que l’exemple de cette application de démonstration vous encourage à coller votre valeur secrète à des fins de test, vous ne devez jamais coder en dur des **secrets** dans une application en cours d’exécution en production. Un tiers peut utiliser votre secret pour accéder aux ressources. Vous pouvez aider à sécuriser les secrets de votre application à l’aide [d’Azure Key Vault.](/azure/key-vault/general/about-keys-secrets-certificates) Pour obtenir un exemple pratique de la façon dont vous pouvez protéger votre application, voir Gérer les secrets dans vos applications serveur avec [Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

1. Copiez le script ci-dessous et collez-le dans votre éditeur de texte favori. Enregistrer sous **Get-Token.ps1**. Vous pouvez également exécuter le code tel quel dans PowerShell ISE, mais vous devez l’enregistrer, car nous devons l’exécuter à nouveau lorsque nous utiliserons le script d’extraction d’incident dans la section suivante.

    Ce script génère un jeton et l’enregistre dans le dossier de travail sous le *nom,Latest-token.txt*.

    ```PowerShell
    # This script gets the app context token and saves it to a file named "Latest-token.txt" under the current directory.
    # Paste in your tenant ID, client ID and app secret (App key).

    $tenantId = '' # Paste your directory (tenant) ID here
    $clientId = '' # Paste your application (client) ID here
    $appSecret = '' # # Paste your own app secret here to test, then store it in a safe place!

    $resourceAppIdUri = 'https://api.security.microsoft.com'
    $oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"
    $authBody = [Ordered] @{
      resource = $resourceAppIdUri
      client_id = $clientId
      client_secret = $appSecret
      grant_type = 'client_credentials'
    }
    $authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
    $token = $authResponse.access_token
    Out-File -FilePath "./Latest-token.txt" -InputObject $token
    return $token
    ```

#### <a name="validate-the-token"></a>Valider le jeton

1. Copiez et collez le jeton que vous avez reçu dans [JWT](https://jwt.ms) pour le décoder.
1. *JWT signifie* *JSON Web Token*. Le jeton décodé contient un certain nombre d’éléments ou de revendications au format JSON. Assurez-vous que la revendication *de rôles* dans le jeton décodé contient les autorisations souhaitées.

    Dans l’image suivante, vous pouvez voir un jeton décodé acquis à partir d’une application, avec ```Incidents.Read.All``` ```Incidents.ReadWrite.All``` , et des ```AdvancedHunting.Read.All``` autorisations :

    ![Image jwt.ms](../../media/api-jwt-ms.png)

### <a name="get-a-list-of-recent-incidents"></a>Obtenir la liste des incidents récents

Le script ci-dessous utilise **Get-Token.ps1** pour accéder à l’API. Il récupère ensuite la liste des incidents qui ont été mis à jour pour la dernière fois au cours des dernières 48 heures, puis enregistre la liste en tant que fichier JSON.

> [!IMPORTANT]
> Enregistrez ce script dans le dossier que vous avez **enregistréGet-Token.ps1**.

```PowerShell
# This script returns incidents last updated within the past 48 hours.

$token = ./Get-Token.ps1

# Get incidents from the past 48 hours.
# The script may appear to fail if you don't have any incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# This URL contains the type of query and the time filter we created above.
# Note that `$filter` does not refer to a local variable in our script --
# it's actually an OData operator and part of the API's syntax.
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the webrequest headers
$headers = @{
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the request and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results.
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get a string containing the execution time. We concatenate that string to the name 
# of the output file to avoid overwriting the file on consecutive runs of the script.
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"

Out-File -FilePath $outputJsonPath -InputObject $incidents
```

Vous avez terminé ! Vous avez réussi :

- Création et inscription d’une application.
- Autorisation accordée à cette application pour lire les alertes.
- Connecté à l’API.
- Utilisé un script PowerShell pour renvoyer les incidents mis à jour au cours des dernières 48 heures.

## <a name="related-articles"></a>Articles connexes

- [Microsoft 365 Defender Vue d’ensemble des API](api-overview.md)
- [Accéder aux API Microsoft 365 Defender de données](api-access.md)
- [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)
- [Créer une application pour accéder Microsoft 365 Defender API au nom d’un utilisateur](api-create-app-user-context.md)
- [Créer une application avec un accès partenaire multi-locataire aux API Microsoft 365 Defender client](api-partner-access.md)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Autorisation OAuth 2.0 pour la connexion de l’utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)