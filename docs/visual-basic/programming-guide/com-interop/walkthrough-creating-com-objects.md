---
title: "Procédure pas à pas : création d'objets COM avec Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="affc5-102">Procédure pas à pas : création d'objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="affc5-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="affc5-103">Lors de la création de nouvelles applications ou des composants, il est préférable de créer des assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="affc5-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="affc5-104">Toutefois, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] facilite également l’exposition d’un composant .NET Framework à COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-104">However, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="affc5-105">Cela vous permet de fournir de nouveaux composants pour des suites d’applications antérieures qui requièrent des composants COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="affc5-106">Cette procédure pas à pas montre comment utiliser [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour exposer [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objets en tant qu’objets COM, avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="affc5-107">Pour exposer des objets COM, le plus simple consiste à l’aide du modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="affc5-108">Le modèle de classe COM crée une nouvelle classe, puis configure votre projet pour générer la couche classe et interopérabilité sous la forme d’un objet COM et l’inscrire auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="affc5-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="affc5-109">Bien que vous pouvez également exposer une classe créée dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] comme un objet COM pour le code non managé à utiliser, il n’est pas un objet COM réel et ne peut pas être utilisé par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="affc5-109">Although you can also expose a class created in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="affc5-110">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="affc5-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="affc5-111">Pour créer un objet COM à l’aide du modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="affc5-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="affc5-112">Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="affc5-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="affc5-113">Dans le **nouveau projet** boîte de dialogue sous le **Types de projets** champ, vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="affc5-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="affc5-114">Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="affc5-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="affc5-115">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="affc5-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="affc5-116">Sélectionnez **ajouter un nouvel élément** à partir de la **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="affc5-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="affc5-117">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="affc5-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="affc5-118">Sélectionnez **classe COM** à partir de la **modèles** liste, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="affc5-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="affc5-119">Ajoute une nouvelle classe et configure le nouveau projet pour COM interop.</span><span class="sxs-lookup"><span data-stu-id="affc5-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="affc5-120">Ajoutez le code tels que les propriétés, méthodes et événements à la classe COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="affc5-121">Sélectionnez **générer ClassLibrary1** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="affc5-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="affc5-122">génère l’assembly et inscrit l’objet COM avec le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="affc5-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="affc5-123">Création d’objets COM sans le modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="affc5-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="affc5-124">Vous pouvez également créer une classe COM manuellement au lieu de l’aide du modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="affc5-125">Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez mieux contrôler la façon dont les objets COM sont définies.</span><span class="sxs-lookup"><span data-stu-id="affc5-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="affc5-126">Pour configurer votre projet pour générer un objet COM</span><span class="sxs-lookup"><span data-stu-id="affc5-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="affc5-127">Ouvrez un nouveau projet d’Application Windows à partir de la **fichier** en cliquant sur **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="affc5-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="affc5-128">Dans le **nouveau projet** boîte de dialogue sous le **Types de projets** champ, vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="affc5-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="affc5-129">Sélectionnez **bibliothèque de classes** à partir de la **modèles** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="affc5-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="affc5-130">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="affc5-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="affc5-131">Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="affc5-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="affc5-132">Le **Concepteur de projets** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="affc5-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="affc5-133">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="affc5-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="affc5-134">Sélectionnez le **inscrire pour COM Interop** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="affc5-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="affc5-135">Pour définir le code dans votre classe pour créer un objet COM.</span><span class="sxs-lookup"><span data-stu-id="affc5-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="affc5-136">Dans **l’Explorateur de solutions**, double-cliquez sur **Class1.vb** pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="affc5-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="affc5-137">Renommez la classe `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="affc5-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="affc5-138">Ajoutez les constantes suivantes à `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="affc5-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="affc5-139">Ils stockera les constantes GUID (Globally Unique Identifier) qui les objets COM doivent obligatoirement avoir.</span><span class="sxs-lookup"><span data-stu-id="affc5-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="affc5-140">Dans le menu **Outils**, cliquez sur **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="affc5-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="affc5-141">Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="affc5-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="affc5-142">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="affc5-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="affc5-143">Remplacez la chaîne vide pour la `ClassId` avec le GUID, les accolades suppression le début et de fin.</span><span class="sxs-lookup"><span data-stu-id="affc5-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="affc5-144">Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , votre code doit apparaître comme suit.</span><span class="sxs-lookup"><span data-stu-id="affc5-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="affc5-145">Répétez les étapes précédentes pour le `InterfaceId` et `EventsId` constantes, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="affc5-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="affc5-146">Assurez-vous que les GUID sont nouveaux et uniques ; dans le cas contraire, votre composant COM pourrait être en conflit avec d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="affc5-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="affc5-147">Ajouter le `ComClass` attribut `ComClass1`, en spécifiant les GUID pour l’ID de classe, les ID d’Interface et les ID des événements comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="affc5-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="affc5-148">Classes COM doivent avoir un sans paramètre `Public Sub New()` constructeur ou la classe n’est pas inscrite correctement.</span><span class="sxs-lookup"><span data-stu-id="affc5-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="affc5-149">Ajoutez un constructeur sans paramètre à la classe :</span><span class="sxs-lookup"><span data-stu-id="affc5-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="affc5-150">Ajouter des propriétés, méthodes et événements à la classe, en terminant par un `End Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="affc5-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="affc5-151">Sélectionnez **générer la Solution** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="affc5-151">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="affc5-152">génère l’assembly et inscrit l’objet COM avec le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="affc5-152"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="affc5-153">Les objets COM que vous générez avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas être utilisé par d’autres [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] applications, car ils ne sont pas des objets COM trues.</span><span class="sxs-lookup"><span data-stu-id="affc5-153">The COM objects you generate with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot be used by other [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="affc5-154">Tente d’ajouter des références à ces objets COM génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="affc5-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="affc5-155">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="affc5-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affc5-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="affc5-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="affc5-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="affc5-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="affc5-158">Procédure pas à pas : implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="affc5-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="affc5-159">#Region (directive)</span><span class="sxs-lookup"><span data-stu-id="affc5-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="affc5-160">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="affc5-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="affc5-161">Dépannage des problèmes liés à l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="affc5-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
