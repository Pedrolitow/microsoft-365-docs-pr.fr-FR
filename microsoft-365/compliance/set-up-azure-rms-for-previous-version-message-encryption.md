---
title: Configurer Azure Rights Management pour la version précédente du chiffrement de messages
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: La version précédente de chiffrement de messages Office 365 dépend de Microsoft Azure Rights Management (anciennement Windows Azure Active Directory Rights Management).
ms.openlocfilehash: 978a8027c79de574b80aeedabcbbd51fa6f9e2a0
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59205900"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Configurer Azure Rights Management pour la version précédente du chiffrement de messages

Cette rubrique décrit les étapes à suivre pour activer puis configurer Azure Rights Management (RMS), qui fait partie d’Azure Information Protection, à utiliser avec la version précédente de chiffrement de messages Office 365 (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Cet article s’applique uniquement à la version précédente d’OME

Si vous n’avez pas encore déplacé votre organisation vers les nouvelles fonctionnalités OME, mais que vous avez déjà déployé OME, les informations de cet article s’appliquent à votre organisation. Microsoft vous recommande d’effectuer un plan pour passer aux nouvelles fonctionnalités OME dès qu’il est raisonnable pour votre organisation. Pour obtenir des instructions, voir [Configurer de chiffrement de messages Office 365 nouvelles fonctionnalités.](set-up-new-message-encryption-capabilities.md) Si vous souhaitez en savoir plus sur le fonctionnement des nouvelles fonctionnalités en premier, voir [chiffrement de messages Office 365](ome.md). Le reste de cet article fait référence au comportement OME avant la publication des nouvelles fonctionnalités OME.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Conditions préalables à l’utilisation de la version précédente chiffrement de messages Office 365
<a name="warmprereqs"> </a>

chiffrement de messages Office 365 (OME), y compris IRM, dépend de Azure Rights Management (Azure RMS). Azure RMS est la technologie de protection utilisée par Azure Information Protection. Pour utiliser OME, votre organisation doit inclure un abonnement Exchange Online ou Exchange Online Protection qui, à son tour, inclut un abonnement Azure Rights Management abonnement.
  
- Si vous ne savez pas ce que comprend votre abonnement, consultez les descriptions du service Exchange Online pour la stratégie de message, la récupération [et la conformité.](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)

- Si vous avez Azure Rights Management mais qu’il n’est pas installé pour Exchange Online ou Exchange Online Protection, cet article explique comment activer Azure Rights Management, puis décrit la meilleure façon de configurer OME pour qu’il fonctionne avec Azure Rights Management.

- Si vous avez déjà installé OME pour qu’il fonctionne avec Azure Rights Management pour Exchange Online ou Exchange Online Protection, en fonction de la façon dont vous l’avez installé, vous pouvez commencer à utiliser OME et ses nouvelles fonctionnalités immédiatement. Cet article explique comment déterminer si vous avez configuré OME correctement, ce qu’il faut faire si vous devez modifier votre configuration et ce qui se produit si vous choisissez de ne pas modifier votre configuration. Par exemple, pour utiliser les nouvelles fonctionnalités, vous devez utiliser Azure RMS avec OME. Vous ne pouvez pas utiliser les nouvelles fonctionnalités avec un service RMS Active Directory local.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Activer Azure Rights Management pour la version précédente d’OME dans Office 365

Vous devez activer les Azure Rights Management afin que les utilisateurs de votre organisation peuvent appliquer la protection des informations aux messages qu’ils envoient, et ouvrir les messages et les fichiers qui ont été protégés par le service Azure Rights Management. Pour obtenir des instructions, voir [Activating Azure Rights Management](/azure/information-protection/activate-service). Une fois que vous avez terminé l’activation, revenir ici et poursuivre les tâches de cet article.
  
## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Configurer la version précédente d’OME pour utiliser Azure RMS en important des domaines de publication approuvé (TPD)

Un TPD est un fichier XML qui contient des informations sur les paramètres de gestion des droits de votre organisation. Par exemple, le TPD contient des informations sur le certificat de licence serveur (SLC) utilisé pour signer et chiffrer les certificats et les licences, les URL utilisées pour la gestion des licences et la publication, etc. Vous importez le TPD dans votre organisation à l’aide de Windows PowerShell.
  
> [!IMPORTANT]
> Auparavant, vous pouviez choisir d’importer des TPD à partir du service AD RMS (Active Directory Rights Management Service) dans votre organisation. Toutefois, cela vous empêchera d’utiliser les nouvelles fonctionnalités OME et n’est pas recommandé. Si votre organisation est actuellement configurée de cette façon, Microsoft vous recommande de créer un plan pour migrer de votre service RMS Active Directory local vers Azure Information Protection en nuage. Pour plus d’informations, voir [Migration d’AD RMS vers Azure Information Protection.](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms) Vous ne pourrez pas utiliser les nouvelles fonctionnalités OME tant que vous n’aurez pas effectué la migration vers Azure Information Protection.
  
 **Pour importer des TPD à partir d’Azure RMS**
  
1. [Connecter à Exchange Online à l’aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Choisissez l’URL de partage de clé qui correspond à l’emplacement géographique de votre organisation :

|**Location**|**URL d’emplacement de partage de clé**|
|:-----|:-----|
|Amérique du Nord  <br/> |https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Union européenne  <br/> |https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Asie  <br/> |https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Amérique du Sud  <br/> |https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
|Office 365 Secteur Public (nuage communautaire propre aux gouvernements)  <br/> Cet emplacement de partage de clés RMS est réservé aux clients qui ont acheté des Office 365 pour les SDK pour le gouvernement.  <br/> |https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc  <br/> |
  
3. Configurez l’emplacement de partage de clés en exécutant la cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit : 

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```
  
   Par exemple, pour configurer l’emplacement de partage de clés si votre organisation est située en Amérique du Nord :

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Exécutez la cmdlet [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) avec le commutateur -RMSOnline pour importer le domaine de Azure Rights Management : 

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Où  *TPDName est*  le nom que vous souhaitez utiliser pour ce domaine. Par exemple, « Contoso North American TPD ». 

5. Pour vérifier que vous avez correctement configuré votre organisation pour utiliser le service Azure Rights Management, exécutez la cmdlet [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) avec le commutateur -RMSOnline comme suit :

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Entre autres choses, cette cmdlet vérifie la connectivité avec le service Azure Rights Management, télécharge le TPD et vérifie sa validité.

6. Exécutez la cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit pour désactiver la Azure Rights Management des modèles d’Outlook sur le web et Outlook : 

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Exécutez la cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit pour activer Azure Rights Management pour votre organisation de messagerie informatique et la configurer pour utiliser Azure Rights Management pour chiffrement de messages Office 365 :

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. Pour vérifier que vous avez correctement importé le TPD et activé Azure Rights Management, utilisez la cmdlet Test-IRMConfiguration pour tester Azure Rights Management fonctionnalité. Pour plus d'informations, consultez « Exemple 1 » dans la rubrique [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>La version précédente d’OME est définie avec Active Directory Rights Management et non Azure Information Protection, que dois-je faire ?
<a name="importTPDs"> </a>

Vous pouvez continuer à utiliser vos règles de flux de messagerie chiffrement de messages Office 365 existantes avec Active Directory Rights Management, mais vous ne pouvez pas configurer ou utiliser les nouvelles fonctionnalités OME. Au lieu de cela, vous devez migrer vers Azure Information Protection. Pour plus d’informations sur la migration et ce que cela signifie pour votre organisation, voir La [migration d’AD RMS vers Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).
  
## <a name="next-steps"></a>Étapes suivantes
<a name="importTPDs"> </a>

Une fois la configuration Azure Rights Management terminée, si vous souhaitez activer les nouvelles fonctionnalités OME, voir Configurer les nouvelles fonctionnalités chiffrement de messages Office 365 intégrées à [Azure Information Protection.](./set-up-new-message-encryption-capabilities.md)
  
Une fois que vous avez défini votre organisation pour qu’elle utilise les nouvelles fonctionnalités OME, vous êtes prêt à définir des règles de flux de messagerie pour protéger les messages électroniques avec de nouvelles [fonctionnalités OME.](define-mail-flow-rules-to-encrypt-email.md)
  
## <a name="related-topics"></a>Voir aussi
<a name="importTPDs"> </a>

[Chiffrement dans Office 365](encryption.md)
  
[Détails techniques de référence sur le chiffrement dans Office 365](technical-reference-details-about-encryption.md)
  
[Qu’est-ce que Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)