---
title: Forme des Documents WordprocessingML (Visual Basic) | Documents Microsoft
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
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 2b59b6891915f441d3250cefb445166878e41ed6
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="a5441-102">Forme des Documents WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5441-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="a5441-103">Cette rubrique présente la forme XML d'un document WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a5441-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="a5441-104">Formats Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="a5441-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="a5441-105">Le format de fichier natif pour la version 2007 de Microsoft Office System est le format XML ouvert Microsoft Office (communément appelé Open XML).</span><span class="sxs-lookup"><span data-stu-id="a5441-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="a5441-106">Open XML est un format XML compatible avec la norme ECMA et actuellement soumis à un processus de normalisation ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="a5441-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="a5441-107">Le langage de balisage pour les fichiers de traitement de texte dans Open XML se nomme WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a5441-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="a5441-108">Ce didacticiel utilise des fichiers sources WordprocessingML comme entrée pour les exemples.</span><span class="sxs-lookup"><span data-stu-id="a5441-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="a5441-109">Si vous utilisez Microsoft Office 2003, vous pouvez enregistrer des documents au format Office Open XML si vous avez installé le Module de compatibilité Microsoft Office pour formats de fichiers Word, Excel et PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="a5441-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="a5441-110">Forme des documents WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a5441-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="a5441-111">La première chose à comprendre est la forme des documents WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a5441-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="a5441-112">Un document WordprocessingML contient un élément de corps (nommé `w:body`) qui contient les paragraphes du document.</span><span class="sxs-lookup"><span data-stu-id="a5441-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="a5441-113">Chaque paragraphe contient une ou plusieurs exécutions de texte (nommées `w:r`).</span><span class="sxs-lookup"><span data-stu-id="a5441-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="a5441-114">Chaque exécution de texte contient un ou plusieurs segments de texte (nommés `w:t`).</span><span class="sxs-lookup"><span data-stu-id="a5441-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="a5441-115">Voici un document WordprocessingML très simple :</span><span class="sxs-lookup"><span data-stu-id="a5441-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="a5441-116">Ce document contient deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="a5441-116">This document contains two paragraphs.</span></span> <span data-ttu-id="a5441-117">Tous deux contiennent une seule exécution de texte et chaque exécution de texte contient un seul segment de texte.</span><span class="sxs-lookup"><span data-stu-id="a5441-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="a5441-118">Le moyen le plus simple d'afficher le contenu d'un fichier WordprocessingML au format XML consiste à en créer un à l'aide de Microsoft Word, de l'enregistrer, puis d'exécuter le programme suivant qui imprime le code XML sur la console.</span><span class="sxs-lookup"><span data-stu-id="a5441-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="a5441-119">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="a5441-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="a5441-120">Il utilise des types dans le <xref:System.IO.Packaging?displayProperty=fullName>espace de noms.</xref:System.IO.Packaging?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5441-120">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="a5441-121">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="a5441-121">External Resources</span></span>  
 [<span data-ttu-id="a5441-122">Introduire les Formats de fichier Open XML Office (2007)</span><span class="sxs-lookup"><span data-stu-id="a5441-122">Introducing the Office (2007) Open XML File Formats</span></span>](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [<span data-ttu-id="a5441-123">Vue d’ensemble de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a5441-123">Overview of WordprocessingML</span></span>](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [<span data-ttu-id="a5441-124">Office 2003 : Page de téléchargement des schémas de référence XML</span><span class="sxs-lookup"><span data-stu-id="a5441-124">Office 2003: XML Reference Schemas Download page</span></span>](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="a5441-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5441-125">See Also</span></span>  
 [<span data-ttu-id="a5441-126">Didacticiel : Manipulation de contenu dans un Document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5441-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

