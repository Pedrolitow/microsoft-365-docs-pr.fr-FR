---
title: Comment les fonctionnalités de protection dans Microsoft 365 Business Premium sont mappées aux paramètres Intune
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.collection:
- tier1
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Découvrez comment les fonctionnalités de protection de Microsoft 365 Business Premium mappent aux paramètres Intune. L’abonnement vous fournit une licence pour modifier les paramètres Intune.
ms.openlocfilehash: 185eda9e5b5e214716608d4232a0ea81c00d6b4b
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68096366"
---
# <a name="how-do-protection-features-in-microsoft-365-business-premium-map-to-intune-settings"></a>Comment les fonctionnalités de protection dans Microsoft 365 Business Premium sont mappées aux paramètres Intune

## <a name="android-and-ios-application-protection-settings"></a>Paramètres de protection des applications Android et iOS

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Android et iOS sont mis en correspondance avec les paramètres Intune.
  
Pour trouver le paramètre Intune, connectez-vous avec vos informations d’identification d’administrateur Microsoft 365 Business Premium, accédez à **Centres d’administration**, puis **Intune**.
  
 > [!IMPORTANT]
 > 
 > A Microsoft 365 Business Premium subscription gives you a license to modify all the Intune settings. See [Introduction to Intune to get started.](/intune/introduction-intune)
  
Sélectionnez le nom de la stratégie que vous souhaitez &mdash; par exemple, Stratégie d’application pour Android &mdash; , puis choisissez **Paramètres de stratégie**.
  
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
|Réinitialiser le code pin en cas d’échec de la connexion ce nombre de fois (cette option est désactivée si le code pin n’est pas obligatoire)  |Nombre de tentatives avant réinitialisation du code confidentiel  |
|Obliger les utilisateurs à se reconnecter après que les applications Office ont été inactives (cette option est désactivée si le code pin n’est pas requis)  | Revérifier les conditions d'accès requises après (minutes)  <br/>  Cela définit également ce qui suit :  <br/> Le **Délai expiration** est défini en minutes  <br/>  Il s'agit du nombre de minutes défini dans Microsoft 365 Entreprise.  <br/> **Période de grâce hors connexion** est défini sur 720 minutes par défaut  |
|Refuser l'accès aux fichiers professionnels sur les appareils jailbreakés ou rootés  |Bloquer l'exécution des applications gérées sur les appareils jailbreakés ou rootés  |
|Autoriser les utilisateurs à copier le contenu des applications Office dans des applications personnelles  | Restreindre les opérations Couper, Copier et Coller avec d’autres applications  <br/>  Si l’option Microsoft 365 Business Premium est définie sur **Activé**, ces trois options sont également définies sur **Toutes les applications** dans Intune :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** <br/> **Autoriser l'application à recevoir des données d'autres applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** <br/>  Si l'option Microsoft 365 Entreprise est **Activée**, toutes les options Intune sont définies comme suit :  <br/> **Autoriser l'application à transférer des données vers d'autres applications** est défini sur **Applications gérées par une stratégie** <br/> **Autoriser l'application à recevoir des données d'autres applications** est défini sur **Toutes les applications** <br/> **Restreindre les opérations couper, copier et coller avec d'autres applications** est défini sur **Applications gérées par une stratégie avec Coller dans** |
   
## <a name="windows-10-app-protection-settings"></a>Paramètres de protection des applications Windows 10

Le tableau suivant décrit en détail comment les paramètres de stratégie d'application Windows 10 sont mis en correspondance avec les paramètres Intune.
  
To find the Intune setting, sign in with your Microsoft 365 Business Premium admin credentials, and go to [Azure portal](https://portal.azure.com). Select **More services**, and type Intune into the **Filter**. Select **Intune App Protection** \> **App Policy**.
  
 > [!IMPORTANT]
 > Un abonnement Microsoft 365 Business Premium vous donne une licence pour modifier uniquement les paramètres Intune qui correspondent aux paramètres disponibles dans Microsoft 365 Business Premium. 
  
Pour explorer les paramètres disponibles, sélectionnez le nom de stratégie souhaité, puis choisissez **Général, Affectations**, **Applications autorisées**, **Applications exemptées**, **Paramètres requis** ou **Paramètres avancés** dans le volet de navigation gauche. 
  
|**Paramètre de stratégie des applications Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Chiffrer les fichiers professionnels  |**Paramètres avancés** \> **Protection des données**: **Révoquer les clés de chiffrement lors de la désinscription** et **Révoquer l'accès aux données protégées quand l'appareil s'inscrit à MDM** sont tous deux **activés**.  |
|Empêcher les utilisateurs de copier des données d’entreprise dans des fichiers personnels.  |**Required settings** \> **Windows Information Protection mode**. **On** in Microsoft 365 Business Premium maps to: **Hide Overrides**, **Off** in Microsoft 365 Business Premium maps to: **Off**.  |
|Contrôle de l'accès aux documents Office  | S’il est défini sur **Activé** dans Microsoft 365 Business Premium, alors  <br/> **Paramètres avancés** \> **Accès**, **Utiliser Windows Hello Entreprise comme mode de connexion à Windows** est **Activé**, avec les paramètres supplémentaires suivants :  <br/> **Définir le nombre minimal de caractères obligatoires dans le code confidentiel** est défini sur **4**.  <br/> **Configurer l'utilisation des lettres majuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des majuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des lettres minuscules dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation des minuscules pour le code confidentiel**.  <br/> **Configurer l'utilisation des caractères spéciaux dans le code confidentiel Windows Hello Entreprise** est défini sur **Ne pas autoriser l'utilisation de caractères spéciaux dans le code confidentiel**.  <br/> **Spécifiez la période (en jours) pendant laquelle un code PIN peut être utilisé avant que le système exige que l’utilisateur modifie** est défini sur **0**.  <br/> **Spécifier le nombre d'anciens codes confidentiels associés à un compte d'utilisateur qui peuvent être réutilisés** est défini sur **0**.  <br/> **Nombre d'échecs d'authentification autorisés avant la réinitialisation de l'appareil** est défini comme dans Microsoft 365 Entreprise (5 par défaut).  <br/> **Durée maximale (en minutes) autorisée pendant laquelle l'appareil peut rester inactif avant d'être verrouillé par un mot de passe ou un code confidentiel** est défini comme dans Microsoft 365 Entreprise.  |
|Activer la récupération des données protégées  |**Paramètres avancés** \> **Protection des données**: **Afficher l'icône de protection des données d'entreprise** et **Utiliser Azure RMS pour WIP** sont définis sur **Activé**.  |
|Protéger les autres emplacements cloud de l'entreprise  |**Paramètres avancés** \> **Domaines protégés** et **Ressources cloud** affichent les domaines et les sites SharePoint.  |
|Les fichiers utilisés par ces applications sont protégés  |Les applications protégées sont répertoriées dans **Applications autorisées**.  |
   
## <a name="windows-10-device-protection-settings"></a>Paramètres de protection des appareils Windows 10

Le tableau suivant décrit en détail comment les paramètres de configuration des appareils Windows 10 sont mis en correspondance avec les paramètres Intune.
  
To find the Intune setting, sign in with your Microsoft 365 Business Premium admin credentials, and go to [Azure portal](https://portal.azure.com), then select **More services**, and type in Intune into the **Filter**, select **Intune** \> **Device configuration** \> **Profiles**. Then select **Device policy for Windows 10** \> **Properties** \> **Settings**.
  
|**Paramètre de stratégie d'appareil Windows 10**|**Paramètre(s) Intune**|
|:-----|:-----|
|Protéger les ordinateurs des virus et d'autres menaces à l'aide de l'antivirus Windows Defender  |Autoriser la surveillance en temps réel = Activé  <br/> Autoriser la protection cloud = Activé  <br/> Demander aux utilisateurs l'autorisation d'envoyer des échantillons = Envoyer automatiquement des échantillons sécurisés (envoi automatique non PII par défaut)  |
|Protéger les ordinateurs contre les menaces web dans Microsoft Edge  |**SmartScreen** dans **Paramètres du navigateur Edge** est défini sur **Obligatoire**.  |
|Désactiver l'écran d'un appareil resté inactif pendant (minutes)  |Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil (minutes)  |
|Autoriser les utilisateurs à télécharger des applications à partir du Microsoft Store  |Stratégie URI personnalisée  |
|Autoriser les utilisateurs à accéder à Cortana  |**Cortana**\>**générale** est configurée pour **bloquer** dans Intune lorsqu’elle est définie sur **Désactivé** dans Microsoft 365 Business Premium.  |
|Autoriser les utilisateurs à recevoir des conseils de Windows et des annonces de Microsoft  |**Windows à la une**, tous bloqués s’il est défini sur **désactivé** dans Microsoft 365 Business Premium.  |
|Maintenir les appareils Windows 10 à jour automatiquement  | Ce paramètre se trouve dans **Microsoft Intune** \> **Mises à jour de service - Anneaux de mise à jour Windows 10**, sélectionnez **Stratégie de mise à jour pour les appareils Windows 10**, puis **Propriétés** \> **Paramètres**.  <br/>  Lorsque le paramètre Microsoft 365 Business Premium est défini sur **Activé**, tous les paramètres suivants sont définis :  <br/> **Branche de service** est défini sur **CB** (CBB lorsqu'il est désactivé dans Microsoft 365 Entreprise).  <br/> **Mises à jour de produits Microsoft** est défini sur **Autoriser**.  <br/> **Pilotes Windows** est défini sur **Autoriser**.  <br/> **Comportement des mises à jour automatiques** est défini sur **Installation automatique à l'heure de la maintenance** avec ce qui suit :  <br/> **Démarrage après ces heures** est défini sur **06:00**.  <br/> **Fin des heures actives** est défini sur **22:00**.  <br/> **Période de report des mises à jour qualité (jours)** est défini sur **0**.  <br/> **Période de report des mises à jour des fonctionnalités (jours)** est défini sur **0**.  <br/> **Mode de téléchargement de l'optimisation de la distribution** est défini sur **HTTP fusionné avec un appairage derrière le même NAT**.  |

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)
