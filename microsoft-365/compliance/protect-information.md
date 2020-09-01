---
title: Microsoft information protection dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: High
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Implémentez les fonctionnalités Microsoft information protection (MIP) à l’aide de la conformité Microsoft 365 pour vous aider à découvrir, classer et protéger les informations sensibles partout où elles se trouvent.
ms.openlocfilehash: ac4499fceae1e4f754753cf91beaf106d855c517
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47308345"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>Microsoft information protection dans Microsoft 365

>*[Licences pour la conformité des & de sécurité Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Utilisez Microsoft information protection (MIP) pour vous aider à découvrir, classer et protéger des informations sensibles partout où elles se trouvent.

Les fonctionnalités de MIP sont incluses dans la conformité Microsoft 365 et vous donnent les outils permettant de [déterminer vos données](#know-your-data), de [protéger vos données](#protect-your-data)et de [prévenir les pertes de données](#prevent-data-loss).

![Maîtrisez vos données, Protégez vos données, évitez les pertes de données, régissent vos données](../media/powered-by-intelligent-platform.png)

Pour plus d’informations sur la gestion de vos données, consultez la rubrique [Microsoft information Governance dans microsoft 365](manage-Information-governance.md).

## <a name="know-your-data"></a>Ayez une bonne connaissance de vos données

Pour comprendre votre environnement de données et identifier les données importantes dans votre environnement hybride, utilisez les fonctionnalités suivantes :
 
|Fonctionnalité|Quels problèmes est-il résolu ?|Prise en main|
|:------|:------------|:--------------------|:-----------------------------|
|[Types d’informations sensibles](sensitive-information-type-entity-definitions.md)| Identifie les données sensibles à l’aide d’expressions régulières intégrées ou personnalisées ou d’une fonction, avec une preuve corroborante incluant des mots clés, des niveaux de confiance et une proximité.| [Personnaliser un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md)|
|[Classifieurs de formation (préversion)](classifier-getting-started-with.md)| Classifie les données pour vous, à l’aide de l’un des classifieurs intégrés ou de la formation d’un classifieur avec votre propre contenu | [Créer un classifieur de formation (aperçu)](classifier-creating-a-trainable-classifier.md) |
|[Classification des données](data-classification-overview.md) | Identifie les éléments qui ont une étiquette de sensibilité, une étiquette de rétention ou qui ont été classés comme type d’informations sensibles dans votre organisation et les actions que vos utilisateurs ententent de ceux-ci.  | [Prise en main de l’explorateur de contenu](data-classification-content-explorer.md)<br /><br /> [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Protégez vos données

Pour appliquer des actions de protection flexible qui incluent le chiffrement, les restrictions d’accès et les marquages visuels, utilisez les fonctionnalités suivantes :

|Fonctionnalité|Quels problèmes est-il résolu ?|Prise en main|
|:------|:------------|---------------------|:----------------------------|
|[Étiquettes de confidentialité](sensitivity-labels.md)| Une solution unique entre les applications, les services et les appareils pour étiqueter et protéger vos données quand elles transitent à l’intérieur et à l’extérieur de votre organisation <br /><br />Exemple de scénario : [application et affichage des étiquettes de confidentialité dans Power bi et protection des données lors de leur exportation](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview)|[ Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md) |
|[Client de l’étiquetage unifié d’Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2)| Pour les ordinateurs Windows, il étend les étiquettes de confidentialité pour les fonctionnalités supplémentaires qui incluent l’étiquetage et la protection de tous les types de fichiers à partir de l’Explorateur de fichiers et de PowerShell.<br /><br /> Exemples de fonctionnalités supplémentaires : [configurations personnalisées pour le client d’étiquetage unifié Azure information protection](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations)| [Guide de l’administrateur du client d’étiquetage unifié Azure information protection](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Chiffrement à double clé](double-key-encryption.md)| Dans toutes les circonstances, vous seul pouvez déchiffrer le contenu protégé, ou pour les exigences réglementaires, vous devez tenir des clés de chiffrement dans une limite géographique. | [Déployer le chiffrement à double clé](double-key-encryption.md#deploy-double-key-encryption)|
|[Chiffrement de messages Office 365](ome.md) (OME)| Chiffre les messages électroniques et les documents joints qui sont envoyés à tous les utilisateurs sur n’importe quel appareil, afin que seuls les destinataires autorisés puissent lire les informations envoyées par courrier électronique  <br /><br />Exemple de scénario : [révoquer le courrier électronique chiffré par le chiffrement de messages avancé](revoke-ome-encrypted-mail.md) | [Prise en main du chiffrement de messages Office 365](set-up-new-message-encryption-capabilities.md)|
|[Chiffrement de service avec clé client](customer-key-overview.md) | Protège contre l’affichage des données par des systèmes ou du personnel non autorisés et complète le chiffrement de disque BitLocker dans les centres de données Microsoft | [Configurer la clé client pour Office 365](customer-key-set-up.md)|
|[Gestion des droits relatifs à l’information (IRM) dans SharePoint](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Protège les listes et les bibliothèques SharePoint de sorte que lorsqu’un utilisateur extrait un document, le fichier téléchargé est protégé afin que seules les personnes autorisées puissent afficher et utiliser le fichier en fonction des stratégies que vous spécifiez. | [Set up Information Rights Management (IRM) in SharePoint admin center](set-up-irm-in-sp-admin-center.md)|
[Connecteur RMS](https://docs.microsoft.com/azure/information-protection/deploy-rms-connector) |Protection-uniquement pour les déploiements locaux existants qui utilisent Exchange ou SharePoint Server, ou les serveurs de fichiers qui exécutent Windows Server et l’infrastructure de classification des fichiers (ICF) | [Étapes de déploiement du connecteur RMS](https://docs.microsoft.com/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Scanneur d’étiquetage unifié Azure information protection](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner)| Identifie, étiquette et protège les informations sensibles qui se trouvent dans des magasins de données se trouvant sur site | [Configuration et installation du scanneur d’étiquetage unifié Azure information protection](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)| Identifie, étiquette et protège les informations sensibles qui se trouvent dans les magasins de données dans le Cloud | [Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Kit de développement logiciel (SDK) de protection des informations Microsoft](https://docs.microsoft.com/information-protection/develop/overview#microsoft-information-protection-sdk)|Étend les étiquettes de confidentialité aux applications et services tiers  <br /><br /> Exemple de scénario : [définir et obtenir une étiquette de sensibilité (C++)](https://docs.microsoft.com/information-protection/develop/quick-file-set-get-label-cpp) |[Configuration et paramétrage du SDK Microsoft Information Protection (MIP)](https://docs.microsoft.com/information-protection/develop/setup-configure-mip)|

## <a name="prevent-data-loss"></a>Évitez les pertes de données

Pour empêcher le partage accidentel d’informations sensibles, utilisez les fonctionnalités suivantes :


|Fonctionnalité|Quels problèmes est-il résolu ?|Prise en main|
|:------|:------------|:---------------------|:-----------------------------|
|[Protection contre la perte de données](data-loss-prevention-policies.md) (DLP)| Empêche le partage involontaire d’éléments sensibles <br /><br />Exemple de scénario : [protéger les informations sensibles dans la conversation de Microsoft teams et les messages de canal](dlp-microsoft-teams.md) | [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)|
|[Protection contre la perte de données (préversion)](endpoint-dlp-learn-about.md)| Étend les fonctionnalités DLP aux éléments utilisés et partagés sur les ordinateurs Windows 10 | [Prise en main des points de terminaison de protection contre la perte de données (Preview)](endpoint-dlp-getting-started.md)|
