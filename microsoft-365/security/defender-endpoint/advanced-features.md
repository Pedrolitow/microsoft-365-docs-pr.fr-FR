---
title: Configurer des fonctionnalités avancées dans Microsoft Defender pour le point de terminaison
description: Activer des fonctionnalités avancées telles que bloquer un fichier dans Microsoft Defender pour le point de terminaison.
keywords: fonctionnalités avancées, paramètres, bloquer un fichier, examen automatisé, résolution automatique, skype, microsoft defender pour l’identité, office 365, azure information protection, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7fd9ec25c21b2d70238bd5b0d6b58b60731088ea
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845473"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Configurer des fonctionnalités avancées dans Defender pour le point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Selon les produits de sécurité Microsoft que vous utilisez, certaines fonctionnalités avancées peuvent vous être disponibles pour intégrer Defender for Endpoint.

## <a name="enable-advanced-features"></a>Activer les fonctionnalités avancées

1. Dans le volet de navigation, sélectionnez **Préférences configurer les**  >  **fonctionnalités avancées.**
2. Sélectionnez la fonctionnalité avancée que vous souhaitez configurer et basculez le paramètre entre **Le** et **Le.**
3. Cliquez **sur Enregistrer les préférences.**

Utilisez les fonctionnalités avancées suivantes pour être mieux protégés contre les fichiers potentiellement malveillants et obtenir une meilleure compréhension lors des enquêtes de sécurité.

## <a name="automated-investigation"></a>Examen automatisé

Activer cette fonctionnalité pour tirer parti des fonctionnalités automatisées d’examen et de correction du service. Pour plus d’informations, voir [Examen automatisé.](automated-investigations.md)

## <a name="live-response"></a>Réponse en direct

Activer cette fonctionnalité afin que les utilisateurs disposent des autorisations appropriées peuvent démarrer une session de réponse en direct sur les appareils.

Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles.](user-roles.md)

## <a name="live-response-for-servers"></a>Réponse en direct pour les serveurs
Activer cette fonctionnalité afin que les utilisateurs disposent des autorisations appropriées peuvent démarrer une session de réponse en direct sur les serveurs.

Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles.](user-roles.md)


## <a name="live-response-unsigned-script-execution"></a>Exécution de script non signé de réponse en direct

L’activation de cette fonctionnalité vous permet d’exécuter des scripts non signés dans une session de réponse en direct.

## <a name="always-remediate-pua"></a>Toujours corriger puA
Les applications potentiellement indésirables (PUA) sont une catégorie de logiciels qui peut ralentir votre ordinateur, afficher des publicités inattendues ou, au pire, installer d’autres logiciels qui peuvent être inattendus ou indésirables. 

Activer cette fonctionnalité afin que les applications potentiellement indésirables (PUA) soient corrigés sur tous les appareils de votre client, même si la protection PUA n’est pas configurée sur les appareils. Cela permet de protéger les utilisateurs contre l’installation accidentelle d’applications indésirables sur leur appareil. Lorsqu’elle est désactivée, la correction dépend de la configuration de l’appareil. 


## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Limiter la corrélation aux groupes d’appareils dans l’étendue
Cette configuration peut être utilisée dans les scénarios où les opérations SOC locales souhaitent limiter les corrélations d’alertes uniquement aux groupes d’appareils accessibles. En allumer ce paramètre, un incident composé d’alertes entre les groupes d’appareils ne sera plus considéré comme un incident unique. Le SOC local peut ensuite prendre des mesures sur l’incident, car il a accès à l’un des groupes d’appareils impliqués. Toutefois, la soc globale verra plusieurs incidents différents par groupe d’appareils au lieu d’un incident. Nous vous déconseillons d’allumer ce paramètre, sauf si cela l’emporte sur les avantages de la corrélation d’incidents dans l’ensemble de l’organisation.
>[!NOTE]
>La modification de ce paramètre a un impact sur les corrélations d’alertes futures uniquement.

## <a name="enable-edr-in-block-mode"></a>Activer PEPT en mode bloc
La détection et la réponse des points de terminaison (PEPT) en mode blocage offrent une protection contre les artefacts malveillants, même lorsque Antivirus Microsoft Defender est en cours d’exécution en mode passif. Lorsqu’elle est PEPT, elle bloque les artefacts ou comportements malveillants détectés sur un appareil. PEPT en mode blocage fonctionne en arrière-plan pour corriger les artefacts malveillants détectés après une violation.


## <a name="autoresolve-remediated-alerts"></a>Correction automatique des alertes

Pour les locataires créés sur ou après Windows 10, version 1809, la fonctionnalité d’examen et de correction automatisée est configurée par défaut pour résoudre les alertes où l’état des résultats de l’analyse automatisée est « Aucune menace trouvée » ou « Corrigé ».  Si vous ne souhaitez pas que les alertes se résolvent automatiquement, vous devez désactiver manuellement la fonctionnalité.

> [!TIP]
> Pour les locataires créés avant cette version, vous devez activer manuellement cette fonctionnalité à partir de la page [Fonctionnalités avancées.](https://securitycenter.windows.com/preferences2/integration)

> [!NOTE]
>
> - Le résultat de l’action de résolution automatique peut influencer le calcul du niveau de risque de l’appareil, qui est basé sur les alertes actives trouvées sur un appareil.
> - Si un analyste d’opérations de sécurité définit manuellement l’état d’une alerte sur « En cours » ou « Résolu », la fonctionnalité de résolution automatique ne l’est pas.

## <a name="allow-or-block-file"></a>Autoriser ou bloquer un fichier

Le blocage n’est disponible que si votre organisation répond aux exigences ci-après :

- Utilise Antivirus Microsoft Defender comme solution anti-programme malveillant active et,
- La fonctionnalité de protection basée sur le cloud est activée

Cette fonctionnalité vous permet de bloquer les fichiers potentiellement malveillants dans votre réseau. Le blocage d’un fichier empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation.

Pour activer **ou bloquer les fichiers** :

1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **fonctionnalités** avancées  >  **Autoriser ou bloquer le fichier**.

1. Basculez le paramètre entre **« On** » et **« Off**».

    ![Image des paramètres avancés pour la fonctionnalité bloquer les fichiers](images/atp-preferences-setup.png)

1. Sélectionnez **Enregistrer les préférences** en bas de la page.

Après avoir mis en place cette  fonctionnalité, vous pouvez bloquer [des](respond-file-alerts.md#allow-or-block-file) fichiers via l’onglet Ajouter un indicateur sur la page de profil d’un fichier.

## <a name="custom-network-indicators"></a>Indicateurs réseau personnalisés

Cette fonctionnalité vous permet de créer des indicateurs pour les adresses IP, les domaines ou les URL, qui déterminent s’ils seront autorisés ou bloqués en fonction de votre liste d’indicateurs personnalisée.

Pour utiliser cette fonctionnalité, les appareils doivent s’Windows 10 version 1709 ou ultérieure. Ils doivent également avoir une protection réseau en mode blocage et la version 4.18.1906.3 ou ultérieure de la plateforme anti-programme malveillant. Consultez la base de données [KB 4052623.](https://go.microsoft.com/fwlink/?linkid=2099834)

Pour plus d’informations, [voir Gérer les indicateurs.](manage-indicators.md)

> [!NOTE]
> La protection du réseau tire parti des services de réputation qui traiter les demandes dans des emplacements qui peuvent se trouve en dehors de l’emplacement que vous avez sélectionné pour vos données Defender pour le point de terminaison.

## <a name="tamper-protection"></a>Protection contre la falsification
Pendant certains types de cyberattaques, les acteurs malveillants tentent de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos ordinateurs. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils.

La protection contre la falsification verrouille Antivirus Microsoft Defender et empêche vos paramètres de sécurité d’être modifiés par le biais d’applications et de méthodes.

Cette fonctionnalité est disponible si votre organisation utilise Antivirus Microsoft Defender protection basée sur le cloud est activée. Pour plus d’informations, voir Utiliser les technologies de nouvelle génération Antivirus Microsoft Defender par le biais d’une [protection cloud.](cloud-protection-microsoft-defender-antivirus.md)

Maintenez la protection contre la falsification allumée pour empêcher les modifications indésirables apportées à votre solution de sécurité et à ses fonctionnalités essentielles.


## <a name="show-user-details"></a>Afficher les détails de l’utilisateur

Activer cette fonctionnalité pour que vous pouvez voir les détails de l’utilisateur stockés dans Azure Active Directory. Les détails incluent l’image, le nom, le titre et les informations de service d’un utilisateur lors de l’enquête sur les entités de compte d’utilisateur. Les informations de compte d’utilisateur sont disponibles dans les affichages suivants :

- Tableau de bord des opérations de sécurité
- File d’attente des alertes
- Page Détails de l’appareil

Pour plus d’informations, voir [Examiner un compte d’utilisateur.](investigate-user.md)


## <a name="skype-for-business-integration"></a>Skype Entreprise’intégration

L’activation de l Skype Entreprise’intégration vous permet de communiquer avec les utilisateurs à l’aide Skype Entreprise, du courrier électronique ou du téléphone. Cela peut être pratique lorsque vous devez communiquer avec l’utilisateur et atténuer les risques.

> [!NOTE]
> Lorsqu’un appareil est isolé du réseau, vous pouvez choisir d’activer les communications Outlook et Skype dans une fenêtre pop-up qui permet de communications à l’utilisateur pendant qu’il est déconnecté du réseau. Ce paramètre s’applique Skype et Outlook communication lorsque les appareils sont en mode d’isolation.

## <a name="microsoft-defender-for-identity-integration"></a>Intégration de Microsoft Defender pour l’identité

L’intégration à Microsoft Defender for Identity vous permet de pivoter directement dans un autre produit de sécurité Microsoft Identity. Microsoft Defender pour l’identité complète une enquête avec des informations supplémentaires sur un compte suspecté d’être compromis et les ressources associées. En activant cette fonctionnalité, vous enrichirez la fonctionnalité d’examen basé sur l’appareil en pivotant sur le réseau d’un point de vue d’identification.

> [!NOTE]
> Vous devez avoir la licence appropriée pour activer cette fonctionnalité.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Connexion Threat Intelligence

Cette fonctionnalité est disponible uniquement si vous disposez d’un Office 365 E5 ou du module add-on Threat Intelligence. Pour plus d’informations, voir la page Office 365 Entreprise produit E5.

Lorsque vous activerez cette fonctionnalité, vous serez en mesure d’incorporer des données de Microsoft Defender pour Office 365 dans Centre de sécurité Microsoft Defender pour mener une enquête de sécurité complète sur les boîtes aux lettres Office 365 et les appareils Windows.

> [!NOTE]
> Vous devez avoir la licence appropriée pour activer cette fonctionnalité.

Pour recevoir l’intégration d’appareils contextuels dans Office 365 Threat Intelligence, vous devez activer les paramètres Defender pour le point de terminaison dans le tableau de bord sécurité & conformité. Pour plus d’informations, voir [Examen et réponse aux menaces.](/microsoft-365/security/office-365-security/office-365-ti)

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Spécialistes des menaces Microsoft - Notifications d’attaque ciblée

Sur les deux composants De l’Expert en menaces Microsoft, la notification d’attaque ciblée est disponible en général. La fonctionnalité Experts à la demande est toujours en prévisualisation. Vous ne pouvez utiliser la fonctionnalité d’experts à la demande que si vous avez appliqué la prévisualisation et que votre application a été approuvée. Vous pouvez recevoir des notifications d’attaque ciblée de Spécialistes des menaces Microsoft via le tableau de bord des alertes de votre portail Defender pour les points de terminaison et par courrier électronique si vous le configurez.

> [!NOTE]
> La fonctionnalité Spécialistes des menaces Microsoft dans Defender pour le point de terminaison est disponible avec une licence E5 [pour Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).
## <a name="microsoft-cloud-app-security"></a>Microsoft Cloud App Security

L’activation de ce paramètre permet à Defender for Endpoint de Microsoft Cloud App Security fournir une visibilité plus approfondie de l’utilisation des applications cloud. Les données forwarded sont stockées et traitées au même emplacement que vos Sécurité des applications cloud données.

> [!NOTE]
> Cette fonctionnalité sera disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10, version 1709 (os Build 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (os build 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809 (os build 17763.379 avec [KB4489899](https://support.microsoft.com/help/4489899)) ou versions Windows 10 ultérieures.

## <a name="microsoft-secure-score"></a>Degré de sécurisation Microsoft

Envoie les signaux De Microsoft Defender pour point de terminaison au Niveau de sécurité Microsoft dans le centre Microsoft 365 sécurité. L’exploitation de cette fonctionnalité permet à Microsoft Secure Score de visibilité sur la posture de sécurité de l’appareil. Les données forwardées sont stockées et traitées au même emplacement que vos données du Score de sécurisation Microsoft.


### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Activer l’intégration de Microsoft Defender for Endpoint à partir du portail Microsoft Defender for Identity

Pour recevoir l’intégration d’appareils contextuels dans Microsoft Defender pour l’identité, vous devez également activer la fonctionnalité dans le portail Microsoft Defender pour l’identité.

1. Connectez-vous au [portail Microsoft Defender pour l’identité](https://portal.atp.azure.com/) à l’aide d’un rôle Administrateur général ou Administrateur de la sécurité.

2. Cliquez **sur Créer votre instance.**

3. Toggle the Integration setting to **On** and click **Save**.

Après avoir effectué les étapes d’intégration sur les deux portails, vous pourrez voir les alertes pertinentes dans la page Détails de l’appareil ou Détails de l’utilisateur.

## <a name="web-content-filtering"></a>Filtrage du contenu web
Bloquer l’accès aux sites web contenant du contenu indésirable et suivre l’activité web sur tous les domaines. Pour spécifier les catégories de contenu web que vous souhaitez bloquer, créez une stratégie de [filtrage de contenu web.](https://security.microsoft.com/preferences2/web_content_filtering_policy) Assurez-vous que vous avez une protection réseau en mode blocage lors du déploiement de la ligne de base de sécurité [microsoft Defender pour les points de terminaison.](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2)


## <a name="share-endpoint-alerts-with-microsoft-compliance-center"></a>Partager des alertes de point de terminaison avec le Centre de conformité Microsoft
Permet de remettre les alertes de sécurité des points de terminaison et leur état de triage au Centre de conformité Microsoft, ce qui vous permet d’améliorer les stratégies de gestion des risques internes avec des alertes et de corriger les risques internes avant qu’ils ne causent des dommages. Les données forwarded sont traitées et stockées au même emplacement que vos données Office 365 données.

Après avoir configuré les indicateurs de violation de la stratégie de sécurité dans les [paramètres](/microsoft-365/compliance/insider-risk-management-settings#indicators) de gestion des risques internes, les alertes Defender for Endpoint sont partagées avec la gestion des risques internes pour les utilisateurs applicables.



## <a name="microsoft-intune-connection"></a>Microsoft Intune connexion

Defender for Endpoint peut être intégré à [Microsoft Intune](/intune/what-is-intune) pour activer l’accès conditionnel basé sur les risques [de l’appareil.](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune) Lorsque vous [activerez cette fonctionnalité,](configure-conditional-access.md)vous serez en mesure de partager des informations sur l’appareil Defender for Endpoint avec Intune, ce qui améliore l’application de la stratégie.

> [!IMPORTANT]
> Vous devez activer l’intégration sur Intune et Defender pour le point de terminaison pour utiliser cette fonctionnalité. Pour plus d’informations sur les étapes spécifiques, voir [Configurer l’accès conditionnel dans Defender pour le point de terminaison.](configure-conditional-access.md)

Cette fonctionnalité est disponible uniquement si vous disposez des fonctionnalités suivantes :

- Un client sous licence pour Enterprise Mobility + Security E3 et Windows E5 (ou Microsoft 365 Entreprise E5)
- Un environnement Microsoft Intune, avec des appareils gérés par Intune Windows 10 [joints à Azure AD.](/azure/active-directory/devices/concept-azure-ad-join/)


### <a name="conditional-access-policy"></a>Stratégie d’accès conditionnel

Lorsque vous activez l’intégration Intune, Intune crée automatiquement une stratégie d’accès conditionnel (CA) classique. Cette stratégie d’ac classique est une condition préalable à la configuration des rapports d’état dans Intune. Elle ne doit pas être supprimée.

> [!NOTE]
> La stratégie d’ac classique créée par Intune est distincte des stratégies d’accès conditionnel [modernes,](/azure/active-directory/conditional-access/overview/)qui sont utilisées pour configurer les points de terminaison.


## <a name="device-discovery"></a>Découverte d’appareils
Vous permet de trouver des appareils non utilisés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. À l’aide d’appareils intégrés, vous pouvez rechercher des appareils non utilisés dans votre réseau et évaluer les vulnérabilités et les risques. Pour plus d’informations, voir [Détection d’appareils.](device-discovery.md)

> [!NOTE]
> Vous pouvez toujours appliquer des filtres pour exclure les appareils nonmanagés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes API pour filtrer les appareils nonmanagés. 

## <a name="preview-features"></a>Fonctionnalités en préversion

Découvrez les nouvelles fonctionnalités de la version préliminaire de Defender for Endpoint. Essayez les fonctionnalités à venir en allumer l’expérience d’aperçu.

Vous aurez accès aux fonctionnalités à venir, sur lesquelles vous pourrez nous faire part de vos commentaires afin d’améliorer l’expérience globale avant que les fonctionnalités ne soient généralement disponibles.




## <a name="related-topics"></a>Voir aussi

- [Mettre à jour les paramètres de rétention des données](data-retention-settings.md)
- [Configurer des notifications d’alerte](configure-email-notifications.md)
