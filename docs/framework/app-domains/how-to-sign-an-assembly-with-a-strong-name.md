---
title: "Comment : signer un assembly avec un nom fort"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: babd0f6a9b1babf02677d6c6c41c664e0a6541b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="68c70-102">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="68c70-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="68c70-103">Il existe plusieurs façons de signer un assembly avec un nom fort :</span><span class="sxs-lookup"><span data-stu-id="68c70-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="68c70-104">À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68c70-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="68c70-105">Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="68c70-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="68c70-106">À l’aide de l’utilitaire [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour lier un module de code .NET Framework (un fichier .netmodule) à un fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="68c70-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="68c70-107">À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code.</span><span class="sxs-lookup"><span data-stu-id="68c70-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="68c70-108">Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="68c70-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="68c70-109">À l'aide des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="68c70-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="68c70-110">Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="68c70-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="68c70-111">Pour plus d’informations sur la création d’une paire de clés, consultez [Comment : créer une paire de clés publique/privée](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="68c70-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="68c70-112">Pour créer et signer un assembly avec un nom fort à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="68c70-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="68c70-113">Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="68c70-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="68c70-114">Choisissez l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="68c70-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="68c70-115">Sélectionnez la zone **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="68c70-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="68c70-116">Dans la zone **Choisir un fichier de clé de nom fort**, choisissez **\<<Parcourir...>**, puis recherchez le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="68c70-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="68c70-117">Pour créer un fichier de clé, choisissez **\<<Nouveau...>** et entrez son nom dans la boîte de dialogue **Créer une clé de nom fort**.</span><span class="sxs-lookup"><span data-stu-id="68c70-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="68c70-118">Pour créer et signer un assembly avec un nom fort à l'aide de l'utilitaire Assembly Linker</span><span class="sxs-lookup"><span data-stu-id="68c70-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="68c70-119">À l’[invite de commandes Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="68c70-119">At the [Visual Studio Command Prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="68c70-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="68c70-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="68c70-121">où :</span><span class="sxs-lookup"><span data-stu-id="68c70-121">where:</span></span>  
  
     <span data-ttu-id="68c70-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="68c70-122">*assemblyName*</span></span>  
     <span data-ttu-id="68c70-123">Nom de l'assembly fortement signé (un fichier .dll ou .exe) que l'utilitaire Assembly Linker émettra.</span><span class="sxs-lookup"><span data-stu-id="68c70-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="68c70-124">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="68c70-124">*moduleName*</span></span>  
     <span data-ttu-id="68c70-125">Nom d’un module de code .NET Framework (un fichier .netmodule) qui inclut un ou plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="68c70-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="68c70-126">Vous pouvez créer un fichier .netmodule en compilant votre code avec le commutateur `/target:module` en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="68c70-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="68c70-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="68c70-127">*keyfileName*</span></span>  
     <span data-ttu-id="68c70-128">Nom du conteneur ou du fichier qui contient la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="68c70-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="68c70-129">L'utilitaire Assembly Linker interprète un chemin d'accès relatif en relation avec le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="68c70-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="68c70-130">L'exemple suivant signe l'assembly `MyAssembly.dll` avec un nom fort à l'aide du fichier de clé `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="68c70-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="68c70-131">Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="68c70-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="68c70-132">Pour signer un assembly avec un nom fort à l'aide d'attributs</span><span class="sxs-lookup"><span data-stu-id="68c70-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="68c70-133">Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="68c70-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="68c70-134">Compilez le fichier de code source normalement.</span><span class="sxs-lookup"><span data-stu-id="68c70-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68c70-135">Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source.</span><span class="sxs-lookup"><span data-stu-id="68c70-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="68c70-136">Vous pouvez ignorer les avertissements.</span><span class="sxs-lookup"><span data-stu-id="68c70-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="68c70-137">L'exemple de code suivant utilise l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> avec un fichier de clé nommé `keyfile.snk`, situé dans le répertoire où l'assembly est compilé.</span><span class="sxs-lookup"><span data-stu-id="68c70-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="68c70-138">Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="68c70-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="68c70-139">Pour plus d'informations, consultez [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="68c70-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="68c70-140">Pour signer un assembly avec un nom fort à l'aide du compilateur</span><span class="sxs-lookup"><span data-stu-id="68c70-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="68c70-141">Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++.</span><span class="sxs-lookup"><span data-stu-id="68c70-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="68c70-142">Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="68c70-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="68c70-143">Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.</span><span class="sxs-lookup"><span data-stu-id="68c70-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="68c70-144">Pour plus d’informations sur la signature différée, consultez [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="68c70-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="68c70-145">L'exemple suivant utilise le compilateur C# et signe l'assembly `UtilityLibrary.dll` avec un nom fort à l'aide du fichier de clé `sgKey.snk`.</span><span class="sxs-lookup"><span data-stu-id="68c70-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="68c70-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68c70-146">See Also</span></span>  
 [<span data-ttu-id="68c70-147">Création et utilisation d’assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="68c70-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="68c70-148">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="68c70-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="68c70-149">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="68c70-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="68c70-150">Temporisation de signature d'un assembly</span><span class="sxs-lookup"><span data-stu-id="68c70-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [<span data-ttu-id="68c70-151">Gestion d’assembly et signature de manifeste</span><span class="sxs-lookup"><span data-stu-id="68c70-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [<span data-ttu-id="68c70-152">Page Signature, Concepteur de projet</span><span class="sxs-lookup"><span data-stu-id="68c70-152">Signing Page, Project Designer</span></span>](https://msdn.microsoft.com/library/0k50fs3b)
