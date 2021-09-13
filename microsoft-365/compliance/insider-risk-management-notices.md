---
title: Modèles de notifications sur la gestion des risques internes
description: Découvrez les modèles de notification de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 786878e827fed6318a70501e400a719ad9181835
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59206244"
---
# <a name="insider-risk-management-notice-templates"></a>Modèles de notifications sur la gestion des risques internes

Les modèles d’avis de gestion des risques internes vous permettent d’envoyer des messages électroniques aux utilisateurs lorsque leurs activités génèrent une correspondance et une alerte de stratégie. Dans la plupart des cas, les actions de l’utilisateur qui génèrent des alertes sont le résultat d’erreurs ou d’activités accidentelles sans intention malveillante. Les notifications servent de rappels simples aux utilisateurs pour qu’ils soient plus prudents, qu’ils fournissent des liens vers des informations pour la formation à l’actualisation ou vers des ressources de stratégie d’entreprise. Les avis peuvent constituer une partie importante de votre programme de formation sur la conformité interne et peuvent vous aider à créer une piste d’audit documentée pour les utilisateurs avec des activités à risque périodique.

Créez des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’utilisateur associée à l’alerte spécifique en cours de révision. Lorsque vous sélectionnez un modèle d’avis à appliquer à une correspondance de stratégie, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou de les réécrire selon vos besoins.

## <a name="notice-templates-dashboard"></a>Tableau de bord des modèles d’avis

Le **Tableau de bord modèles de notifications** affiche une liste de modèles de notifications configurés et vous permet de créer des modèles de notifications. Les modèles de notifications sont répertoriés à l’aide du modèle de notifications le plus récent répertorié en premier.

![Tableau de bord du modèle de notification de gestion des risques internes.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>HTML pour les notifications

Si vous souhaitez créer plus qu’un simple message électronique texte pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle d’avis. L’exemple suivant fournit le format du corps du message pour un modèle de notification par courrier électronique html de base :

```HTML
<!DOCTYPE html>
<html>
<body>
<h2>Action Required: Contoso User Code of Conduct Policy Training</h2>
<p>A recent activity you've performed has generated a risk alert prohibited by the Contoso User <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
<p>You are required to attend the Contoso User Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
<p>Thank you,</p>
<p><em>Human Resources</em></p>
</body>
</html>
```

> [!NOTE]
> L’implémentation d’attribut href HTML dans les modèles d’avis de gestion des risques internes ne permet actuellement de prendre en charge que des guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="create-a-new-notice-template"></a>Créer un modèle d’avis

Pour créer un modèle de notification de gestion des risques internes, vous utiliserez l’Assistant Notification dans la **solution** de gestion des risques internes dans le Centre de conformité Microsoft 365.

Pour créer un modèle d’avis de gestion des risques internes, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)sélectionnez l’onglet **Modèles d’avis** sur la gestion des risques internes. 
2. Sélectionnez **Créer un modèle de notification** pour ouvrir l’Assistant Notification.
3. Dans la page **Créer un modèle d’avis,** complétez les champs suivants :
    - **Nom du modèle**: entrez un nom convivial pour l’avis. Ce nom apparaît dans la liste des notifications dans le tableau de bord de notification et dans la liste de sélection des notifications lors de l’envoi d’avis à partir d’un cas.
    - **Envoyer à partir** de : Entrez l’adresse e-mail de l’expéditeur pour l’avis. Cette adresse apparaît dans le champ **De :** dans toutes les notifications envoyées aux utilisateurs, sauf si elle est modifiée lors de l’envoi d’une notification à partir d’un cas.
    - Champs Cc et **Cci** : utilisateurs ou groupes facultatifs à notifiés de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement.
    - **Objet**: les informations qui apparaissent dans la ligne d’objet du message, prend en charge les caractères de texte.
    - **Corps du message**: informations qui apparaissent dans le corps du message, prend en charge les valeurs texte ou HTML.
4. Sélectionnez **Créer** pour créer et enregistrer le modèle d’avis ou sélectionnez **Annuler** pour fermer sans enregistrer le modèle d’avis.

## <a name="update-a-notice-template"></a>Mettre à jour un modèle d’avis

Pour mettre à jour un modèle de notification de gestion des risques internes existant, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)sélectionnez l’onglet **Modèles d’avis** sur la gestion des risques internes. 
2. Dans le tableau de bord de notification, sélectionnez le modèle de notification que vous souhaitez gérer.
3. Dans la page Détails de l’avis, sélectionnez **Modifier**
4. Dans la page **Modifier,** vous pouvez modifier les champs suivants :
    - **Nom du modèle**: entrez un nouveau nom convivial pour l’avis. Ce nom apparaît dans la liste des notifications dans le tableau de bord de notification et dans la liste de sélection des notifications lors de l’envoi d’avis à partir d’un cas.
    - **Envoyer à partir de**: mettre à jour l’adresse e-mail de l’expéditeur pour l’avis. Cette adresse apparaît dans le champ **De :** dans toutes les notifications envoyées aux utilisateurs, sauf si elle est modifiée lors de l’envoi d’une notification à partir d’un cas.
    - Champs Cc et **Cci** : mettez à jour les utilisateurs ou groupes facultatifs pour être avertis de la correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement.
    - **Objet**: mettre à jour les informations qui apparaissent dans la ligne d’objet du message, prend en charge les caractères de texte.
    - **Corps du message**: mettre à jour les informations qui apparaissent dans le corps du message, prend en charge les valeurs texte ou HTML.
5. Sélectionnez **Enregistrer** pour mettre à jour et enregistrer l’avis ou sélectionnez **Annuler** pour fermer sans enregistrer le modèle d’avis.

## <a name="delete-a-notice-template"></a>Supprimer un modèle d’avis

Pour supprimer un modèle de notification de gestion des risques internes existant, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)sélectionnez l’onglet **Modèles d’avis** sur la gestion des risques internes. 
2. Dans le tableau de bord de notification, sélectionnez le modèle de notification à supprimer.
3. Sélectionnez **l’icône** Supprimer dans la barre d’outils.
4. Pour supprimer le modèle d’avis, sélectionnez **Oui** dans la boîte de dialogue de suppression. Pour annuler la suppression, sélectionnez **Annuler**.
