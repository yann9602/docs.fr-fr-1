---
title: "Activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e6e97bf935d37f9a39569190b7393a47a54781a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="activity"></a>Activité
Cette rubrique contient des informations sur les suivis d'activité dans le modèle de suivi [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. Les activités traitent des unités permettant à l'utilisateur de réduire la portée d'un échec. Les erreurs qui se produisent au cours d'une même activité sont directement liées entre elles. Par exemple, une opération peut échouer parce que le déchiffrement d'un message a échoué auparavant. Les suivis générés pour les échecs respectifs de l'opération et du déchiffrement apparaissent dans la même activité, dénotant l'existence d'un lien direct entre l'erreur relative au déchiffrement et celle relative à la demande.  
  
## <a name="configuring-activity-tracing"></a>Configuration du suivi des activités  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]Fournit des activités prédéfinies pour les applications de traitement (consultez [liste des activités](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Vous pouvez également définir des activités par programme pour grouper des suivis utilisateur. Pour plus d’informations, consultez [l’émission de Traces de Code utilisateur](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Pour émettre des suivis d'activité pendant l'exécution, utilisez le paramètre `ActivityTracing` de la source de suivi `System.ServiceModel` ou d'autres sources de suivi personnalisées [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], comme illustré dans l'exemple de code de configuration suivant.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Pour en savoir plus sur l’élément de configuration et les attributs utilisés, consultez le [configuration du suivi](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) rubrique.  
  
## <a name="viewing-activities"></a>Affichage des activités  
 Vous pouvez afficher les activités et leur utilité dans le [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Lorsque le suivi des activités est activé, l'outil ci-dessus trie les suivis en fonction des activités concernées. Reportez-vous également au transfert des suivis. Un transfert de suivi indique de quelle manière les différentes activités sont liées les unes par rapport aux autres. Un tel transfert vous indique notamment lorsqu'une activité donnée a provoqué le démarrage d'une autre activité. Par exemple, une demande de message a démarré une négociation de sécurité pour obtenir un jeton de conversation sécurisée.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Corrélation d'activités dans Service Trace Viewer  
 Service Trace Viewer permet d'afficher les activités dans deux vues différentes :  
  
-   **Liste** vue, où l’ID d’activité est utilisé pour corréler des suivis directement entre processus. Les suivis provenant de différents processus, par exemple de processus client et service, mais ayant le même ID d'activité sont regroupés sous la même activité. Par conséquent, si une erreur se produit sur le service et provoque ensuite une erreur sur le client, les deux erreurs s'afficheront dans la même vue d'activité de l'outil.  
  
-   **Graphique** vue, où les activités sont regroupées par processus. Dans cet affichage, un client et un service dont l'ID d'activité est identique ont des traces dans différentes activités. Pour mettre en relation des activités ayant le même ID d'activité, mais émanant de processus différents, l'outil affiche les flux de messages afférents aux activités liées entre elles.  
  
 Pour plus d’informations et pour obtenir un affichage graphique de l’outil Service Trace Viewer, consultez [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) et [à l’aide de Service Trace Viewer pour afficher les suivis corrélés et Résolution des problèmes](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Définition de la portée d'une activité  
 Les activités, définies pendant le design, correspondent à des unités logiques de fonctionnement. Les suivis émis ayant le même ID d'activité sont directement liés les uns aux autres : ils font partie de la même activité. Les activités pouvant franchir les limites de point de terminaison (par exemple, une demande), deux portées sont définies par activité.  
  
-   Portée `Global`, par application. Dans cette portée, l'activité est identifiée par son identificateur d'activité global unique 128 bits (gAId). Le gAid correspond à ce qui est propagé sur des points de terminaison.  
  
-   Portée `Local`, par point de terminaison. Dans le cadre de cette portée, les activités sont identifiées à l'aide de leur identificateur gAId, du nom de la source de suivi émettant leurs suivis et de l'ID de processus. Ce trio constitue l'ID local d'activité, appelé lAId. Le lAId est utilisé pour définir les limites (locales) d'une activité.  
  
## <a name="trace-schema"></a>Schéma de suivi  
 Les traces peuvent être émises à l'aide de tout schéma et sur toutes les plateformes Microsoft. « e2e » (pour « bout en bout ») est un schéma couramment utilisé. Ce schéma comporte l'identificateur à 128 bits (gAId), le nom de la source de suivi et l'ID de processus. Dans le code managé, l'écouteur <xref:System.Diagnostics.XmlWriterTraceListener> émet des suivis dans le schéma E2E.  
  
 Pour définir l'identificateur AID émis avec un suivi, les développeurs peuvent définir la propriété <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> en utilisant un Guid pour le stockage local des threads (Thread Local Storage, TLS). Cela est illustré par l'exemple suivant.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 La définition des identificateurs gAId dans TLS devient évidente lorsque les suivis sont émis à l'aide d'une source de suivi, comme illustré dans l'exemple suivant.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Le suivi émis contiendra le gAId actuellement dans le stockage local des threads, le nom de source de suivi passé comme paramètre au constructeur de la source de suivi, et l'ID du processus actuel.  
  
## <a name="activity-lifetime"></a>Durée de vie des activités  
 Au sens le plus strict, les activités démarrent lorsque leur ID est utilisé pour la première fois dans un suivi émis et s'achèvent lorsque ce même ID est utilisé pour la dernière fois dans un suivi émis. <xref:System.Diagnostics> fournit un ensemble de types de suivis prédéfinis, notamment les suivis de début et de fin, qui permettent de délimiter clairement la durée de vie des activités.  
  
-   Suivi de début : signale le début des activités. Un suivi « Démarrer » fournit un enregistrement du début d’un nouveau jalon de traitement. Ce suivi contient l'ID de la nouvelle activité correspondant à la source de suivi et au processus concernés, sauf lorsque l'ID d'activité est propagé à l'ensemble des points de terminaison, auquel cas il y a un suivi de début par point de terminaison. Parmi les processus provoquant le démarrage d'une nouvelle activité figurent notamment la création d'un nouveau thread pour traitement ou l'entrée d'une nouvelle méthode publique.  
  
-   Suivi de fin : signale la fin des activités. Un suivi « Arrêter » fournit un enregistrement de fin d’un jalon de traitement existant. Ce suivi contient l'ID de l'activité existante correspondant à la source de suivi et au processus concernés, sauf lorsque l'ID d'activité est propagé à l'ensemble des points de terminaison, auquel cas il y a un suivi de fin par point de terminaison.  Les exemples de l’arrêt d’une activité de fin d’un thread de traitement ou de sortie d’une méthode dont le début a été désigné par un suivi « Démarrer ».  
  
-   Suivi d'interruption : signale l'interruption d'une activité. Une trace « Suspend » contient un ID de l’activité dont le traitement est censé reprendre ultérieurement. Aucun suivi depuis la source de suivi en cours n'est émis pour l'ID de cette activité dans l'intervalle de temps qui s'écoule entre ses événements d'interruption et de reprise. Les exemples incluent l'interruption d'une activité lors de l'appel dans une fonction de bibliothèque externe ou lors de l'attente d'une ressource telle qu'un port de terminaison d'E/S.  
  
-   Suivi de reprise : signale la reprise d'une activité. Un suivi de « Reprise » contient un id de l’activité dont le dernier suivi émis à partir de la source de trace en cours a été une trace « Suspend ». Parmi les actions pouvant provoquer la reprise d'une activité figurent notamment les retours d'appel à une fonction de bibliothèque externe ou les indications de reprise envoyées par une ressource, telle qu'un port de terminaison E/S.  
  
-   Transfert :, Car certaines activités sont dus à d’autres, ou se rapportent à d’autres personnes, les activités peuvent être associées à d’autres activités suivis de « Transfert ». Un suivi de transfert enregistre la relation directe existant entre deux activités.  
  
 Les suivis Démarrer et Arrêter ne sont pas critiques pour la corrélation. Toutefois, ils peuvent améliorer les performances, le profilage et la validation de la portée de l'activité.  
  
 Grâce à ces suivis, les outils peuvent optimiser la navigation dans les journaux de suivi. Les événements d'une même activité ou les événements d'activités reliées entre elles (lorsque ces outils prennent en charge les suivis de transfert) peuvent donc être trouvés plus rapidement et facilement. Par exemple, les outils cesseront d'analyser les journaux pour une activité donnée lorsqu'ils verront un suivi Démarrer/Arrêter.  
  
 Ces types de suivis peuvent également être utilisés pour le profilage. Les ressources consommées entre les marqueurs de démarrage et d'arrêt représentent le temps inclusif de l'activité, dont les activités logiques contenues. La soustraction des intervalles de temps entre les suivis Interrompre et Reprendre fournit le temps d'activité réelle.  
  
 Les suivis de fin sont également très utiles lorsqu'il s'agit de valider la portée des activités implémentées. Si certains suivis de traitement apparaissent après le suivi Arrêter au lieu d'apparaître dans une activité donnée, cela peut suggérer une erreur de code.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Instructions relatives à l'utilisation du suivi d'activité  
 La section suivante fournit des instructions sur l'utilisation des suivis ActivityTracing (Démarrer, Arrêter, Interrompre, Reprendre et Transfert).  
  
-   Les suivis correspondent à un graphique cyclique orienté et non à une arborescence. Vous pouvez redonner le contrôle à une activité ayant initié une activité.  
  
-   Une activité désigne une limite de traitement qui peut être explicite pour l'administrateur du système ou pour la supportabilité.  
  
-   Chaque méthode [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], côtés client et serveur, est délimitée par le démarrage d'une nouvelle activité et (une fois la tâche effectuée) par la fin de cette activité qui marque également le retour à l'activité ambiante.  
  
-   Les activités à long terme, telles que l'écoute des connexions ou l'attente des messages, sont représentées par leurs marqueurs de début/fin respectifs.  
  
-   Les activités déclenchées par la réception ou le traitement d'un message sont représentées par les limites de suivi.  
  
-   Les activités représentent des activités, par nécessairement des objets. Une activité doit être interprétée en tant que « cela se produisait quand. . . (un suivi significatif a été émis). »  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du traçage](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [L’émission de Traces de Code utilisateur](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
