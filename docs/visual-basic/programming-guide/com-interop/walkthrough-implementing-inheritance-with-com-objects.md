---
title: "Procédure pas à pas : Implémentation de l’héritage avec les objets COM (Visual Basic) | Documents Microsoft"
ms.custom: 
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
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
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
ms.openlocfilehash: 0e816d1728678467d930de524b894d175f9b0c0a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="cb0f7-102">Procédure pas à pas : implémentation de l'héritage avec les objets COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb0f7-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="cb0f7-103">Vous pouvez dériver des classes Visual Basic à partir de `Public` classes dans les objets COM, même ceux créés dans les versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb0f7-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="cb0f7-104">Les propriétés et méthodes des classes héritées d’objets COM peuvent être substituées ou surchargées comme les propriétés et méthodes de toute autre classe de base peuvent être substituées ou surchargés.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="cb0f7-105">Héritage à partir d’objets COM est utile lorsque vous disposez d’une bibliothèque de classe existante que vous ne souhaitez pas recompiler.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="cb0f7-106">La procédure suivante montre comment utiliser Visual Basic 6.0 pour créer un objet COM contenant une classe, puis l’utiliser comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="cb0f7-107">Pour générer l’objet COM qui est utilisé dans cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="cb0f7-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="cb0f7-108">Dans Visual Basic 6.0, ouvrez un nouveau projet de DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="cb0f7-109">Un projet nommé `Project1` est créé.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-109">A project named `Project1` is created.</span></span> <span data-ttu-id="cb0f7-110">Il a une classe nommée `Class1`.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="cb0f7-111">Dans le **Explorateur de projets**, avec le bouton droit **Project1**, puis cliquez sur **Project1 propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="cb0f7-112">Le **propriétés du projet** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="cb0f7-113">Sur le **général** onglet de la **propriétés du projet** boîte de dialogue, remplacez le nom du projet en tapant `ComObject1` dans les **le nom du projet** champ.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="cb0f7-114">Dans le **Explorateur de projets**, avec le bouton droit `Class1`, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="cb0f7-115">Le **propriétés** fenêtre de la classe s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="cb0f7-116">Modifier la `Name` propriété `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="cb0f7-117">Dans le **Explorateur de projets**, avec le bouton droit `MathFunctions`, puis cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="cb0f7-118">Le **éditeur de Code** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="cb0f7-119">Ajoutez une variable locale pour contenir la valeur de propriété :</span><span class="sxs-lookup"><span data-stu-id="cb0f7-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="cb0f7-120">Ajoutez la propriété `Let` et la propriété `Get` les procédures de propriété :</span><span class="sxs-lookup"><span data-stu-id="cb0f7-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="cb0f7-121">Ajoutez une fonction :</span><span class="sxs-lookup"><span data-stu-id="cb0f7-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="cb0f7-122">Créez et inscrivez l’objet COM en cliquant sur **Créer ComObject1.dll** sur la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cb0f7-123">Bien que vous pouvez également exposer une classe créée avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] comme un objet COM, il n’est pas un véritable objet COM et ne peut pas être utilisé dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-123">Although you can also expose a class created with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="cb0f7-124">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="cb0f7-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="cb0f7-125">Assemblys d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="cb0f7-125">Interop Assemblies</span></span>  
 <span data-ttu-id="cb0f7-126">Dans la procédure suivante, vous allez créer un assembly d’interopérabilité qui sert de pont entre le code non managé (par exemple, un objet COM) et le code managé [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] uses.</span></span> <span data-ttu-id="cb0f7-127">L’assembly d’interopérabilité qui [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] crée gère de nombreux détails de l’utilisation de COM d’objets, tels que *le marshaling d’interopérabilité*, le processus empaqueter des paramètres et valeurs de retour dans les données équivalent types lors de leur déplacement vers et depuis des objets COM.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-127">The interop assembly that [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="cb0f7-128">La référence dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application pointe vers l’assembly d’interopérabilité, pas l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-128">The reference in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="cb0f7-129">Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cb0f7-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="cb0f7-130">Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet d’Application Windows.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-130">Open a new [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="cb0f7-131">Sur le **projet** menu, cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="cb0f7-132">Le **ajouter une référence** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="cb0f7-133">Sur le **COM** onglet, double-cliquez sur `ComObject1` dans les **nom du composant** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="cb0f7-134">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="cb0f7-135">Le **ajouter un nouvel élément** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="cb0f7-136">Dans le **modèles** volet, cliquez sur **classe**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="cb0f7-137">Le nom de fichier par défaut, `Class1.vb`, apparaît dans le **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="cb0f7-138">Remplacez ce champ par MathClass.vb et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="cb0f7-139">Cela crée une classe nommée `MathClass`et affiche son code.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="cb0f7-140">Ajoutez le code suivant au début du `MathClass` pour hériter de la classe COM.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     <span data-ttu-id="cb0f7-141">[!code-vb[VbVbalrInterop&#31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb0f7-141">[!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span></span>  
  
7.  <span data-ttu-id="cb0f7-142">Surcharge de la méthode publique de la classe de base en ajoutant le code suivant à `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="cb0f7-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="cb0f7-143">[!code-vb[VbVbalrInterop n°&32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb0f7-143">[!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span></span>  
  
8.  <span data-ttu-id="cb0f7-144">Étendez la classe héritée en ajoutant le code suivant à `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="cb0f7-144">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="cb0f7-145">[!code-vb[VbVbalrInterop&#33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb0f7-145">[!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span></span>  
  
 <span data-ttu-id="cb0f7-146">La nouvelle classe hérite des propriétés de la classe de base dans l’objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-146">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="cb0f7-147">Pour tester la classe héritée</span><span class="sxs-lookup"><span data-stu-id="cb0f7-147">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="cb0f7-148">Ajouter un bouton à votre formulaire de démarrage et double-cliquez dessus pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-148">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="cb0f7-149">Dans son `Click` procédure gestionnaire d’événements, ajoutez le code suivant pour créer une instance de `MathClass` et appeler les méthodes surchargées :</span><span class="sxs-lookup"><span data-stu-id="cb0f7-149">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     <span data-ttu-id="cb0f7-150">[!code-vb[VbVbalrInterop&#34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb0f7-150">[!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span></span>  
  
3.  <span data-ttu-id="cb0f7-151">Exécutez le projet en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-151">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="cb0f7-152">Lorsque vous cliquez sur le bouton du formulaire, le `AddNumbers` méthode est d’abord appelée avec `Short` numéros, type de données et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] choisit la méthode appropriée à partir de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-152">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="cb0f7-153">Le deuxième appel à `AddNumbers` est dirigé vers la méthode surchargée à partir de `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-153">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="cb0f7-154">Le troisième appel appelle le `SubtractNumbers` (méthode), qui étend la classe.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-154">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="cb0f7-155">La propriété dans la classe de base est définie, et la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-155">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cb0f7-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cb0f7-156">Next Steps</span></span>  
 <span data-ttu-id="cb0f7-157">Vous avez peut-être remarqué que surchargées `AddNumbers` fonction semble avoir les mêmes données de type que la méthode héritée de la classe de base de l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-157">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="cb0f7-158">Il s’agit, car les arguments et paramètres de la méthode de classe de base sont définis comme des nombres entiers 16 bits dans Visual Basic 6.0, mais sont exposés comme des nombres entiers 16 bits de type `Short` dans les versions ultérieures de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-158">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="cb0f7-159">La nouvelle fonction accepte les nombres entiers 32 bits et surcharge la fonction de classe de base.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-159">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="cb0f7-160">Lorsque vous travaillez avec des objets COM, assurez-vous de vérifier la taille et le type des paramètres.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-160">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="cb0f7-161">Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6.0 en tant qu’argument, vous ne peut pas fournir une collection à partir d’une version ultérieure de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-161">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="cb0f7-162">Propriétés et méthodes héritées des classes COM peuvent être substituées, ce qui signifie que vous pouvez déclarer une propriété locale ou une méthode qui remplace une propriété ou une méthode héritée d’une classe COM de base.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-162">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="cb0f7-163">Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution des autres propriétés et méthodes avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb0f7-163">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="cb0f7-164">Si vous substituez une propriété ou une méthode héritée d’une classe COM, vous devez remplacer toutes les autres propriétés et méthodes héritées.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-164">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="cb0f7-165">Les propriétés qui utilisent `ByRef` paramètres ne peut pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="cb0f7-165">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0f7-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb0f7-166">See Also</span></span>  
 <span data-ttu-id="cb0f7-167">[Interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="cb0f7-167">[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="cb0f7-168"> [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb0f7-168"> [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="cb0f7-169"> [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="cb0f7-169"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)</span></span>
