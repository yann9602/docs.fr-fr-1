---
title: "Comment : inscrire et configurer un moniker de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 86938301d28cbb0293ece4b3e12a2ef2d2a54e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="da5cd-102">Comment : inscrire et configurer un moniker de service</span><span class="sxs-lookup"><span data-stu-id="da5cd-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="da5cd-103">Avant d'utiliser le moniker de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans une application COM avec un contrat typé, vous devez inscrire les types avec attributs requis avec COM et paramétrer l'application COM et le moniker avec la configuration de liaison requise.</span><span class="sxs-lookup"><span data-stu-id="da5cd-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="da5cd-104">Pour inscrire les types avec attributs requis avec COM</span><span class="sxs-lookup"><span data-stu-id="da5cd-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="da5cd-105">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil pour récupérer le contrat de métadonnées à partir de la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span><span class="sxs-lookup"><span data-stu-id="da5cd-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="da5cd-106">Cette opération génère le code source d'un assembly client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un fichier de configuration d'application cliente.</span><span class="sxs-lookup"><span data-stu-id="da5cd-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="da5cd-107">Vérifiez que les types dans l'assembly sont marqués comme `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="da5cd-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="da5cd-108">Pour cela, ajoutez l'attribut suivant au fichier AssemblyInfo.cs dans votre projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da5cd-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="da5cd-109">Compilez le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] managé comme un assembly avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="da5cd-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="da5cd-110">Cette procédure requiert une signature à l'aide d'une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="da5cd-110">This requires signing with a cryptographic key pair.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="da5cd-111">[Signature d’un Assembly avec un nom fort](http://go.microsoft.com/fwlink/?LinkId=94874) dans le Guide du développeur .NET.</span><span class="sxs-lookup"><span data-stu-id="da5cd-111"> [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="da5cd-112">Utilisez l'outil Assembly Registration Tool (Regasm.exe) avec l'option `/tlb` pour inscrire les types dans l'assembly avec COM.</span><span class="sxs-lookup"><span data-stu-id="da5cd-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="da5cd-113">Utilisez l'outil Global Assembly Cache Tool (Gacutil.exe) pour ajouter l'assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="da5cd-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da5cd-114">La signature de l'assembly et son ajout au Global Assembly Cache sont deux étapes facultatives, mais elles peuvent simplifier le processus de chargement de l'assembly à partir de l'emplacement approprié au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="da5cd-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="da5cd-115">Pour configurer l’application COM et le moniker à l’aide des paramètres de liaison requis</span><span class="sxs-lookup"><span data-stu-id="da5cd-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="da5cd-116">Placez les définitions de liaison (généré par le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dans le fichier de configuration d’application client généré) dans le fichier de configuration de l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="da5cd-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="da5cd-117">Par exemple, pour un fichier exécutable Visual Basic 6.0 nommé CallCenterClient.exe, la configuration doit être placée dans un fichier nommé CallCenterConfig.exe.config, dans le même répertoire que le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="da5cd-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="da5cd-118">L'application cliente peut maintenant utiliser le moniker.</span><span class="sxs-lookup"><span data-stu-id="da5cd-118">The client application can now use the moniker.</span></span> <span data-ttu-id="da5cd-119">Notez que la configuration de liaison n'est pas requise si vous utilisez l'un des types de liaison standard fournis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da5cd-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="da5cd-120">Le type suivant est inscrit.</span><span class="sxs-lookup"><span data-stu-id="da5cd-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="da5cd-121">L'application est exposée à l'aide d'une liaison `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="da5cd-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="da5cd-122">Pour une configuration de type et d'application donnée, les exemples de chaînes de moniker suivants sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="da5cd-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="da5cd-123">Vous pouvez utiliser l'une ou l'autre de ces chaînes de moniker à partir de l'application Visual Basic 6.0, après avoir ajouté une référence à l'assembly qui contient les types `IMathService`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="da5cd-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="da5cd-124">Dans cet exemple, la définition de la configuration de liaison `Binding1` est stockée dans un fichier de configuration judicieusement nommé pour l'application cliente, par exemple vb6nomapp.exe.config.</span><span class="sxs-lookup"><span data-stu-id="da5cd-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da5cd-125">Vous pouvez utiliser un code semblable dans une application C#, C++ ou d'un autre langage .NET.</span><span class="sxs-lookup"><span data-stu-id="da5cd-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="da5cd-126">Si le moniker est incorrect ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur de type « Syntaxe non valide ».</span><span class="sxs-lookup"><span data-stu-id="da5cd-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="da5cd-127">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="da5cd-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="da5cd-128">Bien que cette rubrique porte sur l'utilisation du moniker de service à partir du code VB 6.0, vous pouvez utiliser un moniker de service à partir d'autres langages.</span><span class="sxs-lookup"><span data-stu-id="da5cd-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="da5cd-129">Lors de l'utilisation d'un moniker à partir du code C++, l'assembly généré par Svcutil.exe doit être importé avec le paramètre « no_namespace named_guids raw_interfaces_only », tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da5cd-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="da5cd-130">Cela modifie les définitions d'interface importées afin que toutes les méthodes retournent un `HResult`.</span><span class="sxs-lookup"><span data-stu-id="da5cd-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="da5cd-131">Toutes les autres valeurs de retour sont converties en paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="da5cd-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="da5cd-132">L'exécution globale des méthodes reste la même.</span><span class="sxs-lookup"><span data-stu-id="da5cd-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="da5cd-133">Cela vous permet de déterminer la cause d'une exception lorsque vous appelez une méthode sur le proxy.</span><span class="sxs-lookup"><span data-stu-id="da5cd-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="da5cd-134">Cette fonctionnalité n'est disponible qu'à partir du code C++.</span><span class="sxs-lookup"><span data-stu-id="da5cd-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5cd-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da5cd-135">See Also</span></span>  
 [<span data-ttu-id="da5cd-136">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="da5cd-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
