---
title: Comment Exchange Online utilise TLS (Transport Layer Security) pour sécuriser les connexions e-mail
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/08/2021
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Découvrez comment Exchange Online et Microsoft 365 utiliser TLS (Transport Layer Security) et le secret de transfert (FS) pour sécuriser les communications par e-mail. Obtenez également des informations sur le certificat émis par Microsoft pour Exchange Online.
ms.openlocfilehash: 7f6d4cb20299e98fc186409977c8ef7b36d329ca
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760820"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie

Découvrez comment Exchange Online et Microsoft 365 utiliser TLS (Transport Layer Security) et le secret de transfert (FS) pour sécuriser les communications par e-mail. Fournit également des informations sur le certificat émis par Microsoft pour Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Principes de base de TLS pour les Microsoft 365 et les Exchange Online

Les protocoles TLS (Transport Layer Security) et SSL (antérieur au protocole TLS) sont des protocoles de chiffrement qui sécurisent les communications sur un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre plusieurs ordinateurs. Le protocole TLS remplace le protocole SSL et est couramment appelé SSL 3.1. Exchange Online utilise TLS pour chiffrer les connexions entre les serveurs Exchange et les connexions entre les serveurs Exchange et d’autres serveurs tels que vos serveurs Exchange locaux ou les serveurs de messagerie de vos destinataires. Une fois la connexion chiffrée, toutes les données envoyées via cette connexion sont envoyées par le biais du canal chiffré. Toutefois, si vous transférez un message qui a été envoyé par le biais d’une connexion chiffrée via le protocole TLS, ce message n’est pas nécessairement chiffré. TLS ne chiffre pas le message, mais uniquement la connexion.
  
Si vous souhaitez chiffrer le message, utilisez une technologie de chiffrement qui chiffre le contenu du message. Par exemple, vous pouvez utiliser Office chiffrement de message ou S/MIME. Pour plus d’informations sur le chiffrement des messages dans Office 365, consultez le [chiffrement des messages dans Office 365](email-encryption.md) et Office 365 Message [Encryption (OME](ome.md)).
  
Utilisez TLS dans les situations où vous souhaitez configurer un canal sécurisé de correspondance entre Microsoft et votre organisation locale ou une autre organisation, telle qu’un partenaire. Exchange Online tente toujours d’utiliser TLS en premier pour sécuriser votre e-mail, mais pas si l’autre partie n’offre pas de sécurité TLS. Poursuivez votre lecture pour découvrir comment sécuriser tous les messages vers vos serveurs locaux ou vos partenaires importants à l’aide de *connecteurs*.

Pour fournir le chiffrement le plus performant à nos clients, Microsoft a déprécié les versions 1.0 et 1.1 de TLS (Transport Layer Security) dans [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) et [Office 365 Cloud de la communauté du secteur public](tls-1-2-in-office-365-gcc.md). Toutefois, vous pouvez continuer à utiliser une connexion SMTP non chiffrée sans TLS. Nous ne recommandons pas la transmission de courrier électronique sans chiffrement.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Comment Exchange Online utilise TLS entre des clients Exchange Online

Exchange Online serveurs chiffrent toujours les connexions à d’autres serveurs Exchange Online dans nos centres de données avec TLS 1.2. Lorsque vous envoyez un message à un destinataire au sein de votre organisation, Exchange Online envoie automatiquement le message via une connexion chiffrée à l’aide de TLS. Exchange Online envoie également des e-mails que vous envoyez à d’autres clients via des connexions chiffrées à l’aide du protocole TLS sécurisé à l’aide du secret de transfert.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Comment Microsoft 365 utilise TLS entre les partenaires Microsoft 365 et externes et approuvés

Par défaut, Exchange Online utilise toujours le *protocole TLS opportuniste*. Le protocole TLS opportuniste signifie Exchange Online tente toujours de chiffrer les connexions avec la version la plus sécurisée de TLS, puis descend la liste des chiffrements TLS jusqu’à ce qu’il trouve une sur laquelle les deux parties peuvent s’entendre. Sauf si vous avez configuré Exchange Online pour vous assurer que les messages envoyés à ce destinataire doivent utiliser des connexions sécurisées, le message est envoyé par défaut sans chiffrement si l’organisation destinataire ne prend pas en charge le chiffrement TLS. Le protocole TLS opportuniste est suffisant pour la plupart des entreprises. Toutefois, pour les entreprises qui ont des exigences de conformité médicale ou bancaire, ou pour les organisations gouvernementales, vous pouvez configurer Exchange Online afin d’exiger ou de forcer l’utilisation du protocole TLS. Pour obtenir des instructions, consultez [Configurer le flux de messagerie à l’aide de connecteurs dans Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Si vous décidez de configurer TLS entre votre organisation et une organisation partenaire approuvée, Exchange Online peut utiliser le *TLS forcé* pour créer des canaux de communication approuvés. Le protocole TLS forcé oblige votre organisation partenaire à s’authentifier auprès de Exchange Online avec un certificat de sécurité pour vous envoyer des messages. Votre partenaire doit gérer ses propres certificats. Exchange Online utilise des connecteurs pour protéger les messages que vous envoyez à partir d’un accès non autorisé avant qu’ils n’arrivent au fournisseur de messagerie du destinataire. Pour plus d’informations sur l’utilisation de connecteurs pour configurer le flux de messagerie, consultez [Configurer le flux de courrier à l’aide de connecteurs dans Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>Déploiements Exchange Server hybrides et TLS

Si vous gérez un déploiement de Exchange hybride, votre serveur Exchange local doit s’authentifier pour Microsoft 365 à l’aide d’un certificat de sécurité afin d’envoyer des messages aux destinataires dont les boîtes aux lettres se trouvent uniquement dans Office 365. Par conséquent, vous devez gérer vos propres certificats de sécurité pour vos serveurs Exchange locaux. Vous devez également stocker et conserver ces certificats de serveur de manière sécurisée. Pour plus d’informations sur la gestion des certificats dans les déploiements hybrides, consultez [La configuration requise pour les déploiements hybrides](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Configuration du TLS forcé pour Exchange Online dans Office 365

Pour les clients Exchange Online, afin que le TLS forcé sécurise l’ensemble de vos messages électroniques envoyés et reçus, vous devez configurer plusieurs connecteurs nécessitant TLS. Vous aurez besoin d’un connecteur pour les messages envoyés aux boîtes aux lettres utilisateur et d’un autre connecteur pour les messages envoyés à partir de boîtes aux lettres utilisateur. Créez ces connecteurs dans le Centre d’administration Exchange dans Office 365. Pour obtenir des instructions, consultez [Configurer le flux de messagerie à l’aide de connecteurs dans Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>Informations de certificat TLS pour Exchange Online

Les informations du certificat utilisées par Exchange Online sont décrites dans le tableau suivant. Si votre partenaire d’entreprise configure le protocole TLS forcé sur son serveur de messagerie, vous devez lui fournir ces informations. Pour des raisons de sécurité, nos certificats changent de temps en temps. Le certificat actuel est valide à partir du 24 septembre 2020.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Informations de certificat actuelles valides à partir du 24 septembre 2020
  
| Attribut | Valeur |
|:-----|:-----|
|Émetteur racine de l’autorité de certification|DigiCert CA - 1|
|Nom du certificat|mail.protection.outlook.com|
|Organisation|Microsoft Corporation|
|Unité d’organisation|www.digicert.com|
|Puissance de clé de certificat|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>Obtenir plus d’informations sur TLS, les certificats et les Microsoft 365 et télécharger des certificats

[Microsoft 365 les chaînes de chiffrement et les téléchargements de certificats](encryption-office-365-certificate-chains.md)

[Microsoft 365 les chaînes de chiffrement et les téléchargements de certificats - DOD et Cloud de la communauté du secteur public High](encryption-office-365-certificate-chains-itar.md)

Pour obtenir la liste des suites de chiffrement prises en charge, consultez [les informations de référence techniques sur le chiffrement](technical-reference-details-about-encryption.md).
  
[Configurer des connecteurs pour un flux de messagerie sécurisé avec une organisation partenaire](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Connecteurs avec sécurité de messagerie électronique renforcée](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Chiffrement dans Microsoft 365](encryption.md)
