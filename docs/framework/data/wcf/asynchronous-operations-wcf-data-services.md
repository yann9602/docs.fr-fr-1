---
title: "Op&#233;rations asynchrones (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opérations asynchrones [WCF Data Services]"
  - "Services de données WCF, opérations asynchrones"
  - "Services de données WCF, bibliothèque cliente"
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Op&#233;rations asynchrones (WCF Data Services)
Les applications Web doivent gérer une latence plus élevée entre le client et le serveur, comparé aux applications qui s'exécutent sur des réseaux internes.  Pour optimiser la performance et l'expérience utilisateur de votre application, nous recommandons d'utiliser les méthodes asynchrones des classes <xref:System.Data.Services.Client.DataServiceQuery%601> et <xref:System.Data.Services.Client.DataServiceContext> lors de l'accès aux serveurs [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sur le Web.  
  
 Bien que les serveurs [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] traitent les requêtes HTTP de façon asynchrone, certaines méthodes des bibliothèques clientes [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] sont synchrones et attendent la fin de l'échange demande\-réponse avant de poursuivre l'exécution.  Les méthodes asynchrones des bibliothèques clientes [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] n'attendent pas la fin de cet échange et permettent que votre application maintienne une interface utilisateur réactive en même temps.  
  
 Vous pouvez effectuer des opérations asynchrones à l'aide d'une paire de méthodes sur les classes <xref:System.Data.Services.Client.DataServiceQuery%601> et <xref:System.Data.Services.Client.DataServiceContext> qui démarrent avec *Begin* et *End* respectivement.  Les méthodes *Begin* inscrivent un délégué appelé par le service lorsque l'opération est terminé.  Les méthodes *End* doivent être appelées dans le délégué inscrit pour gérer le rappel des opérations terminées.  Lorsque vous appelez la méthode *End* pour compléter une opération asynchrone, vous devez le faire de la même instance <xref:System.Data.Services.Client.DataServiceQuery%601> ou <xref:System.Data.Services.Client.DataServiceContext> utilisée pour commencer l'opération.  Chaque méthode *Begin* prend un paramètre `state` qui peut passer un objet d'état au rappel.  Cet objet d'état est récupéré de <xref:System.IAsyncResult> qui est fourni avec le rappel et permet d'appeler la méthode *End* correspondante pour compléter l'opération asynchrone.  Par exemple, lorsque vous fournissez l'instance <xref:System.Data.Services.Client.DataServiceQuery%601> comme paramètre `state` lorsque vous appelez la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> sur l'instance, la même instance <xref:System.Data.Services.Client.DataServiceQuery%601> est retournée par <xref:System.IAsyncResult>.  Puis cette instance de <xref:System.Data.Services.Client.DataServiceQuery%601> est utilisée pour appeler la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pour terminer l'opération de requête.  Pour plus d'informations, consultez [Procédure : exécuter des requêtes de service des données asynchrones](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Seules les opérations asynchrones sont prises en charge par les bibliothèques clientes fournies dans le .NET Framework pour Silverlight.  Pour plus d'informations, consultez [Services de données WCF \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Les bibliothèques clientes .NET Framework prennent en charge les opérations asynchrones suivantes :  
  
|Opération|Méthodes|  
|---------------|--------------|  
|Exécution d'un <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Exécution d'une requête du <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Exécution d'une requête par lot du <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Chargement d'une entité connexe dans <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Enregistrement des modifications apportées aux objets dans <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## Considérations sur le threading relatives aux opérations asynchrones  
 Dans une application multithread, le délégué inscrit comme un rappel pour l'opération asynchrone n'est pas nécessairement appelé sur le même thread utilisé pour appeler la méthode *Begin* qui crée la demande initiale.  Dans une application où le rappel doit être appelé sur un thread spécifique, vous devez marshaler explicitement l'exécution de la méthode *End*, qui gère la réponse, au thread souhaité.  Par exemple, dans les applications WPF \(Windows Presentation Foundation\) et Silverlight, la réponse doit être remarshalée au thread de l'interface utilisateur en utilisant la méthode <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> sur l'objet <xref:System.Windows.Threading.Dispatcher>.  Pour plus d'informations, consultez [Querying the Data Service \(WCF Data Services\/Silverlight\)](http://msdn.microsoft.com/fr-fr/3a7cdc07-c37e-4da2-b98b-c3763fd0970b).  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)