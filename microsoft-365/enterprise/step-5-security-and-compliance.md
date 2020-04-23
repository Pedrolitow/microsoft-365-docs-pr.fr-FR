---
title: 'Étape 5 : considérations relatives à la sécurité et à la conformité'
f1.keywords:
- NOCSH
ms.author: jogruszc
author: JGruszczyk
manager: jemed
ms.date: 05/20/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Découvrez les considérations importantes relatives à la sécurité et à la conformité de Windows et d’Office.
ms.openlocfilehash: 003064f521f1a68c01da9d6a2c9fb19eae7d3eaf
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636771"
---
# <a name="step-5-security-and-compliance-considerations"></a>Étape 5 : considérations relatives à la sécurité et à la conformité

![](../media/step-5-security-and-compliance-media/step-5-security-and-compliance-media-1.png)

<table>
<thead>
<td><img src="../media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-8.png" alt="Step 5" height="135" width="135" /></td>
<td><p><strong>Étape 5 : considérations relatives à la sécurité et à la conformité</strong></p>
<p>Windows 10 et Microsoft 365 Apps pour entreprise offrent non seulement de nouveaux moyens de protéger vos données, vos appareils et vos utilisateurs, mais aussi permettent de détecter et de traiter rapidement les menaces. De plus, découvrez comment traiter les problèmes courants liés au chiffrement du disque, aux applications anti-programme malveillant et aux stratégies lorsque vous migrez vers Windows 10.</p></td>
<td><a href="https://aka.ms/ddev5" target="_blank"><img src="../media/desktop-deployment-center-home-media/desktop-deployment-center-home-media-18.png" alt="Step 5" height="130" width="231" /></a></td>
</thead>
</table>

>[!NOTE]
>La partie relative à la sécurité et à la conformité est la cinquième étape de notre processus de déploiement recommandé couvrant les considérations relatives à la sécurité et à la conformité de Windows 10 et de Microsoft 365 Apps pour entreprise. Pour voir le processus complet de déploiement du bureau, visitez le [Centre de déploiement du bureau moderne](https://aka.ms/HowToShift).
>

Examinons maintenant les options de ciblage de nouvelles fonctionnalités de sécurité et de conformité dans le cadre du déploiement de Windows 10 et Microsoft 365 Apps pour entreprise, ainsi que les considérations et les obstacles courants lors de la migration des versions précédentes de Windows et d’Office. Bon nombre des fonctionnalités de sécurité dans Windows 10 seul façonne l’évolution vers la plateforme la plus récente. Par ailleurs, l’intégration avec les services cloud et les options d’identité utilisant Azure Active Directory donnent accès à de nouvelles protections mises à jour en permanence pour vos données, vos appareils et vos utilisateurs.

## <a name="overcoming-potential-security-related-deployment-blockers"></a>Surmonter les blocages potentiels du déploiement liés à la sécurité

Avant d’expliquer les nouvelles fonctionnalités que vous pouvez ajouter à mesure que vous migrez vers Windows 10 et Microsoft 365 Apps pour entreprise et connectez ces expériences au cloud, commençons avec quelques tendances actuelles qui peuvent souvent interrompre la progression du déploiement.

### <a name="disk-encryption"></a>Chiffrement du disque

Tout d’abord, l’un des premiers défis que vous pouvez rencontrer est le chiffrement de disque dur. De nombreuses solutions de chiffrement de disque dur ne peuvent pas facilement être mises à niveau à partir d’une version antérieure de Windows vers une version plus récente de Windows.

Certaines solutions de chiffrement de disque vous permettent d’effectuer les mises à niveau lors de l’utilisation de l’option « /reflectdrivers » avec la configuration de Windows sur certaines versions de ses plateformes, mais pour d’autres solutions, vous devrez peut-être déchiffrer le lecteur avant le déploiement, puis d’effectuer un nouveau chiffrement après l’installation de Windows 10. De plus, certaines solutions ne vous permettent pas de naviguer à partir de l’enregistrement de démarrage principal (MBR), à l’aide du BIOS hérité, vers la table de partition GUID (GPT), requise pour UEFI. Ceci est important, car la version 64 bits de Windows 10 avec UEFI est requise pour les nouvelles fonctionnalités de sécurité basée sur la virtualisation dans Windows 10. Celles-ci sont décrites ci-après.

Une des options permettant de résoudre ces problèmes est d’utiliser BitLocker dans Windows 10, inclus dans Windows 10 Professionnel et les éditions ultérieures. BitLocker vous permet de suspendre la protection pour les mises à niveau du système d’exploitation et les mises à jour des fonctionnalités dans le cadre du processus.

[Déploiement de base de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-basic-deployment)

### <a name="antivirus-and-antimalware-application-compatibility"></a>Compatibilité des applications anti-programme malveillant et antivirus

Ensuite, tandis que nous avons vu que plus de [99 % des applications Windows sont compatibles](https://www.microsoft.com/microsoft-365/blog/2018/09/06/helping-customers-shift-to-a-modern-desktop/) entre Windows 7 et Windows 10, les exceptions sont souvent les applications antivirus (AV) ou les clients de réseau privé virtuel (VPN). Ces applications implémentent régulièrement des API et des pratiques de développement non standard à l’aide de méthodes souvent non documentées pour protéger votre système ou vous connecter aux ressources réseau.

Par conséquent, ces applications peuvent par nature être fragilisées par les changements lors d’un transfert vers une nouvelle version de Windows. Si votre logiciel antivirus ou VPN ne fonctionne pas dans Windows 10 ou après la mise à niveau, la mesure corrective à prendre est généralement de remplacer l’application que vous utilisez avec une application prise en charge et testée sur Windows 10.

### <a name="security-policies"></a>Stratégies de sécurité

Les paramètres de stratégie de groupe Active Directory utilisés pour les versions antérieures de Windows et Office ne peuvent ne pas être directement transférés vers Windows 10 et Microsoft 365 Apps pour entreprise. De plus, il existe différentes considérations relatives aux nouvelles fonctionnalités de sécurité et de conformité. Il est recommandé d’utiliser le Kit de ressources Microsoft Security Compliance afin de recevoir la ligne de base des stratégies de sécurité pour les versions actuelles de Windows et d’Office. Par ailleurs, il s’avère intéressant de consulter les stratégies relatives à la gestion des appareils mobiles dans le cadre de Microsoft Intune.

![](../media/step-5-security-and-compliance-media/step-5-security-and-compliance-media-3.png)

## 

## <a name="new-security-and-compliance-capabilities-in-microsoft-365"></a>Nouvelles fonctionnalités de sécurité et de conformité dans Microsoft 365

Nous venons d’examiner les considérations pour migrer vos services de protection actuels et les points à prendre en compte avant d’effectuer la migration. Voyons maintenant les nouvelles fonctionnalités que vous pouvez utiliser lorsque vous passez à Windows 10, Microsoft 365 Apps pour entreprise et les options basées sur le cloud à partir d’EMS et au-delà.

### <a name="identity-and-access-management"></a>Gestion des identités et des accès

Commençons par la gestion des identités et des accès. Azure Active Directory est le plan de contrôle des identités pour les applications, appareils et services cloud. Il s’agit de la façon moderne de se connecter à Microsoft 365 et à d’autres services cloud. L’accès conditionnel vous permet de définir différentes exigences d’authentification basées sur l’emplacement d’origine de la connexion, l’appareil utilisé, ainsi que des éléments tels que des comportements inhabituels.

Au niveau de l’appareil, la biométrie peut fournir des identificateurs uniques pour assurer un accès plus simple et plus sécurisé à vos appareils et à vos applications, à mesure que vous avancez vers l’objectif d’éliminer les mots de passe. Windows Hello offre l’authentification multifacteur basée sur appareil. Elle repose sur l’appareil lui-même, votre code PIN ou un identificateur biométrique unique tel que votre visage ou vos empreintes digitales, que vous pouvez appliquer par le biais d’une stratégie.

[Principes de base de gestion des identités Azure](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-fundamentals)

[Comprendre les solutions d’identité Azure](https://docs.microsoft.com/azure/active-directory/fundamentals/understand-azure-identity-solutions)

[Accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

[Windows Hello Entreprise](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)

### <a name="virtualization-based-security"></a>Sécurité basée sur la virtualisation

Au-delà de l’identité, vous pouvez également activer la protection continue contre les menaces connues et inconnues. Pour ce faire, Windows 10 utilise la sécurité essentielle basée sur la virtualisation pour assurer l’intégrité au démarrage et l’intégrité du code à l’aide du démarrage sécurisé. Nous pouvons également aider à arrêter le vol d’informations d’identification avec Credential Guard en isolant les secrets des utilisateurs de Windows. De plus, Application Guard peut isoler et atténuer les menaces basées sur navigateur en exécutant le navigateur dans un conteneur isolé. Toutes ces technologies utilisent la sécurité basée sur la virtualisation dans Windows 10 et sont des changements fondamentaux qui ne peuvent pas être répliqués sur le système Windows 7. Notez que ces changements nécessitent également UEFI, Windows 64 bits et la prise en charge des extensions de virtualisation avec SLAT, au niveau du matériel.

[En savoir plus sur la sécurité basée sur la virtualisation](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-vbs)

### <a name="security-enhancements-from-cloud-services"></a>Améliorations en matière de sécurité des services cloud

Les services cloud fournissent une couche de protection supplémentaire facultative pour améliorer la sécurité de Windows et d’Office. Ils vous permettent d’améliorer le contrôle souvent en temps réel pouvant instantanément détecter, repousser et répondre aux nouvelles attaques et aux nouveaux types d’attaques, particulièrement par rapport à la mise à jour logicielle classique et aux fichiers de signature AV, où les délais de déploiement de mises à jour et de réponse sont intrinsèquement plus lents.

Grâce à Microsoft Intelligent Security Graph, vous avez plus rapidement accès aux informations et aux protections contre les menaces émergentes. Vous trouverez ci-dessous des exemples des services dont vous pouvez bénéficier, en commençant par Office.

Le service **[Protection contre la perte de données](https://docs.microsoft.com/office365/securitycompliance/data-loss-prevention-policies)** intégré à Microsoft 365 Apps pour entreprise vous aide à informer les utilisateurs des stratégies de sécurité lorsque du contenu à risque élevé, tel qu’une carte de crédit ou des numéros d’identification, est détecté. Les stratégies peuvent informer ou bloquer l’envoi et le partage après avoir averti les utilisateurs.

Le service **[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide)** est un service complémentaire qui peut être utilisé avec Office, permettant aux utilisateurs de classer et étiqueter facilement leurs fichiers Office. Il peut déclencher des actions automatiques sur des fichiers étiquetés, telles que le chiffrement ou le verrouillage du partage.

Nous avons également introduit le service de protection **[Liens fiables](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links)** dans les applications Office pour vous protéger contre une liste dynamique de sites web malveillants connus.

De plus, le service **[Pièces jointes fiables](https://docs.microsoft.com/office365/securitycompliance/atp-safe-attachments)** dans Outlook et dans Exchange Online va au-delà du filtrage d’e-mails pour contrôler les pièces jointes. Si une pièce jointe à risque élevé est identifiée, le service Pièces jointes fiables informe l’utilisateur des pièces jointes malveillantes connues et les supprime de la messagerie.

Le service **[Chiffrement de messages Office 365](https://docs.microsoft.com/office365/securitycompliance/encryption) ** (OME) peut également être utilisé pour assurer la protection de la messagerie et des pièces jointes envoyées, garantissant que seuls les destinataires visés peuvent voir le contenu de la messagerie. OME fonctionne de manière transparente avec l’authentification de compte client Google, Yahoo et Microsoft, et les mots de passe à usage unique permettent aux utilisateurs d’autres services de messagerie de recevoir aussi des e-mails en toute sécurité.

#### <a name="additional-windows-10-protections"></a>Protections supplémentaires dans Windows 10

Le service **[Contrôle d’application Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) ** dans Windows 10 permet de désactiver une liste approuvée d’applications autorisées ou refusées dont Microsoft a vérifié la sécurité et tout ce qui est géré par les stratégies de protection des points de terminaison à l’aide de Microsoft Intune.

Le service **[Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/overview)** est une plateforme unifiée dédiée à la protection préventive, à la détection de violation postérieure, à l’analyse automatisée et au traitement. Il protège les points de terminaison contre les cybermenaces, détecte les attaques avancées et les violations de données, automatise les incidents de sécurité et améliore la posture de sécurité.

Le service **[Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) ** permet de réduire la surface d’attaque pour l’exécution des applications en empêchant les programmes malveillants de s’infiltrer dans Windows et en bloquant les processus non approuvés d’accéder aux dossiers protégés.

#### <a name="microsoft-intune"></a>Microsoft Intune

[Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) fonctionne comme un service de gestion basé sur le cloud pour les scénarios mobiles, notamment les appareils Windows, Android et IOS, et peut désormais être configuré pour la co-gestion afin de parfaire et d’étendre des contrôles pour les charges de travail spécifiques gérées par le Gestionnaire de configuration. L’un des avantages ici est que les appareils accédant aux ressources protégées doivent parfois s’inscrire dans la gestion des appareils, même les appareils non gérés, les appareils joints sans domaine ou les appareils joints sans Azure AD. Vous pouvez également bénéficier de l’application de la configuration granulaire et d’une stratégie de conformité au niveau des applications et du système d’exploitation. Les paramètres et les stratégies d’applications peuvent être configurés de manière centralisée et appliqués pour les applications Microsoft 365 Apps pour entreprise et Store dans Windows 10 à l’aide de Microsoft Intune.

## <a name="next-step"></a>Étape suivante

## <a name="step-6-os-deployment-and-feature-updates"></a>[Étape 6 : déploiement du système d’exploitation et mises à jour des fonctionnalités](https://aka.ms/mdd6)

## <a name="previous-step"></a>Étape précédente 

## <a name="step-4-user-files-and-settings"></a>[Étape 4 : paramètres et fichiers utilisateur](https://aka.ms/mdd4)
