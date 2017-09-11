---
title: /Link (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 71ecefc898ca37cbf7299d97518e1ce2547a58da
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="link-visual-basic"></a><span data-ttu-id="722aa-102">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722aa-102">/link (Visual Basic)</span></span>
<span data-ttu-id="722aa-103">Entraîne le compilateur à rendre les informations de type COM dans les assemblys spécifiés disponibles pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="722aa-103">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="722aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="722aa-104">Syntax</span></span>  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="722aa-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="722aa-105">Arguments</span></span>  
  
|<span data-ttu-id="722aa-106">Terme</span><span class="sxs-lookup"><span data-stu-id="722aa-106">Term</span></span>|<span data-ttu-id="722aa-107">Définition</span><span class="sxs-lookup"><span data-stu-id="722aa-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="722aa-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="722aa-108">Required.</span></span> <span data-ttu-id="722aa-109">Liste délimitée par des virgules des noms de fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="722aa-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="722aa-110">Si le nom de fichier contient un espace, placez le nom entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="722aa-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="722aa-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="722aa-111">Remarks</span></span>  
 <span data-ttu-id="722aa-112">La `/link` option vous permet de déployer une application qui a des informations de type incorporées.</span><span class="sxs-lookup"><span data-stu-id="722aa-112">The `/link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="722aa-113">L’application peut ensuite utiliser des types dans un assembly de runtime qui implémentent les informations de type incorporées sans requérir une référence à l’assembly de runtime.</span><span class="sxs-lookup"><span data-stu-id="722aa-113">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="722aa-114">Si différentes versions de l’assembly de runtime sont publiées, l’application qui contient les informations de type incorporées peut fonctionner avec les différentes versions sans devoir être recompilée.</span><span class="sxs-lookup"><span data-stu-id="722aa-114">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="722aa-115">Pour obtenir un exemple, consultez [procédure pas à pas : incorporation de Types provenant d’assemblys gérés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="722aa-115">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="722aa-116">À l’aide de la `/link` option est particulièrement utile lorsque vous travaillez avec COM interop.</span><span class="sxs-lookup"><span data-stu-id="722aa-116">Using the `/link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="722aa-117">Vous pouvez incorporer des types COM afin que votre application ne requiert plus un assembly interop primaire (PIA) sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="722aa-117">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="722aa-118">La `/link` option indique au compilateur d’incorporer les informations de type COM de l’assembly PIA référencé dans le code compilé résultant.</span><span class="sxs-lookup"><span data-stu-id="722aa-118">The `/link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="722aa-119">Le type COM est identifié par la valeur CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="722aa-119">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="722aa-120">Par conséquent, votre application peut s’exécuter sur un ordinateur cible qui a installé les mêmes types COM avec les mêmes valeurs CLSID.</span><span class="sxs-lookup"><span data-stu-id="722aa-120">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="722aa-121">Les applications qui automatisent Microsoft Office sont un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="722aa-121">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="722aa-122">Étant donné que les applications comme Office gardent habituellement la même valeur CLSID dans différentes versions, votre application peut utiliser les types COM référencés comme que .NET Framework 4 ou version ultérieure est installé sur l’ordinateur cible et que votre application utilise les méthodes, propriétés ou événements qui sont inclus dans les types COM référencés.</span><span class="sxs-lookup"><span data-stu-id="722aa-122">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="722aa-123">La `/link` option incorpore uniquement des interfaces, des structures et des délégués.</span><span class="sxs-lookup"><span data-stu-id="722aa-123">The `/link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="722aa-124">L’incorporation de classes COM n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="722aa-124">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="722aa-125">Lorsque vous créez une instance d’un type COM incorporé dans votre code, vous devez créer l’instance à l’aide de l’interface appropriée.</span><span class="sxs-lookup"><span data-stu-id="722aa-125">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="722aa-126">Tente de créer une instance d’un type COM incorporé à l’aide de la coclasse provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="722aa-126">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="722aa-127">Pour définir le `/link` option [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ajoutez une référence d’assembly et affectez le `Embed Interop Types` propriété **true**.</span><span class="sxs-lookup"><span data-stu-id="722aa-127">To set the `/link` option in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="722aa-128">La valeur par défaut pour le `Embed Interop Types` propriété **false**.</span><span class="sxs-lookup"><span data-stu-id="722aa-128">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="722aa-129">Si vous liez à un assembly COM (Assembly A) qui lui-même référence un autre assembly COM (Assembly B), vous devez également lier à l’Assembly B si une des opérations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="722aa-129">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
-   <span data-ttu-id="722aa-130">Un type à partir de l’Assembly A hérite d’un type ou implémente une interface à partir de l’Assembly B.</span><span class="sxs-lookup"><span data-stu-id="722aa-130">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="722aa-131">Un champ, une propriété, un événement ou une méthode qui a un type de paramètre ou type de retour de l’Assembly B est appelé.</span><span class="sxs-lookup"><span data-stu-id="722aa-131">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="722aa-132">Utilisez [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) pour spécifier le répertoire dans lequel sont trouve une ou plusieurs références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="722aa-132">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="722aa-133">Comme le [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur, la `/link` option du compilateur utilise le fichier réponse Vbc.rsp, qui référence fréquemment utilisés [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys.</span><span class="sxs-lookup"><span data-stu-id="722aa-133">Like the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) compiler option, the `/link` compiler option uses the Vbc.rsp response file, which references frequently used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span> <span data-ttu-id="722aa-134">Utilisez le [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) option du compilateur si vous ne souhaitez pas que le compilateur utilise le fichier Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="722aa-134">Use the [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="722aa-135">La forme abrégée de `/link` est `/l`.</span><span class="sxs-lookup"><span data-stu-id="722aa-135">The short form of `/link` is `/l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="722aa-136">Types imbriqués et génériques</span><span class="sxs-lookup"><span data-stu-id="722aa-136">Generics and Embedded Types</span></span>  
 <span data-ttu-id="722aa-137">Les sections suivantes décrivent les limitations sur l’utilisation de types génériques dans les applications qui incorporent des types d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="722aa-137">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="722aa-138">Interfaces génériques</span><span class="sxs-lookup"><span data-stu-id="722aa-138">Generic Interfaces</span></span>  
 <span data-ttu-id="722aa-139">Impossible d’utiliser des interfaces génériques incorporées depuis un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="722aa-139">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="722aa-140">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="722aa-140">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="722aa-141">[!code-vb[VbLinkCompiler n °&1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="722aa-141">[!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]</span></span>  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="722aa-142">Types qui ont des paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="722aa-142">Types That Have Generic Parameters</span></span>  
 <span data-ttu-id="722aa-143">Types qui ont un paramètre générique dont le type est incorporé depuis un assembly d’interopérabilité ne peut pas être utilisées si ce type est d’un assembly externe.</span><span class="sxs-lookup"><span data-stu-id="722aa-143">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="722aa-144">Cette restriction ne s’applique pas aux interfaces.</span><span class="sxs-lookup"><span data-stu-id="722aa-144">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="722aa-145">Par exemple, considérez la <xref:Microsoft.Office.Interop.Excel.Range>interface qui est définie dans le <xref:Microsoft.Office.Interop.Excel>assembly.</xref:Microsoft.Office.Interop.Excel> </xref:Microsoft.Office.Interop.Excel.Range></span><span class="sxs-lookup"><span data-stu-id="722aa-145">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="722aa-146">Si une bibliothèque incorpore des types d’interopérabilité de la <xref:Microsoft.Office.Interop.Excel>assembly et expose une méthode qui retourne un type générique qui a un paramètre dont le type est le <xref:Microsoft.Office.Interop.Excel.Range>de l’interface, que méthode doit retourner une interface générique, comme indiqué dans l’exemple de code suivant.</xref:Microsoft.Office.Interop.Excel.Range> </xref:Microsoft.Office.Interop.Excel></span><span class="sxs-lookup"><span data-stu-id="722aa-146">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 <span data-ttu-id="722aa-147">[!code-vb[VbLinkCompiler n °&2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="722aa-147">[!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]</span></span>  
<span data-ttu-id="722aa-148">[!code-vb[VbLinkCompiler n °&3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="722aa-148">[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]</span></span>  
<span data-ttu-id="722aa-149">[!code-vb[VbLinkCompiler n °&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="722aa-149">[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]</span></span>  
  
 <span data-ttu-id="722aa-150">Dans l’exemple suivant, le code client peut appeler la méthode qui retourne le <xref:System.Collections.IList>interface générique sans erreur.</xref:System.Collections.IList></span><span class="sxs-lookup"><span data-stu-id="722aa-150">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 <span data-ttu-id="722aa-151">[!code-vb[VbLinkCompiler n °&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="722aa-151">[!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="722aa-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="722aa-152">Example</span></span>  
 <span data-ttu-id="722aa-153">Le code suivant compile le fichier source `OfficeApp.vb` et référence des assemblys à partir de `COMData1.dll` et `COMData2.dll` pour produire `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="722aa-153">The following code compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="722aa-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="722aa-154">See Also</span></span>  
 <span data-ttu-id="722aa-155">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="722aa-155">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="722aa-156"> [Procédure pas à pas : Incorporation de Types provenant d’assemblys managés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span><span class="sxs-lookup"><span data-stu-id="722aa-156"> [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) </span></span>  
<span data-ttu-id="722aa-157"> [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="722aa-157"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="722aa-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="722aa-158"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="722aa-159"> [/LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) </span><span class="sxs-lookup"><span data-stu-id="722aa-159"> [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) </span></span>  
<span data-ttu-id="722aa-160"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="722aa-160"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="722aa-161"> [Introduction à COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span><span class="sxs-lookup"><span data-stu-id="722aa-161"> [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)</span></span>
