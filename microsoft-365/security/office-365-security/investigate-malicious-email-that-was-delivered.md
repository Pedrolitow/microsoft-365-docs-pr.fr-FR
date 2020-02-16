---
title: 'Rechercher et identifier les courriers électroniques malveillants qui ont été remis dans Office 365, correction, remède, correction, '
keywords: TIMailData-Inline, incident de sécurité, incident, PowerShell ATP, programmes malveillants de messagerie, utilisateurs compromis, hameçonnage par courrier électronique, programmes malveillants de messagerie, lire les en-têtes de courrier électronique, lire les en-têtes, lire les en-têtes de messages électroniques
f1.keywords:
- NOCSH
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
ms.assetid: 8f54cd33-4af7-4d1b-b800-68f8818e5b2a
ms.collection:
- M365-security-compliance
description: Découvrez comment utiliser les fonctionnalités d’analyse et de réponse aux menaces pour rechercher et examiner des courriers électroniques malveillants.
ms.openlocfilehash: 5fe9e06a582d72b46c4f90f13aee283050a06253
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42088707"
---
# <a name="investigate-and-remediate-malicious-email-that-was-delivered-in-office-365"></a>Examiner et résoudre les courriers électroniques malveillants remis dans Office 365

[Office 365 Advanced Threat Protection](office-365-atp.md) vous permet d’examiner les activités qui permettent de mettre en péril les personnes de votre organisation et de protéger votre organisation. Par exemple, si vous participez à l’équipe de sécurité de votre organisation, vous pouvez rechercher et enquêter sur les messages électroniques suspects qui ont été remis. Vous pouvez le faire à l’aide de l' [Explorateur de menaces (ou des détections en temps réel)](threat-explorer.md).
  
## <a name="before-you-begin"></a>Avant de commencer...

Assurez-vous que les conditions suivantes sont remplies :
  
- Votre organisation dispose d' [Office 365 protection avancée contre les menaces](office-365-atp.md) et des [licences sont attribuées aux utilisateurs](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users).
    
- La [journalisation d’audit Office 365](../../compliance/turn-audit-log-search-on-or-off.md) est activée pour votre organisation. 
    
- Votre organisation a défini des stratégies pour le blocage du courrier indésirable, anti-programme malveillant, anti-hameçonnage, etc. Consultez la rubrique [Protégez-vous contre les menaces dans Office 365](protect-against-threats.md).
    
- Vous êtes un administrateur général Office 365 ou vous avez l’administrateur de sécurité ou le rôle de recherche et de purge affecté dans le centre &amp; de sécurité et de conformité. Consultez [la rubrique autorisations dans le centre &amp; de sécurité conformité Office 365](permissions-in-the-security-and-compliance-center.md). Pour certaines actions, vous devez également avoir un nouveau rôle aperçu affecté. 

#### <a name="preview-role-permissions"></a>Aperçu des autorisations de rôle

Pour effectuer certaines actions, telles que l’affichage des en-têtes de message ou le téléchargement du contenu d’un message électronique, vous devez disposer d’un nouveau rôle appelé *Aperçu* ajouté à un autre groupe de rôles Office 365 approprié. Le tableau suivant clarifie les rôles et les autorisations requis.

|Activité  |Groupe de rôles |Prévisualiser le rôle nécessaire ?  |
|---------|---------|---------|
|Utilisation de l’Explorateur de menaces (et des détections en temps réel) pour analyser les menaces     |Administrateur général Office 365 <br> Administrateur de sécurité <br> Lecteur de sécurité     | Non   |
|Utiliser l’Explorateur de menaces (et les détections en temps réel) pour afficher les en-têtes des messages électroniques, ainsi que pour afficher un aperçu et télécharger des messages électroniques mis en quarantaine    |Administrateur général Office 365 <br> Administrateur de sécurité <br>Lecteur de sécurité   |       Non  |
|Utiliser l’Explorateur de menaces pour afficher les en-têtes et télécharger les messages électroniques remis aux boîtes aux lettres     |Administrateur général Office 365 <br>Administrateur de sécurité <br> Lecteur de sécurité <br> Aperçu   |   Oui      |

> [!NOTE]
> L' *Aperçu* est un rôle et non un groupe de rôles ; le rôle aperçu doit être ajouté à un groupe de rôles existant pour Office 365. Le rôle administrateur général Office 365 est affecté au centre d’administration Microsoft 365[https://admin.microsoft.com](https://admin.microsoft.com)(), et les rôles Administrateur de sécurité et lecteur de sécurité sont affectés dans le centre de sécurité &[https://protection.office.com](https://protection.office.com)de sécurité Office 365 (). Pour en savoir plus sur les rôles et les autorisations, consultez [la rubrique autorisations dans le centre de sécurité & conformité d’Office 365](permissions-in-the-security-and-compliance-center.md).

## <a name="find-and-delete-suspicious-email-that-was-delivered"></a>Rechercher et supprimer les e-mails suspects qui ont été remis

L’Explorateur de menaces est un rapport puissant qui peut servir plusieurs objectifs, tels que la recherche et la suppression de messages, l’identification de l’adresse IP d’un expéditeur de courrier malveillant ou le démarrage d’un incident en vue d’une nouvelle enquête. La procédure suivante décrit l’utilisation de l’Explorateur pour rechercher et supprimer les messages malveillants des boîtes aux lettres du destinataire.

1. **Accédez à l’Explorateur de menaces**: [https://protection.office.com](https://protection.office.com) accédez à et connectez-vous à l’aide de votre compte professionnel ou scolaire pour Office 365. Vous accédez au centre de sécurité &amp; conformité.

2. Dans le lancement rapide de navigation de gauche, choisissez **Explorateur**de **gestion** \> des menaces.

    ![Explorateur avec les champs d’action de remise et d’emplacement de remise.](../../media/ThreatExFields.PNG)

    <!-- You may notice the new **Special actions** column. This feature is aimed at telling admins the outcome of processing an email. The **Special actions** column can be accessed in the same place as **Delivery action** and **Delivery location**. Special actions might be updated at the end of Threat Explorer's email timeline, which is a new feature aimed at making the hunting experience better for admins.-->

3. **Affichages dans l’Explorateur de menaces**: dans le menu **affichage** , choisissez **tous les messages électroniques**.

    ![Menu Affichage de l’Explorateur de menaces, messagerie-programmes malveillants, hameçons, envois et toutes les options de messagerie, également contenu-programmes malveillants.](../../media/tp-InvestigateMalEmail-viewmenu.png)

    La vue de *programmes malveillants* est actuellement la vue par défaut et capture les messages électroniques dans lesquels une menace de programme malveillant est détectée. La vue de *hameçonnage* fonctionne de la même manière, pour les hameçons.

    Toutefois, *tout* le courrier électronique reçoit la liste de tous les messages reçus par l’organisation, qu’ils soient détectés ou non. Comme vous pouvez l’imaginer, il s’agit d’un grand nombre de données, c’est pourquoi cette vue affiche un espace réservé qui demande l’application d’un filtre. (Cette vue est disponible uniquement pour les clients DAV P2.)

    L’affichage des *envois* affiche tous les messages envoyés par l’administrateur ou l’utilisateur qui ont été signalés à Microsoft.

4. **Recherche et filtrage dans l’Explorateur de menaces**: les filtres apparaissent en haut de la page dans la barre de recherche pour aider les administrateurs à effectuer leurs recherches. Vous pouvez remarquer que plusieurs filtres peuvent être appliqués simultanément et que plusieurs valeurs séparées par des virgules ont été ajoutées à un filtre pour limiter la recherche. Rappels :
    - Les filtres correspondent exactement à la plupart des conditions de filtrage.
    - Le filtre de l’objet utilise une requête CONTAINs.
    - Les filtres d’URL fonctionnent avec ou sans protocoles (par exemple, https).
    - Le domaine de l’URL, le chemin d’URL et le domaine d’URL et les filtres de chemin d’accès ne nécessitent aucun protocole pour le filtrage.
    - Vous devez cliquer sur l’icône actualiser chaque fois que vous modifiez les valeurs du filtre pour obtenir les résultats pertinents.

5. **Filtres avancés**: grâce à ces filtres, vous pouvez créer des requêtes complexes et filtrer votre jeu de données. Si vous cliquez sur *filtres avancés* , un menu volant s’ouvre avec des options.

   Le filtrage avancé est un excellent complément des fonctionnalités de recherche. Un filtre **non** booléen a été introduit sur le *destinataire*, l' *expéditeur* et le domaine de l' *expéditeur* pour permettre aux administrateurs d’effectuer des recherches en excluant les valeurs. Cette option apparaît sous le paramètre *de sélection contient aucun de*. **Ne laisser pas** les administrateurs exclure les boîtes aux lettres d’alerte, les boîtes aux lettres de réponse par défaut de leurs investigations et est utile pour les cas où les administrateurs recherchent un sujet spécifique (Subject = "attention") où le destinataire peut être défini sur *none of defaultMail@contoso.com*. Il s’agit d’une recherche de valeur exacte.

   ![Le paramètre Recipients-'ne contient aucun des’filtre avancé.](../../media/tp-InvestigateMalEmail-AdvancedFilter.png)

   Le *filtrage par heures permet à* l’équipe de sécurité de votre organisation d’approfondir rapidement votre organisation. La durée de temps la plus courte autorisée est de 30 minutes. Si vous pouvez limiter l’action suspecte par intervalle de temps (par exemple, il s’est produit 3 heures auparavant), cela limite le contexte et aide à identifier le problème.

  ![L’option filtrage par heures permet de réduire la quantité de données que les équipes de sécurité de données doivent traiter, et dont la durée la plus courte est de 30 minutes.](../../media/tp-InvestigateMalEmail-FilterbyHours.png)

6. **Champs dans l’Explorateur de menaces : l'** Explorateur de menaces expose beaucoup plus d’informations sur la sécurité, telles que l' *action de remise*, l' *emplacement de remise*, l' *action spéciale*, la *direction*, les *remplacements*et les menaces liées à l' *URL*. Il permet également à l’équipe de sécurité de votre organisation d’examiner avec une plus grande certitude. 

    L' *action de remise* est l’action entreprise sur un courrier électronique en raison de stratégies ou de détections existantes. Voici les actions possibles qu’un courrier électronique peut effectuer :
    - **Remis** : le courrier électronique a été remis à la boîte de réception ou au dossier d’un utilisateur et l’utilisateur peut y accéder directement.
    - **Courrier indésirable** (remis à courrier indésirable) : le courrier électronique a été envoyé vers le dossier de courrier indésirable de l’utilisateur ou un dossier supprimé, et l’utilisateur a accès aux messages électroniques dans leur dossier de courrier indésirable ou supprimé.
    - **Bloqué** : tous les messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés. (Cette inaccessibilité est entièrement inaccessible par l’utilisateur.)
    - **Remplacé** : tout message électronique où des pièces jointes malveillantes sont remplacées par des fichiers. txt qui indiquent que la pièce jointe était malveillante

    **Emplacement de remise**: le filtre d’emplacement de remise est disponible afin d’aider les administrateurs à comprendre où se terminent les e-mails malveillants suspectés et les actions qui ont été effectuées. Les données résultantes peuvent être exportées dans la feuille de calcul. Les emplacements de remise possibles sont les suivants :
    - **Boîte de réception ou dossier** : le courrier électronique se trouve dans la boîte de réception ou dans un dossier spécifique, en fonction de vos règles de messagerie.
    - **Local ou externe** : la boîte aux lettres n’existe pas dans le Cloud, mais elle est locale.
    - **Dossier courrier indésirable** : le courrier électronique se trouve dans le dossier courrier indésirable de l’utilisateur.
    - **Dossier éléments supprimés** : le courrier électronique se trouve dans le dossier éléments supprimés d’un utilisateur.
    - **Quarantaine** – message en quarantaine, pas dans la boîte aux lettres d’un utilisateur.
    - **Échec** : la messagerie n’a pas pu atteindre la boîte aux lettres.
    - **Ignoré** : le courrier électronique a été perdu dans le flux de messagerie.

    **Direction**: cette option permet à votre équipe chargée des opérations de sécurité de filtrer en fonction de la « direction » à partir de laquelle un courrier arrive. Les valeurs de direction sont *entrantes*, *sortantes*et *intra-org* (correspondant aux messages entrants dans votre organisation de l’extérieur, qui sont envoyés hors de votre organisation ou qui sont envoyés en interne à votre organisation, respectivement). Ces informations peuvent aider les équipes des opérations de sécurité à emprunter l’usurpation d’identité et l’emprunt d’identité, car il n’est pas possible de trouver une différence entre la valeur de direction (par exemple, *Entrant*) et le domaine de l’expéditeur (qui *semble* être un domaine interne) est évident ! La valeur de la direction est distincte et peut différer du suivi des messages. Les résultats peuvent être exportés dans la feuille de calcul.

    **Substitutions**: ce filtre prend des informations qui s’affichent sous l’onglet Détails du courrier et l’utilise pour exposer les stratégies d’organisation ou d’organisation permettant d’autoriser et de bloquer les messages qui ont été *remplacés*. L’élément le plus important de ce filtre est qu’il permet à l’équipe de sécurité de votre organisation de voir le nombre de messages électroniques suspects qui ont été remis en raison de la configuration. Cela leur donne la possibilité de modifier les autorisation et de les bloquer selon les besoins. Ce jeu de résultats de ce filtre peut être exporté vers la feuille de calcul.

|L’Explorateur de menaces remplace  | Signification  |
|---------|---------|
|Autorisé par la stratégie d’organisation     |   Le courrier a été autorisé dans la boîte aux lettres comme indiqué par la stratégie de l’organisation.       |
|Bloqué par la stratégie d’organisation      |  La remise des messages à la boîte aux lettres a été bloquée par la stratégie de l’organisation.    |
|Extension de fichier bloquée par la stratégie d’organisation     | La remise du fichier à la boîte aux lettres a été bloquée par la stratégie de l’organisation.        |
|Autorisé par la stratégie de l’utilisateur     | Le courrier a été autorisé dans la boîte aux lettres comme indiqué par la stratégie de l’utilisateur.        |
|Bloqué par la stratégie de l’utilisateur     | La remise des messages à la boîte aux lettres a été bloquée par la stratégie de l’utilisateur.        |

**Menace d’URL**: le champ URL Threat a été inclus dans l’onglet *Details (détails* ) d’un e-mail pour indiquer la menace présentée par une URL. Les menaces présentées par une URL peuvent inclure des *programmes malveillants*, des *hameçons*ou du *courrier indésirable*, et une URL sans *menace* indique *aucun* dans la section menaces.

7. **Affichage chronologie du courrier électronique**: votre équipe des opérations de sécurité peut avoir besoin d’approfondir les détails du courrier électronique pour approfondir votre enquête. La chronologie du courrier permet aux administrateurs d’afficher les actions exécutées sur un e-mail à partir de la remise à la post-livraison. Pour afficher une chronologie par courrier électronique, cliquez sur l’objet d’un message électronique, puis cliquez sur chronologie du courrier électronique. (Il apparaît dans les autres en-têtes, tels que Résumé ou détails.) Ces résultats peuvent être exportés dans la feuille de calcul.

    La chronologie du courrier électronique s’ouvre dans une table qui affiche tous les événements de remise et post-remise pour le courrier électronique. S’il n’y a pas d’autres actions sur le courrier électronique, vous devez voir un seul événement pour la remise d’origine qui indique un résultat, comme *bloqué*, avec un verdict comme *hameçonnage*. Les administrateurs peuvent exporter l’intégralité de la chronologie du courrier, y compris tous les détails de l’onglet et de la messagerie (par exemple, objet, expéditeur, destinataire, réseau et ID de message). La chronologie du courrier diminue en fonction de la randomisation, car il y a moins de temps passé à vérifier différents emplacements pour essayer de comprendre les événements qui se sont produits depuis que le courrier électronique est arrivé. Lorsque plusieurs événements se produisent à la même heure ou proches de celle-ci dans un message électronique, ces événements apparaissent dans un affichage chronologie.

8. **Aperçu/téléchargement**: l’Explorateur de menaces offre à votre équipe de sécurité les informations dont il a besoin pour enquêter sur le courrier électronique suspect. Votre équipe des opérations de sécurité peut :

    - [Vérifiez l’action de remise et l’emplacement](#check-the-delivery-action-and-location).

    - [Affichez la chronologie de votre courrier électronique](#view-the-timeline-of-your-email).

    ##### <a name="check-the-delivery-action-and-location"></a>Vérifier l’action de remise et l’emplacement

    Dans l' [Explorateur de menaces (et les détections en temps réel)](threat-explorer.md), **vous disposez maintenant** de colonnes de l’adresse de remise et d' **emplacement de remise** au lieu de l’ancienne colonne d’état de **remise** . Cela permet d’obtenir une image plus complète de l’emplacement de vos messages électroniques. Une partie de cette modification consiste à faciliter les enquêtes pour les équipes des opérations de sécurité, mais le résultat net est de savoir en un clin d’œil l’emplacement des messages électroniques posant problème.

    L’état de remise est désormais divisé en deux colonnes :

    - **Action de remise** : quel est le statut de ce courrier électronique ?

    - **Emplacement de remise** : où ce message électronique a-t-il été routé ?

    L’action de remise est l’action entreprise sur un courrier électronique en raison de stratégies ou de détections existantes. Voici les actions possibles qu’un courrier électronique peut effectuer :

    - **Remis** : le courrier électronique a été remis à la boîte de réception ou au dossier d’un utilisateur et l’utilisateur peut y accéder directement.

    - **Courrier indésirable** – le courrier électronique a été envoyé vers le dossier de courrier indésirable de l’utilisateur ou le dossier supprimé, et l’utilisateur a accès aux messages électroniques dans son dossier de courrier indésirable ou supprimé.

    - **Bloqué** : tous les messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés. (Cette inaccessibilité est entièrement inaccessible par l’utilisateur.)

    - **Remplacé** : tout message électronique où des pièces jointes malveillantes sont remplacées par des fichiers. txt qui indiquent que la pièce jointe était malveillante.
 
    Emplacement de remise : affiche les résultats des stratégies et des détections qui exécutent une post-remise. Elle est liée à une action de remise. Ce champ a été ajouté pour permettre de mieux comprendre l’action entreprise lors de la détection d’un message problématique. Voici les valeurs possibles de l’emplacement de remise :

    - **Boîte de réception ou dossier** : le courrier électronique se trouve dans la boîte de réception ou dans un dossier (en fonction de vos règles de messagerie électronique).

    - **Local ou externe** : la boîte aux lettres n’existe pas sur le Cloud, mais elle est locale.

    - **Dossier courrier indésirable** : le courrier électronique se trouve dans le dossier de courrier indésirable d’un utilisateur.

    - **Dossier éléments supprimés** : le courrier électronique se trouve dans le dossier éléments supprimés d’un utilisateur.

    - **Quarantaine** – message en quarantaine, pas dans la boîte aux lettres d’un utilisateur.

    - **Échec** : la messagerie n’a pas pu atteindre la boîte aux lettres.

    - **Ignoré** : le courrier électronique est perdu dans le flux de messagerie.

     ##### <a name="view-the-timeline-of-your-email"></a>Affichage de la chronologie de votre courrier électronique
  
     La **chronologie par courrier électronique** est un champ dans l’Explorateur de menaces qui facilite la chasse à votre équipe des opérations de sécurité. Lorsque plusieurs événements se produisent ou se ferment à la même heure dans un e-mail, ces événements apparaissent dans un affichage chronologie. Certains événements qui ont lieu après la livraison à la messagerie sont capturés dans la colonne **actions spéciales** . La combinaison des informations de la chronologie d’un message électronique avec toutes les actions spéciales effectuées après la livraison permet aux administrateurs de mieux comprendre les stratégies et la gestion des menaces (par exemple, l’endroit où le courrier a été acheminé et, dans certains cas, l’évaluation finale).

<!-- Reference material

1. **Navigate to Threat Explorer**: Go to [https://protection.office.com](https://protection.office.com) and sign in using your work or school account for Office 365. This takes you to the Security &amp; Compliance Center. 

2. In the left navigation quick-launch, choose **Threat management** \> **Explorer**.

3. Click on the subject of an email message, and then click **Email timeline**. (It appears among other headings on the panel like **Summary** or **Details**.)

    Once you've opened the email timeline, you should see a table that tells you the post-delivery events for that mail. In the case of no further events for the email, you should see a single event for the original delivery that states a result like **Blocked** with a verdict like **Phish**. The tab also has the option to export the entire email timeline, and this exports all the details on the tab and details on the email (things like Subject, Sender, Recipient, Network, and Message ID).

    The email timeline cuts down on randomization because there is less time spent checking different locations to try to understand events that happened since the email arrived. When multiple events happen at, or close to, the same time on an email, those events show up in a timeline view. 
    
    Some events that happen post-delivery to your mail are captured in the **Special actions** column. Combining the information from the email timeline along with special actions taken on email post-delivery gives admins insight into how their policies work, where the email was finally routed, and, in some cases, what the final assessment was. 

4. In the **View** menu, choose **All email**.

    ![Use the View menu to choose between Email and Content reports](../../media/d39013ff-93b6-42f6-bee5-628895c251c2.png)
  
    Notice the labels that appear in the report, such as **Delivered**, **Unknown**, or **Delivered to junk**.

    ![Threat Explorer showing data for all email](../../media/208826ed-a85e-446f-b276-b5fdc312fbcb.png)
    
    (Depending on the actions that were taken on email messages for your organization, you might see other labels, such as **Blocked** or **Replaced**.)
    
5. In the report, choose **Delivered** to view only email messages that ended up in users' inboxes.

    ![Clicking "Delivered to junk" removes that data from view](../../media/e6fb2e47-461e-4f6f-8c65-c331bd858758.png)
  
6. Below the chart, review the **Email** list below the chart.

    ![Below the chart, view a list of email messages that were detected](../../media/dfb60590-1236-499d-97da-86c68621e2bc.png)
  
7. In the list, choose an item to view more details about that email message. For example, you can click the subject line to view information about the sender, recipients, attachments, and other similar email messages.

    ![You can view additional information about an item](../../media/5a5707c3-d62a-4610-ae7b-900fff8708b2.png)
  
8. After viewing information about email messages, select one or more items in the list to activate **+ Actions**.
    
9. Use the **+ Actions** list to apply an action, such as **Move to deleted** items. This deletes the selected messages from the recipients' mailboxes.

    ![When you select one or more email messages, you can choose from several available actions](../../media/ef12e10c-60a7-4f66-8f76-68d77ae26de1.png)

## Dealing with suspicious email messages

Malicious attackers might be sending mail to people in your organization in an attempt to phish their credentials and gain access to your corporate secrets. To help prevent this, you use the threat protection services in Office 365, including [Exchange Online Protection](exchange-online-protection-overview.md) and [Advanced Threat Protection](office-365-atp.md). However, it occasionally happens that an attacker sends email that contains a link (URL) that only later points to malicious content (such as malware). Or, you might realize too late that someone in your organization has been compromised, and while they were compromised, an attacker used their account to send email to other people in your organization. As part of dealing with either of these scenarios, you can remove suspicious email messages from user inboxes. To do that, you can use [Threat Explorer](threat-explorer.md).

## Finding re-routed email messages after actions are taken

Threat Explorer provides your security operations team with the details they need to investigate suspicious email. Your security operations team can:

- [View the email headers and download the email body](#view-the-email-headers-and-download-the-email-body) 

- [Check the delivery action and location](#check-the-delivery-action-and-location)

- [View the timeline of your email](#view-the-timeline-of-your-email)

### View the email headers and download the email body

The ability to preview email headers and download the body of an email body are powerful capabilities in Threat Explorer. Appropriate [permissions](permissions-in-the-security-and-compliance-center.md) must be assigned. See [Preview role permissions](#preview-role-permissions).

To access your message header and email download options, follow these steps: 

1. Go to [https://protection.office.com](https://protection.office.com) and sign in using your work or school account for Office 365. This takes you to the Security &amp; Compliance Center. 
    
2. In the left navigation, choose **Threat management** \> **Explorer**.

3. Click on a subject in the Threat Explorer table. 

    This opens the flyout, where both header preview and email download links are positioned.

    ![Threat Explorer flyout with download and preview links on the page.](../../media/ThreatExplorerDownloadandPreview.PNG)

> [!IMPORTANT]
> This capability doesn't show up for email messages that were never found in a user's mailbox, which can happen if an email was dropped or its delivery failed. In cases where email messages were deleted from users' mailboxes, admins see a "Mail not found" error message.
-->

## <a name="related-topics"></a>Voir aussi

[Protection avancée contre les menaces dans Office 365](office-365-ti.md)
  
[Se protéger contre les menaces dans Office 365](protect-against-threats.md)
  
[Afficher les rapports pour Office 365 protection avancée contre les menaces](view-reports-for-atp.md)
