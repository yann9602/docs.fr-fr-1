---
title: "Création du document Office Open XML source (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 378a83db02c6e07a070fb3770b042ed657860560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="307ec-102">Création du document Office Open XML source (C#)</span><span class="sxs-lookup"><span data-stu-id="307ec-102">Creating the Source Office Open XML Document (C#)</span></span>
<span data-ttu-id="307ec-103">Cette rubrique montre comment créer le document WordprocessingML Office Open XML utilisé par les autres exemples de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="307ec-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="307ec-104">Si vous suivez ces instructions, votre sortie correspondra à la sortie fournie dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="307ec-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="307ec-105">Toutefois, les exemples présentés dans ce didacticiel fonctionnent avec n'importe quel document WordprocessingML valide.</span><span class="sxs-lookup"><span data-stu-id="307ec-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="307ec-106">Pour créer le document utilisé par ce didacticiel, Microsoft Office 2007 ou une version ultérieure, ou bien Microsoft Office 2003 avec le Module de compatibilité Microsoft Office pour les formats de fichiers Word, Excel et PowerPoint 2007 doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="307ec-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="307ec-107">Création du document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="307ec-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="307ec-108">Pour créer le document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="307ec-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="307ec-109">Créez un nouveau document Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="307ec-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="307ec-110">Collez le texte suivant dans le nouveau document :</span><span class="sxs-lookup"><span data-stu-id="307ec-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="307ec-111">Mettez en forme la première ligne à l'aide du style « Titre 1 ».</span><span class="sxs-lookup"><span data-stu-id="307ec-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="307ec-112">Sélectionnez les lignes qui contiennent le code C#.</span><span class="sxs-lookup"><span data-stu-id="307ec-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="307ec-113">La première ligne commence par le mot clé `using`.</span><span class="sxs-lookup"><span data-stu-id="307ec-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="307ec-114">La dernière ligne est la dernière accolade fermante.</span><span class="sxs-lookup"><span data-stu-id="307ec-114">The last line is the last closing brace.</span></span> <span data-ttu-id="307ec-115">Mettez en forme les lignes avec la police Courrier.</span><span class="sxs-lookup"><span data-stu-id="307ec-115">Format the lines with the courier font.</span></span> <span data-ttu-id="307ec-116">Mettez-les en forme avec un nouveau style et nommez le nouveau style « Code ».</span><span class="sxs-lookup"><span data-stu-id="307ec-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="307ec-117">Pour finir, sélectionnez la ligne entière qui contient la sortie et mettez-la en forme avec le style `Code`.</span><span class="sxs-lookup"><span data-stu-id="307ec-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="307ec-118">Enregistrez le document et nommez-le SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="307ec-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="307ec-119">Si vous utilisez Microsoft Word 2003, sélectionnez **Document Word 2007** dans la liste déroulante **Type de fichier**.</span><span class="sxs-lookup"><span data-stu-id="307ec-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307ec-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="307ec-120">See Also</span></span>  
 [<span data-ttu-id="307ec-121">Didacticiel : manipulation de contenu dans un document WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="307ec-121">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
