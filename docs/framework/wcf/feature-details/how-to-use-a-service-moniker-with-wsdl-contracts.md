---
title: "Comment : utiliser un moniker de service avec des contrats WSDL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c36ac73ced510c1ba3b7e16c71f764c46d6c8f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="699fb-102">Comment : utiliser un moniker de service avec des contrats WSDL</span><span class="sxs-lookup"><span data-stu-id="699fb-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="699fb-103">Dans certains cas, vous pouvez avoir besoin d'un client COM Interop entièrement autonome.</span><span class="sxs-lookup"><span data-stu-id="699fb-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="699fb-104">Le service que vous souhaitez appeler peut ne pas exposer de point de terminaison MEX et la DLL du client WCF risque de ne pas être enregistrée pour COM Interop.</span><span class="sxs-lookup"><span data-stu-id="699fb-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="699fb-105">Le cas échéant, vous pouvez créer un fichier WSDL qui décrit le service et le transmet au moniker de service WCF.</span><span class="sxs-lookup"><span data-stu-id="699fb-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="699fb-106">Cette rubrique décrit la manière d'appeler l'exemple de mise en route WCF à l'aide d'un moniker WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="699fb-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="699fb-107">Utilisation du moniker de service WSDL</span><span class="sxs-lookup"><span data-stu-id="699fb-107">Using the WSDL service moniker</span></span>  
  
1.  <span data-ttu-id="699fb-108">Ouvrez et créez l'exemple de solution de mise en route.</span><span class="sxs-lookup"><span data-stu-id="699fb-108">Open and build the GettingStarted sample solution.</span></span>  
  
2.  <span data-ttu-id="699fb-109">Ouvrez Internet Explorer et naviguez jusqu'à http://localhost/ServiceModelSamples/Service.svc pour vous assurer que le service fonctionne.</span><span class="sxs-lookup"><span data-stu-id="699fb-109">Open Internet Explorer and browse to http://localhost/ServiceModelSamples/Service.svc to make sure that the service is working.</span></span>  
  
3.  <span data-ttu-id="699fb-110">Dans le fichier Service.cs, ajoutez l'attribut suivant sur la classe CalculatorService :</span><span class="sxs-lookup"><span data-stu-id="699fb-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  <span data-ttu-id="699fb-111">Ajoutez un espace de noms de liaison au service App.config :</span><span class="sxs-lookup"><span data-stu-id="699fb-111">Add a binding namespace to the service App.config:</span></span>  
  
  
  
5.  <span data-ttu-id="699fb-112">Créez un fichier WSDL pour que l'application le lise.</span><span class="sxs-lookup"><span data-stu-id="699fb-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="699fb-113">Étant donné que les espaces de noms ont été ajoutés lors des étapes 3 et 4, vous pouvez utiliser Internet Explorer pour interroger l'ensemble de la description WSDL du service en naviguant jusqu'à http://localhost/ServiceModelSamples/Service.svc? wsdl.</span><span class="sxs-lookup"><span data-stu-id="699fb-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to http://localhost/ServiceModelSamples/Service.svc?wsdl.</span></span> <span data-ttu-id="699fb-114">Vous pouvez ensuite enregistrer le fichier à partir d'Internet Explorer en tant que serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="699fb-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="699fb-115">Si vous ne spécifiez pas les espaces de noms lors des étapes 3 et 4, le document WSDL renvoyé à l'issue de l'interrogation de l'URL ci-dessus ne sera pas le document WSDL complet.</span><span class="sxs-lookup"><span data-stu-id="699fb-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="699fb-116">Le document WSDL renvoyé inclura plusieurs instructions import qui permettent d'importer d'autres documents WSDL.</span><span class="sxs-lookup"><span data-stu-id="699fb-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="699fb-117">Vous devrez parcourir chaque instruction import et générer le document WSDL complet, en associant le WSDL renvoyé par le service avec le WSDL importé.</span><span class="sxs-lookup"><span data-stu-id="699fb-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6.  <span data-ttu-id="699fb-118">Ouvrez Visual Basic 6.0 et créez un nouveau fichier .exe standard.</span><span class="sxs-lookup"><span data-stu-id="699fb-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="699fb-119">Ajoutez un bouton au formulaire et double-cliquez dessus pour ajouter le code suivant au gestionnaire Click :</span><span class="sxs-lookup"><span data-stu-id="699fb-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  Si le moniker est mal formé ou si le service n'est pas disponible, l'appel de `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.  <span data-ttu-id="699fb-121">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="699fb-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7.  <span data-ttu-id="699fb-122">Exécutez l'application Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="699fb-122">Run the Visual Basic application.</span></span> <span data-ttu-id="699fb-123">Un message s'affiche avec les résultats de l'appel de Subtract(145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="699fb-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699fb-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="699fb-124">See Also</span></span>  
 [<span data-ttu-id="699fb-125">Prise en main</span><span class="sxs-lookup"><span data-stu-id="699fb-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="699fb-126">Vue d’ensemble de l’intégration à des applications COM</span><span class="sxs-lookup"><span data-stu-id="699fb-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
