---
title: Configurer des fonctionnalités avancées dans Microsoft Defender pour point de terminaison
description: Activez les fonctionnalités avancées telles que le fichier de blocs dans Microsoft Defender pour point de terminaison.
keywords: fonctionnalités avancées, paramètres, fichier de blocage, investigation automatisée, résolution automatique, skype, Microsoft Defender pour l’identité, Office 365, azure information protection, intune
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 8aafef819574d14871da0ee3199adfc5da6da2d0
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67798173"
---
# <a name="configure-advanced-features-in-defender-for-endpoint"></a>Configurer des fonctionnalités avancées dans Defender pour point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Selon les produits de sécurité Microsoft que vous utilisez, certaines fonctionnalités avancées peuvent être disponibles pour vous permettre d’intégrer Defender pour point de terminaison.

## <a name="enable-advanced-features"></a>Activer les fonctionnalités avancées

1. Dans le volet de navigation, sélectionnez **Paramètres points** \> **de terminaison Fonctionnalités avancées**\>.
2. Sélectionnez la fonctionnalité avancée que vous souhaitez configurer et basculez le paramètre entre **Activé** et **Désactivé**.
3. Cliquez sur **Enregistrer les préférences**.

Utilisez les fonctionnalités avancées suivantes pour mieux vous protéger contre les fichiers potentiellement malveillants et obtenir de meilleures informations lors des investigations de sécurité.

## <a name="automated-investigation"></a>Investigation automatisée

Activez cette fonctionnalité pour tirer parti des fonctionnalités d’investigation et de correction automatisées du service. Pour plus d’informations, consultez [Examen automatisé](automated-investigations.md).

## <a name="live-response"></a>Réponse en direct

> [!NOTE]
> La réponse en direct nécessite l’activation de **l’investigation automatisée** avant de pouvoir l’activer dans la section Paramètres avancés du portail Microsoft Defender pour point de terminaison.

Activez cette fonctionnalité afin que les utilisateurs disposant des autorisations appropriées puissent démarrer une session de réponse en direct sur les appareils.

Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

## <a name="live-response-for-servers"></a>Réponse en direct pour les serveurs

Activez cette fonctionnalité afin que les utilisateurs disposant des autorisations appropriées puissent démarrer une session de réponse en direct sur les serveurs.

Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

## <a name="live-response-unsigned-script-execution"></a>Exécution de scripts non signés de réponse en direct

L’activation de cette fonctionnalité vous permet d’exécuter des scripts non signés dans une session de réponse en direct.

## <a name="always-remediate-pua"></a>Toujours corriger pua

Les applications potentiellement indésirables (PUA) sont une catégorie de logiciels qui peuvent entraîner l’exécution lente de votre machine, afficher des publicités inattendues ou, au pire, installer d’autres logiciels, qui peuvent être inattendus ou indésirables.

Activez cette fonctionnalité afin que les applications potentiellement indésirables (PUA) soient corrigées sur tous les appareils de votre locataire, même si la protection PUA n’est pas configurée sur les appareils. Cette activation de la fonctionnalité permet de protéger les utilisateurs contre l’installation accidentelle d’applications indésirables sur leur appareil. Lorsqu’elle est désactivée, la correction dépend de la configuration de l’appareil.

## <a name="restrict-correlation-to-within-scoped-device-groups"></a>Restreindre la corrélation à l’intérieur des groupes d’appareils délimités

Cette configuration peut être utilisée pour les scénarios où les opérations SOC locales souhaitent limiter les corrélations d’alerte uniquement aux groupes d’appareils auxquels elles peuvent accéder. En activant ce paramètre, un incident composé d’alertes indiquant que les groupes inter-appareils ne seront plus considérés comme un incident unique. Le soc local peut alors prendre des mesures sur l’incident, car il a accès à l’un des groupes d’appareils impliqués. Toutefois, soc global verra plusieurs incidents différents par groupe d’appareils au lieu d’un incident. Nous vous déconseillons d’activer ce paramètre, sauf si cela l’emporte sur les avantages de la corrélation des incidents dans toute l’organisation.

> [!NOTE]
> La modification de ce paramètre affecte uniquement les corrélations d’alerte futures.

## <a name="enable-edr-in-block-mode"></a>Activer EDR en mode bloc

La détection et la réponse des points de terminaison (EDR) en mode bloc offrent une protection contre les artefacts malveillants, même lorsque l’antivirus Microsoft Defender s’exécute en mode passif. Lorsqu’il est activé, l’EDR en mode bloc bloque les artefacts ou comportements malveillants détectés sur un appareil. L’EDR en mode bloc fonctionne en arrière-plan pour corriger les artefacts malveillants détectés après la violation.

## <a name="autoresolve-remediated-alerts"></a>Alertes corrigées autoresolve

Pour les locataires créés sur ou après Windows 10, version 1809, la fonctionnalité d’investigation et de correction automatisée est configurée par défaut pour résoudre les alertes où l’état du résultat de l’analyse automatisée est « Aucune menace trouvée » ou « Corrigé ». Si vous ne souhaitez pas que les alertes soient résolues automatiquement, vous devez désactiver manuellement la fonctionnalité.

> [!TIP]
> Pour les locataires créés avant cette version, vous devez activer manuellement cette fonctionnalité à partir de la page [Fonctionnalités avancées](https://security.microsoft.com//preferences2/integration) .

> [!NOTE]
>
> - Le résultat de l’action de résolution automatique peut influencer le calcul du niveau de risque de l’appareil, qui est basé sur les alertes actives trouvées sur un appareil.
> - Si un analyste des opérations de sécurité définit manuellement l’état d’une alerte sur « En cours » ou « Résolu », la fonctionnalité de résolution automatique ne la remplacera pas.

## <a name="allow-or-block-file"></a>Autoriser ou bloquer un fichier

Le blocage n’est disponible que si votre organisation répond aux exigences suivantes :

- Utilise l’antivirus Microsoft Defender comme solution de logiciel anti-programme malveillant actif et,
- La fonctionnalité de protection basée sur le cloud est activée

Cette fonctionnalité vous permet de bloquer les fichiers potentiellement malveillants dans votre réseau. Le blocage d’un fichier empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation.

Pour activer **autoriser ou bloquer** des fichiers :

1. Dans le volet de navigation, sélectionnez **Paramètres des** \> **points de terminaison Fonctionnalités avancées générales** \>  \>  \> **Autoriser ou bloquer le fichier**.

1. Activez **et** **désactivez** le paramètre.
 
    :::image type="content" source="../../media/alloworblockfile.png" alt-text="Écran Points de terminaison" lightbox="../../media/alloworblockfile.png":::

1. Sélectionnez **Enregistrer les préférences** en bas de la page.

Après avoir activé cette fonctionnalité, vous pouvez [bloquer des fichiers](respond-file-alerts.md#allow-or-block-file) via l’onglet **Ajouter un indicateur** sur la page de profil d’un fichier.

## <a name="custom-network-indicators"></a>Indicateurs réseau personnalisés

L’activation de cette fonctionnalité vous permet de créer des indicateurs pour les adresses IP, les domaines ou les URL, qui déterminent s’ils seront autorisés ou bloqués en fonction de votre liste d’indicateurs personnalisée.

Pour utiliser cette fonctionnalité, les appareils doivent exécuter Windows 10 version 1709 ou ultérieure, ou Windows 11. Ils doivent également disposer d’une protection réseau en mode bloc et version 4.18.1906.3 ou ultérieure de la plateforme anti-programme malveillant [voir KB 4052623](https://go.microsoft.com/fwlink/?linkid=2099834).

Pour plus d’informations, consultez [Gérer les indicateurs](manage-indicators.md).

> [!NOTE]
> La protection réseau tire parti des services de réputation qui traitent les demandes dans des emplacements qui peuvent se trouver en dehors de l’emplacement que vous avez sélectionné pour vos données Defender pour point de terminaison.

## <a name="tamper-protection"></a>Protection contre les falsifications
Pendant certains types de cyberattaques, les mauvais acteurs essaient de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos machines. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils.

La protection contre les falsifications verrouille essentiellement l’Antivirus Microsoft Defender et empêche la modification de vos paramètres de sécurité par le biais d’applications et de méthodes.

Cette fonctionnalité est disponible si votre organisation utilise l’antivirus Microsoft Defender et que la protection basée sur le cloud est activée. Pour plus d’informations, consultez [Utiliser des technologies de nouvelle génération dans l’antivirus Microsoft Defender via une protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md).

Maintenez la protection contre les falsifications activée pour empêcher les modifications indésirables apportées à votre solution de sécurité et à ses fonctionnalités essentielles.

## <a name="show-user-details"></a>Afficher les détails de l’utilisateur

Activez cette fonctionnalité pour que vous puissiez voir les détails de l’utilisateur stockés dans Azure Active Directory. Les détails incluent l’image, le nom, le titre et les informations de service d’un utilisateur lors de l’examen des entités de compte d’utilisateur. Vous trouverez des informations sur le compte d’utilisateur dans les affichages suivants :

- File d’attente d’alertes
- Page détails de l’appareil

Pour plus d’informations, consultez [Examiner un compte d’utilisateur](investigate-user.md).

## <a name="skype-for-business-integration"></a>intégration Skype Entreprise

L’activation de l’intégration Skype Entreprise vous permet de communiquer avec les utilisateurs à l’aide de Skype Entreprise, d’e-mail ou de téléphone. Cette activation peut être pratique lorsque vous devez communiquer avec l’utilisateur et atténuer les risques.

> [!NOTE]
> Lorsqu’un appareil est isolé du réseau, il existe une fenêtre contextuelle dans laquelle vous pouvez choisir d’activer les communications Outlook et Skype, ce qui permet les communications à l’utilisateur lorsqu’il est déconnecté du réseau. Ce paramètre s’applique aux communications Skype et Outlook lorsque les appareils sont en mode isolation.

## <a name="microsoft-defender-for-identity-integration"></a>intégration Microsoft Defender pour Identity

L’intégration à Microsoft Defender pour Identity vous permet de pivoter directement dans un autre produit de sécurité Microsoft Identity. Microsoft Defender pour Identity augmente une enquête avec plus d’informations sur un compte suspecté compromis et les ressources associées. En activant cette fonctionnalité, vous allez enrichir la fonctionnalité d’investigation basée sur l’appareil en pivotant sur le réseau d’un point de vue d’identification.

> [!NOTE]
> Vous devez disposer de la licence appropriée pour activer cette fonctionnalité.

## <a name="office-365-threat-intelligence-connection"></a>connexion Office 365 Threat Intelligence

Cette fonctionnalité n’est disponible que si vous disposez d’un Office 365 E5 actif ou du module complémentaire Threat Intelligence. Pour plus d’informations, consultez la page du produit Office 365 Entreprise E5.

Lorsque vous activez cette fonctionnalité, vous pouvez incorporer des données de Microsoft Defender pour Office 365 dans Microsoft 365 Defender afin d’effectuer une enquête de sécurité complète sur Office 365 boîtes aux lettres et appareils Windows.

> [!NOTE]
> Vous devez disposer de la licence appropriée pour activer cette fonctionnalité.

Pour recevoir l’intégration contextuelle des appareils dans Office 365 Threat Intelligence, vous devez activer les paramètres Defender pour point de terminaison dans le tableau de bord Sécurité & Conformité. Pour plus d’informations, consultez [Enquête sur les menaces et réponse](/microsoft-365/security/office-365-security/office-365-ti).

## <a name="microsoft-threat-experts---targeted-attack-notifications"></a>Spécialistes des menaces Microsoft - Notifications d’attaque ciblée

Parmi les deux composants Microsoft Threat Expert, la notification d’attaque ciblée est en disponibilité générale. La fonctionnalité Experts à la demande est toujours disponible en préversion. Vous ne pouvez utiliser la fonctionnalité d’experts à la demande que si vous avez demandé la préversion et que votre application a été approuvée. Vous pouvez recevoir des notifications d’attaque ciblées de Spécialistes des menaces Microsoft via le tableau de bord des alertes de votre portail Defender pour point de terminaison et par e-mail si vous le configurez.

> [!NOTE]
> La fonctionnalité Spécialistes des menaces Microsoft dans Defender pour point de terminaison est disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

L’activation de ce paramètre transfère les signaux Defender pour point de terminaison à Microsoft Defender for Cloud Apps afin de fournir une visibilité plus approfondie sur l’utilisation des applications cloud. Les données transférées sont stockées et traitées au même emplacement que vos données Defender pour Cloud Apps.

> [!NOTE]
> Cette fonctionnalité sera disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10, version 1709 (build du système d’exploitation 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (build du système d’exploitation 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809  (OS Build 17763.379 avec [KB4489899](https://support.microsoft.com/help/4489899)), versions ultérieures Windows 10 ou Windows 11.

### <a name="enable-the-microsoft-defender-for-endpoint-integration-from-the-microsoft-defender-for-identity-portal"></a>Activer l’intégration Microsoft Defender pour point de terminaison à partir du portail Microsoft Defender pour Identity

Pour recevoir l’intégration contextuelle des appareils dans Microsoft Defender pour Identity, vous devez également activer la fonctionnalité dans le portail Microsoft Defender pour Identity.

1. Connectez-vous au [portail Microsoft Defender pour Identity](https://portal.atp.azure.com/) avec un rôle Administrateur général ou Administrateur de sécurité.

2. Cliquez sur **Créer votre instance**.

3. Activez le paramètre d’intégration **, puis** cliquez sur **Enregistrer**.

Une fois les étapes d’intégration effectuées sur les deux portails, vous pouvez voir les alertes pertinentes dans les détails de l’appareil ou la page de détails de l’utilisateur.

## <a name="web-content-filtering"></a>Filtrage du contenu web

Bloquez l’accès aux sites web contenant du contenu indésirable et suivez l’activité web dans tous les domaines. Pour spécifier les catégories de contenu web que vous souhaitez bloquer, créez une [stratégie de filtrage de contenu web](https://security.microsoft.com/preferences2/web_content_filtering_policy). Vérifiez que vous avez une protection réseau en mode bloc lors du déploiement de la [base de référence de sécurité Microsoft Defender pour point de terminaison](https://devicemanagement.microsoft.com/#blade/Microsoft_Intune_Workflows/SecurityBaselineSummaryMenu/overview/templateType/2).

## <a name="share-endpoint-alerts-with-microsoft-purview-compliance-portal"></a>Partager des alertes de point de terminaison avec portail de conformité Microsoft Purview

Transfère les alertes de sécurité de point de terminaison et leur état de triage à portail de conformité Microsoft Purview, ce qui vous permet d’améliorer les stratégies de gestion des risques internes avec des alertes et de corriger les risques internes avant qu’ils ne causent des dommages. Les données transférées sont traitées et stockées au même emplacement que vos données Office 365.

Après avoir configuré les [indicateurs de violation de stratégie de sécurité dans les paramètres](/microsoft-365/compliance/insider-risk-management-settings#indicators) de gestion des risques internes, les alertes Defender pour point de terminaison sont partagées avec la gestion des risques internes pour les utilisateurs applicables.

## <a name="authenticated-telemetry"></a>Télémétrie authentifiée

Vous pouvez **activer la** télémétrie authentifiée pour empêcher l’usurpation de données de télémétrie dans votre tableau de bord.

## <a name="microsoft-intune-connection"></a>connexion Microsoft Intune

Defender pour point de terminaison peut être intégré à [Microsoft Intune](/intune/what-is-intune) pour [activer l’accès conditionnel basé sur les risques de l’appareil](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune). Lorsque vous [activez cette fonctionnalité](configure-conditional-access.md), vous pouvez partager les informations de l’appareil Defender pour point de terminaison avec Intune, ce qui améliore l’application des stratégies.

> [!IMPORTANT]
> Vous devez activer l’intégration sur Intune et Defender pour point de terminaison pour utiliser cette fonctionnalité. Pour plus d’informations sur des étapes spécifiques, consultez [Configurer l’accès conditionnel dans Defender pour point de terminaison](configure-conditional-access.md).

Cette fonctionnalité n’est disponible que si vous disposez des prérequis suivants :

- Un locataire sous licence pour Enterprise Mobility + Security E3 et Windows E5 (ou Microsoft 365 Entreprise E5)
- Un environnement Microsoft Intune actif, avec des appareils Windows gérés par Intune [joints à Azure AD](/azure/active-directory/devices/concept-azure-ad-join/).

### <a name="conditional-access-policy"></a>Stratégie d’accès conditionnel

Lorsque vous activez Intune intégration, Intune crée automatiquement une stratégie d’accès conditionnel classique. Cette stratégie d’autorité de certification classique est un prérequis pour la configuration des rapports d’état sur Intune. Il ne doit pas être supprimé.

> [!NOTE]
> La stratégie d’autorité de certification classique créée par Intune est différente des [stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview/) modernes, qui sont utilisées pour configurer des points de terminaison.

## <a name="device-discovery"></a>Découverte d’appareils

Vous permet de trouver des appareils non gérés connectés à votre réseau d’entreprise sans avoir besoin d’appliances supplémentaires ou de modifications de processus fastidieuses. À l’aide d’appareils intégrés, vous pouvez trouver des appareils non gérés dans votre réseau et évaluer les vulnérabilités et les risques. Pour plus d’informations, consultez [Découverte d’appareils](device-discovery.md).

> [!NOTE]
> Vous pouvez toujours appliquer des filtres pour exclure les appareils non gérés de la liste d’inventaire des appareils. Vous pouvez également utiliser la colonne d’état d’intégration sur les requêtes d’API pour filtrer les appareils non gérés.

## <a name="preview-features"></a>Fonctionnalités de préversion

Découvrez les nouvelles fonctionnalités de la préversion de Defender pour point de terminaison. Essayez les fonctionnalités à venir en activant l’expérience de préversion.

Vous aurez accès aux fonctionnalités à venir, sur lesquelles vous pouvez fournir des commentaires pour améliorer l’expérience globale avant que les fonctionnalités ne soient généralement disponibles.

## <a name="download-quarantined-files"></a>Télécharger des fichiers mis en quarantaine

Sauvegardez les fichiers mis en quarantaine dans un emplacement sécurisé et conforme afin qu’ils puissent être téléchargés directement à partir de la quarantaine. Le bouton **Télécharger le fichier** est toujours disponible dans la page du fichier. Ce paramètre est activé par défaut. [En savoir plus sur les exigences](respond-file-alerts.md#download-quarantined-files)

## <a name="related-topics"></a>Voir aussi

- [Mettre à jour les paramètres de rétention des données](data-retention-settings.md)
- [Configurer des notifications d’alerte](configure-email-notifications.md)
