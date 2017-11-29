---
title: "Comment : héberger un service WCF dans une application managée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca834c097f7e8cea14337fece651b2b3059d06b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a>Comment : héberger un service WCF dans une application managée
Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.  
  
 Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>. De cette manière, vous créez et ouvrez l'écouteur pour le service. L'hébergement d'un service selon cette méthode est souvent appelé « auto-hébergement » parce que l'application managée effectue le travail d'hébergement elle-même. Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost>.  
  
 Un service peut également être hébergé dans un service Windows managé, dans le service IIS (Internet Information Services), ou le service WAS (Windows Process Activation Service). [!INCLUDE[crabout](../../../includes/crabout-md.md)]options pour un service d’hébergement, consultez [Services d’hébergement](../../../docs/framework/wcf/hosting-services.md).  
  
 L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure. [!INCLUDE[crabout](../../../includes/crabout-md.md)]hébergement des services dans les applications managées, consultez [hébergement dans une Application gérée](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).  
  
 La procédure suivante montre comment implémenter un service auto-hébergé dans une application console.  
  
### <a name="to-create-a-self-hosted-service"></a>Pour créer un service auto-hébergé  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **nouveau**, **projet...**  à partir de la **fichier** menu.  
  
2.  Dans le **modèles installés** liste, sélectionnez **Visual C#**, **Windows** ou **Visual Basic**, **Windows**. Selon votre [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] paramètres, une ou deux de ces peut se trouver sous le **autres langages** nœud dans le **modèles installés** liste.  
  
3.  Sélectionnez **Application Console** à partir de la **Windows** liste. Type `SelfHost` dans les **nom** , puis cliquez sur **OK**.  
  
4.  Avec le bouton droit **SelfHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** . Sélectionnez **System.ServiceModel** à partir de la **.NET** onglet et cliquez sur **OK**.  
  
    > [!TIP]
    >  Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.  
  
5.  Double-cliquez sur **Program.cs** ou **Module1.vb** dans **l’Explorateur de solutions** pour l’ouvrir dans la fenêtre de code s’il n’est pas déjà ouvert. En tête du fichier, ajoutez les instructions suivantes :  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  Définissez et implémentez un contrat de service. Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]comment définir et implémenter une interface de service, consultez [Comment : définir un contrat de Service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) et [Comment : implémenter un contrat de Service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).  
  
7.  En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base (Uniform Resource Identifier) à <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>. Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service. Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service. [!INCLUDE[crabout](../../../includes/crabout-md.md)]par défaut des points de terminaison, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
9. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
### <a name="to-test-the-service"></a>Pour tester le service  
  
1.  Appuyez sur Ctrl+F5 pour exécuter le service.  
  
2.  Ouvrez **Client Test WCF**.  
  
    > [!TIP]
    >  Pour ouvrir **Client Test WCF**, ouvrez un [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] invite de commandes et exécutez **WcfTestClient.exe**.  
  
3.  Sélectionnez **ajouter Service...**  à partir de la **fichier** menu.  
  
4.  Type `http://localhost:8080/hello` dans la zone d’adresse et cliquez sur **OK**.  
  
    > [!TIP]
    >  Assurez-vous que le service est en cours d'exécution, sinon cette étape échouera. Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.  
  
5.  Double-cliquez sur **SayHello** sous le **Mes projets de Service** nœud. Tapez votre nom dans la **valeur** colonne dans la **demande** liste, puis cliquez sur **Invoke**. Un message de réponse s’affiche dans le **réponse** liste.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>. Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [L’auto-hébergement](../../../docs/framework/wcf/samples/self-host.md)  
 [Hébergement de services](../../../docs/framework/wcf/hosting-services.md)  
 [Guide pratique pour définir un contrat de service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Guide pratique pour implémenter un contrat de service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md)
