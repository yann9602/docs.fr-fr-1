---
title: "How to: Transform XML by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML [Visual Basic], transforming"
  - "LINQ to XML [Visual Basic], transforming XML"
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Transform XML by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) facilitent la lecture du texte XML à partir d'une source donnée et sa transformation dans un nouveau format XML.  Vous pouvez tirer parti de requêtes LINQ pour récupérer le contenu à transformer, ou modifier le contenu dans un document existant pour lui donner un nouveau format XML.  
  
 L'exemple de cette rubrique transforme le contenu d'un document source XML en HTML à afficher dans un navigateur.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### Pour transformer un document XML  
  
1.  Dans Visual Studio, créez un projet Visual Basic dans le modèle de projet **Application console**.  
  
2.  Double\-cliquez sur le fichier Module1.vb créé dans le projet, pour modifier le code Visual Basic.  Ajoutez le code suivant à la section `Sub Main` du module `Module1`.  Ce code crée le document XML source sous forme d'objet <xref:System.Xml.Linq.XDocument>.  
  
    ```vb#  
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
  
     [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  Après le code permettant de créer le document XML source, ajoutez le code suivant, pour récupérer tous les éléments \<Book\> de l'objet et les transformer en un document HTML.  La liste d'éléments \<Book\> se crée en utilisant une requête LINQ qui renvoie une collection d'objets <xref:System.Xml.Linq.XElement> contenant le HTML transformé.  Vous pouvez utiliser des expressions incorporées pour mettre les valeurs du document source dans le nouveau format XML.  
  
     Le document HTML résultant est écrit dans un fichier en utilisant la méthode <xref:System.Xml.Linq.XElement.Save%2A>.  
  
    ```vb#  
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
  
4.  Après la section `Sub Main` du `Module1`, ajoutez une nouvelle méthode \(`Sub`\) pour transformer un nœud \<Description\> en format HTML spécifié.  Cette méthode est appelée par le code de l'étape précédente et s'utilise pour préserver le format des éléments \<Description\>.  
  
     Cette méthode remplace les sous\-éléments de l'élément \<Description\> par le format HTML.  La méthode `ReplaceWith` s'utilise pour préserver l'emplacement des sous\-éléments.  Le contenu transformé de l'élément \<Description\> est inclus dans un élément \(\<p\>\) du paragraphe HTML.  La propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> permet de récupérer le contenu transformé de l'élément \<Description\>.  Cela garantit l'intégration des sous\-éléments au contenu transformé.  
  
     Ajoutez le code suivant, après la section `Sub Main` du `Module1`.  
  
    ```vb#  
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
  
5.  Enregistrez les modifications apportées.  
  
6.  Appuyez sur F5 pour exécuter le code.  Le document enregistré qui résulte de cette opération ressemble à ce qui suit :  
  
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
  
## Voir aussi  
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)