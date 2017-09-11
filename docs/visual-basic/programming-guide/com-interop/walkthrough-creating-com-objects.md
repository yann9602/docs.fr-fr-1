---
title: "Procédure pas à pas : Création d’objets COM avec Visual Basic | Documents Microsoft"
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
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
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
ms.openlocfilehash: 859a8fc7440eecc0cadbfa8ea236dad7cae99247
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="eef1b-102">Procédure pas à pas : création d'objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eef1b-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="eef1b-103">Lors de la création de nouvelles applications ou composants, il est préférable de créer des assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eef1b-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="eef1b-104">Toutefois, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] facilite également l’exposition d’un composant .NET Framework à COM.</span><span class="sxs-lookup"><span data-stu-id="eef1b-104">However, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="eef1b-105">Cela vous permet de fournir de nouveaux composants pour des suites d’applications antérieures qui requièrent des composants COM..</span><span class="sxs-lookup"><span data-stu-id="eef1b-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="eef1b-106">Cette procédure pas à pas montre comment utiliser [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour exposer [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objets en tant qu’objets COM, avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="eef1b-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to expose [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="eef1b-107">Pour exposer des objets COM, le plus simple consiste à l’aide de ce modèle.</span><span class="sxs-lookup"><span data-stu-id="eef1b-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="eef1b-108">Le modèle de classe COM crée une nouvelle classe, puis configure votre projet pour générer la couche classe et interopérabilité sous la forme d’un objet COM et l’inscrire auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="eef1b-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eef1b-109">Bien que vous pouvez également exposer une classe créée dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] en tant qu’objet COM pour le code non managé à utiliser, il n’est pas un véritable objet COM et ne peut pas être utilisé par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="eef1b-109">Although you can also expose a class created in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="eef1b-110">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="eef1b-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="eef1b-111">Pour créer un objet COM à l’aide du modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="eef1b-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="eef1b-112">Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="eef1b-113">Dans le **nouveau projet** boîte de dialogue sous la **Types de projet** champ, vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="eef1b-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="eef1b-114">Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="eef1b-115">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eef1b-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="eef1b-116">Sélectionnez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="eef1b-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="eef1b-117">Le **ajouter un nouvel élément** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eef1b-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="eef1b-118">Sélectionnez **classe COM** à partir de la **modèles** liste, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="eef1b-119">Ajoute une nouvelle classe et configure le nouveau projet pour COM interop.</span><span class="sxs-lookup"><span data-stu-id="eef1b-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="eef1b-120">Ajoutez à la classe COM code tels que les propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="eef1b-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="eef1b-121">Sélectionnez **générer ClassLibrary1** à partir de la **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="eef1b-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="eef1b-122">génère l’assembly et inscrit l’objet COM avec le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="eef1b-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="eef1b-123">Création d’objets COM sans le modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="eef1b-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="eef1b-124">Vous pouvez également créer une classe COM manuellement au lieu d’utiliser le modèle de classe com..</span><span class="sxs-lookup"><span data-stu-id="eef1b-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="eef1b-125">Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez mieux contrôler la façon dont les objets COM sont définies.</span><span class="sxs-lookup"><span data-stu-id="eef1b-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="eef1b-126">Pour configurer votre projet pour générer un objet COM</span><span class="sxs-lookup"><span data-stu-id="eef1b-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="eef1b-127">Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="eef1b-128">Dans le **nouveau projet** boîte de dialogue sous la **Types de projet** champ, vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="eef1b-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="eef1b-129">Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="eef1b-130">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eef1b-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="eef1b-131">Dans **l’Explorateur de solutions**, cliquez sur votre projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="eef1b-132">Le **Concepteur de projets** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="eef1b-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="eef1b-133">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="eef1b-134">Sélectionnez le **inscrire pour COM Interop** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="eef1b-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="eef1b-135">Pour définir le code dans votre classe pour créer un objet COM</span><span class="sxs-lookup"><span data-stu-id="eef1b-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="eef1b-136">Dans **l’Explorateur de solutions**, double-cliquez sur **Class1.vb** pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="eef1b-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="eef1b-137">Renommez la classe `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="eef1b-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="eef1b-138">Ajoutez les constantes suivantes à `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="eef1b-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="eef1b-139">Ils stockera les constantes GUID (Globally Unique Identifier) que les objets COM sont tenus d’avoir.</span><span class="sxs-lookup"><span data-stu-id="eef1b-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     <span data-ttu-id="eef1b-140">[!code-vb[VbVbalrInterop n °&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef1b-140">[!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span></span>  
  
4.  <span data-ttu-id="eef1b-141">Sur le **outils** menu, cliquez sur **créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="eef1b-142">Dans le **créer un GUID** boîte de dialogue, cliquez sur **au Format de Registre** , puis **copie**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="eef1b-143">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="eef1b-143">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="eef1b-144">Remplacez la chaîne vide pour la `ClassId` avec le GUID, accolades suppression de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="eef1b-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="eef1b-145">Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , votre code doit apparaître comme suit.</span><span class="sxs-lookup"><span data-stu-id="eef1b-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     <span data-ttu-id="eef1b-146">[!code-vb[VbVbalrInterop n °&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef1b-146">[!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span></span>  
  
6.  <span data-ttu-id="eef1b-147">Répétez les étapes précédentes pour le `InterfaceId` et `EventsId` constantes, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eef1b-147">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     <span data-ttu-id="eef1b-148">[!code-vb[VbVbalrInterop n °&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef1b-148">[!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eef1b-149">Assurez-vous que les GUID sont nouveaux et uniques ; dans le cas contraire, votre composant COM pourrait être en conflit avec d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="eef1b-149">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="eef1b-150">Ajouter la `ComClass` l’attribut `ComClass1`, en spécifiant le GUID pour l’ID de classe, les ID d’Interface et les ID d’événements comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="eef1b-150">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     <span data-ttu-id="eef1b-151">[!code-vb[VbVbalrInterop n °&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef1b-151">[!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span></span>  
  
8.  <span data-ttu-id="eef1b-152">Classes COM doivent avoir un sans paramètre `Public Sub New()` constructeur ou la classe n’inscrira pas correctement.</span><span class="sxs-lookup"><span data-stu-id="eef1b-152">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="eef1b-153">Ajoutez un constructeur sans paramètre à la classe :</span><span class="sxs-lookup"><span data-stu-id="eef1b-153">Add a parameterless constructor to the class:</span></span>  
  
     <span data-ttu-id="eef1b-154">[!code-vb[VbVbalrInterop n °&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="eef1b-154">[!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span></span>  
  
9. <span data-ttu-id="eef1b-155">Ajoutez des propriétés, méthodes et événements à la classe, en terminant par un `End Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="eef1b-155">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="eef1b-156">Sélectionnez **générer la Solution** à partir de la **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="eef1b-156">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="eef1b-157">génère l’assembly et inscrit l’objet COM avec le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="eef1b-157"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eef1b-158">Les objets COM que vous générez avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas être utilisé par d’autres [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications car ils ne sont pas des objets COM trues.</span><span class="sxs-lookup"><span data-stu-id="eef1b-158">The COM objects you generate with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot be used by other [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="eef1b-159">Tente d’ajouter des références à ces objets COM génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="eef1b-159">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="eef1b-160">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="eef1b-160">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef1b-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eef1b-161">See Also</span></span>  
 <span data-ttu-id="eef1b-162"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="eef1b-162"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>   
<span data-ttu-id="eef1b-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="eef1b-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="eef1b-164"> [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="eef1b-164"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="eef1b-165"> [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="eef1b-165"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="eef1b-166"> [Interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="eef1b-166"> [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="eef1b-167"> [Dépannage des problèmes liés à l’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="eef1b-167"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span></span>
