---
title: Appareils partagés
description: Comment et quand utiliser le mode d’appareil partagé
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
ms.openlocfilehash: 6b022551db4b3ca759ffb6d1f9eae184b64e0683
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60756196"
---
# <a name="shared-devices"></a>Appareils partagés

Microsoft Manged Desktop vous permet d’inscrire des appareils en « mode d’appareil partagé », comme le mode d’appareil partagé proposé [par Microsoft Intune](/mem/intune/configuration/shared-user-device-settings). Les appareils de ce mode sont optimisés pour les situations dans lesquelles les utilisateurs ne sont pas liés à un seul bureau et changent fréquemment d’appareil, en général, pour les travailleurs de la sécurité tels que les collaborateurs de la banque ou les employés. Vous pouvez appliquer n’importe quel profil Microsoft Manged Desktop [aux](profiles.md) appareils dans ce mode. Les appareils inscrits dans ce mode ont des différences importantes :

- [Le stockage de l’appareil](#device-storage) est optimisé pour les utilisateurs partagés.
- [Les comptes inactifs](#deletion-of-inactive-accounts) sont supprimés.
- [Les comptes invités](#guest-accounts) ne sont pas pris en charge par défaut.
- [Microsoft 365 applications pour](#microsoft-365-apps-for-enterprise) les licences d’entreprise est optimisée pour les appareils partagés.

Étant donné que vous faites le choix d’utiliser le mode d’appareil partagé au moment de l’inscription dans Microsoft Manged Desktop, si vous souhaitez le faire sortir de ce mode ultérieurement, vous devez le désins inscrire et l’inscrire à nouveau.

## <a name="when-to-use-shared-device-mode"></a>Quand utiliser le mode d’appareil partagé

Toute situation dans laquelle les utilisateurs changent fréquemment d’appareil.

Par exemple, les courtiers bancaires peuvent se trouver dans un emplacement de gestion des dépôts, mais se déplacer vers un back office pour aider les clients avec un prêt immobilier. À chacun de ces emplacements, l’appareil exécute différentes applications et est optimisé pour ces tâches, bien qu’elles soient utilisées par plusieurs personnes.

En règle générale, les employés se déplacent entre les salles et les bureaux pendant qu’ils interagissent avec des patients, afin qu’ils peuvent se connecter à une station de travail dans un bureau, mais se connecter à leur bureau à distance et prendre des notes, uniquement pour répéter cela dans une autre salle avec un patient différent.

## <a name="when-not-to-use-shared-device-mode"></a>Quand ne pas utiliser le mode d’appareil partagé

Le mode appareil partagé n’est pas un bon choix dans les situations ci-après :

- Lorsque les fichiers d’un utilisateur doivent être stockés localement plutôt que dans le cloud
- Si l’expérience utilisateur doit être différente pour différents utilisateurs sur l’appareil
- Si l’ensemble d’applications dont chaque utilisateur a besoin diffère sensiblement

## <a name="enroll-new-devices-in-shared-device-mode"></a>Inscrire de nouveaux appareils en mode d’appareil partagé

Que vous ou un partenaire gèrez l’inscription, vous pouvez choisir d’utiliser le mode appareil partagé.

Si vous inscrivez **vous-même** des appareils, suivez les étapes de l’inscription de nouveaux appareils vous-même, [](../get-started/register-devices-self.md)puis ajoutez-les au groupe Appareils de l’espace de travail moderne - Mode appareil partagé.

> [!WARNING]
> N’essayez pas de convertir des appareils Microsoft Manged Desktop existants en mode d’appareil partagé en les ajoutant simplement à ce groupe. Les stratégies appliquées peuvent potentiellement entraîner la perte OneDrive fichiers.

Si vous avez un partenaire inscrit des appareils, suivez les étapes de la procédure d’inscription des appareils par les [partenaires,](../get-started/register-devices-partner.md)mais l’append **-Shared** à la balise de groupe, comme indiqué dans le tableau suivant :

|Profil d’appareil  |Balise de groupe (mode standard)  |Balise de groupe (mode appareil partagé)  |
|---------|---------|---------|
|Date sensible | Microsoft365Managed_SensitiveData        |  Microsoft365Managed_SensitiveData-Shared       |
| Utilisateur avec pouvoir         | Microsoft365Managed_PowerUser        | Non pris en charge        |
|Standard     | Microsoft365Managed_Standard        | Microsoft365Managed_Standard-Shared  |

## <a name="consequences-of-shared-device-mode"></a>Conséquences du mode d’appareil partagé

### <a name="device-storage"></a>Stockage d’appareil

Les utilisateurs d’appareils partagés doivent avoir leurs données dans le cloud pour pouvoir les suivre sur d’autres appareils. Une fois que vous avez inscrit des appareils en mode d’appareil [](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) partagé, veillez à activer les fonctionnalités de redirection de fichiers à la demande et de [dossiers](/onedrive/redirect-known-folders) connus de OneDrive. Cette approche réduit l’impact de chaque profil utilisateur sur le stockage de l’appareil. Les appareils en mode d’appareil partagé suppriment automatiquement les profils utilisateur si l’espace disque disponible descend en dessous de 25 %. Cette activité est prévue à minuit à l’heure locale de l’appareil, sauf si le stockage devient extrêmement limité.

Microsoft Manged Desktop le programme CSP [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) pour effectuer ces opérations, veillez donc à ne pas utiliser ces CSP vous-même.

> [!IMPORTANT]
> Formez vos utilisateurs qu’une fois qu’ils ont téléchargé un fichier de grande taille, ils doivent vérifier qu’ils voient l’icône de coche verte sur le fichier avant de se dé connecter. Si son compte est supprimé dans le cadre des opérations de nettoyage et que le fichier n’est pas entièrement chargé dans OneDrive, le fichier est définitivement perdu.

### <a name="deletion-of-inactive-accounts"></a>Suppression de comptes inactifs

Le mode appareil partagé supprime tous les comptes qui n’ont pas été connectés depuis plus de 30 jours.

### <a name="guest-accounts"></a>Comptes invités

Les appareils en mode d’appareil partagé autorisent uniquement les comptes joints à un domaine. Si vous avez besoin de comptes invités sur un appareil, vous pouvez déposer une [demande](../working-with-managed-desktop/admin-support.md) de modification pour les demander à être activés.

### <a name="microsoft-365-apps-for-enterprise"></a>Applications Microsoft 365 pour les entreprises

[Applications Microsoft 365 pour les grandes entreprises](/microsoft-365/managed-desktop/get-started/m365-apps) permet généralement à un utilisateur donné d’installer ces applications sur cinq appareils en même temps. En mode d’appareil partagé, les applications ne sont pas comptabilisées dans la limite, elles peuvent donc les utiliser en itinérance entre les appareils. Le déploiement et les mises à jour Applications Microsoft 365 pour les grandes entreprises fonctionnent comme d’habitude.

### <a name="device-profiles"></a>Profils d’appareil

En mode d’appareil partagé, vous ne pouvez avoir qu’un seul [profil d’appareil](profiles.md) sur un appareil donné. En outre, le profil d’appareil de l’utilisateur Power n’est actuellement pas pris en charge en mode d’appareil partagé.

### <a name="apps-and-policies-assigned-to-users"></a>Applications et stratégies affectées aux utilisateurs

Sur les appareils partagés, vous devez affecter les applications ou stratégies que vous gérez vous-même à des groupes d’appareils, et non à des groupes d’utilisateurs. Cela garantit que chaque utilisateur dispose d’une expérience plus cohérente. L’exception est [Portail d'entreprise](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Limitations du mode d’appareil partagé

### <a name="windows-hello"></a>Windows Hello

Windows Hello l’émulation de carte à puce pour mettre en cache en toute sécurité les pins des [utilisateurs,](/windows/security/identity-protection/hello-for-business/hello-faq)réduisant ainsi le nombre de fois que les utilisateurs doivent s’authentifier. Toutefois, Windows autorise uniquement 10 cartes à puce à la fois sur un appareil donné. Lorsqu’un onzième utilisateur se signe pour la première fois, l’un des comptes existants perd sa carte à puce. Ils pourront se connecter, mais leur code confidentiel ne sera pas mis en cache.

### <a name="universal-print"></a>Impression universelle

Lorsque l’impression universelle installe une imprimante pour un utilisateur unique sur un appareil partagé, cette imprimante devient disponible pour tous les utilisateurs de cet appareil. Il n’existe aucun moyen d’isoler les imprimantes entre les utilisateurs sur des appareils partagés.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Limitations du mode d’appareil partagé dans la version d’aperçu public

### <a name="primary-user"></a>Utilisateur principal

Chaque Microsoft Intune’appareil a un utilisateur principal, qui est affecté lorsqu’un appareil est installé par Autopilot. Toutefois, lorsque des appareils sont partagés, Intune requiert la suppression de l’utilisateur principal.

> [!IMPORTANT]
> Alors que le mode appareil partagé est en prévisualisation publique, veillez à supprimer l’utilisateur principal en suivant les étapes suivantes : connectez-vous au Centre d’administration Microsoft Endpoint Manager, sélectionnez Appareils tous les appareils, sélectionnez un appareil, puis sélectionnez Propriétés Supprimer l’utilisateur principal, puis supprimez l’utilisateur répertorié  >   > ici.

### <a name="deploying-apps-with-company-portal"></a>Déploiement d’applications avec Portail d'entreprise

Certaines applications n’ont probablement pas besoin d’être présentes sur tous les [appareils.](/mem/intune/user-help/install-apps-cpapp-windows)Vous pouvez donc préférer que les utilisateurs installent uniquement ces applications lorsqu’ils en ont besoin à partir de Portail d'entreprise . Microsoft Manged Desktop désactive Portail d'entreprise par défaut pour les appareils en mode d’appareil partagé. Si vous souhaitez Portail d'entreprise activée, vous pouvez déposer une demande de [modification,](../working-with-managed-desktop/admin-support.md)mais vous devez connaître certaines limitations de cette fonctionnalité dans cette prévisualisation publique :

- Pour rendre une application accessible aux utilisateurs dans [Portail d'entreprise,](/mem/intune/apps/apps-deploy) affectez un groupe d’utilisateurs à cette application dans Intune, puis ajoutez chaque utilisateur à ce groupe d’utilisateurs.
- Les appareils ne peuvent pas avoir [d’utilisateur principal.](#primary-user)
- Pour désinstaller une application qu’un utilisateur a installée via Portail d'entreprise, vous devez désinstaller l’application de tous les utilisateurs de cet appareil.

> [!CAUTION]
> Portail d'entreprise ne prend pas en charge les applications affectées à des groupes d’appareils comme disponibles.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Redéploiement des Applications Microsoft 365 pour les grandes entreprises

Lors de la prévisualisation publique, si Microsoft 365 Apps doit être redéployé, les utilisateurs devront contacter leur personnel de support local pour demander un élévation de niveau d’agent et réinstaller des Applications Microsoft 365 pour les grandes entreprises sur cet appareil.

### <a name="microsoft-teams"></a>Microsoft Teams

Lorsqu’un utilisateur démarre Teams pour la première fois, il est invité à mettre à jour l’application avant de pouvoir l’utiliser. Une fois la mise à jour Teams mise à jour est toujours mise à jour en arrière-plan.
