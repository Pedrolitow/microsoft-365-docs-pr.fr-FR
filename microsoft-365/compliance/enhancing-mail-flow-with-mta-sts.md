---
title: 'Amélioration du flux de messagerie avec MTA-STS '
f1.keywords:
- NOCSH
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Découvrez comment améliorer le flux de messagerie avec MTA-STS.
ms.openlocfilehash: 735cce96c61a2083b8f0785ace49a5b199790989
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415188"
---
# <a name="enhancing-mail-flow-with-mta-sts"></a>Amélioration du flux de messagerie avec MTA-STS

La prise en charge de la norme [SMTP MTA Strict Transport Security](https://datatracker.ietf.org/doc/html/rfc8461) (MTA-STS) est ajoutée à Exchange Online. La norme a été développée pour garantir que TLS est toujours utilisé pour les connexions entre les serveurs de messagerie. Il fournit également un moyen d’envoyer des serveurs pour vérifier que le serveur de réception dispose d’un certificat approuvé. Si TLS n’est pas proposé ou si le certificat n’est pas valide, l’expéditeur refuse de remettre des messages. Ces nouvelles vérifications améliorent la sécurité globale de SMTP et protègent contre les attaques de l’intercepteur.

MTA-STS peut être divisé en deux scénarios : la protection entrante et sortante. Le trafic entrant couvre la protection des domaines hébergés dans Exchange Online avec MTA-STS et Sortant couvre les validations MTA-STS effectuées par Exchange Online lors de l’envoi d’e-mails à des domaines protégés par MTA-STS.

## <a name="outbound-protection"></a>Protection sortante

Tous les messages envoyés à partir d’Exchange Online vers des destinataires protégés par MTA-STS sont validés avec ces vérifications de sécurité supplémentaires définies par la norme MTA-STS. Les administrateurs n’ont rien à faire pour qu’elle s’applique. Notre implémentation sortante respecte les souhaits des propriétaires de domaine destinataire via leur stratégie MTA-STS. MTA-STS fait partie de l’infrastructure de sécurité d’Exchange Online, et elle est donc toujours activée (comme d’autres fonctionnalités SMTP de base).

## <a name="inbound-protection"></a>Protection entrante

Les propriétaires de domaine peuvent prendre des mesures pour protéger les e-mails envoyés à leurs domaines avec MTA-STS, si leur enregistrement MX pointe vers Exchange Online. Si votre enregistrement MX pointe vers un service tiers intermédiaire, vous devez vérifier que les exigences MTA-STS sont respectées par ces derniers et suivre leurs instructions.

Une fois MTA-STS configuré pour votre domaine, tous les messages envoyés par les expéditeurs qui prennent en charge MTA-STS effectuent les validations définies par la norme pour garantir une connexion sécurisée. Si vous recevez un e-mail d’un expéditeur qui ne prend pas en charge MTA-STS, l’e-mail sera toujours remis sans la protection supplémentaire. De même, il n’y a aucune interruption des messages si vous n’utilisez pas encore MTA-STS, mais que l’expéditeur le prend en charge. Le seul scénario où les messages ne sont’ pas remis est lorsque les deux côtés utilisent MTA-STS et que la validation MTA-STS échoue.

## <a name="how-to-adopt-mta-sts"></a>Guide pratique pour adopter MTA-STS

MTA-STS permet à un domaine de déclarer la prise en charge de TLS et de communiquer l’enregistrement MX et le certificat de destination à attendre. Il indique également ce qu’un serveur d’envoi doit faire en cas de problème. Cette opération s’effectue à l’aide d’une combinaison d’un enregistrement TXT DNS et d’un fichier de stratégie publié sous forme de page web HTTPS. La stratégie protégée par HTTPS introduit une autre protection de sécurité que les attaquants doivent surmonter.

L’enregistrement TXT MTA-STS d’un domaine indique la prise en charge de MTA-STS à un expéditeur, après quoi la stratégie MTA-STS basée sur HTTPS du domaine est récupérée par l’expéditeur. L’enregistrement TXT suivant est un exemple qui déclare la prise en charge de MTA-STS :

`_mta-sts.contoso.com. 3600 IN TXT v=STSv1; id=20220101000000Z;`

La stratégie MTA-STS d’un domaine doit se trouver à une URL prédéfinie hébergée par l’infrastructure web du domaine. La syntaxe de l’URL est `https://mta-sts.<domain name>/.well-known/mta-sts.txt`. Par exemple, la stratégie de Microsoft.com se trouve à l’adresse suivante : <https://mta-sts.microsoft.com/.well-known/mta-sts.txt>.

```text
version: STSv1
mode: enforce
mx: *.mail.protection.outlook.com
max_age: 604800
```

Tout client dont les enregistrements MX pointent directement vers Exchange Online peut spécifier dans sa propre stratégie, avec les mêmes valeurs que celles indiquées ci-dessus dans la stratégie microsoft.com. Les informations requises uniques dans la stratégie sont l’enregistrement MX qui pointe vers Exchange Online (`*`.mail.protection.outlook.com), et le même certificat est partagé par tous les clients Exchange Online. Il est possible de publier votre stratégie en mode de *test* pour s’assurer qu’elle est valide avant de la remplacer par *appliquer* le mode. Il existe des outils de validation tiers qui peuvent vérifier votre configuration.

Ces stratégies ne sont pas quelque chose qu’Exchange Online peut héberger pour le compte des clients et les clients doivent utiliser le service d’hébergement web qu’ils utilisent. La stratégie doit être protégée par HTTPS avec un certificat pour le sous-domaine `mta-sts.<domain name>`. Il existe des alternatives à l’hébergement d’une stratégie, notamment [cette solution](https://github.com/jpawlowski/mta-sts.template) qui utilise les pages GitHub pour l’héberger.

Une fois l’enregistrement de domaine TXT DNS créé et le fichier de stratégie disponible à l’URL HTTPS requise, le domaine sera protégé par MTA-STS. Des détails sur MTA-STS sont disponibles dans [RFC-8461](https://datatracker.ietf.org/doc/html/rfc8461).
