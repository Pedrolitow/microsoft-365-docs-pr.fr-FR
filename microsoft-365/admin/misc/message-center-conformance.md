---
title: Métadonnées de conformité pour les publications du Centre de messages
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Obtenir une vue d’ensemble des métadonnées de conformité pour les publications du Centre de messages
ms.openlocfilehash: 1205c5429427741f6383fd48205730db1ccbfc98
ms.sourcegitcommit: 1f4c51d022d1cfb6c194bf0f0af9c2841c781d68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2022
ms.locfileid: "68573942"
---
# <a name="conformance-metadata-for-message-center-posts"></a>Métadonnées de conformité pour les publications du Centre de messages

> [!IMPORTANT]
> Ce document privé s’adresse uniquement aux utilisateurs de métadonnées change management: Conformance. Ne partagez pas ce document au-delà de ceux qui sont directement impliqués dans le pilote.

Lors de la planification de nouvelles fonctionnalités ou déploiements de services, vous souhaitez comprendre et évaluer les modifications en fonction de votre secteur d’activité, de votre région et de votre pays. Nous avons entendu vos commentaires lorsqu’il n’y a pas suffisamment d’informations de conformité sur une fonctionnalité nouvelle ou changeante, vous devez effectuer vos propres recherches sur la fonctionnalité ou contacter le Programme de conformité avec des questions.  

Dans ce programme pilote, nous souhaitons fournir de manière proactive des métadonnées pour les fonctionnalités et services Microsoft 365 nouveaux et mis à jour. Notre objectif est de vous aider à évaluer efficacement vos exigences de conformité et à vous aider à prendre des décisions en matière d’adoption et de gestion des changements.  

Par exemple, si, pour une fonctionnalité, les métadonnées ont les valeurs suivantes, la décision d’adoption des fonctionnalités doit être rapide.  

- Les données client sont stockées ? **Non**

- Passer au stockage de données client ? **Non**

- Modifications apportées au flux de données existant ? **Non**

- La fonctionnalité s’intègre aux services tiers ? **Non**

> [!NOTE]
> La liste ci-dessus est légèrement différente de ce que vous avez vu précédemment dans les publications de conformité pilote. Nous avons mis à jour la liste en fonction des commentaires que nous avons reçus des clients pilotes.

Pour les fonctionnalités où les métadonnées sont différentes de la liste ci-dessus, le billet du Centre de messages peut vous fournir de la documentation.

## <a name="understanding-conformance-metadata"></a>Présentation des métadonnées de conformité

|**Nom des métadonnées**|**Valeurs**|**Définition et questions posées**|**Exemple : Oui**|**Exemple : Non**|
|---|---|---|---|
|**Les données client sont stockées**|Oui/Non|Cette modification stocke-t-elle ou traite-t-elle les nouvelles données nettes (classées en tant que données client ou personnelles) qui n’ont pas été précédemment stockées ou traitées par le service/version précédente de cette fonctionnalité ?|Les enregistrements des réunions Teams capturant et collectant des données client sont maintenant stockés.|La fonctionnalité MAU (Monthly Active Users) du service Message Center affiche les utilisateurs actifs mensuels du service agrégé pour un ID de locataire qui n’est pas classé en tant que données client ou personnelle.|
|**Passer au stockage de données client**|Oui/Non|Cette modification utilise-t-elle un service nouveau ou différent pour stocker des données ?|Enregistrements de réunions Teams capturant/collectant des données/du contenu client, et est maintenant stocké.|Réactions étendues dans Teams. Extension des réactions aux messages dans Teams vers un ensemble plus grand. Les réactions les plus récentes stockées sont des données client. Toutefois, la façon dont les données sont stockées ou traitées ne change pas.|
|**Modifications apportées au flux de données existant**|Oui/Non|Cette fonctionnalité traite-t-elle les données via un pipeline de traitement nouveau ou différent ? <br> Ou <br> La fonctionnalité étend-elle simplement un pipeline de traitement existant à des données plus récentes ou expose-t-elle des données déjà exposées sur une surface à une autre ? (**Réponse = Non**).|Lorsque Bing Entreprise a commencé à utiliser du texte de Word pour l’envoyer à Bing, puis à renvoyer des données à Word, le flux de données a changé.|Le score de productivité utilisé sur la page Insights d’expérience dans le Centre d’administration, les données sont affichées sur une nouvelle surface, mais le stockage et le traitement sont identiques. <br> La réponse suggérée dans les conversations de groupe sur Teams Desktop (une extension de conversations 1:1) n’a pas de nouvelles données nettes. Il s’agit d’une extension du pipeline déjà configuré pour la réponse suggérée dans les conversations 1:1.|
|**La fonctionnalité s’intègre à des services tiers**|Oui/Non|Cette fonctionnalité utilise-t-elle un nouveau service ou une application net (interne ou tiers) que les données client peuvent potentiellement être stockées ou traitées en dehors de Microsoft 365 ?|Bing Entreprise peut recevoir du contenu client sous la forme de données de « recherche » pour présenter à un utilisateur des informations/contenus potentiellement pertinents.|La fonctionnalité utilisateurs actifs mensuels (MAU) du service Message Center affiche les utilisateurs actifs mensuels du service à l’aide du rapport d’utilisation API Graph qui se trouve dans la limite de Microsoft 365.|
|

## <a name="join-the-pilot-program"></a>Participer au programme pilote

Vous pouvez participer en répondant à ce [questionnaire](https://go.microsoft.com/fwlink/p/?linkid=2211581).

Lorsqu’un billet du Centre de messages est remis, vous recevez un billet de centre de messages supplémentaire indiquant : **Informations de conformité supplémentaires pour MC######**. Ce billet contient des métadonnées de conformité supplémentaires. Vous pouvez envoyer des commentaires directement sur le billet supplémentaire ou envoyer un e-mail : MCSHDPMS@Microsoft.com. Vous pouvez également envoyer des commentaires sur le [canal Teams](https://go.microsoft.com/fwlink/p/?linkid=2211676).

> [!NOTE]
> Nous allons commencer par les fonctionnalités de Microsoft Teams, OneDrive Entreprise et SharePoint Online.
