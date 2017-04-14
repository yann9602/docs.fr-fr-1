---
title: "Sp&#233;cification du comportement du client au moment de l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comportements (WCF), fourni par le système client"
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Sp&#233;cification du comportement du client au moment de l&#39;ex&#233;cution
Les clients [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], comme les services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], peuvent être configurés pour modifier le comportement à l'exécution en fonction de l'application cliente. Trois attributs sont disponibles pour spécifier le comportement du client au moment de l'exécution. Les objets de rappel de client duplex peuvent utiliser le <xref:System.ServiceModel.CallbackBehaviorAttribute> et <xref:System.ServiceModel.Description.CallbackDebugBehavior> attributs pour modifier leur comportement au moment de l’exécution. L’autre attribut, <xref:System.ServiceModel.Description.ClientViaBehavior>, peut être utilisé pour séparer la destination logique à partir de la destination réseau immédiate. De plus, les types de rappel de client duplex peuvent utiliser certains des comportements du côté service. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Spécifier le comportement d’exécution Service](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Utilisation de CallbackBehaviorAttribute  
 Vous pouvez configurer ou étendre le comportement d’exécution d’une implémentation de contrat de rappel dans une application cliente à l’aide de la <xref:System.ServiceModel.CallbackBehaviorAttribute> classe. Cet attribut exécute une fonction similaire pour la classe de rappel du <xref:System.ServiceModel.ServiceBehaviorAttribute> (classe), à l’exception de l’instanciation des paramètres de comportement et de transaction.  
  
 Le <xref:System.ServiceModel.CallbackBehaviorAttribute> classe doit être appliquée à la classe qui implémente le contrat de rappel. S’applique à une implémentation de contrat non-duplex, une <xref:System.InvalidOperationException> exception est levée au moment de l’exécution. Ce qui suit montre l’exemple de code un <xref:System.ServiceModel.CallbackBehaviorAttribute> classe sur un objet de rappel qui utilise le <xref:System.Threading.SynchronizationContext> objet pour déterminer le thread à marshaler, la <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> pour appliquer la validation du message, propriété et la <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> pour retourner des exceptions en tant que propriété <xref:System.ServiceModel.FaultException> objets de service à des fins de débogage.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Utilisation de CallbackDebugBehavior pour activer le flux d'informations d'exceptions managées  
 Vous pouvez activer le flux des informations d’exception gérées dans un objet de rappel client au service pour le débogage en définissant le <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriété `true` par programme ou à partir de la configuration d’une application de fichiers.  
  
 Le retour d'informations sur les exceptions managées aux services peut constituer un problème de sécurité car les détails d'exception exposent des informations relatives à l'implémentation cliente interne que des services non autorisés pourraient utiliser. En outre, bien que le <xref:System.ServiceModel.Description.CallbackDebugBehavior> propriétés peuvent également être définies par programme, il est facile d’oublier de désactiver <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> lors du déploiement.  
  
 Étant donné les problèmes de sécurité impliqués, il est vivement recommandé :  
  
-   Un fichier de configuration vous permet de définir la valeur de la <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriété `true`.  
  
-   de ne procéder ainsi que dans des scénarios de débogage contrôlés.  
  
 L'exemple de code suivant illustre un fichier de configuration client qui fait en sorte que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] retourne des informations sur les exceptions managées à partir d'un objet de rappel client dans des messages SOAP.  
  
 [!code[SCA.CallbackContract#4](../../../samples/snippets/common/VS_Snippets_CFX/sca.callbackcontract/common/client.exe.config#4)]
 [!code-csharp[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]
 [!code-vb[SCA.CallbackContract#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.callbackcontract/vb/client.exe.config#4)]  
  
## <a name="using-the-clientviabehavior-behavior"></a>Utilisation du comportement ClientViaBehavior  
 Vous pouvez utiliser la <xref:System.ServiceModel.Description.ClientViaBehavior> comportement pour spécifier l’URI pour lequel le canal de transport doit être créé. Utilisez ce comportement lorsque la destination réseau immédiate n'est pas le processeur prévu du message. Cela autorise les conversations à sauts multiples lorsque l'application appelante ne connaît pas nécessairement la destination ultime ou lorsque l'en-tête `Via` de destination n'est pas une adresse.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier le comportement d’exécution de Service](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)