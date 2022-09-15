---
title: Gérer les incidents dans Microsoft 365 Defender
description: Découvrez comment attribuer, mettre à jour l’état,
keywords: incidents, incidents, analyse, réponse, alertes, alertes corrélées, assigner, mettre à jour, état, gérer, classification, microsoft, 365, m365
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 09cc82d196110aa1dcf1e6e62e93e5945c9136b1
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67709088"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Gérer les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La gestion des incidents est essentielle pour s’assurer que les incidents sont nommés, affectés et étiquetés pour optimiser le temps dans votre flux de travail d’incident et pour contenir et traiter plus rapidement les menaces.

Vous pouvez gérer les incidents à partir **d’incidents & alertes > incidents** lors du lancement rapide du portail Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Voici comment gérer vos incidents :

- [Modifier le nom de l’incident](#edit-the-incident-name)
- [Ajouter des balises d’incident](#add-incident-tags)
- [Affecter l’incident à un compte d’utilisateur](#assign-an-incident)
- [Les résoudre](#resolve-an-incident)
- [Spécifier sa classification](#specify-the-classification)
- [Ajouter des commentaires](#add-comments)

Vous pouvez gérer les incidents à partir du volet **Gérer les incidents** pour un incident. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Volet Gérer les incidents dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Vous pouvez afficher ce volet à partir du lien **Gérer l’incident** sur les éléments suivants :

- Volet Propriétés d’un incident dans la file d’attente des incidents.
- **Page récapitulative** d’un incident.

Dans les cas où vous souhaitez déplacer des alertes d’un incident à un autre, vous pouvez également le faire à partir de l’onglet **Alertes** , créant ainsi un incident plus grand ou plus petit qui inclut toutes les alertes pertinentes.

## <a name="edit-the-incident-name"></a>Modifier le nom de l’incident

Microsoft 365 Defender attribue automatiquement un nom en fonction d’attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident. Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*

Vous pouvez modifier le nom de l’incident à partir du champ **Nom** de l’incident dans le volet **Gérer les incidents** .

> [!NOTE]
> Les incidents qui existaient avant le lancement de la fonctionnalité de nommage automatique des incidents conserveront leur nom.

## <a name="add-incident-tags"></a>Ajouter des balises d’incident

Vous pouvez ajouter des balises personnalisées à un incident, par exemple pour marquer un groupe d’incidents avec une caractéristique commune. Vous pouvez filtrer ultérieurement la file d’attente des incidents pour tous les incidents qui contiennent une balise spécifique.

Lorsque vous commencez à taper, vous avez la possibilité de sélectionner dans une liste de balises précédemment utilisées et sélectionnées.

## <a name="assign-an-incident"></a>Affecter un incident

Si aucun incident n’a encore été attribué, vous pouvez sélectionner la zone **Affecter à** et spécifier le compte d’utilisateur. Pour réaffecter un incident, supprimez le compte d’affectation actuel en sélectionnant le « x » en regard du nom du compte, puis sélectionnez la zone **Affecter à** . L’affectation de la propriété d’un incident affecte la même propriété à toutes les alertes qui lui sont associées.

Vous pouvez obtenir la liste des incidents qui vous sont attribués en filtrant la file d’attente des incidents. 

1. Dans la file d’attente d’incidents, sélectionnez **Filtres**.
2. Dans la section **Affectation d’incident** , **désactivez Sélectionner tout** et sélectionnez **Affecté à moi**.
3. Sélectionnez **Appliquer**, puis fermez le volet **Filtres** .

Vous pouvez ensuite enregistrer l’URL résultante dans votre navigateur en tant que signet pour afficher rapidement la liste des incidents qui vous sont attribués.

## <a name="resolve-an-incident"></a>Résoudre un incident

Si l’incident a été corrigé, sélectionnez **Résoudre l’incident** pour déplacer le bouton bascule vers la droite. Notez que la résolution d’un incident résout également toutes les alertes liées et actives liées à l’incident.

Un incident qui n’est pas résolu s’affiche comme **actif**.

## <a name="specify-the-classification"></a>Spécifier la classification

Dans le champ **Classification** , vous spécifiez si l’incident est :

- **Non défini** (valeur par défaut).
- **Vrai positif** avec un type de menace. Utilisez cette classification pour les incidents qui indiquent avec précision une menace réelle. Spécifier le type de menace permet à votre équipe de sécurité de voir les modèles de menace et d’agir pour défendre votre organisation contre celles-ci.
- **Activité informationnelle attendue** avec un type d’activité. Utilisez les options de cette catégorie pour classer les incidents pour les tests de sécurité, l’activité de l’équipe rouge et le comportement inhabituel attendu des applications et des utilisateurs approuvés.
- **Les faux positifs** pour les types d’incidents que vous déterminez peuvent être ignorés, car ils sont techniquement inexacts ou trompeurs.

La classification des incidents et la spécification de leur état et de leur type permettent d’ajuster Microsoft 365 Defender pour fournir une meilleure détermination de la détection au fil du temps.

Regardez cette courte vidéo pour découvrir comment utiliser la classification pour améliorer l’efficacité du triage.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LHJq]

## <a name="add-comments"></a>Ajouter des commentaires

Vous pouvez ajouter plusieurs commentaires à un incident avec le champ **Commentaire** . Chaque commentaire est ajouté aux événements historiques de l’incident. Vous pouvez voir les commentaires et l’historique d’un incident à partir du lien **Commentaires et historique** sur la page **Résumé** .

## <a name="next-steps"></a>Prochaines étapes

Pour les nouveaux incidents, commencez votre [enquête](investigate-incidents.md).

Pour les incidents in-process, poursuivez votre [enquête](investigate-incidents.md).

Pour les incidents résolus, effectuez une [révision post-incident](first-incident-post.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Enquêter sur des incidents](investigate-incidents.md)
