---
title: Créer des stratégies de sécurité des appareils dans Basic Mobility and Security
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
description: Utilisez Basic Mobility and Security pour créer des stratégies d’appareil qui protègent les informations de votre organisation.
ms.openlocfilehash: 077f1e7e0d763aaecfc38fd4b57d9e8912900a3c
ms.sourcegitcommit: 8849dd6f80217c29f427c7f008d918f30c792240
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "49877067"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Créer des stratégies de sécurité des appareils dans Basic Mobility and Security

Vous pouvez utiliser la mobilité et la sécurité de base pour créer des stratégies d’appareil qui aident à protéger les informations de votre organisation sur Microsoft 365 contre tout accès non autorisé. Vous pouvez appliquer des stratégies à n’importe quel appareil mobile de votre organisation où l’utilisateur de l’appareil dispose d’une licence Microsoft 365 applicable et a inscrit l’appareil dans Basic Mobility and Security.

## <a name="before-you-begin"></a>Avant de commencer

> [!IMPORTANT]
> Avant de pouvoir créer une stratégie d’appareil mobile, vous devez activer et configurer Basic Mobility and Security. Pour plus d’informations, voir Vue d’ensemble de la mobilité et de la sécurité de base.

- Découvrez les appareils, les applications pour appareils mobiles et les paramètres de sécurité que Basic Mobility and Security prend en charge. Voir [fonctionnalités de la mobilité et de la sécurité de base.](capabilities.md)
- Créez des groupes de sécurité qui incluent les utilisateurs Microsoft 365 vers qui vous souhaitez déployer des stratégies et pour les utilisateurs que vous souhaitez peut-être exclure du blocage de l’accès à Microsoft 365. Avant de déployer une nouvelle stratégie vers votre organisation, nous vous recommandons de la tester en la déployant vers un petit nombre d'utilisateurs. Vous pouvez créer et utiliser un groupe de sécurité qui inclut uniquement vous-même ou un petit nombre d’utilisateurs De Microsoft 365 qui peuvent tester la stratégie pour vous. Pour en savoir plus sur les groupes de sécurité, voir [Créer, modifier ou supprimer un groupe de sécurité.](https://go.microsoft.com/fwlink/p/?LinkId=518555)
- Pour créer et déployer des stratégies de mobilité et de sécurité de base dans Microsoft 365, vous devez être un administrateur global Microsoft 365. Pour plus d’informations, voir Autorisations dans le [Centre de sécurité & conformité.](https://support.microsoft.com/office/d10608af-7934-490a-818e-e68f17d0e9c1)
- Avant de déployer des stratégies, faites savoir à votre organisation les impacts potentiels de l’inscription d’un appareil dans Basic Mobility and Security. En fonction de la façon dont vous définissez les stratégies, les appareils non conformes peuvent être bloqués pour accéder à Microsoft 365 et aux données, y compris les applications installées, les photos et les informations personnelles sur un appareil inscrit, et les données peuvent être supprimées.

>[!NOTE]
>Les stratégies et règles d’accès créées dans Basic Mobility and Security pour Microsoft 365 Business Standard remplacent Exchange ActiveSync stratégies de boîte aux lettres d’appareil mobile et les règles d’accès aux appareils créées dans le Centre d’administration Exchange. Une fois qu’un appareil est inscrit à Basic Mobility and Security pour Microsoft 365 Business Standard, toute stratégie de boîte aux lettres d’appareil mobile ou règle d’accès aux appareils Exchange ActiveSync appliquée à l’appareil est ignorée. Pour en savoir plus sur Exchange ActiveSync, [voir Exchange ActiveSync dans Exchange Online.](https://go.microsoft.com/fwlink/p/?LinkId=524380)

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Étape 1 : Créer une stratégie d’appareil et déployer sur un groupe de test

Avant de commencer, assurez-vous que vous avez activé et installé Basic Mobility and Security. Pour obtenir des instructions, voir [Vue d’ensemble de la mobilité et de la sécurité de base.](overview.md)

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez **Créer une stratégie**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Paramètres de stratégie de mobilité et de sécurité de base":::

3. Dans la page **Paramètres de stratégie,** spécifiez les exigences que vous souhaitez appliquer aux appareils mobiles de votre organisation.

4. **Exiger la gestion du profil de** messagerie : lorsqu’il est activé, les appareils qui n’ont pas de profil de messagerie géré par Basic Mobility and Security sont considérés comme non conformes. Un appareil ne peut pas avoir de profil de messagerie géré lorsqu’il n’est pas correctement ciblé ou si l’utilisateur a manuellement installé le compte de messagerie sur l’appareil. Lorsque vous  ne l’activez pas (valeur par défaut), ce paramètre n’est pas évalué en matière de conformité ou de non-conformité. Pour obtenir des instructions sur la façon dont les utilisateurs peuvent obtenir la conformité lorsque cette option est sélectionnée, voir Un compte de [messagerie existant a été trouvé.](https://docs.microsoft.com/intune-user-help/existing-company-email-account-found)

5. Dans la page **Voulez-vous appliquer cette** stratégie maintenant ? Choisissez les groupes à appliquer à cette stratégie.

6. Sélectionnez **Créer cette stratégie.**

La stratégie est poussée vers l’appareil de chaque utilisateur à la prochaine fois qu’il se connecte à Microsoft 365 à l’aide de son appareil mobile. Si aucune stratégie n’a été appliquée à l’appareil mobile des utilisateurs auparavant, après avoir déployé la stratégie, ils obtiennent une notification sur leur appareil qui inclut les étapes d’inscription et d’activation de Basic Mobility and Security. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md). Jusqu’à ce qu’ils terminent l’inscription dans Basic Mobility and Security hébergé par le service Intune, l’accès à la messagerie, à OneDrive et à d’autres services est restreint. Une fois l’inscription terminée à l’aide de l’application Portail d’entreprise Intune, ils peuvent utiliser les services et la stratégie est appliquée à leur appareil.

## <a name="step-2-verify-that-your-policy-works"></a>Étape 2 : Vérifier que votre stratégie fonctionne

Une fois que vous avez créé une stratégie d’appareil, vérifiez que la stratégie fonctionne comme prévu avant de la déployer dans votre organisation.

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .
2. Sélectionnez **Afficher la liste des appareils gérés.**
3. Vérifiez le statut des appareils utilisateur auxquels la stratégie est appliquée. Vous souhaitez que **l’état** des appareils soit **géré.**
4. Vous pouvez également faire une réinitialisation complète ou  sélective sur  un appareil en cliquant sur réinitialiser aux usine ou supprimer les données d’entreprise du bouton Gérer après avoir sélectionné un appareil.  Pour obtenir des instructions, voir [Effacer un appareil mobile dans Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Étape 3 : Déployer une stratégie pour votre organisation

Une fois que vous avez créé une stratégie d’appareil et vérifié qu’elle fonctionne comme prévu, déployez-la dans votre organisation.

1. À partir de votre type de navigateur [https://protection.office.com/devicev2](https://protection.office.com/devicev2) : .
2. Sélectionnez la stratégie que vous souhaitez déployer, puis **sélectionnez Modifier** en plus **des groupes appliqués.**
3. Recherchez un groupe à ajouter et cliquez sur **Sélectionner.**
4. Sélectionnez **Fermer** et **modifier le paramètre.**
5. Sélectionnez **Fermer** et **modifier la stratégie.**

La stratégie est poussée vers l’appareil mobile de chaque utilisateur à la prochaine fois qu’il se connecte à Microsoft 365 à partir de son appareil mobile. Si aucune stratégie n’a été appliquée à leur appareil mobile, les utilisateurs obtiennent une notification sur leur appareil avec les étapes nécessaires pour l’inscrire et l’activer pour Basic Mobility and Security. Une fois l’inscription terminée, la stratégie est appliquée à son appareil. Pour plus d’informations, voir [Inscrire votre appareil mobile à l’aide de Basic Mobility and Security](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Étape 4 : Bloquer l’accès à la messagerie pour les appareils non pris en compte

Pour sécuriser les informations de votre organisation, vous devez bloquer l’accès de l’application à la messagerie Microsoft 365 pour les appareils mobiles qui ne sont pas pris en charge par Basic Mobility and Security. Pour obtenir la liste des appareils pris en charge, voir [Appareils pris en charge.](https://support.microsoft.com/office/capabilities-of-basic-mobility-and-security-a1da44e5-7475-4992-be91-9ccec25905b0#bkmk_supporteddevices)

**Pour bloquer l’accès à l’application :**

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .
2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation.**
3. Pour bloquer les appareils non  pris en charge, sélectionnez Bloquer sous Si un appareil n’est pas pris en charge par **Basic Mobility and Security pour Microsoft 365,** puis sélectionnez **Enregistrer**.

   :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Option d’accès de blocage de la mobilité et de la sécurité de base":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Étape 5 : Choisir les groupes de sécurité à exclure des vérifications d’accès conditionnel

Si vous souhaitez exclure certaines personnes des vérifications d’accès conditionnel sur leur appareil mobile et que vous avez créé un ou plusieurs groupes de sécurité pour ces personnes, ajoutez les groupes de sécurité ici. Aucune stratégie n’est appliquée aux personnes de ces groupes pour leurs appareils mobiles pris en charge. Il s’agit de l’option recommandée si vous ne souhaitez plus utiliser la mobilité et la sécurité de base dans votre organisation.

1. À partir de votre navigateur, tapez [https://protection.office.com/devicev2](https://protection.office.com/devicev2) .

2. Sélectionnez **Gérer les paramètres d’accès aux appareils à l’échelle de l’organisation.**

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Mobilité et sécurité de base créent une option de stratégie":::

3. Sélectionnez **Ajouter** pour ajouter le groupe de sécurité dont vous souhaitez exclure les utilisateurs d’un accès bloqué à Microsoft 365. Lorsqu’un utilisateur a été ajouté à cette liste, il peut accéder à la messagerie Microsoft 365 lorsqu’il utilise un appareil non pris en compte.

4. Sélectionnez le groupe de sécurité à utiliser dans le panneau Sélectionner **un** groupe.

5. Sélectionnez le nom, puis **ajoutez**  >  **Enregistrer.**

6. Dans le panneau **Paramètres d’accès aux** appareils à l’échelle de l’organisation, sélectionnez **Enregistrer.**

   :::image type="content" source="../../media/basic-mobility-security/bms-8-allow-access.png" alt-text="Option d’accès autorisé pour la mobilité et la sécurité de base":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Quel est l’impact des stratégies de sécurité sur les différents types d’appareils ?

Lorsque vous appliquez une stratégie aux appareils des utilisateurs, l’impact sur chaque appareil varie légèrement d’un type d’appareil à l’autre. Consultez le tableau suivant pour obtenir des exemples de l’impact des stratégies sur les différents appareils.

|**Stratégie de sécurité**|**Android 4 et version ultérieure**|**Samsung KNOX**|**iOS 6 et les ultérieures**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|Exiger la sauvegarde chiffrée|Non|Oui|Oui|Sauvegarde chiffrée iOS requise.|
|Bloquer la sauvegarde sur le cloud|Oui|Oui|Oui|Sauvegarde Google bloquée sur Android (grisé), sauvegarde sur le cloud sous iOS.|
|Bloquer la synchronisation de documents|Non|Non|Oui|iOS : bloquer les documents dans le cloud.|
|Bloquer la synchronisation de photos |Non|Non|Oui|iOS (natif) : bloquer le flux de photos.|
|Bloquer la capture d’écran |Non|Oui|Oui|Bloqué lors de la tentative.|
|Bloquer la visioconférence |Non|Non|Oui|FaceTime bloqué sur iOS, et non sur Skype ou d’autres.|
|Bloquer l’envoi de données de diagnostic |Non|Oui|Oui|Bloquer l’envoi des rapports d’incident Google sur Android.|
|Bloquer l’accès au magasin d’applications |Non|Oui|Oui|Icône du magasin d’applications manquante sur la page d’accueil Android, désactivée sous Windows, manquante sous iOS.|
|Exiger le mot de passe pour le magasin d’applications |Non|Non|Oui|iOS : Mot de passe requis pour les achats iTunes.|
|Bloquer la connexion au stockage amovible |Non|Oui|N/D|Android : la carte SD est grisée dans les paramètres, Windows avertit l’utilisateur, les applications installées ne sont pas disponibles|
|Bloquer la connexion Bluetooth |Voir les remarques|Voir les remarques|Oui|Nous ne pouvons pas désactiver BlueTooth en tant que paramètre sur Android. Au lieu de cela, nous désactivons toutes les transactions qui nécessitent BlueTooth : distribution audio avancée, contrôle à distance audio/vidéo, appareils mains libres, casque, accès au carnet téléphonique et port série. Un petit message flottant apparaît en bas de la page lorsque l’une d’entre elles est utilisée.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Que se passe-t-il lorsque vous supprimez une stratégie ou un utilisateur de la stratégie ?

Lorsque vous supprimez une stratégie ou supprimez un utilisateur d’un groupe sur lequel la stratégie a été déployée, les paramètres de stratégie, le profil de messagerie Microsoft 365 et les e-mails mis en cache peuvent être supprimés de l’appareil de l’utilisateur. Consultez le tableau suivant pour voir ce qui est supprimé pour les différents types d’appareils.

|**Qu’est-ce qui est supprimé ?**|**iOS 6 et les ultérieures**|**Android 4 et version ultérieure (y compris Samsung KNOX**|
|:-----|:-----|:-----|
|Profils de messagerie<sup>gérés 1</sup>|Oui|Non|
|Bloquer la sauvegarde sur le cloud|Oui|Non|

<sup>1</sup> Si la stratégie a  été déployée avec l’option Profil de messagerie géré, le profil de messagerie géré et les e-mails mis en cache dans ce profil sont supprimés de l’appareil de l’utilisateur.

La stratégie est supprimée de l’appareil mobile pour chaque utilisateur que la stratégie applique lors de la prochaine vérification de son appareil avec Basic Mobility and Security. Si vous déployez une nouvelle stratégie qui s’applique à ces appareils utilisateur, ils sont invités à s’inscrire à nouveau à Basic Mobility and Security.

Vous pouvez également effacer complètement un appareil ou effacer de manière sélective les informations organisationnelles de l’appareil. Pour plus d’informations, voir [Effacer un appareil mobile dans Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-topics"></a>Rubriques connexes

[Vue d’ensemble de la fonction Mobility + Security de Base](overview.md)

[Fonctionnalités Mobility + Security de Base](capabilities.md)
