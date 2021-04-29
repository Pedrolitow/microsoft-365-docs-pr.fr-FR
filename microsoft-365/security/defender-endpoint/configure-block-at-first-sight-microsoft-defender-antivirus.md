---
title: Activer bloquer à la première vue pour détecter les programmes malveillants en quelques secondes
description: Activer la fonctionnalité Bloquer à la première vue pour détecter et bloquer les programmes malveillants en quelques secondes.
keywords: analyser, bloquer à la première vue, programmes malveillants, première vue, cloud, defender, antivirus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: priority
author: denisebmsft
ms.author: deniseb
ms.reviewer: marcmcc
manager: dansimp
ms.custom: nextgen
ms.date: 04/28/2021
ms.technology: mde
ms.openlocfilehash: d4db3549d04e5883f02ba263c06371371d385022
ms.sourcegitcommit: 8c89bc1d106b4716b07a1977d57e4d9ef98aecb3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52079202"
---
# <a name="turn-on-block-at-first-sight"></a> Activer le bloquage à première vue

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Cet article décrit une fonctionnalité antivirus/anti-programme malveillant appelée « bloquer à la première vue » et explique comment activer la fonctionnalité Bloquer à la première vue pour votre organisation. 

> [!TIP]
> Cet article est destiné aux administrateurs d'entreprise et aux professionnels de l'informatique qui gèrent les paramètres de sécurité pour les organisations. Si vous n'êtes pas un administrateur d'entreprise ou un professionnel de l'informatique, mais que vous avez des questions sur bloquer à la première vue, voir Pas un administrateur d'entreprise ou un [professionnel de l'informatique ?](#not-an-enterprise-admin-or-it-pro).

## <a name="what-is-block-at-first-sight"></a>Qu'est-ce que « bloquer à la première vue » ?

Bloquer à la première vue est une fonctionnalité de protection contre les menaces de la nouvelle génération qui détecte les nouveaux programmes malveillants et les bloque en quelques secondes. Bloquer à la première vue est activé lorsque certains paramètres de sécurité sont activés. Ces paramètres sont les suivants :

- Protection cloud 
- Un délai d'envoi d'exemple spécifié (par exemple, 50 secondes) ; et 
- Niveau de blocage de fichiers élevé. 

Dans la plupart des organisations, les paramètres nécessaires pour activer bloquer à la première vue sont configurés avec les déploiements de l'Antivirus Microsoft Defender. 

## <a name="how-it-works"></a>Fonctionnement

Lorsque l'Antivirus Microsoft Defender rencontre un fichier suspect mais non détecté, il interroge notre système de protection cloud. Le système back-end cloud applique l'heuristique, l'apprentissage automatique et l'analyse automatisée du fichier pour déterminer si les fichiers sont malveillants ou ne sont pas une menace.

L'Antivirus Microsoft Defender utilise plusieurs technologies de détection et de prévention pour fournir une protection précise, intelligente et en temps réel. 

![Liste des moteurs de Microsoft Defender AV](images/microsoft-defender-atp-next-generation-protection-engines.png)  

> [!TIP]
> Pour en savoir plus, consultez ce blog : Découvrez les technologies avancées au cœur de Microsoft Defender pour la protection nouvelle génération de point [de terminaison.](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>Quelques informations à connaître sur bloquer à la première vue

- Dans Windows 10, version 1803 ou ultérieure, bloquer à la première vue peut bloquer les fichiers exécutables non portables (tels que JS, VBS ou macros) et les fichiers exécutables.

- Bloquer à la première vue utilise uniquement le système de protection cloud pour les fichiers exécutables et les fichiers exécutables non portables qui sont téléchargés à partir d'Internet ou qui proviennent de la zone Internet. Une valeur de hachage du fichier .exe est vérifiée via le système backend cloud pour déterminer si le fichier est un fichier précédemment non détecté.

- Si le système cloud backend ne parvient pas à effectuer une détermination, l'Antivirus Microsoft Defender verrouille le fichier et charge une copie dans le cloud. Le cloud effectue davantage d'analyses pour parvenir à une détermination avant d'autoriser l'exécution du fichier ou de le bloquer dans toutes les futures rencontres, selon qu'il détermine si le fichier est malveillant ou non une menace.

- Dans de nombreux cas, ce processus peut réduire le temps de réponse des nouveaux programmes malveillants de plusieurs heures à quelques secondes.

- Vous pouvez [spécifier la durée d'exécution](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) d'un fichier pendant que le service de protection informatique analyse le fichier. De plus, vous pouvez personnaliser le message affiché sur le bureau des [utilisateurs](/windows/security/threat-protection//windows-defender-security-center/wdsc-customize-contact-information.md) lorsqu'un fichier est bloqué. Vous pouvez modifier le nom de la société, les informations de contact et l'URL du message.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Activer bloquer à la première vue avec Microsoft Intune

> [!TIP]
> Microsoft Intune fait désormais partie de Microsoft Endpoint Manager.

1. Dans le Centre d'administration Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), accédez aux **profils**  >  **de configuration des appareils.**

2. Sélectionnez ou créez un profil à l'aide du type de profil **Restrictions d'appareil.**

3. Dans les **paramètres de configuration du** profil restrictions d'appareil, définissez ou confirmez les paramètres suivants sous **l'Antivirus Microsoft Defender**:

   - **Protection cloud :** activée
   - **Niveau de blocage de fichiers**: Élevé
   - **Extension de temps pour l'analyse de fichiers par le cloud**: 50
   - **Invite des utilisateurs avant l'envoi** de l'échantillon : envoyer toutes les données sans invite

   ![Config Intune](images/defender/intune-block-at-first-sight.png)

4. Enregistrez vos paramètres.

> [!TIP]
> - La définition du niveau de blocage de fichiers **sur Élevé** applique un niveau élevé de détection. Dans le cas peu probable que le blocage de fichiers entraîne une détection de faux positifs de fichiers légitimes, votre équipe des opérations de sécurité peut restaurer les [fichiers mis en quarantaine.](./restore-quarantined-files-microsoft-defender-antivirus.md)
> - Pour plus d'informations sur la configuration des restrictions d'appareil de l'Antivirus Microsoft Defender dans Intune, voir Configurer les paramètres de [restriction d'appareil dans Microsoft Intune.](/intune/device-restrictions-configure)
> - Pour obtenir la liste des restrictions d'appareil de l'Antivirus Microsoft Defender dans Intune, voir Restriction d'appareil pour les [paramètres Windows 10 (et](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)les plus nouveaux) dans Intune.

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Activer bloquer à la première vue avec Microsoft Endpoint Manager

> [!TIP]
> Si vous recherchez Microsoft Endpoint Configuration Manager, il fait désormais partie de Microsoft Endpoint Manager.

1. Dans Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ), go to **Endpoint security**  >  **Antivirus**.

2. Sélectionnez une stratégie existante ou créez une stratégie à l'aide du type de profil **Antivirus Microsoft Defender.**

3. Définissez ou confirmez les paramètres de configuration suivants :

   - **Activer la protection cloud :** Oui
   - **Niveau de protection cloud :** élevé
   - **Délai d'out étendu de Defender Cloud en secondes**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Bloquer les paramètres à la première vue dans le Gestionnaire de point de terminaison":::

4. Appliquez le profil antivirus Microsoft Defender à un groupe, tel que Tous les utilisateurs, Tous les **appareils** ou Tous **les utilisateurs et appareils.**

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Activer bloquer à la première vue avec la stratégie de groupe

> [!NOTE]
> Nous vous recommandons d'utiliser Intune ou Microsoft Endpoint Manager pour activer bloquer à la première vue. 

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe que vous souhaitez configurer et sélectionnez **Modifier.** 

2. À **l'aide de l'Éditeur de gestion des stratégies** de groupe, go to **Computer configuration**  >  **Administrative**  >  **templates Windows Components**  >  **Microsoft Defender Antivirus**  >  **MAPS**. 

3. Dans la section MAPS, double-cliquez sur **Configurer** la fonctionnalité « Bloquer à la première vue » et définissez-la sur **Activé,** puis sélectionnez **OK.**

    > [!IMPORTANT]
    > Le fait **de définir Always prompt (0)** réduit l'état de protection de l'appareil. Le paramètre **Ne jamais envoyer (2)** signifie que bloquer à la première vue ne fonctionne pas.

4. Dans la section MAPS, double-cliquez sur Envoyer des **exemples** de fichiers lorsque d'autres analyses sont requises et définissez-la **sur Activé.** Sous **Envoyer des exemples de fichier lorsque d'autres analyses sont** **requises, sélectionnez Envoyer** tous les exemples, puis **sélectionnez OK.**

5. Redéployer votre objet de stratégie de groupe sur votre réseau comme vous le faites généralement.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Vérifier que bloquer à la première vue est activé sur des appareils clients individuels

Vous pouvez vérifier que bloquer à la première vue est activé sur des appareils clients individuels à l'aide de l'application Sécurité Windows. Bloquer à la première vue est automatiquement activé tant  que la protection cloud **et** l'envoi automatique d'échantillons sont tous deux activés.

1. Ouvrez l'application Sécurité Windows.

2. Sélectionnez **Protection & virus** contre les **menaces,** puis, sous Paramètres de protection contre & virus, sélectionnez Gérer **les paramètres.**

   ![Capture d'écran de l'étiquette & protection contre les virus dans l'application Sécurité Windows](images/defender/wdav-protection-settings-wdsc.png)

3. Confirmez **que la protection du cloud et** l'envoi automatique **d'échantillons** sont tous deux allumés.

> [!NOTE]
> - Si les paramètres prérequis sont configurés et déployés à l'aide de la stratégie de groupe, les paramètres décrits dans cette section sont grisés et ne peuvent pas être utilisés sur des points de terminaison individuels. 
> - Les modifications apportées via un objet de stratégie de groupe doivent d'abord être déployées sur des points de terminaison individuels avant que le paramètre ne soit mis à jour dans les paramètres Windows.

## <a name="validate-block-at-first-sight-is-working"></a>Vérifier que bloquer à la première vue fonctionne

Pour vérifier que la fonctionnalité fonctionne, suivez les instructions de Validation des [connexions entre votre réseau et le cloud.](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)

## <a name="turn-off-block-at-first-sight"></a>Désactiver bloquer à la première vue

> [!CAUTION]
> La non-utilisation du blocage à la première vue réduit l'état de protection de vos appareils et de votre réseau.

Vous pouvez choisir de désactiver bloquer à la première vue si vous souhaitez conserver les paramètres prérequis sans utiliser réellement la protection bloquer à la première vue. Vous pouvez désactiver temporairement bloquer à la première vue pour voir l'impact de cette fonctionnalité sur votre réseau. Toutefois, nous vous déconseillons de désactiver définitivement la protection bloquer à la première vue.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Désactiver bloquer à la première vue avec Microsoft Endpoint Manager

1. Go to Microsoft Endpoint Manager admin center ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ) and sign in.

2. Go to **Endpoint security**  >  **Antivirus,** and then select your Microsoft Defender Antivirus policy.

3. Under **Manage**, choose **Properties**.

4. En de côté **des paramètres de configuration,** choisissez **Modifier.**

5. Modifiez un ou plusieurs des paramètres suivants :

   - Définissez **Activer la protection cloud sur** **Non** ou **Non configuré.**
   - Définissez **le niveau de protection livré par le cloud** sur Non **configuré.**
   - Clear the check box for **Defender Cloud Extended Timeout In Seconds**.

6. Examinez et enregistrez vos paramètres.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Désactiver bloquer à la première vue avec la stratégie de groupe

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies** de groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d'administration.**

3. Développez l'arborescence à **travers les composants Windows** Microsoft Defender  >  **Antivirus**  >  **MAPS**.

4. Double-cliquez **sur Configurer la fonctionnalité «** Bloquer à la première vue » et définissez l'option sur **Désactivé.**

    > [!NOTE]
    > La désactivation de bloquer à la première vue ne désactive pas ou ne modifie pas les stratégies de groupe prérequises.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Vous n'êtes pas un administrateur d'entreprise ou un professionnel de l'informatique ?

Si vous n'êtes pas un administrateur d'entreprise ou un professionnel de l'informatique, mais que vous avez des questions sur bloquer à la première vue, cette section est pour vous. Bloquer à la première vue est une fonctionnalité de protection contre les menaces qui détecte et bloque les programmes malveillants en quelques secondes. Bien qu'il n'existe pas de paramètre spécifique appelé « Bloquer à la première vue », la fonctionnalité est activée lorsque certains paramètres sont configurés sur votre appareil.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Comment gérer bloquer à la première vue sur ou hors de votre propre appareil

Si vous avez un appareil personnel qui n'est pas géré par une organisation, vous vous demandez peut-être comment activer ou désactiver bloquer à la première vue. Vous pouvez utiliser l'application Sécurité Windows pour gérer bloquer à la première vue.

1. Sur votre ordinateur Windows 10, ouvrez l'application Sécurité Windows.

2. Sélectionnez **Protection contre & virus**.

3. Sous Paramètres & protection contre les virus contre les **menaces,** **sélectionnez Gérer les paramètres.**

4. Effectuez l’une des étapes suivantes :

   - Pour activer bloquer à la première vue, **assurez-vous** que la protection cloud et l'envoi automatique d'échantillons sont tous deux activés. 

   - Pour désactiver bloquer à la première vue, désactivez la protection cloud **ou** l'envoi **automatique d'échantillons.** <br/>
    
     > [!CAUTION]
     > La non-utilisation du blocage à la première vue réduit le niveau de protection de votre appareil. Nous vous déconseillons de désactiver définitivement bloquer à la première vue. 


## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Activer la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Restez protégé avec la sécurité Windows](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)