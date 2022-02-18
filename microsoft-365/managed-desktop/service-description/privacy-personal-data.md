---
title: Confidentialité et données personnelles
description: Détails des données collectées, stockées et utilisées par le service
keywords: R GDPR, rétention, suppression, stockage, rétention, traitement, sécurité, audit
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
manager: dougeby
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: medium
ms.openlocfilehash: a381bc70e73bf3bbb9f654f5d5dfffd2047f8ab5
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62895978"
---
# <a name="privacy"></a>Confidentialité

Microsoft Manged Desktop est un service ITaaS (IT-as-a-Service) pour les clients cloud d’entreprise conçu pour maintenir les appareils Windows employés déployés et mis à jour.

Il assure également la gestion et les opérations des services informatiques, surveille la sécurité et la réponse aux incidents, ainsi que la prise en charge des utilisateurs. Cet article fournit plus de détails sur la plateforme de données et la conformité de la confidentialité pour Microsoft Manged Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Manged Desktop sources de données et objectif

Microsoft Manged Desktop fournit son service aux clients d’entreprise et gère correctement les appareils inscrits des clients à l’aide de données provenant de différentes sources.

Ces sources incluent Azure Active Directory, Microsoft Intune, Microsoft Windows 10 et Microsoft Defender for Endpoint. Ils offrent une vue complète des appareils que Microsoft Manged Desktop gère. Le service utilise également ces services Microsoft pour activer Microsoft Manged Desktop pour fournir des fonctionnalités ITaaS :

| Source de données | Objectif |
| ------ | ------ |
| [Microsoft Windows 10 Entreprise](/windows/windows-10/) | Gestion de l’expérience de configuration des appareils, gestion des connexions à d’autres services et prise en charge opérationnelle pour les professionnels de l’informatique. |
| [Windows Update pour Entreprise](/windows/deployment/update/waas-manage-updates-wufb) | Utilise Windows 10 Entreprise données de diagnostic pour fournir des informations supplémentaires sur Windows 10 mise à jour. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Gestion des appareils et sécurisation de vos données. Les sources de données suivantes sont Microsoft Endpoint Manager :<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/) : authentification et identification de tous les comptes d’utilisateurs.</li><li>[Microsoft Intune](/mem/intune/) : distribution des configurations d’appareils, gestion des appareils et gestion des applications.</li><li>[Analyse des points de](/mem/analytics/overview) terminaison : informations analytiques sur l’utilisation des appareils et des applications.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot) : approvisionnement et déploiement d’appareils.</li><li>[Microsoft Defender pour le point de terminaison](/microsoft-365/security/defender-endpoint/) : fournit des services de sécurité tels que la surveillance de la sécurité des appareils et les données d’aide à la sécurité.</li></ul>
| [Bureau géré Microsoft](https://endpoint.microsoft.com/#home) | Données fournies par le client ou générées par le service lors de l’exécution du service. |
| [Microsoft 365 applications pour entreprise](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Gestion des Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Manged Desktop et stockage des données

Microsoft Manged Desktop s’appuie sur les données de plusieurs produits et services Microsoft pour fournir son service aux clients d’entreprise.

Pour protéger et maintenir les appareils inscrits, nous traiterons et copier les données de ces services vers Microsoft Manged Desktop. Lorsque nous traiterons des données, nous suivons les instructions documentées que vous fournissez, comme indiqué dans les Conditions d’accès aux [services](https://www.microsoft.com/licensing/product-licensing/products) en ligne et la Déclaration [de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement).

Microsoft Manged Desktop de traitement inclut la garantie d’une confidentialité, d’une sécurité et d’une résilience appropriées. Microsoft Manged Desktop utilise des mesures de confidentialité et de sécurité supplémentaires pour garantir une gestion appropriée des données d’identification personnelles.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Manged Desktop stockage des données et emplacement du personnel

Microsoft Manged Desktop stocke ses données dans les centres de données Azure aux États-Unis.

Les données personnelles obtenues par Microsoft Manged Desktop et d’autres services sont requises pour maintenir le service opérationnel. Si un appareil est supprimé de Microsoft Manged Desktop, nous conserveons les données personnelles pendant un maximum de 30 jours. Toutefois, les données d’alerte, collectées par Microsoft Defender pour endpoint, sont stockées pendant 180 jours à des fins de sécurité. Pour plus d’informations sur la rétention des données, consultez [Conservation, suppression et destruction des données dans Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

Microsoft Manged Desktop des équipes des opérations d’ingénierie et des opérations de sécurité se trouvent aux États-Unis et en Inde.

### <a name="microsoft-windows-10-diagnostic-data"></a>Données de diagnostic Windows 10 Microsoft

Microsoft Manged Desktop utilise Windows 10 données de [diagnostic](/windows/privacy/windows-diagnostic-data) améliorées pour maintenir Windows sécurité, à jour, résoudre les problèmes et améliorer les produits.

Le paramètre de données de diagnostic améliorées inclut des informations plus détaillées sur les appareils inscrits Microsoft Manged Desktop et leurs paramètres, fonctionnalités et état de l’appareil. Lorsque des données de diagnostic améliorées sont sélectionnées, les données, y compris les données de diagnostic requises, sont collectées. Pour plus d’informations, voir [Modifications apportées à Windows données de diagnostic sur](/windows/privacy/changes-to-windows-diagnostic-data-collection) le Windows 10 de données de diagnostic et la collecte de données.

La terminologie des données de diagnostic va changer dans les futures versions de Windows. Microsoft Manged Desktop s’engage à traiter uniquement les données dont le service a besoin. Bien que cela signifie que le niveau de diagnostic est passé à **Facultatif**, Microsoft Manged Desktop implémente les stratégies de diagnostic limitées pour affiner la collecte de données de diagnostic requise pour le service. Pour plus d’informations, voir [Modifications apportées à Windows de diagnostic.](/windows/privacy/changes-to-windows-diagnostic-data-collection)

Microsoft Manged Desktop traite et stocke uniquement les données au niveau du système à partir de Windows 10 données de diagnostic facultatives provenant d’appareils inscrits tels que la fiabilité des applications et des appareils, ainsi que des informations sur les performances. Microsoft Manged Desktop ne pas traiter et stocker les données personnelles des clients, telles que les données de conversation et d’historique du navigateur, les données vocales, textuelles ou vocales.

Pour plus d’informations sur la collecte de données de diagnostic de Microsoft Windows 10, voir [la section Où](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) stocker et traiter les données personnelles de la déclaration de confidentialité Microsoft.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update for Business

Microsoft Windows Update for Business utilise les données de Windows diagnostics pour analyser l’état et les échecs de la mise à jour. Microsoft Manged Desktop utilise ces données et les utilise pour atténuer et résoudre les problèmes afin de s’assurer que tous les appareils inscrits sont à jour en fonction d’une cadence de mise à jour prédéfinie.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

L’identification des données utilisées Microsoft Manged Desktop données est stockée par Azure Active Directory (Azure AD) dans un emplacement géographique. L’emplacement géographique est basé sur l’emplacement fourni par l’organisation lors de l’abonnement aux services en ligne Microsoft, tels que Microsoft Apps pour Enterprise et Azure. Pour plus d’informations sur l’emplacement Azure AD données de votre entreprise, voir [Azure Active Directory - Où se trouvent vos données ?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune collecte, traite et partage des données à Microsoft Manged Desktop pour prendre en charge les opérations et les services de l’entreprise. Pour plus d’informations sur les données collectées dans Intune, voir [Collecte de données dans Intune](/mem/intune/protect/privacy-data-collect) 

Pour plus d’informations Microsoft Intune des emplacements de données, consultez [l’emplacement Microsoft 365 données client sont stockées](/microsoft-365/enterprise/o365-data-locations). Intune respecte les sélections d’emplacements de stockage réalisées par l’administrateur pour les données client.

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

Microsoft Defender pour le point de terminaison collecte et stocke des informations pour les appareils inscrits Microsoft Manged Desktop à des fins d’administration, de suivi et de rapport. Les informations collectées incluent :

- Données de fichier (telles que les noms de fichiers, la taille et les hashes)
- Données de processus (processus en cours d’exécution, hashes)
- Données du Registre
- Données de connexion réseau
- Détails de l’appareil (tels que les identificateurs d’appareil, les noms des appareils et la version du système d’exploitation)

Pour plus d’informations sur les emplacements de stockage et de collecte de données de Microsoft Defender for Endpoint, voir Microsoft Defender pour le stockage et la confidentialité des données des [points de terminaison](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

Microsoft 365 Apps for Enterprise collecte et partage des données avec Microsoft Manged Desktop pour s’assurer que ces applications sont à jour avec la dernière version. Ces mises à jour sont basées sur des canaux de mise à jour prédéfin Microsoft Manged Desktop. Pour plus d’informations Microsoft 365 Apps les emplacements de stockage et de collecte de données de l’utilisateur, voir Microsoft Defender pour le stockage et la confidentialité des données [de point de terminaison](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Notification de modification majeure des données

Microsoft Manged Desktop suit un processus de contrôle des changements décrit dans notre infrastructure de communication de service.

Nous informons les clients via Microsoft 365 centre de messages et Microsoft Manged Desktop portail d’administration des incidents de sécurité et des modifications majeures apportées au service.

Les modifications apportées aux types de données recueillies et à l’endroit où elles sont stockées sont considérées comme des modifications importantes. Nous fournirons un minimum de 30 jours de notification avancée de ce changement, comme c’est la pratique standard pour Microsoft 365 et services. Pour plus d’informations, [voir Changements de service et communication](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Conformité

Microsoft Manged Desktop a subi des audits externes et obtenu un ensemble complet d’offres de conformité. Vous trouverez plus d’informations [dans conformité](/microsoft-365/managed-desktop/intro/compliance). Les rapports d’audit peuvent être téléchargés sur le portail d’confiance des [services Microsoft,](https://aka.ms/stp) qui sert de référentiel central pour Microsoft Enterprise Online Services. Microsoft Manged Desktop est répertorié dans ces documents sous la catégorie « Surveillance et gestion ».

### <a name="data-subject-requests"></a>Demandes de la personne concernée

Microsoft Manged Desktop suit les réglementations en matière de confidentialité du R GDPR et du CCPA, qui donnent aux sujets de données des droits spécifiques sur leurs données personnelles.

Ces droits sont les suivants :

- Obtention de copies de données personnelles
- Demande de corrections
- Limitation du traitement de celui-ci
- Suppression
- Réception dans un format électronique afin qu’il puisse être déplacé vers un autre contrôleur.

Pour plus d’informations générales sur les demandes des personnes à l’aide des données, consultez demandes des personnes qui en sont soumises aux données, ainsi que le [R GDPR et le CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Pour exercer des demandes des personnes responsables des données sur les données collectées par Microsoft Manged Desktop système de gestion des cas, consultez les demandes des personnes responsables des données suivantes :

| Demandes de la personne concernée | Description |
| ------ | ------ |
| Données provenant de Microsoft Defender pour les alertes de point de terminaison | Votre administrateur de la sécurité peut demander la suppression ou l’extraction de données personnelles liées aux alertes de Microsoft Defender for Endpoint en envoyant une demande de rapport dans le [portail d’administration](https://aka.ms/memadmin). <br><br> Fournissez les informations suivantes : <br><ul><li>Type de demande : demande de modification</li><li>Catégorie : Sécurité</li><li>Sous-catégorie : Autre</li><li>Description : fournissez les noms d’appareils appropriés.</li></ul> |
| Données provenant de demandes Microsoft Manged Desktop prise en charge | Votre administrateur informatique peut demander la suppression ou l’extraction des demandes de support liées aux données personnelles en envoyant une demande de rapport sur le portail [d’administration](https://aka.ms/memadmin). <br><br> Fournissez les informations suivantes : <ul><li>Type de demande : demande de modification</li><li>Catégorie : Sécurité</li><li>Sous-catégorie : Autre</li><li>Description : fournissez les noms d’appareil ou d’utilisateur appropriés.</li></ul>

Pour les DSR provenant d’autres produits liés au service, consultez les articles suivants :

- Windows [de diagnostic](/compliance/regulatory/gdpr-dsr-windows)
- Données Microsoft [Intune](/compliance/regulatory/gdpr-dsr-intune)
- Données Azure Active [Directory](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Informations juridiques

**Avis de confidentialité de Microsoft aux utilisateurs finaux des produits fournis par les clients de l’organisation** :

La [déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement) informe les utilisateurs finaux que lorsqu’ils se connectent aux produits Microsoft avec un compte de travail :

1. Leur organisation peut contrôler et administrer son compte (y compris le contrôle des paramètres de confidentialité), et accéder à ses données et les traiter.
1. Microsoft peut collecter et traiter les données pour fournir le service à l’organisation et aux utilisateurs finaux.
