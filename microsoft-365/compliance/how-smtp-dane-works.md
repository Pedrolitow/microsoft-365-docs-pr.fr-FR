---
title: Fonctionnement de l’authentification DNS SMTP des entités nommées (DANE) pour sécuriser les communications électroniques
f1.keywords:
- NOCSH
ms.author: v-mathavale
author: v-mathavale
manager: dansimp
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Découvrez comment fonctionne l’authentification DNS SMTP des entités nommées (DANE) pour sécuriser les communications électroniques entre les serveurs de messagerie.
ms.openlocfilehash: 32c39859d9bfdf292fd9c7a315a0ee1ee08eae2e
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2022
ms.locfileid: "62272029"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Fonctionnement de l’authentification DNS SMTP des entités nommées (DANE)

Le protocole SMTP est le principal protocole utilisé pour transférer des messages entre des serveurs de messagerie et n’est pas sécurisé par défaut. Le protocole TLS (Transport Layer Security) a été introduit il y a des années pour prendre en charge la transmission chiffrée de messages sur SMTP. Il est couramment utilisé de façon opportuniste plutôt que comme une exigence, ce qui laisse un trafic de courrier en texte clair, vulnérable à l’interception par des acteurs peu politiques. En outre, SMTP détermine les adresses IP des serveurs de destination par le biais de l’infrastructure DNS publique, susceptible d’être usurpée et d’attaques par l’intermédiaire (MITM). De nombreuses nouvelles normes ont été créées pour renforcer la sécurité de l’envoi et de la réception de messages électroniques, l’une d’entre elles étant l’authentification DNS des entités nommées (DANE).
  
DANE pour SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) utilise la présence d’un enregistrement TLSA (Transport Layer Security Authentication) dans le jeu d’enregistrement DNS d’un domaine pour signaler un domaine et ses serveurs de messagerie prendre en charge DANE. Si aucun enregistrement TLSA n’est présent, la résolution DNS pour le flux de messagerie fonctionne comme d’habitude sans tentative de vérification DANE. L’enregistrement TLSA signale en toute sécurité la prise en charge de TLS et publie la stratégie DANE pour le domaine. Ainsi, les serveurs de messagerie d’envoi peuvent authentifier les serveurs de messagerie de réception légitimes à l’aide du DANE SMTP. Cela le rend résistant aux rétrogradations et aux attaques MITM. DANE a des dépendances directes sur DNSSEC, qui fonctionne en signant numériquement des enregistrements pour les recherche DNS à l’aide du chiffrement à clé publique. Les vérifications DNSSEC se produisent sur les résolvants DNS récursifs, les serveurs DNS qui font des requêtes DNS pour les clients. DNSSEC garantit que les enregistrements DNS ne sont pas falsifiés et qu’ils sont authentifiés.  

Une fois que les enregistrements de ressource liés à MX, A/AAAA et DNSSEC pour un domaine sont renvoyés au résolveur récursif DNS comme DNSSEC authentifié, le serveur de messagerie d’envoi demande l’enregistrement TLSA correspondant à l’entrée ou aux entrées de l’hôte MX. Si l’enregistrement TLSA est présent et qu’il s’est montré authentique à l’aide d’une autre vérification DNSSEC, le résolveur récursif DNS renvoie l’enregistrement TLSA au serveur de messagerie d’envoi. 

Après avoir reçu l’enregistrement TLSA authentique, le serveur de messagerie d’envoi établit une connexion SMTP à l’hôte MX associé à l’enregistrement TLSA authentique. Le serveur de messagerie d’envoi essaiera de configurer TLS et comparera le certificat TLS du serveur avec les données de l’enregistrement TLSA pour vérifier que le serveur de messagerie de destination connecté à l’expéditeur est le serveur de messagerie de réception légitime. Le message est transmis (à l’aide de TLS) si l’authentification réussit. En cas d’échec de l’authentification ou si TLS n’est pas pris en charge par le serveur de destination, Exchange Online retentera l’intégralité du processus de validation en commençant par une requête DNS pour le même domaine de destination après 15 minutes, puis 15 minutes après, puis toutes les heures pour les 24 heures suivantes. Si l’authentification continue d’échouer après 24 heures de nouvelle tentative, le message expire et une NDR avec des détails sur l’erreur est générée et envoyée à l’expéditeur. 

## <a name="what-are-the-components-of-dane"></a>Quels sont les composants de DANE ?

### <a name="tlsa-resource-record"></a>Enregistrement de ressource TLSA

L’enregistrement TLS Authentication (TLSA) permet d’associer le certificat X.509 d’un serveur ou la valeur de clé publique au nom de domaine qui contient l’enregistrement. Les enregistrements TLSA ne peuvent être fiables que si DNSSEC est activé sur votre domaine. Si vous utilisez un fournisseur DNS pour héberger votre domaine, il peut s’agit d’un paramètre proposé lors de la configuration d’un domaine avec eux. Pour en savoir plus sur la signature de zone DNSSEC, consultez ce lien : Vue d’ensemble de [la signature de zone DNSSEC | Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)). 
  
Exemple d’enregistrement TLSA :
  
:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Exemple d’enregistrement TLSA" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Il existe quatre champs configurables propres au type d’enregistrement TLSA : 

**Champ Utilisation du** certificat : spécifie comment le serveur de messagerie d’envoi doit vérifier le certificat du serveur de messagerie de destination.

|Valeur  |Acronyme  |Description |
|---------|---------|---------|
|01<sup></sup>     |PKIX-TA          |Le certificat utilisé est l’ac publique d’ancrage d’autorisation de la chaîne d’autorisation X.509.          |
|11<sup></sup>     |PKIX-EE         |Le certificat vérifié est le serveur de destination . Les vérifications DNSSEC doivent vérifier son authenticité.          |
|2     |DANE-TA         |Utilisez la clé privée du serveur à partir de l’arborescence X.509 qui doit être validée par un ancrage d’trust dans la chaîne d’confiance. L’enregistrement TLSA spécifie l’ancrage d’autorisation à utiliser pour valider les certificats TLS pour le domaine.         |
|3     |DANE-EE         |Correspond uniquement au certificat du serveur de destination.           |

<sup>1</sup> Exchange Online suit les instructions d’implémentation RFC selon que les valeurs de champ d’utilisation de certificat 0 ou 1 ne doivent pas être utilisées lorsque DANE est implémenté avec SMTP.   Lorsqu’un enregistrement TLSA dont la valeur du champ Utilisation du certificat est 0 ou 1 est renvoyé à Exchange Online, Exchange Online le traite comme non utilisable. Si tous les enregistrements TLSA sont inutilisables, Exchange Online n’effectue pas les étapes de validation DANE pour 0 ou 1 lors de l’envoi du message électronique. Au lieu de cela, en raison de la présence d’un enregistrement TLSA, Exchange Online applique l’utilisation de TLS pour envoyer le courrier électronique, l’envoyer si le serveur de messagerie de destination prend en charge TLS ou déposer le courrier électronique et générer une NDR si le serveur de messagerie de destination ne prend pas en charge TLS.     

Dans l’exemple d’enregistrement TLSA, le champ Utilisation du certificat est définie sur « 3 » ; les données d’association de certificats ('abc123... xyz789') correspond au certificat du serveur de destination uniquement.

**Champ Sélecteur** : indique quelles parties du certificat du serveur de destination doivent être vérifiées. 

|Valeur  |Acronyme  |Description  |
|---------|---------|---------|
|0     |Cert         |Utiliser un certificat complet.         |
|1     |SPKI (Informations sur la clé publique du sujet)          |Utilisez la clé publique du certificat et l’algorithme avec lequel la clé publique doit être identifiée.          |

Dans l’exemple d’enregistrement TLSA, le champ Sélecteur est défini sur « 1 » afin que les données d’association de certificat soient mise en correspondance à l’aide de la clé publique du certificat de serveur de destination et de l’algorithme avec lequel la clé publique doit être identifiée.

**Champ de type** correspondant : indique le format du certificat sera représenté dans l’enregistrement TLSA. 

|Valeur  |Acronyme  |Description  |
|---------|---------|---------|
|0     |Complet         |Les données de l’enregistrement TSLA sont le certificat complet ou SPKI.          |
|1     |SHA-256         |Les données de l’enregistrement TSLA sont un hachage SHA-256 du certificat ou du SPKI.          |
|2     |SHA-512         |Les données de l’enregistrement TSLA sont un hachage SHA-512 du certificat ou du SPKI.         |

Dans l’exemple d’enregistrement TLSA, le champ de type correspondant est « 1 » de sorte que les données d’association de certificat sont un hachage SHA-256 des informations de clé publique de l’objet du certificat de serveur de destination

**Données d’association** de certificat : spécifie les données de certificat utilisées pour la mise en correspondance avec le certificat de serveur de destination. Ces données dépendent de la valeur du champ sélecteur et de la valeur de type correspondante.

Dans l’exemple d’enregistrement TLSA, les données d’association de certificats sont définies sur « abc123... xyz789'. Étant donné que la valeur du champ Sélecteur dans l’exemple est définie sur « 1 » , elle fait référence à la clé publique du certificat de serveur de destination et à l’algorithme identifié pour être utilisé avec elle. Et comme la valeur du champ Type correspondant dans l’exemple est définie sur « 1 » , elle fait référence au hachage SHA-256 des informations de clé publique de l’objet à partir du certificat de serveur de destination.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Comment les Exchange Online peuvent-ils utiliser SMTP DANE Outbound ?

En tant Exchange Online client, vous n’avez rien à faire pour configurer cette sécurité améliorée du courrier électronique pour votre courrier sortant. C’est quelque chose que nous avons créé pour vous et qui est utilisé par défaut pour tous les clients Exchange Online et utilisé lorsque le domaine de destination annonce la prise en charge de DANE. Pour profiter des avantages de l’envoi de courrier électronique à l’aide de vérifications DNSSEC et DANE, communiquez à vos partenaires commerciaux avec lesquels vous échangez du courrier électronique afin qu’ils doivent implémenter DNSSEC et DANE afin qu’ils reçoivent des messages électroniques à l’aide de ces normes. 

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Comment les Exchange Online peuvent-ils utiliser le DANE SMTP entrant ?

Actuellement, le DANE SMTP entrant n’est pas pris en charge pour les Exchange Online. La publication de la prise en charge est prévue à la fin de l’année 2022. 

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Quelle est la configuration d’enregistrement TLSA recommandée ?

Selon les recommandations d’implémentation RFC pour SMTP DANE, un enregistrement TLSA composé du champ Utilisation du certificat est 3, le champ Sélecteur est 1 et le champ Type correspondant 1 est recommandé. 

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online messagerie Flow avec SMTP DANE 

Le processus de flux de messagerie pour Exchange Online avec SMTP DANE, illustré dans le diagramme de flux ci-dessous, valide la sécurité des enregistrement de domaine et de ressource via DNSSEC, la prise en charge TLS sur le serveur de messagerie de destination et que le certificat du serveur de messagerie de destination correspond à ce qui est attendu en fonction de son enregistrement TLSA associé. 

Il existe seulement deux scénarios dans lequel une défaillance SMTP DANE entraîne le blocage du courrier électronique :

- Le domaine de destination a signalé la prise en charge DNSSEC, mais un ou plusieurs enregistrements ont été renvoyés comme inauthentiques. 

- Tous les enregistrements MX pour le domaine de destination ont des enregistrements TLSA et aucun des certificats du serveur de destination ne correspond à ce qui était prévu par les données d’enregistrement TSLA, ou une connexion TLS n’est pas prise en charge par le serveur de destination.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange flux de messagerie en ligne avec SMTP DANE" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Technologies associées 

|Technologie  |Informations complémentaires  |
|---------|---------|
|Agent de transfert de courrier **– MTA-STS (Strict Transport Security)** permet d’éviter les rétrogradations et les attaques de l’homme au milieu en fournissant un mécanisme pour définir des stratégies de domaine qui spécifient si le serveur de messagerie de destination prend en charge TLS et ce qu’il faut faire lorsque TLS ne peut pas être négocié, par exemple arrêter la transmission.     |Plus d’informations Exchange Online la prise en charge à venir de MTA-STS entrant et sortant sera publiée plus tard cette année.     [Exchange Online’actualités sur le transport de Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)<br /><br />[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461) |
|**Sender Policy Framework (SPF)** utilise des informations IP pour s’assurer que les systèmes de messagerie de destination font confiance aux messages envoyés à partir de votre domaine personnalisé.    |   [Comment SPF (Sender Policy Framework) empêche l’usurpation d’Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)      |
|**DomainKeys Identified Mail (DKIM)** utilise les informations de certificat X.509 pour s’assurer que les systèmes de messagerie de destination font confiance aux messages sortants envoyés à partir de votre domaine personnalisé.      | [Comment utiliser DKIM pour le courrier électronique dans votre domaine personnalisé - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)        |
|**DMARC (Domain-based Message Authentication, Reporting, and Conformance)** fonctionne avec Sender Policy Framework et DomainKeys Identified Mail pour authentifier les expéditeurs de messages et s’assurer que les systèmes de messagerie de destination font confiance aux messages envoyés à partir de votre domaine.      |  [Utiliser DMARC pour valider le courrier électronique, étapes de configuration - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)       |

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Résolution des problèmes d’envoi de courriers électroniques avec SMTP DANE

Actuellement, il existe quatre codes d’erreur pour DANE lors de l’envoi de messages électroniques Exchange Online. Microsoft met activement à jour cette liste de codes d’erreur. Les erreurs sont visibles dans :
1.  Le Exchange du Centre d’administration via la vue Détails du suivi des messages.
2.  Des NDR sont générées lorsqu’un message n’est pas envoyé en raison d’une défaillance DANE ou DNSSEC.
3.  Outil Analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|NDR Code  |Description  |
|---------|---------|
|5.7.321     |starttls-not-supported: Destination mail server must support TLS to receive mail.          |
|5.7.322     |certificat expiré : le certificat du serveur de messagerie de destination a expiré.          |
|5.7.323     |tlsa-invalid : le domaine a échoué à la validation DANE.          |
|5.7.324     |dnssec-invalid : le domaine de destination a renvoyé des enregistrements DNSSEC non valides.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Résolution des problèmes 5.7.321 starttls-not-supported

Cela indique généralement un problème avec le serveur de messagerie de destination. Après avoir reçu le message :
1.  Vérifiez que l’adresse e-mail de destination a été entrée correctement.
2.  Avertissez l’administrateur de messagerie de destination que vous avez reçu ce code d’erreur afin qu’il puisse déterminer si le serveur de destination est configuré correctement pour recevoir des messages à l’aide de TLS. 
3.  Réessayez d’envoyer le message électronique et examinez les détails du suivi des messages dans le portail Exchange Admin Center.

### <a name="troubleshooting-57322-certificate-expired"></a>Résolution des problèmes d’expiration du certificat 5.7.322

Un certificat X.509 valide qui n’a pas expiré doit être présenté au serveur de messagerie d’envoi. Les certificats X.509 doivent être renouvelés après leur expiration, généralement tous les ans. Après avoir reçu le message :

1.  Avertissez l’administrateur de courrier de destination que vous avez reçu ce code d’erreur et fournissez la chaîne de code d’erreur.
2.  Autorisez le renouvellement du certificat de serveur de destination et la mise à jour de l’enregistrement TLSA pour référencer le nouveau certificat. Ensuite, réessayez d’envoyer le courrier électronique et examinez les détails du suivi des messages pour le message dans Exchange portail du Centre d’administration.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Résolution des problèmes 5.7.323 tlsa-invalid

Ce code d’erreur est lié à une mauvaise configuration d’un enregistrement TLSA et ne peut être généré qu’après le retour d’un enregistrement TLSA authentifié par DNSSEC. Il existe de nombreux scénarios au cours de la validation DANE qui se produisent après le retour de l’enregistrement, ce qui peut entraîner la générer du code. Microsoft travaille activement sur les scénarios couverts par ce code d’erreur, afin que chaque scénario ait un code spécifique. Actuellement, un ou plusieurs de ces scénarios peuvent provoquer la génération du code d’erreur :

1.  Le certificat du serveur de messagerie de destination ne correspond pas à ce qui est attendu par l’enregistrement TLSA authentique.
2.  L’enregistrement TLSA authentique n’est pas correctement configuré.
3.  Le domaine de destination est en cours d’attaque.
4.  Toute autre défaillance DANE.

Après avoir reçu le message :

1. Avertissez l’administrateur de courrier de destination que vous avez reçu ce code d’erreur et fournissez-lui la chaîne de code d’erreur.
2. Laissez à l’administrateur de messagerie de destination le temps de passer en revue la configuration DANE et la validité du certificat du serveur de messagerie. Ensuite, réessayez d’envoyer le courrier électronique et examinez les détails du suivi des messages pour le message dans Exchange portail du Centre d’administration.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Résolution des problèmes 5.7.324 dnssec-invalid

Ce code d’erreur est généré lorsque le domaine de destination a indiqué qu’il était authentifié par DNSSEC, mais que Exchange Online n’a pas pu le vérifier comme DNSSEC authentifié. 

Après avoir reçu le message :

1. Avertissez l’administrateur de courrier de destination que vous avez reçu ce code d’erreur et fournissez-lui la chaîne de code d’erreur.
2. Laissez le temps à l’administrateur de messagerie de destination de passer en revue la configuration DNSSEC de son domaine. Ensuite, réessayez d’envoyer le courrier électronique et examinez les détails du suivi des messages pour le message dans Exchange portail du Centre d’administration.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Résolution des problèmes de réception de courriers électroniques avec SMTP DANE

Actuellement, il existe deux méthodes qu’un administrateur d’un domaine de réception peut utiliser pour valider et dépanner sa configuration DNSSEC et DANE pour recevoir des messages électroniques de Exchange Online à l’aide de ces normes. 

1. Adopter SMTP TLS-RPT (Transport Layer Security Reporting) introduit dans [RFC8460](https://datatracker.ietf.org/doc/html/rfc8460) 
2. Utiliser l’outil Analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) est un mécanisme de rapport permettant aux expéditeurs de fournir des détails aux administrateurs de domaine de destination sur les réussites et les échecs DANE et MTA-STS avec ces domaines de destination respectifs. Pour recevoir des rapports TLS-RPT, vous devez uniquement ajouter un enregistrement TXT dans les enregistrements DNS de votre domaine qui inclut l’adresse e-mail ou l’URI à qui vous souhaitez envoyer les rapports. Exchange Online envoie des rapports TLS-RPT au format JSON. 

Exemple d’enregistrement :

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Exemple d’enregistrement" lightbox="../media/compliance-trial/example-record.png":::

La deuxième méthode consiste à utiliser l’analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), qui peut faire les mêmes vérifications DNSSEC et DANE par rapport à votre configuration DNS que Exchange Online fera lors de l’envoi de messages électroniques à l’extérieur du service. Il s’agit du moyen le plus direct de dépanner les erreurs dans votre configuration pour recevoir des messages électroniques de Exchange Online à l’aide de ces normes. 

Lors du dépannage, les codes d’erreur ci-dessous peuvent être générés :

|NDR Code  |Description |
|---------|---------|
|4/5.7.321     |starttls-not-supported: Destination mail server must support TLS to receive mail.          |
|4/5.7.322     |certificat expiré : le certificat du serveur de messagerie de destination a expiré.          |
|4/5.7.323    |tlsa-invalid : le domaine a échoué à la validation DANE.         |
|4/5.7.324     |dnssec-invalid : le domaine de destination a renvoyé des enregistrements DNSSEC non valides.         |

### <a name="troubleshooting-57321-starttls-not-supported"></a>Résolution des problèmes 5.7.321 starttls-not-supported

> [!NOTE]
> Ces étapes s’adressent aux administrateurs de messagerie qui dépannagent la réception de messages Exchange Online l’aide de SMTP DANE.

Cela indique généralement un problème avec le serveur de messagerie de destination. Serveur de messagerie avec qui teste l’Analyseur de connectivité à distance. Il existe généralement deux scénarios qui génèrent ce code : 

1.  Le serveur de messagerie de destination ne prend pas du tout en charge la communication sécurisée, et les communications simples et non chiffrées doivent être utilisées. 
2.  Le serveur de destination est configuré de manière incorrecte et ignore la commande STARTTLS.
    
Après avoir reçu le message :

1. Vérifiez l’adresse e-mail.
2. Recherchez l’adresse IP associée à l’instruction d’erreur afin de pouvoir identifier le serveur de messagerie à qui l’instruction est associée.
3. Vérifiez le paramètre de votre serveur de messagerie pour vous assurer qu’il est configuré pour écouter le trafic SMTP (généralement les ports 25 et 587).
4. Patientez quelques minutes, puis réessayez le test avec l’outil Analyseur de connectivité à distance.
5. En cas d’échec, essayez de supprimer l’enregistrement TLSA et exécutez à nouveau le test avec l’outil Analyseur de connectivité à distance.
6. En l’absence d’échec, cela peut indiquer que le serveur de messagerie que vous utilisez pour recevoir le courrier ne prend pas en charge STARTTLS et que vous devrez peut-être mettre à niveau vers un serveur de messagerie qui utilise DANE. 

### <a name="troubleshooting-57322-certificate-expired"></a>Résolution des problèmes d’expiration du certificat 5.7.322

> [!NOTE]
> Ces étapes s’adressent aux administrateurs de messagerie qui dépannagent la réception de messages Exchange Online l’aide de SMTP DANE.

Un certificat X.509 valide qui n’a pas expiré doit être présenté au serveur de messagerie d’envoi. Les certificats X.509 doivent être renouvelés après leur expiration, généralement tous les ans. Après avoir reçu le message :

1. Vérifiez l’adresse IP associée à l’instruction d’erreur, afin de pouvoir identifier le serveur de messagerie à qui elle est associée. Recherchez le certificat expiré sur le serveur de messagerie que vous avez identifié.
2. Connectez-vous au site web de votre fournisseur de certificats.
3. Sélectionnez le certificat expiré et suivez les instructions de renouvellement et de paiement du renouvellement.
4. Une fois que votre fournisseur a vérifié l’achat, vous pouvez télécharger un nouveau certificat.
5. Installez le certificat renouvelé sur son serveur de messagerie associé.
6. Mettez à jour l’enregistrement TLSA associé au serveur de messagerie avec les données du nouveau certificat. 
7. Après avoir attendu un laps de temps approprié, réessayez le test à l’aide de l’outil Analyseur de connectivité à distance.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Résolution des problèmes 5.7.323 tlsa-invalid

> [!NOTE]
> Ces étapes s’adressent aux administrateurs de messagerie qui dépannagent la réception de messages Exchange Online l’aide de SMTP DANE.

Ce code d’erreur est lié à une mauvaise configuration d’un enregistrement TLSA et ne peut être généré qu’après le retour d’un enregistrement TSLA authentifié par DNSSEC. Toutefois, de nombreux scénarios au cours de la validation DANE qui se produisent après le retour de l’enregistrement peuvent entraîner la générer. Microsoft travaille activement sur les scénarios couverts par ce code d’erreur, afin que chaque scénario ait un code spécifique. Actuellement, un ou plusieurs de ces scénarios peuvent provoquer la génération du code d’erreur :

1. L’enregistrement TLSA authentique n’est pas correctement configuré.
2. Le certificat n’est pas encore valide/configuré pour une fenêtre de temps future. 
3. Le domaine de destination fait l’objet d’une attaque.
4. Toute autre défaillance DANE.

Après avoir reçu le message :

1. Vérifiez l’adresse IP associée à l’instruction d’erreur pour identifier le serveur de messagerie à qui elle est associée. 
2. Identifiez l’enregistrement TLSA associé au serveur de messagerie identifié. 
3. Vérifiez la configuration de l’enregistrement TLSA pour vous assurer qu’il indique à l’expéditeur d’effectuer les vérifications DANE préférées et que les données de certificat correctes ont été incluses dans l’enregistrement TLSA. 
    1. Si vous devez mettre à jour l’enregistrement pour des incohérences, patientez quelques minutes, puis réexécutez le test avec l’outil Analyseur de connectivité à distance. 
4. Recherchez le certificat sur le serveur de messagerie identifié.
5. Vérifiez la fenêtre de temps pour laquelle le certificat est valide. Si elle est définie pour démarrer la validité à une date ultérieure, elle doit être renouvelé pour la date actuelle.
    1. Connectez-vous au site web de votre fournisseur de certificats.
    2. Sélectionnez le certificat expiré et suivez les instructions de renouvellement et de paiement du renouvellement.
    3. Une fois que votre fournisseur a vérifié l’achat, vous pouvez télécharger un nouveau certificat.
    4. Installez le certificat renouvelé sur son serveur de messagerie associé.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Résolution des problèmes 5.7.324 dnssec-invalid

> [!NOTE]
> Ces étapes s’adressent aux administrateurs de messagerie qui dépannagent la réception de messages Exchange Online l’aide de SMTP DANE.

Ce code d’erreur est généré lorsque le domaine de destination a indiqué qu’il est authentifié par DNSSEC, mais que Exchange Online ne peut pas le vérifier comme DNSSEC authentifié. Cette section n’est pas exhaustive pour la résolution des problèmes DNSSEC et se concentre sur les scénarios où les domaines ont précédemment passé l’authentification DNSSEC, mais pas maintenant. 

Après avoir reçu le message :

1. Si vous utilisez un fournisseur DNS, par exemple GoDaddy, avertissez votre fournisseur DNS de l’erreur afin qu’il puisse travailler sur la résolution des problèmes et la modification de la configuration. 
2. Si vous gérez votre propre infrastructure DNSSEC, de nombreuses configurations DNSSEC erronées peuvent générer ce message d’erreur. Voici quelques problèmes courants à vérifier si votre zone a passé précédemment l’authentification DNSSEC :
    1. Chaîne d’confiance rompue, lorsque la zone parente contient un ensemble d’enregistrements DS qui pointent vers un point qui n’existe pas dans la zone enfant. Ainsi, la zone enfant est marquée comme fausse en validant les résolvants. 
        - Résolvez en revue les ID de clé RRSIG des domaines enfants et en vous assurant qu’ils correspondent aux ID de clé dans les enregistrements DS publiés dans la zone parent. 
    2. L’enregistrement de ressource RRSIG pour le domaine n’est pas valide, il a expiré ou sa période de validité n’a pas commencé. 
        - Résolvez en générant de nouvelles signatures pour le domaine à l’aide de timespans valides. 

## <a name="frequently-asked-questions"></a>Forum Aux Questions

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>En tant Exchange Online client, puis-je refuser d’utiliser DNSSEC et/ou DANE ?

Nous pensons vivement que DNSSEC et DANE augmenteront considérablement la position de sécurité de notre service et bénéficieront à tous nos clients. Nous avons travaillé avec soin au cours de l’année dernière pour réduire les risques et la gravité de l’impact potentiel de ce déploiement pour les clients M365. Nous surveillerons et suivons activement le déploiement pour nous assurer que l’impact négatif est réduit au cours de son déploiement. C’est pour cette raison que les exceptions au niveau du client ou l’option de dés refuse ne seront pas disponibles.
Si vous constatez des problèmes liés à l’enablement de DNSSEC et/ou DANE, les différentes méthodes d’investigation des échecs mentionnés dans ce document vous aideront à identifier la source de l’erreur. Dans la plupart des cas, le problème se fera avec la partie de destination externe et vous devrez communiquer à ces partenaires commerciaux qu’ils doivent configurer correctement DNSSEC et DANE afin de recevoir des messages électroniques de Exchange Online à l’aide de ces normes.

### <a name="how-does-dnssec-relate-to-dane"></a>Quelle est la relation entre DNSSEC et DANE ?

DNSSEC ajoute une couche d’confiance dans la résolution DNS en tirant parti de l’infrastructure à clé publique pour s’assurer que les enregistrements renvoyés en réponse à une requête DNS sont authentifiés. DANE garantit que le serveur de messagerie de réception est le serveur de messagerie légitime et attendu pour l’enregistrement MX authentique. 

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Quelle est la différence entre MTA-STS et DANE pour SMTP ?

DANE et MTA-STS ont le même objectif, mais DANE requiert DNSSEC pour l’authentification DNS, tandis que MTA-STS s’appuie sur des autorités de certification. 

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Pourquoi le TLS opportuniste ne suffit-il pas ?

Le chiffrement TLS opportuniste chiffre la communication entre deux points de terminaison si les deux acceptent de le prendre en charge. Toutefois, même si TLS chiffre la transmission, un domaine peut être usurpé lors de la résolution DNS de telle façon qu’il pointe vers le point de terminaison d’un acteur malveillant au lieu du point de terminaison réel du domaine. Il s’agit d’un écart en matière de sécurité du courrier électronique qui est résolu en implémentant MTA-STS et/ou SMTP DANE avec DNSSEC.  

### <a name="why-isnt-dnssec-sufficient"></a>Pourquoi DNSSEC ne suffit-il pas ?

DNSSEC n’est pas totalement résistant aux attaques man-in-the-Middle et aux attaques de rétrogradation (de TLS pour effacer le texte) pour les scénarios de flux de messagerie. L’ajout de MTA-STS et DANE avec DNSSEC fournit une méthode de sécurité complète pour empêcher les attaques MITM et rétrogradation.

## <a name="additional-links"></a>Liens supplémentaires 

[Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Vue d’ensemble des | DNSSEC Documents Microsoft ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Utiliser DMARC pour valider le courrier électronique, étapes de configuration - Office 365 | Documents Microsoft](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Comment utiliser DKIM pour le courrier électronique dans votre domaine personnalisé - Office 365 | Documents Microsoft](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Comment SPF (Sender Policy Framework) empêche l’usurpation d’Office 365 | Documents Microsoft](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online’actualités sur le transport de Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)