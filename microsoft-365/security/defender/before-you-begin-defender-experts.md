---
title: Exigences clés en matière d’infrastructure avant l’inscription au service Microsoft Defender Experts for Hunting
ms.reviewer: ''
description: Cette section décrit les principales exigences d’infrastructure que vous devez respecter et les informations importantes sur l’accès aux données et la conformité
keywords: service de chasse aux menaces managée, repérage de menaces managée, service de détection et de réponse managée (MDR), MTE, Spécialistes des menaces Microsoft, MTE-TAN, notification d’experts defender, notification d’attaque ciblée, Microsoft Defender experts pour la chasse, la chasse aux menaces et l’analyse.
search.product: Windows 10
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365initiative-defender-endpoint
- tier1
ms.topic: conceptual
search.appverid: met150
ms.openlocfilehash: 24518a28165b18c3afe26fff397095178252ad95
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68062077"
---
# <a name="before-you-begin-using-defender-experts-for-hunting"></a>Avant de commencer à utiliser Defender Experts pour la chasse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Ce document décrit les principales exigences d’infrastructure que vous devez respecter et les informations importantes sur l’accès aux données et la conformité que vous devez connaître avant de vous inscrire au service Microsoft Defender Experts for Hunting. Microsoft comprend que les clients qui utilisent nos services managés nous confient leur ressource la plus précieux, leurs données.

## <a name="check-if-your-environment-meets-licensing-and-access-prerequisites"></a>Vérifier si votre environnement répond aux conditions préalables de licence et d’accès

Microsoft Defender Experts for Hunting est un service distinct de vos produits Defender existants. Avant de vous inscrire à ce service, assurez-vous que vous disposez de la licence et de l’accès nécessaires. 

### <a name="eligibility-and-licensing"></a>Éligibilité et licence

Les clients Defender Experts for Hunting se verront attribuer deux crédits d’experts à la demande le premier de chaque mois, qui peuvent être utilisés pour soumettre des questions. Les crédits inutilisés expirent 90 jours à compter de la date d’affectation ou à la fin de la durée de l’abonnement, selon la valeur la plus courte.

Pour plus d’informations sur les termes des licences commerciales de Microsoft, visitez [cette page](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).

### <a name="access-requirements"></a>Condition d’accès

Tout le monde de votre organisation peut remplir le formulaire d’intérêt client pour Microsoft Defender service Experts for Hunting. Toutefois, vous devez collaborer avec votre responsable commercial pour transiger la référence SKU. Vous pouvez avoir besoin de certains rôles et autorisations pour accéder pleinement aux fonctionnalités du service. Pour plus d’informations, [reportez-vous aux rôles personnalisés dans le contrôle d’accès en fonction du rôle pour Microsoft 365 Defender](custom-roles.md).

## <a name="understand-the-services-availability-and-data-access-requirements"></a>Comprendre les exigences en matière de disponibilité et d’accès aux données du service

Defender Experts for Hunting est un service de chasse aux menaces managé qui recherche de manière proactive les menaces entre les points de terminaison, les e-mails, les identités et les applications cloud. Pour effectuer la chasse en votre nom, les experts Microsoft ont besoin d’accéder à vos Microsoft 365 Defender données de chasse avancées. L’inscription à ce service signifie que vous accordez aux experts Microsoft l’autorisation d’accéder aux données.

Les sections suivantes énumèrent des informations supplémentaires sur l’utilisation, la conformité et la disponibilité des données du service. Pour plus d’informations sur l’engagement de Microsoft en matière de valorisation et de protection de vos données, visitez le [Centre](https://aka.ms/trustcenter-dex4hunting) de gestion de la confidentialité > faites défiler jusqu’à **Des produits et services** >  supplémentaires **managed security services** >  [**Microsoft Defender Expert for Hunting**](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE51fRH).

### <a name="data-collection-usage-and-retention"></a>Collecte, utilisation et rétention des données

Toutes les données utilisées pour la chasse des services Defender existants continueront de résider dans l’emplacement de stockage de service Microsoft 365 Defender d’origine du client. [En savoir plus](../../enterprise/o365-data-locations.md)

Les données opérationnelles Defender Experts for Hunting, telles que les tickets de cas et les notes d’analyste, sont générées et stockées dans un centre de données Microsoft dans la région des États-Unis pour la longueur du service, quel que soit l’emplacement de stockage du service Microsoft 365 Defender. Les données générées pour le tableau de bord de création de rapports sont stockées dans l’emplacement de stockage de service Microsoft 365 Defender du client. Les données de création de rapports et les données opérationnelles sont conservées pendant une période de grâce d’au moins 90 jours après qu’un client a quitté le service.

Les experts Microsoft recherchent [des journaux de chasse avancés](../../security/defender/advanced-hunting-schema-tables.md) dans Microsoft 365 Defender tables de chasse avancées. Les données de ces tables dépendent de l’ensemble des services Defender pour lequel le client est activé (par exemple, Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour Identity, Microsoft Defender for Cloud Apps et Azure Active Directory). Les experts utilisent également un grand ensemble de données internes de renseignement sur les menaces pour informer leur repérage et leur automatisation.

### <a name="security-and-compliance"></a>Sécurité et conformité

Lorsque vous achetez et effectuez l’intégration à Defender Experts for Hunting, vous accordez l’autorisation aux experts Microsoft d’accéder à vos données de chasse avancées.

Ce service a été développé conformément aux normes de sécurité et de confidentialité existantes et travaille à l’élaboration de plusieurs certifications, notamment ISO 27001 et ISO 27018.

### <a name="availability"></a>Disponibilité

Ce service est disponible dans le monde entier pour les clients dans nos clouds publics commerciaux. Il n’est actuellement pas disponible pour les clients dans les clouds gouvernementaux et souverains.

### <a name="languages"></a>Langages

Ce service est actuellement fourni en anglais uniquement.

## <a name="apply-for-microsoft-defender-experts-for-hunting-service"></a>Demander Microsoft Defender experts pour le service de chasse

Si vous ne l’avez pas encore fait, vous pouvez remplir le formulaire d’intérêt client pour Defender Experts for Hunting :

1. Remplissez le [formulaire d’intérêt client](https://aka.ms/DEX4HuntingCustomerInterestForm). Toute personne de votre entreprise peut faire une demande, mais si vous êtes accepté, vous devez travailler avec votre responsable commercial pour transiger la référence SKU.
2. Entrez votre nom, votre nom d’entreprise et votre ID de messagerie d’entreprise.
3. Sélectionnez **Envoyer**. Une personne de notre équipe commerciale contactera dans les cinq jours ouvrables.


### <a name="next-step"></a>Étape suivante

- [Commencer à utiliser Defender Experts for Hunting](onboarding-defender-experts-for-hunting.md)
