---
title: Étiquettes de sensibilité et de classification Azure Active Directory pour les groupes Microsoft 365
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: o365-seccomp
localization_priority: Normal
description: Cet article traite des étiquettes de confidentialité et de classification Azure Active Directory classiques.
ms.openlocfilehash: f11473653884392048d5f9a84f8e284dba5f6f27
ms.sourcegitcommit: 2acd9ec5e9d150389975e854c7883efc186a9432
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "44755388"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Étiquettes de sensibilité et de classification Azure Active Directory pour les groupes Microsoft 365

Cet article traite des étiquettes de confidentialité et de classification Azure Active Directory classiques.

Les étiquettes de sensibilité sont prises en charge par [ces services](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites#support-for-the-sensitivity-labels).

Pour plus d’informations sur les étiquettes de sensibilité, voir [en savoir plus sur les étiquettes de sensibilité](sensitivity-labels.md).

Pour en savoir plus sur les étiquettes de sensibilité et leur comportement pour les sites et les groupes Microsoft 365, reportez-vous à la rubrique [utiliser des étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes microsoft 365 et les sites SharePoint](sensitivity-labels-teams-groups-sites.md).

Consultez les scénarios suivants pour les meilleures pratiques lors de la migration de la classification AAD classique vers les étiquettes de confidentialité.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scénario 1 : le client n’a jamais utilisé les classifications AAD classiques ni les étiquettes de confidentialité pour les documents et les e-mails

- L’administrateur client Active les étiquettes de sensibilité pour les groupes en définissant l’indicateur de client « EnableMIPLabels » sur true via une applet de commande PowerShell das.
- L’administrateur client crée les étiquettes de confidentialité dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com).
    - L’administrateur client peut choisir les actions de fichier et de messagerie telles que le chiffrement et le filigrane.
    - L’administrateur client peut choisir les groupes Microsoft 365 et les actions liées au site SharePoint Online pour les étiquettes de confidentialité.
- L’administrateur client publie la stratégie.
- Les **charges de travail compatibles** affichent les étiquettes de sensibilité. Utilisez les étiquettes de confidentialité pour créer des groupes. Les charges de travail compatibles sont les services qui prennent en charge les étiquettes de sensibilité.
- Les **charges de travail non compatibles** sont les services qui ne prennent pas encore en charge les étiquettes de sensibilité. Les groupes peuvent toutefois être créés, mais ils ne peuvent pas être associés à l’étiquette de sensibilité par le biais de charges de travail non compatibles. Pour associer ces groupes à des étiquettes de confidentialité, les administrateurs du client peuvent exécuter des applets de commande PowerShell.

Tableau 1. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes est visible par l’utilisateur dans la fenêtre de groupe ?|Créer un groupe |Modifier un groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Conforme   |étiquettes de sensibilité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Étiquettes de confidentialité invisibles. |Un utilisateur peut créer un groupe sans sélectionner l’étiquette de confidentialité. <br><br> Remarque : l’administrateur peut exécuter des cmdlets pour appliquer des étiquettes de sensibilité en arrière-plan. |**Cas 1**: étiquette de confidentialité précédemment sélectionnée. Un utilisateur peut modifier un groupe.<br><br> **Cas 2**: étiquette de sensibilité appliquée précédemment en arrière-plan à l’aide de l’applet de commande. Un utilisateur peut modifier un groupe avec succès, à l’exception du cas où l’utilisateur sélectionne une combinaison non valide de paramètre de confidentialité par rapport à l’étiquette. |Aucun changement de comportement.|

> [!NOTE]
> Dans le cas du client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de sensibilité sur son client, et que son utilisateur se trouve sur une version plus ancienne du client de bureau Outlook (Win 32) :
> - L’utilisateur voit des étiquettes de confidentialité apparaître sur l’ancienne version du client de bureau Outlook.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de sensibilité, le paramètre de confidentialité sélectionné est remplacé par le paramètre de confidentialité de l’étiquette de sensibilité appliquée.
> Nous recommandons à vos utilisateurs sur une ancienne version du client Outlook de procéder à la mise à niveau vers la version la plus récente.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scénario 2 : le client utilise déjà les [classifications](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell#create-classifications-for-office-groups-in-your-organization) AAD classiques

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Cas A : le client n’A jamais utilisé d’étiquettes de confidentialité pour les documents et les e-mails

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), nous vous recommandons de créer des étiquettes de confidentialité portant le même nom que les étiquettes Azure ad classiques existantes.
2. Utilisez l’applet de commande PowerShell pour appliquer ces étiquettes de confidentialité aux groupes et sites SharePoint Microsoft 365 existants à l’aide du mappage de nom.
3. L’administrateur peut choisir de supprimer les étiquettes Azure AD classiques :
    - Les charges de travail compatibles indiquent que les étiquettes de confidentialité et les groupes sont créés avec eux.
    - Les charges de travail non compatibles fonctionnent lors de la création de groupes, mais aucune étiquette de confidentialité n’est associée.
4. Les administrateurs peuvent exécuter des applets de commande PowerShell pour appliquer des étiquettes de confidentialité à ces groupes sans étiquette.
    - En guise d’alternative, un administrateur peut choisir de conserver les étiquettes Azure AD classiques :
        - Les charges de travail compatibles affichent ces étiquettes de sensibilité, et les groupes sont créés avec eux. Les charges de travail compatibles sont les services qui prennent en charge les étiquettes de sensibilité.
        - Les charges de travail non compatibles fonctionnent lors de la création de groupes et de l’affichage des étiquettes Azure AD classiques. Ces étiquettes Azure AD classiques sont attachées à ces groupes créés avec des charges de travail non compatibles.
5. Nous recommandons vivement aux administrateurs d’exécuter des applets de commande PowerShell pour appliquer des étiquettes de confidentialité à ces groupes avec des étiquettes Azure AD classiques.

Tableau 2. Comportement des charges de travail compatibles et non compatibles : créer, modifier ou supprimer des groupes

|Charge de travail|Quelle liste d’étiquettes est visible par l’utilisateur dans la fenêtre de groupe ?|Créer un groupe |Modifier un groupe |Delete group |
|:-------|:-------|:--------|:--------|:--------|   
|Conforme   |étiquettes de sensibilité. |Aucun changement de comportement. |Aucun changement de comportement. |Aucun changement de comportement. |
|Non compatible |Anciennes étiquettes AAD classiques. |L’utilisateur peut créer un groupe avec l’étiquette Azure AD classique sélectionnée. <br><br>Remarque : l’administrateur peut exécuter des cmdlets pour appliquer des étiquettes de sensibilité en arrière-plan. |**Cas 1**: étiquette de confidentialité précédemment sélectionnée. Un utilisateur peut modifier un groupe.<br><br> **Cas 2**: étiquettes AAD classiques précédemment sélectionnées. Un utilisateur peut modifier un groupe.<br><br> **Cas 3**: étiquette de sensibilité précédemment appliquée à l’arrière-plan à l’aide de l’applet de commande. L’utilisateur doit pouvoir modifier un groupe, à l’exception d’un cas où l’utilisateur sélectionne une combinaison non valide de paramètre de confidentialité par rapport à l’étiquette. |L’utilisateur peut supprimer un groupe. |

> [!NOTE]
> Dans le cas du client de bureau Outlook (Win 32), une fois que l’administrateur a activé les étiquettes de sensibilité sur son client, et que son utilisateur se trouve sur une version plus ancienne du client de bureau Outlook (Win 32) :
> - L’utilisateur voit des étiquettes de confidentialité apparaître sur l’ancienne version du client de bureau Outlook.
> - Toutefois, lorsque l’utilisateur modifie un groupe et enregistre le groupe avec une étiquette de sensibilité, le paramètre de confidentialité sélectionné est remplacé par le paramètre de confidentialité de l’étiquette de sensibilité appliquée.
> Nous recommandons à vos utilisateurs sur une ancienne version du client Outlook de procéder à la mise à niveau vers la version la plus récente.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Case B : étiquettes de confidentialité utilisées par le client pour les documents et les e-mails

1. Dès que l’administrateur Active la fonctionnalité d’étiquette de confidentialité sur le client en définissant l’indicateur de client « EnableMIPLabels » sur true, les étiquettes de confidentialité de document et de courrier dans les boîtes de dialogue créer et modifier un groupe/site/équipe apparaissent.
2. Un administrateur peut utiliser les mêmes étiquettes de confidentialité de document et de courrier pour appliquer la confidentialité et l’accès des utilisateurs externes au groupe/site/équipe en spécifiant les paramètres de groupe associés :
    1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez l’onglet **sites et groupes** .
    2. Modifier l’étiquette de confidentialité d’un document ou d’un message électronique.

## <a name="sample-script"></a>Exemple de script

Pour obtenir un exemple de script permettant de migrer des groupes avec des étiquettes AAD classiques vers des étiquettes de sensibilité, consultez la rubrique [Classic Azure ad Group classification](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites#classic-azure-ad-group-classification).

