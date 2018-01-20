---
title: "Comment : configurer les composants COM .NET Framework pour l'activation sans inscription"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdae288650a0ff7b1a34b3a38a231d3da6caf560
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="ecfb2-102">Comment : configurer les composants COM .NET Framework pour l'activation sans inscription</span><span class="sxs-lookup"><span data-stu-id="ecfb2-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="ecfb2-103">L’activation sans inscription des composants .NET Framework n’est que légèrement plus compliquée que pour les composants COM.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="ecfb2-104">L’installation requiert deux manifestes :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="ecfb2-105">Les applications COM doivent avoir un manifeste d’application de style Win32 pour identifier le composant managé.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="ecfb2-106">Les composants .NET Framework doivent avoir un manifeste de composant pour les informations d’activation nécessaires au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="ecfb2-107">Cette rubrique explique comment associer un manifeste d’application à une application, comment associer un manifeste de composant à un composant et comment incorporer un manifeste de composant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="ecfb2-108">Pour créer un manifeste d’application</span><span class="sxs-lookup"><span data-stu-id="ecfb2-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="ecfb2-109">À l’aide d’un éditeur XML, créez (ou modifiez) le manifeste d’application de l’application COM qui interagit avec un ou plusieurs composants managés.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="ecfb2-110">Insérez l’en-tête standard suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="ecfb2-111">Pour plus d’informations sur les éléments de manifeste et leurs attributs, consultez [manifestes d’Application](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).</span><span class="sxs-lookup"><span data-stu-id="ecfb2-111">For information about manifest elements and their attributes, see [Application Manifests](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).</span></span>  
  
3.  <span data-ttu-id="ecfb2-112">Identifiez le propriétaire du manifeste.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="ecfb2-113">Dans l’exemple suivant, le fichier manifeste appartient à `myComApp` version 1.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="ecfb2-114">Identifiez les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-114">Identify dependent assemblies.</span></span> <span data-ttu-id="ecfb2-115">Dans l’exemple suivant, `myComApp` dépend de `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="ecfb2-116">Nommez et enregistrez le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-116">Save and name the manifest file.</span></span> <span data-ttu-id="ecfb2-117">Le nom d’un manifeste d’application est le nom de l’exécutable d’assembly suivi de l’extension .manifest.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="ecfb2-118">Par exemple, le nom du fichier manifeste d’application de myComApp.exe est myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="ecfb2-119">Vous pouvez installer un manifeste d’application dans le même répertoire que l’application COM.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="ecfb2-120">Vous pouvez également l’ajouter en tant que ressource au fichier .exe de l’application.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="ecfb2-121">Pour plus d’informations, pour plus d’informations, consultez [à propos des assemblys côte à côte](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).</span><span class="sxs-lookup"><span data-stu-id="ecfb2-121">For additional information, For more information, see [About Side-by-Side Assemblies](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="ecfb2-122">Pour créer un manifeste de composant</span><span class="sxs-lookup"><span data-stu-id="ecfb2-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="ecfb2-123">À l’aide d’un éditeur XML, créez un manifeste de composant pour décrire l’assembly managé.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="ecfb2-124">Insérez l’en-tête standard suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="ecfb2-125">Identifiez le propriétaire du fichier.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-125">Identify the owner of the file.</span></span> <span data-ttu-id="ecfb2-126">L’élément `<assemblyIdentity>` de l’élément `<dependentAssembly>` dans le fichier manifeste d’application doit correspondre à celui figurant dans le manifeste de composant.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="ecfb2-127">Dans l’exemple suivant, le fichier manifeste appartient à `myManagedComp` version 1.2.3.4.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  <span data-ttu-id="ecfb2-128">Identifiez chaque classe dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-128">Identify each class in the assembly.</span></span> <span data-ttu-id="ecfb2-129">Utilisez l’élément `<clrClass>` pour identifier de manière unique chaque classe dans l’assembly managé.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="ecfb2-130">L’élément, qui est un sous-élément de l’élément `<assembly>`, a les attributs décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="ecfb2-131">Attribut</span><span class="sxs-lookup"><span data-stu-id="ecfb2-131">Attribute</span></span>|<span data-ttu-id="ecfb2-132">Description</span><span class="sxs-lookup"><span data-stu-id="ecfb2-132">Description</span></span>|<span data-ttu-id="ecfb2-133">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="ecfb2-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="ecfb2-134">Identificateur qui spécifie la classe à activer.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="ecfb2-135">Oui</span><span class="sxs-lookup"><span data-stu-id="ecfb2-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="ecfb2-136">Chaîne qui informe l’utilisateur sur le composant.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-136">A string that informs the user about the component.</span></span> <span data-ttu-id="ecfb2-137">L’attribut par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-137">An empty string is the default.</span></span>|<span data-ttu-id="ecfb2-138">Non</span><span class="sxs-lookup"><span data-stu-id="ecfb2-138">No</span></span>|  
    |`name`|<span data-ttu-id="ecfb2-139">Chaîne représentant la classe managée.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-139">A string that represents the managed class.</span></span>|<span data-ttu-id="ecfb2-140">Oui</span><span class="sxs-lookup"><span data-stu-id="ecfb2-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="ecfb2-141">Identificateur à utiliser pour une activation à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="ecfb2-142">Non</span><span class="sxs-lookup"><span data-stu-id="ecfb2-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="ecfb2-143">Modèle de thread COM.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-143">The COM threading model.</span></span> <span data-ttu-id="ecfb2-144">"Both" est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-144">"Both" is the default value.</span></span>|<span data-ttu-id="ecfb2-145">Non</span><span class="sxs-lookup"><span data-stu-id="ecfb2-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="ecfb2-146">Spécifie la version du CLR (Common Language Runtime) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="ecfb2-147">Si vous ne spécifiez pas cet attribut et que le CLR n’est pas déjà chargé, le composant est chargé avec la version du CLR la plus récente, antérieure à la version CLR 4.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="ecfb2-148">Si vous spécifiez v1.0.3705, v1.1.4322 ou v2.0.50727, la version passe automatiquement à la version du CLR installée la plus récente antérieure à la version CLR 4 (habituellement v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="ecfb2-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="ecfb2-149">Si une autre version du CLR est déjà chargée et que la version spécifiée peut être chargée in-process côte à côte, la version spécifiée est chargée ; sinon, le CLR chargé est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="ecfb2-150">Cela peut provoquer un échec de chargement.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-150">This might cause a load failure.</span></span>|<span data-ttu-id="ecfb2-151">Non</span><span class="sxs-lookup"><span data-stu-id="ecfb2-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="ecfb2-152">Identificateur de la bibliothèque de types qui contient les informations de type sur la classe.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="ecfb2-153">Non</span><span class="sxs-lookup"><span data-stu-id="ecfb2-153">No</span></span>|  
  
     <span data-ttu-id="ecfb2-154">Toutes les balises d’attribut respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="ecfb2-155">Vous pouvez obtenir des CLSID, des ProgID, des modèles de thread et la version du runtime en affichant la bibliothèque de types exportée de l’assembly à l’aide de l’explorateur d’objets OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="ecfb2-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="ecfb2-156">Le manifeste de composant suivant identifie deux classes, `testClass1` et `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="ecfb2-157">Nommez et enregistrez le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-157">Save and name the manifest file.</span></span> <span data-ttu-id="ecfb2-158">Le nom d’un manifeste de composant est le nom de la bibliothèque d’assemblys suivi de l’extension .manifest.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="ecfb2-159">Par exemple, le nom de myManagedComp.dll est myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="ecfb2-160">Vous devez incorporer le manifeste de composant en tant que ressource dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="ecfb2-161">Pour incorporer un manifeste de composant dans un assembly managé</span><span class="sxs-lookup"><span data-stu-id="ecfb2-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="ecfb2-162">Créez un script de ressources qui contient l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="ecfb2-163">Dans cette instruction, `myManagedComp.manifest` est le nom du manifeste de composant incorporé.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="ecfb2-164">Pour cet exemple, le nom du fichier de script est `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="ecfb2-165">Compilez le script à l’aide de l’outil Compilateur de ressources Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="ecfb2-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="ecfb2-166">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="ecfb2-167">Rc.exe génère le fichier de ressources `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="ecfb2-168">Compilez de nouveau le fichier source de l’assembly et spécifiez le fichier de ressources à l’aide de l’option **/win32res** :</span><span class="sxs-lookup"><span data-stu-id="ecfb2-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="ecfb2-169">`myresource.res` est de nouveau le nom du fichier de ressources contenant la ressource incorporée.</span><span class="sxs-lookup"><span data-stu-id="ecfb2-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecfb2-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecfb2-170">See Also</span></span>  
 [<span data-ttu-id="ecfb2-171">COM Interop sans inscription</span><span class="sxs-lookup"><span data-stu-id="ecfb2-171">Registration-Free COM Interop</span></span>](../../../docs/framework/interop/registration-free-com-interop.md)  
 [<span data-ttu-id="ecfb2-172">Configuration requise pour COM Interop sans inscription</span><span class="sxs-lookup"><span data-stu-id="ecfb2-172">Requirements for Registration-Free COM Interop</span></span>](http://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da)  
 [<span data-ttu-id="ecfb2-173">Configuration des composants COM pour l’Activation sans inscription</span><span class="sxs-lookup"><span data-stu-id="ecfb2-173">Configuring COM Components for Registration-Free Activation</span></span>](http://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe)  
 [<span data-ttu-id="ecfb2-174">Activation sans inscription de composants .NET : une procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="ecfb2-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](http://go.microsoft.com/fwlink/?LinkId=158812)
