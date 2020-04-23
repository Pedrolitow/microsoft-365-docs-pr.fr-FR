---
title: En-têtes de messages anti-courrier indésirable
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 2e3fcfc5-5604-4b88-ac0a-c5c45c03f1db
ms.collection:
- M365-security-compliance
description: Apprenez-en davantage sur les champs et valeurs d’en-tête ajoutés aux messages par Exchange Online Protection.
ms.openlocfilehash: 1bb2468908ef9711242bdb236f7f43f9f6e43eb1
ms.sourcegitcommit: d4d082292dc711a579fe925ad989ea54ec2e27f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "43708582"
---
# <a name="anti-spam-message-headers"></a>En-têtes de messages anti-courrier indésirable

Lorsque Exchange Online Protection (EOP) analyse un message entrant, il insère l'en-tête **X-Forefront-Antispam-Report** dans chaque message. Les champs de cet en-tête permettent de fournir des informations aux administrateurs en ce qui concerne le message et sur la manière dont ce dernier a été traité. Les champs de l'en-tête **X-Microsoft-Antispam** fournissent des informations supplémentaires sur le courrier en nombre et le hameçonnage. En plus de ces deux en-têtes, Exchange Online Protection insère également les résultats de l'authentification d'e-mail pour chaque message qu'il traite dans l'en-tête **Authentication-results** (résultats de l'authentification).

Pour plus d’informations sur le mode d’affichage de l’en-tête d’un e-mail dans divers clients de messagerie, consultez [Afficher les en-têtes de messages Internet dans Outlook](https://support.office.com/article/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Vous pouvez copier et coller le contenu d’une en-tête de message dans l’[Analyseur de message](https://testconnectivity.microsoft.com/?tabid=mha). Cet outil aide à analyser les en-têtes et à les afficher dans un format plus lisible.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Champs d’en-tête de message X-Forefront-Antispam-Report

Après avoir accédé aux informations d’un en-tête de message, recherchez **X-Forefront-Antispam-Report**, puis recherchez les champs ci-dessous. Les autres champs de cet en-tête sont exclusivement utilisés par l’équipe Microsoft de lutte contre les courriers indésirables à des fins de diagnostic.

|||
|---|---|
|**Champ d’en-tête**|**Description**|
|ARC|Le protocole ARC inclut les en-têtes suivants : <ul><li>AAR : enregistre le contenu de l'en-tête Authentication results à partir de DMARC.</li><li>AMS : cet en-tête inclut les signatures de chiffrement du message.</li><li>AS : inclut les signature de chiffrement des en-têtes du message. Cet en-tête contient une balise de chaîne de validation appelée « cv= » incluant le résultat de la chaîne de validation en tant que **aucun**, **succès** ou **échec**.</li></ul>|
|CAT :|Catégorie de stratégie de protection appliquée au message : <ul><li>BULK : En bloc</li><li>DIMP : Emprunt d’identité de domaine</li><li>GIMP : veille des boîtes aux lettres</li><li>HPHSH ou HPHISH : hameçonnage haute confiance </li><li>HSPM : courrier fortement suspecté d’être indésirable</li><li>MALW : Programme malveillant</li><li>PHSH : Hameçonnage</li><li>SPM : courrier indésirable</li><li>SPOOF : usurpation d’identité</li><li>UIMP : emprunt d’identité d’utilisateur</li></ul><br/>Un message entrant peut être signalé par plusieurs formes de protection et plusieurs analyses de détection. Les stratégies ont des priorités différentes, et la stratégie ayant la priorité la plus élevée s'applique en premier. Pour plus d’informations, voir [Quelle stratégie s’applique lorsque plusieurs méthodes de protection et analyses de détection s'exécutent dans votre courrier électronique](how-policies-and-protections-are-combined.md).|
|CIP : \[adresse IP\]|Adresse IP de connexion. Vous pouvez utiliser cette adresse IP dans la liste d'adresses IP autorisées ou dans la liste d’adresses IP bloquées. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).|
|CTRY|Pays source, tel que déterminé par l'adresse IP de connexion, parfois différente de l'adresse IP d'envoi de provenance.|
|H : \[helostring\]|Chaîne HELO ou EHLO du serveur de courrier de connexion.|
|IPV:CAL|Le message a ignoré le filtrage du courrier indésirable, car l’adresse IP source figure dans la liste d’adresses IP autorisées. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).|
|IPV:NLI|L’adresse IP n’était répertoriée sur aucune liste de réputation d’adresses IP.|
|LANG|Langue dans laquelle le message a été rédigé, tel que spécifié par le code du pays (par exemple, ru_RU pour le russe).|
|PTR : \[ReverseDNS\]|Enregistrement PTR (connu également sous le nom d’enregistrement de pointeur ou d’adresse DNS inverse) de l’adresse IP source.|
|SCL|Seuil de niveau (SCL) du message. Plus cette valeur est élevée, plus il est probable que le message est un courrier indésirable. Pour plus d’informations, consultez [Seuil de probabilité de courrier indésirable (SCL)](spam-confidence-levels.md).|
|SFTY|Le message a été identifié comme étant du hameçonnage et sera également marqué par l'une des valeurs suivantes : <ul><li>9.1 : valeur par défaut. Le message contient une URL de hameçonnage, peut contenir d’autres contenus de hameçonnage ou peut avoir été marqué comme message de hameçonnage par un autre filtre de messagerie (par exemple, Exchange Server local) avant d’être relayé vers Microsoft 365.</li><li>9.11 : [Usurpation d’identité intra-organisation ou de soi à soi](anti-spoofing-protection.md#different-types-of-spoofing). Le message a échoué aux vérifications anti-usurpation où le domaine de messagerie de l’expéditeur figurant dans l'en-tête De est le même que, correspond à ou fait partie de la même organisation que le domaine de réception. Le conseil de sécurité relatif à l’usurpation d’identité intra-organisation sera ajouté au message.</li><li>9.19 : Emprunt d’identité de domaine. Le domaine expéditeur tente d’emprunter l’identité d’un domaine protégé (domaine appartenant à l’organisation du destinataire ou domaine personnalisé) spécifié dans une stratégie ATP anti-hameçonnage. Le conseil de sécurité pour l’emprunt d’identité de domaine est ajouté au message (si le conseil de sécurité est activé dans la stratégie ATP anti-hameçonnage).</li><li>9.20 : Emprunt d’identité d’un utilisateur. L’utilisateur expéditeur tente d’emprunter l’identité d’un utilisateur dans l’organisation du destinataire ou un utilisateur protégé spécifié dans une stratégie ATP anti-hameçonnage. Le conseil de sécurité pour l’emprunt d’identité d’un utilisateur est ajouté au message (si le conseil de sécurité est activé dans la stratégie ATP anti-hameçonnage).</li><li>9.21 : [Usurpation d’identité inter-domaines](anti-spoofing-protection.md#different-types-of-spoofing). Le message a échoué aux vérifications anti-usurpation où le domaine de messagerie de l’expéditeur figurant dans l'en-tête De ne s’authentifie pas et est un domaine externe. Utilisé conjointement avec [CompAuth](#authentication-results-message-header-fields-used-by-microsoft-email-authentication)).</li><li>9.22 : similaire au point 9.21 hormis que l’utilisateur possède un expéditeur approuvé qui a été remplacé.</li><li>9.23 : similaire au point 9.22 hormis que l’organisation possède un expéditeur ou un domaine autorisé qui a été remplacé.</li><li>9.24 : similaire au point 9.23 hormis que l’utilisateur possède une règle de flux de courrier Exchange (également connue sous le nom de règle de transport) qui a été remplacée.</li></ul>|
|SFV:BLK|Le filtrage a été ignoré et le message a été bloqué car il a été envoyé à partir d'une adresse figurant sur la liste des expéditeurs bloqués d'un utilisateur (liste Expéditeurs bloqués de l’utilisateur).<br/></br> Pour plus d’informations sur la manière dont les administrateurs peuvent gérer la liste Expéditeurs bloqués d’un utilisateur, consultez [Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).|
|SFV:NSPM|Le filtrage du courrier indésirable a marqué le message comme n'étant pas un courrier indésirable et le message a été envoyé aux destinataires appropriés.|
|SFV:SFE|Le filtrage a été ignoré et le message a été autorisé car il a été envoyé à partir d'une adresse figurant sur la liste des expéditeurs approuvés Outlook d'un utilisateur (liste Expéditeurs approuvés de l’utilisateur).<br/></br> Pour plus d’informations sur la manière dont les administrateurs peuvent gérer la liste Expéditeurs approuvés d’un utilisateur, consultez [Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).|
|SFV:SKA|Le message a ignoré le filtrage du courrier indésirable et a été remis à la boîte de réception, car il correspondait à une entrée dans une liste d’expéditeurs autorisés ou de domaines autorisés dans une stratégie anti-courrier indésirable. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|
|SFV:SKB|Le message a été marqué comme courrier indésirable, car il correspondait à une entrée dans une liste d’expéditeurs bloqués ou de domaines bloqués dans une stratégie anti-courrier indésirable. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|
|SFV:SKI|Semblable à SFV:SKN. Le message a ignoré le filtrage du courrier indésirable pour une autre raison (par exemple, il s’agissait d’un message électronique intra-organisationnel au sein d’un client).|
|SFV:SKN|Le message a été marqué comme n’étant pas du courrier indésirable avant d’être traité par le filtrage du courrier indésirable (par exemple, le message a été marqué comme SCL-1 ou **Contourner le filtrage du courrier indésirable** par une règle de flux de courrier).|
|SFV:SKQ|Le message a été libéré de la quarantaine et a été envoyé aux destinataires appropriés.|
|SFV:SKS|Le message a été marqué comme courrier indésirable avant d’être traité par le filtrage du courrier indésirable (par exemple, le message a été marqué comme SCL-5 à 9 par une règle de flux de courrier).|
|SFV:SPM|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable.|
|SRV:BULK|Le message a été identifié comme courrier en bloc par le filtrage du courrier indésirable et le seuil de niveau de réclamation en bloc (BCL). Lorsque le paramètre _MarkAsSpamBulkMail_ est `On` (activé par défaut), un message électronique en nombre est marqué comme étant du courrier fortement suspecté d’être indésirable (SCL 9). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|
|X-CustomSpam : \[ASFOption\]|Le message correspondait à une option avancée de filtrage de courrier indésirable (ASF). Pour afficher la valeur de l’en-tête X pour chaque paramètre ASF, consultez [Paramètres de filtre de courrier indésirable avancé](advanced-spam-filtering-asf-options.md).|
|

## <a name="x-microsoft-antispam-message-header-fields"></a>Champs d’en-tête de message X-Microsoft-Antispam

Le tableau suivant décrit certains champs utiles de l’en-tête **X-Microsoft-Antispam** des messages. Les autres champs de cet en-tête sont exclusivement utilisés par l’équipe Microsoft de lutte contre les courriers indésirables à des fins de diagnostic.

|||
|---|---|
|**Champ d’en-tête**|**Description**|
|BCL|Niveau de réclamation en bloc (BCL) du message. Un niveau BCL supérieur indique qu’un courrier en nombre (également appelé _message gris_) est susceptible de générer des plaintes (et par conséquent plus susceptible d’être du courrier indésirable). Pour plus d’informations, consultez [Niveau de réclamation en bloc (BCL)](bulk-complaint-level-values.md).|
|

## <a name="authentication-results-message-header"></a>En-tête de message Authentication-results

Les résultats des vérifications de SPF, DKIM et DMARC sont enregistrés ou marqués par Microsoft 365 dans l’en-tête **Authentication-results** des messages lorsque nos serveurs de messagerie reçoivent un e-mail.

### <a name="check-stamp-syntax-and-examples"></a>Syntaxe et exemples de marques de vérification

L’exemple de syntaxe suivant présente une partie de la « marque » au format texte que Microsoft 365 applique à l’en-tête du message pour chaque message qui fait l’objet d’une authentification lorsqu’il est reçu par nos serveurs de messagerie. Cette marque est ajoutée à l’en-tête **Authentication-Results**.

#### <a name="syntax-spf-check-stamp"></a>Syntaxe : marque de vérification SPF

Pour SPF, la syntaxe suivante s’applique.

```text
spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
```

##### <a name="examples-spf-check-stamp"></a>Exemples : marque de vérification SPF

```text
spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
```

#### <a name="syntax-dkim-check-stamp"></a>Syntaxe : marque de vérification DKIM

Pour DKIM, la syntaxe suivante s’applique.

```text
dkim=<pass|fail (reason)|none> header.d=<domain>
```

##### <a name="examples-dkim-check-stamp"></a>Exemples : marque de vérification DKIM

```text
dkim=pass (signature was verified) header.d=contoso.com
dkim=fail (body hash did not verify) header.d=contoso.com
```

#### <a name="syntax-dmarc-check-stamp"></a>Syntaxe : marque de vérification DMARC

Pour DMARC, la syntaxe suivante s’applique.

```text
dmarc=<pass|fail|bestguesspass|none> action=<permerror|temperror|oreject|pct.quarantine|pct.reject> header.from=<domain>
```

##### <a name="examples-dmarc-check-stamp"></a>Exemples : marque de vérification DMARC

```text
dmarc=pass action=none header.from=contoso.com
dmarc=bestguesspass action=none header.from=contoso.com
dmarc=fail action=none header.from=contoso.com
dmarc=fail action=oreject header.from=contoso.com
```

### <a name="authentication-results-message-header-fields-used-by-microsoft-email-authentication"></a>Champs de l’en-tête Authentication-results utilisés par l’authentification de courrier Microsoft

Le tableau ci-dessous décrit les champs et les valeurs possibles pour chaque vérification d’authentification de courrier électronique.

|||
|---|---|
|**Champ d’en-tête**|**Description**|
|action|Indique l’action effectuée par le filtre de courrier indésirable en fonction des résultats de la vérification DMARC. Par exemple : <ul><li>**oreject** ou **o.reject** : signifie « override reject » (ignorer le rejet). Microsoft 365 utilise cette action lorsqu’il reçoit un message qui échoue aux vérifications de DMARC et qui sont issus d’un domaine dont l’enregistrement TXT DMARC a pour stratégie p=reject (rejet). Au lieu de supprimer ou de rejeter le message, Microsoft 365 le marque comme courrier indésirable. Pour obtenir des explications sur cette configuration de Microsoft 365, reportez-vous à la section [Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.quarantine** : indique qu’un pourcentage inférieur à 100 % des messages n’ayant pas satisfait aux vérifications DMARC seront remis malgré tout. Cela signifie que le message n'a pas satisfait les vérifications DMARC et que la stratégie a été définie de manière à mettre les messages en quarantaine, mais que le champ pct n'a pas été défini sur 100 % et que le système a déterminé aléatoirement de ne pas appliquer l'action DMARC conformément à la stratégie du domaine spécifié.</li><li>**pct.reject** : indique qu’un pourcentage inférieur à 100 % des messages n'ayant pas satisfait aux vérifications DMARC seront remis malgré tout. Cela signifie que le message n'a pas satisfait les vérifications DMARC et que la stratégie a été définie de manière à rejeter les messages, mais que le champ pct n'a pas été défini sur 100 % et que le système a déterminé aléatoirement de ne pas appliquer l'action DMARC conformément à la stratégie du domaine spécifié.</li><li>**permerror** : indique qu’une erreur permanente s’est produite lors de l'évaluation DMARC, par exemple, qu’un enregistrement TXT DMARC mal formé a été détecté dans le système DNS. Toute tentative de renvoyer le message produira sans doute le même résultat. Essayez plutôt de contacter le propriétaire du domaine pour résoudre le problème.</li><li>**temperror** : indique qu’une erreur temporaire s’est produite lors de l’évaluation DMARC. Vous pouvez demander à l’expéditeur de renvoyer son message plus tard pour qu’il soit traité correctement.</li></ul>|
|compauth|Résultat de l’authentification composite. Utilisé par Microsoft 365 pour combiner plusieurs types d’authentification tels que SPF, DKIM, DMARC ou toute autre partie du message pour déterminer si le message est authentifié ou non. Utilise le domaine From: comme base d’évaluation.|
|dkim|Décrit les résultats de la vérification DKIM du message. Les valeurs admises sont les suivantes : <ul><li>**pass** : indique que le message a satisfait à la vérification DKIM.</li><li>**fail (raison)**  : indique que le message ne satisfait pas à la vérification DKIM et pourquoi. Par exemple, parce que le message n’a pas été signé ou que la signature n’a pas été vérifiée.</li><li>**none** : indique que le message n’a pas été signé. Cela n’indique pas forcément que le domaine a un enregistrement DKIM ou que l’évaluation de l’enregistrement DKIM ne donne pas de résultat, mais simplement que ce message n’a pas été signé.</li></ul>|
|dmarc|Décrit les résultats de la vérification DMARC pour le message. Les valeurs admises sont les suivantes : <ul><li>**pass** : indique que le message a satisfait à la vérification de DMARC.</li><li>**fail** : indique que le message a échoué à la vérification DMARC.</li><li>**bestguesspass** : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine, mais que s’il en existait un, la vérification DMARC aurait accepté le message. En effet, le domaine dans l’adresse `5321.MailFrom` (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe) correspond au domaine dans l’adresse `5322.From` (également appelée adresse de l’expéditeur ou P2).</li><li>**none** : indique qu’il n’existe aucun enregistrement TXT DKIM pour le domaine expéditeur dans le système DNS.|
|header.d|Domaine défini dans la signature DKIM, s'il y en a un. Il s'agit du domaine auquel la clé publique est demandée.|
|header.from|Domaine de l’adresse `5322.From` dans l’en-tête de l’e-mail (également appelée adresse de l’expéditeur ou P2). Destinataire : voir l’adresse de l’expéditeur dans les clients de courrier.|
|reason (Raison)|Raison pour laquelle l’authentification composite a réussi ou échoué. La valeur est un code à 3 chiffres. Par exemple : <ul><li>**000** : le message n’a pas été authentifié de façon explicite (`compauth=fail`). Par exemple, le message a reçu un échec DMARC et déclenché une action de mise en quarantaine ou de rejet.</li><li>**001** : le message n’a pas été authentifié de façon implicite (`compauth=fail`). Cela signifie que le domaine d’envoi n’a pas publié d’enregistrement d’authentification de courrier ou, s’il la fait, que sa stratégie en cas d’échec était plus faible (erreur SPF récupérable ou neutre, stratégie DMARC de `p=none`).</li><li>**002** : l’organisation a une stratégie pour la paire expéditeur/domaine qui interdit explicitement l’envoi d’e-mails usurpés. Ce paramètre est configuré manuellement par un administrateur.</li><li>**010** : le message a échoué au filtrage DMARC, et déclenché une action de rejet ou de mise en quarantaine, et que le domaine d’envoi est l’un des domaines acceptés de l’organisation (cela fait partie de l’usurpation self-to-self, ou intra-organisationnelle).</li><li>**1xx** ou **7xx** : il s’agit de l’authentification réussie du message (`compauth=pass`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**2xx** : il s’agit de l’authentification implicite avec transfert logiciel (`compauth=softpass`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**3xx** : le message n’a pas été vérifié pour l’authentification composite (`compauth=none`).</li><li>**4xx** ou **9xx** : le message a contourné l’authentification composite(`compauth=none`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**6xx** : le message a échoué à l’authentification de courrier implicite et que le domaine d’envoi est l’un des domaines acceptés de l’organisation (cela fait partie de l’usurpation de soi à soi ou intra-organisation).</li></ul>|
|smtp.mailfrom|Domaine de l’adresse `5321.MailFrom` (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe). Il s’agit de l’adresse e-mail utilisée pour les rapports de non-remise (également appelés notifications d’échec de remise ou notifications de non-remise).|
|spf|Décrit les résultats de la vérification SPF pour le message. Les valeurs admises sont les suivantes : <ul><li>**pass (adresse IP)**  : indique que le message a réussi la vérification SPF et fournit l’adresse IP de l’expéditeur. Le client est autorisé à envoyer ou à relayer le courrier électronique avec le domaine de l’expéditeur.</li><li>**fail (adresse IP)**  : indique que le message a échoué à la vérification SPF et fournit l’adresse IP de l’expéditeur. Dans ce cas, on parle parfois d’_échec sévère_.</li><li>**softfail (raison)**  : indique que l’enregistrement SPF a désigné l’hôte comme n’étant pas autorisé à envoyer mais qu’il est en transition.</li><li>**neutral** : indique que l’enregistrement SPF déclare explicitement qu’il ne peut pas confirmer si l’adresse IP est autorisée.</li><li>**none** : indique que le domaine n’a pas d’enregistrement SPF ou que l’évaluation de l’enregistrement SPF ne donne aucun résultat.</li><li>**temperror** : indique qu’une erreur pouvant être de nature temporaire s’est produite ; il s’agit, par exemple, d’une erreur DNS. L’opération est susceptible de réussir sans intervention de l’administrateur si vous réessayez ultérieurement.</li><li>**permerror** : indique qu’une erreur permanente s’est produite. Cela peut se produire, par exemple, si l’enregistrement SPF du domaine est mal formaté.</li></ul>|
|
