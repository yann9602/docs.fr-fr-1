---
title: "Acc&#232;s aux services &#224; l&#39;aide d&#39;un client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Acc&#232;s aux services &#224; l&#39;aide d&#39;un client
Les applications clientes doivent créer, configurer et utiliser des objets [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de canal ou de client afin de communiquer avec des services.  La rubrique [Vue d'ensemble d'un client WCF](../../../../docs/framework/wcf/wcf-client-overview.md) fournit une vue d'ensemble des objets et des étapes nécessaires pour créer des objets de client et de canal de base, ainsi que des informations sur leur utilisation.  
  
 Cette rubrique fournit des informations détaillées sur certains aspects liés aux applications clientes et aux objets de client et de canal qui peuvent être utiles selon votre scénario.  
  
## Vue d'ensemble  
 Cette rubrique décrit le comportement et les problèmes liés aux éléments suivants :  
  
-   durées de vie de session et de canal ;  
  
-   gestion des exceptions ;  
  
-   présentation des problèmes de blocage ;  
  
-   initialisation de canaux de manière interactive.  
  
### Durées de vie de session et de canal  
 Les applications [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] incluent deux catégories de canaux : les canaux de datagramme et les canaux de session.  
  
 Un canal *de datagramme* est un canal dans lequel tous les messages sont sans corrélation.  Avec un canal de datagramme, si une opération d'entrée ou de sortie échoue, l'opération suivante n'est en général pas affectée et le même canal peut être réutilisé.  Pour cette raison, les canaux de datagramme ne subissent généralement pas de défaillance.  
  
 Les canaux *de session*, en revanche, sont des canaux avec une connexion à l'autre point de terminaison.  Les messages dans une session d'un côté sont toujours en corrélation avec la même session de l'autre côté.  De plus, les deux participants d'une session doivent s'entendre sur le fait que les spécifications de leur conversation ont été satisfaites pour que cette session soit considérée comme réussie.  S'ils ne peuvent se mettre d'accord, le canal de session peut subir une défaillance.  
  
 Ouvrir des clients explicitement ou implicitement en appelant la première opération.  
  
> [!NOTE]
>  Le fait de tenter de détecter de manière explicite des canaux de session défaillants est en général inutile, car le moment où vous en êtes informé dépend de l'implémentation de session.  Par exemple, étant donné que le <xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName> \(avec la session fiable désactivée\) est à la surface de la session de la connexion TCP, si vous écoutez l'événement <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=fullName> sur le service ou le client, vous recevrez sans doute rapidement une notification en cas de panne réseau.  Mais les sessions fiables \(établies par des liaisons dans lesquelles le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=fullName> est activé\) sont conçues pour isoler les services des petites pannes réseau.  Si la session peut être rétablie dans un délai raisonnable, la même liaison \(configuré pour des sessions fiables\) risque de ne subir une défaillance que longtemps après l'interruption.  
  
 La plupart des liaisons fournies par le système \(qui exposent des canaux à la couche Application\) utilisent des sessions par défaut, ce qui n'est pas le cas du <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Utilisation de sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
### Utilisation correcte des sessions  
 Les sessions offrent un moyen de savoir si l'intégralité de l'échange de messages a été effectué et si les deux côtés l'ont considéré réussi.  Il est recommandé qu'une application appelante ouvre le canal, l'utilise et le ferme à l'intérieur d'un bloc try.  Si un canal de session est ouvert, que la méthode <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=fullName> est appelée une fois et que cet appel est retourné avec succès, cela signifie que la session a réussi.  Le terme « réussi » dans ce cas signifie que toutes les garanties de remise spécifiées par la liaison ont été satisfaites et que l'autre côté n'a pas appelé <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=fullName> sur le canal avant d'appeler <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 La section suivante fournit un exemple de cette approche cliente.  
  
### Gestion des exceptions  
 La gestion des exceptions dans les applications clientes est simple.  Si un canal est ouvert, utilisé et fermé à l'intérieur d'un bloc try, cela signifie que la conversation a réussi, à moins qu'une exception ne soit levée.  En général, si une exception est levée, la conversation est abandonnée.  
  
> [!NOTE]
>  L'utilisation de l'instruction `using` \(`Using` dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\) n'est pas recommandée.  Cela est dû au fait que la fin de l'instruction `using` peut provoquer des exceptions qui peuvent masquer d'autres exceptions dont vous devez avoir connaissance.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Avoiding Problems with the Using Statement](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 L'exemple de code suivant illustre le modèle client recommandé à l'aide d'un bloc try\/catch, et non de l'instruction `using`.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  La vérification de la valeur de la propriété <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=fullName> est une condition de concurrence et n'est pas recommandée pour déterminer s'il faut réutiliser ou fermer un canal.  
  
 Les canaux de datagramme ne subissent jamais de défaillance, même si des exceptions se produisent lorsqu'ils sont fermés.  De plus, les clients non\-duplex qui ne parviennent pas à s'authentifier à l'aide d'une conversation sécurisée lèvent en général une exception <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName>.  Toutefois, si le client duplex qui utilise une conversation sécurisée ne parvient pas à s'authentifier, il reçoit une exception <xref:System.TimeoutException?displayProperty=fullName>.  
  
 Pour obtenir des informations plus complètes sur l'utilisation des informations d'erreur au niveau application, consultez [Spécification et gestion des erreurs dans les contrats et les services](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) décrit les exceptions attendues et montre comment les gérer.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la façon de gérer les erreurs lors du développement de canaux, consultez [Gestion des exceptions et des erreurs](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### Blocage de client et performances  
 Lorsqu'une application appelle une opération demande\-réponse de façon synchrone, le client se bloque jusqu'à ce qu'une valeur de retour soit reçue ou qu'une exception \(par exemple <xref:System.TimeoutException?displayProperty=fullName>\) soit levée.  Ce comportement est semblable au comportement local.  Lorsqu'une application appelle de façon synchrone une opération sur un objet de client ou de canal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le client n'est retourné que lorsque la couche de canal peut écrire les données sur le réseau ou lorsqu'une exception est levée.  Et bien que le modèle d'échange de messages unidirectionnel \(spécifié en marquant une opération avec <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=fullName> défini à `true`\) puisse améliorer la capacité de réponse de certains clients, les opérations unidirectionnelles peuvent également subir un blocage, en fonction de la liaison et des messages qui ont déjà été envoyés.  Les opérations unidirectionnelles concernent uniquement l'échange de messages, ni plus ni moins.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Services monodirectionnels](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Les grands segments de données peuvent ralentir le traitement client, quel que soit le modèle d'échange de messages.  Pour comprendre comment gérer ces problèmes, consultez [Données volumineuses et diffusion en continu](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Si votre application doit effectuer davantage de travail pendant qu'une opération se termine, vous devez créer une paire de méthodes asynchrones sur l'interface de contrat de service que votre client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente.  La solution la plus simple consiste à utiliser le commutateur `/async` sur le [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  Pour obtenir un exemple, consultez [Comment : appeler des opérations de service de façon asynchrone](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'augmentation des performances des clients, consultez [Applications clientes de niveau intermédiaire](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### Autoriser l'utilisateur à sélectionner des informations d'identification de manière dynamique  
 L'interface <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> permet aux applications d'afficher une interface utilisateur qui permet à l'utilisateur de choisir des informations d'identification avec lesquelles un canal est créé avant le démarrage des minuteries de délai d'attente.  
  
 Les développeurs d'applications peuvent utiliser un <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> inséré de deux façons.  L'application cliente peut appeler <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(ou une version asynchrone\) avant d'ouvrir le canal \(approche *explicite*\) ou appeler la première opération \(approche *implicite*\).  
  
 Lors de l'utilisation de l'approche implicite, l'application doit appeler la première opération sur une extension <xref:System.ServiceModel.ClientBase%601> ou <xref:System.ServiceModel.IClientChannel>.  Si elle appelle une autre opération que la première, une exception est levée.  
  
 Lors de l'utilisation de l'approche explicite, l'application doit exécuter les étapes suivantes, dans l'ordre :  
  
1.  Appelez <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(ou une version asynchrone\).  
  
2.  Lorsque les initialiseurs ont retourné, appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur l'objet <xref:System.ServiceModel.IClientChannel> ou sur l'objet <xref:System.ServiceModel.IClientChannel> retourné par la propriété <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=fullName>.  
  
3.  Appelez les opérations.  
  
 Il est recommandé que les applications de qualité de production contrôlent le processus d'interface utilisateur en adoptant l'approche explicite.  
  
 Les applications qui utilisent l'approche implicite appellent les initialiseurs d'interface utilisateur, mais si l'utilisateur de l'application ne répond pas avant la fin du délai d'attente d'envoi de la liaison, une exception est levée lorsque l'interface utilisateur retourne.  
  
## Voir aussi  
 [Services duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)   
 [Comment : accéder aux services avec des contrats unidirectionnels et demande\-réponse](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)   
 [Comment : accéder aux services ayant un contrat duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [Comment : accéder à un service WSE 3.0](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)   
 [Comment : utiliser la classe ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)   
 [Comment : appeler des opérations de service de façon asynchrone](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)   
 [Applications clientes de niveau intermédiaire](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)