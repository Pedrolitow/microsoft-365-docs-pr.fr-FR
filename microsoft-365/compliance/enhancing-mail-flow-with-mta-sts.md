---
title: 'Amélioration du flux de messagerie avec MTA-STS '
f1.keywords:
- NOCSH
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.assetid: ''
ms.collection:
- purview-compliance
- m365solution-mip
- m365initiative-compliance
- highpri
description: Découvrez comment améliorer le flux de messagerie avec MTA-STS.
ms.openlocfilehash: 51ea4595c208ded39c980eee0ad9445383754350
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68663540"
---
# <a name="enhancing-mail-flow-with-mta-sts"></a>Amélioration du flux de messagerie avec MTA-STS

La prise en charge de la norme [SMTP MTA Strict Transport Security](https://datatracker.ietf.org/doc/html/rfc8461) (MTA-STS) est ajoutée à Exchange Online. La norme a été développée pour garantir que TLS est toujours utilisé pour les connexions entre les serveurs de messagerie. Il fournit également un moyen d’envoyer des serveurs pour vérifier que le serveur de réception dispose d’un certificat approuvé. Si TLS n’est pas proposé ou si le certificat n’est pas valide, l’expéditeur refuse de remettre des messages. Ces nouvelles vérifications améliorent la sécurité globale de SMTP et protègent contre les attaques de l’intercepteur.

MTA-STS can be broken down into two scenarios: Inbound and Outbound Protection. Inbound covers the protection of domains hosted in Exchange Online with MTA-STS and Outbound covers the MTA-STS validations performed by Exchange Online when sending emails to MTA-STS protected domains.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="outbound-protection"></a>Protection sortante

Tous les messages envoyés à partir d’Exchange Online vers des destinataires protégés par MTA-STS sont validés avec ces vérifications de sécurité supplémentaires définies par la norme MTA-STS. Les administrateurs n’ont rien à faire pour qu’elle s’applique. Notre implémentation sortante respecte les souhaits des propriétaires de domaine destinataire via leur stratégie MTA-STS. MTA-STS fait partie de l’infrastructure de sécurité d’Exchange Online, et elle est donc toujours activée (comme d’autres fonctionnalités SMTP de base).

## <a name="inbound-protection"></a>Protection entrante

Les propriétaires de domaine peuvent prendre des mesures pour protéger les e-mails envoyés à leurs domaines avec MTA-STS, si leur enregistrement MX pointe vers Exchange Online. Si votre enregistrement MX pointe vers un service tiers intermédiaire, vous devez vérifier que les exigences MTA-STS sont respectées par ces derniers et suivre leurs instructions.

Une fois MTA-STS configuré pour votre domaine, tous les messages envoyés par les expéditeurs qui prennent en charge MTA-STS effectuent les validations définies par la norme pour garantir une connexion sécurisée. Si vous recevez un e-mail d’un expéditeur qui ne prend pas en charge MTA-STS, l’e-mail sera toujours remis sans la protection supplémentaire. De même, il n’y a aucune interruption des messages si vous n’utilisez pas encore MTA-STS, mais que l’expéditeur le prend en charge. Le seul scénario où les messages ne sont’ pas remis est lorsque les deux côtés utilisent MTA-STS et que la validation MTA-STS échoue.

## <a name="how-to-adopt-mta-sts"></a>Guide pratique pour adopter MTA-STS

MTA-STS permet à un domaine de déclarer la prise en charge de TLS et de communiquer l’enregistrement MX et le certificat de destination à attendre. Il indique également ce qu’un serveur d’envoi doit faire en cas de problème. Cette communication s’effectue par le biais d’une combinaison d’un enregistrement TXT DNS et d’un fichier de stratégie publié en tant que page web HTTPS. La stratégie protégée par HTTPS introduit une autre protection de sécurité que les attaquants doivent surmonter.

L’enregistrement TXT MTA-STS d’un domaine indique la prise en charge de MTA-STS à un expéditeur, après quoi la stratégie MTA-STS basée sur HTTPS du domaine est récupérée par l’expéditeur. L’enregistrement TXT suivant est un exemple qui déclare la prise en charge de MTA-STS :

`_mta-sts.contoso.com. 3600 IN TXT v=STSv1; id=20220101000000Z;`

La stratégie MTA-STS d’un domaine doit se trouver à une URL prédéfinie hébergée par l’infrastructure web du domaine. La syntaxe de l’URL est `https://mta-sts.<domain name>/.well-known/mta-sts.txt`. Par exemple, la stratégie de Microsoft.com se trouve à l’adresse suivante : <https://mta-sts.microsoft.com/.well-known/mta-sts.txt>.

```text
version: STSv1
mode: enforce
mx: *.mail.protection.outlook.com
max_age: 604800
```

Tout client dont les enregistrements MX pointent directement vers Exchange Online peut spécifier dans sa propre stratégie les mêmes valeurs que celles indiquées ci-dessus dans la stratégie microsoft.com. Les informations requises uniques dans la stratégie sont l’enregistrement MX qui pointe vers Exchange Online (`*`.mail.protection.outlook.com) et le même certificat est partagé par tous les clients Exchange Online. Exchange Online n’autorise qu’une seule organisation à recevoir des e-mails pour un domaine donné, de sorte que l’utilisation d’un caractère générique n’affaiblit pas la sécurité, mais ce n’est peut-être pas le cas pour d’autres services de messagerie. Il est possible de publier votre stratégie en mode *test* pour vous assurer qu’elle est valide avant de la modifier en mode *d’application* . Il existe des outils de validation tiers qui peuvent vérifier votre configuration.

Ces stratégies ne sont pas quelque chose que Exchange Online pouvez héberger pour le compte des clients. Les clients doivent donc configurer la stratégie STS de leur domaine à l’aide des services qu’ils préfèrent. Les services Azure peuvent être facilement utilisés pour l’hébergement de stratégie. Vous trouverez une procédure pas à pas de configuration plus loin dans cet article. La stratégie doit être protégée par HTTPS avec un certificat pour le sous-domaine `mta-sts.<domain name>`.

Une fois l’enregistrement TXT DNS créé et le fichier de stratégie disponible à l’URL HTTPS requise, le domaine est protégé par MTA-STS. Des détails sur MTA-STS sont disponibles dans [RFC 8461](https://datatracker.ietf.org/doc/html/rfc8461).

### <a name="configuring-inbound-mta-sts-with-azure-services"></a>Configuration de MTA-STS entrant avec les services Azure

> [!NOTE]
> Ces flux de configuration ont été développés pour aider Microsoft Exchange Online clients à héberger leur stratégie MTA-STS à l’aide de ressources Azure. Ce flux de configuration suppose que vous êtes un client Exchange Online qui connaît le fonctionnement de MTA-STS et ses exigences. Pour plus d’informations sur le protocole au-delà de cette rubrique, consultez [RFC8461](https://www.rfc-editor.org/rfc/rfc8461.html).

Deux ressources Azure peuvent être utilisées pour héberger la stratégie MTA-STS : [Azure Static Web App](https://azure.microsoft.com/services/app-service/static/) et [Azure Functions](/azure/azure-functions/functions-overview). Bien que cet article explique comment déployer la stratégie à l’aide des deux ressources, la méthode recommandée est [Azure Static Web App](https://azure.microsoft.com/services/app-service/static/) , car elle est conçue pour héberger des pages statiques telles que la stratégie STS, et Azure simplifie la configuration en fournissant un certificat TLS pour la page web MTA-STS prête à l’emploi, sans nécessiter plus de configuration. Si vous ne pouvez pas utiliser [Azure Static Web App](https://azure.microsoft.com/services/app-service/static/), vous pouvez également héberger votre stratégie en tant que code serverless à [l’aide de Azure Functions](/azure/azure-functions/functions-overview). Cette approche n’est pas la méthode recommandée, car Azure Function est une fonctionnalité conçue pour d’autres scénarios et n’émet pas de certificat TLS automatiquement, contrairement à Azure Static Web Apps. Par conséquent, l’utilisation [de Azure Functions](/azure/azure-functions/functions-overview) pour MTA-STS nécessite que vous émettez votre propre « mta-sts . » votre domaine] » et liez-le à la fonction.

Quelle que soit l’approche que vous avez adoptée, nous vous encourageons à vérifier que votre stratégie est correctement configurée et que le temps de réponse est acceptable ( le délai d’expiration selon les recommandations RFC est de 60 secondes).

Ces flux de configuration sont destinés à fournir uniquement des informations techniques sur les fonctionnalités Azure qui peuvent être utilisées pour héberger la stratégie MTA-STS et ne fournissent aucune information sur la facturation ou les coûts des fonctionnalités Azure. Si vous souhaitez connaître les coûts des fonctionnalités Azure, utilisez la [calculatrice de prix](https://azure.microsoft.com/pricing/calculator/) Azure.

#### <a name="option-1-recommended-azure-static-web-app"></a>Option 1 (RECOMMANDÉE) : Application web statique Azure

1. Créez une organisation Azure DevOps ou utilisez une organisation qui existe déjà. Dans cet exemple, une organisation appelée « ContosoCorporation » sera utilisée pour héberger la stratégie MTA-STS.

   :::image type="content" source="../media/projects-tab.png" alt-text="Capture d’écran montrant l’onglet projets." lightbox="../media/projects-tab.png":::

2. Dans **Repos > Files**, clonez votre dépôt dans l’IDE de votre choix. Dans cet exemple, le référentiel sera cloné dans Visual Studio.

   :::image type="content" source="../media/clone-to-vs-code.png" alt-text="Capture d’écran montrant un exemple de clonage dans Visual Studio Code." lightbox="../media/clone-to-vs-code.png":::

3. Une fois le référentiel cloné, créez le chemin d’accès au dossier suivant : `home\.well-known\`. Ensuite, créez les fichiers suivants : 

    - Fichier 1 : accueil\.well-known\mta-sts.txt

   > [!NOTE]
   > Cette configuration permet uniquement Exchange Online de recevoir des messages au nom de votre domaine. Si vous utilisez plusieurs fournisseurs de messagerie, vous devez également référencer les hôtes MX pour les domaines de ces autres fournisseurs. Les caractères génériques ou « * » ne doivent pas être utilisés comme préfixe MX dans tous les scénarios MTA-STS ; Les paramètres ci-dessous sont spécifiques à Exchange Online uniquement et ne doivent PAS être utilisés comme instructions générales pour la configuration de MTA-STS. 

    1. Entrez le texte suivant dans le fichier mta-sts.txt :
        ```powershell
           version: STSv1
           mode: testing
           mx: *.mail.protection.outlook.com
           max_age: 604800
        ```
       > [!NOTE]
       > Il est recommandé de définir initialement le mode de stratégie comme « test ». Ensuite, à la fin de la configuration et après avoir vérifié que la stratégie fonctionne comme prévu, mettez à jour le fichier mta-sts.txt de sorte que le mode soit « appliquer ».
 
       Le fichier doit uniquement contenir le contenu, comme illustré dans la capture d’écran suivante :

       :::image type="content" source="../media/contents-of-file1.png" alt-text="Capture d’écran qui affiche le contenu de File1." lightbox="../media/contents-of-file1.png":::

    - Fichier 2 : home\index.html
    
    1. Créez un fichier index.html et entrez-y le code suivant :
    
       ```powershell
           <!DOCTYPE html>
           <html lang="en">

           <head>
           <meta charset="UTF-8">
           <title>MTA-STS</title>
           </head>

           <body>
           <h1>MTA-STS Static Website index</h1>
           </body>

           </html>
       ```
           
      Le fichier doit uniquement contenir le contenu, comme illustré dans la capture d’écran suivante :
   
      :::image type="content" source="../media/contents-of-file2.png" alt-text="Capture d’écran qui affiche le contenu de File2." lightbox="../media/contents-of-file2.png":::

      Une fois le chemin d’accès au dossier et les fichiers créés, n’oubliez pas de valider les modifications et de les envoyer (push) dans votre branche principale.

4. Créez une application web statique Azure avec la configuration suivante :

    - **Nom** : MTA-STS-StaticWebApp
    - **Type de plan** : Standard
    - **Détails du déploiement** : Azure DevOps
    - **Organisation** : ContosoCorporation
    - **Projet** : MTA-STS_Project
    - **Dépôt** : MTA-STS_Project
    - **Branche** : master
    - **Préréglages de** build : Angular
    - **Emplacement de l’application** : /home
   
    :::image type="content" source="../media/new-app-with-details.png" alt-text="Capture d’écran montrant une application web statique Azure nouvellement créée avec ses informations." lightbox="../media/new-app-with-details.png":::

5. Une fois la création de l’application web statique terminée et la ressource approvisionnée, accédez à **Vue d’ensemble > Gérer le jeton de déploiement** ; copiez ensuite le jeton tel qu’il sera utilisé à l’étape suivante.

6. Accédez à **Pipelines > Créer un pipeline > Azure Repos Git > STS_Project MTA**, puis effectuez les tâches subordonnées suivantes :
    1. Accédez à **Variables > Nouvelle variable** et tapez ce qui suit :
        1. **Nom** : jeton
        1. **Valeur** : (collez le jeton que vous avez copié précédemment)
    1. Une fois la variable enregistrée, revenez à **Passer en revue votre code YAML de pipeline** et collez le code yml suivant, enregistrez et exécutez.
           
       ```powershell
           trigger:
           - main

           pool:
           vmImage: ubuntu-latest

           steps:
           - checkout: self
           submodules: true
           - task: AzureStaticWebApp@0
           inputs:
            app_location: '/home'
            azure_static_web_apps_api_token: $(token)
       ```

       Dans Azure DevOps, pendant le déploiement, si vous rencontrez l’erreur **Aucun parallélisme hébergé n’a été acheté ou accordé**, demandez via ce [formulaire](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbR63mUWPlq7NEsFZhkyH8jChUMlM3QzdDMFZOMkVBWU5BWFM3SDI2QlRBSC4u) ou implémentez une configuration via paramètres de **l’organisation > travaux parallèles > Microsoft Hosted > Modifier > travaux parallèles payants** de sorte que les « travaux parallèles payants » soient autorisés.

7. Une fois le travail terminé, vous pouvez valider le déploiement via le Portail Azure en accédant à **Azure Static Web App > Environment > Browser**. Vous devez voir le contenu du fichier index.html.

8. Ajoutez votre domaine personnel dans **Azure Static Web App > Domaines personnalisés > Ajouter**. Vous devez créer un enregistrement **CNAME** via votre fournisseur DNS (par exemple, GoDaddy) pour vérifier que la zone vous appartient. Une fois la validation terminée, Azure émet un certificat et le lie automatiquement à votre application web statique.

9. Vérifiez que votre stratégie MTA-STS est publiée via : https://mta-sts.[ votre domaine]/.well-known/mta-sts.txt.

10. Créez l’enregistrement DNS TXT MTA-STS via votre fournisseur DNS. Le format est le suivant :
     
    ```powershell
        Hostname: _mta-sts.<domain name>
        TTL: 3600 (recommended)
        Type: TXT
        Text: v=STSv1; id=<ID unique for your domain’s STS policy>Z;
    ```

    > [!NOTE]
    > Vous trouverez un exemple d’enregistrement TXT MTA-STS dans [Guide pratique pour adopter MTA-STS](#how-to-adopt-mta-sts).

11. Une fois l’enregistrement TXT disponible dans DNS, validez votre configuration MTA-STS. Une fois la configuration validée, mettez à jour le fichier mta-sts.txt afin que le mode de stratégie soit « appliquer » ; puis mettez à jour votre ID de stratégie dans l’enregistrement TXT.

#### <a name="option-2-azure-function"></a>Option 2 : Fonction Azure

1. Créez une application de fonction Azure avec la configuration suivante :

    - **Nom de l’application** de fonction : [Au choix]
    - **Publier** : Code
    - **Pile d’exécution** : .NET
    - **Version** : 6
    - **Système d’exploitation** : Windows
    - **Type de plan** : [Au choix]

    :::image type="content" source="../media/new-azure-function-app.png" alt-text="Capture d’écran montrant les configurations d’une nouvelle application de fonction Azure." lightbox="../media/new-azure-function-app.png":::

2. Ajoutez votre domaine personnalisé à l’application de fonction. Vous devez créer un enregistrement **CNAME** pour vérifier que le domaine vous appartient.

   :::image type="content" source="../media/custom-domain-to-add.png" alt-text="Capture d’écran montrant le domaine personnalisé à ajouter à l’application de fonction." lightbox="../media/custom-domain-to-add.png":::

3. Lier vos mta-sts. [votre domaine] à l’application de fonction.

   :::image type="content" source="../media/binding-to-function-app.png" alt-text="Capture d’écran montrant le processus de liaison du domaine à l’application de fonction." lightbox="../media/binding-to-function-app.png":::

4. Dans **Fichier d’application**, ajoutez l’extension suivante au fichier host.json de votre application de fonction pour éliminer le paramètre routePrefix. Cet ajout est nécessaire pour supprimer /api de l’URL de la fonction.
   
    ```powershell
        "extensions": {
    "http": {
      "routePrefix&quot;: &quot;"
      }
    }
    ```

   :::image type="content" source="../media/extension-added-to-app-file.png" alt-text="Capture d’écran montrant l’extension ajoutée au fichier d’application." lightbox="../media/extension-added-to-app-file.png":::

5. Dans votre application de fonction, accédez à **Fonctions > Créer** et configurer les paramètres suivants : 

   > [!NOTE]
   > Bien que cet exemple décrive le développement de la fonction via le portail, vous êtes libre d’utiliser VS Code ou tout autre outil de votre choix.

    - **Environnement de développement** : [Comme votre choix, cet exemple utilise « Développer dans le portail »]
    - **Sélectionner un modèle** : déclencheur HTTP
    - **Nouvelle fonction** : [Au choix]
    - **Niveau d’autorisation** : Anonyme

    :::image type="content" source="../media/create-function-screen.png" alt-text="Capture d’écran montrant la page Créer une fonction." lightbox="../media/create-function-screen.png":::

6. Une fois la fonction créée, ouvrez **Code + Test** et développez en C# une réponse HTTP asynchrone simple qui sera votre stratégie MTA-STS. L’exemple suivant indique que Exchange Online est censé recevoir des e-mails :

   > [!NOTE]
   > Il est recommandé de définir initialement le mode de stratégie comme « test ». Ensuite, à la fin de la configuration et après avoir vérifié que la stratégie fonctionne comme prévu, mettez à jour le fichier mta-sts.txt de sorte que le mode soit « appliquer ».

   :::image type="content" source="../media/mta-sts-policy.png" alt-text="Capture d’écran montrant la stratégie mta-sts développée." lightbox="../media/mta-sts-policy.png":::

7. Dans **Intégration > HTTP (req),** modifiez le déclencheur avec les valeurs suivantes :

    - **Modèle de route** : .well-known/mta-sts.txt
    - **Méthodes HTTP sélectionnées** : GET

    :::image type="content" source="../media/edit-trigger-screen.png" alt-text="Capture d’écran montrant la page Modifier le déclencheur." lightbox="../media/edit-trigger-screen.png":::

8. Vérifiez que votre stratégie MTA-STS est publiée via : https://mta-sts.[ votre domaine]/.well-known/mta-sts.txt.

9. Créez l’enregistrement DNS TXT MTA-STS via votre fournisseur DNS au format suivant :

     ```powershell
        Hostname: _mta-sts.<domain name>
        TTL: 3600 (recommended)
        Type: TXT
        Text: v=STSv1; id=<ID unique for your domain’s STS policy>Z;
     ```

   > [!NOTE]
   > Vous trouverez un exemple d’enregistrement TXT MTA-STS dans [Guide pratique pour adopter MTA-STS](#how-to-adopt-mta-sts).

10. Une fois l’enregistrement TXT disponible dans DNS, validez votre configuration MTA-STS. Une fois la configuration validée, mettez à jour le fichier mta-sts.txt de sorte que le mode de stratégie soit « appliquer » ; puis mettez à jour votre ID de stratégie dans l’enregistrement TXT.
