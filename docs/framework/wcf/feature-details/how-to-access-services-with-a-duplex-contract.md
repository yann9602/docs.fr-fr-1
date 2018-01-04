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
ms.workload: dotnet
ms.openlocfilehash: 425d17fa34b61985ad3600f992e028e156f6adb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="d9f8a-102">Comment : accéder aux services ayant un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="d9f8a-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="d9f8a-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispose d'une fonctionnalité qui permet de créer un service utilisant un modèle de messagerie duplex.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="d9f8a-104">Ce modèle permet à un service de communiquer avec un client via un rappel.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="d9f8a-105">Cette rubrique contient la procédure permettant de créer un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une classe client qui implémente une interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="d9f8a-106">Une liaison double expose l’adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="d9f8a-107">Ce client doit utiliser un mode de sécurité afin de garantir sa connexion à un service fiable.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="d9f8a-108">Pour obtenir un didacticiel sur la création d’un base [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service et le client, consultez [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d9f8a-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="d9f8a-109">Pour accéder à un service duplex</span><span class="sxs-lookup"><span data-stu-id="d9f8a-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="d9f8a-110">Créez un service qui contient deux interfaces.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="d9f8a-111">La première interface est pour le service, la deuxième est pour le rappel.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d9f8a-112">Création d’un service duplex, consultez [Comment : créer un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9f8a-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="d9f8a-113">Exécutez le service.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="d9f8a-114">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer des contrats (interfaces) pour le client.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="d9f8a-115">Pour plus d’informations sur la procédure à suivre, consultez [Comment : créer un Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d9f8a-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="d9f8a-116">Implémentez l'interface de rappel dans la classe client, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
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
  
5.  <span data-ttu-id="d9f8a-117">Créez une instance de la classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="d9f8a-118">Le constructeur a besoin d'une instance de la classe client.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="d9f8a-119">Créez une instance de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide du constructeur qui nécessite un objet <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="d9f8a-120">Le second paramètre du constructeur correspond au nom du point de terminaison trouvé dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="d9f8a-121">Appelez la méthode du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comme requis.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9f8a-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9f8a-122">Example</span></span>  
 <span data-ttu-id="d9f8a-123">L'exemple de code suivant illustre comment créer une classe client qui accède à un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="d9f8a-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d9f8a-124">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9f8a-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f8a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9f8a-125">See Also</span></span>  
 [<span data-ttu-id="d9f8a-126">Didacticiel Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="d9f8a-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="d9f8a-127">Guide pratique pour créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="d9f8a-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="d9f8a-128">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d9f8a-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="d9f8a-129">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="d9f8a-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="d9f8a-130">Guide pratique pour utiliser la classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="d9f8a-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
