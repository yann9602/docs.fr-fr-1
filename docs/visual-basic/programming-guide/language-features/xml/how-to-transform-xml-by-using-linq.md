---
title: "Comment : transformer du code XML à l’aide de LINQ (Visual Basic) | Documents Microsoft"
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
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 12b5bfd059d219a5cb0087e763688d01a75b0533
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="a3170-102">Comment : transformer du code XML à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3170-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="a3170-103">[Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) permet de lire les données XML à partir d’une source et la transformer en un nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="a3170-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="a3170-104">Vous pouvez tirer parti de requêtes LINQ pour récupérer le contenu à transformer, ou modifier le contenu d’un document existant dans un nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="a3170-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="a3170-105">L’exemple de cette rubrique transforme le contenu d’un document source XML en HTML pour les afficher dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="a3170-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="a3170-106">Pour transformer un document XML</span><span class="sxs-lookup"><span data-stu-id="a3170-106">To transform an XML document</span></span>  
  
1.  <span data-ttu-id="a3170-107">Dans Visual Studio, créez un nouveau projet Visual Basic dans les **Application Console** modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="a3170-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2.  <span data-ttu-id="a3170-108">Double-cliquez sur le fichier Module1.vb créé dans le projet pour modifier le code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3170-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="a3170-109">Ajoutez le code suivant à la `Sub Main` de la `Module1` module.</span><span class="sxs-lookup"><span data-stu-id="a3170-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="a3170-110">Ce code crée le document XML source comme un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="a3170-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     <span data-ttu-id="a3170-111">[Comment : charger du code XML à partir d’un fichier, une chaîne ou un flux](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="a3170-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3.  <span data-ttu-id="a3170-112">Après le code pour créer le document XML source, ajoutez le code suivant pour extraire tous les \<livre > éléments de l’objet et les transformer en un document HTML.</span><span class="sxs-lookup"><span data-stu-id="a3170-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="a3170-113">La liste des \<livre > éléments est créé à l’aide d’une requête LINQ qui retourne une collection de <xref:System.Xml.Linq.XElement>objets contenant le HTML transformé.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="a3170-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="a3170-114">Vous pouvez utiliser des expressions incorporées pour mettre les valeurs du document source dans le nouveau format XML.</span><span class="sxs-lookup"><span data-stu-id="a3170-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="a3170-115">Le document HTML résultant est écrit dans un fichier à l’aide de la <xref:System.Xml.Linq.XElement.Save%2A>méthode.</xref:System.Xml.Linq.XElement.Save%2A></span><span class="sxs-lookup"><span data-stu-id="a3170-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  <span data-ttu-id="a3170-116">Après avoir `Sub Main` de `Module1`, ajoutez une nouvelle méthode (`Sub`) pour transformer un \<Description > nœud en format HTML spécifié.</span><span class="sxs-lookup"><span data-stu-id="a3170-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="a3170-117">Cette méthode est appelée par le code à l’étape précédente et est utilisée pour conserver le format de la \<Description > éléments.</span><span class="sxs-lookup"><span data-stu-id="a3170-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="a3170-118">Cette méthode remplace les sous-éléments de le \<Description > élément HTML.</span><span class="sxs-lookup"><span data-stu-id="a3170-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="a3170-119">Le `ReplaceWith` méthode permet de préserver l’emplacement des sous-éléments.</span><span class="sxs-lookup"><span data-stu-id="a3170-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="a3170-120">Le contenu transformé de le \<Description > est inclus dans un paragraphe HTML (\<p >) élément.</span><span class="sxs-lookup"><span data-stu-id="a3170-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="a3170-121">Le <xref:System.Xml.Linq.XContainer.Nodes%2A>propriété est utilisée pour récupérer le contenu transformé de le \<Description > élément.</xref:System.Xml.Linq.XContainer.Nodes%2A></span><span class="sxs-lookup"><span data-stu-id="a3170-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="a3170-122">Cela garantit que les sous-éléments sont inclus dans le contenu transformé.</span><span class="sxs-lookup"><span data-stu-id="a3170-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="a3170-123">Ajoutez le code suivant après `Sub Main` de `Module1`.</span><span class="sxs-lookup"><span data-stu-id="a3170-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  <span data-ttu-id="a3170-124">Enregistrez les modifications apportées.</span><span class="sxs-lookup"><span data-stu-id="a3170-124">Save your changes.</span></span>  
  
6.  <span data-ttu-id="a3170-125">Appuyez sur F5 pour exécuter le code.</span><span class="sxs-lookup"><span data-stu-id="a3170-125">Press F5 to run the code.</span></span> <span data-ttu-id="a3170-126">Enregistré le document résultant ressemblera à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="a3170-126">The resulting saved document will resemble the following:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3170-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3170-127">See Also</span></span>  
 <span data-ttu-id="a3170-128">[Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3170-128">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="a3170-129"> [Manipulation de XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a3170-129"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="a3170-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3170-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="a3170-131"> [Comment : charger du code XML à partir d’un fichier, une chaîne ou un flux de données](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="a3170-131"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="a3170-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="a3170-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="a3170-133"> [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="a3170-133"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>

