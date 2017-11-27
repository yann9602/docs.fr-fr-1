---
title: "Procédure pas à pas : implémentation de l'héritage avec les objets COM (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d6906c58431a0e844e8f430ade10ae819e77ff2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="dcc5d-102">Procédure pas à pas : implémentation de l'héritage avec les objets COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc5d-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="dcc5d-103">Vous pouvez dériver des classes Visual Basic à partir de `Public` classes dans les objets COM, même ceux créés dans les versions antérieures de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcc5d-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="dcc5d-104">Les propriétés et méthodes des classes héritées d’objets COM peuvent être substituées ou surchargées comme les propriétés et méthodes de toute autre classe de base peuvent être remplacées ou surchargés.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="dcc5d-105">L’héritage à partir des objets COM est utile lorsque vous disposez d’une bibliothèque de classe existante que vous ne souhaitez pas recompiler.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="dcc5d-106">La procédure suivante montre comment utiliser Visual Basic 6.0 pour créer un objet COM qui contient une classe, puis l’utiliser comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="dcc5d-107">Pour générer l’objet COM qui est utilisé dans cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="dcc5d-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="dcc5d-108">Dans Visual Basic 6.0, ouvrez un nouveau projet de DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="dcc5d-109">Un projet nommé `Project1` est créé.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-109">A project named `Project1` is created.</span></span> <span data-ttu-id="dcc5d-110">Il comporte une classe nommée `Class1`.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="dcc5d-111">Dans le **Explorateur de projets**, avec le bouton droit **Projet1**, puis cliquez sur **Propriétés Projet1**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="dcc5d-112">Le **propriétés du projet** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="dcc5d-113">Sur le **général** onglet de la **propriétés du projet** boîte de dialogue, changez le nom du projet en tapant `ComObject1` dans les **nom du projet** champ.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="dcc5d-114">Dans le **Explorateur de projets**, avec le bouton droit `Class1`, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="dcc5d-115">Le **propriétés** fenêtre de la classe s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="dcc5d-116">Modifier la `Name` propriété `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="dcc5d-117">Dans le **Explorateur de projets**, avec le bouton droit `MathFunctions`, puis cliquez sur **afficher le Code**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="dcc5d-118">Le **éditeur de Code** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="dcc5d-119">Ajoutez une variable locale pour stocker la valeur de propriété :</span><span class="sxs-lookup"><span data-stu-id="dcc5d-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="dcc5d-120">Ajoutez la propriété `Let` et la propriété `Get` procédures de propriété :</span><span class="sxs-lookup"><span data-stu-id="dcc5d-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="dcc5d-121">Ajouter une fonction :</span><span class="sxs-lookup"><span data-stu-id="dcc5d-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="dcc5d-122">Créer et inscrire l’objet COM en cliquant sur **Créer ComObject1.dll** sur la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dcc5d-123">Bien que vous pouvez également exposer une classe créée avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] comme un objet COM, il n’est pas un objet COM réel et ne peut pas être utilisé dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-123">Although you can also expose a class created with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="dcc5d-124">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="dcc5d-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="dcc5d-125">Assemblys d’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="dcc5d-125">Interop Assemblies</span></span>  
 <span data-ttu-id="dcc5d-126">Dans la procédure suivante, vous allez créer un assembly d’interopérabilité, qui fait Office de pont entre le code non managé (par exemple, un objet COM) et le code managé [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses.</span></span> <span data-ttu-id="dcc5d-127">L’assembly d’interopérabilité qui [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] crée les gère de nombreux détails de l’utilisation de COM d’objets, tels que *le marshaling d’interopérabilité*, le processus empaqueter des paramètres et valeurs de retour des données de l’équivalentes de types lors de leur déplacement à à partir de COM, objets et.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-127">The interop assembly that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="dcc5d-128">La référence dans le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] application pointe vers l’assembly d’interopérabilité, pas l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-128">The reference in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="dcc5d-129">Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="dcc5d-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="dcc5d-130">Ouvrez un nouveau projet d’application Windows [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcc5d-130">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="dcc5d-131">Dans le menu **Projet**, cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="dcc5d-132">Le **ajouter une référence** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="dcc5d-133">Sur le **COM** onglet, double-cliquez sur `ComObject1` dans les **nom du composant** liste et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="dcc5d-134">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="dcc5d-135">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="dcc5d-136">Dans le **modèles** volet, cliquez sur **classe**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="dcc5d-137">Le nom de fichier par défaut, `Class1.vb`, apparaît dans le **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="dcc5d-138">Remplacez ce champ par MathClass.vb et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="dcc5d-139">Cette opération crée une classe nommée `MathClass`et affiche son code.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="dcc5d-140">Ajoutez le code suivant en haut du `MathClass` d’hériter de la classe COM.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="dcc5d-141">Surcharge de la méthode publique de la classe de base en ajoutant le code suivant à `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="dcc5d-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="dcc5d-142">Étendez la classe héritée en ajoutant le code suivant à `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="dcc5d-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="dcc5d-143">La nouvelle classe hérite des propriétés de la classe de base dans l’objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="dcc5d-144">Pour tester la classe héritée</span><span class="sxs-lookup"><span data-stu-id="dcc5d-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="dcc5d-145">Ajouter un bouton à votre formulaire de démarrage, puis double-cliquez dessus pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="dcc5d-146">Dans du bouton `Click` procédure gestionnaire d’événements, ajoutez le code suivant pour créer une instance de `MathClass` et appeler les méthodes surchargées :</span><span class="sxs-lookup"><span data-stu-id="dcc5d-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="dcc5d-147">Exécutez le projet en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="dcc5d-148">Lorsque vous cliquez sur le bouton dans le formulaire, le `AddNumbers` méthode est d’abord appelée avec `Short` nombres, de type de données et [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] choisit la méthode appropriée à partir de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="dcc5d-149">Le deuxième appel à `AddNumbers` est dirigé vers la méthode de surcharge à partir de `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="dcc5d-150">Le troisième appel appelle le `SubtractNumbers` (méthode), qui étend la classe.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="dcc5d-151">La propriété dans la classe de base est définie, et la valeur est affichée.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dcc5d-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dcc5d-152">Next Steps</span></span>  
 <span data-ttu-id="dcc5d-153">Vous avez peut-être remarqué que surchargées `AddNumbers` fonction semble avoir les mêmes données que la méthode héritée de la classe de base de l’objet COM de type.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="dcc5d-154">Il s’agit, car les arguments et les paramètres de la méthode de classe de base sont définis en tant qu’entiers 16 bits dans Visual Basic 6.0, mais elles sont exposées en tant qu’entiers 16 bits de type `Short` dans les versions ultérieures de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="dcc5d-155">La nouvelle fonction accepte les nombres entiers 32 bits et les surcharges de la fonction de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="dcc5d-156">Lorsque vous travaillez avec des objets COM, vérifiez que les types de données et la taille des paramètres.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="dcc5d-157">Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6.0 en tant qu’argument, vous ne peut pas fournir une collection à partir d’une version ultérieure de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="dcc5d-158">Propriétés et méthodes héritées des classes COM peuvent être remplacées, ce qui signifie que que vous pouvez déclarer une propriété locale ou une méthode qui remplace une propriété ou une méthode héritée d’une classe COM de base.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="dcc5d-159">Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution des autres propriétés et méthodes avec les exceptions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dcc5d-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="dcc5d-160">Si vous substituez une propriété ou une méthode héritée d’une classe COM, vous devez substituer toutes les autres propriétés et méthodes héritées.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="dcc5d-161">Les propriétés qui utilisent `ByRef` paramètres ne peut pas être substituées.</span><span class="sxs-lookup"><span data-stu-id="dcc5d-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc5d-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcc5d-162">See Also</span></span>  
 [<span data-ttu-id="dcc5d-163">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dcc5d-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="dcc5d-164">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="dcc5d-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="dcc5d-165">Short (type de données)</span><span class="sxs-lookup"><span data-stu-id="dcc5d-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
