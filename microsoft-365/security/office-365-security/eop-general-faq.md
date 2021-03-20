---
title: Forum Aux Questions d'ordre général concernant Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
ms.assetid: 9dbff00a-474e-4452-aeb5-5be9a6b8c6d5
ms.custom:
- seo-marvel-apr2020
description: Obtenez des réponses aux questions générales les plus courantes sur le service de filtrage du courrier électronique hébergé dans le cloud Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 04246b7c0a241c672328febd1584a56aa11becf2
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50916957"
---
# <a name="eop-general-faq"></a>Forum Aux Questions d’ordre général concernant Exchange Online Protection (EOP)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Nous répondons ici aux questions générales les plus courantes sur le service de filtrage du courrier électronique hébergé dans le cloud Exchange Online Protection (EOP). Pour d'autres rubriques du Forum Aux Questions (FAQ), suivez les liens suivants :

- Questions fréquemment posées sur les messages mis en file d’attente, différés et retournés dans EOP

- [FAQ sur l’administration déléguée](delegated-administration-faq.md)

- [Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.md)

- [FAQ sur la mise en quarantaine](quarantine-faq.md)

- [Forum Aux Questions sur la protection contre les programmes malveillants](anti-malware-protection-faq-eop.md)

- [Forum Aux Questions sur le suivi des messages](/exchange/monitoring/trace-an-email-message/message-trace-faq)

## <a name="what-is-eop"></a>Qu'est-ce que l’EOP ?

EOP est un service de filtrage de courrier électronique hébergé dans le nuage, conçu pour protéger les clients contre le courrier indésirable et les logiciels malveillants, et pour implémenter des règles de stratégie personnalisées. EOP est inclus dans tout abonnement Microsoft 365 qui contient des boîtes aux lettres Exchange Online. EOP est également disponible en tant qu’offre autonome pour protéger les environnements de messagerie locaux.

## <a name="how-do-i-sign-up-for-an-eop-trial-or-purchase-eop"></a>Comment m'inscrire pour un essai d'EOP ou acheter EOP ?

Pour vous inscrire pour un essai d'EOP ou pour l'acheter sur le web, visitez la page [Exchange Online Protection](https://products.office.com/exchange/exchange-email-security-spam-protection). Notez que les fonctionnalités du produit lors de l'achat d'une version d'essai sont identiques à celles du produit avec un abonnement payant, mais que des fonctionnalités supplémentaires fournies avec le plan d'abonnement [Licence d'accès client Exchange Enterprise avec services](https://products.office.com/exchange/microsoft-exchange-server-licensing-licensing-overview) sont également comprises.

## <a name="how-is-eop-priced"></a>Que coûte EOP ?

EOP fait l'objet d'une licence par utilisateur. Pour obtenir les derniers tarifs, consultez la page [Exchange Online Protection](https://products.office.com/exchange/exchange-email-security-spam-protection).

## <a name="how-long-does-it-take-to-put-eop-into-production"></a>Combien de temps faut-il pour qu'EOP soit opérationnel ?

Le filtrage commence dès que vous modifiez votre enregistrement MX, conformément aux étapes décrites dans la rubrique [Configurer votre service EOP](set-up-your-eop-service.md), et que votre courrier électronique circule dans EOP. La propagation de l'enregistrement MX via DNS peut prendre entre 24 et 48 heures. Vous pouvez affiner vos paramètres de protection à tout moment au cours de ce processus.

## <a name="do-i-have-to-use-all-features-of-microsoft-365-to-use-eop-what-if-i-just-want-eop-protection-and-thats-all"></a>Dois-je utiliser toutes les fonctionnalités de Microsoft 365 pour utiliser EOP ? Que se passe-t-il si je souhaite simplement une protection EOP et c’est tout ?

Vous pouvez utiliser EOP pour protéger vos boîtes aux lettres sur site sans utiliser d’autres fonctionnalités de Microsoft 365. C'est ce qu'on appelle un abonnement autonome. Une liste des fonctionnalités d'EOP est disponible dans la rubrique [Description du service de protection Exchange Online](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

## <a name="why-do-i-need-a-microsoft-365-tenant-when-signing-up-for-email-filtering-through-eop"></a>Pourquoi ai-je besoin d’un client Microsoft 365 lors de l’inscription au filtrage des courriers électroniques via EOP ?

Microsoft 365 est le nom donné à une collection de produits et services accessibles via un client Microsoft 365. Pensez au client Microsoft 365 comme point de départ auquel vous pouvez ajouter des licences pour le filtrage du courrier électronique.

## <a name="does-eop-have-a-communication-portal-where-i-can-find-out-about-known-issues-and-expected-resolutions-what-about-new-features"></a>Est-ce qu’EOP dispose d’un portail de communication dans lequel je peux effectuer des recherches sur les problèmes connus et les résolutions attendues ? Qu’en est-il des nouvelles fonctionnalités ?

Le Centre d’administration Microsoft 365 aura certaines de ces informations. Si vous êtes touché par un événement de niveau de service, vous devriez voir une alerte de communication (généralement accompagnée d’une icône en forme de cloche) après vous être ouvert au Centre d’administration Microsoft 365. Nous vous recommandons de lire ces informations et d'effectuer les actions appropriées.

En ce qui concerne les nouvelles fonctionnalités EOP, la feuille de route [De Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=O365) pour les entreprises est une bonne ressource pour trouver des informations sur les nouvelles fonctionnalités à venir. Nous publierons également des articles de blog sur les nouvelles fonctionnalités sur le site [web blogs Microsoft 365.](https://www.microsoft.com/microsoft-365/blog/)

## <a name="does-the-service-work-with-legacy-exchange-versions-such-as-exchange-server-2010-and-non-exchange-environments"></a>Le service fonctionne-t-il avec des versions d'Exchange héritées (par exemple, Exchange Server 2010) et les environnements non Exchange ?

Oui, le service n’est pas un serveur et peut être utilisé avec n’importe quel agent de transfert de courrier SMTP.

## <a name="what-size-organization-can-use-the-service"></a>Quelle doit être la taille de l'organisation pour pouvoir utiliser le service ?

N'importe quelle taille. Le réseau EOP offre une capacité suffisante pour s'adapter à la croissance de votre organisation, quelle qu'en soit la vitesse.

## <a name="what-permissions-do-i-need-to-set-up-eop"></a>De quelles autorisations ai-je besoin pour configurer EOP ?

Pour configurer EOP, vous devez être administrateur général ou administrateur d’entreprise Exchange (groupe de rôles Gestion de l’organisation).

## <a name="how-do-i-know-my-data-and-private-information-are-safe"></a>Comment savoir si mes données et informations sont en sûreté ?

Pour en savoir plus sur les mesures que nous avons prises pour assurer la sécurité de vos données et informations privées, y compris sur les contrats de niveau de service (SLA), visitez le [Centre de gestion de la protection des données d'Office 365](https://www.microsoft.com/trust-center).

## <a name="are-there-any-limits-i-should-be-aware-of-such-as-message-size-limitations"></a>Existe-t-il des limites que je devrais connaître, telles que les limites de taille pour les messages ?

Oui. Pour plus d'informations sur les limites dans EOP, voir [Limites d'Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits).

## <a name="does-eop-support-powershell"></a>EOP prend-il en charge PowerShell ?

Oui, toutes les fonctionnalités EOP sont disponibles via PowerShell : Exchange Online PowerShell pour les organisations ayant des boîtes aux lettres Exchange Online ; EOP PowerShell autonome pour les organisations EOP autonomes. Pour plus d’informations, [voir Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell) et [Exchange Online Protection PowerShell.](/powershell/exchange/exchange-online-protection-powershell)