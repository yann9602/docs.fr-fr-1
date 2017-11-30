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
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Procédure pas à pas : Incorporation d’informations de Type provenant d’assemblys Microsoft Office dans Visual Studio (Visual Basic)
Si vous incorporez des informations de type dans une application qui référence des objets COM, vous pouvez éliminer le besoin d’un assembly PIA (Primary Interop Assembly). En outre, les informations de type incorporées vous permettent d’obtenir l’indépendance de version pour votre application. Autrement dit, votre programme peut être écrit de façon à utiliser des types de plusieurs versions d’une bibliothèque COM sans requérir d’assembly PIA spécifique pour chaque version. Il s’agit d’un scénario courant pour les applications qui utilisent des objets de bibliothèques Microsoft Office. L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec des versions différentes de Microsoft Office sur différents ordinateurs sans devoir redéployer le programme ou l’assembly PIA pour chaque version de Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Conditions préalables  
 Elle requiert les éléments suivants :  
  
-   un ordinateur sur lequel Visual Studio et Microsoft Excel sont installés ;  
  
-   un second ordinateur sur lequel .NET Framework 4 ou version ultérieure et une version différente d’Excel sont installés.  
  
##  <a name="BKMK_createapp"></a> Pour créer une application qui fonctionne avec plusieurs versions de Microsoft Office  
  
1.  Démarrez Visual Studio sur un ordinateur sur lequel Excel est installé.  
  
2.  Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné. Sélectionnez **Application console** dans le volet **Modèles**. Dans la zone **Nom**, entrez `CreateExcelWorkbook`, puis choisissez le bouton **OK**. Le nouveau projet est créé.  
  
4.  Ouvrez le menu contextuel du projet CreateExcelWorkbook, puis choisissez **propriétés**. Choisissez le **références** onglet. Choisissez le bouton **Ajouter** .  
  
5.  Sous l’onglet **.NET**, choisissez la version la plus récente de `Microsoft.Office.Interop.Excel`. Par exemple, **Microsoft.Office.Interop.Excel 14.0.0.0**. Sélectionnez le bouton **OK** .  
  
6.  Dans la liste de références du projet **CreateExcelWorkbook**, sélectionnez la référence pour la version de `Microsoft.Office.Interop.Excel` que vous avez ajoutée à l’étape précédente. Dans la fenêtre **Propriétés**, vérifiez que la propriété `Embed Interop Types` a la valeur `True`.  
  
    > [!NOTE]
    >  L’application créée dans cette procédure pas à pas s’exécute avec différentes versions de Microsoft Office grâce aux informations de type d’interopérabilité incorporées. Si la propriété `Embed Interop Types` a la valeur `False`, vous devez inclure un assembly PIA pour chaque version de Microsoft Office avec laquelle l’application s’exécutera.  
  
7.  Ouvrez le fichier Module1.vb. Remplacez le code du fichier par le code suivant :  
  
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
  
8.  Enregistrez le projet.  
  
9. Appuyez sur CTRL+F5 pour générer et exécuter le projet. Vérifiez qu’un classeur Excel a été créé à l’emplacement spécifié dans l’exemple de code : C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Pour publier l’application sur un ordinateur sur lequel une autre version de Microsoft Office est installée  
  
1.  Ouvrez le projet créé au cours de cette procédure dans Visual Studio.  
  
2.  Dans le menu **Générer**, choisissez **Publier CreateExcelWorkbook**. Suivez les étapes de l’Assistant Publication pour créer une version installable de l’application. Pour plus d’informations, consultez [Assistant Publication (Développement Office dans Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Installez l’application sur un ordinateur sur lequel .NET Framework 4 ou version ultérieure et une version différente d’Excel sont installés.  
  
4.  Quand l’installation est terminée, exécutez le programme installé.  
  
5.  Vérifiez qu’un classeur Excel a été créé à l’emplacement spécifié dans l’exemple de code : C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Incorporation de Types provenant d’assemblys managés dans Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
