---
title: "Écriture du contenu d'un DataSet comme données XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d43fd8ec006f92131056d389ed2153263f7b7f1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-contents-as-xml-data"></a>Écriture du contenu d'un DataSet comme données XML
Dans ADO.NET, vous pouvez écrire une représentation XML d'un objet<xref:System.Data.DataSet>, avec ou sans son schéma. Si les informations de schéma sont incluses inline avec le XML, elles sont écrites à l'aide du langage XSD (XML Schema Definition). Le schéma contient les définitions des tables de l'objet <xref:System.Data.DataSet>, ainsi que les définitions des relations et des contraintes.  
  
 Lorsqu'un objet <xref:System.Data.DataSet> est écrit sous forme de données XML, les lignes de l'objet <xref:System.Data.DataSet> sont écrites dans leur version actuelle. Toutefois, l'objet <xref:System.Data.DataSet> peut aussi être écrit sous la forme d'un DiffGram pour que les valeurs actuelles comme les valeurs d'origine des lignes soient incluses.  
  
 La représentation XML de la <xref:System.Data.DataSet> peuvent être écrites dans un fichier, un flux, un **XmlWriter**, ou une chaîne. Ces différentes possibilités offrent une grande souplesse pour le transport de la représentation XML de l'objet <xref:System.Data.DataSet>. Pour obtenir la représentation XML de la <xref:System.Data.DataSet> sous forme de chaîne, utilisez la **GetXml** méthode comme indiqué dans l’exemple suivant.  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml** retourne la représentation XML de la <xref:System.Data.DataSet> sans informations de schéma. Pour écrire les informations de schéma à partir de la <xref:System.Data.DataSet> (en tant que schéma XML) en une chaîne, utilisez **GetXmlSchema**.  
  
 Pour écrire un <xref:System.Data.DataSet> vers un fichier, flux, ou **XmlWriter**, utilisez le **WriteXml** (méthode). Le premier paramètre que vous passez à **WriteXml** constitue la destination de la sortie XML. Par exemple, passez une chaîne contenant un nom de fichier, un **System.IO.TextWriter** objet et ainsi de suite. Vous pouvez passer un deuxième paramètre facultatif d’un **XmlWriteMode** pour spécifier comment la sortie XML à écrire.  
  
 Le tableau suivant montre les options pour **XmlWriteMode**.  
  
|Option XmlWriteMode|Description|  
|-------------------------|-----------------|  
|**IgnoreSchema**|Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> sous forme de données XML, sans schéma XML. Il s'agit de la valeur par défaut.|  
|**WriteSchema**|Écrit le contenu actuel de l'objet <xref:System.Data.DataSet> en tant que données XML, avec la structure relationnelle comme schéma XML inline.|  
|**DiffGram**|Écrit l'ensemble de l'objet <xref:System.Data.DataSet> en tant que DiffGram, y compris les valeurs d'origine et actuelle. Pour plus d’informations, consultez [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).|  
  
 Lors de l’écriture d’une représentation XML d’un <xref:System.Data.DataSet> contenant **DataRelation** des objets, vous devez probablement le document XML obtenu pour les lignes enfants de chaque relation imbriquée dans leur élément parent. Pour ce faire, affectez le **Nested** propriété de la **DataRelation** à **true** lorsque vous ajoutez le **DataRelation** à la <xref:System.Data.DataSet>. Pour plus d’informations, consultez [d’imbrication de DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).  
  
 Vous trouverez ci-après deux exemples illustrant l'écriture de la représentation XML d'un objet <xref:System.Data.DataSet> dans un fichier. Le premier exemple passe le nom de fichier pour le code XML résultant sous forme de chaîne pour **WriteXml**. Le second exemple passe un **System.IO.StreamWriter** objet.  
  
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
 Vous pouvez spécifier la façon dont une colonne d’une table est représentée en XML à l’aide de la **ColumnMapping** propriété de la **DataColumn** objet. Le tableau suivant présente les différentes **MappingType** les valeurs pour le **ColumnMapping** propriété d’une colonne de table et les données XML résultantes.  
  
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
 [L’écriture des informations de schéma d’un DataSet comme XSD](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
