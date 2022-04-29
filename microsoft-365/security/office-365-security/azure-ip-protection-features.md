---
title: Fonctionnalités de protection dans Azure Information Protection déployées sur des locataires existants
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Cet article explique les modifications apportées aux fonctionnalités de protection dans Azure Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dbfc21b879745567c9273c79356ff60e498d95ff
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130821"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Fonctionnalités de protection dans Azure Information Protection déployées sur des locataires existants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pour faciliter l’étape initiale de protection de vos informations, à compter de juillet 2018, tous les locataires azure Information Protection éligibles auront les fonctionnalités de protection dans Azure Information Protection activées par défaut. Les fonctionnalités de protection dans Azure Information Protection étaient auparavant connues dans Office 365 en tant que Rights Management ou Azure RMS. Si votre organisation dispose d’un plan de service Office E3 ou d’un plan de service plus élevé, vous obtiendrez maintenant une prise en main de la protection des informations par le biais d’Azure Information Protection lorsque nous déploierons ces fonctionnalités.

## <a name="changes-beginning-july-1-2018"></a>Modifications à compter du 1er juillet 2018

À compter du 1er juillet 2018, Microsoft activera la fonctionnalité de protection dans Azure Information Protection pour toutes les organisations disposant de l’un des plans d’abonnement suivants :

- Office 365 Message Encryption est proposé dans le cadre de Office 365 E3 et E5, Microsoft E3 et E5, Office 365 A1, A3 et A5, et Office 365 G3 et G5. Vous n’avez pas besoin de licences supplémentaires pour recevoir les nouvelles fonctionnalités de protection optimisées par Azure Information Protection.

- Vous pouvez également ajouter Azure Information Protection Plan 1 aux plans suivants pour recevoir les nouvelles fonctionnalités de chiffrement de messages Office 365 : Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard ou Office 365 Entreprise E1.

- Chaque utilisateur bénéficiant de Office 365 Chiffrement des messages doit être concédé sous licence pour être couvert par la fonctionnalité.

- Pour obtenir la liste complète, consultez les [descriptions du service Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) pour Office 365 Chiffrement des messages.

Les administrateurs clients peuvent vérifier l’état de la protection dans le portail d’administration Office 365.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="Gestion des droits dans Office 365 qui est activée" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>Pourquoi faisons-nous ce changement?

Office 365 Message Encryption tire parti des fonctionnalités de protection d’Azure Information Protection. Au cœur des améliorations apportées récemment à Office 365 Message Encryption et de nos investissements plus larges dans la protection des informations dans Microsoft 365, nous facisons aux organisations d’activer et d’utiliser nos fonctionnalités de protection, car historiquement, les technologies de chiffrement ont été difficiles à mettre en place. En activant les fonctionnalités de protection dans Azure Information Protection par défaut, vous pouvez rapidement commencer à protéger vos données sensibles.

## <a name="does-this-impact-me"></a>Cela me touche-t-il ?

Si votre organisation a acheté une licence Office 365 éligible, votre locataire sera affecté par cette modification.

> [!IMPORTANT]
> Si vous utilisez services AD RMS (Active Directory Rights Management Services) (AD RMS) dans votre environnement local, vous devez refuser cette modification immédiatement ou migrer vers Azure Information Protection avant de déployer cette modification dans les 30 prochains jours. Pour plus d’informations sur la façon de refuser, consultez « J’utilise AD RMS, comment puis-je refuser ? » » plus loin dans cet article. Si vous préférez migrer, consultez [Migration d’AD RMS vers Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Puis-je utiliser Azure Information Protection avec services AD RMS (Active Directory Rights Management Services) (AD RMS) ?

Non. Il ne s’agit pas d’un scénario de déploiement pris en charge. Sans effectuer les étapes de désactivation supplémentaires, certains ordinateurs peuvent commencer automatiquement à utiliser le service Azure Rights Management et se connecter à votre cluster AD RMS. Ce scénario n’est pas pris en charge et a des résultats peu fiables. Il est donc important que vous désactiviez cette modification dans les 30 prochains jours avant de déployer ces nouvelles fonctionnalités. Pour plus d’informations sur la façon de refuser, consultez « J’utilise AD RMS, comment puis-je refuser ? » » plus loin dans cet article. Si vous préférez migrer, consultez [Migration d’AD RMS vers Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Comment faire savoir si j’utilise AD RMS ?

Utilisez ces instructions de [préparation de l’environnement pour Azure Rights Management lorsque vous avez également services AD RMS (Active Directory Rights Management Services) (AD RMS)](/azure/information-protection/deploy-use/prepare-environment-adrms) pour vérifier si vous avez déployé AD RMS :

1. Bien que facultatif, la plupart des déploiements AD RMS publient le point de connexion de service (SCP) sur Active Directory afin que les ordinateurs de domaine puissent découvrir le cluster AD RMS.

   Utilisez ADSI Edit pour voir si un SCP est publié dans Active Directory : CN=Configuration [nom du serveur], CN=Services, CN=RightsManagementServices, CN=SCP

2. Si vous n’utilisez pas de protocole SCP, Windows ordinateurs qui se connectent à un cluster AD RMS doivent être configurés pour la découverte de services côté client ou la redirection des licences à l’aide du registre Windows : `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`

Pour plus d’informations sur ces configurations de Registre, consultez [Activation de la découverte de service côté client à l’aide du registre Windows](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) et [de la redirection du trafic du serveur de licences](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>J’utilise AD RMS, comment puis-je refuser ?

Pour refuser la modification à venir, procédez comme suit :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-IRMConfiguration à l’aide de la syntaxe suivante :

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>À quoi puis-je m’attendre après cette modification ?

Une fois cette option activée, à condition que vous n’ayez pas choisi, vous pouvez commencer à utiliser la nouvelle version de Office 365 Message Encryption qui a été annoncée lors de [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) et tire parti des fonctionnalités de chiffrement et de protection d’Azure Information Protection.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="Message protégé par OME dans Outlook sur le web" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

Pour plus d’informations sur les nouvelles améliorations, consultez [Office 365 Chiffrement](../../compliance/ome.md) des messages.
