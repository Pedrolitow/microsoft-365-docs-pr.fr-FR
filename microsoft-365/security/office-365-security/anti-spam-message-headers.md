---
title: En-têtes de messages anti-courrier indésirable
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 2e3fcfc5-5604-4b88-ac0a-c5c45c03f1db
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent en savoir plus sur les champs d’en-tête ajoutés aux messages par Exchange Online Protection (EOP)0 Ces champs d’en-tête fournissent des informations sur le message et la manière dont il a été traité.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 89cd21e947923602d2c268a99d2a4a1fc1fba28e
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483231"
---
# <a name="anti-spam-message-headers-in-microsoft-365"></a>En-têtes de message anti-courrier indésirable dans Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans toutes les organisations Microsoft 365, Exchange Online Protection (EOP) analyse tous les messages entrants à la recherche de courrier indésirable, de programmes malveillants et d’autres menaces. Les résultats de ces analyses sont ajoutés aux champs d’en-tête suivants dans les messages :

- **X-Forefront-Antispam-Report** : contient des informations sur le message et sur la manière dont il a été traité.

- **X-Microsoft-Antispam** : contient des informations supplémentaires sur le courrier en nombre et le hameçonnage.

- **Authentication-Results** : contient des informations sur les résultats SPF, DKIM et DMARC (authentification de messagerie électronique).

Cet article décrit les fonctionnalités disponibles dans ces champs d’en-tête.

Pour plus d’informations sur le mode d’affichage de l’en-tête d’un e-mail dans divers clients de messagerie, consultez [Afficher les en-têtes de messages Internet dans Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

> [!TIP]
> Vous pouvez copier et coller le contenu de l'en-tête d’un message dans l'[analyseur d'en-têtes de message](https://mha.azurewebsites.net/). Cet outil aide à analyser les en-têtes et à les afficher dans un format plus lisible.

## <a name="x-forefront-antispam-report-message-header-fields"></a>Champs d’en-tête de message X-Forefront-Antispam-Report

Une fois que vous avez les informations d’en-tête du message, recherchez l’en-tête de **X-Forefront-Antispam-Report**. Cet en-tête comportera plusieurs paires champ/valeur dans cet en-tête séparées par des points-virgules (;). Par exemple :

`...CTRY:;LANG:hr;SCL:1;SRV:;IPV:NLI;SFV:NSPM;PTR:;CAT:NONE;SFTY:;...`

Les champs et valeurs individuels sont décrits dans le tableau suivant.

> [!NOTE]
> L’en-tête **X-Forefront-Antispam-Report** contient de nombreux champs et valeurs d’en-tête différents. Les champs qui ne sont pas décrits dans le tableau sont exclusivement utilisés par l’équipe Microsoft de lutte contre les courriers indésirables à des fins de diagnostic.

|Champ|Description|
|---|---|
|`ARC`|Le protocole `ARC` contient les champs suivants : <ul><li>`AAR` : enregistre le contenu de l'en-tête **Authentication-Results** à partir de DMARC.</li><li>`AMS` : inclut les signature de chiffrement du message.</li><li>`AS`: comprend les signatures cryptographiques des en-têtes de message. Ce champ contient une balise de validation de la chaîne appelée`"cv="`, qui comprend le résultat de la validation de la chaîne (**none**, **pass**, ou **échec**).</li></ul>|
|`CAT:`|Catégorie de stratégie de protection appliquée au message : <ul><li>`BULK` : courrier en nombre</li><li>`DIMP` : Emprunt d’identité de domaine.</li><li>`GIMP` : [emprunt d’identité basé sur la veille des boîtes aux lettre](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>`HPHSH` ou `HPHISH`: hameçonnage à haut niveau de confiance</li><li>`HSPM` : courrier indésirable à probabilité élevée</li><li>`MALW` : programme malveillant</li><li>`PHSH` : hameçonnage</li><li>`SPM` : courrier indésirable</li><li>`SPOOF` : erreur de dépassement de données</li><li>`UIMP` : emprunt d’identité d’un utilisateur</li><li>`AMP` : anti-programme malveillant</li><li>`SAP` : pièces jointes fiables</li><li>`FTBP` : stratégie de type de fichier anti-programme malveillant</li><li>`OSPM` :courrier indésirable sortant</li></ul> <p> Un message entrant peut être signalé par plusieurs formes de protection et plusieurs analyses de détection. Les stratégies ont des priorités différentes, et la stratégie ayant la priorité la plus élevée s'applique en premier. Pour plus d’informations, voir [Quelle stratégie s’applique lorsque plusieurs méthodes de protection et analyses de détection s'exécutent dans votre courrier électronique](how-policies-and-protections-are-combined.md).|
|`CIP:[IP address]`|Adresse IP de connexion. Vous pouvez utiliser cette adresse IP dans la liste d'adresses IP autorisées ou dans la liste d’adresses IP bloquées. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).|
|`CTRY`|Le pays source, tel que déterminé par l'adresse IP de connexion, parfois différente de l'adresse IP d'envoi de provenance.|
|`H:[helostring]`|Chaîne HELO ou EHLO du serveur de courrier de connexion.|
|`IPV:CAL`|Le message a échappé au filtrage du spam car l'adresse IP source figurait dans la liste des adresses IP autorisées. Pour plus d'informations, voir [Configurer le filtrage des connexions](configure-the-connection-filter-policy.md).|
|`IPV:NLI`|L’adresse IP n’a été trouvée sur aucune liste de réputation d’adresses IP.|
|`LANG`|Langue dans laquelle le message a été rédigé, tel que spécifié par le code du pays (par exemple, ru_RU pour le russe).|
|`PTR:[ReverseDNS]`|L’enregistrement PTR (également connu sous le nom de recherche DNS inverse) de l’adresse IP source.|
|`SCL`|Seuil de niveau (SCL) du message. Plus cette valeur est élevée, plus il est probable que le message est un courrier indésirable. Pour plus d’informations, consultez [Seuil de probabilité de courrier indésirable (SCL)](spam-confidence-levels.md).|
|`SFTY`|Le message a été identifié comme étant du hameçonnage et sera également marqué par l'une des valeurs suivantes : <ul><li>9.19 : Emprunt d’identité de domaine. Le domaine d’envoi tente d’[emprunter l’identité d’un domaine protégé](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). L’astuce de sécurité pour l’emprunt d’identité de domaine est ajoutée au message (si l’option est activée).</li><li>9.20 : Emprunt d’identité d’un utilisateur. L'utilisateur expéditeur tente d'usurper l'identité d'un utilisateur de l'organisation du destinataire ou [d'un utilisateur protégé spécifié dans une stratégie](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) anti-hameçonnage de Microsoft Defender pour office 365. Le conseil de sécurité concernant l'usurpation d'identité est ajouté au message (s'il est activé).</li><li>9.25 : premier conseil de sécurité de contact. Cette valeur _peut_ être une indication d’un message suspect ou d’hameçonnage. Pour plus d’informations, consultez [Premier conseil de sécurité de contact](set-up-anti-phishing-policies.md#first-contact-safety-tip).</li></ul>|
|`SFV:BLK`|Le filtrage a été ignoré et le message a été bloqué, car il a été envoyé à partir d’une adresse figurant dans la liste des expéditeurs bloqués d’un utilisateur. <p> Pour plus d’informations sur la manière dont les administrateurs peuvent gérer la liste Expéditeurs bloqués d’un utilisateur, consultez [Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:NSPM`|Le filtrage du courrier indésirable a marqué le message comme n'étant pas un courrier indésirable et le message a été envoyé aux destinataires appropriés.|
|`SFV:SFE`|Le filtrage a été ignoré et le message a été autorisé, car il a été envoyé à partir d’une adresse figurant dans la liste des expéditeurs approuvés d’un utilisateur. <p> Pour plus d’informations sur la manière dont les administrateurs peuvent gérer la liste Expéditeurs approuvés d’un utilisateur, consultez [Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).|
|`SFV:SKA`|Le message n’a pas subit de filtrage du courrier indésirable et a été dirigé vers la boîte de réception, car l’expéditeur fait partie de la liste des expéditeurs autorisés ou de celle des domaines autorisés dans une stratégie anti-courrier indésirable. [Pour plus d'informations, voir Configurer les politiques anti-spam](configure-your-spam-filter-policies.md).|
|`SFV:SKB`|Le message a été marqué comme courrier indésirable, car il correspondait à un expéditeur de la liste des expéditeurs bloqués ou de celle des domaines bloqués dans une stratégie anti-courrier indésirable. Pour plus d'informations, voir [Configurer les politiques anti-spam](configure-your-spam-filter-policies.md).|
|`SFV:SKI`|Semblable à SFV:SKN, le message a ignoré le filtrage du courrier indésirable pour une autre raison (par exemple, il s’agissait d’un message électronique intra-organisationnel au sein d’un client).|
|`SFV:SKN`|Le message a été marqué comme n’étant pas du courrier indésirable avant d’être traité par le filtrage du courrier indésirable (par exemple, le message a été marqué comme SCL-1 ou **Contourner le filtrage du courrier indésirable** par une règle de flux de courrier).|
|`SFV:SKQ`|Le message a été libéré de la quarantaine et envoyé aux destinataires appropriés.|
|`SFV:SKS`|Le message a été marqué comme courrier indésirable avant d’être traité par le filtrage du courrier indésirable (par exemple, le message a été marqué comme SCL-5 à 9 par une règle de flux de courrier).|
|`SFV:SPM`|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable.|
|`SRV:BULK`|Le message a été identifié comme courrier en bloc par le filtrage du courrier indésirable et le seuil de niveau de réclamation en bloc (BCL). Lorsque le paramètre _MarkAsSpamBulkMail_ est `On` (il est activé par défaut), un message électronique en bloc est marqué comme courrier indésirable (SCL 6). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|
|`X-CustomSpam: [ASFOption]`|Le message correspondait à une option avancée de filtrage de courrier indésirable (ASF). Pour afficher la valeur de l’en-tête X pour chaque paramètre ASF, consultez [Paramètres de filtre de courrier indésirable avancé](advanced-spam-filtering-asf-options.md).|

## <a name="x-microsoft-antispam-message-header-fields"></a>Champs d’en-tête de message X-Microsoft-Antispam

Le tableau suivant décrit certains champs utiles de l’en-tête **X-Microsoft-Antispam** des messages. Les autres champs de cet en-tête sont exclusivement utilisés par l’équipe Microsoft de lutte contre les courriers indésirables à des fins de diagnostic.

|Champ|Description|
|---|---|
|`BCL`|Niveau de réclamation en bloc (BCL) du message. Un niveau BCL supérieur indique qu’un courrier en nombre est susceptible de générer des plaintes (et par conséquent plus susceptible d’être du courrier indésirable). Pour plus d’informations, consultez [Niveau de réclamation en bloc (BCL)](bulk-complaint-level-values.md).|

## <a name="authentication-results-message-header"></a>En-tête de message Authentication-results

Les résultats des vérifications d’authentification de la messagerie électronique pour SPF, DKIM et DMARC sont enregistrés (marqués) dans l’en-tête de message **Authentication-Results** dans les messages entrants.

La liste suivante décrit le texte ajouté à l’en-tête **Authentication-Results** pour chaque type de vérification de l’authentification par courrier électronique :

- SPF utilise la syntaxe suivante :

  ```text
  spf=<pass (IP address)|fail (IP address)|softfail (reason)|neutral|none|temperror|permerror> smtp.mailfrom=<domain>
  ```

  Par exemple :

  ```text
  spf=pass (sender IP is 192.168.0.1) smtp.mailfrom=contoso.com
  spf=fail (sender IP is 127.0.0.1) smtp.mailfrom=contoso.com
  ```

- DKIM utilise la syntaxe suivante :

  ```text
  dkim=<pass|fail (reason)|none> header.d=<domain>
  ```

  Par exemple :

  ```text
  dkim=pass (signature was verified) header.d=contoso.com
  dkim=fail (body hash did not verify) header.d=contoso.com
  ```

- DMARC utilise la syntaxe suivante :

  ```text
  dmarc=<pass|fail|bestguesspass|none> action=<permerror|temperror|oreject|pct.quarantine|pct.reject> header.from=<domain>
  ```

  Par exemple :

  ```text
  dmarc=pass action=none header.from=contoso.com
  dmarc=bestguesspass action=none header.from=contoso.com
  dmarc=fail action=none header.from=contoso.com
  dmarc=fail action=oreject header.from=contoso.com
  ```

### <a name="authentication-results-message-header-fields"></a>Champs d’en-tête de message Authentication-Results

Le tableau ci-dessous décrit les champs et les valeurs possibles pour chaque vérification d’authentification de messagerie électronique.

|Champ|Description|
|---|---|
|`action`|Indique l’action effectuée par le filtre de courrier indésirable en fonction des résultats de la vérification DMARC. Par exemple : <ul><li>**oreject** ou **o.reject** : signifie « override reject » (ignorer le rejet). Microsoft 365 utilise cette action lorsqu’il reçoit un message qui échoue aux vérifications de DMARC et qui sont issus d’un domaine dont l’enregistrement TXT DMARC a pour stratégie p=reject (rejet). Au lieu de supprimer ou de rejeter le message, Microsoft 365 le marque comme courrier indésirable. Pour obtenir des explications sur cette configuration de Microsoft 365, reportez-vous à la section [Gestion des messages électroniques entrants qui échouent aux vérifications de DMARC dans Microsoft 365](use-dmarc-to-validate-email.md#how-microsoft-365-handles-inbound-email-that-fails-dmarc).</li><li>**pct.quarantine** indique qu’un pourcentage inférieur à 100 % des messages n’ayant pas satisfait les vérifications DMARC seront remis malgré tout. Cela signifie que le message n’a pas satisfait les vérifications DMARC et que la stratégie a été définie de manière à mettre les messages en quarantaine, mais que le champ pct n’a pas été défini sur 100 % et que le système a déterminé aléatoirement de ne pas appliquer l’action DMARC conformément à la stratégie du domaine spécifié.</li><li>**pct.reject** indique qu’un pourcentage inférieur à 100 % des messages n’ayant pas satisfait les vérifications DMARC seront remis malgré tout. Cela signifie que le message n’a pas satisfait les vérifications DMARC et que la stratégie a été définie de manière à rejeter les messages, mais que le champ pct n’a pas été défini sur 100 % et que le système a déterminé aléatoirement de ne pas appliquer l’action DMARC conformément à la stratégie du domaine spécifié.</li><li>**permerror** indique qu’une erreur permanente s’est produite lors de l’évaluation DMARC, par exemple, qu’un enregistrement TXT DMARC mal formé a été détecté dans le système DNS. Toute tentative de renvoyer le message produira sans doute le même résultat. Essayez plutôt de contacter le propriétaire du domaine pour résoudre le problème.</li><li>**temperror** indique qu’une erreur temporaire s’est produite lors de l’évaluation DMARC. Vous pouvez demander à l’expéditeur de réessayer de renvoyer son message plus tard pour qu’il soit traité correctement.</li></ul>|
|`compauth`|Résultat de l’authentification composite. Utilisé par Microsoft 365 pour combiner plusieurs types d’authentification tels que SPF, DKIM, DMARC ou toute autre partie du message pour déterminer si le message est authentifié ou non. Utilise le domaine From: comme base d’évaluation.|
|`dkim`|Décrit les résultats de la vérification DKIM du message. Les valeurs admises sont les suivantes : <ul><li>**pass** : indique que le message a satisfait à la vérification DKIM.</li><li>**fail (raison)** indique que le message ne satisfait pas la vérification DKIM et pourquoi. Par exemple, parce que le message n’a pas été signé ou que la signature n’a pas été vérifiée.</li><li>**none** indique que le message n’a pas été signé. Cela n’indique pas forcément que le domaine a un enregistrement DKIM ou que l’évaluation de l’enregistrement DKIM ne donne pas de résultat, mais simplement que ce message n’a pas été signé.</li></ul>|
|`dmarc`|Décrit les résultats de la vérification DMARC pour le message. Les valeurs admises sont les suivantes : <ul><li>**pass** : indique que le message a satisfait à la vérification de DMARC.</li><li>**fail** : indique que le message a échoué à la vérification DMARC.</li><li>**bestguesspass** : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine, mais que s’il en existait un, la vérification DMARC aurait accepté le message.</li><li>**none** : indique qu’il n’existe aucun enregistrement TXT DMARC pour le domaine expéditeur dans le système DNS.|
|`header.d`|Domaine défini dans la signature DKIM, s'il y en a un. Il s'agit du domaine auquel la clé publique est demandée.|
|`header.from`|Domaine de l’adresse `5322.From` dans l’en-tête de l’e-mail (également appelée adresse de l’expéditeur ou P2). Le destinataire voit l’adresse de l’expéditeur dans les clients de courrier.|
|`reason`|Raison pour laquelle l’authentification composite a réussi ou échoué. La valeur est un code à 3 chiffres. Par exemple : <ul><li>**000**: Le message a échoué à l'authentification explicite (`compauth=fail`). Par exemple, le message a reçu un échec DMARC et déclenché une action de mise en quarantaine ou de rejet.</li><li>**001**: Le message a échoué à l'authentification implicite (`compauth=fail`). Cela signifie que le domaine d’envoi n’a pas publié d’enregistrement d’authentification de courrier ou, s’il la fait, que sa stratégie en cas d’échec était plus faible (erreur SPF récupérable ou neutre, stratégie DMARC de `p=none`).</li><li>**002** : signifie que l’organisation a une stratégie pour la paire expéditeur/domaine qui interdit explicitement l’envoi d’e-mails usurpés, ce paramètre étant défini manuellement par un administrateur.</li><li>**010** : le message a échoué au filtrage DMARC, et déclenché une action de rejet ou de mise en quarantaine, et que le domaine d’envoi est l’un des domaines acceptés de l’organisation (cela fait partie de l’usurpation self-to-self, ou intra-organisationnelle).</li><li>**1xx** ou **7xx** : il s’agit de l’authentification réussie du message (`compauth=pass`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**2xx** : il s’agit de l’authentification implicite avec transfert logiciel (`compauth=softpass`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**3xx** : le message n’a pas été vérifié pour l’authentification composite (`compauth=none`).</li><li>**4xx** ou **9xx** : le message a contourné l’authentification composite(`compauth=none`). Les deux derniers chiffres sont des codes internes utilisés par Microsoft 365.</li><li>**6xx** : le message a échoué à l’authentification de courrier implicite et que le domaine d’envoi est l’un des domaines acceptés de l’organisation (cela fait partie de l’usurpation de soi à soi ou intra-organisation).</li></ul>|
|`smtp.mailfrom`|Domaine de l’adresse `5321.MailFrom` (également appelée adresse MAIL FROM, expéditeur P1 ou expéditeur d’enveloppe). Il s’agit de l’adresse e-mail utilisée pour les rapports de non-remise (également appelés notifications d’échec de remise ou notifications de non-remise).|
|`spf`|Décrit les résultats de la vérification SPF pour le message. Les valeurs admises sont les suivantes : <ul><li>`pass (IP address)` : indique que le message a réussi la vérification SPF et fournit l’adresse IP de l’expéditeur. Le client est autorisé à envoyer ou à relayer le courrier électronique avec le domaine de l’expéditeur.</li><li>`fail (IP address)`: La vérification SPF du message a échoué et inclut l'adresse IP de l'expéditeur. Ceci est parfois appelé _hard fail_.</li><li>`softfail (reason)` : l’enregistrement SPF a désigné l’hôte comme n’étant pas autorisé à envoyer, mais est en transition.</li><li>`neutral` : l’enregistrement SPF indique explicitement qu’il ne déclare pas si l’adresse IP est autorisée à envoyer.</li><li>`none` : le domaine ne possède pas d’enregistrement SPF ou l’enregistrement SPF ne correspond à aucun résultat.</li><li>`temperror` : une erreur temporaire s’est produite. Par exemple, une erreur DNS. Cette même vérification peut être effectuée ultérieurement.</li><li>`permerror` : une erreur permanente est survenue. Par exemple, un enregistrement SPF mal mis en forme dans le domaine.</li></ul>|
