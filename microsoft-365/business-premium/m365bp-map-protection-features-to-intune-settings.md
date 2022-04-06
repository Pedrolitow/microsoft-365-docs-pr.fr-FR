---
title: Comment les fonctionnalités de protection Microsoft 365 Business Premium sont-Intune paramètres de protection ?
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
ms.date: 04/01/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: aad21b1a-c775-469a-b89c-c5d1d59d27db
description: Découvrez comment les fonctionnalités de protection Microsoft 365 Business Premium sont mapp Intune paramètres. L’abonnement vous fournit une licence pour modifier Intune paramètres.
ms.openlocfilehash: cd3bf2c9db6379b70e02a14b6f07d56b3552cbd2
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635239"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Comment les fonctionnalités de protection Microsoft 365 Business Premium sont-Intune paramètres de protection ?

> [!NOTE]
> Microsoft Defender pour les PME est en Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Cette offre offre des fonctionnalités de sécurité supplémentaires pour les appareils. [En savoir plus sur Defender pour les entreprises](../security/defender-business/mdb-overview.md).

## <a name="android-and-ios-application-protection-settings"></a>Paramètres de protection des applications Android et iOS

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Android et iOS sont mis en correspondance avec les paramètres Intune.
  
Pour trouver le paramètre Intune, connectez-vous à l’Microsoft 365 Business Premium vos informations d’identification d’administrateur, puis dans les centres d’administration **,** **puis Intune**.
  
 > [!IMPORTANT]
 > 
 > Un abonnement Microsoft 365 Business Premium vous donne une licence pour modifier tous les paramètres Intune paramètres. [Consultez l’introduction Intune la mise en place.](/intune/introduction-intune)
  
Sélectionnez le nom de stratégie que vous souhaitez &mdash; , par exemple, Stratégie d’application pour Android &mdash; , puis **sélectionnez Paramètres de stratégie**.
  
Sous **Protéger les fichiers de travail en cas de perte ou de vol des appareils**
  
|**Paramètre de stratégie d'application Android ou iOS**|**Paramètre(s) Intune**|
|:-----|:-----|
|Supprimer les fichiers de travail d'un appareil inactif après  |Intervalle hors connexion (jours) avant la réinitialisation des données d'application  |
|Obliger les utilisateurs à enregistrer les fichiers de travail dans OneDrive Entreprise  <br/> Notez que seul OneDrive Entreprise est autorisé  |Sélectionnez dans quels services de stockage les données d'entreprise peuvent être enregistrées  |
   
Sous **Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles**
  
|**Paramètre de stratégie d'application Android ou iOS**|**Paramètre(s) Intune**|
|:-----|:-----|
|Supprimer les fichiers de travail d'un appareil inactif après  |Intervalle hors connexion (jours) avant la réinitialisation des données d'application  |
|Obliger les utilisateurs à enregistrer les fichiers de travail dans OneDrive Entreprise  <br/> Notez que seul OneDrive Entreprise est autorisé  |Sélectionnez dans quels services de stockage les données d'entreprise peuvent être enregistrées  |
|Chiffrer les fichiers professionnels  |Chiffrer les données des applications  |
|Sous **Gérer la façon dont les utilisateurs accèdent aux fichiers Office sur appareils mobiles** ||
|Exiger un code confidentiel ou une empreinte pour accéder aux applications Office  | Exiger un code confidentiel d'accès  <br/>  Cela définit également :  <br/> **Autoriser un code confidentiel simple** sur **Oui** <br/> **Longueur du code confidentiel** sur 4  <br/> **Autoriser les empreintes digitales à la place du code confidentiel** sur **Oui** <br/> **Désactiver le code confidentiel de l'application quand le code confidentiel de l'appareil est géré** sur **Non** |
|Réinitialiser le code confidentiel en cas d’échec de la connexion à ce nombre de fois (cette désactivation est désactivée si le code confidentiel n’est pas obligatoire)  |Nombre de tentatives avant réinitialisation du code confidentiel  |
|Exiger que les utilisateurs se connectent à nouveau Office applications sont inactives (cette désactivation est désactivée si le code confidentiel n’est pas requis)  | Revérifier les conditions d'accès requises après (minutes)  <br/>  Cela définit également ce qui suit :  <br/> Le **Délai expiration** est défini en minutes  <br/>  Il s'agit du nombre de minutes défini dans Microsoft 365 Entreprise.  <br/> **Période de grâce hors connexion** est défini sur 720 minutes par défaut  |
|Refuser l'accès aux fichiers professionnels sur les appareils jailbreakés ou rootés  |Bloquer l'exécution des applications gérées sur les appareils jailbreakés ou rootés  |
|Autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  | Restreindre les opérations Couper, Copier et Coller avec d’autres applications  <br/>  Si l’option Microsoft 365 Business Premium est définie sur **On**, ces trois options sont également définies sur **Toutes** les applications Intune :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** <br/> **Autoriser l'application à recevoir des données d'autres applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** <br/>  Si l'option Microsoft 365 Entreprise est **Activée**, toutes les options Intune sont définies comme suit :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** est défini sur **Applications gérées par une stratégie** <br/> **Autoriser l'application à recevoir des données d'autres applications** est défini sur **Toutes les applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** est défini sur **Applications gérées par une stratégie avec Coller dans** |
   
## <a name="windows-10-app-protection-settings"></a>Paramètres de protection des applications Windows 10

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour trouver le paramètre Intune, connectez-vous à l’Microsoft 365 Business Premium d’administrateur et [Portail Azure.](https://portal.azure.com) **Sélectionnez Plus de services**, puis tapez Intune dans le **filtre**. Sélectionnez **Intune stratégie d’application de protection** \> **des applications**.
  
 > [!IMPORTANT]
 >
 >Un abonnement Microsoft 365 Business Premium vous donne une licence pour modifier uniquement les paramètres de Intune qui m’indiquent les paramètres disponibles dans Microsoft 365 Business Premium. 
  
Pour explorer les paramètres disponibles, sélectionnez le nom de stratégie de votre choix, puis choisissez Général **, Affectations****, Applications** autorisées **, Applications** exemptées, **Paramètres obligatoires** ou **Paramètres** avancés dans le volet de navigation de gauche. 
  
|**Paramètre de stratégie des applications Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Chiffrer les fichiers professionnels  |**Paramètres avancés** \> **Protection des données**: **Révoquer les clés de chiffrement lors de la désinscription** et **Révoquer l'accès aux données protégées quand l'appareil s'inscrit à MDM** sont tous deux **activés**.  |
|Empêcher les utilisateurs de copier des données d’entreprise dans des fichiers personnels.  |**Paramètres requis** \> **Mode Protection des informations Windows**. **Sur** dans Microsoft 365 Business Premium masque sur : **Masquer les remplacements****, Hors** Microsoft 365 Business Premium masque à : **Off**.  |
|Contrôle de l'accès aux documents Office  | Si cette fonction est définie sur **Sur** dans Microsoft 365 Business Premium, alors  <br/> **Paramètres avancés** \> **Accès**, **Utiliser Windows Hello Entreprise comme mode de connexion à Windows** est **Activé**, avec les paramètres supplémentaires suivants :  <br/> **Définir le nombre minimal de caractères obligatoires dans le code confidentiel** est défini sur **4**.  <br/> **Configurer l'utilisation des lettres majuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des majuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des lettres minuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des minuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des caractères spéciaux dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation de caractères spéciaux dans le code confidentiel**.  <br/> **Spécifiez la période (** en jours) pendant combien de temps (en jours) un code confidentiel peut être utilisé avant que le système exige que l’utilisateur change est définie sur **0**.  <br/> **Spécifier le nombre d'anciens codes confidentiels associés à un compte d'utilisateur qui peuvent être réutilisés** est défini sur **0**.  <br/> **Nombre d'échecs d'authentification autorisés avant la réinitialisation de l'appareil** est défini comme dans Microsoft 365 Entreprise (5 par défaut).  <br/> **Durée maximale (en minutes) autorisée pendant laquelle l'appareil peut rester inactif avant d'être verrouillé par un mot de passe ou un code confidentiel** est défini comme dans Microsoft 365 Entreprise.  |
|Activer la récupération des données protégées  |**Paramètres avancés** \> **Protection des données**: **Afficher l'icône de protection des données d'entreprise** et **Utiliser Azure RMS pour WIP** sont définis sur **Activé**.  |
|Protéger les autres emplacements cloud de l'entreprise  |**Paramètres avancés** \> **Domaines protégés** et **Ressources cloud** affichent les domaines et les sites SharePoint.  |
|Les fichiers utilisés par ces applications sont protégés  |Les applications protégées sont répertoriées dans **Applications autorisées**.  |
   
## <a name="windows-10-device-protection-settings"></a>Paramètres de protection des appareils Windows 10

Le tableau suivant décrit en détail comment les paramètres de configuration des appareils Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, connectez-vous avec vos informations d’identification d’administrateur Microsoft 365 Business Premium, puis [Portail Azure,](https://portal.azure.com) sélectionnez Plus de **services**, puis tapez Intune dans le **filtre,** sélectionnez Intune **Configuration** \> de **l’appareil** \> **Profils**. Sélectionnez ensuite **Stratégie d'appareils pour Windows 10** \> **Propriétés** \> **Paramètres**.
  
|**Paramètre de stratégie d'appareil Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Protéger les ordinateurs des virus et autres menaces à l'aide de l'antivirus Windows Defender  |Autoriser la surveillance en temps réel = Activé  <br/> Autoriser la protection cloud = Activé  <br/> Demander aux utilisateurs l'autorisation d'envoyer des échantillons = Envoyer automatiquement des échantillons sécurisés (envoi automatique non PII par défaut)  |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  |**SmartScreen** dans **Paramètres du navigateur Edge** est défini sur **Obligatoire**.  |
|Désactiver l'écran d'un appareil resté inactif pendant (minutes)  |Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil (minutes)  |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  |Stratégie URI personnalisée  |
|Autoriser les utilisateurs à accéder à Cortana  |**Général** \> **Cortana** est définie pour **bloquer les** Intune lorsque la mise à **l’Microsoft 365 Business Premium**.  |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  |**Windows à la** une, tous bloqués s’ils sont Microsoft 365 Business Premium.  |
|Maintenir les appareils Windows 10 à jour automatiquement  | Ce  paramètre se trouve dans les mises à **jour** \> Microsoft Intune Service : Windows 10 mettre à jour les anneaux, choisir la stratégie de mise à jour pour **Windows 10 appareils**, \> puis **Propriétés** **Paramètres**.  <br/>  Lorsque le paramètre Microsoft 365 Business Premium est sur **On**, tous les paramètres suivants sont définies :  <br/> **La branche** De service est définie **sur CB** (CBB lorsqu’elle est désactivée dans Microsoft 365 Business Premium).  <br/> **Mises à jour de produits Microsoft** est défini sur **Autoriser**.  <br/> **Pilotes Windows** est défini sur **Autoriser**.  <br/> **Comportement des mises à jour automatiques** est défini sur **Installation automatique à l'heure de la maintenance** avec ce qui suit :  <br/> **Démarrage après ces heures** est défini sur **06:00**.  <br/> **Fin des heures actives** est défini sur **22:00**.  <br/> **Période de report des mises à jour qualité (jours)** est défini sur **0**.  <br/> **Période de report des mises à jour des fonctionnalités (jours)** est défini sur **0**.  <br/> **Mode de téléchargement de l'optimisation de la distribution** est défini sur **HTTP fusionné avec un appairage derrière le même NAT**.  |

## <a name="see-also"></a>Voir aussi

[10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)
