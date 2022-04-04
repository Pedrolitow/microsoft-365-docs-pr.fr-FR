---
title: Configurer et gérer les fonctionnalités Spécialistes des menaces Microsoft d’Microsoft 365 Defender
description: Abonnez-vous à Microsoft Threats Experts Microsoft 365 Defender pour configurer, gérer et utiliser ces derniers dans vos opérations de sécurité quotidiennes et votre travail d’administration de la sécurité.
keywords: Spécialistes des menaces Microsoft, service de recherche de menace gérée, MTE, service de recherche géré Microsoft
search.product: Windows 10
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-maave
author: martyav
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.openlocfilehash: 8a8de691ff08b50b56c34ed9e779cc97d48c5fcd
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755843"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities-through-microsoft-365-defender"></a>Configurer et gérer les fonctionnalités Spécialistes des menaces Microsoft d’Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

## <a name="before-you-begin"></a>Avant de commencer

> [!IMPORTANT]
> Avant de vous inscrire, veillez à discuter des conditions d’éligibilité pour le service de recherche de menaces gérées Spécialistes des menaces Microsoft – Targeted Attack Notifications avec votre fournisseur de services techniques Microsoft et votre équipe de compte.

Pour recevoir des notifications d’attaque ciblée, vous devez avoir déployé Microsoft 365 Defender avec des appareils inscrits. Ensuite, envoyez une application via le portail M365 Spécialistes des menaces Microsoft - Notifications d’attaque ciblée.

Contactez votre équipe de compte ou votre représentant Microsoft pour vous abonner à Spécialistes des menaces Microsoft - Experts à la demande. Les experts à la demande vous permet de consulter nos experts en matière de menaces sur la façon de protéger votre organisation contre les détections et les adversaires pertinents.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>Appliquer pour Spécialistes des menaces Microsoft - Service de notifications d’attaques ciblées

Si vous avez déjà Microsoft Defender pour les points de terminaison et les Microsoft 365 Defender, vous pouvez demander des notifications d’Spécialistes des menaces Microsoft – Attaques ciblées via leur portail Microsoft 365 Defender web.  Les notifications d’attaques ciblées vous offrent un aperçu et une analyse spéciaux pour vous aider à identifier les menaces les plus critiques pour votre organisation, afin que vous y répondiez rapidement.

1. Dans le volet de navigation, go to **Paramètres > Endpoints > General > Advanced features > Spécialistes des menaces Microsoft - Targeted Attack Notifications**.

2. Sélectionnez **Appliquer**.

    :::image type="content" source="../../media/mte/mte-collaboratewithmte.png" alt-text="Page Spécialistes des menaces Microsoft paramètres de l’Microsoft 365 Defender web" lightbox="../../media/mte/mte-collaboratewithmte.png":::

3. Entrez votre nom et votre adresse e-mail afin que Microsoft puisse vous contacter à propos de votre application.

    :::image type="content" source="../../media/mte/mte-apply.png" alt-text="Page Spécialistes des menaces Microsoft’application dans le portail Microsoft 365 Defender web" lightbox="../../media/mte/mte-apply.png":::
  
4. Lisez [la déclaration de](https://privacy.microsoft.com/en-us/privacystatement) confidentialité, puis **sélectionnez Envoyer** lorsque vous avez terminé. Vous recevrez un e-mail de bienvenue une fois votre application approuvée.

    :::image type="content" source="../../media/mte/mte-applicationconfirmation.png" alt-text="Confirmation Spécialistes des menaces Microsoft application dans le portail Microsoft 365 Defender web" lightbox="../../media/mte/mte-applicationconfirmation.png":::

5. Une fois que vous avez reçu votre e-mail de bienvenue, vous commencez automatiquement à recevoir des notifications d’attaque ciblée.

6. Vous pouvez vérifier votre état en visitant Paramètres > points de terminaison > **général > fonctionnalités avancées**. Une fois approuvé, le **Spécialistes des menaces Microsoft -** Bascule de notification d’attaque ciblée est visible **et activé.**

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>L’endroit où les notifications d’attaque ciblées s’Spécialistes des menaces Microsoft

Vous pouvez recevoir une notification d’attaque ciblée Spécialistes des menaces Microsoft via les supports suivants :

- Page Microsoft 365 Defender’incidents du portail **d’entreprise**
- Tableau de bord **Microsoft 365 Defender’alertes du** portail d’entreprise
- [API](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) d’alerte OData et [API REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [Table DeviceAlertEvents en](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) recherche avancée
- Votre boîte de réception, si vous choisissez d’envoyer des notifications d’attaque ciblées par courrier électronique. Voir [Créer une règle de notification par courrier électronique ci-dessous](#create-an-email-notification-rule) .

### <a name="create-an-email-notification-rule"></a>Créer une règle de notification par courrier électronique

Vous pouvez créer des règles pour envoyer des notifications par courrier électronique aux destinataires de la notification. Pour plus d’informations, voir  [Configurer les notifications](/windows/security/threat-protection/microsoft-defender-atp/configure-email-notifications) d’alerte pour créer, modifier, supprimer ou dépanner les notifications par courrier électronique.

## <a name="view-targeted-attack-notifications"></a>Afficher les notifications d’attaque ciblée

Vous commencerez à recevoir des notifications d’attaques ciblées Spécialistes des menaces Microsoft votre courrier électronique après avoir configuré votre système pour recevoir une notification par courrier électronique.

1. Sélectionnez le lien dans l’e-mail pour aller dans le contexte d’alerte correspondant dans le tableau de bord balisé avec des **experts en menaces**.

2. Dans la page **Alertes** , sélectionnez la même rubrique d’alerte que celle que vous avez reçue dans l’e-mail pour afficher d’autres détails.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>S’abonner à Spécialistes des menaces Microsoft - Experts à la demande

Si vous êtes déjà un client Microsoft Defender pour points de terminaison, vous pouvez contacter votre représentant Microsoft pour vous abonner à Spécialistes des menaces Microsoft - Experts à la demande.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>Consulter un expert microsoft en matière de menaces sur les activités de cybersécurité suspectes dans votre organisation

Vous pouvez contacter Spécialistes des menaces Microsoft à partir du portail Microsoft 365 Defender web. Les experts peuvent vous aider à comprendre les menaces complexes et les notifications d’attaque ciblée. Associez des experts pour obtenir plus d’informations sur les alertes et les incidents, ou des conseils sur la gestion des compromissions. Obtenir des informations sur le contexte d’intelligence des menaces décrit par votre tableau de bord du portail.

> [!NOTE]
>
> - Les demandes d’alerte liées aux données d’intelligence contre les menaces personnalisées de votre organisation ne sont actuellement pas pris en charge. Pour plus d’informations, consultez vos opérations de sécurité ou votre équipe de réponse aux incidents.
> - Vous devez avoir l’autorisation Gérer les **paramètres** de sécurité dans le centre de sécurité dans le portail Microsoft 365 Defender pour soumettre une demande par le biais du formulaire **Consulter un expert** en menaces.

1. Accédez à la page du portail liée aux informations que vous souhaitez examiner : par **exemple, Périphérique****, Alerte** ou **Incident**. Assurez-vous que la page du portail liée à votre requête est en vue avant d’envoyer une demande d’enquête.

2. Dans le menu supérieur, sélectionnez **? Consultez un expert en menaces**.

    :::image type="content" source="../../media/mte/incidents-action-mte-highlighted.png" alt-text="Le Spécialistes des menaces Microsoft Experts à la demande dans le menu du portail Microsoft 365 Defender" lightbox="../../media/mte/incidents-action-mte-highlighted.png":::

    Un écran volant s’ouvre.

    L’en-tête indique si vous êtes sur un abonnement d’essai ou un abonnement complet Spécialistes des menaces Microsoft - Experts à la demande.

    :::image type="content" source="../../media/mte/mte-trial.png" alt-text="Écran d Spécialistes des menaces Microsoft d’abonnement à la version d’essai des experts à la demande dans le portail Microsoft 365 Defender client" lightbox="../../media/mte/mte-trial.png":::

    Le **champ De la rubrique** Investigation est déjà rempli avec le lien vers la page pertinente pour votre demande.

3. Dans le champ suivant, fournissez suffisamment d’informations pour donner au Spécialistes des menaces Microsoft suffisamment de contexte pour démarrer l’examen.

4. Entrez l’adresse de messagerie que vous souhaitez utiliser pour correspondre à Spécialistes des menaces Microsoft.

> [!NOTE]
> Si vous souhaitez suivre l’état de vos cas d’experts à la demande via le Microsoft Services Hub, faites-en le suivi.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du Microsoft Services Hub.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics"></a>Exemples de rubriques d’examen

### <a name="alert-information"></a>Informations sur les alertes

- Nous avons vu un nouveau type d’alerte pour un binaire « living-off-the-land ». Nous pouvons fournir l’ID d’alerte. Pouvez-vous nous en dire plus sur cette alerte et sur la façon dont nous pouvons l’examiner plus en détail ?
- Nous avons observé deux attaques similaires, qui tentent d’exécuter des scripts PowerShell malveillants mais génèrent des alertes différentes. L’une est « Ligne de commande PowerShell suspecte » et l’autre est « Un fichier malveillant a été détecté en fonction de l’indication fournie par O365 ». Quelle est la différence ?
- Nous avons reçu une alerte impaire aujourd’hui concernant un nombre anormal d’échec de connexion à partir de l’appareil d’un utilisateur à profil élevé. Nous ne pouvons trouver aucune autre preuve de ces tentatives. Comment pouvez Microsoft 365 Defender voir ces tentatives ? Quel type de connexions sont surveillées ?
- Pouvez-vous donner plus de contexte ou d’informations sur l’alerte « Un comportement suspect a été observé par un utilitaire système » ?
- J’ai observé une alerte intitulée « Création d’une règle de redirection/de redirection ». Je pense que l’activité est anodin. Pouvez-vous me dire pourquoi j’ai reçu une alerte ?

### <a name="possible-machine-compromise"></a>Compromission possible de l’ordinateur

- Pouvez-vous expliquer pourquoi nous pouvons voir un message ou une alerte « Processus inconnu observé » sur de nombreux appareils de notre organisation ? Nous vous remercions de toute entrée pour clarifier si ce message ou cette alerte est lié à une activité malveillante.
- Pouvez-vous valider une compromission possible sur le système suivant, à partir de la semaine dernière ? Il se comporte de la même manière qu’une détection précédente de programmes malveillants sur le même système il y a six mois.

### <a name="threat-intelligence-details"></a>Détails de l’intelligence des menaces

- Nous avons détecté un e-mail de hameçonnage qui a remis un document Word malveillant à un utilisateur. Le document a provoqué une série d’événements suspects, qui ont déclenché plusieurs alertes pour une famille de programmes malveillants particulière. Avez-vous des informations sur ce programme malveillant ? Si oui, pouvez-vous nous envoyer un lien ?
- Nous avons récemment vu un billet de blog sur une menace ciblant notre secteur d’activité. Pouvez-vous nous aider à comprendre quelle protection Microsoft 365 Defender contre cet acteur des menaces ?
- Nous avons récemment observé une campagne de hameçonnage menée contre notre organisation. Pouvez-vous nous indiquer si cela a été ciblé spécifiquement à notre entreprise ou secteur vertical ?

### <a name="microsoft-threat-experts-alert-communications"></a>communications Spécialistes des menaces Microsoft’alertes de l’Spécialistes des menaces Microsoft

- Votre équipe de réponse aux incidents peut-elle nous aider à résoudre la notification d’attaque ciblée que nous avons reçu ?
- Nous avons reçu cette notification d’attaque ciblée de Spécialistes des menaces Microsoft. Nous n’avons pas notre propre équipe de réponse aux incidents. Que pouvons-nous faire maintenant et comment contenir l’incident ?
- Nous avons reçu une notification d’attaque ciblée de Spécialistes des menaces Microsoft. Quelles données pouvez-vous nous fournir que nous pouvons transmettre à notre équipe de réponse aux incidents ?

> [!NOTE]
> Spécialistes des menaces Microsoft est un service de recherche de menace gérée et non un service de réponse aux incidents. Toutefois, vous pouvez faire appel à votre propre équipe de réponse aux incidents pour résoudre les problèmes nécessitant une réponse aux incidents. Si vous ne possédez pas votre propre équipe de réponse aux incidents et que vous souhaitez obtenir de l’aide de Microsoft, vous pouvez vous engager avec l’équipe de réponse aux incidents de cybersécurité CSS (CIRT). Ils peuvent ouvrir un ticket pour vous aider à répondre à vos questions.

## <a name="scenario"></a>Scénario

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>Recevoir un rapport d’avancement sur votre demande de recherche gérée

La réponse de Spécialistes des menaces Microsoft varie en fonction de votre demande. Vous recevrez généralement l’une des réponses suivantes :

- Plus d’informations sont nécessaires pour poursuivre l’enquête
- Un fichier ou plusieurs exemples de fichiers sont nécessaires pour déterminer le contexte technique
- L’examen nécessite plus de temps
- Les informations initiales étaient suffisantes pour conclure l’enquête

Si un expert demande plus d’informations ou d’exemples de fichiers, il est essentiel de répondre rapidement pour que l’enquête continue de se déplacer.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des spécialistes des menaces Microsoft](microsoft-threat-experts.md)
