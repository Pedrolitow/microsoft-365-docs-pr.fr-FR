---
title: Configurer et gérer les fonctionnalités de Spécialistes des menaces Microsoft via Microsoft 365 Defender
description: Abonnez-vous à Microsoft Threats Experts via Microsoft 365 Defender pour le configurer, le gérer et l’utiliser dans vos tâches quotidiennes d’administration de sécurité et d’opérations de sécurité.
keywords: Spécialistes des menaces Microsoft, service de chasse aux menaces managée, MTE, service de chasse géré par Microsoft
search.product: Windows 10
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- m365-security
- tier1
ms.openlocfilehash: 7bd977ced10aa2c6823ffc3d766ac552c295e062
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68048965"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Configurer et gérer les fonctionnalités de Spécialistes des menaces Microsoft via Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer

> [!IMPORTANT]
> Avant de présenter votre demande, veillez à discuter des conditions d’éligibilité pour le service de repérage des menaces gérées endpoint Attack Notifications avec votre fournisseur de services techniques Microsoft et votre équipe de compte.

Pour recevoir des notifications d’attaque de point de terminaison, vous devez avoir Microsoft 365 Defender déployées avec des appareils inscrits. Ensuite, envoyez une application via le portail M365 pour les notifications d’attaque de point de terminaison.

Contactez votre équipe de compte ou votre représentant Microsoft pour vous abonner à Spécialistes des menaces Microsoft - Experts à la demande. Experts à la demande vous permet de consulter nos experts en menaces sur la façon de protéger votre organisation contre les détections et les adversaires pertinents.

## <a name="apply-for-endpoint-attack-notifications-service"></a>Appliquer pour le service Endpoint Attack Notifications

Si vous avez déjà Microsoft Defender pour point de terminaison et Microsoft 365 Defender, vous pouvez demander des notifications d’attaque de point de terminaison via votre portail Microsoft 365 Defender.  Les notifications d’attaque de point de terminaison vous offrent des insights et une analyse spéciaux pour vous aider à identifier les menaces les plus critiques pour votre organisation, afin de pouvoir y répondre rapidement.

1. Dans le volet de navigation, accédez à **Paramètres > Points de terminaison > Fonctionnalités générales > avancées > notifications d’attaque de point de terminaison**.

2. Sélectionnez **Appliquer**.

3. Entrez votre adresse e-mail afin que Microsoft puisse vous contacter à propos de votre application.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Page d’application Spécialistes des menaces Microsoft dans le portail Microsoft 365 Defender" lightbox="../../media/mte/mte-apply.png":::
  
4. Lisez la [déclaration de confidentialité](https://privacy.microsoft.com/en-us/privacystatement), puis **sélectionnez Envoyer** lorsque vous avez terminé. Vous recevrez un e-mail de bienvenue une fois votre application approuvée.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Confirmation de l’application Spécialistes des menaces Microsoft dans le portail Microsoft 365 Defender" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Une fois que vous avez reçu votre e-mail de bienvenue, vous commencerez automatiquement à recevoir des notifications d’attaque de point de terminaison.

6. Vous pouvez vérifier votre état en consultant **Paramètres > points de terminaison > fonctionnalités générales > avancées**. Une fois approuvé, le bouton bascule **Notification d’attaque** de point de terminaison est visible **et activé.**

## <a name="where-youll-see-the-endpoint-attack-notifications-from-microsoft-threat-experts"></a>Où vous verrez les notifications d’attaque de point de terminaison à partir de Spécialistes des menaces Microsoft

Vous pouvez recevoir des notifications d’attaque de point de terminaison de Spécialistes des menaces Microsoft via les supports suivants :

- Page **Incidents** du portail Microsoft 365 Defender
- Tableau de bord **Alertes** du portail Microsoft 365 Defender
- [API](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) d’alerte OData et [API REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Table DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) dans la chasse avancée
- Votre boîte de réception, si vous choisissez d’envoyer des notifications d’attaque de point de terminaison par e-mail. Voir [Créer une règle de notification par e-mail](#create-an-email-notification-rule) ci-dessous.

### <a name="create-an-email-notification-rule"></a>Créer une règle de notification par e-mail

Vous pouvez créer des règles pour envoyer des notifications par e-mail aux destinataires de notification. Pour plus d’informations, consultez  [Configurer les notifications d’alerte](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) pour créer, modifier, supprimer ou résoudre les problèmes de notification par e-mail.

## <a name="view-endpoint-attack-notifications"></a>Afficher les notifications d’attaque de point de terminaison

Vous commencerez à recevoir des notifications d’attaque de point de terminaison à partir de Spécialistes des menaces Microsoft dans votre e-mail après avoir configuré votre système pour recevoir une notification par e-mail.

1. Sélectionnez le lien dans l’e-mail pour accéder au contexte d’alerte correspondant dans le tableau de bord balisé avec **Defender Experts**.

2. Dans la page **Alertes** , sélectionnez la même rubrique d’alerte que celle que vous avez reçue dans l’e-mail, pour afficher plus de détails.

### <a name="filter-to-view-just-the-endpoint-attack-notifications"></a>Filtrer pour afficher uniquement les notifications d’attaque de point de terminaison

Vous pouvez filtrer vos incidents et alertes si vous souhaitez uniquement voir les notifications Defender Experts parmi les nombreuses alertes. Pour ce faire, procédez comme suit :

1. Dans le menu de navigation, accédez à **Incidents & alertes Incidents** >  > sélectionnez l’icône ![](../../media/mte/defenderexperts/filter.png) Filtrer.
2. Faites défiler jusqu’au champ **Balises** > activez la case à cocher **Experts Defender** .
3. Sélectionnez **Appliquer**.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>S’abonner à Spécialistes des menaces Microsoft - Experts à la demande
> [!NOTE]
> Experts à la demande n’est pas un service de réponse aux incidents de sécurité. Il vise à mieux comprendre les menaces complexes qui affectent votre organisation. Collaborez avec votre propre équipe de réponse aux incidents de sécurité pour résoudre les problèmes urgents de réponse aux incidents de sécurité. Si vous n’avez pas votre propre équipe de réponse aux incidents de sécurité et que vous souhaitez obtenir l’aide de Microsoft, créez une demande de support dans le [Hub De services Premier](/services-hub/).

Si vous êtes déjà un client Microsoft Defender pour point de terminaison, vous pouvez contacter votre représentant Microsoft pour vous abonner à Spécialistes des menaces Microsoft - Experts à la demande.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Consulter un expert en menaces Microsoft sur les activités suspectes de cybersécurité au sein de votre organisation

Vous pouvez contacter Spécialistes des menaces Microsoft à partir du portail Microsoft 365 Defender. Les experts peuvent vous aider à comprendre les menaces complexes et les notifications d’attaque de point de terminaison. Collaborez avec des experts pour plus d’informations sur les alertes et les incidents, ou pour obtenir des conseils sur la gestion des compromissions. Obtenez des insights sur le contexte de renseignement sur les menaces décrit par le tableau de bord de votre portail.

> [!NOTE]
>
> - Les demandes d’alerte liées aux données personnalisées de renseignement sur les menaces de votre organisation ne sont actuellement pas prises en charge. Pour plus d’informations, consultez votre équipe chargée des opérations de sécurité ou de la réponse aux incidents.
> - Vous devez disposer de l’autorisation **Gérer les paramètres de sécurité dans le centre de sécurité** dans le portail Microsoft 365 Defender pour soumettre une demande par le biais du formulaire **Ask Defender Experts**.

1. Accédez à la page du portail liée aux informations que vous souhaitez examiner : par exemple, **Appareil**, **Alerte** ou **Incident**. Assurez-vous que la page du portail relative à votre demande est affichée avant d’envoyer une demande d’enquête.

2. Dans le menu supérieur, sélectionnez **? Demandez à Defender Experts**. Un écran volant s’ouvre. L’en-tête indique si vous utilisez un abonnement d’essai ou un Spécialistes des menaces Microsoft complet - Abonnement Experts à la demande. Le champ **De la rubrique Investigation** est déjà rempli avec le lien vers la page appropriée pour votre demande.

3. Dans le champ suivant, fournissez suffisamment d’informations pour donner au Spécialistes des menaces Microsoft contexte suffisant pour démarrer l’enquête.

4. Entrez l’adresse e-mail que vous souhaitez utiliser pour correspondre à Spécialistes des menaces Microsoft.

> [!NOTE]
> Si vous souhaitez suivre l’état de vos cas d’experts à la demande via Microsoft Services Hub, contactez votre responsable de compte technique.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Exemples de rubriques d’investigation

### <a name="alert-information"></a>Informations sur les alertes

- Nous avons vu un nouveau type d’alerte pour un binaire vivant hors du pays. Nous pouvons fournir l’ID d’alerte. Pouvez-vous nous en dire plus sur cette alerte et sur la façon dont nous pouvons l’examiner plus en détail ?
- Nous avons observé deux attaques similaires, qui tentent toutes les deux d’exécuter des scripts PowerShell malveillants, mais génèrent des alertes différentes. L’une est « Ligne de commande PowerShell suspecte » et l’autre est « Un fichier malveillant a été détecté en fonction de l’indication fournie par O365 ». Quelle est la différence ?
- Nous avons reçu aujourd’hui une alerte impaire concernant un nombre anormal de connexions ayant échoué à partir de l’appareil d’un utilisateur à profil élevé. Nous ne trouvons aucune preuve supplémentaire de ces tentatives. Comment Microsoft 365 Defender voir ces tentatives ? Quel type de connexions sont surveillés ?
- Pouvez-vous donner plus de contexte ou d’informations sur l’alerte « Comportement suspect par un utilitaire système observé » ?
- J’ai observé une alerte intitulée « Création d’une règle de transfert/redirection ». Je crois que l’activité est bénigne. Pouvez-vous me dire pourquoi j’ai reçu une alerte ?

### <a name="possible-device-compromise"></a>Compromission possible de l’appareil

- Pouvez-vous expliquer pourquoi nous voyons un message ou une alerte pour « Processus inconnu observé » sur de nombreux appareils de notre organisation ? Nous apprécions toute entrée pour préciser si ce message ou cette alerte est lié à une activité malveillante.
- Pouvez-vous vous aider à valider un compromis possible sur le système suivant, datant de la semaine dernière ? Il se comporte de la même façon qu’une détection de programmes malveillants précédente sur le même système il y a six mois.

### <a name="threat-intelligence-details"></a>Détails du renseignement sur les menaces

- Nous avons détecté un e-mail de hameçonnage qui a remis un document Word malveillant à un utilisateur. Le document a provoqué une série d’événements suspects, qui ont déclenché plusieurs alertes pour une famille de programmes malveillants particulier. Avez-vous des informations sur ce programme malveillant ? Si oui, pouvez-vous nous envoyer un lien ?
- Nous avons récemment vu un billet de blog sur une menace qui cible notre industrie. Pouvez-vous nous aider à comprendre quelle protection Microsoft 365 Defender fournit contre cet acteur de menace ?
- Nous avons récemment observé une campagne de hameçonnage menée contre notre organisation. Pouvez-vous nous dire s’il s’agissait spécifiquement de notre entreprise ou verticalement?

### <a name="microsoft-threat-experts-alert-communications"></a>communications d’alerte de Spécialistes des menaces Microsoft

- Votre équipe de réponse aux incidents peut-elle nous aider à traiter la notification d’attaque ciblée que nous avons obtenue ?
- Nous avons reçu des notifications d’attaque de point de terminaison de Spécialistes des menaces Microsoft. Nous n’avons pas notre propre équipe de réponse aux incidents. Que pouvons-nous faire maintenant et comment pouvons-nous contenir l’incident ?
- Nous avons reçu une notification d’attaque ciblée de Spécialistes des menaces Microsoft. Quelles données pouvez-vous nous fournir que nous pouvons transmettre à notre équipe de réponse aux incidents ?

> [!NOTE]
> Spécialistes des menaces Microsoft est un service de chasse aux menaces managé et non un service de réponse aux incidents. Toutefois, vous pouvez collaborer avec votre propre équipe de réponse aux incidents pour résoudre les problèmes qui nécessitent une réponse aux incidents. Si vous n’avez pas votre propre équipe de réponse aux incidents et que vous souhaitez obtenir l’aide de Microsoft, vous pouvez contacter l’équipe de réponse aux incidents de cybersécurité CSS (CIRT). Ils peuvent ouvrir un ticket pour vous aider à répondre à votre demande.

## <a name="scenario"></a>Scénario

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Recevoir un rapport d’avancement sur votre enquête de chasse managée

La réponse de Spécialistes des menaces Microsoft varie en fonction de votre demande. Vous recevrez généralement l’une des réponses suivantes :

- Plus d’informations sont nécessaires pour poursuivre l’enquête
- Un fichier ou plusieurs exemples de fichiers sont nécessaires pour déterminer le contexte technique
- L’enquête nécessite plus de temps
- Les informations initiales étaient suffisantes pour conclure l’enquête

Si un expert demande plus d’informations ou d’exemples de fichiers, il est essentiel de répondre rapidement pour que l’enquête continue.

## <a name="to-proactively-hunt-threats-across-endpoints-office-365-cloud-applications-and-identity-refer-to"></a>Pour chasser de manière proactive les menaces entre les points de terminaison, les Office 365, les applications cloud et l’identité, reportez-vous à : 

- [vue d’ensemble de Microsoft Defender Experts pour la chasse](defender-experts-for-hunting.md)
