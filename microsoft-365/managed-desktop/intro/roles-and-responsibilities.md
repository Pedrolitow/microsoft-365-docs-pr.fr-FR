---
title: Rôles et responsabilités de Bureau géré Microsoft
description: Cet article décrit les rôles et les responsabilités fournis par Microsoft pour le bureau géré Microsoft.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 8ced46ea30c7225fd3e5c8f1309ef482542e51b2
ms.sourcegitcommit: 9a764c2aed7338c37f6e92f5fb487f02b3c4dfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48445782"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Rôles et responsabilités de Bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Lors de l’enregistrement de votre organisation dans Microsoft Managed Desktop, qu’est-ce que Microsoft vous fait pour vous ? Quelles sont les responsabilités de votre organisation ?

## <a name="microsofts-roles-and-responsibilities"></a>Rôles et responsabilités de Microsoft

Microsoft fournit les rôles et responsabilités clés suivants :

Rôle ou responsabilité | Description
--- | ---
Gestion des stratégies MDM | Microsoft appliquera les stratégies MDM conformément aux meilleures pratiques et envisagez de demander des modifications de stratégie. Nous allons également modifier votre client comme indiqué dans stratégies d' [appareil](../service-description/device-policies.md).
prise en charge des utilisateurs | Nous fournissons la prise en charge des appareils, des fenêtres et de la suite de produits Microsoft 365 apps pour Enterprise pour tous les utilisateurs dans l’application d’aide qui est préinstallée sur tous les appareils de bureau gérés par Microsoft. 
Prise en charge du service bureau géré Microsoft | Microsoft prendra en charge votre service informatique via une équipe Microsoft Managed Desktop Operations. Cette équipe prend en charge la résolution des problèmes techniques, les demandes de modification et la gestion des incidents pour l’environnement de bureau géré Microsoft du client. Pour plus d’informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).
Surveillance de la sécurité | Microsoft analysera vos appareils de bureau gérés par Microsoft à l’aide de Microsoft Defender ATP. Si le centre d’opérations de sécurité de bureau géré par Microsoft détecte une menace, nous vous en informerons, en isolant l’appareil et en rectifiant le problème à distance. Pour plus d’informations, consultez la rubrique [sécurité](../service-description/security.md).
Mise à jour de la surveillance et de la gestion | Nous contrôlons activement vos appareils de bureau gérés par Microsoft pour vous assurer que les dernières mises à jour de qualité et de fonctionnalité sont installées pour Microsoft Windows et Microsoft Office. Pour plus d’informations, voir [Comment les mises à jour sont gérées](../service-description/updates.md).
Groupement d’utilisateurs et d’appareils | Microsoft Managed Desktop Operations Team créera et gérera les groupes d’utilisateurs et d’appareils requis dans le cadre des opérations informatiques. Aucune modification de l’appartenance ou de la configuration n’est autorisée pour ces groupes. La modification de ces groupes peut entraîner une configuration inattendue des appareils et une perte de fonctionnalité. Pour tout problème ou question concernant ces groupes une fois établi, les administrateurs informatiques peuvent contacter les opérations de bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Cet ensemble supplémentaire de rôles et de responsabilités courants est requis pour le déploiement, mais n’est pas fourni par Microsoft. Il n’est pas exhaustif, mais applicable à la plupart des organisations. Il y a quelques éléments pour lesquels vous et Microsoft Partagez une responsabilité. 

Rôle ou responsabilité | Description
--- | ---
Gestion des modifications | Microsoft avertira les clients, à l’avance, quand les modifications devront être apportées à leur environnement de bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [service changes and communication](../service-description/servicechanges.md).<br><br>Vous devez disposer de votre propre processus de gestion des modifications et avoir un contact établi avec l’équipe des opérations de bureau géré Microsoft. Vous devez également disposer des ressources nécessaires pour examiner et approuver ces modifications. Pour plus d’informations, consultez la rubrique [opérations et surveillance](../service-description/operations-and-monitoring.md).  
Gestion des identités | Vous êtes responsable de la création de comptes d’utilisateur, de l’affectation d’utilisateurs à des groupes et de la mise à jour des métadonnées. 
Applications Microsoft 365 pour la configuration et la gestion d’entreprise | Microsoft est chargé de s’assurer que les applications Office sont déployées auprès des utilisateurs et que ces applications sont tenues à jour. <br><br> Vous êtes responsable de la gestion des services et des stratégies Microsoft 365, y compris les responsabilités d’administration d’Exchange Online :<br>-Administration de la messagerie<br>-Configuration de la boîte aux lettres et des règles<br>-Gestion Exchange sur site<br><br>Vous êtes également responsable des outils de collaboration, de l’administration de SharePoint Server, de la gestion des domaines et de la sécurité et des stratégies d’information qui sont définies dans le centre d’administration Microsoft 365. 
Support pour les utilisateurs | Vous devez fournir une assistance utilisateur pour : <br>-Infrastructure sur site : toute la connectivité réseau et Internet, l’infrastructure VPN et la configuration client, la salle de conférence locale, les imprimantes, le serveur proxy, la configuration et les pare-feu.<br><br>-Ressources Cloud à l’échelle de l’entreprise : messagerie, SharePoint, services de collaboration et autre infrastructure cloud qui se rapportent à la technologie à l’échelle de l’entreprise.<br><br>-Ligne d’entreprise et toutes les autres applications spécifiques de l’entreprise.
Applications | Les rôles et les responsabilités varient légèrement pour les applications fournies avec Microsoft Managed Desktop et les applications que vous fournissez. <br><br>Pour les applications fournies par Microsoft (Microsoft 365 apps pour entreprises comprenant Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype entreprise, teams et OneNote), **Microsoft** fournit un service complet pour le déploiement, la mise à jour et le support. **Vous** devez obtenir et attribuer des licences pour ces applications, ajouter des utilisateurs à des groupes de sécurité et gérer la fin de la vie et déployer les modules complémentaires dont vous avez besoin.<br><br>Pour les applications que vous fournissez (telles que vos applications métiers), si vous les Empaquetez vous-même ou si vous demandez à un fournisseur non-Microsoft de le faire, **vous** devez effectuer les actions suivantes : <br><br>-Identification des applications requises pour les groupes d’utilisateurs ciblés<br>-Création et gestion de groupes Azure AD pour le déploiement d’applications<br>-Empaquetage d’applications pour répondre aux normes de déploiement Microsoft Intune<br>-Téléchargement d’applications dans Microsoft Intune<br>-Test d’applications dans un environnement de bureau géré Microsoft<br>-Test des applications avec vos utilisateurs<br>-Gestion et affectation des utilisateurs aux applications<br>-Identifier et déployer les mises à jour des applications via Microsoft Intune<br>-Désinstaller et supprimer des applications lorsqu’elles ont été retirées<br>-Approvisionnement et attribution de licences<br>-Prise en charge par l’utilisateur des applications métiers<br>-Gestion à distance des paramètres de l’application<br><br>**Microsoft** fournira des outils de déploiement Microsoft Intune pour fournir les applications aux clients distants.<br><br>Pour plus d’informations, consultez la rubrique [applications](../get-ready/apps.md).
Surveillance de la sécurité et réponse | Vous êtes chargé d’examiner et de résoudre les incidents pour les appareils qui ne sont pas des appareils de bureau gérés par Microsoft et de s’assurer que l’équipe des opérations de bureau géré Microsoft est informée des problèmes susceptibles d’avoir un impact sur le service.
Prise en charge des opérations | Vous devez fournir une liste de contacts préférés et d’experts techniques dans votre organisation. Cela est nécessaire en cas d’incident opérationnel sans lien avec le bureau géré Microsoft. <br><br>Vous êtes également responsable de l’analyse et de la résolution des incidents pour les appareils et les services qui ne se trouvent pas dans le bureau géré Microsoft et de l’assurance que l’équipe Microsoft Managed Desktop Operations est toujours informée.
Infrastructure réseau, y compris VPN | Vous êtes responsable de l’installation, de la configuration et de la gestion (y compris le dépannage et le débogage) de toutes les infrastructures et services liés au réseau, y compris la connectivité Internet, les contrôles réseau, la configuration du proxy et l’infrastructure de connectivité à distance.<br><br>Si un proxy est configuré (dans le matériel ou le logiciel), il existe une collection d’URL qui doivent être autorisées par le proxy. Vous êtes responsable de la résolution des conflits ou des incompatibilités dus à plusieurs proxys. Vous pouvez ajouter des proxys réseau spécifiques à votre organisation à l’aide des paramètres configurables. Pour plus d’informations, consultez la rubrique [configurable Settings](../working-with-managed-desktop/config-setting-ref.md#proxy).<br><br>Pour plus d’informations, consultez la rubrique [configuration du proxy](../get-ready/network.md).
Impression | Vous êtes responsable de l’installation, de la maintenance et de l’administration des imprimantes et des files d’attente d’impression. L’impression en nuage est une solution recommandée, mais cela n’est pas obligatoire. 




