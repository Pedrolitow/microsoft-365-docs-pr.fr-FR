---
title: Affichages des campagnes dans Office 365 - Protection avancée contre les menaces
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Découvrez Campaign Views dans Office 365 - Protection avancée contre les menaces.
ms.openlocfilehash: 40eab14dff8d0c51a35bfbc7a04365a5a025e207
ms.sourcegitcommit: 08a4ee7765f3eba42f0c037c5c564c581e45df3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "42637327"
---
# <a name="campaign-views-in-office-365-atp"></a>Campaign Views dans Office 365 - Protection avancée contre les menaces

Campaign Views est une fonctionnalité de la protection avancée contre les menaces (ATP) dans le Centre de sécurité et de conformité Office 365 qui identifie et catégorise les attaques par hameçonnage dans le service. Campaign Views permet d’effectuer les opérations suivantes :

- Examiner et répondre efficacement aux attaques par hameçonnage.

- Mieux comprendre l’étendue de l’attaque.

- Afficher la valeur pour les décideurs.

Campaign Views vous permet de voir la présentation d’une attaque plus rapidement et plus complètement que n’importe quel autre utilisateur.

## <a name="what-is-a-campaign"></a>Qu’est-ce qu’une campagne ?

Une campagne est une attaque par e-mail coordonné contre une ou plusieurs organisations. Les attaques par courrier électronique qui volent les informations d’identification et les données d’entreprise sont un secteur important et lucratif. À mesure que les technologies augmentent pour empêcher les attaques, les agresseurs modifient leurs méthodes afin de garantir une réussite continue.

Microsoft exploite les grandes quantités de données anti-hameçonnage, anti-courrier indésirable et anti-programme malveillant dans l’ensemble du service Office 365 pour vous aider à identifier les campagnes. Nous analysons et classifions les informations d’attaque en fonction de plusieurs facteurs. Par exemple :

- **Sources d’attaque** : adresses IP sources et domaines de l’e-mail de l’expéditeur.

- **Propriétés du message d’attaque** : le contenu, le style et le ton des messages d’attaques.

- **Destinataires d’attaques** : domaines de destinataires, fonctions de tâche de destinataire (administrateurs, cadres, etc.), types d’entreprise (grand, petit, public, privé, etc.) et industries.

- **Charge utile d’attaque**: liens malveillants, pièces jointes ou autres charges utiles dans les messages d’attaque.

Une campagne peut être à courte durée de vie ou peut s’étendre sur plusieurs jours, semaines ou mois avec des périodes actives et inactives. Une campagne peut être lancée par rapport à votre organisation, ou votre organisation peut faire partie d’une campagne plus importante sur plusieurs sociétés.

## <a name="campaign-views-the-office-365-security--compliance-center"></a>Campaign Views dans le Centre de sécurité et conformité Office 365

Les vues de campagne sont disponibles dans le [Centre de sécurité & conformité](https://protection.office.com) aux **campagnes**de **gestion** \> des menaces.

![Vue d’ensemble des campagnes dans la Centre de sécurité et conformité](../../media/campaigns-overview.png)

Vous pouvez également accéder à la vue campagnes à partir de :

- **Threat management** \> **Explorer** \> **View** Affichage \> des **campagnes marketing** dans l’Explorateur de gestion des menaces

- **Threat management** \> **Explorer** Explorateur \> de gestion des menaces **Afficher** \> **toutes les** \> **campagnes** de messagerie

> [!TIP]
> Si aucune donnée de campagne n’apparaît, essayez de modifier la plage de dates.

La page vue d’ensemble présente les informations suivantes sur la campagne :

- **Nom**

- **Exemple d’objet** : la ligne d’objet de l’un des messages de la campagne. Notez que tous les messages de la campagne n’auront pas nécessairement le même objet.

- **Type**: actuellement, cette valeur est toujours **hameçon**.

- **Sous-type** : s’il est disponible, il s’agit de la marque faisant l’objet d’un hameçonnage par cette campagne. Lorsque la détection est pilotée par la technologie ATP, le préfixe **ATP** est ajouté à la valeur de sous-type.

- **Destinataires** : nombre d’utilisateurs qui ont été ciblés par cette campagne.

- **Boîte de réception**: nombre d’utilisateurs ayant reçu des messages de cette campagne dans leur boîte de réception (non remis au courrier indésirable).

- **Clic**: nombre d’utilisateurs sur lesquels l’utilisateur a cliqué sur l’URL dans le message de hameçonnage.

- **Cliquez sur taux**: pourcentage tel que calculé par «**boîte de réception**sur laquelle l'**utilisateur a cliqué** / ». Cette valeur est un indicateur de l’efficacité de la campagne et indique si les destinataires ont pu identifier le message en tant qu’hameçonnage et éviter de cliquer sur l’URL de la charge utile.

- **Consulté**le nombre d’utilisateurs qui l’ont fait par le biais du site Web de charge utile. S’il y a des valeurs de **clic** , mais que les liens fiables bloquent l’accès au site Web, cette valeur est égale à zéro.

Lorsque vous cliquez sur le nom d’une campagne, les détails de la campagne s’affichent dans une fenêtre mobile.

## <a name="campaign-details"></a>Détails de la campagne

Dans la vue Détails de la campagne, de nombreuses informations sont disponibles sur la campagne :

- Informations sur la campagne :

  - **ID**: identificateur unique de la campagne.

  - **Commencé** et **terminé** : le filtre de la plage de dates que vous avez sélectionné.

  - **Impact**: les données suivantes pour le filtre de plage de dates que vous avez sélectionné :
  
    - Nombre total de destinataires.

    - Nombre de messages qui ont reçu la boîte de réception (c’est-à-dire remis dans la boîte de réception, et non du courrier indésirable).

    - Le nombre d’utilisateurs sur lesquels l’utilisateur a cliqué dans le message de hameçonnage.

    - Howe nombre d’utilisateurs visitaient l’URL.

  - Chronologie de l’activité de la campagne : lorsque la campagne a commencé et se termine et que le volume de messages s’affiche au fil du temps.

### <a name="campaign-flow"></a>Flux de la campagne

Des informations importantes sur la campagne sont présentées dans un diagramme de flux horizontal (appelé diagramme de _Sankey_) dans la section **Flux**. Ces détails vous aideront à comprendre les éléments de la campagne et l’impact potentiel au sein de votre organisation.

![Détails de la campagne ne contenant pas d’URL d’utilisateur](../../media/campaign-details-no-recipient-actions.png)

Si vous pointez sur une bande horizontale dans le diagramme, vous pouvez voir le nombre de messages associés (par exemple, les messages d’une adresse IP source particulière, les messages provenant de l’adresse IP source en utilisant le domaine d’expéditeur spécifié, etc.).

Le diagramme contient les informations suivantes :

- **Adresses IP de l’expéditeur**

- **Domaines de l’expéditeur**

- **Filtrer les verdicts**: les valeurs indiquées ici sont liées aux verdicts de hameçonnage et de filtrage du courrier indésirable disponibles, comme décrit dans [les en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md). Les valeurs disponibles sont décrites dans le tableau suivant :

  |Valeur|Verdict du filtre de courrier indésirable|Description|
  |:-----|:-----|:-----|
  | **Autorisé**|`SFV:SKN` <br/><br/> `SFV:SKI`|Le message a été marqué comme n’étant pas un courrier indésirable et/ou a ignoré le filtrage avant d’être évalué par le filtrage du courrier indésirable (par exemple, par une règle de flux de messagerie, également appelée règle de transport).<br/><br/>Le message a ignoré le filtrage du courrier indésirable pour d’autres raisons (par exemple, l’expéditeur et le destinataire semblent être dans la même organisation).|
  |**Blocked**|`SFV:SKS`|Le message a été marqué comme courrier indésirable avant d’être évalué par le filtrage du courrier indésirable (par exemple, par une règle de flux de messagerie).|
  |**Détecté**|`SFV:SPM`|Le message a été marqué comme courrier indésirable par le filtrage du courrier indésirable.|
  |**Non détecté**|`SFV:NSPM`|Le message a été marqué comme non courrier indésirable par le filtrage du courrier indésirable.|
  |**A**|`SFV:SKQ`|Le message a ignoré le filtrage du courrier indésirable, car il a été mis en quarantaine.|
  |**Autoriser le client**<sup>\*</sup>|`SFV:SKA`|Le message a ignoré le filtrage du courrier indésirable en raison des paramètres de stratégie de blocage du courrier indésirable (par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou le domaine autorisé).|
  |**Bloc de locataire**<sup>\*\*</sup>|`SFV:SKA`|Le message a été bloqué par le filtrage du courrier indésirable en raison des paramètres de stratégie de blocage du courrier indésirable (par exemple, l’expéditeur se trouvait dans la liste des expéditeurs autorisés ou le domaine autorisé).|
  |**Autorisation de l’utilisateur**<sup>\*</sup>|`SFV:SFE`|Le message a ignoré le filtrage du courrier indésirable, car l’expéditeur se trouvait dans la liste des expéditeurs approuvés d’un utilisateur dans Outlook.|
  |**Bloc utilisateur**<sup>\*\*</sup>|`SFV:BLK`|Le message a été bloqué par le filtrage du courrier indésirable, car l’expéditeur se trouvait dans la liste des expéditeurs bloqués d’un utilisateur dans Outlook.|
  |**ZAP**|s/o|La [purge automatique à zéro heure (ZAP)](zero-hour-auto-purge.md) a effectué une action sur le message remis en fonction de vos paramètres de stratégie anti-courrier indésirable (déplacés vers le dossier courrier indésirable ou mis en quarantaine).|

  <sup>\*</sup>Examinez vos stratégies de blocage du courrier indésirable, car le message autorisé aurait probablement été bloqué par le service.

  <sup>\*\*</sup>Examinez vos stratégies de blocage du courrier indésirable, car ces messages doivent être mis en quarantaine et non remis.

- **Emplacements de remise**: vous souhaiterez peut-être examiner les messages qui ont été remis aux destinataires (soit dans la boîte de réception, soit dans le dossier courrier indésirable), même si les utilisateurs n'ont pas cliqué sur l'URL de la charge utile dans le message. Vous pouvez également supprimer les messages mis en quarantaine en quarantaine. Pour plus d’informations, consultez la rubrique [mise en quarantaine des messages électroniques dans Office 365](quarantine-email-messages.md).

  - **Dossier supprimé**

  - **Raccroché**

  - **External**: le destinataire est situé dans votre organisation de messagerie locale.

  - **Échec**

  - **Renvoyé**

  - **Boîte de réception**

  - **Dossier Courrier indésirable**

  - **Mise en quarantaine**

  - **Unknown**

> [!NOTE]
> Dans toutes les couches contenant plus de 10 éléments, les 10 premiers éléments sont affichés, tandis que les autres sont regroupés dans les **autres**.

#### <a name="url-clicks"></a>Clics d’URL

Lorsqu’un message d’hameçonnage est remis à un destinataire (dans la boîte de réception ou dans le dossier courrier indésirable), il y a toujours un risque que l’utilisateur clique sur l’URL de la charge utile. Le fait de ne pas cliquer sur l’URL dans un message remis est une petite mesure de succès, mais vous devez déterminer pourquoi le message de hameçonnage a été remis à sa boîte aux lettres.

Si un utilisateur a cliqué sur l’URL de la charge utile dans le message d’hameçonnage, les actions sont affichées dans la zone de **clics sur l’URL** du diagramme dans la vue Détails de la campagne.

- **Autorisé**

- **BlockPage**: le destinataire a cliqué sur l’URL de charge utile, mais son accès au site Web malveillant a été bloqué par les stratégies de [liens fiables ATP](atp-safe-links.md) de votre organisation.

- **BlockPageOverride**: le destinataire a cliqué sur l’URL de charge utile dans le message, les liens fiables ATP ont essayé de les arrêter, mais ils ont été autorisés à remplacer le bloc. Vous devez examiner vos [stratégies de liens fiables](set-up-atp-safe-links-policies.md) pour savoir pourquoi les utilisateurs sont autorisés à remplacer le verdict des liens fiables et continuer à accéder au site Web malveillant.

- **PendingDetonationPage**: les pièces jointes de protection avancée contre les menaces sont en cours d’ouverture de l’URL de charge utile dans un environnement d’ordinateur virtuel et de l’affichage de ce qui se passe.

- **PendingDetonationPageOverride**: le destinataire a été autorisé à remplacer le processus de détonation de charge utile et à ouvrir l’URL sans attendre les résultats.

### <a name="tabs"></a>Onglets

La vue Détails de la campagne comporte plusieurs onglets qui vous permettent d’approfondir l’examen de la campagne.

- **Clics**sur l’URL : si les utilisateurs ne cliquent pas sur l’URL de la charge utile dans le message d’hameçonnage, cette section est vide. Si un utilisateur a pu cliquer sur l’URL, les valeurs suivantes sont remplies :

  - **Utilisateur**<sup>\*</sup>

  - **URL**<sup>\*</sup>

  - **Cliquez sur heure**

  - **Cliquez sur Action**

- **Adresses IP de l’expéditeur**

  - **IP de l’expéditeur**<sup>\*</sup>

  - **Nombre total**

  - **Nombre de la boîte de réception**

  - **Nombre de bloqués**

  - **SPF transmis**: l’expéditeur a été authentifié par [Sender Policy Framework (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md). Un expéditeur qui ne passe pas la validation SPF indique que l’expéditeur n’est pas authentifié, ou que le message usurpe l’identité d’un expéditeur légitime.

- **Expéditeurs**

  - **Expéditeur**: il s’agit de l’adresse de l’expéditeur réelle dans la commande SMTP Mail from, qui n’est pas nécessairement l’adresse de messagerie de l’expéditeur que les utilisateurs voient dans leurs clients de messagerie.

  - **Nombre total**

  - **Boîte de réception**

  - **Pas de boîte de réception**

  - **DKIM transmis**: l’expéditeur a été authentifié par des [clés de domaine identifiées par des clés de domaine (DKIM)](support-for-validation-of-dkim-signed-messages.md). Un expéditeur qui ne passe pas la validation DKIM indique que l’expéditeur n’est pas authentifié, ou que le message usurpe l’identité d’un expéditeur légitime.

  - **DMARC réussi**: l’expéditeur a été authentifié par [l’authentification de message basée sur un domaine, la création de rapports et la conformité (DMARC)](use-dmarc-to-validate-email.md). Un expéditeur qui ne réussit pas la validation DMARC indique que l’expéditeur n’est pas authentifié ou que le message usurpe l’identité d’un expéditeur légitime.

- **Charge utile**

  - **URL**<sup>\*</sup>

  - **Nombre total**

<sup>\*</sup> Le fait de cliquer sur cette valeur ouvre un nouveau menu mobile qui contient plus de détails sur l’élément spécifié (utilisateur, URL, etc.) au-dessus de la vue Détails de la campagne. Pour revenir à la vue Détails de la campagne, cliquez sur **Terminé** dans la nouvelle fenêtre mobile.

### <a name="buttons"></a>Boutons

Les boutons de la vue Détails de la campagne vous permettent d’utiliser le Power Explorer pour approfondir l’examen de la campagne.

- **Explorer la campagne**: ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de la valeur **ID de campagne** comme filtre de recherche.

- **Explorer les messages**de la boîte de réception : ouvre un nouvel onglet de recherche de l’Explorateur de menaces à l’aide de l' **ID de campagne** et de l' **emplacement de remise : boîte de réception** comme filtre de recherche.
