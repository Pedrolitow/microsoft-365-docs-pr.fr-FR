---
title: Examiner les e-mails malveillants qui ont été remis dans Microsoft 365, rechercher et examiner les e-mails malveillants
keywords: TIMailData-Inline, Incident de sécurité, incident, Microsoft Defender pour point de terminaison PowerShell, programmes malveillants d’e-mail, utilisateurs compromis, hameçonnage d’e-mail, programmes malveillants de messagerie, en-têtes de lecture d’e-mail, en-têtes de lecture, en-têtes d’e-mail ouverts, actions spéciales
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/16/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 8f54cd33-4af7-4d1b-b800-68f8818e5b2a
ms.collection:
- m365-security
description: Découvrez comment utiliser les fonctionnalités d’investigation et de réponse aux menaces pour rechercher et examiner les e-mails malveillants.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 5affd100b73478d1ee983b83dfdaea394a9d3acd
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68092024"
---
# <a name="investigate-malicious-email-that-was-delivered-in-microsoft-365"></a>Examiner les e-mails malveillants qui ont été remis dans Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**

- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Microsoft Defender pour Office 365](defender-for-office-365.md) vous permet d’examiner les activités qui mettent des personnes de votre organisation en danger et de prendre des mesures pour protéger votre organisation. Par exemple, si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez rechercher et examiner les messages électroniques suspects qui ont été remis. Pour ce faire, utilisez [l’Explorateur de menaces (ou des détections en temps réel).](threat-explorer.md)

> [!NOTE]
> Passez à l’article de correction [ici](remediate-malicious-email-delivered-office-365.md).

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que les conditions suivantes sont remplies :

- Votre organisation a [Microsoft Defender pour Office 365](defender-for-office-365.md) et [des licences sont attribuées aux utilisateurs](../../admin/manage/assign-licenses-to-users.md).

- [La journalisation d’audit](../../compliance/turn-audit-log-search-on-or-off.md) est activée pour votre organisation.

- Votre organisation a des stratégies définies pour les programmes anti-courrier indésirable, anti-programmes malveillants, anti-hameçonnage, et ainsi de suite. Consultez [Protéger contre les menaces dans Office 365](protect-against-threats.md).

- Vous êtes administrateur général, ou le rôle Administrateur de sécurité ou Recherche et purge est attribué dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md). Pour certaines actions, le rôle Aperçu doit également être attribué.

### <a name="preview-role-permissions"></a>Autorisations de rôle d’aperçu

Pour effectuer certaines actions, telles que l’affichage des en-têtes de message ou le téléchargement du contenu des messages électroniques, le rôle *Aperçu* doit être ajouté à un autre groupe de rôles approprié. Le tableau suivant clarifie les rôles et autorisations requis.

|Activité|Groupe de rôles|Un rôle d’aperçu est-il nécessaire ?|
|---|---|---|
|Utiliser l’Explorateur de menaces (et les détections en temps réel) pour analyser les menaces|Administrateur général <p> Administrateur de sécurité <p> Lecteur de sécurité|Non|
|Utiliser l’Explorateur de menaces (et les détections en temps réel) pour afficher les en-têtes des messages électroniques, ainsi que pour afficher un aperçu et télécharger des messages électroniques mis en quarantaine|Administrateur général <p> Administrateur de sécurité <p> Lecteur de sécurité|Non|
|Utiliser l’Explorateur de menaces pour afficher les en-têtes, afficher un aperçu de l’e-mail (uniquement dans la page d’entité de messagerie) et télécharger les messages électroniques remis aux boîtes aux lettres|Administrateur général <p> Administrateur de sécurité <p> Lecteur de sécurité <p> Aperçu|Oui|

> [!NOTE]
> **La préversion** est un rôle, pas un groupe de rôles. Le rôle d’aperçu doit être ajouté à un groupe de rôles existant ou à un nouveau groupe de rôles dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
>
> Le rôle Administrateur général se voit attribuer le Centre d'administration Microsoft 365 à l’adresse <https://admin.microsoft.com>. Les rôles Administrateur de sécurité et Lecteur sécurité sont attribués dans Microsoft 365 Defender portail.

Nous comprenons que l’aperçu et le téléchargement des e-mails sont des activités sensibles. L’audit est donc activé pour ces activités. Une fois qu’un administrateur effectue ces activités sur l’e-mail, les journaux d’audit sont générés pour la même chose et peuvent être affichés dans le portail <https://security.microsoft.com>  \> Microsoft 365 Defender sous l’onglet **Recherche** d’audit, puis filtrent sur le nom d’administrateur dans la zone **Utilisateurs**. Les résultats filtrés affichent l’activité **AdminMailAccess**. Sélectionnez une ligne pour afficher les détails dans la section **Plus d’informations** sur les e-mails en préversion ou téléchargés.

## <a name="find-suspicious-email-that-was-delivered"></a>Rechercher les e-mails suspects qui ont été remis

L’Explorateur de menaces est un rapport puissant qui peut servir à plusieurs fins, telles que la recherche et la suppression de messages, l’identification de l’adresse IP d’un expéditeur de courrier malveillant ou le démarrage d’un incident pour une investigation plus approfondie. La procédure suivante se concentre sur l’utilisation de l’Explorateur pour rechercher et supprimer des courriers malveillants des boîtes aux lettres du destinataire.

> [!NOTE]
> Les recherches par défaut dans l’Explorateur n’incluent actuellement pas les éléments remis qui ont été supprimés de la boîte aux lettres cloud par vidage automatique de zéro heure (ZAP). Cette limitation s’applique à toutes les vues (par exemple, les **vues Email \> Malware** ou **Email \> Phish**). Pour inclure les éléments supprimés par ZAP, vous devez ajouter un jeu **d’actions de remise** pour inclure **Removed by ZAP**. Si vous incluez toutes les options, vous verrez tous les résultats de l’action de remise, y compris les éléments supprimés par ZAP.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **l’Explorateur de collaboration** \> Email & . Pour accéder directement à la page **Explorateur** , utilisez <https://security.microsoft.com/threatexplorer>.

   Dans la page **Explorateur** , la colonne **Actions supplémentaires** indique aux administrateurs le résultat du traitement d’un e-mail. La colonne **Actions supplémentaires** est accessible au même emplacement que l’action **de remise** et **l’emplacement de remise**. Les actions spéciales peuvent être mises à jour à la fin de la chronologie des e-mails de l’Explorateur de menaces, qui est une nouvelle fonctionnalité visant à améliorer l’expérience de chasse pour les administrateurs.

2. Dans le menu **Affichage**, choisissez **Email** \> **Tous les e-mails** dans la liste déroulante.

    :::image type="content" source="../../media/tp-InvestigateMalEmail-viewmenu.png" alt-text="Liste déroulante Programmes malveillants" lightbox="../../media/tp-InvestigateMalEmail-viewmenu.png":::

    La vue *Programmes malveillants* est actuellement la valeur par défaut et capture les e-mails où une menace de programme malveillant est détectée. La vue *Phish* fonctionne de la même façon, pour Phish.

    Toutefois, *tous les affichages de courrier* répertorient tous les messages reçus par l’organisation, que des menaces aient été détectées ou non. Comme vous pouvez l’imaginer, il s’agit d’un grand nombre de données, c’est pourquoi cette vue montre un espace réservé qui demande l’application d’un filtre. (Cette vue est disponible uniquement pour les clients Defender pour Office 365 P2.)

    *La vue Soumissions* affiche tous les messages envoyés par l’administrateur ou l’utilisateur qui ont été signalés à Microsoft.

4. **Rechercher et filtrer dans l’Explorateur de menaces** : les filtres apparaissent en haut de la page dans la barre de recherche pour aider les administrateurs dans leurs investigations. Notez que plusieurs filtres peuvent être appliqués en même temps et que plusieurs valeurs séparées par des virgules sont ajoutées à un filtre pour affiner la recherche. N’oubliez pas :

    - Les filtres correspondent exactement à la plupart des conditions de filtre.
    - Le filtre d’objet utilise une requête CONTAINS.
    - Les filtres d’URL fonctionnent avec ou sans protocoles (par exemple, https).
    - Les filtres de domaine d’URL, de chemin d’URL et de domaine d’URL ne nécessitent pas de protocole pour filtrer.
    - Vous devez cliquer sur l’icône Actualiser chaque fois que vous modifiez les valeurs de filtre pour obtenir les résultats pertinents.

5. **Filtres avancés** : avec ces filtres, vous pouvez créer des requêtes complexes et filtrer votre jeu de données. Cliquer sur *Filtres avancés* ouvre un menu volant avec des options.

   Le filtrage avancé est un excellent ajout aux fonctionnalités de recherche. Un NOT booléen sur les filtres de domaine **Destinataire**, **Expéditeur** et **Expéditeur** permet aux administrateurs d’examiner en excluant les valeurs. Cette option n’est **égal à aucune sélection** . Cette option permet aux administrateurs d’exclure les boîtes aux lettres indésirables des investigations (par exemple, les boîtes aux lettres d’alerte et les boîtes aux lettres de réponse par défaut) et est utile pour les cas où les administrateurs recherchent un sujet spécifique (par exemple, Attention) où le destinataire peut être défini sur *Égal à aucun des éléments suivants : defaultMail@contoso.com*. Il s’agit d’une recherche de valeurs exacte.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-AdvancedFilter.png" alt-text="Volet Destinataires" lightbox="../../media/tp-InvestigateMalEmail-AdvancedFilter.png":::

   L’ajout d’un filtre d’heure à la date de début et à la date de fin permet à votre équipe de sécurité d’explorer rapidement. La durée la plus courte autorisée est de 30 minutes. Si vous pouvez limiter l’action suspecte par intervalle de temps (par exemple, il y a 3 heures), cela limite le contexte et aide à identifier le problème.

   :::image type="content" source="../../media/tp-InvestigateMalEmail-FilterbyHours.png" alt-text="Option de filtrage par heures" lightbox="../../media/tp-InvestigateMalEmail-FilterbyHours.png":::

6. **Champs dans l’Explorateur de menaces** : l’Explorateur de menaces expose beaucoup plus d’informations de messagerie liées à la sécurité, telles que *l’action de remise*, *l’emplacement de remise*, *l’action spéciale*, *la directionnalité*, *les remplacements et les menaces* *d’URL*. Il permet également à l’équipe de sécurité de votre organisation d’enquêter avec une plus grande certitude.

    *L’action de remise* est l’action effectuée sur un e-mail en raison de stratégies ou de détections existantes. Voici les actions possibles qu’un e-mail peut effectuer :

    - **Remis** : l’e-mail a été remis à la boîte de réception ou au dossier d’un utilisateur et l’utilisateur peut y accéder directement.
    - **Indésirable** (remis à la courrier indésirable) : l’e-mail a été envoyé au dossier indésirable de l’utilisateur ou au dossier supprimé, et l’utilisateur a accès aux messages électroniques dans son dossier Courrier indésirable ou Supprimé.
    - **Bloqué** : tous les messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés.
    - **Remplacé** : tout e-mail où les pièces jointes malveillantes sont remplacées par des fichiers .txt indiquant que la pièce jointe était malveillante

    **Emplacement de remise** : le filtre d’emplacement de remise est disponible pour aider les administrateurs à comprendre où les messages malveillants suspects se sont terminés et quelles actions ont été effectuées sur celui-ci. Les données obtenues peuvent être exportées vers une feuille de calcul. Les emplacements de livraison possibles sont les suivants :

    - **Boîte de réception ou dossier** : l’e-mail se trouve dans la boîte de réception ou un dossier spécifique, en fonction de vos règles de messagerie.
    - **Local ou externe** : la boîte aux lettres n’existe pas dans le cloud, mais elle est locale.
    - **Dossier courrier indésirable** : l’e-mail se trouve dans le dossier Courrier indésirable d’un utilisateur.
    - **Dossier Éléments supprimés** : l’e-mail se trouve dans le dossier Éléments supprimés d’un utilisateur.
    - **Mise en quarantaine** : e-mail en quarantaine et non dans la boîte aux lettres d’un utilisateur.
    - **Échec** : l’e-mail n’a pas pu atteindre la boîte aux lettres.
    - **Supprimé** : l’e-mail a été perdu quelque part dans le flux de courrier.

    **Directionnalité** : cette option permet à votre équipe chargée des opérations de sécurité de filtrer en fonction de la « direction » d’un courrier provenant ou en cours d’envoi. Les valeurs de direction sont *entrantes*, *sortantes* et *intra-organisation* (correspondant au courrier entrant dans votre organisation de l’extérieur, envoyé hors de votre organisation ou envoyé en interne à votre organisation, respectivement). Ces informations peuvent aider les équipes des opérations de sécurité à repérer l’usurpation d’identité et l’emprunt d’identité, car une incompatibilité entre la valeur directionalité (par exemple, *Entrant*) et le domaine de l’expéditeur (qui semble être un domaine interne) seront *évidents* ! La valeur Directionality est distincte et peut différer de la trace de message. Les résultats peuvent être exportés vers une feuille de calcul.

    **Remplacements** : ce filtre prend les informations qui apparaissent dans l’onglet Détails du courrier et l’utilise pour exposer où les stratégies organisationnelles ou utilisateurs pour autoriser et bloquer les messages ont été *remplacées*. La chose la plus importante à propos de ce filtre est qu’il aide l’équipe de sécurité de votre organisation à voir combien d’e-mails suspects ont été remis en raison de la configuration. Cela leur donne la possibilité de modifier les autorisations et les blocs en fonction des besoins. Ce jeu de résultats de ce filtre peut être exporté vers une feuille de calcul.

    |Remplacements de l’Explorateur de menaces|Qu’est-ce qu’ils signifient ?|
    |---|---|
    |Autorisé par la stratégie d’organisation|Le courrier a été autorisé dans la boîte aux lettres comme indiqué par la stratégie d’organisation.|
    |Bloqué par la stratégie d’organisation|La remise du courrier à la boîte aux lettres a été bloquée, comme indiqué par la stratégie d’organisation.|
    |Extension de fichier bloquée par la stratégie d’organisation|La remise du fichier à la boîte aux lettres a été bloquée, comme indiqué par la stratégie d’organisation.|
    |Autorisé par la stratégie utilisateur|Le courrier a été autorisé dans la boîte aux lettres comme indiqué par la stratégie utilisateur.|
    |Bloqué par la stratégie utilisateur|La remise du courrier à la boîte aux lettres a été bloquée, comme indiqué par la stratégie utilisateur.|

    **Menace d’URL** : le champ de menace d’URL a été inclus dans l’onglet *Détails* d’un e-mail pour indiquer la menace présentée par une URL. Les menaces présentées par une URL peuvent inclure les *programmes malveillants*, *les hameçonnages* ou *le courrier indésirable*, et une URL *sans menace* indiquera *Aucune* dans la section menaces.

7. **Email vue de chronologie** : votre équipe des opérations de sécurité peut avoir besoin d’approfondir les détails de l’e-mail pour approfondir les recherches. La chronologie de l’e-mail permet aux administrateurs d’afficher les actions effectuées sur un e-mail de la remise à la post-remise. Pour afficher une chronologie d’e-mail, cliquez sur l’objet d’un e-mail, puis cliquez sur Email chronologie. (Il apparaît parmi d’autres en-têtes du panneau, tels que Résumé ou Détails.) Ces résultats peuvent être exportés vers une feuille de calcul.

    Email chronologie s’ouvre sur une table qui affiche tous les événements de remise et de post-remise pour l’e-mail. S’il n’y a aucune autre action sur l’e-mail, vous devez voir un événement unique pour la remise d’origine qui indique un résultat, tel que *Bloqué*, avec un verdict comme *Phish*. Les administrateurs peuvent exporter l’intégralité de la chronologie de l’e-mail, y compris tous les détails de l’onglet et de l’e-mail (par exemple, Objet, Expéditeur, Destinataire, Réseau et ID de message). La chronologie de l’e-mail réduit la randomisation, car il y a moins de temps passé à vérifier différents emplacements pour essayer de comprendre les événements qui se sont produits depuis l’arrivée de l’e-mail. Lorsque plusieurs événements se produisent à la même heure ou à proximité d’un e-mail, ces événements s’affichent dans un affichage chronologie.

8. **Préversion/téléchargement** : l’Explorateur de menaces fournit à votre équipe chargée des opérations de sécurité les détails dont elle a besoin pour examiner les e-mails suspects. Votre équipe des opérations de sécurité peut :

    - [Vérifiez l’action de remise et l’emplacement](#check-the-delivery-action-and-location).

    - [Affichez la chronologie de votre e-mail](#view-the-timeline-of-your-email).

### <a name="check-the-delivery-action-and-location"></a>Vérifier l’action de remise et l’emplacement

Dans [l’Explorateur de menaces (et les détections en temps réel),](threat-explorer.md) vous disposez désormais de colonnes **Action de remise** et **Emplacement de remise** au lieu de l’ancienne colonne **État** de remise. Cela donne une image plus complète de l’endroit où vos messages électroniques arrivent. Une partie de l’objectif de cette modification est de faciliter les investigations pour les équipes chargées des opérations de sécurité, mais le résultat net est de connaître l’emplacement des messages électroniques problématiques en un clin d’œil.

L’état de remise est maintenant divisé en deux colonnes :

- **Action de remise** : quel est l’état de cet e-mail ?
- **Emplacement de remise** : où cet e-mail a-t-il été acheminé ?

L’action de remise est l’action effectuée sur un e-mail en raison de stratégies ou de détections existantes. Voici les actions possibles qu’un e-mail peut effectuer :

- **Remis** : l’e-mail a été remis à la boîte de réception ou au dossier d’un utilisateur et l’utilisateur peut y accéder directement.
- **Courrier indésirable** : l’e-mail a été envoyé au dossier indésirable de l’utilisateur ou au dossier supprimé, et l’utilisateur a accès aux messages électroniques dans son dossier Courrier indésirable ou Supprimé.
- **Bloqué** : tous les messages électroniques mis en quarantaine, qui ont échoué ou qui ont été supprimés.
- **Remplacé** : tout e-mail où les pièces jointes malveillantes sont remplacées par des fichiers .txt indiquant que la pièce jointe était malveillante.

L’emplacement de remise affiche les résultats des stratégies et des détections qui s’exécutent après la remise. Il est lié à une action de remise. Ce champ a été ajouté pour donner un aperçu de l’action effectuée lorsqu’un message problématique est détecté. Voici les valeurs possibles de l’emplacement de remise :

- **Boîte de réception ou dossier** : l’e-mail se trouve dans la boîte de réception ou un dossier (selon vos règles de messagerie).
- **Local ou externe** : la boîte aux lettres n’existe pas sur le cloud, mais elle est locale.
- **Dossier indésirable** : l’e-mail se trouve dans le dossier Courrier indésirable d’un utilisateur.
- **Dossier Éléments supprimés** : l’e-mail se trouve dans le dossier Éléments supprimés d’un utilisateur.
- **Mise en quarantaine** : e-mail en quarantaine et non dans la boîte aux lettres d’un utilisateur.
- **Échec** : l’e-mail n’a pas pu atteindre la boîte aux lettres.
- **Supprimé** : l’e-mail est perdu quelque part dans le flux de courrier.

### <a name="view-the-timeline-of-your-email"></a>Afficher la chronologie de votre e-mail

**Email Chronologie** est un champ de l’Explorateur de menaces qui facilite la chasse pour votre équipe des opérations de sécurité. Lorsque plusieurs événements se produisent en même temps ou presque sur un e-mail, ces événements s’affichent dans un affichage chronologie. Certains événements qui se produisent après la remise du courrier électronique sont capturés dans la colonne **Actions spéciales** . La combinaison d’informations provenant de la chronologie d’un e-mail avec toutes les actions spéciales effectuées après la remise donne aux administrateurs un aperçu des stratégies et de la gestion des menaces (par exemple, l’emplacement où le courrier a été routée et, dans certains cas, l’évaluation finale).

> [!IMPORTANT]
> Passez à une rubrique de correction [ici](remediate-malicious-email-delivered-office-365.md).

## <a name="related-topics"></a>Voir aussi

[Corriger les courriers malveillants remis dans Office 365](remediate-malicious-email-delivered-office-365.md)

[Microsoft Defender pour Office 365](office-365-ti.md)

[Protection contre les menaces dans Office 365](protect-against-threats.md)

[Afficher les rapports pour Defender pour Office 365](view-reports-for-mdo.md)
