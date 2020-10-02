---
title: Configurer SPF pour empêcher l’usurpation
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment mettre à jour un enregistrement DNS (service de nom de domaine) afin que vous puissiez utiliser SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.
ms.openlocfilehash: e53facc12ed8ad2b702d2d0514aebe0068c097b7
ms.sourcegitcommit: 61ef32f802a1fb6d1e3a3aa005764ead32a7951e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48318183"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Configurer SPF pour empêcher l’usurpation

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

 **Résumé :** Cet article explique comment mettre à jour un enregistrement DNS (Domain Name Service) afin que vous puissiez utiliser le SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365. L'utilisation de SPF permet de valider les messages sortants envoyés à partir de votre domaine personnalisé.

Afin d’utiliser un domaine personnalisé, Office 365 exige l’ajout d’un enregistrement TXT SPF (Sender Policy Framework) à votre enregistrement DNS pour éviter l’usurpation. SPF identifie les serveurs de messagerie qui sont autorisés à envoyer des messages en votre nom. En bref, SPF, ainsi que DKIM, DMARC et d’autres technologies prises en charge par Office 365, permettent d’éviter l’usurpation et le hameçonnage. SPF est ajouté sous la forme d’un enregistrement TXT qui est utilisé par le système DNS afin d’identifier les serveurs de messagerie autorisés à envoyer des messages au nom de votre domaine personnalisé. Les systèmes de messagerie électronique des destinataires peuvent se reporter à l’enregistrement TXT SPF pour déterminer si un message provenant de votre domaine personnalisé a été envoyé à partir d’un serveur de messagerie autorisé.

Par exemple, supposons que votre domaine personnalisé contoso.com utilise Office 365. Vous ajoutez un enregistrement TXT SPF qui répertorie les serveurs de messagerie Office 365 en tant que serveurs de messagerie légitimes pour votre domaine. Lorsque le serveur de messagerie de réception reçoit un message de la part de joe@contoso.com, le serveur recherche l’enregistrement TXT SPF pour contoso.com et détermine si le message est valide. Si le serveur de réception détecte que le message provient d’un serveur autre que les serveurs de messagerie Office 365 répertoriés dans l’enregistrement SPF, le serveur de messagerie de réception peut choisir de refuser le message en le marquant comme du courrier indésirable.

En outre, si votre domaine personnalisé ne dispose pas d’un enregistrement TXT SPF, certains serveurs de réception peuvent totalement rejeter le message. En effet, le serveur de réception ne peut pas valider le fait que le message provient d’un serveur de messagerie autorisé.

Si vous avez déjà configuré les messages pour Office 365, vous avez déjà inclus les serveurs de messagerie de Microsoft dans le système DNS sous la forme d’un enregistrement TXT SPF. Toutefois, il existe certains cas où vous devez mettre à jour votre enregistrement TXT SPF dans le système DNS. Par exemple :

- Auparavant, vous deviez ajouter un autre enregistrement TXT SPF à votre domaine personnalisé, si vous utilisiez SharePoint Online. Cela n'est plus nécessaire. Ce changement doit réduire le risque que les messages de notification SharePoint Online terminent dans le dossier Courrier indésirable. Mettez votre enregistrement TXT SPF à jour si vous avez atteint la limite de 10 recherches et recevez des erreurs de type « Vous avez dépassé la limite de recherche » et « Trop de sauts ».

- Vous avez un environnement hybride avec Office 365 et Exchange en local.

- Vous avez l’intention de configurer DKIM et DMARC (recommandé).

## <a name="updating-your-spf-txt-record-for-office-365"></a>Mise à jour de votre enregistrement TXT SPF pour Office 365

Avant de mettre à jour l’enregistrement TXT dans le système DNS, vous devez rassembler quelques informations et déterminer le format de l’enregistrement. Cela vous permettra d’éviter de générer des erreurs DNS. Pour obtenir des exemples avancés et des informations plus détaillées sur la syntaxe SPF prise en charge, voir la section [Fonctionnement de SPF pour éviter l’usurpation et le hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

Collectez les informations ci-dessous :

- L'enregistrement TXT SPF actuel pour votre domaine personnalisé. Pour obtenir des instructions, consultez [Recueillez les informations nécessaires pour créer des enregistrements DNS Office 365](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/information-for-dns-records).

- Les adresses IP externes de tous les serveurs de messagerie locaux. Par exemple, **131.107.2.200**.

- Les noms de domaine à utiliser pour tous les domaines de tiers que vous devez inclure dans votre enregistrement TXT SPF. Certains fournisseurs de messagerie en bloc disposent de sous-domaines configurés que leurs clients peuvent utiliser. Par exemple, la société MailChimp a configuré **servers.mcsv.net**.

- La règle de mise en œuvre que vous souhaitez utiliser pour votre enregistrement TXT SPF. Nous vous recommandons **-all**. Pour plus d’informations sur les autres options de syntaxe, voir [Syntaxe d’enregistrement TXT SPF pour Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

### <a name="to-add-or-update-your-spf-txt-record"></a>Pour ajouter ou mettre à jour votre enregistrement TXT SPF

1. Assurez-vous que vous connaissez la syntaxe SPF du tableau suivant.

   ****

   |Élément|Si vous utilisez...|Courant pour les utilisateurs ?|Ajoutez l’élément suivant...|
   |---|---|---|---|
   |1|Un système de messagerie (obligatoire)|Courant. Tous les enregistrements TXT SPF commencent avec cette valeur|`v=spf1`|
   |2|Exchange Online|Courant|`include:spf.protection.outlook.com`|
   |3|Exchange Online dédié uniquement|Non courant|`ip4:23.103.224.0/19 ip4:206.191.224.0/19 ip4:40.103.0.0/16 include:spf.protection.outlook.com`|
   |4|Office 365 Germany, Microsoft Cloud Germany uniquement|Non courant|`include:spf.protection.outlook.de`|
   |5|Système de messagerie tiers|Non courant|`include:<domain_name>`  <br/> Où \<domain_name\> est le domaine du système de messagerie tiers.|
   |6|Système de messagerie en local. Par exemple, Exchange Online Protection et un autre système de messagerie|Non courant|Utilisez l’un des éléments suivants pour chaque système de messagerie supplémentaire : <br> `ip4:<IP_address>` <br/> `ip6:<IP_address>` <br/> `include:<domain_name>` <br/> Où \<IP_address\> et \<domain_name\> sont l’adresse IP et le domaine de l’autre système de messagerie qui envoie des e-mails au nom de votre domaine.|
   |7|Un système de messagerie (obligatoire)|Courant. Tous les enregistrements TXT SPF se terminent par cette valeur|`<enforcement rule>` <br/> Il peut s’agir de plusieurs valeurs. Nous recommandons la valeur « -all ».|
   |

2. Si vous ne l’avez pas encore fait, créez votre enregistrement TXT SPF à l’aide de la syntaxe du tableau.

   Par exemple, si vous êtes entièrement hébergé par Office 365, ce qui signifie que vous n’avez aucun serveur de messagerie local, votre enregistrement TXT SPF inclut les lignes 1, 2 et 7 et se présente comme suit :

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   Il s’agit de l’enregistrement TXT SPF le plus courant. Cet enregistrement fonctionne pratiquement dans tous les cas, peu importe que votre centre de données Microsoft se trouve aux États-Unis, en Europe (y compris en Allemagne) ou dans une autre région.

   Toutefois, si vous avez acheté Office 365 Germany, un composant de Microsoft Cloud Germany, vous devez utiliser l’instruction Include de la ligne 4 au lieu de celle de la ligne 2. Par exemple, si vous êtes entièrement hébergé par Office 365 Germany, ce qui signifie que vous n’avez aucun serveur de messagerie local, votre enregistrement TXT SPF inclut les lignes 1, 4 et 7 et se présente comme suit :

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Si vous avez déjà effectué un déploiement dans Office 365, que vous avez configuré les enregistrements TXT SPF de votre domaine personnalisé et que vous effectuez une migration vers Office 365 Germany, vous devez mettre à jour votre enregistrement TXT SPF. Pour ce faire, remplacez `include:spf.protection.outlook.com` par `include:spf.protection.outlook.de`.

3. Une fois que vous avez formulé votre enregistrement TXT SPF, vous devez mettre à jour l'enregistrement dans le système DNS. Vous ne pouvez avoir qu'un seul enregistrement TXT SPF pour un domaine. Si un enregistrement TXT SPF existe, au lieu d'ajouter un nouvel enregistrement, vous devez mettre à jour l'enregistrement existant. Accédez à [Créer des enregistrements DNS pour Office 365](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), puis cliquez sur le lien correspondant à votre hôte DNS.

4. Testez votre enregistrement TXT SPF.

## <a name="how-to-handle-subdomains"></a>Comment gérer les sous-domaines ?

Il est important de noter que vous devez créer un enregistrement distinct pour chaque sous-domaine, car les sous-domaines n’héritent pas de l’enregistrement SPF de leur domaine de premier niveau.

Un enregistrement SPF (`*.`) supplémentaire est requis pour chaque domaine et sous-domaine afin d’empêcher les agresseurs d’envoyer des revendications de courrier électronique à partir de sous-domaines non existants. Par exemple :

```text
*.subdomain.contoso.com. IN TXT "v=spf1 –all"
```

## <a name="more-information-about-spf"></a>En savoir plus sur SPF

Pour obtenir des exemples avancés, des informations plus détaillées sur la syntaxe SPF prise en charge, l’usurpation, la résolution des problèmes et la façon dont Office 365 prend en charge SPF, voir la section [Fonctionnement de SPF pour éviter l’usurpation et le hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-after-you-set-up-spf-for-office-365"></a>Étapes suivantes : après avoir configuré SPF pour Office 365

Vous rencontrez des problèmes avec votre enregistrement TXT SPF ? Lisez [Résolution des problèmes : meilleures pratiques pour SPF dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

 SPF est conçu pour éviter l'usurpation mais il existe des techniques d'usurpation contre lesquelles SPF ne peut pas vous protéger. Afin de vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Office 365. Consultez [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md) pour commencer. Ensuite, consultez la rubrique [Utiliser DMARC pour valider les e-mails dans Office 365](use-dmarc-to-validate-email.md).
