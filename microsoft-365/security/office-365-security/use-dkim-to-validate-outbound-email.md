---
title: Utiliser le service DKIM pour les e-mails dans votre domaine personnalisé dans Office 365, 2 048 bits, 1 024 bits, procédure, mode de fonctionnement, SPF, DMARC
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 10/8/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
description: 'Résumé : Cet article décrit comment utiliser DKIM (DomainKeys Identified Mail) avec Office 365 pour vous assurer que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine personnalisé.'
ms.openlocfilehash: 350a8aa793270522b3ca79b9f0fda09c49f21a62
ms.sourcegitcommit: 5710ce729c55d95b8b452d99ffb7ea92b5cb254a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "39971642"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain-in-office-365"></a>Utiliser DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365

 **Résumé :** cet article décrit comment utiliser DKIM (DomainKeys Identified Mail) avec Office 365 pour vous assurer que les systèmes de messagerie de destination approuvent les messages sortants envoyés à partir de votre domaine personnalisé.

Vous devez utiliser DKIM en plus de SPF et DMARC pour empêcher les usurpateurs d’envoyer des messages qui semblent provenir de votre domaine. DKIM vous permet d'ajouter une signature numérique aux messages électroniques sortants dans l'en-tête du message. Cela peut paraître compliqué, mais ce n’est vraiment pas le cas. Lorsque vous configurez DKIM, vous autorisez votre domaine à associer ou signer son nom à un message électronique à l’aide d’une authentification de chiffrement. Les systèmes de messagerie qui reçoivent des messages électroniques de votre domaine peuvent utiliser cette signature numérique pour déterminer si le courrier entrant est légitime.

En bref, vous utilisez une clé privée pour chiffrer l’en-tête du message électronique sortant de votre domaine. Vous publiez une clé publique sur les enregistrements DNS de votre domaine que les serveurs de réception peuvent utiliser pour décoder la signature. Ils utilisent la clé publique pour vérifier que les messages sont réellement envoyés par vous et pas par une personne qui tente d'*usurper* votre domaine.

Office 365 configure automatiquement DKIM pour les domaines initiaux 'onmicrosoft.com'. Cela signifie que vous n’avez rien à faire pour configurer DKIM pour les noms de domaine initial (par exemple, litware.onmicrosoft.com). Pour plus d'informations sur les domaines, consultez l'article [Forum aux questions sur les domaines](https://docs.microsoft.com/office365/admin/setup/domains-faq#why-do-i-have-an-onmicrosoftcom-domain).

Vous pouvez également choisir de n'effectuer aucun réglage DKIM pour votre domaine personnalisé. Si vous ne configurez pas DKIM, Office 365 crée une paire de clés privée et publique, active la signature DKIM et configure la stratégie par défaut d'Office 365 pour votre domaine personnalisé. Bien que cela soit suffisant pour la plupart des clients Office 365, vous devez configurer manuellement DKIM pour votre domaine personnalisé dans les circonstances suivantes :

- Vous avez plusieurs domaines personnalisés dans Office 365

- Vous envisagez de configurer DMARC également (recommandé)

- Vous souhaitez contrôler votre clé privée

- Vous souhaitez personnaliser vos enregistrements CNAME

- Vous souhaitez configurer des clés DKIM pour les e-mails provenant d’un domaine tiers, par exemple, si vous utilisez un programme d’envoi de courrier en nombre tiers.

Contenu de cet article :

- [Pourquoi DKIM est plus efficace que SPF seul pour empêcher l’usurpation d’identité malveillante dans Office 365](use-dkim-to-validate-outbound-email.md#HowDKIMWorks)

- [Mise à niveau manuelle de vos clés 1024 bits vers les clés de chiffrement DKIM 2048 bits](use-dkim-to-validate-outbound-email.md#1024to2048DKIM)

- [Étapes nécessaires pour configurer manuellement DKIM dans Office 365](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365)

- [Configuration de DKIM pour plusieurs domaines personnalisés dans Office 365](use-dkim-to-validate-outbound-email.md#DKIMMultiDomain)

- Désactivation de la stratégie de signature DKIM pour un domaine personnalisé dans Office 365

- Comportement par défaut pour DKIM et Office 365

- Configuration de DKIM permettant à un service tiers d’envoyer des courriers électroniques au nom de votre domaine personnalisé, ou d’usurper ce dernier

- [Étapes suivantes : après avoir configuré DKIM pour Office 365](use-dkim-to-validate-outbound-email.md#DKIMNextSteps)

> [!NOTE]
> Microsoft 365 prend en charge l’utilisateur de l’option DKIM 1024 ou 2048 bits. Si vous utilisez 1024 et que vous voulez configurer le processus DKIM 2048 bits, restez attentif aux étapes de la rotation de votre configuration de signature DKIM dans cet article. À la fin de l’année 2019, Microsoft prendra en charge les clés 2048 bits par défaut pour tous les clients.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing-in-office-365"></a>Pourquoi DKIM est plus efficace que SPF seul pour empêcher l’usurpation d’identité malveillant dans Office 365
<a name="HowDKIMWorks"> </a>

SPF ajoute des informations à une enveloppe de message, mais DKIM chiffre réellement une signature dans l’en-tête du message. Lorsque vous transférez un message, des parties de l’enveloppe de ce message peuvent être supprimées par le serveur de transfert. Étant donné que la signature numérique reste dans le message électronique, car elle fait partie de l’en-tête du message, DKIM fonctionne même lorsqu’un message a été transféré, comme illustré dans l’exemple suivant.

![Diagramme illustrant l’authentification DKIM correcte d’un message envoyé lors de l’échec du contrôle SPF](../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

Dans cet exemple, si vous aviez publié un seul enregistrement SPF TXT pour votre domaine, le serveur de messagerie du destinataire pourrait avoir marqué vos messages électroniques comme du courrier indésirable et généré un résultat faux positif. L’ajout de DKIM dans ce scénario réduit le signalement de courrier indésirable faux positif. Étant donné que DKIM repose à la fois sur le chiffrement de clé publique et les adresses IP pour l’authentification, DKIM représente une forme d’authentification beaucoup plus puissante que SPF. Nous vous recommandons d’utiliser à la fois SPF, DKIM et DMARC dans votre déploiement.

Détail important : DKIM utilise une clé privée pour insérer une signature chiffrée dans les en-têtes du message. Le domaine qui fournit la signature, aussi appelé domaine sortant, est inséré en tant que valeur du champ **d=** dans l’en-tête. Le domaine qui réalise la vérification, aussi appelé domaine du destinataire, utilise ensuite le champ **d=** pour rechercher la clé publique du système DNS et authentifier le message. Si le message est vérifié, la vérification DKIM a réussi.

## <a name="manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Mise à niveau manuelle de vos clés 1024 bits vers les clés de chiffrement DKIM 2048 bits
<a name="1024to2048DKIM"> </a>

Étant donné que le nombre de bits 1024 et 2048 sont pris en charge pour les clés DKIM, ces instructions vous indiquent comment mettre à niveau votre clé 1024 bits vers 2048. Les étapes ci-dessous concernent deux cas d’utilisation ; veuillez choisir celui qui correspond le mieux à votre configuration.

1. Lorsque vous **avez déjà configuré DKIM**, vous pouvez faire pivoter le nombre de bits comme suit :
    1. [Connectez-vous aux charges de travail Office 365 via PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window). (L’applet de commande provient d’Exchange Online.)
    1. Exécutez ensuite la cmdlet suivante :

&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`Rotate-DkimSigningConfig -KeySize 2048 -Identity {Guid of the existing Signing Config}`

1. Ou pour une **nouvelle implémentation de DKIM** :
    1. [Connectez-vous aux charges de travail Office 365 via PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-all-office-365-services-in-a-single-windows-powershell-window). (Il s’agit d’une cmdlet Exchange Online).
    1. Saisissez la cmdlet suivante :

&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `New-DkimSigningConfig -DomainName {Domain for which config is to be created} -KeySize 2048 -Enabled $True`

Restez connecté à Office 365 pour *vérifier* la configuration.

2. Exécutez la cmdlet :

&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; `Get-DkimSigningConfig | fl`

> [!TIP]
>Cette nouvelle clé 2048 bits prend effet sur RotateOnDate et envoie des e-mails avec la clé 1024 bits au niveau intermédiaire. Après quatre jours, vous pouvez à nouveau effectuer un test à l’aide de la touche 2048 bits (autrement dit, une fois que la rotation prend effet sur le deuxième sélecteur).

Si vous voulez faire pivoter vers le deuxième sélecteur, vos options sont a) laisser le service Office 365 faire pivoter le sélecteur et effectuer la mise à niveau vers le nombre de bits 2048 dans les 6 mois, ou b) après 4 jours et confirmation que le nombre de bits 2048 est utilisé, faire pivoter manuellement la deuxième touche du sélecteur en utilisant la cmdlet appropriée répertoriée ci-dessus.

## <a name="steps-you-need-to-do-to-manually-set-up-dkim-in-office-365"></a>Étapes nécessaires pour configurer manuellement DKIM dans Office 365
<a name="SetUpDKIMO365"> </a>

Pour configurer DKIM, suivez les étapes ci-dessous :

- [Publication de deux enregistrements CNAME pour votre domaine personnalisé dans le système DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)

- [Activation de la signature DKIM pour votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publication de deux enregistrements CNAME pour votre domaine dans le système DNS
<a name="Publish2CNAME"> </a>

Pour chaque domaine auquel vous souhaitez ajouter une signature DKIM dans le système DNS, vous devez publier deux enregistrements CNAME.

Exécutez les commandes suivantes :

```powershell
    New-DkimSigningConfig -DomainName <domain> -Enabled $false
    Get-DkimSigningConfig -Identity <domain> | fl Selector1CNAME, Selector2CNAME
```

Créer des CNAMes référencés dans une sortie de commande Get-DkimSigningConfig

```powershell
    Set-DkimSigningConfig -Identity <domain> -Enabled $true
```

Les enregistrements CNAME dans votre DNS pointent vers des enregistrements TXT DKIM qui existent déjà dans le DNS sur les serveurs DNS Microsoft pour Office 365.

Office 365 effectue une rotation automatique des clés à l’aide des deux enregistrements que vous établissez. Si vous avez configuré des domaines personnalisés en plus du domaine initial dans Office 365, vous devez publier deux enregistrements CNAME pour chaque domaine supplémentaire. Par conséquent, si vous avez deux domaines, vous devez publier deux enregistrements CNAME supplémentaires, et ainsi de suite.

Utilisez le format suivant pour les enregistrements CNAME.

> [!IMPORTANT]
> Si vous êtes l’un de nos clients GCC High, nous calculons _domainGuid_ différemment. Au lieu de rechercher l’enregistrement MX pour votre _initialDomain_ afin de calculer _domainGuid_, nous le calculons directement à partir du domaine personnalisé. Par exemple, si votre domaine personnalisé est « contoso.com », les points étant remplacés par des tirets, votre domainGuid devient « contoso-com ». Par conséquent, quel que soit l’enregistrement MX sur lequel pointe votre initialDomain, vous devez toujours utiliser la méthode ci-dessus pour calculer la domainGuid à utiliser dans vos enregistrements CNAMe.

```text
Host name:          selector1._domainkey
Points to address or value: selector1-<domainGUID>._domainkey.<initialDomain>
TTL:                3600

Host name:          selector2._domainkey
Points to address or value: selector2-<domainGUID>._domainkey.<initialDomain>
TTL:                3600
```

Où :

- Pour Office 365, les sélecteurs seront toujours « selector1 » ou « selector2 ».

- _domainGUID_ est identique à  _domainGUID_ dans l’enregistrement MX personnalisé pour votre domaine personnalisé figurant devant mail.protection.outlook.com. Par exemple, dans l’enregistrement MX suivant pour le domaine contoso.com, le _domainGUID_ est contoso-com :

    ```text
    contoso.com.  3600  IN  MX   5 contoso-com.mail.protection.outlook.com
    ```

- _initialDomain_ est le domaine que vous avez utilisé lorsque vous vous êtes inscrit à Office 365. Les domaines initiaux se terminent toujours par onmicrosoft.com. Pour plus d’informations sur la détermination de votre [domaine initial](https://docs.microsoft.com/office365/admin/setup/domains-faq#why-do-i-have-an-onmicrosoftcom-domain), voir Forum aux questions sur les domaines.

Par exemple, si vous avez un domaine initial cohovineyardandwinery.onmicrosoft.com, ainsi que deux domaines personnalisés cohovineyard.com et cohowinery.com, vous devez configurer deux enregistrements CNAME pour chaque domaine supplémentaire, soit un total de quatre enregistrements CNAME.

```text
Host name:          selector1._domainkey
Points to address or value: selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:          selector2._domainkey
Points to address or value: selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:          selector1._domainkey
Points to address or value: selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:          selector2._domainkey
Points to address or value: selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

### <a name="enable-dkim-signing-for-your-custom-domain-in-office-365"></a>Activation de la signature DKIM pour votre domaine personnalisé dans Office 365
<a name="EnableDKIMinO365"> </a>

Une fois que vous avez publié les enregistrements CNAME dans le système DNS, vous êtes prêt à activer la signature DKIM par l’intermédiaire d’Office 365. Vous pouvez effectuer cette action par le biais du Centre d’administration Microsoft 365 ou à l’aide de PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-through-the-admin-center"></a>Activation de la signature DKIM pour votre domaine personnalisé par l’intermédiaire du Centre d’administration

1. [Connectez-vous à Office 365](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) à l’aide de votre compte professionnel ou scolaire.

2. Sélectionnez l’icône du lanceur d’applications située en haut à gauche et choisissez **Administrateur**.

3. Dans le volet de navigation en bas à gauche, développez **Administrateur** et choisissez **Exchange**.

4. Accédez à **Protection** > \>dkim**.

5. Sélectionnez le domaine pour lequel vous souhaitez activer DKIM, puis pour **Signer les messages pour ce domaine avec des signatures DKIM**, choisissez **Activer**. Répétez cette étape pour chaque domaine personnalisé.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Activation de la signature DKIM pour votre domaine personnalisé à l’aide de PowerShell

1. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

2. Exécutez la commande suivante :

    ```powershell
    Set-DkimSigningConfig -Identity <domain> -Enabled $true
    ```

   Où _domain_ est le nom du domaine personnalisé pour lequel vous souhaitez activer la signature DKIM.

   Par exemple, pour le domaine contoso.com :

    ```powershell
    Set-DkimSigningConfig -Identity contoso.com -Enabled $true
    ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-office-365"></a>Confirmation du fait que la signature DKIM est correctement configurée pour Office 365

Patientez quelques minutes avant de suivre ces étapes permettant de confirmer que vous avez correctement configuré DKIM. Cela donne le temps aux informations DKIM relatives au domaine de se propager dans l’ensemble du réseau.

- Envoyez un message à partir d’un compte au sein de votre domaine Office 365 compatible avec DKIM à un autre compte de messagerie, tel qu’outlook.com ou Hotmail.com.

- N’utilisez pas un compte aol.com à des fins de test. Il est possible qu’AOL ignore la vérification DKIM si la vérification SPF aboutit. Cela annule votre test.

- Ouvrez le message et examinez l’en-tête. Les instructions pour afficher l’en-tête du message varient en fonction de votre client de messagerie. Pour obtenir des instructions sur l’affichage des en-têtes de messages dans Outlook, consultez l’article [](https://support.office.com/article/CD039382-DC6E-4264-AC74-C048563D212C)Afficher des en-têtes de messages électroniqueshttps://support.office.com/article/CD039382-DC6E-4264-AC74-C048563D212C.

  Le message signé par DKIM contient le domaine et le nom d’hôte que vous avez définis lorsque vous avez publié les entrées CNAME. Le message se présente un peu comme cet exemple :

  ```text
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Recherchez l’en-tête des résultats de l’authentification. Bien que chaque service de réception utilise un format légèrement différent pour apposer un cachet sur le courrier entrant, le résultat doit inclure un élément qui ressemble à **DKIM=test** ou **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain-in-office-365"></a>Configuration de DKIM pour plusieurs domaines personnalisés dans Office 365
<a name="DKIMMultiDomain"> </a>

Si un jour vous décidez d’ajouter un autre domaine personnalisé et que vous souhaitez activer DKIM pour ce nouveau domaine, vous devez effectuer les étapes décrites dans cet article pour chaque domaine. Plus spécifiquement, réalisez toutes les étapes indiquées dans la section [Configuration manuelle de DKIM dans Office 365](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain-in-office-365"></a>Désactivation de la stratégie de signature DKIM pour un domaine personnalisé dans Office 365
<a name="DisableDKIMSigningPolicy"> </a>

La désactivation de la stratégie de signature ne désactive pas complètement DKIM. Après un certain temps, Office 365 applique automatiquement la stratégie Office 365 par défaut pour votre domaine. Pour plus d’informations, voir [Comportement par défaut pour Exchange Online Protection (EOP) et Office 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Pour désactiver la stratégie de signature DKIM à l’aide de Windows PowerShell

1. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

2. Exécutez l’une des commandes suivantes pour chaque domaine pour lequel vous souhaitez désactiver la signature DKIM.

    ```powershell
    $p = Get-DkimSigningConfig -Identity <domain>
    $p[0] | Set-DkimSigningConfig -Enabled $false
    ```

   Par exemple :

    ```powershell
    $p = Get-DkimSigningConfig -Identity contoso.com
    $p[0] | Set-DkimSigningConfig -Enabled $false
    ```

   Ou

    ```powershell
    Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
    ```

    Où _number_ est l’index de la stratégie. Par exemple :

    ```powershell
    Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
    ```

## <a name="default-behavior-for-dkim-and-office-365"></a>Comportement par défaut pour DKIM et Office 365
<a name="DefaultDKIMbehavior"> </a>

Si vous n’activez pas DKIM, Office 365 crée automatiquement une clé publique DKIM 1024 bits pour votre domaine par défaut et la clé privée associée que nous stockons en interne dans notre centre de données. Par défaut, Office 365 utilise une configuration de signature par défaut pour les domaines ne disposant d’aucune stratégie définie. Cela signifie que si vous ne configurez pas DKIM vous-même, Office 365 utilise sa stratégie par défaut et les clés qu’il crée pour activer DKIM sur votre domaine.

En outre, si vous désactivez la signature DKIM, après un certain temps, Office 365 applique automatiquement sa stratégie par défaut pour votre domaine.

Dans l’exemple suivant, supposons que DKIM pour fabrikam.com a été activé par Office 365 et pas par l’administrateur du domaine. Cela signifie que les enregistrements CNAME requis n’existent pas dans le système DNS. Les signatures DKIM pour les courriers électroniques provenant de ce domaine se présenteront comme suit :

```text
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

Dans cet exemple, le domaine et le nom d’hôte contiennent les valeurs vers lesquelles l’enregistrement CNAME pointerait si la signature DKIM pour fabrikam.com avait été activée par l’administrateur du domaine. Au bout d’un certain temps, chaque message envoyé à partir d’Office 365 comportera une signature DKIM. Si vous activez DKIM vous-même, le domaine est identique à celui de l’adresse de l’expéditeur, ici fabrikam.com. Dans le cas contraire, DKIM ne s’aligne pas et utilise le domaine initial de votre organisation. Pour plus d’informations sur la façon de déterminer votre domaine initial, consultez la rubrique [](https://docs.microsoft.com/office365/admin/setup/domains-faq#why-do-i-have-an-onmicrosoftcom-domain)Forum aux questions sur les domaineshttps://support.office.com/fr-fr/article/Domains-FAQ-1272bad0-4bd4-4796-8005-67d6fb3afc5a#bkmk_whydoihaveanonmicrosoft.comdomain.

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Configurer DKIM de sorte qu’un service tiers puisse envoyer du courrier au nom de votre domaine personnalisé
<a name="SetUp3rdPartyspoof"> </a>

Certains fournisseurs de services de messagerie en masse ou de services SaaS vous permettent de configurer des clés DKIM pour les courriers électroniques qui proviennent de leur service. Cela requiert une coordination entre vous-même et le tiers pour configurer les enregistrements DNS nécessaires. Aucune organisation ne le fait exactement de la même manière que les autres. Ainsi, le processus dépend entièrement de l’organisation.

Un exemple de message montrant un élément DKIM configuré correctement pour contoso.com et bulkemailprovider.com peut se présenter comme suit :

```text
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

Dans cet exemple, pour obtenir ce résultat :

1. Le fournisseur de messagerie en masse a attribué à Contoso une clé DKIM publique.

2. Contoso a publié la clé DKIM sur son enregistrement DNS.

3. Lorsque de l’envoi de courrier électronique, le fournisseur de messagerie en masse signe la clé avec la clé privée correspondante. Ainsi, le fournisseur de messagerie en masse joint la signature DKIM à l’en-tête du message.

4. Les systèmes de messagerie de réception effectuent une vérification DKIM en authentifiant la valeur d=<domaine> de l’option DKIM-Signature, en la comparant au domaine indiqué dans l’adresse From: (5322.From) du message. Dans cet exemple, les valeurs sont les mêmes :

    sender@**contoso.com**

    d=**contoso.com**

## <a name="next-steps-after-you-set-up-dkim-for-office-365"></a>Étapes suivantes : après avoir configuré DKIM pour Office 365
<a name="DKIMNextSteps"> </a>

Bien que DKIM soit conçu pour éviter l’usurpation, DKIM fonctionne mieux avec SPF et DMARC. Une fois que vous avez configuré DKIM, si vous n’avez pas encore configuré SPF, vous devez le faire. Pour consulter une brève présentation de SPF et le configurer rapidement, voir [Configurer SPF dans Office 365 pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Pour consulter des informations plus approfondies sur l’utilisation de SPF par Office 365, la résolution des problèmes et les déploiements non standard tels que les déploiements hybrides, voir Comment Office 365 utilise SPF (Sender Policy Framework) pour empêcher l’usurpation d’identité. voir Utiliser DMARC pour valider les e-mails dans Office 365. [ comprend la syntaxe et les champs d’en-tête utilisés par Office 365 pour les vérifications DMARC.
