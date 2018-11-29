<a name="crit-windows10-step1"></a>
### <a name="required-your-microsoft-365-domains-are-added-and-verified"></a>Obligatoire : ajout et vérification de vos domaines Microsoft 365

Le locataire Azure AD pour vos abonnements Office 365 et Intune est configuré avec vos noms de domaines Internet (par exemple, contoso.com), plutôt qu’avec un nom de domaine incluant « onmicrosoft.com ». 

Sinon, vous êtes limité concernant les méthodes d’authentification configurables. Par exemple, les authentifications fédérée et directe ne peuvent pas utiliser le nom de domaine « onmicrosoft.com ».

Si nécessaire, l’[Étape 1](../windows10-prepare-your-org.md) peut vous aider à répondre à cette exigence.

### <a name="optional-your-users-are-added-and-licensed"></a>Facultatif : ajout de vos utilisateurs et obtention de licence

Les comptes correspondant à vos utilisateurs sont ajoutés, soit directement dans votre locataire Azure AD pour vos abonnements Office 365 et Intune, soit à partir de la synchronisation d’annuaires de votre version locale de Windows Server AD.

Une fois que les utilisateurs sont ajoutés, vous pouvez leur attribuer des licences Microsoft 365 Entreprise, soit directement en tant qu’administrateur d’utilisateurs ou administrateur général, soit automatiquement via l’appartenance à un groupe.

Si nécessaire, l’[Étape 1](../windows10-prepare-your-org.md) peut vous aider avec cette option.

### <a name="optional-diagnostics-are-enabled"></a>Facultatif : les diagnostics sont activés

Vous avez activé les paramètres de données de diagnostic à l’aide d’une stratégie de groupe, de Microsoft Intune, de l’éditeur du Registre ou à l’invite de commandes.

Si nécessaire, l’[Étape 1](../windows10-prepare-your-org.md) peut vous aider avec cette option.

<a name="crit-windows10-step2"></a>
### <a name="required-for-in-place-upgrade-created-a-configuration-manager-task-sequence-for-an-operating-system-deployment"></a>Obligatoire pour la mise à niveau sur place : création d’une séquence de tâches du Gestionnaire de configuration pour le déploiement d’un système d’exploitation

Pour démarrer une séquence de tâches du Gestionnaire de configuration afin d’effectuer une mise à niveau sur place sur un périphérique exécutant Windows 7 ou Windows 8.1, vous devez avoir :

- défini le niveau de données de diagnostic Windows approprié ;
- vérifié la préparation de la mise à niveau Windows ; et
- créé une séquence de tâches du Gestionnaire de configuration qui inclut une collection de périphériques et le déploiement d’un système d’exploitation avec une image de système d’exploitation Windows 10.

Une fois ces éléments en place, vous pouvez effectuer des mises à niveau sur place sur les périphériques qui sont prêts à recevoir la mise à niveau de Windows. Pour optimiser Microsoft 365 Entreprise, mettez à niveau autant de périphériques exécutant Windows 7 et Windows 8.1 que possible. 

Chaque périphérique exécutant Windows 10 Entreprise peut bénéficier des avantages de la solution intégrée de Microsoft 365 Entreprise. Les autres périphériques exécutant Windows 7 ou Windows 8.1 ne peuvent pas utiliser les technologies associées au cloud, ni les fonctionnalités de sécurité avancée de Windows 10 Entreprise.

Si nécessaire, l’[Étape 2](../windows10-deploy-inplaceupgrade.md) peut vous aider à répondre à cette exigence.

<a name="crit-windows10-step3"></a>
### <a name="required-for-new-devices-configured-windows-autopilot"></a>Obligatoire pour les nouveaux périphériques : configuration de Windows Autopilot

Pour utiliser Windows Autopilot afin de déployer et de personnaliser Windows 10 Entreprise sur un nouveau périphérique, vous devez :

- définir le niveau de données de diagnostic Windows approprié ; et
- remplir les conditions préalables pour Windows Autopilot, qui incluent les éléments suivants :
- Inscription du périphérique et personnalisation OOBE
- Insertion de la marque de votre entreprise pour OOBE
- Inscription automatique de la gestion des appareils mobiles dans Microsoft Intune
- Connectivité réseau aux services cloud utilisés par Windows Autopilot
- Pré-installation de Windows 10 version 1703 ou ultérieure sur les périphériques
- Sélection du programme de déploiement Windows Autopilot pour votre organisation

Une fois la configuration de Windows Autopilot terminée, vous pouvez l’utiliser pour configurer et personnaliser Windows 10 Entreprise pour OOBE (out-of-the-box experience) pour :

- les nouveaux périphériques et
- les périphériques qui ont déjà exécuté une configuration prédéfinie dans votre organisation. 

Windows Autopilot configure le périphérique et le connecte à Azure AD.

Sans Windows Autopilot, vous devez configurer manuellement les nouveaux périphériques, y compris la connexion à Azure AD.

Si nécessaire, l’[Étape 3](../windows10-deploy-autopilot.md) peut vous aider à répondre à cette exigence.

<a name="crit-windows10-step4"></a>
### <a name="optional-you-are-using-windows-analytics-device-health-to-monitor-your-windows-10-enterprise-based-devices"></a>Facultatif : utilisation de la fonctionnalité d’intégrité de l’appareil Windows Analytics pour surveiller vos périphériques basés sur Windows 10 Entreprise

Vous utilisez les informations de surveillance de l’intégrité des appareils pour détecter et solutionner les problèmes pouvant avoir une incidence sur les utilisateurs finaux. Résoudre rapidement les problèmes des utilisateurs permet de réduire vos coûts du support et de prouver à vos utilisateurs l’engagement de l’équipe informatique lié à Windows 10 Entreprise, ce qui permet de développer l’adoption au sein de votre organisation. 

Si nécessaire, l’[Étape 4](../windows10-enable-windows-analytics.md) peut vous aider avec cette option.

<a name="crit-windows10-step5a"></a>
### <a name="required-you-are-using-windows-defender-antivirus-or-your-own-antimalware-solution"></a>Obligatoire : utilisation de l’antivirus Windows Defender ou de votre propre solution anti-programme malveillant

Vous avez déployé l’antivirus Windows Defender ou votre propre solution antivirus pour protéger vos périphériques exécutant Windows 10 Entreprise contre les programmes malveillants. Si vous avez déployé l’antivirus Windows Defender, vous avez implémenté une méthode de création de rapports, telle que System Center Configuration Manager ou Microsoft Intune, pour surveiller l’activité et les événements antivirus.

Si nécessaire, l’[Étape 5](../windows10-enable-security-features.md#windows10-sec-av) peut vous aider à répondre à cette exigence.

<a name="crit-windows10-step5b"></a>
### <a name="required-you-are-using-windows-defender-exploit-guard"></a>Obligatoire : utilisation de Windows Defender Exploit Guard

Vous avez déployé Windows Defender Exploit Guard pour protéger vos périphériques exécutant Windows 10 Entreprise contre les intrusions et avez implémenté une méthode de création de rapports, telle que System Center Configuration Manager ou Microsoft Intune, pour surveiller les événements et l’activité liés aux intrusions.

Si nécessaire, l’[Étape 5](../windows10-enable-security-features.md#windows10-sec-eg) peut vous aider à répondre à cette exigence.

<a name="crit-windows10-step5c"></a>
### <a name="required-you-are-using-windows-defender-advanced-threat-protection-microsoft-365-enterprise-e5-only"></a>Obligatoire : utilisation du service Protection avancée contre les menaces Windows Defender (Microsoft 365 Entreprise E5 uniquement)

Vous avez déployé le service Protection avancée contre les menaces Windows Defender (ATP) pour détecter, examiner et traiter les menaces avancées contre votre réseau et vos périphériques exécutant Windows 10 Entreprise. 

Vous avez éventuellement intégré Windows Defender ATP à d’autres outils pour développer ses fonctionnalités.

Si nécessaire, l’[étape 5](../windows10-enable-security-features.md#windows10-sec-atp) peut vous aider à répondre à cette exigence.
