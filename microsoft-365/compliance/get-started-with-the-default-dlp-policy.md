---
title: Prise en main de la stratégie DLP par défaut
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e0ada764-6422-4b44-9472-513bed04837b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment utiliser le rapport pour affiner la stratégie de protection contre la perte de données par défaut de votre organisation.
ms.openlocfilehash: d47568f009745edaa8205ce65b4de9b481f58139
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641491"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Prise en main de la stratégie DLP par défaut

Avant même de créer votre première stratégie de Protection contre la perte de données Microsoft Purview (DLP), DLP vous aide à protéger vos informations sensibles avec une stratégie par défaut. Cette stratégie par défaut et sa recommandation (illustrée ci-dessous) permettent de sécuriser votre contenu sensible en vous avertissant lorsque des e-mails ou des documents contenant un numéro de carte de crédit ont été partagés avec une personne externe à votre organisation. Vous verrez cette recommandation sur la page **d’accueil** du portail de conformité Microsoft Purview. 
  
Vous pouvez utiliser ce widget pour afficher rapidement quand et combien d’informations sensibles ont été partagées, puis affiner la stratégie DLP par défaut en un ou deux clics. Vous pouvez également modifier la stratégie DLP par défaut à tout moment, car elle est entièrement personnalisable. Notez que si vous ne voyez pas la recommandation au début, essayez de cliquer sur **+Plus** en bas de la section **Recommandé pour vous** . 
  
![Widget nommé Protéger davantage le contenu partagé.](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Afficher le rapport et affiner la stratégie DLP par défaut

Lorsque le widget vous indique que les utilisateurs ont partagé des informations sensibles avec des personnes extérieures à votre organisation, **choisissez Affiner la stratégie DLP** en bas. 
  
Le rapport détaillé vous indique quand et combien de contenu contenant des numéros de carte de crédit ont été partagés au cours des 30 derniers jours. Notez que l’affichage des correspondances de règle peut prendre jusqu’à 48 heures dans le widget.
  
Pour protéger les informations sensibles, la stratégie DLP par défaut :
  
- Détecte quand le contenu dans Exchange, SharePoint et OneDrive qui contient au moins un numéro de carte de crédit est partagé avec des personnes extérieures à votre organisation.
    
- Affiche un conseil de stratégie et envoie une notification par e-mail aux utilisateurs lorsqu’ils tentent de partager ces informations sensibles avec des personnes extérieures à votre organisation. Pour plus d’informations sur ces options, consultez [Envoyer des notifications par e-mail et afficher des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md).
    
- Génère des rapports d’activité détaillés pour vous permettre de suivre les personnes qui ont partagé le contenu avec des personnes extérieures à votre organisation et quand elles l’ont fait. Vous pouvez utiliser les [rapports DLP et les](view-the-dlp-reports.md) [données du journal d’audit](search-the-audit-log-in-security-and-compliance.md) (où **DLP** **d’activité** = ) pour afficher ces informations.
    
Pour affiner rapidement la stratégie DLP par défaut, vous pouvez choisir de l’avoir :
  
- Envoyez-vous un e-mail de rapport d’incident lorsque les utilisateurs partagent ces informations sensibles avec des personnes extérieures à votre organisation.
    
- Ajoutez d’autres utilisateurs au rapport d’incident d’e-mail.
    
- Bloquez l’accès au contenu contenant les informations sensibles, mais autorisez l’utilisateur à remplacer et partager ou envoyer s’il le faut.
    
Pour plus d’informations sur les rapports d’incidents ou la restriction de l’accès, consultez [les informations de référence sur la protection contre la perte de données](data-loss-prevention-policies.md).
  
Si vous souhaitez modifier ces options ultérieurement, vous pouvez modifier la stratégie DLP par défaut à tout moment . Consultez la section suivante.
  
![Paramètres du widget nommé Protéger davantage le contenu partagé.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Modifier la stratégie DLP par défaut

Cette stratégie est nommée **stratégie DLP par défaut** et apparaît sous **Protection contre la perte de données** **sur la page** Stratégie du portail de conformité Microsoft Purview. 
  
Cette stratégie est entièrement personnalisable, identique à toute stratégie DLP que vous créez vous-même à partir de zéro. Vous pouvez également désactiver ou supprimer la stratégie, afin que vos utilisateurs ne reçoivent plus de conseils de stratégie ou de notifications par e-mail.
  
![Stratégie DLP nommée stratégie DLP par défaut.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Lorsque le widget s’affiche et n’apparaît pas

Le widget nommé **Protéger davantage le contenu partagé** apparaît dans la section **Recommandé pour vous** de la page **d’accueil** du portail de conformité Microsoft Purview. 
  
Ce widget s’affiche uniquement quand :
  
- Il n’existe aucune stratégie de protection contre la perte de données dans le centre d’administration portail de conformité Microsoft Purview ou Exchange. Ce widget est destiné à vous aider à bien démarrer avec DLP. Il n’apparaît donc pas si vous disposez déjà de stratégies DLP.
    
- Le contenu contenant au moins une carte de crédit a été partagé avec une personne externe à votre organisation au cours des 30 derniers jours.
    
Notez que les correspondances de règle peuvent prendre jusqu’à 48 heures pour être disponibles pour le widget. Par conséquent, une fois les informations sensibles partagées en externe détectées, l’affichage de la recommandation peut prendre jusqu’à deux jours.
  
Enfin, après avoir utilisé le widget pour affiner la stratégie DLP par défaut, le widget disparaît de la page **d’accueil** . 
  

