---
title: Confidentialité et données personnelles
description: Détaille les données collectées, stockées et utilisées par le service
keywords: RGPD, rétention, suppression, stockage, rétention, traitement, sécurité, audit
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
ms.openlocfilehash: e7c9912e3890d9b13003c7f3264490f67c4fc305
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128343"
---
# <a name="privacy"></a>Confidentialité

Microsoft Managed Desktop est un service ITaaS (IT-as-a-Service) destiné aux clients cloud d’entreprise, conçu pour que les appareils Windows des employés restent déployés et mis à jour.

Il fournit également la gestion et les opérations des services informatiques, surveille la sécurité et la réponse aux incidents, ainsi que le support utilisateur. Cet article fournit plus d’informations sur la plateforme de données et la conformité de la confidentialité pour Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Managed Desktop sources de données et l’objectif

Microsoft Managed Desktop fournit son service aux clients d’entreprise et gère correctement les appareils inscrits des clients à l’aide de données provenant de différentes sources.

Ces sources incluent Azure Active Directory, Microsoft Intune, Microsoft Windows 10 et Microsoft Defender pour point de terminaison. Ils fournissent une vue complète des appareils que Microsoft Managed Desktop gère. Le service utilise également ces services Microsoft pour permettre à Microsoft Managed Desktop de fournir des fonctionnalités ITaaS :

| Source de données | Objectif |
| ------ | ------ |
| [Microsoft Windows 10 Entreprise](/windows/windows-10/) | Gestion de l’expérience de configuration des appareils, gestion des connexions à d’autres services et support opérationnel pour les professionnels de l’informatique. |
| [Windows Update pour Entreprise](/windows/deployment/update/waas-manage-updates-wufb) | Utilise Windows 10 Entreprise données de diagnostic pour fournir des informations supplémentaires sur Windows 10 mise à jour. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Gestion des appareils et sécurisation de vos données. Les sources de données suivantes sont sous Microsoft Endpoint Manager :<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/) : Authentification et identification de tous les comptes d’utilisateur.</li><li>[Microsoft Intune](/mem/intune/) : distribution des configurations d’appareils, de la gestion des appareils et de la gestion des applications.</li><li>[Endpoint Analytics](/mem/analytics/overview) : Insights analytiques sur l’utilisation des appareils et des applications.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot) : approvisionnement et déploiement d’appareils.</li><li>[Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/) : fournit des services de sécurité tels que la surveillance de la sécurité des appareils et des données de renseignement de sécurité.</li></ul>
| [Bureau géré Microsoft](https://endpoint.microsoft.com/#home) | Données fournies par le client ou générées par le service pendant l’exécution du service. |
| [applications Microsoft 365 pour l’entreprise](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Gestion des Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Managed Desktop processus de données et stockage

Microsoft Managed Desktop s’appuie sur les données de plusieurs produits et services Microsoft pour fournir son service aux clients d’entreprise.

Pour protéger et gérer les appareils inscrits, nous traitons et copieons les données de ces services vers Microsoft Managed Desktop. Lorsque nous traitons des données, nous suivons les instructions documentées que vous fournissez, comme indiqué dans les [conditions des services en ligne](https://www.microsoft.com/licensing/product-licensing/products) et la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

Les tâches de processeur de Microsoft Managed Desktop incluent la garantie d’une confidentialité, d’une sécurité et d’une résilience appropriées. Microsoft Managed Desktop utilise des mesures supplémentaires de confidentialité et de sécurité pour garantir une gestion appropriée des données d’identification personnelles.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Managed Desktop le stockage des données et l’emplacement du personnel

Microsoft Managed Desktop stocke ses données dans les centres de données Azure du États-Unis.

Les données personnelles obtenues par Microsoft Managed Desktop et d’autres services sont nécessaires pour maintenir le service opérationnel. Si un appareil est supprimé de Microsoft Managed Desktop, nous conservons les données personnelles pendant un maximum de 30 jours. Toutefois, les données d’alerte, collectées par Microsoft Defender pour point de terminaison, sont stockées pendant 180 jours à des fins de sécurité. Pour plus d’informations sur la rétention des données, consultez [Conservation, suppression et destruction des données dans Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

Microsoft Managed Desktop équipes d’opérations d’ingénierie et d’opérations de sécurité se trouvent dans les États-Unis, en Inde et en Roumanie.

### <a name="microsoft-windows-10-diagnostic-data"></a>Données de diagnostic Microsoft Windows 10

Microsoft Managed Desktop utilise [Windows 10 données de diagnostic améliorées](/windows/privacy/windows-diagnostic-data) pour maintenir Windows sécurisé, à jour, résoudre les problèmes et apporter des améliorations aux produits.

Le paramètre de données de diagnostic amélioré inclut des informations plus détaillées sur les appareils inscrits dans Microsoft Managed Desktop et leurs paramètres, fonctionnalités et intégrité des appareils. Lorsque des données de diagnostic améliorées sont sélectionnées, les données, y compris les données de diagnostic requises, sont collectées. Pour plus d’informations, consultez [Modifications apportées à Windows collecte de données de diagnostic](/windows/privacy/changes-to-windows-diagnostic-data-collection) sur le paramètre de données de diagnostic Windows 10 et la collecte de données.

La terminologie des données de diagnostic changera dans les versions ultérieures de Windows. Microsoft Managed Desktop s’engage à traiter uniquement les données dont le service a besoin. Bien que cela signifie que le niveau de diagnostic passe à **Facultatif**, Microsoft Managed Desktop implémente les stratégies de diagnostic limitées pour affiner la collecte des données de diagnostic requise pour le service. Pour plus d’informations, consultez [Modifications apportées à Windows collecte de données de diagnostic](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop traite et stocke uniquement les données au niveau du système à partir de Windows 10 données de diagnostic facultatives provenant d’appareils inscrits, tels que la fiabilité des applications et des appareils, ainsi que des informations sur les performances. Microsoft Managed Desktop ne traite pas et ne stocke pas les données personnelles des clients, telles que l’historique des conversations et des navigateurs, la voix, le texte ou les données vocales.

Pour plus d’informations sur la collecte de données de diagnostic de Microsoft Windows 10, consultez la section [Where we store and process personal data](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) de la Déclaration de confidentialité Microsoft.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update for Business

Microsoft Windows Update for Business utilise les données des diagnostics Windows pour analyser l’état et les échecs de mise à jour. Microsoft Managed Desktop utilise ces données et les utilise pour atténuer et résoudre les problèmes afin de s’assurer que tous les appareils inscrits sont à jour en fonction d’une cadence de mise à jour prédéfinie.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

L’identification des données utilisées par Microsoft Managed Desktop est stockée par Azure Active Directory (Azure AD) dans un emplacement géographique. L’emplacement géographique est basé sur l’emplacement fourni par l’organisation lors de l’abonnement à Microsoft services en ligne, tel que Microsoft Apps pour Enterprise et Azure. Pour plus d’informations sur l’emplacement de vos données Azure AD, consultez [Azure Active Directory - Où se trouvent vos données ?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune collecte, traite et partage des données à Microsoft Managed Desktop pour prendre en charge les opérations et services métier. Pour plus d’informations sur les données collectées dans Intune, consultez [Collecte de données dans Intune](/mem/intune/protect/privacy-data-collect)

Pour plus d’informations sur Microsoft Intune emplacements de données, consultez [l’emplacement où sont stockées vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Intune respecte les sélections d’emplacement de stockage effectuées par l’administrateur pour les données client.

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison collecte et stocke des informations pour les appareils inscrits dans Microsoft Managed Desktop à des fins d’administration, de suivi et de création de rapports. Les informations collectées sont les suivantes :

- Données de fichier (telles que les noms de fichiers, la taille et les hachages)
- Données de processus (processus en cours d’exécution, hachages)
- Données de Registre
- Données de connexion réseau
- Détails de l’appareil (tels que les identificateurs d’appareil, les noms d’appareils et la version du système d’exploitation)

Pour plus d’informations sur la collecte de données et les emplacements de stockage de Microsoft Defender pour point de terminaison, consultez [Microsoft Defender pour point de terminaison stockage et confidentialité des données](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

Microsoft 365 Apps pour Enterprise collecte et partage des données avec Microsoft Managed Desktop pour vous assurer que ces applications sont à jour avec la dernière version. Ces mises à jour sont basées sur des canaux de mise à jour prédéfinis gérés par Microsoft Managed Desktop. Pour plus d’informations sur la collecte de données et les emplacements de stockage de Microsoft 365 Apps, consultez [Microsoft Defender pour point de terminaison stockage et confidentialité des données](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Notification majeure de modification des données

Microsoft Managed Desktop suit un processus de contrôle des modifications comme indiqué dans notre infrastructure de communication de service.

Nous informons les clients via le centre de messages Microsoft 365 et Microsoft Managed Desktop portail d’administration des incidents de sécurité et des modifications majeures apportées au service.

Les modifications apportées aux types de données collectées et à l’emplacement où elles sont stockées sont considérées comme des modifications matérielles. Nous fournirons un minimum de 30 jours de notification avancée de cette modification, comme c’est la pratique standard pour Microsoft 365 produits et services. Pour plus d’informations, consultez [modifications du service et communication](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Conformité

Microsoft Managed Desktop a fait l’objet d’audits externes et a obtenu un ensemble complet d’offres de conformité. Vous trouverez plus d’informations dans [Conformité](/microsoft-365/managed-desktop/intro/compliance). Les rapports d’audit sont disponibles en téléchargement sur le [portail Microsoft Service Trust](https://aka.ms/stp), qui sert de référentiel central pour Microsoft Enterprise Online Services. Microsoft Managed Desktop est répertoriée dans ces documents sous la catégorie « Surveillance et gestion ».

### <a name="data-subject-requests"></a>Demandes de la personne concernée

Microsoft Managed Desktop suit les réglementations en matière de confidentialité du RGPD et du CCPA, qui accordent aux personnes concernées des droits spécifiques sur leurs données personnelles.

Ces droits sont les suivants :

- Obtention de copies de données personnelles
- Demande de corrections
- Restriction du traitement de celui-ci
- Suppression
- Réception dans un format électronique afin qu’il puisse être déplacé vers un autre contrôleur.

Pour plus d’informations générales sur les demandes de personnes concernées(DSR), consultez [demandes de personnes concernées et RGPD et CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Pour effectuer des demandes de personnes concernées sur les données collectées par le système de gestion de cas Microsoft Managed Desktop, consultez les demandes de personnes concernées suivantes :

| Demandes de la personne concernée | Description |
| ------ | ------ |
| Données provenant d’alertes Microsoft Defender pour point de terminaison | Votre administrateur de sécurité peut demander la suppression ou l’extraction de données personnelles liées à Microsoft Defender pour point de terminaison alertes en envoyant une demande de rapport dans le [portail d’administration](https://aka.ms/memadmin). <br><br> Fournissez les informations suivantes : <br><ul><li>Type de demande : Modifier la demande</li><li>Catégorie : Sécurité</li><li>Sous-catégorie : Autre</li><li>Description : Fournissez les noms d’appareils appropriés.</li></ul> |
| Données des demandes de support Microsoft Managed Desktop | Votre administrateur informatique peut demander la suppression ou l’extraction de demandes de support liées aux données personnelles en envoyant une demande de rapport sur le [portail d’administration](https://aka.ms/memadmin). <br><br> Fournissez les informations suivantes : <ul><li>Type de demande : Modifier la demande</li><li>Catégorie : Sécurité</li><li>Sous-catégorie : Autre</li><li>Description : Indiquez les noms d’appareils ou d’utilisateurs appropriés.</li></ul>

Pour obtenir des DSR d’autres produits liés au service, consultez les articles suivants :

- Windows [données de diagnostic](/compliance/regulatory/gdpr-dsr-windows)
- [Données microsoft Intune](/compliance/regulatory/gdpr-dsr-intune)
- Données Azure Active [Directory](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Informations juridiques

**Avis de confidentialité de Microsoft aux utilisateurs finaux des produits fournis par les clients organisationnels** :

La [Déclaration de confidentialité Microsoft](https://privacy.microsoft.com/privacystatement) informe les utilisateurs finaux que lorsqu’ils se connectent à des produits Microsoft avec un compte professionnel :

1. Leur organisation peut contrôler et administrer leur compte (y compris le contrôle des paramètres liés à la confidentialité), ainsi que l’accès et le traitement de leurs données.
1. Microsoft peut collecter et traiter les données pour fournir le service à l’organisation et aux utilisateurs finaux.
