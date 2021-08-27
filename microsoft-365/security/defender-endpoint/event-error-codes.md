---
title: Passer en revue les événements et les erreurs à l’aide de l’Observateur d’événements
description: Obtenez des descriptions et d’autres étapes de dépannage (si nécessaire) pour tous les événements signalés par le service Microsoft Defender for Endpoint.
keywords: résoudre les problèmes, observateur d’événements, résumé du journal, code d’échec, échec, service Microsoft Defender pour point de terminaison, ne peut pas démarrer, rompu, ne peut pas démarrer
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 05/21/2018
ms.technology: mde
ms.openlocfilehash: 6f652987caf977e520dc0681b54c605f7a03b3e5
ms.sourcegitcommit: 132b8dc316bcd4b456de33d6a30e90ca69b0f956
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58607318"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Passer en revue les événements et les erreurs à l’aide de l’Observateur d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Observateur d'événements
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Vous pouvez passer en revue les ID d’événement dans [l’Observateur d’événements](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) sur des appareils individuels.

Par exemple, si les appareils n’apparaissent pas dans la liste **Appareils,** vous devrez peut-être rechercher des ID d’événement sur les appareils. Vous pouvez ensuite utiliser ce tableau pour déterminer d’autres étapes de résolution des problèmes.

**Ouvrez l’Observateur d’événements et recherchez le journal des événements du service Microsoft Defender for Endpoint :**

1. Cliquez **sur Démarrer** dans le menu Windows, tapez Observateur d’événements, puis appuyez sur **Entrée.** 

2. Dans la liste des journaux, sous **Résumé du journal,** faites défiler jusqu’à ce que **microsoft-Windows-SENSE/Opérationnel .** Double-cliquez sur l’élément pour ouvrir le journal.

   Vous pouvez également accéder au journal en expandant **Journaux** des applications et des services \> **Microsoft** \> **Windows** \> **SENSE** et cliquer sur **Opérationnel**.

   > [!NOTE]
   > SENSE est le nom interne utilisé pour faire référence au capteur comportemental qui alimente Microsoft Defender pour endpoint.

3. Les événements enregistrés par le service apparaissent dans le journal. Consultez le tableau suivant pour obtenir la liste des événements enregistrés par le service.

   <br>

   ****

   |ID de l'événement|Message|Description|Action|
   |---|---|---|---|
   |1 |Service Microsoft Defender pour point de terminaison démarré `variable` (version).|Se produit lors du démarrage, de l’arrêt et de l’intégration du système.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |2 |Arrêt du service Microsoft Defender pour point de terminaison.|Se produit lorsque l’appareil est arrêté ou déboardé.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |3 |Le service Microsoft Defender for Endpoint n’a pas réussi à démarrer. Code d’échec `variable` : .|Le service n’a pas commencé.|Examinez les autres messages pour déterminer la cause possible et les étapes de résolution des problèmes.|
   |4 |Microsoft Defender for Endpoint service contacted the server at `variable` .|Variable = URL des serveurs de traitement Defender pour les points de terminaison. <p> Cette URL correspond à celle qui s’est vue dans l’activité du pare-feu ou du réseau.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |5 |Le service Microsoft Defender for Endpoint n’a pas réussi à se connecter au serveur à l’emplacement `variable` .|Variable = URL des serveurs de traitement Defender pour les points de terminaison. <p> Le service n’a pas pu contacter les serveurs de traitement externes à cette URL.|Vérifiez la connexion à l’URL. Voir [Configurer le proxy et la connectivité Internet.](configure-proxy-internet.md)|
   |6 |Le service Microsoft Defender for Endpoint n’est pas intégré et aucun paramètre d’intégration n’a été trouvé.|L’appareil n’a pas été correctement intégré et ne sera pas signalé au portail.|L’intégration doit être exécuté avant de démarrer le service. <p> Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |7 |Le service Microsoft Defender for Endpoint n’a pas réussi à lire les paramètres d’intégration. Échec : `variable` .|Variable = description détaillée de l’erreur. L’appareil n’a pas été correctement intégré et ne sera pas signalé au portail.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |8 |Le service Microsoft Defender for Endpoint n’a pas réussi à nettoyer sa configuration. Code d’échec `variable` : .|**Lors de l’intégration :** Le service n’a pas réussi à nettoyer sa configuration pendant l’intégration. Le processus d’intégration se poursuit. <p> **Lors de laboarding :** Le service n’a pas réussi à nettoyer sa configuration pendant le déboardage. Le processus deboarding est terminé, mais le service continue de s’exécute.|**Intégration :** Aucune action n’est requise. <p> **Pare-papiers :** Redémarrez le système. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |9 |Le service Microsoft Defender for Endpoint n’a pas réussi à modifier son type de démarrage. Code d’échec `variable` : .|**Lors de l’intégration :** L’appareil n’a pas été correctement intégré et ne sera pas signalé au portail. <p>**Lors de laboarding :** Échec de la modification du type de démarrage du service. Le processus deboarding se poursuit. |Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |10 |Le service Microsoft Defender for Endpoint n’a pas réussi à rendre persistantes les informations d’intégration. Code d’échec `variable` : .|L’appareil n’a pas été correctement intégré et ne sera pas signalé au portail.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |11 |Intégration ou ré-intégration du service Defender for Endpoint terminée.|L’appareil est correctement intégré.|Notification de fonctionnement normal ; aucune action n’est requise. <p> L’apparition de l’appareil sur le portail peut prendre plusieurs heures.|
   |12 |Microsoft Defender for Endpoint n’a pas réussi à appliquer la configuration par défaut.|Le service n’a pas pu appliquer la configuration par défaut.|Cette erreur doit être résolue après un court moment.|
   |13 |ID d’appareil Microsoft Defender pour point de terminaison calculé : `variable` .|Processus de fonctionnement normal.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |15 |Microsoft Defender pour le point de terminaison ne peut pas démarrer le canal de commande avec l’URL : `variable` .|Variable = URL des serveurs de traitement Defender pour les points de terminaison. <p> Le service n’a pas pu contacter les serveurs de traitement externes à cette URL.|Vérifiez la connexion à l’URL. Voir [Configurer le proxy et la connectivité Internet.](configure-proxy-internet.md)|
   |17 |Le service Microsoft Defender for Endpoint n’a pas réussi à modifier l’emplacement du service Expériences des utilisateurs connectés et télémétrie. Code d’échec `variable` : .|Une erreur s’est produite avec Windows service de télémétrie.|[Assurez-vous que le service de données](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)de diagnostic est activé >assurez-vous que le service de données de diagnostic est activé. <p> Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |18 |OOBE (Windows Bienvenue) est terminé.|Le service démarre uniquement une fois Windows mises à jour ont terminé l’installation.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |19|La OOBE (Windows Bienvenue) n’est pas encore terminée.|Le service démarre uniquement une fois Windows mises à jour ont terminé l’installation.|Notification de fonctionnement normal ; aucune action n’est requise. <p> Si cette erreur persiste après un redémarrage du système, assurez-vous que toutes Windows mises à jour sont entièrement installées.|
   |20|Impossible d’attendre la fin de la Windows OOBE (bienvenue). Code d’échec `variable` : .|Erreur interne.|Si cette erreur persiste après un redémarrage du système, assurez-vous que toutes Windows mises à jour sont entièrement installées.|
   |25|Le service Microsoft Defender for Endpoint n’a pas réussi à réinitialiser l’état d’état d’état dans le Registre. Code d’échec `variable` : .|L’appareil n’a pas été correctement intégré. Il signale au portail, mais le service peut ne pas apparaître comme inscrit dans SCCM ou le Registre.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |26|Le service Microsoft Defender for Endpoint n’a pas réussi à définir l’état d’intégration dans le Registre. Code d’échec `variable` : .|L’appareil n’a pas été correctement intégré. <p> Il signale au portail, mais le service peut ne pas apparaître comme inscrit dans SCCM ou le Registre.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |27|Le service Microsoft Defender pour points de terminaison n’a pas réussi à activer le mode sensible SENSE Antivirus Microsoft Defender. Échec du processus d’intégration. Code d’échec `variable` : .|Normalement, Antivirus Microsoft Defender passe à un état passif spécial si un autre produit anti-programme malveillant en temps réel s’exécute correctement sur l’appareil, et que l’appareil fait des rapports à Defender pour endpoint.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md) <p> Assurez-vous que la protection contre les programmes malveillants en temps réel s’exécute correctement.|
   |28|Échec de l’inscription au service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint. Code d’échec `variable` : .|Une erreur s’est produite avec Windows service de télémétrie.|[Assurez-vous que le service de données de diagnostic est activé.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) <p> Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |29|Échec de la lecture des paramètres deboarding. Type d’erreur : %1, Code d’erreur : %2, Description : %3|Cet événement se produit lorsque le système ne peut&#39;pas lire les paramètres de hors-carte.|Assurez-vous que l’appareil dispose d’un accès à Internet, puis exécutez à nouveau l’intégralité du processus deboarding. Assurez-vous que le package deboarding n’a pas expiré.|
   |30|Le service Microsoft Defender pour points de terminaison n’a pas réussi à désactiver le mode sensible SENSE Antivirus Microsoft Defender. Code d’échec `variable` : .|Normalement, Antivirus Microsoft Defender passe à un état passif spécial si un autre produit anti-programme malveillant en temps réel s’exécute correctement sur l’appareil, et que l’appareil fait des rapports à Defender pour endpoint.|Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md) <p> Assurez-vous que la protection contre les programmes malveillants en temps réel s’exécute correctement.|
   |31|Échec de l’agrégation du service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint. Code d’échec `variable` : .|Une erreur s’est produite avec Windows service de télémétrie lors de l’intégration. Le processus deboarding se poursuit.|[Recherchez les erreurs avec le service Windows télémétrie.](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled)|
   |32|Le service Microsoft Defender for Endpoint n’a pas réussi à demander à s’arrêter après le processus deboarding. Code d’échec : %1|Une erreur s’est produite lors de la procédure deboarding.|Redémarrez l’appareil.|
   |33|Le service Microsoft Defender for Endpoint n’a pas réussi à rendre persistant le GUID SENSE. Code d’échec `variable` : .|Un identificateur unique est utilisé pour représenter chaque appareil qui rapporte au portail. <p> Si l’identificateur ne persiste pas, le même appareil peut apparaître deux fois dans le portail.|Vérifiez les autorisations du Registre sur l’appareil pour vous assurer que le service peut mettre à jour le Registre.|
   |34|Le service Microsoft Defender pour points de terminaison n’a pas réussi à s’ajouter en tant que dépendance au service Expériences des utilisateurs connectés et télémétrie, ce qui a provoqué l’échec du processus d’intégration. Code d’échec `variable` : .|Une erreur s’est produite avec Windows service de télémétrie.|[Assurez-vous que le service de données de diagnostic est activé.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) <p> Vérifiez que les paramètres et les scripts d’intégration ont été correctement déployés. Essayez de redéployer les packages de configuration. <p> Voir [Appareils Windows 10 intégrés.](configure-endpoints.md)|
   |35|Le service Microsoft Defender pour points de terminaison n’a pas réussi à se supprimer en tant que dépendance au service Expériences des utilisateurs connectés et télémétrie. Code d’échec `variable` : .|Une erreur s’est produite avec Windows service de télémétrie lors de la déboarding. Le processus deboarding se poursuit.|Recherchez les erreurs avec le service Windows de diagnostic.|
   |36|L’inscription au service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint a réussi. Code d’achèvement `variable` : .|L’inscription de Defender pour endpoint auprès du service Expériences des utilisateurs connectés et télémétrie s’est terminée correctement.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |37|Microsoft Defender pour le point de terminaison A est sur le point de dépasser son quota. Module : %1, Quota : {%2} {%3}, Pourcentage d’utilisation du quota : %4.|L’appareil a presque utilisé son quota alloué de la fenêtre actuelle de 24 heures. Il est sur le point d’être limitée.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |38|La connexion réseau est identifiée comme faible. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. Connexion avec indicateur : %2, Internet disponible : %3, réseau gratuit disponible : %4.|L’appareil utilise un réseau payant/payant et contacte le serveur moins fréquemment.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |39|La connexion réseau est identifiée comme normale. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. Connexion avec indicateur : %2, Internet disponible : %3, réseau gratuit disponible : %4.|L’appareil n’utilise pas une connexion payante/payante et contacte le serveur comme d’habitude.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |40|L’état de la batterie est identifié comme faible. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. État de la batterie : %2.|L’appareil a un niveau de batterie faible et contacte le serveur moins fréquemment.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |41|L’état de la batterie est identifié comme normal. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. État de la batterie : %2.|L’appareil n’a pas un niveau de batterie faible et contacte le serveur comme d’habitude.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |42|Le composant Microsoft Defender pour le point de terminaison n’a pas réussi à effectuer une action. Composant : %1, Action : %2, Type d’exception : %3, Message d’exception : %4|Erreur interne. Le service n’a pas réussi à démarrer.|Si cette erreur persiste, contactez le support technique.|
   |43|Le composant Microsoft Defender pour le point de terminaison n’a pas réussi à effectuer une action. Composant : %1, Action : %2, Type d’exception : %3, Erreur d’exception : %4, Message d’exception : %5|Erreur interne. Le service n’a pas réussi à démarrer.|Si cette erreur persiste, contactez le support technique.|
   |44|Arrêt du service Defender pour point de terminaison terminé.|Le service a été offboarded.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |45|Échec de l’inscription et du démarrage de la session de suivi des événements [%1]. Code d’erreur : %2|Une erreur s’est produite lors du démarrage du service lors de la création d’une session ETW. Cela a provoqué l’échec du démarrage du service.|Si cette erreur persiste, contactez le support technique.|
   |46|Échec de l’inscription et du démarrage de la session de suivi des événements [%1] en raison d’un manque de ressources. Code d’erreur : %2. Cela est très probable car il y a trop de sessions de suivi d’événements actives. Le service réessaye dans 1 minute.|Une erreur s’est produite lors du démarrage du service lors de la création d’une session ETW en raison d’un manque de ressources. Le service a démarré et est en cours d’exécution, mais ne signale aucun événement de capteur tant que la session ETW n’est pas démarrée.|Notification de fonctionnement normal ; aucune action n’est requise. Le service essaiera de démarrer la session toutes les minutes.|
   |47|Session de suivi d’événements correctement inscrite et démarrée : récupérée après les tentatives précédentes qui ont échoué.|Cet événement suit l’événement précédent après le démarrage réussi de la session ETW.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |48|Échec de l’ajout d’un fournisseur [%1] à la session de suivi des événements [%2]. Code d’erreur : %3. Cela signifie que les événements de ce fournisseur ne seront pas signalés.|Échec de l’ajout d’un fournisseur à la session ETW. Par conséquent, les événements du fournisseur ne sont pas signalés.|Vérifiez le code d’erreur. Si l’erreur persiste, contactez le support technique.|
   |49|Commande de configuration cloud non valide reçue et ignorée. Version : %1, état : %2, code d’erreur : %3, message : %4|Le service cloud a reçu un fichier de configuration non valide qui a été ignoré.|Si cette erreur persiste, contactez le support technique.|
   |50|Nouvelle configuration cloud appliquée avec succès. Version : %1.|Application réussie d’une nouvelle configuration à partir du service cloud.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |51|La nouvelle configuration cloud n’a pas réussi à s’appliquer, version : %1. Application réussie de la dernière bonne configuration connue, version %2.|Le service cloud a reçu un fichier de configuration non bon. La dernière bonne configuration connue a été appliquée avec succès.|Si cette erreur persiste, contactez le support technique.|
   |52|La nouvelle configuration cloud n’a pas réussi à s’appliquer, version : %1. Échec également de l’application de la dernière bonne configuration connue, version %2. La configuration par défaut a été correctement appliquée.|Le service cloud a reçu un fichier de configuration non bon. Échec de l’application de la dernière bonne configuration connue et la configuration par défaut a été appliquée.|Le service tentera de télécharger un nouveau fichier de configuration dans un délai de 5 minutes. Si l’événement n’est pas #50 - contactez le support technique.|
   |53|Configuration cloud chargée à partir du stockage persistant, version : %1.|La configuration a été chargée à partir d’un stockage persistant au démarrage du service.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |55|Échec de la création dulogger automatique ETW sécurisé. Code d’échec : %1|Échec de la création de l’enregistreur de journaux ETW sécurisé.|Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.|
   |56|Échec de la suppression dulogger automatique ETW sécurisé. Code d’échec : %1|Échec de la suppression de la session ETW sécurisée lors du déboardage.|Contactez le support technique.|
   |57|Capture d’un instantané de l’ordinateur à des fins de dépannage.|Un package d’enquête, également appelé package d’investigation, est en cours de collecte.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |59|Commande de démarrage : %1|Démarrage de l’exécution de la commande de réponse.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |60|Échec d’exécuter la commande %1, erreur : %2.|Échec de l’exécution de la commande de réponse.|Si cette erreur persiste, contactez le support technique.|
   |61|Les paramètres de commande de collecte de données ne sont pas valides : SasUri : %1, compressionLevel : %2.|Échec de la lecture ou de l’analyse des arguments de commande de collecte de données (arguments non valides).|Si cette erreur persiste, contactez le support technique.|
   |62|Échec du démarrage du service Expériences des utilisateurs connectés et télémétrie. Code d’échec : %1|Le service Expériences des utilisateurs connectés et télémétrie (diagtrack) n’a pas réussi à démarrer. La télémétrie de point de terminaison autre que Microsoft Defender ne sera pas envoyée à partir de cet ordinateur.|Recherchez d’autres conseils de dépannage dans le journal des événements : Microsoft-Windows-UniversalTelemetryClient/Operational.|
   |63|Mise à jour du type de démarrage du service externe. Nom : %1, type de démarrage réel : %2, type de démarrage attendu : %3, code de sortie : %4|Type de démarrage mis à jour du service externe.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |64|Démarrage du service externe arrêté. Nom : %1, code de sortie : %2|Démarrage d’un service externe.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |65|Échec du chargement du pilote minifilter du composant Événements de sécurité Microsoft. Code d’échec : %1|Échec du chargement du MsSecFlt.sys du système de fichiers.|Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.|
   |66|Mise à jour de stratégie : mode latence - %1|La stratégie C# de connexion C a été mise à jour.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |68|Le type de démarrage du service est inattendu. Nom du service : %1, type de démarrage réel : %2, type de démarrage attendu : %3|Type de démarrage de service externe inattendu.|Corriger le type de démarrage du service externe.|
   |69|Le service est arrêté. Nom du service : %1|Le service externe est arrêté.|Démarrez le service externe.|
   |70|Mise à jour de stratégie : autoriser la collecte d’exemples - %1|L’exemple de stratégie de collecte a été mis à jour.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |71|Réussi à exécuter la commande : %1|La commande a été exécutée avec succès.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |72|Nous avons essayé d’envoyer le premier rapport de profil d’ordinateur complet. Code de résultat : %1|Informations uniquement.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |73|Sense starting for platform: %1|Informations uniquement.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |74|La balise d’appareil dans le Registre dépasse la limite de longueur. Nom de la balise : %2. Limite de longueur : %1.|La balise d’appareil dépasse la limite de longueur.|Utilisez une balise d’appareil plus courte.|
   |81|Échec de la création dugger automatique Microsoft Defender for Endpoint ETW. Code d’échec : %1|Échec de la création de la session ETW.|Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.|
   |82|Échec de la suppression dugger automatique Microsoft Defender for Endpoint ETW. Code d’échec : %1|Échec de la suppression de la session ETW.|Contactez le support technique.|
   |84|Définissez Antivirus Windows Defender mode en cours d’exécution. Forcer le mode passif : %1, code de résultat : %2.|Définir le mode d’exécution de Defender (actif ou passif).|Notification de fonctionnement normal ; aucune action n’est requise.|
   |85|Échec du déclenchement de Microsoft Defender pour le point de terminaison exécutable. Code d’échec : %1|Échec de l’exécution de SenseIR.|Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.|
   |86|Le démarrage a arrêté à nouveau le service externe qui devrait être en service. Nom : %1, code de sortie : %2|Recommencez le service externe.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |87|Impossible de démarrer le service externe. Nom : %1|Échec du démarrage du service externe.|Contactez le support technique.|
   |88|Mise à jour à nouveau du type de démarrage du service externe. Nom : %1, type de démarrage réel : %2, type de démarrage attendu : %3, code de sortie : %4|Mise à jour du type de démarrage du service externe.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |89|Impossible de mettre à jour le type de démarrage du service externe. Nom : %1, type de début réel : %2, type de début attendu : %3|Ne peut pas mettre à jour le type de démarrage du service externe.|Contactez le support technique.|
   |90|Échec de la configuration de System Guard Runtime Monitor pour la connexion au service cloud dans la région géographique %1. Code d’échec : %2|System Guard Runtime Monitor n’envoie pas de données d’attestation au service cloud.|Vérifiez les autorisations sur le chemin d’accès d’inscription : « HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm ». Si aucun problème n’est détecté, contactez le support technique.|
   |91|Échec de la suppression des informations de région de System Guard Runtime Monitor. Code d’échec : %1|System Guard Runtime Monitor n’envoie pas de données d’attestation au service cloud.|Vérifiez les autorisations sur le chemin d’accès d’inscription : « HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm ». Si aucun problème n’est détecté, contactez le support technique.|
   |92|Arrêt du quota de cyber-données du capteur car le quota de données est dépassé. Reprendra l’envoi une fois la période de quotas franchie. Masque d’état : %1|Dépassez la limite de limitation.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |93|Reprise de l’envoi des données cyber du capteur. Masque d’état : %1|Reprendre l’envoi de cyber-données.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |94|L’exécutable Microsoft Defender for Endpoint a démarré|L’exécutable SenseCE a démarré.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |95|L’exécutable Microsoft Defender for Endpoint a pris fin|L’exécutable SenseCE a pris fin.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |96|Microsoft Defender for Endpoint Init a appelé. Code de résultat : %2|L’exécutable SenseCE a appelé l’initialisation MCE.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |97|Il existe des problèmes de connectivité au cloud pour le scénario DLP|Certains problèmes de connectivité réseau affectent le flux de classification DLP.|Vérifiez la connectivité réseau.|
   |98|La connectivité au cloud pour le scénario DLP a été restaurée|La connectivité au réseau a été restaurée et le flux de classification DLP peut continuer.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |99|Sense a rencontré l’erreur suivante lors de la communication avec le serveur : (%1). Résultat : (%2)|Une erreur de communication s’est produite.|Pour plus d’informations, consultez les événements suivants dans le journal des événements.|
   |100|Échec du démarrage de l’exécutable Microsoft Defender for Endpoint. Code d’échec : %1|L’exécutable SenseCE n’a pas réussi à démarrer.|Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.|
   |102|L’exécutable de détection et de réponse réseau microsoft Defender pour points de terminaison a démarré|L’exécutable SenseNdr a démarré.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |103|L’exécutable de détection et de réponse réseau microsoft Defender pour points de terminaison a pris fin|L’exécutable SenseNdr a pris fin.|Notification de fonctionnement normal ; aucune action n’est requise.|
   |

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="see-also"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Configurer les paramètres de proxy du dispositif et de connectivité Internet](configure-proxy-internet.md)
- [Résoudre des problèmes avec Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
- [Vue d’ensemble de l’analyseur client](overview-client-analyzer.md)
- [Télécharger et exécuter l’analyseur client](download-client-analyzer.md)
- [Comprendre le de rapport HTML de l’analyseur](analyzer-report.md)