---
title: Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft
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
description: Découvrez comment créer des alertes pour les activités dans le Gestionnaire de conformité Microsoft qui peuvent avoir un impact sur votre score de conformité.
ms.openlocfilehash: bb81588be31b2c13113953c585112ee2f5a56875
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319131"
---
# <a name="microsoft-compliance-manager-alerts-and-alert-policies"></a>Alertes et stratégies d’alerte du Gestionnaire de conformité Microsoft

**Dans cet article :** Découvrez comment définir **des alertes** pour certaines activités dans le Gestionnaire de conformité, comment gérer les alertes et comment créer  des stratégies d’alerte pour définir des conditions d’alerte.

## <a name="overview"></a>Vue d’ensemble
Le gestionnaire de conformité peut vous alerter sur les modifications dès qu’elles se produisent afin de rester au fait de vos objectifs de conformité. Par exemple, vous pouvez configurer des alertes pour vous informer lorsque la valeur du score d’une action d’amélioration a augmenté ou diminué en raison d’une modification de configuration dans votre client, ou lorsqu’une action d’amélioration a été affectée à un utilisateur pour effectuer des tâches d’implémentation ou de test. Affichez [les types d’événements](#create-an-alert-policy) pour lesquels vous pouvez créer des alertes.

Pour créer des alertes, vous devez d’abord configurer une stratégie d’alerte pour décrire les conditions qui déclenchent une alerte et la fréquence des notifications. Lorsque nous détectons une correspondance à vos conditions de stratégie, vous recevez une notification par courrier électronique avec des détails afin de déterminer s’il faut examiner ou prendre des mesures supplémentaires.


Toutes les alertes sont répertoriées sous l’onglet **Alertes** dans le Gestionnaire de conformité et toutes les stratégies d’alerte sont répertoriées sous l’onglet Stratégies **d’alerte**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Comprendre les pages des stratégies d’alertes et d’alertes

> [!IMPORTANT]
> Les utilisateurs doivent  détenir le rôle lecteur sécurité dans Azure Active Directory (AD) pour accéder **aux pages des** **stratégies d’alertes** et d’alertes dans le Gestionnaire de conformité. Des rôles supplémentaires du Gestionnaire de sécurité et de conformité sont nécessaires pour travailler avec les alertes et les stratégies d’alerte. Obtenez les détails ci-dessous dans [autorisations de stratégie d’alerte](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Page Stratégies d’alerte

Sélectionnez **l’onglet Stratégies d’alerte** dans le Gestionnaire de conformité pour afficher et gérer vos stratégies d’alerte. La page **Stratégies d’alerte** contient un tableau répertoriant toutes les stratégies créées par votre organisation. À partir de cette page, vous pouvez créer de nouvelles stratégies, modifier des stratégies existantes, modifier l’état d’activation et supprimer des stratégies.

Dans la **colonne État**, **active** signifie que la stratégie est en vigueur et déclenche des alertes lorsque les conditions sont remplies. **Inactive** signifie que la stratégie existe, mais qu’elle ne génère pas d’alertes. Le tableau des stratégies indique également la gravité de la stratégie et la date de la dernière modification de la stratégie.

Pour afficher les détails d’une stratégie individuelle, sélectionnez sa ligne dans le tableau. Un volet volant s’affiche et affiche tous les détails. Sélectionnez **le bouton Action** en bas du volet et sélectionnez parmi les options pour modifier la stratégie, afficher ses alertes ou la supprimer. Les commandes d’ajout, de modification, de suppression, d’activation et de désactivation sont également disponibles en haut du tableau, au-dessus des filtres.

Pour commencer à créer une stratégie d’alerte, voir [Créer une stratégie d’alerte](#create-an-alert-policy).

### <a name="alerts-page"></a>Page Alertes

Sélectionnez **l’onglet Alertes** dans le Gestionnaire de conformité pour afficher et gérer vos alertes. La page **Alertes** contient un tableau répertoriant chaque alerte générée par une stratégie d’alerte, ainsi que sa gravité et l’événement déclencheur (par exemple, la modification du score d’une action) et la date de l’alerte.

Pour afficher une alerte individuelle, sélectionnez sa ligne dans le tableau. Un volet volant s’affiche et affiche tous les détails sous **l’onglet Vue** d’ensemble du volet. **L’onglet Journal des** événements affiche les actions entreprises par les utilisateurs qui ont déclenché l’alerte.

Le bouton **Action** en bas du volet fournit des options pour affecter l’alerte à un utilisateur pour le suivi, envoyer un e-mail à l’utilisateur dont les actions ont généré l’alerte ou afficher les détails de la stratégie qui a généré l’alerte. Vous pouvez également faire les mêmes actions en sélectionnant le bouton arrondi qui apparaît à gauche du nom de l’alerte lorsque vous pointez sur sa ligne, puis en sélectionnant l’un des boutons situés en haut du tableau, au-dessus des filtres.

Pour commencer à travailler avec des alertes, voir [Affichage et gestion des alertes](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Autorisations de stratégie d’alerte

Le tableau ci-dessous décrit les utilisateurs qui peuvent créer et modifier des alertes et des stratégies d’alerte en fonction de leur type de rôle. En plus de détenir un rôle gestionnaire de conformité, les utilisateurs ont également besoin d’un rôle Azure AD comme suit :

- Rôle lecteur **sécurité dans** Azure AD pour l’affichage des alertes et des stratégies d’alerte
- Rôle **d’administrateur de** la sécurité dans Azure AD pour la création ou la mise à jour des stratégies d’alerte
 
En savoir plus [sur les rôles Azure dans le Centre de conformité Microsoft 365](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-microsoft-365-compliance-center).


| Role | Peut créer et modifier des stratégies | Peut modifier les alertes | 
| :------------- | :-------------: | :------------: |
| **Administration du Gestionnaire de conformité**| Oui  | Oui | 
| **Évaluateur du Gestionnaire de conformité**| Oui | Oui | 
| **Contribution du Gestionnaire de conformité**| Oui | Oui | 
| **Administrateur général**| Non | Non  | 
| **Lecteur du Gestionnaire de conformité**| Non | Non | 

Découvrez comment définir [des autorisations utilisateur et attribuer des rôles pour le Gestionnaire de conformité](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Créer une stratégie d’alerte

Vous pouvez créer des stratégies pour vous alerter lorsque certaines modifications ou événements liés à des actions d’amélioration se produisent. Les types d’événements sont répertoriés ci-dessous.

### <a name="alert-event-types"></a>Types d’événements d’alerte

- **Changement de score** : augmentation ou diminution du nombre de points attribués pour une action d’amélioration en raison des modifications de configuration apportées par une personne de votre organisation. Par exemple, si votre organisation crée une stratégie de gestion des risques internes, cela peut augmenter vos points pour une certaine action d’un certain montant.
- **Changement d’affectation** : une action d’amélioration a été attribuée à un utilisateur, ré-affectée à un autre utilisateur ou non affectée à un utilisateur.
- **Changement d’état d’implémentation** : un utilisateur a modifié l’état d’implémentation d’une action d’amélioration.
- **Modification de l’état du** test : un utilisateur a modifié l’état de test d’une action d’amélioration.
- **Modification de la preuve** : un utilisateur a téléchargé ou supprimé un document de preuve dans l’onglet **Documents** de l’action d’amélioration.

### <a name="policy-creation-steps"></a>Étapes de création de stratégie

Pour créer une stratégie pour générer des alertes basées sur un ou plusieurs événements, suivez les étapes ci-dessous :

1. Dans **le Gestionnaire de conformité**, allez sur la page **Stratégies** d’alerte et sélectionnez **+Ajouter** pour démarrer l’Assistant création de stratégie.

2. Dans la page **Nom et description** , entrez un nom pour la stratégie et une description facultative, puis sélectionnez **Suivant**.

3. Dans la page **Conditions** , sélectionnez un ou plusieurs événements qui déclencheront une alerte. Sous **l’en-tête** de l’activité d’action d’amélioration, sélectionnez Ajouter des **sous-conditions** et cochez la case qui s’affiche lorsque vous pointez à gauche de chaque nom de condition. Vous pouvez choisir une ou plusieurs conditions pour une stratégie : modification d’affectation, modification de preuve, changement d’état d’implémentation, changement de score, changement d’état de test. Lorsque vous avez terminé, sélectionnez **Suivant**.

4. Dans la page **Résultats** , choisissez ce qui se produit lorsqu’une correspondance de stratégie est détectée :
      - Sélectionnez un niveau de gravité pour l’alerte lorsqu’une correspondance est détectée : faible, moyenne ou élevée.
      - Sélectionnez la fréquence de notification par courrier électronique lors de la détection d’une correspondance. Vous pouvez choisir d’être averti à chaque correspondance ou de choisir un seuil d’un certain nombre de correspondances supérieures à trois.
      - Si vous choisissez d’être averti après au moins trois correspondances, vous devez indiquer le nombre de minutes au cours des lesquelles ce seuil doit être atteint (par exemple, 4 correspondances dans les 90 minutes).
  
    Lorsque vous avez terminé, sélectionnez **Suivant**.

5. Dans la page **Destinataire de l’alerte** , sélectionnez d’autres utilisateurs de votre organisation pour recevoir un courrier électronique lorsque les conditions de stratégie sont remplies. L’utilisateur qui crée la stratégie est le destinataire par défaut. **Sélectionnez +Sélectionnez les destinataires** et cochez les cases en regard de chaque nom d’utilisateur dans le volet volant auquel vous souhaitez recevoir la notification par courrier électronique. Lorsque vous avez terminé, **sélectionnez Ajouter des destinataires**, puis **suivant**.

6. Examinez toutes les sélections et a apporté des modifications à chaque section en sélectionnant , puis sélectionnez **Suivant**. Lorsque vous avez terminé la révision, **sélectionnez Créer une stratégie**.

7. Lorsque votre stratégie est créée, sélectionnez **Terminé**. Vous arrivez à **la page des** stratégies d’alerte avec le volet volant de la stratégie que vous avez créée et que vous avez déjà ouverte.

Votre stratégie est active une fois que vous la créez, ce qui signifie qu’elle commence à détecter les correspondances et à générer des alertes. Consultez la section **Gestion des stratégies** ci-dessous pour savoir comment désactiver ou supprimer des stratégies.

La création ou la mise à jour d’une stratégie peut prendre jusqu’à 24 heures avant que les alertes ne soient générées par cette stratégie. [Consultez les détails de l’alerte ci-dessous](#view-alert-details) pour en savoir plus sur le déclenchement d’événements et l’agrégation d’alertes.

## <a name="managing-policies"></a>Gestion des stratégies

La page **Stratégies d’alerte** contient une liste de toutes vos stratégies. Consultez [la page Stratégies d’alerte](#alert-policies-page) pour mieux comprendre cette page. Tous les utilisateurs de votre organisation peuvent afficher des stratégies, mais certaines actions sont limitées à certains rôles ; voir [Autorisations de stratégie d’alerte](#alert-policy-permissions).

### <a name="view-policy-details"></a>Afficher les détails de la stratégie

Sélectionnez une stratégie dans sa ligne dans **la page** Stratégies d’alerte pour afficher un panneau volant affichant les détails de la stratégie, y compris ses conditions de correspondance, si et quand les notifications d’alerte sont envoyées et à qui, et niveau de gravité.

Le **bouton Actions** en bas du panneau vous offre des options pour modifier la stratégie, supprimer la stratégie ou afficher les alertes.

### <a name="view-a-policys-alerts"></a>Afficher les alertes d’une stratégie

Dans le panneau volant de la stratégie, sélectionnez **Actions** , puis **affichez les alertes**. Vous serez directement placé sur la page Alertes avec une vue filtrée de toutes les alertes générées par cette stratégie. Découvrez comment travailler [avec les alertes](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Modifier une stratégie

Vous pouvez modifier n’importe quel aspect d’une stratégie à l’exception de son nom. Si vous souhaitez modifier son nom, vous devez créer une stratégie avec un nouveau nom.

Pour modifier une stratégie, sélectionnez le bouton arrondi qui apparaît à gauche de son nom lorsque vous pointez sur sa ligne sur **la page** Stratégies d’alerte, puis sélectionnez le bouton Modifier dans la partie supérieure, au-dessus des filtres.

Vous serez conduit à l’Assistant Création de stratégie dans lequel vous pouvez apporter et enregistrer des modifications à votre stratégie.  Vous pouvez également sélectionner la stratégie pour faire monter son panneau d’informations et, à partir du bouton **Actions** , sélectionner **Modifier la stratégie**. Après avoir de nouveau travaillé dans l’Assistant, examinez vos sélections et, à l’étape finale, sélectionnez **Mettre** à jour pour enregistrer vos modifications.

La générer par la stratégie mise à jour peut prendre jusqu’à 24 heures.

### <a name="activate-or-inactivate-a-policy"></a>Activer ou désactiver une stratégie

Les stratégies sont activées par défaut dès qu’elles sont créées. Lorsqu’elle est active, une stratégie crée une alerte (affichée sur la page Alertes) lorsque les conditions sont **remplies** et envoie un message électronique de notification aux destinataires désignés.

Pour modifier une stratégie en état **inactif** , ce qui signifie qu’elle ne génère pas d’alertes, sélectionnez le bouton arrondi qui apparaît à gauche du nom de la stratégie lorsque vous pointez sur sa ligne. Sélectionnez ensuite **la commande Désactiver** au-dessus du tableau. L’état de votre stratégie est désormais Inactif. Pour réactiver la stratégie, suivez le même processus et sélectionnez le **bouton Activer** au-dessus des filtres.

### <a name="delete-a-policy"></a>Suppression d’une stratégie

Pour supprimer une stratégie, vous pouvez sélectionner le bouton à côté de son nom dans **la page** Stratégies d’alerte et sélectionner **Supprimer** en haut de la page. Vous pouvez également sélectionner la stratégie pour faire monter son panneau d’informations et, à partir du bouton **Actions** , sélectionner **Supprimer la stratégie**.

La suppression est permanente. Une fois que vous avez supprimé une stratégie, elle ne génère plus d’alertes ni de notifications par courrier électronique. En savoir plus [sur les alertes connectées aux stratégies supprimées](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Affichage et gestion des alertes

La page **Alertes** affiche un tableau avec toutes les alertes générées par toutes vos stratégies. Les alertes sont générées presque immédiatement après qu’un événement correspondant aux conditions de la stratégie s’est produit. Le nom de l’alerte est identique à celui de la stratégie qui a généré l’alerte.

Une alerte peut uniquement être générée à partir d’une stratégie active. Une fois qu’une alerte est générée, elle reste répertoriée sur la page **Alertes** , que la stratégie soit active ou inactive.

### <a name="filter-your-view-of-alerts"></a>Filtrer votre affichage des alertes
Vous pouvez filtrer votre affichage des alertes en sélectionnant la commande **Filtrer** au-dessus du tableau de **votre page Alertes** . Dans le **volet** de filtrage volant, sélectionnez l’une des options de filtre ci-après :

- Type d’événement
- Severity
- Statut
- Utilisateur affecté à
- Date de détection
- Nom de la stratégie

Après avoir fait vos sélections, sélectionnez **Appliquer**. Le volet volant se ferme et votre page **Alertes** mise à jour affiche votre affichage filtré. Vos filtres sont affichés en haut du tableau, même si toutes les colonnes de filtre ne peuvent pas s’afficher dans le tableau.

### <a name="view-alert-details"></a>Afficher les détails de l’alerte

Pour afficher tous les détails de l’alerte, y compris les événements qui l’ont déclenchée, sélectionnez sa ligne dans le tableau. Un volet volant affiche les détails de l’alerte sous l’onglet **Vue** d’ensemble du panneau.

L’onglet Journal des événements du panneau volant répertorie les activités qui ont généré l’alerte, telles qu’une modification de score ou d’affectation, ainsi que le nom de l’utilisateur associé à chaque action et la date détectée.

### <a name="alert-events"></a>Événements d’alerte

La **colonne Événements** de **la page Alertes** indique les conditions d’une stratégie qui ont été détectées ; en d’autres termes, l’activité qui a généré l’alerte. **L’onglet Journal des** événements du panneau Détails de l’alerte répertorie chaque instance d’un événement, l’utilisateur associé et la date détectée. Les valeurs d’événement sont répertoriées ci-dessous :

- **Changement de score** : indique le nombre d’augmentation ou de diminution en points
- **Modification de l’affectation** : une action d’amélioration a été affectée à un utilisateur, ré-affectée à un autre utilisateur ou non affectée à un utilisateur
- **Changement d’état d’implémentation** : un utilisateur a modifié l’état d’implémentation d’une action d’amélioration
- **Modification de l’état du** test : un utilisateur a modifié l’état de test d’une action d’amélioration.
- **Modification de la preuve** : un utilisateur a téléchargé ou supprimé un document de preuve dans l’onglet Documents de l’action d’amélioration
- **Multi-événement :** plusieurs instances du même type d’événement ont été détectées ; par exemple, une action d’amélioration unique qui a été réassignée plusieurs fois
- **Multi-condition** : plusieurs conditions au sein d’une stratégie unique ont été détectées

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Agrégation d’alertes pour plusieurs événements en une minute

Lorsque plusieurs événements qui correspondent aux conditions d’une stratégie d’alerte se produisent avec une minute, ils sont ajoutés à une alerte existante par un processus appelé agrégation d’alertes.

Par exemple, lorsqu’un événement se produit et correspond à une stratégie, une alerte est générée et affichée sur la page **Alertes** et une notification est envoyée. Si un autre événement correspondant à la même stratégie se produit dans les minutes suivant le premier événement, le Gestionnaire de conformité ajoute des détails sur l’événement supplémentaire sous l’onglet Journal des événements de l’alerte existante au lieu de déclencher une nouvelle alerte. L’objectif de l’agrégation d’alertes est de réduire la « lassitude » des alertes et de vous permettre de vous concentrer et d’agir sur moins d’alertes.

### <a name="taking-action-on-alerts"></a>Action sur les alertes

Lorsqu’une de vos stratégies génère une alerte, vous pouvez afficher les événements à l’origine de l’alerte et déterminer si vous devez vérifier les événements ou les examiner plus en détail.

Pour prendre une action sur une alerte, sélectionnez sa ligne sur la page **Alertes** pour faire monter le panneau volant avec ses détails, sélectionnez le bouton **Actions** et choisissez parmi les options répertoriées ci-dessous. Vous pouvez également prendre des mesures en sélectionnant le bouton arrondi qui apparaît à gauche du nom de l’alerte lorsque vous pointez sur sa ligne et en sélectionnant l’un des boutons d’action situés en haut de la page, au-dessus des filtres.

**Affecter une** alerte : vous pouvez affecter l’alerte à un utilisateur pour examiner ou vérifier les événements à l’origine de l’alerte. Lorsque vous choisissez cette option, un panneau s’ouvre dans lequel vous pouvez sélectionner un utilisateur dans votre organisation et lui affecter l’alerte. Vous pouvez filtrer l’affichage de vos alertes en sélectionnant **Filtres** dans la page **Alertes** et en entrant le nom de l’utilisateur dans le champ Affecté **à** .

**Alerte par** courrier électronique : vous pouvez envoyer un courrier électronique à l’utilisateur associé à l’activité de l’alerte pour confirmer qu’il a pris l’action. Lorsque vous avez choisi cette option, elle ouvre un modèle de courrier électronique avec des informations de base sur l’alerte, que vous pouvez personnaliser avec d’autres instructions et envoyées à l’utilisateur.

**Afficher les détails de** la stratégie : vous souhaitez peut-être passer en revue les paramètres de la stratégie qui a déclenché l’alerte. Notez que lorsque vous sélectionnez cette option, vous êtes directement conduit à **la page** Stratégies d’alerte avec le panneau Détails de la stratégie déjà ouvert. Vous ne serez plus sur votre page **Alertes** lorsque vous fermerez le panneau Détails de la stratégie.

**Modifier l’état** : vous pouvez mettre à jour l’état de votre alerte en fonction de votre examen de son impact et selon qu’elle doit être en examen. Pour plus d’informations sur les statuts des alertes, dans la section suivante.

### <a name="alert-status"></a>État de l’alerte

Lorsqu’une alerte est créée, son état est **Actif**. Lorsque vous examinez les détails de chaque alerte, vous pouvez mettre à jour son état à l’un des états répertoriés ci-dessous :

- **Actif :** état par défaut de l’alerte jusqu’à ce que son état soit modifié
- **Examen : l’alerte** est en cours d’examen
- **Résolu :** l’alerte ne nécessite pas d’examen ou de suivi plus approfondie
- **Rejeté** : l’alerte n’est pas pertinente ou n’a pas besoin d’examen

Pour affecter ou modifier l’état d’une alerte, sélectionnez une alerte à partir de sa ligne  dans le tableau, sélectionnez Modifier l’état en haut de la page, au-dessus des filtres. Dans le volet volant Mettre à jour l’état de l’alerte, sélectionnez un état dans le menu déroulant, puis sélectionnez Mettre **à jour l’alerte**.

Une fois qu’une alerte est générée, son état est indépendant de l’état de la stratégie qui a généré l’alerte. Par exemple, il est possible d’avoir une alerte **active** associée à une stratégie **inactive**, et il est possible d’avoir un  état d’investigation sur une alerte générée par une stratégie qui a ensuite été désactivée ou supprimée.

### <a name="when-policies-are-deleted"></a>Quand les stratégies sont supprimées

Lorsqu’une stratégie est supprimée, toutes les alertes générées par cette stratégie restent dans votre page **Alertes** , mais aucune nouvelle alerte n’est générée.

## <a name="email-notifications-of-alerts"></a>Notifications par courrier électronique des alertes

Lorsque vous créez une stratégie, un message électronique est envoyé à l’utilisateur qui l’a créée pour l’avertir qu’une correspondance a été détectée. Vous pouvez choisir d’envoyer ces notifications par courrier électronique à d’autres utilisateurs de votre organisation. Les alertes se produisent en temps quasi réel et les notifications par courrier électronique sont envoyées dès qu’une alerte est générée. Le courrier électronique contient le nom de l’événement, la gravité, l’heure détectée et un lien pour afficher l’alerte dans le Gestionnaire de conformité.

### <a name="remove-users-from-receiving-alerts"></a>Supprimer les utilisateurs de la réception d’alertes

Si vous désignez des destinataires d’alerte, puis décidez ultérieurement de les supprimer, suivez les étapes ci-dessous. Notez que le créateur de la stratégie reçoit toujours des notifications par courrier électronique lorsque des correspondances de stratégie sont détectées.

1. Commencez les étapes de [modification de votre stratégie](#edit-a-policy).
2. Lorsque vous arrivez à l’écran **Destinataires de l’alerte** , **sélectionnez +Sélectionner des destinataires**.
3. Dans le panneau volant Sélectionner des **destinataires** , recherchez l’utilisateur que vous souhaitez supprimer des notifications et décochez la case à gauche de son nom, puis sélectionnez le bouton Ajouter des **destinataires** (ce qui a pour effet d’enregistrer votre sélection).
4. Continuez à l’aide de l’Assistant et confirmez que l’utilisateur n’apparaît pas sous **Destinataires** dans la page Révision et fin. **Sélectionnez Mettre à** jour pour enregistrer vos paramètres et terminer.
