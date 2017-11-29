---
title: My.Forms, objet
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="e5c4a-102">My.Forms, objet</span><span class="sxs-lookup"><span data-stu-id="e5c4a-102">My.Forms Object</span></span>
<span data-ttu-id="e5c4a-103">Fournit des propriétés pour accéder à une instance de chaque Windows form déclaré dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c4a-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="e5c4a-104">Remarks</span></span>  
 <span data-ttu-id="e5c4a-105">Le `My.Forms` objet fournit une instance de chaque formulaire dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="e5c4a-106">Le nom de la propriété est le même que le nom du formulaire auquel la propriété accède.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="e5c4a-107">Pour plus d’informations sur l’ajout de formes à un projet, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="e5c4a-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="e5c4a-108">Vous pouvez accéder aux écrans fournis par le `My.Forms` objet en utilisant le nom du formulaire, sans qualification.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="e5c4a-109">Étant donné que le nom de propriété est identique au nom de type du formulaire, ainsi vous permet d’accéder à un formulaire comme s’il avait une instance par défaut.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="e5c4a-110">Par exemple, `My.Forms.Form1.Show` équivaut à `Form1.Show`.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="e5c4a-111">Le `My.Forms` objet expose uniquement les formulaires associés au projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="e5c4a-112">Il ne fournit pas d’accès aux formulaires déclarés dans les DLL référencées.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="e5c4a-113">Pour accéder à un formulaire par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*. *Formulaire*.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="e5c4a-114">Vous pouvez utiliser le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriété pour obtenir une collection de formulaires ouverts de toute l’application.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="e5c4a-115">L’objet et ses propriétés sont disponibles uniquement pour les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5c4a-116">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e5c4a-116">Properties</span></span>  
 <span data-ttu-id="e5c4a-117">Chaque propriété de la `My.Forms` objet fournit l’accès à une instance d’un formulaire dans le projet actuel.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="e5c4a-118">Le nom de la propriété est le même que le nom du formulaire auquel accède la propriété et le type de propriété est le même que le type de formulaire.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c4a-119">S’il existe un conflit de noms, le nom de propriété pour accéder à un formulaire est *RootNamespace*_*Namespace*\_*formulaire*.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="e5c4a-120">Par exemple, prenons deux formulaires nommés `Form1.`si une de ces formes est dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1`, vous accédez à ce formulaire via `My.Forms.WindowsApplication1_Namespace1_Form1`.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="e5c4a-121">Le `My.Forms` objet fournit l’accès à l’instance du formulaire principal de l’application qui a été créé au démarrage.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="e5c4a-122">Pour toutes les autres formes, le `My.Forms` objet crée une nouvelle instance du formulaire lorsqu’il est accessible et l’enregistre.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="e5c4a-123">Les tentatives suivantes pour accéder à cette propriété retournent cette instance du formulaire.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="e5c4a-124">Vous pouvez supprimer un formulaire en assignant `Nothing` à la propriété de ce formulaire.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="e5c4a-125">Les appels de méthode setter de propriété le <xref:System.Windows.Forms.Form.Close%2A> méthode du formulaire, puis assigne `Nothing` à la valeur stockée.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="e5c4a-126">Si vous assignez une valeur autre que `Nothing` à la propriété, la méthode setter lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="e5c4a-127">Vous pouvez tester si une propriété de la `My.Forms` objet stocke une instance du formulaire à l’aide de la `Is` ou `IsNot` opérateur.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="e5c4a-128">Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c4a-129">En règle générale, les `Is` ou `IsNot` opérateur doit lire la valeur de la propriété pour effectuer la comparaison.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="e5c4a-130">Toutefois, si la propriété stocke actuellement `Nothing`, la propriété crée une nouvelle instance de la forme et puis retourne cette instance.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="e5c4a-131">Toutefois, le compilateur Visual Basic traite les propriétés de la `My.Forms` différemment de l’objet et permet la `Is` ou `IsNot` opérateur afin de vérifier l’état de la propriété sans modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c4a-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5c4a-132">Example</span></span>  
 <span data-ttu-id="e5c4a-133">Cet exemple modifie le titre de la valeur par défaut `SidebarMenu` formulaire.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="e5c4a-134">Pour cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu`.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="e5c4a-135">Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="e5c4a-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="e5c4a-136">Ce code ne fonctionne que dans un projet d’Application Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c4a-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c4a-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5c4a-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="e5c4a-138">Disponibilité par Type de projet</span><span class="sxs-lookup"><span data-stu-id="e5c4a-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="e5c4a-139">Type de projet</span><span class="sxs-lookup"><span data-stu-id="e5c4a-139">Project type</span></span>|<span data-ttu-id="e5c4a-140">Disponible</span><span class="sxs-lookup"><span data-stu-id="e5c4a-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="e5c4a-141">Application Windows</span><span class="sxs-lookup"><span data-stu-id="e5c4a-141">Windows Application</span></span>|<span data-ttu-id="e5c4a-142">**Oui**</span><span class="sxs-lookup"><span data-stu-id="e5c4a-142">**Yes**</span></span>|  
|<span data-ttu-id="e5c4a-143">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="e5c4a-143">Class Library</span></span>|<span data-ttu-id="e5c4a-144">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-144">No</span></span>|  
|<span data-ttu-id="e5c4a-145">Application console</span><span class="sxs-lookup"><span data-stu-id="e5c4a-145">Console Application</span></span>|<span data-ttu-id="e5c4a-146">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-146">No</span></span>|  
|<span data-ttu-id="e5c4a-147">Bibliothèque de contrôles Windows</span><span class="sxs-lookup"><span data-stu-id="e5c4a-147">Windows Control Library</span></span>|<span data-ttu-id="e5c4a-148">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-148">No</span></span>|  
|<span data-ttu-id="e5c4a-149">Bibliothèque de contrôles Web</span><span class="sxs-lookup"><span data-stu-id="e5c4a-149">Web Control Library</span></span>|<span data-ttu-id="e5c4a-150">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-150">No</span></span>|  
|<span data-ttu-id="e5c4a-151">Service Windows</span><span class="sxs-lookup"><span data-stu-id="e5c4a-151">Windows Service</span></span>|<span data-ttu-id="e5c4a-152">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-152">No</span></span>|  
|<span data-ttu-id="e5c4a-153">Site web</span><span class="sxs-lookup"><span data-stu-id="e5c4a-153">Web Site</span></span>|<span data-ttu-id="e5c4a-154">Non</span><span class="sxs-lookup"><span data-stu-id="e5c4a-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5c4a-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5c4a-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="e5c4a-156">Objects</span><span class="sxs-lookup"><span data-stu-id="e5c4a-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="e5c4a-157">Comment : ajouter des Windows Forms à un projet</span><span class="sxs-lookup"><span data-stu-id="e5c4a-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="e5c4a-158">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e5c4a-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="e5c4a-159">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e5c4a-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="e5c4a-160">Accès aux formulaires de l’application</span><span class="sxs-lookup"><span data-stu-id="e5c4a-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
