---
title: Gérer les étiquettes de confidentialité dans les applications Office
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Informations pour que les administrateurs informatiques gèrent les étiquettes de niveau de confidentialité dans les applications Office pour le bureau, les appareils mobiles et le web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 04c87543f25cf3349f179fa4a7f3ebc523e3d6ec
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53656510"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Gérer les étiquettes de confidentialité dans les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous avez [publié](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) des étiquettes de niveau de confidentialité du Centre de conformité ou du Centre d’étiquettes équivalent Microsoft 365, elles commencent à apparaître dans les applications Office pour que les utilisateurs classifient et protègent les données dès qu’elles sont créées ou modifiées.

Les informations de cet article vous aideront à gérer les étiquettes de niveau de confidentialité dans les applications Office. Par exemple, identifiez les versions minimales d’applications dont vous avez besoin pour prendre en charge l’étiquette intégrée, et comprenez les interactions avec le client d’étiquetage unifiée Azure Information Protection, ainsi que la compatibilité avec d’autres applications et services.

## <a name="labeling-client-for-desktop-apps"></a>Client d’étiquetage pour les applications de bureau

Pour utiliser des étiquettes de niveau de confidentialité intégrées aux applications de bureau Office pour Windows et Mac, vous devez utiliser une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, telles qu’Office 2016 ou Office 2019.

Pour utiliser des étiquettes de niveau de confidentialité avec ces éditions autonomes d’Office sur les ordinateurs Windows, installez le [client étiquetage Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de confidentialité dans les applications

Pour chaque fonctionnalité, les tableaux suivants listent la version minimale d’Office dont vous avez besoin pour prendre en charge les étiquettes de niveau de confidentialité à l’aide d’étiquettes intégrées. Ou, si la fonctionnalité d’étiquette est en prévisualisation ou en cours de révision pour une prochaine version. Utilisez la [feuille de route de Microsoft 365](https://aka.ms/MIPC/Roadmap) pour obtenir des détails sur les futures versions.

Les nouvelles versions des applications Office sont disponibles à différents moments pour différents canaux de mise à jour. Pour plus d’informations, notamment sur la configuration de votre canal de mise à jour afin de tester une nouvelle fonctionnalité d’étiquetage qui vous intéresse, consultez [Présentation des canaux de mise à jour de Microsoft 365 Apps](/DeployOffice/overview-update-channels). Les nouvelles fonctionnalités en préversion privée ne sont pas incluses dans le tableau, mais il est possible que vous soyez en mesure de participer à ces préversions en nomant votre organisation pour le [programme de préversion privé Microsoft Information Protection](https://aka.ms/mip-preview).

> [!NOTE]
> Les noms des canaux de mise à jour des applications Office ont récemment changé. Par exemple, le Canal mensuel est désormais Canal actuel et Office Insider le Canal bêta. Si vous souhaitez en savoir plus, consultez [Modifications apportées aux canaux de mise à jour des applications Microsoft 365](/deployoffice/update-channels-changes).

Office pour iOS et Office pour Android : les étiquettes de niveau de confidentialité sont intégrées dans l’[application Office](https://www.microsoft.com/fr-FR/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

Des fonctionnalités supplémentaires sont disponibles lorsque vous installez le client de l’étiquetage unifié d’Azure Information Protection, qui s’exécute uniquement sur les ordinateurs Windows. Pour plus d’informations, consultez [Comparer les clients d’étiquetage pour les ordinateurs Windows](/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités d’étiquettes de confidentialité dans Word, Excel et PowerPoint

Les nombres répertoriés sont la version minimale de l’application Office requise pour chaque fonctionnalité.

|Fonctionnalité                                                                                                        |Windows |Mac |iOS    |Android      |Web                                                         |
|------------------------------------------------------------------------------------------------------------------|----------------|------------|-------|-------------|------------------------------------------------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/fr-FR/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | 2010+           | 16.42+     | 2.42+ | 16.0.13328+ | En cours de déploiement |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+          | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Inviter les utilisateurs](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |2004+ | 16.35+   | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Audit de l’activité des utilisateurs liée à une étiquette](data-classification-activity-explorer.md)                      | 2011+ | 16.43+ | 2.46+ | 16.0.13628+ | Oui <sup>\*</sup>                                                        |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | 2101+             | 16.45+         | 2.47+ | 16.0.13628+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | 2009+                                  | 16.44+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | 2009+                                  | En cours de révision | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Prise en charge de la co-édition et de l'enregistrement automatique](sensitivity-labels-coauthoring.md) pour les documents étiquetés et chiffrés | 2106+ |  16.50+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|

**Note de bas de page :**

<sup>\*</sup> N’inclut pas de texte de justification pour supprimer une étiquette ou abaisser le niveau de classification pour le moment

### <a name="sensitivity-label-capabilities-in-outlook"></a>Fonctionnalités d’étiquettes de confidentialité dans Outlook

Les nombres répertoriés sont la version minimale de l’application Office requise pour chaque fonctionnalité.

|Fonctionnalité                                                                                                        |Outlook pour Windows |Outlook pour Mac |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|------------------------------------------------------------------------------------------------------------------|---------------------------|------------------------|---------------|-------------------|-------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/fr-FR/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Ne pas transférer](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | 1910+                     | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Chiffrer uniquement](encryption-sensitivity-labels.md#let-users-assign-permissions)  |2011+ | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Oui |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | 2101+                        | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Oui                |
|[Audit de l’activité des utilisateurs liée à une étiquette](data-classification-activity-explorer.md) | 2011+ | Déploiement : 16.51+ <sup>\*</sup> | En cours de déploiement : 4.2126+ | En cours de déploiement : 4.2126+ | En cours de révision |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | 2009+                      | 16.44+ <sup>\*</sup>                    | En cours de révision           | En cours de révision               | Oui |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | 2009+                      | En cours de révision                    | En cours de révision           | En cours de révision               | Oui |
|[Paramètres différents pour l’étiquette par défaut et l’étiquette obligatoire](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | 2105+                      | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Oui |
|

**Notes de bas de page :**

<sup>\*</sup> Nécessite le [nouveau Outlook pour Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Client d’étiquetage intégré à Office et autres solutions d’étiquetage

Le client d’étiquetage intégré à Office télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir des Centres d’administration suivants :

- Centre de conformité Microsoft 365
- Centre de sécurité et conformité Office 365 (portail d’administration plus ancien)

Pour utiliser le client d’étiquetages intégré à Office, une ou plusieurs [stratégies d’étiquette doivent être publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) auprès des utilisateurs de l’un des Centres d’administration répertoriés et d’une [version prise en charge d’Office](#support-for-sensitivity-label-capabilities-in-apps).

Si ces deux conditions sont remplies mais que vous devez désactiver le client d’étiquetage intégré à Office, utilisez le paramètre de stratégie de groupe suivant :

1. Accédez à **Configuration de l'utilisateur/Stratégies/Modèles d'administration/Microsoft Office 2016/Paramètres de sécurité**.

2. Définissez **Utiliser la fonctionnalité de niveau de confidentialité d’Office pour appliquer et afficher les étiquettes de niveau de confidentialité** à **0**. 
 
Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service). Le paramètre prend effet lorsque les applications Office redémarrent.

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Client d’étiquetage intégré à Office et client Azure Information Protection

Si les clients ont [Azure Information Protection installé](/azure/information-protection/rms-client/aip-clientv2), par défaut, le client d’étiquetage intégré est désactivé dans leurs applications Office. 

Pour utiliser l’étiquetage intégrée plutôt que le client Azure Information Protection pour les applications Office, nous vous recommandons d’utiliser le paramètre de stratégie de groupe **Liste des compléments gérés** telle que documentée dans [Aucun complément chargé en raison des paramètres de stratégie de groupe pour les programmes Office 2013 et Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

Pour Microsoft Word 2016, Excel 2016, PowerPoint 2016 et Outlook 2016, spécifiez les identificateur programmatique suivants pour le client Azure Information Protection et définissez l’option **0 : le complément est toujours désactivé (bloqué)**

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 


Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service).

> [!NOTE]
> Si vous utilisez le paramètre de stratégie de groupe **Utiliser la fonctionnalité de confidentialité d’Office pour appliquer et afficher les étiquettes de confidentialité** et définissez ce paramètre sur **1**, dans certains cas, le client Azure Information Protection risque de se charger encore dans les applications Office. Le blocage du chargement du complément dans chaque application empêche que cela ne se produise.

Vous pouvez également désactiver ou supprimer de manière interactive le complément Office **Microsoft Azure Information Protection** de Word, Excel, PowerPoint et Outlook. Cette méthode est appropriée pour un ordinateur unique et des tests ad-hoc. Pour obtenir de instructions, consultez [Afficher, gérer et installer des compléments dans les programmes Office (pour les utilisateurs)](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d). 

Quelle que soit la méthode choisie, les modifications prennent effet au redémarrage des applications Office. Le client Azure Information Protection reste installé sur l’ordinateur, ce qui vous permet de continuer à étiqueter des fichiers en dehors de vos applications Office en désactivant ou en supprimant ce dernier. Par exemple, à l’aide de l’Explorateur de fichiers ou de PowerShell.

Pour plus d’informations sur les fonctionnalités pris en charge par les clients Azure Information Protection et le client d’étiquetage intégré à Office, consultez [Choisir votre solution d’étiquetage Windows](/azure/information-protection/rms-client/use-client#choose-your-windows-labeling-solution) dans la documentation sur la protection des informations Azure.

## <a name="office-file-types-supported"></a>Types de fichiers Office pris en charge

Les applications Office qui utilisent des étiquetages intégrés pour les fichiers Word, Excel et PowerPoint utilisent le format Open XML (par exemple, .docx et .xlsx) mais pas les formats Microsoft Office 97-2003 (tels que .doc et .xls), les formats Open Document (tels que .odt et .ods) ou d’autres formats. Lorsqu’un type de fichier n’est pas pris en charge pour l'étiquetage intégré, le bouton **Niveau de confidentialité** n’est pas disponible dans l’application Office.

Le client d’étiquetage unifié Azure Information Protection prend en charge les formats Open XML et Microsoft Office 97-2003. Pour plus d’informations, consultez [Types de fichiers pris en charge par le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) à partir du guide d’administration de ce client.

Pour les autres solutions d'étiquetage, consultez leur documentation pour connaître les types de fichiers pris en charge.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de niveau de confidentialité

Les [modèles de protection](/azure/information-protection/configure-policy-templates) définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez un étiquetage intégré. Cette expérience simplifiée illustre le fait qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus avec les étiquettes de niveau de confidentialité dont le chiffrement est activé.

Si vous devez convertir des modèles de protection existants en étiquettes, utilisez le Portail Azure et les instructions suivantes : [Pour convertir des modèles en étiquettes](/azure/information-protection/configure-policy-templates#to-convert-templates-to-labels).

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Options de gestion des droits relatifs à l'information (IRM) et étiquettes de niveau de confidentialité

Les étiquettes de niveau de confidentialité que vous configurez pour appliquer le chiffrement suppriment la complexité des utilisateurs afin de spécifier leurs propres paramètres de chiffrement. Dans de nombreuses applications Office, ces paramètres de chiffrement individuels peuvent toujours être configurés manuellement par les utilisateurs à l’aide des options de gestion des droits relatifs à l'information (IRM). Par exemple, pour les applications Windows :

- Pour un document : **Fichier** > **Informations** > **Protéger le document** > **Restreindre l’accès**
- pour un courrier électronique : Sous l’onglet **Options** > **Chiffrer** 
  
Lorsque les utilisateurs étiquettent initialement un document ou un e-mail, ils peuvent remplacer les paramètres de configuration de votre étiquette par leurs propres paramètres de chiffrement. Par exemple :

- Un utilisateur applique l’étiquette **Confidentiel \ Tous les employés** à un document. Cette étiquette est configurée pour appliquer des paramètres de chiffrement à tous les utilisateurs de l’organisation. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès à un utilisateur extérieur à votre organisation. Le résultat final est un document étiqueté **Confidentiel \ Tous les employés** et chiffré, mais les utilisateurs de votre organisation ne peuvent pas l’ouvrir comme prévu.

- Un utilisateur applique l’étiquette **Confidentiel \ Destinataires uniquement** à un message électronique. Ce message est configuré pour appliquer le paramètre de chiffrement de **Ne pas transférer**. Dans l’application Outlook, cet utilisateur sélectionne ensuite manuellement le paramètre IRM pour Chiffrer uniquement. Le résultat final est que même si le courrier électronique reste chiffré, il peut être transmis par les destinataires, même s’il porte l’étiquette **Confidentiel \ Destinataires uniquement**.
    
    À titre d’exception, pour Outlook sur le web, les options du menu **Chiffrer** ne sont pas disponibles pour qu’un utilisateur puisse les sélectionner lorsque l’étiquette actuellement sélectionnée applique le chiffrement.

- Un utilisateur applique l’étiquette **Général** à un document, et cette étiquette n’est pas configurée pour appliquer le chiffrement. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès au document. Le résultat final est un document étiqueté **Général**, mais qui applique également le chiffrement de sorte que certains utilisateurs ne peuvent pas l’ouvrir comme prévu.

Si le document ou l'e-mail est déjà étiqueté, un utilisateur peut effectuer l'une de ces actions si le contenu n'est pas déjà chiffré ou s'il dispose du [droit d'utilisation](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Exporter ou Contrôle total. 

Pour une expérience d’étiquette plus cohérente avec des rapports significatifs, fournissez des étiquettes et des instructions appropriées aux utilisateurs afin qu’ils appliquent uniquement des étiquettes pour protéger les documents et e-mails. Par exemple :

- Pour les cas d’exception, les utilisateurs doivent attribuer leurs propres autorisations, fournir des étiquettes qui [permettent aux utilisateurs d’attribuer leurs propres autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- Pour éviter que les utilisateurs suppriment manuellement le chiffrement après avoir sélectionné une étiquette qui l’applique, offrez une alternative de sous-étiquette lorsque les utilisateurs ont besoin d’une étiquette avec la même classification, mais pas de chiffrement. Par exemple :
    - **Confidentiel \ Tous les employés**
    - **Confidentiel \ Tout le monde (aucun chiffrement)**

- Désactivez les paramètres IRM pour empêcher les utilisateurs de les sélectionner :
    - Outlook pour Windows : 
        - Clés de Registre (DWORD:00000001) *DisableDNF* et *DisableEO* de HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM
        - S’assurer que le paramètre de stratégie **Configurer l’option de chiffrement par défaut pour le bouton Chiffrer** n’est pas configuré
    - Outlook pour Mac : 
        - Clés des paramètres de sécurité *DisableEncryptOnly* et *DisableDoNotForward* documentées dans [Définir les préférences pour Outlook pour Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook sur le web : 
        - Paramètres *SimplifiedClientAccessDoNotForwardDisabled* et *SimplifiedClientAccessEncryptOnlyDisabled* documentés pour [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook pour iOS et Android : ces applications ne prennent pas en charge l'application de chiffrement sans étiquette par les utilisateurs, donc rien à désactiver.

> [!NOTE]
> Si les utilisateurs suppriment manuellement le chiffrement d’un document étiqueté stocké dans SharePoint ou OneDrive et que vous avez [activé les étiquettes de niveau de confidentialité des fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), le chiffrement d’étiquettes est restauré automatiquement au prochain accès ou téléchargement du document. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Appliquer des étiquettes de niveau de confidentialité aux fichiers, courriers électroniques et pièces jointes

Les utilisateurs ne peuvent appliquer qu’une étiquette à la fois pour chaque document ou e-mail.

Lorsque vous étiquetez un courrier électronique qui contient des pièces jointes, celles-ci héritent de l’étiquette uniquement si l’étiquette que vous appliquez au courrier électronique applique le chiffrement et que la pièce jointe qui est un document Office n’est pas déjà chiffré. Étant donné que l’étiquette héritée applique le chiffrement, la pièce jointe devient de nouveau chiffrée.

Une pièce jointe n’hérite pas des étiquettes du courrier électronique lorsque l’étiquette appliquée au courrier électronique n’applique pas le chiffrement ou si la pièce jointe est déjà chiffrée.

Exemples d’héritage des étiquettes, où l’étiquette **Confidentiel** applique le chiffrement et l’étiquette **Général** n’applique pas le chiffrement :

- Un utilisateur crée un courrier électronique et applique l’étiquette **Confidentiel** à ce message. Ils ajoutent ensuite un document Word qui n’est pas étiqueté ou chiffré. À la suite de l'héritage, le document est nouvellement étiqueté **Confidentiel** et le chiffrement est désormais appliqué à partir de cette étiquette.

- Un utilisateur crée un courrier électronique et applique l’étiquette **Confidentiel** à ce message. Ils ajoutent ensuite un document Word étiqueté **Général** ce fichier n’est pas chiffré. À la suite de l'héritage, le document est étiqueté de nouveau **Confidentiel** et le chiffrement est désormais appliqué à partir de cette étiquette.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de confidentialité

**Avec des applications RMS** : si vous ouvrez un document ou un courrier électronique chiffrés et étiquetés dans une [application RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de niveau de confidentialité, l’application applique toujours le chiffrement et la gestion des droits.

**Avec le client Azure Information Protection** : vous pouvez afficher et modifier les étiquettes de niveau de confidentialité que vous appliquez aux documents et courriers électroniques à l’aide du client d’étiquetage intégré à Office à l’aide du client Azure Information Protection, et inversement.

**Avec les autres versions d’Office** : tous les utilisateurs autorisés peuvent ouvrir des documents étiquetés et des messages électroniques dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions d’Office pris en charge ou à l’aide du client Azure Information Protection. Les versions des logiciels Office pris en charge sont répertoriées dans la [section précédente](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par des étiquettes de niveau de confidentialité

Pour utiliser le client d’étiquetage intégré à Office avec Office sur le web pour les documents dans SharePoint ou OneDrive, assurez-vous que vous avez [activé étiquettes de niveau de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Prise en charge des utilisateurs externes et du contenu étiqueté

Lorsque vous étiquetez un document ou un message électronique, l’étiquette est stockée en tant que métadonnées incluant votre client et un GUID d’étiquette. Lorsqu’un document ou un courrier électronique étiquetés est ouvert par une application Office qui prend en charge les étiquettes de niveau de confidentialité, ces métadonnées sont lues et uniquement si l’utilisateur appartient au même client, l’étiquette s’affiche dans son application. Par exemple, pour les étiquettes intégrées pour Word, PowerPoint et Excel, le nom de l’étiquette s’affiche dans la barre d’état. 

Cela signifie que si vous partagez des documents avec une autre organisation qui utilise des noms d’étiquettes différents, chaque organisation peut appliquer et voir sa propre étiquette appliquée au document. Toutefois, les éléments suivants d’une étiquette appliquée sont visibles par les utilisateurs extérieurs à votre organisation :

- Marquages de contenu. Lorsqu’une étiquette applique un en-tête, un pied de page ou un filigrane, ceux-ci sont ajoutés directement au contenu et restent visibles jusqu’à ce que quelqu’un les modifie ou les supprime.

- Nom et description du modèle de protection sous-jacente à partir d’une étiquette qui applique le chiffrement. Ces informations s’affichent dans une barre des messages en haut du document, pour fournir des informations sur les personnes autorisées à ouvrir le document et leurs droits d’utilisation pour ce document.

### <a name="sharing-encrypted-documents-with-external-users"></a>Partage de documents chiffrés avec des utilisateurs externes

En plus de restreindre l’accès aux utilisateurs de votre propre organisation, vous pouvez étendre l’accès à tout autre utilisateur possédant un compte dans Azure Active Directory. Toutefois, si votre organisation utilise des stratégies d’accès conditionnel, consultez la [section suivante](#conditional-access-policies) pour considérations supplémentaires.

Toutes les applications Office et autres [applications RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) peuvent ouvrir des documents chiffrés une fois que l’utilisateur s’est authentifié correctement. 

Si les utilisateurs externes n’ont pas de compte dans Azure Active Directory, ils peuvent s’authentifier à l’aide de comptes invités dans votre client. Ces comptes invités peuvent également servir à accéder à des documents partagés dans SharePoint ou OneDrive lorsque vous avez [activé des étiquettes de niveau de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

- Une option consiste à créer ces comptes invités vous-même. Vous pouvez spécifier une adresse de messagerie que ces utilisateurs utilisent déjà. Par exemple, son adresse Gmail.
    
    Cette option vous permet de restreindre l’accès et les droits à des utilisateurs spécifiques en spécifiant leur adresse de messagerie dans les paramètres de chiffrement. L'inconvénient est la surcharge administrative liée à la création du compte et à la coordination avec la configuration de l'étiquette.

- Une autre option consiste à utiliser [intégration de SharePoint et OneDrive à Azure AD B2B (préversion)](/sharepoint/sharepoint-azureb2b-integration-preview) de sorte que les comptes invités soient créés automatiquement lorsque vos utilisateurs partagent des liens.
    
    Cette option offre un coût d’administration minimal, car les comptes sont créés automatiquement et une configuration d’étiquette plus simple. Dans ce scénario, vous devez sélectionner l’option de chiffrement [Ajouter des utilisateur authentifiés](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users), car vous ne connaissez pas les adresses de messagerie à l’avance. Ce paramètre ne vous permet pas de restreindre l’accès et les droits d’utilisation à des utilisateurs spécifiques.

Les utilisateurs externes peuvent également utiliser un compte Microsoft pour ouvrir des documents chiffrés lorsqu’ils utilisent les applications Windows et Microsoft 365 ([anciennement des applications Office 365](/deployoffice/name-change)) ou la version autonome d’Office 2019. Plus récemment pris en charge pour les autres plateformes, les comptes Microsoft sont également pris en charge pour l’ouverture de documents chiffrés sur macOS (Microsoft 365 Apps, version 16.42+), Android (version 16.0.13029+) et iOS (version 2.42+). Par exemple, un utilisateur de votre organisation partage un document chiffré avec un utilisateur extérieur à votre organisation, et les paramètres de chiffrement spécifient une adresse de messagerie Gmail pour l’utilisateur externe. Cet utilisateur externe peut créer son propre compte Microsoft qui utilise son adresse de messagerie Gmail. Ensuite, une fois qu’ils se sont ouverts avec ce compte, ils peuvent ouvrir le document et le modifier, conformément aux restrictions d’utilisation qui leur sont spécifiées. Pour consulter un exemple pas à pas de ce scénario, consultez[Ouverture et modification du document protégé](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> L’adresse de messagerie du compte Microsoft doit correspondre à l’adresse de messagerie spécifiée pour restreindre l’accès aux paramètres de chiffrement.

Lorsqu’un utilisateur avec un compte Microsoft ouvre un document chiffré de cette façon, il crée automatiquement un compte invité pour le client si un compte invité du même nom n’existe pas encore. Lorsque le compte invité existe, il peut ensuite être utilisé pour ouvrir des documents dans SharePoint et OneDrive à l’aide d’Office sur le web, en plus d’ouvrir des documents chiffrés à partir des applications Office de bureau et mobiles pris en charge.

Toutefois, le compte invité automatique n’est pas créé immédiatement dans ce scénario, en raison d’une latence de réplication. Si vous spécifiez des adresses de messagerie personnelles dans le cadre de vos paramètres de chiffrement d’étiquettes, nous vous recommandons de créer des comptes invités correspondants dans Azure Active Directory. Indiquez ensuite à ces utilisateurs qu’ils doivent utiliser ce compte pour ouvrir un document chiffré de votre organisation.

> [!TIP]
> Étant donné que vous ne savez pas si les utilisateurs externes utiliseront une application cliente Office prise en charge, le partage de liens à partir de SharePoint et OneDrive après avoir créé des comptes invités (pour des utilisateurs spécifiques) ou lorsque vous utilisez [l’intégration de SharePoint et OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) (pour tout utilisateur authentifié) est une méthode plus fiable pour prendre en charge la collaboration sécurisée avec les utilisateurs externes.

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Si votre organisation a implémenté des [stratégies d’accès conditionnel Azure Active Directory](/azure/active-directory/conditional-access/overview), vérifiez leur configuration. Si les stratégies incluent **Microsoft Azure Information Protection** et que la stratégie s’étend aux utilisateurs externes, ces utilisateurs externes doivent avoir un compte invité dans votre client, même s’ils ont un compte Azure AD dans leur propre client.

Sans ce compte invité, ils ne peuvent pas ouvrir le document chiffré et voir un message d’erreur. Le texte du message peut l’informer que son compte doit être ajouté en tant qu’utilisateur externe dans le client, avec des instructions incorrectes pour ce scénario pour **SSe déconnecter et se reconnecter avec un compte utilisateur Azure Active Directory différent.**.

Si vous ne pouvez pas créer et configurer des comptes invités dans votre client pour des utilisateurs externes qui doivent ouvrir des documents chiffrés par vos étiquettes, vous devez supprimer Azure Information Protection des stratégies d’accès conditionnel ou exclure des utilisateurs externes des stratégies.

Pour plus d’informations sur l’accès conditionnel et Azure Information Protection, le service de chiffrement utilisé par les étiquettes de niveau de confidentialité, consultez la question fréquemment posée, [Azure Information Protection est répertorié comme application cloud disponible pour l’accès conditionnel. Comment cela fonctionne-t-il ?](/azure/information-protection/faqs#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Délai de marquage et de chiffrage de contenus par les applications Office.

Selon l’application que vous utilisez, les applications Office appliquent différemment le marquage et le chiffrement de contenu avec une étiquette de niveau de sensible.

| Application | Marquage du contenu | Chiffrement |
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Après l’envoi du message électronique par Exchange Online | Immédiatement |
| Outlook sur le web, iOS et Android | Après l’envoi du message électronique par Exchange Online | Après l’envoi du message électronique par Exchange Online |
|

Pour ce faire, vous pouvez utiliser les solutions qui appliquent des étiquettes de niveau de confidentialité aux fichiers en dehors des applications Office en leur appliquant des métadonnées d’étiquette. Dans ce scénario, le contenu marqué à partir de la configuration de l’étiquette n’est pas inséré dans le fichier, mais le chiffrement est appliqué. 

Lorsque ces fichiers sont ouverts dans une application de bureau Office, les marquages de contenu sont automatiquement appliquées par le client de l’étiquetage unifié d’Azure Information Protection. Les marques de contenu ne sont pas automatiquement appliquées lorsque vous utilisez l’étiquette intégrée pour les applications de bureau, mobiles ou web.

Les scénarios qui incluent l’application d’une étiquette de confidentialité en dehors des applications Office sont les suivants :

- Scanneur, Explorateur de fichiers et PowerShell à partir du client d’étiquetage unifié Azure Information Protection 

- Stratégies d’étiquetage automatique pour SharePoint et OneDrive

- Données étiquetées et chiffrées exportées à partir de Power BI

- Microsoft Cloud App Security

Dans ces scénarios, à l’aide de leurs applications Office, un utilisateur avec une étiquette intégrée peut appliquer les marquages de contenu de l’étiquette en supprimant ou en remplaçant temporairement l’étiquette actuelle, puis en rappliquant l’étiquette d’origine.

### <a name="dynamic-markings-with-variables"></a>Marquages dynamiques avec des variables

> [!IMPORTANT]
> Actuellement, toutes les applications, sur toutes les plateformes, ne prennent pas en charge les marquages de contenu dynamiques que vous pouvez spécifier pour vos en-têtes, pieds de page et filigranes. Pour les applications qui ne prennent pas en charge cette fonctionnalité, elles appliquent les marquages comme le texte original spécifié dans la configuration de l'étiquette, plutôt que de résoudre les variables.
> 
> Le client de l’étiquetage unifié Azure Information Protection prend en charge les marquages dynamiques. Pour obtenir des étiquetages intégrés à Office, consultez les tableaux de la section [fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) sur cette page pour connaître les versions minimales prises en charge.

Lorsque vous configurez une étiquette de confidentialité pour le marquage du contenu, vous pouvez utiliser les variables suivantes dans la chaîne de texte pour votre en-tête, pied de page ou filigrane :

| Variable | Description | Exemple lors de l’application d’une étiquette |
| -------- | ----------- | ------- |
| `${Item.Label}` | Nom complet de l’étiquette appliquée | **Général**|
| `${Item.Name}` | Nom de fichier ou objet du courrier électronique du contenu étiqueté | **Sales.docx** |
| `${Item.Location}` | Chemin d’accès et nom de fichier du document étiqueté, ou objet du courrier électronique étiqueté | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Nom d’affichage de l’utilisateur appliquant l’étiquette | **Richard Simone** |
| `${User.PrincipalName}` | Nom d’utilisateur principal Azure AD de l’utilisateur appliquant l’étiquette | **rsimone\@contoso.com** |
| `${Event.DateTime}` | Date et heure auxquelles le contenu est étiqueté, dans le fuseau horaire local de l’utilisateur appliquant l’étiquette dans les applications Microsoft 365, ou UTC (temps universel coordonné) pour Office Online et les stratégies d’étiquetage automatique | **10/08/2020 13:30** |

> [!NOTE]
> La syntaxe de ces variables respecte la casse.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Définition de différents marquages visuels pour Word, Excel, PowerPoint et Outlook

En tant que variable supplémentaire, vous pouvez configurer des marquages visuels par type d’application Office à l’aide d’une instruction de variable « If.App » dans la chaîne de texte et identifier le type d’application à l’aide des valeurs **Word**, **Excel**, **PowerPoint** ou **Outlook**. Vous pouvez également abréger ces valeurs, ce qui est nécessaire si vous souhaitez en spécifier plusieurs dans la même instruction If.App.

Utilisez la syntaxe suivante :

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Comme pour les autres marquages visuels dynamiques, la syntaxe est sensible à la casse, ce qui inclut les abréviations pour chaque type d’application (WEPO).

Exemples :

- **Définissez le texte d’en-tête des documents Word uniquement :**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Dans les en-têtes de document Word uniquement, l’étiquette applique le texte d’en-tête « Ce document Word est sensible ». Aucun texte d’en-tête n’est appliqué aux autres applications Office.

- **Définissez le texte du pied de page pour Word, Excel et Outlook, et le texte du pied de pied de l’autre dans PowerPoint :**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    Dans Word, Excel et Outlook, l’étiquette applique le texte de pied de page « Ce contenu est confidentiel ». Dans PowerPoint, l’étiquette applique le texte de pied de l’étiquette « Cette présentation est confidentielle ».

- **Définissez un texte de filigrane spécifique pour Word et PowerPoint, puis du texte en filigrane pour Word, Excel et PowerPoint :**

    `${If.App.WP}This content is ${If.End}Confidential`

    Dans Word et PowerPoint, l’étiquette applique le texte en filigrane « Ce contenu est confidentiel ». Dans Excel, l’étiquette applique le texte en filigrane « Confidentiel ». Dans Outlook, l’étiquette n’applique pas de texte en filigrane, car les filigranes en tant que marquages visuels ne sont pas pris en charge dans Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents

> [!IMPORTANT]
> 
> Le [client de l’étiquetage unifié d’Azure Information Protection](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) prend en charge cette configuration également appelée étiquetage obligatoire. Pour obtenir des étiquetages intégrés aux applications Office, consultez les tableaux de la section [fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) sur cette page pour connaître les versions minimales prises en charge.
>
> Pour utiliser l’étiquetage obligatoire pour les documents et non pour les e-mails, consultez les instructions de la section suivante qui explique comment configurer les options spécifiques à Outlook.
> 
> Pour utiliser l’étiquetage obligatoire pour Power BI, consultez [Stratégie d’étiquette obligatoire pour Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).

Lorsque ce paramètre de stratégie **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails et documents** est sélectionné, les utilisateurs affectés à la stratégie doivent sélectionner et appliquer une étiquette de confidentialité dans les scénarios suivants :

- Spécifique au client d’étiquetage unifié Azure Information Protection :
    - Pour les documents (Word, Excel, PowerPoint) : lorsqu’un document sans texte est enregistré ou que les utilisateurs ferment le document.
    - Pour les messages électroniques (Outlook) : à l’heure où les utilisateurs envoient un message sans texte.

- Pour obtenir des étiquettes intégrées aux applications Office :
    - Pour les documents (Word, Excel, PowerPoint) : lorsqu’un document sans texte est ouvert ou enregistré.
    - Pour les messages électroniques (Outlook) : à l’heure où les utilisateurs envoient un courrier sans texte.

Informations supplémentaires sur l’étiquetage intégré :

- Lorsque les utilisateurs sont invités à ajouter une étiquette de confidentialité parce qu’ils ouvrent un document sans étiquette, ils peuvent ajouter une étiquette ou choisir d’ouvrir le document en mode lecture seule.

- Lorsque l’étiquette obligatoire est en vigueur, les utilisateurs ne peuvent pas supprimer les étiquettes de niveau de confidentialité des documents, mais peuvent modifier une étiquette existante.

Pour obtenir des instructions sur l’utilisation de ce paramètre, consultez les informations sur [paramètres de stratégie](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Si vous utilisez le paramètre de stratégie d’étiquette par défaut pour les documents et messages électroniques en plus de l’étiquette obligatoire : 
>
> L’étiquette par défaut a toujours la priorité sur l’étiquette obligatoire. Toutefois, pour les documents, le client d’étiquetage unifié Azure Information Protection applique l’étiquette par défaut à tous les documents sans étiquettes, tandis que l’étiquette intégrée applique l’étiquette par défaut aux nouveaux documents et non aux documents existants sans étiquettes. Cette différence de comportement signifie que lorsque vous utilisez une étiquette obligatoire avec le paramètre d’étiquette par défaut, les utilisateurs sont invités à appliquer une étiquette de confidentialité plus souvent lorsqu’ils utilisent un étiquetage intégré que lorsqu’ils utilisent le client d’étiquetage unifié Azure Information Protection.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Options spécifiques à Outlook pour l’étiquetage par défaut et l’étiquetage obligatoire

Pour l’étiquetage intégré, identifiez les versions minimales d’Outlook qui prennent en charge ces fonctionnalités à l’aide du [tableau des fonctionnalités pour Outlook](#sensitivity-label-capabilities-in-outlook) sur cette page, et la ligne **Paramètres différents pour l’étiquette par défaut et l’étiquetage obligatoire**. Toutes les versions du client d’étiquetage unifié Azure Information Protection prennent en charge ces options spécifiques à Outlook.

Lorsque l’application Outlook prend en charge un paramètre d’étiquette par défaut différent du paramètre d’étiquette par défaut des documents :

- Dans l’assistant de stratégie d’étiquette, à la page **Appliquer une étiquette par défaut aux e-mails**, vous pouvez spécifier votre choix d’étiquette de confidentialité qui s’appliquera à tous les e-mails sans étiquette, ou aucune étiquette par défaut. Ce paramètre est indépendant du paramètre **Appliquer cette étiquette par défaut aux documents** de la page précédente **Paramètres de stratégie pour les documents** de l’assistant.

Lorsque l’application Outlook ne prend pas en charge un paramètre d’étiquette par défaut différent du paramètre d’étiquette par défaut des documents : Outlook utilise toujours la valeur que vous spécifiez pour **Appliquer cette étiquette par défaut aux documents** à la page **Paramètres de stratégie pour les documents** page de l’assistant stratégie d’étiquette.

Lorsque l’application Outlook prend en charge la désactivation de l’étiquetage obligatoire :

- Dans l’assistant de stratégie d’étiquette, à la page **Paramètres de stratégie**, sélectionnez **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails ou documents**. Sélectionnez ensuite **Suivant** > **Suivant**, puis décochez la case **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails**. Laissez la case cochée si vous souhaitez que l’étiquetage obligatoire s’applique aux e-mails et aux documents.

Lorsque l’application Outlook ne prend pas en charge la désactivation de l’étiquetage obligatoire : si vous sélectionnez **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails ou documents** en tant que paramètre de stratégie, Outlook invite toujours les utilisateurs à sélectionner une étiquette pour les e-mails sans étiquette.

> [!NOTE]
> Si vous avez configuré les paramètres avancés PowerShell **OutlookDefaultLabel** et **DisableMandatoryInOutlook** à l’aide des cmdlets [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) ou [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) :
> 
> Les valeurs que vous avez choisies pour ces paramètres PowerShell apparaissent dans l’assistant de stratégie d’étiquette et fonctionnent automatiquement pour les applications Outlook qui prennent en charge ces paramètres. Les autres paramètres avancés de PowerShell restent pris en charge pour le client d’étiquetage unifié Azure Information Protection uniquement.

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/fr-FR/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.microsoft.com/fr-FR/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
