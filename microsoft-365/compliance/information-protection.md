---
title: Protection de l'information Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: Implémentez les fonctionnalités de la protection des données Microsoft Purview pour vous aider à protéger les informations sensibles où qu’elles se trouvent ou voyagent.
ms.openlocfilehash: b055e71ee6c22cc9804b82a36f339a73675ce914
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294644"
---
# <a name="protect-your-sensitive-data-with-microsoft-purview"></a>Protéger vos données sensibles avec Microsoft Purview

>*[Licences de sécurité et de conformité Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!TIP]
> *Saviez-vous que vous pouvez essayer les versions Premium des neuf solutions Microsoft Purview gratuitement ?* Utilisez la version d’évaluation des solutions Purview de 90 jours pour découvrir comment des fonctionnalités Purview robustes peuvent aider votre organisation à répondre à ses besoins de conformité. Microsoft 365 E3 et Office 365 E3 clients peuvent être démarrés maintenant sur le [Hub d’essais du portail de conformité Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Découvrez plus d’informations sur [les personnes qui peuvent s’inscrire et les conditions d’évaluation](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Implémentez des fonctionnalités de la **Protection des données Microsoft Purview** (anciennement appelée Protection des données Microsoft) pour vous aider à découvrir, classifier et protéger des informations sensibles où qu’elles se trouvent ou voyagent.

Ces fonctionnalités de protection des informations vous donnent les outils nécessaires pour [connaître vos données](#know-your-data), [protéger vos données](#protect-your-data) et [empêcher la perte de données](#prevent-data-loss).

![Image montrant comment la protection des données Microsoft Purview vous aide à découvrir, classifier et protéger des données sensibles.](../media/powered-by-intelligent-platform.png)

Les sections suivantes vous permettront d'en savoir plus sur les fonctionnalités disponibles et sur la manière de les utiliser. Toutefois, si vous recherchez un déploiement guidé, voir [Déployer une solution de protection des informations avec Microsoft Purview](information-protection-solution.md).

Pour plus d'informations sur la gestion de vos données dans le cadre de la conformité ou des exigences réglementaires, voir [La gestion de vos données avec Microsoft Purview](manage-data-governance.md).

## <a name="know-your-data"></a>Connaître vos données

Pour comprendre le paysage de vos données et identifier les données sensibles dans votre environnement hybride, utilisez les fonctionnalités suivantes :

|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|:--------------------|
|[Types d’informations sensibles](sensitive-information-type-learn-about.md)| Identifie les données sensibles à l’aide d’expressions régulières intégrées ou personnalisées, ou à l’aide d'une fonction. Les preuves corroborantes comprennent des mots clés, des niveaux de confiance et la proximité.| [Personnaliser un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md)|
|[Classifieurs avec capacité d’apprentissage](classifier-learn-about.md)| Identifie les données sensibles à l’aide d’exemples de données qui vous intéressent au lieu d’identifier les éléments dans l’élément (mise en correspondance des modèles). Vous pouvez utiliser des classifieurs intégrés ou former un classifieur avec votre propre contenu.| [Prise en main des classifieurs présentant une capacité d’apprentissage](classifier-get-started-with.md) |
|[Classification des données](data-classification-overview.md) | Identification graphique d’éléments de votre organisation qui ont une étiquette de niveau de fidélité, une étiquette de rétention ou qui ont été classés. Vous pouvez également utiliser ces informations pour en savoir plus sur les actions effectuées par vos utilisateurs sur ces éléments. | [Prise en main de l’explorateur de contenu](data-classification-content-explorer.md) <p> [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Protéger ses données

Pour appliquer des actions de protection flexibles qui incluent le chiffrement, les restrictions d’accès et les marquages visuelles, utilisez les fonctionnalités suivantes :

|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|---------------------|
|[Étiquettes de confidentialité](sensitivity-labels.md)| Une solution d'étiquetage unique pour les applications, les services et les appareils afin de protéger vos données lorsqu'elles circulent à l'intérieur et à l'extérieur de votre entreprise. <br /><br /> Exemples de scénarios : <br />- [Gérer les étiquettes de confidentialité pour les applications Office](sensitivity-labels-office-apps.md) <br />- [Chiffrer des documents et des e-mails](encryption-sensitivity-labels.md) <br />-  [Appliquer et afficher des étiquettes dans Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Pour obtenir une liste complète des scénarios pris en charge pour les étiquettes de sensibilité, consultez la documentation Commencer.|[Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md) |
|[Client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)| Pour les ordinateurs Windows, étend l’étiquetage à l’Explorateur de fichiers et à PowerShell, avec des fonctionnalités supplémentaires pour Office applications si nécessaire.| [Guide de l’utilisateur pour l’étiquetage unifié d’Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Chiffrement à double clé](double-key-encryption.md)| Dans tous les cas, seule votre organisation déchiffrer le contenu protégé. Pour respecter les obligations réglementaires, vous devez conserver les clés de chiffrement dans la limite géographique définie. | [Déployer le chiffrement à double clé](double-key-encryption.md#deploy-dke)|
|[Chiffrement de messages Office 365 (OME)](ome.md)| Chiffre les e-mails et les documents joints envoyés à tous les utilisateurs sur tous les appareils, pour que seuls les destinataires autorisés puissent lire les informations envoyées par e-mail. <br /><br />  Exemple de scénario : [révoquer les e-mails chiffrés avec le Chiffrement avancé des messages](revoke-ome-encrypted-mail.md) | [Configurer les nouvelles fonctionnalités de chiffrement de messages](set-up-new-message-encryption-capabilities.md)|
|[Chiffrement du service avec la clé client](customer-key-overview.md) | Empêche l’affichage de données par des systèmes ou du personnel non autorisés, puis complète le chiffrement de disque BitLocker dans les centres de données Microsoft. | [Configurer la clé client pour Office 365](customer-key-set-up.md)|
|[Gestion des droits relatifs à l’information SharePoint](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Protège les listes et les bibliothèques SharePoint. Lorsqu’un utilisateur extrait un document, le fichier téléchargé est protégé pour que seules les personnes autorisées puissent l’afficher et l’utiliser conformément aux stratégies spécifiées. | [Configurer la gestion des droits relatifs à l’information dans le centre d’administration SharePoint](set-up-irm-in-sp-admin-center.md)|
[Connecteur de gestion des droits](/azure/information-protection/deploy-rms-connector) |Offre uniquement une protection pour les déploiements locaux existants qui utilisent Exchange ou SharePoint Server, ou les serveurs de fichiers qui fonctionnent avec Windows Server et l’infrastructure de classification de fichiers. | [Étapes de déploiement du connecteur RMS](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner)| Découvre, étiquette, puis protège les informations sensibles résidant dans des magasins de données locaux. | [Configurer et installer le scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)| Découvre, étiquette, puis protège les informations sensibles résidant dans les magasins de données situés dans le cloud. | [Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Carte de données Microsoft Purview](/azure/purview/overview) |Identifie les données sensibles et applique l’étiquetage automatique au contenu des ressources de carte de données Microsoft Purview. Ceux-ci incluent des fichiers dans le stockage comme Azure Data Lake et Azure Files, ainsi que des données schématisées telles que des colonnes dans Azure SQL base de données et Cosmos DB. |[Étiquetage dans la carte de données Microsoft Purview](/azure/purview/create-sensitivity-label) |
|[Kit de développement logiciel (SDK) de Microsoft Information Protection](/information-protection/develop/overview#microsoft-information-protection-sdk)|Étend les étiquettes de confidentialité aux applications et services tiers. <br /><br />  Exemple de scénario : [définir et obtenir une étiquette de confidentialité (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[Configuration et paramétrage du kit de développement logiciel (SDK) de Microsoft Information Protection (MIP)](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Éviter les pertes de données

Pour éviter le partage excessif accidentel d’informations sensibles, utilisez les fonctionnalités suivantes :


|Fonctionnalité|Utilité|Prise en main|
|:------|:------------|:---------------------|
|[Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)| Permet d’empêcher le partage involontaire d’éléments sensibles. | [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)|
|[Point de terminaison protection contre la perte de données](endpoint-dlp-learn-about.md)| Étend les fonctionnalités DLP aux éléments utilisés et partagés sur les ordinateurs Windows 10. | [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)|
|[Extension de la conformité Microsoft](dlp-chrome-learn-about.md) | Étend les fonctionnalités de protection contre la perte de données au navigateur Chrome | [Prise en main de l’extension de la conformité Microsoft](dlp-chrome-get-started.md)|
|[Scanner local de protection contre la perte de données Microsoft Purview (préversion)](dlp-on-premises-scanner-learn.md)|Étend la surveillance de la protection contre la perte de données des activités sur fichier et des actions de protection pour les partages de fichiers locaux, pour les dossiers locaux et les bibliothèques de documents SharePoint.|[Prise en main du scanner local de protection contre la perte de données sur site Microsoft Purview (préversion)](dlp-on-premises-scanner-get-started.md)|
|[Protéger les informations sensibles dans les messages de conversation et de canal de Microsoft Teams](dlp-microsoft-teams.md) | Étend certaines fonctionnalités de protection contre la perte de données aux messages de canal et aux conversations Teams. | [En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préversion)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Les exigences de licence pour la protection des données Microsoft Purview dépendent des scénarios et des fonctionnalités que vous utilisez, au lieu de définir des exigences de licence pour chaque fonctionnalité répertoriée sur cette page. Pour comprendre vos exigences et options de licence pour la protection des données Microsoft Purview, consultez les sections **Protection des données** des [Recommandations Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) et les [Téléchargement PDF](https://go.microsoft.com/fwlink/?linkid=2139145) connexes pour les exigences de licence au niveau des fonctionnalités.
