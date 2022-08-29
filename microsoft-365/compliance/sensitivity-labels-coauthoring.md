---
title: Activer la co-édition pour les documents chiffrés
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
description: Activez un paramètre qui permet la co-édition et l’enregistrement automatique dans les applications de bureau pour les documents étiquetés et chiffrés dans SharePoint et OneDrive.
ms.openlocfilehash: bc405ee52ba469b342c143ba720e0dc027a0addd
ms.sourcegitcommit: 7374c7b013890744d74e5214f7f8d69ca7874466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67408372"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Activer la co-édition pour les fichiers chiffrés avec les étiquettes de confidentialité

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Activez le paramètre pour prendre en charge la [co-édition](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) pour les applications de bureau Office de telle sorte que lorsque les documents sont étiquetés et chiffrés par les [Étiquettes de confidentialité](sensitivity-labels.md), plusieurs utilisateurs peuvent modifier ces documents en même temps.

Si ce paramètre n’est pas activé pour votre client, les utilisateurs doivent consulter un document chiffré stocké dans SharePoint ou OneDrive lorsqu’ils utilisent les applications de bureau Office. Par conséquent, ils ne peuvent pas collaborer en temps réel. Ils doivent également utiliser Office sur le web lorsque les [étiquettes de confidentialité sont activées pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

En outre, l'activation de cette fonctionnalité entraîne la prise en charge de la fonctionnalité [Enregistrement automatique](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) pour ces fichiers étiquetés et chiffrés.

Pour lire l’annonce de la publication, consultez le billet de blog [la co-édition sur des documents chiffrés par Microsoft Information Protection et des mises à jour d'étiquetage est généralement disponible](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Modifications des métadonnées pour les étiquettes de niveau de confidentialité

> [!IMPORTANT]
> Après avoir activé le paramètre de co-édition, les informations d’étiquette des fichiers non chiffrés ne sont plus enregistrées dans les propriétés personnalisées.
> 
> N'activez pas ce paramètre si vous utilisez des applications, services, scripts ou outils qui lisent ou écrivent des métadonnées d'étiquetage à l'ancien emplacement.

Avant d'activer le paramètre de prise en charge de la co-édition pour les applications de bureau Office, il est important de comprendre que cette action apporte des modifications aux métadonnées d'étiquetage qui sont enregistrées et lues dans les fichiers Office.

Les métadonnées d’étiquetage incluent des informations qui identifient votre client et l’étiquette de confidentialité qui vous a été appliquée. Ce paramètre modifie le format des métadonnées et l'emplacement des fichiers Word, Excel et PowerPoint. Vous n’avez pas besoin d’effectuer d’action pour les fichiers chiffrés ou les e-mails, car la modification des métadonnées pour les fichiers chiffrés est à compatibilité descendante et il n’y a aucune modification pour les e-mails. Toutefois, vous devez connaître les modifications de métadonnées pour les fichiers chiffrés qui peuvent être automatiquement mis à niveau, mais qui ne sont pas rétrocompatibles.

Cette modification affecte à la fois les dossiers nouvellement étiquetés et les dossiers déjà étiquetés. Lorsque vous utilisez des applications et des services qui prennent en charge le paramètre de co-édition :
- Pour les fichiers nouvellement étiquetés, seuls le nouveau format et le nouvel emplacement sont utilisés pour les métadonnées d'étiquetage.
- Pour les fichiers déjà étiquetés, la prochaine fois que le fichier est ouvert et enregistré, si le fichier a des métadonnées dans l’ancien format et l’ancien emplacement, ces informations sont copiées dans le nouveau format et le nouvel emplacement.

Pour en savoir plus sur le changement de métadonnées à partir des ressources suivantes :

- Billet de blog : [Modifications à venir concernant le stockage des métadonnées de protection des informations Microsoft](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Ouvrir spécifications : [2.6.3 LabelInfo et propriétés de document personnalisées](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

En raison de ces modifications, n'activez pas ce paramètre si vous avez des applications, services, scripts ou outils dans votre organisation qui lisent ou écrivent des métadonnées d'étiquetage à l'ancien emplacement. Dans ce cas, voici quelques exemples de conséquences :

- Un document étiqueté apparaît comme sans étiquette pour les utilisateur.

- Un document affiche une étiquette expirée aux utilisateurs.

- La co-création et l’enregistrement automatique ne fonctionnent pas pour un document étiqueté et chiffré si un autre utilisateur l’ouvre dans une application de bureau Office qui ne prend pas en charge les nouvelles métadonnées d’étiquetage. N’ignorez pas que ce scénario peut également se produire pour les utilisateurs externes à votre organisation si les utilisateurs externes et les hôtes avec invitation ont le fichier ouvert.

- Une règle de flux de messagerie Exchange Online qui [identifie les étiquettes en tant que propriétés personnalisées dans les pièces jointes Office](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) ne parvient pas à chiffrer l’e-mail et la pièce jointe, ou les chiffre de manière incorrecte.

Consultez la section suivante pour obtenir la liste des applications et services qui prennent en charge ce paramètre et les modifications apportées aux métadonnées d’étiquetage.

## <a name="prerequisites"></a>Prerequisites

Avant d’activer cette fonctionnalité, assurez-vous de comprendre les conditions préalables suivantes.

- Pour mettre à jour ces informations, vous devez être un administrateur général.

- Les étiquettes de confidentialité [doivent être activées pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) pour le client. Si cette fonctionnalité n’est pas déjà activée, elle sera automatiquement activée lorsque vous sélectionnerez le paramètre pour activer la co-édition pour les fichiers avec des étiquettes de niveau de confidentialité.

- Microsoft 365 Apps for enterprise :
    - **Windows** : Version minimale 2107 du canal actuel ou du canal Enterprise mensuel, ou version minimale 2202 à partir du canal Entreprise semi-annuel (préversion)
    - **macOS** : version minimale 16.51
    - **iOS** : version minimale 2.58
    - **Android** : version minimale 16.0.14931

- Tous les outils opérationnels, applications et services de votre client doivent prendre en charge la nouvelle [métadonnée d’étiquetage](#metadata-changes-for-sensitivity-labels). Si vous utilisez l’une des versions suivantes, vérifiez les versions minimales requises :
    
    - **Client et scanneur d’étiquetage unifié Azure Information Protection :**
        - Version minimale[ 2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620)que vous pouvez installer à partir du [Centre de téléchargement Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
        - Pour les applications Office, il faut disposer des versions minimales indiquées pour Microsoft 365 Apps pour entreprise.
    
    - **Application de synchronisation OneDrive pour Windows ou macOS :**
        - Version minimale 19.002.0121.0008
    
    - **Protection contre la perte de données des points de terminaison (Point de terminaison protection contre la perte de données) :**
        - Windows 10 1809 avec KB4601383
        - Windows 10 1903 et 1909 avec KB 4601380
        - Windows 10 2004 avec KB 4601382
        - Les versions de Windows postérieures à Windows 10 2004 sont prises en charge sans mises à jour de la Base de connaissances
    
    - **Applications et services qui utilisent le Kit de développement logiciel (SDK) Microsoft Information Protection :** 
        - Version minimale 1.7 

Les services Microsoft 365 prennent automatiquement en charge les nouvelles métadonnées d'étiquetage lorsque vous activez cette fonction. Par exemple :

- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Stratégies de protection contre la perte de données qui utilisent des étiquettes de confidentialité en tant que conditions](dlp-sensitivity-label-as-condition.md)
- [Microsoft Defender for Cloud Apps configuré pour appliquer des étiquettes de confidentialité](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

## <a name="limitations"></a>Limites

Avant d’activer le paramètre de client pour la co-édition de fichiers chiffrés avec des étiquettes de niveau de confidentialité, assurez-vous de comprendre les limitations suivantes de cette fonctionnalité.

- En raison des [modifications des métadonnées d'étiquetage](#metadata-changes-for-sensitivity-labels), toutes les applications, services et outils opérationnels de votre client doivent prendre en charge les nouvelles métadonnées d'étiquetage pour une expérience d'étiquetage cohérente et fiable.
    
    Spécifique à Excel : les métadonnées pour une étiquette de confidentialité qui n’applique pas le chiffrement peuvent être supprimées d’un fichier si quelqu’un modifie et enregistre ce fichier à l’aide d’une version d’Excel qui ne prend pas en charge les modifications des métadonnées pour les étiquettes de niveau de sécurité.

- La co-création et l'enregistrement automatique ne sont pas pris en charge et ne fonctionnent pas pour les documents Office étiquetés et chiffrés qui utilisent l'une des [configurations suivantes pour le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings) :
    - **Autoriser les utilisateurs à attribuer des autorisations lorsqu'ils appliquent l'étiquette** et la case à cocher **Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier les autorisations** est sélectionnée. Cette configuration est parfois appelée « autorisations définies par l'utilisateur ».
    - **L’expiration de l'accès des utilisateurs au contenu** est définie sur une valeur autre que **Jamais**.
    - **Chiffrement à double clé** est sélectionnée.
    
    Pour les étiquettes avec l’une de ces configurations de chiffrement, les étiquettes s’affichent dans les applications Office. Toutefois, lorsque les utilisateurs sélectionnent ces étiquettes et que personne d’autre ne modifie le document, ils sont avertis que la co-création et l’enregistrement automatique ne seront pas disponibles. Si quelqu’un d’autre modifie le document, un message indique à l’utilisateur que les étiquettes ne peuvent pas être appliquées.

- Si vous utilisez le client d’étiquette unifiée Azure Information Protection : consultez la documentation de ce client d' [pour plus d’informations requises ou de limitations](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Ces limitations pour le client d’étiquetage unifié incluent un [changement de boîte de dialogue](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) pour les utilisateurs qui sélectionnent des étiquettes qui les invitent à sélectionner des autorisations.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Comment activer la co-édition pour les fichiers avec les étiquettes de confidentialité

> [!CAUTION]
> L'activation de ce paramètre est une action à sens unique. Lorsque la fonctionnalité est en préversion, activez-la uniquement après avoir lu et compris les modifications apportées aux métadonnées, conditions préalables, limitations et problèmes connus consignés sur cette page.

1. Connectez-vous au [Portail de conformité Microsoft Purview](https://compliance.microsoft.com) en tant qu’administrateur général de votre client.

2. Dans le volet de navigation, sélectionnez **Paramètres** > **Co-édition pour les fichiers avec fichiers de confidentialité**.

2. Sur la page **Co-édition pour les fichiers avec étiquettes de confidentialité**, lisez la description de synthèse, les conditions préalables, ce à quoi vous devez vous attendre et l’avertissement selon lequel vous ne pouvez pas désactiver ce paramètre après l'avoir activé.
    
    Sélectionnez ensuite **Activer la co-édition de fichiers avec des étiquettes de niveau de confidentialité**, puis **Appliquer** :
    
    ![Option pour activer la co-édition pour les fichiers avec des étiquettes de niveau de confidentialité.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Attendez 24 heures que ce paramètre soit répliqué dans l’ensemble de votre environnement avant d’utiliser cette nouvelle fonctionnalité pour la co-édition.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Si vous avez besoin de désactiver cette fonctionnalité, contactez le support technique

> [!IMPORTANT]
> Si vous devez désactiver cette fonction, sachez que les informations d'étiquetage peuvent être perdues.

Une fois que vous avez activé la co-édition de fichiers avec des étiquettes de confidentialité pour votre client, vous ne pouvez pas désactiver ce paramètre vous-même. C'est pourquoi il est si important de vérifier et de comprendre les conditions préalables, les conséquences et les limites avant d'activer ce paramètre.

![Option indiquant que la co-édition est activée pour les étiquettes de confidentialité.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Comme vous le voyez sur la capture d'écran lorsque ce paramètre a été activé, vous pouvez contacter le [Support Microsoft](../admin/get-help-support.md) et demander à ce que ce paramètre soit désactivé. Cette demande peut prendre plusieurs jours et vous devrez prouver que vous êtes un administrateur général pour votre locataire. Attendez-vous à ce que les frais de support habituels s'appliquent. 

Si un ingénieur du support technique désactive ce paramètre pour votre client :

- Pour les applications et services qui prendre en charge les nouvelles métadonnées d’étiquetage, les formats et l’emplacement des métadonnées d’origine sont désormais conservés lorsque les étiquettes sont lues ou enregistrées.

- Le nouveau format de métadonnées et l’emplacement des documents Office utilisés pendant l’utilisation du paramètre ne seront pas copiés dans le format et l’emplacement d’origine. Par conséquent, ces informations d’étiquetage pour les fichiers Word, Excel et PowerPoint non chiffrés seront perdues.

- La co-édition et de l'enregistrement automatique ne fonctionnent plus dans votre client pour les documents étiquetés et chiffrés.

- Les étiquettes de niveau de confidentialité restent activées pour les fichiers Office dans OneDrive et SharePoint.
