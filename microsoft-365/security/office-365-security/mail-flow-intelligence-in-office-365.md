---
title: Intelligence de flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c29f75e5-c16e-409e-a123-430691e38276
description: Les administrateurs peuvent en savoir plus sur les codes d’erreur associés à la remise des messages à l’aide de connecteurs (également appelés intelligence de flux de messagerie).
ms.openlocfilehash: 461d9bfa91d88b8bbec52d5aad6ec7a2e534bc96
ms.sourcegitcommit: b64f36d3873fa0041b24bec029deb73ccfdfdbac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877800"
---
# <a name="mail-flow-intelligence-in-eop"></a>Renseignements sur le flux de courriers dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous utilisez généralement un connecteur pour acheminer les messages électroniques d’EOP vers votre environnement de messagerie local. Vous pouvez également utiliser un connecteur pour router les messages de Microsoft 365 vers une organisation partenaire. Lorsque Microsoft 365 ne peut pas fournir ces messages via le connecteur, ils sont mis en file d’attente dans Microsoft 365. Microsoft 365 continue de relancer la remise de chaque message pendant 24 heures. Au bout de 24 heures, le message en file d’attente expire et le message est renvoyé à l’expéditeur d’origine dans une notification d’échec de remise (également appelée notification de non-remise).

Microsoft 365 génère une erreur lorsqu’un message ne peut pas être remis à l’aide d’un connecteur. Les erreurs les plus courantes et leurs solutions sont décrites dans cette rubrique. Les erreurs de notification et de mise en file d’attente pour les messages non remis envoyés via des connecteurs sont appelées _intelligence de flux de messagerie_.

## <a name="error-code-450-44312-dns-query-failed"></a>Code d’erreur : 450 4.4.312 Échec de la requête DNS

En règle générale, cette erreur signifie que Microsoft 365 a essayé de se connecter à l’hôte actif qui est spécifié dans le connecteur, mais que la requête DNS de recherche des adresses IP de l’hôte actif a échoué. Les causes pouvant être à l'origine de cette erreur sont les suivantes :

- Il y a un problème avec le service d'hébergement DNS de votre domaine (la partie qui met à jour les serveurs de noms faisant autorité pour votre domaine).

- Votre domaine a expiré récemment, l'enregistrement MX ne peut donc pas être extrait.

- L’enregistrement MX de votre domaine a récemment été modifié et les serveurs DNS disposent toujours des informations DNS précédemment mises en cache pour votre domaine.

### <a name="how-do-i-fix-error-code-450-44312"></a>Comment corriger le code d’erreur 450 4.4.312 échec ?

- Collaborez avec votre service d’hébergement DNS pour identifier et résoudre le problème lié à votre domaine.

- Si l’erreur provient de votre organisation partenaire (par exemple, un fournisseur de services Cloud tiers), contactez votre partenaire pour résoudre le problème.

## <a name="error-code-450-44315-connection-timed-out"></a>Code d’erreur : 450 4.4.315 Délai de connexion dépassé

En règle générale, cela signifie que Microsoft 365 ne peut pas se connecter au serveur de messagerie de destination. Les détails de l'erreur expliquent le problème. Par exemple :

- Votre serveur de messagerie local est inactif.

- Il y a une erreur dans les paramètres d’hôte actif du connecteur, donc Microsoft 365 tente de se connecter à une adresse IP incorrecte.

### <a name="how-do-i-fix-error-code-450-44315"></a>Comment corriger le code d’erreur 450 4.4.315 délai ?

- Déterminez le scénario qui vous concerne et apportez les corrections nécessaires. Par exemple, si le flux de messagerie fonctionne correctement et que vous n’avez pas modifié les paramètres du connecteur, vous devez vérifier votre environnement de messagerie local pour déterminer si le serveur est inactif ou, s’il y a eu des modifications apportées à votre infrastructure réseau (par exemple, si vous avez modifié les fournisseurs de services Internet, vous avez maintenant des adresses IP différentes).

- Si l’erreur provient de votre organisation partenaire (par exemple, un fournisseur de services Cloud tiers), contactez votre partenaire pour résoudre le problème.

## <a name="error-code-450-44316-connection-refused"></a>Code d’erreur : 450 4.4.316 Connexion refusée.

En règle générale, cette erreur signifie que Microsoft 365 a rencontré une erreur de connexion lorsqu’il a essayé de se connecter au serveur de messagerie de destination. Une cause probable de cette erreur est que votre pare-feu bloque les connexions des adresses IP Microsoft 365. Cette erreur peut également être voulue si vous avez entièrement migré votre système de messagerie local vers Microsoft 365 et arrêté votre environnement de messagerie local.

### <a name="how-do-i-fix-error-code-450-44316"></a>Comment corriger le code d’erreur 450 4.4.316 ?

- Si vous avez des boîtes aux lettres dans votre environnement local, vous devez modifier les paramètres de votre pare-feu pour autoriser les connexions des adresses IP Microsoft 365 sur le port TCP 25 à vos serveurs de messagerie locaux. Pour obtenir la liste des adresses IP Microsoft 365, voir [URL et plages d’adresses IP microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges).

- Si aucun autre message ne doit être remis à votre environnement local, cliquez sur **corriger maintenant** dans l’alerte afin que Microsoft 365 puisse rejeter immédiatement les messages dont les destinataires ne sont pas valides. Cette action réduira le risque de dépasser le quota de destinataires non valides de votre organisation, ce qui peut avoir des répercussions négatives sur la remise normale des messages. Vous pouvez également suivre les instructions suivantes pour résoudre manuellement le problème :

  - Dans le [Centre d’administration Exchange](https://docs.microsoft.com/Exchange/exchange-admin-center), désactivez ou supprimez le connecteur qui remet le courrier électronique de Microsoft 365 à votre environnement de messagerie local :

    1. Dans le centre d’administration Exchange, accédez à connecteurs de **flux de messagerie** \> **Connectors**.

    2. Sélectionnez le connecteur avec la valeur **à partir d'** **Office 365** et la valeur **pour** le **serveur de messagerie de votre organisation** , puis effectuez l’une des opérations suivantes :

       - Supprimez le connecteur en cliquant sur **supprimer** l' ![ icône Supprimer.](../../media/adf01106-cc79-475c-8673-065371c1897b.gif)

       - Désactivez le connecteur en cliquant sur **modifier** l' ![ icône modifier, puis désactivez l’option ](../../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) **activer**.

  - Modifiez le domaine accepté dans Microsoft 365 qui est associé à votre environnement de messagerie local de **relais interne** à **faisant autorité**. Pour obtenir des instructions, consultez la rubrique [gestion des domaines acceptés dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

  **Remarque** : en règle générale, ces modifications prennent entre 30 minutes et une heure pour prendre effet. Après une heure, vérifiez que vous ne recevez plus l’erreur.

- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-44317-cannot-connect-to-remote-server"></a>Code d’erreur : 450 4.4.317 La connexion au serveur distant a échoué

En règle générale, cette erreur signifie que Microsoft 365 est connecté au serveur de messagerie de destination, mais que le serveur a répondu avec une erreur immédiate ou ne répond pas aux exigences de connexion. Les détails de l'erreur expliquent le problème. Par exemple :

- Le serveur de messagerie de destination a répondu avec une erreur « service non disponible », ce qui indique que le serveur n’est pas en mesure de maintenir la communication avec Microsoft 365.

- Le connecteur est configuré pour exiger TLS, mais le serveur de messagerie de destination ne prend pas en charge le protocole TLS.

### <a name="how-do-i-fix-error-code-450-44317"></a>Comment corriger le code d’erreur 450 4.4.317 ?

- Vérifiez les certificats et les paramètres TLS sur vos serveurs de messagerie locaux, ainsi que les paramètres TLS sur le connecteur.

- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-44318-connection-was-closed-abruptly"></a>Code d’erreur : 450 4.4.318 La connexion a été interrompue brusquement

En règle générale, cette erreur signifie que Microsoft 365 rencontre des difficultés pour communiquer avec votre environnement de messagerie local, de sorte que la connexion a été abandonnée. Les causes pouvant être à l'origine de cette erreur sont les suivantes :

- Votre pare-feu utilise des règles d'examen de paquet SMTP, lesquelles ne fonctionnent pas correctement.

- Votre serveur de messagerie local ne fonctionne pas correctement (par exemple, blocage du service, blocage ou ressources système faibles), ce qui entraîne l’expiration du serveur et la fermeture de la connexion à Microsoft 365.

- Il existe des problèmes de réseau entre votre environnement local et Microsoft 365.

### <a name="how-do-i-fix-error-code-450-44318"></a>Comment corriger le code d’erreur 450 4.4.318 la ?

- Déterminez le scénario qui vous concerne et apportez les corrections nécessaires.

- Si le problème est dû à des problèmes de réseau entre votre environnement local et Microsoft 365, contactez votre équipe réseau pour résoudre le problème.

- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="error-code-450-47320-certificate-validation-failed"></a>Code d’erreur : 450 4.7.320 Échec de la validation du certificat

En règle générale, cette erreur signifie que Microsoft 365 a rencontré une erreur lors de la tentative de validation du certificat du serveur de messagerie de destination. Les détails de l'erreur expliquent cette dernière. Par exemple :

- Le certificat est arrivé à expiration.

- Le sujet du certificat ne concorde pas.

- Le certificat n'est plus valide.

### <a name="how-do-i-fix-error-code-450-47320"></a>Comment corriger le code d’erreur 450 4.7.320 échec ?

- Corrigez le certificat ou les paramètres sur le connecteur afin que les messages en file d’attente dans Microsoft 365 puissent être remis.

- Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l’origine de l’erreur, vous devez contacter votre partenaire afin de résoudre le problème.

## <a name="other-error-codes"></a>Autres codes d’erreur

Microsoft 365 rencontre des difficultés lors de la remise de messages à votre serveur de messagerie local ou partenaire. Utilisez les informations sur le **serveur de destination** dans l'erreur afin d'examiner le problème dans votre environnement ou modifiez le connecteur en cas d'erreur de configuration.

Si votre organisation partenaire (par exemple, un fournisseur de services cloud tiers) est à l'origine de l'erreur, vous devez contacter votre partenaire afin de résoudre le problème.
