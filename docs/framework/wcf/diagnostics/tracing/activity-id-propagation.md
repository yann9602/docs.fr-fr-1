---
title: "Propagation d&#39;ID d&#39;activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Propagation d&#39;ID d&#39;activit&#233;
La propagation a lieu lorsque le suivi d'activité ServiceModel est activé \(propagation ServiceModel\) ou désactivé \(propagation d'activité utilisateur\-à\-utilisateur\).  
  
## Le suivi d'activité ServiceModel est activé  
 Si le suivi d'activité \(ActivityTracing\) ServiceModel est activé, la propagation a lieu entre les activités ProcessAction.  
  
### Serveur  
 Lorsque l'attribut `propagateActivity` a la valeur `true` sur le client et sur le serveur, l'ID de l'activité `ProcessAction` sur le serveur est identique à l'ID dans l'en\-tête de message `ActivityId` propagé.  
  
 Lorsque aucun en\-tête `ActivityId` n'est présent dans le message \(autrement dit, `propagateActivity`\=`false` sur le client\) ou lorsque `propagateActivity`\=`false` sur le serveur, le serveur génère un nouvel ID d'activité.  
  
### Client  
 Si le client est à thread unique de façon synchrone, il ignore tout paramètre de `propagateActivity` sur le client ou le serveur.  Au lieu de cela, la réponse est gérée dans l'activité de demande.  Si le client est multithread asynchrone ou synchrone, `propagateActivity`\=`true` sur le client et qu'il y a un en\-tête d'ID d'activité dans le message envoyé par le serveur, le client récupère l'ID d'activité du message et le transfère à l'activité Traiter l'action qui contient l'ID d'activité propagé.  Autrement, le client effectue le transfert de l'activité Traiter le message à une nouvelle activité Traiter l'action.  Ce transfert supplémentaire vers une nouvelle activité Traiter l'action est effectué pour des raisons de cohérence.  À l'intérieur de cette activité, le client récupère l'ID d'activité de l'activité BeginCall à partir du contexte de thread local, lorsque le thread est alloué pour le traitement du message de réponse.  Il transfère ensuite l'ID à l'activité Traiter l'action initiale.  
  
 Si le client est duplex, il fait office de serveur lors de la réception du message.  
  
### Propagation dans les messages d'erreur  
 Il n'y a aucune différence entre la gestion des messages valides et celle des messages d'erreur.  Si `propagateActivity`\=`true`, l'ID d'activité ajouté aux en\-têtes de messages d'erreur SOAP est identique à l'activité ambiante.  
  
## Le suivi d'activité ServiceModel est désactivé  
 Si le suivi d'activité \(ActivityTracing\) ServiceModel est désactivé, la propagation se produit directement entre les activités de code utilisateur sans passer par les activités ServiceModel.  Un ID d'activité défini par l'utilisateur est également propagé par le biais de l'en\-tête d'ID d'activité de message.  
  
 Si `propagateActivity`\=`true` et que `ActivityTracing`\=`off` pour un écouteur de suivi ServiceModel \(que le suivi soit activé sur ServiceModel ou non\), les opérations suivantes ont lieu sur le client ou le serveur :  
  
-   Lors de la demande d'opération ou de l'envoi de réponse, l'ID d'activité dans TLS est propagé hors du code utilisateur jusqu'à ce qu'un message soit formé.  Un en\-tête d'ID d'activité est également inséré dans le message avant qu'il ne soit envoyé.  
  
-   Lors de la réception de la demande ou de la réponse, l'ID d'activité est récupéré à partir de l'en\-tête de message dès que l'objet de message reçu est créé.  L'ID d'activité dans TLS est propagé dès que le message disparaît de la portée, jusqu'à ce que le code utilisateur soit atteint.  
  
 Ces actions garantissent que les traces utilisateur apparaîtront dans la même activité si la propagation est activée.  Toutefois, aucune garantie n'est apportée concernant les traces ServiceModel.  Les traces ServiceModel se produisent dans une activité de code utilisateur seulement si le traitement de ces traces est exécuté sur le même thread que celui où l'activité de code utilisateur a été définie.  
  
 En général, les traces ServiceModel peuvent être observées aux emplacements suivants :  
  
-   Si le suivi ServiceModel est désactivé, tous les suivis émis apparaissent dans les activités utilisateur.  Si la propagation est activée sur le serveur et sur le client, ces traces seront dans la même activité.  
  
-   Si le suivi ServiceModel est activé mais que le suivi d'activité \(ActivityTracing\) est désactivé, les suivis utilisateur apparaissent dans la même activité si la propagation est activée aux deux extrémités.  Les traces ServiceModel apparaissent dans l'activité par défaut 0000, à moins qu'elles ne se produisent dans le même thread que le traitement de code utilisateur où l'activité est définie initialement.  
  
-   Si le suivi ServiceModel et le suivi d'activité \(ActivityTracing\) sont activés, les suivis utilisateur apparaissent dans les activités définies par l'utilisateur et les suivis ServiceModel apparaissent dans les activités définies par ServiceModel.  La propagation a lieu au niveau du ServiceModel.