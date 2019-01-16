---
title: Configuration requise pour le bureau géré Microsoft
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 11/1/2018
ms.openlocfilehash: 303765d6804071b3a3de18ee412304566cbbe089
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867351"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Configuration requise pour le bureau géré Microsoft

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure); do not delete.-->
<!--from Prerequisites -->

Réussite avec l’ordinateur de bureau Microsoft commence par connues, documentée et convenus requise pour l’infrastructure du client. Cette section décrit les conditions préalables. 

Microsoft FastTrack est disponible pour aider les clients à répondre à ces exigences et vous aider à prendre part à l’espace de travail moderne en tant que Service. Pour plus d’informations, voir [Microsoft FastTrack](https://fasttrack.microsoft.com/about). 

Domaine | Détails requis
--- | ---
Gestion des licences | Une licence Microsoft 365 E5 ou équivalentes licences sont requis.<br><br>Cette licence inclut Office 365 E5, Windows 10 entreprise E5 & mobilité d’entreprise + E5 de sécurité (EMS). Pour plus d’informations, voir [Gestion des licences de Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).
Connectivité |  Tous les périphériques de bureau Microsoft requièrent une connectivité à nombreux points de terminaison de service Microsoft à partir du réseau interne d’organisation, y compris :<br>-Mise à jour Windows<br>-Banque Microsoft pour les entreprises<br>-Azure Active Directory<br>-Rapport d’erreurs Windows<br>-Analyse des incidents en ligne<br>-Connecté l’expérience utilisateur et télémétrie<br>-Application OneDrive pour Windows 10<br><br>La liste complète des requis à l’adresse IP et URL sont accessibles dans la [Configuration du serveur Proxy](../get-ready/network.md). 
Azure Active Directory |    Azure Active Directory (AD Azure) doit être la source d’autorité pour tous les comptes d’utilisateurs ou de comptes d’utilisateurs doivent être synchronisées à partir de sur site Active Directory à l’aide d’Azure AD se connecter, version 1.1.654.0 ou version ultérieure. Pour plus d’informations, voir [Azure AD se connecter](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).
Authentification |    Si Azure AD n’est pas la source d’autorité pour les comptes d’utilisateur, vous devez configurer une de ces dans Azure AD se connecter :<br>-Synchronisation de hachage mot de passe (recommandée)<br>-Authentification pass-through<br>-Fédération avec ADFS<br><br>Lorsque la définition des options d’authentification avec écriture différée Azure AD connecter le mot de passe est également requis. Pour plus d’informations, voir [écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback).<br><br>Pour plus d’informations sur les options d’authentification Azure AD, voir [options de connexion utilisateur Azure AD se connecter](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-user-signin).
Office 365 |    Il est vivement recommandé de migrer vers le nuage que les services suivants :<br>-E-mail - migrer vers le nuage boîtes aux lettres Exchange online ou être configuré avec Exchange Online hybride avec Exchange 2013 ou version ultérieure, sur site.<br>Fichiers et dossiers à-migrer vers SharePoint Online/Office 365.<br>-Skype pour les entreprises – migration à Skype pour les entreprises en ligne.
Gestion des périphériques | Microsoft Intune - une solution Mobile Device Manager en nuage uniquement (non hybrides) est nécessaire, qui autorise les administrateurs informatiques à gérer les périphériques de bureau Microsoft à l’aide d’une console web qui est accessible à partir de n’importe où dans le monde. Microsoft Intune est la solution Mobile Device Manager requise.<br><br>Pour plus d’informations, voir [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune). 
Sauvegarde et récupération | Ordinateur de bureau Microsoft requiert synchronisé avec OneDrive entreprise pour la protection des fichiers. Tous les fichiers non synchronisés vers OneDrive entreprise ne sont pas garantis par Microsoft de bureau et peuvent être perdues au cours d’échanges de périphériques ou appels au support technique nécessitant une réinitialisation du périphérique. Ordinateur de bureau Microsoft ne gère pas les lecteurs réseau mappés.  

[Découvrez comment remplir les conditions préalables pour l’inscription de l’ordinateur de bureau Microsoft.](../get-ready/index.md)

Lorsque vous êtes prêt à prendre en main de bureau Microsoft, contactez votre responsable de compte Microsoft. 
