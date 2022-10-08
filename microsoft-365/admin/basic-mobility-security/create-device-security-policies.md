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
ms.openlocfilehash: 5557f6c0d26d1870860b63f7236295ddd39e1171
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68172002"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Créer des stratégies de sécurité des appareils dans Mobilité et sécurité de base

Vous pouvez utiliser La mobilité et la sécurité de base pour créer des stratégies d’appareil qui aident à protéger les informations de votre organisation sur Microsoft 365 contre tout accès non autorisé. Vous pouvez appliquer des stratégies à n’importe quel appareil mobile de votre organisation où l’utilisateur de l’appareil dispose d’une licence Microsoft 365 applicable et a inscrit l’appareil dans Mobilité et sécurité de base.

## <a name="before-you-begin"></a>Avant de commencer

> [!IMPORTANT]
> Avant de pouvoir créer une stratégie d’appareil mobile, vous devez activer et configurer la mobilité et la sécurité de base. Pour plus d’informations, consultez Vue d’ensemble de la mobilité et de la sécurité de base.

- Découvrez les appareils, les applications d’appareil mobile et les paramètres de sécurité pris en charge par Basic Mobility and Security. Consultez [les fonctionnalités de mobilité et de sécurité de base](capabilities.md).
- Créez des groupes de sécurité qui incluent des utilisateurs Microsoft 365 sur lesquels vous souhaitez déployer des stratégies et pour les utilisateurs que vous pouvez exclure de l’accès bloqué à Microsoft 365. Avant de déployer une nouvelle stratégie vers votre organisation, nous vous recommandons de la tester en la déployant vers un petit nombre d'utilisateurs. Vous pouvez créer et utiliser un groupe de sécurité qui inclut uniquement vous-même ou un petit nombre d’utilisateurs Microsoft 365 qui peuvent tester la stratégie pour vous. Pour en savoir plus sur les groupes de sécurité, consultez [Créer, modifier ou supprimer un groupe de sécurité](../email/create-edit-or-delete-a-security-group.md).
- Pour créer et déployer des stratégies de mobilité et de sécurité de base dans Microsoft 365, vous devez être administrateur général de Microsoft 365. Pour plus d’informations, consultez [Autorisations dans le Centre de sécurité & conformité](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Avant de déployer des stratégies, informez votre organisation des impacts potentiels de l’inscription d’un appareil dans Mobilité et sécurité de base. Selon la façon dont vous configurez les stratégies, les appareils non conformes peuvent être bloqués pour accéder à Microsoft 365 et aux données, notamment les applications installées, les photos et les informations personnelles sur un appareil inscrit, et les données peuvent être supprimées.

> [!NOTE]
> Stratégies et règles d’accès créées dans Mobilité et sécurité de base pour Microsoft 365 Business Standard remplacer Exchange ActiveSync stratégies de boîte aux lettres d’appareils mobiles et les règles d’accès aux appareils créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Une fois qu’un appareil est inscrit à Basic Mobility and Security pour Microsoft 365 Business Standard, toute Exchange ActiveSync stratégie de boîte aux lettres d’appareil mobile ou règle d’accès de l’appareil appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, consultez [Exchange ActiveSync dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Étape 1 : Créer une stratégie d’appareil et déployer sur un groupe de tests

Avant de commencer, assurez-vous d’avoir activé et configuré La mobilité et la sécurité de base. Pour obtenir des instructions, consultez [Vue d’ensemble de la mobilité et de la sécurité de base](overview.md).

1. À partir de votre navigateur, tapez <https://compliance.microsoft.com/basicmobilityandsecurity>.

2. Sélectionnez **Créer une stratégie**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Paramètres de stratégie de mobilité et de sécurité de base.":::

3. Dans la page **Paramètres** de stratégie, spécifiez les exigences que vous souhaitez appliquer aux appareils mobiles de votre organisation.

4. **Exiger la gestion du profil de messagerie** : lorsque cette option est activée, les appareils qui n’ont pas de profil de messagerie géré par Mobilité et sécurité de base sont considérés comme non conformes. Un appareil ne peut pas avoir de profil de messagerie géré lorsqu’il n’est pas correctement ciblé ou si l’utilisateur configure manuellement le compte de messagerie sur l’appareil. Lorsque vous le laissez **non activé** (valeur par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour obtenir des instructions sur la façon dont les utilisateurs peuvent être conformes lorsque cette option est sélectionnée, consultez [Un compte de messagerie existant a été trouvé](/intune-user-help/existing-company-email-account-found).

5. Dans la page **Voulez-vous appliquer cette stratégie maintenant ?** , choisissez les groupes auxquels vous souhaitez appliquer cette stratégie.

6. Sélectionnez **Créer cette stratégie**.

La stratégie est envoyée (push) à l’appareil de chaque utilisateur auquel la stratégie s’applique la prochaine fois qu’il se connecte à Microsoft 365 à l’aide de son appareil mobile. Si aucune stratégie n’a été appliquée à son appareil mobile auparavant, une fois la stratégie déployée, les utilisateurs reçoivent une notification sur leur appareil qui inclut les étapes d’inscription et d’activation de la mobilité et de la sécurité de base. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md). Jusqu’à ce qu’ils terminent l’inscription dans mobilité et sécurité de base hébergée par le service Intune, l’accès à la messagerie, à OneDrive et à d’autres services est restreint. Une fois l’inscription terminée à l’aide de l’application Portail d'entreprise Intune, ils peuvent utiliser les services et la stratégie est appliquée à leur appareil.

## <a name="step-2-verify-that-your-policy-works"></a>Étape 2 : Vérifier que votre stratégie fonctionne

Une fois que vous avez créé une stratégie d’appareil, vérifiez que la stratégie fonctionne comme prévu avant de la déployer dans votre organisation.

1. À partir de votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez **Afficher la liste des appareils gérés**.
3. Vérifiez le statut des appareils utilisateur auxquels la stratégie est appliquée. Vous souhaitez que **l’état** des appareils soit **géré.**
4. Vous pouvez également effectuer une réinitialisation complète ou sélective sur un appareil en cliquant sur **La réinitialisation** d’usine ou **supprimer les données d’entreprise** du bouton **Gérer** après avoir sélectionné un appareil. Pour obtenir des instructions, consultez [Réinitialiser un appareil mobile dans Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Étape 3 : Déployer une stratégie dans votre organisation

Une fois que vous avez créé une stratégie d’appareil et vérifié qu’elle fonctionne comme prévu, déployez-la dans votre organisation.

1. À partir de votre type de navigateur : [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez la stratégie à déployer, puis **choisissez Modifier** en regard **des groupes auxquels vous êtes appliqué.**
3. Recherchez un groupe à ajouter, puis cliquez sur **Sélectionner**.
4. Sélectionnez **Fermer** et **modifier le paramètre.**
5. Sélectionnez **Fermer** et **modifier la stratégie.**

La stratégie est envoyée (push) à l’appareil mobile de chaque utilisateur auquel la stratégie s’applique la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Si aucune stratégie n’a été appliquée aux utilisateurs sur leur appareil mobile, ils reçoivent une notification sur leur appareil avec les étapes à suivre pour l’inscrire et l’activer pour la mobilité et la sécurité de base. Une fois l’inscription terminée, la stratégie est appliquée à son appareil. Pour plus d’informations, consultez [Inscrire votre appareil mobile à l’aide de mobilité et de sécurité de base](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Étape 4 : Bloquer l’accès aux e-mails pour les appareils non pris en charge

Pour sécuriser les informations de votre organisation, vous devez bloquer l’accès de l’application à la messagerie Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par mobilité et sécurité de base. Pour obtenir la liste des appareils pris en charge, consultez [Appareils pris en charge](../../admin/basic-mobility-security/capabilities.md).

**Pour bloquer l’accès aux applications :**

1. À partir de votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.
3. Pour bloquer les appareils non pris en charge, choisissez **Accès** sous **Si un appareil n’est pas pris en charge par Mobilité et sécurité de base pour Microsoft 365**, puis **sélectionnez Enregistrer**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="Option d’accès de bloc Mobilité et sécurité de base.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Étape 5 : Choisir les groupes de sécurité à exclure des vérifications d’accès conditionnel

Si vous souhaitez exclure certaines personnes des vérifications d’accès conditionnel sur leur appareil mobile et que vous avez créé un ou plusieurs groupes de sécurité pour ces personnes, ajoutez les groupes de sécurité ici. Aucune stratégie n’est appliquée aux personnes de ces groupes pour leurs appareils mobiles pris en charge. Il s’agit de l’option recommandée si vous ne souhaitez plus utiliser la mobilité et la sécurité de base dans votre organisation.

1. À partir de votre navigateur, tapez [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Mobilité et sécurité de base créent une option de stratégie.":::

3. Sélectionnez **Ajouter** pour ajouter le groupe de sécurité dont les utilisateurs que vous souhaitez exclure d’un accès bloqué à Microsoft 365. Lorsqu’un utilisateur a été ajouté à cette liste, il peut accéder à la messagerie Microsoft 365 lorsqu’il utilise un appareil non pris en charge.

4. Sélectionnez le groupe de sécurité que vous souhaitez utiliser dans le panneau **Sélectionner un groupe** .

5. Sélectionnez le nom, puis **ajoutez Enregistrer** > .

6. Dans le panneau **Paramètres d’accès des appareils à l’échelle de l’organisation** , **choisissez Enregistrer**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-groups.png" alt-text="Mobilité et sécurité de base autorisent l’option d’accès.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Quel est l’impact des stratégies de sécurité sur les différents types d’appareils ?

Lorsque vous appliquez une stratégie aux appareils utilisateur, l’impact sur chaque appareil varie quelque peu d’un type d’appareil à l’autre. Consultez le tableau suivant pour obtenir des exemples de l’impact des stratégies sur les différents appareils.

|**Stratégie de sécurité**|**Android**|**Samsung KNOX**|**iOS**|**Remarques**|
|:-----|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée|Non|Oui|Oui|Sauvegarde chiffrée iOS requise.|
|Bloquer la sauvegarde sur le cloud|Oui|Oui|Oui|Sauvegarde Google bloquée sur Android (grisé), sauvegarde sur le cloud sous iOS.|
|Bloquer la synchronisation de documents|Non|Non|Oui|iOS : bloquer les documents dans le cloud.|
|Bloquer la synchronisation de photos |Non|Non|Oui|iOS (natif) : bloquer le flux de photos.|
|Bloquer la capture d'écran |Non|Oui|Oui|Bloqué lors de la tentative.|
|Bloquer la visioconférence |Non|Non|Oui|FaceTime bloqué sur iOS, pas sur Skype ou d’autres.|
|Bloquer l’envoi de données de diagnostic |Non|Oui|Oui|Bloquer l’envoi des rapports d’incident Google sur Android.|
|Bloquer l’accès au magasin d’applications |Non|Oui|Oui|Icône du magasin d’applications manquante sur la page d’accueil Android, désactivée sous Windows, manquante sous iOS.|
|Exiger le mot de passe pour le magasin d’applications |Non|Non|Oui|iOS : Mot de passe requis pour les achats iTunes.|
|Bloquer la connexion au stockage amovible |Non|Oui|N/A|Android : la carte SD est grisée dans les paramètres, Windows avertit l’utilisateur, les applications installées ne sont pas disponibles|
|Bloquer la connexion Bluetooth |Voir les notes|Voir les notes|Oui|Nous ne pouvons pas désactiver BlueTooth en tant que paramètre sur Android. Au lieu de cela, nous désactivons toutes les transactions qui nécessitent BlueTooth : distribution audio avancée, contrôle à distance audio/vidéo, appareils mains libres, casque, accès au carnet de téléphone et port série. Un petit message flottant apparaît en bas de la page lorsque l’une d’entre elles est utilisée.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Que se passe-t-il lorsque vous supprimez une stratégie ou un utilisateur de la stratégie ?

Lorsque vous supprimez une stratégie ou supprimez un utilisateur d’un groupe sur lequel la stratégie a été déployée, les paramètres de stratégie, le profil de messagerie Microsoft 365 et les e-mails mis en cache peuvent être supprimés de l’appareil de l’utilisateur. Consultez le tableau suivant pour voir ce qui est supprimé pour les différents types d’appareils.

|**Ce qui est supprimé**|**iOS**|**Android (y compris Samsung KNOX)**|
|:-----|:-----|:-----|
|Profils de messagerie<sup>managés 1</sup>|Oui|Non|
|Bloquer la sauvegarde sur le cloud|Oui|Non|

<sup>1</sup> Si la stratégie a été déployée avec l’option **Email profil est géré** sélectionné, le profil de messagerie managé et les e-mails mis en cache dans ce profil sont supprimés de l’appareil utilisateur.

La stratégie est supprimée de l’appareil mobile pour chaque utilisateur que la stratégie s’applique à la prochaine fois que son appareil est connecté avec Mobilité et sécurité de base. Si vous déployez une nouvelle stratégie qui s’applique à ces appareils utilisateur, ils sont invités à se réinscrivez dans Mobilité et sécurité de base.

Vous pouvez également réinitialiser un appareil complètement ou réinitialiser de manière sélective les informations organisationnelles de l’appareil. Pour plus d’informations, consultez [Réinitialiser un appareil mobile dans Mobilité et sécurité de base](wipe-mobile-device.md).

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de la mobilité et de la sécurité de base](overview.md) (article)\
[Fonctionnalités de la mobilité et de la sécurité de base](capabilities.md) (article)