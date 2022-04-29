---
title: Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Découvrez comment créer des alertes pour les activités dans le Gestionnaire de conformité Microsoft Purview qui peuvent avoir un impact sur votre score de conformité.
ms.openlocfilehash: b1e5630e20ace4835f8651d1878e731e423f58b1
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129153"
---
# <a name="microsoft-purview-compliance-manager-alerts-and-alert-policies"></a>Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Dans cet article :** Découvrez comment **définir des alertes** pour certaines activités dans le Gestionnaire de conformité, comment gérer les alertes et comment **créer des stratégies d’alerte** pour définir des conditions d’alerte.

## <a name="overview"></a>Aperçu
Le Gestionnaire de conformité peut vous avertir des modifications dès qu’elles se produisent afin que vous puissiez suivre vos objectifs de conformité. Par exemple, vous pouvez configurer des alertes pour vous informer quand la valeur de score d’une action d’amélioration a augmenté ou diminué en raison d’un changement de configuration dans votre locataire, ou lorsqu’une action d’amélioration a été affectée à un utilisateur pour effectuer un travail d’implémentation ou de test. Affichez les [types d’événements](#create-an-alert-policy) pour lesquels vous pouvez créer des alertes.

Pour créer des alertes, vous devez d’abord configurer une stratégie d’alerte pour décrire les conditions qui déclenchent une alerte et la fréquence des notifications. Lorsque nous détectons une correspondance avec vos conditions de stratégie, vous recevez une notification par e-mail avec des détails afin que vous puissiez déterminer s’il faut examiner ou prendre d’autres mesures.


Toutes les alertes sont répertoriées sous l’onglet **Alertes** dans le Gestionnaire de conformité, et toutes les stratégies d’alerte sont répertoriées sous **l’onglet Stratégies d’alerte**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Présentation des pages Alertes et Stratégies d’alerte

> [!IMPORTANT]
> Les utilisateurs doivent avoir le rôle **lecteur sécurité** dans Azure Active Directory (AD) afin d’accéder aux pages **Alertes** et **Stratégies d’alerte** dans le Gestionnaire de conformité. Des rôles supplémentaires de gestionnaire de sécurité et de conformité sont nécessaires pour utiliser des alertes et des stratégies d’alerte. Obtenez les détails ci-dessous dans [Les autorisations de stratégie d’alerte](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Page Stratégies d’alerte

Sélectionnez l’onglet **Stratégies d’alerte** dans le Gestionnaire de conformité pour afficher et gérer vos stratégies d’alerte. La page **Stratégies d’alerte** contient un tableau répertoriant toutes les stratégies créées par votre organisation. À partir de cette page, vous pouvez créer des stratégies, modifier des stratégies existantes, modifier l’état d’activation et supprimer des stratégies.

Dans la **colonne État**, **Active** signifie que la stratégie est en vigueur et déclenche des alertes lorsque les conditions sont remplies. **Inactif** signifie que la stratégie existe, mais ne génère pas d’alertes. La table stratégies affiche également la gravité de la stratégie et la date à laquelle la stratégie a été modifiée pour la dernière fois.

Pour afficher les détails d’une stratégie individuelle, sélectionnez sa ligne dans le tableau. Un volet volant s’affiche et affiche tous les détails. Sélectionnez le bouton **Action** en bas du volet, puis sélectionnez parmi les options permettant de modifier la stratégie, d’afficher ses alertes ou de la supprimer. Les commandes à ajouter, modifier, supprimer, activer et désactiver sont également disponibles en haut de la table, au-dessus des filtres.

Pour commencer à créer une stratégie d’alerte, consultez [Créer une stratégie d’alerte](#create-an-alert-policy).

### <a name="alerts-page"></a>Page Alertes

Sélectionnez l’onglet **Alertes** dans le Gestionnaire de conformité pour afficher et gérer vos alertes. La page **Alertes** contient un tableau répertoriant chaque alerte générée par une stratégie d’alerte, ainsi que sa gravité et l’événement déclencheur (par exemple, le changement de score d’une action) et la date de l’alerte.

Pour afficher une alerte individuelle, sélectionnez sa ligne dans le tableau. Un volet volant s’affiche et affiche tous les détails sous l’onglet **Vue d’ensemble** du volet. L’onglet **Journal des événements** affiche les actions effectuées par les utilisateurs qui ont déclenché l’alerte.

Le bouton **Action** en bas du volet fournit des options permettant d’affecter l’alerte à un utilisateur pour le suivi, d’envoyer un e-mail à l’utilisateur dont les actions ont généré l’alerte ou d’afficher les détails de la stratégie qui génère l’alerte. Vous pouvez également effectuer les mêmes actions en sélectionnant le bouton rond qui apparaît à gauche du nom de l’alerte lorsque vous pointez sur sa ligne, puis en sélectionnant l’un des boutons situés en haut du tableau, au-dessus des filtres.

Pour commencer à utiliser des alertes, consultez [Affichage et gestion des alertes](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Autorisations de stratégie d’alerte

Le tableau ci-dessous décrit les utilisateurs qui peuvent créer et modifier des alertes et des stratégies d’alerte en fonction de leur type de rôle. En plus d’avoir un rôle gestionnaire de conformité, les utilisateurs ont également besoin d’un rôle Azure AD comme suit :

- Rôle **lecteur Sécurité** dans Azure AD pour afficher les alertes et les stratégies d’alerte
- Rôle **Administrateur de la sécurité** dans Azure AD pour la création ou la mise à jour des stratégies d’alerte
 
En savoir plus sur les [rôles Azure dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-compliance-portal).


| Rôle | Peut créer et modifier des stratégies | Peut modifier des alertes | 
| :------------- | :-------------: | :------------: |
| **Administration du Gestionnaire de conformité**| Oui  | Oui | 
| **Évaluateur du Gestionnaire de conformité**| Oui | Oui | 
| **Contribution du Gestionnaire de conformité**| Oui | Oui | 
| **Administrateur général**| Oui | Oui  | 
| **Lecteur du Gestionnaire de conformité**| Non | Non | 

Découvrez comment [définir des autorisations utilisateur et attribuer des rôles pour le Gestionnaire de conformité](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Créer une stratégie d’alerte

Vous pouvez créer des stratégies pour vous avertir lorsque certaines modifications ou événements liés aux actions d’amélioration se produisent. Les types d’événements sont répertoriés ci-dessous.

### <a name="alert-event-types"></a>Types d’événements d’alerte

- **Changement** de score : augmentation ou diminution des points attribués pour une action d’amélioration en raison des modifications de configuration apportées par une personne de votre organisation. Par exemple, si votre organisation crée une stratégie de gestion des risques internes, cela peut augmenter vos points pour une certaine action d’un certain montant.
- **Modification de l’affectation** : une action d’amélioration a été affectée à un utilisateur, réaffectée à un autre utilisateur ou non attribuée par un utilisateur.
- **Changement d’état de l’implémentation** : un utilisateur a modifié l’état d’implémentation d’une action d’amélioration.
- **Modification de l’état** du test : un utilisateur a modifié l’état de test d’une action d’amélioration.
- **Modification de la preuve** : un utilisateur a chargé ou supprimé un document de preuve sous l’onglet **Documents** de l’action d’amélioration.

### <a name="policy-creation-steps"></a>Étapes de création de stratégie

Pour créer une stratégie pour générer des alertes basées sur un ou plusieurs événements, suivez les étapes ci-dessous :

1. Dans le **Gestionnaire de conformité**, accédez à la page **Stratégies d’alerte** , puis **sélectionnez +Ajouter** pour démarrer l’Assistant Création de stratégie.

2. Dans la page **Nom et description** , entrez un nom pour la stratégie et une description facultative, puis sélectionnez **Suivant**.

3. Dans la page **Conditions** , sélectionnez un ou plusieurs événements qui déclencheront une alerte. Sous l’en-tête **d’activité d’action d’amélioration** , **sélectionnez Ajouter des sous-conditions** et cochez la case qui s’affiche lorsque vous pointez à gauche de chaque nom de condition. Vous pouvez choisir une ou plusieurs conditions pour une stratégie : changement d’affectation, modification des preuves, changement d’état de l’implémentation, changement de score, changement d’état de test. Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Résultats** , choisissez ce qui se passe lorsqu’une correspondance de stratégie est détectée :
      - Sélectionnez un niveau de gravité pour l’alerte lorsqu’une correspondance est détectée : faible, moyenne ou élevée.
      - Sélectionnez la fréquence à laquelle vous souhaitez être averti par e-mail lorsqu’une correspondance est détectée. Vous pouvez choisir d’être averti avec chaque correspondance, ou choisir un seuil d’un certain nombre de correspondances au-dessus de trois.
      - Si vous choisissez d’être averti après trois correspondances ou plus, vous désignez alors le nombre de minutes pendant lesquelles ce seuil doit être atteint (par exemple, 4 correspondances dans les 90 minutes).
  
    Lorsque vous avez terminé, sélectionnez **Suivant**.

5. Dans la page **du destinataire de l’alerte** , sélectionnez d’autres utilisateurs de votre organisation pour recevoir un e-mail lorsque les conditions de stratégie sont remplies. L’utilisateur qui crée la stratégie est le destinataire par défaut. Sélectionnez **+Sélectionner les destinataires** et cochez les cases en regard de chaque nom d’utilisateur dans le volet de menu volant pour lequel vous souhaitez recevoir la notification par e-mail. Lorsque vous avez terminé, **sélectionnez Ajouter des destinataires**, puis **sélectionnez Suivant**.

6. Passez en revue toutes les sélections et apportez des modifications à chaque section en sélectionnant, puis sélectionnez **Suivant**. Une fois l’examen terminé, **sélectionnez Créer une stratégie**.

7. Lorsque votre stratégie est créée, sélectionnez **Terminé**. Vous accédez à votre page **Stratégies d’alerte** avec le volet volant de la stratégie que vous venez de créer déjà ouverte.

Votre stratégie est active une fois que vous la créez, ce qui signifie qu’elle commence à détecter les correspondances et à générer des alertes. Consultez la section **Gestion des stratégies ci-dessous** pour savoir comment désactiver ou supprimer des stratégies.

La création ou la mise à jour d’une stratégie peut prendre jusqu’à 24 heures avant que les alertes ne soient générées par cette stratégie. Consultez [afficher les détails de l’alerte ci-dessous](#view-alert-details) pour en savoir plus sur le déclenchement d’événements et l’agrégation d’alertes.

## <a name="managing-policies"></a>Gestion des stratégies

La page **Stratégies d’alerte** contient une liste de toutes vos stratégies. Consultez la [page Stratégies d’alerte](#alert-policies-page) pour mieux comprendre cette page. Tout utilisateur de votre organisation peut afficher les stratégies, mais certaines actions sont limitées à certains rôles ; consultez [Les autorisations de stratégie d’alerte](#alert-policy-permissions).

### <a name="view-policy-details"></a>Afficher les détails de la stratégie

Sélectionnez une stratégie à partir de sa ligne dans la page **Stratégies d’alerte** pour afficher un panneau volant affichant les détails de la stratégie, y compris ses conditions de correspondance, si et quand les notifications d’alerte sont envoyées, à qui et au niveau de gravité.

Le bouton **Actions** situé en bas du panneau vous permet de modifier la stratégie, de supprimer la stratégie ou d’afficher les alertes.

### <a name="view-a-policys-alerts"></a>Afficher les alertes d’une stratégie

Dans le panneau de menu volant de la stratégie, sélectionnez **Actions** , puis **affichez les alertes**. Vous accédez directement à la page Alertes avec une vue filtrée de toutes les alertes générées par cette stratégie. Découvrez comment [utiliser les alertes](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Modifier une stratégie

Vous pouvez modifier n’importe quel aspect d’une stratégie à l’exception de son nom. Si vous souhaitez modifier son nom, vous devez créer une stratégie avec un nouveau nom.

Pour modifier une stratégie, sélectionnez le bouton rond qui apparaît à gauche de son nom lorsque vous pointez sur sa ligne sur la page **Stratégies d’alerte** , puis **sélectionnez** le bouton Modifier en haut, au-dessus des filtres.

Vous accédez à l’Assistant Création de stratégie, où vous pouvez apporter et enregistrer des modifications à votre stratégie.  Vous pouvez également sélectionner la stratégie pour afficher son panneau de détails, puis, dans le bouton **Actions** , sélectionner **Modifier la stratégie**. Après avoir réexécuté l’Assistant, passez en revue vos sélections et, à l’étape finale, sélectionnez **Mettre à jour** pour enregistrer vos modifications.

La génération des alertes par la stratégie mise à jour peut prendre jusqu’à 24 heures.

### <a name="activate-or-inactivate-a-policy"></a>Activer ou désactiver une stratégie

Les stratégies sont activées par défaut dès qu’elles sont créées. Lorsqu’elle est active, une stratégie crée une alerte (affichée sur la page Alertes) lorsque les conditions sont **remplies** et envoie un e-mail de notification aux destinataires désignés.

Pour remplacer une stratégie par un état **inactif** , ce qui signifie qu’elle ne génère pas d’alertes, sélectionnez le bouton rond qui apparaît à gauche du nom de la stratégie lorsque vous pointez sur sa ligne. Sélectionnez ensuite la commande **Désactiver** au-dessus du tableau. L’état de votre stratégie est désormais inactif. Pour réactiver la stratégie, suivez le même processus et sélectionnez le bouton **Activer** au-dessus des filtres.

### <a name="delete-a-policy"></a>Suppression d’une stratégie

Pour supprimer une stratégie, vous pouvez sélectionner le bouton en regard de son nom dans la page **Stratégies d’alerte** et sélectionner **Supprimer** en haut de la page. Vous pouvez également sélectionner la stratégie pour afficher son panneau de détails, puis, dans le bouton **Actions** , sélectionner **Supprimer la stratégie**.

La suppression est permanente. Une fois que vous avez supprimé une stratégie, elle ne génère plus d’alertes ou de notifications par e-mail. En savoir plus sur [les alertes connectées aux stratégies supprimées](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Affichage et gestion des alertes

La page **Alertes** affiche un tableau avec toutes les alertes générées par toutes vos stratégies. Les alertes sont générées presque immédiatement après qu’un événement correspondant aux conditions de la stratégie se produit. Le nom de l’alerte est le même que celui de la stratégie qui a généré l’alerte.

Une alerte ne peut être générée qu’à partir d’une stratégie active. Une fois qu’une alerte est générée, elle reste répertoriée dans la page **Alertes** , que la stratégie soit active ou inactive.

### <a name="filter-your-view-of-alerts"></a>Filtrer votre vue des alertes
Vous pouvez filtrer votre vue des alertes en sélectionnant la commande **Filtrer** au-dessus du tableau de votre page **Alertes** . Dans le volet de menu volant **Filtrer** , sélectionnez parmi les options de filtre suivantes :

- Type d’événement
- Severity
- État
- Utilisateur affecté à
- Date de détection
- Nom de la stratégie

Après avoir effectué vos sélections, **sélectionnez Appliquer**. Le volet de menu volant se ferme et votre page **Alertes** mise à jour affiche votre affichage filtré. Vos filtres sont affichés en haut du tableau, mais toutes les colonnes de filtre ne peuvent pas s’afficher dans le tableau.

### <a name="view-alert-details"></a>Afficher les détails de l’alerte

Pour afficher tous les détails de l’alerte, y compris les événements qui l’ont déclenchée, sélectionnez sa ligne sur la table. Un volet volant affiche les détails de l’alerte sous l’onglet **Vue d’ensemble** du panneau.

L’onglet **Journal des événements** du panneau de menu volant répertorie les activités qui ont généré l’alerte, telles qu’une modification de score ou une modification d’affectation, ainsi que le nom de l’utilisateur associé à chaque action et la date détectée.

### <a name="alert-events"></a>Événements d’alerte

La colonne **Événements** de la page **Alertes** indique les conditions d’une stratégie qui ont été détectées ; en d’autres termes, l’activité qui a généré l’alerte. L’onglet **Journal des événements** du panneau détails de l’alerte répertorie chaque instance d’un événement, l’utilisateur associé et la date détectée. Les valeurs d’événement sont répertoriées ci-dessous :

- **Changement** de score : indique le nombre d’augmentations ou de diminutions de points
- **Modification de l’affectation** : une action d’amélioration a été affectée à un utilisateur, réaffectée à un autre utilisateur ou non affectée par un utilisateur
- **Changement d’état de l’implémentation** : un utilisateur a modifié l’état d’implémentation d’une action d’amélioration
- **Modification de l’état** du test : un utilisateur a modifié l’état de test d’une action d’amélioration.
- **Modification de la preuve** : un utilisateur a chargé ou supprimé un document de preuve sous l’onglet Documents de l’action d’amélioration
- **Multi-événement** : plusieurs instances du même type d’événement ont été détectées ; par exemple, une action d’amélioration unique qui a été réattribuée plusieurs fois
- **Multi-condition** : plusieurs conditions au sein d’une même stratégie ont été détectées

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Agrégation d’alertes pour plusieurs événements dans un délai d’une minute

Lorsque plusieurs événements qui correspondent aux conditions d’une stratégie d’alerte se produisent avec une minute, ils sont ajoutés à une alerte existante par un processus appelé agrégation d’alerte.

Par exemple, lorsqu’un événement correspond à une stratégie, une alerte est générée et affichée sur la page **Alertes** et une notification est envoyée. Si un autre événement correspondant à la même stratégie se produit dans une minute après le premier événement, le Gestionnaire de conformité ajoute des détails sur l’événement supplémentaire sous l’onglet **Journal des événements** de l’alerte existante au lieu de déclencher une nouvelle alerte. L’objectif de l’agrégation des alertes est de réduire la « fatigue » des alertes et de vous permettre de vous concentrer et d’agir sur moins d’alertes.

### <a name="taking-action-on-alerts"></a>Prise d’une action sur les alertes

Quand l’une de vos stratégies génère une alerte, vous pouvez afficher les événements à l’origine de l’alerte et déterminer si vous devez vérifier ou examiner plus en détail les événements.

Pour effectuer une action sur une alerte, sélectionnez sa ligne dans la page **Alertes** pour afficher les détails du panneau volant, sélectionnez le bouton **Actions** et choisissez parmi les options répertoriées ci-dessous. Vous pouvez également effectuer des actions en sélectionnant le bouton rond qui apparaît à gauche du nom de l’alerte lorsque vous pointez sur sa ligne, puis en sélectionnant l’un des boutons d’action en haut de la page, au-dessus des filtres.

**Affecter l’alerte** : vous pouvez affecter l’alerte à un utilisateur pour examiner ou vérifier les événements à l’origine de l’alerte. Lorsque vous choisissez cette option, un panneau s’ouvre dans lequel vous pouvez sélectionner un utilisateur de votre organisation et lui attribuer l’alerte. Vous pouvez filtrer votre affichage des alertes en sélectionnant **Filtres** dans la page **Alertes** et en entrant le nom de l’utilisateur dans le champ **Affecté au** champ.

**Alerte par e-mail** : vous pouvez envoyer un e-mail à l’utilisateur associé à l’activité de l’alerte pour confirmer qu’il a pris l’action. Lorsque vous avez choisi cette option, elle ouvre un modèle de messagerie contenant des informations de base sur l’alerte, que vous pouvez personnaliser avec d’autres instructions et envoyer à l’utilisateur.

**Afficher les détails** de la stratégie : vous souhaiterez peut-être passer en revue les paramètres de la stratégie qui a déclenché l’alerte. Notez que lorsque vous sélectionnez cette option, vous accédez directement à la page **Stratégies d’alerte** avec le panneau détails de la stratégie déjà ouvert. Vous ne serez plus sur votre page **Alertes** lorsque vous fermerez le panneau des détails de la stratégie.

**Modifier l’état** : vous pouvez mettre à jour l’état de votre alerte en fonction de votre examen de son impact et de la nécessité de l’examiner. Pour en savoir plus sur les états d’alerte, consultez la section suivante.

### <a name="alert-status"></a>État de l’alerte

Lorsqu’une alerte est créée, son état est **Actif**. Lorsque vous passez en revue les détails de chaque alerte, vous pouvez mettre à jour son état dans l’un des états répertoriés ci-dessous :

- **Actif** : état par défaut de l’alerte jusqu’à ce que son état soit modifié
- **Examen : l’alerte** fait l’objet d’une enquête
- **Résolu** : l’alerte ne nécessite pas d’investigation supplémentaire ni de suivi
- **Ignoré :** l’alerte n’est pas pertinente ou n’a pas besoin d’investigation

Pour affecter ou modifier l’état d’une alerte, sélectionnez une alerte dans sa ligne sur la table, puis **sélectionnez Modifier l’état** en haut de la page, au-dessus des filtres. Dans le volet volant Mettre à jour l’état de l’alerte, sélectionnez un état dans le menu déroulant, puis sélectionnez **Mettre à jour l’alerte**.

Une fois qu’une alerte est générée, son état est indépendant de l’état de la stratégie qui a généré l’alerte. Par exemple, il est possible qu’une alerte **active** soit associée à une stratégie **inactive** et qu’il soit possible d’avoir un état **d’examen** sur une alerte qui a été générée par une stratégie qui a ensuite été désactivée ou supprimée.

### <a name="when-policies-are-deleted"></a>Lorsque des stratégies sont supprimées

Lorsqu’une stratégie est supprimée, toutes les alertes qui ont été générées par cette stratégie restent sur votre page **Alertes** , mais aucune nouvelle alerte n’est générée.

## <a name="email-notifications-of-alerts"></a>Notifications par e-mail d’alertes

Lorsque vous créez une stratégie, un e-mail est envoyé à l’utilisateur qui a créé la stratégie pour l’avertir qu’une correspondance a été détectée. Vous pouvez choisir d’envoyer ces notifications par e-mail à d’autres utilisateurs de votre organisation. Les alertes se produisent en quasi-temps réel et les notifications par e-mail sont envoyées dès qu’une alerte est générée. L’e-mail contient le nom de l’événement, la gravité, l’heure détectée et un lien pour afficher l’alerte dans le Gestionnaire de conformité.

### <a name="remove-users-from-receiving-alerts"></a>Supprimer les utilisateurs de la réception d’alertes

Si vous désignez des destinataires d’alerte, puis décidez de les supprimer ultérieurement, suivez les étapes ci-dessous. Notez que le créateur de stratégie reçoit toujours des notifications par e-mail lorsque des correspondances de stratégie sont détectées.

1. Commencez les étapes de [modification de votre stratégie](#edit-a-policy).
2. Lorsque vous arrivez à l’écran **Des destinataires d’alerte** , **sélectionnez +Sélectionner les destinataires**.
3. Dans le volet volant **Sélectionner les destinataires** , recherchez l’utilisateur à supprimer des notifications et décochez la case à gauche de leur nom, puis sélectionnez le bouton **Ajouter des destinataires** (ce qui a pour effet d’enregistrer votre sélection).
4. Continuez tout au long de l’Assistant et vérifiez que l’utilisateur n’apparaît pas sous **Destinataires** dans la page Révision et fin. Sélectionnez **Mettre à jour** pour enregistrer vos paramètres et terminer.
