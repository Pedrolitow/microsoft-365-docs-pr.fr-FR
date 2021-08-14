---
title: Configurer SPF pour empêcher l’usurpation
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment mettre à jour un enregistrement DNS (service de nom de domaine) afin que vous puissiez utiliser SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d5677d8840226551d31e8f846f8763bcee85c19acd79535939d1688083b5e176
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53810185"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Configurer SPF pour empêcher l’usurpation

- [Conditions préalables](#prerequisites)
- [Ajouter ou mettre à jour votre enregistrement TXT SPF](#create-or-update-your-spf-txt-record)
- [Comment gérer les sous-domaines ?](#how-to-handle-subdomains)
- [Résolution des problèmes SPF](#troubleshooting-spf)

<!--
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

Cet article vous explique comment mettre à jour un enregistrement DNS (Domain Name Service) afin que vous puissiez utiliser l’authentification de messagerie SPF (Sender Policy Framework) avec votre domaine personnalisé dans Office 365.

Le SPF permet de *valider* les messages sortants envoyés à partir de votre domaine personnalisé (provenant de la personne qui la dit). Il s’agit d’une première étape de la configuration des méthodes d’authentification complètes recommandées pour le courrier électronique de SPF, [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md).

- [Conditions préalables](#prerequisites)
- [Ajouter ou mettre à jour votre enregistrement TXT SPF](#create-or-update-your-spf-txt-record)
  - [Comment gérer les sous-domaines ?](#how-to-handle-subdomains)
- [Comment fonctionne l’authentification de messagerie SPF ?](#what-does-spf-email-authentication-actually-do)
  - [Résolution des problèmes SPF](#troubleshooting-spf)
- [En savoir plus sur SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Configuration requise

> [!IMPORTANT]
> Si vous êtes une **petite entreprise** ou que vous ne connaissez pas les adresses IP ou la configuration DNS, appelez votre bureau d’enregistrement de domaines Internet (par exemple GoDaddy, Bluehost, web.com) et demander de l’aide sur la *configuration DNS de SPF* (et toute autre méthode d’authentification des e-mails) . <p> **Si vous n'utilisez pas d'URL personnalisé** (et que l’URL utilisée pour Office 365 se termine par **onmicrosoft.com**), SPF a déjà été installé pour vous dans le service Office 365.

C’est parti !

L’enregistrement TXT SPF pour Office 365 sera effectué dans le DNS externe pour tous les domaines ou sous-domaines personnalisés. Vous avez besoin d’informations pour effectuer l’enregistrement. Collectez les informations ci-dessous :

- L’enregistrement TXT SPF pour votre domaine personnalisé, le cas échéant. Si vous souhaitez obtenir des instructions, consultez l’article [Collectez les informations nécessaires pour créer des enregistrements DNS Office 365](../../admin/get-help-with-domains/information-for-dns-records.md).

- Accédez à vos serveurs de messagerie et recherchez les adresses IP externes (requis pour tous les serveurs de messagerie locaux). Par exemple, **131.107.2.200**.

- Les noms de domaine à utiliser pour tous les domaines de tiers que vous devez inclure dans votre enregistrement TXT SPF. Certains fournisseurs de messagerie en bloc disposent de sous-domaines configurés que leurs clients peuvent utiliser. Par exemple, la société MailChimp a configuré **servers.mcsv.net**.

- Déterminez quelle règle de mise en œuvre vous souhaitez utiliser pour votre enregistrement TXT SPF. La règle **-all** est recommandée. Si vous souhaitez obtenir plus d’informations sur les autres options de syntaxe, consultez l’article [Syntaxe d’enregistrement TXT SPF pour Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Afin d'utiliser un domaine personnalisé, Office 365 exige que vous ajoutiez un enregistrement TXT SPF (Sender Policy Framework) à votre enregistrement DNS pour éviter l'usurpation.

## <a name="create-or-update-your-spf-txt-record"></a>Ajouter ou mettre à jour votre enregistrement TXT SPF

1. Assurez-vous que vous connaissez la syntaxe SPF du tableau suivant.

   ****

   |Élément|Si vous utilisez...|Courant pour les utilisateurs ?|Ajoutez l’élément suivant...|
   |---|---|---|---|
   |1|Un système de messagerie (obligatoire)|Courant. Tous les enregistrements TXT SPF commencent avec cette valeur|`v=spf1`|
   |2|Exchange Online|Courant|`include:spf.protection.outlook.com`|
   |3|Exchange Online dédié uniquement|Non courant|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
   |4|Office 365 Germany, Microsoft Cloud Germany uniquement|Non courant|`include:spf.protection.outlook.de`|
   |5|Système de messagerie tiers|Non courant|`include:<domain_name>` <p> \<domain_name\> est le domaine du système de messagerie tiers.|
   |6|Système de messagerie en local. Par exemple, Exchange Online Protection et un autre système de messagerie|Non courant|Utilisez l’un des éléments suivants pour chaque système de messagerie supplémentaire : <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> et \<domain_name\> sont l’adresse IP et le domaine de l’autre système de messagerie qui envoie des e-mails au nom de votre domaine.|
   |7|Un système de messagerie (obligatoire)|Courant. Tous les enregistrements TXT SPF se terminent par cette valeur|`<enforcement rule>` <p> Il peut s’agir de plusieurs valeurs. Nous recommandons la valeur `-all`.|
   |

2. Si vous ne l’avez pas encore fait, créez votre enregistrement TXT SPF à l’aide de la syntaxe du tableau.

   Par exemple, si vous êtes entièrement hébergé par Office 365, ce qui signifie que vous n’avez aucun serveur de messagerie local, votre enregistrement TXT SPF inclut les lignes 1, 2 et 7 et se présente comme suit :

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **L’exemple ci-dessus est l’enregistrement TXT SPF le plus courant**. Cet enregistrement fonctionne pratiquement dans tous les cas, peu importe que votre centre de données Microsoft se trouve aux États-Unis, en Europe (y compris en Allemagne) ou dans une autre région.

   Cependant, si vous avez acheté Office 365 Allemagne, qui fait partie de Microsoft Cloud Allemagne, vous devez utiliser l'instruction include de la ligne 4 au lieu de la ligne 2. Par exemple, si vous êtes entièrement hébergé dans Office 365 Allemagne, c'est-à-dire que vous n'avez pas de serveurs de messagerie sur site, votre enregistrement TXT SPF inclurait les lignes 1, 4 et 7 et se présente comme suit :

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Si vous avez déjà effectué un déploiement dans Office 365, que vous avez configuré les enregistrements TXT SPF de votre domaine personnalisé et que vous effectuez une migration vers Office 365 Germany, vous devez mettre à jour votre enregistrement TXT SPF. Pour ce faire, remplacez `include:spf.protection.outlook.com` par `include:spf.protection.outlook.de`.

3. Une fois que vous avez formulé votre enregistrement TXT SPF, vous devez mettre à jour l'enregistrement dans le système DNS. **Vous ne pouvez avoir qu'un seul enregistrement TXT SPF pour un domaine.** Si un enregistrement TXT SPF existe, au lieu d'ajouter un nouvel enregistrement, vous devez mettre à jour l'enregistrement existant. Accédez à [Créer des enregistrements DNS pour Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), puis sélectionnez le lien correspondant à votre hôte DNS.

4. Testez votre enregistrement TXT SPF.

## <a name="how-to-handle-subdomains"></a>Comment gérer les sous-domaines ?

Il est important de noter que *vous devez créer un enregistrement distinct pour chaque sous-domaine, car les sous-domaines n’héritent pas de l’enregistrement SPF de leur domaine de premier niveau*.

Un enregistrement SPF (`*.`) est requis pour chaque domaine et sous-domaine afin d’empêcher les agresseurs d’envoyer des revendications de courrier électronique à partir de sous-domaines non existants. Par exemple :

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Résolution des problèmes SPF

Vous rencontrez des problèmes avec votre enregistrement TXT SPF ? Lisez [Résolution des problèmes : meilleures pratiques pour SPF dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Comment fonctionne l’authentification de messagerie SPF ?

SPF identifie les serveurs de messagerie qui sont autorisés à envoyer des messages en votre nom. En bref, SPF, ainsi que DKIM, DMARC et d’autres technologies prises en charge par Office 365, permettent d’éviter l’usurpation et le hameçonnage. SPF est ajouté sous la forme d’un enregistrement TXT qui est utilisé par le système DNS afin d’identifier les serveurs de messagerie autorisés à envoyer des messages au nom de votre domaine personnalisé. Les systèmes de messagerie électronique des destinataires peuvent se reporter à l’enregistrement TXT SPF pour déterminer si un message provenant de votre domaine personnalisé a été envoyé à partir d’un serveur de messagerie autorisé.

Par exemple, supposons que votre domaine personnalisé contoso.com utilise Office 365. Vous ajoutez un enregistrement TXT SPF qui répertorie les serveurs de messagerie Office 365 en tant que serveurs de messagerie légitimes pour votre domaine. Lorsque le serveur de messagerie de réception reçoit un message de la part de joe@contoso.com, le serveur recherche l’enregistrement TXT SPF pour contoso.com et détermine si le message est valide. Si le serveur de réception détecte que le message provient d’un serveur autre que les serveurs de messagerie Office 365 répertoriés dans l’enregistrement SPF, le serveur de messagerie de réception peut choisir de refuser le message en le marquant comme du courrier indésirable.

En outre, si votre domaine personnalisé ne dispose pas d’un enregistrement TXT SPF, certains serveurs de réception peuvent totalement rejeter le message. En effet, le serveur de réception ne peut pas valider le fait que le message provient d’un serveur de messagerie autorisé.

Si vous avez déjà configuré les messages pour Office 365, vous avez déjà inclus les serveurs de messagerie de Microsoft dans le système DNS sous la forme d’un enregistrement TXT SPF. Toutefois, il existe certains cas où vous devez mettre à jour votre enregistrement TXT SPF dans le système DNS. Par exemple :

- Auparavant, vous deviez ajouter un autre enregistrement TXT SPF à votre domaine personnalisé, si vous utilisiez SharePoint Online. Cela n'est plus nécessaire. Ce changement doit réduire le risque que les messages de notification SharePoint Online terminent dans le dossier Courrier indésirable. Mettez votre enregistrement TXT SPF à jour si vous avez atteint la limite de 10 recherches et recevez des erreurs de type « Vous avez dépassé la limite de recherche » et « Trop de sauts ».

- Vous avez un environnement hybride avec Office 365 et Exchange en local.

- Vous avez l’intention de configurer DKIM et DMARC (recommandé).

## <a name="more-information-about-spf"></a>En savoir plus sur SPF

Pour obtenir des exemples avancés, des informations plus détaillées sur la syntaxe SPF prise en charge, l’usurpation, la résolution des problèmes et la façon dont Office 365 prend en charge SPF, voir la section [Fonctionnement de SPF pour éviter l’usurpation et le hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Étapes suivantes : DKIM et DMARC

 SPF est conçu pour lutter contre l’usurpation, mais il existe des techniques d’usurpation contre lesquelles SPF ne peut rien faire. Pour vous protéger contre ces techniques, une fois que vous avez configuré SPF, vous devez également configurer DKIM et DMARC pour Office 365.

L’objectif de l’authentification de messagerie [DKIM](use-dkim-to-validate-outbound-email.md) est de prouver que le contenu du courrier n’a pas été falsifié.

L’objectif de l’authentification de messagerie [DMARC](use-dmarc-to-validate-email.md) est de s’assurer que les informations SPF et DKIM correspondent à l’adresse de l’expéditeur.

 Si vous souhaitez obtenir des exemples avancés et des informations plus détaillées sur la syntaxe SPF prise en charge, consultez l’article [Fonctionnement de SPF contre l’usurpation et l’hameçonnage dans Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

*Sélectionnez « Cette page » sous « Commentaires » si vous avez des commentaires sur cette documentation.*
