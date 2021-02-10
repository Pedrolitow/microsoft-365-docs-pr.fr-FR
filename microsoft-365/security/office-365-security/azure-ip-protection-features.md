---
title: Fonctionnalités de protection dans Azure Information Protection en cours de déploiement sur des clients existants
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
localization_priority: Normal
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
ms.openlocfilehash: 2cb78f9e13d8ae429f5f46f2b1051d07ee541a10
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50165978"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Fonctionnalités de protection dans Azure Information Protection en cours de déploiement sur des clients existants

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 (plan 2)](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Pour faciliter l’étape initiale de protection de vos informations, à compter de juillet 2018, les fonctionnalités de protection d’Azure Information Protection seront désactivées par défaut pour tous les locataires éligibles Azure Information Protection. Les fonctionnalités de protection dans Azure Information Protection étaient auparavant connues dans Office 365 en tant que Gestion des droits ou Azure RMS. Si votre organisation dispose d’un plan de service Office E3 ou d’un plan de service plus élevé, vous aurez désormais une idée d’avance pour protéger les informations via Azure Information Protection lors du déploiement de ces fonctionnalités.

## <a name="changes-beginning-july-1-2018"></a>Modifications à partir du 1er juillet 2018

À compter du 1er juillet 2018, Microsoft activera la fonctionnalité de protection dans Azure Information Protection pour toutes les organisations avec l’un des plans d’abonnement suivants :

- Le chiffrement de messages Office 365 est proposé dans le cadre d’Office 365 E3 et E5, Microsoft E3 et E5, Office 365 A1, A3 et A5, ainsi que d’Office 365 G3 et G5. Vous n’avez pas besoin de licences supplémentaires pour recevoir les nouvelles fonctionnalités de protection optimisées par Azure Information Protection.

- Vous pouvez également ajouter Azure Information Protection Plan 1 aux plans suivants pour recevoir les nouvelles fonctionnalités de chiffrement de messages Office 365 : Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard ou Office 365 Entreprise E1.

- Chaque utilisateur bénéficiant du chiffrement de messages Office 365 doit être titulaire d’une licence pour être couvert par la fonctionnalité.

- Pour obtenir la liste complète, consultez les [descriptions du service Exchange Online](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) pour le chiffrement de messages Office 365.

Les administrateurs client peuvent vérifier l’état de la protection dans le portail d’administrateur Office 365.

![Capture d’écran activant la gestion des droits dans Office 365.](../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png)

## <a name="why-are-we-making-this-change"></a>Pourquoi a-t-on fait cette modification ?

Le chiffrement de messages Office 365 tire parti des fonctionnalités de protection d’Azure Information Protection. Au cœur des améliorations récentes apportées au chiffrement de messages Office 365 et de nos investissements plus larges en matière de protection des informations dans Microsoft 365, nous facilitent la mise en place de nos fonctionnalités de protection pour les organisations, car, historiquement, les technologies de chiffrement ont été difficiles à configurer. En allumer les fonctionnalités de protection dans Azure Information Protection par défaut, vous pouvez rapidement commencer à protéger vos données sensibles.

## <a name="does-this-impact-me"></a>Cela m’a-t-il un impact ?

Si votre organisation a acheté une licence Office 365 éligible, votre client sera touché par cette modification.

 **IMPORTANT !** Si vous utilisez services AD RMS (Active Directory Rights Management Services) (AD RMS) dans votre environnement local, vous devez soit refuser cette modification immédiatement, soit migrer vers Azure Information Protection avant de la déployer dans les 30 prochains jours. Pour plus d’informations sur la façon de refuser, voir « J’utilise AD RMS, comment puis-je refuser ? » » plus loin dans cet article. Si vous préférez migrer, voir [Migrer d’AD RMS vers Azure Information Protection.](https://docs.microsoft.com/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Puis-je utiliser Azure Information Protection avec services AD RMS (Active Directory Rights Management Services) (AD RMS) ?

Non. Il ne s’agit pas d’un scénario de déploiement pris en charge. Sans suivre les étapes supplémentaires d’opposition, certains ordinateurs peuvent commencer automatiquement à utiliser le service Azure Rights Management et se connecter à votre cluster AD RMS. Ce scénario n’est pas pris en charge et a des résultats peu fiables. Il est donc important que vous désapprovisionnement de cette modification dans les 30 prochains jours avant de déployer ces nouvelles fonctionnalités. Pour plus d’informations sur la façon de refuser, voir « J’utilise AD RMS, comment puis-je refuser ? » » plus loin dans cet article. Si vous préférez migrer, voir [Migrer d’AD RMS vers Azure Information Protection.](https://docs.microsoft.com/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Comment savoir si j’utilise AD RMS ?

Utilisez ces instructions de préparation de l’environnement pour Azure Rights Management lorsque vous avez également [services AD RMS (Active Directory Rights Management Services) (AD RMS)](https://docs.microsoft.com/azure/information-protection/deploy-use/prepare-environment-adrms) pour vérifier si vous avez déployé AD RMS :

1. Bien que facultatif, la plupart des déploiements AD RMS publient le point de connexion de service (SCP) dans Active Directory afin que les ordinateurs de domaine peuvent découvrir le cluster AD RMS.

Utilisez ADSI Edit pour voir si vous avez un SCP publié dans Active Directory : CN=Configuration [nom du serveur], CN=Services, CN=RightsManagementServices, CN=SCP

2. Si vous n’utilisez pas de SCP, les ordinateurs Windows qui se connectent à un cluster AD RMS doivent être configurés pour la découverte de service côté client ou la redirection de licences à l’aide du Registre Windows : HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation ou HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation

Pour plus d’informations sur ces configurations de Registre, voir Activation de la découverte de service côté client à l’aide du [Registre Windows](https://docs.microsoft.com/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) et redirection du trafic du serveur de [licences.](https://docs.microsoft.com/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic)

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>J’utilise AD RMS, comment puis-je refuser ?

Pour refuser la modification à venir, complétez les étapes suivantes :

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lSet-IRMConfiguration cmdlet à l’aide de la syntaxe suivante :

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>À quoi puis-je m’attendre une fois cette modification réalisée ?

Une fois ce chiffrement activé, à condition que vous n’avez pas choisi de le faire, vous pouvez commencer à utiliser la nouvelle version du chiffrement de messages Office 365 annoncée lors de [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) et qui tire parti des fonctionnalités de chiffrement et de protection d’Azure Information Protection.

![Capture d’écran shows an OME protected message in Outlook on the web.](../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png)

Pour plus d’informations sur les nouvelles améliorations, voir chiffrement de [messages Office 365.](../../compliance/ome.md)
