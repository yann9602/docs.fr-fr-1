---
title: "Procédure pas à pas : accès à un Service Web à l’aide de fournisseurs de Type (F #)"
description: "Découvrez comment utiliser le fournisseur de type de Web Services Description Language (WSDL) disponible dans F # 3.0 pour accéder à un service WSDL."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a><span data-ttu-id="74038-104">Procédure pas à pas : accès à un service Web à l’aide des fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="74038-104">Walkthrough: Accessing a Web Service by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="74038-105">Ce guide a été écrit pour F # 3.0 et sera mise à jour.</span><span class="sxs-lookup"><span data-stu-id="74038-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="74038-106">Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).</span><span class="sxs-lookup"><span data-stu-id="74038-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="74038-107">Les liens de référence d’API vous permettront de MSDN.</span><span class="sxs-lookup"><span data-stu-id="74038-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="74038-108">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="74038-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="74038-109">Cette procédure pas à pas montre comment utiliser le fournisseur de type Web Services Description Language (WSDL) n’est disponible dans F # 3.0 pour accéder à un service WSDL.</span><span class="sxs-lookup"><span data-stu-id="74038-109">This walkthrough shows you how to use the Web Services Description Language (WSDL) type provider that is available in F# 3.0 to access a WSDL service.</span></span> <span data-ttu-id="74038-110">Dans d’autres langages .NET, vous générez le code pour accéder au service web par svcutil.exe appelant, ou en ajoutant une référence web dans, par exemple, un projet c# pour obtenir Visual Studio pour appeler svcutil.exe pour vous.</span><span class="sxs-lookup"><span data-stu-id="74038-110">In other .NET languages, you generate the code to access the web service by calling svcutil.exe, or by adding a web reference in, for example, a C# project to get Visual Studio to call svcutil.exe for you.</span></span> <span data-ttu-id="74038-111">En F #, vous avez la possibilité supplémentaire de l’utilisation du fournisseur de type WSDL, par conséquent, dès que vous écrivez le code qui crée le type WsdlService, les types sont générés et sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="74038-111">In F#, you have the additional option of using the WSDL type provider, so as soon as you write the code that creates the WsdlService type, the types are generated and become available.</span></span> <span data-ttu-id="74038-112">Ce processus s’appuie sur le service est disponible lorsque vous écrivez le code.</span><span class="sxs-lookup"><span data-stu-id="74038-112">This process relies on the service being available when you are writing the code.</span></span>

<span data-ttu-id="74038-113">Cette procédure pas à pas décrit les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="74038-113">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="74038-114">Vous devez effectuer les dans cet ordre pour la procédure pas à pas réussisse :</span><span class="sxs-lookup"><span data-stu-id="74038-114">You must complete them in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="74038-115">Création du projet</span><span class="sxs-lookup"><span data-stu-id="74038-115">Creating the project</span></span>
<br />

- <span data-ttu-id="74038-116">Configuration du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="74038-116">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="74038-117">Appel du service web et le traitement des résultats</span><span class="sxs-lookup"><span data-stu-id="74038-117">Calling the web service, and processing the results</span></span>
<br />


## <a name="creating-the-project"></a><span data-ttu-id="74038-118">Création du projet</span><span class="sxs-lookup"><span data-stu-id="74038-118">Creating the project</span></span>
<span data-ttu-id="74038-119">Dans l’étape, vous créez un projet et ajoutez les références appropriées pour utiliser un fournisseur de type WSDL.</span><span class="sxs-lookup"><span data-stu-id="74038-119">In the step, you create a project and add the appropriate references to use a WSDL type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="74038-120">Pour créer et configurer le projet F#</span><span class="sxs-lookup"><span data-stu-id="74038-120">To create and set up an F# project</span></span>

1. <span data-ttu-id="74038-121">Ouvrez un nouveau projet d’Application Console F #.</span><span class="sxs-lookup"><span data-stu-id="74038-121">Open a new F# Console Application project.</span></span>
<br />

2. <span data-ttu-id="74038-122">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet **référence** nœud, puis choisissez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="74038-122">In **Solution Explorer**, open the shortcut menu for the project's **Reference** node, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="74038-123">Dans le **assemblys** zone, choisissez **Framework**, puis, dans la liste des assemblys disponibles, choisissez **System.Runtime.Serialization** et  **System.ServiceModel**.</span><span class="sxs-lookup"><span data-stu-id="74038-123">In the **Assemblies** area, choose **Framework**, and then, in the list of available assemblies, choose **System.Runtime.Serialization** and **System.ServiceModel**.</span></span>
<br />

4. <span data-ttu-id="74038-124">Dans le **assemblys** zone, choisissez **Extensions**.</span><span class="sxs-lookup"><span data-stu-id="74038-124">In the **Assemblies** area, choose **Extensions**.</span></span>
<br />

5. <span data-ttu-id="74038-125">Dans la liste des assemblys disponibles, choisissez **FSharp.Data.TypeProviders**, puis choisissez le **OK** bouton pour ajouter des références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="74038-125">In the list of available assemblies, choose **FSharp.Data.TypeProviders**, and then choose the **OK** button to add references to these assemblies.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="74038-126">Configuration du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="74038-126">Configuring the type provider</span></span>
<span data-ttu-id="74038-127">Dans cette étape, vous utilisez le fournisseur de type WSDL pour générer des types pour le service web de TerraServer.</span><span class="sxs-lookup"><span data-stu-id="74038-127">In this step, you use the WSDL type provider to generate types for the TerraServer web service.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="74038-128">Pour configurer le fournisseur de type et générer des types</span><span class="sxs-lookup"><span data-stu-id="74038-128">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="74038-129">Ajoutez la ligne suivante de code pour ouvrir l’espace de noms de fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="74038-129">Add the following line of code to open the type provider namespace.</span></span>
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. <span data-ttu-id="74038-130">Ajoutez la ligne suivante de code pour appeler le fournisseur de type avec un service web.</span><span class="sxs-lookup"><span data-stu-id="74038-130">Add the following line of code to invoke the type provider with a web service.</span></span> <span data-ttu-id="74038-131">Dans cet exemple, utilisez le service web TerraServer.</span><span class="sxs-lookup"><span data-stu-id="74038-131">In this example, use the TerraServer web service.</span></span>
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  <span data-ttu-id="74038-132">Si l’URI de service est mal orthographié ou si le service est arrêté ou ne fonctionne pas, une ligne ondulée rouge s’affiche sous cette ligne de code.</span><span class="sxs-lookup"><span data-stu-id="74038-132">A red squiggle appears under this line of code if the service URI is misspelled or if the service itself is down or isn’t performing.</span></span> <span data-ttu-id="74038-133">Si vous pointez sur le code, un message d’erreur décrit le problème.</span><span class="sxs-lookup"><span data-stu-id="74038-133">If you point to the code, an error message describes the problem.</span></span> <span data-ttu-id="74038-134">Vous pouvez obtenir les mêmes informations dans le **liste d’erreurs** fenêtre ou dans le **fenêtre sortie** après la génération.</span><span class="sxs-lookup"><span data-stu-id="74038-134">You can find the same information in the **Error List** window or in the **Output Window** after you build.</span></span>
<br />  <span data-ttu-id="74038-135">Il existe deux façons de spécifier les paramètres de configuration pour une connexion de WSDL, à l’aide du fichier app.config pour le projet, ou en utilisant les paramètres de type statique dans la déclaration de fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="74038-135">There are two ways to specify configuration settings for a WSDL connection, by using the app.config file for the project, or by using the static type parameters in the type provider declaration.</span></span> <span data-ttu-id="74038-136">Vous pouvez utiliser svcutil.exe pour générer des éléments de fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="74038-136">You can use svcutil.exe to generate appropriate configuration file elements.</span></span> <span data-ttu-id="74038-137">Pour plus d’informations sur l’utilisation de svcutil.exe pour générer des informations de configuration pour un service web, consultez [ServiceModel Metadata Utility Tool &#40; SvcUtil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx).</span><span class="sxs-lookup"><span data-stu-id="74038-137">For more information about using svcutil.exe to generate configuration information for a web service, see [ServiceModel Metadata Utility Tool &#40;Svcutil.exe&#41;](https://msdn.microsoft.com/library/aa347733.aspx).</span></span> <span data-ttu-id="74038-138">Pour obtenir une description complète des paramètres de type statique pour le fournisseur de type WSDL, consultez [fournisseur de Type WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="74038-138">For a full description of the static type parameters for the WSDL type provider, see [WsdlService Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).</span></span>
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a><span data-ttu-id="74038-139">Appel du service web et le traitement des résultats</span><span class="sxs-lookup"><span data-stu-id="74038-139">Calling the web service, and processing the results</span></span>
<span data-ttu-id="74038-140">Chaque service web a son propre ensemble de types qui sont utilisés en tant que paramètres pour ses appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="74038-140">Each web service has its own set of types that are used as parameters for its method calls.</span></span> <span data-ttu-id="74038-141">Dans cette étape, vous préparez ces paramètres, appelez une méthode web et traiter les informations qu’elle retourne.</span><span class="sxs-lookup"><span data-stu-id="74038-141">In this step, you prepare these parameters, call a web method, and process the information that it returns.</span></span>


#### <a name="to-call-the-web-service-and-process-the-results"></a><span data-ttu-id="74038-142">Pour appeler le service web et traiter les résultats</span><span class="sxs-lookup"><span data-stu-id="74038-142">To call the web service, and process the results</span></span>

1. <span data-ttu-id="74038-143">Le service web peut expirer ou cesser de fonctionner, donc vous devez inclure l’appel du service web dans une bloc de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="74038-143">The web service might time out or stop functioning, so you should include the web service call in an exception handling block.</span></span> <span data-ttu-id="74038-144">Écrire le code suivant pour essayer d’obtenir des données à partir du service web.</span><span class="sxs-lookup"><span data-stu-id="74038-144">Write the following code to try to get data from the web service.</span></span>
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

<span data-ttu-id="74038-145">Notez que vous créez les types de données qui sont nécessaires pour le service web, tel que **Place** et **emplacement**, comme les types imbriqués sous la WsdlService de type **TerraService**.</span><span class="sxs-lookup"><span data-stu-id="74038-145">Notice that you create the data types that are needed for the web service, such as **Place** and **Location**, as nested types under the WsdlService type **TerraService**.</span></span>
<br />


## <a name="see-also"></a><span data-ttu-id="74038-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74038-146">See Also</span></span>
[<span data-ttu-id="74038-147">Fournisseur de Type de WsdlService</span><span class="sxs-lookup"><span data-stu-id="74038-147">WsdlService Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[<span data-ttu-id="74038-148">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="74038-148">Type Providers</span></span>](index.md)
