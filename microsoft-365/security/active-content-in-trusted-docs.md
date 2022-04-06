---
title: Gérer le contenu actif dans Office documents pour les administrateurs informatiques
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.localizationpriority: medium
ms.prod: m365-security
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ROBOTS: NOINDEX,NOFOLOW
description: Les administrateurs peuvent apprendre à créer des stratégies pour bloquer le contenu actif dans Office documents
ms.openlocfilehash: 33d53ab14fec1b6cd16b8de95befe8bc8a898e16
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468918"
---
# <a name="manage-active-content-in-office-documents"></a>Gérer le contenu actif dans les documents Office

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, ne sont pas disponibles pour tout le monde et peuvent faire l’objet de changements.

Office documents peuvent être automatiquement actualisé, mis à jour ou exécutés lorsqu’ils contiennent _du contenu actif_. Les macros, les contrôles ActiveX contrôles et les Office des macros sont des exemples de contenu actif. Le contenu actif peut fournir des fonctionnalités puissantes et utiles aux utilisateurs, mais les attaquants peuvent également utiliser du contenu actif pour fournir des programmes malveillants.

Les administrateurs peuvent créer des stratégies d’organisation (stratégies de groupe ou stratégies cloud) qui limitent l’utilisation du contenu actif à des ensembles d’utilisateurs spécifiques ou désactivent entièrement le contenu actif. Les utilisateurs peuvent configurer leurs propres paramètres de sécurité et de confidentialité dans le Centre de Office de confidentialité dans leurs applications Office dans  \> le Centre de confidentialité **des options** \> **de fichiers**.

Auparavant, lorsque les utilisateurs identifiaient des documents comme documents fiables, leur sélection permettait l’exécuter, même si un administrateur configurait des stratégies pour bloquer le contenu actif dans Office documents. Désormais, les stratégies définies par les administrateurs prévalent sur l’identification des documents fiables par l’utilisateur. Ce changement de comportement peut entraîner des problèmes pour les utilisateurs.

La logique mise à jour du Centre de confiance est décrite dans le diagramme suivant :

:::image type="content" source="../media/office-trust-center-flow.png" alt-text="Un organigramme décrivant la logique du centre de Microsoft 365 Defender de confiance" lightbox="../media/office-trust-center-flow.png":::

1. Un utilisateur ouvre un document Office qui contient du contenu actif.

2. Si le document est à partir d’un emplacement approuvé, le document est ouvert avec le contenu actif activé. Si le document ne se trouve pas à un emplacement approuvé, l’évaluation se poursuit.

3. C’est ici que le comportement mis à jour prend effet :
   - Auparavant, le paramètre évalué suivant aurait été si l’utilisateur avait identifié ce document comme document approuvé. Si c’est le cas, le document s’ouvre avec le contenu actif activé.
   - À présent, le fait que l’utilisateur a identifié ou non le document comme document approuvé n’est pas pris en compte ici (à l’étape 8).

     Le changement de comportement fondamental est décrit comme suit : les stratégies cloud (étape 4), les stratégies de groupe (étape 6) et les paramètres locaux (étape 7) sont vérifiés avant même que la désignation d’un document approuvé par l’utilisateur soit envisagée. Si l’une de ces étapes bloque l’accès au contenu actif et qu’aucune des étapes n’autorise les remplacements par l’utilisateur, l’identification du document par l’utilisateur en tant que document approuvé n’est pas pertinente.

4. Les stratégies cloud sont vérifiées pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif n’est pas bloqué, l’évaluation continue à l’étape 6.

   Si le contenu actif est bloqué par une stratégie, l’expérience est décrite à l’étape 5.

5. L’ouverture du document est bloquée par une notification dans la barre de confiance. Ce qui se produit ensuite est contrôlé par les paramètres de remplacement de l’utilisateur dans la stratégie : a. **Remplacement de l’utilisateur non autorisé** : l’utilisateur ne peut pas ouvrir le document et l’évaluation s’arrête.
   b. **Remplacement utilisateur autorisé** : l’utilisateur peut cliquer sur le lien dans la barre de confiance pour ouvrir le document avec le contenu actif activé.

6. Les stratégies de groupe sont vérifiées pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif n’est pas bloqué, l’évaluation continue à l’étape 7.

   Si le contenu actif est bloqué par une stratégie, l’expérience est décrite à l’étape 5.

7. Les paramètres locaux sont vérifiés pour voir si ce type de contenu actif est autorisé ou bloqué. Si le contenu actif est bloqué, l’ouverture du document est bloquée avec une notification dans la barre de confiance. Si le contenu actif n’est pas bloqué, l’évaluation se poursuit.

8. Si l’utilisateur a précédemment identifié le document comme document approuvé, le document est ouvert avec le contenu actif activé. Si ce n’est pas le cas, l’ouverture du document est bloquée.

## <a name="what-is-a-trusted-document"></a>Qu’est-ce qu’un document approuvé ?

Les documents Office documents qui s’ouvrent sans invite de sécurité pour les macros, ActiveX contrôles et autres types de contenu actif dans le document. Le affichage protégé ou Application Guard n’est pas utilisé pour ouvrir le document. Lorsque les utilisateurs ouvrent un document approuvé et que tout le contenu actif est activé. Même si le document contient un nouveau contenu actif ou des mises à jour de contenu actif existant, les utilisateurs ne reçoivent pas d’invites de sécurité la prochaine fois qu’ils ouvrent le document.

En raison de ce comportement, les utilisateurs doivent clairement faire confiance aux documents uniquement s’ils font confiance à la source du document.

Si un administrateur bloque le contenu actif à l’aide d’une stratégie ou si les utilisateurs définissent un paramètre du Centre de gestion de la confidentialité qui bloque le contenu actif, le contenu actif reste bloqué.

Si vous souhaitez en savoir plus, consultez les articles suivants :

- [Documents de confiance](https://support.microsoft.com/topic/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53)
- [Ajouter, supprimer ou modifier un emplacement approuvé](https://support.microsoft.com/topic/add-remove-or-change-a-trusted-location-7ee1cdc2-483e-4cbb-bcb3-4e7c67147fb4)
- [Types de contenu actifs dans vos fichiers](https://support.microsoft.com/topic/active-content-types-in-your-files-b7ff2e8a-4055-47d4-8c7d-541e19f62bea)

## <a name="configure-trusted-document-settings-in-office-policies"></a>Configurer les paramètres de document approuvé dans Office stratégies

Les administrateurs ont plusieurs façons de configurer les Office dans une organisation. Par exemple :

- **Office de stratégie cloud** : configurer une stratégie utilisateur qui s’applique à un utilisateur sur tout appareil accédant à des fichiers dans des applications Office avec son compte Azure AD client. Consultez les étapes de [création d’Office de stratégie cloud](/DeployOffice/overview-office-cloud-policy-service) dans Office [Cloud Policy Service](https://config.office.com/officeSettings/officePolicies).
- **Office dans Intune** : utilisez le catalogue Intune Paramètres ou des modèles d’administration pour déployer des stratégies HKCU sur des PC Windows 10 : dans le Centre d’administration [MEM](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/configurationProfiles)  \> sous Profils de **configuration** des appareils.
  - ***Modèles d’administration*** : consultez les instructions d’utilisation Windows 10 modèles pour configurer des [modèles d’administration](/mem/intune/configuration/administrative-templates-windows).
  - ***Paramètres catalogue (prévisualisation)*** : voir les instructions d’utilisation [du catalogue Paramètres (prévisualisation).](/mem/intune/configuration/settings-catalog)
- **Stratégie de groupe** : utilisez votre annuaire Active Directory local pour déployer des objets de stratégie de groupe sur les utilisateurs et les ordinateurs. Pour créer un GPO pour ce paramètre, téléchargez les derniers fichiers de modèle d’administration [(ADMX/ADML) et l’outil de personnalisation Office pour Applications Microsoft 365 pour les grandes entreprises, Office 2019 et Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

## <a name="known-issues"></a>Problèmes connus

- Lorsque la stratégie **VBA Macro notifications** (Access, PowerPoint, Visio, Word) ou **les notifications de macro** (Excel) est définie sur la valeur Désactiver tout sauf les **macros signées** numériquement, la barre de confiance attendue n’est pas affichée et les informations de sécurité en  arrière-plan ne listent pas les détails des macros bloquées, même si le paramètre fonctionne comme prévu. L Office de travail de l’équipe de recherche travaille à résoudre ce problème.

## <a name="admin-options-for-restricting-active-content"></a>Options d’administration pour limiter le contenu actif

Il existe une grande différence entre le niveau de confiance dans le contenu créé en interne et le contenu téléchargé par les utilisateurs à partir d’Internet. Envisagez d’autoriser le contenu actif dans les documents internes et globalement de ne pas autoriser le contenu actif dans les documents à partir d’Internet.

Si vos utilisateurs n’ont pas besoin de types spécifiques de contenu actif, votre option la plus sécurisée consiste à utiliser des stratégies pour désactiver l’accès des utilisateurs à ce contenu actif et autoriser les exceptions si nécessaire.

Les stratégies suivantes sont disponibles :

- **Désactiver les emplacements de confiance :** exceptions pour les groupes disponibles.
- **Désactiver les documents fiables** : exceptions pour les groupes disponibles.
- **Désactiver tout le contenu actif :** exceptions pour les individus.

Les tableaux des sections suivantes décrivent les paramètres qui contrôlent le contenu actif. Ces stratégies, si elles sont appliquées aux utilisateurs, seront appliquées sur les documents de confiance, et l’expérience précédente de l’utilisateur final risque de ne pas être la même. Les tableaux incluent également le paramètre de ligne de base de sécurité recommandé et identifient les autres paramètres pour lequel l’invite de l’utilisateur est disponible (ce qui permet à l’utilisateur d’activer le contenu actif).

### <a name="hkey_current_user-settings"></a>HKEY_CURRENT_USER paramètres

<p>

****
|Catégorie|Application|Nom de la stratégie|Base de référence de sécurité<br>paramètre (recommandé)|Paramètre à l’invite de l’utilisateur<br>et remplacer disponible ?|
|---|---|---|---|---|
|ActiveX|Bureau|ActiveX initialisation des contrôles|**6**|**Oui** pour les valeurs suivantes : <ul><li>**3**</li><li>**4**</li><li>**5**</li><li>**6**</li></ul>|
|ActiveX|Bureau|Autoriser les formulaires Active X One Off|**Charger uniquement les contrôles Outlook**|Non|
|ActiveX|Bureau|Vérifier les objets ActiveX|Il ne s’agit pas d’un paramètre de base de sécurité.|Non|
|ActiveX|Bureau|Désactiver tous les contrôles ActiveX|Il ne s’agit pas d’un paramètre de base de sécurité.|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|ActiveX|Bureau|Charger des contrôles dans Forms3|**1**|**Oui** pour les valeurs suivantes : <ul><li>**2**</li><li>**3**</li></ul>|
|Les & extensibilité|Excel <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Désactiver la notification de la barre de confiance pour les applications non signées et les bloquer|**Enabled**|**Oui** pour la valeur **Disabled**.|
|Les & extensibilité|Excel <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Exiger la signature des compléments d’applications par un éditeur approuvé|**Enabled**|Non|
|Les & extensibilité|Excel|Ne pas afficher l’alerte d’avertissement AutoRepublish|**Disabled**|Non|
|Les & extensibilité|Excel|WebSERVICE Function Notification Paramètres|**Désactiver tout avec notification**|**Oui** pour les valeurs suivantes : <ul><li>**Désactiver tout avec notification**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Bureau|Désactiver le client Office de l’interrogation du serveur SharePoint pour les liens publiés|**Disabled**|Non|
|Les & extensibilité|Bureau|Désactiver l’interface utilisateur provenant des documents et des modèles|Disallow in Word = True <p> Ne pas être Project = False <p> Ne pas être Excel = True <p> Disallow in Visio= False <p> Ne pas être PowerPoint = True <p> Ne pas être autorisé dans Access = True <p> Ne pas être Outlook = True <p> Ne pas être Publisher = True <p> Disallow in InfoPath = True|Non|
|Les & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'accès à un carnet d'adresses|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Configurer Outlook’invite du modèle objet lors de l’accès à la propriété Formula d’un objet UserProperty|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'exécution de l'opération Enregistrer sous|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de la lecture d'informations relatives à des adresses|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de la réponse à des demandes de réunion et de tâches|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Configurer l'invite du modèle objet Outlook lors de l'envoi d'un message|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|Outlook|Définir Outlook’invite d’exécution des actions personnalisées du modèle objet|**Refus automatique**|**Oui** pour les valeurs suivantes : <ul><li>**Utilisateur d’invite**</li><li>**Invite de l’utilisateur en fonction de la sécurité de l’ordinateur**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Les & extensibilité|PowerPoint|Exécuter des programmes|**désactiver (ne pas exécuter de programmes)**|**Oui** pour la valeur **Enable (utilisateur d’invite avant l’exécution)**|
|Les & extensibilité|Word <p> Excel|Désactiver l’utilisation de manifestes par smart document|**Enabled**|Non|
|DDE|Excel|N’autorisez pas le lancement du serveur DDE (Dynamic Data Exchange) dans Excel|**Enabled**|**Oui** pour la valeur **Non configurée**.|
|DDE|Excel|N’autorisez pas la recherche de serveur DDE (Dynamic Data Exchange) dans Excel|**Enabled**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|DDE|Word|Données dynamiques Exchange|**Disabled**|Non|
|Jscript & VBScript|Outlook|Autoriser les scripts dans les formulaires Outlook uniques |**Disabled**|Non|
|Jscript & VBScript|Outlook|Ne pas autoriser Outlook scripts de modèle objet à s’exécuter pour les dossiers publics|**Enabled**|Non|
|Jscript & VBScript|Outlook|Ne pas autoriser Outlook scripts de modèle objet à s’exécuter pour les dossiers partagés|**Enabled**|Non|
|Macros|Excel|Macro Notifications|**Désactiver toutes les macros à l’exception des macros signées numériquement**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Accès <p> PowerPoint <p> Project <p> Éditeur <p> Visio <p> Word|Notification de macro VBA Paramètres|**Désactiver toutes les macros à l’exception des macros signées numériquement** <p> et <p> **Exiger la signature des macros par un éditeur approuvé**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Accès <p> Excel <p> PowerPoint <p> Visio <p> Word|Empêcher l’exécution de macros dans Office fichiers à partir d’Internet|**Enabled**|**Oui** pour les valeurs suivantes : <ul><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|Excel|Analyser les macros chiffrées dans Excel de travail Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|Macros|Bureau|Autoriser VBA à charger les références typelib par chemin d’accès à partir d’emplacements intranet non confiance|**Disabled**|Non|
|Macros|Bureau|Automation Security|**Utiliser le niveau de sécurité des macros de l'application**|Non|
|Macros|Bureau|Désactiver d’autres vérifications de sécurité sur les références de bibliothèque VBA qui peuvent faire référence à des emplacements non sécurisés sur l’ordinateur local|**Disabled**|Non|
|Macros|Bureau|Étendue de l’analyse d’exécuter les macros|**Activer pour tous les documents**|Non|
|Macros|Bureau|Faire confiance uniquement aux macros VBA qui utilisent des signatures V3|Il ne s’agit pas d’un paramètre de base de sécurité.|Non|
|Macros|Outlook|Outlook sécurité des données|**Utiliser la stratégie Outlook de sécurité de l’équipe**|Obligatoire pour activer tous les paramètres Outlook GPO. <p> Mentionné comme une dépendance (cette stratégie ne bloque pas le contenu actif lui-même).|
|Macros|Outlook|Paramètre de sécurité pour les macros|**Avertir pour signé, désactiver non signé**|**Oui** pour les valeurs suivantes : <ul><li>**Toujours avertir**</li><li>**Avertir pour signé, désactiver non signé**</li><li>**Disabled**</li><li>**Non configuré**</li></ul>|
|Macros|PowerPoint|Analyser les macros chiffrées dans PowerPoint présentations Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|Macros|Éditeur|Publisher niveau de sécurité Automation|**Par interface utilisateur (confirmation)**|Non|
|Macros|Word|Analyser les macros chiffrées dans les documents Word Open XML|**Analyser les macros chiffrées (valeur par défaut)**|Non|
|

### <a name="hkey_local_machine-settings"></a>HKEY_LOCAL_MACHINE paramètres

<p>

****
|Catégorie|Application|Nom de la stratégie|Base de référence de sécurité<br>paramètre (recommandé)|Paramètre à l’invite de l’utilisateur<br>et remplacer disponible ?|
|---|---|---|---|---|
|ActiveX|Bureau|Restreindre l’installation ActiveX |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|Les & extensibilité|Bureau|Gestion des modules complémentaires |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|Les & extensibilité|Bureau|Bloquer l’activation de Flash dans Office documents|Consultez les fichiers ADMX/ADML du Guide de sécurité Microsoft pour obtenir la liste des killbits COM qui bloquent toute activation de Flash sur Microsoft 365 applications. Les fichiers ADMX/ADML pour les lignes de base de sécurité d’entreprise sont disponibles dans la [Shared Computer Toolkit.](https://www.microsoft.com/download/details.aspx?id=55319)|Non|
|Jscript & VBScript|Bureau|Restreindre l’JScript héritée pour les Office|**Activé** : <p> Accès : 69632 <p> Excel : 69632 <p> OneNote : 69632 <p> Outlook : 69632 <p> PowerPoint : 69632 <p> Project : 69632 <p> Publisher : 69632 <p> Visio : 69632 <p> Word : 69632|Non|
|Jscript & VBScript|Bureau|Restrictions de sécurité de scripts de fenêtres |excel.exe = True <p> exprwd.exe = True <p> groove.exe = True <p> msaccess.exe = True <p> mse7.exe = True <p> mspub.exe = True <p> onent.exe = True <p> outlook.exe = True <p> powerpnt.exe = True <p> pptview.exe = True <p> spDesign.exe = True <p> visio.exe = True <p> winproj.exe = True <p> winword.exe = True|Non|
|
