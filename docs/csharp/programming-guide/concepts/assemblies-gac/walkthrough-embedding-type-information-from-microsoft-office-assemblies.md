---
title: "Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office dans Visual Studio (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a9a901403f34f33639a3eb5c919c337fec594dfd
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office dans Visual Studio (C#)
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
  
4.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le dossier **Références**, puis choisissez **Ajouter une référence**.  
  
5.  Sous l’onglet **.NET**, choisissez la version la plus récente de `Microsoft.Office.Interop.Excel`. Par exemple, **Microsoft.Office.Interop.Excel 14.0.0.0**. Sélectionnez le bouton **OK** .  
  
6.  Dans la liste de références du projet **CreateExcelWorkbook**, sélectionnez la référence pour la version de `Microsoft.Office.Interop.Excel` que vous avez ajoutée à l’étape précédente. Dans la fenêtre **Propriétés**, vérifiez que la propriété `Embed Interop Types` a la valeur `True`.  
  
    > [!NOTE]
    >  L’application créée dans cette procédure pas à pas s’exécute avec différentes versions de Microsoft Office grâce aux informations de type d’interopérabilité incorporées. Si la propriété `Embed Interop Types` a la valeur `False`, vous devez inclure un assembly PIA pour chaque version de Microsoft Office avec laquelle l’application s’exécutera.  
  
7.  Ouvrez le fichier **Program.cs**. Remplacez le code du fichier par le code suivant :  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
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
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)   
 [/link (Options du compilateur C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)

