---
title: Microsoft OneDrive
description: Comment Microsoft Manged Desktop la OneDrive pour les appareils inscrits
keywords: 'Microsoft Manged Desktop, Microsoft 365, service, documentation, applications, applications métier, applications métier'
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
---

# <a name="microsoft-onedrive"></a>Microsoft OneDrive

Microsoft Manged Desktop utilise [OneDrive Entreprise](/onedrive/plan-onedrive-enterprise) service de stockage cloud pour tous les Microsoft Manged Desktop mobiles. Cela garantit que les appareils sont aussi sans état que possible. Les utilisateurs pourront trouver leurs fichiers quel que soit l’appareil auquel ils se connectent. Par exemple, si vous remplacez un Microsoft Manged Desktop par un nouveau, les fichiers seront automatiquement synchronisés avec le nouvel appareil.

Nous configurons automatiquement ces paramètres par défaut sur les appareils gérés Microsoft :

| Fonctionnalité | Description |
| ------ | ------ |
| Configuration silencieuse | OneDrive est configuré en mode silencieux avec le compte d’utilisateur. Il se connecte automatiquement, sans intervention de l’utilisateur, au compte d’utilisateur qui a été utilisé pour se Windows. Pour plus d’informations, [voir Configuration silencieuse des comptes d’utilisateurs - OneDrive](/onedrive/use-silent-account-configuration) |
| Fichiers à la demande | La fonctionnalité Fichiers à la demande permet aux utilisateurs d’accéder aux fichiers à partir de leur stockage cloud dans OneDrive sans avoir à utiliser inutilement de l’espace disque. Pour plus d’informations, voir [Save disk space with OneDrive Files On-Demand for Windows 10](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e). |
| Configuration de la fonctionnalité « Known Folder Move » | La fonctionnalité De déplacement de dossiers connus est activée en mode silencieux pour la protection des données des utilisateurs dans le cloud, ce qui leur permet d’accéder à leurs fichiers à partir de n’importe quel appareil. Pour plus d’informations, voir [Back up your Documents, Pictures, and Desktop folders with OneDrive](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057). <p> Les utilisateurs ne peuvent pas désactiver la fonctionnalité Déplacement de dossier connu ou modifier l’emplacement des dossiers connus pour garantir une expérience cohérente sur Microsoft Manged Desktop appareils.</p>|

## <a name="user-experience"></a>Expérience utilisateur

Lorsque Microsoft Manged Desktop utilisateurs reçoivent un nouvel appareil, ils bénéficient d’une première expérience d’expérience d’utilisateur, en entrant leurs informations d’identification Azure, lors de la configuration de l’appareil. Une fois ce processus terminé, ils peuvent accéder à leur bureau et avoir la OneDrive expérience utilisateur.

1. Le système indique aux utilisateurs OneDrive a été configuré et qu’ils ont été automatiquement OneDrive.

:::image type="content" source="media/onedrive-sync.png" alt-text="La lecture des notifications que vous synchronisez OneDrive et vous pouvez modifier des fichiers dans OneDrive. Cliquez ici pour afficher vos fichiers.":::

2. Le système indique aux utilisateurs que OneDrive déplacement de dossier connu a été configuré pour eux.

:::image type="content" source="media/onedrive-folders.png" alt-text="Notification lisant Votre service informatique a pris en compte vos dossiers importants. Les dossiers sont désormais pris en OneDrive et disponibles à partir d’autres appareils.":::

3. Pour empêcher les icônes en double sur le Bureau lorsque des appareils sont réinitialisés ou réinitialisés, le système supprime automatiquement les icônes Microsoft Edge et Microsoft Teams du Synchronisation OneDrive. Ces informations sont affichées dans l’Explorateur de fichiers.

:::image type="content" source="media/onedrive-teams.png" alt-text="Explorateur de fichiers affichant Teams listes Edge avec cases à cocher effacées et lecture de texte avec pointage exclu de la synchronisation.":::

## <a name="onedrive-sync-restrictions"></a>Synchronisation OneDrive restrictions

Si vous devez restreindre le Synchronisation OneDrive, nous vous recommandons de contrôler l’accès avec une stratégie Azure Active Directory’accès conditionnel. Pour plus d’informations, voir [Activer la prise en charge de l’accès conditionnel dans Synchronisation OneDrive’application](/onedrive/enable-conditional-access).

Si vous ne pouvez pas utiliser une stratégie Azure AD’accès conditionnel dans votre organisation, votre administrateur informatique doit suivre les étapes suivantes :

1. Si vous ne le connaissez pas déjà, recherchez votre ID de client, comme décrit dans La recherche de [votre ID Microsoft 365 client.](/onedrive/find-your-office-365-tenant-id)
1. Connectez-vous au centre OneDrive’administration.
1. Dans le volet gauche, sélectionnez **Synchroniser**.
1. Sélectionnez **la case à** cocher Autoriser la synchronisation uniquement sur les PC joints à des domaines spécifiques, puis ajoutez l’ID de client à la liste des domaines. Pour plus d’informations, voir [Autoriser la synchronisation uniquement sur les ordinateurs joints à des domaines spécifiques](/onedrive/allow-syncing-only-on-specific-domains).

> [!NOTE]
> Ces instructions s’appliquent uniquement aux locataires Microsoft Manged Desktop. Il existe d’autres paramètres utilisés qui ne sont pas abordés dans cet article.
