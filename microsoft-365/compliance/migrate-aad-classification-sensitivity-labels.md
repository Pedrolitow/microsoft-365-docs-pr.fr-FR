---
title: Azure Active Directory classification et les étiquettes de sensibilité pour Microsoft 365 groupes
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
description: Cet article traite des étiquettes Azure Active Directory classification et de sensibilité classiques.
ms.openlocfilehash: 8999451af155462cbd2f4c08354b01115ac2763cb15da715d5a31ef7836a4d6b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53885830"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Azure Active Directory classification et les étiquettes de sensibilité pour Microsoft 365 groupes

Cet article traite des étiquettes Azure Active Directory classification et de sensibilité classiques.

Les étiquettes de sensibilité sont pris en charge [par ces services.](./sensitivity-labels-teams-groups-sites.md)

Pour obtenir des informations complètes sur les étiquettes de sensibilité, voir [En savoir plus sur les étiquettes de sensibilité.](sensitivity-labels.md)

Pour en savoir plus sur les étiquettes de sensibilité et leur comportement pour les sites et les groupes Microsoft 365, voir Utiliser des étiquettes de niveau de sensibilité pour protéger le contenu dans [les sites Microsoft Teams, Microsoft 365](sensitivity-labels-teams-groups-sites.md)et SharePoint sites.

Consultez les scénarios suivants pour obtenir les meilleures pratiques lors de la migration de la classification AAD classique vers les étiquettes de sensibilité.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scénario 1 : le client n’a jamais utilisé de classifications AAD classiques ou d’étiquettes de sensibilité pour les documents et les e-mails

- L’administrateur client active les étiquettes de niveau de sensibilité pour les groupes en fixant l’indicateur client « EnableMIPLabels » sur true via l’cmdlet PowerShell AAD.
- L’administrateur client crée les étiquettes de niveau de Centre de conformité Microsoft 365 [.](https://compliance.microsoft.com)
    - L’administrateur client peut choisir des actions liées aux fichiers et aux e-mails, telles que le chiffrement et le filigrane.
    - L’administrateur client peut choisir Microsoft 365 groupes et SharePoint actions liées au site en ligne aux étiquettes de niveau de sensibilité.
- L’administrateur client publie la stratégie.
- **Les charges de travail compatibles** indiquent les étiquettes de sensibilité. Utilisez les étiquettes de niveau de sensibilité pour créer des groupes. Les charges de travail compatibles sont les services qui la prise en charge des étiquettes de sensibilité.
- **Les charges de travail non compatibles** sont les services qui ne sont pas encore compatibles avec les étiquettes de sensibilité. Les groupes peuvent être créés, toutefois, ils ne peuvent pas être associés à l’étiquette de sensibilité par le biais de charges de travail non compatibles. Pour associer ces groupes à des étiquettes de niveau de sensibilité, les administrateurs client peuvent exécuter des cmdlets PowerShell.

Tableau 1. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes l’utilisateur voit-il dans la fenêtre de groupe ?|Créer un groupe |Modifier un groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Compatible   |étiquettes de sensibilité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Aucune étiquette de sensibilité n’est visible. |L’utilisateur peut créer un groupe sans sélectionner d’étiquette de sensibilité. <br><br> Notez que l’administrateur peut exécuter des cmdlets pour appliquer des étiquettes de niveau de sensibilité en arrière-plan. |**Cas 1 :** aucune étiquette de niveau de sensibilité précédemment sélectionnée. L’utilisateur peut modifier un groupe.<br><br> **Cas 2 :** étiquette de sensibilité appliquée précédemment en arrière-plan à l’aide de la cmdlet. L’utilisateur peut modifier un groupe avec succès, à l’exclusion du cas où l’utilisateur sélectionne une combinaison non valide de paramètres de confidentialité par rapport à l’étiquette. |Aucun changement de comportement.|

> [!NOTE]
> Dans le cas d’un client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de niveau de sensibilité sur son client et que son utilisateur est sur une version antérieure du client de bureau Outlook (Win 32) :
>
> - L’utilisateur voit les étiquettes de niveau de sensibilité apparaître sur l’ancienne version du client Outlook bureau.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de confidentialité, le paramètre de confidentialité sélectionné est modifié par le paramètre de confidentialité de l’étiquette de confidentialité appliquée.
>
> Nous recommandons à vos utilisateurs d’une ancienne version Outlook la mise à niveau du client vers la version la plus récente.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scénario 2 : le client utilise déjà des classifications AAD [classiques](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Cas A : le client n’a jamais utilisé d’étiquettes de niveau de sensibilité pour les documents et les e-mails

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), nous vous recommandons de créer des étiquettes de sensibilité avec le même nom que les étiquettes Azure AD classiques existantes.
2. Utilisez l’cmdlet PowerShell pour appliquer ces étiquettes de sensibilité aux groupes Microsoft 365 existants et SharePoint sites à l’aide du mappage de noms.
3. L’administrateur peut choisir de supprimer les étiquettes Azure AD classiques :
    - Les charges de travail compatibles montrent que ces étiquettes de sensibilité et groupes sont créés avec eux.
    - Les charges de travail non compatibles fonctionnent lors de la création de groupes, mais aucune étiquette de niveau de sensibilité n’est attachée à ces derniers.
4. Les administrateurs peuvent exécuter des cmdlets PowerShell pour appliquer des étiquettes de niveau de sensibilité à ces groupes sans étiquette.
    - Un administrateur peut également choisir de conserver les étiquettes Azure AD classiques :
        - Les charges de travail compatibles indiquent ces étiquettes de sensibilité et les groupes sont créés avec eux. Les charges de travail compatibles sont les services qui la prise en charge des étiquettes de sensibilité.
        - Les charges de travail non compatibles fonctionnent lors de la création de groupes et montrent les étiquettes Azure AD classiques. Ces étiquettes Azure AD classiques sont attachées à ces groupes créés avec des charges de travail non compatibles.
5. Nous recommandons vivement aux administrateurs d’exécuter des cmdlets PowerShell pour appliquer des étiquettes de niveau de sensibilité à ces groupes avec des étiquettes Azure AD classiques.

Tableau 2. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes l’utilisateur voit-il dans la fenêtre de groupe ?|Créer un groupe |Modifier un groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Compatible   |étiquettes de sensibilité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Anciennes étiquettes AAD classiques. |L’utilisateur peut créer un groupe avec l’étiquette Azure AD classique sélectionnée. <br><br>Notez que l’administrateur peut exécuter des cmdlets pour appliquer des étiquettes de niveau de sensibilité en arrière-plan. |**Cas 1 :** aucune étiquette de niveau de sensibilité précédemment sélectionnée. L’utilisateur peut modifier un groupe.<br><br> **Cas 2**: étiquettes AAD classiques précédemment sélectionnées. L’utilisateur peut modifier un groupe.<br><br> **Cas 3 :** étiquette de sensibilité précédemment appliquée en arrière-plan à l’aide de la cmdlet. L’utilisateur doit être en mesure de modifier un groupe, à l’exception d’un cas où l’utilisateur sélectionne une combinaison non valide de paramètres de confidentialité par rapport à l’étiquette. |L’utilisateur peut supprimer un groupe. |

> [!NOTE]
> Dans le cas d’un client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de niveau de sensibilité sur son client et que son utilisateur est sur une version antérieure du client de bureau Outlook (Win 32) :
>
> - L’utilisateur voit les étiquettes de niveau de sensibilité apparaître sur l’ancienne version du client Outlook bureau.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de confidentialité, le paramètre de confidentialité sélectionné est modifié par le paramètre de confidentialité de l’étiquette de confidentialité appliquée.
>
> Nous recommandons à vos utilisateurs d’une ancienne version Outlook la mise à niveau du client vers la version la plus récente.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Cas B : le client a utilisé des étiquettes de niveau de sensibilité pour les documents et les e-mails

1. Dès que l’administrateur active la fonctionnalité d’étiquette de niveau de sensibilité sur le client en élisant l’indicateur de client « EnableMIPLabels » sur true, les étiquettes de niveau de sensibilité du document et du courrier électronique dans les boîtes de dialogue de création et de modification de groupe/site/équipe s’affichent.
2. Un administrateur peut utiliser les mêmes étiquettes de confidentialité des documents et des e-mails pour appliquer la confidentialité et l’accès des utilisateurs externes au groupe/site/équipe en spécifiant les paramètres de groupe associés :
    1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)sélectionnez **l’onglet Sites et** groupes.
    2. Modifier une étiquette de sensibilité de document ou de courrier électronique.

## <a name="sample-script"></a>Exemple de script

Pour obtenir un exemple de script pour migrer des groupes avec des étiquettes AAD classiques vers des étiquettes de niveau de sensibilité, voir Classification de groupe [Azure AD classique.](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification)