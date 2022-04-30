---
title: Utiliser des clés gérées par le client pour chiffrer les données d’audit de votre organisation
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- m365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser des clés gérées par le client pour chiffrer les enregistrements d’audit de votre organisation.
ms.openlocfilehash: afbae48b0417c42edd7e14220fb21f6402af1da7
ms.sourcegitcommit: e0f890f46ae0bde03cc9e1ce178a7c1b8fbe12db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2022
ms.locfileid: "65145417"
---
# <a name="use-customer-key-to-encrypt-audit-records"></a>Utiliser la clé client pour chiffrer les enregistrements d’audit

Vous pouvez maintenant activer le chiffrement de clé client Microsoft Purview pour les enregistrements d’audit. L’audit s’appuie sur le [chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md) pour chiffrer les données d’audit de votre organisation. L’implémentation de la clé client offre une protection supplémentaire en empêchant les systèmes non autorisés ou le personnel du centre de données Microsoft d’afficher vos données d’audit dans le pipeline d’audit et au repos. L’utilisation de la clé client pour chiffrer vos données d’audit vous permet également de respecter les obligations réglementaires ou de conformité, car votre organisation fournit et contrôle les clés de chiffrement.

La clé client nécessite un abonnement Microsoft 365 E5. Pour plus d’informations, consultez [Microsoft 365 conseils sur la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-customer-key-for-microsoft-365).

Même si vous n’utilisez pas la clé client pour chiffrer vos enregistrements d’audit, les données au repos dans Microsoft 365 sont chiffrées par défaut.

## <a name="implement-customer-key-for-auditing"></a>Implémenter la clé client pour l’audit

Pour implémenter la clé client pour l’audit, vous devez créer une stratégie de chiffrement des données (DEP) multi-charge de travail, qui définit la hiérarchie de chiffrement. Cette hiérarchie est utilisée par le service pour chiffrer vos données d’audit à l’aide des deux clés racine que vous gérez et de la clé de disponibilité générée automatiquement et protégée par Microsoft.

Pour obtenir des instructions détaillées pas à pas, consultez [Configurer la clé client](customer-key-set-up.md).

Une fois la configuration terminée, Microsoft 365 chiffre toutes les données de votre organisation, y compris les enregistrements d’audit, à l’aide des clés identifiées dans le DEP multi-charge de travail que vous avez créé.

## <a name="offboarding-from-customer-key"></a>Désintégrage de la clé client

Si vous décidez de ne plus utiliser la clé client pour attribuer des DEP multi-charges de travail, vous devez contacter le support Microsoft avec une demande de « désinscription » à partir de la clé client. Demandez à l’équipe de support technique de déposer une demande de service auprès de l’équipe de clé client Microsoft Purview. Contactez m365-ck@service.microsoft.com si vous avez des questions. Pour plus [d’informations, consultez Restaurer de la clé client aux clés gérées par Microsoft](customer-key-manage.md#roll-back-from-customer-key-to-microsoft-managed-keys) .

Les clients peuvent ne plus vouloir gérer leurs propres clés et peuvent choisir de se déconnecter de CMK.
Pour l’audit, nous n’avons PAS INTÉGRÉ au MMK. Par conséquent, une fois que le locataire se désinscrit de CMK, il n’y aura PAS de secours au deuxième niveau de chiffrement. Les données seront chiffrées au repos par le chiffrement de stockage Azure par défaut.

<!--
Steps: 

- Customer reaches out to MDEPS team to offboard from CMK.

- MDEPS team offboards the customer and marks their DEPs as disabled -

- New data for the customer / tenant will not be encrypted

- Existing / Older encrypted data will be decrypted using the keys associated with the DEP

NOTE: Even after offboarding, tenant is expected to keep their pre-used encryption keys and keep the MDEPS AAD app access to the AKVs till the lifetime of their encrypted data.
-->

## <a name="offboarding-from-microsoft-365"></a>Désintégrage à partir de Microsoft 365

Le vidage d’un DEP multi-charges de travail n’est pas pris en charge pour la clé client Microsoft Purview. Le DEP multi-charges de travail est utilisé pour chiffrer les données sur plusieurs charges de travail sur tous les utilisateurs locataires. Le vidage d’un DEP à plusieurs charges de travail entraînerait l’inaccessibilité des données provenant de plusieurs charges de travail. Si vous décidez de quitter complètement les services Microsoft Purview, vous pouvez poursuivre le chemin de suppression de locataire selon le [processus documenté](/azure/active-directory/enterprise-users/directory-delete-howto). Découvrez comment supprimer un locataire dans Azure Active Directory. »

<!--
- Customer in this case wants to leave the M365 eco-system and ensure all their data is purged / deleted.
- In case of "multi-workload" DEP - purging or deleting the DEP is NOT allowed by policy.
- In this case the customer would revoke access to the AKV containing the CMK keys.
The customer would proceed with the Tenant Deprovisioning process in order to fully leave the service. They may revoke keys, but not required by the process.
- This change would be reflected in ~24 hours across ALE and MDEPS after caches have expired.
- Ideally since customer is exiting the eco-system, no more audit events would be generated for the customer. However in case there are new audit events for the customer, then they will NOT be encrypted using CMK as customer has offboarded / revoked key access.
-->

## <a name="more-information"></a>Informations supplémentaires

- Il faut jusqu’à 24 heures après avoir effectué les étapes d’implémentation pour chiffrer les enregistrements d’audit de votre organisation.
- Si votre organisation dispose déjà d’une prise en charge MDEPS pour d’autres charges de travail (par exemple, Exchange ou SharePoint), vous devez uniquement l’activer pour plusieurs charges de travail.
- Seuls les enregistrements d’audit générés après l’implémentation de la clé client pour l’audit (ou si votre organisation a implémenté la clé client pour plusieurs charges de travail) sont chiffrés. Les enregistrements d’audit existants ne sont pas chiffrés.
