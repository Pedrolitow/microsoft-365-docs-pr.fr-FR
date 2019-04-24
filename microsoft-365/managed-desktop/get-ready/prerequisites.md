---
title: Conditions préalables pour le bureau géré Microsoft
description: ''
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 11/1/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 8d9c008af9531bc5b829d248665dc5b58ac6034b
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32277385"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Conditions préalables pour le bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Le succès avec le bureau géré Microsoft commence par des exigences connues, documentées et convenues pour l'infrastructure du client. Cette section décrit ces exigences infastructure. 

Microsoft FastTrack est disponible pour aider les clients à répondre à ces exigences et vous aider à vous préparer à participer au bureau géré Microsoft. Pour plus d'informations, consultez la rubrique [Microsoft FastTrack](https://fasttrack.microsoft.com/about). 

Domaine | Détails des éléments prérequis
--- | ---
Gestion des licences | L'une des options de licence suivantes doit être attribuée à chaque utilisateur MMD:<br>-Microsoft 365 E5<br>-Microsoft 365 E3, Enterprise Mobility + Security E5 et Windows 10 entreprise E5<br>-Office 365 E3, Enterprise Mobility + Security E5 et Windows 10 entreprise E5<br><br>Les clients d'accord entreprise existants peuvent avoir besoin de conseils pour activer l'activation d'abonnement Windows 10 entreprise dans le client Azure AD. Pour plus d'informations, consultez la rubrique [deploy Windows 10 Enterprise licenses](https://docs.microsoft.com/windows/deployment/deploy-enterprise-licenses#enabling-subscription-activation-with-an-existing-ea).<br><br>Les licences de produit peuvent être affectées à l'aide de groupes de sécurité en configurant des licences Azure AD Group. Pour plus d'informations, consultez la rubrique [What is Group-based Licensing in Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).<br><br>Pour plus d'informations sur les licences disponibles, consultez la rubrique [Microsoft 365 Licensing](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).
Connectivité |  Tous les périphériques de bureau gérés Microsoft nécessitent une connectivité à de nombreux points de terminaison de service Microsoft à partir du réseau d'entreprise.<br><br>Pour obtenir la liste complète des adresses IP et des URL requises, voir [Configuration réseau](../get-ready/network.md). 
Azure Active Directory |    Azure Active Directory (Azure AD) doit être la source d'autorité pour tous les comptes d'utilisateur, ou les comptes d'utilisateur doivent être synchronisés à partir d'Active Directory local à l'aide de la dernière version prise en charge d'Azure AD Connect.<br><br>Pour plus d'informations sur Azure AD Connect, reportez-vous à la rubrique [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/whatis-azure-ad-connect).<br><br>Pour plus d'informations sur les versions Azure AD Connect prises en charge, reportez-vous à la rubrique [Azure ad Connect: version Release History](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history).
Authentification |    Si Azure AD n'est pas la source d'autorité pour les comptes d'utilisateur, vous devez configurer l'un des éléments suivants dans Azure AD Connect:<br>-Synchronisation de hachage de mot de passe<br>-Authentification directe<br>-Fédération avec ADFS<br><br>Lors de la configuration des options d'authentification avec Azure AD Connect, l'écriture différée du mot de passe est également requise. Pour plus d'informations, consultez la rubrique [écriture différée du mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). <br><br>Pour plus d'informations sur les options d'authentification avec Azure AD, reportez-vous à la rubrique [options de connexion de l'utilisateur Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-user-signin).
Office 365 |    Bien qu'il ne soit pas nécessaire de s'inscrire avec Microsoft maNaged Desktop, il est vivement recommandé de migrer les services suivants vers le Cloud:<br>-Courrier électronique: migrez vers des boîtes aux lettres en nuage, Exchange Online ou configurez Exchange Online hybride avec Exchange 2013 ou une version ultérieure, en local.<br>-Fichiers et dossiers: migrez vers OneDrive entreprise/SharePoint Online.<br>-Outils de collaboration en ligne: migrer vers Teams.
Gestion des périphériques | Les périphériques de bureau gérés Microsoft nécessitent une gestion à l'aide de Microsoft Intune. Intune doit être défini en tant qu'autorité de gestion des appareils mobiles.<br><br>Pour plus d'informations, consultez la rubrique [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune). 
Sauvegarde et récupération des données | Le bureau géré Microsoft requiert la synchronisation des fichiers avec OneDrive entreprise pour la protection. Les fichiers qui ne sont pas synchronisés avec OneDrive entreprise ne sont pas assurés par le bureau géré Microsoft et peuvent être perdus pendant les échanges d'appareils, ou les appels de prise en charge qui nécessitent une réinitialisation de l'appareil.<br><br>Bien que cela ne soit pas obligatoire, le bureau géré Microsoft recommande vivement la migration des lecteurs réseau mappés vers la solution cloud appropriée.  

Lorsque vous êtes prêt à commencer à utiliser Microsoft maNaged Desktop, contactez votre gestionnaire de compte Microsoft. 
