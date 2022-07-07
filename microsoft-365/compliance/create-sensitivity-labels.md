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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: 'Une exigence pour toutes les solutions de protection des données Microsoft Purview : créer, configurer et publier des étiquettes de confidentialité pour classifier et protéger les données de votre organisation.'
ms.openlocfilehash: 486cc10888ebb66a657aa21930fe306073ac1868
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663523"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Créer et configurer des étiquettes de confidentialité et leurs stratégies.

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Toutes les solutions de protection des données Microsoft Purview sont implémentées à l’aide d’[étiquettes de confidentialité](sensitivity-labels.md). Pour créer et publier ces étiquettes, accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft Purview</a>.

Commencez par créer et configurer les étiquettes de confidentialité que vous souhaitez rendre disponibles pour les applications et autres services. Par exemple, les étiquettes que vous voulez que les utilisateurs voient et appliquent à partir des applications Office.

Puis créez une ou plusieurs stratégies d’étiquette contenant les étiquettes et paramètres de stratégie que vous configurez. La stratégie d’étiquette publie en effet les étiquettes et paramètres pour les utilisateurs et emplacements que vous sélectionnez.

> [!TIP]
> Si vous n'avez pas encore d’étiquettes de sensibilité, vous pouvez bénéficier de la création automatique d’étiquettes par défaut et d'une stratégie d’étiquettes par défaut. Même si vous aviez des étiquettes, il peut être utile d’afficher la configuration de ces étiquettes par défaut que nous créons pour les nouveaux clients. Par exemple, vous pouvez effectuer les mêmes configurations manuelles pour accélérer votre propre déploiement d’étiquette.
> 
> Pour plus d'informations, voir [Étiquettes et politiques par défaut pour Microsoft Purview Information Protection](mip-easy-trials.md).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose des autorisations totales pour créer et gérer tous les aspects des étiquettes de confidentialité. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des étiquettes de confidentialité](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Créer et configurer des étiquettes de confidentialité

1. Dans le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com/), sélectionnez **Solutions** > **Protection des données** > **Étiquettes**

2. Dans la page **Étiquettes** , sélectionnez **+ Créer une étiquette** pour démarrer la nouvelle configuration d’étiquette de confidentialité : 
    
    :::image type="content" source="../media/create-sensitivity-label-full.png" alt-text="Créer une étiquette de confidentialité." lightbox="../media/create-sensitivity-label-full.png":::

    > [!NOTE]
    > Par défaut, les clients n’ont pas d’étiquettes. Vous devez alors en créer. Les étiquettes de l’exemple d’image montrent les étiquettes par défaut qui ont été [déplacées à partir d’Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels).

3. Sur la page **Définir l’étendue de cette étiquette**, les options sélectionnées déterminent l’étendue de l’étiquette pour les paramètres que vous pouvez configurer et l’emplacement où ils seront visibles lors de la publication :

    ![Étendues des étiquettes de confidentialité.](../media/sensitivity-labels-scopes.png)

    - Si **Éléments** est sélectionné, vous pouvez configurer les paramètres qui s’appliquent aux applications qui prennent en charge les étiquettes de confidentialité, telles qu’Office Word et Outlook. Si cette option n’est pas sélectionnée, vous verrez la première page de ces paramètres, mais vous ne pourrez pas les configurer et les étiquettes ne seront pas disponibles à la sélection pour les utilisateurs dans ces applications.

    - Si **Groupes et sites** est sélectionné, vous pouvez configurer les paramètres qui s’appliquent aux groupes Microsoft 365 et aux sites pour Teams et SharePoint. Si vous n’avez pas sélectionné cette option, vous verrez la première page de ces paramètres, mais vous ne pourrez pas les configurer et les utilisateurs ne pourront pas sélectionner étiquettes pour les groupes et le site.

    Pour plus d’informations sur l’étendue des **Ressources de données schématisées**, consultez [Étiqueter automatiquement votre contenu dans Microsoft Purview Data Map](/azure/purview/create-sensitivity-label).

4. Suivez les invites de configuration pour les paramètres d’étiquette.

    Pour plus d’informations sur les paramètres d’étiquette, voir [Fonction des étiquettes de confidentialité](sensitivity-labels.md#what-sensitivity-labels-can-do) à partir des informations générales et utilisez l’aide de l’UI pour les paramètres individuels.

5. Répétez ces étapes pour créer d’autres étiquettes. Toutefois, si vous voulez créer une sous-étiquette, commencez par sélectionner l’étiquette parent, puis **...** pour **Plus d’actions**, enfin **Ajouter une sous-étiquette**.

6. Lorsque vous avez créé les étiquettes dont vous avez besoin, vérifiez leur ordre, puis déplacez-les vers le haut ou vers le bas si nécessaire. Pour modifier l’ordre d’une étiquette, sélectionnez **...** pour **Plus d’actions**, puis choisissez **Déplacer vers le haut** ou **Déplacer vers le bas**. Pour plus d’informations, voir [Priorité d'étiquette (trier les thèmes)](sensitivity-labels.md#label-priority-order-matters) dans les informations générales.

Pour modifier une étiquette existante, sélectionnez-la, puis choisissez le bouton **Modifier l'étiquette** :

![Bouton Modifier l’étiquette pour modifier une étiquette de confidentialité](../media/edit-sensitivity-label-full.png)

Ce bouton démarre la configuration **Modifier l'étiquette de confidentialité**, vous permettant de modifier les paramètres d’étiquette à l’étape 4.

Ne supprimez pas une étiquette, sauf si vous comprenez l’impact pour les utilisateurs. Pour plus d’informations, consultez la section [Retrait et suppression d’étiquettes](#removing-and-deleting-labels). 

> [!NOTE]
> Si vous modifiez une étiquette, qui est déjà publiée, à l'aide d'une stratégie d'étiquette, aucune autre étape n'est nécessaire à la fin de la configuration. Par exemple, vous n’avez pas besoin de l’ajouter à une nouvelle stratégie d’étiquette pour que les modifications soient mises à disposition desdits utilisateurs. Veuillez toutefois patienter jusqu'à 24 heures pour que les modifications s’appliquent aux applications et aux services.

Les étiquettes sont disponibles dans des applications ou des services après les avoir publiées. Les étiquettes doivent être [ajoutées à une stratégie d'étiquette](#publish-sensitivity-labels-by-creating-a-label-policy) pour être publiées.

> [!IMPORTANT]
> Dans l'onglet **Étiquettes**, ne pas sélectionner l'onglet **Publier des étiquettes** (ou le bouton **Publier une étiquette** lorsque vous modifiez une étiquette), sauf si vous devez créer une nouvelle stratégie d'étiquette. Plusieurs stratégies d’étiquette sont nécessaires uniquement si les utilisateurs ont besoin d’étiquettes ou de paramètres de stratégie différents. Votre objectif est d’avoir autant de stratégies d’étiquettes que possible, mais il n’est pas rare de n’avoir qu’une seule stratégie d’étiquette par organisation.

### <a name="additional-label-settings-with-security--compliance-powershell"></a>Paramètres d’étiquette supplémentaires avec Security & Compliance PowerShell

Des paramètres d’étiquette supplémentaires sont disponibles avec l’applet de commande [Set-Label](/powershell/module/exchange/set-label) de [Security & Compliance PowerShell](/powershell/exchange/scc-powershell).

Par exemple :

- Utilisez le paramètre *LocaleSettings* pour des déploiements internationaux pour que les utilisateurs voient le nom de l’étiquette et l’info-bulle dans leur langue locale. La [section suivante](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) présente un exemple de configuration qui spécifie le nom de l’étiquette et le texte d’info-bulle pour le français, l’italien et l’allemand.

- Les paramètres avancés pris en charge par l’étiquetage intégré sont inclus dans la documentation PowerShell. Pour plus d'aide sur la spécification de ces paramètres avancés PowerShell, consultez la [section Conseils PowerShell pour la spécification des paramètres avancés](#powershell-tips-for-specifying-the-advanced-settings). Pour connaître les autres paramètres avancés pris en charge par le client d'étiquetage unifié de Microsoft AzureInformation Protection, consultez la [documentation du guide d'administration de ce client](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels).

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Exemple de configuration d'une étiquette de confidentialité dans différentes langues

L’exemple suivant illustre la configuration PowerShell pour une étiquette intitulée « Public » avec un espace réservé au texte pour l’info-bulle. Dans cet exemple, le nom de l’étiquette et le texte d’info-bulle sont configurés pour le français, l'italien et l'allemand.

Suite à cette configuration, les utilisateurs disposant d'applications Office qui utilisent ces langues d’affichage voient leur nom d’étiquette et les info-bulles dans la même langue. De même, si votre client de l'étiquetage unifié Azure Information Protection est installé pour étiqueter des fichiers à partir de l’Explorateur de fichiers, les utilisateurs qui ont accès à ces versions linguistiques de Windows peuvent voir leurs noms d’étiquette et info-bulle dans leur langue locale lorsqu’ils effectuent des clics avec le bouton droit pour l’étiquetage.

Pour les langues que vous devez prendre en charge, utilisez les [identificateurs de langue](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) d'Office (également appelés balises linguistiques), et spécifiez votre propre traduction pour le nom d’étiquette et l’info-bulle.

Avant d’exécuter les commandes dans PowerShell, vous devez tout d’abord vous [connecter à l’interface PowerShell Sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

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

#### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Conseils PowerShell pour la spécification des paramètres avancés

Bien que vous puissiez spécifier une étiquette de niveau de sensibilité par son nom, nous vous recommandons d’utiliser le GUID de l’étiquette pour éviter toute confusion par rapport à la spécification du nom d’étiquette ou du nom complet. Le nom de l’étiquette est unique dans votre client. Vous pouvez donc être sûr de configurer l’étiquette correcte. Le nom d’affichage n’est pas unique et peut entraîner la configuration de l’étiquette incorrecte. Pour trouver le GUID et confirmer l’étendue de l’étiquette :

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Pour supprimer un paramètre avancé d'une étiquette de sensibilité, utilisez la même syntaxe de paramètre AdvancedSettings, mais spécifiez une valeur de chaîne nulle. Par exemple :

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

Pour vérifier la configuration de votre étiquette, y compris les paramètres avancés, utilisez la syntaxe suivante avec le GUID de votre propre étiquette :

```powershell
(Get-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e).settings
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publier des étiquettes de confidentialité en créant une stratégie d’étiquette

1. Dans le [Portail de conformité Microsoft Purview](https://compliance.microsoft.com/), sélectionnez **Solutions** > **Protection des données** > **Stratégies des étiquettes**

2. Sélectionnez la page **Stratégies des étiquettes**, puis **Publier l’étiquette** pour démarrer la configuration **Créer une stratégie** :
    
   :::image type="content" source="../media/publish-sensitivity-labels-full.png" alt-text="Publier des étiquettes." lightbox="../media/publish-sensitivity-labels-full.png":::
    
    > [!NOTE]
    > Par défaut, les clients n’ont pas de stratégies d’étiquette. Vous devez alors créer. 

3. Dans la **Choisissez des étiquettes de confidentialité pour publier** page, sélectionnez le **Choisir les étiquettes de confidentialité pour publier** lien. Sélectionnez les étiquettes que vous souhaitez rendre disponibles dans les applications et les services, puis choisissez **Ajouter**.

    > [!IMPORTANT]
    > Si vous sélectionnez une sous-étiquette, assurez-vous de sélectionner également son étiquette parente.

4. Vérifiez les étiquettes sélectionnées et, pour apporter toute modification, sélectionnez **Modifier**. Sinon, sélectionnez **Suivant**.

5. Suivez les invites pour configurer les paramètres de stratégie.

    Les paramètres de stratégie qui s’affichent correspondent à l’étendue des étiquettes que vous avez sélectionnées. Par exemple, si vous avez sélectionné des étiquettes dont l’étendue est uniquement **Éléments**, vous ne voyez pas les paramètres de stratégie **Appliquer cette étiquette par défaut aux groupes et sites** et **Demander aux utilisateurs d’appliquer une étiquette à leurs groupes et sites**.

    Si vous souhaitez en savoir plus sur ces paramètres, veuillez consulter la rubrique [Fonction des stratégies d’étiquette](sensitivity-labels.md#what-label-policies-can-do) depuis les informations générales, puis utiliser l’aide de l’Assistant pour les paramètres individuels.

    Pour les étiquettes configurées pour les **ressources Microsoft Purview Data Map (préversion)**: ces étiquettes n’ont pas de paramètres de stratégie associés.

6. Répétez ces étapes si vous avez besoin d'autres paramètres de stratégie pour des utilisateurs ou des étendues différents. Par exemple, vous souhaitez employer d’autres étiquettes pour un groupe d’utilisateurs, ou une étiquette par défaut différente pour un sous-ensemble d’utilisateurs. Ou, si vous avez configuré des étiquettes avec des étendues différentes.

7. Si vous créez plusieurs stratégies d’étiquette pouvant entraîner un conflit pour un utilisateur, vérifiez l’ordre des stratégies et, le cas échéant, déplacez-les vers le haut ou vers le bas. Pour modifier l’ordre d’une stratégie d'étiquette, sélectionnez **...** pour **Plus d’actions**, puis choisissez **Déplacer vers le haut** ou **Déplacer vers le bas**. Pour plus d’informations, voir [Priorité de stratégie d'étiquette (trier les thèmes)](sensitivity-labels.md#label-policy-priority-order-matters) dans les informations générales.

L’exécution de la **Créer une stratégie** la configuration publie automatiquement la stratégie d’étiquette. Pour apporter des modifications à une stratégie publiée, il vous suffit la modifier. Vous ne devez sélectionner aucune action de publication ou de republication spécifique.

Pour modifier une stratégie d'étiquette existante, sélectionnez-la, puis choisissez le bouton **Modifier la stratégie** : 

![Modifier une étiquette de confidentialité.](../media/edit-sensitivity-label-policy-full.png)

Ce bouton démarre la **Créer une stratégie** configuration, ce qui vous permet de modifier les étiquettes incluses et les paramètres d’étiquette. Une fois la configuration terminée, toutes les modifications sont automatiquement répliquées vers les utilisateurs et services sélectionnés.

### <a name="additional-label-policy-settings-with-security--compliance-powershell"></a>Paramètres de stratégie d’étiquette supplémentaires avec Security & Compliance PowerShell

Des paramètres de stratégie d’étiquette supplémentaires sont disponibles avec l’applet de commande [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) de [Security & Compliance PowerShell](/powershell/exchange/scc-powershell).

Cette documentation inclut les paramètres avancés pris en charge par l’étiquetage intégré. Pour connaître les autres paramètres avancés pris en charge par le client d'étiquetage unifié de la Protection des données Azure, consultez la [documentation du guide d'administration de ce client](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies).

## <a name="when-to-expect-new-labels-and-changes-to-take-effect"></a>Quand s’attendre à ce que de nouvelles étiquettes et modifications prennent effet

Pour les étiquettes et les paramètres de stratégie d’étiquette, attendez 24 heures pour que les modifications se propagent dans les services. Avec de nombreuses dépendances externes qui ont chacune leurs propres cycles de minutage, il ’ est judicieux d’attendre 24 heures avant de passer du temps à dépanner les étiquettes et les stratégies d’étiquette pour les modifications récentes.

Toutefois, dans certains scénarios, les modifications apportées aux étiquettes et aux stratégies d’étiquette peuvent prendre effet beaucoup plus rapidement ou dépasser 24 heures. Par exemple, pour les étiquettes de confidentialité nouvelles et supprimées pour Word, Excel et PowerPoint sur le web, les mises à jour peuvent être répliquées dans l’heure. Toutefois, pour les configurations qui dépendent du remplissage d’un nouveau groupe et de nouvelles modifications d’appartenance à un groupe, ou de la latence de réplication réseau et des restrictions de bande passante, ces modifications peuvent prendre de 24 à 48 heures.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Utiliser PowerShell pour les étiquettes de confidentialité ainsi que leurs stratégies

Vous pouvez maintenant utiliser [Security & Compliance PowerShell](/powershell/exchange/scc-powershell) pour créer et configurer tous les paramètres que vous voyez dans votre centre d’administration d’étiquetage. Cela signifie qu’outre l’utilisation de PowerShell pour les paramètres qui ne sont pas disponibles dans les centres d’administration pour les étiquettes, vous pouvez désormais créer des scripts pour la création et la maintenance des étiquettes de confidentialité et des stratégies d’étiquette de confidentialité. 

Consultez la documentation ci-après relative aux paramètres et valeurs pris en charge :

- [New-Label](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Set-Label](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

> [!TIP]
> Lorsque vous configurez des paramètres avancés pour une étiquette de confidentialité, il peut être utile de référencer les [conseils PowerShell pour spécifier la section Paramètres avancés](#powershell-tips-for-specifying-the-advanced-settings) sur cette page.

Vous pouvez également utiliser [Remove-Label](/powershell/module/exchange/remove-label) et [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) si vous devez créer un script pour la suppression d’étiquettes de confidentialité ou de stratégies d’étiquette de confidentialité. Toutefois, nous vous conseillons de lire la section suivante avant de supprimer des étiquettes de confidentialité.

## <a name="removing-and-deleting-labels"></a>Retrait et suppression d’étiquettes

Dans un environnement de production, il est peu probable que vous deviez supprimer des étiquettes de confidentialité d’une stratégie d’étiquette ou supprimer des étiquettes de confidentialité. Il est possible que vous deviez effectuer l’une ou l’autre de ces actions pendant une phase de test initiale. Assurez-vous de comprendre ce qui se passe lorsque vous effectuez l’une ou l’autre de ces actions.

Le retrait d'une étiquette d'une stratégie d'étiquetage est moins risqué que sa suppression, et elle peut toujours être rajoutée plus tard si nécessaire. Vous ne pourrez pas supprimer une étiquette si elle se trouve toujours dans une stratégie d’étiquette.

Lorsque vous retirez une étiquette d’une stratégie d’étiquette afin que l’étiquette ne soit plus publiée aux utilisateurs spécifiés à l’origine, la prochaine fois que la stratégie d’étiquette est actualisée, les utilisateurs ne verront plus cette étiquette pour les sélectionner dans leur application Office. Si cette étiquette est déjà appliquée, elle n’est pas supprimée du contenu ou du conteneur. Pour les étiquettes retirées mais qui ont été précédemment appliquées au contenu, les utilisateurs qui utilisent l’étiquetage prédéfini pour Word, Excel et PowerPoint affichent tout de même le nom d’étiquette appliqué dans la barre d’État. Une étiquette de conteneur appliquée continue de protéger le site Teams ou SharePoint.

Par comparaison, lorsque vous supprimez une étiquette :

- Si l’étiquette a appliqué le chiffrement, le modèle de protection sous-jacent est archivé de sorte que le contenu précédemment protégé puisse rester ouvert. En raison de ce modèle de protection archivé, vous ne pouvez pas créer de nouvelle étiquette portant le même nom. Bien qu’il soit possible de supprimer un modèle de protection à l’aide de [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate), ne procédez pas de la sorte, sauf si vous êtes sûr que vous n’avez pas besoin d’ouvrir le contenu chiffré avec le modèle archivé.

- Pour les documents stockés dans SharePoint ou OneDrive et que vous avez [activé les étiquettes de confidentialité pour les fichiers Office](sensitivity-labels-sharepoint-onedrive-files.md) : lorsque vous ouvrez le document dans Office sur le Web, l’étiquette n’est pas appliquée dans l’application et le nom de l’étiquette ne s’affiche plus dans la colonne **Confidentialité** dans SharePoint. Si l’étiquette supprimée a appliqué le chiffrement et que les services peuvent traiter le contenu chiffré, le chiffrement est supprimé. Les actions Egress de ces services entraînent le même résultat. Par exemple, téléchargez, copiez, déplacez-vous vers et ouvrez avec une application de bureau ou Office mobile. Bien que les informations d’étiquette restent dans les métadonnées du fichier, les applications ne peuvent plus mapper l’ID d’étiquette à un nom d’affichage, de sorte que les utilisateurs supposent qu’un fichier n’est pas étiqueté.

- Pour les documents stockés en dehors de SharePoint et OneDrive ou si vous n’avez pas activé d’étiquettes de confidentialité pour les fichiers Office, et pour les e-mails : lorsque vous ouvrez le contenu, les informations d’étiquette dans les métadonnées restent, mais sans l’ID d’étiquette pour le mappage de noms, les utilisateurs ne voient pas le nom d’étiquette appliqué affiché (par exemple, dans la barre d’état pour les applications de bureau). Si l’étiquette supprimée a appliqué un chiffrement, le chiffrement demeure et les utilisateurs continuent de voir le nom et la description du modèle de protection désormais archivé.

- Pour les conteneurs, tels que les sites dans SharePoint et Teams : l’étiquette est supprimée et tous les paramètres configurés avec cette étiquette ne sont plus appliqués. Cette action prend généralement entre 48 et 72 heures pour SharePoint sites et peut être plus rapide pour Teams et Groupes Microsoft 365.

Comme avec toutes les modifications d’étiquette, la suppression d’une étiquette de confidentialité d’une stratégie d’étiquette ou la suppression d’une étiquette de confidentialité prend du temps à répliquer sur tous les utilisateurs et services.

## <a name="next-steps"></a>Étapes suivantes

Pour configurer et utiliser vos étiquettes de confidentialité pour des scénarios déterminés, servez-vous des articles suivants :

- [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](encryption-sensitivity-labels.md)

- [Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)

- [Utiliser des étiquettes de confidentialité avec les équipes, les groupes et les sites](sensitivity-labels-teams-groups-sites.md)

- [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Si vous souhaitez surveiller le mode d’utilisation de vos étiquettes, veuillez consulter la rubrique [Prise en main de la classification des données](data-classification-overview.md).
