---
title: fichier descriptif
description: fichier descriptif
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: a836865906de594436b27c44ebf65ba3ed99c96e
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188191"
---
## <a name="prerequisites"></a>Conditions préalables

Passez en revue les sections suivantes pour connaître les conditions requises pour la gestion de la sécurité pour Microsoft Defender pour point de terminaison scénario :

### <a name="environment"></a>Environnement

Quand un appareil s’intègre à Microsoft Defender pour point de terminaison :


- L’appareil est interrogé pour une présence Endpoint Manager existante, qui est une inscription de gestion des appareils mobiles (GPM) à Intune
- Les appareils sans présence Endpoint Manager activeront la fonctionnalité Gestion de la sécurité
- Une approbation est créée avec Azure Active Directory si elle n’existe pas déjà
- Azure Active Directory confiance est utilisée pour communiquer avec Endpoint Manager (Intune) et récupérer des stratégies
- La récupération de stratégie à partir de Endpoint Manager est appliquée sur l’appareil par Microsoft Defender pour point de terminaison

### <a name="active-directory-requirements"></a>Configuration requise pour Active Directory

Lorsqu’un appareil joint à un domaine crée une approbation avec Azure Active Directory, ce scénario est appelé scénario *de jointure hybride Azure Active Directory*. La gestion de la sécurité pour Microsoft Defender pour point de terminaison prend entièrement en charge ce scénario avec les exigences suivantes :

- Azure Active Directory Connecter (AAD Connecter) doit être synchronisé avec le locataire utilisé à partir de Microsoft Defender pour point de terminaison
- La jonction Azure Active Directory hybride doit être configurée dans votre environnement (via la fédération ou AAD Connecter Sync)
- AAD Connecter Sync doit inclure les objets d’appareil *dans l’étendue* pour la synchronisation avec Azure Active Directory (si nécessaire pour la jointure)
- AAD Connecter règles de synchronisation doivent être modifiées pour Server 2012 R2 (lorsque la prise en charge de Server 2012 R2 est nécessaire)
- Tous les appareils doivent s’inscrire dans le Azure Active Directory du locataire qui héberge Microsoft Defender pour point de terminaison. Les scénarios interlocataires ne sont pas pris en charge. 

### <a name="connectivity-requirements"></a>Prérequis en matière de connectivité

Les appareils doivent avoir accès aux points de terminaison suivants :

- `enterpriseregistration.windows.net`- Pour Azure AD inscription.
- `login.microsoftonline.com`- Pour Azure AD inscription.
- `*.dm.microsoft.com` - L’utilisation d’un caractère générique prend en charge les points de terminaison de service cloud utilisés pour l’inscription, l’archivage et la création de rapports, et qui peuvent changer à mesure que le service évolue.

### <a name="supported-platforms"></a>Plateformes prises en charge

Les stratégies de gestion de la sécurité Microsoft Defender pour point de terminaison sont prises en charge pour les plateformes d’appareils suivantes :

- Windows 10 Professionnel/Enterprise (avec [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Professionnel/Enterprise
- Windows Server 2012 R2 avec [Microsoft Defender pour appareils Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 avec [Microsoft Defender pour les appareils Down-Level](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (avec [KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (avec [KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Licences et abonnements

Pour utiliser la gestion de la sécurité pour Microsoft Defender pour point de terminaison, vous devez :

- Un abonnement qui accorde des licences pour Microsoft Defender pour point de terminaison, comme Microsoft 365, ou une licence autonome pour uniquement Microsoft Defender pour point de terminaison. Un abonnement qui accorde Microsoft Defender pour point de terminaison licences accorde également à votre locataire l’accès au nœud de sécurité point de terminaison du centre d’administration Microsoft Endpoint Manager.

  > [!NOTE]  
  > **Exception** : si vous avez accès à Microsoft Defender pour point de terminaison dans le cadre d’une licence Microsoft Defender pour le cloud uniquement (anciennement Azure Security Center), la gestion de la sécurité pour Microsoft Defender pour point de terminaison fonctionnalité n’est pas disponible.

Le nœud de sécurité du point de terminaison est l’endroit où vous allez configurer et déployer des stratégies pour gérer Microsoft Defender pour point de terminaison pour vos appareils et surveiller l’état de l’appareil.

Pour plus d’informations sur les options, consultez [La configuration minimale requise pour Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Architecture

Le diagramme suivant est une représentation conceptuelle de la solution de gestion de la configuration de la sécurité Microsoft Defender pour point de terminaison.

:::image type="content" alt-text="Représentation conceptuelle de la solution de gestion de la configuration de la sécurité Microsoft Defender pour point de terminaison" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Appareils intégrés à Microsoft Defender pour point de terminaison.

2. Une approbation est établie entre chaque appareil et Azure AD. Lorsqu’un appareil a une approbation existante, celle-ci est utilisée. Lorsque les appareils ne sont pas inscrits, une nouvelle approbation est créée.

3. Les appareils utilisent leur identité Azure AD pour communiquer avec Endpoint Manager. Cette identité permet à Microsoft Endpoint Manager de distribuer les stratégies qui sont ciblées sur les appareils lors de leur enregistrement.

4. Defender pour point de terminaison renvoie l’état de la stratégie à Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Quelle solution dois-je utiliser ?

Microsoft Endpoint Manager inclut plusieurs méthodes et types de stratégies pour gérer la configuration de Defender pour point de terminaison sur les appareils.

Lorsque la protection de votre appareil doit aller au-delà de la gestion de Defender pour point de terminaison, consultez [la vue d’ensemble](/mem/intune/protect/device-protect) de la protection des appareils pour en savoir plus sur les fonctionnalités supplémentaires fournies par Microsoft Endpoint Manager pour protéger les appareils, notamment la *conformité* des appareils, les *applications gérées*, les *stratégies de protection des applications* et l’intégration avec des partenaires tiers de conformité et *de défense contre les menaces mobiles*.

Le tableau suivant peut vous aider à comprendre quelles stratégies qui peuvent configurer les paramètres MDE sont prises en charge par les appareils gérés par les différents scénarios. Lorsque vous déployez une stratégie prise en charge à la fois pour la *configuration de la sécurité MDE* et *Microsoft Endpoint Manager*, une seule instance de cette stratégie peut être traitée par les appareils qui exécutent MDE uniquement et les appareils gérés par Intune ou Configuration Manager.

| Gestionnaire de point de terminaison Microsoft  | Charge de travail | Configuration de la sécurité MDE  |  Gestionnaire de point de terminaison Microsoft |
|----------------|----------------|-------------------|------------|
| Sécurité de point de terminaison    | Antivirus                   | ![Pris en charge](../media/green-check.png)  | ![Pris en charge](../media/green-check.png)  |
|                      | Chiffrement du disque   |           | ![Pris en charge](../media/green-check.png)  |
|                      | Pare-feu (profil et règles)                | ![Pris en charge](../media/green-check.png) | ![Pris en charge](../media/green-check.png)  |
|                      | Détection et réponse du point de terminaison        | ![Pris en charge](../media/green-check.png) | ![Pris en charge](../media/green-check.png)  |
|                      | Réduction de la surface d'attaque    |           | ![Pris en charge](../media/green-check.png)  |
|                      | Protection des comptes       |       | ![Pris en charge](../media/green-check.png)  |
|                      | Conformité des appareils     |   | ![Pris en charge](../media/green-check.png)  |
|                      | Accès conditionnel    |   | ![Pris en charge](../media/green-check.png)  |
|                      | Bases de référence de sécurité      |   | ![Pris en charge](../media/green-check.png)  |

**Les stratégies de sécurité** des points de terminaison sont des groupes discrets de paramètres destinés à être utilisés par les administrateurs de sécurité qui se concentrent sur la protection des appareils de votre organisation.

- **Les stratégies antivirus** gèrent les configurations de sécurité trouvées dans Microsoft Defender pour point de terminaison. Consultez la  [stratégie antivirus](/mem/intune/protect/endpoint-security-antivirus-policy) pour la sécurité des points de terminaison.
- Les stratégies de **réduction de la surface d’attaque** se concentrent sur la réduction des endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Pour plus d’informations, consultez [Vue d’ensemble de la réduction de la surface d’attaque](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) dans la documentation Windows Protection contre les menaces et la stratégie de [réduction de la surface d’attaque](/mem/intune/protect/endpoint-security-asr-policy) pour la sécurité des points de terminaison.
- Les stratégies de **détection et de réponse** des points de terminaison (PEPT) gèrent les fonctionnalités defender pour point de terminaison qui fournissent des détections d’attaque avancées qui sont quasiment en temps réel et exploitables. En fonction de PEPT configurations, les analystes de sécurité peuvent hiérarchiser efficacement les alertes, obtenir une visibilité sur l’étendue complète d’une violation et prendre des mesures de réponse pour corriger les menaces. Consultez [protection évolutive des points de terminaison](/mem/intune/protect/endpoint-security-edr-policy) stratégie pour la sécurité des points de terminaison.
- **Les stratégies de pare-feu** se concentrent sur le pare-feu Defender sur vos appareils. Consultez la stratégie de [pare-feu](/mem/intune/protect/endpoint-security-firewall-policy) pour la sécurité des points de terminaison.
- **Les règles de pare-feu** configurent des règles granulaires pour les pare-feu, notamment des ports, des protocoles, des applications et des réseaux spécifiques. Consultez la stratégie de [pare-feu](/mem/intune/protect/endpoint-security-firewall-policy) pour la sécurité des points de terminaison.
- Les **bases de référence de sécurité** incluent des paramètres de sécurité préconfigurés qui définissent la posture de sécurité recommandée par Microsoft pour différents produits tels que Defender, Edge ou Windows. Les recommandations par défaut proviennent des équipes de produit appropriées et vous permettent de déployer rapidement cette configuration sécurisée recommandée sur les appareils. Bien que les paramètres soient préconfigurés dans chaque base de référence, vous pouvez en créer des instances personnalisées pour établir les attentes de sécurité de votre organisation. Consultez [les bases de référence de sécurité](/mem/intune/protect/security-baselines) pour Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Configurer votre locataire pour prendre en charge Microsoft Defender pour point de terminaison Security Configuration Management

Pour prendre en charge Microsoft Defender pour point de terminaison gestion de la configuration de la sécurité via le centre d’administration Microsoft Endpoint Manager, vous devez activer la communication entre elles à partir de chaque console.

1. Connectez-vous au [portail Microsoft 365 Defender](https://security.microsoft.com/) et accédez à **Paramètres** >  **EndpointsConfiguration** >  **ManagementEnforcement** >  Scope et activez les plateformes pour la gestion des paramètres de sécurité :

   :::image type="content" source="../media/security-settings-mgt.png" alt-text="Activez Microsoft Defender pour point de terminaison gestion des paramètres dans la console Defender.":::

    >[!NOTE]
    >Pour contrôler de manière granulaire l’étendue des points de terminaison gérés via la gestion des paramètres MDE, envisagez d’utiliser le **mode pilote**.

2. Assurez-vous que les utilisateurs concernés disposent des autorisations nécessaires pour gérer les paramètres de sécurité des points de terminaison dans Microsoft Endpoint Manager ou accordez ces autorisations en configurant un rôle dans le portail Defender. Accédez à **l’élément Paramètres** >  **RolesAdd** >  :

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Créez un rôle dans le portail Defender.":::

   > [!TIP]
   > Vous pouvez modifier des rôles existants et ajouter les autorisations nécessaires plutôt que de créer des rôles supplémentaires dans Microsoft Defender pour point de terminaison

3. Lors de la configuration du rôle, ajoutez des utilisateurs et veillez à sélectionner **Gérer les paramètres de sécurité des points de terminaison dans Microsoft Endpoint Manager** :

   :::image type="content" source="../media/add-role.png" alt-text="Accordez aux utilisateurs des autorisations pour gérer les paramètres.":::

4. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Sélectionnez **Sécurité** >  **du point de terminaison Microsoft Defender pour point de terminaison** et **définissez Autoriser Microsoft Defender pour point de terminaison pour appliquer les configurations de sécurité de point de terminaison (préversion)** à **Activé**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Activez Microsoft Defender pour point de terminaison gestion des paramètres dans le centre d’administration Microsoft Endpoint Manager.":::

   Lorsque vous définissez cette option *sur Activé*, tous les appareils de l’étendue de la plateforme dans Microsoft Defender pour point de terminaison qui ne sont pas gérés par Microsoft Endpoint Manager peuvent être intégrés à Microsoft Defender pour point de terminaison.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Intégrer des appareils à Microsoft Defender pour point de terminaison

Microsoft Defender pour point de terminaison prend en charge plusieurs options pour intégrer des appareils. Pour obtenir des conseils [actuels, consultez les outils et méthodes d’intégration pour Windows appareils](/microsoft-365/security/defender-endpoint/security-config-management) dans la documentation defender pour point de terminaison.


> [!IMPORTANT]
> Une fois qu’un appareil est intégré à Microsoft Defender pour point de terminaison, il doit et doit être marqué avec **MDE-Management** avant de pouvoir s’inscrire auprès de Security Management pour Microsoft Defender pour point de terminaison. Pour plus d’informations sur l’étiquetage des appareils dans MDE, consultez [*Créer et gérer des balises d’appareil*](/microsoft-365/security/defender-endpoint/machine-tags).


## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Coexistence avec Microsoft Endpoint Configuration Manager
Dans certains environnements, il peut être préférable d’utiliser la gestion de la sécurité pour Microsoft Defender conjointement avec Configuration Manager. Cela est possible en désactivant les **paramètres de gestion de la sécurité à l’aide de Configuration Manager** bascule dans la **page Paramètres** (Paramètres > points de terminaison > gestion de la configuration > l’étendue d’application) :

:::image type="content" source="../media/manage-security-settings-cfg-mgr.png" alt-text="Gérez les paramètres de sécurité à l’aide de Configuration Manager paramètre.":::

>[!NOTE]
>Lors de l’utilisation de Security Management pour Microsoft Defender pour point de terminaison avec Configuration Manager, la stratégie de sécurité de point de terminaison doit être isolée dans un seul plan de contrôle. Le contrôle de la stratégie via les deux canaux peut entraîner des conflits et des résultats indésirables.


## <a name="create-azure-ad-groups"></a>Créer des groupes Azure AD

Une fois les appareils intégrés à Defender pour point de terminaison, vous devez créer des groupes d’appareils pour prendre en charge le déploiement de la stratégie pour Microsoft Defender pour point de terminaison.

Pour identifier les appareils inscrits auprès de Microsoft Defender pour point de terminaison mais qui ne sont pas gérés par Intune ou Configuration Manager :

1. Connectez-vous [Microsoft Endpoint Manager centre d’administration.](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Accédez aux **appareils DevicesAll** > , puis sélectionnez la colonne **Gérée par** pour trier la vue des appareils.

   Les appareils qui s’intègrent à Microsoft Defender pour point de terminaison et qui sont inscrits mais qui ne sont pas gérés par Intune affichent **Microsoft Defender pour point de terminaison** dans la colonne *Gérée par*. Il s’agit des appareils qui peuvent recevoir une stratégie de gestion de la sécurité pour Microsoft Defender pour point de terminaison.

   Vous trouverez également deux étiquettes pour les appareils qui utilisent la gestion de la sécurité pour Microsoft Defender pour point de terminaison :

   - **MDEJoined** : ajouté aux appareils joints au répertoire dans le cadre de ce scénario.
   - **MDEManaged** - Ajouté aux appareils qui utilisent activement le scénario de gestion de la sécurité. Cette balise est supprimée de l’appareil si Defender pour point de terminaison cesse de gérer la configuration de sécurité.

Vous pouvez créer des groupes pour ces appareils [dans Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) ou [à partir du centre d’administration Microsoft Endpoint Manager](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>Déployer une stratégie de protection des informations Windows

Après avoir créé un ou plusieurs groupes Azure AD qui contiennent des appareils gérés par Microsoft Defender pour point de terminaison, vous pouvez créer et déployer les stratégies suivantes pour la gestion de la sécurité pour Microsoft Defender pour point de terminaison sur ces groupes :

- Antivirus
- Pare-feu
- Règles de pare-feu
- Détection et réponse des points de terminaison

> [!TIP]
> Évitez de déployer plusieurs stratégies qui gèrent le même paramètre sur un appareil.
>
> Microsoft Endpoint Manager prend en charge le déploiement de plusieurs instances de chaque type de stratégie de sécurité de point de terminaison sur le même appareil, chaque instance de stratégie étant reçue par l’appareil séparément. Par conséquent, un appareil peut recevoir des configurations distinctes pour le même paramètre à partir de différentes stratégies, ce qui entraîne un conflit. Certains paramètres (comme les exclusions antivirus) fusionnent sur le client et s’appliquent correctement.

1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Accédez à **Sécurité** des points de terminaison, sélectionnez le type de stratégie que vous souhaitez configurer, antivirus ou pare-feu, puis **sélectionnez Créer une stratégie**.

3. Entrez les propriétés suivantes ou le type de stratégie que vous avez sélectionné :

   - Pour la stratégie antivirus, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et serveur Windows (préversion)**
     - Profil : **Antivirus Microsoft Defender (préversion)**

   - Pour la stratégie de pare-feu, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et serveur Windows (préversion)**
     - Profil : **Pare-feu Microsoft Defender (préversion)**

   - Pour la stratégie règles de pare-feu, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et serveur Windows (préversion)**
     - Profil : **Règles de pare-feu Microsoft Defender (préversion)**

   - Pour la stratégie de détection et de réponse des points de terminaison, sélectionnez :
     - Plateforme : **Windows 10, Windows 11 et serveur Windows (préversion)**
     - Profil : **détection et réponse des points de terminaison (préversion)**

   >[!Note]
   > Ces profils s’appliquent à la fois aux appareils qui communiquent via Mobile Gestion des appareils (MDM) avec Microsoft Intune, ainsi qu’aux appareils qui communiquent à l’aide du client Microsoft Defender pour point de terminaison.
   >
   > Vérifiez que vous examinez votre ciblage et vos groupes si nécessaire.

4. Sélectionnez **Créer**.

5. Dans la page **De base**, entrez un nom et une description pour le profil, puis choisissez **Suivant**.

6. Dans la page **Paramètres de configuration** , sélectionnez les paramètres que vous souhaitez gérer avec ce profil. Pour en savoir plus sur un paramètre, développez sa boîte de dialogue d’informations et *sélectionnez le lien En savoir plus* pour afficher les informations CSP pour le paramètre dans la documentation en ligne.

   Quand vous avez terminé de configurer les paramètres, sélectionner **Suivant**.

7. Dans la page **Affectations**, sélectionnez les groupes Azure AD qui recevront ce profil. Pour plus d’informations sur l’affectation de profils, consultez [Affecter des profils d’utilisateur et d’appareil](/mem/intune/configuration/device-profile-assign).

   Sélectionnez **Suivant** pour continuer.

   > [!TIP]
   >
   > - Les filtres d’affectation ne sont pas pris en charge pour les profils Security Configuration Management.
   > - Seuls les *objets d’appareil* sont applicables à la gestion Microsoft Defender pour point de terminaison. Le ciblage des utilisateurs n’est pas pris en charge.
   > - Les stratégies configurées s’appliquent aux clients Microsoft Intune et Microsoft Defender pour point de terminaison

8. Terminez le processus de création de stratégie, puis dans la page **Vérifier + créer** , **sélectionnez Créer**. Le profil que vous venez de créer apparaît dans la liste lorsque vous sélectionnez le type de stratégie pour le nouveau profil.

9. Attendez que la stratégie soit affectée et affichez une indication de réussite de l’application de la stratégie.

10. Vous pouvez vérifier que les paramètres ont été appliqués localement sur le client à l’aide de l’utilitaire de commande [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
