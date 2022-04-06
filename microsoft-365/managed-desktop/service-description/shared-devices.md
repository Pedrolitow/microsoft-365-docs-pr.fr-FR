---
title: Appareils partagés
description: Comment et quand utiliser le mode d’appareil partagé
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: ad9cb5e69585f0c014050b51b719e539111cf9fa
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687182"
---
# <a name="shared-devices"></a>Appareils partagés

Microsoft Managed Desktop vous permet d’inscrire des appareils en « mode d’appareil partagé », comme le mode d’appareil partagé proposé par [Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

Les appareils de ce mode sont optimisés pour les situations où les utilisateurs ne sont pas attachés à un seul bureau et changent fréquemment d’appareil. Par exemple, les employés de première ligne tels que les diseurs bancaires ou le personnel infirmier. Vous pouvez appliquer n’importe quel [profil](profiles.md) Microsoft Managed Desktop aux appareils de ce mode. Les appareils inscrits dans ce mode présentent des différences importantes :

- [Le stockage des appareils](#device-storage) est optimisé pour les utilisateurs partagés.
- [Les comptes inactifs](#deletion-of-inactive-accounts) sont supprimés.
- [Les comptes invités](#guest-accounts) ne sont pas pris en charge par défaut.
- [Microsoft 365 Applications](#microsoft-365-apps-for-enterprise) pour les licences d’entreprise est optimisée pour les appareils partagés.

Étant donné que vous choisissez d’utiliser le mode d’appareil partagé au moment de l’inscription dans Microsoft Managed Desktop, si vous souhaitez changer de mode ultérieurement, vous devez le désinscrire et l’inscrire à nouveau.

## <a name="when-to-use-shared-device-mode"></a>Quand utiliser le mode d’appareil partagé

Toute situation dans laquelle les utilisateurs changent fréquemment d’appareils.

Par exemple, les diseurs bancaires peuvent se trouver dans un seul emplacement pour gérer les dépôts, mais se déplacer vers un back-office pour aider les clients avec un prêt hypothécaire. Dans chacun de ces emplacements, l’appareil exécute différentes applications et est optimisé pour ces tâches, bien qu’ils soient utilisés par plusieurs personnes.

Le personnel infirmier se déplace généralement entre les salles et les bureaux au fur et à mesure qu’il interagit avec les patients. Ils peuvent se connecter à une station de travail dans un bureau, mais se connecter à leur bureau à distance et prendre des notes, et répéter ce processus dans une autre pièce avec un autre patient.

## <a name="when-not-to-use-shared-device-mode"></a>Quand ne pas utiliser le mode d’appareil partagé

Le mode appareil partagé n’est pas un bon choix dans les situations suivantes :

- Quand les fichiers d’un utilisateur doivent être stockés localement plutôt que dans le cloud
- Si l’expérience utilisateur doit être différente pour différents utilisateurs sur l’appareil
- Si l’ensemble d’applications dont chaque utilisateur a besoin diffère considérablement

## <a name="register-new-devices-in-shared-device-mode"></a>Inscrire de nouveaux appareils en mode d’appareil partagé

À compter de 2203, que vous ou un partenaire gériez l’inscription d’appareils, vous pouvez choisir d’utiliser le Windows profil de [mode de déploiement automatique Autopilot](/mem/autopilot/self-deploying) dans Microsoft Managed Desktop.

Si vous inscrivez vous-même des appareils, vous devez importer de nouveaux appareils dans le Windows panneau Appareils Autopilot.

**Pour importer de nouveaux appareils dans le panneau Windows Appareils Autopilot :**

1. Collectez le [hachage matériel](../get-started/manual-registration.md#obtain-the-hardware-hash) pour les nouveaux appareils auxquels vous souhaitez affecter le Windows profil de mode auto-déploiement Autopilot.
2. Accédez au [portail Microsoft Endpoint Manager](https://endpoint.microsoft.com).
2. Sélectionnez **Appareils** dans le menu de navigation de gauche.
3. Dans la section **De la plateforme,** sélectionnez **Windows**. Sélectionnez ensuite **Windows Inscription**.
4. Dans la section **Windows Autopilot Deployment Programme**, sélectionnez **Appareils**.
5. [Importez](../get-started/manual-registration.md#register-devices-by-using-the-admin-portal) le fichier .CSV contenant tous les hachages matériels collectés à l’étape 1.
6. Une fois que vous avez chargé les Windows appareils Autopilot, vous devez modifier l’attribut de balise de groupe des appareils importés afin Microsoft Managed Desktop pouvez les inscrire à l’aide du profil de mode de déploiement automatique Windows Autopilot. Voir ci-dessous pour les attributs de balise de groupe. Vous devez ajouter **-Shared** à la balise de groupe, comme indiqué dans le tableau ci-dessous :

| Profil d’appareil | Balise de groupe Autopilot (mode standard) | Balise de groupe (mode appareil partagé) |
| ----- | ----- | ----- |
| Données sensibles | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Utilisateur d’alimentation | Microsoft365Managed_PowerUser | Non pris en charge |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

> [!WARNING]
> N’essayez pas de modifier l’attribut d’onglet de groupe en ajoutant **-Shared** to devices previously imported to Windows Autopilot. Les appareils déjà importés dans Windows Autopilot, en utilisant l’une des balises de groupe Microsoft Managed Desktop commençant par *Microsoft365Managed_*, mais sans **-Shared** initialement ajouté, font déjà partie d’un groupe de Azure Active Directory différent. Le Windows profil de mode de déploiement automatique Autopilot n’est pas affecté à ce groupe Azure Active Directory. Si vous devez réutiliser un appareil existant pour qu’il soit un appareil partagé, vous devez supprimer et réinscrire l’appareil dans Windows Autopilot.

Si vous avez des appareils d’inscription de partenaire, suivez les étapes de [l’inscription du partenaire](../get-started/partner-registration.md), mais ajoutez **-Shared** à la balise de groupe, comme indiqué dans le tableau ci-dessus.

## <a name="consequences-of-shared-device-mode"></a>Conséquences du mode d’appareil partagé

### <a name="device-storage"></a>Stockage de l’appareil

Les données des utilisateurs d’appareils partagés doivent être sauvegardées dans le cloud afin qu’elles puissent les suivre sur d’autres appareils. Une fois que vous avez inscrit des appareils en mode d’appareil partagé, veillez à activer les fonctionnalités de redirection [des fichiers à la demande](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) et des [dossiers connus](/onedrive/redirect-known-folders) de OneDrive. Cette approche réduit l’effet de chaque profil utilisateur sur le stockage des appareils. Les appareils en mode appareil partagé suppriment automatiquement les profils utilisateur si l’espace disque libre est inférieur à 25 %. Cette activité est planifiée pour minuit à l’heure locale de l’appareil, sauf si le stockage devient critiquement limité.

Microsoft Managed Desktop utilise le fournisseur CSP [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) pour effectuer ces opérations, veillez donc à ne pas utiliser ces fournisseurs de services partagés vous-même.

> [!IMPORTANT]
> Formez vos utilisateurs pour qu’après avoir téléchargé un fichier volumineux, ils confirment qu’ils voient l’icône de vérification verte sur le fichier avant de se déconnecter. Si son compte est supprimé dans le cadre des opérations de nettoyage et que le fichier n’est pas entièrement chargé dans OneDrive, le fichier est définitivement perdu.

### <a name="deletion-of-inactive-accounts"></a>Suppression de comptes inactifs

Le mode appareil partagé supprime tous les comptes qui n’ont pas été connectés depuis plus de 30 jours.

### <a name="guest-accounts"></a>Comptes invités

Les appareils en mode appareil partagé autorisent uniquement les comptes joints à un domaine. Si vous avez besoin de comptes invités sur un appareil, vous pouvez déposer une [demande de modification](../working-with-managed-desktop/admin-support.md) pour les demander à être activés.

### <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 for entreprise

[Applications Microsoft 365 pour les grandes entreprises](/microsoft-365/managed-desktop/get-started/m365-apps) permet généralement à un utilisateur donné d’installer ces applications sur seulement cinq appareils en même temps. En mode appareil partagé, les applications ne sont pas comptabilisées dans la limite. Elles peuvent donc les utiliser pendant l’itinérance entre les appareils. Le déploiement et les mises à jour de Applications Microsoft 365 pour les grandes entreprises fonctionnent comme d’habitude.

### <a name="device-profiles"></a>Profils d’appareil

En mode appareil partagé, vous ne pouvez avoir qu’un seul [profil d’appareil](profiles.md) sur un appareil donné. En outre, le profil d’appareil utilisateur Power n’est actuellement pas pris en charge en mode d’appareil partagé.

### <a name="apps-and-policies-assigned-to-users"></a>Applications et stratégies affectées aux utilisateurs

Sur les appareils partagés, vous devez affecter des applications ou des stratégies que vous gérez vous-même à des *groupes d’appareils*, et non à des groupes d’utilisateurs. L’affectation à des groupes d’appareils garantit que chaque utilisateur dispose d’une expérience plus cohérente. L’exception est [Portail d'entreprise](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Limitations du mode d’appareil partagé

### <a name="windows-hello"></a>Windows Hello

Windows Hello utilise l’émulation de carte à puce pour mettre en cache en toute sécurité [les codes confidentiels](/windows/security/identity-protection/hello-for-business/hello-faq) utilisateur, ce qui réduit le nombre de fois où les utilisateurs doivent s’authentifier. Toutefois, Windows n’autorise que 10 cartes à puce à la fois sur un appareil donné. Lorsqu’un 11e utilisateur se connecte pour la première fois, l’un des comptes existants perd sa carte à puce. Ils pourront se connecter, mais leur code confidentiel ne sera pas mis en cache.

### <a name="universal-print"></a>Impression universelle

Lorsque l’impression universelle installe une imprimante pour un seul utilisateur sur un appareil partagé, cette imprimante devient disponible pour tous les utilisateurs de cet appareil. Il n’existe aucun moyen d’isoler les imprimantes entre les utilisateurs sur des appareils partagés.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Limitations du mode d’appareil partagé dans la préversion publique

### <a name="primary-user"></a>Utilisateur principal

Chaque Microsoft Intune appareil a un utilisateur principal, qui est affecté lorsqu’un appareil est configuré par Autopilot. Toutefois, lorsque les appareils sont partagés, Intune exige que l’utilisateur principal soit supprimé.

> [!IMPORTANT]
> Bien que le mode d’appareil partagé soit en préversion publique, veillez à supprimer l’utilisateur principal en procédant comme suit : connectez-vous au centre d’administration Microsoft Endpoint Manager, sélectionnez **appareils DevicesAll**>, sélectionnez un appareil, puis sélectionnez **l’utilisateur principal PropertiesRemove**> et supprimez l’utilisateur qui y figure.

### <a name="deploying-apps-with-company-portal"></a>Déploiement d’applications avec Portail d'entreprise

Certaines applications n’ayant probablement pas besoin d’être présentes sur tous les appareils, vous préférerez peut-être que les utilisateurs installent ces applications uniquement lorsqu’ils en ont besoin à partir de [Portail d'entreprise](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Managed Desktop désactive Portail d'entreprise par défaut pour les appareils en mode d’appareil partagé. Si vous souhaitez activer le Portail d'entreprise, vous pouvez déposer une [demande de modification](../working-with-managed-desktop/admin-support.md). Toutefois, vous devez connaître certaines limitations de cette fonctionnalité dans cette préversion publique :

- Pour mettre une application à la disposition des utilisateurs dans Portail d'entreprise, [affectez un groupe d’utilisateurs](/mem/intune/apps/apps-deploy) à cette application dans Intune, puis ajoutez chaque utilisateur à ce groupe d’utilisateurs.
- Les appareils ne peuvent pas avoir [d’utilisateur principal](#primary-user).
- Pour désinstaller une application qu’un utilisateur a installée via Portail d'entreprise, vous devez désinstaller l’application de tous les utilisateurs sur cet appareil.

> [!CAUTION]
> Portail d'entreprise ne prend pas en charge les applications affectées aux groupes d’appareils comme disponibles.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Redéploiement de Microsoft 365 Apps pour Enterprise

Pendant la préversion publique, si Microsoft 365 Apps doit être redéployé, les utilisateurs doivent contacter leur personnel de support local pour demander un élévation de privilèges d’agent et réinstaller Applications Microsoft 365 pour les grandes entreprises sur cet appareil.

### <a name="microsoft-teams"></a>Microsoft Teams

Lorsqu’un utilisateur démarre Teams pour la première fois, il est invité à mettre à jour l’application avant de pouvoir l’utiliser. Une fois la mise à jour autorisée, Teams se maintiendra à jour en arrière-plan.
