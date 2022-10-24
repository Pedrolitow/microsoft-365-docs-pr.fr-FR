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
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier1
search.appverid:
- MOE150
- MET150
description: Informations pour que les administrateurs informatiques gèrent les étiquettes de niveau de confidentialité dans les applications Office pour le bureau, les appareils mobiles et le web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 24ddef2f66af1a707e061f40fcfced27d4094613
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68685017"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Gérer les étiquettes de confidentialité dans les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous avez [publié](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) des étiquettes de sensibilité à partir du portail de conformité Microsoft Purview, elles commencent à apparaître dans les applications Office pour que les utilisateurs puissent classer et protéger les données lorsqu'elles sont créées ou modifiées.

Use the information in this article to help you successfully manage sensitivity labels in Office apps. For example, identify the minimum versions of apps you need for features that are specific to built-in labeling, any additional configuration information for these features, and understand interactions with the Azure Information Protection unified labeling client and other apps and services.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="labeling-client-for-desktop-apps"></a>Client d’étiquetage pour les applications de bureau

Pour utiliser des étiquettes de niveau de confidentialité intégrées aux applications de bureau Office pour Windows et Mac, vous devez utiliser une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, parfois appelées « Office Perpétuelle ».

Le [client d’étiquetage unifié Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) est désormais en [mode maintenance](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613). Si vous utilisez actuellement ce client pour l’étiquetage dans les applications Office, nous vous recommandons de passer à l’étiquetage intégré. Pour plus d’informations, consultez [Migrer le complément Azure Information Protection (AIP) vers l’étiquetage intégré pour les applications Office](sensitivity-labels-aip.md).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de confidentialité dans les applications

Les tableaux suivants répertorient la version minimale d’Office qui a introduit des fonctionnalités spécifiques pour les étiquettes de confidentialité intégrées aux applications Office. Ou, si la fonctionnalité d’étiquette est en préversion publique ou en cours de révision pour une version ultérieure :

- [Tableau des fonctionnalités pour Word, Excel et PowerPoint](#sensitivity-label-capabilities-in-word-excel-and-powerpoint)
- [Tableau des fonctionnalités pour Outlook](#sensitivity-label-capabilities-in-outlook)

Utilisez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Information%20Protection&searchterms=label) pour plus d’informations sur les nouvelles fonctionnalités d’étiquetage prévues pour les versions ultérieures.

Les nouvelles versions des applications Office sont disponibles à différents moments pour différents canaux de mise à jour. Pour Windows, vous obtenez les nouvelles fonctionnalités plus tôt lorsque vous êtes sur le canal actuel ou le canal Enterprise mensuel, plutôt que sur Semi-Annual Enterprise canal. Les numéros de version minimum peuvent également être différents d’un canal de mise à jour à l’autre. Pour plus d’informations, voir [Vue d’ensemble des](/deployoffice/overview-update-channels) canaux de mise à jour Microsoft 365 Apps et historique des mises à jour [pour Microsoft 365 Apps](/officeupdates/update-history-microsoft365-apps-by-date).

Les nouvelles fonctionnalités qui sont en préversion privée ne sont pas incluses dans les tables, mais vous pouvez peut-être rejoindre ces préversions en nommant votre organisation pour le [programme de préversion privée Protection des données Microsoft](https://aka.ms/mip-preview).

Office pour iOS et Office pour Android : les étiquettes de niveau de confidentialité sont intégrées dans l’[application Office](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

> [!TIP]
> Lorsque vous comparez les versions minimales des tables aux versions dont vous disposez, n’oubliez pas la pratique courante des versions de mise en production pour omettre les zéros non significatifs.
> 
> Par exemple, vous avez la version 4.2128.0 et lisez que 4.7.1+ est la version minimale. Pour faciliter la comparaison, lisez 4.7.1 (sans zéros non significatifs) en tant que 4.**0007**.1 (et non 4.**7000**.1). Votre version de 4.2128.0 est supérieure à 4.0007.1. Votre version est donc prise en charge.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités d’étiquettes de confidentialité dans Word, Excel et PowerPoint

Les nombres répertoriés sont les versions minimales de l’application Office requise pour chaque fonctionnalité. 

> [!NOTE]
> For Windows and the Semi-Annual Enterprise Channel, the minimum supported version numbers might not yet be released. [Learn more](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Fonctionnalité |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Complément AIP désactivé par défaut](sensitivity-labels-aip.md#how-to-configure-newer-versions-of-office-to-enable-the-aip-add-in)| Préversion : déploiement sur le [Canal bêta](https://office.com/insider) | Non pertinent  | Non pertinent | Non pertinent| Non pertinent |
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Prise en charge multilingue](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | En cours de révision |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do) aux nouveaux documents                                         | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do) à des documents existants | Canal actuel : 2208+ <br /><br> Canal Entreprise mensuel : 2207+  <br /><br> Semi-Annual Enterprise canal : en cours de révision | 16.63+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+  <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | Canal actuel : 2010+ <br /><br> Canal mensuel des entreprises : 2010+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> - Demander aux utilisateurs des autorisations personnalisées (utilisateurs et groupes)](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Canal actuel : 2004+ <br /><br> Canal Entreprise mensuel : 2004+ <br /><br> Semi-Annual Enterprise canal : 2008+ | 16.35+   | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> - Demander aux utilisateurs des autorisations personnalisées (utilisateurs, groupes et organisations)](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions)                     |Préversion : déploiement sur le [Canal bêta](https://office.com/insider)  | En cours de révision   | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Audit de l’activité des utilisateurs liée à une étiquette](#auditing-labeling-activities)                      | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Canal d’entreprise semestriel | 16.43+ | 2.46+ | 16.0.13628+ | Oui |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | Canal actuel : 2101+ <br /><br> Canal Entreprise mensuel : 2101+ <br /><br> Canal d’entreprise semestriel | 16.45+         | 2.47+ | 16.0.13628+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | Canal actuel : 2009+ <br /><br> Canal Enterprise mensuel : 2009+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.44+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2108+ | 16.49+ | En cours de révision | En cours de révision | [En cours de révision |
|[Prise en charge de la co-édition et de l'enregistrement automatique](sensitivity-labels-coauthoring.md) pour les documents étiquetés et chiffrés | Canal actuel : 2107+ <br /><br> Canal mensuel des entreprises : 2107+ <br /><br> Canal d’entreprise semi-annuel : 2202+ |  16.51+ | 2.58+ | 16.0.14931+  | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Prise en charge du format PDF](#pdf-support)| Canal actuel : 2208+ <br /><br> Canal Entreprise mensuel : 2208+ <br /><br> Semi-Annual Enterprise canal : en cours de révision|  En cours de révision | En cours de révision | En cours de révision | En cours de révision |
|[Barre de sensibilité](#sensitivity-bar) et [couleur d’étiquette d’affichage](#label-colors) | Préversion : déploiement sur le [Canal bêta](https://office.com/insider) | En cours de révision | En cours de révision | En cours de révision | En cours de révision |

### <a name="sensitivity-label-capabilities-in-outlook"></a>Fonctionnalités d’étiquettes de confidentialité dans Outlook

Les nombres répertoriés sont les versions minimales de l’application Office requise pour chaque fonctionnalité. 

> [!NOTE]
> For Windows and the Semi-Annual Enterprise Channel, the minimum supported version numbers might not yet be released. [Learn more](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Fonctionnalité |Outlook pour Windows |Outlook pour Mac |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Complément AIP désactivé par défaut](sensitivity-labels-aip.md#how-to-configure-newer-versions-of-office-to-enable-the-aip-add-in)| Préversion : déploiement sur le [Canal bêta](https://office.com/insider) | Non pertinent  | Non pertinent | Non pertinent| Non pertinent |
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Prise en charge multilingue](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+ | 4.7.1+ | 4.0.39+ | Oui |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Ne pas transférer](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Chiffrer uniquement](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Canal d’entreprise semestriel | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Oui |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | Canal actuel : 2101+ <br /><br> Canal Entreprise mensuel : 2101+ <br /><br> Canal d’entreprise semestriel | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Oui                |
|[Audit de l’activité des utilisateurs liée à une étiquette](#auditing-labeling-activities) | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Canal d’entreprise semestriel | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Oui |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | Canal actuel : 2009+ <br /><br> Canal Enterprise mensuel : 2009+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.44+ <sup>\*</sup>                    | En cours de révision           | En cours de révision               | Oui |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2108+ | 16.49+ | En cours de révision           | En cours de révision               | Oui |
|[Paramètres différents pour l’étiquette par défaut et l’étiquette obligatoire](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Oui |
|[Prise en charge du format PDF](#pdf-support) | Préversion : déploiement sur le [Canal bêta](https://office.com/insider)|  En cours de révision | En cours de révision | En cours de révision | En cours de révision |
|[Appliquer la protection S/MIME](#configure-a-label-to-apply-smime-protection-in-outlook) | Préversion : déploiement sur le [Canal bêta](https://office.com/insider) | 16.61+ <sup>\*</sup>                   | 4.2226+ | 4.2203+ | En cours de révision |
|[Barre de sensibilité](#sensitivity-bar) et [couleur d’étiquette d’affichage](#label-colors) | En cours de révision |  En cours de révision | En cours de révision | En cours de révision | En cours de révision |

**Notes de bas de page :**

<sup>\*</sup> Nécessite le [nouveau Outlook pour Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)

## <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Client d’étiquetage intégré à Office et client Azure Information Protection

Si le [client Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) est installé sur les ordinateurs Windows des utilisateurs, les étiquettes intégrées sont la nouvelle valeur par défaut pour les dernières applications Windows Office qui [prennent en charge l’étiquetage](#labeling-client-for-desktop-apps). Étant donné que les étiquettes intégrées n’utilisent pas de complément Office, telles qu’elles sont utilisées par le client AIP, elles bénéficient d’une stabilité accrue et de meilleures performances. Ils prennent également en charge les fonctionnalités les plus récentes, telles que les classifieurs avancés.

> [!NOTE]
> Si vous ne voyez pas les fonctionnalités d’étiquetage attendues sur les ordinateurs Windows, même si vous confirmez les versions minimales prises en charge pour votre canal de mise à jour Office, cela peut être dû au fait que vous devez [désactiver le complément AIP](sensitivity-labels-aip.md#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps) pour les versions antérieures d’Office.

Pour en savoir plus sur la prise en charge de l’étiquetage avec le client AIP et sur la façon de désactiver ce client uniquement dans les applications Office, consultez [Migrer le complément Azure Information Protection (AIP) vers l’étiquetage intégré pour les applications Office](sensitivity-labels-aip.md).

## <a name="if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows"></a>Si vous devez désactiver l’étiquetage intégré dans Office applications sur Windows

Le client d’étiquetage intégré à Office télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir du Centre de conformité Microsoft 365.

Pour utiliser le client d’étiquetage intégré Office, vous devez disposer d’une ou de plusieurs [stratégies d’étiquette publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) aux utilisateurs à partir du Centre de conformité, et d’une [version prise en charge d’Office](#support-for-sensitivity-label-capabilities-in-apps).

Si ces deux conditions sont remplies, mais que vous devez désactiver les étiquettes intégrées dans les applications Windows Office, utilisez le paramètre stratégie de groupe suivant :

1. Accédez à **Configuration de l'utilisateur/Stratégies/Modèles d'administration/Microsoft Office 2016/Paramètres de sécurité**.

2. Définissez **Utiliser la fonctionnalité de niveau de confidentialité d’Office pour appliquer et afficher les étiquettes de niveau de confidentialité** à **0**.

Si vous devez rétablir cette configuration ultérieurement, remplacez la valeur par **1**. Vous devrez peut-être également remplacer cette valeur par 1 si le bouton **Sensibilité** n’est pas affiché sur le ruban comme prévu. Par exemple, un administrateur précédent a désactivé ce paramètre d’étiquetage.
 
Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service). Le paramètre prend effet au redémarrage de ces applications Office. 

Étant donné que ce paramètre est spécifique aux applications Windows Office, il n’a aucun impact sur les autres applications sur Windows qui prennent en charge les étiquettes de confidentialité (telles que Power BI) ou d’autres plateformes (telles que macOS, les appareils mobiles et Office pour le web). Si vous ne souhaitez pas que certains ou tous les utilisateurs voient et utilisent des étiquettes de confidentialité sur toutes les applications, toutes les plateformes, n’affectent pas de stratégie d’étiquette de confidentialité à ces utilisateurs.

## <a name="office-file-types-supported"></a>Types de fichiers Office pris en charge

En règle générale, les applications Office qui disposent d’un étiquetage intégré pour les fichiers Word, Excel et PowerPoint prennent en charge le format Open XML (par exemple, .docx et .xlsx), mais pas le format Microsoft Office 97-2003 (par exemple, .doc et .xls), le format Open Document (tel que .odt et .ods) ou d’autres formats. Lorsqu’un type de fichier n’est pas pris en charge pour l'étiquetage intégré, le bouton **Niveau de confidentialité** n’est pas disponible dans l’application Office.

Pour connaître les types de fichiers spécifiques pris en charge pour SharePoint et OneDrive lorsque ces services sont activés pour les étiquettes de confidentialité, voir [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md#supported-file-types).

Le client d’étiquetage unifié Azure Information Protection prend en charge les formats Open XML et Microsoft Office 97-2003. Pour plus d’informations, consultez [Types de fichiers pris en charge par le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) à partir du guide d’administration de ce client.

Pour les autres solutions d'étiquetage, consultez leur documentation pour connaître les types de fichiers pris en charge.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de niveau de confidentialité

Les [modèles de protection](/azure/information-protection/configure-policy-templates) définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez un étiquetage intégré. Cette expérience simplifiée illustre le fait qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus avec les étiquettes de niveau de confidentialité dont le chiffrement est activé.

Vous pouvez convertir un modèle existant en étiquette de confidentialité lorsque vous utilisez la cmdlet [New-Label](/powershell/module/exchange/new-label) avec le paramètre *EncryptionTemplateId*.

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Options de gestion des droits relatifs à l'information (IRM) et étiquettes de niveau de confidentialité

Les étiquettes de niveau de confidentialité que vous configurez pour appliquer le chiffrement suppriment la complexité des utilisateurs afin de spécifier leurs propres paramètres de chiffrement. Dans de nombreuses applications Office, ces paramètres de chiffrement individuels peuvent toujours être configurés manuellement par les utilisateurs à l’aide des options de gestion des droits relatifs à l'information (IRM). Par exemple, pour les applications Windows :

- Pour un document : **Fichier** > **Informations** > **Protéger le document** > **Restreindre l’accès**
- pour un courrier électronique : Sous l’onglet **Options** > **Chiffrer** 
  
Lorsque les utilisateurs étiquetent initialement un document ou un e-mail, ils peuvent remplacer vos paramètres de configuration d’étiquette par leurs propres paramètres de chiffrement. Par exemple :

- Un utilisateur applique l’étiquette **Confidentiel \ Tous les employés** à un document. Cette étiquette est configurée pour appliquer des paramètres de chiffrement à tous les utilisateurs de l’organisation. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès à un utilisateur extérieur à votre organisation. Le résultat final est un document étiqueté **Confidentiel \ Tous les employés** et chiffré, mais les utilisateurs de votre organisation ne peuvent pas l’ouvrir comme prévu.

- Un utilisateur applique l’étiquette **Confidentiel \ Destinataires uniquement** à un message électronique. Ce message est configuré pour appliquer le paramètre de chiffrement de **Ne pas transférer**. Dans l’application Outlook, cet utilisateur sélectionne ensuite manuellement le paramètre IRM pour Chiffrer uniquement. Le résultat final est que même si le courrier électronique reste chiffré, il peut être transmis par les destinataires, même s’il porte l’étiquette **Confidentiel \ Destinataires uniquement**.
    
    À titre d’exception, pour Outlook sur le web, les options du menu **Chiffrer** ne sont pas disponibles pour qu’un utilisateur puisse les sélectionner lorsque l’étiquette actuellement sélectionnée applique le chiffrement.

- Un utilisateur applique l’étiquette **Général** à un document, et cette étiquette n’est pas configurée pour appliquer le chiffrement. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès au document. Le résultat final est un document étiqueté **Général**, mais qui applique également le chiffrement de sorte que certains utilisateurs ne peuvent pas l’ouvrir comme prévu.

Si le document ou l'e-mail est déjà étiqueté, un utilisateur peut effectuer l'une de ces actions si le contenu n'est pas déjà chiffré ou s'il dispose du [droit d'utilisation](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Exporter ou Contrôle total. 

For a more consistent label experience with meaningful reporting, provide appropriate labels and guidance for users to apply only labels to protect documents and emails. For example:

- Pour les cas d’exception, les utilisateurs doivent attribuer leurs propres autorisations, fournir des étiquettes qui [permettent aux utilisateurs d’attribuer leurs propres autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- Instead of users manually removing encryption after selecting a label that applies encryption, provide a sublabel alternative when users need a label with the same classification, but no encryption. Such as:
    - **Confidentiel \ Tous les employés**
    - **Confidentiel \ Tout le monde (aucun chiffrement)**

- Désactivez les paramètres IRM pour empêcher les utilisateurs de les sélectionner :
    - Outlook pour Windows : 
        - Clés `DWORD:00000001` de Registre *DisableDNF* et *DisableEO* à partir de `HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM`
        - S’assurer que le paramètre de stratégie **Configurer l’option de chiffrement par défaut pour le bouton Chiffrer** n’est pas configuré
    - Outlook pour Mac : 
        - Clés des paramètres de sécurité *DisableEncryptOnly* et *DisableDoNotForward* documentées dans [Définir les préférences pour Outlook pour Mac](/DeployOffice/mac/preferences-outlook)
    - Outlook sur le web : 
        - Paramètres *SimplifiedClientAccessDoNotForwardDisabled* et *SimplifiedClientAccessEncryptOnlyDisabled* documentés pour [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration)
    - Outlook pour iOS et Android : ces applications ne prennent pas en charge l'application de chiffrement sans étiquette par les utilisateurs, donc rien à désactiver.

> [!NOTE]
> Si les utilisateurs suppriment manuellement le chiffrement d’un document étiqueté stocké dans SharePoint ou OneDrive et que vous avez [activé les étiquettes de niveau de confidentialité des fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), le chiffrement d’étiquettes est restauré automatiquement au prochain accès ou téléchargement du document. 

## <a name="encryption-based-label-matching-for-documents"></a>Correspondance d’étiquette basée sur le chiffrement pour les documents

Lorsqu’un document a été chiffré avec des autorisations définies par l’administrateur, la stratégie de chiffrement est incorporée dans le document. Cela se produit indépendamment de l’étiquetage. Par exemple, lorsqu’une pièce jointe Office hérite du chiffrement d’un e-mail ou qu’un utilisateur a appliqué un modèle de protection à l’aide de la gestion des droits relatifs à l’information (IRM) dans son application Office. Si une étiquette de confidentialité dans le locataire correspond à cette même stratégie de chiffrement, les applications Office attribuent automatiquement cette étiquette correspondante au document.

Dans ce scénario, l’étiquette de confidentialité correspondante peut étiqueter un document sans étiquette et remplacer une étiquette existante qui n’applique pas de chiffrement. Par exemple, l’étiquette **Général** est remplacée par **Confidentiel/ Tous les employés**. Les marquages de contenu de l’étiquette correspondante ne sont pas appliqués automatiquement, sauf si le document n’a pas été étiqueté précédemment et que vous utilisez le complément AIP.

Ce scénario permet de déplacer les anciennes solutions de chiffrement des modèles de protection vers les étiquettes de confidentialité qui appliquent le chiffrement.

Toutefois, vous verrez également ce comportement avec un scénario d’étiquetage pour les pièces jointes des e-mails lorsqu’elles sont ouvertes par le destinataire. Par exemple :

1. Un utilisateur crée un e-mail et joint un document Office non chiffré, puis applique une étiquette à l’e-mail.
    
    L’étiquette applique le chiffrement avec des autorisations définies par l’administrateur, plutôt que les options Ne pas transférer ou Encrypt-Only. Par exemple, pour la configuration de l’étiquette, l’administrateur sélectionne **Attribuer des autorisations maintenant** et spécifie que tous les employés disposent d’un accès en lecture.

2. Lorsque l’e-mail est envoyé, la [pièce jointe hérite automatiquement du chiffrement, mais pas de l’étiquette](encryption-sensitivity-labels.md#email-attachments-for-encrypted-email-messages).

3. Lorsqu’un destinataire du même locataire ouvre le document chiffré, une étiquette correspondante pour les autorisations définies par l’administrateur s’affiche automatiquement pour le document et persiste si le document est enregistré.
    
    En tant qu’événement d’audit affiché dans l’Explorateur d’activités, cet utilisateur a appliqué l’étiquette, et non l’expéditeur de l’e-mail.

La correspondance d’étiquette basée sur le chiffrement fonctionne uniquement au sein du locataire, pour les autorisations définies par l’administrateur, et l’étiquette de confidentialité correspondante doit être publiée à l’utilisateur qui ouvre le document. L’étiquette correspondante est conservée si le document est enregistré.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de confidentialité

**Avec des applications RMS** : si vous ouvrez un document ou un courrier électronique chiffrés et étiquetés dans une [application RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de niveau de confidentialité, l’application applique toujours le chiffrement et la gestion des droits.

**Avec le client Azure Information Protection** : vous pouvez afficher et modifier les étiquettes de niveau de confidentialité que vous appliquez aux documents et courriers électroniques à l’aide du client d’étiquetage intégré à Office à l’aide du client Azure Information Protection, et inversement.

**Avec les autres versions d’Office** : tous les utilisateurs autorisés peuvent ouvrir des documents étiquetés et des messages électroniques dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions d’Office pris en charge ou à l’aide du client Azure Information Protection. Les versions des logiciels Office pris en charge sont répertoriées dans la [section précédente](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par des étiquettes de niveau de confidentialité

Pour utiliser le client d’étiquetage intégré à Office avec Office sur le web pour les documents dans SharePoint ou OneDrive, assurez-vous que vous avez [activé étiquettes de niveau de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="support-for-external-users-and-labeled-content"></a>Prise en charge des utilisateurs externes et du contenu étiqueté

Lorsque vous étiquetez un document ou un message électronique, l’étiquette est stockée en tant que métadonnées incluant votre client et un GUID d’étiquette. Lorsqu’un document ou un courrier électronique étiquetés est ouvert par une application Office qui prend en charge les étiquettes de niveau de confidentialité, ces métadonnées sont lues et uniquement si l’utilisateur appartient au même client, l’étiquette s’affiche dans son application. Par exemple, pour les étiquettes intégrées pour Word, PowerPoint et Excel, le nom de l’étiquette s’affiche dans la barre d’état. 

Cela signifie que si vous partagez des documents avec une autre organisation qui utilise des noms d’étiquettes différents, chaque organisation peut appliquer et voir sa propre étiquette appliquée au document. Toutefois, les éléments suivants d’une étiquette appliquée sont visibles par les utilisateurs extérieurs à votre organisation :

- Content markings. When a label applies a header, footer, or watermark, these are added directly to the content and remain visible until somebody modifies or deletes them.

- Nom et description du modèle de protection sous-jacente à partir d’une étiquette qui applique le chiffrement. Ces informations s’affichent dans une barre des messages en haut du document, pour fournir des informations sur les personnes autorisées à ouvrir le document et leurs droits d’utilisation pour ce document.

### <a name="sharing-encrypted-documents-with-external-users"></a>Partage de documents chiffrés avec des utilisateurs externes

Bien que vous puissiez restreindre l’accès aux utilisateurs de votre propre organisation, vous pouvez également étendre l’accès à tout autre utilisateur disposant d’un compte dans Azure Active Directory (Azure AD). Par défaut, ces utilisateurs externes sont authentifiés sans configuration supplémentaire. Toutefois, une configuration supplémentaire peut être requise pour [les paramètres d’accès interlocataire des identités externes](/azure/active-directory/external-identities/cross-tenant-access-overview) Azure AD et [l’accès conditionnel](/azure/active-directory/conditional-access/overview). 

Si les utilisateurs externes n’ont pas de compte dans Azure AD, ils peuvent s’authentifier à l’aide de comptes invités dans votre locataire. Ces comptes invités peuvent également être utilisés pour accéder à des documents partagés dans SharePoint ou OneDrive lorsque vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Pour plus d’informations sur les fonctionnalités Azure AD facultatives et sur l’utilisation de comptes invités pour les exigences d’authentification, consultez [Configuration Azure AD pour le contenu de chiffrement](encryption-azure-ad-configuration.md).

Toutes les applications Office et autres [applications RMS](/azure/information-protection/requirements-applications#rms-enlightened-applications) peuvent ouvrir des documents chiffrés une fois que l’utilisateur s’est authentifié correctement. 

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

- Microsoft Defender for Cloud Apps

Dans ces scénarios, à l’aide de leurs applications Office, un utilisateur avec une étiquette intégrée peut appliquer les marquages de contenu de l’étiquette en supprimant ou en remplaçant temporairement l’étiquette actuelle, puis en rappliquant l’étiquette d’origine.

### <a name="dynamic-markings-with-variables"></a>Marquages dynamiques avec des variables

> [!IMPORTANT]
> Pour les applications qui ne prennent pas en charge cette fonctionnalité, elles appliquent les marquages comme le texte original spécifié dans la configuration de l'étiquette, plutôt que de résoudre les variables.
> 
> The Azure Information Protection unified labeling client supports dynamic markings. For labeling built in to Office, see the tables in the [capabilities](#support-for-sensitivity-label-capabilities-in-apps) section on this page for minimum versions supported.

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
> The [Azure Information Protection unified labeling client](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) supports this configuration that's also known as mandatory labeling. For labeling built in to Office apps, see the tables in the [capabilities](#support-for-sensitivity-label-capabilities-in-apps) section on this page for minimum versions.
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

- Quand l’étiquetage obligatoire est en vigueur, l’option Imprimer dans un PDF n’est pas disponible lorsqu’un document est étiqueté ou chiffré. Pour plus d’informations, consultez la section [Prise en charge PDF](#pdf-support) sur cette page.

Pour obtenir des instructions sur l’utilisation de ce paramètre, consultez les informations sur [paramètres de stratégie](sensitivity-labels.md#what-label-policies-can-do).

> [!NOTE]
> Si vous utilisez le paramètre de stratégie d’étiquette par défaut pour les documents et messages électroniques en plus de l’étiquette obligatoire : 
>
> L’étiquette par défaut a toujours la priorité sur l’étiquette obligatoire. Toutefois, pour les documents, le client d’étiquetage unifié Azure Information Protection applique l’étiquette par défaut à tous les documents sans étiquettes, tandis que l’étiquette intégrée applique l’étiquette par défaut aux nouveaux documents et non aux documents existants sans étiquettes. Cette différence de comportement signifie que lorsque vous utilisez l’étiquetage obligatoire avec le paramètre d’étiquette par défaut, les utilisateurs sont probablement invités à appliquer une étiquette de confidentialité plus souvent lorsqu’ils utilisent l’étiquetage intégré que lorsqu’ils utilisent le client d’étiquetage unifié Azure Information Protection.
> 
> Déploiement en cours : applications Office qui utilisent l’étiquetage intégré et prennent en charge une étiquette par défaut pour les documents existants. Pour plus d’informations, consultez le [tableau des fonctionnalités](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) pour Word, Excel et PowerPoint.

## <a name="outlook-specific-options-for-default-label-and-mandatory-labeling"></a>Options spécifiques à Outlook pour l’étiquetage par défaut et l’étiquetage obligatoire

For built-in labeling, identify the minimum versions of Outlook that support these features by using the [capabilities table for Outlook](#sensitivity-label-capabilities-in-outlook) on this page, and the row **Different settings for default label and mandatory labeling**. All versions of the Azure Information Protection unified labeling client support these Outlook-specific options.

Lorsque l’application Outlook prend en charge un paramètre d’étiquette par défaut différent du paramètre d’étiquette par défaut des documents :

- Dans la configuration de la stratégie d’étiquette à partir du Centre de conformité Microsoft 365, dans la page **Appliquer une étiquette par défaut aux e-mails** : vous pouvez spécifier votre choix d’étiquette de confidentialité qui sera appliquée à tous les e-mails sans étiquette, ou aucune étiquette par défaut. Ce paramètre est indépendant du paramètre **Appliquer cette étiquette par défaut aux documents** dans la page de configuration précédente des **Paramètres de stratégie pour les documents**.

Lorsque l’application Outlook ne prend pas en charge un paramètre d’étiquette par défaut différent du paramètre d’étiquette par défaut pour les documents : Outlook utilise toujours la valeur que vous spécifiez pour **Appliquer cette étiquette par défaut aux documents** dans la page de configuration de stratégie des **Paramètres de stratégie pour les documents**.

Lorsque l’application Outlook prend en charge la désactivation de l’étiquetage obligatoire :

- Dans la configuration de la stratégie d’étiquette à partir du Centre de conformité Microsoft 365, dans la page **Paramètres de stratégie** : sélectionnez **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails ou documents**. Sélectionnez ensuite **Suivant** > **Suivant**, puis décochez la case **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails**. Laissez la case cochée si vous souhaitez que l’étiquetage obligatoire s’applique aux e-mails et aux documents.

Lorsque l’application Outlook ne prend pas en charge la désactivation de l’étiquetage obligatoire : si vous sélectionnez **Demander aux utilisateurs d’appliquer une étiquette à leurs e-mails ou documents** en tant que paramètre de stratégie, Outlook invite toujours les utilisateurs à sélectionner une étiquette pour les e-mails sans étiquette.

> [!NOTE]
> Si vous avez configuré les paramètres avancés PowerShell **OutlookDefaultLabel** et **DisableMandatoryInOutlook** à l’aide des cmdlets [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy) ou [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) :
> 
> Les valeurs que vous avez choisies pour ces paramètres PowerShell sont reflétées dans la configuration de la stratégie d’étiquette dans le portail de conformité Microsoft Purview, et elles fonctionnent automatiquement pour les applications Outlook qui prennent en charge ces paramètres. Les autres paramètres avancés de PowerShell restent pris en charge pour le client d’étiquetage unifié Azure Information Protection uniquement.

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Configurer une étiquette pour appliquer la protection S/MIME dans Outlook

> [!NOTE]
> Cette fonctionnalité est actuellement en cours de déploiement pour l’étiquetage intégré et à différentes phases de mise en production sur les plateformes. Identifiez les versions minimales d’Outlook qui prennent en charge cette fonctionnalité à l’aide du [tableau des fonctionnalités d’Outlook](#sensitivity-label-capabilities-in-outlook) sur cette page et de la ligne **Appliquer la protection S/MIME**.
> 
> Si vous configurez une étiquette pour appliquer la protection S/MIME, mais qu’Outlook sur Windows ne la prend pas encore en charge, l’étiquette est toujours affichée et peut être appliquée, mais les paramètres S/MIME sont ignorés. Vous ne pourrez pas sélectionner cette étiquette pour les stratégies d’étiquetage automatique Exchange.

Cette configuration n’est pas disponible dans le portail de conformité Microsoft Purview. Vous devez utiliser les paramètres avancés PowerShell avec la cmd [Set-Label](/powershell/module/exchange/set-label) ou [New-Label](/powershell/module/exchange/new-label) après vous être [connecté à Office 365 Centre de sécurité et de conformité PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

Utilisez ces paramètres uniquement lorsque vous disposez d’un [déploiement S/MIME](/microsoft-365/security/office-365-security/s-mime-for-message-signing-and-encryption) opérationnel et que vous souhaitez qu’une étiquette applique automatiquement cette méthode de protection pour les e-mails plutôt [que la protection par défaut qui utilise Rights Management chiffrement à partir de Azure Information Protection](encryption-sensitivity-labels.md). La protection obtenue est la même que lorsqu’un utilisateur sélectionne manuellement les options S/MIME dans Outlook.

|Configuration  |Clé/valeur de paramètre avancée |
|---------|---------|
|**Signature numérique S/MIME** | SMimeSign="True" |
|**Chiffrement S/MIME** | SMimeEncrypt="True"|

L’étiquette que vous configurez pour ces paramètres n’a pas besoin d’être configurée pour le chiffrement dans le portail de conformité. Mais si c’est le cas, la protection S/MIME remplace le chiffrement Rights Management uniquement dans Outlook. Pour les autres applications, l’étiquette applique les paramètres de chiffrement spécifiés dans le portail de conformité Microsoft Purview.

Exemples de commandes PowerShell, où le GUID de l’étiquette de confidentialité est **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

```PowerShell
Set-Label -Identity "8faca7b8-8d20-48a3-8ea2-0f96310a848e" -AdvancedSettings @{SMimeSign="True"}

Set-Label -Identity "8faca7b8-8d20-48a3-8ea2-0f96310a848e" -AdvancedSettings @{SMimeEncrypt="True"}
```

Pour plus d’informations sur la spécification des paramètres avancés de PowerShell, consultez [Conseils PowerShell pour la spécification des paramètres avancés](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="pdf-support"></a>Prise en charge du format PDF

Pour l’étiquetage intégré, utilisez les tables de la section [Fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page pour identifier les versions minimales prises en charge. Le client d’étiquetage unifié Azure Information Protection ne prend pas en charge les PDF dans les applications Office.

Word, Excel et PowerPoint prennent en charge les méthodes suivantes pour convertir un document Office en document PDF :

- Fichier > Enregistrer sous > PDF 
- Fichier > Exporter > PDF
- Partager > Envoyer une copie > PDF

Cette action est enregistrée avec l’événement d’audit de **fichier renommé** à partir du groupe d’audit [Des activités](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities) de fichier et de page. Dans les résultats de la recherche d’audit dans le portail de conformité, vous verrez les détails de cet événement d’audit afficher **SensitivityLabeledFileRenamed** pour le champ **Activité** .

Lorsque le fichier PDF est créé, il hérite de l’étiquette avec les marquages de contenu et le chiffrement. Les fichiers PDF chiffrés peuvent être ouverts avec Microsoft Edge sur Windows ou Mac. Pour obtenir plus d’informations et connaître des lecteurs alternatifs, consultez [Quels lecteurs PDF sont pris en charge pour les PDF protégés ?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)

Outlook ne prend actuellement pas en charge les pièces jointes PDF qui héritent du chiffrement d’un message étiqueté. Toutefois, Outlook prend désormais en charge l’avertissement ou le blocage des utilisateurs de l’impression au format PDF, comme décrit ci-après.

Scénarios PDF non pris en charge :

- Imprimer au format PDF
    
    Si les utilisateurs sélectionnent cette option, ils sont avertis que le document ou l’adresse e-mail perdra la protection de l’étiquette et le chiffrement (s’il est appliqué) et doivent confirmer s’ils veulent continuer. Si votre stratégie d’étiquette de confidentialité requiert une justification pour supprimer une étiquette ou réduire sa classification, cette invite s’affiche.
    
    Étant donné que cette option supprime l’étiquette de confidentialité, cette option ne sera pas disponible pour les utilisateurs si vous utilisez l’étiquetage obligatoire. Cette configuration fait référence au paramètre de stratégie d’étiquette de confidentialité qui oblige les utilisateurs à appliquer une étiquette à leurs e-mails et documents.

- Format PDF/A et chiffrement
    
     Ce format PDF conçu pour l’archivage à long terme n’est pas pris en charge lorsque l’étiquette applique le chiffrement et empêche les utilisateurs de convertir des documents Office au format PDF. Pour plus d’informations sur la configuration, consultez la documentation stratégie de groupe relative à [l’application de la conformité PDF à la norme ISO 19005-1 (PDF/A).](https://admx.help/?Category=Office2016&Policy=office16.Office.Microsoft.Policies.Windows::L_EnforcePDFcompliancewithISO190051PDFA)
    
- Protection par mot de passe et chiffrement
    
    L’option **Fichier** > **Info** > **Protéger le document** > **Chiffrer avec mot de passe** n’est pas prise en charge lorsque l’étiquette du document applique un chiffrement. Dans ce scénario, l’option Chiffrer avec mot de passe devient indisponible pour les utilisateurs.

Pour plus d’informations sur cette fonctionnalité, consultez l’annonce [Appliquer des étiquettes de confidentialité aux fichiers PDF créés avec les applications Office](https://insider.office.com/blog/apply-sensitivity-labels-to-pdfs-created-with-office-apps).

Pour obtenir la documentation de l’utilisateur final, voir [Créer des fichiers PDF protégés à partir de fichiers Office](https://support.microsoft.com/topic/aba7e367-e482-49e7-b746-a385e48d01e4).

## <a name="sensitivity-bar"></a>Barre de sensibilité

Récemment pris en charge en préversion pour les étiquettes intégrées dans Word, Excel et PowerPoint, mais pas encore pour Outlook ou Office sur le Web, consultez les tableaux de la section [fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page pour identifier les versions minimales.

Pour les applications prises en charge, les étiquettes de confidentialité sont désormais affichées dans une barre de confidentialité, en regard du nom de fichier dans la barre de fenêtre supérieure. Par exemple :

![Étiquettes de confidentialité dans la barre de titre de la fenêtre.](../media/sensitivity-bar-example.png)

Les informations sur les étiquettes et la possibilité de sélectionner ou de modifier une étiquette sont également intégrées aux flux de travail utilisateur, notamment l’enregistrement et le changement de nom, l’exportation, le partage, l’impression et [la conversion au format PDF](#pdf-support). Pour plus d’informations et des exemples de captures d’écran, consultez l’annonce du billet de blog, [Nouvelle barre de confidentialité dans Office pour Windows](https://insider.office.com/blog/sensitivity-bar-in-office-for-windows).

Dans le cadre de cette visibilité élevée, ces étiquettes prennent également en charge les couleurs. Pour plus d’informations, consultez la section suivante.

### <a name="label-colors"></a>Couleurs des étiquettes

> [!IMPORTANT]
> Si vos applications d’étiquetage ne prennent pas en charge cette fonctionnalité, elles n’affichent pas les couleurs d’étiquette configurées.
> 
> Le client d’étiquetage unifié Azure Information Protection prend en charge les couleurs des étiquettes. Pour l’étiquetage intégré à Office, les couleurs des étiquettes sont actuellement prises en charge en préversion pour Word, Excel et PowerPoint sur Windows, mais pas encore pour Outlook, macOS ou Office sur le Web. Pour plus d’informations, consultez les tableaux de la section [fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page.

Les étiquettes nouvellement créées n’ont pas de couleur par défaut. Si vos étiquettes ont été [migrées à partir d’Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels) ou si vous avez configuré des couleurs d’étiquette pour le client d’étiquetage unifié Azure Information Protection, ces couleurs d’étiquette sont désormais affichées dans les applications qui les prennent en charge.

Utilisez la portail de conformité Microsoft Purview pour sélectionner l’une des 10 couleurs standard pour les étiquettes de confidentialité. La configuration **de la couleur de** l’étiquette se trouve sur la première page de la configuration de l’étiquette après le nom et la description de l’étiquette.

Vous ne pouvez pas sélectionner de couleurs pour les sous-étiquettes, car elles héritent automatiquement de la couleur d’étiquette de leur étiquette parente.

Si une étiquette est configurée pour une couleur différente de l’une des 10 couleurs par défaut, une case **Utiliser une couleur personnalisée précédemment affectée** est cochée et les options de couleur standard ne sont pas disponibles. Vous pouvez remplacer la couleur personnalisée par l’une des couleurs standard en décochant d’abord la case, puis en sélectionnant l’une des couleurs standard. 

Vous ne pouvez pas utiliser le portail de conformité pour configurer une autre couleur personnalisée. Utilisez plutôt PowerShell, comme décrit dans la section suivante.

#### <a name="configuring-custom-colors-by-using-powershell"></a>Configuration de couleurs personnalisées à l’aide de PowerShell 

Vous pouvez utiliser la **couleur** avancée du paramètre [Sécurité & Conformité PowerShell](/powershell/exchange/scc-powershell) pour définir une couleur pour une étiquette de confidentialité. Cette configuration prend en charge les couleurs que vous ne pouvez pas configurer dans le portail de conformité Microsoft Purview.

Pour spécifier votre choix de couleur, utilisez un code triplet hexadécimal pour les composants RVB (rouge, vert et bleu) de la couleur. Par exemple, #40e0d0 est la valeur hexadécimale RVB pour la couleur turquoise.

Pour plus d’informations sur ces codes, consultez la [\<color>](https://developer.mozilla.org/docs/Web/CSS/color_value) page de la documentation web MSDN. Vous pouvez également trouver [RapidTables](https://www.rapidtables.com/web/color/RGB_Color.html) utile. Vous pouvez identifier ces codes dans de nombreuses applications qui vous permettent de modifier des images. Par exemple, Microsoft Paint vous permet de choisir une couleur personnalisée dans une palette et les valeurs RVB s’affichent automatiquement. Vous pouvez ensuite les copier.

Exemple de commande PowerShell, où le GUID de l’étiquette de confidentialité est **8faca7b8-8d20-48a3-8ea2-0f96310a848e**

```PowerShell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{color="#40e0d0"}
```

Pour plus d’informations pour vous aider à spécifier les paramètres avancés PowerShell pour les étiquettes de confidentialité, consultez [Conseils PowerShell pour spécifier les paramètres avancés](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

## <a name="auditing-labeling-activities"></a>Audit des activités d’étiquetage

Pour plus d’informations sur les événements d’audit générés par les activités des étiquettes de sensibilité, consultez la section d’[activités des étiquettes de confidentialité](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) dans le [journal d’audit du Centre de conformité](search-the-audit-log-in-security-and-compliance.md).

Ces informations d’audit sont visuellement représentées dans l’[ explorateur de contenu](data-classification-content-explorer.md) et l’[explorateur d’activités](data-classification-activity-explorer.md) pour vous aider à comprendre comment vos étiquettes de niveau de confidentialité sont utilisées et où se trouve ce contenu étiqueté. 

You can also create custom reports with your choice of security information and event management (SIEM) software when you [export and configure the audit log records](export-view-audit-log-records.md). For larger-scale reporting solutions, see the [Office 365 Management Activity API reference](/office/office-365-management-api/office-365-management-activity-api-reference).

> [!TIP]
> Pour créer des rapports personnalisés, consultez les billets de blog suivants :
> - [Journaux d’audit de conformité Microsoft 365 via l’API de gestion O365 : Partie 1](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957171)
> - [Journaux d’audit de conformité Microsoft 365 via l’API de gestion O365 : Partie 2](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-365-compliance-audit-log-activities-via-o365/ba-p/2957297) 

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Créer des fichiers PDF protégés à partir de fichiers Office](https://support.microsoft.com/topic/aba7e367-e482-49e7-b746-a385e48d01e4)
