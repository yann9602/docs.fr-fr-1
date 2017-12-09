---
title: "Procédure pas à pas : Incorporation d’informations de Type provenant d’assemblys Microsoft Office dans Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26e6fee5147e8477c64f7eaf0dc2aeb928c13e15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="00845-102">Procédure pas à pas : Incorporation d’informations de Type provenant d’assemblys Microsoft Office dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00845-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="00845-103">Si vous incorporez des informations de type dans une application qui référence des objets COM, vous pouvez éliminer le besoin d’un assembly PIA (Primary Interop Assembly).</span><span class="sxs-lookup"><span data-stu-id="00845-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="00845-104">En outre, les informations de type incorporées vous permettent d’obtenir l’indépendance de version pour votre application.</span><span class="sxs-lookup"><span data-stu-id="00845-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="00845-105">Autrement dit, votre programme peut être écrit de façon à utiliser des types de plusieurs versions d’une bibliothèque COM sans requérir d’assembly PIA spécifique pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="00845-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="00845-106">Il s’agit d’un scénario courant pour les applications qui utilisent des objets de bibliothèques Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="00845-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="00845-107">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec des versions différentes de Microsoft Office sur différents ordinateurs sans devoir redéployer le programme ou l’assembly PIA pour chaque version de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="00845-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="00845-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="00845-108">Prerequisites</span></span>  
 <span data-ttu-id="00845-109">Elle requiert les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="00845-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="00845-110">un ordinateur sur lequel Visual Studio et Microsoft Excel sont installés ;</span><span class="sxs-lookup"><span data-stu-id="00845-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="00845-111">un second ordinateur sur lequel .NET Framework 4 ou version ultérieure et une version différente d’Excel sont installés.</span><span class="sxs-lookup"><span data-stu-id="00845-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="00845-112">Pour créer une application qui fonctionne avec plusieurs versions de Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="00845-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="00845-113">Démarrez Visual Studio sur un ordinateur sur lequel Excel est installé.</span><span class="sxs-lookup"><span data-stu-id="00845-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="00845-114">Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="00845-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="00845-115">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="00845-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="00845-116">Sélectionnez **Application console** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="00845-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="00845-117">Dans la zone **Nom**, entrez `CreateExcelWorkbook`, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="00845-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="00845-118">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="00845-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="00845-119">Ouvrez le menu contextuel du projet CreateExcelWorkbook, puis choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="00845-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="00845-120">Choisissez le **références** onglet. Choisissez le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="00845-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="00845-121">Sous l’onglet **.NET**, choisissez la version la plus récente de `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="00845-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="00845-122">Par exemple, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="00845-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="00845-123">Sélectionnez le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="00845-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="00845-124">Dans la liste de références du projet **CreateExcelWorkbook**, sélectionnez la référence pour la version de `Microsoft.Office.Interop.Excel` que vous avez ajoutée à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="00845-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="00845-125">Dans la fenêtre **Propriétés**, vérifiez que la propriété `Embed Interop Types` a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="00845-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="00845-126">L’application créée dans cette procédure pas à pas s’exécute avec différentes versions de Microsoft Office grâce aux informations de type d’interopérabilité incorporées.</span><span class="sxs-lookup"><span data-stu-id="00845-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="00845-127">Si la propriété `Embed Interop Types` a la valeur `False`, vous devez inclure un assembly PIA pour chaque version de Microsoft Office avec laquelle l’application s’exécutera.</span><span class="sxs-lookup"><span data-stu-id="00845-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="00845-128">Ouvrez le fichier Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="00845-128">Open the Module1.vb file.</span></span> <span data-ttu-id="00845-129">Remplacez le code du fichier par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="00845-129">Replace the code in the file with the following code:</span></span>  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  <span data-ttu-id="00845-130">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="00845-130">Save the project.</span></span>  
  
9. <span data-ttu-id="00845-131">Appuyez sur CTRL+F5 pour générer et exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="00845-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="00845-132">Vérifiez qu’un classeur Excel a été créé à l’emplacement spécifié dans l’exemple de code : C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="00845-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="00845-133">Pour publier l’application sur un ordinateur sur lequel une autre version de Microsoft Office est installée</span><span class="sxs-lookup"><span data-stu-id="00845-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="00845-134">Ouvrez le projet créé au cours de cette procédure dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00845-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="00845-135">Dans le menu **Générer**, choisissez **Publier CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="00845-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="00845-136">Suivez les étapes de l’Assistant Publication pour créer une version installable de l’application.</span><span class="sxs-lookup"><span data-stu-id="00845-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="00845-137">Pour plus d’informations, consultez [Assistant Publication (Développement Office dans Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="00845-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="00845-138">Installez l’application sur un ordinateur sur lequel .NET Framework 4 ou version ultérieure et une version différente d’Excel sont installés.</span><span class="sxs-lookup"><span data-stu-id="00845-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="00845-139">Quand l’installation est terminée, exécutez le programme installé.</span><span class="sxs-lookup"><span data-stu-id="00845-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="00845-140">Vérifiez qu’un classeur Excel a été créé à l’emplacement spécifié dans l’exemple de code : C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="00845-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00845-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00845-141">See Also</span></span>  
 [<span data-ttu-id="00845-142">Procédure pas à pas : Incorporation de Types provenant d’assemblys managés dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00845-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="00845-143">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00845-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
