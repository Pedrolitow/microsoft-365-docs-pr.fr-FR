---
title: Microsoft Defender pour l’état et les paramètres du capteur d’identité dans Microsoft 365 Defender
description: Découvrez comment configurer Microsoft Defender pour les capteurs d’identité et surveiller leur état d’Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 246fd5ca880ca2d7e187283d06f19d071f5d7e0e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468520"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender pour l’état et les paramètres du capteur d’identité dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer et surveiller les capteurs [Microsoft Defender pour l’identité](/defender-for-identity) [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender pour l’identité. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Afficher les paramètres et l’état du capteur d’identité View Defender

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, go to **Paramètres** and then **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités sur la page Paramètres page" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sélectionnez **la** page Capteurs, qui affiche tous vos capteurs Defender pour l’identité. Pour chaque capteur, vous verrez son nom, son appartenance au domaine, le numéro de version, si les mises à jour doivent être retardées, l’état du service, l’état de mise à jour, l’état d’état, le nombre de problèmes d’état et la création du capteur.

    [![Page Capteur.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >Dans le portail Defender pour l’identité, les paramètres du capteur et les informations d’état se sont produits dans des emplacements distincts. Notez que dans Microsoft 365 Defender ils sont maintenant sur la même page.

1. Si vous sélectionnez **Filtres**, vous pouvez choisir les filtres qui seront disponibles. Ensuite, avec chaque filtre, vous pouvez choisir les capteurs à afficher.

    [![Filtres de capteur.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    :::image type="content" source="../../media/defender-identity/filtered-sensor.png" alt-text="Capteur filtré" lightbox="../../media/defender-identity/filtered-sensor.png":::

1. Si vous sélectionnez l’un des capteurs, un volet s’affiche avec des informations sur le capteur et son état d’état.

    [![Détails du capteur.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Si vous sélectionnez l’un des problèmes d’état de santé, vous obtenez un volet avec plus de détails à leur sujet. Si vous choisissez un problème fermé, vous pouvez le rouvrir à partir d’ici.

   :::image type="content" source="../../media/defender-identity/issue-details.png" alt-text="Détails du problème" lightbox="../../media/defender-identity/issue-details.png":::
    

1. Si vous sélectionnez **Gérer le capteur**, un volet s’ouvre et vous permet de configurer les détails du capteur.

   :::image type="content" source="../../media/defender-identity/manage-sensor.png" alt-text="Option Gérer le capteur" lightbox="../../media/defender-identity/manage-sensor.png":::

   :::image type="content" source="../../media/defender-identity/configure-sensor-details.png" alt-text="Page sur laquelle vous configurez les paramètres du capteur" lightbox="../../media/defender-identity/configure-sensor-details.png":::

1. Dans la page **Capteurs** , vous pouvez exporter votre liste de capteurs vers un fichier .csv en sélectionnant **Exporter**.

   :::image type="content" source="../../media/defender-identity/export-sensors.png" alt-text="Liste d’exportation des capteurs" lightbox="../../media/defender-identity/export-sensors.png":::

## <a name="add-a-sensor"></a>Ajouter un capteur

À partir de **la** page Capteurs, vous pouvez ajouter un nouveau capteur.

1. Sélectionnez **Ajouter un capteur**.

   :::image type="content" source="../../media/defender-identity/add-sensor.png" alt-text="Option Ajouter un capteur" lightbox="../../media/defender-identity/add-sensor.png":::

1. Un volet s’ouvre, vous fournissant un bouton pour télécharger le programme d’installation du capteur et une touche d’accès rapide générée.

   :::image type="content" source="../../media/defender-identity/installer-access-key.png" alt-text="Options de téléchargement du programme d’installation et de régénération de la clé" lightbox="../../media/defender-identity/installer-access-key.png":::

1. **Sélectionnez Télécharger le programme** d’installation pour enregistrer le package localement. Le fichier zip inclut les fichiers suivants :

    - Programme d’installation du capteur Defender pour l’identité

    - Fichier de paramètre de configuration avec les informations requises pour se connecter au service cloud Defender for Identity

1. Copiez **la touche d’accès rapide**. La touche d’accès rapide est requise pour que le capteur Defender for Identity se connecte à votre instance de Defender for Identity. La touche d’accès rapide est un mot de passe unique pour le déploiement du capteur, après quoi toutes les communications sont effectuées à l’aide de certificats pour l’authentification et le chiffrement TLS. Utilisez le **bouton de clé** Régénérer si vous avez besoin de régénérer la nouvelle touche d’accès rapide. Elle n’affecte aucun capteur précédemment déployé, car elle est utilisée uniquement pour l’inscription initiale du capteur.

1. Copiez le package sur le serveur ou le contrôleur de domaine dédié sur lequel vous installez le capteur Defender for Identity.

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité De Defender pour l’identité](manage-security-alerts.md)
