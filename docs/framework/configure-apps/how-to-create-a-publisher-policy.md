---
title: "Comment : créer une stratégie d'éditeur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 182882d33772054c7ac4208ca9571fa8018c2a07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="2a286-102">Comment : créer une stratégie d'éditeur</span><span class="sxs-lookup"><span data-stu-id="2a286-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="2a286-103">Les fournisseurs d’assemblys peuvent indiquer que les applications doivent utiliser une version plus récente d’un assembly en incluant un fichier de stratégie de serveur de publication avec l’assembly mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="2a286-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="2a286-104">Le fichier de stratégie d’éditeur spécifie la redirection d’assembly et les paramètres de base de code et utilise le même format comme un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2a286-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="2a286-105">Le fichier de stratégie d’éditeur est compilé dans un assembly et placé dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2a286-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="2a286-106">Il existe trois étapes impliquées dans la création d’une stratégie d’éditeur :</span><span class="sxs-lookup"><span data-stu-id="2a286-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="2a286-107">Créez un fichier de stratégie du serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="2a286-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="2a286-108">Créer un assembly de stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="2a286-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="2a286-109">Ajoutez l’assembly de stratégie du serveur de publication dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2a286-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="2a286-110">Le schéma de la stratégie d’éditeur est décrit dans [redirection des Versions d’Assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="2a286-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="2a286-111">L’exemple suivant montre un éditeur de fichier de stratégie qui redirige une version de `myAssembly` à un autre.</span><span class="sxs-lookup"><span data-stu-id="2a286-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2a286-112">Pour savoir comment spécifier une base de code, consultez [spécifiant l’emplacement d’un Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="2a286-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="2a286-113">Création de l’Assembly de stratégie d’éditeur</span><span class="sxs-lookup"><span data-stu-id="2a286-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="2a286-114">Utilisez le [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer l’assembly de stratégie du serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="2a286-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="2a286-115">Pour créer un assembly de stratégie d’éditeur</span><span class="sxs-lookup"><span data-stu-id="2a286-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="2a286-116">Tapez la commande suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="2a286-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="2a286-117">**Al /link :** *publisherPolicyFile* **/out :** *publisherPolicyAssemblyFile* **/keyfile :**  *keyPairFile* **/platform :** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="2a286-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="2a286-118">Dans cette commande :</span><span class="sxs-lookup"><span data-stu-id="2a286-118">In this command:</span></span>  
  
    -   <span data-ttu-id="2a286-119">Le *publisherPolicyFile* argument est le nom du fichier de stratégie de serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="2a286-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="2a286-120">Le *publisherPolicyAssemblyFile* argument est le nom de l’assembly de stratégie d’éditeur qui résulte de cette commande.</span><span class="sxs-lookup"><span data-stu-id="2a286-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="2a286-121">Le nom de fichier d’assembly doit suivre le format :</span><span class="sxs-lookup"><span data-stu-id="2a286-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="2a286-122">**stratégie.**</span><span class="sxs-lookup"><span data-stu-id="2a286-122">**policy.**</span></span> <span data-ttu-id="2a286-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="2a286-123">*majorNumber* **.**</span></span> <span data-ttu-id="2a286-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="2a286-124">*minorNumber* **.**</span></span> <span data-ttu-id="2a286-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="2a286-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="2a286-126">Le *keyPairFile* argument est le nom du fichier contenant la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="2a286-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="2a286-127">Vous devez signer l’assembly et l’assembly de stratégie d’éditeur avec la même paire de clés.</span><span class="sxs-lookup"><span data-stu-id="2a286-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="2a286-128">Le *processorArchitecture* argument identifie la plateforme ciblée par un assembly spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="2a286-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2a286-129">La possibilité de cibler une architecture de processeur spécifique est nouvelle dans .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a286-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="2a286-130">La commande suivante crée un assembly de stratégie d’éditeur appelé `policy.1.0.myAssembly` à partir d’un fichier de stratégie d’éditeur appelé `pub.config`, assigne un nom fort à l’assembly à l’aide de la paire de clés dans le `sgKey.snk` de fichiers et spécifie que l’assembly cible la x86 architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="2a286-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="2a286-131">L’assembly de stratégie du serveur de publication doit correspondre à l’architecture de processeur de l’assembly auquel il s’applique.</span><span class="sxs-lookup"><span data-stu-id="2a286-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="2a286-132">Par conséquent, si votre assembly a un <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valeur <xref:System.Reflection.ProcessorArchitecture.MSIL>, l’assembly de stratégie d’éditeur pour cet assembly doit être créé avec `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="2a286-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="2a286-133">Vous devez fournir un distinct assembly de stratégie d’éditeur pour chaque assembly spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="2a286-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="2a286-134">Une conséquence de cette règle est que pour modifier l’architecture de processeur pour un assembly, vous devez modifier le composant majeure ou mineure du numéro de version, afin que vous pouvez fournir un nouvel assembly de stratégie de serveur de publication avec l’architecture de processeur correcte.</span><span class="sxs-lookup"><span data-stu-id="2a286-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="2a286-135">L’ancien assembly de stratégie d’éditeur ne peut pas traiter votre assembly une fois que votre assembly possède une architecture de processeur différente.</span><span class="sxs-lookup"><span data-stu-id="2a286-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="2a286-136">Une autre conséquence est que l’éditeur de liens version 2.0 ne peut pas être utilisé pour créer un assembly de stratégie d’éditeur pour un assembly compilé à l’aide de versions antérieures du .NET Framework, car elle spécifie toujours architecture de processeur.</span><span class="sxs-lookup"><span data-stu-id="2a286-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="2a286-137">Ajout de l’Assembly de stratégie de serveur de publication dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="2a286-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="2a286-138">Utilisez le [l’outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour ajouter l’assembly de stratégie de serveur de publication dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2a286-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="2a286-139">Pour ajouter l’assembly de stratégie de serveur de publication dans le global assembly cache</span><span class="sxs-lookup"><span data-stu-id="2a286-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="2a286-140">Tapez la commande suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="2a286-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="2a286-141">**gacutil /i***publisherPolicyAssemblyFile* </span><span class="sxs-lookup"><span data-stu-id="2a286-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="2a286-142">La commande suivante ajoute `policy.1.0.myAssembly.dll` dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="2a286-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2a286-143">L’assembly de stratégie d’éditeur ne peut pas être ajouté dans le global assembly cache, sauf si le fichier de stratégie de serveur de publication d’origine se trouve dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2a286-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a286-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a286-144">See Also</span></span>  
 [<span data-ttu-id="2a286-145">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="2a286-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="2a286-146">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="2a286-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="2a286-147">Configuration d'applications</span><span class="sxs-lookup"><span data-stu-id="2a286-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="2a286-148">Configuration des applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2a286-148">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="2a286-149">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="2a286-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2a286-150">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="2a286-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2a286-151">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="2a286-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
