---
title: Première expérience d’utilisation avec AutoPilot et la page d’état d’enregistrement
description: Comment déployer l’expérience ESP, les paramètres utilisés et les exceptions
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 84656e2f0ae9d148c61c27af2a53e157cd44c171
ms.sourcegitcommit: e6283e7c32ba9628fc45e9abc5cd4d21fb3f7ca9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "48299238"
---
# <a name="first-run-experience-with-autopilot-and-the-enrollment-status-page"></a>Première expérience d’utilisation avec AutoPilot et la page d’état d’enregistrement

Microsoft Managed Desktop utilise à la fois la page d' [État d’enregistrement](https://docs.microsoft.com/windows/deployment/windows-autopilot/enrollment-status) de [Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot) et de Microsoft Intune pour offrir la meilleure expérience de première utilisation possible à vos utilisateurs.

La page État de l’enregistrement est actuellement en version préliminaire publique.

## <a name="initial-deployment"></a>Déploiement initial

Pour fournir l’expérience ESP, vous devez inscrire des appareils dans le service bureau géré Microsoft. Pour plus d’informations sur l’inscription, reportez-vous à la rubrique [enregistrer les nouveaux appareils vous-même](../get-started/register-devices-self.md) ou [les étapes à suivre pour inscrire des](../get-started/register-devices-partner.md)

Une fois que vos appareils sont inscrits auprès du service, vous pouvez activer ESP pour vos appareils de bureau gérés par Microsoft en archivant un ticket de support via le [portail d’administration](https://portal.azure.com/). Lors du déploiement initial de la configuration ESP dans le groupe de test, vous devez classer le ticket. Elle est déployée dans les autres groupes de déploiement suivants (tout d’abord, rapide et large) toutes les 24 heures. Pour suspendre le déploiement, fichier autre ticket demandant les opérations à conserver.

## <a name="autopilot-profile-settings"></a>Paramètres du profil AutoPilot

Microsoft Managed Desktop utilise ces paramètres dans le profil AutoPilot utilisé pour les appareils de vos utilisateurs :


|Paramètres  |Valeur  |
|---------|---------|
|Mode de déploiement |  Piloté par l’utilisateur       |
|Rejoindre Azure AD en tant que     |  Azure AD jointe       |
|Langue (région)     | Système d’exploitation par défaut        |
|Configurer automatiquement le clavier     | Non        |
|Termes du contrat de licence logiciel Microsoft     |  Masquer       |
|Paramètres de confidentialité     | Masquer        |
|Masquer les options de modification de compte     | Afficher        |
|Type de compte d’utilisateur     |  Standard       |
|Autoriser le gant blanc OOBE     |  Oui       |
|Appliquer le modèle de nom d’appareil     | Oui        |
|Entrez un nom     | MMD-% RAND : 11%        |

> [!NOTE]
> Bien que la rovisioning « gant blanc » ne soit activée que pour les clients dont l’option ESP est activée, elle n’est actuellement pas prise en charge dans le bureau géré Microsoft.

## <a name="enrollment-status-page-settings"></a>Paramètres de la page d’état d’enregistrement

Microsoft Managed Desktop utilise ces paramètres pour l’expérience de page d’état d’enregistrement :


|Paramètres  |Valeur  |
|---------|---------|
|Afficher la progression de la configuration de l’application et du profil     | Oui        |
|Afficher une erreur lorsque l’installation prend plus de temps que le nombre de minutes spécifié     |  60       |
|Afficher un message personnalisé lorsque une erreur de délai se produit     |  Oui       |
|Message d’erreur     | Oui, il faut un peu plus de temps pour configurer votre appareil que prévu. Cliquez ci-dessous pour commencer et terminer la configuration en arrière-plan        |
|Autoriser les utilisateurs à collecter des journaux sur les erreurs d’installation     |  Oui       |
|Afficher uniquement la page aux appareils mis en service par OOBE (out-of-Box Experience)     | Oui        |
|Bloquer l’utilisation des appareils jusqu’à ce que toutes les applications et tous les profils soient installés     |  Oui       |
|Autoriser les utilisateurs à réinitialiser le périphérique si une erreur d’installation se produit     |  Oui       |
|Autoriser les utilisateurs à utiliser l’appareil si une erreur d’installation se produit     |  Oui       |
|Bloquer l’utilisation des appareils jusqu’à ce que ces applications requises soient installées si elles sont attribuées à l’utilisateur/périphérique     |  Correction du temps de travail moderne       |



L’expérience de page d’état d’enregistrement se produit en trois phases. Pour plus d’informations, consultez la rubrique relative au [suivi des pages d’état des inscriptions](https://docs.microsoft.com/mem/intune/enrollment/windows-enrollment-status#enrollment-status-page-tracking-information).

L’expérience se déroule comme suit :

1. L’expérience du pilotage automatique démarre et l’utilisateur entre ses informations d’identification.
2. L’appareil ouvre la page d’état de l’enregistrement et procède aux phases de configuration de l’appareil et de l’appareil. La troisième étape (configuration de compte) est *actuellement ignorée* dans la configuration du bureau géré Microsoft car l’ESP utilisateur est désactivé. Le périphérique redémarre.
3. Après le redémarrage, l’appareil ouvre la page de connexion Windows avec d' **autres utilisateurs**.
4. Les utilisateurs entrent de nouveau leurs informations d’identification et le Bureau s’ouvre.

> [!NOTE]
> Les applications Win32 sont déployées uniquement lors de l’utilisation de ESP si la version Windows 10 est 1903 ou ultérieure.

![Page de démarrage de la configuration de AutoPilot affichant les phases de préparation de l’appareil et de configuration de l’appareil.](../../media/mmd-autopilot-screenshot.png)

## <a name="white-glove-provisioning"></a>Provisionnement de gants blancs

Microsoft Managed Desktop ne prend actuellement pas en charge la fonctionnalité « gant blanc » de Windows AutoPilot.

## <a name="exceptions"></a>Exceptions

Si le programme d’installation utilisé par Microsoft Managed Desktop ne correspond pas exactement à vos besoins, vous pouvez classer une demande pour une exception. Pour ce faire, consultez la rubrique Details in [Request an exception](../service-description/customizing.md#request-an-exception). Voici quelques exemples des types d’exceptions dont vous pouvez avoir besoin :

### <a name="autopilot-exception"></a>Exception AutoPilot

Vous souhaiterez peut-être demander un autre modèle de nom d’appareil. Toutefois, vous ne pouvez pas modifier le mode de déploiement, rejoindre Azure en tant que, paramètres de confidentialité ou type de compte d’utilisateur.

### <a name="enrollment-status-page-exception"></a>Exception de page d’état d’enregistrement

- Un nombre de minutes plus long pour le paramètre « afficher une erreur lorsque l’installation prend plus de temps que le nombre de minutes spécifié ».
- Message d’erreur affiché
- Ajout ou suppression d’applications dans le paramètre « bloquer l’utilisation des appareils jusqu’à ce que ces applications requises soient installées si elles sont affectées au paramètre utilisateur/périphérique ».

## <a name="required-applications"></a>Applications requises

- Vous devez cibler les applications dans les *groupes d’appareils* de travail modernes test, tout d’abord, rapide et large. Les applications doivent être installées dans le contexte « système ». Assurez-vous d’effectuer les tests avec ESP dans le groupe test avant de les affecter à tous les groupes.
- Aucune application ne doit redémarrer l’appareil. Nous recommandons que les applications soient définies sur « ne rien faire » lorsque vous créez le package d’application s’ils nécessitent un redémarrage.
- Limitez les applications requises aux applications principales dont un utilisateur a besoin immédiatement lorsqu’il se connecte à l’appareil.
- Conservez la taille totale de toutes les applications sous une limite de 1 Go pour éviter les délais d’expiration pendant la phase d’installation de l’application.
- Idéalement, les applications ne doivent pas avoir de dépendances. Si vous avez des applications qui *doivent* avoir des dépendances, veillez à les configurer, les tester et les valider dans le cadre de votre évaluation ESP.
- Aucune application nécessitant le contexte « User » (par exemple, Teams) ne peut être incluse dans la préversion publique d’ESP.
