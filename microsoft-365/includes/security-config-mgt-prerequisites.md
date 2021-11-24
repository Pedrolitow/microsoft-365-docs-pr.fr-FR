---
title: fichier descriptif
description: inclure fichier
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 3a71ae9b77e49ff88c12383b00faf17d5a52b10d
ms.sourcegitcommit: b51bfed24a9e3b7adf82d4918b76462cd40dffaf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61155423"
---
## <a name="prerequisites"></a>Configuration requise

Examinez les sections suivantes pour obtenir les conditions requises pour la gestion de la sécurité de Microsoft Defender pour le scénario de point de terminaison :

### <a name="environment"></a>Environnement

Lorsqu’un appareil est intégré à Microsoft Defender pour le point de terminaison :

- L’appareil est interrogé pour une présence Endpoint Manager existante, Configuration Manager ou Intune
- Les appareils sans présence Endpoint Manager activent la fonctionnalité Gestion de la sécurité
- Une relation d’Azure Active Directory si elle n’existe pas déjà
- Azure Active Directory confiance est utilisée pour communiquer avec Endpoint Manager (Intune) et récupérer des stratégies
- La stratégie de récupération à Endpoint Manager est appliquée sur l’appareil par Microsoft Defender for Endpoint

### <a name="active-directory-requirements"></a>Conditions requises pour Active Directory

Lorsqu’un appareil joint à un domaine crée une relation d’Azure Active Directory, ce scénario est appelé scénario de joint Azure Active Directory *hybride.* La gestion de la sécurité de Microsoft Defender pour point de terminaison prend entièrement en charge ce scénario avec les conditions suivantes :

- Azure Active Directory Connecter (AAD Connecter) doit être synchronisé avec le client utilisé à partir de Microsoft Defender pour endpoint
- La joint Azure Active Directory hybride doit être configurée dans votre environnement (via federation ou AAD Connecter Sync)
- AAD Connecter Sync doit inclure les objets  d’appareil dans l’étendue pour la synchronisation avec Azure Active Directory (si nécessaire pour la jointage)
- AAD Connecter règles de synchronisation doivent être modifiées pour Server 2012 R2 (lorsque la prise en charge de Server 2012 R2 est nécessaire)
- Tous les appareils doivent s’inscrire dans le Azure Active Directory du client qui héberge Microsoft Defender for Endpoint. Les scénarios entre locataires ne sont pas pris en charge. 

### <a name="connectivity-requirements"></a>Prérequis en matière de connectivité

Les appareils doivent avoir accès aux points de terminaison suivants :

- `enterpriseregistration.windows.net`- Pour l Azure AD ins inscriptions.
- `login.microsoftonline.com`- Pour l Azure AD ins inscriptions.
- `*.dm.microsoft.com` - L’utilisation d’un caractère générique prend en charge les points de terminaison du service cloud qui sont utilisés pour l’inscription, l’enregistrement et les rapports, et qui peuvent changer à mesure que le service est à l’échelle.

### <a name="supported-platforms"></a>Plateformes prises en charge

Les stratégies de microsoft Defender pour la gestion de la sécurité des points de terminaison sont pris en charge pour les plateformes d’appareils suivantes :

- Windows 10 Professional/Enterprise (avec [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows Server 2012 R2 avec [Microsoft Defender pour Down-Level périphériques mobiles](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 avec [Microsoft Defender pour Down-Level appareils mobiles](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (avec [KB5006744)](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0)
- Windows Server 2022


### <a name="licensing-and-subscriptions"></a>Licences et abonnements

Pour utiliser la gestion de la sécurité pour Microsoft Defender pour le point de terminaison, vous devez :

- Un abonnement qui accorde des licences pour Microsoft Defender pour le point de terminaison, comme Microsoft 365, ou une licence autonome uniquement pour Microsoft Defender pour le point de terminaison. Pour plus d’informations sur les options, voir [Minimum requirements for Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/minimum-requirements).

  *Tout abonnement* qui accorde des licences Microsoft Defender pour les points de terminaison accorde également à votre client l’accès au nœud de sécurité endpoint du centre d Microsoft Endpoint Manager’administration. Le nœud de sécurité du point de terminaison est l’endroit où vous allez configurer et déployer des stratégies pour gérer Microsoft Defender pour le point de terminaison pour vos appareils et surveiller l’état de l’appareil.

## <a name="architecture"></a>Architecture

Le diagramme suivant est une représentation conceptuelle de la solution de gestion de la configuration de la sécurité de Microsoft Defender for Endpoint.


:::image type="content" alt-text="Représentation conceptuelle de la solution de gestion de la configuration de la sécurité de Microsoft Defender for Endpoint" source="../security/defender-endpoint/images/mde-architecture.png":::


1. Appareils intégrés à Microsoft Defender pour point de terminaison.

2. Une relation d’confiance est établie entre chaque appareil et Azure AD. Lorsqu’un appareil dispose d’une relation d’confiance existante, elle est utilisée. Lorsque les appareils ne sont pas enregistrés, une nouvelle relation d’confiance est créée.


3. Les appareils utilisent leur identité Azure AD pour communiquer avec les Endpoint Manager. Cette identité permet aux Microsoft Endpoint Manager de distribuer des stratégies ciblées sur les appareils lorsqu’ils sont connectés.

4. Defender pour le point de terminaison signale l’état de la stratégie à Endpoint Manager.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Configurer votre client pour prendre en charge Microsoft Defender pour endpoint Security Configuration Management

Pour prendre en charge microsoft Defender pour la gestion de la configuration de la sécurité des points de terminaison via le centre d’administration Microsoft Endpoint Manager, vous devez activer la communication entre eux à partir de chaque console.

1. Connectez-vous [Microsoft 365 Defender portail,](https://security.microsoft.com/) puis Paramètres l’étendue d’application de la gestion de la configuration des points de terminaison et activez les plateformes pour la gestion des  >    >    >   paramètres de sécurité :

   :::image type="content" source="../media/enable-mde-settings-management-defender.png" alt-text="Activez Microsoft Defender pour la gestion des paramètres de point de terminaison dans Microsoft 365 Defender portail.":::

2. Assurez-vous que les utilisateurs concernés sont autorisés à gérer les paramètres de sécurité des points de terminaison dans Microsoft Endpoint Manager ou à accorder ces autorisations en configurant un rôle dans le portail Microsoft 365 Defender. Go to **Paramètres**  >  **Roles**  >  **Add item:**

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Créez un rôle dans le portail Microsoft 365 Defender web.":::

   > [!TIP]
   > Vous pouvez modifier les rôles existants et ajouter les autorisations nécessaires par rapport à la création de rôles supplémentaires dans Microsoft Defender for Endpoint

3. Lors de la configuration du rôle, ajoutez des utilisateurs et assurez-vous de sélectionner Gérer les **paramètres** de sécurité des points de terminaison dans Microsoft Endpoint Manager :

   :::image type="content" source="../media/add-role.png" alt-text="Accorder aux utilisateurs des autorisations pour gérer les paramètres.":::

4. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Sélectionnez Sécurité des **points** de terminaison Microsoft Defender pour le point de terminaison et définissez Autoriser Microsoft Defender pour le point de terminaison à appliquer les configurations de sécurité des points de terminaison  >   **(prévisualisation)** **sur On**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Activez Microsoft Defender pour la gestion des paramètres de point de terminaison dans Microsoft Endpoint Manager’administration centrale.":::

   Lorsque vous définissez cette option sur *Sur*, tous les appareils de l’étendue de plateforme dans Microsoft Defender pour le point de terminaison qui ne sont pas gérés par Microsoft Endpoint Manager sont éligibles pour l’intégration à Microsoft Defender pour le point de terminaison.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

Microsoft Defender pour le point de terminaison prend en charge plusieurs options pour intégrer des appareils. Pour obtenir des instructions actuelles, voir [outils](/microsoft-365/security/defender-endpoint/security-config-management) et méthodes d’intégration pour Windows dans la documentation de Defender for Endpoint.

> [!IMPORTANT]
> Après l’intégration d’un appareil avec Microsoft Defender pour le point de terminaison, il doit être marqué avec **MDE-Management** avant de pouvoir s’inscrire auprès de la Gestion de la sécurité de Microsoft Defender pour endpoint. Pour plus d’informations sur le marquage des appareils dans MDE, voir [*Créer et gérer des balises d’appareil.*](/microsoft-365/security/defender-endpoint/machine-tag)

Les appareils que vous gérez avec Intune ou Configuration Manager ne sont pas pris en charge pour ce scénario.

## <a name="create-azure-ad-groups"></a>Créer Azure AD groupes

Une fois les appareils intégrés à Defender pour le point de terminaison, vous devez créer des groupes d’appareils pour prendre en charge le déploiement de la stratégie pour Microsoft Defender pour le point de terminaison.

Pour identifier les appareils qui ont été inscrits auprès de Microsoft Defender pour endpoint mais qui ne sont pas gérés par Intune ou Configuration Manager :

1. Connectez-vous [Microsoft Endpoint Manager centre d’administration.](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Go to **Devices**  >  **All devices**, and then select the column Managed **by** to sort the view of devices.

   Les appareils qui sont intégrés à Microsoft Defender pour Endpoint et qui sont inscrits mais qui ne sont pas gérés par Intune ou Configuration Manager affichent **Microsoft Defender pour point** de terminaison dans la colonne Géré *par.* Ce sont les appareils qui peuvent recevoir une stratégie de gestion de la sécurité pour Microsoft Defender pour endpoint.

Vous pouvez créer des groupes pour ces appareils dans [Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) ou à partir du centre d Microsoft Endpoint Manager’administration. [](/mem/intune/fundamentals/groups-add)

## <a name="deploy-policy"></a>Déployer une stratégie de protection des informations Windows

Après avoir créé un ou plusieurs groupes Azure AD qui contiennent des appareils gérés par Microsoft Defender pour Endpoint, vous pouvez créer et déployer les stratégies suivantes pour la gestion de la sécurité de Microsoft Defender for Endpoint sur ces groupes :

- Antivirus
- Pare-feu
- Règles de pare-feu
- Détection et réponse des points de terminaison

> [!TIP]
> Évitez de déployer plusieurs stratégies qui gèrent le même paramètre sur un appareil.
>
> Microsoft Endpoint Manager prend en charge le déploiement de plusieurs instances de chaque type de stratégie de sécurité de point de terminaison sur le même appareil, chaque instance de stratégie étant reçue par l’appareil séparément. Par conséquent, un appareil peut recevoir des configurations distinctes pour le même paramètre à partir de stratégies différentes, ce qui entraîne un conflit. Certains paramètres (comme les exclusions antivirus) fusionnent sur le client et s’appliquent correctement.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Go to **Endpoint security** and then select the type of policy you want to configure, either Antivirus or Firewall, and then select **Create Policy**.

3. Entrez les propriétés suivantes ou le type de stratégie que vous avez sélectionné :

   - Pour la stratégie antivirus, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et Windows Server (prévisualisation)**
     - Profil : **Antivirus Microsoft Defender (prévisualisation)**

   - Pour la stratégie de pare-feu, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et Windows Server (prévisualisation)**
     - Profil : **Pare-feu Microsoft Defender (aperçu)**

   - Pour la stratégie règles de pare-feu, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et Windows Server (prévisualisation)**
     - Profil : règles **du pare-feu Microsoft Defender (aperçu)**

   - Pour la stratégie de détection et de réponse des points de terminaison, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et Windows Server (prévisualisation)**
     - Profil : détection **et réponse des points de terminaison (aperçu)**

4. Sélectionnez **Créer**.

5. Dans la page **Informations de** base, entrez un nom et une description pour le profil, puis choisissez **Suivant**.

6. Dans la page **Paramètres de configuration,** sélectionnez les paramètres que vous souhaitez gérer avec ce profil. Pour en savoir plus sur un paramètre,  développez sa boîte de dialogue d’informations et sélectionnez le lien En savoir plus pour afficher les informations du programme CSP pour le paramètre dans la documentation en ligne.

   Quand vous avez terminé de configurer les paramètres, sélectionner **Suivant**.

7. Dans la page **Affectations,** sélectionnez les groupes Azure AD qui recevront ce profil. Pour plus d’informations sur l’affectation de profils, consultez [Affecter des profils d’utilisateur et d’appareil](/mem/intune/configuration/device-profile-assign).

   Sélectionnez **Suivant** pour continuer.

   > [!TIP]
   >
   > - Les filtres d’affectation ne sont pas pris en charge pour les profils de gestion de la configuration de la sécurité.
   > - Seuls *les objets device sont* applicables pour Microsoft Defender pour la gestion des points de terminaison. Le ciblage utilisateur n’est pas pris en charge.
   > - Les stratégies configurées s’appliquent aux clients Microsoft Intune et Microsoft Defender for Endpoint

8. Terminez le processus de création de stratégie, puis sur la page **Révision +** créer, sélectionnez **Créer.** Le profil que vous venez de créer apparaît dans la liste lorsque vous sélectionnez le type de stratégie pour le nouveau profil.

9. Attendez que la stratégie soit affectée et affichez une indication de réussite que la stratégie a été appliquée.

10. Vous pouvez vérifier que les paramètres sont appliqués localement sur le client à l’aide de l’utilitaire de commande [Get-MpPreference.](/powershell/module/defender/get-mppreference#examples)
