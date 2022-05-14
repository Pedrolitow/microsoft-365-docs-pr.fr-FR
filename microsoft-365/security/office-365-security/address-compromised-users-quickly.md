---
title: Résoudre les comptes d’utilisateur compromis avec une investigation et une réponse automatisées
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, investigation, réponse, correction, menaces, avancées, menaces, protection, compromis
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.custom: ''
ms.date: 06/10/2021
description: Découvrez comment accélérer le processus de détection et de traitement des comptes d’utilisateur compromis avec des fonctionnalités d’investigation et de réponse automatisées dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 97466622a138a6604b9be51333148b472f7cd519
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418267"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Résoudre les comptes d’utilisateur compromis avec une investigation et une réponse automatisées

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) inclut de puissantes fonctionnalités [d’investigation et de réponse automatisées](office-365-air.md) (AIR). Ces fonctionnalités peuvent faire gagner beaucoup de temps et d’efforts à votre équipe chargée des opérations de sécurité face aux menaces. Microsoft continue d’améliorer les fonctionnalités de sécurité. Récemment, les fonctionnalités AIR ont été améliorées pour inclure un playbook de sécurité utilisateur compromis (actuellement en préversion). Lisez cet article pour en savoir plus sur le playbook de sécurité des utilisateurs compromis. Pour plus d’informations, consultez le billet de blog [Accélérer le temps de détection et de réponse à la compromission de l’utilisateur et limiter l’étendue de la violation avec Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053).

![Investigation automatisée pour un utilisateur compromis.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Le playbook de sécurité utilisateur compromis permet à l’équipe de sécurité de votre organisation d’effectuer les opérations suivantes :

- Accélérer la détection des comptes d’utilisateur compromis ;
- Limitez l’étendue d’une violation lorsqu’un compte est compromis ; Et
- Répondez aux utilisateurs compromis de manière plus efficace et plus efficace.

## <a name="compromised-user-alerts"></a>Alertes utilisateur compromises

Lorsqu’un compte d’utilisateur est compromis, des comportements atypiques ou anormaux se produisent. Par exemple, les messages de hameçonnage et de courrier indésirable peuvent être envoyés en interne à partir d’un compte d’utilisateur approuvé. Defender pour Office 365 pouvez détecter ces anomalies dans les modèles de messagerie et l’activité de collaboration dans Office 365. Dans ce cas, des alertes sont déclenchées et le processus d’atténuation des menaces commence.

Par exemple, voici une alerte qui a été déclenchée en raison de l’envoi d’e-mails suspects :

![Alerte déclenchée en raison de l’envoi d’e-mails suspects.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Voici un exemple d’alerte qui a été déclenchée lorsqu’une limite d’envoi a été atteinte pour un utilisateur :

![Alerte déclenchée par l’envoi d’une limite atteinte.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Examiner et répondre à un utilisateur compromis

Lorsqu’un compte d’utilisateur est compromis, des alertes sont déclenchées. Et dans certains cas, ce compte d’utilisateur est bloqué et empêché d’envoyer d’autres messages électroniques tant que le problème n’est pas résolu par l’équipe des opérations de sécurité de votre organisation. Dans d’autres cas, une enquête automatisée commence, ce qui peut entraîner des actions recommandées que votre équipe de sécurité doit effectuer.

- [Afficher et examiner les utilisateurs restreints](#view-and-investigate-restricted-users)

- [Afficher les détails des investigations automatisées](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Vous devez disposer des autorisations appropriées pour effectuer les tâches suivantes. Consultez [Autorisations requises pour utiliser les fonctionnalités AIR](office-365-air.md#required-permissions-to-use-air-capabilities).

Regardez cette courte vidéo pour découvrir comment détecter et répondre aux compromissions de l’utilisateur dans Microsoft Defender pour Office 365 à l’aide d’air (Automated Investigation and Response) et d’alertes utilisateur compromises.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWAl83]

### <a name="view-and-investigate-restricted-users"></a>Afficher et examiner les utilisateurs restreints

Vous disposez de quelques options pour accéder à une liste d’utilisateurs restreints. Par exemple, dans le portail Microsoft 365 Defender, vous pouvez accéder à **Email & Collaboration** \> **Review** \> **Restricted Users**. La procédure suivante décrit la navigation à l’aide du tableau de bord **Alertes** , qui est un bon moyen de voir différents types d’alertes qui ont pu être déclenchées.

1. Ouvrez le portail Microsoft 365 Defender et accédez à <https://security.microsoft.com> **Incidents & alertes Alertes**\>. Ou, pour accéder directement à la page **Alertes** , utilisez <https://security.microsoft.com/alerts>.

2. Dans la page **Alertes** , filtrez les résultats par période et la stratégie nommée **Utilisateur ne peut pas envoyer d’e-mail**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="Page Alertes du portail Microsoft 365 Defender filtrée pour les utilisateurs restreints" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. Si vous sélectionnez l’entrée en cliquant sur le nom, un **utilisateur limité à l’envoi de** la page de courrier s’ouvre avec des détails supplémentaires à consulter. En regard du bouton **Gérer l’alerte** , vous pouvez cliquer sur ![l’icône Autres options.](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’options** , puis sélectionnez **Afficher les détails de l’utilisateur restreint** pour accéder à la page **Utilisateurs restreints** , où vous pouvez [libérer l’utilisateur restreint](removing-user-from-restricted-users-portal-after-spam.md).

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="L’utilisateur ne peut pas envoyer de page d’e-mail" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>Afficher les détails des investigations automatisées

Lorsqu’une enquête automatisée a commencé, vous pouvez voir ses détails et les résultats dans le Centre de sécurité & conformité. Accédez à Investigations **de gestion** \> **des menaces**, puis sélectionnez une enquête pour afficher ses détails.

Pour plus d’informations, consultez [Afficher les détails d’une enquête](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>Gardez à l’esprit les points suivants

- **Restez informé de vos alertes**. Comme vous le savez, plus un compromis n’est pas détecté, plus le potentiel d’impact et de coût à grande échelle pour votre organisation, vos clients et vos partenaires est important. La détection précoce et la réponse en temps opportun sont essentielles pour atténuer les menaces, en particulier lorsque le compte d’un utilisateur est compromis.

- **L’automatisation aide, mais ne remplace pas, votre équipe des opérations de sécurité**. Les fonctionnalités d’investigation et de réponse automatisées peuvent détecter un utilisateur compromis dès le début, mais votre équipe des opérations de sécurité devra probablement s’engager et effectuer des investigations et des corrections. Vous avez besoin d’aide à ce sujet ? Consultez [Vérifier et approuver les actions](air-review-approve-pending-completed-actions.md).

- **Ne vous fiez pas à une alerte de connexion suspecte comme seul indicateur**. Lorsqu’un compte d’utilisateur est compromis, il peut déclencher ou non une alerte de connexion suspecte. Parfois, c’est la série d’activités qui se produit après la compromission d’un compte qui déclenche une alerte. Vous souhaitez en savoir plus sur les alertes ? Consultez les [stratégies d’alerte](../../compliance/alert-policies.md).

## <a name="next-steps"></a>Prochaines étapes

- [Passer en revue les autorisations requises pour utiliser les fonctionnalités AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Rechercher et examiner les e-mails malveillants dans Office 365](investigate-malicious-email-that-was-delivered.md)

- [En savoir plus sur AIR dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Visitez la feuille de route Microsoft 365 pour voir ce qui va bientôt se déployer](https://www.microsoft.com/microsoft-365/roadmap?filters=)
