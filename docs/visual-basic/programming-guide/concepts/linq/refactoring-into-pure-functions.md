---
title: Refactorisation dans des fonctions pures (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3d3dd3b587fd0b244df9ccc5a65fbfbf4b60428e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="6a49c-102">Refactorisation dans des fonctions pures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a49c-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="6a49c-103">L'un des aspects importants des transformations fonctionnelles pures consiste à apprendre à refactoriser le code à l'aide de fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="6a49c-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="6a49c-104">Comme mentionné précédemment dans cette section, une fonction pure présente deux caractéristiques utiles :</span><span class="sxs-lookup"><span data-stu-id="6a49c-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="6a49c-105">Elle n'a aucun effet secondaire.</span><span class="sxs-lookup"><span data-stu-id="6a49c-105">It has no side effects.</span></span> <span data-ttu-id="6a49c-106">La fonction ne change aucune variable et aucune donnée de tout type en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="6a49c-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="6a49c-107">Elle est cohérente.</span><span class="sxs-lookup"><span data-stu-id="6a49c-107">It is consistent.</span></span> <span data-ttu-id="6a49c-108">Étant donné le même ensemble de données d'entrée, elle retournera toujours la même valeur de sortie.</span><span class="sxs-lookup"><span data-stu-id="6a49c-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="6a49c-109">L'une des manières de basculer vers la programmation fonctionnelle consiste à refactoriser le code existant afin d'éliminer les effets secondaires indésirables et les dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="6a49c-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="6a49c-110">De cette manière, vous pouvez créer des versions avec fonctions pures du code existant.</span><span class="sxs-lookup"><span data-stu-id="6a49c-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="6a49c-111">Cette rubrique explique ce qu'est et ce que n'est pas une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="6a49c-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="6a49c-112">Le [didacticiel : manipulation de contenu dans un WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) didacticiel montre comment manipuler un document WordprocessingML et contient deux exemples illustrant comment effectuer une refactorisation à l’aide d’une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="6a49c-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="6a49c-113">Suppression des effets secondaires et des dépendances externes</span><span class="sxs-lookup"><span data-stu-id="6a49c-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="6a49c-114">Les exemples suivants comparent deux fonctions non pures et une fonction pure.</span><span class="sxs-lookup"><span data-stu-id="6a49c-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="6a49c-115">Fonction non pure qui modifie un membre de classe</span><span class="sxs-lookup"><span data-stu-id="6a49c-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="6a49c-116">Dans le code suivant, la fonction `HypenatedConcat` n'est pas pure car elle modifie le membre de données `aMember` dans la classe :</span><span class="sxs-lookup"><span data-stu-id="6a49c-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6a49c-117">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6a49c-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="6a49c-118">Notez qu’il est sans intérêt si les données modifiées aient `public` ou `private` accéder à ou est un `shared` ou un membre d’instance.</span><span class="sxs-lookup"><span data-stu-id="6a49c-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="6a49c-119">Une fonction pure ne change aucune donnée en dehors de la fonction.</span><span class="sxs-lookup"><span data-stu-id="6a49c-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="6a49c-120">Fonction non pure qui modifie un argument</span><span class="sxs-lookup"><span data-stu-id="6a49c-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="6a49c-121">En outre, la version suivante de cette même fonction n'est pas pure car elle modifie le contenu de son paramètre, `sb`.</span><span class="sxs-lookup"><span data-stu-id="6a49c-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6a49c-122">Cette version du programme génère la même sortie que la première version, car la `HypenatedConcat` fonction a modifié la valeur (état) de son premier paramètre en appelant le <xref:System.Text.StringBuilder.Append%2A>fonction membre.</xref:System.Text.StringBuilder.Append%2A></span><span class="sxs-lookup"><span data-stu-id="6a49c-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="6a49c-123">Notez que cette altération a lieu en dépit du fait que `HypenatedConcat` utilise le passage de paramètre avec appel par valeur.</span><span class="sxs-lookup"><span data-stu-id="6a49c-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a49c-124">Pour les types de référence, si vous passez un paramètre par valeur, une copie de la référence à un objet est passée.</span><span class="sxs-lookup"><span data-stu-id="6a49c-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="6a49c-125">Cette copie est toujours associée aux mêmes données d'instance que la référence d'origine (jusqu'à ce que la variable de référence soit assignée à un nouvel objet).</span><span class="sxs-lookup"><span data-stu-id="6a49c-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="6a49c-126">L'appel par référence n'est pas forcément nécessaire pour qu'une fonction modifie un paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a49c-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="6a49c-127">Fonction pure</span><span class="sxs-lookup"><span data-stu-id="6a49c-127">Pure Function</span></span>  
 <span data-ttu-id="6a49c-128">Cette autre version du programme montre comment implémenter la fonction `HypenatedConcat` en tant que fonction pure.</span><span class="sxs-lookup"><span data-stu-id="6a49c-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
```vb  
Module Module1  
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String  
        Return (s & "-" & appendStr)  
    End Function  
  
    Sub Main()  
        Dim s1 As String = "StringOne"  
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")  
        Console.WriteLine(s2)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6a49c-129">Là encore, cette version génère la même ligne de sortie : `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="6a49c-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="6a49c-130">Notez que pour conserver la valeur concaténée, elle est stockée dans la variable intermédiaire `s2`.</span><span class="sxs-lookup"><span data-stu-id="6a49c-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="6a49c-131">L'une des approches qui peuvent se révéler très utiles consiste à écrire des fonctions localement impures (à savoir, qui déclarent et modifient des variables locales) mais globalement pures.</span><span class="sxs-lookup"><span data-stu-id="6a49c-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="6a49c-132">Ces fonctions possèdent une grande partie des caractéristiques de composabilité requises, mais elles évitent certaines des tâches de programmation fonctionnelle plus compliquées, telles que l'utilisation de la récursivité lorsqu'une simple boucle génèrerait le même résultat.</span><span class="sxs-lookup"><span data-stu-id="6a49c-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="6a49c-133">Opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="6a49c-133">Standard Query Operators</span></span>  
 <span data-ttu-id="6a49c-134">L'une des caractéristiques importantes des opérateurs de requête standard est qu'ils sont implémentés en tant que fonctions pures.</span><span class="sxs-lookup"><span data-stu-id="6a49c-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="6a49c-135">Pour plus d’informations, consultez [vue d’ensemble Standard des opérateurs de requête (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a49c-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a49c-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a49c-136">See Also</span></span>  
 <span data-ttu-id="6a49c-137">[Introduction aux Transformations fonctionnelles pures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="6a49c-137">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="6a49c-138"> [Comparaison de la programmation fonctionnelle et de la Programmation impérative (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span><span class="sxs-lookup"><span data-stu-id="6a49c-138"> [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span></span>
