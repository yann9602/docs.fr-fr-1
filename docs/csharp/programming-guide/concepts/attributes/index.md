---
title: Attributs (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2993ef3f424aa6487681e194f21e0f82193342ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-c"></a><span data-ttu-id="600ed-102">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-102">Attributes (C#)</span></span>
<span data-ttu-id="600ed-103">Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.).</span><span class="sxs-lookup"><span data-stu-id="600ed-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="600ed-104">Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*.</span><span class="sxs-lookup"><span data-stu-id="600ed-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="600ed-105">Pour plus d’informations, consultez [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="600ed-105">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="600ed-106">Les attributs ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="600ed-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="600ed-107">Les attributs ajoutent des métadonnées à un programme.</span><span class="sxs-lookup"><span data-stu-id="600ed-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="600ed-108">Les *métadonnées* sont des informations sur les types définis dans un programme.</span><span class="sxs-lookup"><span data-stu-id="600ed-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="600ed-109">Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="600ed-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="600ed-110">Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="600ed-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="600ed-111">Pour plus d’informations, consultez [Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="600ed-111">For more information, see, [Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="600ed-112">Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="600ed-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="600ed-113">Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="600ed-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="600ed-114">Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion.</span><span class="sxs-lookup"><span data-stu-id="600ed-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="600ed-115">Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="600ed-115">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="600ed-116">Utilisation d'attributs</span><span class="sxs-lookup"><span data-stu-id="600ed-116">Using Attributes</span></span>  
 <span data-ttu-id="600ed-117">Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide.</span><span class="sxs-lookup"><span data-stu-id="600ed-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="600ed-118">En C#, vous spécifiez un attribut en plaçant son nom, entouré de crochets ([]), au-dessus de la déclaration de l’entité à laquelle il s’applique.</span><span class="sxs-lookup"><span data-stu-id="600ed-118">In C#, you specify an attribute by placing the name of the attribute, enclosed in square brackets ([]), above the declaration of the entity to which it applies.</span></span>  
  
 <span data-ttu-id="600ed-119">Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :</span><span class="sxs-lookup"><span data-stu-id="600ed-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 <span data-ttu-id="600ed-120">Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme suit :</span><span class="sxs-lookup"><span data-stu-id="600ed-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 <span data-ttu-id="600ed-121">Plusieurs attributs peuvent être placés dans une déclaration :</span><span class="sxs-lookup"><span data-stu-id="600ed-121">More than one attribute can be placed on a declaration:</span></span>  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 <span data-ttu-id="600ed-122">Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée.</span><span class="sxs-lookup"><span data-stu-id="600ed-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="600ed-123"><xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :</span><span class="sxs-lookup"><span data-stu-id="600ed-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="600ed-124">Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="600ed-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="600ed-125">Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code.</span><span class="sxs-lookup"><span data-stu-id="600ed-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="600ed-126">Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="600ed-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="600ed-127">Paramètres d’attributs</span><span class="sxs-lookup"><span data-stu-id="600ed-127">Attribute Parameters</span></span>  
 <span data-ttu-id="600ed-128">Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés.</span><span class="sxs-lookup"><span data-stu-id="600ed-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="600ed-129">Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peuvent pas être omis ; les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="600ed-129">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="600ed-130">Les paramètres positionnels sont spécifiés en premier.</span><span class="sxs-lookup"><span data-stu-id="600ed-130">Positional parameters are specified first.</span></span> <span data-ttu-id="600ed-131">Par exemple, ces trois attributs sont équivalents :</span><span class="sxs-lookup"><span data-stu-id="600ed-131">For example, these three attributes are equivalent:</span></span>  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 <span data-ttu-id="600ed-132">Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés.</span><span class="sxs-lookup"><span data-stu-id="600ed-132">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="600ed-133">Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis.</span><span class="sxs-lookup"><span data-stu-id="600ed-133">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="600ed-134">Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="600ed-134">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="600ed-135">Cibles d'attribut</span><span class="sxs-lookup"><span data-stu-id="600ed-135">Attribute Targets</span></span>  
 <span data-ttu-id="600ed-136">La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut.</span><span class="sxs-lookup"><span data-stu-id="600ed-136">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="600ed-137">Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier.</span><span class="sxs-lookup"><span data-stu-id="600ed-137">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="600ed-138">Par défaut, un attribut s’applique à l’élément qu’il précède.</span><span class="sxs-lookup"><span data-stu-id="600ed-138">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="600ed-139">Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.</span><span class="sxs-lookup"><span data-stu-id="600ed-139">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="600ed-140">Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="600ed-140">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```csharp  
[target : attribute-list]  
```  
  
 <span data-ttu-id="600ed-141">La liste des valeurs `target` possibles est présentée dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="600ed-141">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="600ed-142">Valeur cible</span><span class="sxs-lookup"><span data-stu-id="600ed-142">Target value</span></span>|<span data-ttu-id="600ed-143">S'applique à</span><span class="sxs-lookup"><span data-stu-id="600ed-143">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="600ed-144">Assembly entier</span><span class="sxs-lookup"><span data-stu-id="600ed-144">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="600ed-145">Module d’assembly actuel</span><span class="sxs-lookup"><span data-stu-id="600ed-145">Current assembly module</span></span>|  
|`field`|<span data-ttu-id="600ed-146">Champ dans une classe ou un struct</span><span class="sxs-lookup"><span data-stu-id="600ed-146">Field in a class or a struct</span></span>|  
|`event`|<span data-ttu-id="600ed-147">Événement</span><span class="sxs-lookup"><span data-stu-id="600ed-147">Event</span></span>|  
|`method`|<span data-ttu-id="600ed-148">Méthode ou accesseurs de propriété `get` et `set`</span><span class="sxs-lookup"><span data-stu-id="600ed-148">Method or `get` and `set` property accessors</span></span>|  
|`param`|<span data-ttu-id="600ed-149">Paramètres de méthode ou paramètres d’accesseur de propriété `set`</span><span class="sxs-lookup"><span data-stu-id="600ed-149">Method parameters or `set` property accessor parameters</span></span>|  
|`property`|<span data-ttu-id="600ed-150">Propriété</span><span class="sxs-lookup"><span data-stu-id="600ed-150">Property</span></span>|  
|`return`|<span data-ttu-id="600ed-151">Valeur de retour d’une méthode, indexeur de propriété ou accesseur de propriété `get`</span><span class="sxs-lookup"><span data-stu-id="600ed-151">Return value of a method, property indexer, or `get` property accessor</span></span>|  
|`type`|<span data-ttu-id="600ed-152">Struct, classe, interface, énumération ou délégué</span><span class="sxs-lookup"><span data-stu-id="600ed-152">Struct, class, interface, enum, or delegate</span></span>|  
  
 <span data-ttu-id="600ed-153">L’exemple suivant montre comment appliquer des attributs à des modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="600ed-153">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="600ed-154">Pour plus d’informations, consultez [Attributs courants (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="600ed-154">For more information, see [Common Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 <span data-ttu-id="600ed-155">L’exemple suivant montre comment appliquer des attributs à des méthodes, des paramètres de méthode et des valeurs de retour de méthode en C#.</span><span class="sxs-lookup"><span data-stu-id="600ed-155">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  <span data-ttu-id="600ed-156">Quelle que soit la cible sur laquelle `SomeAttr` est défini comme étant valide, la cible `return` doit être spécifiée, même si `SomeAttr` a été défini pour s’appliquer seulement aux valeurs de retour.</span><span class="sxs-lookup"><span data-stu-id="600ed-156">Regardless of the targets on which `SomeAttr` is defined to be valid, the `return` target has to be specified, even if `SomeAttr` were defined to apply only to return values.</span></span> <span data-ttu-id="600ed-157">En d’autres termes, le compilateur n’utilise pas les informations `AttributeUsage` pour résoudre les cibles d’attribut ambiguës.</span><span class="sxs-lookup"><span data-stu-id="600ed-157">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="600ed-158">Pour plus d’informations, consultez [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span><span class="sxs-lookup"><span data-stu-id="600ed-158">For more information, see [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).</span></span>  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="600ed-159">Utilisations courantes des attributs</span><span class="sxs-lookup"><span data-stu-id="600ed-159">Common Uses for Attributes</span></span>  
 <span data-ttu-id="600ed-160">La liste suivante comprend certaines des utilisations courantes des attributs dans le code :</span><span class="sxs-lookup"><span data-stu-id="600ed-160">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="600ed-161">Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="600ed-161">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="600ed-162">Pour plus d'informations, consultez <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="600ed-162">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="600ed-163">Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif.</span><span class="sxs-lookup"><span data-stu-id="600ed-163">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="600ed-164">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="600ed-164">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="600ed-165">Décrire les propriétés COM des classes, méthodes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="600ed-165">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="600ed-166">Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="600ed-166">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="600ed-167">Décrire un assembly : titre, version, description ou marque.</span><span class="sxs-lookup"><span data-stu-id="600ed-167">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="600ed-168">Décrire les membres d’une classe à sérialiser à des fins de persistance.</span><span class="sxs-lookup"><span data-stu-id="600ed-168">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="600ed-169">Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="600ed-169">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="600ed-170">Décrire les exigences de sécurité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="600ed-170">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="600ed-171">Spécifier les caractéristiques employées pour appliquer la sécurité.</span><span class="sxs-lookup"><span data-stu-id="600ed-171">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="600ed-172">Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.</span><span class="sxs-lookup"><span data-stu-id="600ed-172">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="600ed-173">Obtenir des informations sur l’appelant d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="600ed-173">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="600ed-174">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="600ed-174">Related Sections</span></span>  
 <span data-ttu-id="600ed-175">Pour plus d'informations, voir :</span><span class="sxs-lookup"><span data-stu-id="600ed-175">For more information, see:</span></span>  
  
-   [<span data-ttu-id="600ed-176">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-176">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="600ed-177">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-177">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="600ed-178">Guide pratique pour créer une union C/C++ à l’aide d’attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-178">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="600ed-179">Attributs courants (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-179">Common Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="600ed-180">Informations relatives à l’appelant (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-180">Caller Information (C#)</span></span>](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="600ed-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="600ed-181">See Also</span></span>  
 [<span data-ttu-id="600ed-182">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="600ed-182">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="600ed-183">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="600ed-183">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="600ed-184">Attributs</span><span class="sxs-lookup"><span data-stu-id="600ed-184">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
