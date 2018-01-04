---
title: "Scénarios synchrones utilisant HTTP, TCP ou Canal nommé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76c4c225b333af6d376fa409a05ea5727ede6e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
Cette rubrique décrit les activités et transferts pour différents scénarios de demande/réponse asynchrones, avec des demandes multithread utilisant une connexion HTTP, TCP ou de canal nommé.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Demande/réponse asynchrone sans erreurs  
 Cette section décrit les activités et transferts pour un scénario de demande/réponse asynchrone, avec des clients multithread.  
  
 L'activité de l'appelant se termine lorsque `beginCall` est retourné et `endCall` est retourné. Si un rappel est appelé, celui-ci est retourné.  
  
 L'activité appelée se termine lorsque `beginCall` est retourné, `endCall` est retourné, ou lorsque le rappel est retourné s'il a été appelé à partir de cette activité.  
  
### <a name="asynchronous-client-without-callback"></a>Client asynchrone sans rappel  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>La propagation est activée de chaque côté, avec HTTP  
 ![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Figure 1. Client asynchrone, sans rappel, `propagateActivity` = `true` des deux côtés, HTTP  
  
 Si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.  
  
 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>La propagation est désactivée d'un côté ou de l'autre, avec HTTP  
 Si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction pour transférer vers laquelle. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canal nommé](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Figure 2. Client asynchrone, sans rappel, `propagateActivity` = `false` de chaque côté, HTTP  
  
 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
 Une activité traiter l’Action est créée sur un client asynchrone lorsque `propagateActivity` = `false` à l’appelant ou appelé, et lorsque le message de réponse n’inclut pas un en-tête d’Action.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>La propagation est activée de chaque côté, avec TCP ou Canal nommé  
 ![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canal nommé](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Figure 3 : Client asynchrone, sans rappel, `propagateActivity` = `true` des deux côtés, canal nommé/TCP  
  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Identique à la Figure 1, si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>La propagation est désactivée d'un côté ou de l'autre, avec TCP ou Canal nommé  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Similaire à la figure 2, si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction pour transférer vers laquelle. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canaux nommés](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 La figure 4. Client asynchrone, sans rappel, `propagateActivity` = `false` de chaque côté, canal nommé/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Client asynchrone avec rappel  
 Ce scénario ajoute les activités G et A', pour le rappel et `endCall`, et leurs transferts entrants/sortants.  
  
 Cette section montre seulement l’utilisation de HTTP `propragateActivity` = `true`. Toutefois, les activités et transferts supplémentaires s’appliquent également aux autres cas (c'est-à-dire, `propagateActivity` = `false`, à l’aide de TCP ou canal nommé).  
  
 Le rappel crée une activité (G) lorsque le client appelle le code utilisateur pour notifier que les résultats sont prêts. Le code utilisateur appelle ensuite `endCall` dans le rappel (comme indiqué à la figure 5) ou hors de celui-ci (figure 6). Car on ne sait pas quelle activité utilisateur `endCall` est appelée à partir, cette activité est étiquetée `A’`. L'activité A' peut être identique ou différente de l'activité A.  
  
 ![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 La figure 5. Client asynchrone avec rappel, `endCall` à l'intérieur du rappel  
  
 ![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 La figure 6. Client asynchrone avec rappel, `endCall` hors du rappel  
  
### <a name="asynchronous-server-with-callback"></a>Serveur asynchrone avec rappel  
 ![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Nommé &#45; Canal](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 La figure 7. Serveur asynchrone avec rappel  
  
 La pile de canaux rappelle le client à la réception des messages : les traces de ce processus sont émises dans l'activité ProcessRequest elle-même.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Demande/Réponse asynchrone avec erreurs  
 Des messages d'erreur sont reçus au cours de `endCall`. Sinon, les activités et transferts sont identiques aux scénarios précédents.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Communication unidirectionnelle asynchrone avec ou sans erreurs  
 Aucune réponse ou erreur n'est renvoyée au client.
