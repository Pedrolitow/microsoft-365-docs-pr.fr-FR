---
title: Configuration de la Gestion des droits relatifs à l’information (IRM) pour utiliser un serveur AD RMS local
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3ecde857-4b7c-451d-b4aa-9eeffc8a8c61
ms.collection:
- purview-compliance
- tier3
description: Découvrez comment configurer la gestion des droits relatifs à l’information (IRM) dans Exchange Online pour utiliser un serveur AD RMS (Active Directory Rights Management Service).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 87f776964e6aacb9407350ef905ee7680035dbce
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621403"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>Configuration de la Gestion des droits relatifs à l’information (IRM) pour utiliser un serveur AD RMS local

Pour une utilisation avec des déploiements locaux, gestion des droits relatifs à l’information (IRM) dans Exchange Online utilise Active Directory Rights Management Services (AD RMS), une technologie de protection des informations dans Windows Server 2008 et versions ultérieures. La protection IRM permet d'appliquer un modèle de stratégie de droits AD RMS à un message électronique. Les droits sont attachés au message lui-même afin que la protection se produise en ligne et hors connexion, à l’intérieur et à l’extérieur du pare-feu de votre organisation.

Cette rubrique décrit la configuration de la gestion des droits relatifs à l'information de manière à utiliser un serveur AD RMS. Pour plus d’informations sur l’utilisation de Chiffrement de messages Microsoft Purview avec Azure Active Directory et Azure Rights Management, consultez la FAQ sur le [chiffrement](./ome-faq.yml) des messages.

Pour en savoir plus sur la Gestion des droits relatifs à l'information dans Exchange Online, consultez la rubrique [Gestion des droits relatifs à l'information (IRM) dans Exchange Online](information-rights-management-in-exchange-online.md).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d'exécution estimée de cette tâche : 30 minutes

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Information Rights Management" entry in the [Messaging policy and compliance permissions](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) topic.

- The AD RMS server must be running Windows Server 2008 or later. For details about how to deploy AD RMS, see [Installing an AD RMS Cluster](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- Pour plus d’informations sur l’installation et la configuration de Windows PowerShell et la connexion au service, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cette rubrique, consultez [raccourcis clavier pour le Centre d’administration Exchange dans Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l'aide en participant aux forums Exchange. Visitez les forums sur les pages [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612),[Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542), et [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>Comment procéder ?
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>Étape 1 : utiliser la console AD RMS pour exporter un domaine de publication approuvé (TPD) à partir d'un serveur AD RMS

The first step is to export a trusted publishing domain (TPD) from the on-premises AD RMS server to an XML file. The TPD contains the following settings needed to use RMS features:

- le certificat de licence serveur (SLC) utilisé pour signer et chiffrer les certificats et licences ;

- les URL utilisées pour les licences et les publications ;

- les modèles de stratégie de droits AD RMS créés avec le SLC spécifique au domaine de publication approuvé.

Quand vous importez le domaine de publication approuvé, il est stocké et protégé dans Exchange Online.

1. Ouvrez la console Active Directory Rights Management Services et développez le cluster AD RMS.

2. Dans l'arborescence de la console, développez **Stratégies d'approbation**, puis cliquez sur **Domaines de publication approuvés**.

3. Dans le volet des résultats, sélectionnez le certificat du domaine à exporter.

4. Dans le volet **Actions**, cliquez sur **Exporter le domaine de publication approuvé**.

5. Dans la zone **Fichier de domaine de publication**, cliquez sur **Enregistrer sous** pour enregistrer le fichier dans un emplacement spécifique sur l'ordinateur local. Tapez un nom de fichier, en veillant à spécifier l’extension de `.xml` nom de fichier, puis cliquez sur **Enregistrer**.

6. In the **Password** and **Confirm Password** boxes, type a strong password that will be used to encrypt the trusted publishing domain file. You will have to specify this password when you import the TPD to your cloud-based email organization.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>Étape 2 : utiliser l'Environnement de ligne de commande Exchange Management Shell pour importer le domaine de publication approuvé dans Exchange Online

After the TPD is exported to an XML file, you have to import it to Exchange Online. When a TPD is imported, your organization's AD RMS templates are also imported. When the first TPD is imported, it becomes the default TPD for your cloud-based organization. If you import another TPD, you can use the **Default** switch to make it the default TPD that is available to users.

Pour importer le TPD, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

Vous pouvez obtenir les valeurs des _paramètres ExtranetLicensingUrl_ et _IntranetLicensingUrl_ dans la console Active Directory Rights Management Services. Sélectionnez le cluster AD RMS dans l'arborescence de la console. Les URL des licences s'affichent dans le volet des résultats. Ces URL sont utilisées par les clients de messagerie quand le contenu doit être déchiffré et quand Exchange Online doit déterminer quel domaine de publication approuvé il convient d'utiliser.

When you run this command, you'll be prompted for a password. Enter the password that you specified when you exported the TPD from your AD RMS server.

For example, the following command imports the TPD named Exported TPD using the XML file that you exported from your AD RMS server and saved to the desktop of the Administrator account. The Name parameter is used to specify a name to the TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

Pour plus d'informations sur la syntaxe et les paramètres, consultez la rubrique [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>Comment savez-vous que vous avez importé le TPD ?

To verify that you have successfully imported the TPD, run the **Get-RMSTrustedPublishingDomain** cmdlet to retrieve TPDs in your Exchange Online organization. For details, see the examples in [Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>Étape 3 : utiliser l'Environnement de ligne de commande Exchange Management Shell pour distribuer un modèle de stratégie de droits AD RMS

Après avoir importé le domaine de publication approuvé, vous devez vous assurer qu'un modèle de stratégie de droits AD RMS est distribué. Un modèle distribué est visible pour les utilisateurs Outlook sur le web (anciennement Outlook Web App), qui peuvent ensuite appliquer les modèles à un e-mail.

Pour renvoyer une liste de tous les modèles du domaine de publication approuvé par défaut, exécutez la commande suivante :

```powershell
Get-RMSTemplate -Type All | fl
```

Si la valeur du paramètre _Type_ est `Archived`, le modèle n’est pas visible par les utilisateurs. Seuls les modèles distribués dans le TPD par défaut sont disponibles dans Outlook sur le web.

Pour distribuer un modèle, exécutez la commande suivante :

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

Par exemple, la commande suivante importe le modèle « Propriétaire ».

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez les rubriques [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) et [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>Modèle Ne pas transférer

When you import the default TPD from your on-premises organization into Exchange Online, one AD RMS rights policy template named **Do Not Forward** is imported. By default, this template is distributed when you import the default TPD. You can't use the **Set-RMSTemplate** cmdlet to modify the **Do Not Forward** template.

When the **Do Not Forward** template is applied to a message, only the recipients addressed in the message can read the message. Additionally, recipients can't do the following:

- transférer le message à une autre personne ;
- copier le contenu du message ;
- imprimer le message.

> [!IMPORTANT]
> Le modèle **Ne pas transférer** ne peut pas empêcher qu'un message soit copié avec un programme de capture d'écran tiers, pris en photo, ou simplement copié à la main par les utilisateurs.

You can create additional AD RMS rights policy templates on the AD RMS server in your on-premises organization to meet your IRM protection requirements. If you create additional AD RMS rights policy templates, you have to export the TPD from the on-premises AD RMS server again and refresh the TPD in the cloud-based email organization.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>Comment savez-vous que vous avez correctement distribué le modèle de stratégie de droits AD RMS ?

To verify that you have successfully distributed and AD RMS rights policy template, run the **Get-RMSTemplate** cmdlet to check the template's properties. For details, see the examples in [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>Étape 4: utiliser l'Environnement de ligne de commande Exchange Management Shell pour activer la Gestion des droits relatifs à l'information

Après avoir importé le domaine de publication approuvé et distribué un modèle de stratégie de droits AD RMS, exécutez la commande suivante pour activer la Gestion des droits relatifs à l'information dans votre organisation de messagerie en nuage.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

Pour plus d'informations sur la syntaxe et les paramètres, consultez la rubrique [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>Comment savez-vous que vous avez activé la gestion des droits relatifs à la gestion des droits relatifs à l’information ( IRM) ?

Pour vérifier que l'IRM a bien été activée, exécutez la cmdlet [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) pour vérifier la configuration IRM dans l'organisation Exchange Online.

## <a name="how-do-you-know-this-task-worked"></a>Comment savoir si cette tâche a fonctionné ?
<a name="sectionSection2"> </a>

Pour vérifier que vous avez correctement importé le domaine de publication approuvé et activé la fonctionnalité IRM, procédez comme suit :

- Exécutez la cmdlet **Test-IRMConfiguration** pour tester la fonctionnalité IRM. Pour plus d'informations, consultez « Exemple 1 » dans la rubrique [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- Composez un nouveau message dans Outlook sur le web et protégez-le par IRM en sélectionnant l’option **Définir les autorisations** dans le menu étendu (![Icône Autres options).](../media/ITPro-EAC-MoreOptionsIcon.gif)
