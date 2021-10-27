---
title: Gérer les alertes microsoft Defender pour les points de terminaison
description: Modifiez l’état des alertes, créez des règles de suppression pour masquer les alertes, envoyez des commentaires et examinez l’historique des changements pour les alertes individuelles à l’intérieur du menu Gérer les alertes.
keywords: gérer les alertes, gérer, alertes, état, nouveau, en cours, résolu, résoudre les alertes, supprimer, suppression, règles, contexte, historique, commentaires, modifications
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1d4df8855e9aea643860d21b07473e82019f2323
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60587160"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Gérer les alertes microsoft Defender pour les points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Defender pour le point de terminaison vous avertit des événements malveillants, attributs et informations contextuelles possibles par le biais d’alertes. Un résumé des nouvelles alertes s’affiche dans le tableau de bord Opérations de sécurité **et** vous pouvez accéder à toutes les alertes dans la file **d’attente des alertes.**

Vous pouvez gérer les alertes en sélectionnant une alerte dans la file d’attente des **alertes** ou l’onglet **Alertes** de la page Appareil pour un appareil individuel.

La sélection d’une alerte à l’un de ces endroits fait monter le volet **de gestion des alertes.**

![Image du volet de gestion des alertes et de la file d’attente des alertes.](images/atp-alerts-selected.png)

## <a name="link-to-another-incident"></a>Lien vers un autre incident

Vous pouvez créer un incident à partir de l’alerte ou d’un lien vers un incident existant.

## <a name="assign-alerts"></a>Affecter des alertes

Si une alerte n’est pas encore attribuée, vous pouvez sélectionner Affecter à moi **pour** vous attribuer l’alerte.

## <a name="suppress-alerts"></a>Supprimer des alertes

Il peut y avoir des scénarios dans lequel vous devez supprimer l’apparition d’alertes dans Centre de sécurité Microsoft Defender. Defender pour le point de terminaison vous permet de créer des règles de suppression pour des alertes spécifiques qui sont connues comme étant superflues, telles que des outils ou des processus connus dans votre organisation.

Les règles de suppression peuvent être créées à partir d’une alerte existante. Elles peuvent être désactivées et réactivées si nécessaire.

Lorsqu’une règle de suppression est créée, elle prend effet à partir du moment où la règle est créée. La règle n’affecte pas les alertes existantes déjà dans la file d’attente, avant la création de la règle. La règle sera appliquée uniquement aux alertes qui répondent aux conditions définies après la création de la règle.

Vous pouvez choisir parmi deux contextes pour une règle de suppression :

- **Supprimer l’alerte sur cet appareil**
- **Supprimer une alerte dans mon organisation**

Le contexte de la règle vous permet d’adapter ce qui est mis en avant dans le portail et de vous assurer que seules les alertes de sécurité réelles sont sur le portail.

Vous pouvez utiliser les exemples du tableau suivant pour vous aider à choisir le contexte d’une règle de suppression :

|Contexte|Définition|Exemples de scénarios|
|---|---|---|
|**Supprimer l’alerte sur cet appareil**|Les alertes avec le même titre d’alerte et sur cet appareil spécifique seront supprimées uniquement. <p> Toutes les autres alertes de cet appareil ne seront pas supprimées.|<ul><li>Un chercheur en sécurité examine un script malveillant qui a été utilisé pour attaquer d’autres appareils de votre organisation.</li><li>Un développeur crée régulièrement des scripts PowerShell pour son équipe.</li></ul>|
|**Supprimer une alerte dans mon organisation**|Les alertes avec le même titre d’alerte sur n’importe quel appareil seront supprimées.|<ul><li>Un outil d’administration anodin est utilisé par tous les membres de votre organisation.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Supprimer une alerte et créer une règle de suppression

Créez des règles personnalisées pour contrôler quand les alertes sont supprimées ou résolues. Vous pouvez contrôler le contexte de suppression d’une alerte en spécifiant le titre de l’alerte, l’indicateur de compromis et les conditions. Après avoir spécifié le contexte, vous pourrez configurer l’action et l’étendue de l’alerte.

1. Sélectionnez l’alerte que vous souhaitez supprimer. Le volet gestion  des alertes s’en charge.

2. Sélectionnez **Créer une règle de suppression.**

    Vous pouvez créer une condition de suppression à l’aide de ces attributs. Un opérateur AND est appliqué entre chaque condition, de sorte que la suppression se produit uniquement si toutes les conditions sont remplies.

    - Fichier SHA1
    - Nom de fichier : caractère générique pris en charge
    - Chemin d’accès au dossier - caractère générique pris en charge
    - Adresse IP
    - URL : caractère générique pris en charge
    - Ligne de commande : caractère générique pris en charge

3. Sélectionnez **l’IOC déclenchant l’événement.**

4. Spécifiez l’action et l’étendue de l’alerte.

   Vous pouvez résoudre automatiquement une alerte ou la masquer sur le portail. Les alertes qui sont automatiquement résolues apparaissent dans la section résolue de la file d’attente, de la page d’alertes et de la chronologie de l’appareil, et apparaissent comme résolues dans les API Defender for Endpoint.

   Les alertes marquées comme masquées seront supprimées de l’ensemble du système, à la fois sur les alertes associées de l’appareil et à partir du tableau de bord et ne seront pas diffusées dans les API Defender for Endpoint.

5. Entrez un nom de règle et un commentaire.

6. Cliquez sur **Enregistrer**.

#### <a name="view-the-list-of-suppression-rules"></a>Afficher la liste des règles de suppression

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **suppression de l’alerte.**

2. La liste des règles de suppression affiche toutes les règles créées par les utilisateurs de votre organisation.

Pour plus d’informations sur la gestion des règles de suppression, voir [Gérer les règles de suppression](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Modifier l’état d’une alerte

Vous pouvez catégoriser les alertes **(comme Nouveau,** **En cours** ou **Résolu)** en modifiant leur état au fur et à mesure de l’avancement de votre enquête. Cela vous permet d’organiser et de gérer la façon dont votre équipe peut répondre aux alertes.

Par exemple, un responsable  d’équipe peut passer en revue  toutes les nouvelles alertes et décider de les affecter à la file d’attente En cours pour analyse approfondie.

Le responsable de l’équipe peut  également affecter l’alerte à la file d’attente résolue s’il sait que l’alerte est anodin, provenant d’un appareil non pertinent (par exemple, un appareil appartenant à un administrateur de sécurité) ou traité par le biais d’une alerte antérieure.

## <a name="alert-classification"></a>Classification de l’alerte

Vous pouvez choisir de ne pas définir de classification ou de spécifier si une alerte est une alerte vraie ou une fausse alerte. Il est important de fournir la classification du vrai positif/faux positif. Cette classification permet de surveiller la qualité des alertes et d’améliorer la précision des alertes. Le champ « détermination » définit une fidélité supplémentaire pour une classification « vrai positif ».

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Ajouter des commentaires et afficher l’historique d’une alerte

Vous pouvez ajouter des commentaires et afficher des événements historiques sur une alerte pour voir les modifications précédentes apportées à l’alerte.

Chaque fois qu’une modification ou un commentaire est apporté à une alerte, il est enregistré dans la section Commentaires et **historique.**

Les commentaires ajoutés apparaissent instantanément dans le volet.

## <a name="related-topics"></a>Voir aussi

- [Gérer des règles de suppression](manage-suppression-rules.md)
- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Examiner microsoft Defender pour les alertes de point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte Microsoft Defender pour le point de terminaison](investigate-files.md)
- [Examiner les appareils de la liste Microsoft Defender pour les appareils de point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour le point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Microsoft Defender pour le point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour le point de terminaison](investigate-user.md)
