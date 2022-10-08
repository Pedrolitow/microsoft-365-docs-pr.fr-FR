---
title: Microsoft Defender pour Identity alertes de sécurité dans Microsoft 365 Defender
description: Découvrez comment gérer et examiner les alertes de sécurité émises par Microsoft Defender pour Identity dans Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: m365-security
search.appverid: met150
ms.openlocfilehash: bc3e383f2d60e115bd0b2bc995e7ade605f48120
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68080434"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>Alertes de sécurité Defender pour Identity dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique les principes de base de l’utilisation des alertes de sécurité [Microsoft Defender pour Identity](/defender-for-identity) dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Les alertes Defender pour Identity sont intégrées en mode natif dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> avec un format de page d’alerte d’identité dédié. Il s’agit de la première étape du parcours pour [introduire l’expérience de Microsoft Defender pour Identity complète dans Microsoft 365 Defender](/defender-for-identity/defender-for-identity-in-microsoft-365-defender).

La nouvelle page d’alerte d’identité offre Microsoft Defender pour Identity clients une meilleure enrichissement des signaux inter-domaines et de nouvelles fonctionnalités de réponse d’identité automatisée. Il garantit que vous restez sécurisé et contribue à améliorer l’efficacité de vos opérations de sécurité.

L’un des avantages de l’examen des alertes par le biais de [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) est que Microsoft Defender pour Identity alertes sont corrélées avec les informations obtenues à partir de chacun des autres produits de la suite. Ces alertes améliorées sont cohérentes avec les autres formats d’alerte Microsoft 365 Defender provenant de [Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security) et [de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint). La nouvelle page élimine efficacement la nécessité d’accéder à un autre portail de produit pour examiner les alertes associées à l’identité.

Les alertes provenant de Defender pour Identity peuvent désormais déclencher les Microsoft 365 Defender fonctionnalités [d’investigation et de réponse automatisées (AIR),](/microsoft-365/security/defender/m365d-autoir) notamment la correction automatique des alertes et l’atténuation des outils et des processus qui peuvent contribuer à l’activité suspecte.

> [!IMPORTANT]
> Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé à partir de leur emplacement dans le portail Defender pour Identity. Lisez les détails ci-dessous pour découvrir où trouver les fonctionnalités familières et nouvelles.

## <a name="review-security-alerts"></a>Examiner les alertes de sécurité

Les alertes sont accessibles à partir de plusieurs emplacements, notamment la page **Alertes**, la page Incidents, les pages des **appareils** **individuels** et la page **De chasse avancée**. Dans cet exemple, nous allons passer en revue la **page Alertes**.

Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **incidents & alertes**, puis aux **alertes**.

:::image type="content" source="../../media/defender-identity/incidents-alerts.png" alt-text="Élément de menu Alertes" lightbox="../../media/defender-identity/incidents-alerts.png":::

Pour afficher les alertes de Defender pour Identity, sélectionnez **Filtre** en haut à droite, puis sous **Sources** de service, sélectionnez **Microsoft Defender pour Identity**, puis **Appliquer** :

:::image type="content" source="../../media/defender-identity/filter-defender-for-identity.png" alt-text="Filtre des événements Defender pour Identity" lightbox="../../media/defender-identity/filter-defender-for-identity.png":::

Les alertes sont affichées avec des informations dans les colonnes suivantes : **Nom de l’alerte**, **Balises**, **Gravité**, État de **l’investigation**, **État**, **Catégorie**, **Source de détection**, **Ressources impactées**, **Première activité** et **Dernière activité**.

:::image type="content" source="../../media/defender-identity/filtered-alerts.png" alt-text="Événements Defender pour Identity" lightbox="../../media/defender-identity/filtered-alerts.png":::

## <a name="manage-alerts"></a>Gérer des alertes

Si vous cliquez sur le **nom** de l’alerte pour l’une des alertes, vous accédez à la page avec des détails sur l’alerte. Dans le volet gauche, vous verrez un résumé de **ce qui s’est passé** :

:::image type="content" source="../../media/defender-identity/what-happened.png" alt-text="Volet Ce qui s’est passé" lightbox="../../media/defender-identity/what-happened.png":::

Au-dessus de la zone **Ce qui s’est passé** se trouvent les boutons pour les **comptes**, **l’hôte de destination** et l’hôte **source** de l’alerte. Pour les autres alertes, vous pouvez voir des boutons pour plus d’informations sur des hôtes, des comptes, des adresses IP, des domaines et des groupes de sécurité supplémentaires. Sélectionnez l’une d’elles pour obtenir plus de détails sur les entités impliquées.

Dans le volet droit, vous verrez les détails de **l’alerte**. Ici, vous pouvez voir plus de détails et effectuer plusieurs tâches :

- **Classifier cette alerte** : vous pouvez ici désigner cette alerte comme une **alerte True** ou **False**

    :::image type="content" source="../../media/defender-identity/classify-alert.png" alt-text="Page sur laquelle vous pouvez classer une alerte" lightbox="../../media/defender-identity/classify-alert.png":::

- **État de l’alerte** : dans **la classification définie**, vous pouvez classer l’alerte comme **True** ou **False**. Dans **Affecté à**, vous pouvez attribuer l’alerte à vous-même ou la désaffecter.

    :::image type="content" source="../../media/defender-identity/alert-state.png" alt-text="Volet État de l’alerte" lightbox="../../media/defender-identity/alert-state.png":::

- **Détails** de l’alerte : sous **Détails** de l’alerte, vous pouvez trouver plus d’informations sur l’alerte spécifique, suivre un lien vers la documentation sur le type d’alerte, voir l’incident auquel l’alerte est associée, examiner les investigations automatisées liées à ce type d’alerte et voir les appareils et utilisateurs concernés.

   :::image type="content" source="../../media/defender-identity/alert-details.png" alt-text="Page Détails de l’alerte" lightbox="../../media/defender-identity/alert-details.png":::

- **Commentaires & historique** : vous pouvez ici ajouter vos commentaires à l’alerte et afficher l’historique de toutes les actions associées à l’alerte.

    :::image type="content" source="../../media/defender-identity/comments-history.png" alt-text="Page Commentaires & historique" lightbox="../../media/defender-identity/comments-history.png":::

- **Gérer l’alerte** : si vous sélectionnez **Gérer l’alerte**, vous accédez à un volet qui vous permet de modifier les éléments :
  - **État** : vous pouvez choisir **Nouveau**, **Résolu** ou **En cours**.
  - **Classification** : vous pouvez choisir **l’alerte True** ou **False**.
  - **Commentaire** : vous pouvez ajouter un commentaire sur l’alerte.

    Si vous sélectionnez les trois points en regard de **Gérer l’alerte**, vous pouvez **consulter un expert en menaces**, **exporter** l’alerte dans un fichier Excel ou **lier à un autre incident**.

    :::image type="content" source="../../media/defender-identity/manage-alert.png" alt-text="Option Gérer l’alerte" lightbox="../../media/defender-identity/manage-alert.png":::

    > [!NOTE]
    > Dans le fichier Excel, deux liens sont désormais disponibles : **Afficher dans Microsoft Defender pour Identity** et **Afficher dans Microsoft 365 Defender**. Chaque lien vous permet d’accéder au portail approprié et d’y fournir des informations sur l’alerte.

## <a name="see-also"></a>Voir aussi

- [Examiner les alertes dans Microsoft 365 Defender](../defender/investigate-alerts.md)
