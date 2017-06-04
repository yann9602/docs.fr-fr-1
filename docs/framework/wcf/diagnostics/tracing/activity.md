---
title: "Activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Activit&#233;
Cette rubrique contient des informations sur les suivis d'activité dans le modèle de suivi [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].Les activités correspondent à des unités de traitement qui permettent aux utilisateurs de limiter la portée des défaillances.Les erreurs qui se produisent au cours d'une même activité sont directement liées entre elles.Par exemple, une opération peut échouer parce que le déchiffrement d'un message a échoué auparavant.Les suivis générés pour les échecs respectifs de l'opération et du déchiffrement apparaissent dans la même activité, dénotant l'existence d'un lien direct entre l'erreur relative au déchiffrement et celle relative à la demande.  
  
## Configuration du suivi des activités  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fournit des activités prédéfinies pour le traitement des applications \(consultez [Liste des activités](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)\).Vous pouvez également définir d'autres activités par programme afin de regrouper les suivis d'utilisateur.Pour plus d'informations, consultez [Émission de suivis dans du code utilisateur](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Pour émettre des suivis d'activité pendant l'exécution, utilisez le paramètre `ActivityTracing` de la source de suivi `System.ServiceModel` ou d'autres sources de suivi personnalisées [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], comme illustré dans l'exemple de code de configuration suivant.  
  
```  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Pour plus d'informations sur les éléments et les attributs de configuration, consultez la rubrique [Configuration du suivi](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
## Affichage des activités  
 Vous pouvez afficher les activités et leur utilité dans [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).Lorsque le suivi des activités est activé, l'outil ci\-dessus trie les suivis en fonction des activités concernées.Reportez\-vous également au transfert des suivis.Un transfert de suivi indique la manière dont les activités sont liées entre elles.Un tel transfert vous indique notamment lorsqu'une activité donnée a provoqué le démarrage d'une autre activité.Par exemple, une demande de message peut démarrer un protocole de transfert de sécurité afin d'obtenir un jeton de conversation sécurisée.  
  
### Mise en relation des activités dans Service Trace Viewer  
 Service Trace Viewer permet d'afficher les activités dans deux vues différentes :  
  
-   Affichage **Liste** : l'ID de l'activité est directement utilisé pour mettre en relation les suivis générés pour l'ensemble des processus.Les suivis provenant de différents processus, par exemple de processus client et service, mais ayant le même ID d'activité sont regroupés sous la même activité.Par conséquent, dans cet outil, l'erreur générée sur un service et l'erreur en découlant sur le client s'afficheront toutes les deux dans la même vue et seront regroupées sous la même activité.  
  
-   Affichage **Graphique** : les activités sont regroupées par processus.Dans cet affichage, un client et un service dont l'ID d'activité est identique ont des traces dans différentes activités.Pour mettre en relation des activités ayant le même ID d'activité, mais émanant de processus différents, l'outil affiche les flux de messages afférents aux activités liées entre elles.  
  
 Pour plus d'informations et obtenir un exemple d'affichage graphique dans Service Trace Viewer, consultez [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) et [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## Définition de la portée d'une activité  
 Les activités, définies pendant le design, correspondent à des unités logiques de fonctionnement.Les suivis émis ayant le même ID d'activité sont directement liés les uns aux autres : ils font partie de la même activité.Les activités pouvant franchir les limites de point de terminaison \(une demande\), deux portées sont définies par activité.  
  
-   Portée `Global`, par application.Dans le cadre de cette portée, les activités sont identifiées à l'aide d'un identificateur d'activité global unique à 128 bits, appelé gAId.Cet identificateur est propagé vers l'ensemble des points de terminaison.  
  
-   Portée `Local`, par point de terminaison.Dans le cadre de cette portée, les activités sont identifiées à l'aide de leur identificateur gAId, du nom de la source de suivi émettant leurs suivis et de l'ID de processus.Ce trio constitue l'ID local d'activité, appelé lAId.L'identificateur lAId est utilisé pour définir leurs limites locales.  
  
## Schéma de suivi  
 Les traces peuvent être émises à l'aide de tout schéma et sur toutes les plateformes Microsoft.Le « e2e » \(pour « End to End » ou « bout en bout »\) est un schéma courant.Ce schéma comporte l'identificateur à 128 bits \(gAId\), le nom de la source de suivi et l'ID de processus.Dans le code managé, l'écouteur <xref:System.Diagnostics.XmlWriterTraceListener> émet des suivis dans le schéma E2E.  
  
 Pour définir l'identificateur AID émis avec un suivi, les développeurs peuvent définir la propriété <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> en utilisant un Guid pour le stockage local des threads \(Thread Local Storage, TLS\).C'est ce qu'illustre l'exemple suivant.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 La définition des identificateurs gAId dans TLS devient évidente lorsque les suivis sont émis à l'aide d'une source de suivi, comme illustré dans l'exemple suivant.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Le suivi émis contient l'identificateur gAId en cours dans TLS, le nom de la source de suivi passé sous forme de paramètre au constructeur de la source de suivi ainsi que l'ID de processus en cours.  
  
## Durée de vie des activités  
 Au sens le plus strict, les activités démarrent lorsque leur ID est utilisé pour la première fois dans un suivi émis et s'achèvent lorsque ce même ID est utilisé pour la dernière fois dans un suivi émis.<xref:System.Diagnostics> fournit un ensemble de types de suivis prédéfinis, notamment les suivis de début et de fin, qui permettent de délimiter clairement la durée de vie des activités.  
  
-   Suivi de début : signale le début des activités.Un suivi de début enregistre le début d'un nouveau jalon de traitement.Ce suivi contient l'ID de la nouvelle activité correspondant à la source de suivi et au processus concernés, sauf lorsque l'ID d'activité est propagé à l'ensemble des points de terminaison, auquel cas il y a un suivi de début par point de terminaison.Parmi les processus provoquant le démarrage d'une nouvelle activité figurent notamment la création d'un nouveau thread pour traitement ou l'entrée d'une nouvelle méthode publique.  
  
-   Suivi de fin : signale la fin des activités.Un suivi de fin enregistre la fin d'un jalon de traitement en cours.Ce suivi contient l'ID de l'activité existante correspondant à la source de suivi et au processus concernés, sauf lorsque l'ID d'activité est propagé à l'ensemble des points de terminaison, auquel cas il y a un suivi de fin par point de terminaison.Parmi les actions provoquant la fin d'une activité figurent notamment l'arrêt d'un thread de traitement ou d'une méthode en cours dont le démarrage a été signalé par un suivi de début.  
  
-   Suivi d'interruption : signale l'interruption d'une activité.Ce suivi contient l'ID de l'activité en cours et dont le traitement est censé reprendre ultérieurement.Aucun suivi depuis la source de suivi en cours n'est émis pour l'ID de cette activité dans l'intervalle de temps qui s'écoule entre ses événements d'interruption et de reprise.Parmi les actions pouvant provoquer l'interruption d'une activité figurent notamment les appels à une fonction de bibliothèque externe ou les délais d'attente pour obtenir une ressource, par exemple un port de terminaison E\/S.  
  
-   Suivi de reprise : signale la reprise d'une activité.Ce suivi contient l'ID de l'activité en cours dont le dernier suivi émis depuis la source de suivi en cours correspond à un suivi d'interruption.Parmi les actions pouvant provoquer la reprise d'une activité figurent notamment les retours d'appel à une fonction de bibliothèque externe ou les indications de reprise envoyées par une ressource, telle qu'un port de terminaison E\/S.  
  
-   Suivi de transfert : certaines activités pouvant être initiées par d'autres, les suivis de transfert permettent de relier ces activités entre elles.Un suivi de transfert enregistre la relation directe existant entre deux activités.  
  
 Les suivis de début et de fin ne jouent pas un rôle essentiel lors de la mise en relation des activités.En revanche, ces suivis permettent d'améliorer les performances, le profilage ainsi que la validation des portées d'activité.  
  
 Grâce à ces suivis, les outils peuvent optimiser la navigation dans les journaux de suivi. Les événements d'une même activité ou les événements d'activités reliées entre elles \(lorsque ces outils prennent en charge les suivis de transfert\) peuvent donc être trouvés plus rapidement et facilement.Par exemple, ces outils arrêtent d'analyser les journaux lorsqu'ils tombent sur un suivi de début\/fin pour une activité donnée.  
  
 Ces types de suivis peuvent également être utilisés à des fins de profilage.Les ressources consommées entre les marques de début et de fin représentent la durée globale de l'activité, c'est\-à\-dire durée des activités logiques incluse.La durée effective de l'activité est obtenue en soustrayant les délais écoulés entre les suivis d'interruption et de reprise.  
  
 Les suivis de fin sont également très utiles lorsqu'il s'agit de valider la portée des activités implémentées.Si des suivis de traitement continuent d'être générés un fois le suivi de fin émis, cela peut signifier une défaillance au niveau du code.  
  
## Directives concernant l'utilisation des suivis d'activité  
 Les directives suivantes portent sur l'utilisation des suivis ActivityTracing \(Début, Fin, Interruption, Reprise et Transfert\).  
  
-   Les suivis correspondent à un graphique cyclique orienté et non à une arborescence.Vous pouvez redonner le contrôle à une activité ayant initié une activité.  
  
-   Les activités permettent de délimiter les traitements en cours, ce qui peut s'avérer utile aux administrateurs système ou pour déterminer les capacités de prise en charge.  
  
-   Chaque méthode [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], côtés client et serveur, est délimitée par le démarrage d'une nouvelle activité et \(une fois la tâche effectuée\) par la fin de cette activité qui marque également le retour à l'activité ambiante.  
  
-   Les activités à long terme, telles que l'écoute des connexions ou l'attente des messages, sont représentées par leurs marqueurs de début\/fin respectifs.  
  
-   Les activités déclenchées par la réception ou le traitement d'un message sont représentées par des limites de suivi.  
  
-   Les activités représentent des activités, par nécessairement des objets.Le terme Activité doit être entendu au sens de « voilà ce qui était en train de se passer lorsque.....\(un suivi significatif a été émis\). »  
  
## Voir aussi  
 [Configuration du suivi](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)   
 [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)   
 [Scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)   
 [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)   
 [Émission de suivis dans du code utilisateur](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)