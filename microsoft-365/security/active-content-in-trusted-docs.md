---
title: Gérer le contenu actif dans les documents Office pour les administrateurs informatiques
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.localizationpriority: medium
ms.service: microsoft-365-security
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Les administrateurs peuvent apprendre à créer des stratégies pour bloquer le contenu actif dans les documents Office
ms.openlocfilehash: 000e306fd2120fa2980d384ecdeda039f8d717f8
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736385"
---
# <a name="manage-active-content-in-office-documents"></a>Gérer le contenu actif dans les documents Office

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en préversion, ne sont pas disponibles pour tout le monde et sont susceptibles d’être modifiées.

Les documents Office peuvent être actualisés, mis à jour ou exécutés automatiquement lorsqu’ils contiennent du _contenu actif_. Les macros, les contrôles ActiveX et les compléments Office sont des exemples de contenu actif. Le contenu actif peut fournir des fonctionnalités puissantes et utiles aux utilisateurs, mais les attaquants peuvent également utiliser du contenu actif pour fournir des programmes malveillants.

Les administrateurs peuvent créer des stratégies d’organisation (stratégies de groupe ou stratégies cloud) qui limitent l’utilisation du contenu actif à des ensembles spécifiques d’utilisateurs ou pour désactiver entièrement le contenu actif. Les utilisateurs peuvent configurer leurs propres paramètres de sécurité et de confidentialité dans le Centre de confidentialité Office dans leurs applications **Office dans le** **Centre de gestion** de la \> confidentialité des **options** \> de fichiers.

Auparavant, lorsque les utilisateurs identifiaient des documents en tant que documents approuvés, leur sélection permettait l’exécution du contenu actif, même si un administrateur configurait des stratégies pour bloquer le contenu actif dans les documents Office. À présent, les stratégies définies par les administrateurs sont prioritaires sur l’identification des documents approuvés par l’utilisateur. Ce changement de comportement peut entraîner des problèmes pour les utilisateurs.

La logique mise à jour du Centre de gestion de la confidentialité est décrite dans le diagramme suivant :

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Graphique de flux décrivant la logique du centre de gestion de la confidentialité dans le portail Microsoft 365 Defender" lightbox="../media/office-trust-center-flow.png":::

1. Un utilisateur ouvre un document Office qui contient du contenu actif.

2. Si le document est à partir d’un emplacement approuvé, le document est ouvert avec le contenu actif activé. Si le document ne vient pas d’un emplacement approuvé, l’évaluation continue.

3. C’est ici que le comportement mis à jour prend effet :
   - Auparavant, le paramètre évalué suivant aurait été si l’utilisateur avait identifié ce document comme document approuvé. Si c’est le cas, le document s’ouvre avec le contenu actif activé.
   - À présent, le fait que l’utilisateur ait identifié ou non le document comme document approuvé n’est pas pris en compte ici (à l’étape 8).

     Le changement fondamental de comportement est décrit comme suit : les stratégies cloud (étape 4), les stratégies de groupe (étape 6) et les paramètres locaux (étape 7) sont vérifiés _avant_ même que la désignation utilisateur d’un document approuvé soit prise en compte. Si l’une de ces étapes bloque l’accès au contenu actif **et** qu’aucune des étapes n’autorise les remplacements d’utilisateurs, l’identification par l’utilisateur du document en tant que document approuvé n’est pas pertinente.

4. Les stratégies cloud sont vérifiées pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif n’est pas bloqué, l’évaluation passe à l’étape 6.

   Si le contenu actif est bloqué par la stratégie, l’expérience est décrite à l’étape 5.

5. L’ouverture du document est bloquée par une notification dans la barre d’approbation. Ce qui se passe ensuite est contrôlé par les paramètres de remplacement de l’utilisateur dans la stratégie : a. **Remplacement de l’utilisateur non autorisé** : l’utilisateur ne peut pas ouvrir le document et l’évaluation s’arrête.
   b. **Remplacement de l’utilisateur autorisé** : l’utilisateur peut cliquer sur le lien dans la barre d’approbation pour ouvrir le document avec le contenu actif activé.

6. Les stratégies de groupe sont vérifiées pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif n’est pas bloqué, l’évaluation passe à l’étape 7.

   Si le contenu actif est bloqué par la stratégie, l’expérience est décrite à l’étape 5.

7. Les paramètres locaux sont vérifiés pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif est bloqué, l’ouverture du document est bloquée avec une notification dans la barre d’approbation. Si le contenu actif n’est pas bloqué, l’évaluation continue.

8. Si l’utilisateur a précédemment identifié le document comme document approuvé, le document est ouvert avec le contenu actif activé. Si ce n’est pas le cas, l’ouverture du document est bloquée.

## <a name="what-is-a-trusted-document"></a>Qu’est-ce qu’un document approuvé ?

Les documents approuvés sont des documents Office qui s’ouvrent sans aucune invite de sécurité pour les macros, les contrôles ActiveX et d’autres types de contenu actif dans le document. La vue protégée ou Application Guard n’est pas utilisée pour ouvrir le document. Lorsque les utilisateurs ouvrent un document approuvé et que tout le contenu actif est activé. Même si le document contient du nouveau contenu actif ou des mises à jour du contenu actif existant, les utilisateurs ne recevront pas d’invites de sécurité lors de la prochaine ouverture du document.

En raison de ce comportement, les utilisateurs doivent clairement approuver les documents uniquement s’ils approuvent la source du document.

Si un administrateur bloque le contenu actif à l’aide d’une stratégie ou si les utilisateurs définissent un paramètre du Centre de gestion de la confidentialité qui bloque le contenu actif, le contenu actif reste bloqué.

Si vous souhaitez en savoir plus, consultez les articles suivants :

- [Documents approuvés](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Ajouter, supprimer ou modifier un emplacement approuvé](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Types de contenu actifs dans vos fichiers](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Configurer les paramètres de document approuvé dans les stratégies Office

Les administrateurs ont de nombreuses façons de configurer Office dans une organisation. Par exemple :

- **Service de stratégie cloud Office** : configurez une stratégie basée sur l’utilisateur qui s’applique à un utilisateur sur n’importe quel appareil accédant aux fichiers dans les applications Office avec son compte Azure AD. Consultez les étapes de [création d’une configuration de stratégie cloud Office](/DeployOffice/overview-office-cloud-policy-service) dans le [service Office Cloud Policy.](https://config.office.com/officeSettings/officePolicies)
- **Stratégies Office dans Intune** : utilisez le catalogue de paramètres Intune ou les modèles d’administration pour déployer des stratégies HKCU sur Windows 10 PC : dans le [centre d’administration MEM](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles) sous **Profils de configuration** **des appareils**\>.
  - ***Modèles d’administration*** : consultez les instructions permettant d’utiliser Windows 10 modèles pour configurer [des modèles d’administration](/mem/intune/configuration/administrative-templates-windows).
  - ***Catalogue de paramètres (préversion)*** : consultez les instructions pour utiliser le [catalogue de paramètres (préversion).](/mem/intune/configuration/settings-catalog)
- **Stratégie de groupe** : utilisez votre annuaire Active Directory local pour déployer des objets de stratégie de groupe (GPO) sur les utilisateurs et les ordinateurs. Pour créer un objet de stratégie de groupe pour ce paramètre, téléchargez les [derniers fichiers de modèle d’administration (ADMX/ADML) et l’outil de personnalisation Office pour Applications Microsoft 365 pour les grandes entreprises, Office 2019 et Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Problèmes connus

- Lorsque les **notifications de macro VBA** de stratégie (Access, PowerPoint, Visio, Word) ou **les notifications de macro** (Excel) sont définies sur la valeur **Désactiver toutes, sauf les macros signées numériquement**, la barre de confiance attendue n’est pas affichée et les **informations de sécurité** dans les coulisses ne répertorient pas les détails des macros bloquées, même si le paramètre fonctionne comme prévu. L’équipe Office travaille à résoudre ce problème.

## <a name="admin-options-for-restricting-active-content"></a>Administration options de restriction du contenu actif

Il existe une grande différence entre le niveau de confiance dans le contenu créé en interne et le contenu que les utilisateurs téléchargent à partir d’Internet. Envisagez d’autoriser le contenu actif dans les documents internes et, globalement, de ne pas autoriser le contenu actif dans les documents à partir d’Internet.

Si vos utilisateurs n’ont pas besoin de types spécifiques de contenu actif, votre option la plus sécurisée consiste à utiliser des stratégies pour désactiver l’accès utilisateur à ce contenu actif et autoriser les exceptions en fonction des besoins.

Les stratégies suivantes sont disponibles :

- **Désactiver les emplacements approuvés** : exceptions pour les groupes disponibles.
- **Désactiver les documents approuvés** : exceptions pour les groupes disponibles.
- **Désactiver tout le contenu actif** : exceptions pour les individus.

Les tableaux des sections suivantes décrivent les paramètres qui contrôlent le contenu actif. Ces stratégies, si elles sont appliquées aux utilisateurs, sont appliquées aux documents approuvés, et l’expérience utilisateur final précédente peut ne pas être la même. Les tableaux incluent également le paramètre de base de référence de sécurité recommandé et identifient d’autres paramètres où l’invite de l’utilisateur à remplacer est disponible (ce qui permet à l’utilisateur d’activer le contenu actif).

### <a name="hkey_current_user-settings"></a>paramètres de HKEY_CURRENT_USER

<p>

****
|Catégorie|Application|Nom de la stratégie|Base de référence de sécurité<br>paramètre (recommandé)|Paramètre avec invite d’utilisateur<br>et remplacer disponibles ?|
|---|---|---|---|---|
|Activex|Office|Initialisation du contrôle ActiveX|**6**|**Oui** pour les valeurs suivantes : <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|Activex|Office|Autoriser les formulaires X One désactivés actifs|**Charger uniquement les contrôles Outlook**|Non|
|Activex|Office|Vérifier les objets ActiveX|Pas un paramètre de base de référence de sécurité.|Non|
|Activex|Office|Désactiver tous les contrôles ActiveX|Pas un paramètre de base de référence de sécurité.|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Activex|Office|Contrôles de charge dans Forms3|**1**|**Oui** pour les valeurs suivantes : <ul><li>**2**</li><li>**3**</li></ul>|
|Compléments & extensibilité|Excel <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Désactiver la notification de barre d’approbation pour les compléments d’application non signés et les bloquer|**Enabled**|**Oui** pour la valeur **Disabled**.|
|Compléments & extensibilité|Excel <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Exiger la signature des compléments d’applications par un éditeur approuvé|**Enabled**|Non|
|Compléments & extensibilité|Excel|Ne pas afficher l’alerte d’avertissement de publication automatique|**Disabled**|Non|
|Compléments & extensibilité|Excel|Paramètres de notification de fonction WEBSERVICE|**Désactiver tout avec notification**|**Oui** pour les valeurs suivantes : <ul><li>**Désactiver tout avec notification**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Office|Désactiver l’interrogation du client Office sur SharePoint Server pour les liens publiés|**Disabled**|Non|
|Compléments & extensibilité|Office|Désactiver l’interface utilisateur provenant des documents et des modèles|Interdire dans Word = True <p> Interdire dans Project = False <p> Interdire dans Excel = True <p> Interdire dans Visio= False <p> Interdire dans PowerPoint = True <p> Interdire dans Access = True <p> Interdire dans Outlook = True <p> Interdire dans Publisher = True <p> Interdire dans InfoPath = True|Non|
|Compléments & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'accès à un carnet d'adresses|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Configurer l’invite de modèle objet Outlook lors de l’accès à la propriété Formula d’un objet UserProperty|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'exécution de l'opération Enregistrer sous|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de la lecture d'informations relatives à des adresses|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de la réponse à des demandes de réunion et de tâches|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'envoi d'un message|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|Outlook|Définir l’invite d’exécution des actions personnalisées du modèle objet Outlook|**Refuser automatiquement**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Inviter l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Compléments & extensibilité|PowerPoint|Exécuter des programmes|**désactiver (n’exécutez aucun programme)**|**Oui** pour la valeur **Enable (invite utilisateur avant l’exécution)**|
|Compléments & extensibilité|Word <p> Excel|Désactiver l’utilisation de manifestes par le document intelligent|**Enabled**|Non|
|Dde|Excel|N’autorisez pas le lancement d’un serveur DDE (Dynamic Data Exchange) dans Excel|**Enabled**|**Oui** pour la valeur **Non configurée**.|
|Dde|Excel|N’autorisez pas la recherche de serveur DDE (Dynamic Data Exchange) dans Excel|**Enabled**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Dde|Word|Échange de données dynamiques|**Disabled**|Non|
|Jscript & VBScript|Outlook|Autoriser les scripts dans les formulaires Outlook uniques |**Disabled**|Non|
|Jscript & VBScript|Outlook|Ne pas autoriser l’exécution de scripts de modèle objet Outlook pour les dossiers publics|**Enabled**|Non|
|Jscript & VBScript|Outlook|Ne pas autoriser l’exécution de scripts de modèle objet Outlook pour les dossiers partagés|**Enabled**|Non|
|Macros|Excel|Macro Notifications|**Désactiver toutes les macros à l’exception des macros signées numériquement**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Access <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Paramètres de notification de macro VBA|**Désactiver toutes les macros à l’exception des macros signées numériquement** <p> et <p> **Exiger que les macros soient signées par un éditeur approuvé**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Accès <p> Excel <p> PowerPoint <p> Visio <p> Word|Empêcher l’exécution de macros dans des fichiers Office à partir d’Internet|**Enabled**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Excel|Analyser des macros chiffrées dans des classeurs Excel Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|Macros|Office|Autoriser VBA à charger des références typelib par chemin d’accès à partir d’emplacements intranet non approuvés|**Disabled**|Non|
|Macros|Office|Automatisation de la sécurité|**Utiliser le niveau de sécurité des macros de l'application**|Non|
|Macros|Office|Désactiver d’autres vérifications de sécurité sur les références de bibliothèque VBA qui peuvent faire référence à des emplacements non sécurisés sur l’ordinateur local|**Disabled**|Non|
|Macros|Office|Étendue de l’analyse du runtime de macro|**Activer pour tous les documents**|Non|
|Macros|Office|Approuver uniquement les macros VBA qui utilisent des signatures V3|Pas un paramètre de base de référence de sécurité.|Non|
|Macros|Outlook|Mode de sécurité Outlook|**Utiliser نهج المجموعة de sécurité Outlook**|Requis pour activer tous les paramètres d’objet de stratégie de groupe Outlook. <p> Mentionné comme dépendance (cette stratégie ne bloque pas le contenu actif lui-même).|
|Macros|Outlook|Paramètre de sécurité pour les macros|**Avertir pour signé, désactiver non signé**|**Oui** pour les valeurs suivantes : <ul><li>**Toujours avertir**</li><li>**Avertir pour signé, désactiver non signé**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|PowerPoint|Analyser des macros chiffrées dans des présentations PowerPoint Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|Macros|Éditeur|Niveau de sécurité d’Automation des éditeurs|**Par interface utilisateur (confirmation)**|Non|
|Macros|Word|Analyser des macros chiffrées dans des documents Word Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|

### <a name="hkey_local_machine-settings"></a>paramètres de HKEY_LOCAL_MACHINE

<p>

****
|Catégorie|Application|Nom de la stratégie|Base de référence de sécurité<br>paramètre (recommandé)|Paramètre avec invite d’utilisateur<br>et remplacer disponibles ?|
|---|---|---|---|---|
|Activex|Office|Restreindre l’installation ActiveX |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|Compléments & extensibilité|Office|Gestion des modules complémentaires |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|Compléments & extensibilité|Office|Bloquer l’activation flash dans les documents Office|Consultez les fichiers ADMX/ADML du Guide de sécurité Microsoft pour obtenir la liste des killbits COM pour bloquer toute activation pour Flash dans les applications Microsoft 365. Les fichiers ADMX/ADML pour les bases de référence de sécurité d’entreprise sont disponibles dans le Kit de [ressources de conformité de la sécurité](https://www.microsoft.com/download/details.aspx?id=55319).|Non|
|Jscript & VBScript|Office|Restreindre l’exécution JScript héritée pour Office|**Activé** : <p> Accès : 69632 <p> Excel : 69632 <p> OneNote : 69632 <p> Outlook : 69632 <p> PowerPoint : 69632 <p> Projet : 69632 <p> Éditeur : 69632 <p> Visio : 69632 <p> Word: 69632|Non|
|Jscript & VBScript|Office|Restrictions de sécurité de scripts de fenêtres |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|
