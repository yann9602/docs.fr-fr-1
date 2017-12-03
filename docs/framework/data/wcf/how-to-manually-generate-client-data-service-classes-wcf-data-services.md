---
title: "Comment : générer manuellement les classes de services de données client (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed668fb7648daa8a3571f407b3243291d3f8bd86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="323ec-102">Comment : générer manuellement les classes de services de données client (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="323ec-102">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="323ec-103">s’intègre à Visual Studio pour vous permettre de générer automatiquement des classes de service de données client lorsque vous utilisez la **ajouter une référence de Service** boîte de dialogue pour ajouter une référence à un service de données dans un projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="323ec-103"> integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="323ec-104">Pour plus d’informations, consultez [Comment : ajouter une référence de Service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="323ec-104">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="323ec-105">Vous pouvez également générer manuellement les mêmes classes de service de données client en utilisant l'outil de génération de code, `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="323ec-105">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="323ec-106">Cet outil, inclus avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], génère des classes .NET Framework depuis la définition du service des données.</span><span class="sxs-lookup"><span data-stu-id="323ec-106">This tool, which is included with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="323ec-107">Il peut également être utilisé pour générer des classes de service des données depuis le fichier de modèle conceptuel (.csdl) et depuis le fichier .edmx qui représente un modèle Entity Framework dans un projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="323ec-107">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>  
  
 <span data-ttu-id="323ec-108">L'exemple dans cette rubrique crée des classes de service de données client basées sur l'exemple de service de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="323ec-108">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="323ec-109">Ce service est créé lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="323ec-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="323ec-110">Certains exemples dans cette rubrique requièrent le fichier modèle conceptuel pour le modèle Northwind.</span><span class="sxs-lookup"><span data-stu-id="323ec-110">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="323ec-111">Pour plus d’informations, consultez [Comment : utiliser des EdmGen.exe pour générer des fichiers de modèle et de mappage](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="323ec-111">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="323ec-112">Certains exemples dans cette rubrique requièrent le fichier .edmx pour le modèle Northwind.</span><span class="sxs-lookup"><span data-stu-id="323ec-112">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="323ec-113">Pour plus d’informations, consultez [présentation d’un fichier .edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span><span class="sxs-lookup"><span data-stu-id="323ec-113">For more information, see [.edmx File Overview](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).</span></span>  
  
### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="323ec-114">Pour générer des classes C# qui prennent en charge la liaison de données</span><span class="sxs-lookup"><span data-stu-id="323ec-114">To generate C# classes that support data binding</span></span>  
  
-   <span data-ttu-id="323ec-115">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="323ec-116">Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .</span><span class="sxs-lookup"><span data-stu-id="323ec-116">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="323ec-117">Pour générer des classes Visual Basic qui prennent en charge la liaison de données</span><span class="sxs-lookup"><span data-stu-id="323ec-117">To generate Visual Basic classes that support data binding</span></span>  
  
-   <span data-ttu-id="323ec-118">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-118">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="323ec-119">Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .</span><span class="sxs-lookup"><span data-stu-id="323ec-119">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="323ec-120">Pour générer des classes C# basées sur l'URI de service</span><span class="sxs-lookup"><span data-stu-id="323ec-120">To generate C# classes based on the service URI</span></span>  
  
-   <span data-ttu-id="323ec-121">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-121">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="323ec-122">Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .</span><span class="sxs-lookup"><span data-stu-id="323ec-122">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="323ec-123">Pour générer des classes Visual Basic basées sur l'URI de service</span><span class="sxs-lookup"><span data-stu-id="323ec-123">To generate Visual Basic classes based on the service URI</span></span>  
  
-   <span data-ttu-id="323ec-124">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-124">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="323ec-125">Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .</span><span class="sxs-lookup"><span data-stu-id="323ec-125">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>  
  
### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="323ec-126">Pour générer des classes C# basées sur le fichier de modèle conceptuel (CSDL)</span><span class="sxs-lookup"><span data-stu-id="323ec-126">To generate C# classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="323ec-127">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-127">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="323ec-128">Pour générer des classes Visual Basic basées sur le fichier de modèle conceptuel (CSDL)</span><span class="sxs-lookup"><span data-stu-id="323ec-128">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>  
  
-   <span data-ttu-id="323ec-129">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-129">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="323ec-130">Pour générer des classes C# basées sur le fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="323ec-130">To generate C# classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="323ec-131">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-131">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="323ec-132">Pour générer des classes Visual Basic basées sur le fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="323ec-132">To generate Visual Basic classes based on the .edmx file</span></span>  
  
-   <span data-ttu-id="323ec-133">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="323ec-133">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="323ec-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="323ec-134">See Also</span></span>  
 [<span data-ttu-id="323ec-135">Génération de la bibliothèque cliente du service de données</span><span class="sxs-lookup"><span data-stu-id="323ec-135">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="323ec-136">Comment : ajouter une référence de Service de données</span><span class="sxs-lookup"><span data-stu-id="323ec-136">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)  
 [<span data-ttu-id="323ec-137">Utilitaire de Client de Service de données WCF (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="323ec-137">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)
