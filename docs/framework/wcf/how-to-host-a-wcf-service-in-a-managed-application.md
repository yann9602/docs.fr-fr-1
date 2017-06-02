---
title: "Comment&#160;: h&#233;berger un service WCF dans une application manag&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: 42
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 42
---
# Comment&#160;: h&#233;berger un service WCF dans une application manag&#233;e
Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.  
  
 Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>.De cette manière, vous créez et ouvrez l'écouteur pour le service.L'hébergement d'un service selon cette méthode est souvent appelé « auto\-hébergement » parce que l'application managée effectue le travail d'hébergement elle\-même.Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=fullName> sur <xref:System.ServiceModel.ServiceHost>.  
  
 Un service peut également être hébergé dans un service Windows managé, dans le service IIS \(Internet Information Services\), ou le service WAS \(Windows Process Activation Service\).[!INCLUDE[crabout](../../../includes/crabout-md.md)] les options d'hébergement pour un service, consultez [Hébergement de services](../../../docs/framework/wcf/hosting-services.md).  
  
 L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les services d'hébergement dans les applications managées, consultez [Hébergement dans une application managée](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 La procédure suivante montre comment implémenter un service auto\-hébergé dans une application console.  
  
### Pour créer un service auto\-hébergé  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**.  
  
2.  Dans la liste **Modèles installés**, sélectionnez **Visual C\#**, **Windows** ou **Visual Basic**, **Windows**.Selon les paramètres [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] que vous avez définis, l'une ou les deux options peuvent figurer sous le nœud **Autres langages** dans la liste **Modèles installés**.  
  
3.  Dans la liste **Windows**, sélectionnez **Application console**.Dans la zone **Nom**, tapez `SelfHost` et cliquez sur **OK**.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **SelfHost** et sélectionnez **Ajouter une référence**.Sous l'onglet **.NET**, sélectionnez **System.ServiceModel** et cliquez sur **OK**.  
  
    > [!TIP]
    >  Si la fenêtre **Explorateur de solutions** n'est pas visible, dans le menu **Affichage**, choisissez **Explorateur de solutions**.  
  
5.  Double\-cliquez sur **Program.cs** ou sur **Module1.vb** dans l'**Explorateur de solutions** pour l'ouvrir dans la fenêtre de code, si ce n'est pas encore le cas.En tête du fichier, ajoutez les instructions suivantes :  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Définissez et implémentez un contrat de service.Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)] la procédure de définition et d'implémentation d'une interface de service, consultez [Comment : définir un contrat de service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) et [Comment : implémenter un contrat de service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base \(Uniform Resource Identifier\) à [ServiceHost\(Type, Uri\<xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     <!-- TODO: review snippet reference [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]  -->  
  
    > [!NOTE]
    >  Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service.Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service.[!INCLUDE[crabout](../../../includes/crabout-md.md)] les points de terminaison par défaut, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Appuyez sur Ctrl\+Maj\+B pour générer la solution.  
  
### Pour tester le service  
  
1.  Appuyez sur Ctrl\+F5 pour exécuter le service.  
  
2.  Ouvrez **Client test WCF**.  
  
    > [!TIP]
    >  Pour ouvrir **Client test WCF**, ouvrez une invite de commandes [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et exécutez **WcfTestClient.exe**.  
  
3.  Dans le menu **Fichier**, sélectionnez **Ajouter un service**.  
  
4.  Tapez `http://localhost:8080/hello` dans la zone d'adresse et cliquez sur **OK**.  
  
    > [!TIP]
    >  Assurez\-vous que le service est en cours d'exécution, sinon cette étape échouera.Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.  
  
5.  Double\-cliquez sur **SayHello** sous le nœud **Mes projets de service**.Tapez votre nom dans la colonne **Valeur** dans la liste **Requête**, puis cliquez sur **Appeler**.Un message de réponse apparaît dans la liste **Réponse**.  
  
## Exemple  
 L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>.Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## Voir aussi  
 <xref:System.Uri>   
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>   
 <xref:System.Configuration.ConfigurationManager>   
 [Comment : héberger un service WCF dans IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)   
 [Self\-Host](../../../docs/framework/wcf/samples/self-host.md)   
 [Hébergement de services](../../../docs/framework/wcf/hosting-services.md)   
 [Comment : définir un contrat de service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)   
 [Comment : implémenter un contrat de service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)   
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md)