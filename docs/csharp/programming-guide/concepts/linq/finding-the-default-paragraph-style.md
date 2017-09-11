---
title: "Recherche du style de paragraphe par défaut (C#)"
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
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 834654837b5c7fc747b0df1ee9dc645664a77351
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="71c87-102">Recherche du style de paragraphe par défaut (C#)</span><span class="sxs-lookup"><span data-stu-id="71c87-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="71c87-103">La première tâche du didacticiel Manipulation d’informations dans un document WordprocessingML consiste à rechercher le style par défaut des paragraphes dans le document.</span><span class="sxs-lookup"><span data-stu-id="71c87-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71c87-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="71c87-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="71c87-105">Description</span><span class="sxs-lookup"><span data-stu-id="71c87-105">Description</span></span>  
 <span data-ttu-id="71c87-106">L'exemple suivant ouvre un document WordprocessingML Office Open XML, recherche les parties document et style du package, puis exécute une requête qui recherche le nom du style par défaut.</span><span class="sxs-lookup"><span data-stu-id="71c87-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="71c87-107">Pour plus d'informations sur les packages de documents Office Open XML et leurs parties constituantes, consultez [Détails des documents WordprocessingML Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="71c87-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="71c87-108">La requête recherche un nœud nommé `w:style` qui possède un attribut nommé `w:type` avec la valeur « paragraph » et un attribut nommé `w:default` avec la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="71c87-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="71c87-109">Étant donné qu'il n'y aura qu'un seul nœud XML avec ces attributs, la requête utilise l'opérateur <xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> pour convertir une collection en singleton.</span><span class="sxs-lookup"><span data-stu-id="71c87-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="71c87-110">Elle obtient ensuite la valeur de l'attribut avec le nom `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="71c87-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="71c87-111">Cet exemple utilise des classes de l'assembly WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="71c87-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="71c87-112">Il utilise des types dans l'espace de noms <xref:System.IO.Packaging?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="71c87-112">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71c87-113">Code</span><span class="sxs-lookup"><span data-stu-id="71c87-113">Code</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="71c87-114">Commentaires</span><span class="sxs-lookup"><span data-stu-id="71c87-114">Comments</span></span>  
 <span data-ttu-id="71c87-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="71c87-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="71c87-116">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="71c87-116">Next Steps</span></span>  
 <span data-ttu-id="71c87-117">Dans l'exemple suivant, nous allons créer une requête similaire qui recherche tous les paragraphes d'un document et leurs styles :</span><span class="sxs-lookup"><span data-stu-id="71c87-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="71c87-118">Récupération des paragraphes et de leurs styles (C#)</span><span class="sxs-lookup"><span data-stu-id="71c87-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="71c87-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71c87-119">See Also</span></span>  
 [<span data-ttu-id="71c87-120">Didacticiel : manipulation de contenu dans un document WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="71c87-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)

