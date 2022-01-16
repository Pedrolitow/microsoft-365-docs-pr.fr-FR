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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Informations pour que les administrateurs informatiques gèrent les étiquettes de niveau de confidentialité dans les applications Office pour le bureau, les appareils mobiles et le web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d13c587c86874354e05422b2ff105d923e234c61
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2022
ms.locfileid: "62054883"
---
# <a name="manage-sensitivity-labels-in-office-apps"></a>Gérer les étiquettes de confidentialité dans les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous avez [publié](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) des étiquettes de niveau de confidentialité du Centre de conformité ou du Centre d’étiquettes équivalent Microsoft 365, elles commencent à apparaître dans les applications Office pour que les utilisateurs classifient et protègent les données dès qu’elles sont créées ou modifiées.

Les informations de cet article vous aideront à gérer les étiquettes de niveau de confidentialité dans les applications Office. Par exemple, identifiez les versions minimales d’applications dont vous avez besoin pour prendre en charge l’étiquette intégrée, et comprenez les interactions avec le client d’étiquetage unifiée Azure Information Protection, ainsi que la compatibilité avec d’autres applications et services.

## <a name="labeling-client-for-desktop-apps"></a>Client d’étiquetage pour les applications de bureau

Pour utiliser des étiquettes de niveau de confidentialité intégrées aux applications de bureau Office pour Windows et Mac, vous devez utiliser une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, telles qu’Office 2016 ou Office 2019.

Pour utiliser des étiquettes de niveau de confidentialité avec ces éditions autonomes d’Office sur les ordinateurs Windows, installez le [client étiquetage Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de confidentialité dans les applications

Pour chaque fonctionnalité, les tableaux suivants listent la version minimale d’Office dont vous avez besoin pour prendre en charge les étiquettes de niveau de confidentialité à l’aide d’étiquettes intégrées. Ou, si la fonctionnalité d’étiquette est en prévisualisation ou en cours de révision pour une prochaine version. Utilisez la [Microsoft 365 feuille de route pour](https://aka.ms/MIPC/Roadmap) plus d’informations sur les nouvelles fonctionnalités prévues pour les prochaines publication.

Les nouvelles versions des applications Office sont disponibles à différents moments pour différents canaux de mise à jour. Pour Windows, vous obtenez les nouvelles fonctionnalités plus tôt lorsque vous êtes sur le canal actuel ou le canal Enterprise mensuel, plutôt que sur Semi-Annual Enterprise canal. Les numéros de version minimum peuvent également être différents d’un canal de mise à jour à l’autre. Pour plus d’informations, voir [Vue d’ensemble des](/deployoffice/overview-update-channels) canaux de mise à jour Microsoft 365 Apps et historique des mises à jour [pour Microsoft 365 Apps](/officeupdates/update-history-microsoft365-apps-by-date).

Les nouvelles fonctionnalités en préversion privée ne sont pas incluses dans le tableau, mais il est possible que vous soyez en mesure de participer à ces préversions en nomant votre organisation pour le [programme de préversion privé Microsoft Information Protection](https://aka.ms/mip-preview).

Office pour iOS et Office pour Android : les étiquettes de niveau de confidentialité sont intégrées dans l’[application Office](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

Des fonctionnalités supplémentaires sont disponibles lorsque vous installez le client de l’étiquetage unifié d’Azure Information Protection, qui s’exécute uniquement sur les ordinateurs Windows. Pour plus d’informations, consultez [Comparer les clients d’étiquetage pour les ordinateurs Windows](/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

> [!TIP]
> Lorsque vous comparez les versions minimales des tables aux versions dont vous disposez, n’oubliez pas la pratique courante des versions de mise en production pour omettre les zéros non significatifs.
> 
> Par exemple, vous avez la version 4.2128.0 et lisez que 4.7.1+ est la version minimale. Pour faciliter la comparaison, lisez 4.7.1 (sans zéros non significatifs) en tant que 4.**0007**.1 (et non 4.**7000**.1). Votre version de 4.2128.0 est supérieure à 4.0007.1. Votre version est donc prise en charge.

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités d’étiquettes de confidentialité dans Word, Excel et PowerPoint

Les nombres répertoriés sont les versions minimales de l’application Office requise pour chaque fonctionnalité. 

> [!NOTE]
> Pour Windows et le canal d’entreprise semi-annuel, il se peut que les numéros de version minimum pris en charge ne soient pas encore publiés. [En savoir plus](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)
 
|Fonctionnalité |Windows |Mac |iOS |Android |Web |
|-----------|-------:|----|----|--------|----|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do) aux nouveaux documents                                         | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do) à des documents existants | Préversion : [Canal bêta](https://office.com/insider) | Préversion : [Canal bêta](https://office.com/insider) | En cours de révision | En cours de révision | Déploiement : [Oui, participer](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+  <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | Canal actuel : 2010+ <br /><br> Canal mensuel des entreprises : 2010+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.42+     | 2.42+ | 16.0.13328+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+     | 2.21+ | 16.0.11231+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Inviter les utilisateurs](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |Canal actuel : 2004+ <br /><br> Canal Entreprise mensuel : 2004+ <br /><br> Semi-Annual Enterprise canal : 2008+ | 16.35+   | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Audit de l’activité des utilisateurs liée à une étiquette](data-classification-activity-explorer.md)                      | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Canal d’entreprise semestriel | 16.43+ | 2.46+ | 16.0.13628+ | Oui <sup>\*</sup>                                                        |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | Canal actuel : 2101+ <br /><br> Canal Entreprise mensuel : 2101+ <br /><br> Canal d’entreprise semestriel | 16.45+         | 2.47+ | 16.0.13628+ | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md)                                            
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | Canal actuel : 2009+ <br /><br> Canal Enterprise mensuel : 2009+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.44+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2018+ | En cours de révision | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Prise en charge de la co-édition et de l'enregistrement automatique](sensitivity-labels-coauthoring.md) pour les documents étiquetés et chiffrés | Canal actuel : 2107+ <br /><br> Canal mensuel des entreprises : 2107+ <br /><br> Canal d’entreprise semi-annuel : 2202+ |  16.51+ | En cours de révision | En cours de révision | [Oui : s’inclure](sensitivity-labels-sharepoint-onedrive-files.md) |
|

**Notes de bas de page :**

<sup>\*</sup> N’inclut pas de texte de justification pour supprimer une étiquette ou abaisser le niveau de classification pour le moment

### <a name="sensitivity-label-capabilities-in-outlook"></a>Fonctionnalités d’étiquettes de confidentialité dans Outlook

Les nombres répertoriés sont les versions minimales de l’application Office requise pour chaque fonctionnalité. 

> [!NOTE]
> Pour Windows et le canal d’entreprise semi-annuel, il se peut que les numéros de version minimum pris en charge ne soient pas encore publiés. [En savoir plus](/officeupdates/update-history-microsoft365-apps-by-date#supported-versions)

|Fonctionnalité |Outlook pour Windows |Outlook pour Mac |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|-----------|-------------------:|----------------|---------------|-------------------|-------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Demander une justification pour la modification d'étiquette.](sensitivity-labels.md#what-label-policies-can-do)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquages dynamiques avec des variables](#dynamic-markings-with-variables).                                              | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Ne pas transférer](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Canal actuel : 1910+ <br /><br> Canal Entreprise mensuel : 1910+ <br /><br> Semi-Annual Enterprise canal : 2002+ | 16.21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations : <br /> – Chiffrer uniquement](encryption-sensitivity-labels.md#let-users-assign-permissions)  | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Canal d’entreprise semestriel | 16.48+ <sup>\*</sup> | 4.2112.0+  | 4.2112.0+ | Oui |
|[Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | Canal actuel : 2101+ <br /><br> Canal Entreprise mensuel : 2101+ <br /><br> Canal d’entreprise semestriel | 16.43+ <sup>\*</sup>                    | 4.2111+            | 4.2111+                | Oui                |
|[Audit de l’activité des utilisateurs liée à une étiquette](data-classification-activity-explorer.md) | Canal actuel : 2011+ <br /><br> Canal Entreprise mensuel : 2011+ <br /><br> Semi-Annual Enterprise canal : en cours de révision | 16.51+ <sup>\*</sup> | 4.2126+ | 4.2126+ | Oui |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de types d’informations sensibles                    | Canal actuel : 2009+ <br /><br> Canal Enterprise mensuel : 2009+ <br /><br> Semi-Annual Enterprise canal : 2102+ | 16.44+ <sup>\*</sup>                    | En cours de révision           | En cours de révision               | Oui |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md) <br /> - Utilisation de classifieurs pouvant être formés                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2108+ | En cours de révision                    | En cours de révision           | En cours de révision               | Oui |
|[Paramètres différents pour l’étiquette par défaut et l’étiquette obligatoire](#outlook-specific-options-for-default-label-and-mandatory-labeling)                    | Canal actuel : 2105+ <br /><br> Canal Entreprise mensuel : 2105+ <br /><br> Canal d’entreprise semestriel : 2108+ | 16.43+ <sup>\*</sup>                   | 4.2111+           | 4.2111+               | Oui |
|

**Notes de bas de page :**

<sup>\*</sup> Nécessite le [nouveau Outlook pour Mac](https://support.microsoft.com/office/the-new-outlook-for-mac-6283be54-e74d-434e-babb-b70cefc77439)


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Client d’étiquetage intégré à Office et autres solutions d’étiquetage

Le client d’étiquetage intégré à Office télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir du Centre de conformité Microsoft 365. 

Pour utiliser le client d’étiquetage intégré Office, vous devez disposer d’une ou de plusieurs [stratégies d’étiquette publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) aux utilisateurs à partir du Centre de conformité, et d’une [version prise en charge d’Office](#support-for-sensitivity-label-capabilities-in-apps).

Si ces deux conditions sont remplies, mais que vous devez désactiver les étiquettes intégrées dans les applications Office, utilisez le paramètre stratégie de groupe suivant :

1. Accédez à **Configuration de l'utilisateur/Stratégies/Modèles d'administration/Microsoft Office 2016/Paramètres de sécurité**.

2. Définissez **Utiliser la fonctionnalité de niveau de confidentialité d’Office pour appliquer et afficher les étiquettes de niveau de confidentialité** à **0**. 
 
Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service). Le paramètre prend effet lorsque les applications Office redémarrent.

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Client d’étiquetage intégré à Office et client Azure Information Protection

Si les utilisateurs ont installé le client [Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2) sur leurs ordinateurs Windows, par défaut, les étiquettes intégrées sont désactivées dans les [applications Office qui les prennent en charge](#labeling-client-for-desktop-apps). Étant donné que les étiquettes intégrées n’utilisent pas de complément Office, telles qu’elles sont utilisées par le client Azure Information Protection, elles bénéficient d’une stabilité accrue et de meilleures performances. Ils prennent également en charge les fonctionnalités les plus récentes, telles que les classifieurs avancés.

Au lieu de désinstaller le client Azure Information Protection, nous vous recommandons d’empêcher le chargement du complément Azure Information Protection dans les applications Office. Ensuite, vous bénéficiez des avantages de l’étiquetage intégré dans les applications Office et des avantages du Azure Information Protection fichiers d’étiquetage client en dehors des applications Office. Par exemple, le client Azure Information Protection peut étiqueter tous les types de fichiers à l’aide de Explorateur de fichiers et PowerShell. Pour plus d’informations sur les fonctionnalités d’étiquetage prises en charge en dehors des applications Office, consultez [Étiquettes de confidentialité et Azure Information Protection](sensitivity-labels.md#sensitivity-labels-and-azure-information-protection).

Pour empêcher le chargement du complément client Azure Information Protection dans les applications Office, utilisez le paramètre stratégie de groupe **Liste des compléments gérés** comme indiqué dans [Aucun complément chargé en raison des paramètres de stratégie de groupe pour les programmes Office 2013 et Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

Pour vos applications Office qui prennent en charge l’étiquetage intégré, utilisez la configuration pour Microsoft Word 2016, Excel 2016, PowerPoint 2016 et Outlook 2016, spécifiez les identificateurs de programmation suivants (ProgID) pour le client Azure Information Protection et définissez l’option sur **0 : le complément est toujours désactivé (bloqué)**

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Si vous utilisez le paramètre stratégie de groupe **Utilisez la fonctionnalité De confidentialité dans Office pour appliquer et afficher les étiquettes de confidentialité** et définir cette valeur sur **1**, il existe certaines situations où le client Azure Information Protection peut toujours se charger dans les applications Office. Le fait de bloquer le chargement du complément dans chaque application empêche ce problème.

Vous pouvez également désactiver ou supprimer de manière interactive le complément Office **Microsoft Azure Information Protection** de Word, Excel, PowerPoint et Outlook. Cette méthode est appropriée pour un ordinateur unique et des tests ad-hoc. Pour obtenir de instructions, consultez [Afficher, gérer et installer des compléments dans les programmes Office (pour les utilisateurs)](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d). 

Quelle que soit la méthode choisie, les modifications prennent effet au redémarrage des applications Office.

Pour plus d’informations sur les fonctionnalités prises en charge par le client Azure Information Protection et le client d’étiquetage intégré Office, consultez [Choisir votre solution d’étiquetage Windows](/azure/information-protection/rms-client/use-client#choose-your-windows-labeling-solution) à partir de la documentation Azure Information Protection.

## <a name="office-file-types-supported"></a>Types de fichiers Office pris en charge

Les applications Office qui ont un étiquetage intégré pour les fichiers Word, Excel et PowerPoint prennent en charge le format Open XML (tel que .docx et .xlsx), mais pas le format Microsoft Office 97-2003 (tel que .doc et .xls), le format Open Document (par exemple, .odt et .ods) ou d’autres formats. Lorsqu’un type de fichier n’est pas pris en charge pour l’étiquetage intégré, le bouton **Sensibilité** n’est pas disponible dans l’application Office.

Le client d’étiquetage unifié Azure Information Protection prend en charge les formats Open XML et Microsoft Office 97-2003. Pour plus d’informations, consultez [Types de fichiers pris en charge par le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types) à partir du guide d’administration de ce client.

Pour les autres solutions d'étiquetage, consultez leur documentation pour connaître les types de fichiers pris en charge.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de niveau de confidentialité

Les [modèles de protection](/azure/information-protection/configure-policy-templates) définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez un étiquetage intégré. Cette expérience simplifiée illustre le fait qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus avec les étiquettes de niveau de confidentialité dont le chiffrement est activé.

Vous pouvez convertir un modèle existant en étiquette de confidentialité lorsque vous utilisez la cmdlet [New-Label](/powershell/module/exchange/new-label) avec le paramètre *EncryptionTemplateId*.

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

- Une autre option consiste à utiliser [Intégration de SharePoint et OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration) afin que les comptes invités soient automatiquement créés lorsque vos utilisateurs partagent des liens.
    
    Cette option offre un coût d’administration minimal, car les comptes sont créés automatiquement et une configuration d’étiquette plus simple. Dans ce scénario, vous devez sélectionner l’option de chiffrement [Ajouter des utilisateur authentifiés](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users), car vous ne connaissez pas les adresses de messagerie à l’avance. Ce paramètre ne vous permet pas de restreindre l’accès et les droits d’utilisation à des utilisateurs spécifiques.

Les utilisateurs externes peuvent également utiliser un compte Microsoft pour ouvrir des documents chiffrés lorsqu’ils utilisent les applications Windows et Microsoft 365 ([anciennement des applications Office 365](/deployoffice/name-change)) ou la version autonome d’Office 2019. Plus récemment pris en charge pour les autres plateformes, les comptes Microsoft sont également pris en charge pour l’ouverture de documents chiffrés sur macOS (Microsoft 365 Apps, version 16.42+), Android (version 16.0.13029+) et iOS (version 2.42+). Par exemple, un utilisateur de votre organisation partage un document chiffré avec un utilisateur extérieur à votre organisation, et les paramètres de chiffrement spécifient une adresse de messagerie Gmail pour l’utilisateur externe. Cet utilisateur externe peut créer son propre compte Microsoft qui utilise son adresse de messagerie Gmail. Ensuite, une fois qu’ils se sont ouverts avec ce compte, ils peuvent ouvrir le document et le modifier, conformément aux restrictions d’utilisation qui leur sont spécifiées. Pour consulter un exemple pas à pas de ce scénario, consultez[Ouverture et modification du document protégé](/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document).

> [!NOTE]
> L’adresse de messagerie du compte Microsoft doit correspondre à l’adresse de messagerie spécifiée pour restreindre l’accès aux paramètres de chiffrement.

Lorsqu’un utilisateur avec un compte Microsoft ouvre un document chiffré de cette façon, il crée automatiquement un compte invité pour le client si un compte invité du même nom n’existe pas encore. Lorsque le compte invité existe, il peut ensuite être utilisé pour ouvrir des documents dans SharePoint et OneDrive à l’aide d’Office sur le web, en plus d’ouvrir des documents chiffrés à partir des applications Office de bureau et mobiles pris en charge.

Toutefois, le compte invité automatique n’est pas créé immédiatement dans ce scénario, en raison d’une latence de réplication. Si vous spécifiez des adresses de messagerie personnelles dans le cadre de vos paramètres de chiffrement d’étiquettes, nous vous recommandons de créer des comptes invités correspondants dans Azure Active Directory. Indiquez ensuite à ces utilisateurs qu’ils doivent utiliser ce compte pour ouvrir un document chiffré de votre organisation.

> [!TIP]
> Étant donné que vous ne savez pas si les utilisateurs externes utiliseront une application cliente Office prise en charge, le partage de liens à partir de SharePoint et OneDrive après avoir créé des comptes invités (pour des utilisateurs spécifiques) ou lorsque vous utilisez [l’intégration de SharePoint et OneDrive à Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) (pour tout utilisateur authentifié) est une méthode plus fiable pour prendre en charge la collaboration sécurisée avec les utilisateurs externes.

### <a name="conditional-access-policies"></a>Stratégies d’accès conditionnel

Si votre organisation a implémenté [Azure Active Directory stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview), vérifiez la configuration de ces stratégies. Si les stratégies incluent **Microsoft Azure Information Protection** et que la stratégie s’étend aux utilisateurs externes, ces utilisateurs externes doivent avoir un compte invité dans votre locataire, même s’ils ont un compte Azure AD dans leur propre locataire.

Sans ce compte invité, ils ne peuvent pas ouvrir le document chiffré et voir un message d’erreur. Le texte du message peut les informer que leur compte doit être ajouté en tant qu’utilisateur externe dans le locataire, avec les instructions incorrectes pour ce scénario pour **Se déconnecter et se reconnecter avec un autre compte d’utilisateur Azure Active Directory**.

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

- Microsoft Defender for Cloud Apps

Dans ces scénarios, à l’aide de leurs applications Office, un utilisateur avec une étiquette intégrée peut appliquer les marquages de contenu de l’étiquette en supprimant ou en remplaçant temporairement l’étiquette actuelle, puis en rappliquant l’étiquette d’origine.

### <a name="dynamic-markings-with-variables"></a>Marquages dynamiques avec des variables

> [!IMPORTANT]
> Actuellement, toutes les applications, sur toutes les plateformes, ne prennent pas en charge les marquages de contenu dynamiques que vous pouvez spécifier pour vos en-têtes, pieds de page et filigranes. Pour les applications qui ne prennent pas en charge cette fonctionnalité, elles appliquent les marquages comme le texte original spécifié dans la configuration de l'étiquette, plutôt que de résoudre les variables.
> 
> Le client d’étiquetage unifié Azure Information Protection prend en charge les marquages dynamiques. Pour l’étiquetage intégré à Office, consultez les tableaux de la section [Fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page pour connaître les versions minimales prises en charge.

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

Exemples :

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
> Le [Client de l’étiquetage unifié d’Azure Information Protection](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) prend en charge cette configuration également appelée étiquetage obligatoire. Pour l’étiquetage intégré aux applications Office, consultez les tableaux de la section [Fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page pour connaître les versions minimales.
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
> L’étiquette par défaut a toujours la priorité sur l’étiquette obligatoire. Toutefois, pour les documents, le client d’étiquetage unifié Azure Information Protection applique l’étiquette par défaut à tous les documents sans étiquettes, tandis que l’étiquette intégrée applique l’étiquette par défaut aux nouveaux documents et non aux documents existants sans étiquettes. Cette différence de comportement signifie que lorsque vous utilisez l’étiquetage obligatoire avec le paramètre d’étiquette par défaut, les utilisateurs sont probablement invités à appliquer une étiquette de confidentialité plus souvent lorsqu’ils utilisent l’étiquetage intégré que lorsqu’ils utilisent le client d’étiquetage unifié Azure Information Protection.
> 
> Déploiement en cours : applications Office qui utilisent l’étiquetage intégré et prennent en charge une étiquette par défaut pour les documents existants. Pour plus d’informations, consultez le [tableau des fonctionnalités](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) pour Word, Excel et PowerPoint.

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

- [Appliquer des étiquettes de confidentialité à vos fichiers et vos e-mails dans Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Problèmes connus liés aux étiquettes de confidentialité dans Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Appliquer ou recommander automatiquement des étiquettes de confidentialité pour vos fichiers et e-mails dans Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Problèmes connus liés à l’application ou à la recommandation automatique des étiquettes de confidentialité](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)
