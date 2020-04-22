---
title: Comment les fonctionnalités de protection de Microsoft 365 Business Premium correspondent aux paramètres Intune
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 8/13/2018
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: aad21b1a-c775-469a-b89c-c5d1d59d27db
description: Découvrez comment les fonctionnalités de protection de Microsoft 365 Business Premium correspondent aux paramètres Intune. L’abonnement vous offre une licence pour modifier les paramètres Intune.
ms.openlocfilehash: 572d3364e465067536e8369b49404d3d1de1bb5b
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43633240"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Comment les fonctionnalités de protection de Microsoft 365 Business Premium correspondent aux paramètres Intune

## <a name="android-and-ios-application-protection-settings"></a>Paramètres de protection des applications Android et iOS

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Android et iOS sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, connectez-vous à l’aide de vos informations d’identification d’administrateur Microsoft 365 Business Premium, accédez à **centres d’administration**, puis à **Intune**.
  
 > [!IMPORTANT]
 > 
 > Un abonnement Microsoft 365 Business Premium vous offre une licence pour modifier tous les paramètres Intune. Voir [Introduction to Intune pour commencer.](https://docs.microsoft.com/intune/introduction-intune)
  
Sélectionnez le nom &mdash; de la stratégie souhaitée par exemple, stratégie d’application &mdash; pour Android, puis choisissez **paramètres de stratégie**.
  
Sous **Protéger les fichiers de travail en cas de perte ou de vol des appareils**
  
|**Paramètre de stratégie d'application Android ou iOS**|**Paramètre(s) Intune**|
|:-----|:-----|
|Supprimer les fichiers de travail d'un appareil inactif après  <br/> |Intervalle hors connexion (jours) avant la réinitialisation des données d'application  <br/> |
|Obliger les utilisateurs à enregistrer les fichiers de travail dans OneDrive Entreprise  <br/> Notez que seul OneDrive Entreprise est autorisé  <br/> |Sélectionnez dans quels services de stockage les données d'entreprise peuvent être enregistrées  <br/> |
|||
   
Sous **Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles**
  
|**Paramètre de stratégie d'application Android ou iOS**|**Paramètre(s) Intune**|
|:-----|:-----|
|Supprimer les fichiers de travail d'un appareil inactif après  <br/> |Intervalle hors connexion (jours) avant la réinitialisation des données d'application  <br/> |
|Obliger les utilisateurs à enregistrer les fichiers de travail dans OneDrive Entreprise  <br/> Notez que seul OneDrive Entreprise est autorisé  <br/> |Sélectionnez dans quels services de stockage les données d'entreprise peuvent être enregistrées  <br/> |
|Chiffrer les fichiers professionnels  <br/> |Chiffrer les données des applications  <br/> |
|Sous **Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles** <br/> ||
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  <br/> | Exiger un code confidentiel d'accès  <br/>  Cela définit également :  <br/> **Autoriser un code confidentiel simple** sur **Oui** <br/> **Longueur du code confidentiel** sur 4  <br/> **Autoriser les empreintes digitales à la place du code confidentiel** sur **Oui** <br/> **Désactiver le code confidentiel de l'application quand le code confidentiel de l'appareil est géré** sur **Non** <br/> |
|Réinitialiser le code confidentiel lorsque la connexion échoue autant de fois (cela est désactivé si le code confidentiel n’est pas requis)  <br/> |Nombre de tentatives avant réinitialisation du code confidentiel  <br/> |
|Demander aux utilisateurs de se reconnecter après l’inactivité des applications Office (cette opération est désactivée si le code confidentiel n’est pas requis)  <br/> | Revérifier les conditions d'accès requises après (minutes)  <br/>  Cela définit également ce qui suit :  <br/> Le **Délai expiration** est défini en minutes  <br/>  Il s'agit du nombre de minutes défini dans Microsoft 365 Entreprise.  <br/> **Période de grâce hors connexion** est défini sur 720 minutes par défaut  <br/> |
|Refuser l'accès aux fichiers professionnels sur les appareils jailbreakés ou rootés  <br/> |Bloquer l'exécution des applications gérées sur les appareils jailbreakés ou rootés  <br/> |
|Autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  <br/> | Restreindre les opérations Couper, Copier et Coller avec d’autres applications  <br/>  Si l’option Microsoft 365 Business Premium est définie sur **activé**, ces trois options sont également définies sur **toutes les applications** dans Intune :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** <br/> **Autoriser l'application à recevoir des données d'autres applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** <br/>  Si l'option Microsoft 365 Entreprise est **Activée**, toutes les options Intune sont définies comme suit :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** est défini sur **Applications gérées par une stratégie** <br/> **Autoriser l'application à recevoir des données d'autres applications** est défini sur **Toutes les applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** est défini sur **Applications gérées par une stratégie avec Coller dans** <br/> |
|||
   
## <a name="windows-10-app-protection-settings"></a>Paramètres de protection des applications Windows 10

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, connectez-vous à l’aide de vos informations d’identification d’administrateur Microsoft 365 Business Premium et accédez au [portail Azure](https://portal.azure.com). Sélectionnez **plus de services**, puis tapez Intune dans le **filtre**. Sélectionnez \> **stratégie d’application** **protection des applications Intune** .
  
 > [!IMPORTANT]
 >
 >Un abonnement Microsoft 365 Business Premium vous offre une licence pour modifier uniquement les paramètres Intune qui correspondent aux paramètres disponibles dans Microsoft 365 Business Premium. 
  
Pour explorer les paramètres disponibles, sélectionnez le nom de la stratégie souhaitée, puis choisissez **général, affectations**, **applications autorisées**, **exonération d’applications**, **paramètres obligatoires**ou **Paramètres avancés** dans le volet de navigation de gauche. 
  
|**Paramètre de stratégie des applications Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Chiffrer les fichiers professionnels  <br/> |**Paramètres avancés** \> **Protection des données**: **Révoquer les clés de chiffrement lors de la désinscription** et **Révoquer l'accès aux données protégées quand l'appareil s'inscrit à MDM** sont tous deux **activés**.  <br/> |
|Empêcher les utilisateurs de copier des données d’entreprise dans des fichiers personnels.  <br/> |**Paramètres requis** \> **Mode Protection des informations Windows**. **On** dans Microsoft 365 Business Premium Maps to : **Hide Overrides**, **off** dans Microsoft 365 Business Premium Maps to : **off**.  <br/> |
|Contrôle de l'accès aux documents Office  <br/> | Si ce paramètre est **activé** dans Microsoft 365 Business Premium, puis  <br/> **Paramètres avancés** \> **Accès**, **Utiliser Windows Hello Entreprise comme mode de connexion à Windows** est **Activé**, avec les paramètres supplémentaires suivants :  <br/> **Définir le nombre minimal de caractères obligatoires dans le code confidentiel** est défini sur **4**.  <br/> **Configurer l'utilisation des lettres majuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des majuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des lettres minuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des minuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des caractères spéciaux dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation de caractères spéciaux dans le code confidentiel**.  <br/> **Spécifier la période (en jours) pendant laquelle un code confidentiel peut être utilisé avant que le système demande à l’utilisateur de modifier** est défini sur **0**.  <br/> **Spécifier le nombre d'anciens codes confidentiels associés à un compte d'utilisateur qui peuvent être réutilisés** est défini sur **0**.  <br/> **Nombre d'échecs d'authentification autorisés avant la réinitialisation de l'appareil** est défini comme dans Microsoft 365 Entreprise (5 par défaut).  <br/> **Durée maximale (en minutes) autorisée pendant laquelle l'appareil peut rester inactif avant d'être verrouillé par un mot de passe ou un code confidentiel** est défini comme dans Microsoft 365 Entreprise.  <br/> |
|Activer la récupération des données protégées  <br/> |**Paramètres avancés** \> **Protection des données**: **Afficher l'icône de protection des données d'entreprise** et **Utiliser Azure RMS pour WIP** sont définis sur **Activé**.  <br/> |
|Protéger les autres emplacements cloud de l'entreprise  <br/> |**Paramètres avancés** \> **Domaines protégés** et **Ressources cloud** affichent les domaines et les sites SharePoint.  <br/> |
|Les fichiers utilisés par ces applications sont protégés  <br/> |Les applications protégées sont répertoriées dans **Applications autorisées**.  <br/> |
|||
   
## <a name="windows-10-device-protection-settings"></a>Paramètres de protection des appareils Windows 10

Le tableau suivant décrit en détail comment les paramètres de configuration des appareils Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, connectez-vous à l’aide de vos informations d’identification d’administrateur Microsoft 365 Business Premium, accédez au [portail Azure](https://portal.azure.com), sélectionnez **autres services**et tapez Intune dans le **filtre**, puis sélectionnez **profils**de **configuration** \> d’appareil **Intune** \> . Sélectionnez ensuite **Stratégie d'appareils pour Windows 10** \> **Propriétés** \> **Paramètres**.
  
|**Paramètre de stratégie d'appareil Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Protéger les ordinateurs des virus et autres menaces à l'aide de l'antivirus Windows Defender  <br/> |Autoriser la surveillance en temps réel = Activé  <br/> Autoriser la protection cloud = Activé  <br/> Demander aux utilisateurs l'autorisation d'envoyer des échantillons = Envoyer automatiquement des échantillons sécurisés (envoi automatique non PII par défaut)  <br/> |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  <br/> |**SmartScreen** dans **Paramètres du navigateur Edge** est défini sur **Obligatoire**.  <br/> |
|Désactiver l'écran d'un appareil resté inactif pendant (minutes)  <br/> |Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil (minutes)  <br/> |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  <br/> |Stratégie URI personnalisée  <br/> |
|Autoriser les utilisateurs à accéder à Cortana  <br/> |En **général** \> , **Cortana** est définie sur **bloquer** dans Intune lorsque la valeur est définie sur **désactivé** dans Microsoft 365 Business Premium.  <br/> |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  <br/> |**Windows en vedette**, tous bloqués si ce paramètre est défini sur **désactivé** dans Microsoft 365 Business Premium.  <br/> |
|Maintenir les appareils Windows 10 à jour automatiquement  <br/> | Ce paramètre est dans **Microsoft Intune** \> **service updates-Windows 10 Update Rings**, choose **Update Policy for Windows 10 Devices**, Then **Properties** \> **Settings**.  <br/>  Lorsque le paramètre Microsoft 365 Business Premium est **activé**, tous les paramètres suivants sont définis :  <br/> La **branche de service** est définie sur **CB** (CBB lorsque cette fonctionnalité est désactivée dans Microsoft 365 Business Premium).  <br/> **Mises à jour de produits Microsoft** est défini sur **Autoriser**.  <br/> **Pilotes Windows** est défini sur **Autoriser**.  <br/> **Comportement des mises à jour automatiques** est défini sur **Installation automatique à l'heure de la maintenance** avec ce qui suit :  <br/> **Démarrage après ces heures** est défini sur **06:00**.  <br/> **Fin des heures actives** est défini sur **22:00**.  <br/> **Période de report des mises à jour qualité (jours)** est défini sur **0**.  <br/> **Période de report des mises à jour des fonctionnalités (jours)** est défini sur **0**.  <br/> **Mode de téléchargement de l'optimisation de la distribution** est défini sur **HTTP fusionné avec un appairage derrière le même NAT**.  <br/> |
|||
   

