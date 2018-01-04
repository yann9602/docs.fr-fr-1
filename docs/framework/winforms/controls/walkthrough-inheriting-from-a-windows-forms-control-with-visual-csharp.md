---
title: "Procédure pas à pas : héritage d'un contrôle Windows Forms à l'aide de Visual C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c28e41ad7c9e07dae150035e205e79b3d8cac84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a><span data-ttu-id="1aa3c-102">Procédure pas à pas : héritage d'un contrôle Windows Forms à l'aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="1aa3c-102">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span> #
<span data-ttu-id="1aa3c-103">Avec [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], vous pouvez créer des contrôles personnalisés puissants grâce à *l’héritage*.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-103">With [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="1aa3c-104">L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="1aa3c-105">Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="1aa3c-106">Ce bouton hérite des fonctionnalités de Windows Forms standard <xref:System.Windows.Forms.Button> contrôler et expose une propriété personnalisée nommée `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aa3c-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1aa3c-108">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="1aa3c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1aa3c-109">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="1aa3c-110">Création du projet</span><span class="sxs-lookup"><span data-stu-id="1aa3c-110">Creating the Project</span></span>  
 <span data-ttu-id="1aa3c-111">Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-111">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="1aa3c-112">Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton</span><span class="sxs-lookup"><span data-stu-id="1aa3c-112">To create the ValueButtonLib control library and the ValueButton control</span></span>  
  
1.  <span data-ttu-id="1aa3c-113">Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-113">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="1aa3c-114">Dans la liste des projets [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], sélectionnez le modèle de projet **Bibliothèque de contrôles Windows Forms**, puis saisissez `ValueButtonLib` dans le champ **Nom**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-114">Select the **Windows Forms Control Library** project template from the list of [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] Projects, and type `ValueButtonLib` in the **Name** box.</span></span>  
  
     <span data-ttu-id="1aa3c-115">Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-115">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="1aa3c-116">L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-116">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="1aa3c-117">Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-117">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="1aa3c-118">Pour plus d’informations, consultez l’article [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-118">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>  
  
3.  <span data-ttu-id="1aa3c-119">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.cs**, puis sélectionnez **Renommer** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-119">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="1aa3c-120">Remplacez le nom de fichier par `ValueButton.cs`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-120">Change the file name to `ValueButton.cs`.</span></span> <span data-ttu-id="1aa3c-121">Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « `UserControl1` ».</span><span class="sxs-lookup"><span data-stu-id="1aa3c-121">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>  
  
4.  <span data-ttu-id="1aa3c-122">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis sélectionnez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-122">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="1aa3c-123">Recherchez le `class` ligne de l’instruction, `public partial class ValueButton`et modifier le type à partir duquel ce contrôle hérite <xref:System.Windows.Forms.UserControl> à <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-123">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="1aa3c-124">Cela permet à votre contrôle d’hériter de toutes les fonctionnalités de la <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-124">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>  
  
6.  <span data-ttu-id="1aa3c-125">Dans **l’Explorateur de solutions**, ouvrez le nœud **ValueButton.cs** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.cs**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-125">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="1aa3c-126">Ouvrez ce fichier dans **l’éditeur de code**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-126">Open this file in the **Code Editor**.</span></span>  
  
7.  <span data-ttu-id="1aa3c-127">Recherchez le `InitializeComponent` (méthode) et supprimer la ligne qui assigne la <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-127">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="1aa3c-128">Cette propriété n’existe pas dans le <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-128">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>  
  
8.  <span data-ttu-id="1aa3c-129">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-129">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1aa3c-130">Plus aucun concepteur visuel n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-130">A visual designer is no longer available.</span></span> <span data-ttu-id="1aa3c-131">Étant donné que le <xref:System.Windows.Forms.Button> contrôle effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-131">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="1aa3c-132">Représentation visuelle sera exactement le même que celui de la classe, elle hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si la modification dans le code.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-132">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="1aa3c-133">Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-133">You can still add components, which have no UI elements, to the design surface.</span></span>  
  
## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="1aa3c-134">Ajout d’une propriété à votre contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="1aa3c-134">Adding a Property to Your Inherited Control</span></span>  
 <span data-ttu-id="1aa3c-135">Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant le même aspect que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-135">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="1aa3c-136">Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-136">In this section, you will add a property called `ButtonValue` to your control.</span></span>  
  
#### <a name="to-add-the-value-property"></a><span data-ttu-id="1aa3c-137">Pour ajouter la propriété Valeur</span><span class="sxs-lookup"><span data-stu-id="1aa3c-137">To add the Value property</span></span>  
  
1.  <span data-ttu-id="1aa3c-138">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-138">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="1aa3c-139">Recherchez l’instruction `class`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-139">Locate the `class` statement.</span></span> <span data-ttu-id="1aa3c-140">Saisissez le code suivant immédiatement après `{` :</span><span class="sxs-lookup"><span data-stu-id="1aa3c-140">Immediately after the `{`, type the following code:</span></span>  
  
    ```csharp  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     <span data-ttu-id="1aa3c-141">Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-141">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="1aa3c-142">L’instruction `get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `set` définit la valeur de la variable privée à l’aide du mot clé `value`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-142">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>  
  
3.  <span data-ttu-id="1aa3c-143">Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-143">From the **File** menu, choose **Save All** to save the project.</span></span>  
  
## <a name="testing-your-control"></a><span data-ttu-id="1aa3c-144">Test de votre contrôle</span><span class="sxs-lookup"><span data-stu-id="1aa3c-144">Testing Your Control</span></span>  
 <span data-ttu-id="1aa3c-145">Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-145">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="1aa3c-146">Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-146">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="1aa3c-147">Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant).</span><span class="sxs-lookup"><span data-stu-id="1aa3c-147">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="1aa3c-148">Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-148">In this section, you will build your control and test it in a Windows Form.</span></span>  
  
#### <a name="to-build-your-control"></a><span data-ttu-id="1aa3c-149">Pour générer votre contrôle</span><span class="sxs-lookup"><span data-stu-id="1aa3c-149">To build your control</span></span>  
  
1.  <span data-ttu-id="1aa3c-150">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-150">On the **Build** menu, click **Build Solution**.</span></span>  
  
     <span data-ttu-id="1aa3c-151">L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-151">The build should be successful with no compiler errors or warnings.</span></span>  
  
#### <a name="to-create-a-test-project"></a><span data-ttu-id="1aa3c-152">Pour créer un projet de test</span><span class="sxs-lookup"><span data-stu-id="1aa3c-152">To create a test project</span></span>  
  
1.  <span data-ttu-id="1aa3c-153">Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-153">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="1aa3c-154">Sélectionnez le nœud **Windows** sous le nœud **Visual C#**, puis cliquez sur **Application Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-154">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="1aa3c-155">Dans la zone **Nom**, tapez `Test`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-155">In the **Name** box, type `Test`.</span></span>  
  
4.  <span data-ttu-id="1aa3c-156">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-156">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>  
  
5.  <span data-ttu-id="1aa3c-157">Cliquez sur l’onglet intitulé **Projets**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-157">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="1aa3c-158">Votre projet `ValueButtonLib` s’affiche sous **Nom du projet**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-158">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="1aa3c-159">Double-cliquez sur le projet pour ajouter la référence au projet de test.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-159">Double-click the project to add the reference to the test project.</span></span>  
  
6.  <span data-ttu-id="1aa3c-160">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-160">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>  
  
#### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="1aa3c-161">Pour ajouter votre contrôle au formulaire</span><span class="sxs-lookup"><span data-stu-id="1aa3c-161">To add your control to the form</span></span>  
  
1.  <span data-ttu-id="1aa3c-162">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs** et sélectionnez **Concepteur de vues** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-162">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="1aa3c-163">Dans la **boîte à outils**, cliquez sur **Composants ValueButtonLib**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-163">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="1aa3c-164">Double-cliquez sur **ValueButton**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-164">Double-click **ValueButton**.</span></span>  
  
     <span data-ttu-id="1aa3c-165">Un élément **ValueButton** apparaît sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-165">A **ValueButton** appears on the form.</span></span>  
  
3.  <span data-ttu-id="1aa3c-166">Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-166">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="1aa3c-167">Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-167">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="1aa3c-168">Notez qu’elles sont identiques aux propriétés exposées par un bouton standard, à la différence près qu’il y a une propriété en plus, `ButtonValue`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-168">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>  
  
5.  <span data-ttu-id="1aa3c-169">Affectez à la propriété `ButtonValue` la valeur `5`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-169">Set the `ButtonValue` property to `5`.</span></span>  
  
6.  <span data-ttu-id="1aa3c-170">Dans le **tous les Windows Forms** onglet de la **boîte à outils**, double-cliquez sur **étiquette** pour ajouter un <xref:System.Windows.Forms.Label> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-170">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>  
  
7.  <span data-ttu-id="1aa3c-171">Déplacez l’étiquette au centre du formulaire.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-171">Relocate the label to the center of the form.</span></span>  
  
8.  <span data-ttu-id="1aa3c-172">Double-cliquez sur `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-172">Double-click `valueButton1`.</span></span>  
  
     <span data-ttu-id="1aa3c-173">**L’éditeur de code** s’ouvre à l’événement `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-173">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>  
  
9. <span data-ttu-id="1aa3c-174">Saisissez la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-174">Insert the following line of code.</span></span>  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. <span data-ttu-id="1aa3c-175">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-175">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>  
  
11. <span data-ttu-id="1aa3c-176">Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-176">From the **Debug** menu, select **Start Debugging**.</span></span>  
  
     <span data-ttu-id="1aa3c-177">`Form1` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-177">`Form1` appears.</span></span>  
  
12. <span data-ttu-id="1aa3c-178">Cliquez sur `valueButton1`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-178">Click `valueButton1`.</span></span>  
  
     <span data-ttu-id="1aa3c-179">Le chiffre « 5 » s’affiche dans `label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `label1` via la méthode `valueButton1_Click`.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-179">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="1aa3c-180">Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1aa3c-180">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa3c-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1aa3c-181">See Also</span></span>  
 [<span data-ttu-id="1aa3c-182">Programmation à l’aide de composants</span><span class="sxs-lookup"><span data-stu-id="1aa3c-182">Programming with Components</span></span>](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [<span data-ttu-id="1aa3c-183">Procédures pas à pas de la création de composants</span><span class="sxs-lookup"><span data-stu-id="1aa3c-183">Component Authoring Walkthroughs</span></span>](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [<span data-ttu-id="1aa3c-184">Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="1aa3c-184">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [<span data-ttu-id="1aa3c-185">Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="1aa3c-185">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
