---
title: "Surveillance des échecs d'opération de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42506f7f32d0174b4f980f4e94d370cf4c137276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="11028-102">Surveillance des échecs d'opération de service</span><span class="sxs-lookup"><span data-stu-id="11028-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="11028-103">Si le traçage analytique est activé pour une application, les échecs de service peuvent facilement être surveillés dans l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="11028-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="11028-104">Cette rubrique montre comment déterminer quand une opération de service échoue et comment déterminer la cause de cet échec.</span><span class="sxs-lookup"><span data-stu-id="11028-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="11028-105">Indentification des informations d'échec d'une opération de service</span><span class="sxs-lookup"><span data-stu-id="11028-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="11028-106">Ouvrez l’Observateur d’événements en cliquant sur **Démarrer**, **exécuter**et en entrant `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="11028-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="11028-107">Si vous n’avez pas activé le traçage analytique, développez **journaux des Applications et Services**, **Microsoft**, **Windows**, **serveur d’applications-Applications** .</span><span class="sxs-lookup"><span data-stu-id="11028-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="11028-108">Sélectionnez **vue**, **afficher d’analyse et les journaux de débogage**.</span><span class="sxs-lookup"><span data-stu-id="11028-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="11028-109">Avec le bouton droit **analyse** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="11028-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="11028-110">Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'échec de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="11028-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="11028-111">Ensuite, ouvrez l’exemple créé dans le [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) dans [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Remarque : vous devez exécuter [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] en tant qu’administrateur afin que le service peut être créé.</span><span class="sxs-lookup"><span data-stu-id="11028-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="11028-112">Si vous avez le [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemples installés, vous pouvez ouvrir le [mise en route](../../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé, créé dans le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="11028-112">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="11028-113">Dans le fichier Program.cs du projet serveur, ajoutez la ligne de code suivante au début de la méthode `Divide` dans la classe `CalculatorService` :</span><span class="sxs-lookup"><span data-stu-id="11028-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="11028-114">Dans le fichier Program.cs du projet client, remplacez la valeur de value2 par zéro :</span><span class="sxs-lookup"><span data-stu-id="11028-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="11028-115">Exécutez l’application serveur sans déboguer en appuyant sur **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="11028-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="11028-116">Ouvrez une invite de commandes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11028-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="11028-117">Accédez au répertoire qui contient le client et exécutez ce dernier à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="11028-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="11028-118">Dans l'Observateur d'événements, désactivez et actualisez le journal Analyse et triez les événements par ID d'événement.</span><span class="sxs-lookup"><span data-stu-id="11028-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="11028-119">Rechercher un événement avec l’ID d’événement [ServiceException 219 -](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), qui décrit l’échec du service.</span><span class="sxs-lookup"><span data-stu-id="11028-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="11028-120">Les événements sont mis en mémoire tampon lors de leur envoi à l'Observateur d'événements ; l'événement d'échec peut ne pas apparaître immédiatement.</span><span class="sxs-lookup"><span data-stu-id="11028-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
