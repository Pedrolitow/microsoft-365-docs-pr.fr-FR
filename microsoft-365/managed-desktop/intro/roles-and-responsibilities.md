---
title: Rôles et responsabilités de Bureau géré Microsoft
description: Cet article décrit les rôles et responsabilités fournis par Microsoft pour bureau géré Microsoft.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 94389fbb9a13b9a880b0c4dcaf67d8adcaff0f98
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49841314"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Rôles et responsabilités de Bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Lorsque votre organisation est inscrite au Bureau géré Microsoft, que fait Microsoft pour vous ? Quelles sont les responsabilités de votre organisation ?

## <a name="microsofts-roles-and-responsibilities"></a>Rôles et responsabilités de Microsoft

Microsoft fournit les rôles et responsabilités clés ci-après :

Rôle ou responsabilité | Description
--- | ---
Gestion des stratégies mdm | Microsoft appliquera des stratégies de gestion des stratégies de gestion des stratégies de groupe conformément aux meilleures pratiques et prendra en compte les demandes de modifications de stratégie. Nous apporterons également des modifications à votre client comme prévu dans les stratégies [d’appareil.](../service-description/device-policies.md)
prise en charge des utilisateurs | Nous fournissons un support utilisateur pour les appareils, Windows et la suite de produits Microsoft 365 Apps for enterprise pour tous les utilisateurs inscrits via l’application Obtenir de l’aide qui est préinstallée sur tous les appareils de bureau géré Microsoft. 
Prise en charge du service Bureau géré Microsoft | Microsoft fournira un support à votre service informatique via une équipe d’opérations de bureau géré Microsoft. Cette équipe prendra en charge le dépannage technique, les demandes de modification et la gestion des incidents pour l’environnement Bureau géré Microsoft du client. Pour plus d’informations, [consultez la prise en charge par l’administrateur du Bureau géré Microsoft.](../working-with-managed-desktop/admin-support.md)
Surveillance de la sécurité | Microsoft surveillera vos appareils bureau géré Microsoft à l’aide de Microsoft Defender for Endpoint. Si le Centre d’opérations de sécurité bureau géré Microsoft détecte une menace, nous vous en informons, isolons l’appareil et rectifions le problème à distance. Pour plus d’informations, voir [Sécurité.](../service-description/security.md)
Mise à jour de la surveillance et de la gestion | Nous surveillons activement vos appareils Bureau géré Microsoft pour nous assurer que les dernières mises à jour qualité et fonctionnalités sont installées pour Microsoft Windows et Microsoft Office. Pour plus d’informations, voir [comment les mises à jour sont gérées.](../service-description/updates.md)
Regroupement d’utilisateurs et d’appareils | L’équipe des opérations bureau géré Microsoft créera et gérera les groupes d’appareils et d’utilisateurs requis dans le cadre des opérations informatiques. Aucune modification d’appartenance ou de configuration n’est autorisée pour ces groupes. La modification de ces groupes peut entraîner une configuration inattendue des appareils et une perte de fonctionnalités. Pour tout problème ou toute question concernant ces groupes une fois établis, les administrateurs informatiques peuvent contacter les opérations bureau géré Microsoft. Pour plus d’informations, [consultez la prise en charge par l’administrateur du Bureau géré Microsoft.](../working-with-managed-desktop/admin-support.md)

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Cet ensemble de rôles et de responsabilités courants est requis pour le déploiement, mais ne sont pas fournis par Microsoft. Ce n’est pas exhaustif, mais il s’applique à la plupart des organisations. Vous et Microsoft partagez la responsabilité de certains éléments. 

Rôle ou responsabilité | Description
--- | ---
Gestion des modifications | Microsoft informera à l’avance les clients lorsque des modifications doivent être apportées à leur environnement Bureau géré Microsoft. Pour plus d’informations, [voir changements de service et communication.](../service-description/servicechanges.md)<br><br>Vous devez avoir votre propre processus de gestion des changements et établir un contact avec l’équipe Des opérations bureau gérés microsoft. Vous devez également avoir des ressources pour examiner et approuver ces modifications. Pour plus d’informations, voir [Opérations et surveillance.](../service-description/operations-and-monitoring.md)  
Gestion des identités | Vous êtes responsable de la création de comptes d’utilisateurs, de l’affectation d’utilisateurs à des groupes et de la mise à jour des métadonnées. 
Microsoft 365 Apps for enterprise configuration and management | Microsoft est chargé de s’assurer que les applications Office sont déployées pour les utilisateurs et que ces applications sont tenues à jour. <br><br> Vous êtes responsable de la gestion des services et des stratégies Microsoft 365, y compris les responsabilités d’administration d’Exchange Online :<br>- Administration de la messagerie<br>- Configuration de la boîte aux lettres et des règles<br>- Gestion exchange sur site<br><br>Vous êtes également responsable des outils de collaboration, de l’administration de SharePoint Server, de la gestion de domaine et des stratégies de sécurité et d’informations définies dans le Centre d’administration Microsoft 365. 
Support pour les utilisateurs | Vous devez fournir la prise en charge des utilisateurs pour : <br>- Infrastructure sur site : connectivité réseau et Internet, infrastructure VPN et configuration du client, équipement de salle de conférence local, imprimantes, serveur proxy et configuration, et pare-feu.<br><br>- Ressources cloud à l’échelle de l’entreprise : messagerie, SharePoint, services de collaboration et autres infrastructures cloud liées à l’empreinte technologique à l’échelle de l’entreprise.<br><br>- Secteur d’activité et toutes les autres applications propres à l’entreprise.
Applications | Les rôles et responsabilités varient quelque peu pour les applications fournies dans le cadre du Bureau géré Microsoft par rapport aux applications que vous fournissez. <br><br>Pour les applications fournies par Microsoft (Microsoft 365 Apps for enterprise comprenant Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise, Teams et OneNote), **Microsoft** fournit un service complet pour le déploiement, la mise à jour et le support. **Vous** devez obtenir et attribuer des licences pour ces applications, ajouter des utilisateurs à des groupes de sécurité, gérer la fin de vie et déployer les modules nécessaires.<br><br>Pour les applications que vous fournissez (telles que vos applications métier), que vous les inséliez vous-même dans un package ou que vous en appeliez à un fournisseur autre que **Microsoft,** vous êtes responsable des actions ci-après : <br><br>- Identification des applications nécessaires pour les groupes d’utilisateurs ciblés<br>- Création et gestion de groupes Azure AD pour le déploiement d’applications<br>- Empaquetage d’applications pour répondre aux normes de déploiement de Microsoft Intune<br>- Téléchargement d’applications vers Microsoft Intune<br>- Test des applications dans l’environnement Bureau géré Microsoft<br>- Test des applications avec vos utilisateurs<br>- Gestion et affectation d’utilisateurs à des applications<br>- Identifier et déployer les mises à jour d’application via Microsoft Intune<br>- Désinstallation et suppression d’applications lorsqu’elles ont été retirées<br>- Procuring and assigning licenses<br>- Prise en charge des applications métier par les utilisateurs<br>- Gestion des paramètres d’application à distance<br><br>**Microsoft** fournit des outils de déploiement Microsoft Intune pour fournir les applications aux clients distants.<br><br>Pour plus d’informations, voir [Applications.](../get-ready/apps.md)
Surveillance de la sécurité et réponse | Vous êtes responsable de l’investigation et de la résolution des incidents pour les appareils qui ne sont pas des appareils de bureau géré Microsoft et de vous assurer que l’équipe des opérations du bureau géré Microsoft est informée des problèmes qui peuvent avoir un impact sur le service.
Prise en charge des opérations | Vous devez fournir une liste de contacts préférés et d’experts techniques de votre organisation. Nous avons besoin de ces contacts en cas d’incident opérationnel non lié au Bureau géré Microsoft. <br><br>Vous êtes également responsable de la recherche et de la résolution des incidents pour les appareils et les services qui ne sont pas dans le Bureau géré Microsoft et de vous assurer que l’équipe des opérations du bureau géré Microsoft est toujours informée.
Infrastructure réseau, y compris VPN | Vous êtes responsable de la configuration, de la configuration et de la gestion (y compris le dépannage et le débogage) de toutes les infrastructures et services liés à la mise en réseau, y compris la connectivité Internet, les contrôles réseau, la configuration du proxy et l’infrastructure de connectivité à distance.<br><br>Si un proxy est configuré (en matériel ou logiciel), il existe une collection d’URL qui doit être autorisée par le proxy. Vous êtes responsable de la résolution des conflits ou incompatibilités dus à plusieurs proxies. Vous pouvez ajouter des proxies réseau spécifiques à votre organisation à l’aide de paramètres configurables. Pour plus d’informations, voir [Paramètres configurables.](../working-with-managed-desktop/config-setting-ref.md#proxy)<br><br>Pour plus d’informations, [voir Configuration du proxy.](../get-ready/network.md)
Impression | Vous êtes responsable de l’installation, de la maintenance et de l’administration des imprimantes et des files d’attente d’impression. L’impression dans le cloud est une solution recommandée, mais elle n’est pas obligatoire. 




