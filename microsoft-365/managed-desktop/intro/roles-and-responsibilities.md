---
title: Ordinateur de bureau Microsoft rôles et responsabilités
description: Cette rubrique décrit les rôles et responsabilités fournies par Microsoft pour ordinateur de bureau Microsoft.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 923cde6353e4ff5122317f2c053fef244ee7e1b6
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
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
Déploiement d’applications | Microsoft déploierez des applications approuvées pour les périphériques de bureau Microsoft du client à l’aide de Intune. Pour plus d’informations, voir [Apps](../get-ready/apps.md). 
Prise en charge de l’utilisateur final | Microsoft fournira la prise en charge de l’utilisateur final pour Office, Windows et les appareils suite de produits pour tous les utilisateurs inscrits. 
Prise en charge du service Microsoft de bureau | Microsoft fournira la prise en charge informatiques du client Services via une équipe des opérations Microsoft géré du bureau. Cette équipe va prendre en charge la résolution des problèmes techniques, demandes de modification et la gestion des incidents pour l’environnement du client de bureau Microsoft. Pour plus d’informations, voir [obtenir une assistance](../service-description/support.md).
Surveillance de la sécurité | Microsoft surveillera les périphériques de bureau Microsoft client à l’aide de Windows Defender DAV. Si une menace est détectée par le Microsoft gérées Bureau sécurité opérations Centre (sécurité sociale), Microsoft informera le client, isoler le périphérique et corriger le problème à distance. Pour plus d’informations, voir [sécurité](../service-description/security.md).
Surveillance de la mise à jour et de gestion | Microsoft surveillera activement les périphériques de bureau Microsoft client pour vous assurer que les dernières mises à jour de qualité, de fonctionnalité et de définition sont installés pour Microsoft Windows et Microsoft Office. Pour plus d’informations, voir [la gestion des mises à jour](../service-description/updates.md).
Acquisition de l’appareil | Microsoft sera livraison ordonnées périphériques de bureau Microsoft aux utilisateurs finaux ou le point de distribution informatique de votre choix. Pour plus d’informations, voir [Devices](../get-started/devices.md).

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Voici un ensemble de rôles qui ne sont pas fournis par Microsoft, mais qui sont requis pour un déploiement réussi supplémentaires. Il n’est pas exhaustive mais est généralement utilisé pour la plupart des organisations. 

Rôle ou reponsibility | Description
--- | ---
Gestion du changement | Ordinateur de bureau Microsoft avertira clients, à l’avance, lorsque les modifications doivent être effectuées dans leur environnement de bureau Microsoft. Les clients doivent avoir leur propre processus de gestion des changements et doivent avoir un contact avec un ordinateur de bureau Microsoft. Le client est nécessaire pour dispose des ressources pour examiner et approuver ces modifications. Pour plus d’informations, voir [opérations et surveillance](../service-description/operations-and-monitoring.md).  
Gestion des identités | Création de comptes d’utilisateur, affecter des utilisateurs aux groupes et tenue à jour des métadonnées. 
Gestion et la configuration d’office 365 | Administration Oonline Exchange, y compris :<br>-Courrier électronique administration<br>-Boîte aux lettres et la règle de configuration<br>-Exchange locale gestion<br><br>Outils de collaboration, administration de SharePoint server, gestion de domaine, informations de sécurité et les stratégies définies dans le portail d’administration d’Office 365 (ordinateur de bureau Microsoft permet de garantir les applications Office sont déployées sur les périphériques de l’utilisateur final et se tenir au courant). 
Prise en charge de l’utilisateur final | Le client prendra en charge pour l’utilisateur final : <br>-Dans l’infrastructure du site : tous les connectivité réseau et internet, VPN infrastructure et configuration client, équipement de salle de conférence local, imprimantes, serveur proxy et configuration de pare-feu.<br><br>-Ressources de cloud entreprise : courrier électronique, SharePoint, services de collaboration et autres infrastructure de nuage qui se rapporte à l’empreinte de la technologie de l’entreprise.<br><br>-De-applications métiers : logiciel personnalisé, logiciels-3 rd, logiciels planning (ERP) des ressources d’entreprise, des outils de conception et rien ne spécifiée dans ce document.
Utilisateur et regroupement de périphériques | Équipe chargée des opérations de bureau Microsoft sera créer et gérer des périphériques requis et les groupes d’utilisateurs dans le cadre des opérations informatiques. Le client ne sera pas apporter de modifications à ces associations sans premier contact informatiques par le biais de canaux pris en charge. Tous les détectés modifications seront annulées.
Applications | Clients fournit une liste des applications qu’ils souhaitent utiliser dans leur organisation (au-delà des applications incluses avec licence Microsoft 365). Les clients également fournir un package déployable (Appx ou MSI)<br>Le client est responsable de :<br>-Gestion des licences app – ayant le type approprié et le nombre de licences<br>-Affectation app – applications affectation aux groupes d’utilisateurs Azure AD<br>-Mises à jour app – surveillance, d’empaquetage et le déploiement des mises à jour de sécurité et de fonctionnalité application<br>-Application utilisateur (UAT) de test<br><br>Pour plus d’informations, voir [Apps](../get-ready/apps.md)
Surveillance de la sécurité et de réponse | Si un incident de sécurité est détecté en dehors de l’étendue des opérations de bureau géré Microsoft, nous nécessite une liste des contacts du client par défaut selon la gravité du problème.<br><br>Le client est responsable de l’analyse et de résolution des incidents pour les périphériques non - Microsoft de bureau et en vous assurant que l’équipe des opérations bureau géré Microsoft est informé de tous les problèmes qui peuvent avoir un impact sur le service.
Prise en charge des opérations | Opérations de bureau géré Microsoft doit une liste des contacts du client par défaut et -experts techniques. Nous avons besoin au cas où un incident opérationnelles non - Microsoft de bureau. <br><br>Le client est responsable de l’analyse et de résolution des incidents pour veiller à ce que l’équipe des opérations bureau géré Microsoft est toujours informé de périphériques non - Microsoft de bureau et services.
Infrastructure de réseau, y compris VPN | Le programme d’installation, de configuration et de gestion (y compris le dépannage et le débogage) de l’infrastructure tout en matière de réseau et des services, y compris la connectivité internet, réseau contrôles, les configurations de proxy et l’infrastructure de connectivité à distance.<br><br>Par défaut, ordinateur de bureau Microsoft ne spécifiez ni ne requièrent un proxy. Toutefois, s’il est configuré (dans la configuration matérielle ou logicielle), il est une collection d’URL doit être autorisé par le proxy. Le client est responsable de la résolution des problèmes de conflits ou de détecter les incompatibilités en raison de plusieurs proxys.<br><br>Pour plus d’informations, voir [Configuration du serveur Proxy](../get-ready/network.md).
Impression | Installer, gérer et administrer des imprimantes et des files d’attente. Dans le nuage l’impression est une solution recommandée, mais n’est pas obligatoire. 
Appareils mobiles | Les périphériques et accessoires non fournis par Microsoft de bureau. Équipe chargée des opérations bureau géré Microsoft prend uniquement en charge les périphériques de bureau Microsoft, station d’accueil et les accessoires inclus.




