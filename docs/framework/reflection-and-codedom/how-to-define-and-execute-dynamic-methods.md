---
title: "Guide pratique pour définir et exécuter des méthodes dynamiques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c2b3f1707aab1f83d8f8c6a06bc2efa909134d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="d2591-102">Guide pratique pour définir et exécuter des méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="d2591-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="d2591-103">Les procédures suivantes montrent comment définir et exécuter une méthode dynamique simple et une méthode dynamique liée à une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="d2591-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="d2591-104">Pour plus d’informations sur les méthodes dynamiques, consultez la classe <xref:System.Reflection.Emit.DynamicMethod> et [Scénarios de méthodes dynamiques avec Émission de réflexion](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="d2591-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="d2591-105">Pour définir et exécuter une méthode dynamique</span><span class="sxs-lookup"><span data-stu-id="d2591-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="d2591-106">Déclarez un type délégué pour exécuter la méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="d2591-107">Vous pouvez utiliser un délégué générique pour réduire le nombre de types délégués que vous devez déclarer.</span><span class="sxs-lookup"><span data-stu-id="d2591-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="d2591-108">Le code suivant déclare deux types délégués qui peuvent être utilisés pour la méthode `SquareIt`, et l’un d’eux est générique.</span><span class="sxs-lookup"><span data-stu-id="d2591-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="d2591-109">Créez un tableau qui spécifie les types de paramètre de la méthode dynamique.</span><span class="sxs-lookup"><span data-stu-id="d2591-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="d2591-110">Dans cet exemple, le seul paramètre est un `int` (`Integer` en Visual Basic). Le tableau n’a donc qu’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="d2591-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="d2591-111">Créer un <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="d2591-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="d2591-112">Dans cet exemple, la méthode se nomme `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="d2591-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2591-113">Il n’est pas nécessaire de nommer les méthodes dynamiques. Elles ne peuvent pas être appelées par nom.</span><span class="sxs-lookup"><span data-stu-id="d2591-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="d2591-114">Plusieurs méthodes dynamiques peuvent avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="d2591-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="d2591-115">Toutefois, le nom apparaît dans les piles des appels et peut être utile pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="d2591-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="d2591-116">Le type de la valeur de retour est spécifié comme `long`.</span><span class="sxs-lookup"><span data-stu-id="d2591-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="d2591-117">La méthode est associée au module qui contient la classe `Example`, qui contient l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="d2591-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="d2591-118">Vous pourriez spécifier n’importe quel module chargé.</span><span class="sxs-lookup"><span data-stu-id="d2591-118">Any loaded module could be specified.</span></span> <span data-ttu-id="d2591-119">La méthode dynamique agit comme une méthode `static` au niveau du module (`Shared` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2591-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="d2591-120">Émettez le corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-120">Emit the method body.</span></span> <span data-ttu-id="d2591-121">Dans cet exemple, un objet <xref:System.Reflection.Emit.ILGenerator> est utilisé pour émettre le code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d2591-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d2591-122">Vous pourriez également utiliser un objet <xref:System.Reflection.Emit.DynamicILInfo> conjointement avec des générateurs de code non managé pour émettre le corps de méthode pour un <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="d2591-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="d2591-123">Le code MSIL de cet exemple charge l’argument (qui est un `int`) dans la pile, le convertit en `long`, duplique le `long` et multiplie les deux nombres.</span><span class="sxs-lookup"><span data-stu-id="d2591-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="d2591-124">Cela laisse le résultat au carré sur la pile, et il suffit à la méthode de retourner.</span><span class="sxs-lookup"><span data-stu-id="d2591-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="d2591-125">Créez une instance du délégué (déclaré à l’étape 1) qui représente la méthode dynamique en appelant la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2591-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="d2591-126">La création du délégué achève la méthode, et toute tentative supplémentaire de changement de la méthode (par exemple l’ajout de code MSIL) est ignorée.</span><span class="sxs-lookup"><span data-stu-id="d2591-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="d2591-127">Le code suivant crée le délégué et l’appelle, à l’aide d’un délégué générique.</span><span class="sxs-lookup"><span data-stu-id="d2591-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="d2591-128">Pour définir et exécuter une méthode dynamique liée à un objet</span><span class="sxs-lookup"><span data-stu-id="d2591-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="d2591-129">Déclarez un type délégué pour exécuter la méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="d2591-130">Vous pouvez utiliser un délégué générique pour réduire le nombre de types délégués que vous devez déclarer.</span><span class="sxs-lookup"><span data-stu-id="d2591-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="d2591-131">Le code suivant déclare un type délégué générique qui peut être utilisé pour exécuter n’importe quelle méthode avec un paramètre et une valeur de retour, ou une méthode avec deux paramètres et une valeur de retour si le délégué est lié à un objet.</span><span class="sxs-lookup"><span data-stu-id="d2591-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="d2591-132">Créez un tableau qui spécifie les types de paramètre de la méthode dynamique.</span><span class="sxs-lookup"><span data-stu-id="d2591-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="d2591-133">Si le délégué représentant la méthode doit être lié à un objet, le premier paramètre doit correspondre au type auquel le délégué est lié.</span><span class="sxs-lookup"><span data-stu-id="d2591-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="d2591-134">Cet exemple contient deux paramètres, de type `Example` et `int` (`Integer` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2591-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="d2591-135">Créer un <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="d2591-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="d2591-136">Dans cet exemple, la méthode n’a pas de nom.</span><span class="sxs-lookup"><span data-stu-id="d2591-136">In this example the method has no name.</span></span> <span data-ttu-id="d2591-137">Le type de la valeur de retour est spécifié comme `int` (`Integer` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2591-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="d2591-138">La méthode a accès aux membres privés et protégés de la classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="d2591-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="d2591-139">Émettez le corps de méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-139">Emit the method body.</span></span> <span data-ttu-id="d2591-140">Dans cet exemple, un objet <xref:System.Reflection.Emit.ILGenerator> est utilisé pour émettre le code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d2591-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d2591-141">Vous pourriez également utiliser un objet <xref:System.Reflection.Emit.DynamicILInfo> conjointement avec des générateurs de code non managé pour émettre le corps de méthode pour un <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="d2591-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="d2591-142">Le code MSIL de cet exemple charge le premier argument, qui est une instance de la classe `Example`, et l’utilise pour charger la valeur d’un champ d’instance privé de type `int`.</span><span class="sxs-lookup"><span data-stu-id="d2591-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="d2591-143">Le deuxième argument est chargé, et les deux nombres sont multipliés.</span><span class="sxs-lookup"><span data-stu-id="d2591-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="d2591-144">Si le résultat est supérieur à `int`, la valeur est tronquée et les bits les plus significatifs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="d2591-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="d2591-145">La méthode retourne, avec la valeur de retour sur la pile.</span><span class="sxs-lookup"><span data-stu-id="d2591-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="d2591-146">Créez une instance du délégué (déclaré à l’étape 1) qui représente la méthode dynamique en appelant la surcharge de méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="d2591-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="d2591-147">La création du délégué achève la méthode, et toute tentative supplémentaire de changement de la méthode (par exemple l’ajout de code MSIL) est ignorée.</span><span class="sxs-lookup"><span data-stu-id="d2591-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2591-148">Vous pouvez appeler la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> plusieurs fois afin de créer des délégués liés à d’autres instances du type cible.</span><span class="sxs-lookup"><span data-stu-id="d2591-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="d2591-149">Le code suivant lie la méthode à une nouvelle instance de la classe `Example` dont le champ de test privé a la valeur 42.</span><span class="sxs-lookup"><span data-stu-id="d2591-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="d2591-150">Autrement dit, chaque fois que le délégué est appelé, l’instance de `Example` est passée au premier paramètre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="d2591-151">Le délégué `OneParameter` est utilisé, car le premier paramètre de la méthode reçoit toujours l’instance de `Example`.</span><span class="sxs-lookup"><span data-stu-id="d2591-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="d2591-152">Quand le délégué est appelé, seul le deuxième paramètre est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d2591-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="d2591-153">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2591-153">Example</span></span>  
 <span data-ttu-id="d2591-154">L’exemple de code suivant montre une méthode dynamique simple et une méthode dynamique liée à une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="d2591-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="d2591-155">La méthode dynamique simple prend un argument, un entier 32 bits, et retourne le carré 64 bits de cet entier.</span><span class="sxs-lookup"><span data-stu-id="d2591-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="d2591-156">Un délégué générique est utilisé pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="d2591-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="d2591-157">La deuxième méthode dynamique a deux paramètres, de type `Example` et `int` (`Integer` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d2591-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="d2591-158">Quand la méthode dynamique a été créée, elle est liée à une instance de `Example`, à l’aide d’un délégué générique qui a un argument de type `int`.</span><span class="sxs-lookup"><span data-stu-id="d2591-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="d2591-159">Le délégué n’a pas d’argument de type `Example`, car le premier paramètre de la méthode reçoit toujours l’instance liée de `Example`.</span><span class="sxs-lookup"><span data-stu-id="d2591-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="d2591-160">Quand le délégué est appelé, seul l’argument `int` est fourni.</span><span class="sxs-lookup"><span data-stu-id="d2591-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="d2591-161">Cette méthode dynamique accède à un champ privé de la classe `Example` et retourne le produit du champ privé et l’argument `int`.</span><span class="sxs-lookup"><span data-stu-id="d2591-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="d2591-162">L’exemple de code définit des délégués qui peuvent être utilisés pour exécuter les méthodes.</span><span class="sxs-lookup"><span data-stu-id="d2591-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2591-163">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d2591-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d2591-164">Le code contient les instructions `using` C# (`Imports` en Visual Basic) nécessaires à la compilation.</span><span class="sxs-lookup"><span data-stu-id="d2591-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="d2591-165">Aucune référence d’assembly supplémentaire n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="d2591-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="d2591-166">Compilez le code sur la ligne de commande à l’aide de csc.exe, vbc.exe ou cl.exe.</span><span class="sxs-lookup"><span data-stu-id="d2591-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="d2591-167">Pour compiler le code dans Visual Studio, placez-le dans un modèle de projet d’application console.</span><span class="sxs-lookup"><span data-stu-id="d2591-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2591-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2591-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="d2591-169">Utilisation de l’émission de réflexion</span><span class="sxs-lookup"><span data-stu-id="d2591-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="d2591-170">Scénarios de méthodes dynamiques avec Émission de réflexion</span><span class="sxs-lookup"><span data-stu-id="d2591-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
