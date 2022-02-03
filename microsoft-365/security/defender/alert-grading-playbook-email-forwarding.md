---
title: Notation des alertes pour une activité de forwarding de courrier suspecte
description: Notation des alertes pour une activité suspecte de transport de courrier pour passer en revue les alertes et prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 83e8061d2c9473c274d615c8905b2918e1b72d17
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62355137"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Notation des alertes pour une activité de forwarding de courrier suspecte

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les acteurs des menaces peuvent utiliser des comptes d’utilisateur compromis à plusieurs fins malveillantes, notamment pour lire des e-mails dans la boîte de réception d’un utilisateur, les transmettre à des destinataires externes et envoyer des messages de hameçonnage, entre autres. Il se peut que l’utilisateur ciblé ignore que ses messages électroniques sont en cours de forward. Il s’agit d’une tactique très courante que les attaquants utilisent lorsque les comptes d’utilisateur sont compromis.

Les e-mails peuvent être transmis manuellement ou automatiquement à l’aide de règles de transmission. Le transport automatique peut être implémenté de plusieurs manières, telles que les règles de boîte de réception, Exchange de transport (ETR) et le transport SMTP. Bien que le forwarding manuel nécessite une action directe de la part des utilisateurs, il se peut qu’ils ne connaissent pas tous les e-mails transmis automatiquement. Dans Microsoft 365, une alerte est alerte lorsqu’un utilisateur envoie automatiquement un message électronique à une adresse de messagerie potentiellement malveillante.

Ce manuel vous permet d’examiner les alertes de forwarding de courrier suspect et de les classer rapidement en tant que vrai positif (TP) ou faux positif (FP). Vous pouvez ensuite prendre des mesures recommandées pour les alertes TP afin de corriger l’attaque.

Pour obtenir une vue d’ensemble de la notation des alertes pour Microsoft Defender pour Office 365 et Microsoft Defender pour les applications cloud, consultez [l’article d’introduction](alert-grading-playbooks.md).

Les résultats de l’utilisation de ce manuel sont les :

- Vous avez identifié les alertes associées aux e-mails automatiquement transmis en tant qu’activités malveillantes (TP) ou associées (FP).

  S’il est malveillant, vous [avez arrêté le forwarding automatique](../office-365-security/external-email-forwarding.md) du courrier électronique pour les boîtes aux lettres concernées.

- Vous avez pris les mesures nécessaires si les messages électroniques ont été transmis à une adresse de messagerie malveillante.

## <a name="email-forwarding-rules"></a>Règles de forwarding du courrier électronique

La règle de forwarding de courrier permet aux utilisateurs de configurer une règle pour le forward des messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers la boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de l’organisation. Certains utilisateurs de messagerie, en particulier ceux qui ont plusieurs boîtes aux lettres, configurent des règles de forwarding pour déplacer les courriers électroniques des employeurs vers leurs comptes de messagerie privés. Le forwarding de courrier électronique est une fonctionnalité utile, mais peut également poser un risque de sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou ses partenaires.

### <a name="suspicious-email-forwarding-rules"></a>Règles de forwarding de courrier suspecte

Les attaquants peuvent configurer des règles de messagerie pour masquer les e-mails entrants dans la boîte aux lettres de l’utilisateur compromis afin d’masquer leurs activités malveillantes à l’utilisateur. Ils peuvent également définir des règles dans la boîte aux lettres utilisateur compromise pour supprimer des e-mails, déplacer les messages électroniques dans un autre dossier moins perceptible, tel qu’un dossier RSS, ou les envoyer à un compte externe.  

Certaines règles peuvent déplacer tous les e-mails vers un autre dossier et les marquer comme « lus », tandis que certaines règles peuvent déplacer uniquement les messages électroniques qui contiennent des mots clés spécifiques dans le message électronique ou l’objet. Par exemple, la règle de boîte de réception peut être définie pour rechercher des mots clés tels que « facture », « hameçonnage », « ne pas répondre », « courrier suspect » ou « courrier indésirable » entre autres, et les déplacer vers un compte de messagerie externe. Les personnes malveillantes peuvent également utiliser la boîte aux lettres de l’utilisateur compromis pour distribuer du courrier indésirable, des e-mails de hameçonnage ou des programmes malveillants.
 
Microsoft Defender pour Office 365 détecter et alerter les règles de forwarding de courrier suspectes, ce qui vous permet de rechercher et de supprimer des règles masquées à la source.

Pour plus d’informations, consultez les billets de blog ci-après :

- [Compromission de la messagerie professionnelle](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [Compromission du courrier électronique d’entreprise : utilisation de données sur les menaces entre domaines pour perturber une grande campagne DE GESTION](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)


## <a name="alert-details"></a>Détails de l’alerte

Pour passer en revue l’alerte spécifique, ouvrez la page **Alertes** pour voir la section **Liste d’activités** . Voici un exemple.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Liste des activités liées à l’alerte" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

**Sélectionnez Activité** pour afficher les détails de cette activité dans la barre latérale. Voici un exemple.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Détails de l’activité" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Le **champ Raison** contient les informations suivantes relatives à cette alerte.

- Le type de forwarding (FT) est l’un des suivants :

    -  Exchange Transport Rule (ETR) : règle de transport Exchange et de transport 

    -  SMTP : transmis à l’aide du forwarding de boîtes aux lettres

    -  InboxRule : transmis à l’aide d’une règle de boîte de réception

- ID de suivi des messages (MTI) : il s’agit de l’identificateur (NetworkMessageId) du courrier électronique transmis qui a déclenché cette alerte. NetworkMessageId est l’identificateur unique d’un message électronique dans votre organisation.
- Forwarder (F) : utilisateur qui a transmis ce courrier électronique.
- Liste des destinataires suspects (SRL) : liste des destinataires considérés comme suspects dans cet e-mail.
- Liste des destinataires (RL) : liste de tous les destinataires de ce message électronique.

## <a name="investigation-workflow"></a>Flux de travail d’examen

Lors de l’étude de cette alerte, vous devez déterminer :

- Le compte d’utilisateur et sa boîte aux lettres sont-ils compromis ?
- Les activités sont-elles malveillantes ?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Le compte d’utilisateur et sa boîte aux lettres sont-ils compromis ?

En regardant le comportement passé de l’expéditeur et les activités récentes, vous devez être en mesure de déterminer si le compte de l’utilisateur doit être considéré comme compromis ou non. Vous pouvez voir les détails des alertes à partir de la page de l’utilisateur dans le portail Microsoft 365 Defender web. 

Vous pouvez également analyser ces activités supplémentaires pour la boîte aux lettres concernée :

- Utiliser l’Explorateur de menaces pour comprendre les menaces liées à la messagerie

    - Observez le nombre d’e-mails récents envoyés par l’expéditeur détectés comme hameçonnage, courrier indésirable ou programme malveillant.

    - Observez le nombre d’e-mails envoyés contenant des informations sensibles. 

- Évaluez le comportement de la connectez-vous à risque dans Microsoft Azure portail.
- Recherchez les activités malveillantes sur l’appareil de l’utilisateur.

### <a name="are-the-activities-malicious"></a>Les activités sont-elles malveillantes ?

Examinez l’activité de forwarding du courrier électronique. Par exemple, vérifiez le type d’e-mail, le destinataire de ce courrier électronique ou la manière dont le message est transmis. 

Si vous souhaitez en savoir plus, consultez les articles suivants :

- [Aperçu des messages transférés automatiquement](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [Informations sur les courriers électroniques de nouveaux utilisateurs](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Répondre à un compte d'e-mail compromis](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Signaler les faux positifs et les faux négatifs dans Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

Voici le flux de travail permettant d’identifier les activités suspectes de forwarding de courrier.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="Flux de travail d’investigation d’alerte pour le forwarding de courrier électronique" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Vous pouvez examiner une alerte de forwarding de courrier électronique à l’aide de l’Explorateur de menaces ou avec des requêtes de recherche avancées, en fonction de la disponibilité des fonctionnalités dans le portail Microsoft 365 Defender. Vous pouvez choisir de suivre l’ensemble du processus ou une partie du processus selon vos besoins.

## <a name="using-threat-explorer"></a>Utilisation de l’Explorateur de menaces

L’Explorateur de menaces offre une expérience d’examen interactive pour les menaces liées au courrier électronique afin de déterminer si cette activité est suspecte ou non. Vous pouvez utiliser les indicateurs suivants à partir des informations d’alerte :

- SRL/RL : utilisez la liste des destinataires (suspects) pour rechercher les détails ci-dessous :
 
    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Exemple de liste de destinataires" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

    - Qui d’autres messages électroniques ont été transmis à ces destinataires ?

    - Combien de messages électroniques ont été transmis à ces destinataires ?

    - À quelle fréquence les messages électroniques sont-ils transmis à ces destinataires ?
 

- MTI : utilisez l’ID de suivi des messages/ID de message réseau pour rechercher les détails suivants :

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Exemple d’ID de message réseau" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

    - Quels détails supplémentaires sont disponibles pour cet e-mail ? Par exemple : objet, chemin d’accès de retour et timestamp.

    - Quelle est l’origine de ce courrier électronique ? Existe-t-il des e-mails similaires ?

    - Cet e-mail contient-il des URL ? L’URL pointe-t-elle vers des données sensibles ?

    - L’e-mail contient-il des pièces jointes ? Les pièces jointes contiennent-elles des informations sensibles ?

    - Quelle a été l’action prise sur le courrier électronique ? A-t-il été supprimé, marqué comme lu ou déplacé vers un autre dossier ?

    - Y a-t-il des menaces associées à ce courrier électronique ? Cet e-mail fait-il partie d’une campagne ?

En fonction des réponses à ces questions, vous devez être en mesure de déterminer si un e-mail est malveillant ou non.

## <a name="advanced-hunting-queries"></a>Requêtes de recherche avancées

Pour utiliser [des requêtes de](advanced-hunting-overview.md) recherche avancées pour collecter des informations relatives à une alerte et déterminer si l’activité est suspecte ou non, assurez-vous que vous avez accès aux tableaux suivants :

- EmailEvents : contient des informations relatives au flux de messagerie.

- EmailUrlInfo : contient des informations relatives aux URL dans les e-mails.

- CloudAppEvents - Contient le journal d’audit des activités des utilisateurs.

- IdentityLogonEvents : contient les informations de connexion de tous les utilisateurs.

Voici un exemple.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-advanced-hunting.png" alt-text="Exemple de page de recherche avancée" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-advanced-hunting.png":::

Utilisez des requêtes pour recueillir des informations pour les questions suivantes.

>[!Note]
>Certains paramètres sont propres à votre organisation ou réseau. Remplissez ces paramètres spécifiques comme indiqué dans chaque requête.
>

Exécutez cette requête pour savoir qui d’autre a transmis des messages électroniques à ces destinataires (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Exécutez cette requête pour connaître le nombre de messages électroniques qui ont été transmis à ces destinataires.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

Exécutez cette requête pour savoir à quelle fréquence les messages électroniques sont-ils transmis à ces destinataires .

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

Exécutez cette requête pour savoir si le forwardeur (expéditeur) a créé de nouvelles règles.

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

Exécutez cette requête pour savoir s’il existe des événements de connexion anormaux de cet utilisateur. Par exemple : des IP inconnus, de nouvelles applications, des pays rares, plusieurs événements LogonFailed.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Étude des règles de forwarding

Vous pouvez également rechercher des règles de Exchange à l’aide du centre d’administration, en fonction du type de règle (valeur FT dans l’alerte).

- ETR 

  Exchange de transport sont répertoriées dans la section **Règles**. Vérifiez que toutes les règles sont comme prévu.

- SMTP

  Vous pouvez voir les règles de forwarding de boîte aux lettres en sélectionnant la boîte aux lettres de l’expéditeur **\>  Gérer les paramètres de flux de messagerie \> Modifier le flux de \> messagerie**.

- InboxRule

  Les règles de boîte de réception sont configurées avec le client de messagerie. Vous pouvez utiliser l’cmdlet [Get-InboxRule](/powershell/module/exchange/get-inboxrule) PowerShell pour lister les règles de boîte de réception créées par les utilisateurs.

### <a name="additional-investigation"></a>Examen supplémentaire

En plus des preuves découvertes jusqu’à présent, vous pouvez déterminer s’il existe de nouvelles règles de forwarding en cours de création. Examinez l’adresse IP associée à la règle. Assurez-vous qu’il ne s’agit pas d’une adresse IP anormale et qu’elle est cohérente avec les activités habituelles effectuées par l’utilisateur.

## <a name="recommended-actions"></a>Actions recommandées

Une fois que vous avez déterminez que les activités associées rendent cette alerte vraie positive, classifiez l’alerte et prenez les mesures ci-après pour la correction :

1. Désactivez et supprimez la règle de forwarding de boîte de réception.
2. Pour le type de forwarding InboxRule, réinitialisez les informations d’identification du compte de l’utilisateur.
3. Pour le type de forwarding SMTP ou ETR, examinez les activités du compte d’utilisateur qui a créé l’alerte.

    - Examinez toute autre activité d’administrateur suspecte.

    - Réinitialisez les informations d’identification du compte d’utilisateur.

4. Recherchez les activités supplémentaires provenant de comptes, d’adresses IP et d’expéditeurs suspects touchés.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la notation des alertes](alert-grading-playbooks.md)
- [Règles de forwarding de boîte de réception suspectes](alert-grading-playbook-inbox-forwarding-rules.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Examiner des alertes](investigate-alerts.md)
