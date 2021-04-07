---
title: Meilleures pratiques de configuration d’EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: faf1efd1-3b0c-411a-804d-17f37292eac0
description: Suivez ces recommandations pour Exchange Online Protection (EOP) autonome afin de vous configurer pour réussir et d’éviter les erreurs de configuration courantes.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 94586d409d6d8b53ba68c22b6b4f62d2b72266db
ms.sourcegitcommit: 7ee50882cb4ed37794a3cd82dac9b2f9e0a1f14a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51599472"
---
# <a name="best-practices-for-configuring-standalone-eop"></a>Meilleures pratiques pour la configuration d’EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Suivez ces recommandations pour Exchange Online Protection (EOP) autonome afin de vous configurer pour réussir et d’éviter les erreurs de configuration courantes. Cette rubrique part de l'hypothèse que vous avez déjà effectué le processus de configuration. Si vous n'avez pas encore configuré EOP, consultez la rubrique [Configurer votre service EOP](set-up-your-eop-service.md).

## <a name="use-a-test-domain"></a>Utiliser un domaine de test

Nous vous recommandons d’utiliser un domaine, un sous-domaine ou un domaine au volume restreint de test pour tester les fonctionnalités des services avant de les implémenter sur des domaines de production au volume plus important.

## <a name="synchronize-recipients"></a>Synchronisation des destinataires

Si votre organisation dispose de comptes d’utilisateurs dans un environnement Active Directory local, vous pouvez synchroniser ces comptes avec Azure Active Directory dans le cloud. L'utilisation de la synchronisation d'annuaires est recommandée. Pour en savoir plus sur les avantages de la synchronisation d'annuaires et pour connaître les étapes de sa configuration, voir [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

## <a name="recommended-settings"></a>Paramètres recommandés

Nous permettent aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité pour répondre aux besoins de leur organisation. Bien que, en règle générale, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : Standard et Strict. Ces paramètres sont répertoriés dans les paramètres recommandés pour EOP et Microsoft Defender pour la sécurité [Office 365.](recommended-settings-for-eop-and-office365.md)

### <a name="miscellaneousnon-policy-settings"></a>Paramètres divers/non stratégiques

Ces paramètres couvrent une gamme de fonctionnalités en dehors des stratégies de sécurité.

<br>

****

|Nom de la fonctionnalité de sécurité|Standard|Strict|Commentaire|
|---|---|---|---|
|[Configurer SPF pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md)|Oui|Oui||
|[Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md)|Oui|Oui||
|[Utiliser DMARC pour valider les e-mails dans Office 365](use-dmarc-to-validate-email.md)|Oui|Oui|À `action=quarantine` utiliser pour Standard et `action=reject` Strict.|
|Déployer le [add-in Report Message](enable-the-report-message-add-in.md) ou [le add-in Report Phishing](enable-the-report-phish-add-in.md) pour améliorer les signalements d’e-mails suspects par l’utilisateur final|Oui|Oui||
|Planifier des rapports sur les programmes malveillants et le courrier indésirable|Oui|Oui||
|Le forwarding automatique vers des domaines externes doit être refusé ou surveillé|Oui|Oui||
|L’audit unifié doit être activé|Oui|Oui||
|[Connectivité IMAP à la boîte aux lettres](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)|Désactivé|Désactivé||
|[Connectivité POP à la boîte aux lettres](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)|Désactivé|Désactivé||
|Envoi SMTP authentifié|Désactivé|Désactivé|L’envoi SMTP client authentifié (également appelé envoi SMTP client ou AUTHENTIFICATION SMTP) est requis pour les clients et les appareils POP3 et IMAP4 qui génèrent et envoient des messages électroniques. <p> Pour obtenir des instructions pour activer et désactiver SMTP AUTH de manière globale ou sélective, voir Activer ou désactiver l’envoi SMTP de client authentifié [dans Exchange Online.](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)|
|Connectivité EWS à la boîte aux lettres|Désactivé|Désactivé|Outlook utilise les services web Exchange pour les paramètres de libre/occupé, d’in-bureau et de partage de calendrier. Si vous ne pouvez pas désactiver EWS globalement, vous avez les options suivantes : <ul><li>Utilisez des [stratégies d’authentification](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) pour empêcher EWS d’utiliser l’authentification de base si vos clients la prise en charge de l’authentification moderne (authentification moderne).</li><li>Utilisez les [règles d’accès client](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) pour limiter EWS à des utilisateurs spécifiques ou à des adresses IP sources.</li><li>Contrôler l’accès EWS à des applications spécifiques globalement ou par utilisateur. Pour obtenir des instructions, voir [Contrôler l’accès à EWS dans Exchange.](/exchange/client-developer/exchange-web-services/how-to-control-access-to-ews-in-exchange)</li></ul> <p> Le [add-in](enable-the-report-message-add-in.md) Message [](enable-the-report-phish-add-in.md) de rapport et le module de signalement de hameçonnage utilisent REST par défaut dans les environnements pris en charge, mais reviennent à EWS si REST n’est pas disponible. Les environnements pris en charge qui utilisent REST sont :<ul><li>Exchange Online</li><li>Exchange 2019 ou Exchange 2016</li><li>Outlook pour Windows actuel à partir d’un abonnement Microsoft 365 ou d’un achat one-time Outlook 2019.</li><li>Outlook pour Mac actuel à partir d’un abonnement Microsoft 365 ou d’un achat one-time Outlook pour Mac 2016 ou version ultérieure.</li><li>Outlook pour iOS et Android</li><li>Outlook sur le web</li></ul>|
|[Connectivité PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)|Désactivé|Désactivé|Disponible pour les utilisateurs de boîtes aux lettres ou les utilisateurs de messagerie (objets utilisateur renvoyés par la cmdlet [Get-User).](/powershell/module/exchange/get-user)|
|Utiliser [la veille contre l’usurpation](learn-about-spoof-intelligence.md) d’adresse pour ajouter des expéditeurs à votre liste d’adresses|Oui|Oui||
|[Blocage du périphérie basé sur l’annuaire (DBEB)](/Exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|Activé|Activé|Type de domaine = Faisant autorité|
|[Configurer l’authentification multifacteur pour tous les comptes d’administrateur](../../admin/security-and-compliance/set-up-multi-factor-authentication.md)|Activé|Activé||
|

## <a name="troubleshooting"></a>Résolution des problèmes

Résolution des problèmes généraux et des tendances à l’aide des rapports dans le Centre d’administration. Pour trouver des données concernant un point précis d'un message, utilisez l'outil de suivi des messages. Pour plus d'informations sur la génération de rapports, consultez la rubrique [Création de rapports et suivi des messages dans Exchange Online Protection](reporting-and-message-trace-in-exchange-online-protection.md). En savoir plus sur l’outil de suivi des messages dans le suivi des messages dans le Centre de [sécurité & conformité.](message-trace-scc.md)

## <a name="report-false-positives-and-false-negatives-to-microsoft"></a>Signaler les faux positifs et les faux négatifs à Microsoft

Pour améliorer le filtrage du courrier indésirable dans le service pour tout le monde, vous devez signaler les faux positifs (bon e-mail marqué comme faux) et les faux négatifs (courrier indésirable autorisé) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="create-mail-flow-rules"></a>Création de règles de flux de messagerie

Créez des règles de flux de messagerie (également appelées règles de transport) ou des filtres personnalisés pour répondre aux besoins de votre entreprise.

Lorsque vous déployez une nouvelle règle en production, commencez par sélectionner l'un des modes test pour voir son effet. Lorsque vous estimez que la règle fonctionne de la manière souhaitée, modifiez son mode d'effet en le définissant sur **Appliquer**.

Lors du déploiement d'une nouvelle règle, songez à ajouter l'action supplémentaire **Générer un rapport d'incident** pour contrôler son action.

Dans les environnements hybrides où votre organisation inclut à la fois Exchange local et Exchange Online, prenons en compte les conditions que vous utilisez dans les règles de flux de messagerie. Si vous souhaitez que les règles s’appliquent à l’ensemble de l’organisation, assurez-vous d’utiliser les conditions disponibles dans Exchange local et dans Exchange Online. Bien que la plupart des conditions soient disponibles dans les deux environnements, certaines d’entre elles sont disponibles uniquement dans un environnement ou dans l’autre. Pour plus d’informations, voir règles de flux de messagerie [(règles de transport) dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)