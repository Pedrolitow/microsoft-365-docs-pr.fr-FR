---
title: Microsoft Information Protection dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
description: Implémentez Microsoft Information Protection (MIP) pour vous permettre de protéger les informations sensibles où qu’elles se trouvent.
ms.openlocfilehash: 285b5885f56151bcbd877eb6ede04447c7a405dc
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927038"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>Microsoft Information Protection dans Microsoft 365.

>*[Licences de sécurité et de conformité Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Implémentez Microsoft Information Protection (MIP) pour vous permettre de découvrir, classifier et protéger les informations sensibles où qu’elles se trouvent.

Les fonctionnalités MIP sont incluses dans la Conformité Microsoft 365 et vous donnent les outils nécessaires pour vous permettre de [connaître vos données](#know-your-data), [protéger vos données](#protect-your-data) et [éviter la perte de vos données](#prevent-data-loss).

![Image qui illustre la façon dont MIP vous permet de découvrir, de classifier et de protéger les données sensibles](../media/powered-by-intelligent-platform.png)

Si vous souhaitez en savoir plus sur la gestion de vos données, consultez l’article [Gouvernance des données Microsoft dans Microsoft 365](manage-Information-governance.md).

## <a name="know-your-data"></a>Connaître vos données

> [!NOTE]
> Si vous souhaitez en savoir plus sur la classification et l’étiquetage des données dans Azure Purview, actuellement en préversion, veuillez consulter la section [Étiqueter automatiquement votre contenu dans Azure Purview](/azure/purview/create-sensitivity-label).
> 
> Pour obtenir les annonces de publication concernant Azure Purview, consultez ces billets de blog : [Microsoft Information Protection et Microsoft Azure Purview : Better Together](https://techcommunity.microsoft.com/t5/microsoft-security-and/microsoft-information-protection-and-microsoft-azure-purview/ba-p/1957481) et [Azure Purview à Ignite 2021 du printemps](https://techcommunity.microsoft.com/t5/azure-purview/azure-purview-at-spring-ignite-2021/ba-p/2175919).


Pour comprendre votre paysage de données, puis identifier les données importantes dans votre environnement hybride, utilisez les fonctionnalités suivantes :
 
|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|:--------------------|:-----------------------------|
|[Types d’informations sensibles](sensitive-information-type-entity-definitions.md)| Identifie les données sensibles à l’aide d’expressions régulières intégrées ou personnalisées, ou à l’aide d'une fonction. Les preuves corroborantes comprennent des mots clés, des niveaux de confiance et la proximité.| [Personnaliser un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md)|
|[Classifieurs avec capacité d’apprentissage](classifier-learn-about.md)| Identifie les données sensibles à l’aide d’exemples de données qui vous intéressent au lieu d’identifier les éléments dans l’élément (mise en correspondance des modèles). Vous pouvez utiliser des classifieurs intégrés ou former un classifieur avec votre propre contenu.| [Prise en main des classifieurs présentant une capacité d’apprentissage](classifier-get-started-with.md) |
|[Classification des données](data-classification-overview.md) | Identification graphique d’éléments de votre organisation qui ont une étiquette de niveau de fidélité, une étiquette de rétention ou qui ont été classés. Vous pouvez également utiliser ces informations pour en savoir plus sur les actions effectuées par vos utilisateurs sur ces éléments. | [Prise en main de l’explorateur de contenu](data-classification-content-explorer.md)<br /><br /> [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Protéger ses données

Pour appliquer des actions de protection flexibles qui incluent le chiffrement, les restrictions d’accès et les marquages visuelles, utilisez les fonctionnalités suivantes :

|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|---------------------|:----------------------------|
|[Étiquettes de confidentialité](sensitivity-labels.md)| Une solution unique pour les applications, les services et les appareils qui permet d’étiqueter, puis de protéger vos données lors de leur déplacement à l’intérieur et à l’extérieur de votre organisation. <br /><br />Exemples de scénarios : <br /> [Gérer les étiquettes de confidentialité pour les applications Office](sensitivity-labels-office-apps.md)<br /> [Chiffrer des documents et des e-mails](encryption-sensitivity-labels.md )<br /> [Appliquer et afficher des étiquettes dans Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Si vous souhaitez obtenir la liste complète des scénarios d’étiquettes de niveau de niveau de vie, veuillez consulter la documentation Prise en main.|[Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md) |
|[Client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)| Étend les étiquettes de confidentialité pour des fonctionnalités supplémentaires, qui incluent l’étiquetage et la protection de tous les types de fichiers depuis l’Explorateur de fichiers et PowerShell, pour les ordinateurs Windows<br /><br /> Exemples de fonctionnalités supplémentaires : [configurations personnalisées pour le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-customizations)| [Guide de l’utilisateur pour l’étiquetage unifié d’Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Chiffrement à double clé](double-key-encryption.md)| Dans tous les cas, seule votre organisation déchiffrer le contenu protégé. Pour respecter les obligations réglementaires, vous devez conserver les clés de chiffrement dans la limite géographique définie. | [Déployer le chiffrement à double clé](double-key-encryption.md#deploy-dke)|
|[Chiffrement de messages Office 365 (OME)](ome.md)| Chiffre les e-mails et les documents joints envoyés à tous les utilisateurs sur tous les appareils, pour que seuls les destinataires autorisés puissent lire les informations envoyées par e-mail.  <br /><br />Exemple de scénario : [révoquer les e-mails chiffrés avec le Chiffrement avancé des messages](revoke-ome-encrypted-mail.md) | [Configurer les nouvelles fonctionnalités de chiffrement de messages](set-up-new-message-encryption-capabilities.md)|
|[Chiffrement du service avec la clé client](customer-key-overview.md) | Empêche l’affichage de données par des systèmes ou du personnel non autorisés, puis complète le chiffrement de disque BitLocker dans les centres de données Microsoft. | [Configurer la clé client pour Office 365](customer-key-set-up.md)|
|[Gestion des droits relatifs à l’information SharePoint](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Protège les listes et les bibliothèques SharePoint. Lorsqu’un utilisateur extrait un document, le fichier téléchargé est protégé pour que seules les personnes autorisées puissent l’afficher et l’utiliser conformément aux stratégies spécifiées. | [Configurer la gestion des droits relatifs à l’information dans le centre d’administration SharePoint](set-up-irm-in-sp-admin-center.md)|
[Connecteur de gestion des droits](/azure/information-protection/deploy-rms-connector) |Offre uniquement une protection pour les déploiements locaux existants qui utilisent Exchange ou SharePoint Server, ou les serveurs de fichiers qui fonctionnent avec Windows Server et l’infrastructure de classification de fichiers. | [Étapes de déploiement du connecteur RMS](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner)| Découvre, étiquette, puis protège les informations sensibles résidant dans des magasins de données locaux. | [Configurer et installer le scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security)| Découvre, étiquette, puis protège les informations sensibles résidant dans les magasins de données situés dans le cloud. | [Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Kit de développement logiciel (SDK) de Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk)|Étend les étiquettes de confidentialité aux applications et services tiers.  <br /><br /> Exemple de scénario : [définir et obtenir une étiquette de confidentialité (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[Configuration et paramétrage du kit de développement logiciel (SDK) de Microsoft Information Protection (MIP)](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Éviter les pertes de données

Pour éviter le partage excessif accidentel d’informations sensibles, utilisez les fonctionnalités suivantes :


|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|:---------------------|:-----------------------------|
|[Protection contre la perte de données (DLP)](data-loss-prevention-policies.md)| Permet d’empêcher le partage involontaire d’éléments sensibles. <br /><br />Exemple de scénario : [protéger les informations sensibles dans les messages de conversation et de canal de Microsoft Teams](dlp-microsoft-teams.md) | [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)|
|[Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)| Étend les fonctionnalités DLP aux éléments utilisés et partagés sur les ordinateurs Windows 10. | [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)|