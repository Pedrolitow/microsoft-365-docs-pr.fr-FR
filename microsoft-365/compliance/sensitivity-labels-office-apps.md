---
title: Utiliser les étiquettes de confidentialité dans les applications Office
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment les utilisateurs utilisent les étiquettes de confidentialité dans les applications Office pour le bureau, les applications Office pour mobile et les applications Office pour le Web. Découvrez les applications qui prennent en charge les étiquettes de sensibilité.
ms.openlocfilehash: 87e4425658044d29c9306cdf57c13941c2d62785
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43635792"
---
# <a name="use-sensitivity-labels-in-office-apps"></a>Utiliser les étiquettes de confidentialité dans les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Lorsque vous avez [publié](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) des étiquettes de confidentialité à partir du centre de conformité Microsoft 365 ou d’un centre d’étiquetage équivalent, ils commencent à apparaître dans les applications Office pour permettre aux utilisateurs de classer et de protéger les données lors de leur création ou modification.

Utilisez les informations contenues dans cet article pour vous aider à gérer correctement les étiquettes de confidentialité dans les applications Office. Par exemple, identifiez les versions minimales des applications dont vous avez besoin pour prendre en charge l’étiquetage intégré et comprenez les interactions avec le client d’étiquetage unifié Azure information protection et la compatibilité avec d’autres applications et services.

## <a name="labeling-client-for-desktop-apps"></a>Étiquetage du client pour les applications de bureau

Pour utiliser les étiquettes de confidentialité qui sont intégrées aux applications de bureau Office pour Windows et Mac, vous devez utiliser une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, comme Office 2016 ou Office 2019.

Pour utiliser les étiquettes de confidentialité avec ces éditions autonomes d’Office sur des ordinateurs Windows, installez le [client d’étiquetage unifié Azure information protection](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2).

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de sensibilité dans les applications

Pour chaque fonctionnalité, les tableaux suivants répertorient la version minimale dont vous avez besoin pour cette application afin de prendre en charge les étiquettes de sensibilité à l’aide d’étiquettes intégrées. Ou, si la fonctionnalité étiquette est en préversion publique ou en révision pour une version ultérieure.

De nouvelles versions des applications sont disponibles à différents moments pour différents canaux de mise à jour. Pour plus d’informations, notamment sur la configuration de votre canal de mise à jour afin de pouvoir tester une nouvelle fonctionnalité d’étiquetage qui vous intéresse, consultez la rubrique [vue d’ensemble des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Les nouvelles fonctionnalités de la préversion privée ne sont pas incluses dans le tableau, mais vous pouvez participer à ces aperçus en décrivant votre organisation pour le [programme d’évaluation privée de la protection des informations Microsoft](https://aka.ms/mip-preview).

Des fonctionnalités supplémentaires sont disponibles lorsque vous installez le client d’étiquetage unifié Azure information protection, qui s’exécute sur des ordinateurs Windows uniquement. Pour plus d’informations, reportez-vous à [la rubrique comparer les clients d’étiquetage pour les ordinateurs Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités d’étiquette de sensibilité dans Word, Excel et PowerPoint

Pour iOS et Android : lorsqu’une version minimale est indiquée, la fonctionnalité d’étiquette de sensibilité est également prise en charge avec l' [application Office](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/).

|Fonctionnalité                                                                                                        |Bureau Windows |Bureau Mac |iOS    |Android      |Web                                                         |
|------------------------------------------------------------------------------------------------------------------|----------------|------------|-------|-------------|------------------------------------------------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | En cours de révision                                                        |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Déploiement sur le [canal mensuel](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus#monthly-channel-for-office-365-proplus) (2003 +) | Déploiement sur le [canal mensuel](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus#monthly-channel-for-office-365-proplus) (16.35 +)   | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Afficher l’utilisation des étiquettes avec l’analyse d’étiquette et l'](label-analytics.md) envoi de données pour les administrateurs                      | En cours de révision            | En cours de révision        | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Demander aux utilisateurs d’appliquer une étiquette à leurs courriers électroniques et documents](sensitivity-labels.md#what-label-policies-can-do)   | En cours de révision            | En cours de révision        | En cours de révision   | En cours de révision         | En cours de révision                                                        |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)                    | Aperçu : dans [Office Insider](https://office.com/insider)                                  | En cours de révision | En cours de révision | En cours de révision | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|Prise en charge de l' [enregistrement automatique](https://support.office.com/article/6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) et de la [co-création](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) sur des documents étiquetés et protégés | En cours de révision | En cours de révision | En cours de révision | En cours de révision | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|

### <a name="sensitivity-label-capabilities-in-outlook"></a>Fonctionnalités d’étiquette de confidentialité dans Outlook

|Fonctionnalité                                                                                                        |Outlook sur le bureau Windows |Outlook sur le bureau Mac  |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|------------------------------------------------------------------------------------------------------------------|---------------------------|------------------------|---------------|-------------------|-------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Fournir un lien aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-label-policies-can-do)                                              | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | 1910+                     | 16.21 +                 | 4.7.1 +         | 4.0.39 +           | Oui               |
|[Afficher l’utilisation des étiquettes avec l’analyse d’étiquette et l'](label-analytics.md) envoi de données pour les administrateurs                      | En cours de révision                       | En cours de révision                    | En cours de révision           | En cours de révision               | En cours de révision               |
|[Demander aux utilisateurs d’appliquer une étiquette à leurs courriers électroniques et documents](sensitivity-labels.md#what-label-policies-can-do)   | En cours de révision                       | En cours de révision                    | En cours de révision           | En cours de révision               | En cours de révision               |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)                    | Aperçu : déploiement vers [Office Insider](https://office.com/insider)                       | En cours de révision                    | En cours de révision           | En cours de révision               | Oui |
|

## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Client d’étiquetage Office intégré et autres solutions d’étiquetage

Le client d’étiquetage Office intégré télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir des centres d’administration suivants :

- Centre de conformité Microsoft 365
- Centre de sécurité Microsoft 365
- Centre de sécurité et conformité Office 365

Pour utiliser le client d’étiquetage Office intégré, une ou plusieurs stratégies d’étiquette doivent être [publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) pour les utilisateurs à partir d’un des centres d’administration et d’une [version prise en charge d’Office](#support-for-sensitivity-label-capabilities-in-apps).

Si ces deux conditions sont remplies, mais que vous devez désactiver le client d’étiquetage Office intégré, utilisez le paramètre de stratégie de groupe suivant :

1. Accédez à **Configuration utilisateur/modèles d’administration/Microsoft Office 2016/paramètres de sécurité**

2. Set **Utilisez la fonctionnalité de sensibilité dans Office pour appliquer et afficher les étiquettes de confidentialité** à **0**. 
 
Déployer ce paramètre à l’aide de la stratégie de groupe ou à l’aide du [service de stratégie de Cloud Office](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service). Le paramètre prend effet lorsque les applications Office redémarrent.

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Client d’étiquetage Office intégré et le client Azure information protection

Si les utilisateurs ont un des clients Azure information protection[installés (ou client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2) [classique](https://docs.microsoft.com/azure/information-protection/rms-client/aip-client)), par défaut, le client d’étiquetage intégré est désactivé dans leurs applications Office. 

Pour utiliser l’étiquetage intégré plutôt que le client Azure information protection pour les applications Office, suivez les instructions de la section précédente, mais définissez le paramètre de stratégie de groupe **Utilisez la fonctionnalité de confidentialité dans Office pour appliquer et afficher les étiquettes de confidentialité** à **1**. 

Vous pouvez également désactiver ou supprimer le complément Office, **Azure information protection**. Cette méthode est adaptée à un seul ordinateur et à un test ad hoc. Pour obtenir des instructions, consultez la rubrique [afficher, gérer et installer des compléments dans les programmes Office](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d). 

Lorsque vous désactivez ou supprimez ce complément Office, le client Azure information protection reste installé de sorte que vous puissiez continuer à étiqueter les fichiers en dehors de vos applications Office. Par exemple, à l’aide de l’Explorateur de fichiers ou de PowerShell.

Pour plus d’informations sur les fonctionnalités prises en charge par les clients Azure information protection et le client d’étiquetage Office intégré, reportez-vous à la rubrique [Choose the Labeling client to use for Windows Computers](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) from the Azure information protection documentation.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de sensibilité

Les modèles de [protection](https://docs.microsoft.com/azure/information-protection/configure-policy-templates)définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez l’étiquetage prédéfini. Cette expérience simplifiée indique qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus avec les étiquettes de sensibilité dont le chiffrement est activé.

Si vous devez convertir des modèles de protection existants en étiquettes, utilisez le portail Azure et les instructions suivantes : [pour convertir des modèles en étiquettes](https://docs.microsoft.com/azure/information-protection/configure-policy-templates#to-convert-templates-to-labels).

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Options de la gestion des droits relatifs à l’information (IRM) et des étiquettes de confidentialité

Les étiquettes de sensibilité que vous configurez pour appliquer le chiffrement suppriment la complexité des utilisateurs pour spécifier leurs propres paramètres de chiffrement. Dans de nombreuses applications Office, ces paramètres de chiffrement individuels peuvent toujours être configurés manuellement par les utilisateurs à l’aide des options de gestion des droits relatifs à l’information (IRM). Par exemple, pour les applications Windows :

- Pour un document : **File** > **informations** > de fichier**protéger le document** > protéger**l’accès restreint**
- pour un e-mail : sous l’onglet **Options** > **chiffrer** 
  
Lorsque les utilisateurs étiquetent initialement un document ou un message électronique, ils peuvent toujours remplacer vos paramètres de configuration d’étiquette par leurs propres paramètres de chiffrement. Par exemple :

- Un utilisateur applique l’étiquette **confidentialité \ tous les employés** à un document et cette étiquette est configurée pour appliquer les paramètres de chiffrement pour tous les utilisateurs de l’organisation. Cet utilisateur configure manuellement les paramètres IRM pour restreindre l’accès à un utilisateur en dehors de votre organisation. Le résultat final est un document étiqueté **confidentiel \ tous les employés** et chiffré, mais les utilisateurs de votre organisation ne peuvent pas l’ouvrir comme prévu.

- Un utilisateur applique l’étiquette **confidentialité \ des destinataires uniquement** à un e-mail et ce courrier électronique est configuré pour appliquer le paramètre de chiffrement **ne pas transférer**. Cet utilisateur configure ensuite manuellement les paramètres IRM de sorte que le courrier électronique ne soit pas restreint. Le résultat final est le transfert du courrier électronique par les destinataires, en dépit de l’étiquette **confidentialité \ des destinataires uniquement** .

- Un utilisateur applique l’étiquette **général** à un document, et cette étiquette n’est pas configurée pour appliquer le chiffrement. Cet utilisateur configure ensuite manuellement les paramètres IRM pour limiter l’accès au document. Le résultat final est un document étiqueté **général** , mais qui applique également le chiffrement afin que certains utilisateurs ne puissent pas l’ouvrir comme prévu.

Si le document ou l’adresse de messagerie est déjà étiqueté, un utilisateur peut effectuer l’une des actions suivantes si le contenu n’est pas déjà chiffré ou s’il dispose de l’exportation [droite](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) ou contrôle total. 

Pour une étiquette plus cohérente avec un rapport significatif, fournissez des étiquettes et des conseils appropriés pour que les utilisateurs ne puissent appliquer que des étiquettes pour protéger des documents. Par exemple :

- Pour les cas d’exception où les utilisateurs doivent affecter leurs propres autorisations, fournissez des étiquettes qui [permettent aux utilisateurs d’affecter leurs propres autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions). 

- Au lieu de supprimer manuellement le chiffrement après avoir sélectionné une étiquette qui applique le chiffrement, fournissez une alternative de sous-étiquette lorsque les utilisateurs ont besoin d’une étiquette avec la même classification, mais pas de chiffrement. Par exemple :
    - **Confidentiel \ tous les employés**
    - **Confidentiel \ tout le monde (pas de chiffrement)**

> [!NOTE]
> Si les utilisateurs suppriment manuellement le chiffrement d’un document étiqueté qui est stocké dans SharePoint ou OneDrive, et que vous avez [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et onedrive](sensitivity-labels-sharepoint-onedrive-files.md), le chiffrement des étiquettes est automatiquement restauré lors de l’accès ou du téléchargement suivant du document. 

## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Appliquer des étiquettes de confidentialité à des fichiers, des e-mails et des pièces jointes

Les utilisateurs peuvent appliquer une seule étiquette à la fois pour chaque document ou courrier électronique.

Lorsque vous étiquetez un message électronique comportant des pièces jointes, les pièces jointes n’héritent pas de l’étiquette, à une exception près :

- La pièce jointe est un document Office avec une étiquette qui n’applique pas le chiffrement et l’étiquette que vous appliquez au message électronique applique le chiffrement. Dans ce cas, le document Office envoyé par e-mail hérite de l’étiquette de l’e-mail avec ses paramètres de chiffrement.

Sinon : 

- Si les pièces jointes possèdent une étiquette, elles conservent leur étiquette d’origine.
- Si les pièces jointes sont chiffrées sans étiquette, le chiffrement reste, mais ils ne sont pas étiquetés.
- Si les pièces jointes n’ont pas d’étiquette, elles ne sont pas étiquetées.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de sensibilité

**Avec des applications avec gestion des**droits relatifs à l’urgence : Si vous ouvrez un document étiqueté et chiffré ou un message électronique dans une application à l’aide de [RMS](https://docs.microsoft.com/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de sensibilité, l’application applique toujours le chiffrement et la gestion des droits.

**Avec le client Azure information protection**: vous pouvez afficher et modifier les étiquettes de confidentialité que vous appliquez aux documents et aux courriers électroniques avec le client d’étiquetage Office intégré à l’aide du client Azure information protection, et inversement.

**Avec d’autres versions d’Office**: tout utilisateur autorisé peut ouvrir des documents étiquetés et des courriers électroniques dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions d’Office prises en charge ou à l’aide du client Azure information protection. Les versions des applications Office prises en charge sont répertoriées dans la [section précédente](#support-for-sensitivity-label-capabilities-in-apps).

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par les étiquettes de confidentialité

Pour utiliser le client d’étiquetage Office intégré avec Office sur le Web pour des documents dans OneDrive entreprise ou SharePoint Online, vérifiez que vous avez opté pour l’aperçu afin d' [activer les étiquettes de sensibilité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="when-office-365-applies-content-marking-and-encryption"></a>Lorsque Office 365 applique le marquage de contenu et le chiffrement

Office 365 applique le marquage de contenu et le chiffrement avec une étiquette de sensibilité différemment, en fonction de l’application que vous utilisez.

| Application | Marquage du contenu | Chiffrement |
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Après l’envoi du courrier électronique par Exchange Online | Immédiatement |
| Outlook sur le web, iOS et Android | Après l’envoi du courrier électronique par Exchange Online | Après l’envoi du courrier électronique par Exchange Online |
|

## <a name="end-user-documentation"></a>Documentation destinée aux utilisateurs finaux

- [Appliquer des étiquettes de niveau de confidentialité à vos documents et vos e-mails dans Office](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)

- [Problèmes connus lorsque vous appliquez des étiquettes de niveau de confidentialité à vos fichiers Office](https://support.office.com/article/known-issues-when-you-apply-sensitivity-labels-to-your-office-files-b169d687-2bbd-4e21-a440-7da1b2743edc)