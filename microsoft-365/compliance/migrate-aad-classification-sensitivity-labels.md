---
title: Étiquettes de classification et de sensibilité AAD pour les groupes Microsoft 365
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: Cet article traite des étiquettes de confidentialité et de classification Azure Active Directory classiques.
ms.openlocfilehash: 260b71d703f2534e5e2ddcf4ef45fe28a914eeab
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623780"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Étiquettes de classification et de sensibilité Azure Active Directory pour les groupes Microsoft 365

Cet article traite des étiquettes de confidentialité et de classification Azure Active Directory classiques.

Ces [services](./sensitivity-labels-teams-groups-sites.md) prennent en charge les étiquettes de confidentialité.

Pour obtenir des informations complètes sur les étiquettes de confidentialité, consultez [En savoir plus sur les étiquettes de confidentialité](sensitivity-labels.md).

Pour en savoir plus sur les étiquettes de confidentialité et leur comportement pour les sites et les groupes Microsoft 365, consultez [Utiliser des étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md).

Consultez les scénarios suivants pour connaître les meilleures pratiques lors de la migration de la classification AAD classique vers les étiquettes de confidentialité.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scénario 1 : Le locataire n’a jamais utilisé de classifications AAD classiques ou d’étiquettes de confidentialité pour les documents et les e-mails

- Tenant Administration active les étiquettes de confidentialité pour les groupes en définissant l’indicateur de locataire « EnableMIPLabels » sur true via l’applet de commande powershell AAD.
- Le Administration de locataire crée les étiquettes de confidentialité dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com).
    - L’administrateur client peut choisir des actions liées aux fichiers et aux e-mails, telles que le chiffrement et le filigrane.
    - L’administrateur client peut choisir Groupes Microsoft 365 et les actions liées au site SharePoint Online aux étiquettes de confidentialité.
- Le client Administration publie la stratégie.
- **Les charges de travail compatibles affichent des** étiquettes de confidentialité. Utilisez les étiquettes de confidentialité pour créer des groupes. Les charges de travail compatibles sont les services qui prennent en charge les étiquettes de confidentialité.
- **Les charges de travail non compatibles sont les** services qui ne prennent pas encore en charge les étiquettes de confidentialité. Les groupes peuvent être créés, mais ils ne peuvent pas être associés à l’étiquette de confidentialité via des charges de travail non compatibles. Pour associer ces groupes à des étiquettes de confidentialité, les administrateurs de locataires peuvent exécuter des applets de commande PowerShell.

Tableau 1. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes l’utilisateur voit-il dans la fenêtre de groupe ?|Créer un groupe |Modifier le groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Compatible   |étiquettes de confidentialité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Aucune étiquette de confidentialité visible. |L’utilisateur peut créer un groupe sans sélectionner l’étiquette de confidentialité. <br><br> Notez que l’administrateur peut exécuter des applets de commande pour appliquer des étiquettes de confidentialité en arrière-plan. |**Cas 1** : Aucune étiquette de confidentialité précédemment sélectionnée. L’utilisateur peut modifier un groupe.<br><br> **Cas 2** : étiquette de sensibilité appliquée précédemment en arrière-plan à l’aide de l’applet de commande. L’utilisateur peut modifier un groupe avec succès, à l’exception du cas où l’utilisateur sélectionne une combinaison non valide du paramètre de confidentialité en ce qui concerne l’étiquette. |Aucun changement de comportement.|

> [!NOTE]
> Dans le cas du client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de confidentialité sur son locataire et que son utilisateur se trouve sur une version antérieure du client de bureau Outlook (Win 32) :
>
> - L’utilisateur voit les étiquettes de confidentialité apparaître sur l’ancienne version du client de bureau Outlook.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de confidentialité, le paramètre de confidentialité sélectionné est remplacé par le paramètre de confidentialité de l’étiquette de confidentialité appliquée.
>
> Nous vous recommandons de mettre à niveau vos utilisateurs sur une ancienne version du client Outlook vers la version la plus récente.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scénario 2 : Le locataire utilise déjà [des classifications AAD classiques](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Cas A : Le locataire n’a jamais utilisé d’étiquettes de confidentialité pour les documents et les e-mails

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), nous vous recommandons de créer des étiquettes de confidentialité portant le même nom que les étiquettes Azure AD classiques existantes.
2. Utilisez l’applet de commande PowerShell pour appliquer ces étiquettes de confidentialité aux groupes Microsoft 365 existants et aux sites SharePoint à l’aide du mappage de noms.
3. Administration pouvez choisir de supprimer les étiquettes Azure AD classiques :
    - Les charges de travail compatibles montrent que ces étiquettes de confidentialité et ces groupes sont créés avec eux.
    - Les charges de travail non compatibles fonctionnent lors de la création de groupes, mais aucune étiquette de confidentialité n’y est attachée.
4. Les administrateurs peuvent exécuter des applets de commande PowerShell pour appliquer des étiquettes de confidentialité à ces groupes sans étiquettes.
    - Un administrateur peut également choisir de conserver les étiquettes Azure AD classiques :
        - Les charges de travail compatibles affichent ces étiquettes de confidentialité et des groupes sont créés avec eux. Les charges de travail compatibles sont les services qui prennent en charge les étiquettes de confidentialité.
        - Les charges de travail non compatibles fonctionnent lors de la création de groupes et affichent des étiquettes Azure AD classiques. Ces étiquettes Azure AD classiques sont attachées à ces groupes créés avec des charges de travail non compatibles.
5. Nous recommandons vivement aux administrateurs d’exécuter des applets de commande PowerShell pour appliquer des étiquettes de confidentialité à ces groupes avec des étiquettes Azure AD classiques.

Tableau 2. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes l’utilisateur voit-il dans la fenêtre de groupe ?|Créer un groupe |Modifier le groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Compatible   |étiquettes de confidentialité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Anciennes étiquettes AAD classiques. |L’utilisateur peut créer un groupe avec l’étiquette Azure AD classique sélectionnée. <br><br>Notez que l’administrateur peut exécuter des applets de commande pour appliquer des étiquettes de confidentialité en arrière-plan. |**Cas 1** : Aucune étiquette de confidentialité précédemment sélectionnée. L’utilisateur peut modifier un groupe.<br><br> **Cas 2** : Étiquettes AAD classiques précédemment sélectionnées. L’utilisateur peut modifier un groupe.<br><br> **Cas 3** : étiquette de confidentialité précédemment appliquée en arrière-plan à l’aide de l’applet de commande. L’utilisateur doit être en mesure de modifier un groupe, à l’exception d’un cas où l’utilisateur sélectionne une combinaison non valide du paramètre de confidentialité par rapport à l’étiquette. |L’utilisateur peut supprimer un groupe. |

> [!NOTE]
> Dans le cas du client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de confidentialité sur son locataire et que son utilisateur se trouve sur une version antérieure du client de bureau Outlook (Win 32) :
>
> - L’utilisateur voit les étiquettes de confidentialité apparaître sur l’ancienne version du client de bureau Outlook.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de confidentialité, le paramètre de confidentialité sélectionné est remplacé par le paramètre de confidentialité de l’étiquette de confidentialité appliquée.
>
> Nous vous recommandons de mettre à niveau vos utilisateurs sur une ancienne version du client Outlook vers la version la plus récente.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Cas B : Le locataire a utilisé des étiquettes de confidentialité pour les documents et les e-mails

1. Dès que l’administrateur active la fonctionnalité d’étiquette de confidentialité sur le locataire en définissant l’indicateur de locataire « EnableMIPLabels » sur true, les étiquettes de confidentialité du document et de l’e-mail dans les boîtes de dialogue de création et de modification de groupe/site/équipe s’affichent.
2. Un administrateur peut utiliser les mêmes étiquettes de confidentialité des documents et des e-mails pour appliquer la confidentialité et l’accès des utilisateurs externes sur le groupe/site/équipe en spécifiant les paramètres de groupe associés :
    1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), sélectionnez l’onglet **Sites et groupes**.
    2. Modifiez une étiquette de confidentialité de document ou d’e-mail.

## <a name="sample-script"></a>Exemple de script

Pour obtenir un exemple de script permettant de migrer des groupes avec des étiquettes AAD classiques vers des étiquettes de confidentialité, consultez [classification de groupe Azure AD classique](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).
