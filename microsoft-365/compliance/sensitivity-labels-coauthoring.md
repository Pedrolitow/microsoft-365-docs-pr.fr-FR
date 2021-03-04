---
title: Activer la co-édition pour les documents chiffrés par étiquettes de niveau de confidentialité dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
ms.topic: article
description: Activez un paramètre qui permet la co-édition et l’enregistrement automatique dans les applications de bureau pour les documents étiquetés et chiffrés dans SharePoint et OneDrive.
ms.openlocfilehash: a5c3e84e4ca8874f99a07294dccfd2e4ad7ed81f
ms.sourcegitcommit: 070724118be25cd83418d2a56863da95582dae65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "50417378"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Activer la co-édition pour les fichiers chiffrés avec les étiquettes de confidentialité

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

> [!NOTE]
> Cette fonctionnalité est en phase aperçu et est sujette à modifications. 
>
> Activez cette fonctionnalité dans un client de test plutôt que dans un client de production, car :
> - Cette fonctionnalité apporte des modifications aux métadonnées d'étiquetage et toutes les applications sur toutes les plateformes ne prennent pas actuellement en charge cette modification.
> - Vous ne pouvez pas désactiver cette fonction vous-même une fois qu'elle est activée

Activez le paramètre pour prendre en charge la [co-édition](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) pour les applications de bureau Office de telle sorte que lorsque les documents sont étiquetés et chiffrés par les [Étiquettes de confidentialité](sensitivity-labels.md), plusieurs utilisateurs peuvent modifier ces documents en même temps.

Si ce paramètre n’est pas activé pour votre client, les utilisateurs doivent consulter un document chiffré stocké dans SharePoint ou OneDrive lorsqu’ils utilisent les applications de bureau Office. Par conséquent, ils ne peuvent pas collaborer en temps réel. Ils doivent également utiliser Office sur le web lorsque les [étiquettes de confidentialité sont activées pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

En outre, l'activation de cette fonctionnalité entraîne la prise en charge de la fonctionnalité [Enregistrement automatique](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) pour ces fichiers étiquetés et chiffrés.

## <a name="metadata-changes-for-sensitivity-labels"></a>Modifications des métadonnées pour les étiquettes de niveau de confidentialité

> [!IMPORTANT]
> Après avoir activé le paramètre de co-édition, les informations d’étiquette des fichiers non chiffrés ne sont plus enregistrées dans les propriétés personnalisées.
> 
> N'activez pas ce paramètre si vous avez des applications, services, scripts ou outils dans votre organisation qui lisent ou écrivent des métadonnées d'étiquetage à l'ancien emplacement.

Avant d'activer le paramètre de prise en charge de la co-édition pour les applications de bureau Office, il est important de comprendre que cette action apporte des modifications aux métadonnées d'étiquetage qui sont enregistrées et lues dans les fichiers Office.

Les métadonnées d’étiquetage incluent des informations qui identifient votre client et l’étiquette de confidentialité qui vous a été appliquée. Ce paramètre modifie le format des métadonnées et l'emplacement des fichiers non chiffrés pour Word, Excel et PowerPoint. Il n'y a pas de modification des métadonnées d'étiquetage pour les fichiers ou les courriers électroniques chiffrés.

Cette modification affecte à la fois les dossiers nouvellement étiquetés et les dossiers déjà étiquetés. Lorsque vous utilisez des applications et des services qui prennent en charge le paramètre de co-édition :
- Pour les fichiers nouvellement étiquetés, seuls le nouveau format et le nouvel emplacement sont utilisés pour les métadonnées d'étiquetage.
- Pour les fichiers déjà étiquetés, la prochaine fois que le fichier est ouvert et enregistré, si le fichier possède des métadonnées dans l’ancien format et dans l’ancien emplacement, il est copié dans le nouveau format et le nouvel emplacement.

Pour en savoir plus sur le changement de métadonnées à partir des ressources suivantes :

- Billet de blog : [Modifications à venir concernant le stockage des métadonnées de protection des informations Microsoft](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Ouvrir spécifications : [2.6.3 LabelInfo et propriétés de document personnalisées](https://docs.microsoft.com/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

En raison de ces modifications, n'activez pas ce paramètre si vous avez des applications, services, scripts ou outils dans votre organisation qui lisent ou écrivent des métadonnées d'étiquetage à l'ancien emplacement. Dans ce cas, voici quelques exemples de conséquences :

- Un document étiqueté apparaît pour les utilisateurs comme sans étiquette

- Un document affiche une étiquette périmée aux utilisateurs

- La co-édition et l’enregistrement automatique ne fonctionnent pas pour un document étiqueté et chiffré si un autre utilisateur l’a ouvert dans une application de bureau Office qui ne prend pas en charge les nouvelles métadonnées d’étiquetage

- Une règle de flux de messagerie Exchange Online qui [identifie les étiquettes comme des propriétés personnalisées dans les pièces jointes Office](https://docs.microsoft.com/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) ne permet pas de chiffrer le courrier et la pièce jointe, ou les chiffre de manière incorrecte

Consultez la section suivante pour obtenir la liste des applications et services qui prennent en charge ce paramètre et les modifications apportées aux métadonnées d’étiquetage.

## <a name="prerequisites"></a>Prerequisites

Avant d’activer cette fonctionnalité, assurez-vous de comprendre les conditions préalables suivantes.

- Vous devez utiliser un client de test pour cette préversion.

- Pour mettre à jour ces informations, vous devez être un administrateur général.

- Les étiquettes de confidentialité [doivent être activées pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) pour le client. Si cette fonctionnalité n’est pas déjà activée, elle sera automatiquement activée lorsque vous sélectionnerez le paramètre pour activer la co-édition pour les fichiers avec des étiquettes de niveau de confidentialité.

- Tous les outils opérationnels, applications et services de votre client doivent prendre en charge la nouvelle [métadonnée d’étiquetage](#metadata-changes-for-sensitivity-labels):
    
    - **Microsoft 365 Apps for enterprise:**
        - Windows : [Canal actuel (préversion)](https://office.com/insider) avec la build minimale 16.0.13801.20182 ou [Canal bêta](https://office.com/insider) avec la build minimale 16.0.13819.20006
        - macOS : [Canal bêta](https://office.com/insider) avec build minimale 16.47.218.0
        - iOS : pas encore pris en charge
        - Android : pas encore pris en charge
    
    - **Client et scanneur d’étiquetage unifié Azure Information Protection :** 
        - Une préversion publique (version minimale 2.10.45.0) que vous pouvez installer à partir du [Centre de téléchargement Microsoft](https://aka.ms/aip-coauth-pp) et de l’une des versions de Microsoft 365 Apps for enterprise pour Windows répertoriées dans l’élément précédent.
    
    - **Application de synchronisation OneDrive pour Windows ou macOS :**
        - Version minimale 19.002.0121.0008
    
    - **Protection contre la perte de données des points de terminaison (Point de terminaison protection contre la perte de données) :**
        - Windows 10 1809 avec KB4601383
        - Windows 10 1903 et 1909 avec KB 4601380
        - Windows 10 2004 avec KB 4601382
    
    - **Applications et services qui utilisent le Kit de développement logiciel (SDK) Microsoft Information Protection :** 
        - Version minimale 1.7 

Les services Microsoft 365 prennent automatiquement en charge les nouvelles métadonnées d'étiquetage lorsque vous activez cette fonction. Par exemple :

- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Stratégies de protection contre la perte de données qui utilisent des étiquettes de confidentialité en tant que conditions](dlp-sensitivity-label-as-condition.md)
- [Microsoft Cloud App Security configuré pour appliquer des étiquettes de niveau de confidentialité](https://docs.microsoft.com/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

## <a name="limitations"></a>Limites

Avant d’activer le paramètre de client pour la co-édition de fichiers chiffrés avec des étiquettes de niveau de confidentialité, assurez-vous de comprendre les limitations suivantes de cette fonctionnalité.

- En raison des [modifications des métadonnées d'étiquetage](#metadata-changes-for-sensitivity-labels), toutes les applications, services et outils opérationnels de votre client doivent prendre en charge les nouvelles métadonnées d'étiquetage pour une expérience d'étiquetage cohérente et fiable.
    
    Spécifique à Excel : les métadonnées pour une étiquette de confidentialité qui n’applique pas le chiffrement peuvent être supprimées d’un fichier si quelqu’un modifie et enregistre ce fichier à l’aide d’une version d’Excel qui ne prend pas en charge les modifications des métadonnées pour les étiquettes de niveau de sécurité.

- La co-création et l'enregistrement automatique ne sont pas pris en charge et ne fonctionnent pas pour les documents Office étiquetés et chiffrés qui utilisent l'une des [configurations suivantes pour le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings) :
    - **Permettre aux utilisateurs d'attribuer des autorisations lorsqu’ils appliquent l’étiquette** et la case à cocher **Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations** est sélectionnée. Cette configuration est parfois appelée « Autorisations définies par l’utilisateur ».
    - **L’expiration de l'accès des utilisateurs au contenu** est définie sur une valeur autre que **Jamais**.
    - **Chiffrement à double clé** est sélectionnée.
    
    Pour les étiquettes avec l’une de ces configurations de chiffrement, les étiquettes s’affichent dans les applications Office. Toutefois, lorsque les utilisateurs sélectionnent ces étiquettes et que personne d'autre ne modifie le document, ils sont avertis que la co-édition et l'enregistrement automatique ne seront pas disponibles. Si quelqu’un d’autre modifie le document, un message indique à l’utilisateur que les étiquettes ne peuvent pas être appliquées.

## <a name="known-issues-for-this-preview"></a>Problèmes connus dans cette préversion

Cette version préliminaire de la co-édition pour les fichiers chiffrés avec des étiquettes de niveau de confidentialité présente les problèmes connus suivants :

- Les utilisateurs ne peuvent pas appliquer d’étiquettes dans Office sur le web pour les fichiers Word, Excel et PowerPoint dont la taille est supérieur à 300 Mo. Pour ces fichiers, vous pouvez utiliser les applications de bureau Office pour appliquer une étiquette, mais vous devez être la seule personne à ouvrir le fichier.

- Lorsque vous utilisez les [stratégies DLP qui utilisent des étiquettes de confidentialité comme conditions](dlp-sensitivity-label-as-condition.md), les pièces jointes non chiffrées pour les courriers électroniques ne sont pas prise en charge.

- Les applications Office pour iOS et Android ne sont pas pris en charge.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Activer la co-édition pour les fichiers avec les étiquettes de confidentialité

> [!CAUTION]
> L'activation de ce paramètre est une action à sens unique. Si la fonctionnalité est en préversion, testez-la uniquement dans un environnement non-production et après avoir lu et compris les modifications apportées aux métadonnées, conditions préalables, limitations et problèmes connus consignés sur cette page.

Pendant la préversion, vous devez utiliser une URL spécifique pour accéder à ce paramètre dans le Centre de conformité Microsoft 365.

1. Connectez-vous au Centre de conformité Microsoft 365 en tant qu’administrateur général pour votre client de test en utilisant le lien suivant :
    
    ````
    https://compliance.microsoft.com/co-authoring_for_files_with_sensitivity_labels
    ````
    Ce lien vous dirige directement vers le paramètre de client, à savoir **Co-édition de fichiers avec des étiquettes de niveau de confidentialité**.

    > [!IMPORTANT]
    > Avant de continuer, vérifiez que vous êtes inscrit à un client de test qui n’affecte pas vos utilisateurs : 
    >
    > Sélectionnez le cercle avec vos initiales de compte dans la partie supérieure droite du Centre de conformité, et confirmez que le nom du client affiche bien le client test prévu.
    
2. Lisez la description de synthèse, les conditions préalables, ce à quoi vous devez vous attendre et l’avertissement selon lequel vous ne pouvez pas désactiver ce paramètre après l'avoir activé. Sélectionnez ensuite **Activer la co-édition de fichiers avec des étiquettes de niveau de confidentialité**, puis **Appliquer** :
    
    ![Option pour activer la co-édition pour les fichiers avec des étiquettes de niveau de confidentialité](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Attendez 24 heures que ce paramètre soit répliqué dans l’ensemble de votre environnement avant de tester cette nouvelle fonctionnalité pour la co-édition.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Si vous avez besoin de désactiver cette fonctionnalité, contactez le support technique

> [!IMPORTANT]
> Si vous devez désactiver cette fonction, sachez que les informations d'étiquetage peuvent être perdues.

Une fois que vous avez activé la co-édition de fichiers avec des étiquettes de confidentialité pour votre client, vous ne pouvez pas désactiver ce paramètre vous-même. C'est pourquoi il est si important de vérifier et de comprendre les conditions préalables, les conséquences et les limites avant d'activer ce paramètre. C'est également la raison pour laquelle nous vous recommandons de tester cette fonctionnalité avec un client test plutôt qu'avec un client de production.

![Option indiquant que la co-édition est activée pour les étiquettes de confidentialité.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Comme vous le voyez sur la capture d'écran lorsque ce paramètre a été activé, vous pouvez contacter le [Support Microsoft](https://docs.microsoft.com/office365/admin/contact-support-for-business-products) et demander à ce que ce paramètre soit désactivé. Cette demande peut prendre plusieurs jours et vous devrez prouver que vous êtes un administrateur général pour votre client. Attendez-vous à ce que les frais de support habituels s'appliquent. 

Si un ingénieur du support technique désactive ce paramètre pour votre client :

- Pour les applications et services qui prendre en charge les nouvelles métadonnées d’étiquetage, les formats et l’emplacement des métadonnées d’origine sont désormais conservés lorsque les étiquettes sont lues ou enregistrées.

- Le nouveau format de métadonnées et l’emplacement des documents Office utilisés pendant l’utilisation du paramètre ne seront pas copiés dans le format et l’emplacement d’origine. Par conséquent, ces informations d’étiquetage pour les fichiers Word, Excel et PowerPoint non chiffrés seront perdues.

- La co-édition et l’enregistrement automatique ne fonctionnent plus dans votre client.

- Les étiquettes de niveau de confidentialité restent activées pour les fichiers Office dans OneDrive et SharePoint.
