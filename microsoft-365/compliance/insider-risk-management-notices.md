---
title: Modèles d’avis de gestion des risques initiés
description: Découvrez les modèles d’avis de gestion des risques inSided dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 92844691cba4adf39c7b4eee30de97ccff9d0890
ms.sourcegitcommit: 87cc278ea2ddcd536ecfaa3dfae9a5ddaa502cf9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42179085"
---
# <a name="insider-risk-management-notice-templates"></a>Modèles d’avis de gestion des risques initiés

Les modèles d’avis de gestion des risques initiés vous permettent d’envoyer des messages électroniques aux employés lorsque leurs activités génèrent une mise en correspondance et une alerte de stratégie. Dans la plupart des cas, les actions de l’employé qui génèrent des alertes résultent d’erreurs ou d’activités involontaires sans avoir de mal. Les notifications servent de rappels simples aux employés pour être plus prudents ou fournir des liens ou des informations pour les ressources de la formation ou de la stratégie d’entreprise. Les notifications peuvent être une partie importante de votre programme de formation interne et peuvent vous aider à créer une piste d’audit documentée pour les employés ayant des activités de risque récurrent.

Créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’employé associée à l’alerte spécifique en cours de révision. Lorsque vous sélectionnez un modèle d’avis à appliquer à une correspondance de stratégie, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou de remplacer les champs selon vos besoins.

## <a name="notice-templates-dashboard"></a>Tableau de bord modèles de notification

Le **tableau de bord des modèles d’avis** affiche une liste de modèles d’avis configurés et vous permet de créer des modèles d’avis. Les modèles d’avis sont répertoriés dans l’ordre de la date de contrepassation avec le modèle d’avis le plus récent répertorié en premier.

![Tableau de bord des modèles d’avis de gestion des risques initiés](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>HTML pour les notifications

Si vous souhaitez créer un message électronique en texte simple pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle de notification. L’exemple suivant fournit le format du corps des messages pour un modèle de notification par courrier électronique HTML de base :

```HTML
<!DOCTYPE html>
<html>
<body>
<h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
<p>A recent activity you've performed has generated a risk alert prohibited by the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
<p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
<p>Thank you,</p>
<p><em>Human Resources</em></p>
</body>
</html>
```

> [!NOTE]
> HTML href attribute Implementation dans les modèles d’avis sur la gestion des risques Insider prennent en charge uniquement les guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="create-a-new-notice-template"></a>Créer un nouveau modèle d’avis

Pour créer un modèle d’avis de gestion des risques inSided, vous allez utiliser l’Assistant d’avertissement dans la solution de **gestion des risques inSided** dans le centre de conformité Microsoft 365.

Procédez comme suit pour créer un modèle d’avis de gestion des risques Insider :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **modèles de notification** .
2. Sélectionnez **créer un modèle d’avis** pour ouvrir l’Assistant d’avertissement.
3. Sur la page **créer un nouveau modèle d’avis** , renseignez les champs suivants :
    - **Nom du modèle**: entrez un nom convivial pour l’avis. Ce nom apparaît dans la liste des notifications du tableau de bord d’avertissement et dans la liste de sélection des notifications lors de l’envoi de notifications à partir d’un cas.
    - **Envoyer de**: entrez l’adresse de messagerie de l’expéditeur pour l’avis. Cette adresse apparaît dans le champ **de :** de toutes les notifications envoyées aux employés, sauf si elles ont été modifiées lors de l’envoi d’une notification à partir d’un cas.
    - Champs **CC et BCC** : utilisateurs ou groupes facultatifs à avertir de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement.
    - **Objet**: informations qui s’affichent dans la ligne d’objet du message, prend en charge les caractères de texte.
    - **Corps du message**: informations qui s’affichent dans le corps du message, prend en charge le texte ou les valeurs html.
4. Sélectionnez **créer** pour créer et enregistrer le modèle d’avis, ou cliquez sur **Annuler** pour fermer sans enregistrer le modèle d’avis.

## <a name="update-a-notice-template"></a>Mettre à jour un modèle d’avis

Pour mettre à jour un modèle d’avis de gestion des risques inSided existant, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **modèles de notification** .
2. Dans le tableau de bord d’avis, sélectionnez le modèle d’avis que vous souhaitez gérer.
3. Sur la page Détails de l’avis, sélectionnez **modifier** .
4. Sur la page de **modification** , vous pouvez modifier les champs suivants :
    - **Nom du modèle**: entrez un nouveau nom convivial pour l’avis. Ce nom apparaît dans la liste des notifications du tableau de bord d’avertissement et dans la liste de sélection des notifications lors de l’envoi de notifications à partir d’un cas.
    - **Envoyer de**: mettez à jour l’adresse de messagerie de l’expéditeur pour l’avis. Cette adresse apparaît dans le champ **de :** de toutes les notifications envoyées aux employés, sauf si elles ont été modifiées lors de l’envoi d’une notification à partir d’un cas.
    - Champs **CC et CCI** : mettre à jour des utilisateurs ou des groupes facultatifs pour être informés de la correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement.
    - **Subject**: mettre à jour les informations qui s’affichent dans la ligne d’objet du message, prend en charge les caractères de texte.
    - **Corps du message**: mettre à jour les informations qui s’affichent dans le corps du message, prend en charge le texte ou les valeurs html.
5. Sélectionnez **Enregistrer** pour mettre à jour et enregistrer l’avis ou sélectionnez **Annuler** pour fermer sans enregistrer le modèle d’avis.

## <a name="delete-a-notice-template"></a>Supprimer un modèle d’avertissement

Pour supprimer un modèle d’avis de gestion des risques inSided existant, procédez comme suit :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **modèles de notification** .
2. Dans le tableau de bord d’avis, sélectionnez le modèle d’avertissement que vous souhaitez supprimer.
3. Sélectionnez l’icône de **suppression** dans la barre d’outils.
4. Pour supprimer le modèle d’avertissement, sélectionnez **Oui** dans la boîte de dialogue Supprimer. Pour annuler la suppression, sélectionnez **Annuler**.
