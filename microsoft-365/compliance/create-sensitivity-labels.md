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
description: "Une exigence pour l'ensemble des solutions Microsoft Information Protection : créer, configurer et publier des étiquettes de confidentialité afin de classer et protéger les documents et messages électroniques de votre organisation."
ms.openlocfilehash: 96784edb6cf31d024d94e12a76c96b2f61340f04
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44679078"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Créer et configurer des étiquettes de confidentialité et leurs stratégies.

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

L'ensemble des solutions Microsoft Information Protection (parfois sous la forme abrégée MIP) sont mises en œuvre à l’aide d’[étiquettes de confidentialité](sensitivity-labels.md). Pour créer et publier ces étiquettes, accédez au centre d'administration des étiquettes, tel que le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Vous pouvez également utiliser le Centre de sécurité Microsoft 365 ou le Centre de sécurité et conformité.

Commencez par créer et configurer les étiquettes de confidentialité que vous souhaitez rendre disponibles pour les applications et autres services. Par exemple, les étiquettes que vous voulez que les utilisateurs voient et appliquent à partir des applications Office. 

Puis créez une ou plusieurs stratégies d’étiquette contenant les étiquettes et paramètres de stratégie que vous configurez. La stratégie d’étiquette publie en effet les étiquettes et paramètres pour les utilisateurs et emplacements que vous sélectionnez.

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose des autorisations totales pour créer et gérer tous les aspects des étiquettes de confidentialité. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des étiquettes de confidentialité](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Créer et configurer des étiquettes de confidentialité

1. Dans le centre d’administration pour les étiquettes, accédez aux étiquettes de confidentialité :
    
    - Centre de conformité Microsoft 365 : 
        - **Solutions** > **Information protection**
        
        Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**. 
    
    - Centre de sécurité Microsoft 365 : 
        - **Classification** > **des étiquettes de confidentialité**
    
    - Centre de sécurité et conformité :
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

### <a name="additional-label-settings-with-security--compliance-center-powershell"></a>Paramètres d’étiquette supplémentaires dans le Centre de sécurité et conformité PowerShell

D’autres paramètres d’étiquette sont disponibles dans l’applet de commande [Set-Label](https://docs.microsoft.com/powershell/module/exchange/set-label?view=exchange-ps) depuis le [Centre de sécurité et conformité PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

Utilisez le paramètre *LocaleSettings* pour des déploiements internationaux pour que les utilisateurs voient le nom de l’étiquette et l’info-bulle dans leur langue locale. Reportez-vous à la section suivante pour consulter un exemple de configuration. 

L'utilisation de cette applet de commande vous permet également de spécifier des [paramètres avancés](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations) pour le client de l'étiquetage unifié Azure Information Protection. Ces paramètres avancés incluent le paramètre de couleur d’étiquette et l’application d’une propriété personnalisée lorsqu’une étiquette est appliquée. Pour obtenir la liste complète, voir [Paramètres avancés disponibles pour les stratégies d’étiquette](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies). 

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Exemple de configuration d'une étiquette de confidentialité dans différentes langues

L’exemple suivant illustre la configuration PowerShell pour une étiquette intitulée « Public » avec un espace réservé au texte pour l’info-bulle. Dans cet exemple, le nom de l’étiquette et le texte d’info-bulle sont configurés pour le français, l'italien et l'allemand.

Suite à cette configuration, les utilisateurs disposant d'applications Office qui utilisent ces langues d’affichage voient leur nom d’étiquette et les info-bulles dans la même langue. De même, si votre client de l'étiquetage unifié Azure Information Protection est installé pour étiqueter des fichiers à partir de l’Explorateur de fichiers, les utilisateurs qui ont accès à ces versions linguistiques de Windows peuvent voir leurs noms d’étiquette et info-bulle dans leur langue locale lorsqu’ils effectuent des clics avec le bouton droit pour l’étiquetage.

Pour les langues que vous devez prendre en charge, utilisez les [identificateurs de langue](https://docs.microsoft.com/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) d'Office (également appelés balises linguistiques), et spécifiez votre propre traduction pour le nom d’étiquette et l’info-bulle.

Avant d’exécuter les commandes dans PowerShell, vous devez tout d’abord vous [connecter au Centre de sécurité et conformité PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps).


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
$TooltipLocaleSettings = [PSCustomObject]@{LocaleKey='Tooltip';
Settings=@(
@{key=$Languages[0];Value=$Tooltips[0];}
@{key=$Languages[1];Value=$Tooltips[1];}
@{key=$Languages[2];Value=$Tooltips[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $DisplayNameLocaleSettings -Depth 3 -Compress),(ConvertTo-Json $TooltipLocaleSettings -Depth 3 -Compress)
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publier des étiquettes de confidentialité en créant une stratégie d’étiquette

1. Dans le centre d’administration pour les étiquettes, accédez aux étiquettes de confidentialité :
    
    - Centre de conformité Microsoft 365 : 
        - **Solutions** > **Information protection**
        
        Si vous ne voyez pas immédiatement cette option, sélectionnez tout d’abord **Tout afficher**. 
    
    - Centre de sécurité Microsoft 365 : 
        - **Classification** > **des étiquettes de confidentialité**
    
    - Centre de sécurité et conformité :
        - **Classification** > **des étiquettes de confidentialité**

2. Sélectionnez l'onglet **Stratégies d'étiquette**.

3. Sélectionnez **Publier des étiquettes** pour démarrer l'**Assistant de création de stratégie**.

4. Sélectionnez **Choisir des étiquettes de confidentialité à publier**. Sélectionnez les étiquettes que vous souhaitez rendre disponibles dans les applications et les services, puis choisissez **Ajouter**.
    
    > [!NOTE]
    > Si vous sélectionnez une sous-étiquette, assurez-vous de sélectionner également son étiquette parente.
    
5. Vérifiez les étiquettes sélectionnées et, pour apporter toute modification, sélectionnez **Modifier**. Autrement, sélectionnez **Suivant**.

6. Suivez les invites pour configurer les paramètres de stratégie.
    
    Pour plus d’informations sur ces paramètres, voir [Fonction des stratégies d'étiquette](sensitivity-labels.md#what-label-policies-can-do) à partir des informations générales.

7. Répétez ces étapes si vous avez besoin d'autres paramètres de stratégie pour des utilisateurs ou des emplacements différents. Par exemple, vous souhaitez employer d’autres étiquettes pour un groupe d’utilisateurs, ou une étiquette par défaut différente pour un sous-ensemble d’utilisateurs.

8. Si vous créez plusieurs stratégies d’étiquette pouvant entraîner un conflit pour un utilisateur ou un emplacement, vérifiez l’ordre des stratégies et, le cas échéant, déplacez-les vers le haut ou vers le haut. Pour modifier l’ordre d’une stratégie d'étiquette, sélectionnez **...** pour **Plus d’actions**, puis choisissez **Déplacer vers le haut ** ou **Déplacer vers le bas**. Pour plus d’informations, voir [Priorité de stratégie d'étiquette (trier les thèmes)](sensitivity-labels.md#label-policy-priority-order-matters) dans les informations générales.

La stratégie d’étiquette est publiée automatiquement dès la fin de l'Assistant. Pour apporter des modifications à une stratégie publiée, il vous suffit la modifier. Vous ne devez sélectionner aucune action de publication ou de republication spécifique.

Pour modifier une stratégie d'étiquette existante, sélectionnez-la, puis choisissez **Modifier la stratégie**. Cette opération démarre l’Assistant **Créer une stratégie** qui vous permet de modifier les étiquettes incluses et leurs paramètres. Une fois l’exécution de l’Assistant terminée, toutes les modifications sont automatiquement répliquées vers les services et les utilisateurs sélectionnés.

Les utilisateurs peuvent généralement voir les étiquettes dans leurs applications Office dans les heures qui suivent. Veuillez toutefois patienter 24 heures pour vos stratégies d’étiquettes et toute modification apportée à celles-ci se répliquent vers l'ensemble des utilisateurs et des services.

### <a name="additional-label-policy-settings-with-security--compliance-center-powershell"></a>Paramètres de stratégie d’étiquette supplémentaires dans le Centre de sécurité et conformité PowerShell

Des paramètres de stratégie d’étiquette supplémentaires sont disponibles dans l’applet de commande [Set-Label](https://docs.microsoft.com/powershell/module/exchange/set-label?view=exchange-ps) depuis le [Centre de sécurité et conformité PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

L'utilisation de cette applet de commande vous permet de spécifier des [paramètres avancés](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations) pour le client de l'étiquetage unifié Azure Information Protection. Ces paramètres avancés incluent la définition d’une autre étiquette par défaut pour Outlook et l’implémentation de messages contextuels dans Outlook qui avertissent, justifient ou bloquent les messages envoyés. Pour obtenir la liste complète, voir [Paramètres avancés disponibles pour les étiquettes](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels). 

Vous pouvez également utiliser cette applet de commande pour ajouter et supprimer des étiquettes vers ou à partir d'une stratégie d’étiquette.

## <a name="removing-and-deleting-labels"></a>Retrait et suppression d’étiquettes

Dans un environnement de production, il est peu probable que vous deviez supprimer des étiquettes de confidentialité d’une stratégie d’étiquette ou supprimer des étiquettes de confidentialité. Il est possible que vous deviez effectuer l’une ou l’autre de ces actions pendant une phase de test initiale. Assurez-vous de comprendre ce qui se passe lorsque vous effectuez l’une ou l’autre de ces actions.

La retrait d’une étiquette d’une stratégie d’étiquette est moins risquée que sa suppression, et vous pouvez toujours l’ajouter à une stratégie d’étiquette ultérieurement si nécessaire :

- Lorsque vous retirez une étiquette d’une stratégie d’étiquette afin que l’étiquette ne soit plus publiée aux utilisateurs spécifiés à l’origine, la prochaine fois que la stratégie d’étiquette est actualisée, les utilisateurs ne verront plus cette étiquette pour les sélectionner dans leur application Office. En revanche, si l’étiquette a été appliquée aux documents ou aux courriers électroniques, elle n’est pas retirée de ce contenu. Tout chiffrement appliqué par l’étiquette est conservé et le modèle de protection sous-jacent reste publié. 

- Pour les étiquettes retirées mais qui ont été précédemment appliquées au contenu, les utilisateurs qui utilisent l’étiquetage prédéfini pour Word, Excel et PowerPoint affichent tout de même le nom d’étiquette appliqué dans la barre d’État. De même, les étiquettes qui ont été retirées et qui ont été appliquées aux sites SharePoint affichent encore le nom de l’étiquette dans la colonne **Sensibilité**.

Par comparaison, lorsque vous supprimez une étiquette :

- Si l’étiquette a appliqué le chiffrement, le modèle de protection sous-jacent est archivé de sorte que le contenu précédemment protégé puisse rester ouvert. En raison de ce modèle de protection archivé, vous ne pouvez pas créer de nouvelle étiquette portant le même nom. Bien qu’il soit possible de supprimer un modèle de protection à l’aide de [PowerShell](https://docs.microsoft.com/powershell/module/aipservice/remove-aipservicetemplate), ne procédez pas de la sorte, sauf si vous êtes sûr que vous n’avez pas besoin d’ouvrir le contenu chiffré avec le modèle archivé.

- Pour les applications de bureau : les informations d’étiquette sont conservées dans les métadonnées, mais étant donné qu’un ID d’étiquette vers un mappage de nom n’est plus possible, les utilisateurs ne voient pas le nom d’étiquette appliqué affiché (par exemple, dans la barre d’État) de sorte que le contenu ne soit pas étiqueté. Si l’étiquette a appliqué le chiffrement, le chiffrement reste et une fois le contenu ouvert, utilise toujours le nom et la description du modèle de protection désormais archivé.

- Pour Office sur le Web : les utilisateurs ne voient pas le nom de l’étiquette sur la barre d’État ni dans la colonne **Sensibilité**. Les informations d’étiquette dans les métadonnées restent uniquement si l’étiquette n’applique pas le chiffrement. Si l’étiquette a appliqué le chiffrement et que vous avez activé des [étiquettes de confidentialité pour SharePoint et Onedrive](sensitivity-labels-sharepoint-onedrive-files.md), les informations d’étiquette dans les métadonnées sont supprimées et le chiffrement est supprimé. 

## <a name="next-steps"></a>Étapes suivantes

Pour configurer et utiliser vos étiquettes de confidentialité pour des scénarios déterminés, servez-vous des articles suivants :

- [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](encryption-sensitivity-labels.md)

- [Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)

- [Utiliser des étiquettes de confidentialité avec les équipes, les groupes et les sites](sensitivity-labels-teams-groups-sites.md)

- [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Pour contrôler l'utilisation de vos étiquettes, voir [Afficher l’utilisation d'étiquettes avec l'analyse des étiquettes](label-analytics.md).
