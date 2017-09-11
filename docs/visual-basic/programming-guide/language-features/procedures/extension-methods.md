---
title: "Méthodes d’extension (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
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
ms.openlocfilehash: 0705929da72bcb3001228a90bbb9d5ba7c248bf7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="1f40e-102">Méthodes d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f40e-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="1f40e-103">Méthodes d’extension permettent aux développeurs d’ajouter des fonctionnalités personnalisées aux types de données qui sont déjà définis sans créer un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="1f40e-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="1f40e-104">Méthodes d’extension permettent d’écrire une méthode qui peut être appelée comme s’il s’agissait d’une méthode d’instance du type existant.</span><span class="sxs-lookup"><span data-stu-id="1f40e-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f40e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="1f40e-105">Remarks</span></span>  
 <span data-ttu-id="1f40e-106">Une méthode d’extension peut uniquement être un `Sub` procédure ou d’un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="1f40e-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="1f40e-107">Vous ne pouvez pas définir une propriété d’extension, un champ ou un événement.</span><span class="sxs-lookup"><span data-stu-id="1f40e-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="1f40e-108">Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension `<Extension()>` à partir de la <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms.</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1f40e-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span>  
  
 <span data-ttu-id="1f40e-109">Le premier paramètre dans une définition de méthode d’extension Spécifie le type de données s’étend de la méthode.</span><span class="sxs-lookup"><span data-stu-id="1f40e-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="1f40e-110">Lorsque la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode.</span><span class="sxs-lookup"><span data-stu-id="1f40e-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f40e-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f40e-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1f40e-112">Description</span><span class="sxs-lookup"><span data-stu-id="1f40e-112">Description</span></span>  
 <span data-ttu-id="1f40e-113">L’exemple suivant définit un `Print` extension pour le <xref:System.String>type de données.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1f40e-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="1f40e-114">Utilise la méthode `Console.WriteLine` pour afficher une chaîne.</span><span class="sxs-lookup"><span data-stu-id="1f40e-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="1f40e-115">Le paramètre de la `Print` (méthode), `aString`, indique que la méthode étend la <xref:System.String>classe.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1f40e-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 <span data-ttu-id="1f40e-116">[!code-vb[VbVbalrExtensionMethods n °&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-116">[!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-117">Notez que la définition de méthode d’extension est marquée avec l’attribut d’extension `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="1f40e-117">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="1f40e-118">Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d’extension doit être marqué.</span><span class="sxs-lookup"><span data-stu-id="1f40e-118">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="1f40e-119"><xref:System.Runtime.CompilerServices>doit être importé pour accéder à l’attribut d’extension.</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="1f40e-119"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="1f40e-120">Méthodes d’extension peuvent être déclarées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="1f40e-120">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="1f40e-121">En règle générale, le module dans lequel une méthode d’extension est définie n’est pas le même module que celui dans lequel il est appelé.</span><span class="sxs-lookup"><span data-stu-id="1f40e-121">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="1f40e-122">Au lieu de cela, le module qui contient la méthode d’extension est importé, si nécessaire, pour qu’il soit dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="1f40e-122">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="1f40e-123">Une fois le module qui contient `Print` est dans la portée, la méthode peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire qui n’accepte aucun argument, tel que `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="1f40e-123">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 <span data-ttu-id="1f40e-124">[!code-vb[VbVbalrExtensionMethods n °&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-124">[!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-125">L’exemple suivant, `PrintAndPunctuate`, est également une extension <xref:System.String>, cette fois définie avec deux paramètres.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1f40e-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="1f40e-126">Le premier paramètre, `aString`, indique que la méthode d’extension étend <xref:System.String>.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="1f40e-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="1f40e-127">Le deuxième paramètre, `punc`, est destinée à être une chaîne de signes de ponctuation qui est passée comme un argument lorsque la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="1f40e-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="1f40e-128">La méthode affiche la chaîne suivie par les signes de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="1f40e-128">The method displays the string followed by the punctuation marks.</span></span>  
  
 <span data-ttu-id="1f40e-129">[!code-vb[VbVbalrExtensionMethods n °&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-129">[!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-130">La méthode est appelée en envoyant un argument de chaîne pour `punc`:`example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="1f40e-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="1f40e-131">L’exemple suivant `Print` et `PrintAndPunctuate` définies et appelées.</span><span class="sxs-lookup"><span data-stu-id="1f40e-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="1f40e-132"><xref:System.Runtime.CompilerServices>est importé dans le module de définition pour permettre l’accès à l’attribut d’extension.</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="1f40e-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1f40e-133">Code</span><span class="sxs-lookup"><span data-stu-id="1f40e-133">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="1f40e-134">Ensuite, les méthodes d’extension sont placées dans la portée et appelées.</span><span class="sxs-lookup"><span data-stu-id="1f40e-134">Next, the extension methods are brought into scope and called.</span></span>  
  
```vb  
Imports ConsoleApplication2.StringExtensions  
Module Module1  
  
    Sub Main()  
  
        Dim example As String = "Example string"  
        example.Print()  
  
        example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="1f40e-135">Commentaires</span><span class="sxs-lookup"><span data-stu-id="1f40e-135">Comments</span></span>  
 <span data-ttu-id="1f40e-136">Il est requis pour pouvoir exécuter ces ou comme méthodes d’extension est qu’elles dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="1f40e-136">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="1f40e-137">Si le module qui contient une méthode d’extension est dans la portée, il est visible dans IntelliSense et peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire.</span><span class="sxs-lookup"><span data-stu-id="1f40e-137">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="1f40e-138">Notez que lorsque les méthodes sont appelées, aucun argument n’est envoyé au premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="1f40e-138">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="1f40e-139">Paramètre `aString` dans la méthode précédente définitions est lié au `example`, l’instance de `String` qui les appelle.</span><span class="sxs-lookup"><span data-stu-id="1f40e-139">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="1f40e-140">Le compilateur utilise `example` comme argument envoyé au premier paramètre.</span><span class="sxs-lookup"><span data-stu-id="1f40e-140">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="1f40e-141">Si une méthode d’extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d’extension s’exécute.</span><span class="sxs-lookup"><span data-stu-id="1f40e-141">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="1f40e-142">Cela ne s’applique pas aux méthodes d’instance ordinaire.</span><span class="sxs-lookup"><span data-stu-id="1f40e-142">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="1f40e-143">Vous pouvez vérifier explicitement `Nothing` dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-143">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="1f40e-144">Types qui peuvent être étendus</span><span class="sxs-lookup"><span data-stu-id="1f40e-144">Types That Can Be Extended</span></span>  
 <span data-ttu-id="1f40e-145">Vous pouvez définir une méthode d’extension sur la plupart des types qui peuvent être représentées dans une liste de paramètres Visual Basic, notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f40e-145">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="1f40e-146">Classes (types référence)</span><span class="sxs-lookup"><span data-stu-id="1f40e-146">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="1f40e-147">Structures (types valeur)</span><span class="sxs-lookup"><span data-stu-id="1f40e-147">Structures (value types)</span></span>  
  
-   <span data-ttu-id="1f40e-148">Interfaces</span><span class="sxs-lookup"><span data-stu-id="1f40e-148">Interfaces</span></span>  
  
-   <span data-ttu-id="1f40e-149">Délégués</span><span class="sxs-lookup"><span data-stu-id="1f40e-149">Delegates</span></span>  
  
-   <span data-ttu-id="1f40e-150">Arguments ByRef et ByVal</span><span class="sxs-lookup"><span data-stu-id="1f40e-150">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="1f40e-151">Paramètres de méthode générique</span><span class="sxs-lookup"><span data-stu-id="1f40e-151">Generic method parameters</span></span>  
  
-   <span data-ttu-id="1f40e-152">Tableaux</span><span class="sxs-lookup"><span data-stu-id="1f40e-152">Arrays</span></span>  
  
 <span data-ttu-id="1f40e-153">Étant donné que le premier paramètre spécifie le type de données qui s’étend de la méthode d’extension, il est obligatoire et ne peut pas être facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f40e-153">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="1f40e-154">Pour cette raison, `Optional` paramètres et `ParamArray` paramètres ne peut pas être le premier paramètre dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="1f40e-154">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="1f40e-155">Méthodes d’extension ne sont pas considérés dans la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="1f40e-155">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="1f40e-156">Dans l’exemple suivant, l’instruction `anObject.PrintMe()` déclenche un <xref:System.MissingMemberException>d’exceptions, la même exception que vous verriez si la seconde `PrintMe` définition de méthode d’extension ont été supprimés.</xref:System.MissingMemberException></span><span class="sxs-lookup"><span data-stu-id="1f40e-156">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 <span data-ttu-id="1f40e-157">[!code-vb[VbVbalrExtensionMethods&#9;](./codesnippet/VisualBasic/extension-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-157">[!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="1f40e-158">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="1f40e-158">Best Practices</span></span>  
 <span data-ttu-id="1f40e-159">Méthodes d’extension fournissent un moyen pratique et puissant d’étendre un type existant.</span><span class="sxs-lookup"><span data-stu-id="1f40e-159">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="1f40e-160">Toutefois, pour les utiliser avec succès, il existe certains points à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="1f40e-160">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="1f40e-161">Ces considérations s’appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter les applications qui utilisent des méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-161">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="1f40e-162">Plus généralement, les méthodes d’extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d’extension ajoutées aux types que vous contrôlez.</span><span class="sxs-lookup"><span data-stu-id="1f40e-162">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="1f40e-163">Un certain nombre de choses peut se produire dans les classes que vous ne possédez pas pouvant interférer avec vos méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-163">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="1f40e-164">Si un membre d’instance accessible existe qui a une signature qui est compatible avec les arguments dans l’instruction d’appel, sans conversions restrictives requises d’un argument pour un paramètre, la méthode d’instance servira plutôt que n’importe quelle méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-164">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="1f40e-165">Par conséquent, si une méthode d’instance appropriée est ajoutée à une classe à un moment donné, un membre d’extension existant que vous fier peut devenir inaccessible.</span><span class="sxs-lookup"><span data-stu-id="1f40e-165">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="1f40e-166">L’auteur d’une méthode d’extension ne peut pas empêcher d’autres programmeurs d’écrire des méthodes d’extension en conflit qui peuvent être prioritaires sur l’extension d’origine.</span><span class="sxs-lookup"><span data-stu-id="1f40e-166">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="1f40e-167">Vous pouvez améliorer la robustesse en plaçant les méthodes d’extension dans leur propre espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f40e-167">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="1f40e-168">Les consommateurs de votre bibliothèque peuvent ensuite inclure un espace de noms exclure ou sélection parmi les espaces de noms, séparément du reste de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="1f40e-168">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="1f40e-169">Il peut être plus sûr d’étendre les interfaces plutôt que d’étendre les classes, surtout si vous ne possédez pas l’interface ou la classe.</span><span class="sxs-lookup"><span data-stu-id="1f40e-169">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="1f40e-170">Une modification dans une interface affecte chaque classe qui l’implémente.</span><span class="sxs-lookup"><span data-stu-id="1f40e-170">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="1f40e-171">Par conséquent, l’auteur peut être moins susceptible d’ajouter ou modifier des méthodes dans une interface.</span><span class="sxs-lookup"><span data-stu-id="1f40e-171">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="1f40e-172">Toutefois, si une classe implémente deux interfaces qui ont des méthodes d’extension avec la même signature, aucune méthode d’extension est visible.</span><span class="sxs-lookup"><span data-stu-id="1f40e-172">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="1f40e-173">Étendez le type le plus spécifique que vous pouvez.</span><span class="sxs-lookup"><span data-stu-id="1f40e-173">Extend the most specific type you can.</span></span> <span data-ttu-id="1f40e-174">Dans une hiérarchie de types, si vous sélectionnez un type à partir de laquelle d’autres types sont dérivés, il existe des couches de l’introduction de méthodes d’instance ou d’autres méthodes d’extension qui peuvent interférer avec les vôtres.</span><span class="sxs-lookup"><span data-stu-id="1f40e-174">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="1f40e-175">Méthodes d’extension, les propriétés et les méthodes d’Instance</span><span class="sxs-lookup"><span data-stu-id="1f40e-175">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="1f40e-176">Lorsqu’une méthode d’instance dans la portée a une signature qui est compatible avec les arguments d’une instruction d’appel, la méthode d’instance est choisie plutôt que n’importe quelle méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-176">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="1f40e-177">La méthode d’instance est prioritaire même si la méthode d’extension est une meilleure correspondance.</span><span class="sxs-lookup"><span data-stu-id="1f40e-177">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="1f40e-178">Dans l’exemple suivant, `ExampleClass` contient une méthode d’instance nommée `ExampleMethod` qui a un paramètre de type `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1f40e-178">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="1f40e-179">Méthode d’extension `ExampleMethod` étend `ExampleClass`, et a un paramètre de type `Long`.</span><span class="sxs-lookup"><span data-stu-id="1f40e-179">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 <span data-ttu-id="1f40e-180">[!code-vb[VbVbalrExtensionMethods n °&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-180">[!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-181">Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d’extension, car `arg1` est `Long` et est compatible uniquement avec le `Long` paramètre dans la méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="1f40e-181">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="1f40e-182">Le deuxième appel à `ExampleMethod` a un `Integer` argument, `arg2`, et il appelle la méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="1f40e-182">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 <span data-ttu-id="1f40e-183">[!code-vb[VbVbalrExtensionMethods n °&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-183">[!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-184">Maintenant inversez les types de données des paramètres dans les deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="1f40e-184">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 <span data-ttu-id="1f40e-185">[!code-vb[VbVbalrExtensionMethods n °&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-185">[!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-186">Cette fois, le code de `Main` appelle la méthode d’instance les deux fois.</span><span class="sxs-lookup"><span data-stu-id="1f40e-186">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="1f40e-187">C’est parce que les deux `arg1` et `arg2` ont une conversion étendue à `Long`, et la méthode d’instance est prioritaire sur la méthode d’extension dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="1f40e-187">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 <span data-ttu-id="1f40e-188">[!code-vb[VbVbalrExtensionMethods&#7;](./codesnippet/VisualBasic/extension-methods_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-188">[!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-189">Par conséquent, une méthode d’extension ne peut pas remplacer une méthode d’instance existante.</span><span class="sxs-lookup"><span data-stu-id="1f40e-189">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="1f40e-190">Toutefois, lorsqu’une méthode d’extension a le même nom qu’une méthode d’instance, mais les signatures n’entrent pas en conflit, les deux méthodes sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="1f40e-190">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="1f40e-191">Par exemple, si classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui ne prend aucun arguments, les méthodes d’extension portant le même nom mais des signatures différentes sont autorisées, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1f40e-191">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 <span data-ttu-id="1f40e-192">[!code-vb[VbVbalrExtensionMethods n °&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="1f40e-192">[!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]</span></span>  
  
 <span data-ttu-id="1f40e-193">La sortie de ce code est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1f40e-193">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="1f40e-194">La situation est plus simple avec des propriétés : si une méthode d’extension a le même nom en tant que propriété de la classe qu’elle étend, la méthode d’extension n’est pas visible et n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="1f40e-194">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="1f40e-195">Priorité de méthode d’extension</span><span class="sxs-lookup"><span data-stu-id="1f40e-195">Extension Method Precedence</span></span>  
 <span data-ttu-id="1f40e-196">Lorsque deux méthodes d’extension qui ont des signatures identiques sont dans la portée et accessible, avec une priorité plus élevée est appelé.</span><span class="sxs-lookup"><span data-stu-id="1f40e-196">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="1f40e-197">Priorité d’une méthode d’extension est basée sur le mécanisme utilisé pour placer la méthode dans la portée.</span><span class="sxs-lookup"><span data-stu-id="1f40e-197">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="1f40e-198">La liste suivante montre la hiérarchie des priorités, du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="1f40e-198">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="1f40e-199">Méthodes d’extension définies dans le module actuel.</span><span class="sxs-lookup"><span data-stu-id="1f40e-199">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="1f40e-200">Méthodes d’extension définies à l’intérieur des données types dans l’espace de noms actuel ou l’un de ses parents, les espaces de noms enfants étant prioritaires sur les espaces de noms parent.</span><span class="sxs-lookup"><span data-stu-id="1f40e-200">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="1f40e-201">Méthodes d’extension définies dans les importations de type dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="1f40e-201">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="1f40e-202">Méthodes d’extension définies dans les importations d’espace de noms dans le fichier actuel.</span><span class="sxs-lookup"><span data-stu-id="1f40e-202">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="1f40e-203">Méthodes d’extension définies dans les importations de type au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="1f40e-203">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="1f40e-204">Méthodes d’extension définies dans les importations de l’espace de noms au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="1f40e-204">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="1f40e-205">Si la priorité ne résout pas l’ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="1f40e-205">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="1f40e-206">Si le `Print` méthode dans l’exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="1f40e-206">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f40e-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f40e-207">See Also</span></span>  
 <span data-ttu-id="1f40e-208"><xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="1f40e-208"><xref:System.Runtime.CompilerServices></span></span>   
 <span data-ttu-id="1f40e-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="1f40e-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></span></span>   
<span data-ttu-id="1f40e-210"> [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-210"> [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
<span data-ttu-id="1f40e-211"> [Module, instruction](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-211"> [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="1f40e-212"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-212"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="1f40e-213"> [Paramètres facultatifs](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-213"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="1f40e-214"> [Tableaux de paramètres](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-214"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="1f40e-215"> [Vue d’ensemble des attributs](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="1f40e-215"> [Attributes overview](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="1f40e-216"> [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="1f40e-216"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
