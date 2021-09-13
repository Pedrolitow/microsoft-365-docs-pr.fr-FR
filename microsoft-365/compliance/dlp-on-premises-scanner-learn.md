---
title: 'En savoir plus sur le scanner local de prévention des pertes de données Microsoft 365 '
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Le scanneur local de protection contre la perte de données Microsoft 365 en local étend la surveillance des activités sur fichier et des actions de protection pour les partages de fichiers locaux, pour les dossiers locaux et les bibliothèques de documents SharePoint. Le scanneur Azure Information Protection (AIP) analyse, puis protège les fichiers.
ms.openlocfilehash: c59c6b90f6c219528cbff8a4aadc6472a48ecd23
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183544"
---
# <a name="learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>En savoir plus sur le scanner local de prévention des pertes de données Microsoft 365

Le scanneur de protection contre la perte de données Microsoft Points de terminaison Protection contre la perte de données (Endpoint DLP) fait partie de la suite de fonctionnalités de protection contre la perte de données (DLP) Microsoft 365 que vous pouvez utiliser pour découvrir, puis protéger les éléments sensibles dans les services Microsoft 365. Si vous souhaitez en savoir plus sur les offres DLP de Microsoft, veuillez consulter la rubrique [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md).

Le **scanneur local de protection contre la perte de données** analyse les données locales au repos dans les partages de fichiers, ainsi que dans les dossiers et bibliothèques de documents SharePoint pour y rechercher les éléments sensibles. En cas de fuite, ces éléments constitueraient un risque pour votre organisation ou un risque de violation de la stratégie de conformité. Ainsi, vous bénéficiez de la visibilité et du contrôle dont vous avez besoin pour garantir une utilisation et une protection correctes de ces éléments, puis éviter tout comportement risqué susceptible de les compromettre. Le scanneur local de protection contre la perte de données détecte les informations sensibles à l’aide de types d’informations [intégrées](sensitive-information-type-entity-definitions.md) ou [sensibles personnalisées](create-a-custom-sensitive-information-type.md), d’[étiquettes de niveau de](sensitivity-labels.md) ou de propriétés de fichier. Les informations relatives aux actions des utilisateurs avec les éléments sensibles apparaissent dans [l’Explorateur d’activités](data-classification-activity-explorer.md), et vous pouvez appliquer des actions de protection à ces éléments via les [stratégies DLP](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>Le scanneur local de protection contre la perte de données s’appuie sur le scanneur Azure Information Protection

Le scanneur local de protection contre la perte de données s’appuie sur une implémentation complète du scanneur Azure Information Protection (AIP) pour surveiller, étiqueter, puis protéger les éléments sensibles. Si vous n’êtes pas familiarisé avec le scanneur AIP, nous vous recommandons vivement de vous y familiariser. Veuillez consulter les articles suivants :

- [Qu'est-ce qu'Azure Information Protection ?](/azure/information-protection/what-is-information-protection)
- [Qu’est-ce que le scanneur d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner)
- [Configuration requise pour l’installation et le déploiement du scanneur d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-prereqs)
- [Tutoriel : Installation du scanneur d’étiquetage unifié Azure Information Protection (AIP)](/azure/information-protection/tutorial-install-scanner)
- [Configurer et installer le scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Client d’étiquetage unifié Azure Information Protection : historique des versions et stratégie de support](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>Actions du scanneur local de protection contre la perte de données

Le scanneur local de protection contre la perte de données détecte les fichiers par l’une des quatre méthodes ci-après :

- types d’informations sensibles
- étiquettes de confidentialité
- extension du fichier
- propriétés de document personnalisées sur les fichiers Office uniquement 

Lorsqu’un fichier détecté présente un risque potentiel en cas de fuite ou de violation de stratégie de conformité, le scanneur local de protection contre la perte de données peut effectuer l’une de ces quatre actions.

|Opération |Description  |
|---------|---------|
|**Empêcher ces personnes d’accéder à un fichier stocké dans un scanneur local : Tout le monde** | Cette action bloque l’accès à tous les comptes à l’exception du propriétaire du contenu, du dernier compte qui a modifié l’élément et de l’administrateur. Pour ce faire, le programme supprime tous les comptes des autorisations NTFS/SharePoint au niveau du fichier, à l’exception du propriétaire du fichier, du propriétaire du référentiel (défini dans le paramètre de [définition du propriétaire du référentiel](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) dans le travail d’analyse de contenu), du dernier modificateur (peut être identifié dans SharePoint uniquement) et de l’administrateur. Le compte du scanneur bénéficie également des droits FC sur le fichier.|
|**Empêcher ces personnes d’accéder à un fichier stocké dans un scanneur local : bloquer l’accès (public) à l’échelle de l’organisation**    |Cette action supprime les SID **_Tout le monde_*_, _*_NT AUTHORITY\utilisateurs identifiés_*_ et _*_Utilisateurs du domaine_** de la liste de contrôle d’accès au fichier (ACL). Seuls les utilisateurs et les groupes qui ont reçu explicitement les droits d’accès au fichier ou au dossier parent pourront accéder au fichier.|
|**Définir des autorisations sur le fichier**|Cette action force le fichier à hériter des autorisations de son dossier parent. Par défaut, cette action n’est applicable que si les autorisations du dossier parent sont plus restrictives que celles déjà appliquées au fichier. Par exemple, si vous avez défini la liste de contrôle d'accès du fichier pour autoriser uniquement des **_utilisateurs spécifiques_*_ et que vous avez configuré le dossier parent pour autoriser le groupe _*_Utilisateurs du domaine_*_, le fichier n’héritera pas des autorisations du dossier parent. Vous pouvez remplacer ce comportement en sélectionnant l’option _* Inherit even if parent permissions are less restrictive** (Hériter, même si les autorisations parent sont moins restrictives).|
|**Supprimer le fichier d’un emplacement incorrect**|Cette action remplace le fichier d’origine par un fichier stub avec l’extension .txt, puis place une copie du fichier d’origine dans un dossier de mise en quarantaine. 

## <a name="whats-different-in-the-on-premises-scanner"></a>Différences dans le scanneur local

Vous devez tenir compte d’un certain nombre de concepts supplémentaires avant d’examiner en profondeur le scanneur local.

### <a name="aip-repositories-and-content-scan-jobs"></a>Référentiels et tâches d’analyse de contenu AIP

Vous devez créer une tâche d’analyse de contenu AIP, puis spécifier les référentiels qui hébergent les fichiers que le moteur DLP doit évaluer selon vous. Veillez à activer les règles DLP dans la tâche d’analyse de contenu AIP créée.

### <a name="policy-tips"></a>Conseils de stratégie

Les [Conseils de stratégie](use-notifications-and-policy-tips.md) ne sont pas disponibles sur le scanneur local.


### <a name="viewing-dlp-on-premises-scanner-events"></a>Affichage des événements liés au scanneur local de protection contre la perte de données

Affichez les données du scanneur local de protection contre la perte de données dans l’[Explorateur d’activités](data-classification-activity-explorer.md) du Centre de conformité M365. 

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous en savez plus sur le scanneur local de protection contre la perte de données, vos prochaines étapes sont les suivantes :

1. [Prise en main du scanner local de protection contre la perte de données](dlp-on-premises-scanner-get-started.md)
2. [Utilisation du scanneur local de protection contre la perte de données](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>Voir aussi

- [Prise en main du scanner local de protection contre la perte de données Microsoft](dlp-on-premises-scanner-get-started.md)
- [Utilisation du scanneur local de protection contre la perte de données Microsoft](dlp-on-premises-scanner-use.md)
- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)