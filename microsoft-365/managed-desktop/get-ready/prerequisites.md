---
title: Conditions préalables pour le bureau géré Microsoft
description: ''
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 6351dd4696ed21b177dc2789b18c380fba4ebe91
ms.sourcegitcommit: 6b5370cded5d8259c9ed561eed324227f74c410b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "36171724"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Conditions préalables pour le bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Cette rubrique décrit les exigences en matière d’infrastructure que vous devez respecter pour garantir la réussite avec le bureau géré Microsoft. 

Microsoft FastTrack est disponible pour vous aider à répondre à ces exigences et vous aider à vous préparer à participer au bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [Microsoft FastTrack](https://fasttrack.microsoft.com/about). 

Domaine | Détails des éléments prérequis
--- | ---
Licences |Microsoft Managed Desktop requiert l’une des deux licences (ou équivalences) Microsoft 365 suivantes:<br>-Microsoft 365 E5<br>-Microsoft 365 E3 avec le complément de sécurité Microsoft 365 E5<br><br>Pour plus d’informations sur les licences disponibles, consultez la rubrique [Microsoft 365 Licensing](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).
Connectivité |  Tous les périphériques de bureau gérés Microsoft nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d’entreprise.<br><br>Pour obtenir la liste complète des adresses IP et des URL requises, voir [Configuration réseau](../get-ready/network.md). 
Azure Active Directory |    Azure Active Directory (Azure AD) doit être la source d’autorité pour tous les comptes d’utilisateur, ou les comptes d’utilisateur doivent être synchronisés à partir d’Active Directory local à l’aide de la dernière version prise en charge d’Azure AD Connect.<br><br>L’itinérance de l’état de l' [entreprise](https://docs.microsoft.com/azure/active-directory/devices/enterprise-state-roaming-overview) doit être activée pour les utilisateurs du bureau géré Microsoft.<br><br>Pour plus d’informations sur Azure AD Connect, reportez-vous à la rubrique [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect).<br><br>Pour plus d’informations sur les versions Azure AD Connect prises en charge, reportez-vous à la rubrique [Azure ad Connect: version Release History](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history).
Authentification |    Si Azure AD n’est pas la source d’autorité pour les comptes d’utilisateur, vous devez configurer l’un des éléments suivants dans Azure AD Connect:<br>-Synchronisation de hachage de mot de passe<br>-Authentification directe<br>-Fédération avec ADFS<br><br>Lors de la configuration des options d’authentification avec Azure AD Connect, l’écriture différée de mot de passe est également recommandée. Pour plus d’informations, consultez la rubrique [écriture différée du mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). <br><br>Pour plus d’informations sur les options d’authentification avec Azure AD, reportez-vous à la rubrique [options de connexion de l’utilisateur Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-user-signin).
Office 365 |    OneDrive entreprise doit être activé pour les utilisateurs du bureau géré Microsoft.<br><br>Bien qu’il ne soit pas nécessaire de s’inscrire avec Microsoft Managed Desktop, nous vous recommandons vivement de migrer les services suivants vers le Cloud:<br>-Email: migrer vers des boîtes aux lettres en nuage, Exchange Online ou une configuration avec Exchange Online hybride avec Exchange 2013 ou version ultérieure, en local.<br>-Fichiers et dossiers: migrer vers OneDrive entreprise ou SharePoint Online.<br>-Outils de collaboration en ligne: migrer vers Teams.
Gestion des périphériques | Les périphériques de bureau gérés Microsoft nécessitent une gestion à l’aide de Microsoft Intune. Intune doit être défini en tant qu’autorité de gestion des appareils mobiles.<br><br>Pour plus d’informations, consultez la rubrique [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune). 
Sauvegarde et récupération des données | Le bureau géré Microsoft requiert la synchronisation des fichiers avec OneDrive entreprise pour la protection. Tous les fichiers qui ne sont pas synchronisés avec OneDrive entreprise ne sont pas assurés par le bureau géré Microsoft et peuvent être perdus pendant les échanges d’appareils ou les appels de prise en charge exigeant une réinitialisation de l’appareil.<br><br>Bien que cela ne soit pas obligatoire, le bureau géré Microsoft recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée. 

Lorsque vous êtes prêt à commencer à utiliser Microsoft Managed Desktop, contactez votre gestionnaire de compte Microsoft. 
