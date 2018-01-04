---
title: Extension de clients
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2444488418b7647111cf4b89db0c41a8e66470d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-clients"></a>Extension de clients
Dans une application appelante, la couche de modèle de service est chargée de traduire les appels de méthode du code d'application en messages sortants, de les envoyer vers les canaux sous-jacents, de retraduire les résultats en valeurs de retour et paramètres de sortie dans le code d'application, et de retourner de nouveau les résultats à l'appelant. Les extensions de modèle de service modifient ou implémentent le comportement et les fonctionnalités d’exécution ou de communication qui impliquent des fonctionnalités de répartiteur ou client, des comportements personnalisés, l’interception de messages et de paramètres, ainsi que d’autres fonctionnalités d’extensibilité.  
  
 Cette rubrique décrit comment utiliser les classes <xref:System.ServiceModel.Dispatcher.ClientRuntime> et <xref:System.ServiceModel.Dispatcher.ClientOperation> dans une application cliente [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] afin de modifier le comportement d'exécution par défaut d'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou d'intercepter ou de modifier des messages, paramètres ou valeurs de retour avant ou à la suite de leur envoi ou de leur récupération dans la couche du canal. Pour plus d’informations sur l’extension de l’exécution du service, consultez [extension des répartiteurs](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Pour plus d’informations sur les comportements qui modifient et insérer des objets de personnalisation dans l’exécution du client, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Clients  
 Sur un client, un canal ou objet client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] convertit des appels de méthode en messages sortants et messages entrants aux résultats de l'opération retournés à l'application appelante. (Pour plus d’informations sur les types de clients, consultez [Architecture de Client WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 Les types de clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ont des types d'exécution qui gèrent ce point de terminaison, et les fonctionnalités au niveau de l'opération. Lorsqu'une application appelle une opération, <xref:System.ServiceModel.Dispatcher.ClientOperation> traduit les objets sortants en message, traite des intercepteurs, confirme que l'appel sortant est conforme au contrat cible, et transmet le message sortant à <xref:System.ServiceModel.Dispatcher.ClientRuntime>, qui est chargé de créer et de gérer des canaux sortants (et canaux entrants dans le cas de services duplex), de gérer le traitement des messages sortants supplémentaires (tel que la modification de l'en-tête), de traiter des intercepteurs de message dans les deux directions, et de router des appels duplex entrants vers l'objet <xref:System.ServiceModel.Dispatcher.DispatchRuntime> côté client approprié. <xref:System.ServiceModel.Dispatcher.ClientOperation> et <xref:System.ServiceModel.Dispatcher.ClientRuntime> fournissent tous deux des services similaires lorsque les messages (y compris les erreurs) sont retournés au client.  
  
 Ces deux classes d'exécution constituent l'extension principale permettant de personnaliser le traitement des canaux et objets client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. La classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> permet aux utilisateurs d'intercepter et d'étendre l'exécution du client sur l'ensemble des messages du contrat. La classe <xref:System.ServiceModel.Dispatcher.ClientOperation> permet aux utilisateurs d'intercepter et d'étendre l'exécution du client pour tous les messages d'une opération donnée.  
  
 La modification des propriétés ou l'insertion de personnalisations sont effectuées en utilisant des comportements de contrat, de point de terminaison et d'opération. Pour plus d’informations sur l’utilisation de ces types de comportements pour effectuer des personnalisations de runtime de client, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scénarios  
 L'extension du système client peut être justifiée pour un certain nombre de raisons, dont les suivantes :  
  
-   Validation personnalisée des messages. Un utilisateur souhaite s'assurer qu'un message est valide pour un schéma spécifique. Cela peut être accompli en implémentant l'interface <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> et en assignant l'implémentation à la propriété <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>. Pour obtenir des exemples, consultez [Comment : inspecter ou modifier des Messages sur le Client](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) et [Comment : inspecter ou modifier des Messages sur le Client](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Enregistrement personnalisé des messages. Un utilisateur souhaite inspecter et enregistrer des jeux de messages d'application qui transitent par un point de terminaison. Cela peut également être accompli à l'aide des interfaces de l'intercepteur de messages.  
  
-   Transformations personnalisées des messages. Plutôt que de modifier le code d'application, l'utilisateur souhaite appliquer certaines transformations au message dans l'exécution (pour le contrôle de version par exemple). Cela peut, à nouveau, être accompli à l'aide des interfaces de l'intercepteur de messages.  
  
-   Modèle personnalisé de données. Un utilisateur souhaite disposer d'un modèle de données ou de sérialisation autre que ceux pris en charge par défaut dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (à savoir, les objets <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> et <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>). Cela peut être accompli en implémentant les interfaces du formateur de messages. Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> et la propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType>.  
  
-   Validation personnalisée des paramètres. Un utilisateur souhaite que les paramètres typés soient valides (par opposition à XML). Cela peut être accompli à l'aide des interfaces de l'inspecteur de paramètres. Pour obtenir un exemple, consultez [Comment : inspecter ou modifier les paramètres](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) ou [validation côté Client](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Utilisation de la classe ClientRuntime  
 La classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> est un point d'extensibilité auquel vous pouvez ajouter des objets d'extension qui interceptent des messages et étendent le comportement du client. Les objets d'interception peuvent traiter tous les messages d'un contrat spécifique, traiter uniquement les messages de certaines opérations, exécuter l'initialisation de canal personnalisée et implémenter un autre comportement d'application cliente personnalisé.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> retourne l'objet d'exécution de répartition pour les clients de rappel initiés par le service.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> accepte un objet de sélecteur d'opération personnalisé.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> permet d'ajouter un initialiseur de canal qui peut inspecter ou modifier le canal client.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> obtient une collection d'objets <xref:System.ServiceModel.Dispatcher.ClientOperation> auxquels vous pouvez ajouter des intercepteurs de messages personnalisés qui fournissent les fonctionnalités spécifiques aux messages de cette opération.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> permet à une application de désactiver certains en-têtes d'adressage automatique afin de contrôler directement l'adressage.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> affecte la valeur de la destination du message au niveau du transport afin de prendre en charge les intermédiaires et d'autres scénarios.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> obtient une collection d'objets <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> auxquels vous pouvez ajouter des intercepteurs de messages personnalisés pour l'ensemble des messages transitant via un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Par ailleurs, un certain nombre d'autres propriétés récupèrent les informations de contrat :  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Si le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] duplex, les propriétés suivantes récupèrent également les informations client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de rappel :  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Pour étendre l'exécution de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur l'ensemble d'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez les propriétés disponibles sur la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> afin de déterminer si la modification d'une propriété ou l'implémentation d'une interface et l'ajout de celle-ci à une propriété crée les fonctionnalités que vous recherchez. Après avoir choisi l'extension spécifique à générer, insérez-la dans la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime> appropriée en implémentant un comportement client permettant d'accéder à la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime> en cas d'appel.  
  
 Vous pouvez insérer des objets d'extension personnalisés dans une collection à l'aide d'un comportement d'opération (objet qui implémente <xref:System.ServiceModel.Description.IOperationBehavior>), d'un comportement de contrat (objet qui implémente <xref:System.ServiceModel.Description.IContractBehavior>) ou d'un comportement de point de terminaison (objet qui implémente <xref:System.ServiceModel.Description.IEndpointBehavior>). L'objet de comportement installé est ajouté à la collection appropriée de comportements par programme ou de façon déclarative (en implémentant un attribut personnalisé), ou en implémentant un objet <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> personnalisé pour que le comportement soit inséré à l'aide d'un fichier de configuration d'application. Pour plus d’informations, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Pour obtenir des exemples qui illustrent l’interception entre un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez [Comment : inspecter ou modifier des Messages sur le Client](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Utilisation de la classe ClientOperation  
 La classe <xref:System.ServiceModel.Dispatcher.ClientOperation> correspond à l'emplacement des modifications d'exécution du client et au point d'insertion des extensions personnalisées qui sont limitées à une seule opération de service. (Pour modifier le comportement d'exécution du client pour tous les messages d'un contrat, utilisez la classe <xref:System.ServiceModel.Dispatcher.ClientRuntime>.)  
  
 Utilisez la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> pour localiser l'objet <xref:System.ServiceModel.Dispatcher.ClientOperation> qui représente une opération de service particulière. Les propriétés suivantes vous permettent d'insérer des objets personnalisés dans le système client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> permet d'insérer une implémentation <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> personnalisée pour une opération ou de modifier le formateur actuel.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> permet d'insérer une implémentation <xref:System.ServiceModel.Dispatcher.IParameterInspector> personnalisée ou de modifier l'implémentation actuelle.  
  
 Les propriétés suivantes vous permettent de modifier le système dans l'interaction à l'aide du formateur et des inspecteurs de paramètre personnalisés :  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> permet de contrôler la sérialisation d'un message sortant.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> permet de contrôler la désérialisation d'un message entrant.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> permet de contrôler l'action WS-Addressing du message de demande.  
  
-   Les propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> et <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> permettent de spécifier les méthodes clientes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associées à une opération asynchrone.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> permet d'obtenir une collection contenant les types qui peuvent apparaître dans les erreurs SOAP comme type de détail.  
  
-   Les propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> et <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> permettent respectivement de contrôler si une session est initiée ou détruite, lorsque l'opération est appelée.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> permet de contrôler si l'opération est monodirectionnelle.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> permet d'obtenir l'objet contenant <xref:System.ServiceModel.Dispatcher.ClientRuntime>.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> permet d'obtenir le nom de l'opération.  
  
-   La propriété <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> permet de contrôler la méthode mappée à l'opération.  
  
 Pour étendre l'exécution de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur une seule opération de service, consultez les propriétés disponibles sur la classe <xref:System.ServiceModel.Dispatcher.ClientOperation> afin de déterminer si la modification d'une propriété ou l'implémentation d'une interface et l'ajout de celle-ci à une propriété crée les fonctionnalités que vous recherchez. Après avoir choisi l'extension spécifique à générer, insérez-la dans la propriété <xref:System.ServiceModel.Dispatcher.ClientOperation> appropriée en implémentant un comportement client permettant d'accéder à la classe <xref:System.ServiceModel.Dispatcher.ClientOperation> en cas d'appel. Dans ce comportement, vous pouvez ensuite modifier la propriété <xref:System.ServiceModel.Dispatcher.ClientRuntime> en fonction de vos besoins.  
  
 En général, l'implémentation d'un comportement d'opération (objet qui implémente l'interface <xref:System.ServiceModel.Description.IOperationBehavior> ) suffit, mais vous pouvez également utiliser des comportements de point de terminaison et de contrat en localisant le <xref:System.ServiceModel.Description.OperationDescription> d'une opération spécifique et en joignant le comportement à cet emplacement. Pour plus d’informations, consultez [configuration et l’extension de l’exécution des comportements](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Pour utiliser votre comportement personnalisé à partir de la configuration, installez-le à l'aide d'un gestionnaire de section de configuration de comportement personnalisé. Vous pouvez également l'installer en créant un attribut personnalisé.  
  
 Pour obtenir des exemples qui illustrent l’interception entre un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez [Comment : inspecter ou modifier les paramètres](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime>  
 <xref:System.ServiceModel.Dispatcher.ClientOperation>  
 [Guide pratique pour inspecter ou modifier des messages sur le client](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)  
 [Guide pratique pour inspecter ou modifier des paramètres](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
