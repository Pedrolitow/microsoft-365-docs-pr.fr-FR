---
title: Configurer et gérer les fonctionnalités de Spécialistes des menaces Microsoft
ms.reviewer: ''
description: Inscrivez-vous auprès de Microsoft Threats Experts pour le configurer, le gérer et l’utiliser dans vos tâches quotidiennes d’administration de la sécurité et d’opérations de sécurité.
keywords: Spécialistes des menaces Microsoft, service de chasse aux menaces managée, MTE, service de chasse géré par Microsoft
search.product: Windows 10
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: be03708d59616a46ec37e97fe0a48a3f43b7bfdd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68638629"
---
# <a name="configure-and-manage-microsoft-defender-experts-capabilities"></a>Configurer et gérer les fonctionnalités Microsoft Defender Experts

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>Avant de commencer

> [!NOTE]
> Discutez des conditions d’éligibilité avec votre fournisseur de services techniques Microsoft et votre équipe de compte avant de vous appliquer au service de repérage des menaces managées Endpoint Attack Notifications.

Assurez-vous que Defender pour point de terminaison est déployé dans votre environnement avec des appareils inscrits, et pas seulement sur une configuration de laboratoire.

Si vous êtes un client Defender pour point de terminaison, vous devez demander **des notifications d’attaque** de point de terminaison pour obtenir des insights et une analyse spéciaux afin d’identifier les menaces les plus critiques, afin de pouvoir y répondre rapidement. Contactez votre équipe de compte ou votre représentant Microsoft pour vous abonner à **Microsoft Defender Experts - Experts à la demande** afin de consulter nos experts en matière de menaces sur les détections et les adversaires pertinents.

## <a name="apply-for-endpoint-attack-notifications-service"></a>Appliquer pour le service Endpoint Attack Notifications

Si vous êtes déjà client Defender pour point de terminaison, vous pouvez appliquer via le portail Microsoft 365 Defender.

1. Dans le volet de navigation, accédez à **Paramètres > Fonctionnalités générales > avancées > notifications d’attaque de point de terminaison**.

2. Cliquez sur **Appliquer**.

   :::image type="content" source="images/mte-collaboratewithmte.png" alt-text="Paramètres Microsoft Defender Experts" lightbox="images/mte-collaboratewithmte.png":::

3. Entrez votre nom et votre adresse e-mail afin que Microsoft puisse vous revenir sur votre application.

   :::image type="content" source="images/mte-apply.png" alt-text="Champ Nom dans la page d’application Microsoft Defender Experts" lightbox="images/mte-apply.png":::

4. Lisez la [déclaration de confidentialité](https://privacy.microsoft.com/privacystatement), puis cliquez sur **Envoyer** lorsque vous avez terminé. Vous recevrez un e-mail de bienvenue une fois votre application approuvée.

   :::image type="content" source="images/mte-applicationconfirmation.png" alt-text="Message de confirmation de l’application Microsoft Defender Experts" lightbox="images/mte-applicationconfirmation.png":::

Une fois accepté, vous recevrez un e-mail de bienvenue et vous **verrez** la modification du bouton Appliquer à un bouton bascule « activé ». Si vous souhaitez vous retirer du service Endpoint Attack Notifications, faites glisser le bouton bascule « désactivé », puis cliquez sur **Enregistrer les préférences** en bas de la page.

## <a name="where-youll-see-the-endpoint-attack-notifications-from-microsoft-defender-experts"></a>Où vous verrez les notifications d’attaque de point de terminaison de Microsoft Defender Experts

Vous pouvez recevoir une notification d’attaque ciblée de Microsoft Defender Experts via le support suivant :

- Page **Incidents** du portail Defender pour point de terminaison
- Tableau de bord **Alertes** du portail Defender pour point de terminaison
- [API](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) d’alerte OData et [API REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Table DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) dans la chasse avancée
- Votre e-mail, si vous choisissez de le configurer

Pour recevoir des notifications d’attaque de point de terminaison par e-mail, créez une règle de notification par e-mail.

### <a name="create-an-email-notification-rule"></a>Créer une règle de notification par e-mail

Vous pouvez créer des règles pour envoyer des notifications par e-mail aux destinataires de notification. Pour plus d’informations, consultez  [Configurer les notifications d’alerte](configure-email-notifications.md) pour créer, modifier, supprimer ou résoudre les problèmes de notification par e-mail.

## <a name="view-the-endpoint-attack-notifications"></a>Afficher les notifications d’attaque de point de terminaison

Vous commencerez à recevoir des notifications d’attaque de point de terminaison de Microsoft Defender Experts dans votre e-mail après avoir configuré votre système pour recevoir une notification par e-mail.

1. Cliquez sur le lien dans l’e-mail pour accéder au contexte d’alerte correspondant dans le tableau de bord balisé avec **les experts en menaces**.

2. Dans le tableau de bord, sélectionnez la même rubrique d’alerte que celle que vous avez reçue de l’e-mail pour afficher les détails.

### <a name="filter-to-view-just-the-endpoint-attack-notifications"></a>Filtrer pour afficher uniquement les notifications d’attaque de point de terminaison

Vous pouvez filtrer vos incidents et alertes si vous souhaitez uniquement voir les notifications d’attaque de point de terminaison parmi les nombreuses alertes. Pour ce faire, procédez comme suit :

1. Dans le menu de navigation, accédez à **Incidents & alertes Alertes** > **d’incidents**/ > sélectionnez l’icône ![Filtrer pour afficher les notifications](../../media/mte/defenderexperts/filter.png) Defender Experts.
2. Faites défiler jusqu’au champ Balises > activez la case à cocher **Defender Experts** .
3. Sélectionnez **Appliquer**.

## <a name="subscribe-to-microsoft-defender-experts---experts-on-demand"></a>S’abonner à Microsoft Defender Experts - Experts à la demande

Il est disponible en tant que service d’abonnement. Si vous êtes déjà client Defender pour point de terminaison, vous pouvez contacter votre représentant Microsoft pour vous abonner à Microsoft Defender Experts - Experts à la demande.
> [!NOTE]
> Experts à la demande n’est pas un service de réponse aux incidents de sécurité. Il vise à mieux comprendre les menaces complexes qui affectent votre organisation. Collaborez avec votre propre équipe de réponse aux incidents de sécurité pour résoudre les problèmes urgents de réponse aux incidents de sécurité. Si vous n’avez pas votre propre équipe de réponse aux incidents de sécurité et que vous souhaitez obtenir l’aide de Microsoft, créez une demande de support dans le [Hub De services Premier](/services-hub/).

## <a name="ask-defender-experts-about-suspicious-cybersecurity-activities-in-your-organization"></a>Demandez aux experts Defender les activités suspectes de cybersécurité au sein de votre organisation

Vous pouvez collaborer avec Microsoft Defender experts qui peuvent être engagés directement à partir du portail Microsoft 365 Defender pour leur réponse. Les experts fournissent des insights pour mieux comprendre les menaces complexes, les notifications d’attaque ciblées que vous recevez, ou si vous avez besoin d’informations supplémentaires sur les alertes, un appareil potentiellement compromis ou un contexte de renseignement sur les menaces que vous voyez sur le tableau de bord de votre portail.

> [!NOTE]
>
> - Les demandes d’alerte liées aux données personnalisées de renseignement sur les menaces de votre organisation ne sont actuellement pas prises en charge. Pour plus d’informations, consultez votre équipe chargée des opérations de sécurité ou de la réponse aux incidents.
> - Vous devez disposer de l’autorisation **Gérer les paramètres de sécurité** dans le portail Microsoft 365 Defender pour pouvoir soumettre l’enquête **Ask Defender Experts**.

1. Accédez à la page du portail avec les informations pertinentes que vous souhaitez examiner, par exemple, la page **Incident** . Vérifiez que la page de l’alerte ou de l’appareil concerné est affichée avant d’envoyer une demande d’enquête.

2. Dans le menu supérieur droit, cliquez sur le bouton **?** . Ensuite, **sélectionnez Ask Defender Experts**

![Page d’abonnement à la version d’évaluation de Microsoft Ask Defender Experts](../../media/mte/flyout-screen-trial-subscription.png)

Un écran volant s’ouvre. L’écran suivant montre quand vous êtes sur un abonnement d’essai. L’écran suivant montre quand vous êtes sur un abonnement complet Microsoft Defender Experts - Experts à la demande.

Le champ **De la rubrique d’enquête** est prérempli avec le lien vers la page appropriée pour votre demande d’enquête. Par exemple, un lien vers la page d’incident, d’alerte ou de détails de l’appareil à laquelle vous vous êtes rendu lorsque vous avez effectué la demande.

3. Dans le champ suivant, fournissez suffisamment d’informations pour donner au Microsoft Defender Experts suffisamment de contexte pour démarrer l’enquête.

4. Entrez l’adresse e-mail que vous souhaitez utiliser pour correspondre à Microsoft Defender Experts.

> [!NOTE]
> Si vous souhaitez suivre l’état de vos cas d’experts à la demande par le biais de Microsoft Services Hub, contactez votre gestionnaire de compte customer success.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-defender-experts---experts-on-demand"></a>Exemples de rubriques d’investigation que vous pouvez consulter avec Microsoft Defender Experts - Experts à la demande

### <a name="alert-information"></a>Informations sur les alertes

- Nous voyons un nouveau type d’alerte pour un binaire vivant hors du pays : [AlertID]. Pouvez-vous nous en dire plus sur cette alerte et sur la façon dont nous pouvons examiner plus en détail ?
- Nous avons observé deux attaques similaires, qui tentent d’exécuter des scripts PowerShell malveillants, mais génèrent des alertes différentes. L’une est « Ligne de commande PowerShell suspecte » et l’autre est « Un fichier malveillant a été détecté en fonction de l’indication fournie par O365 ». Quelle est la différence ?
- Je reçois aujourd’hui une alerte impaire pour le nombre anormal de connexions ayant échoué à partir de l’appareil d’un utilisateur à profil élevé. Je ne trouve pas d’autres preuves concernant ces tentatives de connexion. Comment Defender pour point de terminaison peut-il voir ces tentatives ? Quel type de connexions sont surveillées ?
- Pouvez-vous donner plus de contexte ou d’insights sur cette alerte : « Un comportement suspect par un utilitaire système a été observé ».

### <a name="possible-device-compromise"></a>Compromission possible de l’appareil

- Pouvez-vous nous aider à répondre à la raison pour laquelle nous voyons « Processus inconnu observé ? » Ce message ou cette alerte est fréquemment affiché sur de nombreux appareils. Nous apprécions toute entrée pour préciser si ce message ou cette alerte est lié à une activité malveillante.
- Pouvez-vous vous aider à valider une compromission possible sur le système suivant le [date] avec des comportements similaires à ceux de la détection de programmes malveillants [nom du programme malveillant] précédente sur le même système en [mois] ?

### <a name="threat-intelligence-details"></a>Détails du renseignement sur les menaces

- Nous avons détecté un e-mail de hameçonnage qui a remis un document Word malveillant à un utilisateur. Le document Word malveillant a provoqué une série d’événements suspects, qui ont déclenché plusieurs alertes endpoint Attack Notifications pour les programmes malveillants [nom du programme malveillant]. Avez-vous des informations sur ce programme malveillant ? Si oui, pouvez-vous m’envoyer un lien ?
- J’ai récemment vu une [référence de médias sociaux, par exemple, Twitter ou blog] post sur une menace qui cible mon industrie. Pouvez-vous m’aider à comprendre la protection fournie par Defender pour point de terminaison contre cet acteur de menace ?

### <a name="defender-experts-alert-communications"></a>Communications d’alerte des experts Defender

- Votre équipe de réponse aux incidents peut-elle nous aider à traiter les notifications d’attaque de point de terminaison que nous avons obtenues ?
- J’ai reçu ces notifications d’attaque de point de terminaison de Microsoft Defender Experts. Nous n’avons pas notre propre équipe de réponse aux incidents. Que pouvons-nous faire maintenant et comment pouvons-nous contenir l’incident ?
- J’ai reçu des notifications d’attaque de point de terminaison de Microsoft Defender Experts. Quelles données pouvez-vous nous fournir que nous pouvons transmettre à notre équipe de réponse aux incidents ?

  > [!NOTE]
  > Microsoft Defender Experts est un service de repérage de cybersécurité géré et non un service de réponse aux incidents. Toutefois, vous pouvez collaborer avec votre propre équipe de réponse aux incidents pour résoudre les problèmes qui nécessitent une réponse aux incidents. Si vous n’avez pas votre propre équipe de réponse aux incidents et que vous souhaitez obtenir l’aide de Microsoft, vous pouvez contacter l’équipe de réponse aux incidents de cybersécurité CSS (CIRT). Ils peuvent ouvrir un ticket pour vous aider à répondre à votre demande.

## <a name="scenario"></a>Scénario

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Recevoir un rapport d’avancement sur votre enquête de chasse managée

La réponse de Microsoft Defender Experts varie en fonction de votre demande. Ils vous envoient un rapport d’avancement sur votre demande **d’experts Ask Defender** dans un délai de deux jours pour communiquer l’état de l’enquête dans les catégories suivantes :

- Plus d’informations sont nécessaires pour poursuivre l’enquête
- Un fichier ou plusieurs exemples de fichiers sont nécessaires pour déterminer le contexte technique
- L’enquête nécessite plus de temps
- Les informations initiales étaient suffisantes pour conclure l’enquête

Il est essentiel d’intervenir rapidement pour que l’enquête continue.

#### <a name="to-proactively-hunt-threats-across-endpoints-office-365-cloud-applications-and-identity-refer-to"></a>Pour chasser de manière proactive les menaces entre les points de terminaison, les Office 365, les applications cloud et l’identité, reportez-vous à

- [Vue d’ensemble des experts Microsoft Defender dans Microsoft 365](../defender/defender-experts-for-hunting.md)
