---
title: Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- MET150
description: Utilisez Mobilité et sécurité de base pour créer des stratégies d’appareil qui protègent les informations de votre organisation.
ms.openlocfilehash: da81f8b002d6bc2292f5067110de368004e4a1ff
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727628"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base

Vous pouvez utiliser Mobilité et sécurité de base pour créer des stratégies d’appareil qui aident à protéger les informations de votre organisation sur Microsoft 365 contre tout accès non autorisé. Vous pouvez appliquer des stratégies à n’importe quel appareil mobile de votre organisation où l’utilisateur de l’appareil dispose d’une licence Microsoft 365 applicable et a inscrit l’appareil dans Mobilité et sécurité de base.

## <a name="before-you-begin"></a>Avant de commencer

> [!IMPORTANT]
> Avant de pouvoir créer une stratégie d’appareil mobile, vous devez activer et configurer Mobilité et sécurité de base. Pour plus d’informations, consultez Vue d’ensemble de la mobilité et de la sécurité de base.

- Découvrez les appareils, les applications d’appareil mobile et les paramètres de sécurité pris en charge par Basic Mobility and Security. Consultez [Fonctionnalités de mobilité et de sécurité de base](capabilities.md).
- Créez des groupes de sécurité qui incluent les utilisateurs Microsoft 365 sur lesquels vous souhaitez déployer des stratégies et pour les utilisateurs que vous souhaitez peut-être exclure de l’accès bloqué à Microsoft 365. Avant de déployer une nouvelle stratégie vers votre organisation, nous vous recommandons de la tester en la déployant vers un petit nombre d'utilisateurs. Vous pouvez créer et utiliser un groupe de sécurité qui inclut uniquement vous-même ou un petit nombre d’utilisateurs Microsoft 365 qui peuvent tester la stratégie pour vous. Pour en savoir plus sur les groupes de sécurité, consultez [Créer, modifier ou supprimer un groupe de sécurité](../email/create-edit-or-delete-a-security-group.md).
- Pour créer et déployer des stratégies de mobilité et de sécurité de base dans Microsoft 365, vous devez être un administrateur général Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le Centre de conformité & sécurité](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Avant de déployer des stratégies, informez votre organisation des impacts potentiels de l’inscription d’un appareil dans Mobilité et sécurité de base. Selon la façon dont vous configurez les stratégies, les appareils non conformes peuvent être bloqués pour accéder à Microsoft 365 et aux données, y compris les applications installées, les photos et les informations personnelles sur un appareil inscrit, et les données peuvent être supprimées.

> [!NOTE]
> Les stratégies et règles d’accès créées dans Mobilité et sécurité de base pour Microsoft 365 Business Standard remplacent Exchange ActiveSync stratégies de boîte aux lettres des appareils mobiles et les règles d’accès aux appareils créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Une fois qu’un appareil est inscrit dans Mobilité et sécurité de base pour Microsoft 365 Business Standard, toute stratégie de boîte aux lettres d’appareil mobile Exchange ActiveSync ou règle d’accès à l’appareil appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, consultez [Exchange ActiveSync dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Étape 1 : Créer une stratégie d’appareil et déployer sur un groupe de test

Avant de commencer, vérifiez que vous avez activé et configuré Mobilité et sécurité de base. Pour obtenir des instructions, consultez [Vue d’ensemble de la mobilité et de la sécurité de base](overview.md).

1. Dans votre navigateur, tapez <https://compliance.microsoft.com/basicmobilityandsecurity>.

2. Sélectionnez **Créer une stratégie**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Paramètres de stratégie mobilité et sécurité de base.":::

3. Dans la page **Paramètres de** stratégie, spécifiez les exigences que vous souhaitez appliquer aux appareils mobiles de votre organisation.

4. **Exiger la gestion du profil de messagerie** : lorsqu’il est activé, les appareils qui n’ont pas de profil de messagerie géré par Basic Mobility and Security sont considérés comme non conformes. Un appareil ne peut pas avoir de profil de messagerie managé lorsqu’il n’est pas correctement ciblé, ou si l’utilisateur a configuré manuellement le compte de messagerie sur l’appareil. Lorsque vous laissez non **activé** (valeur par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour obtenir des instructions sur la façon dont les utilisateurs peuvent être conformes lorsque cette option est sélectionnée, consultez [Un compte de messagerie existant a été trouvé](/intune-user-help/existing-company-email-account-found).

5. Dans la page **Voulez-vous appliquer cette stratégie maintenant ?** , choisissez les groupes auxquels vous souhaitez appliquer cette stratégie.

6. Sélectionnez **Créer cette stratégie**.

La stratégie est envoyée (push) à l’appareil de chaque utilisateur, la stratégie s’applique à la prochaine fois qu’il se connecte à Microsoft 365 à l’aide de son appareil mobile. Si les utilisateurs n’ont pas encore appliqué de stratégie à leur appareil mobile, après avoir déployé la stratégie, ils reçoivent une notification sur leur appareil qui inclut les étapes d’inscription et d’activation de mobilité et de sécurité de base. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md). Tant qu’ils n’ont pas terminé l’inscription dans mobilité de base et sécurité hébergés par le service Intune, l’accès à la messagerie, à OneDrive et à d’autres services est limité. Une fois l’inscription terminée à l’aide de l’application Portail d'entreprise Intune, ils peuvent utiliser les services et la stratégie est appliquée à leur appareil.

## <a name="step-2-verify-that-your-policy-works"></a>Étape 2 : Vérifier que votre stratégie fonctionne

Une fois que vous avez créé une stratégie d’appareil, vérifiez qu’elle fonctionne comme prévu avant de la déployer dans votre organisation.

1. Dans votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez **Afficher la liste des appareils gérés**.
3. Vérifiez le statut des appareils utilisateur auxquels la stratégie est appliquée. Vous souhaitez que **l’état** des appareils soit **géré.**
4. Vous pouvez également effectuer une réinitialisation complète ou sélective sur un appareil en cliquant sur le bouton **Réinitialisation aux paramètres d’usine** ou **Supprimer les données de l’entreprise** dans **Gérer** après avoir sélectionné un appareil. Pour obtenir des instructions, consultez [Réinitialiser un appareil mobile dans Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Étape 3 : Déployer une stratégie dans votre organisation

Une fois que vous avez créé une stratégie d’appareil et vérifié qu’elle fonctionne comme prévu, déployez-la dans votre organisation.

1. À partir de votre navigateur, tapez : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez la stratégie que vous souhaitez déployer, puis choisissez **Modifier** en regard de **Groupes appliqués.**
3. Recherchez un groupe à ajouter, puis cliquez sur **Sélectionner**.
4. Sélectionnez **Fermer** et **modifier le paramètre.**
5. Sélectionnez **Fermer** et **modifier la stratégie.**

La stratégie est envoyée à l’appareil mobile de chaque utilisateur, la stratégie s’applique à la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Si aucune stratégie n’a été appliquée à leur appareil mobile, les utilisateurs reçoivent une notification sur leur appareil avec les étapes à suivre pour l’inscrire et l’activer pour Mobilité et sécurité de base. Une fois l’inscription terminée, la stratégie est appliquée à leur appareil. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de Mobilité et sécurité de base](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Étape 4 : Bloquer l’accès à la messagerie pour les appareils non pris en charge

Pour sécuriser les informations de votre organisation, vous devez bloquer l’accès des applications à la messagerie Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par mobilité et sécurité de base. Pour obtenir la liste des appareils pris en charge, consultez [Appareils pris en charge](../../admin/basic-mobility-security/capabilities.md).

**Pour bloquer l’accès aux applications :**

1. Dans votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.
3. Pour bloquer les appareils non pris en charge, choisissez **Accès** sous **Si un appareil n’est pas pris en charge par Mobilité et sécurité de base pour Microsoft 365**, puis sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="Option de blocage de l’accès mobilité et sécurité de base.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Étape 5 : Choisir les groupes de sécurité à exclure des vérifications d’accès conditionnel

Si vous souhaitez exclure certaines personnes des vérifications d’accès conditionnel sur leur appareil mobile et que vous avez créé un ou plusieurs groupes de sécurité pour ces personnes, ajoutez les groupes de sécurité ici. Aucune stratégie n’est appliquée aux membres de ces groupes pour leurs appareils mobiles pris en charge. Il s’agit de l’option recommandée si vous ne souhaitez plus utiliser mobilité et sécurité de base dans votre organisation.

1. Dans votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Mobilité et sécurité de base créent une option de stratégie.":::

3. Sélectionnez **Ajouter** pour ajouter le groupe de sécurité qui contient des utilisateurs que vous souhaitez exclure de l’accès bloqué à Microsoft 365. Lorsqu’un utilisateur a été ajouté à cette liste, il peut accéder à la messagerie Microsoft 365 lorsqu’il utilise un appareil non pris en charge.

4. Sélectionnez le groupe de sécurité que vous souhaitez utiliser dans le panneau **Sélectionner un groupe** .

5. Sélectionnez le nom, puis **Ajouter Enregistrer** > **.**

6. Dans le panneau **Paramètres d’accès aux appareils à l’échelle** de l’organisation, choisissez **Enregistrer**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-groups.png" alt-text="Option d’autorisation d’accès mobilité et sécurité de base.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Quel est l’impact des stratégies de sécurité sur les différents types d’appareils ?

Lorsque vous appliquez une stratégie aux appareils des utilisateurs, l’impact sur chaque appareil varie quelque peu selon les types d’appareils. Consultez le tableau suivant pour obtenir des exemples de l’impact des stratégies sur les différents appareils.

|**Stratégie de sécurité**|**Android**|**Samsung KNOX**|**iOS**|**Remarques**|
|:-----|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée|Non|Oui|Oui|Sauvegarde chiffrée iOS requise.|
|Bloquer la sauvegarde sur le cloud|Oui|Oui|Oui|Bloquer la sauvegarde Google sur Android (grisé), la sauvegarde cloud sur iOS supervisé.|
|Bloquer la synchronisation de documents|Non|Non|Oui|iOS : bloquer les documents dans le cloud sur les appareils iOS supervisés.|
|Bloquer la synchronisation de photos |Non|Non|Oui|iOS (natif) : bloquer le flux de photos.|
|Bloquer la capture d'écran |Non|Oui|Oui|Bloqué lors de la tentative.|
|Bloquer la visioconférence |Non|Non|Oui|FaceTime bloqué sur les appareils iOS supervisés, et non sur Skype ou d’autres.|
|Bloquer l’envoi de données de diagnostic |Non|Oui|Oui|Bloquer l’envoi des rapports d’incident Google sur Android.|
|Bloquer l’accès au magasin d’applications |Non|Oui|Oui|Icône de l’App Store manquante sur la page d’accueil Android, désactivée sur Windows et appareils iOS supervisés.|
|Exiger le mot de passe pour le magasin d’applications |Non|Non|Oui|iOS : Mot de passe requis pour les achats iTunes.|
|Bloquer la connexion au stockage amovible |Non|Oui|N/A|Android : la carte SD est grisée dans les paramètres, Windows avertit l’utilisateur que les applications installées ne sont pas disponibles|
|Bloquer la connexion Bluetooth |Voir les notes|Voir les notes|Oui|Nous ne pouvons pas désactiver BlueTooth en tant que paramètre sur Android. Au lieu de cela, nous désactivons toutes les transactions qui nécessitent BlueTooth : distribution audio avancée, contrôle à distance audio/vidéo, appareils mains libres, casque, accès au répertoire téléphonique et port série. Un petit message flottant apparaît en bas de la page lorsque l’une d’entre elles est utilisée.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Que se passe-t-il lorsque vous supprimez une stratégie ou un utilisateur de la stratégie ?

Lorsque vous supprimez une stratégie ou supprimez un utilisateur d’un groupe sur lequel la stratégie a été déployée, les paramètres de stratégie, le profil de messagerie Microsoft 365 et les e-mails mis en cache peuvent être supprimés de l’appareil de l’utilisateur. Consultez le tableau suivant pour voir ce qui est supprimé pour les différents types d’appareils.

|**Éléments supprimés**|**iOS**|**Android (y compris Samsung KNOX**|
|:-----|:-----|:-----|
|Profils de messagerie<sup>managés 1</sup>|Oui|Non|
|Bloquer la sauvegarde sur le cloud|Oui|Non|

<sup>1</sup> Si la stratégie a été déployée avec l’option **Email profil géré est** sélectionnée, le profil de messagerie managé et les e-mails mis en cache dans ce profil sont supprimés de l’appareil utilisateur.

La stratégie est supprimée de l’appareil mobile pour chaque utilisateur, la stratégie s’applique à la prochaine fois que son appareil s’est connecté avec Mobilité et sécurité de base. Si vous déployez une nouvelle stratégie qui s’applique à ces appareils utilisateur, ceux-ci sont invités à se réinscrire dans Mobilité et sécurité de base.

Vous pouvez également réinitialiser complètement un appareil ou réinitialiser de manière sélective les informations organisationnelles de l’appareil. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de la mobilité et de la sécurité de base](overview.md) (article)\
[Fonctionnalités de mobilité et de sécurité de base](capabilities.md) (article)