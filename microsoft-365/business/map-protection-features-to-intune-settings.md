---
title: Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune
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
ms.custom: OKR_SMB_M365
search.appverid:
- BCS160
- MET150
ms.assetid: aad21b1a-c775-469a-b89c-c5d1d59d27db
description: Découvrez les fonctionnalités de protection de Microsoft 365 Business Map aux paramètres Intune. L’abonnement vous offre une licence pour modifier les paramètres Intune.
ms.openlocfilehash: 316dc8efbe69057f049bf8fadd3c3f41c358a33e
ms.sourcegitcommit: 6003d6da0a85c97357eb3dba3918eb145f381fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "37287956"
---
# <a name="how-do-protection-features-in-microsoft-365-business-map-to-intune-settings"></a>Correspondance entre les fonctionnalités de protection de Microsoft 365 Business et les paramètres Intune

## <a name="android-and-ios-application-protection-settings"></a>Paramètres de protection des applications Android et iOS

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Android et iOS sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, alors que vous êtes connecté avec vos informations d’identification d’administrateur professionnel Microsoft 365, accédez à **centres d’administration**, puis **Intune**.
  
 **Important :** Un abonnement Microsoft 365 Business vous offre une licence pour modifier tous les paramètres Intune. Voir [Introduction to Intune pour commencer.](https://docs.microsoft.com/intune/introduction-intune)
  
Cliquez sur le nom de la stratégie que vous souhaitez sélectionner, par exemple Stratégie d'application pour Android, puis sur **Paramètres de stratégie**.
  
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
|Réinitialiser le code confidentiel lorsque la connexion échoue plusieurs fois (désactivé si le code confidentiel n'est pas exigé)  <br/> |Nombre de tentatives avant réinitialisation du code confidentiel  <br/> |
|Demander aux utilisateurs de se reconnecter à l'issue d'une période d'inactivité des applications Office (désactivé si le code confidentiel n'est pas exigé)  <br/> | Revérifier les conditions d'accès requises après (minutes)  <br/>  Cela définit également ce qui suit :  <br/> Le **Délai expiration** est défini en minutes  <br/>  Il s'agit du nombre de minutes défini dans Microsoft 365 Entreprise.  <br/> **Période de grâce hors connexion** est défini sur 720 minutes par défaut  <br/> |
|Refuser l'accès aux fichiers professionnels sur les appareils jailbreakés ou rootés  <br/> |Bloquer l'exécution des applications gérées sur les appareils jailbreakés ou rootés  <br/> |
|Autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  <br/> | Restreindre les opérations de couper, copier et coller avec d'autres applications  <br/>  Si l'option Microsoft 365 Entreprise est **Activée**, ces trois options sont également définies sur **Toutes les applications** dans Intune :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** <br/> **Autoriser l'application à recevoir des données d'autres applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** <br/>  Si l'option Microsoft 365 Entreprise est **Activée**, toutes les options Intune sont définies comme suit :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** est défini sur **Applications gérées par une stratégie** <br/> **Autoriser l'application à recevoir des données d'autres applications** est défini sur **Toutes les applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** est défini sur **Applications gérées par une stratégie avec Coller dans** <br/> |
|||
   
## <a name="windows-10-app-protection-settings"></a>Paramètres de protection des applications Windows 10

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, alors que vous êtes connecté avec vos informations d’identification d’administrateur professionnel Microsoft 365, accédez à [portail Azure](https://portal.azure.com), sélectionnez **plus de services**, puis tapez Intune dans le **filtre**, sélectionnez **protection** \> **des applications Intune Stratégie d’application**.
  
 **Important**: Un abonnement à Microsoft 365 Business fournit une licence qui vous permet uniquement de modifier les paramètres Intune correspondant aux paramètres disponibles dans Microsoft 365 Business. 
  
Cliquez sur le nom de la stratégie que vous souhaitez sélectionner, puis choisissez **Général, Affectations**, **Applications autorisées**, **Applications exemptes**, **Paramètres requis** ou **Paramètres avancés** dans le volet de navigation gauche pour explorer les paramètres disponibles. 
  
|**Paramètre de stratégie des applications Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Chiffrer les fichiers professionnels  <br/> |**Paramètres avancés** \> **Protection des données**: **Révoquer les clés de chiffrement lors de la désinscription** et **Révoquer l'accès aux données protégées quand l'appareil s'inscrit à MDM** sont tous deux **activés**.  <br/> |
|Empêcher les utilisateurs de copier des données d’entreprise dans des fichiers personnels.  <br/> |**Paramètres requis** \> **Mode Protection des informations Windows**. **Activé** dans Microsoft 365 Entreprise établit une correspondance avec : **Masquer le choix d'ignorer les avertissements**, **Désactivé** dans Microsoft 365 Entreprise établit une correspondance avec : **Désactivé**.  <br/> |
|Contrôle de l'accès aux documents Office  <br/> | Si ce champ est **Activé** dans Microsoft 365 Entreprise,  <br/> **Paramètres avancés** \> **Accès**, **Utiliser Windows Hello Entreprise comme mode de connexion à Windows** est **Activé**, avec les paramètres supplémentaires suivants :  <br/> **Définir le nombre minimal de caractères obligatoires dans le code confidentiel** est défini sur **4**.  <br/> **Configurer l'utilisation des lettres majuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des majuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des lettres minuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des minuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des caractères spéciaux dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation de caractères spéciaux dans le code confidentiel**.  <br/> **Spécifier la durée (en jours) pendant laquelle un code confidentiel peut être utilisé avant que le système demande à l'utilisateur de le changer** est défini sur **0**.  <br/> **Spécifier le nombre d'anciens codes confidentiels associés à un compte d'utilisateur qui peuvent être réutilisés** est défini sur **0**.  <br/> **Nombre d'échecs d'authentification autorisés avant la réinitialisation de l'appareil** est défini comme dans Microsoft 365 Entreprise (5 par défaut).  <br/> **Durée maximale (en minutes) autorisée pendant laquelle l'appareil peut rester inactif avant d'être verrouillé par un mot de passe ou un code confidentiel** est défini comme dans Microsoft 365 Entreprise.  <br/> |
|Activer la récupération des données protégées  <br/> |**Paramètres avancés** \> **Protection des données**: **Afficher l'icône de protection des données d'entreprise** et **Utiliser Azure RMS pour WIP** sont définis sur **Activé**.  <br/> |
|Protéger les autres emplacements cloud de l'entreprise  <br/> |**Paramètres avancés** \> **Domaines protégés** et **Ressources cloud** affichent les domaines et les sites SharePoint.  <br/> |
|Les fichiers utilisés par ces applications sont protégés  <br/> |Les applications protégées sont répertoriées dans **Applications autorisées**.  <br/> |
|||
   
## <a name="windows-10-device-protection-settings"></a>Paramètres de protection des appareils Windows 10

Le tableau suivant décrit en détail comment les paramètres de configuration des appareils Windows 10 sont mis en correspondance avec les paramètres Intune.
  
Pour rechercher le paramètre Intune, alors que vous êtes connecté avec vos informations d’identification d’administrateur professionnel Microsoft 365, accédez à [portail Azure](https://portal.azure.com), sélectionnez **plus de services**, puis tapez Intune dans le **filtre**, sélectionnez appareil **Intune** \> ** ** \> **profils**de configuration. Sélectionnez ensuite **Stratégie d'appareils pour Windows 10** \> **Propriétés** \> **Paramètres**.
  
|**Paramètre de stratégie d'appareil Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Protéger les ordinateurs des virus et autres menaces à l'aide de l'antivirus Windows Defender  <br/> |Autoriser la surveillance en temps réel = Activé  <br/> Autoriser la protection cloud = Activé  <br/> Demander aux utilisateurs l'autorisation d'envoyer des échantillons = Envoyer automatiquement des échantillons sécurisés (envoi automatique non PII par défaut)  <br/> |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  <br/> |**SmartScreen** dans **Paramètres du navigateur Edge** est défini sur **Obligatoire**.  <br/> |
|Désactiver l'écran d'un appareil resté inactif pendant (minutes)  <br/> |Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil (minutes)  <br/> |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  <br/> |Stratégie URI personnalisée  <br/> |
|Autoriser les utilisateurs à accéder à Cortana  <br/> |**Général** \> **Cortana** est défini sur **Bloquer** dans Intune lorsque ce champ est **Désactivé** dans Microsoft 365 Entreprise.  <br/> |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  <br/> |**Windows à la une**, tous bloqués si ce champ est **Désactivé** dans Microsoft 365 Entreprise.  <br/> |
|Maintenir automatiquement les appareils Windows 10 à jour  <br/> | Ce paramètre se trouve dans **Microsoft Intune** \> **Mises à jour de service - Anneaux de mise à jour Windows 10**. Sélectionnez **Stratégie de mise à jour pour les appareils Windows 10**, puis **Propriétés** \> **Paramètres**.      <br/>  Lorsque le paramètre Microsoft 365 Entreprise est **Activé**, tous les paramètres suivants sont définis comme suit :  <br/> **Branche de service** est défini sur **CB** (CBB lorsqu'il est désactivé dans Microsoft 365 Entreprise).  <br/> **Mises à jour de produits Microsoft** est défini sur **Autoriser**.  <br/> **Pilotes Windows** est défini sur **Autoriser**.  <br/> **Comportement des mises à jour automatiques** est défini sur **Installation automatique à l'heure de la maintenance** avec ce qui suit :  <br/> **Démarrage après ces heures** est défini sur **06:00**.  <br/> **Fin des heures actives** est défini sur **22:00**.  <br/> **Période de report des mises à jour qualité (jours)** est défini sur **0**.  <br/> **Période de report des mises à jour des fonctionnalités (jours)** est défini sur **0**.  <br/> **Mode de téléchargement de l'optimisation de la distribution** est défini sur **HTTP fusionné avec un appairage derrière le même NAT**.  <br/> |
|||
   

