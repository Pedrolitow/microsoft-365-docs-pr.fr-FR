---
title: Configurer Azure Rights Management pour la version précédente de Message Encryption
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: La version précédente de Office 365 Message Encryption dépend de Microsoft Azure Rights Management (anciennement Windows Azure Active Directory Rights Management).
ms.openlocfilehash: 386056c282ea5f4ad996cc7ae7c50926436fe720
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641359"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Configurer Azure Rights Management pour la version précédente de Message Encryption

Cette rubrique décrit les étapes à suivre pour activer et configurer Azure Rights Management (RMS), qui fait partie d’Azure Information Protection, à utiliser avec la version précédente de Office 365 Message Encryption (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Cet article s’applique uniquement à la version précédente d’OME

Si vous n’avez pas encore déplacé votre organisation vers Chiffrement de messages Microsoft Purview, mais que vous avez déjà déployé OME, les informations contenues dans cet article s’appliquent à votre organisation. Microsoft vous recommande d’effectuer un plan pour passer à Chiffrement de messages Microsoft Purview dès qu’il est raisonnable pour votre organisation. Pour obtenir des instructions, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Si vous souhaitez en savoir plus sur le fonctionnement des nouvelles fonctionnalités en premier, consultez [Chiffrement](ome.md) des messages. Le reste de cet article fait référence au comportement OME avant la publication de Chiffrement de messages Microsoft Purview.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Conditions préalables à l’utilisation de la version précédente de Office 365 Message Encryption
<a name="warmprereqs"> </a>

Office 365 chiffrement des messages (OME), y compris IRM, dépend de Azure Rights Management (Azure RMS). Azure RMS est la technologie de protection utilisée par Azure Information Protection. Pour utiliser OME, votre organisation doit inclure un abonnement Exchange Online ou Exchange Online Protection qui, à son tour, inclut un abonnement Azure Rights Management.

- Si vous n’êtes pas sûr de ce que votre abonnement inclut, consultez les descriptions de service Exchange Online pour la stratégie [de message, la récupération et la conformité](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Si vous avez Azure Rights Management mais qu’il n’est pas configuré pour Exchange Online ou Exchange Online Protection, cet article explique comment activer Azure Rights Management, puis décrit la meilleure façon de configurer OME pour qu’il fonctionne avec Azure Rights Management.

- Si vous avez déjà configuré OME pour qu’il fonctionne avec Azure Rights Management pour Exchange Online ou Exchange Online Protection, selon la façon dont vous l’avez configuré, vous pouvez être prêt à commencer à utiliser OME et ses nouvelles fonctionnalités immédiatement. Cet article explique comment déterminer si vous avez correctement configuré OME, ce qu’il faut faire si vous devez modifier votre configuration et ce qui se passe si vous choisissez de ne pas modifier votre configuration. Par exemple, pour utiliser les nouvelles fonctionnalités, vous devez utiliser Azure RMS avec OME. Vous ne pouvez pas utiliser les nouvelles fonctionnalités avec une Active Directory local RMS.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Activer Azure Rights Management pour la version précédente d’OME dans Office 365

Vous devez activer Azure Rights Management afin que les utilisateurs de votre organisation puissent appliquer une protection des informations aux messages qu’ils envoient, et ouvrir les messages et fichiers qui ont été protégés par le service Azure Rights Management. Pour obtenir des instructions, consultez [Activation de Azure Rights Management](/azure/information-protection/activate-service). Une fois l’activation terminée, revenez ici et poursuivez les tâches décrites dans cet article.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Configurer la version précédente d’OME pour utiliser Azure RMS en important des domaines de publication approuvés (TPD)

Un TPD est un fichier XML qui contient des informations sur les paramètres de gestion des droits de votre organisation. Par exemple, le TPD contient des informations sur le certificat de licence de serveur (SLC) utilisé pour la signature et le chiffrement des certificats et des licences, les URL utilisées pour les licences et la publication, et ainsi de suite. Vous importez le TPD dans votre organisation à l’aide de PowerShell.

> [!IMPORTANT]
> Auparavant, vous pouviez choisir d’importer des TDT à partir du service Active Directory Rights Management (AD RMS) dans votre organisation. Toutefois, cela vous empêchera d’utiliser Chiffrement de messages Microsoft Purview et n’est pas recommandé. Si votre organisation est actuellement configurée de cette façon, Microsoft vous recommande de créer un plan de migration de votre Active Directory local RMS vers azure Information Protection basé sur le cloud. Pour plus d’informations, consultez [Migration d’AD RMS vers Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Vous ne pourrez pas utiliser Chiffrement de messages Microsoft Purview tant que vous n’aurez pas terminé la migration vers Azure Information Protection.

**Pour importer des TPD à partir d’Azure RMS** :

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Choisissez l’URL de partage de clés qui correspond à l’emplacement géographique de votre organisation :

   |Emplacement|URL de l’emplacement de partage de clés|
   |---|---|
   |Amérique du Nord|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Union européenne|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Asie|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Amérique du Sud|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Office 365 Secteur Public (nuage communautaire propre aux gouvernements)  <br/> Cet emplacement de partage de clés RMS est réservé aux clients qui ont acheté Office 365 pour les références SKU gouvernementales.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. Configurez l’emplacement de partage de clés en exécutant la cmdlet [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit :

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   Par exemple, pour configurer l’emplacement de partage de clés si votre organisation se trouve dans Amérique du Nord :

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Exécutez l’applet de commande [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) avec le commutateur -RMSOnline pour importer le TPD à partir de Azure Rights Management :

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Où  *TPDName*  est le nom que vous souhaitez utiliser pour le TPD. Par exemple, « Contoso North American TPD ».

5. Pour vérifier que vous avez correctement configuré votre organisation pour utiliser le service Azure Rights Management, exécutez l’applet de commande [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) avec le commutateur -RMSOnline comme suit :

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Entre autres choses, cette applet de commande vérifie la connectivité avec le service Azure Rights Management, télécharge le TPD et vérifie sa validité.

6. Exécutez l’applet de commande [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit pour désactiver la disponibilité des modèles Azure Rights Management dans Outlook sur le web et Outlook :

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Exécutez l’applet de commande [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) comme suit pour activer Azure Rights Management pour votre organisation de messagerie basée sur le cloud et la configurer pour qu’elle utilise Azure Rights Management pour Office 365 chiffrement des messages :

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. Pour vérifier que vous avez correctement importé le TPD et activé Azure Rights Management, utilisez l’applet de commande Test-IRMConfiguration pour tester Azure Rights Management fonctionnalités. Pour plus d'informations, consultez « Exemple 1 » dans la rubrique [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>J’ai la version précédente d’OME configurée avec Active Directory Rights Management et non Azure Information Protection, que dois-je faire ?
<a name="importTPDs"> </a>

Vous pouvez continuer à utiliser vos règles de flux de messagerie Office 365 Message Encryption existantes avec Active Directory Rights Management, mais vous ne pouvez pas configurer ou utiliser Chiffrement de messages Microsoft Purview. Au lieu de cela, vous devez migrer vers Azure Information Protection. Pour plus d’informations sur la migration et ce que cela signifie pour votre organisation, consultez [Migration d’AD RMS vers Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>Étapes suivantes
<a name="importTPDs"> </a>

Une fois que vous avez terminé Azure Rights Management configuration, si vous souhaitez activer Chiffrement de messages Microsoft Purview, voir [Configurer Chiffrement de messages Microsoft Purview](./set-up-new-message-encryption-capabilities.md).

Une fois que vous avez configuré votre organisation pour utiliser Chiffrement de messages Microsoft Purview, vous êtes prêt à [définir des règles de flux de messagerie](define-mail-flow-rules-to-encrypt-email.md).

## <a name="related-topics"></a>Voir aussi
<a name="importTPDs"> </a>

[Chiffrement dans Office 365](encryption.md)

[Détails techniques de référence sur le chiffrement dans Office 365](technical-reference-details-about-encryption.md)

[Qu’est-ce que Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)
