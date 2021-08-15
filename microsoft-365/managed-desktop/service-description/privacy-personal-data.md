---
title: Confidentialité et données personnelles
description: Détails des données collectées, stockées et utilisées par le service
keywords: R GDPR, rétention, suppression, stockage, rétention, traitement, sécurité, audit
ms.service: m365-md
ms.sitesec: library
author: jaimeo
manager: laurawi
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: normal
ms.openlocfilehash: 15268fb8203aad48c0515277851f38f22719d8f06a1fc2af12c84e37df8b6b46
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53877652"
---
# <a name="overview"></a>Vue d’ensemble

Microsoft Manged Desktop est un service ITaaS (IT-as-a-Service) pour les clients cloud d’entreprise conçu pour maintenir les appareils Windows employés déployés et mis à jour. Il assure également la gestion et les opérations des services informatiques, surveille la sécurité et la réponse aux incidents, ainsi que la prise en charge des utilisateurs. Cette documentation fournit des détails supplémentaires sur la plateforme de données et la conformité de la confidentialité pour Microsoft Manged Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Manged Desktop sources de données et objectif

Microsoft Manged Desktop fournit son service aux clients d’entreprise et gère correctement les appareils inscrits des clients à l’aide de données provenant de différentes sources. Ces sources, notamment Azure Active Directory, Microsoft Intune, Microsoft Windows 10 et Microsoft Defender pour le point de terminaison, fournissent une vue complète des appareils que Microsoft Manged Desktop gère. Le service utilise également ces services Microsoft pour activer Microsoft Manged Desktop pour fournir des fonctionnalités ITaaS :

- [Microsoft Windows 10 Entreprise](/windows/windows-10/) - pour la gestion de l’expérience de configuration des appareils, la gestion des connexions à d’autres services et la prise en charge opérationnelle pour les professionnels de l’informatique.
- [Windows mise à jour](/windows/deployment/update/waas-manage-updates-wufb) pour entreprise : utilise Windows 10 Entreprise données de diagnostic pour fournir des informations supplémentaires sur Windows 10 mise à jour. 
- [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) : pour la gestion des appareils et la sécurisation de vos données.
  - [Microsoft Azure Active Directory](/azure/active-directory/) - pour l’authentification et l’identification de tous les comptes d’utilisateurs. 
  - [Microsoft Intune](/mem/intune/) : pour distribuer les configurations des appareils, la gestion des appareils et la gestion des applications.
  - [Analyse des points de](/mem/analytics/overview) terminaison : pour obtenir des informations analytiques sur l’utilisation des appareils et des applications.
  - [Windows Autopilot](/microsoft-365/windows/windows-autopilot) : pour la mise en service et le déploiement d’appareils.
  - [Microsoft Defender pour point de terminaison :](/microsoft-365/security/defender-endpoint/) fournit des services de sécurité tels que la surveillance de la sécurité des appareils et les données d’intelligence de sécurité.
- [Microsoft Manged Desktop](https://endpoint.microsoft.com/#home) : données fournies par le client ou générées par le service lors de l’exécution du service.
- [Microsoft 365 applications pour entreprise :](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1) pour la gestion des Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Manged Desktop de données et stockage

Microsoft Manged Desktop s’appuie sur les données de plusieurs produits et services Microsoft pour fournir son service aux clients d’entreprise. Pour atteindre l’objectif de protection et de maintenance des appareils inscrits, nous allons traiter et copier les données de ces services vers Microsoft Manged Desktop. Lorsque nous traiterons des données, nous suivons les instructions documentées que vous fournissez, comme indiqué dans les Conditions d’accès aux services en ligne et la Déclaration de confidentialité Microsoft. Lorsque nous traiterons des données, nous suivons les instructions documentées que vous fournissez, comme indiqué dans les conditions d’accès aux [services](https://www.microsoft.com/licensing/product-licensing/products) en ligne et la déclaration [de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement). Microsoft Manged Desktop de processeur inclut la garantie d’une confidentialité, d’une sécurité et d’une résilience appropriées. Microsoft Manged Desktop utilise des mesures de confidentialité et de sécurité supplémentaires pour garantir une gestion appropriée des données d’identification personnelles. 


## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Manged Desktop stockage des données et emplacement du personnel

Microsoft Manged Desktop stocke ses données dans les centres de données Azure aux États-Unis. Les données personnelles obtenues par Microsoft Manged Desktop et d’autres services sont requises pour maintenir le service opérationnel. Si un appareil est supprimé de Microsoft Manged Desktop, nous conserveons les données personnelles pendant un maximum de 30 jours, à l’exception des données d’alerte collectées par Microsoft Defender pour endpoint, qui sont stockées pendant 180 jours à des fins de sécurité. Pour plus d’informations sur la rétention des données, voir [Rétention, suppression](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview)et destruction des données dans Microsoft 365 .

Microsoft Manged Desktop Les équipes des opérations d’ingénierie et des opérations de sécurité sont situées aux États-Unis et en Inde. 

## <a name="microsoft-windows-10-diagnostic-data"></a>Données de diagnostic Windows 10 Microsoft

Microsoft Manged Desktop utilise [Windows 10](/windows/privacy/windows-diagnostic-data) données de diagnostic améliorées pour maintenir Windows sécurité, à jour, résoudre les problèmes et améliorer les produits. Le paramètre de données de diagnostic améliorées inclut des informations plus détaillées sur les appareils inscrits dans Microsoft Manged Desktop et leurs paramètres, fonctionnalités et état de l’appareil. Lorsque des données de diagnostic améliorées sont sélectionnées, les données, y compris les données de diagnostic requises, sont collectées. Pour [plus d’informations sur Windows la collecte](/windows/privacy/changes-to-windows-diagnostic-data-collection) de données de diagnostic, voir Windows 10 données de diagnostic et la collecte de données.

La terminologie des données de diagnostic va changer dans les futures versions de Windows. Microsoft Manged Desktop s’engage à traiter uniquement les données dont le service a besoin. Bien que cela signifie que le niveau de diagnostic est passé à **Facultatif,** Microsoft Manged Desktop implémente les stratégies de diagnostic limitées pour affiner la collecte des données de diagnostic requises pour le service. Pour plus d’informations, voir [Modifications apportées à Windows de diagnostic.](/windows/privacy/changes-to-windows-diagnostic-data-collection)

Microsoft Manged Desktop traite et stocke uniquement les données au niveau du système à partir de Windows 10 données de diagnostic facultatives provenant d’appareils inscrits tels que les informations de fiabilité et de performances des applications et des appareils. Microsoft Manged Desktop ne permet pas de traiter et de stocker les données personnelles des clients, telles que l’historique de conversation et de navigateur, les données vocales, textuelles ou vocales. 

Pour plus d’informations sur la collecte de données de diagnostic de Microsoft Windows 10, voir la [section](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) Où stocker et traiter les données personnelles de la déclaration de confidentialité Microsoft.

## <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update for Business
Microsoft Windows Update for Business utilise les données de Windows diagnostics pour analyser l’état et les échecs de la mise à jour. Microsoft Manged Desktop utilise ces données pour atténuer et résoudre les problèmes afin de s’assurer que tous les appareils inscrits sont à jour en fonction d’une cadence de mise à jour prédéfinie.

## <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory
L’identification des données utilisées par Microsoft Manged Desktop est stockée par Azure Active Directory (Azure AD) dans un emplacement géographique basé sur l’emplacement fourni par l’organisation lors de l’abonnement aux services en ligne Microsoft, tels que Microsoft Apps pour entreprise et Azure. L’identification des données utilisées par Microsoft Manged Desktop est stockée par Azure AD dans un emplacement géographique basé sur l’emplacement fourni par l’organisation lors de l’abonnement à des services en ligne Microsoft tels que Microsoft Apps pour entreprise et Azure. Pour plus d’informations sur l’emplacement de vos données Azure AD, voir [Azure Active Directory - Où se](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9) trouvent vos données ?

## <a name="microsoft-intune"></a>Microsoft Intune
Microsoft Intune collecte, traite et partage des données à Microsoft Manged Desktop pour prendre en charge les opérations et les services de l’entreprise. Pour [plus d’informations](/mem/intune/protect/privacy-data-collect) sur les données collectées dans Intune, voir Collecte de données dans Intune. 

Pour plus d’informations Microsoft Intune des emplacements de données, consultez [l’emplacement Microsoft 365 données client sont stockées.](/microsoft-365/enterprise/o365-data-locations) Intune respecte les sélections d’emplacements de stockage réalisées par l’administrateur pour les données client.

## <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison
Microsoft Defender pour le point de terminaison collecte et stocke des informations pour les appareils inscrits Microsoft Manged Desktop à des fins d’administration, de suivi et de rapport. Les informations collectées comprennent les données de fichier (telles que les noms de fichiers, la taille et les hages), les données de processus (processus en cours d’exécution, hèses), les données de Registre, les données de connexion réseau et les détails des périphériques (tels que les identificateurs de périphérique, les noms de périphérique et la version du système d’exploitation). Consultez [Microsoft Defender pour le stockage et](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect) la confidentialité des données des points de terminaison pour plus d’informations sur Microsoft Defender pour la collecte de données et les emplacements de stockage des points de terminaison. 

## <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise 
Applications Microsoft 365 pour les grandes entreprises collecte et partage des données avec Microsoft Manged Desktop pour s’assurer que ces applications sont à jour avec la dernière version en fonction des canaux de mise à jour prédéfincis gérés par Microsoft Manged Desktop. Consultez [Microsoft Defender pour le stockage et](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect) la confidentialité des données des points de terminaison pour plus d’informations Microsoft 365 Apps’emplacements de stockage et de collecte de données de l’utilisateur.

## <a name="major-data-change-notification"></a>Notification de modification majeure des données
Microsoft Manged Desktop suit un processus de contrôle des changements décrit dans notre infrastructure de communication de service. Nous informons les clients via Microsoft 365 centre de messages et Microsoft Manged Desktop portail d’administration des incidents de sécurité et des modifications majeures apportées au service. Les modifications apportées aux types de données recueillies et à l’endroit où elles sont stockées sont considérées comme des modifications importantes. Nous fournirons un minimum de 30 jours de notification avancée de cette modification, comme c’est la pratique standard pour Microsoft 365 produits et services. Pour plus d’informations, [voir Changements de service et communication.](/microsoft-365/managed-desktop/service-description/servicechanges)

## <a name="compliance"></a>Conformité
Microsoft Manged Desktop a subi des audits externes et obtenu un ensemble complet d’offres de conformité. Vous trouverez plus d’informations dans Microsoft Manged Desktop [conformité.](/microsoft-365/managed-desktop/intro/compliance) Les rapports d’audit peuvent [](https://aka.ms/stp)être téléchargés sur le portail d’confiance des services Microsoft, qui sert de référentiel central pour Microsoft Enterprise Online Services. (Microsoft Manged Desktop est répertorié dans ces documents sous la catégorie « Surveillance et gestion ».) 

## <a name="legal"></a>Informations juridiques
Déclaration de confidentialité microsoft aux utilisateurs finaux des produits fournis par les clients de l’organisation : la déclaration de confidentialité [Microsoft](https://privacy.microsoft.com/privacystatement) informe les utilisateurs finaux que lorsqu’ils se connectent aux produits Microsoft avec un compte de travail, a) leur organisation peut contrôler et administrer leur compte (y compris le contrôle des paramètres de confidentialité), accéder et traiter leurs données, et b) Microsoft peut collecter et traiter les données pour fournir le service à **l’organisation** et aux utilisateurs finaux.
