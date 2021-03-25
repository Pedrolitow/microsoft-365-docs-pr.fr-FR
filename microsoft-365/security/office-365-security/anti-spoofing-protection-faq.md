---
title: FAQ sur la protection contre l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent consulter les questions fréquemment posées et leurs réponses sur la protection contre l’usurpation d’adresse dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5843ee7f791fbc2c37914194b153fdd05866d0a
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51203932"
---
# <a name="anti-spoofing-protection-faq"></a>FAQ sur la protection contre l’usurpation d’identité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cet article fournit des questions fréquemment posées et des réponses sur la protection contre l’usurpation d’adresses pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou les organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online.

Pour obtenir des questions et des réponses sur la protection anti-courrier indésirable, consultez la faq sur la [protection anti-courrier indésirable.](anti-spam-protection-faq.md)

Pour obtenir des questions et des réponses sur la protection anti-programme malveillant, consultez la faq sur la [protection anti-programme malveillant.](anti-malware-protection-faq-eop.md)

## <a name="why-did-microsoft-choose-to-junk-unauthenticated-inbound-email"></a>Pourquoi Microsoft a-t-il choisi de courrier indésirable entrant non authentifié ?

Microsoft estime que le risque de continuer à autoriser les messages entrants non authentifiés est plus élevé que le risque de perdre des messages entrants légitimes.

## <a name="does-junking-unauthenticated-inbound-email-cause-legitimate-email-to-be-marked-as-spam"></a>Le courrier indésirable entrant non authentifié entraîne-t-il la marque du courrier légitime comme courrier indésirable ?

Lorsque Microsoft a activé cette fonctionnalité en 2018, certains faux positifs se sont produits (les messages de qualité ont été marqués comme faux). Toutefois, au fil du temps, les expéditeurs se sont ajustés aux exigences. Le nombre de messages qui ont été identifiés comme usurpés est devenu négligeable pour la plupart des chemins d’accès aux e-mails.

Microsoft lui-même a d’abord adopté les nouvelles exigences d’authentification de messagerie plusieurs semaines avant de le déployer pour les clients. S’il y a eu des perturbations au début, elles ont progressivement diminué.

## <a name="is-spoof-intelligence-available-to-microsoft-365-customers-without-defender-for-office-365"></a>La veille contre l’usurpation d’informations est-elle disponible pour les clients Microsoft 365 sans Defender pour Office 365 ?

Oui. Depuis octobre 2018, la veille contre l’usurpation d’adresse est disponible pour toutes les organisations ayant des boîtes aux lettres dans Exchange Online et les organisations EOP autonomes sans boîtes aux lettres Exchange Online.

## <a name="how-can-i-report-spam-or-non-spam-messages-back-to-microsoft"></a>Comment signaler des messages comme étant ou n’étant pas du courrier indésirable à Microsoft ?

Voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="im-an-admin-and-i-dont-know-all-of-sources-for-messages-in-my-email-domain"></a>Je suis un administrateur et je ne sais pas toutes les sources de messages dans mon domaine de messagerie !

See [You don’t know all sources for your email](email-validation-and-authentication.md#you-dont-know-all-sources-for-your-email).

## <a name="what-happens-if-i-disable-anti-spoofing-protection-for-my-organization"></a>Que se passe-t-il si je désactive la protection contre l’usurpation d’accès pour mon organisation ?

Nous vous déconseillons de désactiver la protection contre l’usurpation d’usurpation d’accès. La désactivation de la protection permettra de remettre davantage de messages de hameçonnage et de courrier indésirable dans votre organisation. Tout le hameçonnage n’est pas une usurpation d’informations, et tous les messages usurpés ne seront pas manqués. Toutefois, votre risque sera plus élevé.

À présent que le filtrage amélioré pour les [connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) est disponible, nous vous déconseillons de la mettre hors service de protection contre l’usurpation d’adresse lorsque votre courrier électronique est acheminé via un autre service avant EOP.

## <a name="does-anti-spoofing-protection-mean-i-will-be-protected-from-all-phishing"></a>La protection contre l’usurpation d’usurpation signifie-t-elle que je suis protégé contre tout hameçonnage ?

Malheureusement, non. Les attaquants s’adaptent pour utiliser d’autres techniques (par exemple, les comptes compromis ou les comptes dans les services de messagerie gratuits). Toutefois, la protection anti-hameçonnage fonctionne beaucoup mieux pour détecter ces autres types de méthodes d’hameçonnage. Les couches de protection dans EOP sont conçues pour fonctionner ensemble et s’appuyer les unes sur les autres.

## <a name="do-other-large-email-services-block-unauthenticated-inbound-email"></a>D’autres services de messagerie de grande taille bloquent-ils les messages entrants non authentifiés ?

Presque tous les grands services de messagerie implémentent des vérifications SPF, DKIM et DMARC traditionnelles. Certains services ont d’autres contrôles plus stricts, mais peu vont jusqu’à EOP pour bloquer les e-mails non authentifiés et les traiter comme des messages usurpés. Toutefois, le secteur prend davantage en compte les problèmes de courrier électronique non authentifié, en particulier en raison du problème de hameçonnage.

## <a name="do-i-still-need-to-enable-the-advanced-spam-filter-setting-spf-record-hard-fail-_markasspamspfrecordhardfail_-if-i-enable-anti-spoofing"></a>Ai-je toujours besoin d’activer le paramètre De filtrage avancé du courrier indésirable « Enregistrement SPF : échec en dur » (_MarkAsSpamSpfRecordHardFail_) si j’active la détection d’usurpation d’adresses ?

Non. Ce paramètre ASF n’est plus requis. La protection contre l’usurpation d’usurpation considère à la fois les pannes de SPF et un ensemble de critères beaucoup plus large. Si vous avez activé la détection d’usurpation d’identité et l’option **Enregistrement SPF : échec sévère** (_MarkAsSpamSpfRecordHardFail_), vous obtiendrez probablement davantage de faux positifs.

Nous vous recommandons de désactiver cette fonctionnalité, car elle n’offre pratiquement aucun avantage supplémentaire pour la détection du courrier indésirable ou du hameçonnage, et générerait à la place principalement des faux positifs. Pour plus d’informations, consultez les paramètres de filtrage avancé du courrier indésirable [(ASF) dans EOP.](advanced-spam-filtering-asf-options.md)

## <a name="does-sender-rewriting-scheme-help-fix-forwarded-email"></a>Le modèle de réécriture des expéditeurs aide-t-il à corriger le courrier électronique transmis ?

Schéma de réécriture de l’expéditeur ne résout que partiellement le problème du courrier transféré. La réécriture du message SMTP **MAIL FROM**, SRS permet de s’assurer que le message transmis passe SPF à la destination suivante. Toutefois, étant donné que la prévention  de l’usurpation d’adresse est basée sur l’adresse De en combinaison avec le domaine de signature **MAIL FROM** ou DKIM (ou d’autres signaux), il ne suffit pas d’empêcher le courrier électronique transmis par SRS d’être marqué comme usurpé.