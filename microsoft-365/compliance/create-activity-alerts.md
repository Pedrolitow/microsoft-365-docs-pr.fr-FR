---
title: Créer des alertes d’activité
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 11/7/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MED150
- BCS160
- MET150
ms.assetid: 72bbad69-035b-4d33-b8f4-549a2743e97d
ROBOTS: NOINDEX, NOFOLLOW
description: Ajouter et gérer des alertes d’activité dans le portail de conformité Microsoft Purview afin que Microsoft 365 vous envoie des notifications par e-mail lorsque les utilisateurs effectuent des activités spécifiques
ms.openlocfilehash: b08c23ec80562418112266d03c58f4b764a128ba
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018094"
---
# <a name="create-activity-alerts"></a>Créer des alertes d’activité

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez créer une alerte d’activité qui vous enverra une notification par e-mail lorsque les utilisateurs effectuent des activités spécifiques dans Office 365. Les alertes d’activité sont similaires à la recherche d’événements dans le journal d’audit, sauf que vous recevrez un e-mail lorsqu’un événement pour une activité pour laquelle vous avez créé une alerte se produit.

 **Pourquoi utiliser des alertes d’activité au lieu de rechercher dans le journal d’audit ?** Il peut y avoir certains types d’activités ou d’activités effectuées par des utilisateurs spécifiques que vous souhaitez vraiment connaître. Au lieu de vous rappeler de rechercher ces activités dans le journal d’audit, vous pouvez utiliser des alertes d’activité pour Microsoft 365 vous envoyer un e-mail lorsque les utilisateurs effectuent ces activités. Par exemple, vous pouvez créer une alerte d’activité pour vous avertir lorsqu’un utilisateur supprime des fichiers dans SharePoint, ou vous pouvez créer une alerte pour vous avertir lorsqu’un utilisateur supprime définitivement des messages de sa boîte aux lettres. La notification par e-mail qui vous est envoyée inclut des informations sur l’activité qui a été effectuée et l’utilisateur qui l’a effectuée.

> [!NOTE]
> Les alertes d’activité sont déconseillées. Nous vous recommandons de commencer à utiliser des stratégies d’alerte dans le Centre de sécurité et de conformité au lieu de créer des alertes d’activité. Les stratégies d’alerte fournissent des fonctionnalités supplémentaires, telles que la possibilité de créer une stratégie d’alerte qui déclenche une alerte quand un utilisateur effectue une activité spécifiée, et d’afficher des alertes sur la page **Afficher les alertes** dans le Centre de sécurité et de conformité. Pour plus d’informations, consultez [Stratégies d’alerte](alert-policies.md).

## <a name="confirm-roles-and-configure-audit-logging"></a>Confirmer les rôles et configurer la journalisation d’audit

- Le rôle Configuration de l’organisation doit vous être attribué dans le portail de conformité Microsoft Purview pour gérer les alertes d’activité. Par défaut, ce rôle est attribué aux groupes de rôles Administrateur de conformité et Gestion de l’organisation. Pour plus d’informations sur l’ajout de membres à des groupes de [rôles, consultez Donner aux utilisateurs l’accès au portail de conformité Microsoft Purview](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

- Vous (ou un autre administrateur) devez d’abord activer la journalisation d’audit pour votre organisation avant de pouvoir commencer à utiliser des alertes d’activité. Pour ce faire, cliquez simplement sur **Démarrer l’enregistrement de l’activité de l’utilisateur et de l’administrateur** dans la page **Alertes d’activité** . (Si vous ne voyez pas ce lien, l’audit a déjà été activé pour votre organisation.) Vous pouvez également activer l’audit sur la page **Recherche de journal d’audit** dans le portail de conformité (accédez à **Audit**). Vous n’avez à le faire qu’une seule fois pour votre organisation.

- Vous pouvez créer des alertes pour les mêmes activités que celles que vous pouvez rechercher dans le journal d’audit. Consultez la section [Plus d’informations](#more-information) pour obtenir la liste des scénarios courants (et l’activité spécifique à surveiller) pour lesquelles vous pouvez créer des alertes.

- Vous pouvez utiliser la page **Alertes d’activité** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a> pour créer des alertes uniquement pour les activités effectuées par les utilisateurs répertoriés dans le carnet d’adresses de votre organisation. Vous ne pouvez pas utiliser cette page pour créer des alertes pour les activités effectuées par des utilisateurs externes qui ne sont pas répertoriés dans le carnet d’adresses.

## <a name="create-an-activity-alert"></a>Créer une alerte d’activité

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a>.

2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.

3. Dans la page **Alertes d’activité** , cliquez sur ![l’icône Ajouter.](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Nouveau**.

   La page de menu volant pour créer une alerte d’activité s’affiche.


    ![Créez une alerte d’activité.](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. Renseignez les champs suivants pour créer une alerte d’activité :

    1. **Nom** : tapez un nom pour l’alerte. Les noms d’alerte doivent être uniques au sein de votre organisation.

    1. **Description** (facultatif) : décrivez l’alerte, comme les activités et les utilisateurs suivis et les utilisateurs auxquels les notifications par e-mail sont envoyées. Les descriptions fournissent un moyen rapide et facile de décrire l’objectif de l’alerte à d’autres administrateurs.

    1. **Type d’alerte** : assurez-vous que l’option **Personnalisée** est sélectionnée.

    1. **Envoyez cette alerte quand** - Cliquez sur **Envoyer cette alerte quand** , puis configurez ces deux champs :

       - **Activités** : cliquez sur la liste déroulante pour afficher les activités pour lesquelles vous pouvez créer une alerte. Il s’agit de la même liste d’activités que celle affichée lorsque vous effectuez une recherche dans le journal d’audit. Vous pouvez sélectionner une ou plusieurs activités spécifiques, ou cliquer sur le nom du groupe d’activités pour sélectionner toutes les activités du groupe. Pour obtenir une description de ces activités, consultez la section « Activités auditées » dans [le journal d’audit](search-the-audit-log-in-security-and-compliance.md#audited-activities). Lorsqu’un utilisateur effectue l’une des activités que vous avez ajoutées à l’alerte, une notification par e-mail est envoyée.

       - **Utilisateurs** : cliquez sur cette zone, puis sélectionnez un ou plusieurs utilisateurs. Si les utilisateurs de cette zone effectuent les activités que vous avez ajoutées à la zone **Activités** , une alerte est envoyée. Laissez la zone **Utilisateurs** vide pour envoyer une alerte quand un utilisateur de votre organisation effectue les activités spécifiées par l’alerte.

    1. **Envoyer cette alerte :** cliquez sur **Envoyer cette alerte**, puis cliquez dans la zone **Destinataires** et tapez un nom pour ajouter des utilisateurs qui recevront une notification par e-mail lorsqu’un utilisateur (spécifié dans la zone **Utilisateurs** ) effectue une activité (spécifiée dans la zone **Activités** ). Notez que vous êtes ajouté à la liste des destinataires par défaut. Vous pouvez supprimer votre nom de cette liste.

5. Cliquez sur **Enregistrer** pour créer l’alerte.

    La nouvelle alerte s’affiche dans la liste de la page **Alertes d’activité** .

    ![Une liste d’alertes s’affiche sur la page Alertes d’activité.](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    L’état de l’alerte est **activé.** Notez que les destinataires qui recevront une notification par e-mail lorsqu’une alerte est envoyée sont également répertoriés.

## <a name="turn-off-an-activity-alert"></a>Désactiver une alerte d’activité

Vous pouvez désactiver une alerte d’activité afin qu’aucune notification par e-mail ne soit envoyée. Une fois que vous avez désactivé l’alerte d’activité, elle est toujours affichée dans la liste des alertes d’activité pour votre organisation, et vous pouvez toujours afficher ses propriétés.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a>.

2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.

3. Dans la liste des alertes d’activité pour votre organisation, cliquez sur l’alerte que vous souhaitez désactiver.

4. Dans la page **Modifier l’alerte** , cliquez sur le bouton bascule **Activé** pour désactiver l’état **, puis** cliquez sur **Enregistrer**.

    L’état de l’alerte sur les pages **Alertes d’activité** est défini sur **Désactivé**.

Pour réactiver une alerte d’activité, répétez ces étapes, puis cliquez sur le bouton bascule **Désactivé** pour activer l’état **.**

## <a name="more-information"></a>Plus d’informations

- Voici un exemple de notification par e-mail envoyée aux utilisateurs spécifiés dans le champ Envoyé cette alerte (et répertoriée sous **Destinataires** sur la page **Alertes d’activité** ) dans le portail de conformité.

    ![Exemple de notification par e-mail envoyée pour une alerte d’activité.](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- Voici quelques activités courantes de document et d’e-mail pour lesquelles vous pouvez créer des alertes d’activité. Les tables décrivent l’activité, le nom de l’activité pour laquelle créer une alerte et le nom du groupe d’activités sous lequel l’activité est répertoriée dans la liste **déroulante Activités** . Pour afficher la liste complète des activités pour lesquelles vous pouvez créer des alertes d’activité, consultez la section « Activités auditées » dans [le journal d’audit](search-the-audit-log-in-security-and-compliance.md#audited-activities).

    > [!TIP]
    > Vous pouvez créer une alerte d’activité pour une seule activité effectuée par n’importe quel utilisateur. Vous pouvez également créer une alerte d’activité qui suit plusieurs activités effectuées par un ou plusieurs utilisateurs.

    Le tableau suivant répertorie certaines activités courantes liées aux documents dans SharePoint ou OneDrive Entreprise.

    | Lorsqu’un utilisateur effectue cette opération... | Créer une alerte pour cette activité | Groupe d’activités |
    |:-----|:-----|:-----|
    |Affiche un document sur un site.  |Fichier consulté  |Activités de fichiers et de dossiers  |
    |Modifie ou modifie un document.  |Fichier modifié  |Activités de fichiers et de dossiers  |
    |Partage un document avec un utilisateur extérieur à votre organisation.  |Partager un fichier, un dossier ou un site  <br/> And  <br/> Invitation de partage créée  <br/> Pour plus d’informations, voir [Utiliser l’audit du partage dans le journal d’audit](use-sharing-auditing.md).  |Activités de demande d’accès et de partage  |
    |Charge ou télécharge un document.  |Fichier téléchargé  <br/> Et/ou  <br/> Fichier téléchargé  |Activités de fichiers et de dossiers  |
    |Modifie les autorisations d’accès à un site.  |Autorisations de site modifiées  |Activités d’administration des sites  |

    Le tableau suivant répertorie certaines activités courantes liées à l’e-mail dans Exchange Online.

    | Lorsqu’un utilisateur effectue cette opération... | Créer une alerte pour cette activité | Groupe d’activités |
    |:-----|:-----|:-----|
    |Supprime définitivement (vide) un message électronique de sa boîte aux lettres.  |Messages supprimés de la boîte aux lettres  | Activités de la boîte aux lettres Exchange  |
    |Envoie un e-mail à partir d’une boîte aux lettres partagée.  |Message envoyé à l’aide d’autorisations Envoyer en tant que  <br/> And  <br/> Message envoyé à l’aide d’autorisations Envoyer de la part de  | Activités de la boîte aux lettres Exchange  |

- Vous pouvez également utiliser les applets de commande **New-ActivityAlert** et **Set-ActivityAlert** dans Security & Compliance PowerShell pour créer et modifier des alertes d’activité. Gardez à l’esprit les éléments suivants si vous utilisez ces applets de commande pour créer ou modifier des alertes d’activité :

  - Si vous utilisez une applet de commande pour ajouter une activité à l’alerte qui n’est pas répertoriée dans la liste **déroulante Activités** , un message s’affiche dans la page de propriétés de l’alerte indiquant « Cette alerte comporte des opérations personnalisées qui ne sont pas répertoriées dans le sélecteur ».

  - Une bonne raison d’utiliser les applets de commande pour créer ou modifier une alerte d’activité consiste à envoyer des notifications par e-mail à une personne externe à votre organisation. Cet utilisateur externe est répertorié dans la liste des destinataires de l’alerte. Toutefois, si vous supprimez cet utilisateur externe de l’alerte, il ne peut pas être ajouté à nouveau à l’alerte à l’aide de la page **Modifier l’alerte** . Vous devrez rajouter l’utilisateur externe à l’aide de l’applet de commande **Set-ActivityAlert** ou utiliser l’applet de commande **New-ActivityAlert** pour ajouter le même utilisateur externe (ou différent) à une nouvelle alerte.
