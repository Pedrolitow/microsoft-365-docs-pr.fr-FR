---
title: Veille sur le flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c29f75e5-c16e-409e-a123-430691e38276
description: Les administrateurs peuvent en savoir plus sur les codes d’erreur associés à la remise des messages à l’aide de connecteurs (également appelés renseignements sur le flux de messagerie).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 84029f2f3387913b810c6886a2ac546e587aaca7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60169490"
---
# <a name="mail-flow-intelligence-in-eop"></a>Renseignements sur le flux de courriers dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, vous utilisez généralement un connecteur pour router les messages électroniques d’EOP vers votre environnement de messagerie local. Vous pouvez également utiliser un connecteur pour router des messages depuis Microsoft 365 vers une organisation partenaire. Lorsque Microsoft 365 ne peut pas remettre ces messages via le connecteur, ils sont mis en file d’attente Microsoft 365. Microsoft 365 continueront de réessayer de remise pour chaque message pendant 24 heures. Au bout de 24 heures, le message mis en file d’attente expire et le message est renvoyé à l’expéditeur d’origine dans une non-remise (également appelée rapport de non-remise).

Microsoft 365 génère une erreur lorsqu’un message ne peut pas être remis à l’aide d’un connecteur. Les erreurs les plus courantes et leurs solutions sont décrites dans cet article. Collectivement, les erreurs de mise en file d’accès et de notification pour les messages non transmis envoyés via des connecteurs sont appelées informations de _flux de messagerie._

## <a name="error-code-450-44312-dns-query-failed"></a>Code d’erreur : 450 4.4.312 Échec de la requête DNS

En règle générale, cette erreur signifie Microsoft 365 tentative de connexion à l’hôte intelligent spécifié dans le connecteur, mais que la requête DNS pour rechercher les adresses IP de l’hôte intelligent a échoué. Les causes pouvant être à l'origine de cette erreur sont les suivantes :

- Il y a un problème avec le service d'hébergement DNS de votre domaine (la partie qui met à jour les serveurs de noms faisant autorité pour votre domaine).

- Votre domaine a expiré récemment, l'enregistrement MX ne peut donc pas être extrait.

- L’enregistrement MX de votre domaine a récemment été modifié et les serveurs DNS ont encore mis en cache les informations DNS de votre domaine.

### <a name="how-do-i-fix-error-code-450-44312"></a>Comment corriger le code d’erreur 450 4.4.312 ?

- Travaillez avec votre service d’hébergement DNS pour identifier et résoudre le problème avec votre domaine.

- Si l’erreur vient de votre organisation partenaire (par exemple, un fournisseur de services cloud tiers), contactez votre partenaire pour résoudre le problème.

## <a name="error-code-450-44315-connection-timed-out"></a>Code d’erreur : 450 4.4.315 Délai de connexion dépassé

En règle générale, cela signifie Microsoft 365 ne peut pas se connecter au serveur de messagerie de destination. Les détails de l'erreur expliquent le problème. Par exemple :

- Votre serveur de messagerie local est en panne.

- Une erreur s’est produite dans les paramètres d’hôte intelligent du connecteur, Microsoft 365 tente de se connecter à une adresse IP erronée.

### <a name="how-do-i-fix-error-code-450-44315"></a>Comment corriger le code d’erreur 450 4.4.315 ?

- Déterminez le scénario qui vous concerne et apportez les corrections nécessaires. Par exemple, si le flux de messagerie fonctionne correctement et que vous n’avez pas modifié les paramètres du connecteur, vous devez vérifier votre environnement de messagerie local pour voir si le serveur est en panne ou si des modifications ont été apportées à votre infrastructure réseau (par exemple, vous avez modifié des fournisseurs de services Internet, vous disposez donc d’adresses IP différentes).

- Si l’erreur vient de votre organisation partenaire (par exemple, un fournisseur de services cloud tiers), contactez votre partenaire pour résoudre le problème.

## <a name="error-code-450-44316-connection-refused"></a>Code d’erreur : 450 4.4.316 Connexion refusée.

En règle générale, cette erreur signifie Microsoft 365 a rencontré une erreur de connexion lors de la connexion au serveur de messagerie de destination. Une cause probable de cette erreur est que votre pare-feu bloque les connexions à Microsoft 365 adresses IP. Ou bien, cette erreur peut se faire par conception si vous avez complètement migré votre système de messagerie local vers Microsoft 365 et arrêté votre environnement de messagerie local.

### <a name="how-do-i-fix-error-code-450-44316"></a>Comment corriger le code d’erreur 450 4.4.316 ?

- Si vous avez des boîtes aux lettres dans votre environnement local, vous devez modifier les paramètres de votre pare-feu pour autoriser les connexions entre les adresses IP Microsoft 365 sur le port TCP 25 et vos serveurs de messagerie locaux. Pour obtenir la liste des adresses IP Microsoft 365, voir Microsoft 365 [URL et plages d’adresses IP.](../../enterprise/urls-and-ip-address-ranges.md)

- Si aucun autre message ne doit être remis à  votre environnement local, cliquez sur Corriger maintenant dans l’alerte pour que Microsoft 365 puisse immédiatement rejeter les messages avec des destinataires non valides. Cette action réduira le risque de dépasser le quota de destinataires non valides de votre organisation, ce qui peut avoir des répercussions négatives sur la remise normale des messages. Vous pouvez également suivre les instructions suivantes pour résoudre manuellement le problème :

  - Dans le [Centre d Exchange(EAC),](/Exchange/exchange-admin-center)désactivez ou supprimez le connecteur qui fournit le courrier électronique depuis Microsoft 365 vers votre environnement de messagerie local :

    1. Dans le EAC, allez à **Connecteurs de flux** \> **de messagerie.**

    2. Sélectionnez le  connecteur avec la valeur **De Office 365** et la valeur **À** du serveur de messagerie de votre organisation et faites **l’une** des étapes suivantes :
       - Supprimez le connecteur en cliquant sur **Supprimer** ![ l’icône Supprimer.](../../media/adf01106-cc79-475c-8673-065371c1897b.gif)
       - Désactivez le connecteur en cliquant sur **l’icône** ![ Modifier.](../../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) et effacer **l’activer.**

  - Modifiez le domaine accepté dans Microsoft 365 qui est associé à votre environnement de messagerie local de **Relais** interne à **Faisant autorité**. Pour obtenir des instructions, [voir Gérer les domaines acceptés dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

  **Remarque**: en règle générale, ces modifications prennent entre 30 minutes et une heure pour prendre effet. Après une heure, vérifiez que vous ne recevez plus l’erreur.

- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-44317-cannot-connect-to-remote-server"></a>Code d’erreur : 450 4.4.317 La connexion au serveur distant a échoué

En règle générale, cette erreur signifie Microsoft 365 connecté au serveur de messagerie de destination, mais que le serveur a répondu avec une erreur immédiate ou ne répond pas aux exigences de connexion. Les détails de l'erreur expliquent le problème. Par exemple :

- Le serveur de messagerie de destination a répondu par une erreur « Service non disponible », ce qui indique que le serveur ne peut pas maintenir la communication avec Microsoft 365.
- Le connecteur est configuré pour exiger TLS, mais le serveur de messagerie de destination ne prend pas en charge TLS.

### <a name="how-do-i-fix-error-code-450-44317"></a>Comment corriger le code d’erreur 450 4.4.317 ?

- Vérifiez les paramètres et les certificats TLS sur vos serveurs de messagerie locaux, ainsi que les paramètres TLS sur le connecteur.
- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-44318-connection-was-closed-abruptly"></a>Code d’erreur : 450 4.4.318 La connexion a été interrompue brusquement

En règle générale, cette erreur signifie Microsoft 365 a des difficultés à communiquer avec votre environnement de messagerie local, de sorte que la connexion a été abandonnée. Les causes pouvant être à l'origine de cette erreur sont les suivantes :

- Votre pare-feu utilise des règles d'examen de paquet SMTP, lesquelles ne fonctionnent pas correctement.
- Votre serveur de messagerie local ne fonctionne pas correctement (par exemple, les incidents de service ou les ressources système faibles), ce qui entraîne le délai d’accès du serveur et la fermeture de la connexion à Microsoft 365.
- Il existe des problèmes réseau entre votre environnement local et les Microsoft 365.

### <a name="how-do-i-fix-error-code-450-44318"></a>Comment corriger le code d’erreur 450 4.4.318 ?

- Déterminez le scénario qui vous concerne et apportez les corrections nécessaires.
- Si le problème est dû à des problèmes réseau entre votre environnement local et Microsoft 365, contactez votre équipe réseau pour résoudre le problème.
- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-47320-certificate-validation-failed"></a>Code d’erreur : 450 4.7.320 Échec de la validation du certificat

En règle générale, cette erreur signifie Microsoft 365'une erreur s’est produite lors de la tentative de validation du certificat du serveur de messagerie de destination. Les détails de l'erreur expliquent cette dernière. Par exemple :

- Le certificat est arrivé à expiration.
- Le sujet du certificat ne concorde pas.
- Le certificat n'est plus valide.

### <a name="how-do-i-fix-error-code-450-47320"></a>Comment corriger le code d’erreur 450 4.7.320 ?

- Corrigez le certificat ou les paramètres sur le connecteur afin que les messages en file d’attente Microsoft 365 soient remis.
- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="other-error-codes"></a>Autres codes d’erreur

Microsoft 365 a des difficultés à remettre des messages à votre serveur de messagerie local ou partenaire. Utilisez les informations sur le **serveur de destination** dans l'erreur afin d'examiner le problème dans votre environnement ou modifiez le connecteur en cas d'erreur de configuration.

Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l'origine de l'erreur, vous devez contacter votre partenaire afin de résoudre le problème.
