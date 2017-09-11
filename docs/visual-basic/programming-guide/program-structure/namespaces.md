---
title: Espaces de noms dans Visual Basic | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names, avoiding conflicts
- naming conflicts, namespaces
- namespaces, assemblies
- Visual Basic code, namespaces
- fully qualified names
- naming conventions, naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bfc9f8f71b5ce5e05b6509ad490354663f894651
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-in-visual-basic"></a><span data-ttu-id="5ed68-102">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ed68-102">Namespaces in Visual Basic</span></span>
<span data-ttu-id="5ed68-103">Les espaces de noms permettent d’organiser les objets définis dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="5ed68-103">Namespaces organize the objects defined in an assembly.</span></span> <span data-ttu-id="5ed68-104">Les assemblys peuvent contenir plusieurs espaces de noms, qui peuvent à leur tour contenir d’autres espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-104">Assemblies can contain multiple namespaces, which can in turn contain other namespaces.</span></span> <span data-ttu-id="5ed68-105">Les espaces de noms permettent d’éviter les ambiguïtés et de simplifier les références quand de grands groupes d’objets, tels que des bibliothèques de classes, sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="5ed68-105">Namespaces prevent ambiguity and simplify references when using large groups of objects such as class libraries.</span></span>  
  
 <span data-ttu-id="5ed68-106">Par exemple, le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] définit la <xref:System.Windows.Forms.ListBox>classe dans le <xref:System.Windows.Forms?displayProperty=fullName>espace de noms.</xref:System.Windows.Forms?displayProperty=fullName> </xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="5ed68-106">For example, the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] defines the <xref:System.Windows.Forms.ListBox> class in the <xref:System.Windows.Forms?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="5ed68-107">Le fragment de code suivant montre comment déclarer une variable en utilisant le nom qualifié complet de cette classe :</span><span class="sxs-lookup"><span data-stu-id="5ed68-107">The following code fragment shows how to declare a variable using the fully qualified name for this class:</span></span>  
  
 <span data-ttu-id="5ed68-108">[!code-vb[VbVbalrApplication n °&6;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-108">[!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]</span></span>  
  
## <a name="avoiding-name-collisions"></a><span data-ttu-id="5ed68-109">Éviter les collisions de noms</span><span class="sxs-lookup"><span data-stu-id="5ed68-109">Avoiding Name Collisions</span></span>  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]<span data-ttu-id="5ed68-110">espaces de noms de résoudre le problème parfois appelé *contre la pollution de l’espace de noms*, dans lequel le développeur d’une bibliothèque de classes est entravé par l’utilisation de noms similaires dans une autre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="5ed68-110"> namespaces address a problem sometimes called *namespace pollution*, in which the developer of a class library is hampered by the use of similar names in another library.</span></span> <span data-ttu-id="5ed68-111">Ces conflits avec des éléments existants sont également connus sous le terme de *collisions de noms*.</span><span class="sxs-lookup"><span data-stu-id="5ed68-111">These conflicts with existing components are sometimes called *name collisions*.</span></span>  
  
 <span data-ttu-id="5ed68-112">Par exemple, si vous créez une classe nommée `ListBox`, vous pouvez l’utiliser dans votre projet sans qualification.</span><span class="sxs-lookup"><span data-stu-id="5ed68-112">For example, if you create a new class named `ListBox`, you can use it inside your project without qualification.</span></span> <span data-ttu-id="5ed68-113">Toutefois, si vous souhaitez utiliser le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox>classe dans le même projet, vous devez utiliser une référence qualifiée complète pour rendre la référence unique.</xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="5ed68-113">However, if you want to use the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox> class in the same project, you must use a fully qualified reference to make the reference unique.</span></span> <span data-ttu-id="5ed68-114">Si la référence n’est pas unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur indiquant que le nom est ambigu.</span><span class="sxs-lookup"><span data-stu-id="5ed68-114">If the reference is not unique, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name is ambiguous.</span></span> <span data-ttu-id="5ed68-115">L’exemple de code suivant montre comment déclarer ces objets :</span><span class="sxs-lookup"><span data-stu-id="5ed68-115">The following code example demonstrates how to declare these objects:</span></span>  
  
 <span data-ttu-id="5ed68-116">[!code-vb[VbVbalrApplication&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-116">[!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-117">L’illustration ci-dessous montre deux hiérarchies d’espaces de noms, chacune contenant un objet nommé `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="5ed68-117">The following illustration shows two namespace hierarchies, both containing an object named `ListBox`.</span></span>  
  
 <span data-ttu-id="5ed68-118">![Hiérarchie de Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span><span class="sxs-lookup"><span data-stu-id="5ed68-118">![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")</span></span>  
  
 <span data-ttu-id="5ed68-119">Par défaut, chaque fichier exécutable que vous créez à l’aide de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contient un espace de noms portant le même nom que votre projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-119">By default, every executable file you create with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contains a namespace with the same name as your project.</span></span> <span data-ttu-id="5ed68-120">Par exemple, si vous définissez un objet dans un projet nommé `ListBoxProject`, le fichier exécutable, ListBoxProject.exe, contient un espace de noms appelé `ListBoxProject`.</span><span class="sxs-lookup"><span data-stu-id="5ed68-120">For example, if you define an object within a project named `ListBoxProject`, the executable file ListBoxProject.exe contains a namespace called `ListBoxProject`.</span></span>  
  
 <span data-ttu-id="5ed68-121">Plusieurs assemblys peuvent utiliser le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-121">Multiple assemblies can use the same namespace.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5ed68-122"> les traite alors comme un ensemble unique de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-122"> treats them as a single set of names.</span></span> <span data-ttu-id="5ed68-123">Par exemple, vous pouvez définir des classes pour un espace de noms appelé `SomeNameSpace` dans un assembly nommé `Assemb1`, et définir des classes supplémentaires pour le même espace de noms d’un assembly nommé `Assemb2`.</span><span class="sxs-lookup"><span data-stu-id="5ed68-123">For example, you can define classes for a namespace called `SomeNameSpace` in an assembly named `Assemb1`, and define additional classes for the same namespace from an assembly named `Assemb2`.</span></span>  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="5ed68-124">Noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="5ed68-124">Fully Qualified Names</span></span>  
 <span data-ttu-id="5ed68-125">Les noms qualifiés complets sont des références d’objet dont le préfixe est le nom de l’espace de noms dans lequel l’objet est défini.</span><span class="sxs-lookup"><span data-stu-id="5ed68-125">Fully qualified names are object references that are prefixed with the name of the namespace in which the object is defined.</span></span> <span data-ttu-id="5ed68-126">Vous pouvez utiliser les objets définis dans d’autres projets si vous créez une référence à la classe (en choisissant **Ajouter une référence** dans le menu **Projet** ), puis utiliser le nom qualifié complet de l’objet dans votre code.</span><span class="sxs-lookup"><span data-stu-id="5ed68-126">You can use objects defined in other projects if you create a reference to the class (by choosing **Add Reference** from the **Project** menu) and then use the fully qualified name for the object in your code.</span></span> <span data-ttu-id="5ed68-127">Le fragment de code suivant montre comment utiliser le nom qualifié complet d’un objet provenant de l’espace de noms d’un autre projet :</span><span class="sxs-lookup"><span data-stu-id="5ed68-127">The following code fragment shows how to use the fully qualified name for an object from another project's namespace:</span></span>  
  
 <span data-ttu-id="5ed68-128">[!code-vb[VbVbalrApplication n °&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-128">[!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-129">Les noms qualifiés complets empêchent les conflits de nommage, car ils permettent au compilateur d’identifier l’objet utilisé.</span><span class="sxs-lookup"><span data-stu-id="5ed68-129">Fully qualified names prevent naming conflicts because they make it possible for the compiler to determine which object is being used.</span></span> <span data-ttu-id="5ed68-130">Toutefois, les noms peuvent devenir longs et compliqués.</span><span class="sxs-lookup"><span data-stu-id="5ed68-130">However, the names themselves can get long and cumbersome.</span></span> <span data-ttu-id="5ed68-131">Pour contourner ce problème, utilisez l’instruction `Imports` pour définir un *alias*, qui est un nom abrégé utilisable à la place d’un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-131">To get around this, you can use the `Imports` statement to define an *alias*—an abbreviated name you can use in place of a fully qualified name.</span></span> <span data-ttu-id="5ed68-132">L’exemple de code ci-dessous crée les alias de deux noms qualifiés complets, puis utilise ces alias pour définir deux objets.</span><span class="sxs-lookup"><span data-stu-id="5ed68-132">For example, the following code example creates aliases for two fully qualified names, and uses these aliases to define two objects.</span></span>  
  
 <span data-ttu-id="5ed68-133">[!code-vb[VbVbalrApplication&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-133">[!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-134">[!code-vb[VbVbalrApplication&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-134">[!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-135">Si vous utilisez l’instruction `Imports` sans alias, vous pouvez vous servir de tous les noms de l’espace de noms sans qualification, à condition qu’ils soient uniques au sein du projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-135">If you use the `Imports` statement without an alias, you can use all the names in that namespace without qualification, provided they are unique to the project.</span></span> <span data-ttu-id="5ed68-136">Si votre projet contient des instructions `Imports` pour les espaces de noms contenant des éléments de même nom, vous devez fournir un nom qualifié complet quand vous l’utilisez.</span><span class="sxs-lookup"><span data-stu-id="5ed68-136">If your project contains `Imports` statements for namespaces that contain items with the same name, you must fully qualify that name when you use it.</span></span> <span data-ttu-id="5ed68-137">Imaginons, par exemple, que votre projet contient les deux instructions `Imports` suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ed68-137">Suppose, for example, your project contained the following two `Imports` statements:</span></span>  
  
 <span data-ttu-id="5ed68-138">[!code-vb[VbVbalrApplication&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-138">[!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-139">Si vous essayez d’utiliser `Class1` sans fournir son nom qualifié complet, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur indiquant que le nom `Class1` est ambigu.</span><span class="sxs-lookup"><span data-stu-id="5ed68-139">If you attempt to use `Class1` without fully qualifying it, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produces an error stating that the name `Class1` is ambiguous.</span></span>  
  
## <a name="namespace-level-statements"></a><span data-ttu-id="5ed68-140">Instructions au niveau de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="5ed68-140">Namespace Level Statements</span></span>  
 <span data-ttu-id="5ed68-141">Dans un espace de noms, vous pouvez définir des éléments tels que des modules, des interfaces, des classes, des délégués, des énumérations, des structures et d’autres espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-141">Within a namespace, you can define items such as modules, interfaces, classes, delegates, enumerations, structures, and other namespaces.</span></span> <span data-ttu-id="5ed68-142">Vous ne pouvez pas définir d’éléments tels que des propriétés, des procédures, des variables et des événements au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-142">You cannot define items such as properties, procedures, variables and events at the namespace level.</span></span> <span data-ttu-id="5ed68-143">Ces éléments doivent être déclarés dans des conteneurs tels que des modules, des structures ou des classes.</span><span class="sxs-lookup"><span data-stu-id="5ed68-143">These items must be declared within containers such as modules, structures, or classes.</span></span>  
  
## <a name="global-keyword-in-fully-qualified-names"></a><span data-ttu-id="5ed68-144">Mot clé Global dans les noms qualifiés complets</span><span class="sxs-lookup"><span data-stu-id="5ed68-144">Global Keyword in Fully Qualified Names</span></span>  
 <span data-ttu-id="5ed68-145">Si vous avez défini une hiérarchie imbriquée d’espaces de noms, le code à l’intérieur de cette hiérarchie peut ne pas d’accéder à la <xref:System?displayProperty=fullName>espace de noms du .NET Framework.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-145">If you have defined a nested hierarchy of namespaces, code inside that hierarchy might be blocked from accessing the <xref:System?displayProperty=fullName> namespace of the .NET Framework.</span></span> <span data-ttu-id="5ed68-146">L’exemple suivant illustre une hiérarchie dans laquelle le `SpecialSpace.System` espace de noms bloque l’accès à <xref:System?displayProperty=fullName>.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-146">The following example illustrates a hierarchy in which the `SpecialSpace.System` namespace blocks access to <xref:System?displayProperty=fullName>.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="5ed68-147">Par conséquent, le compilateur Visual Basic ne peut pas résoudre correctement la référence à <xref:System.Int32?displayProperty=fullName>, car `SpecialSpace.System` ne définit pas `Int32`.</xref:System.Int32?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-147">As a result, the Visual Basic compiler cannot successfully resolve the reference to <xref:System.Int32?displayProperty=fullName>, because `SpecialSpace.System` does not define `Int32`.</span></span> <span data-ttu-id="5ed68-148">Vous pouvez utiliser le mot clé `Global` pour démarrer la chaîne de qualification au niveau le plus externe de la bibliothèque de classes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ed68-148">You can use the `Global` keyword to start the qualification chain at the outermost level of the .NET Framework class library.</span></span> <span data-ttu-id="5ed68-149">Cela vous permet de spécifier le <xref:System?displayProperty=fullName>espace de noms ou un autre espace de noms dans la bibliothèque de classes.</xref:System?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-149">This allows you to specify the <xref:System?displayProperty=fullName> namespace or any other namespace in the class library.</span></span> <span data-ttu-id="5ed68-150">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="5ed68-150">The following example illustrates this.</span></span>  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 <span data-ttu-id="5ed68-151">Vous pouvez utiliser `Global` pour accéder à d’autres espaces de noms racine, tel que <xref:Microsoft.VisualBasic?displayProperty=fullName>et n’importe quel espace de noms associé à votre projet.</xref:Microsoft.VisualBasic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-151">You can use `Global` to access other root-level namespaces, such as <xref:Microsoft.VisualBasic?displayProperty=fullName>, and any namespace associated with your project.</span></span>  
  
## <a name="global-keyword-in-namespace-statements"></a><span data-ttu-id="5ed68-152">Mot clé Global dans les instructions Namespace</span><span class="sxs-lookup"><span data-stu-id="5ed68-152">Global Keyword in Namespace Statements</span></span>  
 <span data-ttu-id="5ed68-153">Vous pouvez également utiliser le `Global` mot clé dans une [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ed68-153">You can also use the `Global` keyword in a [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span> <span data-ttu-id="5ed68-154">pour définir un espace de noms hors de l’espace de noms racine de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-154">This lets you define a namespace out of the root namespace of your project.</span></span>  
  
 <span data-ttu-id="5ed68-155">Tous les espaces de noms dans votre projet sont basés sur l’espace de noms racine du projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-155">All namespaces in your project are based on the root namespace for the project.</span></span>  <span data-ttu-id="5ed68-156">Visual Studio définit le nom de votre projet comme espace de noms racine par défaut pour l’ensemble du code de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-156">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="5ed68-157">Par exemple, si votre projet est nommé `ConsoleApplication1`, ses éléments de programmation appartiennent à l’espace de noms `ConsoleApplication1`.</span><span class="sxs-lookup"><span data-stu-id="5ed68-157">For example, if your project is named `ConsoleApplication1`, its programming elements belong to namespace `ConsoleApplication1`.</span></span> <span data-ttu-id="5ed68-158">Si vous déclarez `Namespace Magnetosphere`, les références à `Magnetosphere` dans le projet doivent accéder à `ConsoleApplication1.Magnetosphere`.</span><span class="sxs-lookup"><span data-stu-id="5ed68-158">If you declare `Namespace Magnetosphere`, references to `Magnetosphere` in the project will access `ConsoleApplication1.Magnetosphere`.</span></span>  
  
 <span data-ttu-id="5ed68-159">Les exemples suivants utilisent le mot clé `Global` pour déclarer un espace de noms hors de l’espace de noms racine du projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-159">The following examples use the `Global` keyword to declare a namespace out of the root namespace for the project.</span></span>  
  
 <span data-ttu-id="5ed68-160">[!code-vb[VbVbalrApplication&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-160">[!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]</span></span>  
  
 <span data-ttu-id="5ed68-161">Dans une déclaration d’espace de noms, `Global` ne peut pas être imbriqué dans un autre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-161">In a namespace declaration, `Global` cannot be nested in another namespace.</span></span>  
  
 <span data-ttu-id="5ed68-162">Vous pouvez utiliser la [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) pour afficher et modifier les **racine Namespace** du projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-162">You can use the [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) to view and modify the **Root Namespace** of the project.</span></span>  <span data-ttu-id="5ed68-163">Pour les nouveaux projets, l’ **espace de noms racine** correspond par défaut au nom du projet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-163">For new projects, the **Root Namespace** defaults to the project name.</span></span> <span data-ttu-id="5ed68-164">Pour définir `Global` comme espace de noms de premier niveau, effacez l’entrée **Espace de noms racine** pour que la zone soit vide.</span><span class="sxs-lookup"><span data-stu-id="5ed68-164">To cause `Global` to be the top-level namespace, you can clear the **Root Namespace** entry so that the box is empty.</span></span> <span data-ttu-id="5ed68-165">Quand l’entrée **Espace de noms racine** est effacée, vous n’avez pas besoin de spécifier le mot clé `Global` dans les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5ed68-165">Clearing **Root Namespace** removes the need for the `Global` keyword in namespace declarations.</span></span>  
  
 <span data-ttu-id="5ed68-166">Si une instruction `Namespace` déclare un nom qui est également un espace de noms dans le .NET Framework, l’espace de noms .NET Framework n’est plus disponible si le mot clé `Global` n’est pas utilisé dans un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="5ed68-166">If a `Namespace` statement declares a name that is also a namespace in the .NET Framework, the .NET Framework namespace becomes unavailable if the `Global` keyword is not used in a fully qualified name.</span></span> <span data-ttu-id="5ed68-167">Pour permettre l’accès à cet espace de noms .NET Framework sans utiliser le mot clé `Global` , ajoutez le mot clé `Global` dans l’instruction `Namespace` .</span><span class="sxs-lookup"><span data-stu-id="5ed68-167">To enable access to that .NET Framework namespace without using the `Global` keyword, you can include the `Global` keyword in the `Namespace` statement.</span></span>  
  
 <span data-ttu-id="5ed68-168">Dans l’exemple suivant, le mot clé `Global` est utilisé dans la déclaration d’espace de noms `System.Text` .</span><span class="sxs-lookup"><span data-stu-id="5ed68-168">The following example has the `Global` keyword in the `System.Text` namespace declaration.</span></span>  
  
 <span data-ttu-id="5ed68-169">Si le `Global` mot clé n’était pas présent dans la déclaration d’espace de noms, <xref:System.Text.StringBuilder>n’est pas accessible sans spécifier `Global.System.Text.StringBuilder`.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="5ed68-169">If the `Global` keyword was not present in the namespace declaration, <xref:System.Text.StringBuilder> could not be accessed without specifying `Global.System.Text.StringBuilder`.</span></span> <span data-ttu-id="5ed68-170">Pour un projet nommé `ConsoleApplication1`, les références à `System.Text` accèdent à `ConsoleApplication1.System.Text` si le mot clé `Global` n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="5ed68-170">For a project named `ConsoleApplication1`, references to `System.Text` would access `ConsoleApplication1.System.Text` if the `Global` keyword was not used.</span></span>  
  
 <span data-ttu-id="5ed68-171">[!code-vb[VbVbalrApplication n °&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ed68-171">[!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed68-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ed68-172">See Also</span></span>  
 <span data-ttu-id="5ed68-173"><xref:System.Windows.Forms.ListBox></xref:System.Windows.Forms.ListBox></span><span class="sxs-lookup"><span data-stu-id="5ed68-173"><xref:System.Windows.Forms.ListBox></span></span>   
 <span data-ttu-id="5ed68-174"><xref:System.Windows.Forms?displayProperty=fullName></xref:System.Windows.Forms?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ed68-174"><xref:System.Windows.Forms?displayProperty=fullName></span></span>   
<span data-ttu-id="5ed68-175"> [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ed68-175"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="5ed68-176"> [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="5ed68-176"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="5ed68-177"> [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5ed68-177"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="5ed68-178"> [Instruction Imports (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="5ed68-178"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="5ed68-179"> [Écriture de code dans les solutions Office](https://msdn.microsoft.com/library/bb608596)</span><span class="sxs-lookup"><span data-stu-id="5ed68-179"> [Writing Code in Office Solutions](https://msdn.microsoft.com/library/bb608596)</span></span>
