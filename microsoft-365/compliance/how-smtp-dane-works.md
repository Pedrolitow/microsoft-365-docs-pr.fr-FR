---
title: Fonctionnement de l’authentification DNS SMTP des entités nommées (DANE) pour sécuriser les communications par e-mail
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
description: Découvrez comment l’authentification DNS SMTP des entités nommées (DANE) fonctionne pour sécuriser les communications par e-mail entre les serveurs de messagerie.
ms.openlocfilehash: 2af2a166ff73bbe7888ed9265ec8733105eb2007
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759432"
---
# <a name="how-smtp-dns-based-authentication-of-named-entities-dane-works"></a>Fonctionnement de l’authentification DNS SMTP des entités nommées (DANE)

Le protocole SMTP est le protocole principal utilisé pour transférer des messages entre les serveurs de messagerie et n’est pas sécurisé par défaut. Le protocole TLS (Transport Layer Security) a été introduit il y a des années pour prendre en charge la transmission chiffrée des messages via SMTP. Il est couramment utilisé de manière opportuniste plutôt que comme une exigence, laissant beaucoup de trafic de courrier en texte clair, vulnérable à l’interception par des acteurs malveillants. En outre, SMTP détermine les adresses IP des serveurs de destination via l’infrastructure DNS publique, qui est vulnérable à l’usurpation d’identité et aux attaques de l’intercepteur (MITM). Cela a conduit à la création de nombreuses nouvelles normes pour renforcer la sécurité pour l’envoi et la réception d’e-mails, dont l’une est l’authentification DNS des entités nommées (DANE).

DANE pour SMTP [RFC 7672](https://tools.ietf.org/html/rfc7672) utilise la présence d’un enregistrement TLSA (Transport Layer Security Authentication) dans le jeu d’enregistrements DNS d’un domaine pour signaler un domaine et ses serveurs de messagerie prennent en charge DANE. Si aucun enregistrement TLSA n’est présent, la résolution DNS pour le flux de courrier fonctionne comme d’habitude sans aucune tentative de vérification DANE. L’enregistrement TLSA signale en toute sécurité la prise en charge de TLS et publie la stratégie DANE pour le domaine. Ainsi, l’envoi de serveurs de messagerie peut authentifier correctement les serveurs de messagerie de réception légitimes à l’aide de SMTP DANE. Cela le rend résistant aux attaques de rétrograde et MITM. DANE a des dépendances directes sur DNSSEC, qui fonctionne en signant numériquement des enregistrements pour les recherches DNS à l’aide du chiffrement à clé publique. Les vérifications DNSSEC se produisent sur les programmes de résolution DNS récursifs, les serveurs DNS qui effectuent des requêtes DNS pour les clients. DNSSEC garantit que les enregistrements DNS ne sont pas falsifiés et qu’ils sont authentiques.

Une fois que les enregistrements de ressources liés à MX, A/AAAA et DNSSEC pour un domaine sont retournés au programme de résolution récursif DNS au moment de l’authentification DNSSEC, le serveur de messagerie d’envoi demande l’enregistrement TLSA correspondant à l’entrée ou aux entrées de l’hôte MX. Si l’enregistrement TLSA est présent et s’il est prouvé qu’il est authentique à l’aide d’une autre vérification DNSSEC, le programme de résolution récursif DNS retourne l’enregistrement TLSA au serveur de messagerie d’envoi.

Après avoir reçu l’enregistrement TLSA authentique, le serveur de messagerie d’envoi établit une connexion SMTP à l’hôte MX associé à l’enregistrement TLSA authentique. Le serveur de messagerie d’envoi tente de configurer TLS et de comparer le certificat TLS du serveur avec les données de l’enregistrement TLSA pour vérifier que le serveur de messagerie de destination connecté à l’expéditeur est le serveur de messagerie de réception légitime. Le message est transmis (à l’aide de TLS) si l’authentification réussit. En cas d’échec de l’authentification ou si TLS n’est pas pris en charge par le serveur de destination, Exchange Online réessayez l’intégralité du processus de validation en commençant par une requête DNS pour le même domaine de destination après 15 minutes, puis 15 minutes après, puis toutes les heures pendant les 24 heures suivantes. Si l’authentification continue d’échouer après 24 heures de nouvelle tentative, le message expire et une NDR avec les détails de l’erreur est générée et envoyée à l’expéditeur.

## <a name="what-are-the-components-of-dane"></a>Quels sont les composants de DANE ?

### <a name="tlsa-resource-record"></a>Enregistrement de ressource TLSA

L’enregistrement TLS (TLSA) est utilisé pour associer le certificat X.509 ou la valeur de clé publique d’un serveur au nom de domaine qui contient l’enregistrement. Les enregistrements TLSA ne peuvent être approuvés que si DNSSEC est activé sur votre domaine. Si vous utilisez un fournisseur DNS pour héberger votre domaine, il peut s’agir d’un paramètre proposé lors de la configuration d’un domaine avec lui. Pour en savoir plus sur la signature de zone DNSSEC, consultez ce lien : [Vue d’ensemble de la | DNSSEC Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11)).

Exemple d’enregistrement TLSA :

:::image type="content" source="../media/compliance-trial/example-TLSA-record.png" alt-text="Exemple d’enregistrement TLSA" lightbox="../media/compliance-trial/example-TLSA-record.png":::

Il existe quatre champs configurables uniques au type d’enregistrement TLSA :

**Champ d’utilisation du certificat** : spécifie comment le serveur de messagerie d’envoi doit vérifier le certificat du serveur de messagerie de destination.

|Valeur|Acronyme|Description|
|---|---|---|
|01<sup></sup>|PKIX-TA|Le certificat utilisé est l’autorité de certification publique d’ancrage de confiance de la chaîne d’approbation X.509.|
|11<sup></sup>|PKIX-EE|Le certificat vérifié est le serveur de destination ; Les vérifications DNSSEC doivent vérifier son authenticité.|
|2|DANE-TA|Utilisez la clé privée du serveur de l’arborescence X.509 qui doit être validée par une ancre de confiance dans la chaîne d’approbation. L’enregistrement TLSA spécifie l’ancre d’approbation à utiliser pour valider les certificats TLS pour le domaine.|
|3|DANE-EE|Correspond uniquement au certificat du serveur de destination.|

<sup>1</sup> Exchange Online suit les instructions d’implémentation RFC selon lesquelles les valeurs de champ d’utilisation de certificat 0 ou 1 ne doivent pas être utilisées lorsque DANE est implémenté avec SMTP. Lorsqu’un enregistrement TLSA dont la valeur de champ Utilisation du certificat est 0 ou 1 est retourné à Exchange Online, Exchange Online le traite comme non utilisable. Si tous les enregistrements TLSA sont jugés inutilisables, Exchange Online n’effectue pas les étapes de validation DANE pour 0 ou 1 lors de l’envoi de l’e-mail. Au lieu de cela, en raison de la présence d’un enregistrement TLSA, Exchange Online appliquera l’utilisation de TLS pour l’envoi de l’e-mail, l’envoi de l’e-mail si le serveur de messagerie de destination prend en charge TLS ou la suppression de l’e-mail et la génération d’une NDR si le serveur de messagerie de destination ne prend pas en charge TLS.

Dans l’exemple d’enregistrement TLSA, le champ d’utilisation du certificat est défini sur « 3 », de sorte que les données d’association de certificats (« abc123 ... xyz789') serait mis en correspondance avec le certificat du serveur de destination uniquement.

**Champ sélecteur** : indique quelles parties du certificat du serveur de destination doivent être vérifiées.

|Valeur|Acronyme|Description|
|---|---|---|
|0|Cert|Utilisez un certificat complet.|
|1|SPKI (Informations sur la clé publique de l’objet)|Utilisez la clé publique du certificat et l’algorithme avec lequel la clé publique est identifiée pour être utilisée.|

Dans l’exemple d’enregistrement TLSA, le champ sélecteur est défini sur « 1 » afin que les données d’association de certificats soient mises en correspondance à l’aide de la clé publique du certificat de serveur de destination et de l’algorithme avec lequel la clé publique est identifiée pour être utilisée.

**Champ de type correspondant** : indique le format auquel le certificat sera représenté dans l’enregistrement TLSA.

|Valeur|Acronyme|Description|
|---|---|---|
|0|Complet|Les données de l’enregistrement TSLA sont le certificat complet ou SPKI.|
|1|SHA-256|Les données de l’enregistrement TSLA sont un hachage SHA-256 du certificat ou de l’infrastructure SPKI.|
|2|SHA-512|Les données de l’enregistrement TSLA sont un hachage SHA-512 du certificat ou de l’infrastructure SPKI.|

Dans l’exemple d’enregistrement TLSA, le champ de type correspondant est défini sur « 1 » afin que les données d’association de certificats soient un hachage SHA-256 des informations de clé publique de l’objet à partir du certificat du serveur de destination

**Données d’association** de certificats : spécifie les données de certificat utilisées pour la correspondance avec le certificat de serveur de destination. Ces données dépendent de la valeur du champ sélecteur et de la valeur de type correspondant.

Dans l’exemple d’enregistrement TLSA, les données de l’association de certificats sont définies sur « abc123 ». xyz789'. Étant donné que la valeur de champ du sélecteur dans l’exemple est définie sur « 1 », elle référence la clé publique du certificat de serveur de destination et l’algorithme qui est identifié pour être utilisé avec elle. Étant donné que la valeur du champ Type de correspondance dans l’exemple est définie sur « 1 », elle référence le hachage SHA-256 des informations de clé publique de l’objet à partir du certificat du serveur de destination.

## <a name="how-can-exchange-online-customers-use-smtp-dane-outbound"></a>Comment Exchange Online clients peuvent-ils utiliser SMTP DANE Outbound ?

En tant que client Exchange Online, vous n’avez rien à faire pour configurer cette sécurité de messagerie améliorée pour votre e-mail sortant. C’est quelque chose que nous avons créé pour vous et il est activé par défaut pour tous les clients Exchange Online et est utilisé lorsque le domaine de destination publie la prise en charge de DANE. Pour tirer parti des avantages de l’envoi d’e-mails avec des vérifications DNSSEC et DANE, communiquez avec vos partenaires commerciaux avec lesquels vous échangez des e-mails qu’ils doivent implémenter DNSSEC et DANE afin qu’ils puissent recevoir des e-mails à l’aide de ces normes.

## <a name="how-can-exchange-online-customers-use-smtp-dane-inbound"></a>Comment Exchange Online clients peuvent-ils utiliser SMTP DANE entrant ?

Actuellement, SMTP DANE entrant n’est pas pris en charge pour Exchange Online. La prise en charge devrait être publiée fin 2022.

## <a name="what-is-the-recommended-tlsa-record-configuration"></a>Quelle est la configuration d’enregistrement TLSA recommandée ?

Par guide d’implémentation RFC pour SMTP DANE, un enregistrement TLSA composé du champ Utilisation du certificat défini sur 3, du champ Sélecteur défini sur 1 et du champ Type de correspondance défini sur 1 est recommandé.

## <a name="exchange-online-mail-flow-with-smtp-dane"></a>Exchange Online Mail Flow avec SMTP DANE

Le processus de flux de messagerie pour Exchange Online avec SMTP DANE, illustré dans le graphique de flux ci-dessous, valide la sécurité des enregistrements de domaine et de ressource via DNSSEC, la prise en charge de TLS sur le serveur de messagerie de destination, et que le certificat du serveur de messagerie de destination correspond à ce qui est attendu en fonction de son enregistrement TLSA associé.

Il n’existe que deux scénarios où un échec SMTP DANE entraîne le blocage de l’e-mail :

- Le domaine de destination a signalé la prise en charge de DNSSEC, mais un ou plusieurs enregistrements ont été retournés comme non authentifiés.

- Tous les enregistrements MX du domaine de destination ont des enregistrements TLSA et aucun des certificats du serveur de destination ne correspond à ce qui était attendu pour les données d’enregistrement TSLA, ou une connexion TLS n’est pas prise en charge par le serveur de destination.

:::image type="content" source="../media/compliance-trial/mail-flow-smtp-dane.png" alt-text="Exchange flux de messagerie en ligne avec SMTP DANE" lightbox="../media/compliance-trial/mail-flow-smtp-dane.png":::

## <a name="related-technologies"></a>Technologies associées

|Technologie|Informations complémentaires|
|---|---|
|**Mail Transfer Agent - Strict Transport Security (MTA-STS)** permet de contrer les attaques de rétrogradation et d’intercepteur en fournissant un mécanisme pour définir des stratégies de domaine qui spécifient si le serveur de messagerie de destination prend en charge TLS et ce qu’il faut faire quand TLS ne peut pas être négocié, par exemple arrêter la transmission.|Plus d’informations sur la prise en charge à venir de Exchange Online pour MTA-STS entrant et sortant sera publiée plus tard cette année. <br/><br/> [Exchange Online Transport News de Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699) <br/><br/> [rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)|
|**Le SPF (Sender Policy Framework)** utilise des informations IP pour garantir que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine personnalisé.|[Comment Le SPF (Sender Policy Framework) empêche l’usurpation d’identité - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)|
|**DomainKeys Identified Mail (DKIM)** utilise les informations de certificat X.509 pour s’assurer que les systèmes de messagerie de destination approuvent les messages envoyés sortants de votre domaine personnalisé.|[Comment utiliser DKIM pour l’e-mail dans votre domaine personnalisé - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)|
|**DMARC (Domain-Based Message Authentication, Reporting, and Conformance)** fonctionne avec Sender Policy Framework et DomainKeys Identified Mail pour authentifier les expéditeurs de courrier et s’assurer que les systèmes de messagerie de destination approuvent les messages envoyés à partir de votre domaine.|[Utiliser DMARC pour valider l’e-mail, les étapes de configuration - Office 365 - Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)|

## <a name="troubleshooting-sending-emails-with-smtp-dane"></a>Résolution des problèmes d’envoi de courriers électroniques avec SMTP DANE

Actuellement, il existe quatre codes d’erreur pour DANE lors de l’envoi d’e-mails avec Exchange Online. Microsoft met activement à jour cette liste de codes d’erreur. Les erreurs sont visibles dans :

1. Le Exchange portail du Centre d’administration via la vue Détails de la trace des messages.
2. DRS générés lorsqu’un message n’est pas envoyé en raison d’une défaillance DANE ou DNSSEC.
3. Outil Analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365).

|NDR Code|Description|
|---|---|
|5.7.321|starttls-not-supported : le serveur de messagerie de destination doit prendre en charge TLS pour recevoir le courrier.|
|5.7.322|certificat expiré : le certificat du serveur de messagerie de destination a expiré.|
|5.7.323|tlsa-invalid : échec de la validation DANE du domaine.|
|5.7.324|dnssec-invalid : le domaine de destination a retourné des enregistrements DNSSEC non valides.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Résolution des problèmes 5.7.321 starttls-not-supported

Cela indique généralement un problème avec le serveur de messagerie de destination. Après avoir reçu le message :

1. Vérifiez que l’adresse e-mail de destination a été correctement entrée.
2. Avertissez l’administrateur de messagerie de destination que vous avez reçu ce code d’erreur afin qu’il puisse déterminer si le serveur de destination est configuré correctement pour recevoir des messages à l’aide de TLS.
3. Réessayez d’envoyer l’e-mail et passez en revue les détails de la trace du message dans le portail Exchange Centre d’administration.

### <a name="troubleshooting-57322-certificate-expired"></a>Résolution des problèmes liés à l’expiration du certificat 5.7.322

Un certificat X.509 valide qui n’a pas expiré doit être présenté au serveur de messagerie d’envoi. Les certificats X.509 doivent être renouvelés après leur expiration, généralement tous les ans. Après avoir reçu le message :

1. Avertissez l’administrateur de l’e-mail de destination que vous avez reçu ce code d’erreur et fournissez la chaîne de code d’erreur.
2. Laissez le temps au certificat du serveur de destination d’être renouvelé et à l’enregistrement TLSA d’être mis à jour pour référencer le nouveau certificat. Ensuite, réessayez d’envoyer l’e-mail et passez en revue les détails de la trace du message dans le portail Exchange Centre d’administration.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Résolution des problèmes 5.7.323 tlsa-invalid

Ce code d’erreur est lié à une configuration incorrecte d’enregistrement TLSA et ne peut être généré qu’une fois qu’un enregistrement TLSA authentifié DNSSEC a été retourné. Il existe de nombreux scénarios pendant la validation DANE qui se produisent après le retour de l’enregistrement, ce qui peut entraîner la génération du code. Microsoft travaille activement sur les scénarios couverts par ce code d’erreur, afin que chaque scénario ait un code spécifique. Actuellement, un ou plusieurs de ces scénarios peuvent entraîner la génération du code d’erreur :

1. Le certificat du serveur de messagerie de destination ne correspond pas à ce qui est attendu par l'enregistrement TLSA authentique.
2. L’enregistrement TLSA authentique n’est pas correctement configuré.
3. Le domaine de destination est attaqué.
4. Toute autre défaillance DANE.

Après avoir reçu le message :

1. Avertissez l’administrateur de l’e-mail de destination que vous avez reçu ce code d’erreur et fournissez-lui la chaîne de code d’erreur.
2. Laissez le temps à l’administrateur de messagerie de destination de passer en revue la configuration DANE et la validité du certificat du serveur de messagerie. Ensuite, réessayez d’envoyer l’e-mail et passez en revue les détails de la trace du message dans le portail Exchange Centre d’administration.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Résolution des problèmes 5.7.324 dnssec-invalid

Ce code d’erreur est généré lorsque le domaine de destination a indiqué qu’il était authentifié DNSSEC, mais Exchange Online n’a pas pu le vérifier en tant qu’authentificateur DNSSEC.

Après avoir reçu le message :

1. Avertissez l’administrateur de l’e-mail de destination que vous avez reçu ce code d’erreur et fournissez-lui la chaîne de code d’erreur.
2. Laissez le temps à l’administrateur de messagerie de destination de passer en revue la configuration DNSSEC de son domaine. Ensuite, réessayez d’envoyer l’e-mail et passez en revue les détails de la trace du message dans le portail Exchange Centre d’administration.

## <a name="troubleshooting-receiving-emails-with-smtp-dane"></a>Résolution des problèmes de réception d’e-mails avec SMTP DANE

Actuellement, il existe deux méthodes qu’un administrateur d’un domaine de réception peut utiliser pour valider et résoudre les problèmes de leur configuration DNSSEC et DANE afin de recevoir des e-mails de Exchange Online à l’aide de ces normes.

1. Adopter SMTP TLS-RPT (Transport Layer Security Reporting) introduit dans [RFC8460](https://datatracker.ietf.org/doc/html/rfc8460)
2. Utiliser l’outil Analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365)

TLS-RPT [https://datatracker.ietf.org/doc/html/rfc8460](https://datatracker.ietf.org/doc/html/rfc8460) est un mécanisme de création de rapports permettant aux expéditeurs de fournir aux administrateurs de domaine de destination des détails sur les réussites et les échecs DANE et MTA-STS avec ces domaines de destination respectifs. Pour recevoir des rapports TLS-RPT, vous devez uniquement ajouter un enregistrement TXT dans les enregistrements DNS de votre domaine qui inclut l’adresse e-mail ou l’URI auquel vous souhaitez envoyer les rapports. Exchange Online envoie des rapports TLS-RPT au format JSON.

Exemple d’enregistrement :

:::image type="content" source="../media/compliance-trial/example-record.png" alt-text="Exemple d’enregistrement" lightbox="../media/compliance-trial/example-record.png":::

La deuxième méthode consiste à utiliser l’analyseur de connectivité à distance [Microsoft Remote Connectivity Analyzer](https://testconnectivity.microsoft.com/tests/o365), qui peut effectuer les mêmes vérifications DNSSEC et DANE par rapport à votre configuration DNS que Exchange Online effectuera lors de l’envoi d’e-mails en dehors du service. Il s’agit du moyen le plus direct de résoudre les erreurs dans votre configuration pour recevoir des e-mails de Exchange Online à l’aide de ces normes.

Lors de la résolution des problèmes, les codes d’erreur ci-dessous peuvent être générés :

|NDR Code|Description|
|---|---|
|4/5.7.321|starttls-not-supported : le serveur de messagerie de destination doit prendre en charge TLS pour recevoir le courrier.|
|4/5.7.322|certificat expiré : le certificat du serveur de messagerie de destination a expiré.|
|4/5.7.323|tlsa-invalid : échec de la validation DANE du domaine.|
|4/5.7.324|dnssec-invalid : le domaine de destination a retourné des enregistrements DNSSEC non valides.|

### <a name="troubleshooting-57321-starttls-not-supported"></a>Résolution des problèmes 5.7.321 starttls-not-supported

> [!NOTE]
> Ces étapes sont destinées aux administrateurs de messagerie qui résolvez les problèmes de réception de courrier électronique à partir de Exchange Online à l’aide de SMTP DANE.

Cela indique généralement un problème avec le serveur de messagerie de destination. Serveur de messagerie avec lequel l’analyseur de connectivité à distance teste la connexion. Il existe généralement deux scénarios qui génèrent ce code :

1.  Le serveur de messagerie de destination ne prend pas en charge la communication sécurisée du tout, et une communication simple et non chiffrée doit être utilisée.
2.  Le serveur de destination est mal configuré et ignore la commande STARTTLS.

Après avoir reçu le message :

1. Vérifiez l’adresse e-mail.
2. Recherchez l’adresse IP associée à l’instruction d’erreur afin de pouvoir identifier le serveur de messagerie auquel l’instruction est associée.
3. Vérifiez le paramètre de votre serveur de messagerie pour vous assurer qu’il est configuré pour écouter le trafic SMTP (généralement les ports 25 et 587).
4. Patientez quelques minutes, puis réessayez le test avec l’outil Remote Connectivity Analyzer.
5. Si elle échoue toujours, essayez de supprimer l’enregistrement TLSA et réexélectionnez le test avec l’outil Analyseur de connectivité à distance.
6. S’il n’y a pas d’échec, cela peut indiquer que le serveur de messagerie que vous utilisez pour recevoir des messages ne prend pas en charge STARTTLS et que vous devrez peut-être effectuer une mise à niveau vers un serveur qui le fait pour utiliser DANE.

### <a name="troubleshooting-57322-certificate-expired"></a>Résolution des problèmes liés à l’expiration du certificat 5.7.322

> [!NOTE]
> Ces étapes sont destinées aux administrateurs de messagerie qui résolvez les problèmes de réception de courrier électronique à partir de Exchange Online à l’aide de SMTP DANE.

Un certificat X.509 valide qui n’a pas expiré doit être présenté au serveur de messagerie d’envoi. Les certificats X.509 doivent être renouvelés après leur expiration, généralement tous les ans. Après avoir reçu le message :

1. Vérifiez l’adresse IP associée à l’instruction d’erreur afin de pouvoir identifier le serveur de messagerie auquel il est associé. Recherchez le certificat expiré sur le serveur de messagerie que vous avez identifié.
2. Connectez-vous au site web de votre fournisseur de certificats.
3. Sélectionnez le certificat arrivé à expiration et suivez les instructions pour renouveler et payer le renouvellement.
4. Une fois que votre fournisseur a vérifié l’achat, vous pouvez télécharger un nouveau certificat.
5. Installez le certificat renouvelé dans son serveur de messagerie associé.
6. Mettez à jour l’enregistrement TLSA associé au serveur de messagerie avec les données du nouveau certificat.
7. Après avoir attendu une durée appropriée, réessayez le test avec l’outil Remote Connectivity Analyzer.

### <a name="troubleshooting-57323-tlsa-invalid"></a>Résolution des problèmes 5.7.323 tlsa-invalid

> [!NOTE]
> Ces étapes sont destinées aux administrateurs de messagerie qui résolvez les problèmes de réception de courrier électronique à partir de Exchange Online à l’aide de SMTP DANE.

Ce code d’erreur est lié à une configuration incorrecte d’enregistrement TLSA et ne peut être généré qu’une fois qu’un enregistrement TSLA DNSSEC authentique a été retourné. Toutefois, il existe de nombreux scénarios pendant la validation DANE qui se produisent après le retour de l’enregistrement, ce qui peut entraîner la génération du code. Microsoft travaille activement sur les scénarios couverts par ce code d’erreur, afin que chaque scénario ait un code spécifique. Actuellement, un ou plusieurs de ces scénarios peuvent entraîner la génération du code d’erreur :

1. L’enregistrement TLSA authentique n’est pas correctement configuré.
2. Le certificat n’est pas encore valide/configuré pour une fenêtre de temps ultérieure.
3. Le domaine de destination fait l’objet d’une attaque.
4. Toute autre défaillance DANE.

Après avoir reçu le message :

1. Vérifiez l’adresse IP associée à l’instruction d’erreur pour identifier le serveur de messagerie auquel il est associé.
2. Identifiez l’enregistrement TLSA associé au serveur de messagerie identifié.
3. Vérifiez la configuration de l’enregistrement TLSA pour vous assurer qu’il signale à l’expéditeur d’effectuer les vérifications DANE préférées et que les données de certificat correctes ont été incluses dans l’enregistrement TLSA.
    1. Si vous devez effectuer des mises à jour de l’enregistrement en cas d’incohérences, patientez quelques minutes, puis réexécutez le test avec l’outil Analyseur de connectivité à distance.
4. Recherchez le certificat sur le serveur de messagerie identifié.
5. Vérifiez la fenêtre de temps pour laquelle le certificat est valide. S’il est défini pour démarrer la validité à une date ultérieure, il doit être renouvelé pour la date actuelle.
    1. Connectez-vous au site web de votre fournisseur de certificats.
    2. Sélectionnez le certificat arrivé à expiration et suivez les instructions pour renouveler et payer le renouvellement.
    3. Une fois que votre fournisseur a vérifié l’achat, vous pouvez télécharger un nouveau certificat.
    4. Installez le certificat renouvelé dans son serveur de messagerie associé.

### <a name="troubleshooting-57324-dnssec-invalid"></a>Résolution des problèmes 5.7.324 dnssec-invalid

> [!NOTE]
> Ces étapes sont destinées aux administrateurs de messagerie qui résolvez les problèmes de réception de courrier électronique à partir de Exchange Online à l’aide de SMTP DANE.

Ce code d’erreur est généré lorsque le domaine de destination indique qu’il est authentifié DNSSEC, mais Exchange Online ne peut pas le vérifier en tant qu’authentificateur DNSSEC. Cette section ne sera pas complète pour la résolution des problèmes DNSSEC et se concentre sur les scénarios où les domaines ont précédemment passé l’authentification DNSSEC, mais pas maintenant.

Après avoir reçu le message :

1. Si vous utilisez un fournisseur DNS, par exemple GoDaddy, avertissez votre fournisseur DNS de l’erreur afin qu’il puisse travailler sur la résolution des problèmes et la modification de la configuration.
2. Si vous gérez votre propre infrastructure DNSSEC, de nombreuses configurations incorrectes DNSSEC peuvent générer ce message d’erreur. Problèmes courants à vérifier si votre zone transmettait précédemment l’authentification DNSSEC :
    1. Chaîne de confiance rompue, lorsque la zone parente contient un ensemble d’enregistrements DS qui pointent vers quelque chose qui n’existe pas dans la zone enfant. Par conséquent, la zone enfant est marquée comme incorrecte en validant les programmes de résolution.
        - Résolvez les problèmes en examinant les ID de clé RRSIG des domaines enfants et en veillant à ce qu’ils correspondent aux ID de clé dans les enregistrements DS publiés dans la zone parente.
    2. L’enregistrement de ressource RRSIG pour le domaine n’est pas valide dans le temps, il a expiré ou sa période de validité n’a pas commencé.
        - Résolvez les problèmes en générant de nouvelles signatures pour le domaine à l’aide d’intervalles de temps valides.

## <a name="frequently-asked-questions"></a>Forum Aux Questions

### <a name="as-an-exchange-online-customer-can-i-opt-out-of-using-dnssec-andor-dane"></a>En tant que client Exchange Online, puis-je refuser d’utiliser DNSSEC et/ou DANE ?

Nous croyons fermement que DNSSEC et DANE augmenteront considérablement la position de sécurité de notre service et profiteront à tous nos clients. Nous avons travaillé avec diligence au cours de la dernière année pour réduire le risque et la gravité de l’impact potentiel que ce déploiement pourrait avoir pour les clients M365. Nous allons surveiller et suivre activement le déploiement pour nous assurer que l’impact négatif est réduit au fur et à mesure de son déploiement. Pour cette raison, les exceptions au niveau du locataire ou la désactivation ne seront pas disponibles.
Si vous rencontrez des problèmes liés à l’activation de DNSSEC et/ou DANE, les différentes méthodes d’examen des échecs indiquées dans ce document vous aideront à identifier la source de l’erreur. Dans la plupart des cas, le problème concerne la partie de destination externe et vous devez communiquer à ces partenaires commerciaux qu’ils doivent configurer correctement DNSSEC et DANE afin de recevoir des e-mails de Exchange Online à l’aide de ces normes.

### <a name="how-does-dnssec-relate-to-dane"></a>Comment DNSSEC est-il lié à DANE ?

DNSSEC ajoute une couche d’approbation à la résolution DNS en tirant parti de l’infrastructure de clé publique pour s’assurer que les enregistrements retournés en réponse à une requête DNS sont authentiques. DANE garantit que le serveur de messagerie de réception est le serveur de messagerie légitime et attendu pour l’enregistrement MX authentique.

### <a name="what-is-the-difference-between-mta-sts-and-dane-for-smtp"></a>Quelle est la différence entre MTA-STS et DANE pour SMTP ?

DANE et MTA-STS servent le même objectif, mais DANE requiert DNSSEC pour l’authentification DNS, tandis que MTA-STS s’appuie sur les autorités de certification.

### <a name="why-isnt-opportunistic-tls-sufficient"></a>Pourquoi le protocole TLS opportuniste n’est-il pas suffisant ?

Le protocole TLS opportuniste chiffre la communication entre deux points de terminaison si les deux acceptent de la prendre en charge. Toutefois, même si TLS chiffre la transmission, un domaine peut être usurpé lors de la résolution DNS de sorte qu’il pointe vers le point de terminaison d’un acteur malveillant au lieu du point de terminaison réel du domaine. Il s’agit d’un écart dans la sécurité de la messagerie qui est résolu en implémentant MTA-STS et/ou SMTP DANE avec DNSSEC.

### <a name="why-isnt-dnssec-sufficient"></a>Pourquoi DNSSEC n’est-il pas suffisant ?

DNSSEC n’est pas entièrement résistant aux attaques man-in-the-middle et aux attaques de passage à une version antérieure (de TLS à texte clair) pour les scénarios de flux de courrier. L’ajout de MTA-STS et DANE ainsi que DNSSEC fournit une méthode de sécurité complète pour contrer les attaques MITM et de rétrograde.

## <a name="additional-links"></a>Liens supplémentaires

[Rechercher et corriger des problèmes après avoir ajouté votre domaine ou des enregistrements DNS](/microsoft-365/admin/get-help-with-domains/find-and-fix-issues)

[Vue d’ensemble des | DNSSEC Microsoft Docs](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj200221(v=ws.11))

[Utiliser DMARC pour valider l’e-mail, les étapes de configuration - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email)

[Comment utiliser DKIM pour l’e-mail dans votre domaine personnalisé - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/use-dkim-to-validate-outbound-email)

[Comment Le SPF (Sender Policy Framework) empêche l’usurpation d’identité - Office 365 | Microsoft Docs](/microsoft-365/security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing)

[Exchange Online Transport News de Microsoft Ignite 2020 - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-online-transport-news-from-microsoft-ignite-2020/ba-p/1687699)

[rfc8461 (ietf.org)](https://datatracker.ietf.org/doc/html/rfc8461)
