---
title: "Références aux éléments déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9b3847164b4e577a9265a746b9329218b4af928b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="21cd9-102">Références aux éléments déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21cd9-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="21cd9-103">Lorsque votre code fait référence à un élément déclaré, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur correspond au nom de la référence à la déclaration appropriée de ce nom.</span><span class="sxs-lookup"><span data-stu-id="21cd9-103">When your code refers to a declared element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="21cd9-104">Si plus d’un élément est déclaré avec le même nom, vous pouvez contrôler lequel de ces éléments doit être référencé par *éligible* son nom.</span><span class="sxs-lookup"><span data-stu-id="21cd9-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="21cd9-105">Le compilateur tente de correspondre à une référence de nom à une déclaration de nom avec la *plus petite portée*.</span><span class="sxs-lookup"><span data-stu-id="21cd9-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="21cd9-106">Cela signifie qu’il commence par le code qui effectue la référence et parcourt niveaux successifs d’éléments conteneurs.</span><span class="sxs-lookup"><span data-stu-id="21cd9-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="21cd9-107">L’exemple suivant montre des références à deux variables portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="21cd9-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="21cd9-108">L’exemple déclare deux variables, chacune nommée `totalCount`, à différents niveaux de portée dans le module `container`.</span><span class="sxs-lookup"><span data-stu-id="21cd9-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="21cd9-109">Lors de la procédure `showCount` affiche `totalCount` sans qualification, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur résout la référence à la déclaration avec la plus petite portée, à savoir la déclaration locale à l’intérieur de `showCount`.</span><span class="sxs-lookup"><span data-stu-id="21cd9-109">When the procedure `showCount` displays `totalCount` without qualification, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="21cd9-110">Lorsqu’il qualifie `totalCount` avec le module conteneur `container`, le compilateur résout la référence à la déclaration avec une portée plus large.</span><span class="sxs-lookup"><span data-stu-id="21cd9-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="21cd9-111">Qualifier un nom d’élément</span><span class="sxs-lookup"><span data-stu-id="21cd9-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="21cd9-112">Si vous souhaitez substituer ce processus de recherche et spécifier un nom déclaré dans une portée plus large, vous devez *qualifier* le nom de l’élément conteneur de la portée plus large.</span><span class="sxs-lookup"><span data-stu-id="21cd9-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="21cd9-113">Dans certains cas, vous devrez peut-être également qualifier l’élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="21cd9-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="21cd9-114">Qualifier un moyen de nom précèdent dans votre instruction source avec les informations qui identifient où l’élément cible est défini.</span><span class="sxs-lookup"><span data-stu-id="21cd9-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="21cd9-115">Cette information est appelée un *chaîne de qualification*.</span><span class="sxs-lookup"><span data-stu-id="21cd9-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="21cd9-116">Il peut inclure un ou plusieurs espaces de noms et un module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="21cd9-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="21cd9-117">La chaîne de qualification sans ambiguïté doit spécifier que le module, classe ou structure qui contient l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="21cd9-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="21cd9-118">Le conteneur peut se trouver dans un autre élément conteneur, généralement un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="21cd9-119">Vous devrez peut-être inclure plusieurs éléments conteneurs dans la chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="21cd9-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="21cd9-120">Pour accéder à un élément déclaré en qualifiant son nom</span><span class="sxs-lookup"><span data-stu-id="21cd9-120">To access a declared element by qualifying its name</span></span>  
  
1.  <span data-ttu-id="21cd9-121">Déterminer l’emplacement dans lequel l’élément a été défini.</span><span class="sxs-lookup"><span data-stu-id="21cd9-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="21cd9-122">Il peut s’agir d’un espace de noms, ou même d’une hiérarchie d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="21cd9-123">Dans l’espace de noms de niveau le plus bas, l’élément doit être contenu dans un module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="21cd9-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2.  <span data-ttu-id="21cd9-124">Déterminer un chemin d’accès de qualification basé sur l’emplacement de l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="21cd9-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="21cd9-125">Démarrer avec l’espace de noms de niveau supérieur, passez à l’espace de noms de niveau le plus bas et se terminer par le module, classe ou structure qui contient l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="21cd9-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="21cd9-126">Chaque élément dans le chemin d’accès doit contenir l’élément qui le suit.</span><span class="sxs-lookup"><span data-stu-id="21cd9-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="21cd9-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="21cd9-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3.  <span data-ttu-id="21cd9-128">Préparer la chaîne de qualification de l’élément cible.</span><span class="sxs-lookup"><span data-stu-id="21cd9-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="21cd9-129">Placez un point (`.`) après chaque élément dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="21cd9-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="21cd9-130">Votre application doit avoir accès à chaque élément dans votre chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="21cd9-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  <span data-ttu-id="21cd9-131">Écrire l’expression ou une instruction d’assignation qui fait référence à l’élément cible de façon normale.</span><span class="sxs-lookup"><span data-stu-id="21cd9-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  <span data-ttu-id="21cd9-132">Faites précéder le nom de l’élément cible avec la chaîne de qualification.</span><span class="sxs-lookup"><span data-stu-id="21cd9-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="21cd9-133">Le nom doit suivre immédiatement le point (`.`) qui suit le module, classe ou structure qui contient l’élément.</span><span class="sxs-lookup"><span data-stu-id="21cd9-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="21cd9-134">Le compilateur utilise la chaîne de qualification pour rechercher une déclaration claire et non équivoque à laquelle il peut correspondre à la référence d’élément cible.</span><span class="sxs-lookup"><span data-stu-id="21cd9-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="21cd9-135">Vous devrez peut-être également qualifier une référence de nom si votre application a accès à plusieurs éléments de programmation qui porte le même nom.</span><span class="sxs-lookup"><span data-stu-id="21cd9-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="21cd9-136">Par exemple, le <xref:System.Windows.Forms> et <xref:System.Web.UI.WebControls> contiennent des espaces de noms à la fois un `Label` classe (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> et <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="21cd9-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="21cd9-137">Si votre application utilise à la fois, ou si elle définit sa propre `Label` (classe), vous devez distinguer les différents `Label` objets.</span><span class="sxs-lookup"><span data-stu-id="21cd9-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="21cd9-138">Inclure l’alias d’espace de noms ou d’importation dans la déclaration de variable.</span><span class="sxs-lookup"><span data-stu-id="21cd9-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="21cd9-139">L’exemple suivant utilise l’alias d’importation.</span><span class="sxs-lookup"><span data-stu-id="21cd9-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="21cd9-140">Membres d’autres éléments conteneurs</span><span class="sxs-lookup"><span data-stu-id="21cd9-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="21cd9-141">Lorsque vous utilisez un membre non partagé d’une autre classe ou structure, vous devez tout d’abord qualifier le nom du membre avec une variable ou une expression qui pointe vers une instance de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="21cd9-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="21cd9-142">Dans l’exemple suivant, `demoClass` est une instance d’une classe nommée `class1`.</span><span class="sxs-lookup"><span data-stu-id="21cd9-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="21cd9-143">Vous ne pouvez pas utiliser le nom de la classe pour qualifier un membre qui n’est pas [partagé](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="21cd9-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="21cd9-144">Vous devez d’abord créer une instance dans une variable objet (dans ce cas `demoClass`) et de le référencer par le nom de variable.</span><span class="sxs-lookup"><span data-stu-id="21cd9-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="21cd9-145">Si une classe ou une structure a un `Shared` membre, vous pouvez qualifier ce membre avec le nom de classe ou structure, ou avec une variable ou une expression qui pointe vers une instance.</span><span class="sxs-lookup"><span data-stu-id="21cd9-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="21cd9-146">Un module n’a pas d’instances séparées et tous ses membres sont `Shared` par défaut.</span><span class="sxs-lookup"><span data-stu-id="21cd9-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="21cd9-147">Par conséquent, vous qualifiez un membre de module avec le nom du module.</span><span class="sxs-lookup"><span data-stu-id="21cd9-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="21cd9-148">L’exemple suivant montre des références qualifiées aux procédures de membre de module.</span><span class="sxs-lookup"><span data-stu-id="21cd9-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="21cd9-149">L’exemple déclare deux `Sub` procédures, toutes deux nommées `perform`, dans différents modules d’un projet.</span><span class="sxs-lookup"><span data-stu-id="21cd9-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="21cd9-150">Chacun d’eux peut être spécifiée sans qualification dans son propre module, mais doit être qualifiée si référencée ailleurs.</span><span class="sxs-lookup"><span data-stu-id="21cd9-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="21cd9-151">Étant donné que la dernière référence dans `module3` ne qualifie pas `perform`, le compilateur ne peut pas résoudre cette référence.</span><span class="sxs-lookup"><span data-stu-id="21cd9-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="21cd9-152">Références aux projets</span><span class="sxs-lookup"><span data-stu-id="21cd9-152">References to Projects</span></span>  
 <span data-ttu-id="21cd9-153">Pour utiliser [Public](../../../../visual-basic/language-reference/modifiers/public.md) les éléments définis dans un autre projet, vous devez d’abord définir un *référence* à la bibliothèque d’assembly ou le type de ce projet.</span><span class="sxs-lookup"><span data-stu-id="21cd9-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="21cd9-154">Pour définir une référence, cliquez sur **ajouter une référence** sur la **projet** menu, ou encore utiliser le [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) option du compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="21cd9-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="21cd9-155">Par exemple, vous pouvez utiliser le modèle d’objet XML de le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21cd9-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="21cd9-156">Si vous définissez une référence à la <xref:System.Xml> espace de noms, vous pouvez déclarer et utiliser une de ses classes, telles que <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="21cd9-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="21cd9-157">L’exemple suivant utilise <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="21cd9-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="21cd9-158">Importation d’éléments conteneurs</span><span class="sxs-lookup"><span data-stu-id="21cd9-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="21cd9-159">Vous pouvez utiliser la [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) à *importer* les espaces de noms qui contiennent les modules ou classes que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="21cd9-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="21cd9-160">Cela vous permet de faire référence aux éléments définis dans un espace de noms importé sans qualifier complètement leurs noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="21cd9-161">L’exemple suivant réécrit l’exemple précédent pour importer le <xref:System.Xml> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="21cd9-162">En outre, le `Imports` instruction peut définir un *alias d’importation* pour chaque espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="21cd9-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="21cd9-163">Cela peut rendre le code source plus court et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="21cd9-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="21cd9-164">L’exemple suivant réécrit l’exemple précédent pour utiliser `xD` en tant qu’alias pour la <xref:System.Xml> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="21cd9-165">La `Imports` instruction ne rend pas les éléments d’autres projets disponibles à votre application.</span><span class="sxs-lookup"><span data-stu-id="21cd9-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="21cd9-166">Autrement dit, il ne prend pas la place de la définition d’une référence.</span><span class="sxs-lookup"><span data-stu-id="21cd9-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="21cd9-167">L’importation d’un espace de noms simplement supprime la nécessité de qualifier les noms définis dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="21cd9-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="21cd9-168">Vous pouvez également utiliser le `Imports` statement pour importer des modules, des classes, des structures et des énumérations.</span><span class="sxs-lookup"><span data-stu-id="21cd9-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="21cd9-169">Vous pouvez ensuite utiliser les membres de ces éléments importés sans qualification.</span><span class="sxs-lookup"><span data-stu-id="21cd9-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="21cd9-170">Toutefois, vous devez toujours qualifier les membres non partagés de classes et les structures avec une variable ou une expression qui correspond à une instance de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="21cd9-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="21cd9-171">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="21cd9-171">Naming Guidelines</span></span>  
 <span data-ttu-id="21cd9-172">Lorsque vous définissez deux ou plusieurs éléments de programmation qui ont le même nom, un *ambiguïté de noms* peuvent entraîner lorsque le compilateur tente de résoudre une référence à ce nom.</span><span class="sxs-lookup"><span data-stu-id="21cd9-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="21cd9-173">Si plusieurs définitions sont dans la portée, ou si aucune définition n’est dans la portée, la référence est résolue.</span><span class="sxs-lookup"><span data-stu-id="21cd9-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="21cd9-174">Pour obtenir un exemple, consultez « Exemple de référence qualifiée » sur cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="21cd9-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="21cd9-175">Pour éviter toute ambiguïté, vous pouvez affecter des noms uniques de tous les éléments de.</span><span class="sxs-lookup"><span data-stu-id="21cd9-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="21cd9-176">Ensuite, vous pouvez faire référence à n’importe quel élément sans devoir qualifier son nom avec un espace de noms, un module ou une classe.</span><span class="sxs-lookup"><span data-stu-id="21cd9-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="21cd9-177">Vous réduisez également le risque de faire référence par erreur à l’élément incorrect.</span><span class="sxs-lookup"><span data-stu-id="21cd9-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="21cd9-178">Clichés instantanés</span><span class="sxs-lookup"><span data-stu-id="21cd9-178">Shadowing</span></span>  
 <span data-ttu-id="21cd9-179">Lorsque deux éléments de programmation partagent le même nom, un d’eux peut masquer, ou *ombre*, autre.</span><span class="sxs-lookup"><span data-stu-id="21cd9-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="21cd9-180">Un élément occulté n’est pas disponible pour la référence ; au lieu de cela, lorsque votre code utilise le nom de l’élément occulté, le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur résout vers l’élément d’occultation.</span><span class="sxs-lookup"><span data-stu-id="21cd9-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="21cd9-181">Pour obtenir une explication plus détaillée avec des exemples, consultez [occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="21cd9-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21cd9-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21cd9-182">See Also</span></span>  
 [<span data-ttu-id="21cd9-183">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="21cd9-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="21cd9-184">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="21cd9-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="21cd9-185">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="21cd9-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="21cd9-186">Variables</span><span class="sxs-lookup"><span data-stu-id="21cd9-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="21cd9-187">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="21cd9-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="21cd9-188">New (opérateur)</span><span class="sxs-lookup"><span data-stu-id="21cd9-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="21cd9-189">Public</span><span class="sxs-lookup"><span data-stu-id="21cd9-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
