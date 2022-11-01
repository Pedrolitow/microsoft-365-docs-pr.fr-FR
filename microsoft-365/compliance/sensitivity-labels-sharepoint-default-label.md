---
title: Configurer une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- purview-compliance
- tier1
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Configurez une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint pour les documents nouveaux et non étiquetés.
ms.openlocfilehash: cfa0eda2c3c30502c3d190976cf8e5418e6233d5
ms.sourcegitcommit: b439d097e55bba35d9328447d993bbcac7a178a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68803221"
---
# <a name="configure-a-default-sensitivity-label-for-a-sharepoint-document-library"></a>Configurer une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Cette fonctionnalité est en phase aperçu et est sujette à modifications. Il s’agit également d’une fonctionnalité Premium avec des détails de licence à fournir lorsque la fonctionnalité devient en disponibilité générale (GA).
> 
> Pour lire l’annonce de la préversion, consultez le [billet de blog](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/public-preview-default-label-for-a-document-library-in/ba-p/3585136).

Lorsque SharePoint est [activé pour les étiquettes de confidentialité](sensitivity-labels-sharepoint-onedrive-files.md), vous pouvez configurer une étiquette par défaut pour les bibliothèques de documents. Ensuite, cette étiquette est appliquée à tous les nouveaux fichiers chargés dans cette bibliothèque ou aux fichiers existants modifiés dans la bibliothèque s’ils n’ont pas encore d’étiquette de confidentialité, ou s’ils ont une étiquette de confidentialité mais avec une [priorité inférieure](sensitivity-labels.md#label-priority-order-matters).

Par exemple, vous configurez l’étiquette **Confidentiel** comme étiquette de confidentialité par défaut pour une bibliothèque de documents. Un utilisateur dont l’étiquette de stratégie par défaut **est Général** enregistre un nouveau fichier dans cette bibliothèque. SharePoint étiquetera ce fichier comme **confidentiel** en raison de la priorité plus élevée de cette étiquette. Pour obtenir un résumé rapide des résultats possibles, consultez [L’article Sur cette page, une étiquette existante sera-t-elle remplacée](#will-an-existing-label-be-overridden) ?

Une étiquette par défaut offre un niveau de protection de base et une forme d’étiquetage automatique sans inspection du contenu. Pour vous aider à faire la distinction entre l’étiquette par défaut de cette fonctionnalité et l’étiquette par défaut dans les stratégies d’étiquette :

- **Étiquette de confidentialité par défaut pour une bibliothèque de documents** : étiquetage basé sur l’emplacement, applicable uniquement à SharePoint. Remplace une étiquette de priorité inférieure, sauf si elle est appliquée manuellement.
- **Étiquette de confidentialité par défaut d’une stratégie** : toujours applicable à tous les emplacements. Ne remplace jamais une étiquette existante.

Lorsque vous utilisez Office sur le Web pour créer ou modifier un fichier, l’étiquette de confidentialité par défaut d’une bibliothèque de documents peut être appliquée sans délai. Toutefois, l’étiquetage n’est pas immédiat si vous chargez un fichier ou le créez à l’aide de Microsoft 365 Apps sur Windows, macOS, iOS ou Android, puis que vous enregistrez dans SharePoint :

- Chargement de fichier : l’application de l’étiquette peut prendre quelques minutes.
- Microsoft 365 Apps : l’étiquette est appliquée après la fermeture de l’application.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="will-an-existing-label-be-overridden"></a>Une étiquette existante sera-t-elle remplacée ?

Résumé des résultats :

|Étiquette existante |Remplacer par l’étiquette par défaut de la bibliothèque |
|:-----|:-----|:-----|
|Appliqué manuellement, n’importe quelle priorité| Non |
|Application automatique, priorité inférieure | Oui |
|Application automatique, priorité plus élevée | Non |
|Étiquette par défaut de la stratégie, priorité inférieure | Oui |
|Étiquette par défaut de la stratégie, priorité plus élevée | Non |

## <a name="requirements"></a>Configuration requise

- Vous avez [créé et publié](create-sensitivity-labels.md) des étiquettes de confidentialité, et elles sont publiées pour les utilisateurs qui sélectionnent une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint.

- Vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md). Pour vérifier cet état, vous pouvez exécuter `Get-SPOTenant -EnableAIPIntegration` à partir de [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) pour confirmer que la valeur est définie sur true.

- [La gestion des droits relatifs à l’information (IRM) SharePoint n’est pas activée pour la bibliothèque](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists). Cette ancienne technologie n’est pas compatible avec l’utilisation d’une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint. Si une bibliothèque est activée pour irm, vous ne pourrez pas sélectionner d’étiquette de confidentialité par défaut.

## <a name="limitations"></a>Limites

- Ne s’applique pas aux fichiers existants au repos dans SharePoint.

- À moins que vous n’ayez [activé la co-création de fichiers chiffrés avec des étiquettes de confidentialité](sensitivity-labels-coauthoring.md), l’application de l’étiquette de confidentialité par défaut pour une bibliothèque de documents s’affiche lorsque les utilisateurs sélectionnent l’option **Fichier** \> **Enregistrer sous** .

- Comme avec les étiquettes de confidentialité pour Office sur le Web, certaines [configurations d’étiquette qui appliquent le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings) ne conviennent pas à SharePoint et ne prennent donc pas en charge une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint :
    - **Permettre aux utilisateurs d'attribuer des autorisations lorsqu’ils appliquent l’étiquette** et la case à cocher **Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations** est sélectionnée. Ce paramètre est parfois appelé « autorisations définies par l’utilisateur ».
    - **L’expiration de l'accès des utilisateurs au contenu** est définie sur une valeur autre que **Jamais**.
    - **Chiffrement à double clé** est sélectionnée.

## <a name="how-to-configure-a-default-sensitivity-label-for-a-sharepoint-document-library"></a>Comment configurer une étiquette de confidentialité par défaut pour une bibliothèque de documents SharePoint

Pour une bibliothèque de documents existante :

1. Dans SharePoint, accédez à la bibliothèque \> de documents **Paramètres Paramètres** \> **De la bibliothèque.**

2. Dans le volet volant Paramètres de la **bibliothèque** , sélectionnez **Étiquettes de confidentialité par défaut**, puis sélectionnez une étiquette dans la zone de liste déroulante. Par exemple :
    
    ![Capture d’écran montrant la configuration d’une étiquette de confidentialité par défaut pour une bibliothèque SharePoint.](../media/default-sensitivity-label-spo2.png)
    
    Bien que vous voyiez que le paramètre mentionne la prise en charge des fichiers PDF, ce type de fichier n’est actuellement pas pris en charge pour ce scénario.

Si vous créez une bibliothèque de documents, vous pouvez configurer le même paramètre **Étiquettes de confidentialité par défaut** à partir du volet volant **Créer une bibliothèque de documents** .

Les autorisations requises pour définir et modifier une étiquette de confidentialité par défaut pour une bibliothèque SharePoint sont héritées. Comme pour la possibilité de modifier le nom et la description de la bibliothèque, tout membre de site SharePoint dispose de cette autorisation.

## <a name="monitoring-application-of-library-default-sensitivity-labels"></a>Application de surveillance des étiquettes de confidentialité par défaut de la bibliothèque

Utilisez la colonne **Confidentialité** SharePoint pour afficher les noms des étiquettes de confidentialité appliquées aux fichiers. Lorsque l’étiquette a été appliquée par cette fonctionnalité, l’info-bulle pour le nom de l’étiquette affiche **Ce fichier a été automatiquement étiqueté**. Toutefois, cette info-bulle n’est pas exclusive à l’étiquette de confidentialité par défaut pour une bibliothèque de documents. Il s’affiche également lorsque des étiquettes de confidentialité sont appliquées à l’aide de stratégies d’étiquetage automatique ou à la suite de l’étiquette par défaut d’un utilisateur à partir des stratégies d’étiquette de confidentialité.

Pour identifier spécifiquement quand l’étiquette a été appliquée en raison de l’étiquette de confidentialité par défaut de la bibliothèque, utilisez le [journal d’audit dans le portail de conformité](search-the-audit-log-in-security-and-compliance.md) et l’événement **d’audit du fichier d’étiquette de sensibilité appliqué** du groupe Activités de **l’étiquette de confidentialité** . Ensuite :
1. Sélectionnez une entrée pour afficher les détails dans un volet volant.

2. Dans le volet d’informations, faites défiler jusqu’à la **section SensitivityLabelEventData** et identifiez la valeur **d’ActionScourceDetails**.

3. La valeur **6** est utilisée pour le moment où l’étiquette a été appliquée en raison de l’étiquette de confidentialité par défaut pour la bibliothèque de documents.

Pour auditer le paramètre de configuration de cette fonctionnalité, utilisez l’événement **d’audit de liste mis à jour** du groupe d’activités de **liste SharePoint** . Dans le volet volant détails de la bibliothèque de documents, faites défiler jusqu’à la section **SensitivityLabelEventData** où **OldSensitivityLabeld** et **SensitivityLabelId** peuvent refléter trois changements d’états :

- Étiquette de confidentialité appliquée
- Étiquette de confidentialité modifiée d’une étiquette à l’autre
- Étiquette de confidentialité supprimée

Pour mapper les GUID d’étiquettes de confidentialité aux noms d’étiquettes, utilisez l’applet [de commande Get-Label](/powershell/module/exchange/get-label) :

1. Pour commencer, [connectez-vous à l’interface PowerShell Sécurité et conformité](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Exécutez ensuite la commande suivante, où vous spécifiez le GUID :

    ```powershell
    Get-Label -Identity "<GUID>" | Name

## Next steps

Default labeling ensures a minimum level of protection but doesn't take into account the file contents that might require a higher level of protection. Consider supplementing this labeling method with [automatic labeling](apply-sensitivity-label-automatically.md) that uses content inspection, and encourage [manual labeling](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) for users to replace the default label when needed.
