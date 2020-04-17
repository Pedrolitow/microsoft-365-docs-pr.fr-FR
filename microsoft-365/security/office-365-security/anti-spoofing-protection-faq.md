---
title: Forum aux questions sur la protection contre l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Forum aux questions et réponses pour les administrateurs concernant la protection contre l’usurpation d’identité dans Exchange Online et autonome Exchange Online Protection (EOP).
ms.openlocfilehash: b39e48fd57b899e6296d40ab10aac265cb4165a3
ms.sourcegitcommit: 9ed3283dd6dd959faeca5c22613f9126261b9590
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "43529858"
---
# <a name="anti-spoofing-protection-faq-in-office-365"></a>Forum aux questions sur la protection contre l’usurpation d’identité dans Office 365

Cette rubrique fournit des questions fréquemment posées et des réponses sur la protection contre l’usurpation d’identité pour les clients Office 365 avec des boîtes aux lettres dans Exchange Online ou des clients Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online.

Pour obtenir des questions et des réponses sur la protection contre le courrier indésirable, consultez la rubrique [protection contre le courrier indésirable](anti-spam-protection-faq.md).

Pour obtenir des questions et des réponses sur la protection contre les programmes malveillants, consultez la rubrique [anti-malware protection FAQ dans Office 365](anti-malware-protection-faq-eop.md)

## <a name="why-did-microsoft-choose-to-junk-unauthenticated-inbound-email"></a>Pourquoi Microsoft a-t-il choisi de courrier indésirable entrant non authentifié ?

En raison de l’impact des attaques par hameçonnage et de l’authentification de messagerie depuis plus de 15 ans, Microsoft estime que le risque de continuer à autoriser le courrier entrant non authentifié est plus élevé que le risque de perte de courrier entrant légitime.

## <a name="does-junking-unauthenticated-inbound-email-cause-legitimate-email-to-be-marked-as-spam"></a>Le courrier indésirable non authentifié a-t-il été marqué comme courrier indésirable ?

Lorsque Microsoft a activé cette fonctionnalité dans 2018, certains faux positifs se sont produits (bons messages ont été marqués comme incorrects). Toutefois, au fil du temps, les expéditeurs ajustés aux nouvelles exigences en matière d’authentification des expéditeurs et le nombre de messages qui ont été identifiés de manière indéterminée comme usurpés est devenu négligeable pour la plupart des chemins d’accès.

Microsoft a d’abord adopté les nouvelles exigences d’authentification de messagerie plusieurs semaines avant de la déployer auprès des clients. S’il y a eu des perturbations au début, elles ont progressivement diminué.

## <a name="is-spoof-intelligence-available-to-office-365-customers-without-atp"></a>La fonctionnalité d’usurpation d’identité est-elle disponible pour les clients Office 365 sans ATP ?

Oui. À compter du 2018 octobre, toutes les organisations disposant de boîtes aux lettres Exchange Online et d’organisations EOP autonomes sont accessibles à toutes les organisations sans boîtes aux lettres Exchange Online.

La technologie de détection d’usurpation d’identité a été déployée pour les organisations qui avaient des abonnements Office 365 entreprise E5 ou le complément Office 365 Advanced Threat Protection (ATP) pour leur abonnement.

## <a name="how-can-i-report-spam-or-non-spam-messages-back-to-microsoft"></a>Comment signaler des messages comme étant ou n’étant pas du courrier indésirable à Microsoft ?

Voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="im-an-admin-and-i-dont-know-all-of-sources-for-messages-in-my-email-domain"></a>Je suis administrateur et je ne sais pas toutes les sources pour les messages dans mon domaine de messagerie.

Consultez [la rubrique ne connaissant pas toutes les sources de votre courrier électronique](email-validation-and-authentication.md#you-dont-know-all-sources-for-your-email).

## <a name="what-happens-if-i-disable-anti-spoofing-protection-for-my-organization"></a>Que se passe-t-il si je désactive la protection contre l’usurpation d’identité pour mon organisation ?

Nous vous le déconseillons car vous manquerez davantage de messages de hameçonnage et de courrier indésirable. Tout hameçonnage n’est pas de l’usurpation d’identité, et toutes les usurpations d’identité ne seront pas manquées. Cependant, vous courrez un risque supérieur à celui auquel s’expose un client qui active la détection d’usurpation d’identité.

Maintenant que le [filtrage amélioré pour les connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) est disponible, il n’est plus recommandé de désactiver la protection contre l’usurpation d’identité si votre enregistrement MX pointe vers un autre serveur ou service avant de remettre le courrier électronique à EOP.

## <a name="does-anti-spoofing-protection-mean-i-will-be-protected-from-all-phishing"></a>La protection contre l’usurpation d’identité signifie-t-elle une protection contre tous les tentatives de hameçonnage ?

Malheureusement, non. Les agresseurs s’adapteront pour utiliser d’autres techniques (par exemple, des comptes compromis ou des comptes dans les services de messagerie gratuits). Toutefois, la protection anti-hameçonnage fonctionne bien mieux pour détecter ces autres types de méthodes de hameçonnage. Les couches de protection dans Office 365 sont conçues conjointement et s’imbriquent les unes sur les autres.

## <a name="do-other-large-email-services-block-unauthenticated-inbound-email"></a>D’autres services de messagerie volumineux bloquent-ils le courrier électronique entrant non authentifié ?

Presque tous les grands services de messagerie mettent en œuvre des vérifications SPF, DKIM et DMARC classiques. Certains services ont d’autres contrôles plus rigoureux, mais il n’y a pas d’aller plus loin qu’Office 365 pour bloquer les messages électroniques non authentifiés et les traiter comme des messages falsifiés. Toutefois, le secteur informatique est de plus en plus conscient des problèmes liés à la messagerie non authentifiée, en particulier en raison du problème de hameçonnage.

## <a name="do-i-still-need-to-enable-the-advanced-spam-filter-setting-spf-record-hard-fail-_markasspamspfrecordhardfail_-if-i-enable-anti-spoofing"></a>Dois-je toujours activer le paramètre de filtrage du courrier indésirable avancé « enregistrement SPF : échec matériel » (_MarkAsSpamSpfRecordHardFail_) si j’active la détection d’usurpation d’identité ?

Non. Ce paramètre ASF n’est plus nécessaire, car la détection d’usurpation d’identité ne prend pas seulement en compte le blocage de SPF, mais un ensemble plus large de critères. Si vous avez activé la détection d’usurpation d’identité et l’option **Enregistrement SPF : échec sévère** (_MarkAsSpamSpfRecordHardFail_), vous obtiendrez probablement davantage de faux positifs.

Nous vous recommandons de désactiver cette fonctionnalité car elle ne fournit quasiment aucun avantage supplémentaire pour détecter le courrier indésirable ou le message de hameçonnage, et générera plutôt des faux positifs. Pour plus d’informations, voir [Paramètres de filtre de courrier indésirable avancé (ASF) dans Office 365](advanced-spam-filtering-asf-options.md).

## <a name="does-sender-rewriting-scheme-help-fix-forwarded-email"></a>Le schéma de réécriture de l’expéditeur aide-t-il à résoudre les messages transférés ?

Schéma de réécriture de l’expéditeur ne résout que partiellement le problème du courrier transféré. En réécrivant le **courrier SMTP à partir de**, le service SRS peut s’assurer que le message transféré passe par SPF à la destination suivante. Toutefois, étant donné que la détection d’usurpation d’identité est basée sur l’adresse **de** l’expéditeur en combinaison avec le domaine de la signature DKIM ou DKIM (ou **d'** autres signaux), il n’est pas suffisant d’empêcher le marquage du courrier remis comme falsifié.
