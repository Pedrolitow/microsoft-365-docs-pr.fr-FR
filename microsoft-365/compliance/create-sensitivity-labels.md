---
title: Créer et publier des étiquettes de confidentialité
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Instructions pour créer, configurer et publier des étiquettes de confidentialité afin de classer et protéger les documents et messages électroniques de votre organisation.
ms.openlocfilehash: 73df1928a89218a419a9d774a7830ecad4aceb6d
ms.sourcegitcommit: 2913fd74ad5086c7cac6388447285be9aa5a8e44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41661860"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Créer et configurer des étiquettes de confidentialité et leurs stratégies.

Pour créer et publier vos [étiquettes de confidentialité](sensitivity-labels.md), accédez au centre d’administration des étiquettes tel que le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Vous pouvez également utiliser le Centre de sécurité Microsoft 365 ou le Centre de sécurité et conformité Office 365.

Commencez par créer et configurer les étiquettes de confidentialité que vous souhaitez rendre disponibles pour les services et dans les applications Office. Puis créez une ou plusieurs stratégies d’étiquette contenant les étiquettes et paramètres de stratégie que vous configurez. La stratégie d’étiquette publie en effet les étiquettes et paramètres pour les utilisateurs et emplacements que vous sélectionnez.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Autorisations nécessaires pour la création et la gestion d'étiquettes de confidentialité

Les membres de votre équipe de conformité qui créeront des étiquettes de confidentialité ont besoin d’autorisations dans le Centre de conformité Microsoft 365, le Centre de sécurité Microsoft 365 ou le Centre de sécurité et conformité Office 365. 

Par défaut, votre administrateur de clients a accès à ces centres d’administration et pourra accorder l’accès aux responsables de la conformité et à d’autres personnes sans leur octroyer toutes les autorisations d’un administrateur de clients. Pour accorder cet accès administrateur délégué limité, allez à la page **Autorisations** de l’un de ces centres d’administration, puis d’ajouter des membres au groupe de rôles **Administrateur des données de conformité**, **Administrateur de la conformité** ou **Administrateur de la sécurité**.

Pour obtenir des instructions, reportez-vous à la rubrique [Octroi de l’accès au Centre de sécurité et conformité Office 365 aux utilisateurs](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center).

Ces autorisations sont seulement nécessaires pour créer et configurer des étiquettes de confidentialité et leurs stratégies d’étiquette. Elles ne sont pas requises pour l'application d'étiquettes dans des applications ou des services.

## <a name="create-and-configure-sensitivity-labels"></a>Créer et configurer des étiquettes de confidentialité

1. Dans le centre d’administration pour les étiquettes, accédez aux étiquettes de confidentialité :
    
    - Centre de conformité Microsoft 365 : 
        - **Solutions** > **protection des informations**
        
        Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**. 
    
    - Centre de sécurité Microsoft 365 : 
        - **Classification** > **des étiquettes de confidentialité**
    
    - Centre de sécurité et conformité Office 365 :
        - **Classification** > **des étiquettes de confidentialité**

2. Sous l’onglet **Étiquettes**, sélectionnez **+ Créer une étiquette** pour démarrer l’assistant **Nouvelle étiquette de confidentialité**.

3. Suivez les invites de paramètres d'étiquette.
    
    Pour plus d’informations sur les paramètres d’étiquette, voir [Fonction des étiquettes de confidentialité](sensitivity-labels.md#what-sensitivity-labels-can-do) à partir des informations générales.

4. Répétez ces étapes pour créer d’autres étiquettes. Toutefois, si vous voulez créer une sous-étiquette, commencez par sélectionner l’étiquette parent et choisissez **...** pour **Plus d’actions**, puis **Ajouter une sous-étiquette**.

5. Lorsque vous avez créé les étiquettes dont vous avez besoin, vérifiez leur ordre et déplacez-les vers le haut ou vers le bas si nécessaire. Pour modifier l’ordre d’une étiquette, sélectionnez **...** pour **Plus d’actions**, puis choisissez **Déplacer vers le haut** ou **Déplacer vers le bas**. Pour plus d’informations, voir [Priorité d'étiquette (trier les thèmes)](sensitivity-labels.md#label-priority-order-matters) dans les informations générales.

Pour modifier une étiquette existante, sélectionnez-la, puis choisissez **Modifier l'étiquette**. L’Assistant **Modifier l'étiquette de confidentialité** démarre, vous permettant de modifier les paramètres d’étiquette à l’étape 3. 

> [!NOTE]
> Si vous modifiez une étiquette, qui est déjà publiée, à l'aide d'une stratégie d'étiquette, aucune autre étape n'est nécessaire à la fin de l'Assistant. Par exemple, vous n’avez pas besoin de l’ajouter à une nouvelle stratégie d’étiquette pour que les modifications soient mises à disposition desdits utilisateurs. Veuillez toutefois patienter jusqu'à 24 heures pour que les modifications se répliquent vers les utilisateurs et les services.

Les étiquettes sont disponibles dans des applications ou des services après les avoir publiées. Les étiquettes doivent être [ajoutées à une stratégie d'étiquette](#publish-sensitivity-labels-by-creating-a-label-policy) pour être publiées.

> [!IMPORTANT]
> Dans l'onglet **Étiquettes**, ne pas sélectionner l'onglet **Publier des étiquettes** (ou le bouton **Publier une étiquette** lorsque vous modifiez une étiquette), sauf si vous devez créer une nouvelle stratégie d'étiquette. Plusieurs stratégies d’étiquette sont nécessaires uniquement si les utilisateurs ont besoin d’étiquettes ou de paramètres de stratégie différents. Votre objectif est d’avoir autant de stratégies d’étiquettes que possible, mais il n’est pas rare de n’avoir qu’une seule stratégie d’étiquette par organisation.

### <a name="additional-label-settings-with-office-365-security--compliance-center-powershell"></a>Paramètres d’étiquette supplémentaires dans le Centre de sécurité et conformité Office 365 PowerShell

D’autres paramètres d’étiquette sont disponibles dans l’applet de commande [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps) depuis le [Centre de sécurité et conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

Utilisez le paramètre *LocaleSettings* pour des déploiements internationaux pour que les utilisateurs voient le nom de l’étiquette et l’info-bulle dans leur langue locale. Reportez-vous à la section suivante pour consulter un exemple de configuration. 

L'utilisation de cette applet de commande vous permet également de spécifier des [paramètres avancés](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations) pour le client de l'étiquetage unifié Azure Information Protection. Ces paramètres avancés incluent le paramètre de couleur d’étiquette et l’application d’une propriété personnalisée lorsqu’une étiquette est appliquée. Pour obtenir la liste complète, voir [Paramètres avancés disponibles pour les stratégies d’étiquette](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies). 

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Exemple de configuration d'une étiquette de confidentialité dans différentes langues

L’exemple suivant illustre la configuration PowerShell pour une étiquette intitulée « Public » avec un espace réservé au texte pour l’info-bulle. Dans cet exemple, le nom de l’étiquette et le texte d’info-bulle sont configurés pour le français, l'italien et l'allemand.

Suite à cette configuration, les utilisateurs disposant d'applications Office qui utilisent ces langues d’affichage voient leur nom d’étiquette et les info-bulles dans la même langue. De même, si votre client de l'étiquetage unifié Azure Information Protection est installé pour étiqueter des fichiers à partir de l’Explorateur de fichiers, les utilisateurs qui ont accès à ces versions linguistiques de Windows peuvent voir leurs noms d’étiquette et info-bulle dans leur langue locale lorsqu’ils effectuent des clics avec le bouton droit pour l’étiquetage.

Pour les langues que vous devez prendre en charge, utilisez les [identificateurs de langue](https://docs.microsoft.com/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) d'Office (également appelés balises linguistiques), et spécifiez votre propre traduction pour le nom d’étiquette et l’info-bulle.

Avant d’exécuter les commandes dans PowerShell, vous devez tout d’abord vous [connecter au Centre de sécurité et conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps).


```powershell
$Languages = @("fr-fr","it-it","de-de")
$DisplayNames=@("Publique","Publico","Oeffentlich")
$Tooltips = @("Texte Français","Testo italiano","Deutscher text")
$label = "Public"
$DisplayNameLocaleSettings = [PSCustomObject]@{LocaleKey='DisplayName';
Settings=@(
@{key=$Languages[0];Value=$DisplayNames[0];}
@{key=$Languages[1];Value=$DisplayNames[1];}
@{key=$Languages[2];Value=$DisplayNames[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $DisplayNameLocaleSettings -Depth 3 -Compress)
$TooltipLocaleSettings = [PSCustomObject]@{LocaleKey='Tooltip';
Settings=@(
@{key=$Languages[0];Value=$Tooltips[0];}
@{key=$Languages[1];Value=$Tooltips[1];}
@{key=$Languages[2];Value=$Tooltips[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $TooltipLocaleSettings -Depth 3 -Compress)
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publier des étiquettes de confidentialité en créant une stratégie d’étiquette

1. Dans le centre d’administration pour les étiquettes, accédez aux étiquettes de confidentialité :
    
    - Centre de conformité Microsoft 365 : 
        - **Solutions** > **protection des informations**
        
        Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**. 
    
    - Centre de sécurité Microsoft 365 : 
        - **Classification** > **des étiquettes de confidentialité**
    
    - Centre de sécurité et conformité Office 365 :
        - **Classification** > **des étiquettes de confidentialité**

2. Sélectionnez l'onglet **Stratégies d'étiquette**.

3. Sélectionnez **Publier des étiquettes** pour démarrer l'**Assistant de création de stratégie**.

4. Sélectionnez **Choisir des étiquettes de confidentialité à publier**. Sélectionnez les étiquettes que vous souhaitez rendre disponibles dans les applications et les services, puis choisissez **Ajouter**.

5. Vérifiez les étiquettes sélectionnées et, pour apporter toute modification, sélectionnez **Modifier**. Autrement, sélectionnez **Suivant**.

6. Suivez les invites pour configurer les paramètres de stratégie.
    
    Pour plus d’informations sur les paramètres, voir [Fonction des stratégies d'étiquette](sensitivity-labels.md#what-label-policies-can-do) à partir des informations générales.

7. Répétez ces étapes si vous avez besoin d'autres paramètres de stratégie pour des utilisateurs ou des emplacements différents. Par exemple, vous souhaitez employer d’autres étiquettes pour un groupe d’utilisateurs, ou une étiquette par défaut différente pour un sous-ensemble d’utilisateurs.

8. Si vous créez plusieurs stratégies d’étiquette pouvant entraîner un conflit pour un utilisateur ou un emplacement, vérifiez l’ordre des stratégies et, le cas échéant, déplacez-les vers le haut ou vers le haut. Pour modifier l’ordre d’une stratégie d'étiquette, sélectionnez **...** pour **Plus d’actions**, puis choisissez **Déplacer vers le haut ** ou **Déplacer vers le bas**. Pour plus d’informations, voir [Priorité de stratégie d'étiquette (trier les thèmes)](sensitivity-labels.md#label-policy-priority-order-matters) dans les informations générales.

La stratégie d’étiquette est publiée automatiquement dès la fin de l'Assistant. Pour apporter des modifications à une stratégie publiée, il vous suffit la modifier. Vous ne devez sélectionner aucune action de publication ou de republication spécifique.

Pour modifier une stratégie d'étiquette existante, sélectionnez-la, puis choisissez **Modifier la stratégie**. Cette opération démarre l’Assistant **Créer une stratégie** qui vous permet de modifier les étiquettes incluses et leurs paramètres. Une fois l’exécution de l’Assistant terminée, toutes les modifications sont automatiquement répliquées vers les services et les utilisateurs sélectionnés.

Les utilisateurs peuvent généralement voir les étiquettes dans leurs applications Office dans les heures qui suivent. Veuillez toutefois patienter 24 heures pour vos stratégies d’étiquettes et toute modification apportée à celles-ci se répliquent vers l'ensemble des utilisateurs et des services.

### <a name="additional-label-policy-settings-with-office-365-security--compliance-center-powershell"></a>Paramètres de stratégie d'étiquette supplémentaires dans le Centre de sécurité et conformité Office 365 PowerShell

D’autres paramètres de stratégie d’étiquette sont disponibles dans l’applet de commande [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps) depuis le [Centre de sécurité et conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

L'utilisation de cette applet de commande vous permet de spécifier des [paramètres avancés](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations) pour le client de l'étiquetage unifié Azure Information Protection. Ces paramètres avancés incluent la définition d’une autre étiquette par défaut pour Outlook et l’implémentation de messages contextuels dans Outlook qui avertissent, justifient ou bloquent les messages envoyés. Pour obtenir la liste complète, voir [Paramètres avancés disponibles pour les étiquettes](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels). 

Vous pouvez également utiliser cette applet de commande pour ajouter et supprimer des étiquettes vers ou à partir d'une stratégie d’étiquette.


## <a name="next-steps"></a>Étapes suivantes

Pour configurer et utiliser vos étiquettes de confidentialité pour des scénarios déterminés, servez-vous des articles suivants :

- [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](encryption-sensitivity-labels.md)

- [Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)

- [Utiliser des étiquettes de confidentialité avec les équipes, les groupes et les sites](sensitivity-labels-teams-groups-sites.md)

- [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Pour contrôler l'utilisation de vos étiquettes, voir [Afficher l’utilisation d'étiquettes avec l'analyse des étiquettes](label-analytics.md).