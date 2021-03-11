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
ms.openlocfilehash: e98d42e79ac270e6ccce46e88e3b8ff00f8bfc0a
ms.sourcegitcommit: 88ab08c0fa1acbc9e066009e131b9f2b0d506c64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "50712305"
---
# <a name="privacy-and-personal-data"></a>Confidentialité et données personnelles

Les utilisateurs peuvent recevoir, transmettre et stocker des données sur des appareils gérés par Bureau géré Microsoft. Ils font confiance au fait que la confidentialité des données est protégée et utilisée uniquement d’une manière cohérente avec leurs attentes. Cet article explique comment Bureau géré Microsoft collecte, stocke, conserve, traite, sécurisation, partage, audite et exporte des données personnelles. Vous découvrirez également comment un administrateur peut afficher, corriger et supprimer des données personnelles.

Bureau géré Microsoft n’utilise pas les données personnelles collectées dans le cadre de la fourniture du service à des fins de profilage, de publicité ou de marketing.

## <a name="data-collection-of-microsoft-managed-desktop"></a>Collecte de données du Bureau géré Microsoft

Lorsque les utilisateurs inscrivent des appareils d’entreprise dans bureau géré Microsoft, la collecte de données est gérée (sur la couche technique) à l’aide de Windows et Microsoft Intune. Ces sources collectent des données personnelles sur les appareils des utilisateurs, telles que les noms des appareils du Bureau géré Microsoft, afin de pouvoir identifier l’appareil à gérer et à fournir avec les expériences Bureau géré Microsoft.

Bureau géré Microsoft ne collecte pas les données par lui-même pour fournir son service (à l’exception des informations [de contact de l’administrateur informatique).](#it-admin-contact-information) Au lieu de cela, Bureau géré Microsoft réutilise les données que d’autres sources, telles que Windows et Microsoft Intune, ont déjà collectées. Bureau géré Microsoft utilise les données collectées par ces services à partir d’appareils inscrits :

- Les données de diagnostic Windows provenant d’appareils gérés par Le Bureau géré Microsoft sont envoyées aux magasins de données de diagnostic Windows de Microsoft.
- Bureau géré Microsoft utilise [la gestion moderne](https://docs.microsoft.com/learn/modules/introduction-to-modern-management-in-microsoft-365/) pour gérer les appareils inscrits. Dans le cadre de la « gestion moderne », les appareils doivent être inscrits dans Azure Active Directory du client.
- Pour distribuer sa configuration hautement optimisée et sécurisée aux appareils inscrits, Bureau géré Microsoft utilise Microsoft Intune.
- Bureau géré Microsoft utilise les données d’intelligence de sécurité de Microsoft Defender Advanced Thread Protection pour les clients qui utilisent ce service.

## <a name="data-storage-and-sources-in-microsoft-managed-desktop"></a>Stockage de données et sources dans le Bureau géré Microsoft

Une fois que Microsoft Managed Desktop a obtient les données, il doit fournir son service, son stockage et le traitement de ces données comme suit :

### <a name="storing-data-storage-location-and-data-retention"></a>Stockage des données, emplacement de stockage et rétention des données

Bureau géré Microsoft stocke ses données dans un ou plusieurs des services de stockage Microsoft suivants :

- Azure SQL
- Stockage Azure
- Dynamics 365

Bureau géré Microsoft stocke ses données aux États-Unis. Les données personnelles sont conservées par Bureau géré Microsoft pendant un maximum de 30 jours, à l’exception des données d’alerte pour les appareils bureau géré Microsoft collectés par Microsoft Defender pour endpoint. Les données d’alerte réelles (qui peuvent inclure des données personnelles) sont stockées pendant 180 jours. Les données d’alerte avec des données personnelles supprimées sont stockées pendant deux ans au maximum. Conformément au Règlement général sur la protection des données (R GDPR) et au CCPA (California Consumer Privacy Act), Le Bureau géré Microsoft honore les droits des personnes ayant des données pour toutes les données personnelles stockées dans les données d’alerte.

### <a name="staff-location"></a>Emplacement du personnel

Les équipes des opérations de bureau géré Microsoft et des opérations de sécurité sont situées aux États-Unis et en Inde.

## <a name="data-usage-of-microsoft-managed-desktop"></a>Utilisation des données du Bureau géré Microsoft

Bureau géré Microsoft utilise les données ci-après :


| Sources de données |Utilisation avec bureau géré Microsoft  |
|---------|---------|
|Données Azure Active Directory     | Utilisé dans les rapports créés pour les administrateurs clients, qui sont disponibles dans le portail d’administration du bureau géré Microsoft.        |
|Données Intune     | Utilisé dans les rapports créés pour les administrateurs clients, qui sont disponibles dans le portail d’administration du bureau géré Microsoft.        |
|Microsoft Defender pour point de terminaison     |  Utilisé pour traiter les menaces de sécurité détectées sur les appareils inscrits par le Centre d’opérations de sécurité (SOC) de Bureau géré Microsoft.  |
|Données de diagnostic Windows     |Permet de déterminer l’état de mise à jour des appareils gérés et de fournir et d’améliorer l’offre ITaaS (It-as-a-Service) de Bureau géré Microsoft.         |
|Données de contact de l’administrateur     | Utilisé par bureau géré Microsoft pour communiquer avec les administrateurs clients.        |


### <a name="entities-processed-by-microsoft-managed-desktop"></a>Entités traitées par bureau géré Microsoft

Bureau géré Microsoft traite ces entités pour fournir le service :

- Données d’appareil
- Paramètres de sécurité de l’appareil
- Système d’exploitation et matériel de l’appareil
- Informations agrégées sur l’état de l’appareil
- Informations de diagnostic d’appareil
- Données client
- Ressources Azure Active Directory
- Données de stratégie et de configuration
- Métadonnées et données d’alerte de Microsoft Defender for Endpoint
- Données de diagnostic Windows
- Données d’utilisation des produits et services

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Les données d’identité utilisées par Bureau géré Microsoft sont stockées par Azure Active Directory dans un emplacement géographique basé sur l’adresse fournie par l’organisation lors de l’abonnement à un service en ligne Microsoft tel qu’Office 365 ou Azure. Consultez [Microsoft Azure — Où sont mes](http://azuredatacentermap.azurewebsites.net/) données client ? pour obtenir une carte montrant les centres de données pour Azure Active Directory.

Pour plus d’informations sur les régions qu’Azure utilise pour le stockage de données, voir [Azure Active Directory – Où se](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)trouvent vos données .

### <a name="microsoft-intune"></a>Microsoft Intune

Les données Intune peuvent être stockées dans différentes régions, telles que l’Europe du Nord (Irlande) et l’Europe de l’Ouest (Pays-Bas). Votre administrateur informatique crée un compte client et choisit le pays où les données seront stockées lorsqu’ils s’inscrivent initialement dans les services Intune. Pour obtenir la liste des emplacements de centres de données utilisés par Intune, consultez [Microsoft Intune](http://intunedatacentermap.azurewebsites.net/)— Où sont mes données client ? . Pour plus d’informations sur le stockage et l’utilisation des données par Intune, voir [Collecte de données dans Intune.](https://docs.microsoft.com/intune/privacy-data-collect)

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison

Les données de Microsoft Defender pour point de terminaison peuvent être stockées dans plusieurs régions différentes. Pour cette raison, Defender pour point de terminaison fonctionne dans les centres de données Microsoft Azure dans l’Union européenne, au Royaume-Uni et aux États-Unis, comme indiqué dans [Microsoft Defender pour le](http://intunedatacentermap.azurewebsites.net/)point de terminaison — Emplacements de stockage de données . Pour plus d’informations sur le stockage et l’utilisation des données par Defender pour le point de terminaison, voir quelles données [Microsoft Defender for Endpoint collecte-t-il ?](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy#what-data-does-microsoft-defender-atp-collect)

### <a name="windows-10"></a>Windows 10

Comme indiqué dans la Déclaration de confidentialité [Microsoft,](https://privacy.microsoft.com/privacystatement)« les données personnelles collectées par Microsoft peuvent être stockées et traitées dans votre région, aux États-Unis et dans tout autre pays où Microsoft ou ses filiales, filiales ou fournisseurs de services exploitent des installations. [...] En règle générale, l’emplacement de stockage principal se trouve dans la région du client ou aux États-Unis, souvent avec une sauvegarde vers un centre de données dans une autre région. Les emplacements de stockage sont choisis pour fonctionner efficacement, améliorer les performances et créer des redondances afin de protéger les données en cas de panne ou d’un autre problème. Nous prenons des mesures pour nous assurer que les données que nous collectons dans le cadre de cette déclaration de confidentialité sont traitées conformément aux dispositions de cette déclaration et aux exigences de la loi applicable où que se trouvent les données. »

Pour plus d’informations sur la collecte de données de diagnostic de Windows 10, voir la [section](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) « Où stocker et traiter les données personnelles » de la déclaration de confidentialité Microsoft.

## <a name="data-access-protection"></a>Protection de l’accès aux données

L’accès direct aux magasins de données internes du Bureau géré Microsoft est restreint de plusieurs manières :

- Elle nécessite une approbation de niveau de tête d’ingénierie.
- Il est à la fois audité et limité dans le temps.
- Il nécessite l’utilisation d’une station de travail hautement sécurisée et restreinte.
- Toutes les données sont chiffrées pendant qu’elles sont stockées.
- Il n’existe aucun accès permanent.
- L’accès au portail de gestion interne du Bureau géré Microsoft nécessite une station de travail hautement sécurisée et restreinte.

## <a name="processing-personal-data-in-a-compliant-manner"></a>Traitement des données personnelles de manière conforme
Bureau géré Microsoft traite les données personnelles avec des systèmes certifiés ISO. Pour plus d’informations, voir [Conformité.](../intro/compliance.md)

## <a name="profiling-and-marketing"></a>Profilage et marketing

Bureau géré Microsoft n’utilise pas les données personnelles collectées dans le cadre de la fourniture du service à des fins de profilage, de publicité ou de marketing.

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes des personnes concernées pour le RGPD et le CCPA

Le Règlement général sur la protection des données [(R GDPR)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) de l’Union européenne accorde des droits aux personnes (connues dans la réglementation sous le nom de personnes responsables des données) pour gérer les données personnelles collectées par un employeur ou tout autre type d’agence ou d’organisation (appelé contrôleur de données ou contrôleur uniquement). Dans le RGPD, les données personnelles sont définies de façon générale comme toute donnée relative à une personne physique identifiée ou identifiable. Le RGPD confère aux personnes concernées des droits précis sur leurs données personnelles ; ces droits vous donnent la possibilité d’obtenir des copies de ces données personnelles, de les modifier, d’en limiter le traitement, de les supprimer ou de les recevoir dans un format électronique afin de pouvoir les transférer à un autre responsable du traitement. Une demande officielle d’une personne concernée à un responsable du traitement pour effectuer une action sur ses données personnelles est appelée demande de droits de la personne concernée ou DPC dans le présent document.

De même, le CCPA fournit des droits de confidentialité et des obligations aux consommateurs de la Californie, y compris des droits similaires aux droits des personnes morales du R GDPR, tels que le droit de supprimer, d’accéder et de recevoir (portabilité) leurs informations personnelles. Le CCPA prévoit également certaines divulgations, des protections contre la discrimination lors du choix de l’exercice des droits et des exigences de « désa opt-out/opt-in » pour certains transferts de données classés comme « ventes ». Les ventes sont largement définies pour inclure le partage de données à des fins importantes. Pour plus d’informations sur le CCPA, voir le [California Consumer Privacy Act](https://docs.microsoft.com/microsoft-365/compliance/offering-ccpa?view=o365-worldwide) et le [Forum aux questions California Consumer Privacy Act](https://docs.microsoft.com/microsoft-365/compliance/ccpa-faq?view=o365-worldwide).

La section suivante explique comment Bureau géré Microsoft permet aux contrôleurs de rechercher, d’accéder aux données personnelles ou aux informations personnelles utilisées par Bureau géré Microsoft et d’agir sur ces données.

> [!NOTE]
> Si vous recherchez des informations générales sur le R GDPR, consultez la [section R GDPR](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted) du portail d’confiance des services.

### <a name="it-admin-contact-information"></a>Informations de contact de l’administrateur informatique

Un administrateur client peut afficher, corriger et supprimer ses propres données personnelles (telles que ses propres informations de contact) directement dans la section Contact d’administration du portail Bureau géré Microsoft.

## <a name="microsoft-defender-for-endpoint-alert-data"></a>Données d’alerte microsoft Defender pour point de terminaison

Les administrateurs de sécurité peuvent demander l’extraction ou la suppression de données personnelles liées aux alertes microsoft Defender pour les points de terminaison sur un appareil géré par bureau géré Microsoft dans leur environnement. L’administrateur de la sécurité doit se connecter au portail d’administration du bureau géré Microsoft [et](https://aka.ms/memadmin) envoyer une demande de support. Sélectionnez  le **type** de  demande de support de demande de **modification,** catégorie de sécurité **et** sous-catégorie d’autres **,** puis indiquez les noms d’appareils pertinents dans la description, ainsi que votre demande d’extraction ou de suppression de données.

### <a name="user-related-personal-data"></a>Données personnelles liées à l’utilisateur

En dehors de cela, Bureau géré Microsoft ne collecte pas les données personnelles par lui-même. Au lieu de cela, il s’appuie sur les données personnelles collectées par d’autres Microsoft Enterprise Online Services et utilise ces données. Les administrateurs informatiques qui souhaitent répondre aux demandes de leurs utilisateurs pour afficher, corriger et supprimer leurs données personnelles peuvent utiliser les fonctionnalités respectives des services sous-jacents dont dépend Microsoft Managed Desktop. Si vous êtes intéressé par l’affichage ou la suppression des données personnelles utilisées par ces services, consultez d’abord les demandes des personnes soumises aux données pour Azure concernant l’article [R GDPR.](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure)

En outre, utilisez les instructions suivantes pour exercer des DSR pour les services dont Dépend Microsoft Managed Desktop pour la collecte de données personnelles :

- [Azure Active Directory](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-azure?view=o365-worldwide)
- [Microsoft Intune](https://docs.microsoft.com/microsoft-365/compliance/gdpr-dsr-intune?view=o365-worldwide)
- [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)
- [Windows 10](https://docs.microsoft.com/windows/privacy/windows-10-and-privacy-compliance)
