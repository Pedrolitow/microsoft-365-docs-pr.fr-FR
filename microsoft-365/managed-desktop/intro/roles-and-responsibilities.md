---
title: Rôles et responsabilités du bureau géré Microsoft
description: Cette rubrique décrit les rôles et les responsabilités fournis par Microsoft pour le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 0288dfd2ee84f406c4bcdf4a604d1370afeefed7
ms.sourcegitcommit: fb3815ee186b2b3ec790ee32a9d7b1628d623b0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "39202175"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Rôles et responsabilités du bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Lors de l’enregistrement de votre organisation dans Microsoft Managed Desktop, qu’est-ce que Microsoft vous fait pour vous ? Quelles sont les responsabilités de votre organisation ?

## <a name="microsofts-roles-and-responsibilities"></a>Rôles et responsabilités de Microsoft

Vous trouverez ci-dessous quelques rôles et responsabilités clés qui seront fournis par Microsoft.

Rôle ou responsabilité | Description
--- | ---
Gestion des stratégies MDM | Microsoft appliquera les stratégies MDM conformément aux meilleures pratiques et envisagez de demander des modifications de stratégie. Nous allons également modifier votre client comme indiqué dans stratégies de [périphérique](../service-description/device-policies.md).
Prise en charge des utilisateurs finaux | Microsoft fournit la prise en charge de l’utilisateur final pour les appareils, les fenêtres et la suite de produits Office pour tous les utilisateurs dans l’application d’aide qui est préinstallée sur tous les appareils de bureau gérés par Microsoft. 
Prise en charge du service bureau géré Microsoft | Microsoft fournira une assistance aux services informatiques des clients par le biais d’une équipe Microsoft Managed Desktop Operations. Cette équipe prend en charge la résolution des problèmes techniques, les demandes de modification et la gestion des incidents pour l’environnement de bureau géré Microsoft du client. Pour plus d’informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).
Surveillance de la sécurité | Microsoft analysera le client les appareils de bureau gérés par Microsoft à l’aide de Microsoft Defender ATP. Si une menace est détectée par le centre d’opérations de sécurité du bureau géré Microsoft, Microsoft avertit le client, isole l’appareil et corrige le problème à distance. Pour plus d’informations, consultez la rubrique [sécurité](../service-description/security.md).
Mise à jour de la surveillance et de la gestion | Microsoft analysera activement les périphériques de bureau gérés par le client pour s’assurer que les dernières mises à jour de qualité et de fonctionnalité sont installées pour Microsoft Windows et Microsoft Office. Pour plus d’informations, voir [Comment les mises à jour sont gérées](../service-description/updates.md).
Groupement d’utilisateurs et d’appareils | Microsoft Managed Desktop Operations Team créera et gérera les groupes d’utilisateurs et d’appareils requis dans le cadre des opérations informatiques. Aucune modification de l’appartenance ou de la configuration n’est autorisée pour ces groupes. La modification de ces groupes peut entraîner une configuration inattendue des appareils et une perte de fonctionnalité. Pour tout problème ou question concernant ces groupes une fois établi, les administrateurs informatiques peuvent contacter les opérations de bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Vous trouverez ci-dessous un ensemble supplémentaire de rôles et de responsabilités courants qui ne sont pas fournis par Microsoft, mais qui sont requis pour un déploiement réussi. Il n’est pas exhaustif, mais applicable à la plupart des organisations. Il existe quelques éléments ci-dessous que Microsoft et le client partagent responsibilties. 

Rôle ou responsabilité | Description
--- | ---
Gestion des modifications | Microsoft avertira les clients, à l’avance, quand les modifications devront être apportées à leur environnement de bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [service changes and communication](../service-description/servicechanges.md) .<br><br>Le client doit avoir son propre processus de gestion des modifications et disposer d’un contact établi avec l’équipe des opérations de bureau géré Microsoft. Le client doit également disposer de ressources pour vérifier et approuver ces modifications. Pour plus d’informations, consultez la rubrique [opérations et surveillance](../service-description/operations-and-monitoring.md).  
Gestion des identités | Le client est responsable de la création de comptes d’utilisateurs, de l’affectation d’utilisateurs à des groupes et de la mise à jour des métadonnées. 
Configuration et gestion d’Office 365 ProPlus | Microsoft est chargé de s’assurer que les applications Office sont déployées sur les utilisateurs finaux et que ces applications sont tenues à jour. <br><br> Le client est responsable de la gestion des services et des stratégies Office 365, y compris les responsabilités d’administration d’Exchange Online :<br>-Administration de la messagerie<br>-Configuration de la boîte aux lettres et des règles<br>-Gestion Exchange sur site<br><br>Le client est également responsable des outils de collaboration, de l’administration de SharePoint Server, de la gestion de domaine, de la sécurité et des stratégies d’information définies dans le portail d’administration Office 365. 
Prise en charge des utilisateurs finaux | Le client est responsable de la fourniture de la prise en charge des utilisateurs finaux pour : <br>-Infrastructure de site : toutes les connexions réseau et Internet, l’infrastructure VPN et la configuration client, la salle de conférence locale, les imprimantes, le serveur proxy et la configuration, les pare-feu.<br><br>-Ressources Cloud à l’échelle de l’entreprise : messagerie, SharePoint, services de collaboration et autre infrastructure cloud qui se rapportent à la technologie à l’échelle de l’entreprise.<br><br>-Ligne professionnelle et toute autre application spécifique à une société.
Applications | Les rôles et les responsabilités varient quelque peu pour les applications fournies dans le cadre de Microsoft Managed Desktop par rapport à celles que vous fournissez. <br><br>Pour les applications fournies par Microsoft (Office 365 ProPlus, qui comprend Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype entreprise, teams et OneNote), **Microsoft** fournit un service complet pour le déploiement, la mise à jour et le support. **Vous** devez obtenir et attribuer des licences pour ces applications, ajouter des utilisateurs à des groupes de sécurité et gérer la fin de vie et déployer les compléments Office 365 addons dont vous avez besoin.<br><br>Pour les applications que vous fournissez (telles que vos applications métiers), si vous les Empaquetez vous-même ou si vous demandez à un fournisseur non-Microsoft de le faire, **vous** devez effectuer les actions suivantes : <br><br>-Identification des applications requises pour les groupes d’utilisateurs ciblés<br>-Création et gestion de groupes Azure AD pour le déploiement d’applications<br>-Empaquetage d’applications pour répondre aux normes de déploiement Microsoft Intune<br>-Téléchargement d’applications dans Microsoft Intune<br>-Test d’applications dans un environnement de bureau géré Microsoft<br>-Test des applications avec vos utilisateurs finaux<br>-Gestion et affectation des utilisateurs aux applications<br>-Identifier et déployer les mises à jour des applications via Microsoft Intune<br>-Désinstaller et supprimer des applications lorsqu’elles ont été retirées<br>-Approvisionnement et attribution de licences<br>-Prise en charge de l’utilisateur final pour les applications métiers<br>-Gestion à distance des paramètres de l’application<br><br>**Microsoft** fournira des outils de déploiement Microsoft Intune pour fournir les applications aux clients distants.<br><br>Pour plus d’informations, consultez la rubrique [applications](../get-ready/apps.md)
Surveillance et réponse de la sécurité | Le client est chargé d’examiner et de résoudre les incidents pour les appareils de bureau gérés non-Microsoft et de s’assurer que l’équipe des opérations de bureau géré Microsoft est informée des problèmes susceptibles d’avoir un impact sur le service.
Prise en charge des opérations | Le client est responsable de la fourniture d’une liste de contacts et d’experts en matière de clientèle préférés. Microsoft en a besoin pour le cas où il s’agit d’un incident opérationnel non géré par Microsoft. <br><br>Le client est également responsable de l’enquête et de la résolution des incidents pour les appareils et services de bureau gérés non-Microsoft et en s’assurant que l’équipe Microsoft Managed Desktop Operations est toujours informée.
Infrastructure réseau, y compris VPN | Le client est responsable de l’installation, de la configuration et de la gestion (y compris le dépannage et le débogage) de toutes les infrastructures et services liés au réseau, y compris la connectivité Internet, les contrôles réseau, la configuration du proxy et la télécommande infrastructure de connectivité.<br><br>Si un proxy est configuré (dans le matériel ou le logiciel), il existe une collection d’URL qui doivent être autorisées par le proxy. Le client est responsable de la résolution des conflits ou des incompatibilités en raison de plusieurs proxys. Vous pouvez ajouter des proxys réseau spécifiques à votre organisation à l’aide des paramètres configurables. Pour plus d’informations, consultez la rubrique [configurable Settings](../working-with-managed-desktop/config-setting-ref.md#proxy).<br><br>Pour plus d’informations, consultez la rubrique [configuration du proxy](../get-ready/network.md).
Impression | Le client est responsable de l’installation, de la maintenance et de l’administration des imprimantes et des files d’attente d’impression. L’impression Cloud est recommandée, mais elle n’est pas obligatoire. 




