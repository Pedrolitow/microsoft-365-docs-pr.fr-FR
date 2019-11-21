---
title: Étiquettes de confidentialité dans les applications Office
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 11/20/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment les utilisateurs utilisent les étiquettes de confidentialité dans les applications Office pour le bureau, les applications Office pour mobile et les applications Office pour le Web. Découvrez les applications qui prennent en charge les étiquettes de sensibilité.
ms.openlocfilehash: 1b472185df2d45717cba6cfca30176768bf9cd4e
ms.sourcegitcommit: 5f96fa472cbdca30c2cfe24d66c9c6fcaedb1a6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38755592"
---
# <a name="sensitivity-labels-in-office-apps"></a>Étiquettes de confidentialité dans les applications Office

Cet article décrit les aspects suivants :

- Configuration requise pour votre environnement avant d’appliquer des étiquettes de confidentialité à des e-mails, des fichiers et des pièces jointes.
- Les fonctionnalités d’étiquette de sensibilité sont prises en charge par chaque application Office.
- Que se passe-t-il lorsque vous combinez les étiquettes de confidentialité avec d’autres technologies de sécurité et de conformité Microsoft qui fonctionnent avec les applications Office.
- La manière dont les personnes de votre organisation peuvent utiliser des étiquettes de confidentialité lorsqu’elles utilisent les applications Office pour Windows et les applications Office pour le Web.
- Où accéder aux personnes de votre organisation qui ont commencé avec des étiquettes de confidentialité.

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Exigences en matière d’abonnement et de gestion des licences pour les étiquettes de sensibilité

Les utilisateurs doivent avoir au moins une des licences suivantes affectées :

- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ou version supérieure

- [Office 365 E3](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e3-business-software) ou version supérieure

- [Azure information protection Premium P1](https://azure.microsoft.com/pricing/details/information-protection/) ou version supérieure

Le client d’étiquetage Office intégré prend en charge les étiquettes de confidentialité avec une version d’abonnement d’Office. Le client ne prend pas en charge les versions autonomes, par exemple, Office 2016 ou Office 2019.

Pour utiliser l’étiquette de sensibilité automatique ou recommandée, vos utilisateurs ont besoin d’une des licences suivantes :

- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) ou version ultérieure

- [Office 365 E5](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software) ou version ultérieure

- [Azure information protection Premium P2](https://azure.microsoft.com/pricing/details/information-protection/) ou version supérieure

## <a name="support-for-sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Prise en charge des fonctionnalités d’étiquette de sensibilité dans Word, Excel et PowerPoint

Pour chaque fonctionnalité, le tableau suivant répertorie la version minimale dont vous avez besoin pour cette application. TBD signifie que vous ne pouvez pas utiliser cette fonctionnalité sur cette plateforme.

|Fonctionnalité                                                                                                        |Bureau Windows |Bureau Mac |iOS    |Android      |Web                                                         |
|------------------------------------------------------------------------------------------------------------------|----------------|------------|-------|-------------|------------------------------------------------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | À déterminer                                                        |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-label-policies-can-do)                                              | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+          | 16.21 +     | 2.21+ | 16.0.11231+ | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | TBD            | TBD        | TBD   | TBD         | TBD                                                        |
|[Afficher l’utilisation des étiquettes avec l’analyse d’étiquette et l'](label-analytics.md) envoi de données pour les administrateurs                      | TBD            | TBD        | TBD   | TBD         | TBD                                                        |
|
  [Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](sensitivity-labels.md#what-label-policies-can-do)   | TBD            | TBD        | TBD   | TBD         | TBD                                                        |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)                    | Aperçu : dans le déploiement vers [Office Insider](https://office.com/insider)                                  | TBD | TBD | TBD | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|Prise en charge de l' [enregistrement automatique](https://support.office.com/article/6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) et de la [co-création](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) sur des documents étiquetés et protégés | TBD | TBD | TBD | TBD | [Aperçu](sensitivity-labels-sharepoint-onedrive-files.md) |
|

## <a name="support-for-sensitivity-label-capabilities-in-outlook"></a>Prise en charge des fonctionnalités d’étiquette de sensibilité dans Outlook

Pour chaque fonctionnalité, le tableau suivant répertorie la version minimale dont vous avez besoin pour cette application. TBD signifie que vous ne pouvez pas utiliser cette fonctionnalité sur cette plateforme.

|Fonctionnalité                                                                                                        |Outlook sur le bureau Windows |Outlook sur le bureau Mac  |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|------------------------------------------------------------------------------------------------------------------|---------------------------|------------------------|---------------|-------------------|-------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-label-policies-can-do)                                              | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | 1910+                     | 16.21 +                 | 4.71 +         | 4.0.39 +           | Oui               |
|[Afficher l’utilisation des étiquettes avec l’analyse d’étiquette et l'](label-analytics.md) envoi de données pour les administrateurs                      | TBD                       | TBD                    | TBD           | TBD               | TBD               |
|
  [Demander aux utilisateurs d'appliquer une étiquette à leurs e-mails et documents](sensitivity-labels.md#what-label-policies-can-do)   | TBD                       | TBD                    | TBD           | TBD               | TBD               |
|[Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md)                    | TBD                       | TBD                    | TBD           | TBD               | Aperçu : dans le déploiement vers la [version ciblée](https://docs.microsoft.com/office365/admin/manage/release-options-in-office-365?view=o365-worldwide) |
|

## <a name="about-the-office-built-in-labeling-client"></a>À propos du client d’étiquetage Office intégré

Le client d’étiquetage Office intégré télécharge les étiquettes et les paramètres de stratégie à partir des centres d’administration suivants :

- Centre de sécurité et conformité Office 365

- Centre de sécurité Microsoft 365

- Centre de conformité Microsoft 365

Le client d’étiquetage Office intégré est automatiquement activé pour les utilisateurs auxquels une ou plusieurs stratégies d' [étiquette sont publiées](sensitivity-labels.md#what-label-policies-can-do) .

Pour utiliser le client d’étiquetage intégré dans Office sous Windows, vous ne pouvez pas exécuter simultanément le complément Azure information protection dans Office. Vous pouvez désinstaller temporairement ou définitivement le client Azure information protection, ou vous pouvez le laisser installé et configurer Office pour l’empêcher de s’exécuter.

1. Effectuez l’une des options suivantes :

    **Pour plusieurs ordinateurs :** Configurez le paramètre **utiliser la fonctionnalité de confidentialité dans Office pour appliquer et afficher les étiquettes de confidentialité** . Recherchez ce paramètre sous **Configuration utilisateur/modèles d’administration/Microsoft Office 2016/paramètres de sécurité**. Déployez ce paramètre par le biais d’une stratégie de groupe ou à l’aide du [service de stratégie de Cloud Office](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service).

    **Pour un ordinateur unique :** Voir « afficher, gérer et installer des compléments dans les programmes Office », et [désactiver ou supprimer définitivement](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d) le complément Azure information protection sur un seul ordinateur.

2. Redémarrez toutes les applications Office.

Pour plus d’informations sur les applications clientes pour la protection des informations, consultez [le côté client d’Azure information protection](https://docs.microsoft.com/azure/information-protection/rms-client/use-client).

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de sensibilité

Les modèles de [protection](https://docs.microsoft.com/azure/information-protection/configure-policy-templates)définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement des messages Office 365, sont masqués dans l’expérience utilisateur Office lorsque les étiquettes de confidentialité sont activées, car elles sont redondantes avec des étiquettes de sensibilité dont le chiffrement est activé.

## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Appliquer des étiquettes de confidentialité à des fichiers, des e-mails et des pièces jointes

Les utilisateurs peuvent appliquer une seule étiquette à la fois pour chaque document ou courrier électronique.

Lorsque vous étiquetez un message électronique comportant des pièces jointes, les pièces jointes n’héritent pas de l’étiquette. Si les pièces jointes ont une étiquette, elles conservent cette étiquette appliquée séparément. Si les pièces jointes n’ont pas d’étiquette, les pièces jointes restent sans étiquette. Toutefois, si l’étiquette de l’e-mail applique la protection, cette protection est appliquée aux pièces jointes Office.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de sensibilité

**Avec des applications RMS**. Si vous ouvrez un document étiqueté _et chiffré_ ou un message électronique dans une [application RMS](https://docs.microsoft.com/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de sensibilité, l’application applique toujours le chiffrement et la gestion des droits.

**Avec le client Azure information protection**. Vous pouvez afficher et modifier les étiquettes de confidentialité que vous appliquez aux documents et aux courriers électroniques avec le client d’étiquetage Office intégré avec le client Azure information protection, et inversement.

**Avec d’autres versions d’Office**. Tout utilisateur autorisé peut ouvrir des documents étiquetés et des courriers électroniques dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions Office prises en charge ou dans le client Azure information protection. Les versions des applications Office prises en charge sont répertoriées dans les tableaux de cet article.

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par les étiquettes de confidentialité

Pour utiliser le client d’étiquetage Office intégré dans Office sur le Web, le document doit se trouver dans une instance OneDrive entreprise ou SharePoint Online qui a opté pour les [étiquettes activer la sensibilité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="when-office-365-applies-marks-and-encryption-to-content"></a>Lorsque Office 365 applique des marques et chiffrement au contenu

Office 365 applique les marques de contenu ou le chiffrement avec une étiquette de sensibilité différemment en fonction de l’application que vous utilisez.

| Application | Marquage du contenu | Chiffrement |
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Après l’envoi du courrier électronique par Exchange Online | Immédiatement |
| Outlook sur le web, iOS et Android | Après l’envoi du courrier électronique par Exchange Online | Après l’envoi du courrier électronique par Exchange Online |
|

## <a name="more-resources"></a>Autres ressources

[Forum aux questions sur la classification et l’étiquetage dans Azure Information Protection](https://docs.microsoft.com/azure/information-protection/faqs-infoprotect)

[Appliquer des étiquettes de niveau de confidentialité à vos documents et vos e-mails dans Office](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
