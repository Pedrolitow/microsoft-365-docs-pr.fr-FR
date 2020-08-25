---
title: Forum aux questions sur la protection contre l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent consulter les questions fréquemment posées et les réponses sur la protection contre l’usurpation d’identité dans Exchange Online Protection (EOP).
ms.openlocfilehash: 3547b0a0af6d2e541d4ec3546d9bbd4aa34c3a6b
ms.sourcegitcommit: 787b198765565d54ee73972f664bdbd5023d666b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "46867138"
---
# <a name="anti-spoofing-protection-faq"></a>Forum aux questions sur la protection contre l’usurpation d’identité

Cet article fournit des questions fréquemment posées et des réponses sur la protection contre l’usurpation d’identité pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online.

Pour obtenir des questions et des réponses sur la protection contre le courrier indésirable, consultez la rubrique [protection contre le courrier indésirable](anti-spam-protection-faq.md).

Pour obtenir des questions et des réponses sur la protection contre les programmes malveillants, consultez la rubrique [anti-malware protection FAQ](anti-malware-protection-faq-eop.md) .

## <a name="why-did-microsoft-choose-to-junk-unauthenticated-inbound-email"></a>Pourquoi Microsoft a-t-il choisi de courrier indésirable entrant non authentifié ?

Microsoft pense que le risque de continuer à autoriser les messages électroniques entrants non authentifiés est supérieur au risque de perdre des messages entrants légitimes.

## <a name="does-junking-unauthenticated-inbound-email-cause-legitimate-email-to-be-marked-as-spam"></a>Le courrier indésirable non authentifié a-t-il été marqué comme courrier indésirable ?

Lorsque Microsoft a activé cette fonctionnalité dans 2018, certains faux positifs se sont produits (bons messages ont été marqués comme incorrects). Toutefois, au fil du temps, les expéditeurs sont adaptés à la configuration requise. Le nombre de messages qui ont été identifiés de manière indéterminée comme usurpés est devenu négligeable pour la plupart des chemins d’accès.

Microsoft a d’abord adopté les nouvelles exigences d’authentification de messagerie plusieurs semaines avant de la déployer auprès des clients. S’il y a eu des perturbations au début, elles ont progressivement diminué.

## <a name="is-spoof-intelligence-available-to-microsoft-365-customers-without-atp"></a>Est-ce que des usurpations d’identité sont disponibles pour les clients Microsoft 365 sans ATP ?

Oui. À partir du 2018 octobre, toutes les organisations disposant de boîtes aux lettres dans Exchange Online et d’organisations EOP autonomes ne disposant pas de boîtes aux lettres Exchange Online sont accessibles à l’aide des usurpations d’identité.

La technologie de détection d’usurpation d’identité était initialement disponible dans Office 365 Advanced Threat Protection. Par exemple, les abonnements Microsoft E5 ou les modules complémentaires ATP.

## <a name="how-can-i-report-spam-or-non-spam-messages-back-to-microsoft"></a>Comment signaler des messages comme étant ou n’étant pas du courrier indésirable à Microsoft ?

Voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="im-an-admin-and-i-dont-know-all-of-sources-for-messages-in-my-email-domain"></a>Je suis administrateur et je ne sais pas toutes les sources pour les messages dans mon domaine de messagerie.

Consultez [la rubrique ne connaissant pas toutes les sources de votre courrier électronique](email-validation-and-authentication.md#you-dont-know-all-sources-for-your-email).

## <a name="what-happens-if-i-disable-anti-spoofing-protection-for-my-organization"></a>Que se passe-t-il si je désactive la protection contre l’usurpation d’identité pour mon organisation ?

Nous vous déconseillons de désactiver la protection contre l’usurpation d’identité. La désactivation de la protection autorise la remise de messages de hameçonnage et de courrier indésirable au sein de votre organisation. Tous les messages d’hameçonnage ne sont pas usurpés et tous les messages falsifiés ne sont pas manqués. Toutefois, votre risque sera plus élevé.

Maintenant que le [filtrage amélioré pour les connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) est disponible, nous ne recommandons plus la désactivation de la protection contre l’usurpation d’identité lorsque votre courrier électronique est acheminé via un autre service avant EOP.

## <a name="does-anti-spoofing-protection-mean-i-will-be-protected-from-all-phishing"></a>La protection contre l’usurpation d’identité signifie-t-elle une protection contre tous les tentatives de hameçonnage ?

Malheureusement, non. Les agresseurs s’adapteront pour utiliser d’autres techniques (par exemple, des comptes compromis ou des comptes dans les services de messagerie gratuits). Toutefois, la protection anti-hameçonnage fonctionne bien mieux pour détecter ces autres types de méthodes de hameçonnage. Les couches de protection dans EOP sont conçues conjointement et se développent les unes sur les autres.

## <a name="do-other-large-email-services-block-unauthenticated-inbound-email"></a>D’autres services de messagerie volumineux bloquent-ils le courrier électronique entrant non authentifié ?

Presque tous les grands services de messagerie mettent en œuvre des vérifications SPF, DKIM et DMARC classiques. Certains services ont d’autres contrôles plus rigoureux, mais il n’y a pas d’exprès de EOP pour bloquer les messages électroniques non authentifiés et les traiter comme des messages falsifiés. Toutefois, le secteur informatique est de plus en plus conscient des problèmes liés à la messagerie non authentifiée, en particulier en raison du problème de hameçonnage.

## <a name="do-i-still-need-to-enable-the-advanced-spam-filter-setting-spf-record-hard-fail-_markasspamspfrecordhardfail_-if-i-enable-anti-spoofing"></a>Dois-je toujours activer le paramètre de filtrage du courrier indésirable avancé « enregistrement SPF : échec matériel » (_MarkAsSpamSpfRecordHardFail_) si j’active la détection d’usurpation d’identité ?

Non. Ce paramètre ASF n’est plus obligatoire. La protection contre l’usurpation d’identité considère à la fois les pannes matérielles SPF et un ensemble plus large de critères. Si vous avez activé la détection d’usurpation d’identité et l’option **Enregistrement SPF : échec sévère** (_MarkAsSpamSpfRecordHardFail_), vous obtiendrez probablement davantage de faux positifs.

Nous vous recommandons de désactiver cette fonctionnalité car elle ne fournit quasiment aucun avantage supplémentaire pour détecter le courrier indésirable ou le message de hameçonnage, et générera plutôt des faux positifs. Pour plus d’informations, voir [paramètres du filtre de courrier indésirable avancé (ASF) dans EOP](advanced-spam-filtering-asf-options.md).

## <a name="does-sender-rewriting-scheme-help-fix-forwarded-email"></a>Le schéma de réécriture de l’expéditeur aide-t-il à résoudre les messages transférés ?

Schéma de réécriture de l’expéditeur ne résout que partiellement le problème du courrier transféré. En réécrivant le **courrier SMTP à partir de**, le service SRS peut s’assurer que le message transféré passe par SPF à la destination suivante. Toutefois, étant donné que la détection d’usurpation d’identité est basée sur l’adresse **de** l’expéditeur en combinaison avec le domaine de la signature DKIM ou DKIM (ou **d'** autres signaux), il n’est pas suffisant d’empêcher le marquage du courrier remis comme falsifié.
