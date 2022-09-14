---
title: Gérer les alertes Microsoft Defender pour point de terminaison
description: Modifiez l’état des alertes, créez des règles de suppression pour masquer les alertes, envoyez des commentaires et passez en revue l’historique des modifications pour les alertes individuelles avec le menu Gérer les alertes.
keywords: gérer les alertes, gérer, alertes, état, nouveau, en cours, résolu, résoudre les alertes, supprimer, supprimer, supprimer, règles, contexte, historique, commentaires, modifications
ms.service: microsoft-365-security
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
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 68cdc07ea2396910acdf3d86201db4b72f17f380
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67688519"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Gérer les alertes Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Defender pour point de terminaison vous avertit des événements malveillants, des attributs et des informations contextuelles possibles par le biais d’alertes. Un résumé des nouvelles alertes s’affiche dans le **tableau de bord Des opérations de sécurité** et vous pouvez accéder à toutes les alertes de la **file d’attente d’alertes**.

Vous pouvez gérer les alertes en sélectionnant une alerte dans la **file d’attente Alertes** ou l’onglet **Alertes** de la page Appareil pour un appareil individuel.

La sélection d’une alerte dans l’un ou l’autre de ces emplacements fait apparaître le **volet de gestion des alertes**.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Volet Gestion des alertes et file d’attente alertes" lightbox="images/atp-alerts-selected.png":::

Regardez cette vidéo pour découvrir comment utiliser la nouvelle page d’alerte Microsoft Defender pour point de terminaison.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4yiO5]

## <a name="link-to-another-incident"></a>Lien vers un autre incident

Vous pouvez créer un incident à partir de l’alerte ou d’un lien vers un incident existant.

## <a name="assign-alerts"></a>Attribuer des alertes

Si aucune alerte n’est encore attribuée, vous pouvez sélectionner **Affecter à moi pour vous** attribuer l’alerte.

## <a name="suppress-alerts"></a>Supprimer les alertes

Dans certains scénarios, vous devez supprimer l’affichage d’alertes dans Microsoft 365 Defender. Defender pour point de terminaison vous permet de créer des règles de suppression pour des alertes spécifiques qui sont connues pour être inoffensifs, telles que des outils ou des processus connus dans votre organisation.

Des règles de suppression peuvent être créées à partir d’une alerte existante. Ils peuvent être désactivés et réactivés si nécessaire.

Lorsqu’une règle de suppression est créée, elle prend effet à partir du moment où la règle est créée. La règle n’affecte pas les alertes existantes déjà dans la file d’attente, avant la création de la règle. La règle est appliquée uniquement aux alertes qui remplissent les conditions définies après la création de la règle.

Il existe deux contextes pour une règle de suppression parmi lesquels vous pouvez choisir :

- **Supprimer l’alerte sur cet appareil**
- **Supprimer une alerte dans mon organisation**

Le contexte de la règle vous permet d’adapter ce qui est exposé dans le portail et de vous assurer que seules les alertes de sécurité réelles sont exposées dans le portail.

Vous pouvez utiliser les exemples du tableau suivant pour choisir le contexte d’une règle de suppression :

|Contexte|Définition|Exemples de scénarios|
|---|---|---|
|**Supprimer l’alerte sur cet appareil**|Les alertes avec le même titre d’alerte et sur cet appareil spécifique seront supprimées uniquement. <p> Toutes les autres alertes sur cet appareil ne seront pas supprimées.|<ul><li>Un chercheur en sécurité étudie un script malveillant qui a été utilisé pour attaquer d’autres appareils de votre organisation.</li><li>Un développeur crée régulièrement des scripts PowerShell pour son équipe.</li></ul>|
|**Supprimer une alerte dans mon organisation**|Les alertes avec le même titre d’alerte sur n’importe quel appareil seront supprimées.|<ul><li>Un outil d’administration bénin est utilisé par tous les membres de votre organisation.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Supprimer une alerte et créer une règle de suppression

Créez des règles personnalisées pour contrôler quand les alertes sont supprimées ou résolues. Vous pouvez contrôler le contexte de suppression d’une alerte en spécifiant le titre de l’alerte, l’indicateur de compromission et les conditions. Après avoir spécifié le contexte, vous serez en mesure de configurer l’action et l’étendue sur l’alerte.

1. Sélectionnez l’alerte que vous souhaitez supprimer. Le volet **Gestion des alertes** s’affiche.

2. Sélectionnez **Créer une règle de suppression**.

    Vous pouvez créer une condition de suppression à l’aide de ces attributs. Un opérateur AND est appliqué entre chaque condition. Par conséquent, la suppression se produit uniquement si toutes les conditions sont remplies.

    - Fichier SHA1
    - Nom de fichier - caractère générique pris en charge
    - Chemin d’accès au dossier - caractère générique pris en charge
    - Adresse IP
    - URL - caractère générique pris en charge
    - Ligne de commande - caractère générique pris en charge

3. Sélectionnez le **ioc de déclenchement**.

4. Spécifiez l’action et l’étendue de l’alerte.

   Vous pouvez résoudre automatiquement une alerte ou la masquer à partir du portail. Les alertes qui sont automatiquement résolues apparaissent dans la section résolue de la file d’attente d’alertes, de la page d’alertes et de la chronologie de l’appareil et apparaissent comme résolues dans les API Defender pour point de terminaison.

   Les alertes marquées comme masquées seront supprimées de l’ensemble du système, à la fois sur les alertes associées de l’appareil et à partir du tableau de bord, et ne seront pas diffusées sur les API Defender pour point de terminaison.

5. Entrez un nom de règle et un commentaire.

6. Cliquez sur **Enregistrer**.

#### <a name="view-the-list-of-suppression-rules"></a>Afficher la liste des règles de suppression

1. Dans le volet de navigation, sélectionnez **Suppression des alertes de paramètres**\>.

2. La liste des règles de suppression affiche toutes les règles que les utilisateurs de votre organisation ont créées.

Pour plus d’informations sur la gestion des règles de suppression, consultez [Gérer les règles de suppression](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Modifier l’état d’une alerte

Vous pouvez catégoriser les alertes ( **nouvelles**, **en cours** ou **résolues**) en modifiant leur état à mesure que votre investigation progresse. Cela vous permet d’organiser et de gérer la façon dont votre équipe peut répondre aux alertes.

Par exemple, un responsable d’équipe peut examiner toutes les **nouvelles** alertes et décider de les affecter à la file d’attente **En cours** pour une analyse plus approfondie.

Le responsable de l’équipe peut également affecter l’alerte à la file d’attente **Résolue** s’il sait que l’alerte est sans gravité, provenant d’un appareil non pertinent (par exemple, appartenant à un administrateur de sécurité) ou traité par le biais d’une alerte antérieure.

## <a name="alert-classification"></a>Classification de l’alerte

Vous pouvez choisir de ne pas définir de classification ou de spécifier si une alerte est une alerte vraie ou une fausse alerte. Il est important de fournir la classification des vrais positifs/faux positifs. Cette classification est utilisée pour surveiller la qualité des alertes et rendre les alertes plus précises. Le champ « détermination » définit une fidélité supplémentaire pour une classification « vrai positif ».

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Ajouter des commentaires et afficher l’historique d’une alerte

Vous pouvez ajouter des commentaires et afficher des événements historiques sur une alerte pour voir les modifications précédentes apportées à l’alerte.

Chaque fois qu’une modification ou un commentaire est apporté à une alerte, il est enregistré dans la section **Commentaires et historique** .

Les commentaires ajoutés apparaissent instantanément dans le volet.

## <a name="related-topics"></a>Voir aussi

- [Gérer des règles de suppression](manage-suppression-rules.md)
- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Examiner les alertes Microsoft Defender pour point de terminaison](investigate-alerts.md)
- [Examiner un fichier associé à une alerte de Microsoft Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste des appareils Microsoft Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Microsoft Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte de Microsoft Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Microsoft Defender pour point de terminaison](investigate-user.md)
