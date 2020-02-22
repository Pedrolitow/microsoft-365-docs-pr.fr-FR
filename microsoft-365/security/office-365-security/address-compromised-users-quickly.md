---
title: Adresser des comptes d’utilisateurs compromis avec une enquête et une réponse automatisées dans Office 365 protection avancée contre les menaces
keywords: AIR, autoIR, ATP, automatisation, analyse, réponse, correction, menaces, avancé, menace, protection, compromis
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.date: 02/20/2020
description: Découvrez comment accélérer le processus de détection et d’adressage des comptes d’utilisateurs compromis avec des fonctionnalités d’analyse et de réponse automatisées dans Office 365 Advanced Threat Protection Plan 2.
ms.openlocfilehash: 7dfa1db02e777e3fdb546ebf948ebc297f1caad5
ms.sourcegitcommit: 8876c216954b94adce9cdf493c49bd5a10190a3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42228562"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>Adresser des comptes d’utilisateurs compromis avec une enquête et une réponse automatisées

[Office 365 Advanced Threat Protection Plan 2](office-365-atp.md#office-365-atp-plan-1-and-plan-2) inclut de puissantes fonctionnalités d’analyse [et de réponse automatisées](office-365-air.md) (air). De telles fonctionnalités peuvent permettre à l’équipe de vos opérations de sécurité de gagner beaucoup de temps et d’efforts sur les menaces. Microsoft continue d’améliorer les fonctionnalités de sécurité. Récemment, les fonctionnalités AIR ont été améliorées pour inclure un manuel de sécurité de l’utilisateur compromis (actuellement en version d’évaluation). Lisez cet article pour en savoir plus sur le manifeste de sécurité de l’utilisateur compromis. Pour plus d’informations, reportez-vous au billet de blog [accélérer le temps nécessaire pour détecter et répondre à la compromission d’un utilisateur et limiter la portée de violation avec Office 365 ATP](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) .

![Enquête automatisée pour un utilisateur compromis](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

Les manifestes de sécurité de l’utilisateur compromis permettent à l’équipe de sécurité de votre organisation de :

- Accélérer la détection des comptes d’utilisateurs compromis ;

- Limiter l’étendue d’une violation lorsqu’un compte est compromis ; les 

- Répondez plus efficacement aux utilisateurs compromis.

## <a name="compromised-user-alerts"></a>Alertes utilisateur compromises

Lorsqu’un compte d’utilisateur est compromis, des comportements atypiques ou anormaux se produisent. Par exemple, les messages de hameçonnage et de courrier indésirable peuvent être envoyés en interne à partir d’un compte d’utilisateur approuvé. Office 365 Advanced Threat Protection peut détecter de telles anomalies dans les modèles de courrier électronique et l’activité de collaboration dans Office 365. Lorsque cela se produit, les alertes sont déclenchées et le processus de minimisation des menaces commence.

Par exemple, voici une alerte qui a été déclenchée en raison d’un envoi de courrier électronique suspect :

![Alerte déclenchée en raison d’un envoi suspect de courrier électronique](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

Et voici un exemple d’alerte déclenchée lorsqu’une limite d’envoi a été atteinte pour un utilisateur :

![Alerte déclenchée par la limite d’envoi atteinte](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>Examiner et répondre à un utilisateur compromis

Lorsqu’un compte d’utilisateur est compromis, des alertes sont déclenchées. Dans certains cas, ce compte d’utilisateur est bloqué et ne peut pas envoyer d’autres messages électroniques tant que le problème n’est pas résolu par l’équipe des opérations de sécurité de votre organisation. Dans les autres cas, une enquête automatisée commence, ce qui peut entraîner des actions recommandées que votre équipe de sécurité doit prendre.

- [Afficher et examiner les utilisateurs avec accès restreint](#view-and-investigate-restricted-users)

- [Afficher les détails des enquêtes automatisées](#view-details-about-automated-investigations)

> [!IMPORTANT]
> Vous devez disposer des autorisations appropriées pour effectuer les tâches suivantes. Consultez la rubrique [Required Permissions to use air Capabilities](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>Afficher et examiner les utilisateurs avec accès restreint

Vous disposez de plusieurs options pour accéder à une liste d’utilisateurs restreints. Par exemple, dans le centre de sécurité & conformité Office 365, vous pouvez accéder à la **gestion** > des menaces**examiner** > **les utilisateurs restreints**. La procédure suivante décrit la navigation à l’aide du tableau de bord **alertes** , qui permet de visualiser les différents types d’alertes qui ont pu être déclenchés.

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous.

2. Dans le volet de navigation, choisissez**tableau de bord** **alertes** > .

3. Dans le widget **autres alertes** , choisissez **utilisateurs restreints**.<br/>
   ![Autre widget alertes](/microsoft-365/media/office365atp-otheralertswidget.jpg)<br/>
   La liste des utilisateurs avec accès restreint s’ouvre.<br/>![Utilisateurs restreints dans Office 365](/microsoft-365/media/office365atp-restrictedusers.jpg) 

4. Sélectionnez un compte d’utilisateur dans la liste pour afficher les détails et effectuer une action, par exemple, [libérer l’utilisateur restreint](removing-user-from-restricted-users-portal-after-spam.md). 

### <a name="view-details-about-automated-investigations"></a>Afficher les détails des enquêtes automatisées

Lorsqu’une enquête automatisée a commencé, vous pouvez consulter ses détails et résultats dans le centre de conformité Office 365 Security &. Accédez aux **** > **enquêtes**de gestion des menaces, puis sélectionnez une enquête pour en afficher les détails.

Pour en savoir plus, consultez la rubrique [afficher les détails d’une enquête](air-view-investigation-results.md#view-details-of-an-investigation).

## <a name="keep-the-following-points-in-mind"></a>Gardez les points suivants à l’esprit

- **Restez au fait des alertes**. Comme vous le sachiez, plus un compromis est long, plus le risque d’impact et de coût étendu pour votre organisation, vos clients et vos partenaires est élevé. La détection précoce et la réponse opportune sont essentielles pour atténuer les menaces, et notamment lorsque le compte d’un utilisateur est compromis. 

- **L’automatisation aide, mais ne remplace pas, votre équipe de sécurité des opérations**. Les fonctionnalités d’analyse et de réponse automatisées peuvent détecter rapidement un utilisateur compromis, mais votre équipe des opérations de sécurité devra probablement s’engager et effectuer des recherches et des corrections. Vous avez besoin d’aide ? Voir [examiner et approuver des actions](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air#review-and-approve-actions).

- **Ne reposez pas sur une alerte de connexion suspecte comme seul indicateur**. Lorsqu’un compte d’utilisateur est compromis, il se peut qu’il déclenche ou non une alerte de connexion suspecte. Parfois, il s’agit de la série d’activités qui se produisent après la compromission d’un compte qui déclenche une alerte. Vous souhaitez en savoir plus sur les alertes ? Consultez la rubrique [Alert Policies](https://docs.microsoft.com/microsoft-365/compliance/alert-policies).

## <a name="next-steps"></a>Étapes suivantes

- [Vérifier les autorisations requises pour utiliser les fonctionnalités AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [Rechercher et identifier des courriers électroniques malveillants dans Office 365](investigate-malicious-email-that-was-delivered.md)

- [En savoir plus sur AIR dans Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Consultez la feuille de route Microsoft 365 pour découvrir les éléments bientôt disponibles et à déployer](https://www.microsoft.com/microsoft-365/roadmap?filters=)

