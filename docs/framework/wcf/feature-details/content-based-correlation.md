---
title: "Corrélation basée sur le contenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dda6e063744b8a745c5f4be576344ff2823de267
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="content-based-correlation"></a>Corrélation basée sur le contenu
Lorsque les services de workflow communiquent avec des clients et d'autres services, il existe souvent des données dans les messages échangés qui servent uniquement à lier un message à une instance particulière. La corrélation basée sur le contenu utilise ces données dans les messages, par exemple un numéro de client ou un ID de commande, pour router les messages vers l'instance de workflow appropriée. Cette rubrique explique comment utiliser la corrélation basée sur le contenu dans les workflows.  
  
## <a name="using-content-based-correlation"></a>Utilisation de la corrélation basée sur le contenu  
 La corrélation basée sur le contenu est utilisée lorsqu'un service de workflow possède plusieurs méthodes accessibles par un client unique et dispose de quelques données dans les messages échangés qui identifient l'instance souhaitée.  
  
> [!NOTE]
>  La corrélation basée sur le contenu est utile lorsque la corrélation de contexte ne peut pas être utilisée parce que la liaison ne fait pas partie des liaisons d’échange de contexte compatibles. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]corrélation de contexte, consultez [échange de contexte](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
 Chaque activité de messagerie utilisée dans ce type de communication doit spécifier à quel emplacement dans le message se trouvent les données identifiant l'instance de manière unique. Cela s'effectue en fournissant un objet <xref:System.ServiceModel.MessageQuerySet>, utilisant un objet <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> ou une propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, qui recherche dans le message les données identifiant l'instance de manière unique.  
  
> [!WARNING]
>  Les données utilisées pour identifier l'instance sont hachées en une clé de corrélation. Il est important de s'assurer que les données utilisées pour la corrélation sont uniques, pour éviter que des conflits se produisent dans la clé hachée, entraînant des confusions dans le routage des messages. Par exemple, une corrélation basée uniquement sur un nom de client risque de provoquer un conflit, au cas où d'autres clients aient un nom identique. Les deux-points (`:`) ne doivent pas être utilisés à l'intérieur des données qui servent à mettre les messages en corrélation. En effet, ils servent déjà à délimiter la clé et la valeur de la requête de message pour former la chaîne qui est ensuite hachée.  
  
 Dans l’exemple suivant, la première <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> dans un service de workflow retourne un `OrderId`, qui est ensuite transmis par le client sur l’appel à ce qui suit <xref:System.ServiceModel.Activities.Receive> activité dans le service de workflow.  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 L'exemple précédent montre une corrélation basée sur le contenu initialisée par l'activité <xref:System.ServiceModel.Activities.SendReply>. L'objet <xref:System.ServiceModel.MessageQuerySet> spécifie que les données utilisées pour identifier les prochains messages vers ce service correspondent à `OrderId`.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 L'activité <xref:System.ServiceModel.Activities.Receive> qui succède à l'activité <xref:System.ServiceModel.Activities.SendReply> dans le workflow respecte la corrélation initialisée par l'activité <xref:System.ServiceModel.Activities.SendReply>. Les deux activités partagent le même <xref:System.ServiceModel.Activities.CorrelationHandle>, mais chacune possède son propre <xref:System.ServiceModel.MessageQuerySet> et son propre <xref:System.ServiceModel.XPathMessageQuery> qui spécifie où se trouvent les données d'identification dans ce message particulier. Pour l'activité qui initialise la corrélation, ce <xref:System.ServiceModel.MessageQuerySet> est spécifié dans la propriété <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>, et pour toutes les activités <xref:System.ServiceModel.Activities.Receive> qui lui succèdent, il est spécifié à l'aide de la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Une corrélation basée sur le contenu peut être initialisée par n'importe quelle activité de messagerie (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply>) lorsque les données circulent dans le cadre d'un message. Si ces données particulières ne circulent pas dans le cadre d'un message, la corrélation peut alors être initialisée de manière explicite à l'aide de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. Si plusieurs fragments de données sont nécessaires pour identifier le message de manière unique, plusieurs requêtes peuvent être ajoutées au <xref:System.ServiceModel.MessageQuerySet>. Dans ces exemples, un objet <xref:System.ServiceModel.Activities.CorrelationHandle> a été fourni de manière explicite à chacune des activités à l'aide des propriétés `CorrelatesWith` ou `CorrelationHandle`, mais si une seule corrélation est nécessaire pour l'intégralité du workflow, comme dans cet exemple où tout est mis en corrélation en fonction d'`OrderId`, la gestion de handle de corrélation implicite fournie par <xref:System.ServiceModel.Activities.WorkflowServiceHost> suffit.  
  
## <a name="using-the-initializecorrelation-activity"></a>Utilisation de l'activité InitializeCorrelation  
 Dans l'exemple précédent, l'`OrderId` était transmis à l'appelant via l'activité <xref:System.ServiceModel.Activities.SendReply>, celle qui a initialisé la corrélation. Le même comportement peut être obtenu à l'aide de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. L'activité <xref:System.ServiceModel.Activities.InitializeCorrelation> prend le <xref:System.ServiceModel.Activities.CorrelationHandle> et un dictionnaire d'éléments qui représentent les données utilisées pour mapper le message à l'instance correcte. Pour utiliser l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation> dans l'exemple précédent, supprimez la propriété <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> de l'activité <xref:System.ServiceModel.Activities.SendReply> et initialisez la corrélation à l'aide de l'activité <xref:System.ServiceModel.Activities.InitializeCorrelation>.  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 L'activité <xref:System.ServiceModel.Activities.InitializeCorrelation> est alors utilisée dans le workflow, une fois remplies les variables qui contiennent les données, mais avant l'activité <xref:System.ServiceModel.Activities.Receive> qui se met en corrélation avec l'objet <xref:System.ServiceModel.Activities.CorrelationHandle> initialisé.  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>Configuration de requêtes XPath à l'aide du Workflow Designer  
 Dans les exemples précédents, les activités et les requêtes XPath utilisées dans les requêtes de message ont été spécifiées dans le code. Le Workflow Designer de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] fournit également la possibilité de générer des XPaths à partir de types `DataContract` pour la corrélation basée sur le contenu. Le premier XPath configuré dans l'exemple précédent a été configuré pour l'activité <xref:System.ServiceModel.Activities.SendReply>.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 Sélectionnez l’activité de messagerie pour laquelle vous souhaitez configurer le XPath dans le Workflow Designer. Si l’activité initialise la corrélation, comme dans l’exemple précédent, cliquez sur le bouton de sélection pour la **CorrelationInitializers** propriété dans le **propriétés** fenêtre. Cela permet d’afficher le **ajouter des initialiseurs de corrélation** boîte de dialogue. Dans cette fenêtre, vous pouvez spécifier le type de corrélation et sélectionner le contenu utilisé pour la corrélation. Le <xref:System.ServiceModel.Activities.CorrelationHandle> la variable est spécifiée dans le **ajouter initialiseur** boîte, le type de corrélation et les données utilisées pour la corrélation est sélectionné à partir de la **requêtes XPath** section de la boîte de dialogue.  
  
 ![Boîte de dialogue CorrelationInitializer](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 La deuxième requête XPath de l'exemple précédent a été configurée dans l'activité <xref:System.ServiceModel.Activities.Receive>.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Pour configurer la requête XPath pour une activité de messagerie qui n’initialise pas la corrélation, sélectionnez l’activité dans le Concepteur de flux de travail, puis cliquez sur le bouton de sélection pour la **CorrelatesOn** propriété dans le  **Propriétés** fenêtre. Cela permet d’afficher le **définition CorrelatesOn** boîte de dialogue.  
  
 ![Définition de CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 Dans cette boîte de dialogue, spécifiez la <xref:System.ServiceModel.Activities.CorrelationHandle> et choisissez des éléments dans le **requêtes XPath** liste pour générer la requête XPath.
