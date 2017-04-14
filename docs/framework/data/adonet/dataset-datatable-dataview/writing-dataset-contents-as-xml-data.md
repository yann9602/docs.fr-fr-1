---
title: "&#201;criture du contenu d&#39;un DataSet comme donn&#233;es XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# &#201;criture du contenu d&#39;un DataSet comme donn&#233;es XML
Dans ADO.NET, vous pouvez écrire une représentation XML d’un <xref:System.Data.DataSet>, avec ou sans son schéma. Si les informations de schéma sont incluses inline avec le XML, elles sont écrites à l'aide du langage XSD (XML Schema Definition). Le schéma contient les définitions des tables de la <xref:System.Data.DataSet> , ainsi que les définitions des relations et des contraintes.  
  
 Lorsqu’un <xref:System.Data.DataSet> est écrit en tant que données XML, les lignes de la <xref:System.Data.DataSet> sont écrites dans leur version actuelle. Toutefois, le <xref:System.Data.DataSet> peuvent également être écrites en tant que DiffGram, afin que l’actuel et les valeurs d’origine des lignes à inclus.  
  
 La représentation XML de la <xref:System.Data.DataSet> peuvent être écrites dans un fichier, un flux, un **XmlWriter**, ou une chaîne. Ces différentes possibilités offrent une grande souplesse pour le transport de la représentation XML de la <xref:System.Data.DataSet>. Pour obtenir la représentation XML de la <xref:System.Data.DataSet> sous forme de chaîne, utilisez la **GetXml** méthode comme illustré dans l’exemple suivant.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** retourne la représentation XML de la <xref:System.Data.DataSet> sans informations de schéma. Pour écrire les informations de schéma à partir de la <xref:System.Data.DataSet> (en tant que schéma XML) dans une chaîne, utilisez **GetXmlSchema**.  
  
 Pour écrire un <xref:System.Data.DataSet> dans un fichier, flux, ou **XmlWriter**, utilisez la **WriteXml** (méthode). Le premier paramètre que vous passez à **WriteXml** est la destination de la sortie XML. Par exemple, passez une chaîne contenant un nom de fichier, un **System.IO.TextWriter** objet et ainsi de suite. Vous pouvez passer un deuxième paramètre facultatif d’un **XmlWriteMode** pour spécifier comment la sortie XML doit être écrite.  
  
 Le tableau suivant présente les options de **XmlWriteMode**.  
  
|Option XmlWriteMode|Description|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Écrit le contenu actuel de la <xref:System.Data.DataSet> en tant que données XML, sans schéma XML. Il s'agit de la valeur par défaut.|  
|**WriteSchema**|Écrit le contenu actuel de la <xref:System.Data.DataSet> en tant que données XML avec la structure relationnelle comme schéma XML inline.|  
|**DiffGram**|Écrit l’ensemble de <xref:System.Data.DataSet> en tant que DiffGram, y compris les valeurs d’origine et actuelles. Pour plus d’informations, consultez [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Lorsque vous écrirez une représentation XML d’un <xref:System.Data.DataSet> contenant **DataRelation** des objets, vous souhaiterez certainement que le XML obtenu les lignes enfants de chaque relation imbriquée dans leur élément parent. Pour ce faire, affectez le **Nested** propriété de la **DataRelation** à **true** lorsque vous ajoutez le **DataRelation** à la <xref:System.Data.DataSet>. Pour plus d’informations, consultez [d’imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Voici deux exemples illustrant l’écriture de la représentation XML d’un <xref:System.Data.DataSet> dans un fichier. Le premier exemple passe le nom de fichier pour le code XML résultant sous forme de chaîne pour **WriteXml**. Le second exemple passe un **System.IO.StreamWriter** objet.  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>Mappage de colonnes à des éléments, des attributs et du texte XML  
 Vous pouvez spécifier la façon dont une colonne d’une table est représentée en XML à l’aide de la **ColumnMapping** propriétés de la **DataColumn** objet. Le tableau suivant présente les différentes **MappingType** les valeurs pour le **ColumnMapping** propriété d’une colonne de table et le XML obtenu.  
  
|Valeur MappingType|Description|  
|-----------------------|-----------------|  
|**Élément**|Il s'agit de la valeur par défaut. La colonne est écrite sous la forme d'un élément XML, où ColumnName représente le nom de l'élément et le contenu de la colonne est écrit en tant que texte de l'élément. Exemple :<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**Attribut**|La colonne est écrite sous la forme d'un attribut XML de l'élément XML de la ligne actuelle, où ColumnName représente le nom de l'attribut et le contenu de la colonne est écrit en tant que valeur de l'attribut. Exemple :<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|Le contenu de la colonne est écrit sous forme de texte dans l'élément XML de la ligne actuelle. Exemple :<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> Notez que **SimpleContent** ne peut pas être définie pour une colonne d’une table qui a **élément** colonnes ou des relations imbriquées.|  
|**Masqué**|La colonne n'est pas écrite dans la sortie XML.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [Imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [Écriture des informations de schéma d’un DataSet comme XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)   
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)