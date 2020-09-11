---
title: Créer des stratégies de sécurité des appareils dans la sécurité et la mobilité de base
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Utilisez la sécurité et la mobilité de base pour créer des stratégies d’appareil qui protègent les informations de votre organisation.
ms.openlocfilehash: eddd3454e8f00bab7a830e7710331cafd097d7de
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430166"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Créer des stratégies de sécurité des appareils dans la sécurité et la mobilité de base 

Vous pouvez utiliser la mobilité et la sécurité de base pour créer des stratégies d’appareil qui permettent de protéger les informations de votre organisation sur Microsoft 365 contre les accès non autorisés. Vous pouvez appliquer des stratégies à n’importe quel appareil mobile de votre organisation où l’utilisateur de l’appareil dispose d’une licence Microsoft 365 applicable et s’il a été mis en œuvre dans la sécurité et la mobilité de base.

## <a name="before-you-begin"></a>Avant de commencer

>[!IMPORTANT]
>Avant de pouvoir créer une stratégie d’appareil mobile, vous devez activer et configurer la sécurité et la mobilité de base. Pour plus d’informations, reportez-vous à la rubrique Overview of Basic Mobility and Security.

- Découvrez les appareils, les applications d’appareils mobiles et les paramètres de sécurité pris en charge par la mobilité et la sécurité de base. Découvrez [les fonctionnalités de la sécurité et de la mobilité de base](capabilities.md).
- Créez des groupes de sécurité qui incluent les utilisateurs de Microsoft 365 sur lesquels vous souhaitez déployer des stratégies et pour les utilisateurs que vous souhaitez exclure de l’accès bloqué à Microsoft 365. Avant de déployer une nouvelle stratégie vers votre organisation, nous vous recommandons de la tester en la déployant vers un petit nombre d'utilisateurs. Vous pouvez créer et utiliser un groupe de sécurité qui inclut uniquement vous-même ou un petit nombre d’utilisateurs de Microsoft 365 qui peuvent tester la stratégie pour vous. Pour en savoir plus sur les groupes de sécurité, consultez [la rubrique créer, modifier ou supprimer un groupe de sécurité](https://go.microsoft.com/fwlink/p/?LinkId=518555).
- Pour créer et déployer des stratégies de mobilité et de sécurité de base dans Microsoft 365, vous devez être un administrateur général Microsoft 365. Pour plus d’informations, consultez [la rubrique autorisations dans le centre de sécurité & conformité](https://support.microsoft.com/office/d10608af-7934-490a-818e-e68f17d0e9c1).
- Avant de déployer des stratégies, faites en sorte que votre organisation connaisse les impacts potentiels de l’inscriptions d’un appareil dans la sécurité et la mobilité de base. En fonction de la configuration des stratégies, les appareils non conformes ne peuvent pas accéder à Microsoft 365 et aux données, notamment les applications installées, les photos et les informations personnelles sur un appareil inscrit, et les données peuvent être supprimées.

>[!NOTE]
>Les stratégies et les règles d’accès créées dans MDM pour Microsoft 365 Business standard remplacent les stratégies de boîte aux lettres d’appareil mobile Exchange ActiveSync et les règles d’accès des appareils créées dans le centre d’administration Exchange. Après l’enregistrement d’un appareil dans MDM pour Microsoft 365 Business standard, toute stratégie de boîte aux lettres d’appareil mobile Exchange ActiveSync ou règle d’accès aux appareils appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, consultez la rubrique [Exchange ActiveSync dans Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=524380).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Étape 1 : créer une stratégie d’appareil et la déployer sur un groupe de test

Avant de commencer, assurez-vous que vous avez activé et configuré la mobilité et la sécurité de base. Pour obtenir des instructions, voir [Overview of Basic Mobility and Security](overview.md).

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez **Créer une stratégie**.

    :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de sécurité et de mobilité de base":::

3. Sur la page **paramètres de stratégie** , spécifiez les conditions requises à appliquer aux appareils mobiles de votre organisation.

4. **Exiger la gestion du profil de messagerie**: lorsque cette option est activée, les appareils qui n’ont pas de profil de messagerie géré par la mobilité et la sécurité de base ne sont pas considérés comme conformes. Un appareil ne peut pas avoir un profil de messagerie géré lorsqu’il n’est pas correctement ciblé, ou si l’utilisateur a configuré manuellement le compte de messagerie sur l’appareil. Lorsque vous la laissez **désactivée** (valeur par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour obtenir des instructions sur la façon dont les utilisateurs peuvent être conformes lorsque cette option est sélectionnée, consultez [un compte de messagerie existant](https://docs.microsoft.com/intune-user-help/existing-company-email-account-found).

5. Sur la page **voulez-vous appliquer cette stratégie maintenant ?** , sélectionnez les groupes auxquels vous souhaitez appliquer cette stratégie.

6. Sélectionnez **créer cette stratégie**.

La stratégie est poussée vers le périphérique de chaque utilisateur auquel la stratégie s’applique la prochaine fois qu’elle se connecte à Microsoft 365 à l’aide de son appareil mobile. Si aucune stratégie n’a été appliquée à l’appareil mobile pour les utilisateurs, après avoir déployé la stratégie, ils reçoivent une notification sur leur appareil qui inclut les étapes nécessaires à l’inscription et à l’activation de la sécurité et de la mobilité de base. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device.md). Jusqu’à ce qu’ils complètent la sécurité et la mobilité de base hébergée par le service Intune, l’accès à la messagerie, à OneDrive et à d’autres services est restreint. Une fois que l’utilisateur a terminé l’enregistrement à l’aide de l’application portail d’entreprise Intune, il peut utiliser les services et la stratégie est appliquée à son appareil.

## <a name="step-2-verify-that-your-policy-works"></a>Étape 2 : vérifier que votre stratégie fonctionne

Une fois que vous avez créé une stratégie d’appareil, vérifiez que la stratégie fonctionne comme prévu avant de la déployer dans votre organisation.

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .
2. Sélectionnez **afficher la liste des appareils gérés**.
3. Vérifiez le statut des appareils utilisateur auxquels la stratégie est appliquée. Vous voulez que l' **État** des périphériques soit **géré.**
4. Vous pouvez également effectuer une réinitialisation complète ou sélective sur un appareil en cliquant sur l’option **Réinitialiser en usine** ou supprimer les données de l' **entreprise** du bouton **gérer** après avoir sélectionné un appareil. Pour obtenir des instructions, consultez la rubrique [effacer un appareil mobile dans Microsoft 365.

Étape 3 : déployer une stratégie pour votre organisation

Une fois que vous avez créé une stratégie d’appareil et vérifié qu’elle fonctionne comme prévu, déployez-la dans votre organisation.

1. À partir de votre type de navigateur : [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .
2. Sélectionnez la stratégie que vous souhaitez déployer, puis cliquez sur **modifier** en regard de **groupes appliqués à.**
3. Recherchez un groupe à ajouter, puis cliquez sur **Sélectionner**.
4. Sélectionnez **Fermer** et **modifier le paramètre.**
5. Sélectionnez **Fermer** et **modifier la stratégie.**

La stratégie est poussée vers l’appareil mobile de chaque utilisateur auquel la stratégie s’applique lors de sa prochaine connexion à Microsoft 365 à partir de son appareil mobile. Si aucune stratégie n’a été appliquée à l’appareil mobile pour les utilisateurs, ces derniers reçoivent une notification sur leur appareil en vous permettant de les inscrire et de les activer pour la sécurité et la mobilité de base. Une fois l’enregistrement terminé, la stratégie est appliquée à son appareil. Pour plus d’informations, consultez [la rubrique inscrire votre appareil mobile à l’aide de la sécurité et de la sécurité de base](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Étape 4 : bloquer l’accès à la messagerie pour les appareils non pris en charge

Pour sécuriser les informations de votre organisation, vous devez bloquer l’accès de l’application aux courriers électroniques Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par la sécurité et la mobilité de base. Pour obtenir la liste des appareils pris en charge, consultez la rubrique [appareils pris en charge](https://support.microsoft.com/office/capabilities-of-basic-mobility-and-security-a1da44e5-7475-4992-be91-9ccec25905b0#bkmk_supporteddevices). 

**Pour bloquer l’accès aux applications :**

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .
2. Sélectionnez **gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.
3. Pour bloquer les appareils non pris en charge, sélectionnez **bloquer** sous **si un appareil n’est pas pris en charge par MDM pour Microsoft 365**, puis sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Option de base de mobilité et d’accès aux blocs de sécurité":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Étape 5 : Choisir les groupes de sécurité à exclure des vérifications d’accès conditionnel

Si vous souhaitez exclure certaines personnes des vérifications d’accès conditionnel sur leur appareil mobile et que vous avez créé un ou plusieurs groupes de sécurité pour ces personnes, ajoutez les groupes de sécurité ici. Les personnes de ces groupes n’auront aucune stratégie appliquée pour leurs appareils mobiles pris en charge. Cette option est recommandée si vous ne souhaitez plus utiliser la mobilité et la sécurité de base dans votre organisation.

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez **gérer les paramètres d’accès aux appareils à l’échelle de l’organisation**.

    :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Mobilité et sécurité de base créer une option de stratégie":::

3. Sélectionnez **Ajouter** pour ajouter le groupe de sécurité dont les utilisateurs doivent être exclus de l’accès à Microsoft 365. Lorsqu’un utilisateur a été ajouté à cette liste, il peut accéder aux courriers électroniques Microsoft 365 lorsqu’il utilise un appareil non pris en charge.

4. Sélectionnez le groupe de sécurité que vous souhaitez utiliser dans le panneau **Sélectionner un groupe** .

5. Sélectionnez le nom, puis **Ajouter**un  >  **enregistrement**.

6. Dans le panneau **paramètres d’accès aux appareils** à l’échelle de l’organisation, sélectionnez **Enregistrer**.

    :::image type="content" source="../../media/basic-mobility-security/bms-8-allow-access.png" alt-text="Option de sécurité et de mobilité de base-autoriser l’accès":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Quel est l’impact des stratégies de sécurité sur les différents types d’appareils ?

Lorsque vous appliquez une stratégie aux appareils utilisateur, l’impact sur chaque appareil varie en fonction des types d’appareil. Consultez le tableau suivant pour obtenir des exemples de l’impact des stratégies sur les différents appareils.

|**Stratégie de sécurité**|**Android 4 et versions ultérieures**|**Samsung KNOX**|**iOS 6 et versions ultérieures**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée|Non|Oui|Oui|sauvegarde chiffrée iOS requise.|
|Bloquer la sauvegarde sur le cloud|Oui|Oui|Oui|Sauvegarde Google bloquée sur Android (grisé), sauvegarde sur le cloud sous iOS.|
|Bloquer la synchronisation de documents|Non|Non|Oui|iOS : bloquer les documents dans le cloud.|
|Bloquer la synchronisation de photos |Non|Non|Oui|iOS (natif) : bloquer le flux de photos.|
|Bloquer la capture d’écran |Non|Oui|Oui|Bloqué lors de la tentative.|
|Bloquer la visioconférence |Non|Non|Oui|FaceTime bloqué sur iOS, pas sur Skype ou sur d’autres.|
|Bloquer l’envoi de données de diagnostic |Non|Oui|Oui|Bloquer l’envoi des rapports d’incident Google sur Android.|
|Bloquer l’accès au magasin d’applications |Non|Oui|Oui|Icône du magasin d’applications manquante sur la page d’accueil Android, désactivée sous Windows, manquante sous iOS.|
|Exiger le mot de passe pour le magasin d’applications |Non|Non|Oui|iOS : Mot de passe requis pour les achats iTunes.|
|Bloquer la connexion au stockage amovible |Non|Oui|N/D|Android : la carte SD est grisée dans paramètres, Windows avertit l’utilisateur, les applications installées ne sont pas disponibles|
|Bloquer la connexion Bluetooth |Voir les remarques|Voir les remarques|Oui|Nous ne pouvons pas désactiver BlueTooth comme paramètre sur Android. Au lieu de cela, nous désactivons toutes les transactions nécessitant BlueTooth : distribution audio avancée, télécommande audio/vidéo, appareils libres, casque, accès aux annuaires téléphoniques et port série. Un petit message flottant apparaît en bas de la page lorsque l’une d’entre elles est utilisée.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Que se passe-t-il lorsque vous supprimez une stratégie ou un utilisateur de la stratégie ?

Lorsque vous supprimez une stratégie ou que vous supprimez un utilisateur d’un groupe sur lequel la stratégie a été déployée, les paramètres de stratégie, le profil de messagerie Microsoft 365 et les courriers électroniques mis en cache peuvent être supprimés de l’appareil de l’utilisateur. Consultez le tableau suivant pour voir les éléments supprimés pour les différents types d’appareils.

|**Fonctionnalités supprimées**|**iOS 6 et versions ultérieures**|**Android 4 et versions ultérieures (y compris Samsung KNOX**|
|:-----|:-----|:----------------------|
|Profils de messagerie gérés<sup>1</sup>|Oui|Non|
|Bloquer la sauvegarde sur le cloud|Oui|Non|
<sup>1</sup> Si la stratégie a été déployée avec l’option le **profil de messagerie est géré** , le profil de courrier géré et les courriers électroniques mis en cache dans ce profil sont supprimés de l’appareil utilisateur.

La stratégie est supprimée de l’appareil mobile pour chaque utilisateur auquel la stratégie s’applique à la prochaine vérification de la mobilité et de la sécurité de base par l’appareil. Si vous déployez une nouvelle stratégie qui s’applique à ces périphériques utilisateur, ils sont invités à effectuer une nouvelle inscription dans la sécurité et la mobilité de base.

Vous pouvez également réinitialiser un périphérique complètement ou effacer de manière sélective les informations organisationnelles de l’appareil. Pour plus d’informations, reportez-vous à [la rubrique essuyage d’un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md). 

## <a name="related-topics"></a>Voir aussi

[Vue d’ensemble de la sécurité et de la mobilité de base](overview.md)

[Fonctionnalités de la mobilité et de la sécurité de base](capabilities.md)
