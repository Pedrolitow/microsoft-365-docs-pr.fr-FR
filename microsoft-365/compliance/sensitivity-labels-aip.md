---
title: Migrer le complément Azure Information Protection (AIP) vers Protection des données Microsoft Purview’étiquetage intégré pour les applications Office
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier1
search.appverid:
- MOE150
- MET150
description: Pour Office 365 applications, comprenez la migration du complément Azure Information Protection (AIP) vers l’étiquetage intégré pour protéger les données sensibles.
ms.openlocfilehash: b2cf7289bd93d29494625f23bc77cd759fc50920
ms.sourcegitcommit: ca082da1c51a3f643f152492579eef5679d52bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68547793"
---
# <a name="migrate-the-azure-information-protection-aip-add-in-to-built-in-labeling-for-office-apps"></a>Migrer le complément Azure Information Protection (AIP) vers l’étiquetage intégré pour les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Lorsque vous utilisez [des étiquettes de confidentialité](sensitivity-labels.md) dans Microsoft 365 Apps sur des ordinateurs Windows, nous vous recommandons d’utiliser l’étiquetage intégré aux applications Office, même si le [client d’étiquetage unifié Azure Information Protection (AIP)](/azure/information-protection/rms-client/aip-clientv2) est installé. À l’avenir, le complément AIP sera désactivé par défaut dans les dernières versions des applications Office.

Pour préparer cette modification, utilisez cet article pour comprendre les avantages de l’utilisation de l’étiquetage intégré, les principales fonctionnalités ayant la parité, et comment contrôler la migration du complément AIP vers l’expérience d’étiquetage plus récente.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="built-in-labeling-vs-the-aip-client"></a>Étiquetage intégré par rapport au client AIP

L’étiquetage intégré constitue la pierre angulaire d’un [déploiement Protection des données Microsoft Purview](information-protection-solution.md), car cette technologie d’étiquetage s’étend sur plusieurs plateformes (Windows, macOS, iOS, Android et web), ainsi que sur les applications et services Microsoft, et au-delà. L’étiquetage intégré est également conçu pour fonctionner avec d’autres fonctionnalités de Microsoft Purview, telles que la classification des données et Protection contre la perte de données Microsoft Purview (DLP).

Comme les étiquettes intégrées n'utilisent pas de module complémentaire d'Office, elles bénéficient d'une plus grande stabilité et de meilleures performances. Ils prennent également en charge les fonctionnalités Microsoft Purview les plus récentes, telles que les classifieurs avancés.

Jusqu’à récemment, l’étiquetage intégré était désactivé par défaut dans Office pour les applications Windows lors de l’installation du client AIP. Cette valeur par défaut ne sera plus le cas pour les versions plus récentes d’Office. Vous pouvez contrôler le comportement par défaut en suivant les instructions de la section suivante: [Comment désactiver le complément AIP pour utiliser l’étiquetage intégré pour les applications Office](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps). Par exemple, désactivez le complément pour les tests initiaux sur quelques ordinateurs, puis passez à un pilote pour quelques utilisateurs. Lorsque vous êtes prêt, migrez tous les utilisateurs vers l’expérience d’étiquetage plus récente.

Lorsque vous conservez le client AIP installé mais désactivé dans les applications Office, les autres fonctionnalités du client AIP restent prises en charge :

- Options de clic droit dans l'explorateur de fichiers pour que les utilisateurs puissent appliquer des étiquettes à tous les types de fichiers.

- Une visionneuse pour afficher les fichiers cryptés pour les textes, les images ou les documents PDF.

- Module PowerShell pour découvrir des informations sensibles dans des fichiers locaux, et appliquer ou supprimer des étiquettes et un chiffrement à partir de ces fichiers.

- Un scanner pour découvrir les informations sensibles stockées dans les magasins de données sur site, puis, en option, étiqueter ce contenu.

Pour plus d'informations sur ces fonctionnalités qui étendent l'étiquetage au-delà des applications Office, voir [le guide de l'administrateur du client d'étiquetage unifié ](/azure/information-protection/rms-client/clientv2-admin-guide)d' Azure Information Protection dans la documentation AIP.

Indépendamment de l'étiquetage, vous pouvez continuer à utiliser le module PowerShell [AIPService](/powershell/module/aipservice) pour la gestion du service de chiffrement au niveau des locataires. Par exemple, configurez l'accès des super-utilisateurs lorsque vous devez supprimer le cryptage pour la récupération des données, suivre et révoquer les documents qui ont été ouverts par le client AIP, et configurer la période de validité de la licence d'utilisation pour l'accès hors ligne. Pour plus d'informations, voir [Administrer la protection d' Azure Information Protection à l'aide de PowerShell](/azure/information-protection/administer-powershell).

> [!NOTE]
> Les étiquettes intégrées nécessitent une édition d'abonnement des applications Office. Si vous disposez d’éditions autonomes d’Office, parfois appelées « Office Perpetual », effectuez une mise à niveau vers Microsoft 365 Apps pour Entreprise afin de bénéficier des dernières fonctionnalités d’étiquetage.

## <a name="benefits-of-using-built-in-labeling-for-office-apps-vs-the-aip-add-in"></a>Avantages de l’utilisation de l’étiquetage intégré pour les applications Office et le complément AIP

Le client AIP est en [mode maintenance](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) et nous vous déconseillons d’utiliser le complément AIP pour les applications Office pour les raisons suivantes :

- Aucune nouvelle fonctionnalité d'étiquetage ne sera prise en charge.
- Les modules complémentaires sont moins stables car ils peuvent entrer en conflit avec d'autres modules complémentaires, ce qui peut entraîner la suspension ou le plantage des applications Office ou la désactivation automatique du module complémentaire.
- En tant que complément, il s’exécute [plus lentement](/deployoffice/fieldnotes/performance-recommendations#office-add-ins) et peut être désactivé par les utilisateurs pour contourner les exigences d’étiquetage.
- Toute correction de bogue nécessitera la réinstallation du client Azure Information Protection.
- The labeling experience for users is slightly different from built-in labels that users have on their other devices (macOS, iOS, Android), and when they use Office for the web. This difference can increase costs for training and support.
- De nouvelles fonctionnalités d’étiquetage Office ne sont prises [en charge que par l’étiquetage intégré](#features-supported-only-by-built-in-labeling-for-office-apps), et la liste ne cesse de croître.

Utilisez le complément AIP pour vos applications Windows Office uniquement si vous l'avez déjà déployé auprès des utilisateurs et que vous avez besoin de temps pour les faire migrer vers l'étiquetage intégré. Ou, s’il existe une fonctionnalité clé dont les utilisateurs ont besoin et qui n’est pas encore disponible pour leur canal de mise à jour Office.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Fonctionnalités prises en charge uniquement par l'étiquetage intégré pour les applications Office

> [!NOTE]
> De nombreuses nouvelles fonctionnalités d’étiquetage sont en cours de planification ou de développement. Attendez-vous donc à ce que la liste de cette section augmente au fil du temps.

Some features are only supported by built-in labeling for Office apps, and won't be supported by the AIP add-in. These include:

- Pour l’étiquetage automatique et recommandé :
    - Accès aux services de classification intelligents qui incluent [les classifieurs entraînables](classifier-learn-about.md), [la correspondance exacte des données (EDM)](sit-learn-about-exact-data-match-based-sits.md) et [les entités nommées](named-entities-learn.md)
    - Détection d'informations sensibles au moment de la saisie des utilisateurs
    - Dans Word, les utilisateurs peuvent examiner et supprimer le contenu sensible identifié.
- [Barre de confidentialité](sensitivity-labels-office-apps.md#sensitivity-bar) intégrée aux workflows utilisateur existants
- [Prise en charge du format PDF](sensitivity-labels-office-apps.md#pdf-support)
- Pour les étiquettes qui permettent aux utilisateurs d'attribuer des permissions, différentes permissions (lecture ou modification) peuvent être accordées aux utilisateurs ou aux groupes.
- Cryptage uniquement pour les e-mails
- Support pour le changement de compte
- Les utilisateurs ne peuvent pas désactiver l'étiquetage

Regardez une courte démonstration pour voir certaines de ces fonctionnalités en action :

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE58yhH]

Pour être informé de la disponibilité de nouvelles fonctionnalités d'étiquetage intégré, voir les sections [Nouveautés de Microsoft Purview](whats-new.md) et **Étiquettes de sensibilité**.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Comment désactiver le complément AIP pour utiliser l'étiquetage intégré des applications Office ?

Pour les dernières applications Office, le complément AIP est désactivé par défaut. Vous n’avez donc rien à configurer :

- **Build 16.0.15716.0+**: Actuellement dans le [canal bêta](https://office.com/insider)
- **Canal actuel** et **canal d’entreprise mensuel** : version 2211+ (pas encore publiée)
- **Canal semi-annuel** : version 2301+ (pas encore publiée)

Si vous avez l’une de ces versions et que vous devez utiliser le complément AIP plutôt que l’étiquetage intégré, vous devez [configurer un nouveau paramètre pour remplacer la valeur par défaut](#how-to-configure-newer-versions-of-office-to-enable-the-aip-add-in).

> [!IMPORTANT]
> Si vous avez déjà utilisé le complément AIP comme client d’étiquetage par défaut dans les applications Office et que vous utilisez les versions d’Office répertoriées dans cette section, le complément AIP est automatiquement désactivé et remplacé par l’étiquetage intégré.

Pour désactiver le complément AIP pour les versions antérieures, consultez la section suivante.

N’oubliez pas que lorsque le complément AIP est désactivé, vous pouvez toujours utiliser le client AIP pour étendre l’étiquetage au-delà des applications Office.

### <a name="how-to-configure-older-versions-of-office-to-disable-the-aip-add-in"></a>Comment configurer des versions antérieures d’Office pour désactiver le complément AIP

Pour les applications Office antérieures aux versions répertoriées dans la section précédente, pour empêcher le chargement du complément AIP dans les applications Office, utilisez la **stratégie de groupe définition de la liste des compléments managés** comme indiqué dans [Aucun complément chargé en raison des paramètres de stratégie de groupe pour les programmes Office 2013 et Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

Pour vos applications Windows Office qui prennent en charge l'étiquetage intégré, utilisez la configuration pour Microsoft Word 2016, Excel 2016, PowerPoint 2016 et Outlook 2016, spécifiez les identifiants programmatiques (ProgID) suivants pour le client AIP, et définissez l'option sur 0 **: Le module complémentaire est toujours désactivé (bloqué)**

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> If you use the Group Policy setting **Use the Sensitivity feature in Office to apply and view sensitivity labels** and set this to **1**, there are some situations where the AIP add-in might still load in Office apps. Blocking the add-in from loading in each app prevents this happening.

Vous pouvez également désactiver ou supprimer de manière interactive le complément Office **Microsoft Azure Information Protection** de Word, Excel, PowerPoint et Outlook. Cette méthode est appropriée pour un ordinateur unique et des tests ad-hoc. Pour obtenir de instructions, consultez [Afficher, gérer et installer des compléments dans les programmes Office (pour les utilisateurs)](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Quelle que soit la méthode choisie, les modifications prennent effet au redémarrage des applications Office.

Si, après avoir apporté ces modifications, le bouton **Confidentialité** ne s’affiche pas dans le ruban Office, vérifiez si l’étiquetage de sensibilité a été [désactivé](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows) avec **la fonctionnalité Utiliser la fonctionnalité De confidentialité dans Office pour appliquer et afficher le paramètre d’étiquettes de confidentialité** . Bien qu’il ne s’agit pas de la configuration par défaut pour les applications Office, un administrateur peut avoir défini explicitement cette configuration à l’aide de stratégie de groupe ou en modifiant directement le Registre.

### <a name="how-to-configure-newer-versions-of-office-to-enable-the-aip-add-in"></a>Comment configurer des versions plus récentes d’Office pour activer le complément AIP

> [!CAUTION]
> Si vous avez précédemment défini la valeur **d’Utiliser la fonctionnalité De confidentialité dans Office pour appliquer et afficher des étiquettes de confidentialité** sur **0** (ou si vous avez utilisé la clé de Registre équivalente **d’UseOfficeForLabelling**) pour désactiver l’étiquetage intégré, car vous souhaitiez utiliser le complément AIP : À l’avenir, si vous ne configurez pas le nouveau paramètre décrit dans cette section, vous ne pourrez pas utiliser l’étiquetage de sensibilité avec le complément AIP ou l’étiquetage intégré.

Dans les [versions plus récentes d’Office](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps), le complément AIP est désactivé par défaut. Pour l’activer, vous devez configurer un nouveau paramètre Office sous **Configuration utilisateur/Modèles d’administration/Microsoft Office 2016/Paramètres de sécurité** :

- **Utilisez le complément Azure Information Protection pour l’étiquetage de confidentialité**. Définissez la valeur sur **1**.

Déployez ce paramètre à l’aide d’une stratégie de groupe ou à l’aide du [service de stratégies cloud Office](/DeployOffice/overview-office-cloud-policy-service).

Vous devrez peut-être configurer d’autres paramètres Office :

1. Le paramètre de sécurité **Utiliser la fonctionnalité De confidentialité dans Office pour appliquer et afficher les étiquettes de confidentialité** doit être **0** ou non configuré.

2. Si la liste des compléments managés bloque le complément AIP, comme décrit dans la section précédente, vous devez supprimer ces entrées pour le complément AIP ou définir leur valeur sur **1 : le complément est toujours activé.** 

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Parité des fonctionnalités pour l'étiquetage intégré et le complément AIP pour les applications Office.

De nombreuses fonctions d'étiquetage prises en charge par le complément AIP sont désormais prises en charge par l'étiquetage intégré. Pour obtenir une liste plus détaillée des fonctionnalités disponibles, des versions minimales qui peuvent être nécessaires et des informations de configuration, consultez [Gérer les étiquettes de confidentialité dans les applications Office](sensitivity-labels-office-apps.md). Pour prendre en charge une fonctionnalité spécifique, vous devrez peut-être modifier votre [canal de mise à jour Office](/deployoffice/overview-update-channels).
 
More features are planned and in development. If there's a specific feature that you're interested in, check the [Microsoft 365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Information%20Protection&searchterms=label) and consider joining the [Microsoft Information Protection in Office Private Preview](https://aka.ms/MIP/PreviewRing).

Utilisez les informations suivantes pour vous aider à déterminer si les fonctionnalités que vous utilisez avec le complément AIP sont actuellement disponibles avec l’étiquetage intégré. Les fonctionnalités qui ne sont pas encore disponibles mais qui sont en cours de planification ou de déploiement peuvent retarder votre migration finale pour les utilisateurs, mais vous pouvez commencer à tester les autres fonctionnalités maintenant pour accélérer une migration ultérieure.

|Fonction ou capacité complémentaire de l'AIP|Étiquetage intégré |
|:-------------------------------|:----------------:|
|**Catégorie : Général** ||
|Rapports et audits centraux|![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Cloud pour le secteur public|![Pris en charge.](../media/yes-icon.png)|
|Administration pouvez désactiver l’étiquetage pour toutes les applications|  ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows)|
|**Catégorie : Expérience utilisateur** ||
|Bouton d'étiquetage sur le ruban|![Pris en charge.](../media/yes-icon.png)|
|Prise en charge multilingue des noms d'étiquettes et des infobulles| ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Visibilité des étiquettes sur une barre d’outils| [Dans la préversion](sensitivity-labels-office-apps.md#sensitivity-bar) |
|Couleurs des étiquettes| [Dans la préversion](sensitivity-labels-office-apps.md#label-colors) |
|**Catégorie : actions d’étiquetage** ||
|Étiquetage manuel |  ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Étiquetage par défaut | ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels.md#what-label-policies-can-do)|
|Étiquette par défaut <br> – Articles nouveaux et existants <br> - Paramètres distincts pour le mail|  ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels.md#what-label-policies-can-do) |
|Recommandé ou automatique |![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Justification du déclassement |  ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels.md#what-label-policies-can-do)|
| **Catégorie : Marquage visuel** | |
|En-têtes, pieds de page, filigrane| ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels.md#what-label-policies-can-do)|
|Marquage dynamique| ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Marquage visuel par application| ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Catégorie : Cryptage** | |
|Autorisations définies par l'administrateur | ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](encryption-sensitivity-labels.md#assign-permissions-now) |
|Permissions définies par l'utilisateur <br> - Ne pas transférer pour Outlook <br> – Permissions personnalisées des utilisateurs et des groupes pour Word, Excel, PowerPoint| ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Permissions définies par l'utilisateur <br> – Autorisations personnalisées à l'échelle de l'organisation en spécifiant les domaines pour Word, Excel, PowerPoint. | [Dans la préversion](encryption-sensitivity-labels.md#support-for-organization-wide-custom-permissions) |
|Co-auteur et AutoSave | ![Pris en charge.](../media/yes-icon.png) <br>[Si vous souhaitez en savoir plus](sensitivity-labels-coauthoring.md) |
| | |

N’oubliez pas d’utiliser la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?filters=Microsoft%20Information%20Protection&searchterms=label) pour identifier et suivre les nouvelles fonctionnalités en développement.

### <a name="support-for-powershell-advanced-settings"></a>Prise en charge des paramètres avancés de PowerShell

Le client AIP supporte de nombreuses personnalisations en utilisant les [paramètres avancés de PowerShell](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Pour connaître les paramètres avancés applicables aux applications Office qui sont également prises en charge par l’étiquetage intégré, consultez la liste dans [New-Label](/powershell/module/exchange/new-label) ou [Set-Label](/powershell/module/exchange/set-label), et [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) ou [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

Cependant, il se peut que vous n'ayez pas besoin d'utiliser PowerShell pour configurer les paramètres pris en charge, car ils sont inclus dans la configuration standard du portail de conformité Microsoft Purview. Par exemple, la configuration de l’interface utilisateur pour choisir les couleurs d’étiquette et désactiver l’étiquetage obligatoire pour Outlook.

Les configurations suivantes du complément AIP qui ne sont pas encore prises en charge par l’étiquetage intégré sont les suivantes :

- [Héritage des étiquettes à partir des pièces jointes des e-mails](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME pour Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
    - Ce paramètre commence à être [déployé en avant-première pour l'étiquetage intégré sur toutes les plateformes.](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook)
- [Messages popup de partage excessif pour Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Sous-étiquette par défaut pour une étiquette parent](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Supprimer les marquages de contenu externe](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Fonctionnalités non prévues pour être prises en charge par l'étiquetage intégré pour les applications Office

Bien que de nouvelles fonctionnalités pour l'étiquetage intégré soient ajoutées en permanence, le module complémentaire AIP Office prend en charge les fonctionnalités suivantes qui ne sont pas prévues pour être disponibles dans les futures versions de l'étiquetage intégré :

- Application des étiquettes aux formats Microsoft Office 97-2003, tels que les fichiers .doc.
- Journalisation de l’utilisation locale dans le journal des événements Windows
- Ordinateurs déconnectés de façon permanente
- Des éditions autonomes d'Office (parfois appelées « Office perpétuelle ») plutôt que des éditions sur abonnement.

## <a name="migration-planning-for-the-aip-add-in-for-office-apps"></a>Planification de la migration pour le complément AIP pour les applications Office

Pour passer en douceur à l’utilisation de l’étiquetage intégré pour les applications Office, utilisez les informations de cette page pour préparer un plan de migration qui inclut les tâches suivantes :

- Identifiez les fonctionnalités que vous utilisez actuellement et testez-les avec l’étiquetage intégré pour vous assurer que vous comprenez la configuration et l’expérience utilisateur.

- Identifiez les nouvelles fonctionnalités que vous souhaitez utiliser et décidez de les inclure dans la migration ou à une étape ultérieure.

- Assurez-vous que toutes les dépendances sont en place, telles que Microsoft 365 Apps pour Entreprise est déployée avec le canal de mise à jour correct et le complément AIP désactivé, et que [les licences appropriées sont attribuées aux utilisateurs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling).

- Mettez à jour la documentation et la formation internes, et préparez votre support technique et les utilisateurs pour le changement.

Pour vous aider dans votre parcours de migration, nous vous recommandons les [instructions de migration et le playbook de Microsoft Purview Customer Experience Engineering (CxE).](https://microsoft.github.io/ComplianceCxE/playbooks/AIP2MIPPlaybook)
