---
title: Étiquettes de confidentialité dans les applications Office
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
ms.openlocfilehash: 4b81968c6f60377195afb2715a2a6aabdb9dea51
ms.sourcegitcommit: 2436c983402157ed3d09682d78792783313a64f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2020
ms.locfileid: "41787504"
---
# <a name="sensitivity-labels-in-office-apps"></a>Étiquettes de confidentialité dans les applications Office

Cet article décrit les aspects suivants :

- Configuration requise pour votre environnement avant d’appliquer des étiquettes de confidentialité à des e-mails, des fichiers et des pièces jointes.
- Les fonctionnalités d’étiquette de sensibilité sont prises en charge par chaque application Office.
- Que se passe-t-il lorsque vous combinez les étiquettes de confidentialité avec d’autres technologies de sécurité et de conformité Microsoft qui fonctionnent avec les applications Office.
- La manière dont les personnes de votre organisation peuvent utiliser des étiquettes de confidentialité lorsqu’elles utilisent les applications Office pour Windows et les applications Office pour le Web.
- Ressources supplémentaires pour aider les personnes de votre organisation à commencer à utiliser des étiquettes de confidentialité.

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Exigences en matière d’abonnement et de gestion des licences pour les étiquettes de sensibilité

Les utilisateurs doivent avoir au moins une des licences suivantes affectées :

- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ou version supérieure

- [Office 365 E3](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e3-business-software) ou version supérieure

- [Azure information protection Premium P1](https://azure.microsoft.com/pricing/details/information-protection/) ou version supérieure

Le client d’étiquetage Office intégré prend en charge les étiquettes de confidentialité avec une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, comme Office 2016 ou Office 2019. Pour utiliser les étiquettes de confidentialité avec ces éditions d’Office sur des ordinateurs Windows, installez le client d’étiquetage unifié Azure information protection.

Pour utiliser l’étiquette de sensibilité automatique ou recommandée, vos utilisateurs ont besoin d’une des licences suivantes :

- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ou version ultérieure

- [Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software) ou version ultérieure

- [Azure Information Protection Premium P2](https://azure.microsoft.com/pricing/details/information-protection/)

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de sensibilité dans les applications

Pour chaque fonctionnalité, les tableaux suivants répertorient la version minimale dont vous avez besoin pour cette application afin de prendre en charge les étiquettes de sensibilité à l’aide d’étiquettes intégrées. Ou, si la fonctionnalité étiquette est en préversion publique ou en révision pour une version ultérieure.

De nouvelles versions des applications sont disponibles à différents moments pour différents canaux de mise à jour. Pour plus d’informations, notamment sur la configuration de votre canal de mise à jour afin de pouvoir tester une nouvelle fonctionnalité d’étiquetage qui vous intéresse, consultez la rubrique [vue d’ensemble des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Les nouvelles fonctionnalités de la préversion privée ne sont pas incluses dans le tableau, mais vous pouvez participer à ces aperçus en décrivant votre organisation pour le [programme d’évaluation privée de la protection des informations Microsoft](https://aka.ms/mip-preview).

Des fonctionnalités supplémentaires sont disponibles lorsque vous installez le client d’étiquetage unifié Azure information protection, qui s’exécute sur des ordinateurs Windows uniquement. Pour plus d’informations, reportez-vous à [la rubrique comparer les clients d’étiquetage pour les ordinateurs Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers).

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités d’étiquette de sensibilité dans Word, Excel et PowerPoint

|Fonctionnalité                                                                                                        |Bureau Windows |Bureau Mac |iOS    |Android      |Web                                                         |
|------------------------------------------------------------------------------------------------------------------|----------------|------------|-------|-------------|------------------------------------------------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | En cours de révision                                                        |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | Aperçu : dans le déploiement vers [Office Insider](https://office.com/insider)            | Aperçu : dans le déploiement vers [Office Insider](https://office.com/insider)        | En cours de révision   | En cours de révision         | En cours de révision                                                        |
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
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)                    | En cours de révision                       | En cours de révision                    | En cours de révision           | En cours de révision               | Aperçu : dans le déploiement vers la [version ciblée](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide) |
|

## <a name="about-the-office-built-in-labeling-client"></a>À propos du client d’étiquetage Office intégré

Le client d’étiquetage Office intégré télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir des centres d’administration suivants :

- Centre de conformité Microsoft 365
- Centre de sécurité Microsoft 365
- Centre de sécurité et conformité Office 365

Pour utiliser le client d’étiquetage Office intégré, une ou plusieurs stratégies d’étiquette doivent être [publiées](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) pour les utilisateurs à partir de l’un des centres d’administration affichés.

Toutefois, si les utilisateurs ont installé l’un des clients Azure information protection[(ou client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2) [classique](https://docs.microsoft.com/azure/information-protection/rms-client/aip-client)), par défaut, le client d’étiquetage intégré est désactivé dans leurs applications Office. Pour utiliser l’étiquetage intégré plutôt que le client Azure information protection pour les applications Office, désactivez ou désinstallez le complément Office pour Azure information protection :

1. Effectuez l’une des options suivantes :
    
    - **Pour plusieurs ordinateurs :** Configurez le paramètre **utiliser la fonctionnalité de confidentialité dans Office pour appliquer et afficher les étiquettes de confidentialité** . Recherchez ce paramètre sous **Configuration utilisateur/modèles d’administration/Microsoft Office 2016/paramètres de sécurité**. Déployez ce paramètre par le biais d’une stratégie de groupe ou à l’aide du [service de stratégie de Cloud Office](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service).
    
    - **Pour un ordinateur unique :** Voir « afficher, gérer et installer des compléments dans les programmes Office » pour plus d’informations sur la façon de [désactiver ou de supprimer définitivement](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d) le complément Azure information protection sur un seul ordinateur.

2. Redémarrez toutes les applications Office.

Lorsque vous désactivez ou désinstallez ce complément Office, le client Azure information protection reste installé de sorte que vous puissiez continuer à étiqueter les fichiers en dehors de vos applications Office. Par exemple, à l’aide de l’Explorateur de fichiers ou de PowerShell.

Pour plus d’informations sur les fonctionnalités prises en charge par les clients Azure information protection et le client d’étiquetage Office intégré, reportez-vous à la rubrique [Choose the Labeling client to use for Windows Computers](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) from the Azure information protection documentation.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de sensibilité

Les modèles de [protection](https://docs.microsoft.com/azure/information-protection/configure-policy-templates)définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez l’étiquetage prédéfini. Cette expérience simplifiée indique qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus avec les étiquettes de sensibilité dont le chiffrement est activé.

Si vous devez convertir des modèles de protection existants en étiquettes, utilisez le portail Azure et les instructions suivantes : [pour convertir des modèles en étiquettes](https://docs.microsoft.com/azure/information-protection/configure-policy-templates#to-convert-templates-to-labels).

## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Appliquer des étiquettes de confidentialité à des fichiers, des e-mails et des pièces jointes

Les utilisateurs peuvent appliquer une seule étiquette à la fois pour chaque document ou courrier électronique.

Lorsque vous étiquetez un message électronique comportant des pièces jointes, les pièces jointes n’héritent pas de l’étiquette. Si les pièces jointes ont une étiquette, elles conservent cette étiquette appliquée séparément. Si les pièces jointes n’ont pas d’étiquette, les pièces jointes restent sans étiquette. Toutefois, si l’étiquette de l’e-mail applique la protection, cette protection est appliquée aux pièces jointes Office.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de sensibilité

**Avec des applications RMS**. Si vous ouvrez un document étiqueté _et chiffré_ ou un message électronique dans une [application RMS](https://docs.microsoft.com/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de sensibilité, l’application applique toujours le chiffrement et la gestion des droits.

**Avec le client Azure information protection**. Vous pouvez afficher et modifier les étiquettes de confidentialité que vous appliquez aux documents et aux courriers électroniques avec le client d’étiquetage Office intégré avec le client Azure information protection, et inversement.

**Avec d’autres versions d’Office**. Tout utilisateur autorisé peut ouvrir des documents étiquetés et des courriers électroniques dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions Office prises en charge ou dans le client Azure information protection. Les versions des applications Office prises en charge sont répertoriées dans les tableaux de cet article.

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par les étiquettes de confidentialité

Pour utiliser le client d’étiquetage Office intégré dans Office sur le Web, le document doit se trouver dans une instance OneDrive entreprise ou SharePoint Online qui a opté pour les [étiquettes activer la sensibilité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="when-office-365-applies-content-marking-and-encryption-to-content"></a>Lorsque Office 365 applique le marquage de contenu et le chiffrement au contenu

Office 365 applique le marquage de contenu et le chiffrement avec une étiquette de sensibilité différemment, en fonction de l’application que vous utilisez.

| Application | Marquage du contenu | Chiffrement |
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Après l’envoi du courrier électronique par Exchange Online | Immédiatement |
| Outlook sur le web, iOS et Android | Après l’envoi du courrier électronique par Exchange Online | Après l’envoi du courrier électronique par Exchange Online |
|

## <a name="more-resources"></a>Autres ressources

- [Appliquer des étiquettes de niveau de confidentialité à vos documents et vos e-mails dans Office](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)

- [Problèmes connus lorsque vous appliquez des étiquettes de niveau de confidentialité à vos fichiers Office](https://support.office.com/article/known-issues-when-you-apply-sensitivity-labels-to-your-office-files-b169d687-2bbd-4e21-a440-7da1b2743edc)
