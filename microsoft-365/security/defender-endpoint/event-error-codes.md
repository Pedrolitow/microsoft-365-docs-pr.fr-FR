---
title: Passer en revue les événements et les erreurs à l'aide de l'Observateur d'événements
description: Obtenez des descriptions et d'autres étapes de dépannage (si nécessaire) pour tous les événements signalés par le service Microsoft Defender for Endpoint.
keywords: résoudre les problèmes, observateur d'événements, résumé du journal, code d'échec, échec, service Microsoft Defender pour point de terminaison, ne peut pas démarrer, rompu, ne peut pas démarrer
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
ms.openlocfilehash: a8b7268e89470a85a34015967b69abb1818fe64f
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933840"
---
# <a name="review-events-and-errors-using-event-viewer"></a>Passer en revue les événements et les erreurs à l'aide de l'Observateur d'événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Observateur d'événements
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-enablesiem-abovefoldlink)

Vous pouvez passer en revue les ID d'événement dans [l'Observateur d'événements](https://msdn.microsoft.com/library/aa745633(v=bts.10).aspx) sur des appareils individuels.

Par exemple, si les appareils n'apparaissent pas dans la liste **Appareils,** vous devrez peut-être rechercher des ID d'événement sur les appareils. Vous pouvez ensuite utiliser ce tableau pour déterminer d'autres étapes de résolution des problèmes.

**Ouvrez l'Observateur d'événements et recherchez le journal des événements du service Microsoft Defender for Endpoint :**

1. Cliquez **sur Démarrer** dans le menu Windows, tapez Observateur **d'événements,** puis appuyez sur **Entrée.**

2. Dans la liste des journaux, sous **Résumé du journal,** faites défiler jusqu'à ce que **microsoft-Windows-SENSE/Opérationnel s'offre à vous.** Double-cliquez sur l'élément pour ouvrir le journal.

   a.  Vous pouvez également accéder au journal en expandant **Applications et services Journaux**  >  **Microsoft**  >  **Windows**  >  **SENSE** et en cliquant sur **Opérationnel**.

   > [!NOTE]
   > SENSE est le nom interne utilisé pour faire référence au capteur comportemental qui alimente Microsoft Defender pour endpoint.

3. Les événements enregistrés par le service apparaissent dans le journal. Consultez le tableau suivant pour obtenir la liste des événements enregistrés par le service.

<table>
<tbody style="vertical-align:top;">
<tr>
<th>ID de l'événement</th>
<th>Message</th>
<th>Description</th>
<th>Action</th>
</tr>
<tr>
<td>1</td>
<td>Service Microsoft Defender pour point de terminaison démarré <code>variable</code> (version).</td>
<td>Se produit lors du démarrage, de l'arrêt et de l'intégration du système.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>2</td>
<td>Arrêt du service Microsoft Defender pour point de terminaison.</td>
<td>Se produit lorsque l'appareil est arrêté ou déboardé.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>3</td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à démarrer. Code d'échec <code>variable</code> : .</td>
<td>Le service n'a pas commencé.</td>
<td>Examinez les autres messages pour déterminer la cause possible et les étapes de résolution des problèmes.</td>
</tr>
<tr>
<td>4 </td>
<td>Microsoft Defender for Endpoint service contacted the server at <code>variable</code> .</td>
<td>Variable = URL des serveurs de traitement Defender pour les points de terminaison.<br>
Cette URL correspond à celle qui s'est vue dans l'activité du pare-feu ou du réseau.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>5 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à se connecter au serveur à l'emplacement <code>variable</code> .</td>
<td>Variable = URL des serveurs de traitement Defender pour les points de terminaison.<br>
Le service n'a pas pu contacter les serveurs de traitement externes à cette URL.</td>
<td>Vérifiez la connexion à l'URL. Voir <a href="configure-proxy-internet.md" data-raw-source="[Configure proxy and Internet connectivity](configure-proxy-internet.md)">Configurer le proxy et la connectivité Internet.</a></td>
</tr>
<tr>
<td>6 </td>
<td>Le service Microsoft Defender for Endpoint n'est pas intégré et aucun paramètre d'intégration n'a été trouvé.</td>
<td>L'appareil n'a pas été correctement intégré et ne sera pas signalé au portail.</td>
<td>L'intégration doit être exécuté avant de démarrer le service.<br>
Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>7 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à lire les paramètres d'intégration. Échec : <code>variable</code> .</td>
<td>Variable = description détaillée de l'erreur. L'appareil n'a pas été correctement intégré et ne sera pas signalé au portail.</td>
<td>Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>8 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à nettoyer sa configuration. Code d'échec <code>variable</code> : .</td>
<td><b>Lors de l'intégration :</b> Le service n'a pas réussi à nettoyer sa configuration pendant l'intégration. Le processus d'intégration se poursuit. <br><br> <b>Lors de laboarding :</b> Le service n'a pas réussi à nettoyer sa configuration pendant le déboardage. Le processus deboarding est terminé, mais le service continue de s'exécute.
 </td>
<td><b>Intégration :</b> Aucune action n'est requise. <br><br> <b>Pare-papiers :</b> Redémarrez le système.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>9 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à modifier son type de démarrage. Code d'échec <code>variable</code> : .</td>
<td><b>Lors de l'intégration :</b> L'appareil n'a pas été correctement intégré et ne sera pas signalé au portail. <br><br><b>Lors de laboarding :</b> Échec de la modification du type de démarrage du service. Le processus deboarding se poursuit. </td>
<td>Vérifiez que les paramètres d'intégration et les scripts ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>10 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à rendre persistantes les informations d'intégration. Code d'échec <code>variable</code> : .</td>
<td>L'appareil n'a pas été correctement intégré et ne sera pas signalé au portail.</td>
<td>Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>11</td>
<td>Intégration ou ré-intégration du service Defender for Endpoint terminée.</td>
<td>L'appareil est correctement intégré.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.<br>
L'apparition de l'appareil sur le portail peut prendre plusieurs heures.</td>
</tr>
<tr>
<td>12 </td>
<td>Microsoft Defender pour le point de terminaison n'a pas réussi à appliquer la configuration par défaut.</td>
<td>Le service n'a pas pu appliquer la configuration par défaut.</td>
<td>Cette erreur doit être résolue après un court moment.</td>
</tr>
<tr>
<td>13</td>
<td>ID d'appareil Microsoft Defender pour point de terminaison calculé : <code>variable</code> .</td>
<td>Processus de fonctionnement normal.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>15 </td>
<td>Microsoft Defender pour le point de terminaison ne peut pas démarrer le canal de commande avec l'URL : <code>variable</code> .</td>
<td>Variable = URL des serveurs de traitement Defender pour les points de terminaison.<br>
Le service n'a pas pu contacter les serveurs de traitement externes à cette URL.</td>
<td>Vérifiez la connexion à l'URL. Voir <a href="configure-proxy-internet.md" data-raw-source="[Configure proxy and Internet connectivity](configure-proxy-internet.md)">Configurer le proxy et la connectivité Internet.</a></td>
</tr>
<tr>
<td>17 </td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à modifier l'emplacement du service Expériences des utilisateurs connectés et télémétrie. Code d'échec <code>variable</code> : .</td>
<td>Une erreur s'est produite avec le service de télémétrie Windows.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Assurez-vous que le service de données de diagnostic est activé.</a><br>
Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>18 </td>
<td>OOBE (Bienvenue dans Windows) est terminé.</td>
<td>Le service démarre uniquement une fois l'installation des mises à jour Windows terminée.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>19</td>
<td>OOBE (Bienvenue dans Windows) n'est pas encore terminé.</td>
<td>Le service démarre uniquement une fois l'installation des mises à jour Windows terminée.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.<br>
Si cette erreur persiste après un redémarrage du système, assurez-vous que toutes les mises à jour Windows sont entièrement installées.</td>
</tr>
<tr>
<td>20</td>
<td>Impossible d'attendre la fin de la OOBE (Bienvenue dans Windows). Code d'échec <code>variable</code> : .</td>
<td>Erreur interne.</td>
<td>Si cette erreur persiste après un redémarrage du système, assurez-vous que toutes les mises à jour Windows sont entièrement installées.</td>
</tr>
<tr>
<td>25</td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à réinitialiser l'état d'état d'état dans le Registre. Code d'échec <code>variable</code> : .</td>
<td>L'appareil n'a pas été correctement intégré.
Il signale au portail, mais le service peut ne pas apparaître comme inscrit dans SCCM ou le Registre.</td>
<td>Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>26</td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à définir l'état d'intégration dans le Registre. Code d'échec <code>variable</code> : .</td>
<td>L'appareil n'a pas été correctement intégré.<br>
Il signale au portail, mais le service peut ne pas apparaître comme inscrit dans SCCM ou le Registre.</td>
<td>Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>27</td>
<td>Le service Microsoft Defender pour points de terminaison n'a pas réussi à activer le mode sensible SENSE dans l'Antivirus Microsoft Defender. Échec du processus d'intégration. Code d'échec <code>variable</code> : .</td>
<td>Normalement, l'Antivirus Microsoft Defender passe à un état passif spécial si un autre produit anti-programme malveillant en temps réel s'exécute correctement sur l'appareil, et que l'appareil fait des rapports à Defender pour le point de terminaison.</td>
<td>Vérifiez que les paramètres d'intégration et les scripts ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a><br>
Assurez-vous que la protection contre les programmes malveillants en temps réel s'exécute correctement.</td>
</tr>
<tr>
<td>28</td>
<td>Échec de l'inscription au service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint. Code d'échec <code>variable</code> : .</td>
<td>Une erreur s'est produite avec le service de télémétrie Windows.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Assurez-vous que le service de données de diagnostic est activé.</a><br>
Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>29</td>
<td>Échec de la lecture des paramètres deboarding. Type d'erreur : %1, Code d'erreur : %2, Description : %3 </td>
<td>Cet événement se produit lorsque le système ne peut&#39;pas lire les paramètres de hors-carte.</td>
<td>Assurez-vous que l'appareil dispose d'un accès à Internet, puis exécutez à nouveau l'intégralité du processus deboarding. Assurez-vous que le package deboarding n'a pas expiré.</td>
</tr>
<tr>
<td>30</td>
<td>Le service Microsoft Defender pour points de terminaison n'a pas réussi à désactiver le mode sensible SENSE dans l'Antivirus Microsoft Defender. Code d'échec <code>variable</code> : .</td>
<td>Normalement, l'Antivirus Microsoft Defender passe à un état passif spécial si un autre produit anti-programme malveillant en temps réel s'exécute correctement sur l'appareil, et que l'appareil fait des rapports à Defender pour le point de terminaison.</td>
<td>Vérifiez que les paramètres et les scripts d'intégration ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés</a><br>
Assurez-vous que la protection contre les programmes malveillants en temps réel s'exécute correctement.</td>
</tr>
<tr>
<td>31</td>
<td>Échec de l'agrégation du service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint. Code d'échec <code>variable</code> : .</td>
<td>Une erreur s'est produite avec le service de télémétrie Windows lors de l'intégration. Le processus deboarding se poursuit.</td>
<td><a href="troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled" data-raw-source="[Check for errors with the Windows telemetry service](troubleshoot-onboarding.md#ensure-the-diagnostic-data-service-is-enabled)">Recherchez les erreurs avec le service de télémétrie Windows.</a></td>
</tr>
<tr>
<td>32</td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à demander à s'arrêter après le processus deboarding. Code d'échec : %1</td>
<td>Une erreur s'est produite lors de la procédure deboardage.</td>
<td>Redémarrez l'appareil.</td>
</tr>
<tr>
<td>33</td>
<td>Le service Microsoft Defender for Endpoint n'a pas réussi à rendre persistant le GUID SENSE. Code d'échec <code>variable</code> : .</td>
<td>Un identificateur unique est utilisé pour représenter chaque appareil signalant au portail.<br>
Si l'identificateur ne persiste pas, le même appareil peut apparaître deux fois dans le portail.</td>
<td>Vérifiez les autorisations du Registre sur l'appareil pour vous assurer que le service peut mettre à jour le Registre.</td>
</tr>
<tr>
<td>34</td>
<td>Le service Microsoft Defender pour points de terminaison n'a pas réussi à s'ajouter en tant que dépendance au service Expériences des utilisateurs connectés et télémétrie, ce qui a provoqué l'échec du processus d'intégration. Code d'échec <code>variable</code> : .</td>
<td>Une erreur s'est produite avec le service de télémétrie Windows.</td>
<td><a href="troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy" data-raw-source="[Ensure the diagnostic data service is enabled](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)">Assurez-vous que le service de données de diagnostic est activé.</a><br>
Vérifiez que les paramètres d'intégration et les scripts ont été correctement déployés. Essayez de redéployer les packages de configuration.<br>
Voir <a href="configure-endpoints.md" data-raw-source="[Onboard Windows 10 devices](configure-endpoints.md)">Appareils Windows 10 intégrés.</a></td>
</tr>
<tr>
<td>35</td>
<td>Le service Microsoft Defender pour points de terminaison n'a pas réussi à se supprimer en tant que dépendance au service Expériences des utilisateurs connectés et télémétrie. Code d'échec <code>variable</code> : .</td>
<td>Une erreur s'est produite avec le service de télémétrie Windows lors de la déboarding. Le processus deboarding se poursuit.
</td>
<td>Recherchez les erreurs avec le service de données de diagnostic Windows.</td>
</tr>
<tr>
<td>36</td>
<td>L'inscription au service Expériences des utilisateurs connectés et télémétrie de Microsoft Defender for Endpoint a réussi. Code d'achèvement <code>variable</code> : .</td>
<td>L'inscription de Defender pour endpoint auprès du service Expériences des utilisateurs connectés et télémétrie s'est terminée correctement.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>37</td>
<td>Microsoft Defender pour le point de terminaison A est sur le point de dépasser son quota. Module : %1, Quota : {%2} {%3}, Pourcentage d'utilisation du quota : %4.</td>
<td>L'appareil a presque utilisé son quota alloué de la fenêtre actuelle de 24 heures. Il est sur le point d'être limitée.</td>
<td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
<tr>
<td>38</td>
<td>La connexion réseau est identifiée comme faible. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. Connexion avec indicateur : %2, Internet disponible : %3, réseau gratuit disponible : %4.</td>
<td>L’appareil utilise un réseau payant/payant et contacte le serveur moins fréquemment.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>39</td>
<td>La connexion réseau est identifiée comme normale. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. Connexion avec indicateur : %2, Internet disponible : %3, réseau gratuit disponible : %4.</td>
<td>L’appareil n’utilise pas une connexion payante/payante et contacte le serveur comme d’habitude.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>40</td>
<td>L’état de la batterie est identifié comme faible. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. État de la batterie : %2.</td>
<td>L’appareil a un niveau de batterie faible et contacte le serveur moins fréquemment.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>41</td>
<td>L’état de la batterie est identifié comme normal. Microsoft Defender pour le point de terminaison contactera le serveur toutes les %1 minutes. État de la batterie : %2.</td>
<td>L’appareil n’a pas un niveau de batterie faible et contacte le serveur comme d’habitude.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>42</td>
<td>Le composant Microsoft Defender pour le point de terminaison n’a pas réussi à effectuer une action. Composant : %1, Action : %2, Type d’exception : %3, Message d’exception : %4</td>
<td>Erreur interne. Le service n’a pas réussi à démarrer.</td>
<td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
<td>43</td>
<td>Le composant Microsoft Defender pour le point de terminaison n’a pas réussi à effectuer une action. Composant : %1, Action : %2, Type d’exception : %3, Erreur d’exception : %4, Message d’exception : %5</td>
<td>Erreur interne. Le service n’a pas réussi à démarrer.</td>
<td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
<td>44</td>
<td>Arrêt du service Defender pour point de terminaison terminé.</td>
<td>Le service a été offboarded.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>45</td>
<td>Échec de l’inscription et du démarrage de la session de suivi des événements [%1]. Code d’erreur : %2</td>
<td>Une erreur s’est produite lors du démarrage du service lors de la création d’une session ETW. Cela a provoqué l’échec du démarrage du service.</td>
<td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
<td>46</td>
<td>Échec de l’inscription et du démarrage de la session de suivi des événements [%1] en raison d’un manque de ressources. Code d’erreur : %2. Cela est très probable car il y a trop de sessions de suivi d’événements actives. Le service réessaye dans 1 minute.</td>
<td>Une erreur s’est produite lors du démarrage du service lors de la création d’une session ETW en raison d’un manque de ressources. Le service a démarré et est en cours d’exécution, mais ne signale aucun événement de capteur tant que la session ETW n’est pas démarrée.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise. Le service essaiera de démarrer la session toutes les minutes.</td>
</tr>
<tr>
<td>47</td>
<td>Session de suivi d’événements correctement inscrite et démarrée : récupérée après les tentatives précédentes qui ont échoué.</td>
<td>Cet événement suit l’événement précédent après le démarrage réussi de la session ETW.</td>
<td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
<td>48</td>
<td>Échec de l’ajout d’un fournisseur [%1] à la session de suivi des événements [%2]. Code d’erreur : %3. Cela signifie que les événements de ce fournisseur ne seront pas signalés.</td>
<td>Échec de l’ajout d’un fournisseur à la session ETW. Par conséquent, les événements du fournisseur ne sont pas signalés.</td>
<td>Vérifiez le code d’erreur. Si l’erreur persiste, contactez le support technique.</td>
</tr>
</tr>
<tr>
   <td>49</td>
   <td>Commande de configuration cloud non valide reçue et ignorée. Version : %1, état : %2, code d’erreur : %3, message : %4</td>
   <td>Le service cloud a reçu un fichier de configuration non valide qui a été ignoré.</td>
   <td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>50</td>
   <td>Nouvelle configuration cloud appliquée avec succès. Version : %1.</td>
   <td>Application réussie d’une nouvelle configuration à partir du service cloud.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>51</td>
   <td>La nouvelle configuration cloud n’a pas réussi à s’appliquer, version : %1. Application réussie de la dernière bonne configuration connue, version %2.</td>
   <td>Le service cloud a reçu un fichier de configuration non bon. La dernière bonne configuration connue a été appliquée avec succès.</td>
   <td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>52</td>
   <td>La nouvelle configuration cloud n’a pas réussi à s’appliquer, version : %1. Échec également de l’application de la dernière bonne configuration connue, version %2. La configuration par défaut a été correctement appliquée.</td>
   <td>Le service cloud a reçu un fichier de configuration non bon. Échec de l’application de la dernière bonne configuration connue et la configuration par défaut a été appliquée.</td>
   <td>Le service tentera de télécharger un nouveau fichier de configuration dans un délai de 5 minutes. Si l’événement n’est pas #50 - contactez le support technique.</td>
</tr>
<tr>
   <td>53</td>
   <td>Configuration cloud chargée à partir du stockage persistant, version : %1.</td>
   <td>La configuration a été chargée à partir d’un stockage persistant au démarrage du service.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>55</td>
   <td>Échec de la création dulogger automatique ETW sécurisé. Code d’échec : %1</td>
   <td>Échec de la création de l’enregistreur de journaux ETW sécurisé.</td>
   <td>Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>56</td>
   <td>Échec de la suppression dulogger automatique ETW sécurisé. Code d’échec : %1</td>
   <td>Échec de la suppression de la session ETW sécurisée lors du déboardage.</td>
   <td>Contactez le support technique.</td>
</tr>
<tr>
   <td>57</td>
   <td>Capture d’un instantané de l’ordinateur à des fins de dépannage.</td>
   <td>Un package d’enquête, également appelé package d’investigation, est en cours de collecte.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>59</td>
   <td>Commande de démarrage : %1</td>
   <td>Démarrage de l’exécution de la commande de réponse.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>60</td>
   <td>Échec d’exécuter la commande %1, erreur : %2.</td>
   <td>Échec de l’exécution de la commande de réponse.</td>
   <td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>61</td>
   <td>Les paramètres de commande de collecte de données ne sont pas valides : SasUri : %1, compressionLevel : %2.</td>
   <td>Échec de la lecture ou de l’analyse des arguments de commande de collecte de données (arguments non valides).</td>
   <td>Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>62</td>
   <td>Échec du démarrage du service Expériences des utilisateurs connectés et télémétrie. Code d’échec : %1</td>
   <td>Le service Expériences des utilisateurs connectés et télémétrie (diagtrack) n’a pas réussi à démarrer. La télémétrie d’un point de terminaison autre que Microsoft Defender ne sera pas envoyée à partir de cet ordinateur.</td>
   <td>Recherchez d’autres conseils de dépannage dans le journal des événements : Microsoft-Windows-UniversalTelemetryClient/Operational.</td>
</tr>
<tr>
   <td>63</td>
   <td>Mise à jour du type de démarrage du service externe. Nom : %1, type de démarrage réel : %2, type de démarrage attendu : %3, code de sortie : %4</td>
   <td>Type de démarrage mis à jour du service externe.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>64</td>
   <td>Démarrage du service externe arrêté. Nom : %1, code de sortie : %2</td>
   <td>Démarrage d’un service externe.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>65</td>
   <td>Échec du chargement du pilote minifilter du composant Événements de sécurité Microsoft. Code d’échec : %1</td>
   <td>Échec du chargement du MsSecFlt.sys du système de fichiers.</td>
   <td>Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>66</td>
   <td>Mise à jour de stratégie : mode latence - %1</td>
   <td>La stratégie C# de connexion C a été mise à jour.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>68</td>
   <td>Le type de démarrage du service est inattendu. Nom du service : %1, type de démarrage réel : %2, type de démarrage attendu : %3</td>
   <td>Type de démarrage de service externe inattendu.</td>
   <td>Corriger le type de démarrage du service externe.</td>
</tr>
<tr>
   <td>69</td>
   <td>Le service est arrêté. Nom du service : %1</td>
   <td>Le service externe est arrêté.</td>
   <td>Démarrez le service externe.</td>
</tr>
<tr>
   <td>70</td>
   <td>Mise à jour de stratégie : autoriser la collecte d’exemples - %1</td>
   <td>L’exemple de stratégie de collecte a été mis à jour.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>71</td>
   <td>Réussi à exécuter la commande : %1</td>
   <td>La commande a été exécutée avec succès.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>72</td>
   <td>Nous avons essayé d’envoyer le premier rapport de profil d’ordinateur complet. Code de résultat : %1</td>
   <td>Informations uniquement.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>73</td>
   <td>Sense starting for platform: %1</td>
   <td>Informations uniquement.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>74</td>
   <td>La balise de périphérique dans le Registre dépasse la limite de longueur. Nom de la balise : %2. Limite de longueur : %1.</td>
   <td>La balise d’appareil dépasse la limite de longueur.</td>
   <td>Utilisez une balise d’appareil plus courte.</td>
</tr>
<tr>
   <td>81</td>
   <td>Échec de la création dugger automatique Microsoft Defender for Endpoint ETW. Code d’échec : %1</td>
   <td>Échec de la création de la session ETW.</td>
   <td>Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>82</td>
   <td>Échec de la suppression dugger automatique Microsoft Defender for Endpoint ETW. Code d’échec : %1</td>
   <td>Échec de la suppression de la session ETW.</td>
   <td>Contactez le support technique.</td>
</tr>
<tr>
   <td>84</td>
   <td>Définissez Windows Defender mode d’exécution antivirus. Forcer le mode passif : %1, code de résultat : %2.</td>
   <td>Définir le mode d’exécution de Defender (actif ou passif).</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>85</td>
   <td>Échec du déclenchement de Microsoft Defender pour le point de terminaison exécutable. Code d’échec : %1</td>
   <td>Échec de l’exécution de SenseIR.</td>
   <td>Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>86</td>
   <td>Le démarrage a arrêté à nouveau le service externe qui devrait être en service. Nom : %1, code de sortie : %2</td>
   <td>Recommencez le service externe.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>87</td>
   <td>Impossible de démarrer le service externe. Nom : %1</td>
   <td>Échec du démarrage du service externe.</td>
   <td>Contactez le support technique.</td>
</tr>
<tr>
   <td>88</td>
   <td>Mise à jour à nouveau du type de démarrage du service externe. Nom : %1, type de démarrage réel : %2, type de démarrage attendu : %3, code de sortie : %4</td>
   <td>Mise à jour du type de démarrage du service externe.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>89</td>
   <td>Impossible de mettre à jour le type de démarrage du service externe. Nom : %1, type de début réel : %2, type de démarrage attendu : %3</td>
   <td>Ne peut pas mettre à jour le type de démarrage du service externe.</td>
   <td>Contactez le support technique.</td>
</tr>
<tr>
   <td>90</td>
   <td>Échec de la configuration de System Guard Runtime Monitor pour la connexion au service cloud dans la région géographique %1. Code d’échec : %2</td>
   <td>System Guard Runtime Monitor n’envoie pas de données d’attestation au service cloud.</td>
   <td>Vérifiez les autorisations sur le chemin d’accès d’inscription : « HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm ». Si aucun problème n’est détecté, contactez le support technique.</td>
</tr>
<tr>
   <td>91</td>
   <td>Échec de la suppression des informations de région de System Guard Runtime Monitor. Code d’échec : %1</td>
   <td>System Guard Runtime Monitor n’envoie pas de données d’attestation au service cloud.</td>
   <td>Vérifiez les autorisations sur le chemin d’accès d’inscription : « HKLM\Software\Microsoft\Windows\CurrentVersion\Sgrm ». Si aucun problème n’est détecté, contactez le support technique.</td>
</tr>
<tr>
   <td>92</td>
   <td>Arrêt du quota de cyber-données du capteur car le quota de données est dépassé. Reprendra l’envoi une fois la période de quotas franchie. Masque d’état : %1</td>
   <td>Dépassez la limite de limitation.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>93</td>
   <td>Reprise de l’envoi des données cyber du capteur. Masque d’état : %1</td>
   <td>Reprendre l’envoi de cyber-données.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>94</td>
   <td>L’exécutable Microsoft Defender for Endpoint a démarré</td>
   <td>L’exécutable SenseCE a démarré.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>95</td>
   <td>L’exécutable Microsoft Defender for Endpoint a pris fin</td>
   <td>L’exécutable SenseCE a pris fin.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>96</td>
   <td>Microsoft Defender for Endpoint Init a appelé. Code de résultat : %2</td>
   <td>L’exécutable SenseCE a appelé l’initialisation MCE.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>97</td>
   <td>Il existe des problèmes de connectivité au cloud pour le scénario DLP</td>
   <td>Certains problèmes de connectivité réseau affectent le flux de classification DLP.</td>
   <td>Vérifiez la connectivité réseau.</td>
</tr>
<tr>
   <td>98</td>
   <td>La connectivité au cloud pour le scénario DLP a été restaurée</td>
   <td>La connectivité au réseau a été restaurée et le flux de classification DLP peut continuer.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>99</td>
   <td>Sense a rencontré l’erreur suivante lors de la communication avec le serveur : (%1). Résultat : (%2)</td>
   <td>Une erreur de communication s’est produite.</td>
   <td>Pour plus d’informations, consultez les événements suivants dans le journal des événements.</td>
</tr>
<tr>
   <td>100</td>
   <td>Échec du démarrage de l’exécutable Microsoft Defender for Endpoint. Code d’échec : %1</td>
   <td>L’exécutable SenseCE n’a pas réussi à démarrer.</td>
   <td>Redémarrez l’appareil. Si cette erreur persiste, contactez le support technique.</td>
</tr>
<tr>
   <td>102</td>
   <td>L’exécutable de détection et de réponse réseau microsoft Defender pour points de terminaison a démarré</td>
   <td>L’exécutable SenseNdr a démarré.</td>
   <td>Notification de fonctionnement normal ; aucune action n’est requise.</td>
</tr>
<tr>
   <td>103</td>
   <td>L'exécutable de détection et de réponse réseau microsoft Defender pour points de terminaison a pris fin</td>
   <td>L'exécutable SenseNdr a pris fin.</td>
   <td>Notification de fonctionnement normal ; aucune action n'est requise.</td>
</tr>
</tbody>
</table>

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-eventerrorcodes-belowfoldlink)

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Configurer les paramètres de proxy d'appareil et de connectivité Internet](configure-proxy-internet.md)
- [Résoudre des problèmes avec Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
