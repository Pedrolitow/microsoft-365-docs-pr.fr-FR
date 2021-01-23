---
title: Utiliser les étiquettes de confidentialité dans les applications Office
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment les utilisateurs utilisent des étiquettes de niveau de sensibilité dans les applications Office pour ordinateur de bureau, mobile et web, et quelles applications la prise en charge des étiquettes de niveau de sensibilité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d84735cc51b26df6b4c28ffc3bf8fb99f896f1ae
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49925694"
---
# <a name="use-sensitivity-labels-in-office-apps"></a>Utiliser les étiquettes de confidentialité dans les applications Office

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Lorsque vous [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) avez publié des étiquettes de niveau de sensibilité à partir du Centre de conformité Microsoft 365 ou du centre d’étiquetage équivalent, elles commencent à apparaître dans les applications Office pour que les utilisateurs classifient et protègent les données telles qu’elles sont créées ou modifiées.

Utilisez les informations de cet article pour vous aider à gérer correctement les étiquettes de sensibilité dans les applications Office. Par exemple, identifiez les versions minimales des applications dont vous avez besoin pour prendre en charge l’étiquetage intégré et comprenez les interactions avec le client d’étiquetage unifié Azure Information Protection et la compatibilité avec d’autres applications et services.

## <a name="labeling-client-for-desktop-apps"></a>Client d’étiquetage pour les applications de bureau

Pour utiliser des étiquettes de niveau de sensibilité intégrées aux applications de bureau Office pour Windows et Mac, vous devez utiliser une édition d’abonnement d’Office. Ce client d’étiquetage ne prend pas en charge les éditions autonomes d’Office, telles qu’Office 2016 ou Office 2019.

Pour utiliser des étiquettes de sensibilité avec ces éditions autonomes d’Office sur les ordinateurs Windows, installez le client d’étiquetage unifié [Azure Information Protection.](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2)

## <a name="support-for-sensitivity-label-capabilities-in-apps"></a>Prise en charge des fonctionnalités d’étiquette de sensibilité dans les applications

Pour chaque fonctionnalité, les tableaux suivants listent la version Minimale d’Office dont vous avez besoin pour prendre en charge les étiquettes de sensibilité à l’aide de l’étiquetage intégré. Ou, si la fonctionnalité d’étiquette est en prévisualisation publique ou en révision pour une prochaine version. Utilisez la [feuille de route Microsoft 365](https://aka.ms/MIPC/Roadmap) pour plus d’informations sur les prochaines publication.

Les nouvelles versions des applications Office sont disponibles à différents moments pour différents canaux de mise à jour. Pour plus d’informations, notamment sur la configuration de votre canal de mise à jour afin de pouvoir tester une nouvelle fonctionnalité d’étiquetage qui vous intéresse, voir Vue d’ensemble des canaux de mise à jour pour [Microsoft 365 Apps.](https://docs.microsoft.com/DeployOffice/overview-update-channels) Les nouvelles fonctionnalités qui sont en prévisualisation privée ne sont pas incluses dans le tableau, mais vous pourrez peut-être rejoindre ces aperçus en nomant votre organisation pour le programme d’aperçu privé [de Microsoft Information Protection.](https://aka.ms/mip-preview)

> [!NOTE]
> Les noms des canaux de mise à jour pour les applications Office ont récemment été modifiés. Par exemple, le canal mensuel est désormais canal actuel et Office Insider est désormais canal bêta. Pour plus d’informations, voir [Modifications apportées aux canaux de mise à jour de Microsoft 365 Apps.](https://docs.microsoft.com/deployoffice/update-channels-changes)

Office pour iOS et Office pour Android : les étiquettes de niveau de sensibilité sont intégrées dans [l’application Office.](https://www.microsoft.com/en-us/microsoft-365/blog/2020/02/19/new-office-app-android-ios-available/)

Des fonctionnalités supplémentaires sont disponibles lorsque vous installez le client d’étiquetage unifié Azure Information Protection, qui s’exécute uniquement sur les ordinateurs Windows. Pour plus d’informations, voir [Comparer les clients d’étiquetage pour les ordinateurs Windows.](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#compare-the-labeling-clients-for-windows-computers)

### <a name="sensitivity-label-capabilities-in-word-excel-and-powerpoint"></a>Fonctionnalités des étiquettes de sensibilité dans Word, Excel et PowerPoint

Les numéros répertoriés sont la version minimale de l’application Office requise pour chaque fonctionnalité.

|Fonctionnalité                                                                                                        |Windows |Mac |iOS    |Android      |Web                                                         |
|------------------------------------------------------------------------------------------------------------------|----------------|------------|-------|-------------|------------------------------------------------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md)                                                        |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquer le contenu](sensitivity-labels.md#what-sensitivity-labels-can-do)                                              | 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Marquages dynamiques avec variables](#dynamic-markings-with-variables)                                              | 2010+           | 16,42+     | 2,42+ | 16.0.13328+ | En cours d’examen |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+          | 16,21+     | 2.21+ | 16.0.11231+ | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     |2004+ | 16,35+   | En cours d’examen   | En cours d’examen         | En cours d’examen                                                        |
|[Afficher l’utilisation des étiquettes avec l’analyse des étiquettes](label-analytics.md) et envoyer des données aux administrateurs                      | Aperçu : [Canal actuel (prévisualisation)](https://office.com/insider)            | Aperçu : [Canal actuel (prévisualisation)](https://office.com/insider)        | En cours d’examen   | En cours d’examen         | Oui <sup>\*</sup>                                                        |
|[Exiger que les utilisateurs appliquent une étiquette à leurs e-mails et documents](sensitivity-labels.md#what-label-policies-can-do)   | Aperçu : déploiement sur [le canal actuel (prévisualisation)](https://office.com/insider)             | Aperçu : déploiement sur [le canal actuel (prévisualisation)](https://office.com/insider)         | En cours d’examen   | Aperçu : [canal bêta](https://office.com/insider)         | En cours d’examen                                            
|[Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)                    | 2009+                                  | Déploiement : 16,44+ | En cours d’examen | En cours d’examen | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|Prise [en charge de l’auto-ave](https://support.office.com/article/6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) et de la [co-auteur sur](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) les documents étiquetés et chiffrés | En cours d’examen | En cours d’examen | En cours d’examen | En cours d’examen | [Oui - opt-in](sensitivity-labels-sharepoint-onedrive-files.md) |
|

**Note de bas de page :**

<sup>\*</sup> Actuellement, n’inclut pas de texte de justification pour supprimer une étiquette ou réduire le niveau de classification

### <a name="sensitivity-label-capabilities-in-outlook"></a>Fonctionnalités des étiquettes de sensibilité dans Outlook

Les numéros répertoriés sont la version minimale de l’application Office requise pour chaque fonctionnalité.

|Fonctionnalité                                                                                                        |Outlook pour Windows |Outlook pour Mac |Outlook sur iOS |Outlook sur Android |Outlook sur le web |
|------------------------------------------------------------------------------------------------------------------|---------------------------|------------------------|---------------|-------------------|-------------------|
|[Appliquer, modifier ou supprimer manuellement une étiquette](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)| 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Appliquer une étiquette par défaut](sensitivity-labels.md#what-label-policies-can-do)                                         | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Exiger une justification pour modifier une étiquette](sensitivity-labels.md#what-label-policies-can-do)                     | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Fournir un lien d’aide vers une page d’aide personnalisée](sensitivity-labels.md#what-label-policies-can-do)                       | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquer le contenu](sensitivity-labels.md#what-label-policies-can-do)                                              | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Marquages dynamiques avec variables](#dynamic-markings-with-variables)                                              | En cours d’examen                     | En cours d’examen                 | En cours d’examen         | En cours d’examen           | En cours d’examen               |
|[Attribuer des autorisations maintenant](encryption-sensitivity-labels.md#assign-permissions-now)                                 | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Permettre aux utilisateurs d’attribuer des autorisations](encryption-sensitivity-labels.md#let-users-assign-permissions)                     | 1910+                     | 16,21+                 | 4.7.1+         | 4.0.39+           | Oui               |
|[Exiger que les utilisateurs appliquent une étiquette à leurs e-mails et documents](#require-users-to-apply-a-label-to-their-email-and-documents)   | Aperçu : [Canal actuel (prévisualisation)](https://office.com/insider)                        | 16,43+                     | En cours d’examen            | En cours d’examen                | Oui                |
|[Afficher l’utilisation des étiquettes avec l’analyse des étiquettes](label-analytics.md) et envoyer des données aux administrateurs                      | Aperçu : [Canal actuel (prévisualisation)](https://office.com/insider)                       | Aperçu : [Canal actuel (prévisualisation)](https://office.com/insider)                    | En cours d’examen           | En cours d’examen               | Oui               |
|[Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)                    | 2009+                      | 16,44+                    | En cours d’examen           | En cours d’examen               | Oui |
|


## <a name="office-built-in-labeling-client-and-other-labeling-solutions"></a>Client d’étiquetage intégré Office et autres solutions d’étiquetage

Le client d’étiquetage intégré Office télécharge les étiquettes de confidentialité et les paramètres de stratégie d’étiquette de confidentialité à partir des centres d’administration suivants :

- Centre de conformité Microsoft 365
- Centre de sécurité Microsoft 365
- Centre de sécurité et conformité Office 365

Pour utiliser le client d’étiquetage intégré Office, [](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) vous devez avoir publié une ou plusieurs stratégies d’étiquette pour les utilisateurs à partir de l’un des centres d’administration répertoriés et d’une version prise en charge [d’Office.](#support-for-sensitivity-label-capabilities-in-apps)

Si ces deux conditions sont remplies, mais que vous devez désactiver le client d’étiquetage intégré Office, utilisez le paramètre de stratégie de groupe suivant :

1. Accédez **à Configuration utilisateur/Modèles d’administration/Microsoft Office 2016/Paramètres de sécurité.**

2. Définir Utiliser la fonctionnalité De sensibilité dans Office pour appliquer et afficher les **étiquettes de** sensibilité sur **0**. 
 
Déployez ce paramètre à l’aide de la stratégie de groupe ou du service de stratégie [cloud Office.](https://docs.microsoft.com/DeployOffice/overview-office-cloud-policy-service) Le paramètre prend effet lors du redémarrage des applications Office.

### <a name="office-built-in-labeling-client-and-the-azure-information-protection-client"></a>Client d’étiquetage intégré Office et client Azure Information Protection

Si l’un des clients Azure Information Protection est installé[(client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-clientv2) d’étiquetage unifié ou [client](https://docs.microsoft.com/azure/information-protection/rms-client/aip-client)classique), par défaut, le client d’étiquetage intégré est désactivé dans leurs applications Office. 

Pour utiliser l’étiquetage intégré plutôt que le client Azure Information Protection pour les applications Office, utilisez les instructions de la section précédente, mais définissez le paramètre de stratégie de groupe Utiliser la fonctionnalité Confidentialité dans **Office** pour appliquer et afficher les étiquettes de confidentialité sur **1**. 

Vous pouvez également désactiver ou supprimer le add-in Office, **Azure Information Protection**. Cette méthode convient à un seul ordinateur et à des tests ad hoc. Pour obtenir des instructions, voir Afficher, gérer et installer des modules dans [les programmes Office.](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d) 

Lorsque vous désactivez ou supprimez ce add-in Office, le client Azure Information Protection reste installé afin de pouvoir continuer à étiqueter des fichiers en dehors de vos applications Office. Par exemple, à l’aide de l’Explorateur de fichiers ou de PowerShell.

Pour plus d’informations sur les fonctionnalités qui sont pris en charge par les clients Azure Information Protection et le client d’étiquetage intégré Office, voir choisir le client d’étiquetage à utiliser pour les ordinateurs [Windows](https://docs.microsoft.com/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) dans la documentation Azure Information Protection.

## <a name="office-file-types-supported"></a>Types de fichiers Office pris en charge

Les applications Office qui ont des fichiers d’étiquetage intégrés pour Word, Excel et PowerPoint prisent en charge le format Open XML (tel que .docx et .xlsx), mais pas le format Microsoft Office 97-2003 (tel que .doc et .xls). Lorsqu’un type de fichier n’est pas  pris en charge pour l’étiquetage intégré, le bouton Sensibilité n’est pas disponible dans l’application Office.

Le client d’étiquetage unifié Azure Information Protection prend en charge les formats Open XML et Microsoft Office 97-2003. Pour plus d’informations, consultez les types de fichiers pris en charge par le client d’étiquetage unifié [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-file-types) à partir du guide d’administration de ce client.

Pour d’autres solutions d’étiquetage, consultez leur documentation pour les types de fichiers pris en charge.

## <a name="protection-templates-and-sensitivity-labels"></a>Modèles de protection et étiquettes de sensibilité

Les [modèles](https://docs.microsoft.com/azure/information-protection/configure-policy-templates)de protection définis par l’administrateur, tels que ceux que vous définissez pour le chiffrement de messages Office 365, ne sont pas visibles dans les applications Office lorsque vous utilisez l’étiquetage intégré. Cette expérience simplifiée reflète qu’il n’est pas nécessaire de sélectionner un modèle de protection, car les mêmes paramètres sont inclus dans les étiquettes de niveau de sensibilité pour qui le chiffrement est activé.

Si vous devez convertir des modèles de protection existants en étiquettes, utilisez le portail Azure et les instructions suivantes : Pour convertir des [modèles en étiquettes.](https://docs.microsoft.com/azure/information-protection/configure-policy-templates#to-convert-templates-to-labels)

## <a name="information-rights-management-irm-options-and-sensitivity-labels"></a>Options de gestion des droits de l’information (IRM) et étiquettes de sensibilité

Les étiquettes de niveau de sensibilité que vous configurez pour appliquer le chiffrement éliminent la complexité pour les utilisateurs qui souhaitent spécifier leurs propres paramètres de chiffrement. Dans de nombreuses applications Office, ces paramètres de chiffrement individuels peuvent toujours être configurés manuellement par les utilisateurs à l’aide des options de gestion des droits numériques (IRM). Par exemple, pour les applications Windows :

- Pour un document : **restreindre l’accès**  >  **au**  >  **document de protection des**  >  **fichiers**
- pour un e-mail : à partir de **l’onglet Options** > **Chiffrer** 
  
Lorsque les utilisateurs étiquetent initialement un document ou un e-mail, ils peuvent toujours remplacer vos paramètres de configuration d’étiquette par leurs propres paramètres de chiffrement. Par exemple :

- Un utilisateur applique l’étiquette **Confidentiel \ Tous** les employés à un document et cette étiquette est configurée pour appliquer les paramètres de chiffrement pour tous les utilisateurs de l’organisation. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès à un utilisateur extérieur à votre organisation. Le résultat final est un document étiqueté Confidentiel **\** Tous les employés et chiffré, mais les utilisateurs de votre organisation ne peuvent pas l’ouvrir comme prévu.

- Un utilisateur applique l’étiquette **Confidentiel \ Destinataires uniquement** à un e-mail et ce courrier électronique est configuré pour appliquer le paramètre de chiffrement Ne pas **forwarder**. Cet utilisateur configure ensuite manuellement les paramètres IRM afin que le courrier électronique ne soit pas limité. Le résultat final est que le courrier électronique peut être transmis par des destinataires, même s’il a l’étiquette **Confidentiel \ Destinataires uniquement.**

- Un utilisateur applique **l’étiquette Général** à un document et cette étiquette n’est pas configurée pour appliquer le chiffrement. Cet utilisateur configure ensuite manuellement les paramètres IRM pour restreindre l’accès au document. Le résultat final est un document  étiqueté Général, mais qui applique également le chiffrement afin que certains utilisateurs ne peuvent pas l’ouvrir comme prévu.

Si le document ou l’e-mail est déjà étiqueté, un utilisateur peut faire l’une de ces actions si le contenu n’est pas déjà chiffré ou s’il a le droit d’utilisation [Exporter](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) ou Contrôle total. 

Pour une expérience d’étiquette plus cohérente avec des rapports significatifs, fournissez des étiquettes et des instructions appropriées pour que les utilisateurs appliquent uniquement des étiquettes pour protéger les documents. Par exemple :

- Pour les cas d’exception où les utilisateurs doivent attribuer leurs propres autorisations, fournissez des étiquettes qui permettent [aux utilisateurs d’attribuer leurs propres autorisations.](encryption-sensitivity-labels.md#let-users-assign-permissions) 

- Au lieu que les utilisateurs suppriment manuellement le chiffrement après avoir sélectionné une étiquette qui applique le chiffrement, fournissez une alternative de sous-étiquette lorsque les utilisateurs ont besoin d’une étiquette avec la même classification, mais pas de chiffrement. Par exemple :
    - **Confidentiel \ Tous les employés**
    - **Confidentiel \ Tout le monde (pas de chiffrement)**

> [!NOTE]
> Si les utilisateurs suppriment manuellement le chiffrement d’un document étiqueté stocké dans SharePoint ou OneDrive et que vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et [OneDrive,](sensitivity-labels-sharepoint-onedrive-files.md)le chiffrement d’étiquette est automatiquement restauré lors du prochain accès ou téléchargement du document. 


## <a name="apply-sensitivity-labels-to-files-emails-and-attachments"></a>Appliquer des étiquettes de niveau de sensibilité à des fichiers, des e-mails et des pièces jointes

Les utilisateurs ne peuvent appliquer qu’une seule étiquette à la fois pour chaque document ou courrier électronique.

Lorsque vous étiquetez un message électronique qui a des pièces jointes, les pièces jointes n’héritent pas de l’étiquette à une exception près :

- La pièce jointe est un document Office avec une étiquette qui n’applique pas le chiffrement, et l’étiquette que vous appliquez au message électronique applique le chiffrement. Dans ce cas, le document Office envoyé par courrier électronique hérite de l’étiquette de l’e-mail avec ses paramètres de chiffrement.

Sinon : 

- Si les pièces jointes ont une étiquette, elles conservent leur étiquette initialement appliquée.
- Si les pièces jointes sont chiffrées sans étiquette, le chiffrement reste, mais elles ne sont pas étiquetées.
- Si les pièces jointes n’ont pas d’étiquette, elles ne sont pas étiquetées.

## <a name="sensitivity-label-compatibility"></a>Compatibilité des étiquettes de sensibilité

Avec les applications avec RMS : si vous ouvrez un document ou un **e-mail** étiqueté et chiffré dans une [application rms](https://docs.microsoft.com/azure/information-protection/requirements-applications#rms-enlightened-applications) qui ne prend pas en charge les étiquettes de sensibilité, l’application applique toujours le chiffrement et la gestion des droits.

Avec le **client Azure Information Protection**: vous pouvez afficher et modifier les étiquettes de sensibilité que vous appliquez aux documents et aux e-mails avec le client d’étiquetage intégré Office à l’aide du client Azure Information Protection, et inversement.

**Avec d’autres versions d’Office**: tout utilisateur autorisé peut ouvrir des documents étiquetés et des e-mails dans d’autres versions d’Office. Toutefois, vous pouvez uniquement afficher ou modifier l’étiquette dans les versions d’Office pris en charge ou à l’aide du client Azure Information Protection. Les versions d’application Office pris en charge sont répertoriées dans [la section précédente.](#support-for-sensitivity-label-capabilities-in-apps)

## <a name="support-for-sharepoint-and-onedrive-files-protected-by-sensitivity-labels"></a>Prise en charge des fichiers SharePoint et OneDrive protégés par des étiquettes de sensibilité

Pour utiliser le client d’étiquetage intégré Office avec Office sur le web pour les documents dans SharePoint ou OneDrive, assurez-vous que vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et [OneDrive.](sensitivity-labels-sharepoint-onedrive-files.md)

## <a name="support-for-external-users-and-labeled-content"></a>Prise en charge des utilisateurs externes et du contenu étiqueté

Lorsque vous étiquetez un document ou un e-mail, l’étiquette est stockée en tant que métadonnées incluant votre client et un GUID d’étiquette. Lorsqu’un document ou un e-mail étiqueté est ouvert par une application Office qui prend en charge les étiquettes de sensibilité, ces métadonnées sont lues et uniquement si l’utilisateur appartient au même client, l’étiquette s’affiche dans son application. Par exemple, pour l’étiquetage intégré pour Word, PowerPoint et Excel, le nom de l’étiquette s’affiche dans la barre d’état. 

Cela signifie que si vous partagez des documents avec une autre organisation qui utilise des noms d’étiquettes différents, chaque organisation peut appliquer et voir sa propre étiquette appliquée au document. Toutefois, les éléments suivants d’une étiquette appliquée sont visibles pour les utilisateurs extérieurs à votre organisation :

- Marquages de contenu. Lorsqu’une étiquette applique un en-tête, un pied de page ou un filigrane, ceux-ci sont ajoutés directement au contenu et restent visibles jusqu’à ce que quelqu’un les modifie ou les supprime.

- Nom et description du modèle de protection sous-jacent à partir d’une étiquette qui a appliqué le chiffrement. Ces informations s’affichent dans une barre de messages en haut du document, afin de fournir des informations sur les personnes autorisées à ouvrir le document et leurs droits d’utilisation pour ce document.

### <a name="sharing-encrypted-documents-with-external-users"></a>Partage de documents chiffrés avec des utilisateurs externes

En plus de restreindre l’accès aux utilisateurs de votre propre organisation, vous pouvez étendre l’accès à tout autre utilisateur ayant un compte dans Azure Active Directory. Toutes les applications Office et [autres applications rmS](https://docs.microsoft.com/azure/information-protection/requirements-applications#rms-enlightened-applications) peuvent ouvrir des documents chiffrés une fois que l’utilisateur s’est authentifié.

Si les utilisateurs externes n’ont pas de compte dans Azure Active Directory, ils peuvent s’authentifier à l’aide de comptes invités dans votre client. Ces comptes invités peuvent également être utilisés pour accéder aux documents partagés dans SharePoint ou OneDrive lorsque vous avez activé les étiquettes de niveau de sensibilité pour les fichiers Office dans SharePoint et [OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

- Une option consiste à créer ces comptes invités vous-même. Vous pouvez spécifier n’importe quelle adresse de messagerie que ces utilisateurs utilisent déjà. Par exemple, leur adresse Gmail.
    
    L’avantage de cette option est que vous pouvez restreindre l’accès et les droits à des utilisateurs spécifiques en spécifiant leur adresse de messagerie dans les paramètres de chiffrement. L’inconvénient est la surcharge d’administration pour la création de compte et la coordination avec la configuration de l’étiquette.

- Une autre option consiste à utiliser l’intégration de SharePoint et OneDrive avec [Azure AD B2B (prévisualisation)](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) afin que les comptes invités soient créés automatiquement lorsque vos utilisateurs partagent des liens.
    
    L’avantage de cette option est une surcharge administrative minimale, car les comptes sont créés automatiquement et une configuration d’étiquette plus simple. Pour ce scénario, vous devez [](encryption-sensitivity-labels.md#requirements-and-limitations-for-add-any-authenticated-users) sélectionner l’option de chiffrement Ajouter un utilisateur authentifié, car vous ne connaîtrez pas les adresses e-mail à l’avance. L’inconvénient est que ce paramètre ne vous permet pas de restreindre l’accès et les droits d’utilisation à des utilisateurs spécifiques.

Les utilisateurs externes peuvent également utiliser un compte Microsoft pour les documents chiffrés lorsqu’ils utilisent Microsoft 365 Apps (anciennement applications[Office 365)](https://docs.microsoft.com/deployoffice/name-change)sur Windows, et nouvellement pris en charge sur macOS (version 16.42+), Android (version 16.0.13029+) et iOS (version 2.42+). Par exemple, une personne partage un document chiffré avec elle, et les paramètres de chiffrement spécifient leur adresse de messagerie Gmail. Cet utilisateur peut créer son propre compte Microsoft qui utilise son adresse de messagerie Gmail. Ensuite, une fois qu’ils se sont signés avec ce compte, ils peuvent ouvrir le document et le modifier, conformément aux restrictions d’utilisation spécifiées pour cet utilisateur. Pour obtenir un exemple pas à pas de ce scénario, voir Ouverture et modification [du document protégé.](https://docs.microsoft.com/azure/information-protection/secure-collaboration-documents#opening-and-editing-the-protected-document)

> [!NOTE]
> L’adresse de messagerie du compte Microsoft doit correspondre à l’adresse de messagerie spécifiée pour restreindre l’accès aux paramètres de chiffrement.

Lorsqu’un utilisateur avec un compte Microsoft ouvre un document chiffré de cette façon, il crée automatiquement un compte invité pour le client si un compte invité du même nom n’existe pas déjà. Lorsque le compte invité existe, il peut ensuite être utilisé pour ouvrir des documents dans SharePoint et OneDrive à l’aide d’un navigateur (Office sur le web), en plus d’ouvrir des documents chiffrés à partir de l’application de bureau Windows. 

Toutefois, le compte invité automatique n’est pas créé immédiatement dans ce scénario, en raison de la latence de réplication. Si vous spécifiez des adresses de messagerie personnelles dans le cadre de vos paramètres de chiffrement d’étiquette, nous vous recommandons de créer des comptes invités correspondants dans Azure Active Directory. Ensuite, indiquez à ces utilisateurs qu’ils doivent utiliser ce compte pour ouvrir un document chiffré à partir de votre organisation.

> [!TIP]
> Étant donné que vous ne pouvez pas être sûr que les utilisateurs externes utiliseront une application cliente Office prise en charge, le partage de liens à partir de SharePoint et OneDrive après la création de comptes invités (pour des utilisateurs spécifiques) ou lorsque vous utilisez l’intégration de SharePoint et OneDrive avec [Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) (pour tout utilisateur authentifié) est une méthode plus fiable pour prendre en charge la collaboration sécurisée avec des utilisateurs externes.

## <a name="when-office-apps-apply-content-marking-and-encryption"></a>Quand les applications Office appliquent le marquage et le chiffrement de contenu

Les applications Office appliquent le marquage et le chiffrement de contenu avec une étiquette de sensibilité différemment, en fonction de l’application que vous utilisez.

| Application | Marquage du contenu | Chiffrement |
| --- | --- | --- |
| Word, Excel, PowerPoint sur toutes les plateformes | Immédiatement | Immédiatement |
| Outlook pour PC et Mac | Une fois qu’Exchange Online a envoyé l’e-mail | Immédiatement |
| Outlook sur le web, iOS et Android | Une fois qu’Exchange Online a envoyé l’e-mail | Une fois qu’Exchange Online a envoyé l’e-mail |
|

Les solutions qui appliquent des étiquettes de niveau de sensibilité à des fichiers en dehors des applications Office le font en appliquant des métadonnées d’étiquetage au fichier. Dans ce scénario, le marquage de contenu à partir de la configuration de l’étiquette n’est pas inséré dans le fichier, mais le chiffrement est appliqué. 

Lorsque ces fichiers sont ouverts dans une application de bureau Office, les marquages de contenu sont automatiquement appliqués par le client d’étiquetage unifié Azure Information Protection. Les marquages de contenu ne sont pas appliqués automatiquement lorsque vous utilisez l’étiquetage intégré pour les applications de bureau, mobiles ou web.

Les scénarios qui incluent l’application d’une étiquette de sensibilité en dehors des applications Office sont les suivants :

- Scanneur, Explorateur de fichiers et PowerShell à partir du client d’étiquetage unifié Azure Information Protection 

- Stratégies d’étiquetage automatique pour SharePoint et OneDrive

- Données étiquetées et chiffrées exportées à partir de Power BI

- Microsoft Cloud App Security

Dans ces scénarios, à l’aide de leurs applications Office, un utilisateur avec l’étiquetage intégré peut appliquer les marquages de contenu de l’étiquette en supprimant ou en remplaçant temporairement l’étiquette actuelle, puis en réappliqueant l’étiquette d’origine.

### <a name="dynamic-markings-with-variables"></a>Marquages dynamiques avec variables

> [!IMPORTANT]
> Actuellement, toutes les applications sur toutes les plateformes ne peuvent pas prendre en charge les marquages de contenu dynamique que vous pouvez spécifier pour vos en-têtes, pieds de page et filigranes. Pour les applications qui ne la prisent pas en charge, elles appliquent les marquages en tant que texte d’origine spécifié dans la configuration d’étiquette, plutôt que de résoudre les variables.
> 
> Le client d’étiquetage unifié Azure Information Protection prend en charge les marquages dynamiques. Pour l’étiquetage intégré à Office, consultez les tableaux de la section [fonctionnalités](#support-for-sensitivity-label-capabilities-in-apps) de cette page.

Lorsque vous configurez une étiquette de sensibilité pour les marquages de contenu, vous pouvez utiliser les variables suivantes dans la chaîne de texte pour votre en-tête, pied de page ou filigrane :

| Variable | Description | Exemple lors de l’application d’une étiquette |
| -------- | ----------- | ------- |
| `${Item.Label}` | Nom complet de l’étiquette appliquée| **Général**|
| `${Item.Name}` | Nom de fichier ou objet de l’e-mail du contenu étiqueté | **Sales.docx** |
| `${Item.Location}` | Chemin d’accès et nom de fichier du document en cours d’étiquetage, ou l’objet de l’e-mail d’un e-mail étiqueté | **\\\Sales\2020\Q3\Report.docx**|
| `${User.Name}` | Nom complet de l’utilisateur qui applique l’étiquette| **Président Dussy** |
| `${User.PrincipalName}` | Nom d’utilisateur principal (UPN) Azure AD de l’utilisateur qui applique l’étiquette | **rsimone \@ contoso.com** |
| `${Event.DateTime}` | Date et heure d’étiquetage du contenu, dans le fuseau horaire local de l’utilisateur qui applique l’étiquette | **10/8/2020 13:30** |

> [!NOTE]
> La syntaxe de ces variables est sensible à la cas.

#### <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Définition de marquages visuels différents pour Word, Excel, PowerPoint et Outlook

En tant que variable supplémentaire, vous pouvez configurer des marquages visuels par type d’application Office à l’aide d’une instruction de variable « If.App » dans la chaîne de texte et identifier le type d’application à l’aide des valeurs **Word,** **Excel,** **PowerPoint** ou **Outlook.** Vous pouvez également abrévier ces valeurs, ce qui est nécessaire si vous souhaitez spécifier plusieurs valeurs dans la même instruction If.App.

> [!NOTE]
> Pour plus d’informations, des instructions pour Outlook sont incluses, bien qu’elles soient actuellement uniquement prise en charge par le client d’étiquetage unifié Azure Information Protection.

Utilisez la syntaxe suivante :

```
${If.App.<application type>}<your visual markings text> ${If.End}
```

Comme pour les autres marquages visuels dynamiques, la syntaxe est sensible à la cas.

Exemples :

- **Définissez le texte d’en-tête pour les documents Word uniquement :**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Dans les en-têtes de document Word uniquement, l’étiquette applique le texte d’en-tête « Ce document Word est sensible ». Aucun texte d’en-tête n’est appliqué à d’autres applications Office.

- **Définissez du texte de pied de groupe pour Word, Excel et Outlook, et un texte de pied de pied de groupe différent pour PowerPoint :**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    Dans Word, Excel et Outlook, l’étiquette applique le texte de pied de ligne « Ce contenu est confidentiel ». Dans PowerPoint, l’étiquette applique le texte de pied de groupe « Cette présentation est confidentielle ».

- **Définissez du texte en filigrane spécifique pour Word et PowerPoint, puis du texte filigrane pour Word, Excel et PowerPoint :**

    `${If.App.WP}This content is ${If.End}Confidential`

    Dans Word et PowerPoint, l’étiquette applique le texte filigrane « This content is Confidential ». Dans Excel, l’étiquette applique le texte filigrane « Confidentiel ». Dans Outlook, l’étiquette n’applique aucun texte filigrane, car les filigranes en tant que marquages visuels ne sont pas pris en charge pour Outlook.

## <a name="require-users-to-apply-a-label-to-their-email-and-documents"></a>Exiger que les utilisateurs appliquent une étiquette à leurs e-mails et documents

> [!IMPORTANT]
> Également appelé étiquetage obligatoire, toutes les applications sur toutes les plateformes ne permettent pas actuellement de prendre en charge le paramètre de stratégie Exiger que les utilisateurs appliquent une étiquette à leurs e-mails **et documents.**
> 
> Le client d’étiquetage unifié [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/rms-client/install-unifiedlabelingclient-app) prend en charge l’étiquetage obligatoire et pour l’étiquetage intégré aux applications Office. Consultez les tableaux dans la section fonctionnalités de cette page. [](#support-for-sensitivity-label-capabilities-in-apps)

Lorsque ce paramètre de stratégie est sélectionné, les utilisateurs affectés à la stratégie doivent sélectionner et appliquer une étiquette de confidentialité dans les scénarios suivants :

- Pour le client d’étiquetage unifié Azure Information Protection :
    - Pour les documents (Word, Excel, PowerPoint) : lorsqu’un document sans la même identité est enregistré ou qu’un utilisateur ferme le document.
    - Pour les e-mails (Outlook) : à l’heure où les utilisateurs envoient un message sans bel.

- Pour l’étiquetage intégré aux applications Office :
    - Pour les documents ((Word, Excel, PowerPoint) : lorsqu’un document non créé est ouvert ou enregistré.
    - Pour les e-mails (Outlook) : à l’heure où les utilisateurs envoient un message électronique sans bel.

Informations supplémentaires pour l’étiquetage intégré :

- Lorsque les utilisateurs sont invités à ajouter une étiquette de niveau de sensibilité parce qu’ils ouvrent un document non étiqueté, ils peuvent ajouter une étiquette ou choisir d’ouvrir le document en mode lecture seule.

- Lorsque l’étiquetage obligatoire est en vigueur, les utilisateurs ne peuvent pas supprimer les étiquettes de niveau de sensibilité des documents, mais peuvent modifier une étiquette existante.

## <a name="end-user-documentation"></a>Documentation de l’utilisateur final

- [Appliquer des étiquettes de niveau de confidentialité à vos documents et vos e-mails dans Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)

- [Problèmes connus lorsque vous appliquez des étiquettes de niveau de confidentialité à vos fichiers Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)
