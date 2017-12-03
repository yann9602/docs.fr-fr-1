---
title: "Comment : accéder aux services ayant un contrat duplex"
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
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ec8b7f37dc7f04a7ddb2c6373b50e98fe41cf98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>Comment : accéder aux services ayant un contrat duplex
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispose d'une fonctionnalité qui permet de créer un service utilisant un modèle de messagerie duplex. Ce modèle permet à un service de communiquer avec un client via un rappel. Cette rubrique contient la procédure permettant de créer un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une classe client qui implémente une interface de rappel.  
  
 Une liaison double expose l'adresse IP du client au service. Ce client doit utiliser un mode de sécurité afin de garantir sa connexion à un service fiable.  
  
 Pour obtenir un didacticiel sur la création d’un base [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service et le client, consultez [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).  
  
### <a name="to-access-a-duplex-service"></a>Pour accéder à un service duplex  
  
1.  Créez un service qui contient deux interfaces. La première interface est pour le service, la deuxième est pour le rappel. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Création d’un service duplex, consultez [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
2.  Exécutez le service.  
  
3.  Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer des contrats (interfaces) pour le client. Pour plus d’informations sur la procédure à suivre, consultez [Comment : créer un Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
4.  Implémentez l'interface de rappel dans la classe client, comme illustré dans l'exemple suivant.  
  
    ```csharp  
    public class CallbackHandler : ICalculatorDuplexCallback  
    {  
        public void Result(double result)  
        {  
            Console.WriteLine("Result ({0})", result);  
        }  
        public void Equation(string equation)  
        {  
            Console.WriteLine("Equation({0})", equation);  
        }  
    }  
    ```  
  
    ```vb  
    Public Class CallbackHandler   
    Implements ICalculatorDuplexCallback  
       Public Sub Result (ByVal result As Double)  
          Console.WriteLine("Result ({0})", result)  
       End Sub  
        Public Sub Equation(ByVal equation As String)  
            Console.Writeline("Equation({0})", equation)  
        End Sub  
    End Class  
    ```  
  
5.  Créez une instance de la classe <xref:System.ServiceModel.InstanceContext>. Le constructeur a besoin d'une instance de la classe client.  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  Créez une instance de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide du constructeur qui nécessite un objet <xref:System.ServiceModel.InstanceContext>. Le second paramètre du constructeur correspond au nom du point de terminaison trouvé dans le fichier de configuration.  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  Appelez la méthode du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comme requis.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre comment créer une classe client qui accède à un contrat duplex.  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel Bien démarrer](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Guide pratique pour créer un client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Comment : utiliser la classe ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
