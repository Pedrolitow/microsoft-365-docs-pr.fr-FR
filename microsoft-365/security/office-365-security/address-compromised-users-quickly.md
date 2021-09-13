---
title: Résoudre les comptes d’utilisateur compromis grâce à un examen et à une réponse automatisés
keywords: AIR, autoIR, Microsoft Defender pour point de terminaison, automatisé, examen, réponse, correction, menaces, avancé, menace, protection, compromis
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.date: 06/10/2021
description: Découvrez comment accélérer le processus de détection et de traitement des comptes d’utilisateur compromis à l’aide de fonctionnalités automatisées d’examen et de réponse dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4a90768038bde3126dd4ac3e5016f4d04aded9af
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177412"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Résoudre les comptes d’utilisateur compromis grâce à un examen et à une réponse automatisés

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


[Microsoft Defender pour Office 365 Plan 2 inclut](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) des fonctionnalités d’investigation [et de](office-365-air.md) réponse automatisées (AIR) puissantes. Ces fonctionnalités peuvent faire gagner beaucoup de temps et d’efforts à votre équipe en matière d’opérations de sécurité pour gérer les menaces. Microsoft continue d’améliorer les fonctionnalités de sécurité. Récemment, les fonctionnalités AIR ont été améliorées pour inclure un manuel de sécurité utilisateur compromis (actuellement en prévisualisation). Lisez cet article pour en savoir plus sur le manuel de sécurité des utilisateurs compromis. Pour plus d’informations, voir le billet de blog Accélérer le temps de détection et de réponse à la compromission de l’utilisateur et limiter l’étendue des violations avec [Microsoft Defender pour Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) plus d’informations.

![Examen automatisé pour un utilisateur compromis.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Le manuel de sécurité des utilisateurs compromis permet à l’équipe de sécurité de votre organisation de :

- Accélérer la détection des comptes d’utilisateur compromis ;
- Limiter l’étendue d’une violation lorsqu’un compte est compromis ; et
- Répondre plus efficacement aux utilisateurs compromis.

## <a name="compromised-user-alerts"></a>Alertes utilisateur compromises

Lorsqu’un compte d’utilisateur est compromis, des comportements inhabituels ou anormaux se produisent. Par exemple, les messages de hameçonnage et de courrier indésirable peuvent être envoyés en interne à partir d’un compte d’utilisateur approuvé. Defender for Office 365 détecter de telles anomalies dans les modèles de messagerie et l’activité de collaboration au sein Office 365. Lorsque cela se produit, les alertes sont déclenchées et le processus de prévention des menaces commence.

Par exemple, voici une alerte déclenchée en raison de l’envoi de messages électroniques suspects :

![Alerte déclenchée en raison d’un envoi de courrier suspect.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Voici un exemple d’alerte déclenchée lorsqu’une limite d’envoi a été atteinte pour un utilisateur :

![Alerte déclenchée par la limite d’envoi atteinte.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Examiner un utilisateur compromis et y répondre

Lorsqu’un compte d’utilisateur est compromis, des alertes sont déclenchées. Et dans certains cas, ce compte d’utilisateur est bloqué et empêché d’envoyer d’autres messages électroniques jusqu’à ce que le problème soit résolu par l’équipe des opérations de sécurité de votre organisation. Dans d’autres cas, une enquête automatisée commence, ce qui peut entraîner des actions recommandées que votre équipe de sécurité doit prendre.

- [Afficher et examiner les utilisateurs restreints](#view-and-investigate-restricted-users)

- [Afficher les détails sur les enquêtes automatisées](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Vous devez avoir les autorisations appropriées pour effectuer les tâches suivantes. Voir [Autorisations requises pour utiliser les fonctionnalités AIR.](office-365-air.md#required-permissions-to-use-air-capabilities)

### <a name="view-and-investigate-restricted-users"></a>Afficher et examiner les utilisateurs restreints

Vous avez plusieurs options pour naviguer vers une liste d’utilisateurs restreints. Par exemple, dans le portail Microsoft 365 Defender, vous pouvez aller à **Email & collaboration** \> **Review** \> **Restricted Users**. La procédure suivante décrit la navigation à l’aide du tableau de bord **Alertes,** qui est un bon moyen de voir différents types d’alertes qui ont pu être déclenchées.

1. Ouvrez le portail Microsoft 365 Defender ( ) et allez à <https://security.microsoft.com> **Incidents &** \> **alertes**. Ou, pour aller directement à la page **Alertes,** utilisez <https://security.microsoft.com/alerts> .

2. Dans la page **Alertes,** filtrez les résultats par période et la stratégie nommée Utilisateur ne peut pas envoyer **de courrier électronique.**

   ![La page Alertes du portail Microsoft 365 Defender filtré pour les utilisateurs restreints.](../../media/m365-sc-alerts-page-with-restricted-user.png)

3. Si vous sélectionnez l’entrée en cliquant sur le nom, une **page** utilisateur dont l’envoi est restreint s’ouvre avec des détails supplémentaires que vous pouvez consulter. En plus du bouton **Gérer l’alerte,** vous pouvez cliquer sur ![ l’icône Options supplémentaires.](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’options,** puis sélectionnez Afficher les détails des utilisateurs restreints pour aller à la **page** **Utilisateurs restreints,** où vous pouvez libérer [l’utilisateur restreint.](removing-user-from-restricted-users-portal-after-spam.md)

   ![L’utilisateur ne peut pas envoyer de courrier à partir du centre d’alertes.](../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png)

### <a name="view-details-about-automated-investigations"></a>Afficher les détails sur les enquêtes automatisées

Lorsqu’une enquête automatisée a commencé, vous pouvez voir ses détails et ses résultats dans le Centre de sécurité & conformité. Go to **Threat management** \> **Investigations,** and then select an investigation to view its details.

Pour en savoir plus, [consultez les détails d’une enquête.](air-view-investigation-results.md)

## <a name="keep-the-following-points-in-mind"></a>Gardez les points suivants à l’esprit

- **Restez au fait de vos alertes.** Comme vous le savez, plus une compromission est longue et plus le risque d’impact et de coût pour votre organisation, vos clients et vos partenaires est élevé. Une détection précoce et une réponse rapide sont essentielles pour atténuer les menaces, en particulier lorsque le compte d’un utilisateur est compromis.

- **Automation aide, mais ne remplace pas, votre équipe des opérations de sécurité.** Les fonctionnalités d’examen et de réponse automatisées peuvent détecter un utilisateur compromis dès le début, mais votre équipe en matière d’opérations de sécurité devra probablement s’impliquer et faire des recherches et des corrections. Vous avez besoin d’aide ? Consultez [et approuvez les actions.](air-review-approve-pending-completed-actions.md)

- **Ne comptez pas sur une alerte de connexion suspecte comme seul indicateur.** Lorsqu’un compte d’utilisateur est compromis, il peut ou non déclencher une alerte de connexion suspecte. Parfois, c’est la série d’activités qui se produisent après qu’un compte est compromis qui déclenche une alerte. Vous souhaitez en savoir plus sur les alertes ? Voir [stratégies d’alerte.](../../compliance/alert-policies.md)

## <a name="next-steps"></a>Étapes suivantes

- [Passer en revue les autorisations requises pour utiliser les fonctionnalités AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Rechercher et examiner les e-mails malveillants dans Office 365](investigate-malicious-email-that-was-delivered.md)

- [En savoir plus sur AIR dans Microsoft Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Consultez la feuille Microsoft 365 de l’Microsoft 365 pour voir ce qui sera bientôt disponible et sera disponible](https://www.microsoft.com/microsoft-365/roadmap?filters=)