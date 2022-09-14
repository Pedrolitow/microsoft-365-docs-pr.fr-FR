---
title: Nouveautés de Microsoft Defender pour point de terminaison sur Android
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour point de terminaison sur Android.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, macos, whatsnew
ms.service: microsoft-365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.subservice: mde
ms.openlocfilehash: 3ebaab5770cfc8a4c474b66b8c1cbd6717c8f36a
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679578"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Nouveautés de Microsoft Defender pour point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

>[!IMPORTANT]
> Le **moteur anti-programme malveillant** de Microsoft Defender pour point de terminaison est désormais en disponibilité générale. Tous les utilisateurs doivent disposer d’une version Microsoft Defender pour point de terminaison supérieure à **1.0.3815.0000** pour utiliser cette nouvelle fonctionnalité de protection contre les programmes malveillants. Les utilisateurs sur Microsoft Defender pour point de terminaison version inférieure à 1.0.3815.0000 recevront des notifications et des messages de superposition dans l’application pour mettre à jour leur application Microsoft Defender pour point de terminaison. Les utilisateurs peuvent cliquer sur le lien fourni dans le message de superposition pour accéder au magasin de jeux managé et mettre à jour l’application. 
>
> Si les utilisateurs ne peuvent pas accéder au Play Store, l’application peut être mise à jour via le portail d’entreprise. 

## <a name="privacy-controls"></a>Contrôles de confidentialité

Microsoft Defender pour point de terminaison sur Android active les contrôles de confidentialité pour les administrateurs et les utilisateurs finaux. Cela inclut les contrôles pour les appareils inscrits (GPM) et non inscrits (MAM) (en préversion). Les administrateurs peuvent configurer la confidentialité dans le rapport d’alerte, tandis que les utilisateurs finaux peuvent configurer les informations partagées avec leur organisation. Pour plus d’informations, consultez [contrôles de confidentialité (GPM)](/microsoft-365/security/defender-endpoint/android-configure#privacy-controls) et [contrôles de confidentialité (MAM).](/microsoft-365/security/defender-endpoint/android-configure-mam#configure-privacy-controls)

## <a name="optional-permissions-and-disable-web-protection"></a>Autorisations facultatives et désactivation de la protection web

Microsoft Defender pour point de terminaison sur Android active les **autorisations facultatives** dans le flux d’intégration. Actuellement, les autorisations requises par MDE sont obligatoires dans le flux d’intégration. Avec cette fonctionnalité, l’administrateur peut déployer MDE sur des appareils sans appliquer les autorisations **VPN** et **Accessibilité** obligatoires lors de l’intégration. Les utilisateurs finaux peuvent intégrer l’application sans les autorisations obligatoires et passer en revue ultérieurement ces autorisations. Cette fonctionnalité est actuellement présente uniquement pour les appareils non inscrits (MAM). Pour plus d’informations, consultez [autorisations facultatives](/microsoft-365/security/defender-endpoint/android-configure-mam#optional-permissions).


## <a name="microsoft-defender-on-android-enterprise-byod-personal-profile"></a>Profil personnel BYOD microsoft defender sur Android Entreprise
Microsoft Defender pour point de terminaison est désormais pris en charge sur le profil personnel Android Entreprise (BYOD uniquement) avec toutes les fonctionnalités clés, notamment l’analyse des programmes malveillants, la protection contre les liens de hameçonnage, la protection réseau et la gestion des vulnérabilités. Cette prise en charge est associée à [des contrôles de confidentialité](/microsoft-365/security/defender-endpoint/android-configure#privacy-controls) pour garantir la confidentialité des utilisateurs sur le profil personnel. Pour plus d’informations, lisez [l’annonce](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-the-public-preview-of-defender-for-endpoint-personal/ba-p/3370979) et le [guide de déploiement](/microsoft-365/security/defender-endpoint/android-intune#set-up-microsoft-defender-in-personal-profile-on-android-enterprise-in-byod-mode).

## <a name="network-protection"></a>Protection réseau
La protection réseau sur Microsoft Defender pour point de terminaison est désormais en préversion publique. La protection réseau offre une protection contre les menaces non autorisées Wi-Fi connexes, le matériel non fiable comme les périphériques d’ananas et avertit l’utilisateur si une menace associée est détectée. Les utilisateurs verront également une expérience guidée pour se connecter à des réseaux sécurisés et modifier des réseaux lorsqu’ils sont connectés à une connexion non sécurisée.

Il inclut plusieurs contrôles d’administration pour offrir de la flexibilité, tels que la possibilité de configurer la fonctionnalité à partir du centre microsoft Endpoint Manager Administration. Les administrateurs peuvent également activer les contrôles de confidentialité pour configurer les données envoyées par Defender pour point de terminaison à partir d’appareils Android. 

Si vous souhaitez participer à cette préversion publique, partagez votre ID de locataire avec nous sur networkprotection@microsoft.com. Pour plus d’informations, consultez [la protection réseau](/microsoft-365/security/defender-endpoint/android-configure).

>[!NOTE]
>Microsoft Defender n’est plus pris en charge pour les versions inférieures à 1.0.3011.0302. Les utilisateurs sont invités à effectuer une mise à niveau vers les dernières versions pour sécuriser leurs appareils.
Pour mettre à jour, les utilisateurs peuvent utiliser les étapes suivantes :
>1. Dans votre profil professionnel, accédez à Managed Play Store.
>2. Appuyez sur l’icône de profil en haut à droite, puis sélectionnez « Gérer les applications et l’appareil ».
>3. Recherchez MDE sous mises à jour disponibles, puis sélectionnez Mettre à jour.
>
>Si vous rencontrez des problèmes, [envoyez des commentaires dans l’application](/security/defender-endpoint/android-support-signin#send-in-app-feedback).

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Microsoft Defender pour point de terminaison est désormais Microsoft Defender dans le Play Store

Microsoft Defender pour point de terminaison est désormais disponible en tant que **Microsoft Defender** dans le play store. Avec cette mise à jour, l’application sera disponible en préversion pour **les consommateurs de la région des États-Unis**. En fonction de la façon dont vous vous connectez à l’application avec votre compte professionnel ou personnel, vous aurez accès aux fonctionnalités de Microsoft Defender pour point de terminaison ou aux fonctionnalités de Microsoft Defender pour les particuliers. Pour plus d’informations, consultez [ce blog](https://www.microsoft.com/microsoft-365/microsoft-defender-for-individuals) .

## <a name="vulnerability-management"></a>Gestion des vulnérabilités

Le 25 janvier 2022, nous avons annoncé la disponibilité générale de la gestion des vulnérabilités sur Android et iOS. Pour plus d’informations, consultez [le billet techcommunity ici](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Modifications d’autorisation à venir pour Microsoft Defender pour point de terminaison exécutant Android 11 ou version ultérieure (novembre 2021)

Version de publication : 1.0.3501.0301 Mois de publication : novembre 2021 Microsoft Defender pour point de terminaison a publié cette mise à jour requise par [Google](https://developer.android.com/distribute/play-policies#APILevel30) pour la mise à niveau vers l’API Android 30. Cette modification invite les utilisateurs à accéder à [une nouvelle autorisation de stockage](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) pour les appareils exécutant Android 11 ou version ultérieure. Les utilisateurs doivent accepter cette nouvelle autorisation de stockage une fois qu’ils ont mis à jour l’application Defender avec la version 1.0.3501.0301 ou ultérieure. Cela garantit que la fonctionnalité de sécurité des applications de Defender pour point de terminaison fonctionne sans interruption. Pour plus d’informations, consultez les sections suivantes.

**Comment cela affectera votre organisation :** Ces modifications prendront effet si vous utilisez Microsoft Defender pour point de terminaison sur les appareils exécutant Android 11 ou version ultérieure et que vous mettez à jour Defender pour point de terminaison pour publier la build 1.0.3501.0301 ou ultérieure.

> [!NOTE]
> Les nouvelles autorisations de stockage ne peuvent pas être configurées par l’administrateur pour « Approuver automatiquement » via Microsoft Endpoint Manager. L’utilisateur doit prendre des mesures pour fournir l’accès à cette autorisation.

- **Expérience utilisateur :** Les utilisateurs recevront une notification indiquant qu’il manque une autorisation pour la sécurité des applications. Si l’utilisateur refuse cette autorisation, la fonctionnalité « Sécurité des applications » est désactivée sur l’appareil. Si l’utilisateur n’accepte pas ou refuse l’autorisation, il continue à recevoir l’invite lors du déverrouillage de son appareil ou de l’ouverture de l’application, jusqu’à ce qu’elle ait été approuvée.

> [!NOTE]
> Si votre organisation affiche un aperçu de la fonctionnalité « Protection contre les falsifications » et si les nouvelles autorisations de stockage ne sont pas accordées par l’utilisateur dans les 7 jours suivant la mise à jour vers la dernière version, l’utilisateur risque de perdre l’accès aux ressources d’entreprise.

**Consignes de préparation :**

Informez vos utilisateurs et le support technique (le cas échéant) que les utilisateurs doivent accepter les nouvelles autorisations lorsqu’ils sont invités à mettre à jour Defender pour point de terminaison pour générer 1.0.3501.0301 ou version ultérieure. Pour accepter les autorisations, les utilisateurs doivent :

1. Appuyez sur la notification Defender pour point de terminaison dans l’application ou ouvrez l’application Defender pour point de terminaison. Les utilisateurs verront un écran qui répertorie les autorisations nécessaires. Une coche verte est manquante en regard de l’autorisation de stockage.

2. Appuyez **sur Commencer**.

3. Appuyez sur le bouton bascule Autoriser **l’accès pour gérer tous les fichiers.**

4. L’appareil est désormais protégé.

  > [!NOTE]
  > Cette autorisation permet à Microsoft Defender pour point de terminaison d’accéder au stockage sur l’appareil de l’utilisateur, ce qui permet de détecter et de supprimer les applications malveillantes et indésirables. Microsoft Defender pour point de terminaison accède/analyse uniquement au fichier de package d’application Android (.apk). Sur les appareils dotés d’un profil professionnel, Defender pour point de terminaison analyse uniquement les fichiers liés au travail.
