---
title: "Procédure : créer un service de workflow qui appelle un autre service de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c99748e77f1fccd9512c8915d0f4068d0da51a41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="aba54-102">Procédure : créer un service de workflow qui appelle un autre service de workflow</span><span class="sxs-lookup"><span data-stu-id="aba54-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>
<span data-ttu-id="aba54-103">Il est parfois nécessaire pour un service de workflow d'obtenir des informations d'un autre service de workflow.</span><span class="sxs-lookup"><span data-stu-id="aba54-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span>  <span data-ttu-id="aba54-104">Cette rubrique montre comment appeler un service de workflow à partir d'un autre service.</span><span class="sxs-lookup"><span data-stu-id="aba54-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="aba54-105">Dans cette rubrique, vous créerez deux services de workflow ; un qui a une méthode qui inverse la chaîne d'entrée et un autre qui convertit la chaîne d'entrée en majuscules après avoir inversé la chaîne qui utilise le premier service.</span><span class="sxs-lookup"><span data-stu-id="aba54-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>  
  
### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="aba54-106">Pour créer le service de workflow Reverser</span><span class="sxs-lookup"><span data-stu-id="aba54-106">To create the Reverser workflow service</span></span>  
  
1.  <span data-ttu-id="aba54-107">Exécutez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="aba54-107">Run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] as an administrator.</span></span>  
  
2.  <span data-ttu-id="aba54-108">Sélectionnez **fichier**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="aba54-108">Select **File**, **New Project**.</span></span> <span data-ttu-id="aba54-109">Sous le **Workflow** nœud dans le **modèles installés** volet, sélectionnez **Application de Service de Workflow WCF**.</span><span class="sxs-lookup"><span data-stu-id="aba54-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="aba54-110">Nommez la solution `NestedServices` puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aba54-110">Name the solution `NestedServices` and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="aba54-111">Sous **serveurs**, assurez-vous que **utiliser le serveur Web IIS Local** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="aba54-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="aba54-112">Cliquez sur **créer un répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="aba54-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="aba54-113">Cliquez sur **OK** dans la boîte de dialogue indiquant que le répertoire virtuel a été créé.</span><span class="sxs-lookup"><span data-stu-id="aba54-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>  
  
4.  <span data-ttu-id="aba54-114">Dans l’Explorateur de solutions, renommez Service1.xamlx `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="aba54-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>  
  
5.  <span data-ttu-id="aba54-115">Sur le **propriétés du projet** pour le nouveau projet, cliquez sur le **Web** onglet. Définir le **Action de démarrage** à **Page spécifique**, puis sélectionnez StringReverserService.xamlx en tant que la page de démarrage.</span><span class="sxs-lookup"><span data-stu-id="aba54-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>  
  
6.  <span data-ttu-id="aba54-116">Ouvrez le fichier StringReverserService.xamlx dans le concepteur et supprimez les activités `ReceiveRequest` et `SendReply` existantes, puis faites glisser une activité `ReceiveAndSendReply` dans l'activité de la séquence existante.</span><span class="sxs-lookup"><span data-stu-id="aba54-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="aba54-117">Définir le **NomOpération** sur ReverseString.</span><span class="sxs-lookup"><span data-stu-id="aba54-117">Set the **OperationName** to ReverseString.</span></span>  
  
    2.  <span data-ttu-id="aba54-118">Définir le **ServiceContractName** sur IReverseString.</span><span class="sxs-lookup"><span data-stu-id="aba54-118">Set the **ServiceContractName** to IReverseString.</span></span>  
  
    3.  <span data-ttu-id="aba54-119">Sélectionnez le **CanCreateInstance** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="aba54-119">Select the **CanCreateInstance** check box.</span></span>  
  
7.  <span data-ttu-id="aba54-120">Sélectionnez le **SequentialService** activité, puis cliquez sur le **Variables** onglet en bas du concepteur.</span><span class="sxs-lookup"><span data-stu-id="aba54-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="aba54-121">Créez deux nouvelles variables nommées StringToReverse et ReversedStringToReturn de type String.</span><span class="sxs-lookup"><span data-stu-id="aba54-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>  
  
8.  <span data-ttu-id="aba54-122">Cliquez sur le **définir** lien dans le **réception** activité.</span><span class="sxs-lookup"><span data-stu-id="aba54-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="aba54-123">Cliquez sur le **paramètres**et créez un paramètre nommé InputString de type String qui assigne à StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="aba54-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>  
  
9. <span data-ttu-id="aba54-124">Cliquez sur le **définir** lien dans le **SendReplyToReceive** activité.</span><span class="sxs-lookup"><span data-stu-id="aba54-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="aba54-125">Cliquez sur le **paramètres**et créez un paramètre nommé ReversedString de type String, assigné à ReversedStringToReturn.</span><span class="sxs-lookup"><span data-stu-id="aba54-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>  
  
10. <span data-ttu-id="aba54-126">Pour implémenter la logique pour le service, créez une nouvelle classe nommée StringLibrary dans le projet.</span><span class="sxs-lookup"><span data-stu-id="aba54-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="aba54-127">Remplacez la définition de la classe par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aba54-127">Replace the class definition with the following code.</span></span>  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. <span data-ttu-id="aba54-128">Pour appeler la méthode ReverseString sur l’entrée, faites glisser un **InvokeMethod** activité à partir de la boîte à outils vers l’espace entre le **réception** et **SendReply** activités.</span><span class="sxs-lookup"><span data-stu-id="aba54-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="aba54-129">Définissez les propriétés de l'activité comme ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="aba54-129">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="aba54-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="aba54-130">**MethodName**: ReverseString</span></span>  
  
    2.  <span data-ttu-id="aba54-131">**Résultat**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="aba54-131">**Result**: ReversedStringToReturn</span></span>  
  
    3.  <span data-ttu-id="aba54-132">**Paramètres**: créez un paramètre avec un **Direction** in, un **Type** de chaîne et une **valeur** stringtoreverse.</span><span class="sxs-lookup"><span data-stu-id="aba54-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>  
  
    4.  <span data-ttu-id="aba54-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="aba54-133">**TargetType**: NestedServices.StringLibrary</span></span>  
  
12. <span data-ttu-id="aba54-134">Testez le service en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="aba54-134">Test the service by pressing F5.</span></span> <span data-ttu-id="aba54-135">Dans le Client test WCF qui s'affiche, double-cliquez sur la méthode ReverseString().</span><span class="sxs-lookup"><span data-stu-id="aba54-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="aba54-136">Dans le volet de requête, entrez `Sample` pour la valeur du paramètre InputString.</span><span class="sxs-lookup"><span data-stu-id="aba54-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="aba54-137">Cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="aba54-137">Click **Invoke**.</span></span> <span data-ttu-id="aba54-138">Le service doit retourner « elpmaS ».</span><span class="sxs-lookup"><span data-stu-id="aba54-138">The service should return "elpmaS".</span></span>  
  
### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="aba54-139">Pour créer le service de workflow UpperCaser</span><span class="sxs-lookup"><span data-stu-id="aba54-139">To create the UpperCaser workflow service</span></span>  
  
1.  <span data-ttu-id="aba54-140">Cliquez sur le projet NestedServices et sélectionnez **ajouter**, **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="aba54-140">Right-click the NestedServices project and select **Add**, **New Item**.</span></span> <span data-ttu-id="aba54-141">Dans le **Workflow** nœud, sélectionnez **Service de Workflow WCF**et nommez le nouveau service `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="aba54-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="aba54-142">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="aba54-142">Click **Add**.</span></span> <span data-ttu-id="aba54-143">Un nouveau service de workflow nommé UpperCaserService.xamlx doit être ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="aba54-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>  
  
2.  <span data-ttu-id="aba54-144">Ouvrez le fichier Uppercaserservices.xamlx dans le concepteur et supprimez les **ReceiveRequest** et `SendReply` activités et faites glisser un `ReceiveAndSendReply` activité dans l’activité de séquence existante.</span><span class="sxs-lookup"><span data-stu-id="aba54-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="aba54-145">Définir le **NomOpération** sur UpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="aba54-145">Set the **OperationName** to UpperCaseString.</span></span>  
  
    2.  <span data-ttu-id="aba54-146">Définir le **ServiceContractName** sur IUpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="aba54-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>  
  
    3.  <span data-ttu-id="aba54-147">Sélectionnez le **CanCreateInstance** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="aba54-147">Select the **CanCreateInstance** check box.</span></span>  
  
3.  <span data-ttu-id="aba54-148">Sélectionnez l’activité SequentialService, puis cliquez sur le **Variables** onglet en bas du concepteur.</span><span class="sxs-lookup"><span data-stu-id="aba54-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="aba54-149">Créez trois nouvelles variables nommées StringToUpper, StringToReverse et StringToReturn de type String.</span><span class="sxs-lookup"><span data-stu-id="aba54-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>  
  
4.  <span data-ttu-id="aba54-150">Cliquez sur le **définir** lien dans le **réception** activité.</span><span class="sxs-lookup"><span data-stu-id="aba54-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="aba54-151">Cliquez sur le **paramètres**et créez un paramètre nommé InputString de type String qui assigne à StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="aba54-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>  
  
5.  <span data-ttu-id="aba54-152">Cliquez sur le **définir** lien dans le **SendReplyToReceive** activité.</span><span class="sxs-lookup"><span data-stu-id="aba54-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="aba54-153">Cliquez sur le **paramètres**et créez un paramètre nommé ModifiedString de type String, assigné à StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="aba54-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>  
  
6.  <span data-ttu-id="aba54-154">Pour implémenter la logique pour le service, créez une nouvelle méthode dans la classe StringLibrary à l'aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="aba54-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  <span data-ttu-id="aba54-155">Pour appeler la méthode UpperCaseString sur l’entrée, faites glisser un **InvokeMethod** activité à partir de la boîte à outils vers l’espace entre le **réception** et **SendReply** activités.</span><span class="sxs-lookup"><span data-stu-id="aba54-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="aba54-156">Définissez les propriétés de l'activité comme ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="aba54-156">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="aba54-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="aba54-157">**MethodName**: UpperCaseString</span></span>  
  
    2.  <span data-ttu-id="aba54-158">**Résultat**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="aba54-158">**Result**: StringToReverse</span></span>  
  
    3.  <span data-ttu-id="aba54-159">**Paramètres**: créez un paramètre avec un **Direction** in, un **Type** de chaîne et une **valeur** stringtoupper.</span><span class="sxs-lookup"><span data-stu-id="aba54-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>  
  
    4.  <span data-ttu-id="aba54-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="aba54-160">**TargetType**: NestedServices.StringLibrary</span></span>  
  
8.  <span data-ttu-id="aba54-161">Vous allez maintenant appeler le premier service sur la chaîne modifiée.</span><span class="sxs-lookup"><span data-stu-id="aba54-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="aba54-162">Cliquez sur le projet et sélectionnez **ajouter une référence de Service**.</span><span class="sxs-lookup"><span data-stu-id="aba54-162">Right-click the project and select **Add Service Reference**.</span></span> <span data-ttu-id="aba54-163">Ajoutez une référence de service à http://localhost/NestedServices/StringReverserService.xamlx et générez le projet pour créer une activité personnalisée permettant d'accéder au premier service Web.</span><span class="sxs-lookup"><span data-stu-id="aba54-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>  
  
9. <span data-ttu-id="aba54-164">Faites glisser une instance de la nouvelle activité sur le flux de travail entre les **InvokeMethod** activité et le **SendReplyToReceive** activités.</span><span class="sxs-lookup"><span data-stu-id="aba54-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="aba54-165">Assignez la variable StringToReverse à la propriété InputString de la nouvelle activité, et la variable StringToReturn à la propriété StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="aba54-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>  
  
10. <span data-ttu-id="aba54-166">Ouvrez la page de propriétés pour le projet NestedServices et modifiez le **Page spécifique** dans les **Web** onglet par uppercaserservice.xamlx.</span><span class="sxs-lookup"><span data-stu-id="aba54-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>  
  
11. <span data-ttu-id="aba54-167">Testez le service en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="aba54-167">Test the service by pressing F5.</span></span> <span data-ttu-id="aba54-168">Dans le Client test WCF qui s'affiche, double-cliquez sur la méthode ReverseString().</span><span class="sxs-lookup"><span data-stu-id="aba54-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="aba54-169">Dans le volet de requête, entrez `Sample` pour la valeur du paramètre InputString.</span><span class="sxs-lookup"><span data-stu-id="aba54-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="aba54-170">Cliquez sur **appeler**.</span><span class="sxs-lookup"><span data-stu-id="aba54-170">Click **Invoke**.</span></span> <span data-ttu-id="aba54-171">Le service doit retourner « ELPMAS ».</span><span class="sxs-lookup"><span data-stu-id="aba54-171">The service should return "ELPMAS".</span></span>  
  
### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="aba54-172">Pour créer un client qui appelle les services</span><span class="sxs-lookup"><span data-stu-id="aba54-172">To create a client to call the services</span></span>  
  
1.  <span data-ttu-id="aba54-173">Ajoutez à la solution un nouveau projet d'application console nommé Client.</span><span class="sxs-lookup"><span data-stu-id="aba54-173">Add a new Console application project called Client to the solution.</span></span>  
  
2.  <span data-ttu-id="aba54-174">Cliquez sur le projet Client, puis sélectionnez **ajouter une référence de Service**.</span><span class="sxs-lookup"><span data-stu-id="aba54-174">Right-click the Client project and select **Add Service Reference**.</span></span> <span data-ttu-id="aba54-175">Dans la fenêtre qui s’affiche, cliquez sur **Discover**.</span><span class="sxs-lookup"><span data-stu-id="aba54-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="aba54-176">Sélectionnez StringReverserService.xamlx et entrez ReverseService comme espace de noms.</span><span class="sxs-lookup"><span data-stu-id="aba54-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="aba54-177">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="aba54-177">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="aba54-178">Remplacez le code de la méthode Main dans Program.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aba54-178">Replace the Main method in Program.cs with the following code.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
