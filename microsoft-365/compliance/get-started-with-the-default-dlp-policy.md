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
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: e0ada764-6422-4b44-9472-513bed04837b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment utiliser le rapport pour affiner la stratégie de protection contre la perte de données (DLP) par défaut de votre organisation.
ms.openlocfilehash: 95c4ebae431bea1db033826459ca1595614ab5cb
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182312"
---
# <a name="get-started-with-the-default-dlp-policy"></a>Prise en main de la stratégie DLP par défaut

Avant même de créer votre première stratégie de protection contre la perte de données (DLP), la protection contre la perte de données contribue à protéger vos informations sensibles avec une stratégie par défaut. Cette stratégie par défaut et ses recommandations (indiquées ci-dessous) permettent de sécuriser votre contenu sensible en vous notifiant lorsque des messages électroniques ou des documents contenant un numéro de carte de crédit ont été partagés avec une personne extérieure à votre organisation. Vous verrez cette recommandation sur la page **d’accueil** du Centre de conformité &amp; de la sécurité. 
  
Vous pouvez utiliser ce widget pour afficher rapidement quand et combien d’informations sensibles ont été partagées, puis affiner la stratégie DLP par défaut en un ou deux clics. Vous pouvez également modifier la stratégie DLP par défaut à tout moment, car elle est entièrement personnalisable. Notez que si vous ne voyez pas la recommandation au début, essayez de cliquer sur **+Plus** en bas de la section **Recommandé pour vous.** 
  
![Widget nommé « Protéger davantage le contenu partagé ».](../media/2bae6dbc-cc92-4f35-b54c-c36e60226b5b.png)
  
## <a name="view-the-report-and-refine-the-default-dlp-policy"></a>Afficher le rapport et affiner la stratégie DLP par défaut

Lorsque le widget vous indique que les utilisateurs ont partagé des informations sensibles avec des personnes extérieures à votre organisation, sélectionnez Affiner la stratégie **DLP** en bas. 
  
Le rapport détaillé vous indique quand et combien de contenu contenant des numéros de carte de crédit ont été partagés au cours des 30 derniers jours. Notez que l’exposition des correspondances de règles dans le widget peut prendre jusqu’à 48 heures.
  
Pour protéger les informations sensibles, la stratégie DLP par défaut :
  
- Détecte le moment où le contenu Exchange, SharePoint et OneDrive contenant au moins un numéro de carte de crédit est partagé avec des personnes extérieures à votre organisation.
    
- Affiche un conseil de stratégie et envoie une notification par courrier électronique aux utilisateurs lorsqu’ils tentent de partager ces informations sensibles avec des personnes extérieures à votre organisation. Pour plus d’informations sur ces options, voir Envoyer des notifications par courrier électronique et afficher des conseils de stratégie [pour les stratégies DLP.](use-notifications-and-policy-tips.md)
    
- Génère des rapports d’activité détaillés afin que vous pouvez suivre des éléments tels que les personnes qui ont partagé le contenu avec des personnes extérieures à votre organisation et quand elles l’ont fait. Vous pouvez utiliser les rapports [DLP](view-the-dlp-reports.md) et les données du journal [d’audit](search-the-audit-log-in-security-and-compliance.md) (où **Activité**  =  **DLP**) pour voir ces informations.
    
Pour affiner rapidement la stratégie DLP par défaut, vous pouvez choisir de l’utiliser :
  
- Envoyez-vous un e-mail de rapport d’incident lorsque les utilisateurs partagent ces informations sensibles avec des personnes extérieures à votre organisation.
    
- Ajoutez d’autres utilisateurs au rapport d’incident de courrier électronique.
    
- Bloquez l’accès au contenu contenant les informations sensibles, mais autorisez l’utilisateur à remplacer, partager ou envoyer s’il le faut.
    
Pour plus d’informations sur les rapports d’incident ou la restriction de l’accès, consultez la référence [de protection contre la perte de données.](data-loss-prevention-policies.md)
  
Si vous souhaitez modifier ces options ultérieurement, vous pouvez modifier la stratégie DLP par défaut à tout moment (voir la section suivante).
  
![Paramètres widget nommé Protéger davantage le contenu partagé.](../media/dad30a84-2715-4c0a-a5c5-44d85492363e.png)
  
## <a name="edit-the-default-dlp-policy"></a>Modifier la stratégie DLP par défaut

Cette stratégie est nommée **Stratégie DLP par défaut** et apparaît sous Protection contre la perte de données dans la page Stratégie du Centre de conformité de   &amp; sécurité. 
  
Cette stratégie est entièrement personnalisable, comme toute stratégie DLP que vous créez vous-même à partir de zéro. Vous pouvez également désactiver ou supprimer la stratégie afin que vos utilisateurs ne reçoivent plus de conseils de stratégie ou de notifications par courrier électronique.
  
![Stratégie DLP nommée Stratégie DLP par défaut.](../media/260731e8-4d57-4c98-abec-07b052ec48d5.png)
  
## <a name="when-the-widget-does-and-does-not-appear"></a>Lorsque le widget s’affiche et n’apparaît pas

Le widget nommé **Protéger davantage le** contenu partagé apparaît dans la section Recommandé pour vous de la page **d’accueil** du Centre de conformité de la  &amp; sécurité. 
  
Ce widget apparaît uniquement lorsque :
  
- Il n’existe aucune stratégie de protection contre la perte de données dans le Centre de conformité de sécurité &amp; Exchange centre d’administration. Ce widget est destiné à vous aider à démarrer avec DLP, afin qu’il n’apparaisse pas si vous avez déjà des stratégies DLP.
    
- Le contenu contenant au moins une carte de crédit a été partagé avec une personne extérieure à votre organisation au cours des 30 derniers jours.
    
Notez que les correspondances de règles peuvent prendre jusqu’à 48 heures pour être disponibles pour le widget. Ainsi, une fois les informations sensibles partagées en externe détectées, l’apparition de la recommandation peut prendre jusqu’à deux jours.
  
Enfin, une fois que vous avez utilisé le widget pour affiner la stratégie DLP par défaut, le widget disparaît de la page **d’accueil.** 
  

