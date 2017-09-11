---
title: "Création du Document Office Open XML Source (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23511c4f083dca41c7d1b1302d11dc8b75f974cb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="f9aad-102">Création du Document Office Open XML Source (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9aad-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="f9aad-103">Cette rubrique montre comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="f9aad-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="f9aad-104">Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="f9aad-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="f9aad-105">Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.</span><span class="sxs-lookup"><span data-stu-id="f9aad-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="f9aad-106">Pour créer le document utilisé par ce didacticiel, vous devez avoir Microsoft Office 2007 ou version ultérieure, ou vous devez disposer de Microsoft Office 2003 avec le Pack de compatibilité Microsoft Office pour Word, Excel et Formats de fichier PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="f9aad-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="f9aad-107">Création du document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="f9aad-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="f9aad-108">Pour créer le document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="f9aad-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="f9aad-109">Créez un nouveau document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="f9aad-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="f9aad-110">Collez le texte suivant dans le nouveau document :</span><span class="sxs-lookup"><span data-stu-id="f9aad-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="f9aad-111">Mettez en forme la première ligne à l'aide du style « Titre 1 ».</span><span class="sxs-lookup"><span data-stu-id="f9aad-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="f9aad-112">Sélectionnez les lignes qui contiennent le code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f9aad-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="f9aad-113">La première ligne commence par le mot clé `Imports`.</span><span class="sxs-lookup"><span data-stu-id="f9aad-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="f9aad-114">La dernière ligne est « End Class ».</span><span class="sxs-lookup"><span data-stu-id="f9aad-114">The last line is "End Class".</span></span> <span data-ttu-id="f9aad-115">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="f9aad-115">Format the lines with the courier font.</span></span> <span data-ttu-id="f9aad-116">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="f9aad-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="f9aad-117">Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="f9aad-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="f9aad-118">Enregistrez le document et nommez-le SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="f9aad-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9aad-119">Si vous utilisez Microsoft Word 2003, sélectionnez **Document Word 2007** dans les **enregistrer en tant que Type** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="f9aad-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9aad-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9aad-120">See Also</span></span>  
 [<span data-ttu-id="f9aad-121">Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9aad-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
