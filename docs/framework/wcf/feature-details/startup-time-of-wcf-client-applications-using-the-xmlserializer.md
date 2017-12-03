---
title: "Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14f5cf25bbcde4732162f2c44c83661a0ac739ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="28106-102">Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="28106-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="28106-103">Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.</span><span class="sxs-lookup"><span data-stu-id="28106-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28106-104">Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.</span><span class="sxs-lookup"><span data-stu-id="28106-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="28106-105">Le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaires à partir des assemblys compilés pour l’application.</span><span class="sxs-lookup"><span data-stu-id="28106-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="28106-106">Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28106-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="28106-107">Les contrats de service et d'opération qui utilisent <xref:System.Xml.Serialization.XmlSerializer> sont marqués avec <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="28106-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="28106-108">Pour générer du code de sérialisation XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="28106-108">To generate XmlSerializer serialization code</span></span>  
  
1.  <span data-ttu-id="28106-109">Compilez votre code de service ou client dans un ou plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="28106-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2.  <span data-ttu-id="28106-110">Ouvrez une invite de commandes du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="28106-110">Open an SDK command prompt.</span></span>  
  
3.  <span data-ttu-id="28106-111">À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.</span><span class="sxs-lookup"><span data-stu-id="28106-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="28106-112">L'argument `assemblyPath` spécifie le chemin d'accès à un assembly contenant des types de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="28106-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="28106-113">Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="28106-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="28106-114">Svcutil.exe peut uniquement générer du code de sérialisation C#.</span><span class="sxs-lookup"><span data-stu-id="28106-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="28106-115">Un fichier de code source est généré pour chaque assembly d'entrée.</span><span class="sxs-lookup"><span data-stu-id="28106-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="28106-116">Vous ne pouvez pas utiliser le **/Language** commutateur changer le langage du code généré.</span><span class="sxs-lookup"><span data-stu-id="28106-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="28106-117">Pour spécifier le chemin d’accès aux assemblys dépendants, utilisez la **/reference** option.</span><span class="sxs-lookup"><span data-stu-id="28106-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4.  <span data-ttu-id="28106-118">Rendez le code de sérialisation généré disponible pour votre application en utilisant l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="28106-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="28106-119">Compiler le code de sérialisation généré dans un assembly séparé portant le nom [*assembly d’origine*]. .XmlSerializers.dll (par exemple, MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="28106-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="28106-120">Votre application doit être en mesure de charger l'assembly, qui doit être signé avec la même clé que l'assembly d'origine.</span><span class="sxs-lookup"><span data-stu-id="28106-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="28106-121">Si vous recompilez l'assembly d'origine, vous devez régénérer l'assembly de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="28106-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="28106-122">Compilez le code de sérialisation généré dans un assembly distinct et utilisez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> sur le contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="28106-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="28106-123">Définissez les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> pour pointer vers l'assembly de sérialisation compilé.</span><span class="sxs-lookup"><span data-stu-id="28106-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="28106-124">Compilez le code de sérialisation généré dans votre assembly d'application et ajoutez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> au contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="28106-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="28106-125">Ne définissez pas les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="28106-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="28106-126">L'assembly de sérialisation par défaut est supposé être l'assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="28106-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="28106-127">Pour générer le code de sérialisation XmlSerializer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="28106-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1.  <span data-ttu-id="28106-128">Créer le service WCF et le client projets dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28106-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="28106-129">Ensuite, ajoutez une référence de service au projet client.</span><span class="sxs-lookup"><span data-stu-id="28106-129">Then, add a service reference to the client project.</span></span>  
  
2.  <span data-ttu-id="28106-130">Ajouter un <xref:System.ServiceModel.XmlSerializerFormatAttribute> au contrat de service dans le *reference.cs* fichier dans le projet d’application cliente sous **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="28106-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="28106-131">Notez que vous devez afficher tous les fichiers dans **l’Explorateur de solutions** pour afficher ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="28106-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3.  <span data-ttu-id="28106-132">Générez l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="28106-132">Build the client app.</span></span>  
  
4.  <span data-ttu-id="28106-133">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un sérialiseur prégénéré *.cs* fichier à l’aide de la commande :</span><span class="sxs-lookup"><span data-stu-id="28106-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="28106-134">L’argument assemblyPath Spécifie le chemin d’accès à l’assembly client WCF.</span><span class="sxs-lookup"><span data-stu-id="28106-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="28106-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="28106-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="28106-136">Le *WCFClient.XmlSerializers.dll.cs* fichier sera généré.</span><span class="sxs-lookup"><span data-stu-id="28106-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5.  <span data-ttu-id="28106-137">Compilez l’assembly de sérialisation prégénéré est réservé.</span><span class="sxs-lookup"><span data-stu-id="28106-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="28106-138">En fonction de l’exemple à l’étape précédente, la commande de compilation serait le suivant :</span><span class="sxs-lookup"><span data-stu-id="28106-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="28106-139">Assurez-vous que le texte généré *WCFClient.XmlSerializers.dll* est dans le même répertoire que l’application cliente, qui est *WCFClient.exe* dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="28106-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6.  <span data-ttu-id="28106-140">Exécutez l’application cliente comme d’habitude.</span><span class="sxs-lookup"><span data-stu-id="28106-140">Run the client app as usual.</span></span> <span data-ttu-id="28106-141">L’assembly de sérialisation prégénéré servira.</span><span class="sxs-lookup"><span data-stu-id="28106-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28106-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="28106-142">Example</span></span>  
 <span data-ttu-id="28106-143">La commande suivante génère des types de sérialisation pour les types `XmlSerializer` que les contrats de service de l'assembly utilisent.</span><span class="sxs-lookup"><span data-stu-id="28106-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="28106-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28106-144">See Also</span></span>  
 [<span data-ttu-id="28106-145">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="28106-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
