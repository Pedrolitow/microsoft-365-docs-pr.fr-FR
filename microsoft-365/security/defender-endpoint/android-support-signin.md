---
title: Résoudre les problèmes sur Microsoft Defender pour point de terminaison sur Android
description: Résoudre les problèmes de Microsoft Defender pour point de terminaison sur Android
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mde, android, cloud, connectivité, communication
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 73e87075f17413e361f380d7556dc3988ac4a7f7
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67693320"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Résolution des problèmes sur Microsoft Defender pour point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Lors de l’intégration d’un appareil, vous pouvez rencontrer des problèmes de connexion après l’installation de l’application.

Pendant l’intégration, vous pouvez rencontrer des problèmes de connexion après l’installation de l’application sur votre appareil.

Cet article fournit des solutions pour résoudre les problèmes d’authentification.

## <a name="sign-in-failed---unexpected-error"></a>Échec de la connexion : erreur inattendue

**Échec de la connexion :** *erreur inattendue, essayez ultérieurement*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Erreur d’échec de connexion Erreur inattendue dans la page de connexion du portail Microsoft Defender 365." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**Message:**

Erreur inattendue, essayez ultérieurement

**Cause :**

Une version antérieure de l’application « Microsoft Authenticator » est installée sur votre appareil.

**Solution :**

Installez la dernière version de [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) à partir de Google Play Store et réessayez.

## <a name="sign-in-failed---invalid-license"></a>Échec de la connexion : licence non valide

**Échec de la connexion :** *licence non valide, contactez l’administrateur*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Détails du contact de directive dans la page de connexion du portail Microsoft Defender 365" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**Message :** *Licence non valide, contactez l’administrateur*

**Cause :**

Vous n’avez pas attribué de licence Microsoft 365 ou votre organisation n’a pas de licence pour Microsoft 365 Entreprise abonnement.

**Solution :**

Contactez votre administrateur pour obtenir de l'aide.

## <a name="report-unsafe-site"></a>Signaler un site non sécurisé

Les sites web de hameçonnage empruntent l’identité de sites web dignes de confiance pour obtenir vos informations personnelles ou financières. Visitez la page [Fournir des commentaires sur la protection réseau](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) si vous souhaitez signaler un site web qui pourrait être un site de hameçonnage.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Les pages d’hameçonnage ne sont pas bloquées sur certains appareils OEM

**S’applique à :** Oem spécifiques uniquement

- **Xiaomi**

Le hameçonnage et les menaces web dangereuses détectées par Defender pour point de terminaison pour Android ne sont pas bloqués sur certains appareils Xiaomi. Les fonctionnalités suivantes ne fonctionnent pas sur ces appareils.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="Message de notification de site non sécurisé" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Cause :**

Les appareils Xiaomi incluent un nouveau modèle d’autorisation. Cela empêche Defender pour point de terminaison pour Android d’afficher des fenêtres contextuelles pendant son exécution en arrière-plan.

Autorisation des appareils Xiaomi : « Afficher les fenêtres contextuelles en cours d’exécution en arrière-plan ».

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Volet de configuration contextuelle dans le portail Microsoft Defender 365" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Solution :**

Activez l’autorisation requise sur les appareils Xiaomi.

- Afficher les fenêtres contextuelles en cours d’exécution en arrière-plan.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Impossible d’autoriser l’autorisation de « protection permanente » lors de l’intégration sur certains appareils OEM


**S’applique à :** Appareils OEM spécifiques uniquement.

- **Xiaomi**

L’application Defender demande l’autorisation d’optimisation de la batterie/protection permanente sur les appareils dans le cadre de l’intégration de l’application, et la sélection **d’Autoriser** renvoie une erreur indiquant que l’autorisation n’a pas pu être définie. Elle affecte uniquement la dernière autorisation appelée « Protection permanente ». 

**Cause :**

Xiaomi a modifié les autorisations d’optimisation de la batterie dans Android 11. Defender pour point de terminaison n’est pas autorisé à configurer ce paramètre pour ignorer les optimisations de batterie.

**Solution :**

>[!IMPORTANT]
>Ce problème a été résolu. Mettez à jour la dernière version de l’application pour terminer le processus d’intégration. Si le problème persiste, envoyez un **[commentaire dans l’application](/microsoft-365/security/defender-endpoint/android-support-signin#send-in-app-feedback)**.


## <a name="send-in-app-feedback"></a>Envoyer des commentaires dans l’application

Si un utilisateur rencontre un problème qui n’est pas déjà résolu dans les sections ci-dessus ou qui ne peut pas être résolu à l’aide des étapes répertoriées, l’utilisateur peut fournir des **commentaires dans l’application** ainsi que des **données de diagnostic**. Notre équipe peut ensuite examiner les journaux pour fournir la solution appropriée. Les utilisateurs peuvent suivre ces étapes pour effectuer les mêmes opérations :

1. Ouvrez **l’application MDE** sur votre appareil, puis cliquez sur **l’icône de profil** dans le coin supérieur gauche.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Icône de profil dans le portail Microsoft Defender pour point de terminaison" lightbox="images/select-profile-icon-1.jpg":::

2. Sélectionnez « Aide & commentaires ».

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="L’option Aide & commentaires qui peut être sélectionnée dans le portail Microsoft Defender pour point de terminaison" lightbox="images/selecthelpandfeedback2.png":::

3. Sélectionnez « Envoyer des commentaires à Microsoft ».

    :::image type="content" alt-text="Sélectionnez Envoyer des commentaires à Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4. Choisissez parmi les options données. Pour signaler un problème, sélectionnez « Je veux signaler un problème ».

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Je souhaite signaler une option de problème" lightbox="images/report-issue-4.jpg":::

5. Fournissez des détails sur le problème auquel vous êtes confronté et vérifiez « Envoyer des données de diagnostic ». Nous vous recommandons de vérifier « Inclure votre adresse e-mail » afin que l’équipe puisse vous contacter à l’aide d’une solution ou d’un suivi.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Volet sur lequel vous pouvez ajouter des détails et joindre des données de diagnostic" lightbox="images/finalsubmit5.png":::

6. Cliquez sur « Envoyer » pour envoyer les commentaires.

