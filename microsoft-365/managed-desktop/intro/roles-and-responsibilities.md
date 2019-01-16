---
title: Ordinateur de bureau Microsoft rôles et responsabilités
description: Cette rubrique décrit les rôles et responsabilités fournies par Microsoft pour ordinateur de bureau Microsoft.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 96131f7577e0e655067c70bffdd75163ba790adf
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867480"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Ordinateur de bureau Microsoft rôles et responsabilités


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Lorsque votre organisation est inscrit à Microsoft de bureau, ce que Microsoft ne vous ? Et quelles sont les responsabilités de votre organisation ?

## <a name="microsofts-roles-and-responsibilities"></a>Rôles et responsabilités de Microsoft

Vous trouverez ci-dessous quelques principaux rôles et responsabilités qui seront fournies par Microsoft.

Rôle ou responsabilité | Description
--- | ---
Gestion des stratégies de Mobile Device Manager | Microsoft s’appliquer des stratégies de Mobile Device Manager conformément aux meilleures pratiques et prendre en compte les demandes de modification de la stratégie de. Il sera également apporter des modifications à votre client énoncées dans les [stratégies d’appareil](../service-description/device-policies.md).
Prise en charge de l’utilisateur final | Microsoft fournira la prise en charge de l’utilisateur final pour Office, Windows et les appareils suite de produits pour tous les utilisateurs inscrits par le biais de l’application d’obtenir de l’aide qui est préinstallé sur tous les périphériques de bureau Microsoft. 
Prise en charge du service Microsoft de bureau | Microsoft fournira la prise en charge informatiques du client Services via une équipe des opérations Microsoft géré du bureau. Cette équipe va prendre en charge la résolution des problèmes techniques, demandes de modification et la gestion des incidents pour l’environnement du client de bureau Microsoft. Pour plus d’informations, voir [administration prise en charge de l’ordinateur de bureau Microsoft](../working-with-managed-desktop/admin-support.md).
Surveillance de la sécurité | Microsoft surveillera les périphériques de bureau Microsoft client à l’aide de Windows Defender DAV. Si une menace est détectée par le Microsoft gérées Bureau sécurité opérations Centre (sécurité sociale), Microsoft informera le client, isoler le périphérique et corriger le problème à distance. Pour plus d’informations, voir [sécurité](../service-description/security.md).
Surveillance de la mise à jour et de gestion | Microsoft surveillera activement les périphériques de bureau Microsoft client pour vous assurer que les dernières mises à jour de la qualité et les fonctionnalités sont installés pour Microsoft Windows et Microsoft Office. Pour plus d’informations, voir [la gestion des mises à jour](../service-description/updates.md).
Utilisateur et regroupement de périphériques | Équipe chargée des opérations de bureau Microsoft sera créer et gérer des périphériques requis et les groupes d’utilisateurs dans le cadre des opérations informatiques. Il ne doit pas être modifications apportées à ces groupes sans l’approbation de l’équipe chargée des opérations de bureau Microsoft.

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Vous trouverez ci-dessous un ensemble de rôles et responsabilités qui ne sont pas fournies par Microsoft, mais qui sont requis pour un déploiement réussi supplémentaires. Il n’est pas exhaustive mais n’est applicable pour la plupart des organisations. Il existe quelques éléments ci-dessous que Microsoft et le client partagent responsibilties. 

Rôle ou responsabilité | Description
--- | ---
Gestion du changement | Microsoft avertira clients, à l’avance, lorsque les modifications doivent être effectuées dans leur environnement de bureau Microsoft. Le client est nécessaire de posséder leur propre gestion des modifications traiter et qu’un contact établi avec l’équipe chargée des opérations de bureau géré Microsoft. Le client est également requis pour que les ressources pour examiner et approuver ces modifications. Pour plus d’informations, voir [opérations et surveillance](../service-description/operations-and-monitoring.md).  
Gestion des identités | Le client est responsable de la création de comptes d’utilisateurs, affectation à des groupes d’utilisateurs et tenue à jour des métadonnées. 
Gestion et la configuration d’office 365 | Microsoft est responsable applications Office sont déployées sur les utilisateurs finaux et les applications sont tenues à jour. <br><br> Le client est responsable de la gestion des stratégies, y compris les responsabilités d’administration Exchange Online et des services Office 365 :<br>-Courrier électronique administration<br>-Boîte aux lettres et la règle de configuration<br>-Exchange locale gestion<br><br>Le client est également responsable des outils de collaboration, administration de SharePoint server, gestion de domaine, informations de sécurité et les stratégies définies dans le portail d’administration d’Office 365. 
Prise en charge de l’utilisateur final | Le client est chargé de fournir une prise en charge de l’utilisateur final pour : <br>-Dans l’infrastructure du site : tous les connectivité réseau et internet, VPN infrastructure et configuration client, équipement de salle de conférence local, imprimantes, serveur proxy et configuration de pare-feu.<br><br>-Ressources de cloud entreprise : courrier électronique, SharePoint, services de collaboration et autres infrastructure de nuage qui se rapporte à l’empreinte de la technologie de l’entreprise.<br><br>-Secteur d’activité et d’autres applications spécifiques société.
Applications | Microsoft fournit des instructions de déploiement pour les applications approuvées à l’aide de Intune à la demande.<br><br>Le client est responsable de :<br>-Qui fournit une liste des applications pour leur organisation (en dehors des applications Office 365)<br>-Gestion des licences app<br>– Ayant le type approprié et le nombre de licences<br>-Affectation app<br>– Applications affectation aux groupes d’utilisateurs Azure AD<br>-Mises à jour app<br>– Surveillance, l’empaquetage et déploiement de mises à jour de sécurité et de fonctionnalité application<br>-Application utilisateur (UAT) de test<br>-Fourniture d’un package déployable approprié<br><br>Pour plus d’informations, voir [Apps](../get-ready/apps.md)
Surveillance de la sécurité et de réponse | Le client est responsable de l’analyse et de résolution des incidents pour les périphériques non - Microsoft de bureau et en vous assurant que l’équipe des opérations bureau géré Microsoft est informé de tous les problèmes qui peuvent avoir un impact sur le service.
Prise en charge des opérations | Le client est chargé de fournir une liste des contacts du client par défaut et -experts techniques. Microsoft a besoin de ces au cas où un incident opérationnelles non - Microsoft de bureau. <br><br>Le client est également responsable de l’analyse et de résolution des incidents pour veiller à ce que l’équipe des opérations bureau géré Microsoft est toujours informé de périphériques non - Microsoft de bureau et services.
Infrastructure de réseau, y compris VPN | Le client est responsable du programme d’installation, configuration et gestion (y compris le dépannage et le débogage) de toutes les infrastructure en matière de réseau et les services, y compris la connectivité internet, réseau contrôles, les configurations de proxy et à distance infrastructure de connexion.<br><br>Si un proxy est configuré (dans la configuration matérielle ou logicielle), il existe une collection d’URL doit être autorisé par le proxy. Le client est responsable de la résolution des problèmes de conflits ou de détecter les incompatibilités en raison de plusieurs proxys.<br><br>Pour plus d’informations, voir [Configuration du serveur Proxy](../get-ready/network.md).
Impression | Le client est chargé de l’installation, de maintenance et d’administration des imprimantes et des files d’attente. Dans le nuage l’impression est une solution recommandée, mais n’est pas obligatoire. 




