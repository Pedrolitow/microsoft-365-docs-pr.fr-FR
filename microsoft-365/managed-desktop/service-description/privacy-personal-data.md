---
title: Confidentialité et données personnelles
description: Détails des données collectées, stockées et utilisées par le service
keywords: RGPD, rétention, suppression, stockage, rétention, traitement, sécurité, audit
ms.service: m365-md
ms.sitesec: library
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.topic: article
ms.localizationpriority: normal
ms.openlocfilehash: e7eb3eaa6961993f8c77645c8d6760e6701817e2
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547937"
---
# <a name="privacy-and-personal-data"></a>Confidentialité et données personnelles

Les utilisateurs peuvent recevoir, transmettre et stocker des données sur des appareils gérés par le bureau géré Microsoft. Ils font confiance à la confidentialité de la confidentialité des données et à leur utilisation uniquement de manière cohérente avec leurs attentes. Cet article explique comment Microsoft Managed Desktop recueille, stocke, conserve, traite, sécurise, partage, audite et exporte les données personnelles. Vous découvrirez également comment un administrateur peut afficher, corriger et supprimer des données personnelles.

Microsoft Managed Desktop n’utilise pas les données personnelles collectées dans le cadre de la fourniture du service de création de profils, de publicité ou de marketing.

## <a name="data-collection-of-microsoft-managed-desktop"></a>Collecte de données du bureau géré Microsoft

Lorsque les utilisateurs inscrivent des appareils d’entreprise dans Microsoft Managed Desktop, la collecte de données est gérée sur la couche technique, à l’aide de Windows et Microsoft Intune. Ces sources recueillent des données personnelles sur les appareils des utilisateurs, telles que les noms de périphérique pour que le bureau géré Microsoft puisse identifier l’appareil à gérer et fourni avec l’expérience de bureau géré Microsoft.

Microsoft Managed Desktop ne collecte pas les données en lui-même de fournir son service (à l’exception des informations de contact de l' [administrateur informatique](#it-admin-contact-information). Au lieu de cela, le bureau géré Microsoft réutilise les données que d’autres sources, telles que Windows et Microsoft Intune, ont déjà recueillies. Microsoft Managed Desktop utilise des données collectées par les services suivants :

- Les données de diagnostic Windows provenant d’appareils gérés par Microsoft Managed Desktop sont envoyées aux magasins de données de diagnostic Windows de Microsoft.
- Microsoft Managed Desktop utilise une [gestion moderne](https://docs.microsoft.com/learn/modules/introduction-to-modern-management-in-microsoft-365/) pour la gestion des appareils. Dans ce cas, les appareils doivent être inscrit dans l’Azure Active Directory du client.
- Pour distribuer sa configuration hautement optimisée et sécurisée aux périphériques, Microsoft Managed Desktop utilise Microsoft Intune.
- Microsoft Managed Desktop utilise les données d’aide à la sécurité de Microsoft Defender Advanced threads pour les clients qui utilisent ce service.

## <a name="data-storage-and-sources-in-microsoft-managed-desktop"></a>Stockage et sources de données dans le bureau géré Microsoft

Une fois que Microsoft Managed Desktop obtient les données, il doit fournir le service, le stockage et le traitement de ces données comme suit :

### <a name="storing-data-storage-location-and-data-retention"></a>Stockage des données, de l’emplacement de stockage et de la rétention des données

Le bureau géré Microsoft stocke ses données dans un ou plusieurs des services de stockage Microsoft suivants :

- Azure SQL
- Stockage Azure

Le bureau géré Microsoft stocke ses données aux États-Unis. Les données personnelles sont conservées par Microsoft Managed Desktop pendant une période de 30 jours maximum.

## <a name="data-usage-of-microsoft-managed-desktop"></a>Utilisation des données du bureau géré Microsoft

Microsoft Managed Desktop utilise les données suivantes :


| Sources de données |Utilisation avec le bureau géré Microsoft  |
|---------|---------|
|Données Azure Active Directory     | Utilisé dans les rapports créés pour les administrateurs de clients, qui sont disponibles dans le portail d’administration de bureau géré Microsoft.        |
|Données Intune     | Utilisé dans les rapports créés pour les administrateurs de clients, qui sont disponibles dans le portail d’administration de bureau géré Microsoft.        |
|Microsoft Defender – Protection avancée contre les menaces (ATP)     |  Utilisé pour l’adressage des menaces de sécurité détectées sur les périphériques mis en service par le centre d’opérations de sécurité de bureau géré Microsoft.  |
|Données de diagnostic Windows     |Permet de déterminer l’état de mise à jour des appareils gérés, ainsi que de fournir et d’améliorer l’offre de service informatique-As-a-service (ITaaS) de Microsoft Managed Desktop.         |
|Données de contact d’administration     | Utilisé par le bureau géré Microsoft pour communiquer avec les administrateurs de client.        |


### <a name="entities-processed-by-microsoft-managed-desktop"></a>Entités traitées par Microsoft Managed Desktop

Le bureau géré Microsoft traite ces entités pour fournir le service :

- Données de l’appareil
- Paramètres de sécurité de l’appareil
- Système d’exploitation et matériel de l’appareil
- Informations agrégées sur l’intégrité de l’appareil
- Informations de diagnostic du périphérique
- Données client
- Ressources Azure Active Directory
- Données de stratégie et de configuration
- Métadonnées ATP de Microsoft Defender
- Données de diagnostic Windows
- Données d’utilisation des produits et des services

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Les données d’identité utilisées par Microsoft Managed Desktop sont stockées par Azure Active Directory à un emplacement géographique en fonction de l’adresse fournie par l’Organisation lors de l’abonnement à un service Microsoft Online tel qu’Office 365 ou Azure. Voir [Microsoft Azure, où se trouvent les données de mon client ?](http://azuredatacentermap.azurewebsites.net/) pour une carte montrant les centres de données pour Azure Active Directory.

Pour plus d’informations sur les régions utilisées par Azure pour le stockage de données, reportez-vous à la rubrique [Azure Active Directory – où se trouve vos données](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9).

### <a name="microsoft-intune"></a>Microsoft Intune

Les données Intune peuvent être stockées dans quelques régions différentes, telles que Europe du Nord (Irlande) et Europe (Pays-Bas). Votre administrateur informatique crée un compte client et choisit le pays où les données seront stockées lors de l’inscription initiale dans les services Intune. Pour obtenir la liste des emplacements de centre de données utilisés par Intune, voir [Microsoft Intune, où se trouvent mes données client ?](http://intunedatacentermap.azurewebsites.net/). Pour plus d’informations sur le stockage et l’utilisation des données par Intune, consultez la rubrique [collecte de données dans Intune](https://docs.microsoft.com/intune/privacy-data-collect).

### <a name="microsoft-defender-advanced-threat-protection"></a>Microsoft Defender – Protection avancée contre les menaces

Les données de protection avancée contre les menaces Microsoft Defender peuvent être stockées dans quelques régions différentes. Pour cette raison, Microsoft Defender ATP fonctionne dans les centres de données Microsoft Azure de l’Union européenne, au Royaume-Uni et aux États-Unis, comme indiqué à l' [emplacement de stockage des données Microsoft Defender ATP](http://intunedatacentermap.azurewebsites.net/). Pour plus d’informations sur le stockage et l’utilisation des données par Microsoft Defender ATP, voir [Quelles sont les données collectées par Microsoft Defender ATP ?](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy#what-data-does-microsoft-defender-atp-collect)

### <a name="windows-10"></a>Windows 10

Comme indiqué dans la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement), «les données personnelles collectées par Microsoft peuvent être stockées et traitées dans votre région, aux États-Unis et dans tout autre pays où Microsoft ou ses affiliés, filiales ou prestataires de services fonctionnent. [...] En règle générale, l’emplacement de stockage principal se trouve dans la région du client ou aux États-Unis, souvent avec une sauvegarde dans un centre de contenu dans une autre région. Le ou les emplacements de stockage sont choisis pour fonctionner efficacement, pour améliorer les performances et pour créer des redondances afin de protéger les données en cas de panne ou d’un autre problème. Nous faisons en sorte que les données collectées dans le cadre de la présente déclaration de confidentialité soient traitées conformément aux dispositions de cette déclaration et aux exigences de la loi applicable où les données sont situées. "

Pour plus d’informations sur la collecte de données de diagnostic de Windows 10, consultez la section [« emplacement de stockage et de traitement des données personnelles »](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) de la déclaration de confidentialité de Microsoft.

## <a name="data-access-protection"></a>Protection de l’accès aux données

L’accès direct aux magasins de données internes du bureau géré par Microsoft est restreint de plusieurs façons :

- Elle requiert une approbation au niveau du responsable du service technique.
- Elle est à la fois auditée et limitée dans le temps.
- Elle nécessite l’utilisation d’une station de travail hautement sécurisée et restreinte.
- Toutes les données sont chiffrées lorsqu’elles sont stockées.
- Il n’y a pas d’accès permanent.
- L’accès au portail de gestion interne de Microsoft Managed Desktop nécessite une station de travail hautement sécurisée et restreinte.

## <a name="processing-personal-data-in-a-compliant-manner"></a>Traitement des données personnelles de manière conforme
Microsoft Managed Desktop traite les données personnelles avec des systèmes certifiés ISO. Pour plus d’informations, consultez [la rubrique conformité](../intro/compliance.md).

## <a name="profiling-and-marketing"></a>Profilage et marketing

Microsoft Managed Desktop n’utilise pas les données personnelles collectées dans le cadre de la fourniture du service de création de profils, de publicité ou de marketing.

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes des personnes concernées pour le RGPD et le CCPA

Le [Règlement général sur la protection des données (RGPD)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) de l’Union européenne accorde des droits aux personnes (répertoriées dans le règlement en tant que personnes concernées par les données) afin de gérer les données personnelles collectées par un employeur ou un autre type d’agence ou d’organisation (appelé contrôleur de données ou simplement contrôleur). Dans le RGPD, les données personnelles sont définies de façon générale comme toute donnée relative à une personne physique identifiée ou identifiable. Le RGPD confère aux personnes concernées des droits précis sur leurs données personnelles ; ces droits vous donnent la possibilité d’obtenir des copies de ces données personnelles, de les modifier, d’en limiter le traitement, de les supprimer ou de les recevoir dans un format électronique afin de pouvoir les transférer à un autre responsable du traitement. Une demande officielle d’une personne concernée à un responsable du traitement pour effectuer une action sur ses données personnelles est appelée demande de droits de la personne concernée ou DPC dans le présent document.

De la même façon, le California Consumer Act (CCPA) fournit des droits de confidentialité et des obligations aux consommateurs de la Californie, notamment des droits similaires aux droits des personnes concernées par RGPD, tels que le droit de supprimer, d’accéder et de recevoir (portabilité) leurs informations personnelles. Le CCPA fournit également des informations de divulgation, des protections contre la discrimination lors de l’élection de droits d’exercice, et des exigences de « refus d’adhésion » pour certains transferts de données classées comme « ventes ». Les ventes sont largement définies pour inclure le partage de données à des fins importantes. Pour plus d’informations sur le CCPA, voir le [California Consumer Privacy Act](https://docs.microsoft.com/microsoft-365/compliance/offering-ccpa?view=o365-worldwide) et le [Forum aux questions California Consumer Privacy Act](https://docs.microsoft.com/microsoft-365/compliance/ccpa-faq?view=o365-worldwide).

La section suivante explique comment Microsoft Managed Desktop aide les contrôleurs à rechercher, à accéder et à agir sur des données personnelles ou des informations personnelles utilisées par le bureau géré Microsoft.

> [!NOTE]
> Si vous recherchez des informations générales sur le RGPD, consultez la [section RGPD](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) du portail d’approbation de services.

### <a name="it-admin-contact-information"></a>Informations de contact de l’administrateur informatique

Un administrateur client peut afficher, corriger et supprimer ses données personnelles directement dans la section contact d’administration du portail de bureau géré Microsoft.

### <a name="user-related-personal-data"></a>Données personnelles liées à l’utilisateur

À part cela, Microsoft Managed Desktop ne collecte pas de données personnelles de sa propre façon. Au lieu de cela, il s’appuie sur et utilise des données personnelles collectées par d’autres services Microsoft Enterprise online. Les administrateurs informatiques qui cherchent à répondre à leurs demandes d’affichage, de correction et de suppression de leurs données personnelles peuvent utiliser les fonctionnalités respectives des services sous-jacents dont dépend Microsoft le bureau géré par Microsoft. Si vous souhaitez afficher ou supprimer des données personnelles utilisées par ces services, consultez First the [Azure Data subject requests for the RGPD](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure) article.

Par ailleurs, utilisez les instructions suivantes pour exercer DSR pour les services que Microsoft Managed Desktop dépend de la collecte de données personnelles :

- [Azure Active Directory](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure?view=o365-worldwide)
- [Microsoft Intune](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-intune?view=o365-worldwide)
- [Microsoft Defender - PACM](https:/docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
- [Windows 10](https://docs.microsoft.com/windows/privacy/windows-10-and-privacy-compliance)
