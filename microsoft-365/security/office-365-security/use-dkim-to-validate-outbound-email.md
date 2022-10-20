---
title: Utiliser DKIM pour le courrier électronique dans votre domaine personnalisé
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment utiliser DKIM (DomainKeys Identified Mail) avec Microsoft 365 pour vous assurer que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine personnalisé.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 31eca37a3fa2b8fd47ad2628f940b4938c34c509
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640013"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Cet article répertorie les étapes de l’utilisation de DomainKeys Identified Mail (DKIM) avec Microsoft 365 pour vous assurer que les systèmes d’e-mail de destination approuvent les messages sortants envoyés à partir de votre domaine personnalisé.

Contenu de cet article :

- [Pourquoi DKIM est plus efficace que SPF seul pour empêcher l’usurpation d’identité malveillante](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Étapes pour Créer, activer et désactiver DKIM à partir du portail Microsoft 365 Defender](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [Procédure de mise à niveau manuelle de vos clés 1024 bits vers les clés de chiffrement DKIM 2048 bits](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [Étapes de la configuration manuelle de DKIM](#steps-to-manually-set-up-dkim)
- [Étapes de configuration de DKIM pour plusieurs domaines personnalisés](#to-configure-dkim-for-more-than-one-custom-domain)
- [Désactivation de la stratégie de signature DKIM pour un domaine personnalisé](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [Comportement par défaut pour DKIM et Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- Configuration de DKIM permettant à un service tiers d’envoyer des courriers électroniques au nom de votre domaine personnalisé, ou d’usurper ce dernier
- [Étapes suivantes : après avoir configuré DKIM pour Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 configure automatiquement DKIM pour les domaines initiaux 'onmicrosoft.com'. Cela signifie que vous n’avez rien à faire pour configurer DKIM pour les noms de domaine initial (par exemple, litware.onmicrosoft.com). Pour plus d'informations sur les domaines, consultez l'article [Forum aux questions sur les domaines](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM fait partie du trio de méthodes d'authentification (SPF, DKIM et DMARC) qui permet d'empêcher les attaquants d'envoyer des messages qui semblent provenir de votre domaine.

DKIM lets you add a digital signature to outbound email messages in the message header. When you configure DKIM, you authorize your domain to associate, or sign, its name to an email message using cryptographic authentication. Email systems that get email from your domain can use this digital signature to help verify whether incoming email is legitimate.

À la base, une clé privée chiffre l’en-tête dans le courrier sortant d’un domaine. La clé publique est publiée dans les enregistrements DNS, et les serveurs de réception peuvent utiliser cette clé pour décoder la signature. La vérification DKIM permet aux serveurs de réception de confirmer que les courriers viennent vraiment de votre domaine et non d’une personne *usurpant* votre domaine.

> [!TIP]
>You can choose to do nothing about DKIM for your custom domain too. If you don't set up DKIM for your custom domain, Microsoft 365 creates a private and public key pair, enables DKIM signing, and then configures the Microsoft 365 default policy for your custom domain.

 Microsoft-365's built-in DKIM configuration is sufficient coverage for most customers. However, you should manually configure DKIM for your custom domain in the following circumstances:

- Vous avez plusieurs domaines personnalisés dans Microsoft 365
- Vous allez également configurer DMARC (**recommandé**)
- Vous souhaitez contrôler votre clé privée
- Vous souhaitez personnaliser vos enregistrements CNAME
- Vous souhaitez configurer des clés DKIM pour les e-mails provenant d’un domaine tiers, par exemple, si vous utilisez un programme d’envoi de courrier en nombre tiers.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Pourquoi DKIM est plus efficace que SPF seul pour empêcher l’usurpation d’identité malveillante
<a name="HowDKIMWorks"> </a>

SPF adds information to a message envelope but DKIM *encrypts* a signature within the message header. When you forward a message, portions of that message's envelope can be stripped away by the forwarding server. Since the digital signature stays with the email message because it's part of the email header, DKIM works even when a message has been forwarded as shown in the following example.

![Diagramme illustrant l'authentification DKIM correcte d'un message transféré lors de l'échec du contrôle SPF](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

In this example, if you had only published an SPF TXT record for your domain, the recipient's mail server could have marked your email as spam and generated a false positive result. **The addition of DKIM in this scenario reduces *false positive* spam reporting.** Because DKIM relies on public key cryptography to authenticate and not just IP addresses, DKIM is considered a much stronger form of authentication than SPF. We recommend using both SPF and DKIM, as well as DMARC in your deployment.

> [!TIP]
> DKIM uses a private key to insert an encrypted signature into the message headers. The signing domain, or outbound domain, is inserted as the value of the **d=** field in the header. The verifying domain, or recipient's domain, then uses the **d=** field to look up the public key from DNS, and authenticate the message. If the message is verified, the DKIM check passes.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Étapes de création, d’activation et de désactivation de DKIM à partir du Portail Microsoft 365 Defender

Tous les domaines acceptés de votre locataire s’affichent dans le portail Microsoft 365 Defender sous la page DKIM. Si vous ne le voyez pas, ajoutez votre domaine accepté à partir de la [page domaines](/microsoft-365/admin/setup/add-domain#add-a-domain).
Une fois votre domaine ajouté, suivez les étapes ci-dessous pour configurer DKIM.

Étape 1 : cliquer sur le domaine sur lequel vous souhaitez configurer DKIM sur la page DKIM (https://security.microsoft.com/dkimv2 ou https://protection.office.com/dkimv2)).

:::image type="content" source="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png" alt-text="Page DKIM dans le portail Microsoft 365 Defender avec un domaine sélectionné" lightbox="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png":::

Étape 2 : faites glisser le bouton bascule pour **Activer**. Vous verrez une fenêtre contextuelle indiquant que vous devez ajouter des enregistrements CNAME.

:::image type="content" source="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png" alt-text="Menu volant Détails du domaine avec le bouton Créer des clés DKIM" lightbox="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png":::

Étape 3 : copier le CNAMES affiché dans la fenêtre contextuelle

:::image type="content" source="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png" alt-text="Fenêtre contextuelle Publier les noms de cluster qui contient les deux enregistrements CNAME à copier" lightbox="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png":::

Étape 4 : publier les enregistrements CNAME copiés sur votre fournisseur de services DNS.

Sur le site web de votre fournisseur DNS, ajoutez des enregistrements CNAME pour DKIM que vous souhaitez activer. Dans le nouvel enregistrement, vérifiez que chacun des champs sont définis par les valeurs suivantes :

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

Étape 5 : revenir à la page DKIM pour activer DKIM.

:::image type="content" source="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png" alt-text="Bouton bascule pour activer DKIM" lightbox="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png":::

Si vous voyez l'erreur L’enregistrement CNAME n'existe pas, cela peut être dû à :

1. Synchronisation avec le serveur DNS, ce qui peut prendre quelques secondes à quelques heures, si le problème persiste répétez les étapes
2. Recherchez les erreurs de copier-coller, telles que l’espace supplémentaire ou les onglets, etc.

Si vous souhaitez désactiver DKIM, basculez vers le mode Désactiver

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Mise à niveau manuelle de vos clés 1024 bits vers les clés de chiffrement DKIM 2048 bits
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 configure automatiquement DKIM pour les domaines *onmicrosoft.com*. Aucune étape n’est nécessaire pour utiliser DKIM pour les noms de domaine initiaux (par exemple, litware.*onmicrosoft.com*). Pour plus d'informations sur les domaines, consultez l'article [Forum aux questions sur les domaines](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Étant donné que le nombre de bits 1024 et 2048 sont pris en charge pour les clés DKIM, ces instructions vous indiquent comment mettre à niveau votre clé 1024 bits vers 2048 dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Les étapes ci-dessous concernent deux cas d’utilisation ; veuillez choisir celui qui correspond le mieux à votre configuration.

- Lorsque vous **avez déjà configuré DKIM**, vous pouvez faire pivoter le nombre de bits en exécutant la commande suivante :

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **ou**

- Pour une **nouvelle implémentation de la fonctionnalité DKIM**, exécutez la commande suivante :

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Restez connecté à Exchange Online PowerShell pour *vérifier* la configuration en exécutant la commande suivante :

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Cette nouvelle clé 2048 bits prend effet sur RotateOnDate et envoie des e-mails avec la clé 1024 bits au niveau intermédiaire. Après quatre jours, vous pouvez à nouveau effectuer un test à l’aide de la touche 2048 bits (autrement dit, une fois que la rotation prend effet sur le deuxième sélecteur).

Si vous souhaitez faire pivoter vers le deuxième sélecteur, après quatre jours et confirmer que le nombre de bits 2048 est en cours d’utilisation, faites pivoter manuellement la deuxième clé de sélecteur à l’aide de l’applet de commande appropriée répertoriée ci-dessus.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez les articles suivants : [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig)et [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>Étapes de la configuration manuelle de DKIM
<a name="SetUpDKIMO365"> </a>

Pour configurer DKIM, suivez les étapes ci-dessous :

- [Publication de deux enregistrements CNAME pour votre domaine personnalisé dans le système DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Activation de la signature DKIM pour votre domaine personnalisé](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publication de deux enregistrements CNAME pour votre domaine dans le système DNS
<a name="Publish2CNAME"> </a>

Pour chaque domaine auquel vous souhaitez ajouter une signature DKIM dans le système DNS, vous devez publier deux enregistrements CNAME.

> [!NOTE]
> Si vous n’avez pas lu l’intégralité de l’article, il est possible que vous ayez manqué les informations de connexion PowerShell qui vous ont été utiles : [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Exécutez les commandes suivantes dans Exchange Online PowerShell pour créer les enregistrements du sélecteur :

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

If you have provisioned custom domains in addition to the initial domain in Microsoft 365, you must publish two CNAME records for each additional domain. So, if you have two domains, you must publish two additional CNAME records, and so on.

Utilisez le format suivant pour les enregistrements CNAME.

> [!IMPORTANT]
> Si vous êtes l’un de nos clients GCC High, nous calculons _customDomainIdentifier_ différemment ! Au lieu de chercher l’enregistrement MX de votre _initialDomain_ pour calculer _customDomainIdentifier_, nous le calculons directement à partir du domaine personnalisé. Par exemple, si votre domaine personnalisé est « contoso.com » votre _customDomainIdentifier_ devient « contoso-com », tous les points sont remplacés par un tiret. Ainsi, quel que soit l’enregistrement MX vers lequel pointe votre _initialDomain_, vous utiliserez toujours la méthode ci-dessus pour calculer la _customDomainIdentifier_ à utiliser dans vos enregistrements CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Où :

- Pour Microsoft 365, les sélecteurs seront toujours « selector1 » ou « selector2 ».
- _customDomainIdentifier_ is the same as the _customDomainIdentifier_ in the customized MX record for your custom domain that appears before mail.protection.outlook.com. For example, in the following MX record for the domain contoso.com, the _customDomainIdentifier_ is contoso-com:

  > contoso.com.  3600  IN  MX   5 contoso-com.mail.protection.outlook.com

- _initialDomain_ is the domain that you used when you signed up for Microsoft 365. Initial domains always end in onmicrosoft.com. For information about determining your initial domain, see [Domains FAQ](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Par exemple, si vous avez un domaine initial cohovineyardandwinery.onmicrosoft.com, ainsi que deux domaines personnalisés cohovineyard.com et cohowinery.com, vous devez configurer deux enregistrements CNAME pour chaque domaine supplémentaire, soit un total de quatre enregistrements CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector1._domainkey
Points to address or value:    selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

> [!NOTE]
> Il est important de créer le deuxième enregistrement, mais il est possible qu’un seul sélecteur soit disponible au moment de la création. Par essence, le deuxième sélecteur peut pointer vers une adresse qui n’a pas encore été créée. Nous vous recommandons de créer le deuxième enregistrement CNAME, car la rotation de votre clé sera transparente.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Étapes d’activation de la signature DKIM pour votre domaine personnalisé
<a name="EnableDKIMinO365"> </a>

Once you have published the CNAME records in DNS, you are ready to enable DKIM signing through Microsoft 365. You can do this either through the Microsoft 365 admin center or by using PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Pour activer la signature DKIM pour votre domaine personnalisé dans le portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **E-mail et Collaboration**\>**Stratégies et règles**\>**Stratégies de menace**\>**Paramètres d’authentification d’e-mail** dans la section **Règles**\>**DKIM**. Pour accéder directement à la page DKIM, utilisez <https://security.microsoft.com/dkimv2>.

2. Dans la page **DKIM**, sélectionnez le domaine en cliquant sur le nom.

3. Dans le menu volant des détails qui s’affiche, changez le paramètre **Signer les messages pour ce domaine avec des signatures DKIM** à **Activé** (![Basculer sur.](../../media/scc-toggle-on.png))

   Lorsque vous avez terminé, cliquez sur **Rotation des clés DKIM**.

4. Répétez ces étapes pour chaque domaine personnalisé.

5. Si vous configurez DKIM pour la première fois et que vous voyez l’erreur « Aucune clé DKIM enregistrée pour ce domaine », vous devez utiliser Windows PowerShell pour activer la signature DKIM, comme expliqué à l’étape suivante.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Activation de la signature DKIM pour votre domaine personnalisé à l’aide de PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Aucune clé DKIM enregistrée pour cette erreur de domaine" lightbox="../../media/dkim.png":::
> Si vous configurez DKIM pour la première fois et que vous voyez l’erreur « Aucune clé DKIM enregistrée pour ce domaine », exécutez la commande à l’étape 2 ci-dessous (par exemple, `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`) pour afficher la clé.

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez la syntaxe suivante :

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> est le nom du domaine personnalisé pour lequel vous souhaitez activer la signature DKIM.

   Cet exemple permet d’activer la signature DKIM pour le domaine contoso.com :

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>Confirmation du fait que la signature DKIM est correctement configurée pour Microsoft 365

Wait a few minutes before you follow these steps to confirm that you have properly configured DKIM. This allows time for the DKIM information about the domain to be spread throughout the network.

- Envoyez un message à partir d’un compte au sein de votre domaine Microsoft 365 compatible avec DKIM à un autre compte de messagerie, tel qu’outlook.com ou Hotmail.com.
- Do not use an aol.com account for testing purposes. AOL may skip the DKIM check if the SPF check passes. This will nullify your test.
- Open the message and look at the header. Instructions for viewing the header for the message will vary depending on your messaging client. For instructions on viewing message headers in Outlook, see [View internet message headers in Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  The DKIM-signed message will contain the host name and domain you defined when you published the CNAME entries. The message will look something like this example:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Look for the Authentication-Results header. While each receiving service uses a slightly different format to stamp the incoming mail, the result should include something like **DKIM=pass** or **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>Configuration de DKIM pour plusieurs domaines personnalisés
<a name="DKIMMultiDomain"> </a>

If at some point in the future you decide to add another custom domain and you want to enable DKIM for the new domain, you must complete the steps in this article for each domain. Specifically, complete all steps in [What you need to do to manually set up DKIM](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Désactivation de la stratégie de signature DKIM pour un domaine personnalisé
<a name="DisableDKIMSigningPolicy"> </a>

La désactivation de la stratégie de signature ne désactive pas complètement DKIM. Au bout d’un certain temps, Microsoft 365 applique automatiquement la stratégie par défaut pour votre domaine, si la stratégie par défaut est toujours dans l’état activé. Si vous souhaitez désactiver complètement DKIM, vous devez désactiver DKIM sur les domaines personnalisés et par défaut. Pour plus d'informations, voir [Comportement par défaut pour DKIM et Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Pour désactiver la stratégie de signature DKIM à l’aide de Windows PowerShell

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’une des commandes suivantes pour chaque domaine pour lequel vous souhaitez désactiver la signature DKIM.

   ```powershell
   $p = Get-DkimSigningConfig -Identity <Domain>
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Par exemple :

   ```powershell
   $p = Get-DkimSigningConfig -Identity contoso.com
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Ou

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   Where _number_ is the index of the policy. For example:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>Comportement par défaut pour DKIM et Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

If you do not enable DKIM, Microsoft 365 automatically creates a 2048-bit DKIM public key for your Microsoft Online Email Routing Address (MOERA)/initial domain and the associated private key which we store internally in our datacenter. By default, Microsoft 365 uses a default signing configuration for domains that do not have a policy in place. This means that if you do not set up DKIM yourself, Microsoft 365 will use its default policy and keys it creates to enable DKIM for your domain.

En outre, si vous désactivez la signature DKIM sur votre domaine personnalisé après l’avoir activé, au bout d’un certain temps, Microsoft 365 applique automatiquement la stratégie de domaine MOERA/initiale pour votre domaine personnalisé.

In the following example, suppose that DKIM for fabrikam.com was enabled by Microsoft 365, not by the administrator of the domain. This means that the required CNAMEs do not exist in DNS. DKIM signatures for email from this domain will look something like this:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

In this example, the host name and domain contain the values to which the CNAME would point if DKIM-signing for fabrikam.com had been enabled by the domain administrator. Eventually, every single message sent from Microsoft 365 will be DKIM-signed. If you enable DKIM yourself, the domain will be the same as the domain in the From: address, in this case fabrikam.com. If you don't, it will not align and instead will use your organization's initial domain. For information about determining your initial domain, see [Domains FAQ](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Configurer DKIM de sorte qu’un service tiers puisse envoyer du courrier au nom de votre domaine personnalisé
<a name="SetUp3rdPartyspoof"> </a>

Some bulk email service providers, or software-as-a-service providers, let you set up DKIM keys for email that originates from their service. This requires coordination between yourself and the third-party in order to set up the necessary DNS records. Some third-party servers can have their own CNAME records with different selectors. No two organizations do it exactly the same way. Instead, the process depends entirely on the organization.

Un exemple de message montrant un élément DKIM configuré correctement pour contoso.com et bulkemailprovider.com peut se présenter comme suit :

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

Dans cet exemple, pour obtenir ce résultat :

1. Le fournisseur de messagerie en masse a attribué à Contoso une clé DKIM publique.

2. Contoso a publié la clé DKIM sur son enregistrement DNS.

3. When sending email, Bulk Email Provider signs the key with the corresponding private key. By doing so, Bulk Email Provider attached the DKIM signature to the message header.

4. Receiving email systems perform a DKIM check by authenticating the DKIM-Signature d=\<domain\> value against the domain in the From: (5322.From) address of the message. In this example, the values match:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>Identifier les domaines qui n’envoient pas de courrier électronique

Les organisations doivent indiquer de façon explicite si un domaine n’envoie pas de courrier électronique en spécifiant `v=DKIM1; p=` dans l’enregistrement DKIM de ces domaines. Cela indique aux serveurs de messagerie qu’il n’existe pas de clé publique valide pour le domaine, et que les courriers électroniques provenant de ce domaine doivent être rejetés. Vous devez procéder de la sorte pour chaque domaine et sous-domaine à l’aide d’un DKIM avec caractère générique.

Par exemple, l’enregistrement DKIM se présente comme suit :

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Étapes suivantes : après avoir configuré DKIM pour Microsoft 365
<a name="DKIMNextSteps"> </a>

**Bien que DKIM soit conçu pour éviter l’usurpation, DKIM fonctionne mieux avec SPF et DMARC.**

Once you have set up DKIM, if you have not already set up SPF you should do so. For a quick introduction to SPF and to get it configured quickly, see [**Set up SPF in Microsoft 365 to help prevent spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). For a more in-depth understanding of how Microsoft 365 uses SPF, or for troubleshooting or non-standard deployments such as hybrid deployments, start with [How Microsoft 365 uses Sender Policy Framework (SPF) to prevent spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

Next, see [**Use DMARC to validate email**](use-dmarc-to-validate-email.md). [Anti-spam message headers](anti-spam-message-headers.md) includes the syntax and header fields used by Microsoft 365 for DKIM checks.

**Ce test validera** que la configuration de signature DKIM a été correctement configurée et que les entrées DNS appropriées ont été publiées.

> [!NOTE]
> Cette fonctionnalité nécessite un compte administrateur Microsoft 365. Cette fonctionnalité nʼest pas disponible pour Microsoft 365 Secteur Public, Microsoft 365 géré par 21Vianet ou Microsoft 365 Allemagne.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Exécuter des tests : DKIM</a></p>
</div>

## <a name="more-information"></a>Plus d’informations

Rotation des clés via PowerShell : [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[Utiliser DMARC pour valider les messages électroniques](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Utiliser des expéditeurs ARC approuvés pour les flux de messagerie légitimes](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders)
