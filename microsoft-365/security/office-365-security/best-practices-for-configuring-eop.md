---
title: Meilleures pratiques de configuration d’EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: faf1efd1-3b0c-411a-804d-17f37292eac0
description: Suivez ces recommandations sur les meilleures pratiques pour la protection autonome d’Exchange Online Protection (EOP) afin de vous configurer pour réussir et éviter les erreurs de configuration courantes.
ms.openlocfilehash: cb3aa36720a6a46932d69341394304937bb1a296
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203562"
---
# <a name="best-practices-for-configuring-standalone-eop"></a>Meilleures pratiques pour la configuration d’EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Suivez ces recommandations sur les meilleures pratiques pour la protection autonome d’Exchange Online Protection (EOP) afin de vous configurer pour réussir et éviter les erreurs de configuration courantes. Cette rubrique part de l'hypothèse que vous avez déjà effectué le processus de configuration. Si vous n'avez pas encore configuré EOP, consultez la rubrique [Configurer votre service EOP](set-up-your-eop-service.md).

## <a name="use-a-test-domain"></a>Utiliser un domaine de test

Nous vous recommandons d’utiliser un domaine, un sous-domaine ou un domaine au volume restreint de test pour tester les fonctionnalités des services avant de les implémenter sur des domaines de production au volume plus important.

## <a name="synchronize-recipients"></a>Synchronisation des destinataires

Si votre organisation dispose de comptes d’utilisateur existants dans un environnement Active Directory local, vous pouvez synchroniser ces comptes avec Azure Active Directory dans le Cloud. L'utilisation de la synchronisation d'annuaires est recommandée. Pour en savoir plus sur les avantages de la synchronisation d'annuaires et pour connaître les étapes de sa configuration, voir [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

## <a name="recommended-settings"></a>Paramètres recommandés

Nous habilitons les administrateurs de sécurité à personnaliser leurs paramètres de sécurité afin de répondre aux besoins de leur organisation. Même si, en règle générale, il existe deux niveaux de sécurité dans EOP et Office 365 ATP, qui nous sont recommandés : standard et strict. Ces paramètres sont répertoriés dans la [section Paramètres recommandés pour la sécurité de l’ATP et d’Office 365](recommended-settings-for-eop-and-office365-atp.md).

### <a name="miscellaneousnon-policy-settings"></a>Paramètres divers/non de stratégie

Ces paramètres couvrent un éventail de fonctionnalités en dehors des stratégies de sécurité.

****

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|[Configurer SPF pour empêcher l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md)|Oui|Oui||
|[Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md)|Oui|Oui||
|[Utiliser DMARC pour valider les e-mails dans Office 365](use-dmarc-to-validate-email.md)|Oui|Oui|Utilisez `action=quarantine` for standard et `action=reject` strict.|
|Déployer le [complément de message de rapport](enable-the-report-message-add-in.md) afin d’améliorer la création de rapports d’utilisateur final de courrier suspect|Oui|Oui||
|Planifier les programmes malveillants et le courrier indésirable|Oui|Oui||
|Le transfert automatique vers les domaines externes ne doit pas être autorisé ni surveillé|Oui|Oui||
|L’audit unifié doit être activé|Oui|Oui||
|[Connectivité IMAP à la boîte aux lettres](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)|Désactivé|Désactivé||
|[Connectivité POP à la boîte aux lettres](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)|Désactivé|Désactivé||
|Envoi SMTP authentifié|Désactivé|Désactivé|L’envoi SMTP de client authentifié (également appelé envoi SMTP client ou authentification SMTP) est requis pour les clients POP3 et IMAP4 pour envoyer des courriers électroniques.|
|Connectivité EWS à la boîte aux lettres|Désactivé|Désactivé||
|[Connectivité PowerShell](https://docs.microsoft.com/powershell/exchange/disable-access-to-exchange-online-powershell)|Désactivé|Désactivé|Disponible pour les utilisateurs de boîte aux lettres ou les utilisateurs de messagerie (objets utilisateur retournés par la cmdlet [Get-User](https://docs.microsoft.com/powershell/module/exchange/get-user) ).|
|Utiliser les [renseignements frauduleux](learn-about-spoof-intelligence.md) pour ajouter des expéditeurs à votre liste verte|Oui|Oui||
|[Blocage du périmètre basé sur l’annuaire (DBEB)](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|Activé|Activé|Type de domaine = faisant autorité|
|[Configurer l’authentification multifacteur pour tous les comptes d’administrateur](https://docs.microsoft.com/microsoft-365/admin/security-and-compliance/set-up-multi-factor-authentication)|Activé|Activé||
|

## <a name="troubleshooting"></a>Résolution des problèmes

Résoudre les problèmes et tendances généraux à l’aide des rapports dans le centre d’administration. Pour trouver des données concernant un point précis d'un message, utilisez l'outil de suivi des messages. Pour plus d'informations sur la génération de rapports, consultez la rubrique [Création de rapports et suivi des messages dans Exchange Online Protection](reporting-and-message-trace-in-exchange-online-protection.md). Pour plus d’informations sur l’outil de suivi des messages [, consultez la rubrique suivi des messages dans le centre de sécurité & Compliance Center](message-trace-scc.md).

## <a name="report-false-positives-and-false-negatives-to-microsoft"></a>Signaler les faux positifs et les faux négatifs à Microsoft

Pour améliorer le filtrage du courrier indésirable dans le service pour tout le monde, vous devez signaler les faux positifs (courrier électronique marqué comme incorrect) et les faux négatifs (courrier incorrect autorisé) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="create-mail-flow-rules"></a>Création de règles de flux de messagerie

Créez des règles de flux de messagerie (également appelées règles de transport) ou des filtres personnalisés pour répondre aux besoins de votre entreprise.

Lorsque vous déployez une nouvelle règle en production, commencez par sélectionner l'un des modes test pour voir son effet. Lorsque vous estimez que la règle fonctionne de la manière souhaitée, modifiez son mode d'effet en le définissant sur **Appliquer**.

Lors du déploiement d'une nouvelle règle, songez à ajouter l'action supplémentaire **Générer un rapport d'incident** pour contrôler son action.

Dans les environnements hybrides où votre organisation inclut Exchange sur site et Exchange Online, prenez en compte les conditions que vous utilisez dans les règles de flux de messagerie. Si vous souhaitez que les règles s’appliquent à l’ensemble de l’organisation, veillez à utiliser les conditions disponibles dans Exchange local et dans Exchange Online. Alors que la plupart des conditions sont disponibles dans les deux environnements, il existe quelques éléments qui ne sont disponibles que dans un seul environnement ou l’autre. Pour plus d’informations, consultez la rubrique [règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).
