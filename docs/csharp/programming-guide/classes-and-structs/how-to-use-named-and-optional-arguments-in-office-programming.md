---
title: "Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c773e7a6d902b9e61e724a69c9fdf5d61606de50
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="da121-102">Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="da121-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="da121-103">Les arguments nommés et les arguments facultatifs, qui ont été introduits avec [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], rendent la programmation en C# plus pratique, plus souple et plus lisible.</span><span class="sxs-lookup"><span data-stu-id="da121-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="da121-104">De plus, ces fonctionnalités facilitent considérablement l’accès aux interfaces COM, telles que les API Microsoft Office Automation.</span><span class="sxs-lookup"><span data-stu-id="da121-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="da121-105">Dans l’exemple suivant, la méthode [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) a seize paramètres qui représentent les caractéristiques d’une table, comme le nombre de colonnes et de lignes, la mise en forme, les bordures, les polices et les couleurs.</span><span class="sxs-lookup"><span data-stu-id="da121-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="da121-106">Ces seize paramètres sont facultatifs, car la plupart du temps, il n’est pas nécessaire de spécifier des valeurs pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="da121-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="da121-107">Toutefois, en l’absence d’arguments nommés et facultatifs, une valeur ou une valeur d’espace réservé doit être fournie pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="da121-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="da121-108">Avec les arguments nommés et facultatifs, vous spécifiez des valeurs uniquement pour les paramètres qui sont nécessaires à votre projet.</span><span class="sxs-lookup"><span data-stu-id="da121-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="da121-109">Pour que vous puissiez effectuer ces procédures, Microsoft Office Word doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="da121-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="da121-110">Pour créer une application console</span><span class="sxs-lookup"><span data-stu-id="da121-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="da121-111">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da121-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="da121-112">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="da121-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="da121-113">Dans le volet **Catégories de modèles**, développez **Visual C#**, puis cliquez sur **Windows**.</span><span class="sxs-lookup"><span data-stu-id="da121-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="da121-114">Regardez en haut du volet **Modèles** pour vérifier que **.NET Framework 4**, ou version ultérieure, apparaît dans la zone **Framework cible**.</span><span class="sxs-lookup"><span data-stu-id="da121-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="da121-115">Dans le volet **Modèles**, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="da121-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="da121-116">Attribuez un nom à votre projet dans le champ **Nom**.</span><span class="sxs-lookup"><span data-stu-id="da121-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="da121-117">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da121-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="da121-118">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="da121-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="da121-119">Pour ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="da121-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="da121-120">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="da121-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="da121-121">La boîte de dialogue **Ajouter une référence** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="da121-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="da121-122">Dans la page **.NET**, sélectionnez **Microsoft.Office.Interop.Word** dans la liste **Nom du composant**.</span><span class="sxs-lookup"><span data-stu-id="da121-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="da121-123">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="da121-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="da121-124">Pour ajouter les directives using nécessaires</span><span class="sxs-lookup"><span data-stu-id="da121-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="da121-125">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **Program.cs**, puis cliquez sur **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="da121-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="da121-126">Ajoutez les directives `using` suivantes en début du fichier de code.</span><span class="sxs-lookup"><span data-stu-id="da121-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     <span data-ttu-id="da121-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span></span>  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="da121-128">Pour afficher du texte dans un document Word</span><span class="sxs-lookup"><span data-stu-id="da121-128">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="da121-129">Dans la classe `Program` du fichier Program.cs, ajoutez la méthode suivante pour créer une application Word et un document Word.</span><span class="sxs-lookup"><span data-stu-id="da121-129">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="da121-130">La méthode [Add](http://go.microsoft.com/fwlink/?LinkId=145381) comprend quatre paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="da121-130">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="da121-131">Cet exemple utilise leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="da121-131">This example uses their default values.</span></span> <span data-ttu-id="da121-132">Par conséquent, aucun argument n’est nécessaire dans l’instruction appelante.</span><span class="sxs-lookup"><span data-stu-id="da121-132">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     <span data-ttu-id="da121-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span></span>  
  
2.  <span data-ttu-id="da121-134">Ajoutez le code suivant à la fin de la méthode pour définir l’emplacement d’affichage du texte dans le document, ainsi que le texte à afficher.</span><span class="sxs-lookup"><span data-stu-id="da121-134">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     <span data-ttu-id="da121-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span></span>  
  
### <a name="to-run-the-application"></a><span data-ttu-id="da121-136">Pour exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="da121-136">To run the application</span></span>  
  
1.  <span data-ttu-id="da121-137">Ajoutez l’instruction suivante à Main.</span><span class="sxs-lookup"><span data-stu-id="da121-137">Add the following statement to Main.</span></span>  
  
     <span data-ttu-id="da121-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span></span>  
  
2.  <span data-ttu-id="da121-139">Appuyez sur CTRL+F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="da121-139">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="da121-140">Un document Word contenant le texte spécifié s’affiche.</span><span class="sxs-lookup"><span data-stu-id="da121-140">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="da121-141">Pour convertir le texte en tableau</span><span class="sxs-lookup"><span data-stu-id="da121-141">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="da121-142">Utilisez la méthode `ConvertToTable` pour inclure le texte dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="da121-142">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="da121-143">La méthode comprend seize paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="da121-143">The method has sixteen optional parameters.</span></span> <span data-ttu-id="da121-144">IntelliSense place les paramètres facultatifs entre crochets, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="da121-144">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="da121-145">![Liste des paramètres de la méthode ConvertToTable.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="da121-145">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="da121-146">Paramètres ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="da121-146">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="da121-147">Les arguments nommés et facultatifs permettent de spécifier des valeurs uniquement pour les paramètres que vous voulez modifier.</span><span class="sxs-lookup"><span data-stu-id="da121-147">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="da121-148">Ajoutez le code suivant à la fin de la méthode `DisplayInWord` pour créer un tableau simple.</span><span class="sxs-lookup"><span data-stu-id="da121-148">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="da121-149">L’argument spécifie que les virgules présentes dans le texte de la chaîne comprise dans `range` séparent les cellules du tableau.</span><span class="sxs-lookup"><span data-stu-id="da121-149">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     <span data-ttu-id="da121-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span></span>  
  
     <span data-ttu-id="da121-151">Dans les versions antérieures du langage C#, l’appel de `ConvertToTable` nécessite un argument de référence pour chaque paramètre, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="da121-151">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     <span data-ttu-id="da121-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span></span>  
  
2.  <span data-ttu-id="da121-153">Appuyez sur CTRL+F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="da121-153">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="da121-154">Pour tester d’autres paramètres</span><span class="sxs-lookup"><span data-stu-id="da121-154">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="da121-155">Pour modifier le tableau de sorte qu’il comporte une colonne et trois lignes, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis appuyez sur CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="da121-155">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     <span data-ttu-id="da121-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span></span>  
  
2.  <span data-ttu-id="da121-157">Pour spécifier un format prédéfini pour le tableau, remplacez la dernière ligne de `DisplayInWord` par l’instruction suivante, puis appuyez sur CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="da121-157">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="da121-158">Le format peut être n’importe quelle constante [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382).</span><span class="sxs-lookup"><span data-stu-id="da121-158">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     <span data-ttu-id="da121-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="da121-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="da121-160">Example</span></span>  
 <span data-ttu-id="da121-161">Le code suivant contient l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="da121-161">The following code includes the full example.</span></span>  
  
 <span data-ttu-id="da121-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="da121-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da121-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da121-163">See Also</span></span>  
 [<span data-ttu-id="da121-164">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="da121-164">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)

