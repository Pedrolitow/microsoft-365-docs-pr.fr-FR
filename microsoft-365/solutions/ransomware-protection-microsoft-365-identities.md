---
title: Étape 3. Protéger vos identités
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: rançongiciel, rançongiciel géré par les humains, rançongiciel géré par l’homme, HumOR, attaque par extorsion, attaque par rançongiciel, chiffrement, cryptovirologie
description: Utilisez des connexions sécurisées et l’accès conditionnel pour protéger vos ressources Microsoft 365 contre les attaques par rançongiciel.
ms.openlocfilehash: 5761cb402be3fb0be907be8f3677a8e3ecbfd875
ms.sourcegitcommit: 7e7effd8ef4ffe75cdee7bb8517fec8608e4c230
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2021
ms.locfileid: "59444549"
---
# <a name="step-3-protect-identities"></a>Étape 3. Protéger vos identités

Utilisez les sections suivantes pour protéger votre organisation contre la compromission des informations d’identification, qui constitue généralement la première étape d’une attaque par rançongiciel plus importante.

## <a name="increase-sign-in-security"></a>Renforcer la sécurité de la connexion

Utilisez [l’authentification sans mot de passe](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) pour les comptes d’utilisateur dans Azure Active Directory (Azure AD).

Pendant la transition vers l’authentification sans mot de passe, utilisez ces meilleures pratiques pour les comptes d’utilisateur qui utilisent toujours l’authentification par mot de passe :

- Bloquez les mots de passe faibles et personnalisés connus avec la [Protection de mots de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad).
- Étendez le blocage des mots de passe faibles et personnalisés connus à vos [Active Directory Domain Services (AD DS) locaux avec Protection de mots de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).
- Autorisez vos utilisateurs à modifier leurs propres mots de passe avec la [Réinitialisation du mot de passe libre-service (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks).

Ensuite, implémentez les [Stratégies communes pour les identités et l’accès aux appareils](/microsoft-365/security/office-365-security/identity-access-policies). Ces stratégies fournissent une sécurité plus élevée pour l’accès aux services cloud Microsoft 365. 

Pour les utilisateurs qui se connectent, ces stratégies sont les suivantes :

- Exiger l’authentification multifacteur (MFA) pour les comptes prioritaires (immédiatement) et finalement tous les comptes d’utilisateurs.
- Exiger l’utilisation de l’authentification multifacteur pour les connexions à risque élevé.
- Exiger que les utilisateurs à risque élevé avec des connexions à risque élevé modifient leurs mots de passe.

## <a name="prevent-privilege-escalation"></a>Empêcher l’escalade des privilèges

Utilisez les meilleures pratiques ci-après :

- Implémentez le principe du [privilège minimum](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) et utilisez la protection par mot de passe comme décrit dans [Renforcer la sécurité de la connexion](#increase-sign-in-security) pour les comptes d’utilisateur qui utilisent encore des mots de passe pour leur connexion. 
- Évitez d’utiliser des comptes de service de niveau administrateur à l’échelle du domaine. 
- Limitez les privilèges d’administration locaux pour restreindre l’installation de Chevaux de Troie autorisant un accès à distance (RAT) et d’autres applications indésirables.
- Utilisez l’accès conditionnel Azure AD pour valider explicitement la confiance des utilisateurs et des stations de travail avant d’autoriser l’accès aux portails d’administration. Consultez [cet exemple](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management) pour le Portail Azure.
- Activez la gestion des mots de passe de l’administrateur local.
- Déterminez l’endroit où les comptes à privilèges élevés se connectent et exposent des informations d’identification. Les comptes à privilèges élevés ne doivent pas être présents sur les stations de travail.
- Désactivez le stockage local des mots de passe et des informations d’identification.

## <a name="impact-on-users-and-change-management"></a>Impact sur les utilisateurs et la gestion des modifications

Vous devez sensibiliser les utilisateurs de votre organisation aux :

- Nouvelles exigences en matière de mots de passe plus forts.
- Modifications apportées aux processus de signature, telles que l’utilisation obligatoire de l’authentification multifacteur et l’enregistrement de la méthode d’authentification secondaire MFA.
- Utilisation de la maintenance des mots de passe avec SSPR. Par exemple, plus aucun appel au support technique pour une réinitialisation de mot de passe.
- L’invite pour exiger une authentification multifacteur ou une modification de mot de passe pour les connexions considérées comme risquées.

## <a name="resulting-configuration"></a>Configuration résultante

Voici la protection pour votre client contre les rançongiciels concernant les étapes 1 à 3.

![Protection contre les rançongiciels pour votre client Microsoft 365 après l’étape 3](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step3.png)

## <a name="next-step"></a>Étape suivante

[![Étape 4 pour la protection contre les rançongiciels avec Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step4.png)](ransomware-protection-microsoft-365-devices.md)

Poursuivez [l’étape 4](ransomware-protection-microsoft-365-devices.md) pour protéger les appareils (points de terminaison) dans votre client Microsoft 365. 
