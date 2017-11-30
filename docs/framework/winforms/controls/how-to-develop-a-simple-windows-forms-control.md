---
title: "Comment : développer un contrôle Windows Forms simple"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 941bcb3d69a80ff415cb76d69414ad25e3a8c76d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a><span data-ttu-id="2bf9d-102">Comment : développer un contrôle Windows Forms simple</span><span class="sxs-lookup"><span data-stu-id="2bf9d-102">How to: Develop a Simple Windows Forms Control</span></span>
<span data-ttu-id="2bf9d-103">Cette section vous guide à travers les étapes clés de création d’un contrôle Windows Forms personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-103">This section walks you through the key steps for authoring a custom Windows Forms control.</span></span> <span data-ttu-id="2bf9d-104">Le contrôle simple développé dans cette procédure pas à pas permet l’alignement de ses <xref:System.Windows.Forms.Control.Text%2A> propriété à modifier.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-104">The simple control developed in this walkthrough allows the alignment of its <xref:System.Windows.Forms.Control.Text%2A> property to be changed.</span></span> <span data-ttu-id="2bf9d-105">Il ne permet pas de déclencher ni de gérer des événements.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-105">It does not raise or handle events.</span></span>  
  
### <a name="to-create-a-simple-custom-control"></a><span data-ttu-id="2bf9d-106">Pour créer un contrôle personnalisé simple</span><span class="sxs-lookup"><span data-stu-id="2bf9d-106">To create a simple custom control</span></span>  
  
1.  <span data-ttu-id="2bf9d-107">Définissez une classe qui dérive de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-107">Define a class that derives from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  <span data-ttu-id="2bf9d-108">Définissez des propriétés.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-108">Define properties.</span></span> <span data-ttu-id="2bf9d-109">(Vous ne doivent pas définir les propriétés, car un contrôle hérite de nombreuses propriétés de la <xref:System.Windows.Forms.Control> classe, mais la plupart des contrôles personnalisés définissent généralement des propriétés supplémentaires.) Le fragment de code suivant définit une propriété nommée `TextAlignment` qui `FirstControl` utilise pour mettre en forme l’affichage de la <xref:System.Windows.Forms.Control.Text%2A> héritée de la propriété <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-109">(You are not required to define properties, because a control inherits many properties from the <xref:System.Windows.Forms.Control> class, but most custom controls generally do define additional properties.) The following code fragment defines a property named `TextAlignment` that `FirstControl` uses to format the display of the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="2bf9d-110">Pour plus d’informations sur la définition des propriétés, consultez [Vue d’ensemble des propriétés](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-110">For more information about defining properties, see [Properties Overview](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     <span data-ttu-id="2bf9d-111">Lorsque vous définissez une propriété qui modifie l’affichage visuel du contrôle, vous devez appeler la <xref:System.Windows.Forms.Control.Invalidate%2A> méthode pour redessiner le contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-111">When you set a property that changes the visual display of the control, you must invoke the <xref:System.Windows.Forms.Control.Invalidate%2A> method to redraw the control.</span></span> <span data-ttu-id="2bf9d-112"><xref:System.Windows.Forms.Control.Invalidate%2A>est défini dans la classe de base <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-112"><xref:System.Windows.Forms.Control.Invalidate%2A> is defined in the base class <xref:System.Windows.Forms.Control>.</span></span>  
  
3.  <span data-ttu-id="2bf9d-113">Substituez la méthode protégée <xref:System.Windows.Forms.Control.OnPaint%2A> héritée de la méthode <xref:System.Windows.Forms.Control> pour fournir la logique de rendu à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-113">Override the protected <xref:System.Windows.Forms.Control.OnPaint%2A> method inherited from <xref:System.Windows.Forms.Control> to provide rendering logic to your control.</span></span> <span data-ttu-id="2bf9d-114">Si vous ne substituez pas <xref:System.Windows.Forms.Control.OnPaint%2A>, votre contrôle ne sera pas en mesure de se dessiner.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-114">If you do not override <xref:System.Windows.Forms.Control.OnPaint%2A>, your control will not be able to draw itself.</span></span> <span data-ttu-id="2bf9d-115">Dans le fragment de code suivant, le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode affiche le <xref:System.Windows.Forms.Control.Text%2A> héritée de la propriété <xref:System.Windows.Forms.Control> avec l’alignement spécifié par le `alignmentValue` champ.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-115">In the following code fragment, the <xref:System.Windows.Forms.Control.OnPaint%2A> method displays the <xref:System.Windows.Forms.Control.Text%2A> property inherited from <xref:System.Windows.Forms.Control> with the alignment specified by the `alignmentValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  <span data-ttu-id="2bf9d-116">Fournissez des attributs à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-116">Provide attributes for your control.</span></span> <span data-ttu-id="2bf9d-117">Les attributs permettent à un concepteur visuel d’afficher correctement votre contrôle ainsi que ses propriétés et événements au moment du design.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-117">Attributes enable a visual designer to display your control and its properties and events appropriately at design time.</span></span> <span data-ttu-id="2bf9d-118">Le fragment de code suivant applique des attributs à la propriété `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-118">The following code fragment applies attributes to the `TextAlignment` property.</span></span> <span data-ttu-id="2bf9d-119">Dans un concepteur, tels que Visual Studio, le <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribut (indiqué dans le fragment de code), la propriété à afficher sous une catégorie logique.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-119">In a designer such as Visual Studio, the <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribute (shown in the code fragment) causes the property to be displayed under a logical category.</span></span> <span data-ttu-id="2bf9d-120">Le <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribut entraîne une chaîne descriptive à afficher en bas de la **propriétés** fenêtre lorsque le `TextAlignment` propriété est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-120">The <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribute causes a descriptive string to be displayed at the bottom of the **Properties** window when the `TextAlignment` property is selected.</span></span> <span data-ttu-id="2bf9d-121">Pour plus d’informations sur les attributs, consultez [Attributs en mode design pour les composants](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-121">For more information about attributes, see [Design-Time Attributes for Components](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).</span></span>  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  <span data-ttu-id="2bf9d-122">(facultatif) Fournissez des ressources pour votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-122">(optional) Provide resources for your control.</span></span> <span data-ttu-id="2bf9d-123">Vous pouvez fournir une ressource, par exemple une image bitmap, pour votre contrôle en utilisant une option de compilateur (`/res` pour C#) afin d’empaqueter des ressources avec votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-123">You can provide a resource, such as a bitmap, for your control by using a compiler option (`/res` for C#) to package resources with your control.</span></span> <span data-ttu-id="2bf9d-124">Au moment de l’exécution, la ressource peut être récupérée à l’aide des méthodes de la <xref:System.Resources.ResourceManager> classe.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-124">At run time, the resource can be retrieved using the methods of the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="2bf9d-125">Pour plus d’informations sur la création et l’utilisation de ressources, consultez [Ressources dans des applications de bureau](../../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-125">For more information about creating and using resources, see the [Resources in Desktop Apps](../../../../docs/framework/resources/index.md).</span></span>  
  
6.  <span data-ttu-id="2bf9d-126">Compilez et déployez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-126">Compile and deploy your control.</span></span> <span data-ttu-id="2bf9d-127">Pour compiler et déployer `FirstControl,`, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2bf9d-127">To compile and deploy `FirstControl,` execute the following steps:</span></span>  
  
    1.  <span data-ttu-id="2bf9d-128">Enregistrez le code de l’exemple suivant dans un fichier source (par exemple, FirstControl.cs ou FirstControl.vb).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-128">Save the code in the following sample to a source file (such as FirstControl.cs or FirstControl.vb).</span></span>  
  
    2.  <span data-ttu-id="2bf9d-129">Compilez le code source dans un assembly et enregistrez-le dans le répertoire de votre application.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-129">Compile the source code into an assembly and save it in your application's directory.</span></span> <span data-ttu-id="2bf9d-130">Pour ce faire, exécutez la commande suivante à partir du répertoire qui contient le fichier source.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-130">To accomplish this, execute the following command from the directory that contains the source file.</span></span>  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         <span data-ttu-id="2bf9d-131">L’option du compilateur `/t:library` indique au compilateur que l’assembly créé est une bibliothèque (et non un exécutable).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-131">The `/t:library` compiler option tells the compiler that the assembly you are creating is a library (and not an executable).</span></span> <span data-ttu-id="2bf9d-132">L’option `/out` spécifie le chemin d’accès et le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-132">The `/out` option specifies the path and name of the assembly.</span></span> <span data-ttu-id="2bf9d-133">L’option `/r` fournit le nom des assemblys référencés par votre code.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-133">The`/r` option provides the name of the assemblies that are referenced by your code.</span></span> <span data-ttu-id="2bf9d-134">Dans cet exemple, vous créez un assembly privé que seules vos applications peuvent utiliser.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-134">In this example, you create a private assembly that only your applications can use.</span></span> <span data-ttu-id="2bf9d-135">Par conséquent, vous devez l’enregistrer dans le répertoire de votre application.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-135">Hence, you have to save it in your application's directory.</span></span> <span data-ttu-id="2bf9d-136">Pour plus d’informations sur l’empaquetage et le déploiement d’un contrôle à des fins de distribution, consultez [Déploiement](../../../../docs/framework/deployment/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-136">For more information about packaging and deploying a control for distribution, see [Deployment](../../../../docs/framework/deployment/index.md).</span></span>  
  
 <span data-ttu-id="2bf9d-137">L’exemple suivant présente le code pour `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-137">The following sample shows the code for `FirstControl`.</span></span> <span data-ttu-id="2bf9d-138">Le contrôle est inséré dans l’espace de noms `CustomWinControls`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-138">The control is enclosed in the namespace `CustomWinControls`.</span></span> <span data-ttu-id="2bf9d-139">Un espace de noms fournit un regroupement logique des types connexes.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-139">A namespace provides a logical grouping of related types.</span></span> <span data-ttu-id="2bf9d-140">Vous pouvez créer votre contrôle dans un espace de noms nouveau ou existant.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-140">You can create your control in a new or existing namespace.</span></span> <span data-ttu-id="2bf9d-141">En C#, la déclaration `using` (en Visual Basic, `Imports`) autorise l’accès aux types à partir d’un espace de noms sans le nom qualifié complet du type.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-141">In C#, the `using` declaration (in Visual Basic, `Imports`) allows types to be accessed from a namespace without using the fully qualified name of the type.</span></span> <span data-ttu-id="2bf9d-142">Dans l’exemple suivant, la `using` déclaration permet au code d’accéder à la classe <xref:System.Windows.Forms.Control> de <xref:System.Windows.Forms?displayProperty=nameWithType> simplement <xref:System.Windows.Forms.Control> au lieu de devoir utiliser le nom qualifié complet <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-142">In the following example, the `using` declaration allows code to access the class <xref:System.Windows.Forms.Control> from <xref:System.Windows.Forms?displayProperty=nameWithType> as simply <xref:System.Windows.Forms.Control> instead of having to use the fully qualified name <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a><span data-ttu-id="2bf9d-143">Utilisation du contrôle personnalisé dans un formulaire</span><span class="sxs-lookup"><span data-stu-id="2bf9d-143">Using the Custom Control on a Form</span></span>  
 <span data-ttu-id="2bf9d-144">L’exemple suivant montre un formulaire simple qui utilise `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-144">The following example shows a simple form that uses `FirstControl`.</span></span> <span data-ttu-id="2bf9d-145">Il crée trois instances de `FirstControl`, chacune présentant une valeur différente pour la propriété `TextAlignment`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-145">It creates three instances of `FirstControl`, each with a different value for the `TextAlignment` property.</span></span>  
  
#### <a name="to-compile-and-run-this-sample"></a><span data-ttu-id="2bf9d-146">Pour compiler et exécuter cet exemple</span><span class="sxs-lookup"><span data-stu-id="2bf9d-146">To compile and run this sample</span></span>  
  
1.  <span data-ttu-id="2bf9d-147">Enregistrez le code de l’exemple suivant dans un fichier source (SimpleForm.cs ou SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-147">Save the code in the following example to a source file (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
2.  <span data-ttu-id="2bf9d-148">Compilez le code source dans un assembly exécutable en exécutant la commande suivante à partir du répertoire contenant le fichier source.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-148">Compile the source code into an executable assembly by executing the following command from the directory that contains the source file.</span></span>  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     <span data-ttu-id="2bf9d-149">CustomWinControls.dll est l’assembly qui contient la classe `FirstControl`.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-149">CustomWinControls.dll is the assembly that contains the class `FirstControl`.</span></span> <span data-ttu-id="2bf9d-150">Cet assembly doit se trouver dans le même répertoire que le fichier source pour le formulaire qui y accède (SimpleForm.cs ou SimpleForms.vb).</span><span class="sxs-lookup"><span data-stu-id="2bf9d-150">This assembly must be in the same directory as the source file for the form that accesses it (SimpleForm.cs or SimpleForms.vb).</span></span>  
  
3.  <span data-ttu-id="2bf9d-151">Exécutez SimpleForm.exe à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2bf9d-151">Execute SimpleForm.exe using the following command.</span></span>  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="2bf9d-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bf9d-152">See Also</span></span>  
 [<span data-ttu-id="2bf9d-153">Propriétés dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bf9d-153">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="2bf9d-154">Événements dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2bf9d-154">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
