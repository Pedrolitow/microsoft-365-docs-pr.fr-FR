---
title: Meilleures pratiques pour la configuration de EOP et Office 365 ATP
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 12/9/2016
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: faf1efd1-3b0c-411a-804d-17f37292eac0
description: Pour vous donner un maximum de chances de succès et éviter les erreurs courantes de configuration, suivez ces recommandations relatives aux meilleures pratiques pour Exchange Online Protection (EOP).
ms.openlocfilehash: 053b5f551be528e7eedb3c218bb1e49ab6b8be91
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599741"
---
# <a name="best-practices-for-configuring-eop-and-office-365-atp"></a>Meilleures pratiques pour la configuration de EOP et Office 365 ATP

Pour vous donner un maximum de chances de succès et éviter les erreurs courantes de configuration, suivez ces recommandations relatives aux meilleures pratiques pour Exchange Online Protection (EOP). Cette rubrique part de l'hypothèse que vous avez déjà effectué le processus de configuration. Si vous n'avez pas encore configuré EOP, consultez la rubrique [Configurer votre service EOP](set-up-your-eop-service.md).

## <a name="use-a-test-domain"></a>Utiliser un domaine de test

Nous vous recommandons d’utiliser un domaine, un sous-domaine ou un domaine au volume restreint de test pour tester les fonctionnalités des services avant de les implémenter sur des domaines de production au volume plus important.

## <a name="synchronize-recipients"></a>Synchronisation des destinataires

Si votre organisation dispose de comptes d’utilisateur existants dans un environnement Active Directory local, vous pouvez synchroniser ces comptes avec Azure Active Directory dans le Cloud. L'utilisation de la synchronisation d'annuaires est recommandée. Pour en savoir plus sur les avantages de la synchronisation d'annuaires et pour connaître les étapes de sa configuration, voir [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

## <a name="recommended-settings"></a>Paramètres recommandés

Nous permettez aux administrateurs de sécurité de personnaliser les paramètres de sécurité qui satistfy les besoins de leurs environnements. Même si, en règle générale, il existe deux niveaux de sécurité dans EOP et Office 365 ATP, qui nous sont recommandés : standard et strict. Ces paramètres sont répertoriés dans la [section Paramètres recommandés pour la sécurité de l’ATP et d’Office 365](recommended-settings-for-eop-and-office365-atp.md). 

### <a name="miscellaneousnon-policy-settings"></a>Paramètres divers/non de stratégie

Ces paramètres couvrent un éventail de fonctionnalités en dehors des stratégies de sécurité.

Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|[Configurer SPF dans Office 365 pour empêcher l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md)|Oui|Oui||
|[Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md)|Oui|Oui||
|[Utiliser DMARC pour valider les e-mails dans Office 365](use-dmarc-to-validate-email.md)|Oui|Oui|Utilisez action = Quarantine for standard et action = Reject pour strict.|
|Déployer le complément de rapport de message pour améliorer la création de rapports d’utilisateur final sur les E-mails suspects|Oui|Oui||
|Planifier les programmes malveillants et le courrier indésirable|Oui|Oui||
|Le transfert automatique vers les domaines externes ne doit pas être autorisé ni surveillé|Oui|Oui||
|L’audit unifié doit être activé|Oui|Oui||
|Connectivité IMAP à la boîte aux lettres|Désactivé|Désactivé||
|Connectivité POP à la boîte aux lettres|Désactivé|Désactivé||
|Envoi authentifié SMTP vers la boîte aux lettres|Désactivé|Désactivé||
|Connectivité EWS à la boîte aux lettres|Désactivé|Désactivé||
|Connectivité PowerShell|Désactivé|Désactivé||
|Utiliser l’intelligence d’usurpation d’identité pour les expéditeurs de liste d’autorisation dès que possible|Oui|Oui||
|Blocage du périmètre basé sur l’annuaire (DBEB)|Activé|Activé|Type de domaine = faisant autorité|
|[Configurer l’authentification multifacteur pour tous les comptes d’administrateur](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)|Activé|Activé||

## <a name="troubleshooting"></a>Résolution des problèmes

Résoudre les problèmes et tendances généraux à l’aide des rapports dans le centre d’administration. Pour trouver des données concernant un point précis d'un message, utilisez l'outil de suivi des messages. Pour plus d'informations sur la génération de rapports, consultez la rubrique [Création de rapports et suivi des messages dans Exchange Online Protection](reporting-and-message-trace-in-exchange-online-protection.md). Pour plus d'informations sur l'outil de suivi des messages, consultez la rubrique [Trace an Email Message](https://docs.microsoft.com/exchange/monitoring/trace-an-email-message/trace-an-email-message).

## <a name="reporting-false-positive-and-false-negatives-to-microsoft"></a>Signalement des faux positifs et faux négatifs à Microsoft

Les administrateurs doivent envoyer des faux négatifs (courrier indésirable) et faux positifs (non indésirables) à Microsoft via notre portail d’envoi administratif. Les e-mails, les fichiers et les URL peuvent être envoyés pour aider les administrateurs à déterminer la raison pour laquelle nous avons remis ou ne fournissons pas de messages aux utilisateurs finaux. Pour plus d’informations, reportez-vous à [la rubrique Procédure d’envoi de courrier indésirable, de hameçonnage, d’URL et de fichiers à Microsoft pour Office 365](admin-submission.md).

Les utilisateurs finaux peuvent également signaler directement à Microsoft les faux négatifs (courrier indésirable) et les faux positifs (non du courrier indésirable) en cas d’échec des verdicts. Pour plus d’informations, consultez la rubrique soumettre des messages de courrier indésirable, des courriers [indésirables et des tentatives de hameçonnage à Microsoft pour analyse](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md).


## <a name="create-mail-flow-rules"></a>Création de règles de flux de messagerie

Créez des règles de flux de messagerie ou des filtres personnalisés pour répondre aux besoins de votre entreprise.

Lorsque vous déployez une nouvelle règle en production, commencez par sélectionner l'un des modes test pour voir son effet. Lorsque vous estimez que la règle fonctionne de la manière souhaitée, modifiez son mode d'effet en le définissant sur **Appliquer**.

Lors du déploiement d'une nouvelle règle, songez à ajouter l'action supplémentaire **Générer un rapport d'incident** pour contrôler son action.

Dans les environnements hybrides où votre organisation inclut Exchange et Office 365 sur site, prenez en compte les conditions que vous utilisez dans les règles de flux de messagerie. Si vous souhaitez que les règles s’appliquent à l’ensemble de l’organisation, veillez à utiliser des conditions qui sont disponibles dans Exchange sur site et dans Office 365. Alors que la plupart des conditions sont disponibles dans les deux environnements, il existe quelques éléments qui ne sont disponibles que dans un seul environnement ou l’autre. Pour plus d’informations, consultez la rubrique [règles de flux de messagerie (règles de transport) dans Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).


