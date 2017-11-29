---
title: "Propriétés et méthodes surchargées (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a872540716941ccd0dbb8b058508b89ce26a988
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="81a4f-102">Propriétés et méthodes surchargées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81a4f-102">Overloaded Properties and Methods (Visual Basic)</span></span>
<span data-ttu-id="81a4f-103">La surcharge est la création de plusieurs procédures, constructeur d’instance ou propriété dans une classe ayant le même nom, mais différents types d’arguments.</span><span class="sxs-lookup"><span data-stu-id="81a4f-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="81a4f-104">Utilisation de la surcharge</span><span class="sxs-lookup"><span data-stu-id="81a4f-104">Overloading Usage</span></span>  
 <span data-ttu-id="81a4f-105">La surcharge est particulièrement utile lorsque votre modèle objet impose l’utilisation de noms identiques pour les procédures qui fonctionnent sur les différents types de données.</span><span class="sxs-lookup"><span data-stu-id="81a4f-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="81a4f-106">Par exemple, une classe qui peut afficher plusieurs types de données différents peut avoir `Display` procédures ressemblent à ceci :</span><span class="sxs-lookup"><span data-stu-id="81a4f-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 <span data-ttu-id="81a4f-107">Sans surcharge, vous devez créer des noms distincts pour chaque procédure, même si celles-ci effectuent la même chose, comme le montre l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="81a4f-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 <span data-ttu-id="81a4f-108">La surcharge rend plus facile d’utiliser des propriétés ou méthodes, car elle fournit un choix de types de données qui peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="81a4f-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="81a4f-109">Par exemple, surchargées `Display` méthode décrite ci-dessus peut être appelée avec des lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="81a4f-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 <span data-ttu-id="81a4f-110">Au moment de l’exécution [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appelle la procédure correcte basés sur les types de données des paramètres que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="81a4f-110">At run time, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="81a4f-111">Règles de surcharge</span><span class="sxs-lookup"><span data-stu-id="81a4f-111">Overloading Rules</span></span>  
 <span data-ttu-id="81a4f-112">Vous créez un membre surchargé pour une classe en ajoutant deux ou plusieurs propriétés ou méthodes portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="81a4f-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="81a4f-113">À l’exception des membres dérivés surchargés, chaque membre surchargé doit avoir des listes de paramètres différentes, et les éléments suivants ne peut pas être utilisés comme une fonctionnalité de différenciation lors de la surcharge d’une propriété ou procédure :</span><span class="sxs-lookup"><span data-stu-id="81a4f-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="81a4f-114">Modificateurs, tels que `ByVal` ou `ByRef`, qui s’appliquent à un membre ou les paramètres du membre.</span><span class="sxs-lookup"><span data-stu-id="81a4f-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="81a4f-115">Noms des paramètres</span><span class="sxs-lookup"><span data-stu-id="81a4f-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="81a4f-116">Types de retour de procédures</span><span class="sxs-lookup"><span data-stu-id="81a4f-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="81a4f-117">Le `Overloads` mot clé est facultatif lors de la surcharge, mais si une surcharge membre utilise le `Overloads` (mot clé), puis tous les autres membres surchargés portant le même nom doivent également spécifier ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="81a4f-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="81a4f-118">Les classes dérivées peuvent surcharger les membres hérités avec des membres qui ont des paramètres identiques et les types de paramètre, un processus appelé *occultation par nom et signature*.</span><span class="sxs-lookup"><span data-stu-id="81a4f-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="81a4f-119">Si le `Overloads` mot clé est utilisé lors de l’occultation par nom et signature, implémentation de la classe dérivée du membre sera utilisée au lieu de l’implémentation de la classe de base, et toutes les autres surcharges de ce membre seront disponibles pour les instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="81a4f-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="81a4f-120">Si le `Overloads` mot clé est omis lors de la surcharge d’un membre hérité avec un membre qui a des paramètres identiques et les types de paramètres, puis la surcharge est appelée *occultation par le nom*.</span><span class="sxs-lookup"><span data-stu-id="81a4f-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="81a4f-121">L’occultation par le nom remplace l’implémentation héritée d’un membre et rend toutes les autres surcharges indisponibles pour les instances de la classe dérivée et ses descendants.</span><span class="sxs-lookup"><span data-stu-id="81a4f-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="81a4f-122">Le `Overloads` et `Shadows` modificateurs ne peuvent pas être utilisés avec la même propriété ou méthode.</span><span class="sxs-lookup"><span data-stu-id="81a4f-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="81a4f-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="81a4f-123">Example</span></span>  
 <span data-ttu-id="81a4f-124">L’exemple suivant crée des méthodes surchargées qui acceptent soit un `String` ou `Decimal` représentation sous forme d’un montant en dollars et de retourner une chaîne contenant la taxe.</span><span class="sxs-lookup"><span data-stu-id="81a4f-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="81a4f-125">Pour utiliser cet exemple pour créer une méthode surchargée</span><span class="sxs-lookup"><span data-stu-id="81a4f-125">To use this example to create an overloaded method</span></span>  
  
1.  <span data-ttu-id="81a4f-126">Ouvrez un nouveau projet et ajoutez une classe nommée `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="81a4f-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="81a4f-127">Ajoutez le code suivant à la classe `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="81a4f-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  <span data-ttu-id="81a4f-128">Ajoutez la procédure suivante à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="81a4f-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  <span data-ttu-id="81a4f-129">Ajouter un bouton à votre formulaire et appelez le `ShowTax` procédure à partir de la `Button1_Click` événements du bouton.</span><span class="sxs-lookup"><span data-stu-id="81a4f-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="81a4f-130">Exécutez le projet et cliquez sur le bouton du formulaire pour tester surchargées `ShowTax` procédure.</span><span class="sxs-lookup"><span data-stu-id="81a4f-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="81a4f-131">Au moment de l’exécution, le compilateur choisit la fonction surchargée adéquate qui correspond aux paramètres utilisés.</span><span class="sxs-lookup"><span data-stu-id="81a4f-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="81a4f-132">Lorsque vous cliquez sur le bouton, la méthode surchargée est appelée en premier avec un `Price` paramètre qui est une chaîne et le message « le prix est une chaîne.</span><span class="sxs-lookup"><span data-stu-id="81a4f-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="81a4f-133">La taxe est $5,12" s’affiche.</span><span class="sxs-lookup"><span data-stu-id="81a4f-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="81a4f-134">`TaxAmount`est appelée avec un `Decimal` la valeur de la deuxième fois et le message, « le prix est une valeur décimale.</span><span class="sxs-lookup"><span data-stu-id="81a4f-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="81a4f-135">La taxe est $5,12" s’affiche.</span><span class="sxs-lookup"><span data-stu-id="81a4f-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a4f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81a4f-136">See Also</span></span>  
 [<span data-ttu-id="81a4f-137">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="81a4f-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="81a4f-138">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81a4f-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="81a4f-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="81a4f-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="81a4f-140">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="81a4f-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="81a4f-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="81a4f-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="81a4f-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="81a4f-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="81a4f-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="81a4f-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="81a4f-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="81a4f-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="81a4f-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="81a4f-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
