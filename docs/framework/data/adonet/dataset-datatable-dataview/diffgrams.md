---
title: "DiffGrams | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DiffGrams
Un DiffGram est un format XML qui identifie la version actuelle et la version d'origine d'éléments de données.  L'objet <xref:System.Data.DataSet> utilise le format DiffGram pour charger son contenu et le rendre persistent, ainsi que pour le sérialiser en vue de son transport via une connexion réseau.  Lorsqu'un objet <xref:System.Data.DataSet> est écrit en tant que DiffGram, il remplit le DiffGram en y plaçant toutes les informations requises pour recréer précisément le contenu, mais pas le schéma, de l'objet <xref:System.Data.DataSet>, y compris des valeurs de colonne provenant des versions de la ligne, des informations d'erreur de ligne et de l'ordre des lignes **Original** et **Current**.  
  
 Lors de l'envoi et de l'extraction d'un objet <xref:System.Data.DataSet> à partir d'un service Web XML, le format DiffGram est implicitement utilisé.  En outre, lorsque vous chargez le contenu d'un <xref:System.Data.DataSet> à partir de XML à l'aide de la méthode **ReadXml** ou lorsque vous écrivez le contenu d'un <xref:System.Data.DataSet> en XML à l'aide de la méthode **WriteXml**, vous pouvez spécifier que le contenu sera lu ou écrit sous la forme d'un DiffGram.  Pour plus d’informations, consultez [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) et [Écriture du contenu d'un DataSet sous forme de données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 Si le format DiffGram est principalement utilisé par le .NET Framework en tant que format de sérialisation pour le contenu d'un objet <xref:System.Data.DataSet>, vous pouvez aussi l'utiliser pour modifier des données dans les tables d'une base de données Microsoft SQL Server.  
  
 Un DiffGram est généré en écrivant le contenu de toutes les tables dans un élément **\<diffgram\>**.  
  
### Pour générer un Diffgram  
  
1.  Générez une liste des tables racine \(autrement dit, les tables sans parent\).  
  
2.  Pour chaque table et ses descendants dans la liste, écrivez la version actuelle de toutes les lignes dans la première section Diffgram.  
  
3.  Pour chaque table dans <xref:System.Data.DataSet>, écrivez la version d'origine de toutes les lignes \(le cas échéant\) dans la section **\<before\>** du Diffgram.  
  
4.  Pour les lignes qui contiennent des erreurs, écrivez le contenu de l'erreur dans la section **\<errors\>** du DiffGram.  
  
 Un DiffGram est traité dans l'ordre du début du fichier XML à la fin.  
  
### Pour traiter un Diffgram  
  
1.  Traitez la première section du DiffGram qui contient la version actuelle des lignes.  
  
2.  Traitez la deuxième section ou la section **\<before\>** qui contient la version d'origine de la ligne des lignes modifiées et supprimées.  
  
    > [!NOTE]
    >  Si une ligne est marquée comme supprimée, l'opération de suppression peut aussi supprimer les descendants de la ligne, en fonction de la propriété `Cascade` du <xref:System.Data.DataSet> en cours.  
  
3.  Traitez la section **\<errors\>**.  Définissez les informations d'erreur pour la ligne et la colonne spécifiées pour chaque élément dans cette section.  
  
> [!NOTE]
>  Si vous affectez <xref:System.Data.XmlWriteMode> à DiffGram, le contenu du <xref:System.Data.DataSet> cible et du <xref:System.Data.DataSet> d'origine peut être différent.  
  
## Format DiffGram  
 Le format DiffGram est divisé en trois sections : les données actuelles, les données d'origine \(ou « avant »\) et une section d'erreurs, comme indiqué dans l'exemple suivant.  
  
```  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 Le format DiffGram est constitué des blocs de données suivants :  
  
 **\<**  ***DataInstance***  **\>**  
 Le nom de cet élément, ***DataInstance***, est utilisé à des fins d'explication dans cette documentation.  Un élément ***DataInstance*** représente un <xref:System.Data.DataSet> ou une ligne dans un <xref:System.Data.DataTable>.  À la place de *DataInstance* devrait figurer le nom du <xref:System.Data.DataSet> ou du <xref:System.Data.DataTable>.  Ce bloc du format DiffGram contient les données actuelles, qu'elles aient ou non été modifiées.  Un élément, ou ligne, ayant subi une modification est reconnaissable à l'annotation **diffgr:hasChanges**.  
  
 **\<diffgr:before\>**  
 Ce bloc du format DiffGram contient la version d'origine d'une ligne.  Les éléments de ce bloc sont mis en correspondance avec les éléments du bloc ***DataInstance*** à l'aide de l'annotation **diffgr:id**.  
  
 **\<diffgr:errors\>**  
 Ce bloc du format DiffGram contient les informations d'erreur concernant une ligne donnée du bloc ***DataInstance***.  Les éléments de ce bloc sont mis en correspondance avec les éléments du bloc ***DataInstance*** à l'aide de l'annotation **diffgr:id**.  
  
## Annotations DiffGram  
 Les DiffGrams utilisent plusieurs annotations pour relier les éléments des différents blocs DiffGram qui représentent différentes versions d'une ligne ou des informations d'erreur dans le <xref:System.Data.DataSet>.  
  
 Le tableau suivant décrit les annotations DiffGram définies dans l'espace de noms DiffGram **urn:schemas\-microsoft\-com:xml\-diffgram\-v1**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**id**|Sert à apparier les éléments des blocs **\<diffgr:before\>** et **\<diffgr:errors\>** avec ceux du bloc **\<** ***DataInstance*** **\>**.  Les valeurs de l'annotation **diffgr:id** se présentent sous la forme *\[TableName\]\[RowIdentifier\]*.  Par exemple : `<Customers diffgr:id="Customers1">`.|  
|**parentId**|Identifie l'élément du bloc **\<** ***DataInstance*** **\>** qui est le parent de l'élément en cours.  Les valeurs de l'annotation **diffgr:parentId** se présentent sous la forme *\[TableName\]\[RowIdentifier\]*.  Par exemple : `<Orders diffgr:parentId="Customers1">`.|  
|**hasChanges**|Identifie une ligne du bloc **\<** ***DataInstance*** **\>** comme ayant été modifiée.  L'annotation **hasChanges** peut avoir l'une des deux valeurs suivantes :<br /><br /> **inserted**<br /> Identifie une ligne **Added**.<br /><br /> **modified**<br /> Identifie une ligne **Modified** qui contient une version de la ligne **Original** dans le bloc **\<diffgr:before\>**.  Notez que les lignes **Deleted** auront une version de la ligne **Original** dans le bloc **\<diffgr:before\>**, mais qu'il n'y aura pas d'élément annoté dans le bloc **\<** ***DataInstance*** **\>**.|  
|**hasErrors**|Identifie une ligne dans le bloc **\<** ***DataInstance*** **\>** avec un élément **RowError**.  L'élément en erreur est placé dans le bloc **\<diffgr:errors\>**.|  
|**Erreur**|Contient le texte de l'élément **RowError** pour un élément donné du bloc **\<diffgr:errors\>**.|  
  
 Le <xref:System.Data.DataSet> inclut annotations supplémentaires lors de la lecture ou de l'écriture de son contenu en tant que DiffGram.  Le tableau suivant décrit ces annotations supplémentaires, définies dans l'espace de noms **urn:schemas\-microsoft\-com:xml\-msdata**.  
  
|Annotation|Description|  
|----------------|-----------------|  
|**RowOrder**|Conserve l'ordre des lignes des données d'origine et identifie l'index d'une ligne dans un <xref:System.Data.DataTable> donné.|  
|**Hidden**|Identifie une colonne comme ayant une propriété **ColumnMapping** avec pour valeur **MappingType.Hidden**.  L'attribut est écrit sous la forme **msdata:hidden** *\[ColumnName\]*\="*value*".  Par exemple : `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.<br /><br /> Notez que les colonnes masquées ne sont écrites sous la forme d'un attribut DiffGram que si elles contiennent des données.  Sinon, elles sont ignorées.|  
  
## Exemple de DiffGram  
 Un exemple du format DiffGram vous est proposé ci\-après.  Cet exemple illustre le résultat d'une mise à jour effectuée sur une ligne d'une table avant validation des modifications.  La ligne dont le CustomerID est « ALFKI » a été modifiée, mais pas mise à jour.  En conséquence, il y a une ligne **Current** avec une annotation **diffgr:id** « Customers1 » dans le bloc **\<** ***DataInstance*** **\>** et une ligne **Original** avec une annotation **diffgr:id** « Customers1 » dans le bloc **\<diffgr:before\>**.  La ligne dont le CustomerID est « ANATR » comprend un élément **RowError**. Elle porte donc l'annotation `diffgr:hasErrors="true"` et il y a un élément associé dans le bloc **\<diffgr:errors\>**.  
  
```  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## Voir aussi  
 [Utilisation de XML dans un DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Chargement d'un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [Écriture du contenu d'un DataSet sous forme de données XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)