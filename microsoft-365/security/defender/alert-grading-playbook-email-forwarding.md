---
title: Classement des alertes pour l’activité de transfert de courrier suspect
description: Classement des alertes pour l’activité de transfert de courrier suspect afin de passer en revue les alertes et de prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- met150
ms.openlocfilehash: 4077976243f52c1ace16a0e37361b5f40b9f5a62
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091320"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Classement des alertes pour l’activité de transfert de courrier suspect

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à plusieurs fins malveillantes, notamment la lecture d’e-mails dans la boîte de réception d’un utilisateur, le transfert d’e-mails à des destinataires externes et l’envoi de courriers de hameçonnage, entre autres. L’utilisateur ciblé peut ne pas savoir que ses e-mails sont transférés. Il s’agit d’une tactique très courante que les attaquants utilisent lorsque des comptes d’utilisateur sont compromis.

Les e-mails peuvent être transférés manuellement ou automatiquement à l’aide de règles de transfert. Le transfert automatique peut être implémenté de plusieurs façons, comme les règles de boîte de réception, la règle de transport Exchange (ETR) et le transfert SMTP. Bien que le transfert manuel nécessite une action directe de la part des utilisateurs, il se peut qu’ils ne soient pas au courant de tous les e-mails transférés automatiquement. Dans Microsoft 365, une alerte est déclenchée lorsqu’un utilisateur transfère automatiquement un e-mail à une adresse e-mail potentiellement malveillante.

Ce playbook vous aide à examiner les alertes suspectes d’activité de transfert Email et à les classer rapidement comme un vrai positif (TP) ou un faux positif (FP). Vous pouvez ensuite prendre les actions recommandées pour les alertes TP afin de corriger l’attaque.

Pour obtenir une vue d’ensemble de la notation des alertes pour Microsoft Defender pour Office 365 et Microsoft Defender for Cloud Apps, consultez [l’article d’introduction](alert-grading-playbooks.md).

Les résultats de l’utilisation de ce playbook sont les suivants :

- Vous avez identifié les alertes associées aux e-mails transférés automatiquement comme étant des activités malveillantes (TP) ou bénignes (FP).

  En cas de malveillance, vous avez [arrêté le transfert automatique de courrier](../office-365-security/external-email-forwarding.md) pour les boîtes aux lettres concernées.

- Vous avez pris les mesures nécessaires si des e-mails ont été transférés vers une adresse e-mail malveillante.

## <a name="email-forwarding-rules"></a>Email règles de transfert

Email règles de transfert permettent aux utilisateurs de créer une règle pour transférer les messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers la boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de l’organisation. Certains utilisateurs de messagerie, en particulier ceux qui ont plusieurs boîtes aux lettres, configurent des règles de transfert pour déplacer les e-mails de l’employeur vers leur compte de messagerie privé. Email transfert est une fonctionnalité utile, mais peut également poser un risque pour la sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou ses partenaires.

### <a name="suspicious-email-forwarding-activity"></a>Activité suspecte de transfert d’e-mail

Les attaquants peuvent configurer des règles de messagerie pour masquer les e-mails entrants dans la boîte aux lettres de l’utilisateur compromise afin de masquer leurs activités malveillantes à l’utilisateur. Ils peuvent également définir des règles dans la boîte aux lettres de l’utilisateur compromis pour supprimer les e-mails, déplacer les e-mails vers un autre dossier moins visible, tel qu’un dossier RSS, ou transférer des e-mails vers un compte externe.

Certaines règles peuvent déplacer tous les e-mails vers un autre dossier et les marquer comme « lus », tandis que certaines règles peuvent déplacer uniquement les messages contenant des mots clés spécifiques dans le message électronique ou l’objet. Par exemple, la règle de boîte de réception peut être définie pour rechercher des mots clés tels que « facture », « hameçonnage », « ne pas répondre », « courrier suspect » ou « courrier indésirable », entre autres, et les déplacer vers un compte de messagerie externe. Les attaquants peuvent également utiliser la boîte aux lettres d’utilisateur compromise pour distribuer du courrier indésirable, des e-mails de hameçonnage ou des programmes malveillants.

Microsoft Defender pour Office 365 pouvez détecter et alerter les règles de transfert d’e-mail suspectes, ce qui vous permet de rechercher et de supprimer des règles masquées à la source.

Pour plus d’informations, consultez les billets de blog suivants :

- [Compromis Email d’entreprise](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Compromission de la messagerie professionnelle en arrière-plan : utilisation de données de menace inter-domaines pour interrompre une grande campagne DEC](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)

## <a name="alert-details"></a>Détails de l’alerte

Pour passer en revue l’alerte d’activité de transfert suspecte Email, ouvrez la page **Alertes** pour afficher la section **Liste d’activités**. Voici un exemple.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Liste des activités liées à l’alerte" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Sélectionnez **Activité**  pour afficher les détails de cette activité dans la barre latérale. Voici un exemple.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Détails de l’activité" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Le champ **Raison** contient les informations suivantes relatives à cette alerte.

- Le type de transfert (FT) est l’un des éléments suivants :
  - Règle de transport Exchange (ETR) : transfert à l’aide et règle de transport Exchange
  - SMTP : transféré à l’aide du transfert de boîte aux lettres
  - InboxRule : transféré à l’aide d’une règle de boîte de réception

- ID de trace de message (MTI) : il s’agit de l’identificateur (NetworkMessageId) de l’e-mail transféré qui a déclenché cette alerte. NetworkMessageId est l’identificateur unique d’un e-mail dans votre organisation.
- Redirecteur (F) : utilisateur qui a transféré cet e-mail.
- Liste des destinataires suspects (SRL) : liste des destinataires considérés comme suspects dans cet e-mail.
- Liste des destinataires :liste de tous les destinataires de cet e-mail.

## <a name="investigation-workflow"></a>Flux de travail d’investigation

Lors de l’examen de cette alerte, vous devez déterminer :

- Le compte d’utilisateur et sa boîte aux lettres sont-ils compromis ?
- Les activités sont-elles malveillantes ?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Le compte d’utilisateur et sa boîte aux lettres sont-ils compromis ?

En examinant le comportement passé de l’expéditeur et les activités récentes, vous devez être en mesure de déterminer si le compte de l’utilisateur doit être considéré comme compromis ou non. Vous pouvez voir les détails des alertes déclenchées à partir de la page de l’utilisateur dans le portail Microsoft 365 Defender.

Vous pouvez également analyser ces activités supplémentaires pour la boîte aux lettres affectée :

- Utiliser l’Explorateur de menaces pour comprendre les menaces liées aux e-mails
  - Observez le nombre d’e-mails récents envoyés par l’expéditeur qui sont détectés comme des hameçonnages, du courrier indésirable ou des programmes malveillants.
  - Observez le nombre d’e-mails envoyés contenant des informations sensibles.

- Évaluez le comportement de connexion à risque dans microsoft Portail Azure.
- Recherchez les activités malveillantes sur l’appareil de l’utilisateur.

### <a name="are-the-activities-malicious"></a>Les activités sont-elles malveillantes ?

Examinez l’activité de transfert d’e-mail. Par exemple, vérifiez le type d’e-mail, le destinataire de cet e-mail ou la manière dont l’e-mail est transféré.

Si vous souhaitez en savoir plus, consultez les articles suivants :

- [Aperçu des messages transférés automatiquement](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Informations sur les courriers électroniques de nouveaux utilisateurs](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Répondre à un compte d'e-mail compromis](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Signaler les faux positifs et les faux négatifs dans Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Voici le flux de travail permettant d’identifier les activités suspectes de transfert de courrier électronique.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Flux de travail d’investigation des alertes pour le transfert de courrier électronique" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Vous pouvez examiner une alerte de transfert par e-mail à l’aide de l’Explorateur de menaces ou avec des requêtes de repérage avancées, en fonction de la disponibilité des fonctionnalités dans le portail Microsoft 365 Defender. Vous pouvez choisir de suivre l’intégralité du processus ou une partie du processus en fonction des besoins.

## <a name="using-threat-explorer"></a>Utilisation de l’Explorateur de menaces

L’Explorateur de menaces fournit une expérience d’investigation interactive pour les menaces liées aux e-mails afin de déterminer si cette activité est suspecte ou non. Vous pouvez utiliser les indicateurs suivants à partir des informations d’alerte :

- Liste de révocation de certificats/liste de révocation de certificats : utilisez la liste des destinataires (suspects) pour trouver les informations suivantes :

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Exemple de liste de destinataires" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

  - Qui d’autre a transféré des e-mails à ces destinataires ?
  - Combien d’e-mails ont été transférés à ces destinataires ?
  - À quelle fréquence les e-mails sont-ils transférés à ces destinataires ?

- MTI : Utilisez l’ID de trace de message/L’ID de message réseau pour trouver les informations suivantes :

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Exemple d’ID de message réseau" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

  - Quels détails supplémentaires sont disponibles pour cet e-mail ? Par exemple : objet, chemin d’accès de retour et horodatage.
  - Quelle est l’origine de cet e-mail ? Y a-t-il des e-mails similaires ?
  - Cet e-mail contient-il des URL ? L’URL pointe-t-elle vers des données sensibles ?
  - L’e-mail contient-il des pièces jointes ? Les pièces jointes contiennent-elles des informations sensibles ?
  - Quelle a été l’action effectuée sur l’e-mail ? A-t-il été supprimé, marqué comme lu ou déplacé vers un autre dossier ?
  - Existe-t-il des menaces associées à cet e-mail ? Cet e-mail fait-il partie d’une campagne ?

En fonction des réponses à ces questions, vous devez être en mesure de déterminer si un e-mail est malveillant ou bénin.

## <a name="advanced-hunting-queries"></a>Requêtes de repérage avancées

Pour utiliser des requêtes [de chasse avancées](advanced-hunting-overview.md) pour collecter des informations relatives à une alerte et déterminer si l’activité est suspecte ou non, assurez-vous d’avoir accès aux tableaux suivants :

- EmailEvents : contient des informations relatives au flux de courrier électronique.

- EmailUrlInfo : contient des informations relatives aux URL dans les e-mails.

- CloudAppEvents : contient le journal d’audit des activités des utilisateurs.

- IdentityLogonEvents : contient des informations de connexion pour tous les utilisateurs.

> [!NOTE]
> Certains paramètres sont propres à votre organisation ou réseau. Renseignez ces paramètres spécifiques comme indiqué dans chaque requête.

Exécutez cette requête pour savoir qui d’autre a transféré des e-mails à ces destinataires (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Exécutez cette requête pour savoir combien d’e-mails ont été transférés à ces destinataires.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

Exécutez cette requête pour déterminer la fréquence à laquelle les e-mails sont transférés à ces destinataires.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

Exécutez cette requête pour savoir si l’e-mail contient des URL.

```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

Exécutez cette requête pour savoir si l’e-mail contient des pièces jointes.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

Exécutez cette requête pour savoir si le redirecteur (expéditeur) a créé de nouvelles règles.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with display name of Forwarder
let action_types = pack_array(
    "New-InboxRule",
    "UpdateInboxRules",
    "Set-InboxRule",
    "Set-Mailbox",
    "New-TransportRule",
    "Set-TransportRule");
CloudAppEvents
| where AccountDisplayName == sender
| where ActionType in (action_types)
```

Exécutez cette requête pour savoir s’il y a eu des événements de connexion anormaux de la part de cet utilisateur. Par exemple : adresses IP inconnues, nouvelles applications, pays rares, événements logonFailed multiples.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Examen des règles de transfert

Vous pouvez également trouver des règles de transfert suspectes à l’aide du Centre d’administration Exchange, en fonction du type de règle (valeur FT dans l’alerte).

- ETR

  Les règles de transport Exchange sont répertoriées dans la section **Règles** . Vérifiez que toutes les règles sont comme prévu.

- SMTP

  Vous pouvez voir les règles de transfert de boîte aux lettres en sélectionnant la boîte aux **lettres\> gérer les paramètres \> de flux de courrier de l’expéditeur Email modifier le \> transfert**.

- InboxRule

  Les règles de boîte de réception sont configurées avec le client de messagerie. Vous pouvez utiliser l’applet de commande [PowerShell Get-InboxRule](/powershell/module/exchange/get-inboxrule) pour répertorier les règles de boîte de réception créées par les utilisateurs.

### <a name="additional-investigation"></a>Examen supplémentaire

En plus des preuves découvertes jusqu’à présent, vous pouvez déterminer si de nouvelles règles de transfert sont créées. Examinez l’adresse IP associée à la règle. Assurez-vous qu’il ne s’agit pas d’une adresse IP anormale et qu’il est cohérent avec les activités habituelles effectuées par l’utilisateur.

## <a name="recommended-actions"></a>Actions recommandées

Une fois que vous avez déterminé que les activités associées font de cette alerte un vrai positif, classifiez l’alerte et effectuez les actions suivantes pour la correction :

1. Désactivez et supprimez la règle de transfert de boîte de réception.
2. Pour le type de transfert InboxRule, réinitialisez les informations d’identification du compte de l’utilisateur.
3. Pour le type de transfert SMTP ou ETR, examinez les activités du compte d’utilisateur qui a créé l’alerte.

    - Examinez toutes les autres activités d’administration suspectes.

    - Réinitialiser les informations d’identification du compte d’utilisateur.

4. Recherchez des activités supplémentaires provenant de comptes impactés, d’adresses IP et d’expéditeurs suspects.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du classement des alertes](alert-grading-playbooks.md)
- [Règle de transfert de boîte de réception suspect](alert-grading-playbook-inbox-forwarding-rules.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Examiner des alertes](investigate-alerts.md)
