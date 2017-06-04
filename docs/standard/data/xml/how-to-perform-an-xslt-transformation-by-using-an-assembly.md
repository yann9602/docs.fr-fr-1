---
title: "Proc&#233;dure&#160;: effectuer une transformation XSLT &#224; l&#39;aide d&#39;un assembly | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: effectuer une transformation XSLT &#224; l&#39;aide d&#39;un assembly
Le compilateur XSLT \(xsltc.exe\) compile des feuilles de style XSLT et génère un assembly.  L'assembly peut être passé directement dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName>.  
  
### Pour copier les fichiers XML et XSLT sur votre ordinateur local  
  
-   Copiez le fichier XSLT sur votre ordinateur local et nommez\-le Transform.xsl.  
  
    ```  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
-   Copiez le fichier XML sur votre ordinateur local et nommez\-le `books.xml`.  
  
    ```  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### Pour compiler la feuille de style avec le script activé.  
  
1.  L'exécution de la commande suivante depuis la ligne de commande crée deux assemblys nommés `Transform.dll` et `Transform_Script1.dll` \(C'est le comportement par défaut.  Sauf spécification contraire, le nom de la classe et de l'assembly est par défaut celui de la feuille de style principale\) :  
  
    ```  
    xsltc /settings:script+ Transform.xsl  
    ```  
  
 La commande suivante donne explicitement à la classe le nom Transform :  
  
```  
xsltc /settings:script+ /class:Transform Transform.xsl  
```  
  
### Pour inclure l'assembly compilé comme référence lorsque vous compilez votre code.  
  
1.  Vous pouvez inclure un assembly dans Visual Studio en ajoutant une référence dans l'Explorateur de solutions ou à partir de la ligne de commande.  
  
2.  Pour la ligne de commande en C\#, utilisez la syntaxe suivante :  
  
    ```  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3.  Pour la ligne de commande en Visual Basic, utilisez la syntaxe suivante :  
  
    ```  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### Pour utiliser l'assembly compilé dans votre code.  
  
1.  L'exemple suivant montre comment exécuter la transformation XSLT à l'aide de la feuille de style compilée.  
  
 [!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
 [!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
 Pour établir de manière dynamique une liaison avec l'assembly compilé, remplacez  
  
```  
xslt.Load(typeof(Transform))  
```  
  
 par  
  
```  
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"))  
```  
  
 dans l'exemple ci\-dessus.  Pour plus d'informations sur la méthode Assembly.Load, voir <xref:System.Reflection.Assembly.Load%2A>.  
  
## Voir aussi  
 <xref:System.Xml.Xsl.XslCompiledTransform>   
 [XSLT Compiler \(xsltc.exe\)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)   
 [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)   
 [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)