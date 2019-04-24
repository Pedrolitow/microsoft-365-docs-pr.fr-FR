---
title: Rôles et responsabilités du bureau géré Microsoft
description: Cette rubrique décrit les rôles et les responsabilités fournis par Microsoft pour le bureau géré Microsoft.
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 161be07907754cdd7a0cd88dd3342d4b5e3c72e4
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32283557"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Rôles et responsabilités du bureau géré Microsoft


<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Lors de l'enregistrement de votre organisation dans Microsoft maNaged Desktop, qu'est-ce que Microsoft vous fait pour vous? Quelles sont les responsabilités de votre organisation?

## <a name="microsofts-roles-and-responsibilities"></a>Rôles et responsabilités de Microsoft

Vous trouverez ci-dessous quelques rôles et responsabilités clés qui seront fournis par Microsoft.

Rôle ou responsabilité | Description
--- | ---
Gestion des stratégies MDM | Microsoft appliquera les stratégies MDM conformément aux meilleures pratiques et envisagez de demander des modifications de stratégie. Nous allons également modifier votre client comme indiqué dans stratégies de [périphérique](../service-description/device-policies.md).
Prise en charge de l'utilisateur final | Microsoft fournit la prise en charge de l'utilisateur final pour les appareils, les fenêtres et la suite de produits Office pour tous les utilisateurs dans l'application d'aide qui est préinstallée sur tous les appareils de bureau gérés par Microsoft. 
Prise en charge du service bureau géré Microsoft | Microsoft fournira une assistance aux services informatiques des clients par le biais d'une équipe Microsoft maNaged Desktop Operations. Cette équipe prend en charge la résolution des problèmes techniques, les demandes de modification et la gestion des incidents pour l'environnement de bureau géré Microsoft du client. Pour plus d'informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).
Surveillance de la sécurité | Microsoft analysera les périphériques de bureau gérés par le client à l'aide de Windows Defender ATP. Si une menace est détectée par le centre d'opérations de sécurité du bureau géré Microsoft, Microsoft avertit le client, isole l'appareil et corrige le problème à distance. Pour plus d'informations, consultez la rubrique [sécurité](../service-description/security.md).
Mise à jour de la surveillance et de la gestion | Microsoft analysera activement les périphériques de bureau gérés par le client pour s'assurer que les dernières mises à jour de qualité et de fonctionnalité sont installées pour Microsoft Windows et Microsoft Office. Pour plus d'informations, voir [Comment les mises à jour sont gérées](../service-description/updates.md).
Groupement d'utilisateurs et d'appareils | Microsoft maNaged Desktop Operations Team créera et gérera les groupes d'utilisateurs et d'appareils requis dans le cadre des opérations informatiques. Aucune modification de l'appartenance ou de la configuration n'est autorisée pour ces groupes. La modification de ces groupes peut entraîner une configuration inattendue des appareils et une perte de fonctionnalité. Pour tout problème ou question concernant ces groupes une fois établi, les administrateurs informatiques peuvent contacter les opérations de bureau géré Microsoft. Pour plus d'informations, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).

## <a name="your-roles-and-responsibilities"></a>Vos rôles et responsabilités

Vous trouverez ci-dessous un ensemble supplémentaire de rôles et de responsabilités courants qui ne sont pas fournis par Microsoft, mais qui sont requis pour un déploiement réussi. Il n'est pas exhaustif, mais applicable à la plupart des organisations. Il existe quelques éléments ci-dessous que Microsoft et le client partagent responsibilties. 

Rôle ou responsabilité | Description
--- | ---
Gestion des modifications | Microsoft avertira les clients, à l'avance, quand les modifications devront être apportées à leur environnement de bureau géré Microsoft. Le client doit avoir son propre processus de gestion des modifications et disposer d'un contact établi avec l'équipe des opérations de bureau géré Microsoft. Le client doit également disposer de ressources pour vérifier et approuver ces modifications. Pour plus d'informations, consultez la rubrique [opérations et surveillance](../service-description/operations-and-monitoring.md).  
Gestion des identités | Le client est responsable de la création de comptes d'utilisateurs, de l'affectation d'utilisateurs à des groupes et de la mise à jour des métadonnées. 
Configuration et gestion d'Office 365 | Microsoft est chargé de s'assurer que les applications Office sont déployées sur les utilisateurs finaux et que ces applications sont tenues à jour. <br><br> Le client est responsable de la gestion des services et des stratégies Office 365, y compris les responsabilités d'administration d'Exchange Online:<br>-Administration de la messagerie<br>-Configuration de la boîte aux lettres et des règles<br>-Gestion Exchange sur site<br><br>Le client est également responsable des outils de collaboration, de l'administration de SharePoint Server, de la gestion de domaine, de la sécurité et des stratégies d'information définies dans le portail d'administration Office 365. 
Prise en charge de l'utilisateur final | Le client est responsable de la fourniture de la prise en charge des utilisateurs finaux pour: <br>-Infrastructure de site: toutes les connexions réseau et Internet, l'infrastructure VPN et la configuration client, la salle de conférence locale, les imprimantes, le serveur proxy et la configuration, les pare-feu.<br><br>-Ressources Cloud à l'échelle de l'entreprise: messagerie, SharePoint, services de collaboration et autre infrastructure cloud qui se rapportent à la technologie à l'échelle de l'entreprise.<br><br>-Ligne professionnelle et toute autre application spécifique à une société.
Applications | Microsoft fournira des conseils de déploiement pour les applications approuvées à l'aide d'Intune sur demande.<br><br>Le client est responsable des éléments suivants:<br>-Fourniture d'une liste d'applications pour leur organisation (en dehors des applications Office 365)<br>-Gestion des licences d'application<br>, Avec le type et la quantité corrects de licences<br>-Affectation d'application<br>– Affectation d'applications à des groupes d'utilisateurs Azure AD<br>-Mises à jour de l'application<br>– Surveillance, empaquetage et déploiement de la fonctionnalité et des mises à jour de sécurité de l'application<br>-Test d'application utilisateur (UAT)<br>-Fourniture d'un package déployable approprié<br><br>Pour plus d'informations, consultez la rubrique [applications](../get-ready/apps.md)
Surveillance et réponse de la sécurité | Le client est chargé d'examiner et de résoudre les incidents pour les appareils de bureau gérés non-Microsoft et de s'assurer que l'équipe des opérations de bureau géré Microsoft est informée des problèmes susceptibles d'avoir un impact sur le service.
Prise en charge des opérations | Le client est responsable de la fourniture d'une liste de contacts et d'experts en matière de clientèle préférés. Microsoft en a besoin pour le cas où il s'agit d'un incident opérationnel non géré par Microsoft. <br><br>Le client est également responsable de l'enquête et de la résolution des incidents pour les appareils et services de bureau gérés non-Microsoft et en s'assurant que l'équipe Microsoft maNaged Desktop Operations est toujours informée.
Infrastructure réseau, y compris VPN | Le client est responsable de l'installation, de la configuration et de la gestion (y compris le dépannage et le débogage) de toutes les infrastructures et services liés au réseau, y compris la connectivité Internet, les contrôles réseau, la configuration du proxy et la télécommande infrastructure de connectivité.<br><br>Si un proxy est configuré (dans le matériel ou le logiciel), il existe une collection d'URL qui doivent être autorisées par le proxy. Le client est responsable de la résolution des conflits ou des incompatibilités en raison de plusieurs proxys. Vous pouvez ajouter des proxys réseau spécifiques à votre organisation à l'aide des paramètres configurables. Pour plus d'informations, [](../working-with-managed-desktop/config-setting-ref.md#proxy)consultez la rubrique configurable Settings.<br><br>Pour plus d'informations, consultez la rubrique [configuration du proxy](../get-ready/network.md).
Impression | Le client est responsable de l'installation, de la maintenance et de l'administration des imprimantes et des files d'attente d'impression. L'impression Cloud est recommandée, mais elle n'est pas obligatoire. 




