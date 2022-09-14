---
title: Suivre les menaces de sécurité émergentes et y répondre avec l’affichage des campagnes dans Microsoft Defender pour Office 365
description: Procédure pas à pas des campagnes de menaces dans Microsoft Defender pour Office 365 pour montrer comment elles peuvent être utilisées pour enquêter sur une attaque par e-mail coordonnée contre votre organisation.
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
search.appverid: met150
ms.openlocfilehash: 79ff9f29b37dca665635a9728567c78d0b945435
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686276"
---
# <a name="track-and-respond-to-emerging-threats-with-campaigns-in-microsoft-defender-for-office-365"></a>Suivre et répondre aux menaces émergentes avec des campagnes dans Microsoft Defender pour Office 365

Les campagnes peuvent être utilisées pour suivre et répondre aux menaces émergentes, car les campagnes vous permettent d’examiner une attaque par e-mail coordonnée contre votre organisation. À mesure que de nouvelles menaces ciblent votre organisation, Microsoft Defender pour Office 365 détecte et met automatiquement en corrélation les messages malveillants. 

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 2 (inclus dans les plans E5).
- Autorisations suffisantes (rôle Lecteur sécurité).
- Cinq à dix minutes pour effectuer ces étapes.

## <a name="what-is-a-campaign-in-microsoft-defender-for-office-365"></a>Qu’est-ce qu’une campagne dans Microsoft Defender pour Office 365

Une campagne est une attaque par e-mail coordonné contre une ou plusieurs organisations. Email attaques qui volent des informations d’identification et des données d’entreprise sont un secteur important et lucratif. À mesure que les technologies permettant d’arrêter les attaques augmentent et se multiplient, les attaquants modifient leurs méthodes pour poursuivre leur réussite.

Microsoft tire parti de grandes quantités de données anti-hameçonnage, anti-courrier indésirable et anti-programme malveillant sur l’ensemble du service pour aider à identifier les campagnes. Nous analysons et classons les informations d’attaque en fonction de plusieurs facteurs, par exemple :

- **Source d’attaque** : adresses IP sources et domaines de messagerie de l’expéditeur.
- **Propriétés du message** : contenu, style et tonalité des messages.
- **Destinataires du message** : la façon dont les destinataires sont liés, par exemple, les domaines de destinataire, les fonctions de travail des destinataires (tels que les administrateurs et les cadres), les types d’entreprise (tels que les grands, les petits, les publics et les privés) et les secteurs d’activité.
- **Charge utile d’attaque** : liens malveillants, pièces jointes ou autres charges utiles dans les messages.

Une campagne peut être de courte durée ou peut s’étendre sur plusieurs jours, semaines ou mois avec des périodes actives et inactives. Une campagne peut être lancée auprès de votre organisation spécifique, ou votre organisation peut faire partie d’une campagne plus importante au sein *de plusieurs* entreprises.

> [!TIP]
> Pour en savoir plus sur les données disponibles dans une campagne, lisez [Vues de campagne dans Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/campaigns).

## <a name="watch-the-exploring-campaign-views-video"></a>Regarder la vidéo *Exploring campaign views*

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGBL8]

## <a name="investigating-a-suspicious-email-campaign-using-threat-reports"></a>Examen d’une campagne de messagerie suspecte à l’aide de rapports de menaces

Si une campagne a ciblé votre organisation et que vous souhaitez en savoir plus sur l’impact : 
1. Accédez à la [page de campagne](https://security.microsoft.com/campaigns).
1. Sélectionnez le nom de la campagne que vous souhaitez examiner. 
1. À l’ouverture du menu volant, **sélectionnez Télécharger le rapport sur les menaces**.
1. Ouvrez le rapport sur les menaces et fournissez plus d’informations sur la campagne. Les informations contenues dans le rapport incluent : 
- **Résumé:** Résumé général du type de campagne et du nombre d’utilisateurs ciblés dans votre organisation. 
- **Analyse:** Graphique chronologique du démarrage de la campagne, du nombre de messages ciblant votre organisation, ainsi que de la destination et des verdicts des messages. 
- **Origine de l’attaque :** Adresses IP et domaines d’envoi principaux avec un nombre de messages qui ont été remis aux boîtes de réception de votre organisation. Cela vous permet d’examiner qui cible votre organisation. 
- **Email modèle et charge utile :** ligne d’objet des e-mails qui faisaient partie de la campagne et des URL (et leur fréquence) présentes dans le cadre de la campagne.
- **Recommandations:** Recommandations pour les étapes suivantes pour corriger les messages.

## <a name="investigate-inboxed-messages-that-are-part-of-a-email-threat-campaign"></a>Examiner les messages boîte de réception qui font partie d’une campagne de menaces par e-mail

1. Accédez à la [page de campagne](https://security.microsoft.com/campaigns).
1. Faites défiler la liste des campagnes dans la **vue Détails**, sous le graphique.
1. Sélectionnez le nom de la campagne à examiner. Si le nombre de clics de la campagne est supérieur à zéro, cela indique qu’un utilisateur de votre organisation a cliqué sur une URL ou téléchargé un fichier à partir de l’e-mail.
1. Le menu volant de la campagne affiche plus d’informations sur la campagne, le graphique affiche une chronologie de la campagne du début à la date de fin de la campagne, et le diagramme de flux horizontal affiche les étapes de la campagne depuis son origine, le verdict et l’emplacement actuel des messages.
1. Sous le diagramme de flux, sélectionnez l’onglet **Clics d’URL** pour afficher les informations relatives au clic. Ici, vous pouvez voir l’utilisateur qui a cliqué sur une URL, si l’utilisateur est marqué comme un utilisateur de compte prioritaire, l’URL elle-même et l’heure du clic. 
1. Si vous souhaitez en savoir plus sur les messages dans la boîte de réception et les messages cliqués, sélectionnez **Explorer les messages** > **boîte de réception**. Un nouvel onglet s’ouvre et accède à l’Explorateur de menaces. 
1. Dans la **vue détails** de l’Explorateur, vous pouvez référencer **la dernière livraison** pour déterminer si un message est toujours dans la boîte de réception ou a été déplacé en quarantaine par le système ZAP. _Pour obtenir plus de détails sur le message spécifique, sélectionnez le message. Le menu volant fournit des informations supplémentaires. Lorsque vous sélectionnez la **page Ouvrir l’entité d’e-mail** en haut à gauche du menu volant, un nouvel onglet s’ouvre et vous donne des informations supplémentaires sur le message._
1.  Si vous souhaitez effectuer une action et déplacer les messages hors de la boîte de réception, vous pouvez sélectionner le message, puis sélectionner **Actions** >  de message **Déplacer vers le dossier indésirable**. Cela garantit que votre utilisateur ne continue pas à interagir avec le message malveillant qui pourrait entraîner une violation potentielle. 

## <a name="next-steps"></a>Prochaines étapes

Pour en savoir plus, lisez les [vues de campagne dans Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/campaigns).
