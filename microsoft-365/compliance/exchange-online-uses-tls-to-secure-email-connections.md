---
title: Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/2/2018
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Découvrez comment Exchange Online et Microsoft 365 transport TLS (Transport Layer Security) et FS (Transport Layer Security) pour sécuriser les communications électroniques. Obtenez également des informations sur le certificat émis par Microsoft pour Exchange Online.
ms.openlocfilehash: cc7ca631f9322fdc8a85cfaba197e63d06d08aee
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59175907"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Mode d’utilisation de TLS par Exchange Online pour sécuriser les connexions de messagerie

Découvrez comment Exchange Online et Microsoft 365 transport TLS (Transport Layer Security) et FS (Transport Layer Security) pour sécuriser les communications électroniques. Fournit également des informations sur le certificat émis par Microsoft pour Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Informations de base sur TLS pour Microsoft 365 et Exchange Online

Les protocoles TLS (Transport Layer Security) et SSL (antérieur au protocole TLS) sont des protocoles de chiffrement qui sécurisent les communications sur un réseau à l’aide de certificats de sécurité pour chiffrer une connexion entre plusieurs ordinateurs. Le protocole TLS remplace le protocole SSL et est couramment appelé SSL 3.1. Pour Exchange Online, nous utilisons TLS pour chiffrer les connexions entre nos serveurs Exchange et les connexions entre nos serveurs Exchange et d’autres serveurs tels que vos serveurs Exchange locaux ou les serveurs de messagerie de vos destinataires. Une fois la connexion chiffrée, toutes les données envoyées via cette connexion sont envoyées par le biais du canal chiffré. Toutefois, si vous transférez un message qui a été envoyé par le biais d’une connexion chiffrée via le protocole TLS, ce message n’est pas nécessairement chiffré. En effet, en termes simples, TLS ne chiffre pas le message, mais uniquement la connexion.
  
Si vous souhaitez chiffrer le message, vous devez utiliser une technologie de chiffrement qui chiffre le contenu du message, par exemple, le chiffrement de messages Office. Voir [Email encryption in Office 365](email-encryption.md) et [Office 365 Message Encryption (OME)](ome.md) pour plus d’informations sur les options de chiffrement de messages dans Office 365. 
  
Nous vous recommandons d’utiliser TLS dans les situations où vous souhaitez configurer un canal sécurisé de correspondance entre Microsoft et votre organisation locale ou une autre organisation, telle qu’un partenaire. Exchange Online tente toujours d’utiliser TLS en premier pour sécuriser votre messagerie, mais cette initiative peut s’avérer impossible si l’autre partie n’offre pas de sécurité TLS. Continuez à lire pour savoir comment sécuriser tous les messages vers vos serveurs locaux ou vos partenaires importants à l’aide *de connecteurs.* 

Pour fournir le meilleur chiffrement de classe à nos clients, Microsoft a supprimé les versions TLS 1.0 et 1.1 dans [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) et [Office 365 Cloud de la communauté du secteur public](tls-1-2-in-office-365-gcc.md). Toutefois, vous pouvez continuer à utiliser une connexion SMTP non chiffrée sans TLS. Nous vous déconseillons de transmettre le courrier électronique sans chiffrement.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Comment Exchange Online utilise TLS entre des clients Exchange Online

Les serveurs Exchange Online chiffrent toujours les connexions à d’autres serveurs Exchange Online de nos centres de données avec le protocole TLS 1.2. Lorsque vous envoyez un courrier électronique à un destinataire qui se trouve au sein de votre organisation, ce courrier électronique est automatiquement envoyé via une connexion chiffrée à l’aide de TLS. En outre, tous les messages que vous envoyez à d’autres clients sont envoyés via des connexions chiffrées à l’aide de TLS et sécurisées à l’aide du secret de forward.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Utilisation Microsoft 365 TLS entre les partenaires Microsoft 365 externes et les partenaires de confiance externes

Par défaut, Exchange Online utilise toujours le protocole TLS opportuniste. Cela signifie qu’Exchange Online essaie toujours de chiffrer les connexions avec la version la plus sécurisée de protocole TLS en premier, puis suit l’ordre de la liste de chiffrement TLS jusqu’à ce qu’il trouve un chiffrement fonctionnant pour les deux parties. Sauf si vous avez configuré Exchange Online pour vous assurer que les messages envoyés à ce destinataire sont uniquement envoyés par le biais de connexions sécurisées, le message sera envoyé par défaut non chiffré si l’organisation du destinataire ne prend pas en charge le chiffrement TLS. Le protocole TLS opportuniste est suffisant pour la plupart des entreprises. Toutefois, pour les entreprises qui ont des exigences de conformité telles que des organisations médicales, bancaires ou gouvernementales, vous pouvez configurer des Exchange Online pour exiger ou forcer le TLS. Pour obtenir des instructions, voir [Configurer le flux de messagerie à l’aide de connecteurs Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Si vous décidez de configurer TLS entre votre organisation et une organisation partenaire approuvée, Exchange Online peut utiliser le TLS forcé pour créer des canaux de communication approuvés. Le TLS forcé exige que votre organisation partenaire vous authentifie auprès d’Exchange Online avec un certificat de sécurité afin de vous envoyer des messages électroniques. Votre partenaire doit gérer ses propres certificats pour effectuer cette action. Dans Exchange Online, nous utilisons des connecteurs pour protéger les messages que vous envoyez contre tout accès non autorisé avant qu’ils n’arrivent chez le fournisseur de messagerie du destinataire. Pour plus d’informations sur l’utilisation des connecteurs pour configurer le flux de messagerie, voir Configurer le flux de messagerie à l’aide de [connecteurs Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>Déploiements Exchange Server hybrides et TLS

Si vous gérez un déploiement Exchange hybride, votre serveur Exchange local doit s’authentifier sur Microsoft 365 à l’aide d’un certificat de sécurité afin d’envoyer des messages aux destinataires dont les boîtes aux lettres sont uniquement en Office 365. Par conséquent, vous devez gérer vos propres certificats de sécurité pour vos serveurs Exchange locaux. Vous devez également stocker et conserver ces certificats de serveur de manière sécurisée. Pour plus d’informations sur la gestion des certificats dans les déploiements hybrides, voir [Certificate requirements for hybrid deployments](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Configuration du TLS forcé pour Exchange Online dans Office 365

Pour les clients Exchange Online, afin que le TLS forcé sécurise l’ensemble de vos messages électroniques envoyés et reçus, vous devez configurer plusieurs connecteurs nécessitant TLS. Vous avez besoin d’un connecteur pour les messages envoyés à vos boîtes aux lettres d’utilisateur, et un autre connecteur pour les messages envoyés à partir de vos boîtes aux lettres d’utilisateur. Créez ces connecteurs dans le Centre d’administration Exchange dans Office 365. Pour obtenir des instructions, voir [Configurer le flux de messagerie à l’aide de connecteurs Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-certificate-information-for-exchange-online"></a>Informations de certificat TLS pour Exchange Online

Les informations du certificat utilisées par Exchange Online sont décrites dans le tableau suivant. Si votre partenaire commercial configure le TLS forcé sur son serveur de messagerie, vous devez lui fournir ces informations. N’oubliez pas que, pour des raisons de sécurité, nos certificats sont modifiés de temps à autre. Nous avons déployé une mise à jour de notre certificat dans nos centres de données. Le nouveau certificat est valide à partir du 3 septembre 2018.
  
 **Informations de certificat actuelles valides depuis le 3 septembre 2018**
  
| Attribut | Valeur |
|:-----|:-----|
|Émetteur racine de l’autorité de certification  <br/> |GlobalSign Root CA – R1 <br/> |
|Nom du certificat  <br/> |mail.protection.outlook.com  <br/> |
|Organisation  <br/> |Microsoft Corporation  <br/> |
|Unité d’organisation  <br/> |  <br/> |
|Puissance de clé de certificat  <br/> |2048  <br/> |
   
 **Informations de certificats supprimés valides jusqu’au 3 septembre 2018**
  
Pour garantir une transition fluide, nous continuerons à fournir les anciennes informations de certificat pour votre référence pendant un certain temps. Toutefois, vous devez utiliser les informations de certificat actuelles à partir de maintenant.
  
****

| Attribut | Valeur |
|:-----|:-----|
|Émetteur racine de l’autorité de certification  <br/> |Baltimore CyberTrust Root  <br/> |
|Nom du certificat  <br/> |mail.protection.outlook.com  <br/> |
|Organisation  <br/> |Microsoft Corporation  <br/> |
|Unité d’organisation  <br/> |Microsoft Corporation  <br/> |
|Puissance de clé de certificat  <br/> |2048  <br/> |
   
## <a name="prepare-for-the-new-exchange-online-certificate"></a>Préparer le nouveau certificat Exchange Online certificat

Le nouveau certificat est émis par une autorité de certification différente du certificat précédent utilisé par Exchange Online. Par conséquent, vous devrez peut-être effectuer certaines actions pour utiliser le nouveau certificat.

Le nouveau certificat nécessite une connexion aux points de terminaison de la nouvelle ca dans le cadre de la validation du certificat. Si vous ne le faites pas, le flux de messagerie peut être affecté de manière négative. Si vous protégez vos serveurs de messagerie à l’aide de pare-feu qui leur permet uniquement de se connecter à certaines destinations, vous devez vérifier si votre serveur est en mesure de valider le nouveau certificat. Pour confirmer que votre serveur peut utiliser le nouveau certificat, complétez les étapes suivantes :

1. Connecter à votre Exchange Server en utilisant Windows PowerShell puis exécutez la commande suivante :  
  `certutil -URL https://crl.globalsign.com/gsorganizationvalsha2g3.crl`

1. Dans la fenêtre qui s’affiche, choisissez **Récupérer.**

1. Lorsque l’utilitaire termine sa vérification, il renvoie un état. Si l’état affiche **OK,** votre serveur de messagerie peut valider correctement le nouveau certificat. Si ce n’est pas le cas, vous devez déterminer la cause de l’échec des connexions. Vous devez probablement mettre à jour les paramètres d’un pare-feu. La liste complète des points de terminaison qui doivent être accessibles est la suivante :
    - ocsp.globalsign.com
    - crl.globalsign.com
    - secure.globalsign.com   

Normalement, vous recevez automatiquement les mises à jour de vos certificats racine via Windows Update. Toutefois, certains déploiements ont mis en place une sécurité supplémentaire qui empêche ces mises à jour de se produire automatiquement. Dans ces déploiements verrouillés où Windows Update ne peut pas mettre à jour automatiquement les certificats racines, vous devez vous assurer que le certificat d’ac racine correct est installé en effectuant les étapes suivantes :
1.  Connecter à votre Exchange Server en utilisant Windows PowerShell puis exécutez la commande suivante :  
  `certmgr.msc`

2. Sous **Autorité de certification racine de confiance/Certificats**, confirmez que le nouveau certificat est répertorié.

## <a name="get-more-information-about-tls-and-microsoft-365"></a>Obtenir plus d’informations sur TLS et Microsoft 365

Pour obtenir la liste des suites de chiffrement pris en charge, voir détails de référence [technique sur le chiffrement.](technical-reference-details-about-encryption.md)
  
[Configurer des connecteurs pour un flux de messagerie sécurisé avec une organisation partenaire](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Connecteurs avec sécurité de messagerie électronique renforcée](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Chiffrement dans Microsoft 365](encryption.md)
