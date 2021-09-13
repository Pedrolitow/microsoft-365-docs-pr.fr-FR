---
title: Création d’une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContentPropertyContainsWords
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Découvrez comment utiliser une stratégie de protection contre la perte de données (DLP) pour protéger les documents qui ont des propriétés d’un système tiers.
ms.openlocfilehash: 60440162834bbef34c6e3adc2a60053cd9015e9d
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209389"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>Création d’une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés

Microsoft 365 stratégies de protection contre la perte de données (DLP) peuvent utiliser des propriétés de classification ou des propriétés d’élément pour identifier les éléments sensibles. Par exemple, vous pouvez utiliser :

- Windows Propriétés de l’infrastructure de classification des fichiers de serveur (FCI)
- SharePoint de document
- propriétés de document du système tiers

![Diagramme montrant Office 365 système de classification externe et externe.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Par exemple, votre organisation peut utiliser l’IFCI du serveur Windows pour identifier les éléments avec des données personnelles telles que les  numéros de sécurité sociale, puis classer le document en fixant la propriété Informations d’identification personnelle sur Les informations d’identification personnelle sur **les** données d’identification personnelle élevées, moyennes, faibles, publiques ou non en fonction du type et du nombre d’occurrences de données personnelles trouvées dans le document.   

Dans Microsoft 365, vous pouvez créer une stratégie DLP qui identifie les documents dont la propriété est définie sur des valeurs spécifiques, telles que High **et** **Medium,** puis prend une action telle que le blocage de l’accès à ces fichiers. La même stratégie peut disposer d’une autre règle qui exécute une action différente si la propriété est définie sur **Faible**, telle que l’envoi d’une notification par courrier électronique. De cette façon, DLP s’intègre à l’CI de Windows Server et peut aider à protéger les documents Office téléchargés ou partagés sur Microsoft 365 à partir de serveurs de fichiers Windows Server.

Une stratégie DLP recherche simplement une paire nom/valeur de propriété spécifique. N’importe quelle propriété de document peut être utilisée, tant que la propriété possède une propriété gérée correspondante pour la recherche SharePoint. Par exemple, une collection de sites SharePoint peut utiliser un type de contenu nommé **Relevé de voyage** avec un champ obligatoire nommé **Client**. Lorsqu’une personne crée un relevé de voyage, elle doit entrer le nom du client. Cette paire nom/valeur de propriété peut également être utilisée dans une stratégie DLP, par exemple,  si vous souhaitez une règle qui bloque l’accès au document pour les invités lorsque le champ Client contient **Contoso**.

Si vous souhaitez appliquer votre stratégie DLP au contenu avec des étiquettes Microsoft 365 spécifiques, vous ne devez pas suivre les étapes ci-après. Découvrez plutôt comment utiliser une [étiquette de rétention comme condition dans une stratégie DLP.](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

## <a name="before-you-create-the-dlp-policy"></a>Avant de créer la stratégie DLP

Avant de pouvoir utiliser une propriété ICF Windows Server ou une autre propriété dans une stratégie DLP, vous devez créer une propriété gérée dans le Centre d’administration SharePoint. Voici pourquoi.

Exemples

> [!NOTE]
> N’oubliez pas d’utiliser un nom de propriété gérée et non un nom de propriété analyse lors de la création de règles DLP à l’aide de la `ContentPropertyContainsWords` condition.

Ceci est important car la DLP utilise le robot de recherche pour identifier et classer les informations sensibles sur vos sites, puis stocke ces informations sensibles dans une partie sécurisée de l’index de recherche. Lorsque vous chargez un document vers Office 365, SharePoint crée automatiquement les propriétés analysées basées sur les propriétés du document. En revanche, pour utiliser une ICF ou une autre propriété dans une stratégie DLP, la propriété analysée doit être mappée sur une propriété gérée afin que le contenu avec cette propriété soit conservé dans l’index.

Pour plus d’informations sur la recherche et les propriétés gérées, voir Gérer le schéma de [recherche dans SharePoint Online.](/sharepoint/manage-search-schema)

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>Étape 1 : chargement d’un document avec la propriété nécessaire vers Office 365

Vous devez d’abord charger un document avec la propriété que vous souhaitez référencer dans votre stratégie DLP. Microsoft 365 détectera la propriété et créera automatiquement une propriété analyse à partir de cette propriété. Dans l’étape suivante, vous allez créer une propriété gérée, puis la ma cartographier sur cette propriété gérée.

### <a name="step-2-create-a-managed-property"></a>Étape 2 : création d’une propriété gérée

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>.

2. In the left navigation, choose **Admin centers** \> **SharePoint**. Vous vous trouvez maintenant dans le Centre d’administration SharePoint.

3. In the left navigation, choose **search** \> on the search **administration** page Manage \> **Search Schema**.

   ![page d’administration de la recherche SharePoint centre d’administration.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. Dans la page **Propriétés gérées,** \> **nouvelle propriété gérée**.

   ![Page Propriétés gérées avec le bouton Nouvelle propriété gérée mis en évidence.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Entrez un nom et une description pour la propriété. Ce nom apparaîtra dans vos stratégies DLP.

6. Pour **Type**, sélectionnez **Texte**.

7. Sous **Caractéristiques principales**, sélectionnez **Utilisable dans une requête** et **Affichable dans les résultats d’une recherche**.

8. Sous **Mappages aux propriétés** \> **analyser, ajoutez un mappage.**

9. Dans  la boîte de dialogue de sélection des propriétés analyse, recherchez et sélectionnez la propriété analyse qui correspond à la propriété Windows Server FCI ou à une autre propriété que vous utiliserez dans votre stratégie \> DLP \> **OK.**

   ![boîte de dialogue de sélection de propriétés analyse.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. En bas de la page \> **OK**.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>Création d’une stratégie DLP qui utilise une propriété ICF ou une autre propriété

Dans cet exemple, une organisation utilise l’CI sur Windows serveurs de fichiers basés sur un serveur ; plus précisément, ils utilisent la propriété de classification FCI nommée **Personally Identifiable Information** avec les valeurs possibles **de High**, **Moderate**, **Low**, **Public** et **Not PII**. À présent, ils souhaitent utiliser leur classification FCI existante dans leurs stratégies DLP dans Office 365.

D’abord, ils suivent les étapes ci-dessus pour créer une propriété gérée dans SharePoint Online, qui est mappée sur la propriété analysée créée automatiquement à partir de la propriété ICF.

Ensuite, ils créent une stratégie DLP avec deux règles qui utilisent toutes deux la condition **Propriétés document contiennent l’une de ces valeurs**:

- **Contenu des pii FCI - Élevé, Modéré** La première règle limite l’accès au document  si la propriété de  classification FCI Informations d’identification personnelle est élevée ou modérée et si le document est partagé avec des personnes **extérieures** à l’organisation.

- **Contenu des pii FCI - Faible** La deuxième règle envoie une notification au propriétaire du document si la propriété de classification FCI **Informations** d’identification personnelle est faible et que le document est partagé avec des personnes **extérieures** à l’organisation.

### <a name="create-the-dlp-policy-by-using-powershell"></a>Créer la stratégie DLP à l’aide de PowerShell

Les propriétés **de document** de condition contiennent l’une de ces valeurs n’est temporairement pas disponible dans l’interface utilisateur du Centre de conformité de sécurité, mais vous pouvez toujours utiliser cette condition à l’aide &amp; de PowerShell. Vous pouvez utiliser les cmdlets pour utiliser une stratégie DLP et utiliser les cmdlets avec le paramètre pour ajouter la condition Que les propriétés document contiennent l’une de  `New\Set\Get-DlpCompliancePolicy`  `New\Set\Get-DlpComplianceRule` ces  `ContentPropertyContainsWords` **valeurs**.

Pour plus d’informations sur ces cmdlets, voir [ &amp; cmdlets du Centre](/powershell/exchange/exchange-online-powershell)de conformité de sécurité.

1. [Connecter au Centre de conformité de sécurité à &amp; l’aide de PowerShell à distance](/powershell/exchange/connect-to-scc-powershell)

2. Créez la stratégie à l’aide  `New-DlpCompliancePolicy` de .

Ce PowerShell crée une stratégie DLP qui s’applique à tous les emplacements.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Créez les deux règles décrites ci-dessus à l’aide de , où une règle est pour la valeur Faible, et une autre règle pour les valeurs Élevée `New-DlpComplianceRule` **et** Modéré.  

   Voici un exemple PowerShell qui crée ces deux règles. Les paires nom/valeur de propriété sont entre guillemets et un nom de propriété peut spécifier plusieurs valeurs séparées par des virgules sans espace, comme  `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Windows L’IF de serveur inclut de nombreuses propriétés intégrées, y compris les informations **d’identification** personnelle utilisées dans cet exemple. Les valeurs possibles pour chaque propriété peuvent être différentes pour chaque organisation. Les **valeurs Élevée,** **Modéré** et **Faible** utilisées ici ne sont qu’un exemple. Pour votre organisation, vous pouvez afficher les propriétés de classification Windows Server FCI avec leurs valeurs possibles dans le Gestionnaire de ressources du serveur de fichiers sur le serveur de fichiers Windows Server. Pour plus d’informations, voir [Créer une propriété de classification.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11))

Lorsque vous avez terminé, votre stratégie doit avoir deux nouvelles règles qui utilisent toutes les deux les propriétés **document contiennent l’une de ces conditions de** valeurs. Cette condition n’apparaîtra pas dans l’interface utilisateur, bien que les autres conditions, actions et paramètres apparaissent.

Une règle bloque l’accès au contenu pour lequel la propriété **Informations d’identification personnelle** est définie sur **Haut** ou **Modéré**. Une deuxième règle envoie une notification sur le contenu pour lequel la propriété **Informations d’identification personnelle** est définie sur **Faible**.

![Boîte de dialogue nouvelle stratégie DLP affichant deux règles qui viennent d’être créées.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>Après avoir créé la stratégie DLP

Les étapes des sections précédentes créent une stratégie DLP qui détectera rapidement le contenu avec cette propriété, mais uniquement si ce contenu vient d’être téléchargé (afin que le contenu soit indexé) ou si ce contenu est ancien mais simplement modifié (afin que le contenu soit de nouveau indexé).

Pour détecter tout le contenu avec cette propriété, vous voudrez peut-être demander manuellement la réindexation de votre bibliothèque, site ou collection de sites, afin que la stratégie DLP connaisse tout le contenu avec cette propriété. Dans SharePoint Online, le contenu est automatiquement analysé selon une planification d’analyse définie. Le robot récupère le contenu qui a été modifié depuis la dernière analyse et met à jour l’index. Si vous avez besoin que votre stratégie DLP protège le contenu avant la prochaine analyse planifiée, vous pouvez suivre cette procédure.

> [!CAUTION]
> La réindexation d’un site peut entraîner une charge importante sur le système de recherche. Ne ré-indexez pas votre site, sauf si votre scénario l’exige absolument.

Pour plus d’informations, voir [Demander manuellement l’analyse et la réindexation d’un site, d’une bibliothèque ou d’une liste](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Réindexer un site (facultatif)

1. Sur le site, choisissez **Paramètres** (icône d’engrenage en haut à \> **droite) Paramètres**.

2. Sous **Recherche,** choisissez **Site de recherche** et de disponibilité hors connexion \> **Réindexé.**

## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)

- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)

- [Envoyer des notifications et afficher des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)

- [Contenu des modèles de stratégie DLP](what-the-dlp-policy-templates-include.md)

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)